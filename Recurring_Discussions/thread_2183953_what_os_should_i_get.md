---
title: "what os should i get"
date: 2013-10-27
forum: Recurring Discussions
---

### Post by vlcplayerfan on 2013-10-27
i hate unity 

want i need is 

the os to run Ubuntu apps
look like mac os or how the old Ubuntu looked before it changed to unity

also needs to be able to work with [FONT=Arial][COLOR=#202020][COLOR=#ff00ff][FONT=Arial][SIZE=2][COLOR=#202020]Mobile Intel(R) 945 Express Chipset Family (128 MB) 

ubuntu could not work with it had to run in [/COLOR][/SIZE][/FONT][/COLOR][/COLOR][/FONT]fail safe graphics mode then i was able to load the os 

any help would be great
[FONT=Arial][COLOR=#202020][COLOR=#ff00ff][/COLOR][/COLOR][/FONT]

---

### Post by Lars Noodén on 2013-10-27
All the *buntus run the same apps from the same repositories.  If you liked the old style GUI, then probably your closest bet would be Xubuntu.  

If you want an OS X-like dock then [glx-dock](http://www.glx-dock.org/) should do the job.  It used to be called Cairo Dock, so you may have to look for it under the old name in the repository.

All the linuxes are modular, so you can always swap out the pre-packaged Desktop Environment or Window Manager for one of your choice.  Same thing for the actual configuration of the DE or WM.

---

### Post by vlcplayerfan on 2013-10-27
thx

---

### Post by vlcplayerfan on 2013-10-28
anybody more help

---

### Post by Lars Noodén on 2013-10-28
What was wrong with Xubuntu?

---

### Post by ian-weisser on 2013-10-28
Seems like Lars answered the question you asked. Correctly and concisely.
Did you intend to ask a different question? Or a followup?

---

### Post by buzzingrobot on 2013-10-28
Concentrate on finding something that will work with that GPU.  That's your stumbling block.  Newer interfaces that rely on 3D capabilities are going to give you problems.

Ubuntu pre-Unity was the panel-based Gnome 2. If you want to a panel-based interface, that's available via KDE (Kubuntu), XFCE, (Xubuntu) or LXDE (Lubuntu). Also available is Mate, which is a near-identical fork and recompilation of Gnome 2.  It's not available as an official Ubuntu version, but is offered on several Ubuntu derivatives, and can be installed directly on Ubuntu by following the directions at mate-desktop.org.

If you want a dock-based interface, there is Unity (Ubuntu), Gnome Shell (Ubuntu-Gnome) or, perhaps, Elementary OS (a derivative based on 12,04).

Docks can be installed independently, too.  Cairo, Docky and Plank offer different capabilities and styles.

---

### Post by vlcplayerfan on 2013-10-28
> **Lars Noodén said:**
> What was wrong with Xubuntu?


could not get it working with [FONT=Arial][COLOR=#202020][COLOR=#ff00ff][FONT=Arial][SIZE=2][COLOR=#202020]Mobile Intel(R) 945 Express Chipset Family (128 MB) [/COLOR][/SIZE][/FONT][/COLOR][/COLOR][/FONT]

---

### Post by vlcplayerfan on 2013-10-29
bump

---

### Post by ibjsb4 on 2013-10-29
You didn't have to scrap Ubuntu just because of the Unity desktop.  The old style desktop can be installed a chosen at boot (login).

[https://apps.ubuntu.com/cat/applications/saucy/gnome-session-flashback/](https://apps.ubuntu.com/cat/applications/saucy/gnome-session-flashback/)

also

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by Bucky Ball on 2013-10-29
*Thread moved to **Recurring Discussions**.*

---

### Post by vlcplayerfan on 2013-10-30
> **ibjsb4 said:**
> You didn't have to scrap Ubuntu just because of the Unity desktop.  The old style desktop can be installed a chosen at boot (login).

[https://apps.ubuntu.com/cat/applications/saucy/gnome-session-flashback/](https://apps.ubuntu.com/cat/applications/saucy/gnome-session-flashback/)

also

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)


thanks man TY

but how to get it working with my graphics card properly?

---

### Post by vlcplayerfan on 2013-10-31
bump

---

### Post by Lars Noodén on 2013-10-31
> **vlcplayerfan said:**
> but how to get it working with my graphics card properly?

That's the real question here.  I would recommend starting a thread with that specific question in the [hardware section](http://it.slashdot.org/comments.pl?sid=4396411&cid=45284965) so other people can see it.

---

### Post by carlwsnyder on 2013-10-31
Did you try an Ubuntu/Xubuntu Live disk? or did you dive in and directly install?  Were you trying to get graphics acceleration working when your installation busted? Do you know which kernel you were installing/version of Xubuntu?  You graphics drivers are installed as kernel modules.  If you are having kernel problems, you may want to install Xubuntu 12.04 rather than a later version, and not update until 14.04 or later.  The only other option is to install a non-Ubuntu/non-Debian derived distribution to see if that runs better.

My own experience with the hardware which I have used was that the Debian derived kernels worked better, and I couldn't get Fedora, or OpenSuSE to work.  I could get Mageia/Mandriva family distros to work, but the Debian family worked better. YMMV.

---

### Post by ibjsb4 on 2013-10-31
> **Lars Noodén said:**
> That's the real question here.  I would recommend starting a thread with that specific question in the [hardware section]("http://it.slashdot.org/comments.pl?sid=4396411&cid=45284965") so other people can see it.

Good idea and post your computer specs (ram, cpu, video).

---

