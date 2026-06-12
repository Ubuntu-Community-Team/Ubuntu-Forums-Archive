---
title: "How to release code under BSD"
date: 2009-09-26
forum: Programming Talk
---

### Post by nmccrina on 2009-09-26
I'm starting a text-based adventure game, and would like to release it under the BSD license. However, after poking around the internet for a while, I can't find any guidelines as to how to go about including the license in my code. Should I include the full text of the license at the top of all the source files (.cpp and .h), or should there just be a LICENSE.txt, or what? :confused:

Thanks for your input!

---

### Post by -grubby on 2009-09-26
A file called "LICENSE" and a small copyright notice (I.e "Copyright (C) 2009 Some dude" should work.

---

### Post by tom66 on 2009-09-26
Usually there's something like a warranty disclaimer, copyright, version at the top of the file. I found this on Wikipedia:

```

Copyright (c) <year>, <copyright holder>
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:
    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.
    * Redistributions in binary form must reproduce the above copyright
      notice, this list of conditions and the following disclaimer in the
      documentation and/or other materials provided with the distribution.
    * Neither the name of the <organization> nor the
      names of its contributors may be used to endorse or promote products
      derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY <copyright holder> ''AS IS'' AND ANY
EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL <copyright holder> BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

```

---

### Post by Bachstelze on 2009-09-26
[ftp://itsuki.fkraiem.org/pub/NALG/NALG-0.1rc3/NALG.py](ftp://itsuki.fkraiem.org/pub/NALG/NALG-0.1rc3/NALG.py) for example.

It is usualy better to put the full text of the licence in every source file.

---

### Post by phrostbyte on 2009-09-26
A file called LICENSE or COPYING is a typical convention. People sometimes put the license or an small portion of it in the header too. You can look at some source tarballs on the 'net for inspiration. :)

---

### Post by ZuLuuuuuu on 2009-09-27
Actually, are there any guidelines to how to release a software? For example, I see files like AUTHORS, INSTALL, LICENSE without any extensions, I see source code is distributed with tar.gz, I see some software come with makefiles etc. But these conventions change from software to software, slightly. Where do these conventions come from and is there a place I can find all the conventions?

---

### Post by nvteighen on 2009-09-27
The only requirement is that you state your copyright and your licensing terms in some convenient way. How you do it is up to you.

But, of course, in Free Software, as your code could be taken off your project and reused anywhere else, the usual thing done is:

1. Put the copyright and licensing info in each header and source file. Also add any other relevant copyright info for any code you've taken an used in that file.
2. Put a copyright file in the project's root directory. Also add other copyright and licensing info from other projects which are appliable only after compiling (shared and static libraries, usually).
3. An AUTHORS file is useful when you decide to assign copyright to a team... (e.g. Mozilla).
4. The COPYING file is the "standard" place where you have your GPL text put.

But these are guidelines. Do whatever you think is clear enough to state your code is BSD.

---

