---
title: "Cant log in ! Please help"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by andrew.thebatman on 2008-09-06
PLEASE HELP ME ! I CANT LOG IN !

:(after rebooting my computer, i now get a the folloing message when i attempt to log in ....

'GDM could not write to your autherization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possable to log in. Please contact your system administrator'

I am useing Ubuntu Efty Edge, my computer is a Dell Dimension 3000 desktop, 80gig hard drive ( maybe it has got full up ) and 512mb memory !

The last session my girlfriend (she broke my computer :lolflag: ) was running Ktorrent and there seemed to be a problem running flash videos, thats why i rebooted !

Thanks in advance:)

Andrew.thebatman

---

### Post by billgoldberg on 2008-09-06
> **andrew.thebatman said:**
> PLEASE HELP ME ! I CANT LOG IN !

:(after rebooting my computer, i now get a the folloing message when i attempt to log in ....

'GDM could not write to your autherization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possable to log in. Please contact your system administrator'

I am useing Ubuntu Efty Edge, my computer is a Dell Dimension 3000 desktop, 80gig hard drive ( maybe it has got full up ) and 512mb memory !

The last session my girlfriend (she broke my computer :lolflag: ) was running Ktorrent and there seemed to be a problem running flash videos, thats why i rebooted !

Thanks in advance:)

Andrew.thebatman

Ubuntu Edge is an unsupported ancient version of Ubuntu.

Back up your files to an external HDD or something using a Ubuntu live cd and install Ubuntu 8.04.1

---

### Post by andrew.thebatman on 2008-09-06
Thanks billgoldberg ! 

I am running the live cd ( edgy eft ) and plan to copy the files from my hard drive onto a usb stick !

However i cannot see any of the files that are on the hard drive when i am running the live cd !

I have searched the forums and i think that my hard drive is not mounted !

using GNOME Partition Editor i can see that the main partition of my hard drive is called /dev/hda1 ! I cannot see anything that relates to this while  using the Device Manager !
I can also navigate to a folder called /dev/hda1 but i cannot open it and it dosnt contain anything anyway, so im guessing its to do with the live cd

Can anybody offer any more help ? 

Thanks in advance 

andrew.thebatman

---

### Post by Quiver on 2008-09-12
> 
after rebooting my computer, i now get a the folloing message when i attempt to log in ....

'GDM could not write to your autherization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possable to log in. Please contact your system administrator'


The exact same thing just happened to me.
 I'm running Ubuntu Fiesty Fawn on a PIII w/ 1GB of ram and a 40GB HD.  (And -- let me just say -- I love it! And, I love these forums which I've never posted to, but have helped me out many times)

The last time I was able to log I was using PhotoRec (which is awesome), and it had stopped working because it had filled up the main partition of my hard drive.  I was then able to log in as another user, but after I rebooted I got the same message.

 So, luckily, I had just burned an Xubuntu 8.04.1 alternate install CD. :) I tried an option called ummm...  Rescue Something?... I forget what it was called, but it gave me a command line without actually installing itself on my hard drive.

  I thought that if I could delete some files to free up some space then I'd be able to log in.  I could access other partitions but not the one where Ubuntu is installed.  I'm not very strong with the command line, so I might have missed something.

  I was able to empty one partition.  I installed Xubuntu onto there and I'm running that now.  I still can't access that full partition and I had important stuff on there.

  Any help would be greatly appreciated.

---

### Post by shadow-of-sin on 2008-09-12
> **andrew.thebatman said:**
> Thanks billgoldberg ! 

I am running the live cd ( edgy eft ) and plan to copy the files from my hard drive onto a usb stick !

However i cannot see any of the files that are on the hard drive when i am running the live cd !

I have searched the forums and i think that my hard drive is not mounted !

using GNOME Partition Editor i can see that the main partition of my hard drive is called /dev/hda1 ! I cannot see anything that relates to this while  using the Device Manager !
I can also navigate to a folder called /dev/hda1 but i cannot open it and it dosnt contain anything anyway, so im guessing its to do with the live cd

Can anybody offer any more help ? 

Thanks in advance 

andrew.thebatman
Try this (to mount your drive):
-Open the terminal (Applications-->Accesories-->Terminal)
-Type these commands:
```
sudo mkdir /media/olddisk
sudo mount /dev/hda1 /media/olddisk

```

Then you should be able to see your drive in nautilus

---

### Post by KIAaze on 2008-09-12
I had this problem a few times already.
The easiest is to boot into recovery mode/single user mode.

From there you can delete unecessary files.
All I usually have to do is run
```
sudo apt-get clean
```
since most of the time it's installing programs that caused my root partition to fill up.

Of course, I have no idea if Edgy Eft has a single user boot mode available.
If not, Grub should allow you to edit the boot command when you hit "e" at the boot menu.

If your boot command looks like this for example:
```
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a76c113d-5ed5-4d00-9885-d5eeebdfed19 ro
```
Just add "single" at the end:
```
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=a76c113d-5ed5-4d00-9885-d5eeebdfed19 ro **single**

```

---

### Post by Quiver on 2008-09-12
Thanks, I got it.:)

 I first tried KIAaze's approach.  It would have worked but I'm asked for the root password.  I guess I haven't used it in a while and I've forgotten it.  I hope I have it written down somewhere.:-k
 I was able to mount the partition that I needed using shadow-of-sin's approach.  I had trouble with this at first, because the name of the partition had changed.  It was hda1, but while in Xubuntu it became sda4.  I finally noticed it in GRUB, while rebooting.  Then I was able to mount it and remove some stuff.

Thanks to you both.  
For me this problem is solved!=D>

---

### Post by KIAaze on 2008-09-13
:/
I'm stupid. I completely forgot. There's a much easier way:
**ctrl+alt+F1 -> virtual terminal**
No need for a root password there as you can log in with your normal login.

Actually, that's what I usually use. I have no idea why I suggested the single user mode instead. Either it has something to do with me getting a black screen now when I switch to virtual terminals (Intrepid bug) or I must have been a bit sleepy or confused...
Or I just didn't have that problem for too long now.

Anyway, you solved your problem. :)

---

### Post by Quiver on 2008-09-14
Okay.  That would've been easy -- I'll try it next time.
But, look, this problem seems like a problem to me.  It seems to me that Ubuntu should either:
 1) prevent itself from filling the partition up completely
 2) warm me that a full partition will make it difficult for me to log in
 3) include in the > 'GDM could not write to your autherization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possable to log in. Please contact your system administrator' notice that Ctrl-Alt-F1 is an option
 4)or include the virtual terminal option as one of the options on the login page.
  This is the first big problem that I've had in more than a year, but it seems like one that should be fixed.

---

### Post by Yannick Le Saint kyncani on 2008-09-14
> **Quiver said:**
> Okay.  That would've been easy -- I'll try it next time.
But, look, this problem seems like a problem to me.  It seems to me that Ubuntu should either:
 1) prevent itself from filling the partition up completely
 2) warm me that a full partition will make it difficult for me to log in

It does so in hardy heron :)

---

### Post by andrew.thebatman on 2008-09-16
Thanks shadow-of-sin 

Your command line worked and i can now see my hard drive in nautilus

Im going to back up the data i need this weekend und then upgrade to hardy heron !

Also thanks to everyone who took the time to look at this and try to help out !

---

