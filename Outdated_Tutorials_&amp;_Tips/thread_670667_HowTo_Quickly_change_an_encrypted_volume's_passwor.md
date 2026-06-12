---
title: "HowTo: Quickly change an encrypted volume's password"
date: 2008-01-17
forum: Outdated Tutorials &amp; Tips
---

### Post by PetePete on 2008-01-17
ok so this is my first Howto, me kind to me :)
[B]
How to change the password on an encrypted volume [/B]

This is intended for use on encrypted volumes using Gutsy's disk encryption install from alt cd . May work on others but not entirely sure.

ok first things first, because I'm not a super ubuntu geek with binary dripping out of my fingers I suggest you backup all your data incase the below does happen to destroy your computer..

right now on with the facts.

get a ubuntu live cd, not the alternative install, the real deal. 
Now load up a live session
(make cuppa tea, pc spec depending)
okie dokie it should have loaded up now, run a terminal and type the following:

```

sudo -i
apt-get install cryptsetup

```

once thats finished, type following;
```

modprobe dm_crypt
modprobe sha256
modprobe aes_i586

```

ok what we've just done is install cryptsetup and loaded the modules for it into the kernel so it can be used straight away

the next bit you are going to need to know the partition for the encrypted bit is on, dont worry if you are not sure as you can do a bit of trial and error here (assuming  you only have  1 encrypted partition) if its not the correct one cryptsetup will tell you... when you do find it you will be asked for a password.

On the default guided disk encryption install you need to use sda5

```

cryptsetup -y luksAddKey /dev/sda5

```

the following will be shown..
--> enter orig password
key slot 0 unlocked
--> enter new password
--> reenter new password
command successful

you have now just added another password for the encrypted volume, the new password has been stored in key slot 1.


Next you need to delete the first password....
```

cryptsetup luksDelKey /dev/sda5 0

```
-->enter new password
key slot 1 unlocked
Command successful

And thats it!! no need to re-encrypt by copying the whole system.. done in 10 minutes! :)

any questions feel free to ask, but please make note of the high possibility that I wont have a monkeys what you are on about..

---

### Post by bodhi.zazen on 2008-01-18
Thank you PetePete, nice follow-up :)

---

### Post by jbkerns on 2008-01-19
I am a noob and really do not want to seem to sound negative, but if encrypted volumes in Ubuntu are really that fragile, do they have a point at all?

I was planning to get an Alt CD for Heron in April and  encrypt my entire drive but now I am wondering if I would be better off making a vfat partition and placing a Truecrypt volume there for all my data.  Constantly mounting the TrueCrypt volume after login would be a pain.

Thank you for this post. It was print and file worthy.  I look forward to and appreciate anyone's thoughts on my above ideas.

Namaste.

---

### Post by shaggy999 on 2008-02-02
Going the truecrypt method is *far* less secure. The most you can encrypt is anything in your /home/user directory after you've logged in. While your personal data might be encrypted, remember that your system is full of information. The system logs many of the things that you do. For example, whenever you sudo the command is kept! So people can still poke around on the rest of your system to discover things. In addition your swap file will not be encrypted. You have to unencrypt your data sometime, right? Where do you think the temporary copy is placed while working with it? Yup, swap. Using an encrypted file system EVERYTHING is encrypted w/ the exception of the /boot partition. But there's nothing interesting there, so nothing to worry about!

I just installed my system using the alternate CD yesterday, and while it was initially confusing to setup if you try to set it up manually (which I did, there's an auto-config option, but I wanted a seperate root and /home partitions which necessitated the manual setup) there are plenty of great howto guides out there.

As for the complexity of the setup, well... I tried to use truecrypt as well and followed the 'unix anonymization' guide but got completely lost at the first step. This way is way easier.

And to make it easier to change my password later I just created a bootable USB key w/ the gutsy live CD *and* made changes persistent on it. So I grabbed important applications w/ aptitude and wrote up a quick script that does the modprobe thing and asks for my password!

Simple!

---

### Post by jbkerns on 2008-02-08
Shaggy999, thanks for straightening me out and the food for thought. I am looking forward for the alt CD in April.

---

### Post by sparklyprgs on 2008-04-19
!BUMP! :cool:

excellent. thanks PetePete and shaggy999.   i was looking for this EXACT info.

two things: changing the password should be incorporated into the os eventually imho. a 10 min process is pretty bad for a noob / average user (think great aunt :-). a bootable usb / live cd is obviously very cool but still not ideal.

i want to able to setup other peoples computer with ubuntu for them (they won't be present during install) and give the fully working secure system to them with *SIMPLE* instructions on how to change the password from what ever it is i used when setting it up.

i hope 8 has this feature!

---

### Post by canonfdr on 2008-11-20
Your a rock star, Thanks this is exactly what I was looking for and worked in 1.

---

### Post by i-o on 2008-12-18
In Ubuntu 8.xx - Alternate CD installations and partitioning done: 'Guided - use entire disk and set up encrypted LVM'. In these cases with 'standard laptop' the password change goes like this:

    $ sudo cryptsetup -y luksAddKey /AddKey /dev/sda1 
    $ reboot
-------------
    $ sudo cryptsetup luksDelKey /dev/sda1 0 

DONE.

---

### Post by i-o on 2010-11-30
Now, what have changed in Ubuntu 10.10 and how this is done in that?
In identical situation giving command;

$ sudo cryptsetup -y luksAddKey /AddKey /dev/sda1

Results message; "Device /AddKey doesn't exist or access denied."

---

### Post by Travisher on 2011-03-16
You have a spurious / in front of Addkey

cryptsetup -y luksAddKey /dev/sda5

on the 10.10 version the deletion is luksKillSlot instead of luksDelKey but the old command still works

Otherwise the instructions above just work.

Edit! 
having experimented today. Don't do this!
Instead use SystemRescueCD as it automounts the LUKS partitions and has the right tools.
Don't use luksKillSlot, luksDelKey may be an obsolete command but what it does seems to work whereas luksKillSlot as suggested by the program when you enter luksDelKey seems to break things.
If you have the luxury of a spare machine or harddisk experiment on that first.

---

### Post by i-o on 2011-03-17
To find out which key slots are in use;
$ sudo cryptsetup luksDump /dev/sda5

To add a new key;
$ sudo cryptsetup -y luksAddKey /dev/sda5

To kill a key;
$ sudo cryptsetup luksKillSlot /dev/sda5 0

---

### Post by hojjat on 2011-05-06
I just wanted to thank you for this great HowTo. It was very useful.

For people who are unsure about the consequences, I suggest installing Ubuntu in a virtual machine (e.g. using VirtualBox) and messing around with there, to make sure they know what they should do to their actual installation).

---

### Post by tubbygweilo on 2011-05-07
Hmmmm... just goes to show how important it is to control physical access to an encrypted machine.

---

