---
title: "how to solve X server problem"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Unewbeginner on 2008-05-13
Hello. I have some problem with Ubuntu 8.04 so I'm installing 7.04 instead. but after installing it and rebooting the system, I can't get in the Graphic user interface. I only get some message saying that my X server has some problems.

I'm pretty new for Ubuntu so could anyone give me some hint how to solve this problem in terminal? 

I could download the driver via another computer, and copy it to a flash drive, but I don't know what I should do next. how could I get the directory of the flash drive.

Thanks

---

### Post by Lord_Dicranius on 2008-05-13
What exactly is the error you are getting regarding the X server?  That would be very helpful in helping you fix your issue :)

---

### Post by zenwalker on 2008-05-13
Well Xorg probs can be many. U need to be specific here. Plz let us know the what exact problems u r facing.

Type startx when u failed GUI mode and broght back to CLI. Then paste those errors here.

Also, u can edit /etc/X11/Xorg.conf file to see any screen resolution or related problems.

---

### Post by Unewbeginner on 2008-05-13
> **Lord_Dicranius said:**
> What exactly is the error you are getting regarding the X server?  That would be very helpful in helping you fix your issue :)

something like "no screen detected, we've disabled your X server. you could start it after you configure it correctly".

I think I should download the update driver to solve that problem.

btw, the progress bar stuck at 85% when I installed the system. I searched online and someone suggested to use the following code to get it around:

Ctrl + Alt + F2
killall apt-get
Ctrl + Alt + F1

I tried it and it worked to me. The progress bar was moving again and finished installation.

Do you think my command has anything to do with this problem?

thanks

---

### Post by Unewbeginner on 2008-05-13
hello, here is the exact system message:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

I clicked "yes", and got some information:

No devices detected
Fatal server error:
no screens found


And then I could also got detailed output, where I could see the information about my monitor (Hanns.G) and Video Card (nVidia).

And the final message is:

The X server is now disabled. restart GDM when it is configured correctly.

---

### Post by Unewbeginner on 2008-05-13
> **zenwalker said:**
> 

Type startx when u failed GUI mode and broght back to CLI. Then paste those errors here.

Also, u can edit /etc/X11/Xorg.conf file to see any screen resolution or related problems.

I typed startx and here is the message:

--------------------------------------------
Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 know processed) with 0 events remaining.
--------------------------------------------

BTW, I tried installed it again and it went smoothly after 85%. but I still have this GUI problem.

Could anyone help me out? thanks

---

### Post by Unewbeginner on 2008-05-13
hello, I downloaded the new driver for my video card (NVIDIA-Linux-x86-169.12-pkg1.run), and I copied it to a flash drive. Could anyone let me know how to access it through terminal? It seems that I can only access the file system in terminal.

Thanks

---

### Post by Canis familiaris on 2008-05-13
To get back X:
Press Ctrl + Alt + F1 to go to tty0
In the command prompt, type:
```
sudo dpkg-reconfigure xserver-xorg

```
Choose graphics driver as "vesa" if all else fails.

---

### Post by Canis familiaris on 2008-05-13
After GUI runs you can try installing your graphics driver.

---

### Post by Unewbeginner on 2008-05-13
> **Anurag_panda said:**
> To get back X:
Press Ctrl + Alt + F1 to go to tty0
In the command prompt, type:
```
sudo dpkg-reconfigure xserver-xorg

```
Choose graphics driver as "vesa" if all else fails.


Hello. thanks for your information. But I still can't make it work.

I Press Ctrl + Alt + F1, but it's tty1 not tty0
I typed the code and followed with the instrucitons. I didn't see any option about graphics driver.

Anything I'm missing?

One more information: when i restart my computer, the monitor tells me it out of range.

---

### Post by redbob on 2008-05-13
I already saw that not always dpkg works in Hardy. You could save your day if you "force" xserver to accept vesa configuration. Type this command > sudo nano /etc/X11/xorg.confand change the respective section:> Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

so you do a restart in gdm> sudo /etc/init.d/gdm restartTell us what you got!

---

