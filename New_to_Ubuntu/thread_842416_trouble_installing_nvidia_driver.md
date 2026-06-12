---
title: "trouble installing nvidia driver"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by nfrsbmschmck on 2008-06-27
I just got ubuntu the other day as I was having troubles with windows. Of course the first thing I try to accomplish in Linux is just not working for me. I am trying to install the nvidia drivers for my 8800GT and use them to use both my monitors. nvidia thankfully had a linux driver that I downloaded to the desktop and I typed the following into the terminal

sudo sh Desktop/NVIDIA-Linux-x86-173.14.09pkg1.run

it says that it cannot open it.
so I typed in

sudo sh /home/charles/Desktop/NVIDIA-Linux-x86-173.14.09-pkg1.run

that opens it but then it says that I have an X server running and I need to exit from that before I can install the driver. So I looked up how to quit the X server and tried ctrl-alt-F1 to enter the console. I even added

sudo /etc/init.d/gdm stop

which I found someone say that that stops the X server. Anyway, in the non GUI console when I type in the same lines it now goes back to saying that it can't open it.
I realize I probably should have sat down and learned more about linux before I tried to do something specific, but oh well.

Thanks for any help!

---

### Post by Pjotr123 on 2008-06-27
Don't use the restricted driver that you downloaded manually. First try the restricted driver in the software repo's of Ubuntu. If that one's too old, try using Envy. 

A simple how-to:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

(no hyperlinks in the content list, you have to scroll down)

---

### Post by PmDematagoda on 2008-06-27
I agree with Pjotr123, this is especially since the driver in the Ubuntu repos is currently atleast 169.12 which works with the 8800GT card, to install the driver go to System>Administration>Hardware Drivers and enable the Nvidia driver.

---

### Post by ChameleonDave on 2008-06-27
> **nfrsbmschmck said:**
> I just got ubuntu the other day as I was having troubles with windows. Of course the first thing I try to accomplish in Linux is just not working for me. I am trying to install the nvidia drivers for my 8800GT and use them to use both my monitors. nvidia thankfully had a linux driver that I downloaded to the desktop and I typed the following into the terminal

sudo sh Desktop/NVIDIA-Linux-x86-173.14.09pkg1.run

it says that it cannot open it.
so I typed in

sudo sh /home/charles/Desktop/NVIDIA-Linux-x86-173.14.09-pkg1.run

that opens it but then it says that I have an X server running and I need to exit from that before I can install the driver. So I looked up how to quit the X server and tried ctrl-alt-F1 to enter the console. I even added

sudo /etc/init.d/gdm stop

which I found someone say that that stops the X server. Anyway, in the non GUI console when I type in the same lines it now goes back to saying that it can't open it.
I realize I probably should have sat down and learned more about linux before I tried to do something specific, but oh well.

Thanks for any help!

If the first command failed to find the file, and the second succeeded, then you got the path wrong.  Make sure the path is right.  If it is on your desktop, then this will work:

```
sudo sh ~/Desktop/NVIDIA-Linux-x86-173.14.09-pkg1.run
```

You might just want to make sure the file is executable first:

```
chmod +rwx ~/Desktop/NVIDIA-Linux*
```

And you definitely do need to make sure that GDM and any other graphical program is totally shut down before running the script.


Edit: of course, this assumes that the drivers in the official repositories don't work for you, and that EnvyNG didn't get the card working either.

---

### Post by bumanie on 2008-06-27
That nvidia driver would be too old for your video card. You should download the 'generic' ubuntu driver and try it first. System --> Administration --> Hardware Drivers and enable the driver.

---

### Post by PmDematagoda on 2008-06-27
> **bumanie said:**
> That nvidia driver would be too old for your video card. You should download the 'generic' ubuntu driver and try it first. System --> Administration --> Hardware Drivers and enable the driver.

Actually, the 173 driver is much newer than the one that is currently(or has it changed?) in the Ubuntu repositories and in any case the 173 driver is for the 9-series cards, so it would work rather well with the OP's 8800GT.

---

