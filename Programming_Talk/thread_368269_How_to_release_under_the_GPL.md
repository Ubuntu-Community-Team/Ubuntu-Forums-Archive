---
title: "How to release under the GPL"
date: 2007-02-23
forum: Programming Talk
---

### Post by Greykrrr on 2007-02-23
hi

I am currently a small piece of software which really is more for pratice than anything. However I would like to release it for others to see but I feel that it would be best to release it under a license than as freeware.

I just don't know exactly how to do this. I have had a look at the GNU foundations homepage but I am still a little as to where to put copyright and legal notices and just what all that means.

Also I heard somewhere about a kind of GPL-o-matic which could spit out a version of the GPL that was better suited individuals (so that legal disputes should not be tried in the US for instance).

Anyway. None of this is really crucial to the program but I feel that this part of it can be good practice as well for when/if I actually write something that is really worth protecting.

---

### Post by Ed Ropple on 2007-02-23
Make a file called COPYING. Insert the text of the GPL in it (and do remember that it is within your rights as a developer to remove the "or any later version" clause in the GPL). Insert reference to the GPL in all source files as well.

Put a line within the output or display of the program that says something along the lines of "XXXX is released under the General Public License, (C) 2007 Yourname Here".

That should cover you.

---

### Post by rolando2424 on 2007-02-23
I just put this on the top of the source file (all my python script have been only one file :D)

> # This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.


And then put a copy of the full license in my website.

---

### Post by pmasiar on 2007-02-23
> **Greykrrr said:**
> (...)where to put copyright and legal notices and just what all that means.

Also I heard somewhere about a kind of GPL-o-matic which could spit out a version of the GPL that was better suited individuals (so that legal disputes should not be tried in the US for instance).

Most important thing to avoid IMHO is to have your own *custom* GPL-like license. Because if you have customized GPL, something need be ignored, and one ot two will happen: 

(1) if you are lucky, your  *GPL customizations* will be ignored and code will be used by other people.
(2) if not lucky, your *code* will be ignored.

Of course there is a slight possibility someone hiring a lawyer to figure out how to use your code with standard GPL - when pigs fly.... :-)

Another *sure way to obscurity* for your program IMHO is to remove "... or later versions" clause. GPL V3 is coming, it is inevitable, and you want to be compatible. Stallman was right with GPL V1 and V2, I bet he will be right again - and now it is not only RMS, lot of legal experts are looking into it. And I do not consider Linus or any other kernel hackers be *legal* experts in matter of GPL :-) Eben Moglen is one, Lessig is another.

BTW GPL V3 allows (IMHO, IIUC) to slight changes in wording (like changing the ruling law) which GPL V2 did not considered - yet another reason to keep "... or later" clause :-)

If you do not want to be bothered by legal matters, you can assign copyright to FSF - free software foundation - they have legal resources to handle it.

IANAL, IMHO, YMMV. This is free advice - use at your own risk. To get expert advice taking into consideration all your concerns, you may want to hire a lawyer.

---

### Post by Greykrrr on 2007-02-23
> **pmasiar said:**
> To get expert advice taking into consideration all your concerns, you may want to hire a lawyer.

Not quite there yet ;)

But yes, I actually agree with you. v3 of the GPL doesn't seem like such a bad idea and I like what it has to say about DRM. 

I don't actually intend to change any of the points in the license, the only thing I am concerned about is , _if_ a dispute should occur for whatever reason, I would like to be able to defend my position in Europe before a European court and its laws and since the GPL is written in the US for the US courts I don't know if I am bound to defend dispute before an american court. And that is the only detail I am trying to figure out about the GPL. Other than that, I find it to be a good and sound license.

Another thing is those notices that are to go in the source files, does that mean _all_ source files? Class files and headers as well?

Btw, what do all those abbreviations mean? IMHO, YMMV and all that. I've seen it used quite a bit in these forums but I don't get it...

---

### Post by pmasiar on 2007-02-23
> **Greykrrr said:**
> the only thing I am concerned about is , _if_ a dispute should occur for whatever reason, I would like to be able to defend my position in Europe before a European court 

Check FSF-Europe - [http://en.wikipedia.org/wiki/Free_Software_Foundation_Europe](http://en.wikipedia.org/wiki/Free_Software_Foundation_Europe) they may have some good generic solution for this FAQ.

> those notices that are to go in the source files, does that mean _all_ source files? Class files and headers as well?

All files covered by the license, obviously.

> Btw, what do all those abbreviations mean? IMHO, YMMV and all that. .

[http://www.acronymfinder.com/](http://www.acronymfinder.com/) knows all of them, see also [http://en.wikipedia.org/wiki/Tla](http://en.wikipedia.org/wiki/Tla)

---

### Post by SuperMike on 2007-02-23
I would agree not to customize your own GPL but, instead, use a separate kind of license more suitable for that. With straight GPL, you get the slight chance that your legal protection can come from the writers of the GPL. That's the case that happened recently last year where someone wrote a model railroad management computer program, released it under the GPL, and got taken to court by a patent troll. I think I read the FSF showed up with their lawyers to defend him.

---

### Post by pmasiar on 2007-02-23
> **SuperMike said:**
> I would agree not to customize your own GPL but, instead, use a separate kind of license more suitable for that. With straight GPL, you get the slight chance that your legal protection can come from the writers of the GPL. That's the case that happened recently last year where someone wrote a model railroad management computer program, released it under the GPL, and got taken to court by a patent troll. I think I read the FSF showed up with their lawyers to defend him.


what "separate kind"? BSD? can you be more specific? who will protect you with this mythical other licence?

FSF protected the railroad guy exactly because it was GPL. If it was something non-GPL, why should they? you just proved that sticking with GPL is *better*, not worse.

---

