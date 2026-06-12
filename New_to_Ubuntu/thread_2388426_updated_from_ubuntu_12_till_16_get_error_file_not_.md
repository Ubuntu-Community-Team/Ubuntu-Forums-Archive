---
title: "updated from ubuntu 12 till 16 get error file not found"
date: 2018-04-02
forum: New to Ubuntu
---

### Post by dave1956 on 2018-04-02
Hi all
I have had to nick the wifes chrome book to ask for help here and set a new account, old account may have had as many as 10 posts, (not sure)
Any way... decided to upgrade from ver 12 LTS of Ubuntu to ver 16 LTS, all went well told the thing to save tho old files of which I had backed up most of, but forgot to backup the important ones, (firefox book-marks) oh-dear... On the final part of the new install just at the end ubuntu 16 could not complete err saving old or new files or the old files into the new files, but it did ask for a reboot.. done that

 all I get now is 
error: file not found
grub rescue

Now I have looked this up and done ls "enter" and I got the following 
(hd0) (hd0,msdos6)  (hd0,msdos5)  (hd0,msdos1)  (hd1)  (hd1,msdos1)    nothing new there, so I done the usual ls (hd0,msdos6)  for all of them and got the same back  error: unknown filesystem

SOoo,  I rebooted the live disc took a look all my files, which are on number 3 hard drive.. 3rd one down or the bottom one.
Next I went to install, but rather then install and wipe all files on the install menu page I clicked on the bottom line which reads some like:  do something else, this is the shorten version of what I can see

/dev/sda
  /dev/sda1 ntfs  160039MB
/dev/sdb
  /dev/sdb1 ntfs  winXP 18405MB
  /dev/sdb6  ext4  115220MB Ubuntu 16
  /dev/sdb5 swap

So Ubuntu is hiding in a sdb6  ext6 partition 

How do I make grub boot into there ?

Should add it is a multi-boot computer and I still need XP now and again (sorry to say)

Can some one help please

Dave

---

### Post by yancek on 2018-04-02
According to the partition/drive info you posted, the only partition with a Linux filesystem is sdb6, which in Grub2 would be (hd1,msdos6) which does not show in your ls output.  If Grub is properly installed on sdb6, the following chainload commands at a grub prompt should boot it.  If this fails, post back whatever error messages you see.

```
set root=(hd1,msdos6)  (hit the Enter key)
chainloader +1  (hit the Enter key)
boot  (hit  the Enter key)
```

---

### Post by dave1956 on 2018-04-03
Hi yancek
I turned on the computer and this is now what the screen has on it after using the above code

error: file not found.
grub rescue> set root=(hd1,msdos6)
grub rescue> chainloader +1
Unknown command 'chainloader'
grub rescue> boot
Unknown command 'boot'
grub rescue>


And that is what I see on the screen, I shall switch it off and wait for a reply

Dave
PS. I live in Northern Ireland hence the time delay

OK
Back on again, only this time I am running the computer using the live disc.  I have discovered that firefox auto bookmarks or something like that. or keeps the last 15, "think that is what I read"
On my Hard drive which I can access, does any-one know where I could find my firefox book marks so as I can do a backup and then do a clean install of ubuntu 16

Thanks
Dave

---

### Post by yancek on 2018-04-03
Before you get to grub rescue, do you see a Grub menu.  If you do, hit the c key on your keyboard and try the commands.  If you just get grub rescue>, try the commands at the link below, about half way down the page.

[https://unix.stackexchange.com/questions/148041/recovering-from-grub-rescue-crash](https://unix.stackexchange.com/questions/148041/recovering-from-grub-rescue-crash)

---

### Post by coffeecat on 2018-04-03
@dave1956, the link suffices. I've removed all the copy-pasted text in your post. The linuxandubuntu.com's website's policy on copying is clearly stated at the bottom of the page:

> Any material in this site can not be reproduced without permission.

---

### Post by dave1956 on 2018-04-03
coffeecat sorry about that. did not do it on purpose

Dave

Ok yancek
I now know what this computer done.  As I have 2 hard drives fitted one being an IDE drive the other is a SATA drive.
The SATA drive has ubuntu / winXP installed on them and the IDE drive is a slave for photographs etc.
So when I done this upgrade to ubuntu 16 it put the grub on the IDE drive which is not set as master boot... I how have it set to boot and it works, don't like ubuntu 16, but 2 late now.
The other thing I done was mis-spell the user name, I thought it was Da-Boss, err no it should be DaBoss.  Ubuntu has now created a second user and the files (doc's, photographs, downloads, music) are all under the first user: DaBoss, 
Still can not find he firefox book marks, about 100... you know all important one's like travago to find a holiday, different airlines, ferry's and the like. and the less important one, like e-bay and online banking 

If I could only back them up I would do a fresh install on this thing
Dave

---

### Post by dave1956 on 2018-04-05
Yancek
As I now have this thing up and running, I ran a small experiment yesterday while it were raining.

I unplugged the IDE drive and tried to boot up the live DVD, after 2 hours of it "the computer"  doing nothing, bar the bit where it starts to boot, goes to the first Ubuntu splash screen and on the second dot in, it stalls but the hard drive light is on and I can hear the drive running.
I have concluded that some how Ubuntu knows that the IDE drive is missing and therefore so is the MBR 
With that now in mind, if my IDE drive was to fail, how would I, or indeed any one else that runs a dual hard drive system reinstall Ubuntu
I had thought of doing the following to get grub back onto the SATA drive as I had thought of formatting the IDE drive which is only my back up drive r save to drive for photographs etc

Sudo add-apt-repository -y ppa:yannubuntu/boot-repair (hit the enter key)
Sudo apt-get update (hit the enter key)
Sudo apt-get install -y boot-repair && boot-repair (hit the enter key)

It was just a thought
Thanks for your help

Dave

---

### Post by yancek on 2018-04-05
On  a system using MBR such as yours, Grub will install boot code to the MBR of the drive it sees as sda which apparently was your backup drive.  You can select the drive to install this code when doing an install by using the manual install method, referred to as Something Else in Ubuntu.  In your case it appears that should be /dev/sdb.  If you can now boot Ubuntu and running:  sudo fdisk -l shows your xp/Ubuntu partition as /dev/sdb, install Grub to that drive's MBR with the command:

> sudo grub-install /dev/sdb

---

### Post by dave1956 on 2018-04-06
yancek
I have wrote that down in my note book (paper) and will keep it for ref.. just need to make this post as solved 

Thankyou
Dave

---

### Post by oldos2er on 2018-04-06
> **dave1956 said:**
>  need to make this post as solved

Dave

You can mark it 'Solved' under the Thread Tools menu at the top of the page.

---

