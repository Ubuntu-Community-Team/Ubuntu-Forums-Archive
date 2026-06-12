---
title: "Ubuntu / kubuntu"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by TomTravis on 2008-07-26
I am a beginner at learning this linux stuff.  I've made attempts with slackware in the past and read a few books but did not seem to catch on, so I am trying it again.

I decided to dive into UBUNTU because I needed something to teach at a week long church computer camp for middle school kids that I volunteer at every year.  It is difficult to teach kids anything new about windows and the old computers we had would not run XP well so I decided we would all learn about UBUNTU together. It was amazing how fast the kids picked up UBUNTU after I took their windows away from them.

We loaded and ran UBUNTU with the GNU interface.  I've been reading about KUBUNTU and the KDE interface.  My question is, can I go from GNU to KDE and back, or do I have to boot into the KDE environment if I want to simply check out KDE?

Thanks for giving me a great OS to teach at my camp.

Tom Travis

---

### Post by hyper_ch on 2008-07-26
you can install kubuntu-desktop on an existing system... but it requires about 200 mb to download...

```

sudo aptitude install kubuntu-desktop

```

---

### Post by SuperSonic4 on 2008-07-26
Ubuntu uses GNOME, GNU is a software licence.

you can do ```
sudo apt-get install kubuntu-desktop
```. That will install the Kubuntu desktop and you can change session at the login screen.

If you want to keep them entirely separate I suggest partioning the drive and installing them separately.

You can use apt-get or aptitude install. The latter is better if you need to remove it I believe.

---

### Post by silkstone on 2008-07-26
Once you've installed the KDE desktop on an Ubuntu machine, or vice versa, you can choose which to use at the login screen - so log out and in again to switch.

You can also run KDE applications in a Gnome environment, although you have to install the relevant dependencies (should be done automatically if you install with Synaptic).

KDE is a little closer to Windows in its look and feel, but Gnome is simpler.

---

### Post by TomTravis on 2008-07-26
Thanks everyone.  I am installing KDE now.

Tom Travis

---

### Post by TomTravis on 2008-07-26
I did the "sudo aptitude install kubuntu-desktop" and KDE seemed to install smoothly.  When I log out and back in, it takes me straight to GNOME without giving me a choice.  When I did the install with the above, I did select GNOME as my default desktop.  How can I make it switch, or what did I do wrong?

Tom

---

### Post by eightmillion on 2008-07-26
On the login screen, there should be a drop down box that says something like sessions or session type. You need to change that to KDE.

---

### Post by TomTravis on 2008-07-26
I told you wrong.  I actually did "sudo apt-get install kubuntu-desktop" if that makes a difference.

I'll log out again and look close to see what if any options I have.

Tom

---

### Post by TomTravis on 2008-07-26
It worked,  I am now in KDE.

Thanks,

Tom

---

### Post by eightmillion on 2008-07-26
No problem. Have fun. :)

---

### Post by hyper_ch on 2008-07-26
now install xubuntu-desktop ;)

---

### Post by ejpyle on 2008-07-26
> **TomTravis said:**
> I am a beginner at learning this linux stuff.  I've made attempts with slackware in the past and read a few books but did not seem to catch on, so I am trying it again.

I decided to dive into UBUNTU because I needed something to teach at a week long church computer camp for middle school kids that I volunteer at every year.  It is difficult to teach kids anything new about windows and the old computers we had would not run XP well so I decided we would all learn about UBUNTU together. It was amazing how fast the kids picked up UBUNTU after I took their windows away from them.

We loaded and ran UBUNTU with the GNU interface.  I've been reading about KUBUNTU and the KDE interface.  My question is, can I go from GNU to KDE and back, or do I have to boot into the KDE environment if I want to simply check out KDE?

Thanks for giving me a great OS to teach at my camp.

Tom Travis

I think KDE is great....it has a windows feel while Gnome has an OSX feel to it....only problem is that there are lots of bugs....

I just went back to Gnome from KDE because Dolphin has a bug where it generates an Amarok error when moving the mouse over HTML or XML files...there are only temp fixes for it and I am not to fond of those.

If you install the KDE desktop outlines in someone elses post you can switch between the 2 by clicking "sessions" at the login field though you will likely have cluttered menus.

---

### Post by RobbyemCee on 2008-07-26
> **TomTravis said:**
> It worked,  I am now in KDE.



I found KDE to be a little "choppy" and "laggy" when I installed it. Are you finding the same thing? Or is KDE running smooth for you?

-RobbyemCee

---

