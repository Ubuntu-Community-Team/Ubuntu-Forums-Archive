---
title: "Etiquette?"
date: 2008-07-30
forum: Programming Talk
---

### Post by theyain on 2008-07-30
I realize that this could easily be in the wrong place, however this is the closest match to what I want to talk about.

-----

There is a program I want to use, however it lacks a very important feature I need and the development of said program died about four years ago (at version 0.2).  But I would not only like to add that feature, but I want to go a step further and actually create a new branch/fork (gah, can't think of the correct term!) of that program.

Now before I do that, I was curious as to the proper etiquette of new version numbers, attribution, naming, and things like that.   Basically what I am asking is what should I worry about when starting a new project like this by branching off of an old, dead one?

-----

Also, to keep this semi on topic; does anyone have any good Linux based C# tutorials?  I've become a wee bit rusty.


PS, sorry if my sentence structure, spelling, and everything else seems off.  I can't sleep so I'm extremely tired.

---

### Post by tinny on 2008-07-30
Interesting question. Do you know what license this application is released under?

I guess one of the first things you could do is touch base with the project maintainer in a friendly way to ascertain that the project really is dead and that they arent just lacking some motivation.

Who knows a friendly "hi I really like your project, are you still developing this? Would you like some help", just might be the thing the project maintainer needs to pick things up again.

---

### Post by nvteighen on 2008-07-30
First of all, check the license! Naming and attribution may be regulated by that document.

As of versioning numbers, there are funny cases, like the glibc vs. linux-libc  ([http://en.wikipedia.org/wiki/Glibc#A_temporary_fork](http://en.wikipedia.org/wiki/Glibc#A_temporary_fork))... Probably you should start from 0.0.1 to keep it clear that's the first release of your fork?

EDIT: tinny has posted a better idea.

---

### Post by rjack on 2008-07-30
> **theyain said:**
> Basically what I am asking is what should I worry about when starting a new project like this by branching off of an old, dead one?

As long as you respect the project's license you're ok.

But it would be nice to send a mail to the author anyway. Probabily she/he would be happy to know that someone is interested in her/his abandoned project.

---

### Post by LaRoza on 2008-07-30
> **theyain said:**
> 
There is a program I want to use, however it lacks a very important feature I need and the development of said program died about four years ago (at version 0.2).  But I would not only like to add that feature, but I want to go a step further and actually create a new branch/fork (gah, can't think of the correct term!) of that program.

Now before I do that, I was curious as to the proper etiquette of new version numbers, attribution, naming, and things like that.   Basically what I am asking is what should I worry about when starting a new project like this by branching off of an old, dead one?
Here is a good article (from Cathedral and the Bazaar): [http://catb.org/~esr/writings/homesteading/homesteading/](http://catb.org/~esr/writings/homesteading/homesteading/)

If you want to really be the new owner of the project, follow the guidelines in that book. If you just want to use it for yourself, you don't have to worry about it (and if you decide to own it, you can always use your work to support your cause)


> 
Also, to keep this semi on topic; does anyone have any good Linux based C# tutorials?  I've become a wee bit rusty.

See my wiki. Doesn't have a lot of C# on it, but it has some. If you are asking about using C# on Linux (how to compile, etc) see the sticky.

---

### Post by theyain on 2008-07-30
> **tinny said:**
> Interesting question. Do you know what license this application is released under?

GPL

> 
I guess one of the first things you could do is touch base with the project maintainer in a friendly way to ascertain that the project really is dead and that they arent just lacking some motivation.

4 years of inactivity made me think it was dead, and the fact that he removed all reference of it from his website also made me think this.

> 
Who knows a friendly "hi I really like your project, are you still developing this? Would you like some help", just might be the thing the project maintainer needs to pick things up again.

Just emailed him as a just in case.

---

### Post by nvteighen on 2008-07-30
> **theyain said:**
> GPL

Neither GPLv2 nor GPLv3 include any term to change the name of the product in a fork, unless trademarks apply, but you are required to mark "prominently" your version as modified.

Attribution in GPL is achieved my mantaining copyright notices intact.

Usually, what's done is:
1. Include a COPYING file with the text of the applied license.
2. Include a COPYRIGHT file where you put your copyright notice + the license notice + all required notices from all works you have used.

---

### Post by theyain on 2008-07-30
> **LaRoza said:**
> Here is a good article (from Cathedral and the Bazaar): [http://catb.org/~esr/writings/homesteading/homesteading/](http://catb.org/~esr/writings/homesteading/homesteading/)

If you want to really be the new owner of the project, follow the guidelines in that book.

Thank you for the book.  This actually covers quite a few things I was curious about.

> **nvteighen said:**
> Neither GPLv2 nor GPLv3 include any term to change the name of the product in a fork, unless trademarks apply, but you are required to mark "prominently" your version as modified.

However I can change it, correct? And would changing the name be a prominent mark showing that my version is a modified version of the original? If not, what would be then?

Sorry if these are basic questions, again I'm tired.  I'm probably going to hit my self in the head when I reread this thread in the morning.

Also, there is neither a COPYRIGHT or COPYING text file in the source tar ball.  The only reason why I knew it was under GPL was that a README said that it was under GPL.  Not even the entire license was include.  Just "Licensed under GNU General Public License".



And on a side not, My only way of contacting the orig author was through his email which no longer seems to be valid (delivery failure).

---

### Post by LaRoza on 2008-07-30
> **theyain said:**
> Thank you for the book.  This actually covers quite a few things I was curious about.

And on a side not, My only way of contacting the orig author was through his email which no longer seems to be valid (delivery failure).

In that case, it can be yours. You did your best.

---

### Post by nvteighen on 2008-07-30
> **theyain said:**
> 
However I can change it, correct? And would changing the name be a prominent mark showing that my version is a modified version of the original? If not, what would be then?

I think it's prominent enough. The spirit of GPL in this is to avoid the original developers being blamed for any silly thing you do :)

> 
Also, there is neither a COPYRIGHT or COPYING text file in the source tar ball.  The only reason why I knew it was under GPL was that a README said that it was under GPL.  Not even the entire license was include.  Just "Licensed under GNU General Public License".

I was talking of what's usual and most readable... The license just requires you to keep all notices intact, so if the notice is "Licensed under GNU General Public License", keep that intact... Take a look on how do "real" applications do this (at /usr/share/doc/<any package>).

Also, as there's no GPL version explicitly mentioned, you're allowed to use **any** published version of the license. I'd **suggest** you to move to GPLv3 (but, GPLv2 is easier to read... look at both; the differences are mainly legal subtilities)

My way would be to put something like this in COPYRIGHT:
```

    blah-forked - Fork of blah

    Copyright (c) 2008 me

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>.

    On Debian GNU/Linux based systems, you may find a copy of the License
    text at /usr/share/common-licenses/GPL-3.

This notices are required by the work(s) this is/are based on:

    blah:

    Copyright (c) 2008 blah's developer(s)

    Licensed under GPL General Public License.


```

---

### Post by pmasiar on 2008-07-30
> **theyain said:**
> My only way of contacting the orig author was through his email which no longer seems to be valid (delivery failure).

... so the code is yours! Consider releasing any changed file under "GPLv3 or later", and prominently thank original developer on your project website.

---

