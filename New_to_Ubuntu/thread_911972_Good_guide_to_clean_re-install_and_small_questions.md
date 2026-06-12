---
title: "Good guide to clean re-install and small questions"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Maupertus on 2008-09-06
Hey guys,

couple of questions, but I've been having a couple of strange problems with Ubuntu lately, so I wanted to do a clean install and do everything right from the beginning. So I wanted to know if anyone can give me a couple of good tips for a re-install and maybe a good how-to guide, because I'm feeling a bit nervous as it's the first time I'm doing this with my main OS/PC. (I must admit I'd been thinking about doing something new like Fedora, but Ubuntu is what I know and like, and if I ever get a 'redundant' second pc, I'll fool around with different OS's

I was wondering if it's smart to make a different partition for my /home and if this will have a large impact on usability/workability etc.

Last question: there used to be a lot of sources.lists here and online, but with the coming of the whole graphical usage of synaptic I've got the feeling that less people are editing the sources.list with gedit. I want to run Ubuntu64 again (as I've always done) is there a good way to keep check on my sources list? It's been getting a bit euh....cluttered lately. *blush*


Sorry for the newbie questions, although I've been a ubuntu fan since 2005, I'm just feeling bit nervous and annoyed with the problems. :(

---

### Post by sanemanmad on 2008-09-06
Well Maupertus ~

One advantage to using a separate partition for your ~ dir is that you would not have to 'relocate' your data in a situation where you needed to reinstall (probably similar to now). So easiest put. you create less risk of losing all your data from a re-install or 'kernel panic' etc...

---

### Post by starcannon on 2008-09-06
I make a separate /home on all of my installs, this as saved me uncountable hours.

My usual way of doing things:

15gb for /
SWAP     equal to my ram or double my ram if the machine in question has less than 2gb.
Whatever is left for /home

this is a general partitioning scheme, I do things much differently on a device like an eeepc.
GL

---

### Post by Vivaldi Gloria on 2008-09-06
> **Maupertus said:**
> I was wondering if it's smart to make a different partition for my /home and if this will have a large impact on usability/workability etc.

I prefer NOT to make a home partition but a seperate storage partition as I expained here:

[http://ubuntuforums.org/showthread.php?t=911729](http://ubuntuforums.org/showthread.php?t=911729)

I like having fresh /home and config files when I reinstall/upgrade ubuntu but also keeping my files intact on a seperate storage partition.

> I've got the feeling that less people are editing the sources.list with gedit. I want to run Ubuntu64 again (as I've always done) is there a good way to keep check on my sources list? 

I know no better way than that software repos program (i forgot its exact name) in the system menu > admin menu.

---

### Post by Maupertus on 2008-09-06
Okay, so basicly there's not really a good reason for a 'normal' user to set up a seperate /home partition except with very large problems like a kernelpanic. So although I'm going to increase my Swap to 4GB (twice my RAM) I don't think I'll need it. I mostly came to this conclusion because of my general obsessive order in my files, and all my documents, music and what so ever are stored on an extra HD.

Can I just boot the iso and install over my current partition or are strange things happening?

I'm currently sharing a 250Gig NTFS HD with my XP partition, are there settings I should save except my Evolution settings?

---

### Post by Vivaldi Gloria on 2008-09-06
> **Maupertus said:**
> not really a good reason for a 'normal' user
... my files, and all my documents, music and what so ever are stored on an extra HD.

If your files live on an external disk then you can live without a home or storage partition. But if you'll use the internal disk for your files then I suggest you make a home or storage partition.

> Can I just boot the iso and install over my current partition or are strange things happening?

Yeah. Just boot it. Don't plug in the external hd but.

> I'm currently sharing a 250Gig NTFS HD with my XP partition, are there settings I should save except my Evolution settings?

Firefox bookmarks? Not sure what you have so I don't know what you should save. Making a backup of config files wouldn't hurt:

[http://ubuntuforums.org/showthread.php?t=792639&highlight=script](http://ubuntuforums.org/showthread.php?t=792639&highlight=script)

---

### Post by Maupertus on 2008-09-06
What about fstab. When I installed 7.04 I had to edit a lot in fstab to make my second NTFS HD mount properly and automaticly in Ubuntu. Will I have to do the same when I re-install 8.04?

---

### Post by Vivaldi Gloria on 2008-09-06
> **Maupertus said:**
> What about fstab. When I installed 7.04 I had to edit a lot in fstab to make my second NTFS HD mount properly and automaticly in Ubuntu. Will I have to do the same when I re-install 8.04?

I don't remember if you can do the ntfs mount settings in the ubuntu installer. Try it. If it doesn't work then you'll need to [[COLOR="Olive"]fstab[/COLOR]]("http://ubuntuforums.org/showthread.php?&t=283131")

---

