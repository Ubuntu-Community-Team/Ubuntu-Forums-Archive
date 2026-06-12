---
title: "Tesla Drivers"
date: 2015-05-08
forum: New to Ubuntu
---

### Post by phillip16 on 2015-05-08
Hello everyone,

I am extremely new to Ubuntu. About as green as grass. 

I am attempting to install drivers for a Nvidia Tesla C1060 graphics and I was wondering, what is the best method to do this?

Looking in the user manual: [http://www.nvidia.com/docs/IO/56484/NV_C1060_UserManual_Guide_FINAL.pdf](http://www.nvidia.com/docs/IO/56484/NV_C1060_UserManual_Guide_FINAL.pdf) on page 16, it specifies how to do this.

Which I am following the directions but it is asking me to kill the X-server and to change the default run level such that it will boot to VGA. Killing the X-server, I can do, but chagning the defualt run level, I do not know how. How do I proceed to this in the command line?

Also, are there any other better methods then what nvidia has said?

Thank you for your help and I await your reply!

---

### Post by oldfred on 2015-05-08
Just install Ubuntu and in System drivers install the correct legacy driver for your system.
Do not download from nVidia.

This says the 340.xx is correct, but if 14.04 you may not have that in repository. Just install newest. But do not install anything newer than 340.xx or wrong older legacy driver. If you accidentally install wrong driver be sure to totally purge old first. Otherwise major conflicts.

 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Screen shots are from my older nVidia and 12.04 (I think). But process is still the same. The 331. were the most current then and my 9600GT uses the same legacy driver as yours. The 340.xx was just converted to a legacy driver.

---

### Post by phillip16 on 2015-05-09
Cool, thanks.

Also, I have a Geforce GTX 480 installed which allows me to have displays plugged in. The Tesla Series is designed only for calculations.

So, would I follow the same process for the GTX 480?

---

### Post by phillip16 on 2015-05-09
Ok, so earlier, I download the 340.87.run from nvidia website. (64 bit version)

Now, under the additional Drivers tab, I only have options for the Geforce GTX and not the tesla. Should I go ahead and install the Geforce from the Additional Drivers tab and then execute the run file for the Tesla drivers?

Actaully, I am not 100% familiar with Nvidia. I am a little familiar with AMD and I know that their workstation cards are not updated in the same file as the desktop cards. However, for nvidia, are the workstatin card drivers in the same file as the desktop?

---

### Post by phillip16 on 2015-05-09
Oh ok, scratch that, I can install the Tesla drivers from Additional Drivers tab

So it looks like, I can install the 331.113 version and it says that it has been tested!

---

### Post by oldfred on 2015-05-09
I know that mixed drivers causes all sorts of issues.
And installing directly from nVidia with a .run file will force you to re-integrate it into every kernel update, or a major hassle for a new user.
Always best to use repository or if you really need newer drivers use a ppa which is another repository.

Have no idea how two totally different cards needing different drivers may work. That may not even be possible. Or use the newest driver for the oldest card and it may work ok for newer card as long as it is not one of the very new ones that has to have the very newest drivers.

---

### Post by phillip16 on 2015-05-09
OK so an interesting thing happened, I also installed the nvidia Xserver configurator using apt-get.

Now, I always have this pop up about how to OS could not configure the monitor error. I forget exactly what it was but it was a CRC. I clicked ok and then, Ubuntu crashed :(

I then rebooted and the computer was unable to boot into Ubuntu. All I get is a blinking cursor..

After a few times restarting, I now get the option to boot into Ubuntu, boot into recovery, or perform memtest.

Any ideas?

Also, this is the second time this has happened. First time around, I reinstalled Ubuntu. During that time, I installed the Geforce drivers first and the pop-up went away. I think that time, it occurred after I killed X-server. Not too sure

---

### Post by oldfred on 2015-05-10
Did you install nVidia from the .run and then xServer from repository?

The only time I have had issues with nVidia was first boot after install and then I had to use nomodeset. I think nomodeset is now a default on the recovery boot grub entry. If you only have Ubuntu you do not get grub menu normally. But after boot errors then it will appear. Use shift key if you want grub menu.

Is monitor very old so it does not have an EDID. Then nVidia would not now how to configure it and you have to do that manually. I have not had to do that since 2006/2007, so do not know current procedures.

---

### Post by phillip16 on 2015-05-10
I installed them from the xServer repository.

The monitor is a dell (that could be the issue) and I believe it is from 2010. Connected via DVI.

---

### Post by oldfred on 2015-05-10
Monitor should be ok. 
Mine is an HP from 2006 and has no issues due to monitor. It is always seen correctly.

---

### Post by phillip16 on 2015-05-12
Ok, I am still unable to boot to the OS. I got to the recovery menu and tried the failsafe graphics card option. Unfortunately, when I boot again into the OS, I get black screen with blinking cursor.

---

### Post by phillip16 on 2015-05-12
Hey everyone, I had a friend help me. Not too sure what he did but I can now boot into the OS

---

