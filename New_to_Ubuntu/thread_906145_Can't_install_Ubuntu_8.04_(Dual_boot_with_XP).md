---
title: "Can't install Ubuntu 8.04 (Dual boot with XP)"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Nuuk on 2008-08-31
Last year I installed Ubuntu 7.10 on an old PIII computer. It was comparatively straight forward and I liked using Ubuntu.

I now want to add Ubuntu to another PC that already runs Windows XP Pro and have downloaded and burned the 8.04 Desktop application. Actually I have both the Live and Alternate versions - BOTH MD5SUMed and burned to CD at x1.

The PC I am trying to install to is a SocketA board with an Athlon XP1600 CPU and 512 meg of RAM. The IDE hard drive is 80 gig with XP on the drive C. The size of drive D is 12 gig and it is empty and waiting for Ubuntu.

However when I run the installation CD (Live version) after selecting install (or Check CD) I get a black screen with a flashing cursor in the top left corner. With the Alternate version, the screen goes blank and then I get the following message:

[35.349459] crc error

[35.360524] Kernel panic - not synching. VFS' unable to mount root on wn-block(104,1)

I have Googled the error message and all replies seem to refer to either writing your own code, or existing Ubuntu systems stopping working. I've also spent a few days reading but can't find an answer.

So could somebody tell me why I can't get 8.04 on to this PC please? :confused:

---

### Post by Sef on 2008-08-31
What's your graphics card?  Your problem sounds like a conflict with it.  You can try replacing it with another card that you have or boot into safe mode.  That's F4 or another F* button.

---

### Post by Badoxide on 2008-08-31
Hello.Nuuk

I am not all to sure if this may help you, but it seems to have helped this guy, anyways I had a look around this is what I found. Best of luck.

[http://64.233.179.104/translate_c?hl=en&sl=ru&u=http://ubuntuforums.org/archive/index.php/t-550737.html&prev=/search%3Fq%3DVFS%2527%2Bunable%2Bto%2Bmount%2Broot%2Bon%2Bwn-block(104,1)%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26hs%3Djzh&usg=ALkJrhh7Qb-jmVvbSfkQYCW87fF2fFMapw](http://64.233.179.104/translate_c?hl=en&sl=ru&u=http://ubuntuforums.org/archive/index.php/t-550737.html&prev=/search%3Fq%3DVFS%2527%2Bunable%2Bto%2Bmount%2Broot%2Bon%2Bwn-block(104,1)%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26hs%3Djzh&usg=ALkJrhh7Qb-jmVvbSfkQYCW87fF2fFMapw)


B-O

---

### Post by Nuuk on 2008-08-31
Radeon 7000 graphics card. I'll try installing in SAFE mode and see what happens.

Thanks for the replies.

---

### Post by Nuuk on 2008-09-03
Well SAFE mode didn't work either, and nothing else I have found has worked for me either. So I guess I will try 7.10 and see if that works. :confused:

---

### Post by Nuuk on 2008-09-03
OK 7.10 goes on OK although it runs painfully slow.

I have started the install process but when I get to the partitions bit, I select manual, then select what is drive D in Windows but then I get the message

NO ROOT FILE SYSTEM IS DEFINED

PLEASE CORRECT THIS FROM THE PARTITIONING MENU

But there is nothing to tell me what to do then. Help!

Edit - here is the screen that I get to show me the available drives. I now not sure which one corresponds to drive D in Windows. Why does it go from 1 to 5? And surely there should be one drive that is totally unused. :confused:

[IMG]http://nickw.worldonline.co.uk/etc/ui1.jpg[/IMG]

---

### Post by Nuuk on 2008-09-05
Done it! This is what I did for anybody else looking to install Ubuntu on a hard drive that already has Windows and another (spare) formatted drive.

Run the Live CD and click on INSTALL.
Go through the first few pages of questions.
When you come to the Partitions page, identify your spare drive and delete it.
You will then see FREE SPACE in the list on the left.
Right click on FREE SPACE and then select NEW PARTITION
I subtracted around 512 meg from the total free space and used that figure to format the / partition. Leave the other details as EXT3 and name it /
The hard drive is then rescanned.
Right click on FREE SPACE again to make the SWAP partition.
Accept the remaining space for the size, select SWAP as the type of folder and click APPLY.
You should now be able to proceed with the Ubuntu installation.

I was amazed that Ubuntu picked up sp much stuff from the existing XP installation. Even the Desktop picture! :)

---

### Post by Crafty Kisses on 2008-09-05
Yeah it sounds like a hardware issue, what are your system specs?

---

### Post by pawanspace on 2008-09-18
Hi, 

I have a single drive where I have installed Windows, If I will follow your process it will not harm Windows right?

Pawan

---

### Post by Sealbhach on 2008-09-18
Careful.

If I were you, I would create the patitions in Windows first. 

The when you open up the Live CD, you know that one partition contains your windows installation and should be untouched.

.

---

