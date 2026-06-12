---
title: "How to do a &quot;Grub-like&quot; menu?"
date: 2010-02-22
forum: Programming Talk
---

### Post by trilobite on 2010-02-22
Hi all - 
 I've been doing a few small and simple public-domain apps. One thing I'd like to be able to do is an app with a menu similar to that of Grub's graphical menu. ( Grub is a boot-manager, for those who haven't heard of it). 

I should mention that I'd like to be able to do this in C. 

In Grub, you can move the highlight up and down among a number of menu options, and select an OS to boot. I'm just wondering if anyone has done (or knows of) any public-domain code to do menus like this. I can't look at Grub itself, of course, as it is not public-domain, but GPL. 

Maybe if this menu code is simple enough to do, some example code could even be posted here?  
Many thanks in advance - bye for now - 
- trilobite

---

### Post by Bachstelze on 2010-02-22
> **trilobite said:**
> I can't look at Grub itself, of course, as it is not public-domain, but GPL. 

How does GRUB being GPL prevent you from *looking* at it?

---

### Post by lloyd_b on 2010-02-22
> **trilobite said:**
> Hi all - 
 I've been doing a few small and simple public-domain apps. One thing I'd like to be able to do is an app with a menu similar to that of Grub's graphical menu. ( Grub is a boot-manager, for those who haven't heard of it). 

I should mention that I'd like to be able to do this in C. 

In Grub, you can move the highlight up and down among a number of menu options, and select an OS to boot. I'm just wondering if anyone has done (or knows of) any public-domain code to do menus like this. I can't look at Grub itself, of course, as it is not public-domain, but GPL. 

Maybe if this menu code is simple enough to do, some example code could even be posted here?  
Many thanks in advance - bye for now - 
- trilobite

The ncurses library provides relatively easy methods to implement this.  I'd suggest looking at [this site]("http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/index.html"), as it has good references (though I believe the code itself is under an MIT style license, rather than public domain).

Lloyd B.

---

### Post by rabidbadger on 2010-02-22
Another good reference for ncurses programming [is here]("http://web.cs.mun.ca/%7Erod/ncurses/ncurses.html"). But you could also ask yourself why you would want to add [another layer of abstraction/bloat]("http://www.landley.net/notes.html#17-02-2010") to your code? Just writing out the straight escape sequences is not -- as some would like to tell you -- akin to eating your firstborn, providing that you know your target platform...

---

### Post by trilobite on 2010-02-22
Hi all -  

Many thanks to all who've replied - much appreciated! 
I will look at the links you've provided - they sound very useful. 

As to why I "can't look at Grub, with it being GPL" - although I'm not a lawyer, I was under the impression that if you were doing a project with license "a" (whether it be GPL, public-domain or whatever), then looking at code with a different license is "legally unsafe". I'm unclear as to where the dividing line is between "getting ideas" from (say) GPL'ed code, and those ideas being so similar that they then constitute a "derived work". *That* is what I'm trying to avoid.  

Given that I can't actually *use* GPL'ed, BSD'ed code in a public-domain project, I tend to steer away from looking at it, for exactly the reason I've mentioned.  
- trilobite

---

