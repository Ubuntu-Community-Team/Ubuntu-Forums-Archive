---
title: "how to solve library between sudo ghci and ghci in haskell"
date: 2015-09-26
forum: Programming Talk
---

### Post by zerop2 on 2015-09-26
some library must need sudo ghci in order to succeed to install

but some library only can run in normal user mode, ghci

when i use with normal user mode ghci, i can not use the library which installed with sudo cabal install before

when run in sudo ghci mode, has error, only no error in normal user mode

*Main> let aa = splitOn " " "head tail [1,2,3]" 
*Main> let bb = filter (not . null) aa 


<interactive>:21:22: Not in scope: `.'

---

