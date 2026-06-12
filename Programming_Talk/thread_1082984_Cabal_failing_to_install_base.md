---
title: "Cabal failing to install base"
date: 2009-02-28
forum: Programming Talk
---

### Post by viraptor on 2009-02-28
Hi
I'm trying to install Yi, but that depends on many other packages. I got the deps list down to:

Configuring yi-0.5.3...
cabal: At least the following dependencies are missing:
base >=4,
binary >=0.4.2 && <0.5,
ghc ==6.8.3 || ==6.10.1,
pointedlist >=0.3.1

But then 'cabal install base --reinstall' returns:
cabal: cannot configure base-4.0.0.0. It requires ghc-prim -any and integer
-any
There is no available version of ghc-prim that satisfies -any
There is no available version of integer that satisfies -any

Any ideas on how to fix it?

---

### Post by bgilbert on 2009-05-14
I'm having the exact same problem....did you ever find a solution?


***Update***

I've found what the problem is and the solution. Apparently the version of GHC available in the repositories is an older version: 6.8.2. Which between revisions 6.8.2 and 6.8.3 the 'base' was updated to version 4. Cabal is unable to update the base version, it needs to be done through and updated GHC install. 

Details on installing the newest version of GHC (6.10.3) are located here: [http://www.johnmacfarlane.net/Gitit%20on%20Ubuntu?diff&to=b51a2d9]("http://www.johnmacfarlane.net/Gitit%20on%20Ubuntu?diff&to=b51a2d9")

---

