---
title: "[SOLVED] Software Licensing Question"
date: 2008-09-28
forum: Programming Talk
---

### Post by snova on 2008-09-28
Every source tarball I've ever seen has licensing comments at the top of each source file, and sometimes in other places as well. All of them are exactly the same, and the redundancy seems pointless to me.

I'm just wondering, is this a legal requirement? Why can't you just say "MySoft is licensed so-and-so, a copy of which is included" in the readme and be done with it?

I've even seen one project (Amarok) go so far as to say in the HACKING file that it was *necessary*, but there wasn't any explanation for it, or I wouldn't be asking. I looked around on Google, but I couldn't find anything that looked right.

So I'm asking: is this legally required? Why?

---

### Post by DrMega on 2008-09-28
It is necessary to license software to stop someone else from pinching it and claiming it as their own, and then suing the creators/distributors of the original.

Take the GPL for example. It is open source so you can modify it and redistribute it etc, but you can't then release it as closed source and then claim credit for it and sue the creators of it.

Licensing is necessary because there will always be someone who wants to rip you off.

---

### Post by LaRoza on 2008-09-28
> **snova said:**
> Every source tarball I've ever seen has licensing comments at the top of each source file, and sometimes in other places as well. All of them are exactly the same, and the redundancy seems pointless to me.

I'm just wondering, is this a legal requirement? Why can't you just say "MySoft is licensed so-and-so, a copy of which is included" in the readme and be done with it?

I've even seen one project (Amarok) go so far as to say in the HACKING file that it was *necessary*, but there wasn't any explanation for it, or I wouldn't be asking. I looked around on Google, but I couldn't find anything that looked right.

So I'm asking: is this legally required? Why?

Because source code isn't usually one document.

I don't understand the confusion. It is the code that is licensed, so the code should have a reference to it.

If you look at the "code_standards" file in the sysres program, for example, you see:

```

The following standards are used in all source files:

The first two lines must be:

#!/usr/bin/env python
# -*- coding: utf-8 -*-

A blank line, then:

################################################################################
##<file name>: <description>.
##Copyright (C) 2008  <your name>
##
##This program is free software: you can redistribute it and/or modify
##it under the terms of the GNU General Public License as published by
##the Free Software Foundation, either version 3 of the License, or
##(at your option) any later version.
##
##This program is distributed in the hope that it will be useful,
##but WITHOUT ANY WARRANTY; without even the implied warranty of
##MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
##GNU General Public License for more details.
##
##You should have received a copy of the GNU General Public License
##along with this program.  If not, see <http://www.gnu.org/licenses/>.
################################################################################

All indents must be *four spaces*.

Do not do "from module import *" at all.

```

All code files follow that.

---

### Post by DrMega on 2008-09-28
Sorry I hadn't read the post properly.

As LaRoza said it is the code that is licensed (and usually the concept too).

If I was a dodgey thieving sort and wanted to nick a big function library and then call it my own, if it wasn't made clear what the license was (on that file) I would have a better chance of getting away with it.

Also it is a good practice for consistency. Each file should really summarise what is in there, who did it, why and when.

---

### Post by snova on 2008-09-28
I certainly see the point of licensing, that isn't the question. I just don't know why it has to be in *every single file*- is there a legal reason for it?

If it was a requirement that every licensed file have a statement clarifying it as such, then that would answer my question- it *is* necessary.

Put otherwise, I'm querying the necessity of stating the licensing terms of a project within every source file making it up.

But until I know that for certain, I have to wonder why one can't simply write somewhere in the readme that all sources are licensed in such a way, and then not have to duplicate the same statement everywhere.

It's not that I'm lazy, I just don't see *why*.

> It is the code that is licensed, so the code should have a reference to it.

This makes me wonder if it has something to do with copyright law, but I'm not exactly a lawyer... I guess I'll try looking that up.

EDIT: DrMega beat me to it. Bother. Must be this erratic connection, or my own impatience to hit the reply button without waiting for the whole page...

Ok, it makes sense to clarify the terms on each and every file so that there is no ambiguity, but why does this have to be done on a per-file basis? Is there law in effect to necessitate this? I suppose the real question is whether it is legal for one file to contain the distribution terms for another.

The Wikipedia article is *long*...

Based on what you've been saying so far, I think you've implied that the thing being distributed must have terms attached to it, and it can't be anywhere else. If this is the case, then that's the answer.

---

### Post by DrMega on 2008-09-28
> **snova said:**
> I have to wonder why one can't simply write somewhere in the readme that all sources are licensed in such a way, and then not have to duplicate the same statement everywhere.

Imagine if I was to download the source of some GPL licensed app, and then modify it, and in my modified version I used a copyright protected third party library, then redistributed. It wouldn't be legal because it had the third party copyrighted file in there. If I then passed that on to you, and you used it. You would have no way to know that the copyright protected file I added wasn't covered by the same license as the rest of the app.

Conversely, if I release a commercial app and it uses a GPL license library file, if that file had no license info in there I could just claim it was mine. Of course you could argue that I'd just taken it out, but then if it came to a legal dispute and you could show several copies of the same identical file, from reputable sources, with the GLP info in it, then I'd be pretty powerless to win.

---

### Post by LaRoza on 2008-09-28
Also consider it isn't one work. The code isn't a single object (or an object at all).

A book can have the "license" on the front cover and it is easy to verify any part of that work. Code isn't indexed or published like that.

The code of sysres has a history. The license is in each and every code file. If there is a problem, one could easily look up the license of the code. If it were not licensed like that, it would be much harder. I would technically have copyright, but I couldn't prove it.

Without each "file" having its license set out, it might as well be not licensed.

---

### Post by snova on 2008-09-28
> **DrMega said:**
> Imagine if I was to download the source of some GPL licensed app, and then modify it, and in my modified version I used a copyright protected third party library, then redistributed. It wouldn't be legal because it had the third party copyrighted file in there. If I then passed that on to you, and you used it. You would have no way to know that the copyright protected file I added wasn't covered by the same license as the rest of the app.

Conversely, if I release a commercial app and it uses a GPL license library file, if that file had no license info in there I could just claim it was mine. Of course you could argue that I'd just taken it out, but then if it came to a legal dispute and you could show several copies of the same identical file, from reputable sources, with the GLP info in it, then I'd be pretty powerless to win.

Ok then, that makes sense. It's necessary practice in order to cover what happens if the file is taken out of context.

That answers my question, then. Thank you for the clarification.

That was fast... I'd only just finished editing my last post when I found another reply! I can hardly keep up sometimes.

---

### Post by snova on 2008-09-28
Argh, I just finished the last reply and now LaRoza sneaks in another post in between! This place moves *fast*.

I think that covers my question, though.

---

### Post by drubin on 2008-09-28
> **snova said:**
> Argh, I just finished the last reply and now LaRoza sneaks in another post in between! This place moves *fast*.

I think that covers my question, though.

She tends to do that alot...

Just remember to make things as solved if they are solve. Using the thread tools just above your first post.

---

