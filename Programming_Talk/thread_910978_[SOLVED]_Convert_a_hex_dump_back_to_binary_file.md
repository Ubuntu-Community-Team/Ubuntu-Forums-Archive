---
title: "[SOLVED] Convert a hex dump back to binary file"
date: 2008-09-05
forum: Programming Talk
---

### Post by troyaner on 2008-09-05
Hi everyone!
I converted a binary file by 
od -t x1 gcalcli-1.4.tgz > gc.txt
to

0000000 1f 8b 08 00 61 12 11 47 00 03 c4 3c 6b 77 da 48
0000020 96 fd d9 7f 61 be 54 48 fb 48 4a 0c 06 c7 4e ba
0000040 99 e0 19 62 e3 84 33 b6 f1 c1 78 d2 59 77 d6 47
0000060 40 01 ea 08 89 d6 23 98 de d9 fd ed 7b 6f 3d a4
0000100 2a bd c0 e9 ee 19 9d 6e 83 4a b7 ee ab ee ab 6e
0000120 89 cc 27 b6 3b 71 9d ef fe cc ab 09 d7 9b 93 13
0000140 fc 6c bd 39 69 b2 fb d6 f1 31 ...

how do I get it back to working binary?

---

### Post by ghostdog74 on 2008-09-05
have you deleted the original? otherwise, you can try using xxd instead of od. man xxd for more info. uudecode/uuencode can also do this for you.

---

### Post by troyaner on 2008-09-05
no, I was looking for an integrity-safe way to mail a bin, google doesn't let me :D 
after some replacing xxd made the job

Thank you very much!!

---

