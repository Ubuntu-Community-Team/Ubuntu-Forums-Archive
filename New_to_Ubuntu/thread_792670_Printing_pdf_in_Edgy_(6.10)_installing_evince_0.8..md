---
title: "Printing pdf in Edgy (6.10): installing evince 0.8.1 or adobe 8.1?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by adli on 2008-05-13
Hi, I am an absolute beginner to ubuntu with a fuzzy recollection of linux in general. i'm trying to figure out some printing issues that i'm having and make some decisions... 

I am running Ubuntu 7.04 which has evince 0.8.1 which works well for me. But the machine I'm trying to sort out is running Ubuntu 6.10 (Edgy Eft) and evince 0.6.1 which unfortunately less print options than evince 0.8.1 In particular I need the Edgy machine to be able to access landscape/portrait printing options which are available in evince 0.8.1 but not 0.6.1. As I see it I have two options:

(1) I was thinking that I could just install evince 0.8.1 on the Edgy machine - is this possible? I've downloaded the evince 0.8.1 package for Feisty. But it contains no deb file and needs to be compiled. I ran a [FONT="Courier New"] ./configure[/FONT] on the package which informed me that I was missing gtk+-2.0, libgnomeui-2.0 and libxml-2.0. So I thought I would hunt those down and then try reinstalling evince 0.8.1 - but then it occured to me that I should check: Can evince 0.8.1 can be installed on Edgy? If so, how is this best done?

(2) I could just install Adobe 8.1 which is free and a number of people have been giving it good reviews on the ubuntu forums. Any major problems with this avenue?

I've been reading about the various pdf reader options but need to stick to one that relies on gnome.  

Any help/advice would be greatly appreciated!

---

### Post by Bloch on 2008-05-13
I'm afraid I can't remember what Edgy was like.

In general you can't install packages from a more recent version on an older version of ubuntu. The binaries for that package have to be compiled for that particular version.

However it is worth a try - download the .deb file and see if it installs.

Compiling yourself is not for newbies. I've tried it with mixed success - entering ./configure etc etc without having a clue what I was doing. The trouble is, the instructions for compiling rightfully assume the user knows *something* about linux, even if only how to change permissions on directories.

The best route seems to be the Adobe 8.1

---

### Post by adli on 2008-05-13
thank bloch! good to have some affirmation. I have got the Adobe Reader 8.1 deb installer and it all works pretty well :)

---

