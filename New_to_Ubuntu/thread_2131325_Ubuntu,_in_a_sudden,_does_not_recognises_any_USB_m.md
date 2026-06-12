---
title: "Ubuntu, in a sudden, does not recognises any USB memory stick, CD or external HD."
date: 2013-04-01
forum: New to Ubuntu
---

### Post by viriatovigo on 2013-04-01
I am using Ubuntu 12.04

Since last Friday, when I do plug a USB memory stick it shows up in Disk Utility but it doesn't shows in the Launcher. This is a new thing because every Friday I did back up all my documents in the USB memory stick without any problem but since last Friday I can not do it because I can't open it at all.

 

 I did try to back up in a DVD but, again, it shows up in the Disk Utility but it doesn't in the Launcher.
 

 And now, every month I do back up my PC using the "Buckup" applications enclosed in Ubuntu. Not this month... Also do not recognises the external HD as before...

I would appreciate if someone can help me to resolve this issue because I an going to follow the advice from cmcanulty and install Lubuntu instead of Ubuntu because is more than obvious that I am not geek enough to use Ubuntu; but I am going to lose all the information on My Documents because I can not back up them any more and there is a lot of business information. Please, help. Thank you.

---

### Post by AndyOpie150 on 2013-04-01
Did you recieve any updates prior to this happening? If not, How much space is on your hard drive?  What I'm thinking is....... you could install another distro if you have the space then go through it to backup you info.

---

### Post by viriatovigo on 2013-04-01
Ta AndyOpie150.

I do receive Ubuntu updates automatically nearly every single day.

My HD is 80Gb but I have not a clue how much is available. In Windows right clicking in the HD and then left clicking in "Properties" was straight away to know it but in Linux everything becomes a epic trial to find anything. In the Disk Utility just says "Available: - ". Great... 

I believe that should be  available near half of the HD but I don't know, I don't know how much space takes thinks in Ubuntu and I have not a clue about how to find out. With Windows I had a huge amount of programs and was only used about a quarter of the HD.

I have no idea what "Distro" means. I am new on Ubuntu.

Kind regards.

Tino

---

### Post by Bashing-om on 2013-04-01
viriatovigo;
Not sure what I can do to help, but will do as much as I can. As I understand it, you can not mount or access your usb drive ?

With that in mind, let's look and see if ubuntu "sees" that drive; With the drive inserted:
what is the result of terminal commands:
```
lsusb
ls -la /media

```
Remember to "safely remove" the device prior to physical removal.[INDENT=3]
try'n to help

[/INDENT]

---

### Post by viriatovigo on 2013-04-01
Hey, Bashing-om!

Yes!! Now the sticks and CD do show in both, the Disk Utility and the Launcher, but a new thing occurs. Until now I could, as I said earlier, back up al My Documents, but now I just did try and says that can not be done because the document are read-only. Whaaat? How were not read-only one week ago and in a sudden they are??? And, What has to do read-only with copy and paste? If they become read-only by a mysterious happening it should mean that can not be modified, but... Copy and paste????

By the way, still can not read the external HD.

I and really nervous because now I can not do anything; not change from Ubuntu to Lubuntu o Xubuntu and not copy any thing to put it in AppleMac Mountain Lion (N-o  w-a-y  I am going back to Windows ever) without losing every thing and there is a lot of information (near 6.000 emails saved, near 3.000 sheets of business information...). 

I think that my mistake was to move to Linux straight away. I should keep working on Mac and when confident move to Linux. Too late...

---

### Post by Bashing-om on 2013-04-01
viriatovigo;
Never too late to make the move to open source and this great operating system. All it takes is a bit of time and effort to learn the tools.

In your case, the disk in all likely hood became "read only" because ubuntu detected file system errors and locked it to prevent any further corruption,
Let's look at the disk and see how it is formatted and then see what we might be able to do from ubuntu's perspective on that disk.

Boot up from a liveCD, so no disks are mounted;
 Plug in the disk and let's see/
terminal codes:
```
sudo fdisk -lu
sudo parted -l  
sudo parted /dev/sda unit s print
```

When we know more we may be able to run a file system check/repair, also we will want to know that the disk is not filled to capacity(when we know the disk identifier).[INDENT=2]
but, one thing at a time and we will get there
[/INDENT]

---

### Post by viriatovigo on 2013-04-01
Hi Bashing-om

