---
title: "New linux name..."
date: 2007-03-06
forum: Other OS Talk
---

### Post by kevanr on 2007-03-06
Anybody ever come up with a name for a linux distro you think is cool? I need ideas for the name of the distro I am making.

---

### Post by maxamillion on 2007-03-06
What is your distro geared for? what is the main purpose of it? what sets it apart from others? ...

these would be things i would consider when thinking of a name so that the name would suite the distro.

---

### Post by kevanr on 2007-03-06
IT security, hopefully have KDE, lots of security tools. As well as programming packages.

---

### Post by kevanr on 2007-03-06
Anybody have ideas?

---

### Post by RAV TUX on 2007-03-06
> **kevanr said:**
> Anybody ever come up with a name for a linux distro you think is cool? I need ideas for the name of the distro I am making.what is your base OS?, or are you building this yourself?

---

### Post by kevanr on 2007-03-06
Well, I am thinking of three different bases, Kubuntu, Knoppix, and Austrumi. Leaning more towards Kubuntu.

---

### Post by Nikron on 2007-03-06
Well, choose the name of a species of Penguin.  That's what I'd do.
Magellanic sounds like a good name to me.

[Magellanic Penguins...]("http://www.siec.k12.in.us/~west/proj/penguins/magell.html")

---

### Post by RAV TUX on 2007-03-06
> **kevanr said:**
> Well, I am thinking of three different bases, Kubuntu, Knoppix, and Austrumi. Leaning more towards Kubuntu.

If you want superior hardware detection then you should use KNOPPIX,...if you want to build your distro easily you could use Morphix(based on KNOPPIX)....I am not sure about building on Kubuntu...


*moving to the other OS forum*

---

### Post by Nils Olav on 2007-03-06
[cough]gobolinux[/cough]

---

### Post by Quillz on 2007-03-06
If I ever made a Linux distro, I'd call it either MyLinux or iLinux.

---

### Post by kevanr on 2007-03-06
I was planning on using "reconstructor" and editing the iso for Kubuntu, but morphix sounds interesting, I am downloading a version.

---

### Post by 3rdalbum on 2007-03-07
> **kevanr said:**
> I was planning on using "reconstructor" and editing the iso for Kubuntu, but morphix sounds interesting, I am downloading a version.

Morphix has a very small number of available packages, and Reconstructor doesn't give a very fine degree of detail.

What I'd recommend is this: [https://help.ubuntu.com/community/LiveCDCustomization/6%2e06]("https://help.ubuntu.com/community/LiveCDCustomization/6%2e06")

This guide shows you how to unpack the SquashFS filesystem onto your hard disk, ready for you to make absolutely any changes you want. Wanna hack around with gdm.conf, replace Xorg with Xvesa, or include custom Gnome configuration for every new user that is created? Making manual changes to the uncompressed filesystem is the only way to do it; plus you learn a lot about a typical Linux system in the process!

---

### Post by kevanr on 2007-03-07
I am having a problem, this is what I am getting when following the instructions:

kevan@kevanr:~$ mkdir ~/live
kevan@kevanr:~$ mv ubuntu-6.06.1-desktop-i386.iso ~/live
kevan@kevanr:~$ cd ~/live
kevan@kevanr:~/live$ mkdir mount
kevan@kevanr:~/live$ sudo mount -o loop ubuntu-6.06.1-desktop-i386.iso mnt
Password:
mount: mount point mnt does not exist
kevan@kevanr:~/live$ mkdir extract-cd
kevan@kevanr:~/live$ rsync --exclude=/casper/filesystem.squashfs -a mnt/ extract-cd
rsync: link_stat "/home/kevan/live/mnt/." failed: No such file or directory (2)
rsync error: some files could not be transferred (code 23) at main.c(892) [sender=2.6.8]
kevan@kevanr:~/live$

---

### Post by kevanr on 2007-03-07
Nevermind that, I got it to work. It shows how to purge packages, how do you add packages?

---

### Post by RAV TUX on 2007-03-07
> **kevanr said:**
> I was planning on using "reconstructor" and editing the iso for Kubuntu, but morphix sounds interesting, I am downloading a version.

**[[B][B]Dreamlinux**[/B]]("http://www.dreamlinux.com.br/english/") is based on morphix[/B]


they have done a pretty awesome job.

---

### Post by kevanr on 2007-03-08
they have this:

[http://www.dreamlinux.com.br/english/tutor-ficha1.html](http://www.dreamlinux.com.br/english/tutor-ficha1.html)

But where do you download those files?

---

### Post by kevanr on 2007-03-08
I found . Mkdistro 2.0,  . mainsidxfree.tar.gz. But I cannot find DreamBase.

---

### Post by kevanr on 2007-03-08
I could use some help here...anybody have an idea?

---

### Post by jclmusic on 2007-03-08
> **kevanr said:**
> IT security, hopefully have KDE, lots of security tools. As well as programming packages.

Securix
Sekurix
Informatix
Technotix
Teknotix
lol

i like the idea of using the name of a breed of penguin.

---

### Post by kevanr on 2007-03-09
Lol-I forgot about this thread. I and my 'co-designer' decided to call it Shanira (Shaw-nere-ah), it is Swahili or Afrikaans for 'warmed by the sun'. Thanks for suggestions!

---

### Post by ahmatti on 2007-03-19
> **3rdalbum said:**
> Reconstructor doesn't give a very fine degree of detail.

What I'd recommend is this: [https://help.ubuntu.com/community/LiveCDCustomization/6%2e06]("https://help.ubuntu.com/community/LiveCDCustomization/6%2e06")

This guide shows you how to unpack the SquashFS filesystem onto your hard disk, ready for you to make absolutely any changes you want.

Actually this exactly what you can do from Reconstructor terminal...

---

### Post by 3rdalbum on 2007-03-20
> **ahmatti said:**
> Actually this exactly what you can do from Reconstructor terminal...

I've not tried Reconstructor lately so I haven't checked out that feature, but the manual method is still useful for adding configuration files directly from your own system.

---

### Post by ahmatti on 2007-03-22
> **3rdalbum said:**
> I've not tried Reconstructor lately so I haven't checked out that feature, but the manual method is still useful for adding configuration files directly from your own system.

You can actually do that with reconstructor too. Of course it is always cool to know how to make things manually :)

---

### Post by darksong on 2007-03-22
I think your user name you make a good linux name -

kevanr Linux 

Got a certain ring to it :D

---

