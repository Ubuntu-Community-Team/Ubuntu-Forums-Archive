---
title: "How do I clear screen in terminal"
date: 2013-11-19
forum: New to Ubuntu
---

### Post by shai3 on 2013-11-19
I'm using Ubuntu 13.10 on a VMware virtual machine installed on my Mac for about three days now.

In terminal on the Mac there is command-K which clears the screen; I really like it.

I'm using the Terminal application that came with Ubuntu.

From the GUI menu I see "Reset." But when I go to the keyboard shortcuts part of the Terminal app, it says "Disabled" next to "Reset."

How can I enable a keyboard shortcut to clear or reset the screen?

Thank you.

Shai

---

### Post by BrunoLotse on 2013-11-19
Hi:)To clear screen in terminal try shortcut ```
Control-L
```    or type command ```
clear
```Cheers,Bruno

---

### Post by The Cog on 2013-11-19
Ooh! I never knew the ^L one.

In rare occasions (especially when catting binaries to the console by mistake), the console gets stuck in a mode where things don't print properly. In those instances, I use **reset** which seems more thorough in restoring settings.

---

### Post by shai3 on 2013-11-19
Wow, so easy. Thanks.

Are those documented somewhere?

Shai

---

### Post by Lars Noodén on 2013-11-19
It looks like both clear and ctrl-L are described in the manual page for bash, but you almost have to know they are there to find them.  If you look hard you can find it in there.

```

man bash

```

If I recall correctly, ctrl-l was 'form feed' and used to advance the teletype to the next fold in the paper.   It got carried over to clear the screen when we moved off of paper.

---

### Post by philinux on 2013-11-19
> **shai3 said:**
> Wow, so easy. Thanks.

Are those documented somewhere?

Shai

