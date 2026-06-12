---
title: "Creative Commons project hosting service available?"
date: 2008-09-16
forum: Programming Talk
---

### Post by irrdev on 2008-09-16
I am currently developing a network library which I soon plan to release. However, I would like to retain my rights over the library, without making it closed-source. The [Creative Commons]("http://creativecommons.org/") licenses seem perfect for my needs. However, I have been unable to find a SourceForge or Google Code equivalent which will allow me to host my library solely under this license. Does such a hosting service exist? I would like to have a SVN repository, file hosting, and preferably website hosting, too. Any suggestions?

Thanks in advance! :smile:

---

### Post by cb951303 on 2008-09-16
direct quotation form fsf.org

> 
Creative Commons Attribution 2.0 license (a.k.a. CC-BY) and
Creative Commons Attribution-Sharealike 2.0 license (a.k.a. CC-BY-SA):

This is a non-copyleft free license that is good for art and entertainment works, and educational works. Please don't use it for software or documentation, since it is incompatible with the GNU GPL and with the GNU FDL.

---

### Post by irrdev on 2008-09-16
I realise that the Creative Commons Licenses are not compatible with the GPL. I wish to retain full rights to my code, however, although I am happy for users to compile it on their platform and use it in closed-source/commercial software. None of the OSI-approved licenses grant this freedom without sacrificing the rights of the developer. When I create applications, I am fine with releasing this software under the GPL, and I have done just that with two previous projects. Software libraries are different, however, as licenese such as the GPL "infect" the projects which use them. The BDS license, on the other hand, retains absolutely no rights for me, the developer. The Creative Commons license is therefore my preferred choice.

---

### Post by tinny on 2008-09-16
What rights does creative commons give you that GPL doesnt?

(Im trying to learn about this sort of thing right now :-) )

---

### Post by kavon89 on 2008-09-16
If you have a Gmail account, have a look at Google Sites. They have a pretty nice system going which would allow other developers or authorized people to edit and update the website to help collaborate. I believe the bandwidth is unlimited but you've only got 100MB of storage.

EDIT: After re-reading your first post, this suggestion is probably not helpful in your case but I'll leave it here anyway.

---

### Post by nvteighen on 2008-09-16
> **irrdev said:**
> I realise that the Creative Commons Licenses are not compatible with the GPL. I wish to retain full rights to my code, however, although I am happy for users to compile it on their platform and use it in closed-source/commercial software. None of the OSI-approved licenses grant this freedom without sacrificing the rights of the developer. When I create applications, I am fine with releasing this software under the GPL, and I have done just that with two previous projects. Software libraries are different, however, as licenese such as the GPL "infect" the projects which use them. The BDS license, on the other hand, retains absolutely no rights for me, the developer. The Creative Commons license is therefore my preferred choice.

1. CC licenses are somewhat flawed for software, they don't distinguish between source code and object code; they just refer to "works"... the problem is that in software the very same code can be presented in two ways and both have different consequences on the right the user has over the same copyrighted work.

2. You're absolutely wrong about BSD-style licenses. Read the bolded text of this BSD-style template:
```

Copyright (c) <year> <your name>
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions
are met:
1. [b]Redistributions of source code must retain the above copyright
   notice, this list of conditions and the following disclaimer.[/b]
2. Redistributions in binary form [b]must reproduce the above copyright
   notice[/b], this list of conditions and the following disclaimer in the
   documentation and/or other materials provided with the distribution.
3. Neither the name of <your name> nor the names of its contributors
   may be used to endorse or promote products derived from this software
   without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE REGENTS AND CONTRIBUTORS ``AS IS'' AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
ARE DISCLAIMED.  IN NO EVENT SHALL THE REGENTS OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS
OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION)
HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY
OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF
SUCH DAMAGE.

```

3. And you have also the MIT License (aka X11 License):
```

Copyright (c) <year> <copyright holders>

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

[b]The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.[/b]

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

```

---

### Post by irrdev on 2008-09-18
Thanks nvteighen for the corrections. The BDS license is still a bit too liberal for me, but the MIT license looks promising, as does the Mozilla Public License. The latter in particular seems to be the closes OSI license to what I am looking for. I am going to look into this further. :smile:

---

### Post by nvteighen on 2008-09-18
Remember the BSD and MIT license texts are in the public domain and you can make them fit to your needs.

---

### Post by irrdev on 2008-09-18
> **nvteighen said:**
> Remember the BSD and MIT license texts are in the public domain and you can make them fit to your needs.
Does SourceForge host projects released under the BSD/MIT license with slight modifications?

---

### Post by pmasiar on 2008-09-18
> **irrdev said:**
> Does SourceForge host projects released under the BSD/MIT license with slight modifications?

"slight modification" is a poison - it will prevent people moving code from and to your project, prevent collaboration. Think twice about it, and then don't do it :-)

It's not about what modifications you want or like: it's about what you absolutely cannot avoid, and why. Chances are, if license was good for other, is good for you - or pick different one, don't create your own version without advice of a competent lawyer.

---

