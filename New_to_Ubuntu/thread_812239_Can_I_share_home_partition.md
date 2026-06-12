---
title: "Can I share /home partition?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Miljet on 2008-05-29
I have set up this old HP computer to experiment with various distros. I currently have ubuntu Hardy Heron 8.04 installed with a separate /home partition. I am about to install xubuntu 8.04 and was wondering if I can share the same /home partition, or do I need to make a separate one?

What about other distros like DSL or Puppy?

---

### Post by doorknob60 on 2008-05-29
You can, but you might have some problems like launchers that don't work and that kind of stuff. Also, to instal Xubuntu, you don't need to download and install it seperately, just use this in a terminal:
```
sudo apt-get install xubuntu-desktop
```
Then you can choose whether to start Gnome or Xfce from the login screen under Sessions.

---

### Post by kwacka on 2008-05-29
There should be no problem at all with Xubuntu, all the Ubuntus share the same user I.D.s (e.g the first user is 1000). DSL was once based on Debian, so it will probably use the same UID format.

You _might_ have problems with something like SuSE - IIRC their USD starts at 500.

---

### Post by Miljet on 2008-05-29
Yes, I know that you can install different desktops in an installation, but that's not what I want. I am experimenting with distros that I can recommend to kids and grandkids with older systems and limited resources. Therefore, I want a completely separate install so I can see how much it affects resource usage.

I think that I just answered my own question. If I want completely independent installs, I probably shouldn't try to share partitions.

Thanks for the replies.

---

### Post by kansasnoob on 2008-05-29
Gosh, I've never tried sharing a home partition with another distro. I do have a triple boot set up with XP and and 2 Hardy's. But one of the Hardy partitions is just there for fiddling with. If it hasn't broken in more than 3 days I'm being lazy.

But I do share an ntfs data partition between Win and Hardy. I'll have to see what happens if I try to read from or write to that partition from my other Ubuntu OS.

---

### Post by kwacka on 2008-05-30
so, for example:
/dev/hda1 /  (Ubuntu)
/dev/hda2 /swap
/dev/hda5 logical
      /dev/hda6 /home
      /dev/hda7 /   (mandriva)
      /dev/hda8 /   (fedora)

is not a problem as long as all distros /etc/fstab files show:
/dev/hda6 is /Home
/Home/user A is the same user name in all distros
/Home/user A has the same UID in all distros.

there's quite a bit of stuff out there, just use google

---

