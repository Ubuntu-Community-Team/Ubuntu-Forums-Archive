---
title: "haskell hPrint has problem, it can not write all in the list"
date: 2015-07-26
forum: Programming Talk
---

### Post by zerop2 on 2015-07-26
is it caused by the file limitation of ubuntu ?
or 
is it caused by the hPrint?
or
is it caused by memory?

import System.IO
let allparams = replicateM 3 [1, 2, 3]
let allparamscol = replicateM 3 allparams
outh <- openFile "allmatrix3.txt" WriteMode
hPrint outh allparamscol

martin@ubuntu:~/mal$ tail -f allmatrix3.txt

,1]],[[3,3,3],[3,2,3],[3,1,2]],[[3,3,3],[3,2,3],[3,1,3]],[[3,3,3],[3,2,3],[3,2,1]],[[3,3,3],[3,2,3],[3,2,2]],[[3,3,3],[3,2,3],[3,2,3]],[[3,3,3],[3,2,3],[3,3,1]],[[3,3,3],[3,2,3],[3,3,2]],[[3,3,3],[3,2,3],[3,3,3]],[[3,3,3],[3,3,1],[1,1,1]],[[3,3,3],[3,3,1],[1,1,2]],[[3,3,3],[3,3,1],[1,1,3]],[[3,3,3],[3,3,1],[1,2,1]],[[3,3,3],[3,3,1],[1,2,2]],[[3,3,3],[3,3,1],[1,2,3]],[[3,3,3],[3,3,1],[1,3,1]],[[3,3,3],[3,3,1],[1,3,2]],[[3,3,3],[3,3,1],[1,3,3]],[[3,3,3],[3,3,1],[2,1,1]],[[3,3,3],[3,3,1],[2,1,2]],[[3,3,3],[3,3,1],[2,1,3]],[[3,3,3],[3,3,1],[2,2,1]],[[3,3,3],[3,3,1],[2,2,2]],[[3,3,3],[3,3,1],[2,2,3]],[[3,3


^C
martin@ubuntu:~/mal$

---

### Post by zerop2 on 2015-07-26
expect [[[1...],[2..]],[[1...],[2..]]] to [[[1...],[2..]];[[1...],[2..]]]

import System.IO
let allparams = replicateM 3 [1, 2, 3]
let allparamscol = replicateM 3 allparams
outh <- openFile "allmatrix3.txt" WriteMode
hPrint outh allparamscol

---

### Post by steeldriver on 2015-07-26
I've never used Haskell - but is it perhaps just a matter of buffering? There's a suggestion here that you should be using hClose to properly close the file handle and flush the i/o buffer:

[http://book.realworldhaskell.org/read/io.html](http://book.realworldhaskell.org/read/io.html)

---

### Post by zerop2 on 2015-07-26
thank you, after close, it is completed

---

