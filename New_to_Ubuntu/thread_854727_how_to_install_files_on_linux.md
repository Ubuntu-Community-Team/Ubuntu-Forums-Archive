---
title: "how to install files on linux"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by alien8predator on 2008-07-09
Hey All,
I just installed Ubuntu on my vmware sever, because I want to start to get to know and learn how to use linux. I've succesfully created partitioned installed and updated. I've seen that I linux has a way you can search programs and install them as packages. Now my problem is I downloaded an iso file which is not standard and I have no idea how to install it. I found this topic (by using the search function) as an example to see if it would work, but I don't quite get it yet:

[http://ubuntuforums.org/showthread.php?p=5185023#post5185023](http://ubuntuforums.org/showthread.php?p=5185023#post5185023)


I'll be searching for the answers until I get some replies.

---

### Post by Xerp on 2008-07-09
"How to install anything in Ubuntu":

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

As for the ISO file ([http://en.wikipedia.org/wiki/ISO_image](http://en.wikipedia.org/wiki/ISO_image)), this is not something you install. You can either burn it to optical media, or mount it:

Example:
```
sudo mount -o loop ISO_Image.iso /media/myiso
```

---

### Post by halitech on 2008-07-09
what exactly did you download and what program is it you are trying to install?

---

### Post by alien8predator on 2008-07-09
ghost4linux and clonezilla

---

### Post by Sydius on 2008-07-09
ISO files are like CDs or DVDs, but in file form.  If you're in Linux, you can mount them to make them act like a DVD or CD.  If you're in Windows, you can use something like Deamon Tools to create virtual CD/DVD drives, in which you can mount them.  In either, you can burn them to an actual CD or DVD using a burner, if you have one.

---

### Post by alien8predator on 2008-07-09
I figured that part out. I have gmount installed. But how to continue on from there I'm still trying to figure out.

---

### Post by edm1 on 2008-07-09
The reason they are not in the ubuntu repositories is because the programs are supposed to be run as a live cd. You are supposed to burn the iso to a cd and boot the computer using it.

What is it you are trying to do with the programs? There may be a more suitable application for your needs.

---

### Post by alien8predator on 2008-07-09
I'm wanting to make images of a working OS, so if my OS for example crashes I can put an image back.

---

### Post by halitech on 2008-07-09
try remastersys

Remastersys is a tool that can be used to do 2 things with an existing Klikit or Ubuntu or derivative installation.

   1. It can make a full system backup including personal data to a live cd or dvd that you can use anywhere and install.
   2. It can make a distributable copy you can share with friends.  This will not have any of your personal user data in it.

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

---

### Post by edm1 on 2008-07-09
PartImage is what you're after. [Here's a guide]("http://www.psychocats.net/ubuntu/partimage").

p.s. if you are using a VM could you not just copy the virtual image??

---

### Post by alien8predator on 2008-07-09
Yeah I could, but I'm wanting to know how to to it so I can apply it in a network envirnoment. I found a tar.gz file, but I'm getting an error message when extracting it to the desktop now.

---

