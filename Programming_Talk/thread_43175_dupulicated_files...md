---
title: "dupulicated files.."
date: 2005-06-21
forum: Programming Talk
---

### Post by kimes on 2005-06-21
Let me tell you my case. I've got lots of lots of gigabytes files some might be dupulicated.. My task is to remove extactly dupulucated things.. At first I thought I can check'em with file size. but soon I realized that I can't make sure those files are EXACTLY same only with file size. so I searched internet and found 'md5' or 'crc' which is also builtin(?) tools in linux.. I was happy but I again realized that It takes too long time to digest those files which is over number of gigabytes..

How can I handle this kind of situation?
I'm thinking after take some number of bytes on the front of file and digest only for it. it must take much shorter time but the result wouldn't be good..
Is there any other better algorithm?

---

### Post by Alexander Kirillov on 2005-06-21
[QUOTE=kimes]Let me tell you my case. I've got lots of lots of gigabytes files some might be dupulicated.. My task is to remove extactly dupulucated things.. At first I thought I can check'em with file size. but soon I realized that I can't make sure those files are EXACTLY same only with file size. so I searched internet and found 'md5' or 'crc' which is also builtin(?) tools in linux.. I was happy but I again realized that It takes too long time to digest those files which is over number of gigabytes..

How can I handle this kind of situation?
I'm thinking after take some number of bytes on the front of file and digest only for it. it must take much shorter time but the result wouldn't be good..
Is there any other better algorithm?[/QUOTE]
 I'd do it like this:
 1. look for files of the same size 
 2. once you found files of the same size, start comparing them byte-by-byte until you reach end of file or find a difference. 

It will be definitely faster than computing md5

---

