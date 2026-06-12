---
title: "Multiplatform file archiving and retrieval (best method?)"
date: 2008-05-08
forum: Programming Talk
---

### Post by vmlinuz on 2008-05-08
I am currently writing a multi-platform application in C/C++. My application must have the ability to write files and directories to an archive. Also, the application's license is not GPL-compatible (yet).

Do you have suggestions as to what format I should use (tgz, zip, etc.) and how I should write/read that format (libraries)?

---

### Post by dempl_dempl on 2008-05-08
Hmm.. I'm currently writing a library which would suite your needs :)  . 

The only thing is , I'm STILL writing it :) . 

I've done quite a research on that field. Tell me what you do, and I'll give you a link to the good library .

In general , this is the very good option:

[http://www.artpol-software.com/ZipArchive/](http://www.artpol-software.com/ZipArchive/)

It's pure C++ , compiles nicely , and it's fully PkZip  compatible ( AES encryption and stuff ) and it can be licensed under non-GNU gpl

The next one is Minizip.

You can find it as a part of **zlib** library under **contrib** directory  . It has couple of few bugs,  though , but you'll hardly going to notice them ( all of them are password-related )

[www.zlib.net/](www.zlib.net/) 

Cheers!

---

### Post by aks44 on 2008-05-08
libtar + zlib ?

---

### Post by vmlinuz on 2008-05-08
I need to:

- read/write files' contents
- list directory contents
- create file/directory, remove file/directory (basic file manipulation)

I don't know how patent-encumbered zip is, but I'd much rather go with tar+gz.

---

### Post by dempl_dempl on 2008-05-08
> **vmlinuz said:**
> I need to:

- read/write files' contents
- list directory contents
- create file/directory, remove file/directory (basic file manipulation)

I don't know how patent-encumbered zip is, but I'd much rather go with tar+gz.

Then the Zlib and Minizip is all what you need .

Zip is patent-free . Tar+Gzip can be tiresome. It's a lot easier to use minizip than any tar+gz library .

Cheers!

---

### Post by vmlinuz on 2008-05-08
Thank you very much.

Looks like minizip isn't in the repos. Do I have to manually compile it, or am I missing something?

---

### Post by dempl_dempl on 2008-05-08
> **vmlinuz said:**
> Thank you very much.

Looks like minizip isn't in the repos. Do I have to manually compile it, or am I missing something?

yes you do.

Go to the zlib site.

[www.zlib.net](www.zlib.net)

Download the library . 

Unpack it.

In directory **contrib** , you'll find minizip directory.

Set up paths and stuff.... 


Cheers!

---

### Post by vmlinuz on 2008-05-08
The license is stated in zip.h:
>    Condition of use and distribution are the same than zlib :

  This software is provided 'as-is', without any express or implied
  warranty.  In no event will the authors be held liable for any damages
  arising from the use of this software.

  Permission is granted to anyone to use this software for any purpose,
  including commercial applications, and to alter it and redistribute it
  freely, subject to the following restrictions:

  1. The origin of this software must not be misrepresented; you must not
     claim that you wrote the original software. If you use this software
     in a product, an acknowledgment in the product documentation would be
     appreciated but is not required.
  2. Altered source versions must be plainly marked as such, and must not be
     misrepresented as being the original software.
  3. This notice may not be removed or altered from any source distribution.


Does this mean I can simply include and compile it directly into my (non-OSS) application?

---

### Post by dempl_dempl on 2008-05-08
> **vmlinuz said:**
> The license is stated in zip.h:

...
Permission is granted to anyone to use this software for any purpose,
including commercial applications, and to alter it and redistribute it
freely, subject to the following restrictions:
..
Does this mean I can simply include and compile it directly into my (non-OSS) application?

Yes.

---

### Post by vmlinuz on 2008-05-08
Thank you very much for all your answers, dempl_dempl.

________________
Regards,
vmlinuz

---

### Post by dempl_dempl on 2008-05-08
He he ... now .. you're making me blush :)

---