[http://linux.about.com/od/lts_guide/a/gdelts17.htm](http://linux.about.com/od/lts_guide/a/gdelts17.htm)

ctrl r is awesome

[http://how-to.wikia.com/wiki/How_to_use_short-cut_keys_in_xterm_and_other_terminals](http://how-to.wikia.com/wiki/How_to_use_short-cut_keys_in_xterm_and_other_terminals)

---

### Post by t0p on 2013-11-19
> **shai3 said:**
> Are those documented somewhere?

Shai

[The Linux Documentation Project]("http://www.tldp.org/") (tldp.org) is a handy site to find tutorials and other things Linux.  Check it out.

---

### Post by public3 on 2013-11-19
If you have garbage output all over you screen (just weird looking symbols/non-english chars) 'reset' will also work like a charm.

---

### Post by DuckHook on 2013-11-20
The Bash man page is excruciating. Does anyone actually understand it? Don't get me wrong... I very much appreciate all of the contributions that the FOSS community has made to the Linux-sphere, but that has to be the densest, most obscure and jargon-laden piece of arcanna I've ever tried to decipher. In my opinion, it stands as a shining example of how not to write a man page, which, after all, is at least partly meant to be a help document. What most distros need is a Bash cheater sheet for the rest of us. Perhaps just eight or ten screens deep and filled with stuff like <Ctrl>+<r> and <Ctrl>+<l> with one- or two-line summaries of use and function.

Ahh. Feel better now that I've got that off my chest.

---

### Post by Lars Noodén on 2013-11-20
> **DuckHook said:**
> The Bash man page is excruciating...

Yeah, it's definitely not one of the best.  The format used is not hard to work with and is quick to learn, so if you are good at technical writing, you could propose a new version upstream.  It really needs reworking.

---

### Post by amakwana-serpentcs on 2013-11-20
Use Ctrl + L or write > clear and press enter to clear screen.

---

### Post by drmrgd on 2013-11-20
> **DuckHook said:**
> The Bash man page is excruciating. Does anyone actually understand it? Don't get me wrong... I very much appreciate all of the contributions that the FOSS community has made to the Linux-sphere, but that has to be the densest, most obscure and jargon-laden piece of arcanna I've ever tried to decipher. In my opinion, it stands as a shining example of how not to write a man page, which, after all, is at least partly meant to be a help document. What most distros need is a Bash cheater sheet for the rest of us. Perhaps just eight or ten screens deep and filled with stuff like <Ctrl>+<r> and <Ctrl>+<l> with one- or two-line summaries of use and function.

Ahh. Feel better now that I've got that off my chest.

You've clearly never read the docs for [R]("http://www.r-project.org/") :)

Seriously, though, a cheat sheet is not a bad idea.  Had a quick look (just for kicks), and found this:

[http://cli.learncodethehardway.org/bash_cheat_sheet.pdf](http://cli.learncodethehardway.org/bash_cheat_sheet.pdf)

Seems like it could be handy.

---

### Post by vasa1 on 2013-11-20
> **DuckHook said:**
> The Bash man page is excruciating. ....
Regex(7) isn't far away ;)

---

### Post by shai3 on 2013-11-20
Gang,

Thanks for the great advice, great conversation, and great links.

@philinux, whoa, Ctrl-r IS awesome. So much good stuff out there to find.

This Linux newbie is having fun :P.

Shai

---

### Post by efflandt on 2013-11-20
I am old school, so when binary output to the screen messes it up or playing with ansi screen codes makes newly typed text invisible (black on black or white on white text/background), I (blindly if necessary) type: **stty sane** (when it has gone insane)

But I guess that does the same as **reset** by setting terminal settings to their default values

---

### Post by jimmyh1972 on 2013-11-20
clear

---

### Post by squakie on 2013-11-20
you would really enjoy the unix manuals from the mid-80's ;)

---

### Post by DuckHook on 2013-11-20
> **drmrgd said:**
> ...a cheat sheet is not a bad idea.  Had a quick look (just for kicks), and found this:

[http://cli.learncodethehardway.org/bash_cheat_sheet.pdf](http://cli.learncodethehardway.org/bash_cheat_sheet.pdf)Exactly what the doctor ordered. Thanks for the link.

---

### Post by Zill on 2013-11-21
> **DuckHook said:**
> The Bash man page is excruciating...
I must agree with this one.  ;-)

I have been using Linux for over ten years now and am still discovering new features.  My thanks go to BrunoLotse for Ctrl-l.

I must admit to getting a chuckle from the newbies who pop up here after using Ubuntu for a week or two and declare that they now know *everything* about Linux and shortly intend to produce their own distro. :-)

---

### Post by BrunoLotse on 2013-11-21
> **Zill said:**
> I must agree with this one.  ;-)I have been using Linux for over ten years now and am still discovering new features.  My thanks go to BrunoLotse for Ctrl-l.Hi:) My pleasure!!!> **Zill said:**
> I must admit to getting a chuckle from the newbies who pop up here after using Ubuntu for a week or two and declare that they now know *everything* about Linux and shortly intend to produce their own distro. :-)True, very true:)Cheers,Bruno

---

### Post by thesleash on 2013-11-21
type "clear" without quotes into the terminal

---

### Post by squakie on 2013-11-21
And then there's old guys like me, who years ago knew unix and some proprietary OS's inside and out, come on here expecting I could pick up where I left off, and end up making a complete fool of myself.  I didn't like it though when some person was trying to help me with a networking problem (in the end it was the same things I had already tried) and told me that years of systems programming was basically just pushing JCL.  What an insult - try binary debugging and coding some time ;)  But alas, I still expect things from myself going back to those days and I turn around here, and well, it just gets laughable - people think I'm an idiot and I'm starting to feel like one.  All those years long ago now doing extremely technical OS work, and now I can't even figure out the basics of a unix-like OS ;) ;)

---

### Post by drmrgd on 2013-11-22
> **DuckHook said:**
> Exactly what the doctor ordered. Thanks for the link.

No problem at all!  It's a useful resource for me too.

I also wanted to pass this along.  I was looking for something else in my docs folder and stumbled across this .pdf that I forgot I had.  It's a very useful guide for sysadmins with some common commands and things.  I actually need to have another read through it myself, I think!  Here's a link to it:

[http://cb.vu/unixtoolbox.pdf](http://cb.vu/unixtoolbox.pdf)

---

### Post by DuckHook on 2013-11-22
Just better and better. Much thanks.

---

