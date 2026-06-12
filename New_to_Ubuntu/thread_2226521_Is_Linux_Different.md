---
title: "Is Linux Different?"
date: 2014-05-27
forum: New to Ubuntu
---

### Post by gtravis3 on 2014-05-27
I'm working through a Linux book, and often various commands, files and directories that are used in the book return 'does not exist' or cant be found, located, info(ed), nor produce the results shown in the book. 
I'm currently using Lubuntu, and have got to wondering if Linux in it is different, i.e. less complete than Linux in Ubuntu DE or even perhaps GNU/Linux distrubitions?
Thank you for your help,
trav

---

### Post by egeezer on 2014-05-27
Lubuntu is rather lean on all kinds of resources, and I guess that extends to the commands that are included in the default installation.  I've encountered the same thing myself, and (just for reference) I looked in my copy of TLCL (The Linux Command Line) and I can find the opposite there: commands I have available and use frequently that are not included in that book.  "Linux" is a term that embraces all the variety of things people can do with it.  Ubuntu is made from Debian, but a ton of commands are different even in those two, and if you go beyond those into Slackware SUSE or Fedora you'll find even more.    The flip side of being able to do anything you want with a system is a steep learning curve!

---

### Post by matt_symes on 2014-05-27
Hi

Post some of the commands that are not found.

Kind regards

---

### Post by QIII on 2014-05-27
And the title of the book.  By and large all Linux distros use the same directory conventions and store files in pretty much the same places, but there are exceptions.  If you are looking at a book geared towards .rpm (Red Hat) based distros, there are a few minor differences.

---

### Post by tgalati4 on 2014-05-27
Everything in linux is a suggestion.  If it works, great.  If it doesn't, then you have work to do.

Some helpful commands:

```
apropos terminal
which firefox
locate bash
```

---

### Post by Impavidus on 2014-05-27
There are many different variants of Linux. Ubuntu and Lubuntu are just two closely related versions of it, two flavours of one of many distributions. In fact, "Linux" only refers to the kernel, the core of the operating system, with which most people rarely interact directly. Of course, most Linuces have many things in common. There are only a few shells around and the standard utilities (grep, sort, sed, cat, ...) can be found on every Linux.

Your book could also be a bit outdated sometimes. Things in Linux can change fast compared to the time it takes to write, publish and print a book.

---

### Post by Bashing-om on 2014-05-27
gtravis3; Hey

+1 to all the aboves !

Show us some examples and let's all have a discussion. As Impavidus notes, this is a constantly evolving system; what was yesterday may no longer apply.

[INDENT][INDENT]keep on, you will get the hang of it
[/INDENT][/INDENT]

---

### Post by vasa1 on 2014-05-27
+1 to posting specific commands and the title of the book. Please edit your initial post to include the information.

---

### Post by vasa1 on 2014-05-27
And purely to see how much diversity there is in the warm friendly world of Linux ;) ;) you can look at this somewhat old image: h t t p : //futurist.se/gldt/wp-content/uploads/12.10/gldt1210.png (*remove the spaces to make the link functional*). It's extremely large so don't go there if you have limited resources.

---

### Post by Rob Sayer on 2014-05-28
A "Linux book" could be a number of things.  Linux itself isn't really just one thing for the vast majority of users.  How old is the book?  Is it based on Red Hat or some other non Debian based distro?  Different distros use slightly different tools and locations with their added libraries.

I saw a thread here recently started by a noob XP refugee who had installed yum to install apps from the terminal.  This didn't work because it's not the ubuntu package tool.  Apt is.  I don't even know how the hell he installed it in the first place.

One important thing is that technically linux is *just the kernel*.  And it's highly modular.  This partly why linux can be found in a digital watch or a computer desktop that has hardware requirements similar to windows 7 or 8.  You don't have to compile kernel modules for hardware you don't have, though for newbies distros that support this aren't a good idea.
 
It's true you may be lacking some tools by default in lubuntu, which I've had installed on my netbook until recently (Xubuntu now).  I had to install linux-build-essential to backport my wireless in lubuntu 13.10, and I don't think gksu was installed by default either.  I'd kind of expect them to be installed (especially gksu) even in a lightweight DE.

---

### Post by matt_symes on 2014-05-29
Hi

Technologies change over time as well.

devfs->udev

hal->udev

usplash->Xsplash->plymouth

lilo->grub->grub2

They all have different commands and that is just the tip of the iceburg for just one distribution over a relatively short period of time.

If you want to learn the innards the be prepared for one wild rollercoaster :)

Kind regards

---

### Post by jakke1975 on 2014-05-29
Lubuntu really isn't the best OS to start learning about Linux. I can understand the choice if you're installing it in a virtual machine on top of a Windows installation or on a very old computer you still had lying around somewhere... but if you see the possibility, install Ubuntu instead.
Lubuntu is a stripped-down version of Ubuntu so it can run on very few resources and still look and feel very responsive. Of course, if you choose to have something "lite", you'll have to pay for it in other ways, e.g. manually installing software that has been left out of the basic installation to keep it small and tidy.

Ubuntu however, has a decent starters pack of tools to start and learn about Linux. It also has a great community that can help you with all of your problems.
As been mentioned before (i.e. title of the book, commands, etc), you should ideally include as much information in your requests, bar any personal information that is of no use to anyone, and you'll find that most of your questions will be answered in no time at all ;)

By the way, welcome to the club, and I hope you'll enjoy working with Linux (in the near future?) as much as I do!

---

### Post by Rob Sayer on 2014-05-29
Lubuntu may not be the best learner version per se, but if you're talking about an old XP machine with a half gig of RAM it's as good as it gets.

---

