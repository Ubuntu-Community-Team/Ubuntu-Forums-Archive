---
title: "Downsize/copy to smaller hard drive ?"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by Greg Mueller on 2014-04-09
Using Ubuntu 12.04 with a KDE desktop

I am using a 250gb HD, but I'm only using les than 50gb of it. I'd like to move everything to an 80gb HD
I tried using the dd comand (sudo dd if=/dev/sda/ of=/dev/sdb)

didn't work

Tried changing the partion on the drive so it was only 65gb and then tried (sudo dd if=/dev/sda1/ of=/dev/sdb)

didn't work

Can someone suggest a way that I can clone my operating sytem and files to the 80gb hard drive from the 250gb drive?

---

### Post by grier-devon on 2014-04-09
I would recommend using Clonezilla, though dd should work and maybe something wrong with your syntax
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Greg Mueller on 2014-04-09
Could be syntax
I watched a youtube video which said you use what I did.....

---

### Post by grier-devon on 2014-04-09
I have not used dd but there is GUI for dd if you are set on using that called gdiskdump
[https://launchpad.net/gdiskdump](https://launchpad.net/gdiskdump)

EDIT: So I just got done playing with gdiskdump and honestly I don't think there is a easier tool to use. I did not clone anything but I went through the motions as if I was going to and could not believe how easy the tool was. Give it a shot and let me know what you think. If it does not install let me know as I had to install it differently but I am also running Ubuntu 14.04 and the app center gives me a hard time installing anything from outside the repositories so I just installed it from the web in the command line.

---

