---
title: "how to not specify the type when run eval from library plugins"
date: 2015-09-26
forum: Programming Talk
---

### Post by zerop2 on 2015-09-26
*Main> eval "head [1,2,3] :: Int" [] :: IO (Maybe Int)
Just 7
*Main> eval "head [1,2,3]" [] :: IO (Maybe Int)


<eval>:1:7:
    No instance for (Num a0) arising from the literal `1'
    The type variable `a0' is ambiguous
    Possible fix: add a type signature that fixes these type variable(s)
    Note: there are several potential instances:
      instance Num Double -- Defined in `GHC.Float'
      instance Num Float -- Defined in `GHC.Float'
      instance Integral a => Num (GHC.Real.Ratio a)
        -- Defined in `GHC.Real'
      ...plus 11 others
    In the expression: 1
    In the first argument of `head', namely `[1, 2, 3]'
    In the expression: head [1, 2, 3]


<eval>:1:19:
    No instance for (Typeable a0) arising from a use of `toDyn'
    The type variable `a0' is ambiguous
    Possible fix: add a type signature that fixes these type variable(s)
    Note: there are several potential instances:
      instance Typeable Dynamic -- Defined in `Data.Dynamic'
      instance [overlap ok] Typeable ()
        -- Defined in `Data.Typeable.Internal'
      instance [overlap ok] Typeable Bool
        -- Defined in `Data.Typeable.Internal'
      ...plus 19 others
    In the expression: toDyn nws
    In the expression: let nws = head [...] in toDyn nws
    In an equation for `resource':
        resource = let nws = head ... in toDyn nws
Nothing

---

### Post by Vaphell on 2015-09-26
i'd risk saying you wont find much haskell help here. Try something like [https://www.reddit.com/r/haskell](https://www.reddit.com/r/haskell)

---

