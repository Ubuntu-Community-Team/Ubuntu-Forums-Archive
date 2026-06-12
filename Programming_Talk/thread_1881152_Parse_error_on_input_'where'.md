---
title: "Parse error on input 'where'"
date: 2011-11-15
forum: Programming Talk
---

### Post by william2011 on 2011-11-15
Haskell : ghc test1.hs
Parse error on input 'where'
 
promote f = Gen (\n r -> \a -> m n r where Gen m = f a)
 
change heireachy
 
promote :: (a -> Gen b) -> (Gen (a->b))
promote f = Gen (\n r -> 
\a -> 
m n r 
where Gen m = f a)
 
i do not see any problem in above code, why error

---

### Post by cgroza on 2011-11-15
You can't have a where inside a lamda. You still can put it outside the lambda and it will still have tho same effects.
Example:
```

f = (\x -> 5 + z) where z = 5 -- correct

f = (\x -> 5 + z where z = 5) -- incorrect

```

Also, please use code tags since the indentation in Haskell matters.

---

