---
title: "Diplomacy concerning backend"
date: 2010-01-05
forum: Packaging and Compiling Programs
---

### Post by J V on 2010-01-05
I've written a gtk+ gpl front-end for a CLI program.

I emailed the creator of the back-end a week ago questioning credits on about pages etc, but he hasn't responded.

I would like to package this and possibly get it into the repositories after some community testing but I need a "Diplomatic" solution before I can give anyone the program.

Does anyone have experience with this?

---

### Post by J V on 2010-01-06
bump... Any ideas at all?

---

### Post by Umang on 2010-01-07
Since no experienced person has replied as yet, might as well give you my opinion.

I think you should give him the credits you think he deserves and change it should he reply later. If you think he has done as much work on the final product as you have, then give him equal credit. (e.g. "Backend by ABC, Frontend by XYZ"). Otherwise give him less/more appropriately.

Since you are forking it, and aren't required to take any permission to fork an open-source project, I doubt there is anything wrong with going ahead. (Just make sure the licences are compatible)

---

### Post by J V on 2010-01-08
Looks BSD to me...

> Copyright (c) 1999, 2000, 2001, 2002
Adel I. Mirzazhanov. All rights reserved

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions
are met:
 
     1.Redistributions of source code must retain the above copyright notice,
       this list of conditions and the following disclaimer. 
     2.Redistributions in binary form must reproduce the above copyright
       notice, this list of conditions and the following disclaimer in the
       documentation and/or other materials provided with the distribution. 
     3.The name of the author may not be used to endorse or promote products
       derived from this software without specific prior written permission. 
           
THIS SOFTWARE IS PROVIDED BY THE AUTHOR  ``AS IS'' AND ANY EXPRESS
OR IMPLIED WARRANTIES, INCLUDING,  BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
ARE DISCLAIMED.  IN  NO  EVENT  SHALL THE AUTHOR BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO,  PROCUREMENT OF SUBSTITUTE
GOODS OR SERVICES;  LOSS OF USE,  DATA,  OR  PROFITS;  OR BUSINESS
INTERRUPTION)  HOWEVER  CAUSED  AND  ON  ANY  THEORY OF LIABILITY,
WHETHER  IN  CONTRACT,   STRICT   LIABILITY,  OR  TORT  (INCLUDING
NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.If anyone wants to test it heres a tar.gz, depends on the apg package...

Python and glade, feel free to look under the hood (Bit messy at the moment though lol)

---

### Post by Umang on 2010-01-08
Yes, I don't think point three should be a source of worry. You would just say "Special thanks to Adel I. Mirzazhanov" or "Backend (backend-project-name) Copyright (c) 1999, 2000, 2001, 2002 Adel I. Mirzazhanov."

What bothers me is "All rights reserved". That's not open-source. With the GPL you are disowning the whole source code, claiming just to be its only author not owner. He is *reserving* _all_ rights.

I've never used the BSD licence, so I have no idea about what you can do and what you cannot (or even whether this is BSD or not). 

It beats me, why complicate matters so much? Just stick to GPL, LGPL and whichever three or four major licences exist? Anyway, this is more than a decade ago, so I might have playing with QB when he was doing this, so I have no foot to stand on.

---

### Post by J V on 2010-01-08
Right, well, legally this *is* a completley seperate project, I will compose some sort of extra credits thing while I'm at it...

Edit: Know how to make a yelp file? Would save me the trouble of that stupid highlighted text on the help windows :)

---

### Post by Umang on 2010-01-09
Here's some stuff I found about BSD and GPL compliance.

[http://www.gnu.org/licenses/license-list.html#ModifiedBSD](http://www.gnu.org/licenses/license-list.html#ModifiedBSD) is compliant with the GPL.
[http://www.gnu.org/licenses/license-list.html#OriginalBSD](http://www.gnu.org/licenses/license-list.html#OriginalBSD) is not compliant with the GPL.

It appears to me that this is the modified version, which is GPL compliant. So you can use it just like you would have used a GPL library, I think. You'll have to verify this again.

About "All Rights Reserved", I am embarased to say that I've messed up in this regard. I blindly copied a template for netbeans ([link]("http://rubenlaguna.com/wp/2009/03/05/gplv3-license-template-for-netbeans/")) when I was first writing my project, as a result, every page of source in the project has "All Right Reserved" even though it is GPL3. If it weren't for this thread, I might not have every noticed. Anyway, that leaves me with some work to do. rgrep rgrep rgrep ...

About the yelp file, I believe you'll get more help if post on a separate, new thread.

---

