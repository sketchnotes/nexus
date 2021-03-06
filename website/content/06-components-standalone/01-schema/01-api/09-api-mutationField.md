---
title: mutationField
---

## mutationField

Mutations are usually best split up, and are one of the most common use-cases for `extendType`. `mutationField` exists as a shorthand for this common case:

```ts
export const createUser = mutationField('createUser', {
  type: SomeType,
  resolve() {
    // ...
  },
})
```

as shorthand for:

```ts
export const createUser = extendType({
  type: "Mutation",
  definition(t) {
    t.field('createUser', {
      type: SomeType
      resolve() {
        // ...
      }
    })
  }
})
```

You can also use it with a function as the first argument, which will pass the `t` provided to the defintion block, especially useful when using with the [connection plugin](plugin-connection.md):

```ts
export const usersQueryField = mutationField(t => {
  t.connectionField('updateUsersList', {
    type: SomeType,
    resolve() {
      // ...
    },
  })
})
```