I don't know if I did explain me right... For the "sudo parted /dev/sda unit s print" I infer that you are talking about the main HD, but what I am talking about is that now the PC, with the main HD, in a sudden can not read the external 1Tb HD in which I used to back up my PC in one of the partitions. In other partition is a copy of Ubuntu 12.04 as a copy to install in case of emergency, in other partition is AppleMac Mountian Lion as a copy to install in case of emergency (AppleMac is not in this PC but in my laptop), and a 4th partition is free and the rest of the HD is empty.

When I do plug the external HD it says in first place that "Can not be found media..." , and then, referring to each partition, one by one (Apple, Linux, etc.), "Unable to mount. Error mounting. Failed (a lot of things failed...)".

Of course, when I did install Ubuntu 12.04 for first time, I did the CD as required by the Ubuntu installation web site and I am keeping it correctly labelled. It works because I had to install Ubuntu 12.04 after the try to upgrade to 12.10 that did a real mess in my PC.

So now I am not sure if your scripts to write in the terminal are related to de main HD or the external HD. I understand that sda means the main HD, not the external one that I can't remember now how it was called, some sd?, but certainly not sda.

" All it takes is a bit of time and effort to learn the tools." Yes... All the others that did try to help me in other threads told me so when I said that Linux is too much for me and that I am not a geek, but patience is not one of my virtues, I always want the things done yesterday (typical Mediterranean... and old  man...). I think that I need to cool down a bit...

---

### Post by AndyOpie150 on 2013-04-01
I think Bashing-om's advice is way better.
I'm pretty sure he was trying to ask you to plug in the external hard drive then run the commands.

---

### Post by Bashing-om on 2013-04-01
viriatovigo;

Not to know is not a sin, none were born knowing, oopps I just made an error as you are correct in that sda refers to the 1st hard disk. 
Still, we need to know what the file systems on your backup disk and that of the individual partitions.Until we KNOW what the format is as well as what the disk's identity is, there is nothing that can be done.
The terminal commands "fdisk and parted" will give us the needed info ( if the hard drive can even be recognized); on all partitions that the system recognizes.
Please post the output of terminal commands:
```
sudo fdisk -lu
sudo parted -l
``` from a liveCD so that no partitions are mounted and no additional damage can be done.
We will do that last "parted" command when we know the device id.[INDENT]
inquiring minds, want to know

[/INDENT]

---

### Post by viriatovigo on 2013-04-01
Ta AndyOpie150.

As far as to me  concern, you are trying to help me to your best and that is all a point. Thank you so much.

Bashing-om just did answer after your post so, following your advise, I'll keep by his/her advice.

Ta Bashig-om.

The problem, as I said, is that for some reason now  my PC can not find the external HD but the funny thing is that, after saying so, start saying that de partitions can  not be mounted... How can identify the partitions if the HD can not be found???? One of the many mysteries of the hyperspace to me...

Any way... What I am going to do is to plug it in the laptop and Mountain Lion has not problem to open it, so I will write down the details and I will back to you with them. But tomorrow... That now is 01:10am  in the UK and I feel tired after being all bl**dy day fighting with this evil machine.

Talk to you soon and many thanks for your patience to help me.

Kind regards.

Tino

---

### Post by Bashing-om on 2013-04-01
Tino;
I understand; it will all wait until the morrow, I too am tired and id getting difficult to think properly. I am going lightly from here to my sleep period.
[INDENT=3]
my regards to you also, good night

[/INDENT]

---

### Post by viriatovigo on 2013-04-03
Hi AndyOpie150 and Bashing-om,

Yes!!! Bingo!!! Problem resolved.

Since our last communication, I've been day and night googling "How to remove the USB stick 'read-only' issue". Loads of people with the same problem and loads of different solutions per thread. I did try **all of them**, one by one... Until 2 hours ago one of the advises did work for me and all My Documents are backed up as usual.

The solution was: Plug the USB stick and then open it, then in the menu bar: File>Properties (Hey! there it was like in Windows the pie chart telling me the capacity and how much was in use) >Permissions and there it was a lot off "File access" where I did chose "Read and write" and, Bingo! Did work.

I am hungry, thirsty and tired. I am going to make a large French baguette sandwich, drink a half box of Guinness and I am going to sleep.

Thank you both for your patience and  your will to help me. Very much appreciated. 

All the best.

Tino.

---

### Post by Bashing-om on 2013-04-03
Tino; 
Glad you are glad and have a resolution ! I appreciate your consideration and update of your staus.
please mark this thread as solved.
interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.[INDENT=5]
it's all a learning experiece

[/INDENT]

---

