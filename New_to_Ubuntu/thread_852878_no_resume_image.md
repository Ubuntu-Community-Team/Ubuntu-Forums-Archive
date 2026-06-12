---
title: "no resume image"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Ddub on 2008-07-08
I installed Kubuntu over Ubuntu 8.04 following these instructions:

The updated packages for Kubuntu 8.04 are located in the Kubuntu Member's KDE 4 Personal Package Archive (PPA) repositories. To update to this latest beta release of KDE 4.1, please complete the following:

   1. Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main to your /etc/apt/sources.list.
   2. If you already have the kubuntu-kde4-desktop packages installed, simply type sudo apt-get update && sudo apt-get dist-upgrade and answer the questions in which you are prompted. If you do not have kubuntu-kde4-desktop installed, simply type sudo apt-get update && sudo apt-get install kubuntu-kde4-desktop and answer the questions. Both of these options are to be typed at the command prompt.

I then updated it partially and then restarted. Kubuntu was still working at this point. I got the rest of the updates and restarted a second time. Now Kubuntu says it can't find a resume image and kicks me into a terminal session. The screen then goes black three times and the normal sounds associated with the login screen play but the screen is blank.

Does anyone know what caused this and how to reverse it?

---

### Post by ChameleonDave on 2008-07-08
It installed fine for me.

I'm not sure about this resume image stuff.

Generally, if you are stuck on the command line, you can get into a graphical session with commands such as "startkde", "startx", "sudo gdm", and suchlike.

---

### Post by Ddub on 2008-07-08
Ok so how do I uninstall it from the terminal so I can go back to Gnome?

---

### Post by ChameleonDave on 2008-07-08
> **Ddub said:**
> Ok so how do I uninstall it from the terminal so I can go back to Gnome?

No need to uninstall KDE.  That won't fix the problem.  Obviously something got screwed up in the installation process.  It will still be screwed up without KDE installed.

Were you able to access the graphical desktop using one of the commands I suggested?

You may need to reinstall or reconfigure your graphics card.

---

### Post by ChameleonDave on 2008-07-08
> **Ddub said:**
>  Now Kubuntu says it can't find a resume image and kicks me into a terminal session.

OK, I've looked that up.

The "no resume image" is not an error.  It comes up at every boot.  Ubuntu is looking in the swap space for a file indicating that you hibernated instead of shutting down, last time you used the computer.  If you shut down fully then it will fail to find a resume image, and report this.  Normally, this message goes by quickly, and you don't notice it.  This time, because the graphical desktop has failed to start, you are left staring at the message.

Here is a command that people suggest may help with the sort of booting problems you are having:

```
sudo update-initramfs -u
```

---

### Post by abn91c on 2008-07-08
> **Ddub said:**
> Ok so how do I uninstall it from the terminal so I can go back to Gnome?
  you install may be hosed, you probably should have used synaptic to install kubuntu.Anyways, to remove it at the prompt do: sudo aptitude remove kubuntu-desktop

---

### Post by ChameleonDave on 2008-07-08
Another possibility is that the log-in manager KDM is malfunctioning.  In which case, you should make sure that you are using GDM, which you know works.

```

sudo apt-get install gdm && sudo apt-get remove kdm kdm-kde4

```
A blue screen with questions may come up.  Answer that you want to use GDM.

---

### Post by ChameleonDave on 2008-07-08
> **abn91c said:**
> you install may be hosed, you probably should have used synaptic to install kubuntu.Anyways, to remove it at the prompt do: sudo aptitude remove kubuntu-desktop

There is no reason to think that Synaptic would have done a better job that apt-get.  Synaptic uses apt-get behind the scenes.

Removing "kubuntu-desktop" won't do anything, because it is just a meta-package, which uses dependencies to install a whole host of other programs.

What we need to do is allow him to use his computer normally.  Once that is achieved, he can decide which desktops he wants to install/remove.

---

### Post by Ddub on 2008-07-09
I tried the startkde, startx, and sudo gdm. It said startkde wasn't installed. Startx gave me an error about my video card (NVIDIA GeForce FX5200)not having the proper drivers which makes sense because I just switched to the restricted driver. Sudo gdm gave me the same problem as before when the screen blinks three times then goes blank. I hadn't noticed before but the monitor isn't picking up anything when this happens, making me think it's the video card that's the problem. I guess I could try installing the drivers again but I don't know how to do it from the command line.

---

### Post by ChameleonDave on 2008-07-09
OK, the FX5200 shouldn't be a problem.  My girlfriend has one, and she also runs Hardy Heron with KDE 4.

Do this:

```
sudo apt-get install -y envyng-qt
sudo envyng -t
```

Then press 1.

That should set up your card.

---

### Post by Ddub on 2008-07-09
It works now, thanks so much.

---

### Post by ChameleonDave on 2008-07-09
> **Ddub said:**
> It works now, thanks so much.

Great!  So you're able to log into GNOME okay now?  Can you also get into KDE 4?

Perhaps you could use the "Thread Tools" menu to mark this as solved.

---

### Post by Ddub on 2008-07-10
Gnome works. I've removed KDE4 because I heard it was incomplete. I'm downloading KDE 3.5.9 now and will test it when it's finished.

---

### Post by Ddub on 2008-07-10
KDE works too.

---

### Post by ChameleonDave on 2008-07-10
> **ddub said:**
> kde Works Too.

Maxum&#275; gaudeo bon&#333; tu&#333; &#275;uent&#363;!

---

### Post by Ddub on 2008-07-10
Haha... Latina tua non mala est.

---

