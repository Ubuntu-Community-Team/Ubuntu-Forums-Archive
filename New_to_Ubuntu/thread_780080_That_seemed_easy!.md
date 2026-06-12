---
title: "That seemed easy!"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by vapd on 2008-05-03
Well the install of Hardy Heron was simple. Is there an Ubuntu version of Device Manager anywhere so I can check everything is installed correctly? Or some kind of stress test software like Orthos?

Thanks

---

### Post by Paqman on 2008-05-03
Go to (I think) Applications > System > Hardware Testing. It'll run through some of the main systems.

---

### Post by Bodsda on 2008-05-03
Go to System--> Administrator--> Hardware test

---

### Post by vapd on 2008-05-03
Found it, havnt been able to test the sound as I cant be bothered to plug speakers in atm, but I noticed that it didnt mention the USB controllers or the firewire or the PCI adsl modem (not that I am using it nor do I intend to). Is this normal?

---

### Post by Bodsda on 2008-05-03
Yes, the hardware test only tests certain things. For your piece of mind try running these commands 

```
lsusb
```
^^ will show usb devices

```
lspci
```
^^ will show pci devices

---

### Post by gameryoshi600 on 2008-05-03
also try looking at the restricted drivers which are now in hardy called "Hardware drivers"
system>administration>hardware drivers

---

### Post by vapd on 2008-05-03
hi,
I typed in 1susb in the terminal and got:

Command not found

What am I doing wrong?

Thanks

---

### Post by Bodsda on 2008-05-03
Lsusb (little ell 'L' 'l')

```
lsusb
```

---

### Post by vapd on 2008-05-03
got it, thanks! All seems in order.

Sorry to keep asking questions but I have some more, I am trying to get my refresh rate (still using an old CRT!) to 72 and it wont let me set above 60. I am using an old KVM switch on the Ubuntu rig and my newer PC running win2k, it is happily at 72 on the windows rig with the same resolution as the ubuntu one. AGP card in the Ubuntu rig is 9800se so I cant see it being a problem with that. Any ideas?

---

### Post by Bodsda on 2008-05-03
you have to edit xorg.conf. can u paste the contents of    /etc/X11/xorg.conf here please.

also what is the make and model of your monitor?

(cant stick around atm im afraid but more info on your problem is here -- [http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

---

### Post by vapd on 2008-05-03
okay I will have a read of that. 

Just wondering as I am getting an LCD next week (Tuesday or Friday depending on when I can wangle a day off) do I need to worry about it as I doubt I will have to change the refresh rate with it? Or will I need to do you think?

And how do I display the contents of /etc/X11/xorg.conf ? I have tried typing this into the terminal but just get no such file or directory?

Thanks again!

Okay it was a typo, got it right eventually and got the message permission denied so I tried again but with sudo, and then my password as prompted but then I got command not found? I know I am doing something wrong but I dont know what. Sorry to be a pain.

---

### Post by MONODA on 2008-05-03
you need to specify a command to run on the file /etc/X11/xorg.conf like this:
sudo cat /xorg.conf

just copy paste the results of that command here. you probably want to configure keyboard shortcuts in the terminal. BTW linux is case sensitive.

---

### Post by sailor2001 on 2008-05-03
it's much easier to go direct to the directory to check or change anything for you monitor....... /usr/share/applications/screen & graffic

---

### Post by vapd on 2008-05-04
Hi sailor2001, had a look at that but 60 is the max option I have there as well.

Hi MONODA I have tried sudo cat/xorg.conf and just get the command not found.

My monitor is a Dell 1025HE

I am going to have a look at Bodsda's link.

Thanks

Edit: just typed in the first line on that link that was designed to back up the such and such file and when I hit enter the screen jolted and I just have a lot of white text on a full screen of black! I hit ctrl/alt/del as nothing else seemed to be happening and the system is rebooting. Is this normal?

Another edit: oh no I am an idiot, I typed the line below which was designed to stop xorg (I think). Will keep trying!

---

### Post by vapd on 2008-05-04
Well I have to hold my hands up and say that I obviously dont know what I am doing, but I am trying!

I did the back up step in the above link. Then typed the code to get to text only mode. This time when I hit enter the screen went to a similar one to last time but not the same. Less text. Oh well, I then typed in 

sudo dpkg-reconfigure xserver-xorg

and expected something to happen, but it didnt. So I typed:

sudo /etc/init.d/gdm start

and expected to get the desktop back but nothing happened again?

Dont know what I am doing wrong but any help is appreciated!

---

### Post by MONODA on 2008-05-05
> Hi sailor2001, had a look at that but 60 is the max option I have there as well.

Hi MONODA I have tried sudo cat/xorg.conf and just get the command not found.

My monitor is a Dell 1025HE

I am going to have a look at Bodsda's link.

Thanks

Edit: just typed in the first line on that link that was designed to back up the such and such file and when I hit enter the screen jolted and I just have a lot of white text on a full screen of black! I hit ctrl/alt/del as nothing else seemed to be happening and the system is rebooting. Is this normal?

Another edit: oh no I am an idiot, I typed the line below which was designed to stop xorg (I think). Will keep trying!
oops, sorry type:
> sudo cat /etc/X11/xorg.conf
and copy paste it into a post here.

---

