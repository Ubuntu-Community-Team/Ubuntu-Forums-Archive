---
title: "Have GeForce video driver but it won't install..."
date: 2008-09-14
forum: New to Ubuntu
---

### Post by BillyBlaze on 2008-09-14
Okay after farting around forever I found from nvida what looks to be the right driver for my card. 

[http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html)

Problem is if I double click the download it wont run gives me some sort of error. Okay no problem. I:
     1. Right clicked on the file and chose properties.
     2. Chose the permissions tab, then checked "Allowed executing as             
        program"

Not bad for a rookie huh... Anyway. The file starts to run but won't in the "display" mode. If I chose to run the file in "terminal" it start. 

Now here's my issue. Just after it starts I get a message from nvida saying nvida installer must be ran as root. ???

In terminal I've logged in as superuser, then returned to install the driver, but got the same message. 

How on earth do I run this installer as root like it asks for?????

---

### Post by Mornedhel on 2008-09-14
Have you tried enabling the driver in the Hardware Drivers manager ? (System > Administration > Hardware Drivers) This is the recommended way, as it pulls the driver from the official Ubuntu repositories.

Assuming you have :

You need to run the file from the terminal. You make it sound as if you sudo'ed in the terminal, then double-clicked the .run file in Nautilus. You need to do this in a terminal :

[when in the appropriate directory]
sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run
[enter your password, proceed]

---

### Post by 1/0 on 2008-09-14
Why not use the driver in the repository? Its much easier to install and not that bad. You'll find instructions [here](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) that probably explains it better than I do.

---

### Post by BillyBlaze on 2008-09-14
Thanks for the responce. When I go into system > administration there is no Hardware drivers. Only Restricted drivers manager.

But yea your 100% correct. I sudo'd, then double clicked the icon and close run in terminal. 

If I run it straight from terminal what would be the command to execute the file?

---

### Post by 1/0 on 2008-09-14
```
./filename
```
After having made it executable
```
chmod +x filename
```

---

### Post by 1/0 on 2008-09-14
You might like the *nvidia-settings package*. Its a gui that gives you some info and settings in one window.

---

### Post by Mornedhel on 2008-09-14
Try the Restricted Drivers first (are you using Gutsy ?)

If it doesn't work (you will need a reboot), from the terminal :

sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run

Shouldn't need to change the permissions since you say you already did so.

---

### Post by BillyBlaze on 2008-09-14
I checked into using the hardware device manager option. I'm running Ubuntu version 7.10, and it doesn't have the option of hardware drivers. In 7.10 it has "restricted driver manager" I've turned on the one and only driver that it lists in there, but still no effect. 

I can't change my screen resolution to my monitor of 1920 x 1200, and I'm unable to use the "visual effets" in the appearance section. 

As far as the Gutsy option. Call me a rookie, but I don't know what that is. 

The other option I was given was to run: sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run

This is what it came back with: 

wmanganaro@wmanganaro-tower:~$ sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run
sh: Can't open NVIDIA-Linux-x86-173.14.12-pkg1.run

---

### Post by Mornedhel on 2008-09-14
> **BillyBlaze said:**
> I checked into using the hardware device manager option. I'm running Ubuntu version 7.10, and it doesn't have the option of hardware drivers. In 7.10 it has "restricted driver manager" I've turned on the one and only driver that it lists in there, but still no effect.

Did you restart your computer ? There should be an icon on the top-right panel asking you to restart your computer.

> **BillyBlaze said:**
> As far as the Gutsy option. Call me a rookie, but I don't know what that is.

I was just wondering if you were using the previous version of Ubuntu, called Gutsy Gibbon. Apparently you are, since you say you're running on 7.10. In the current release (8.04, "Hardy Heron"), the Restricted Drivers entry was renamed to Hardware Drivers. Hence, much confusion.

> **BillyBlaze said:**
> wmanganaro@wmanganaro-tower:~$ sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run
sh: Can't open NVIDIA-Linux-x86-173.14.12-pkg1.run

I apologize for not making myself clear from the start. In the terminal, you need to be in the folder where you saved the file you mention in your original post. I assume it's still on your desktop, so the complete string of commands should be :

cd Desktop
sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run

You may need to replace 'Desktop' by the folder you put the file in, and 'NVIDIA-Linux-x86-173.14.12-pkg1.run' by the actual name of that file. I went to the URL you gave in your original post to get the correct filename, but I might have gotten it wrong.

---

### Post by 1/0 on 2008-09-14
Try:

```
sudo apt-get install nvidia-xconfig
```

Then simply run:
```
sudo nvidia-xconifg
```

If you run the other one you'll have to manually update it, manually reconfigure and so on. Not at all something I would recommend someone just starting off with GNU/Linux.

---

### Post by BillyBlaze on 2008-09-14
Thanks Mornedhel for the detailed explanation. I'm still pretty new to this. 

I did what you said, and here's what I got:

wmanganaro@wmanganaro-tower:~/Desktop$ ls
NVIDIA-Linux-x86-173.14.12-pkg1(2).run  NVIDIA-Linux-x86-173.14.12-pkg1.run

wmanganaro@wmanganaro-tower:~/Desktop$ NVIDIA-Linux-x86-173.14.12-pkg1.run
bash: NVIDIA-Linux-x86-173.14.12-pkg1.run: command not found

wmanganaro@wmanganaro-tower:~/Desktop$ 

wmanganaro@wmanganaro-tower:~/Desktop$ 

As you can see I listed the contents of the desktop folder to make sure I was spelling it right. I don't know why but I get this "command not found" error?

---

### Post by Mornedhel on 2008-09-14
Almost there, almost there.

1. You positive the Restricted Drivers manager didn't do the trick, even after rebooting ? Not sure the official drivers fresh from the NVidia site will work, since the restricted drivers *are* official as well, just maybe not up-to-date.

2. If it didn't : you forgot the sudo sh before the NVIDIA-... filename. Also, extra tip for console use : type sudo sh NV and press TAB (that's right, before you've finished typing the filename).

---

