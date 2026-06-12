---
title: "Where is the sidebar? 11.04"
date: 2011-09-26
forum: New to Ubuntu
---

### Post by mirkaim on 2011-09-26
Hello.

I am new to linux and, of course, Ubuntu. I just installed it as a virtual machine and the left sidebar that I see in many videos is no there. I think there was an error about Unity not installing or something.

If the sidebar is Unity, then how can I get it turned back on or installed? 

Thanks.

P.S. I also tried installing it on an old laptop but the sidebar didn't load there either so I don't know what is going on.

---

### Post by mikewhatever on 2011-09-26
The side bar, called the Launcher, is on the left side of the screen, if, of cause, Unity is running. Unity in 11.04 doesn't work with all hardware. Older graphics cards are blacklisted, newer Nvidia and ATI ones need proprietary drivers installed, and so on. Unity in 11.10 should work with most of the cards.

So, if you don't get the Launcher on the left, post the output of **lspci** from Terminal.

---

### Post by mirkaim on 2011-09-26
I see this:

00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter

Since it's running on VirtualBox and an old crappy laptop, I guess these display devices aren't going to cut it. Is that probably the case?

Thanks for the reply.

---

### Post by hyper2hottie on 2011-09-26
That would most likely be the problem.  11.04 will run gnome 2 if your hardware can not run Unity.  Do you have a bar across the bottom of the screen where your applications go?

---

### Post by technosysind on 2011-09-26
Have you installed experimental drivers or proprietary drivers??

---

### Post by mirkaim on 2011-09-26
I do have the task bar looking one with the "show desktop" and the open windows. I haven't tried any experimental drivers yet since I thought VirtualBox would let me just use the save drivers as the host (NVidia) instead of their built in one. But that's a problem for VirtualBox instead of Ubuntu.

Actually, is there somewhere that shows me the display driver and will let me change it? VirtualBox might have a way to use some better drivers.

---

### Post by hyper2hottie on 2011-09-26
It is definitely running gnome 2 then.  You could try
[http://www.theopensourcerer.com/2011/04/21/ubuntu-natty-in-virtualbox-with-unity/](http://www.theopensourcerer.com/2011/04/21/ubuntu-natty-in-virtualbox-with-unity/)
to make it work.  Though i have not tried using this advice so I don't know that it works.
You might have not given it enough ram or vid card ram.  It could also be that you are missing **virtualbox-ose-guest-x11 **as suggested in the link above.

---

### Post by coffeecat on 2011-09-26
> **mirkaim said:**
> 00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter

Since it's running on VirtualBox

You are running it as a guest OS in VirtualBox. The guest OS sees a virtual graphics device, not the real hardware. You need to install Guest Additions in the guest OS and enable 3D acceleration under Display in VirtualBox settings for the virtual machine. Even so, you will only get sufficient 3D acceleration in your guest OS if the host system has access to an adequate video card/driver combination.

---

### Post by Paqman on 2011-09-26
It's unlikely that you're going to get good enough 3D performance in a VM even if you do what coffeecat suggested. 3D graphics in virtualisation is still in it s infancy, although it's making good progress.

For now what you can do is install the 2D version of Unity. Open up the package manager, install the package unity-2d, log out and when you go to log back in, instead of Ubuntu Classic, choose Unity 2D as your desktop.

---

### Post by mirkaim on 2011-09-26
Thanks for all the answers. I have installed Ubuntu on a hard drive normally and it found additional NVidia drivers and now I can see Unity. The quest for Ubuntu knowledge continues.

Thanks!

---

### Post by mirkaim on 2011-09-27
edit:
nevermind.

---

### Post by mikee55 on 2011-09-27
I have the same issue, but happily I'm in Ubuntu classic mode, and have Cairodock installed
Open the terminal and copy and past the command bellow :

&#65279;sudo add-apt-repository ppa:cairo-dock-team/ppa

Refresh the repositories:

sudo apt-get update  

Now install cairo-dock :

sudo apt-get install cairo-dock cairo-dock-plug-ins

---

