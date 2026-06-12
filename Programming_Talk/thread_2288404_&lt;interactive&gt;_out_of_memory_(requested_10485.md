---
title: "&lt;interactive&gt;: out of memory (requested 1048576 bytes) in ubuntu in vmware player"
date: 2015-07-27
forum: Programming Talk
---

### Post by zerop2 on 2015-07-27
*Main> let allparams = replicateM 4 [1, 2, 3, 4]
*Main> let allparamscol = replicateM 4 allparams
*Main> outh <- openFile "allmatrix4.txt" WriteMode
*Main> hPrint outh allparamscol
<interactive>: out of memory (requested 1048576 bytes)
martin@ubuntu:~/mal$ 

since maple is so slow in all combinations of matrix, would like to copy the result to maple from haskell

---

