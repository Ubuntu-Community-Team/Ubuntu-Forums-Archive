---
title: "Keyboard Layout Indicator Not Present in  12.10"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by riderplus on 2012-12-26
That's right. I read and read this bug [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1045914...no](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1045914...no) help. I added the PPA, updated...nothing happened. No indicator. I can't switch between layouts.

---

### Post by squakie on 2012-12-27
The link goes to the "not found".

I assume you've already checked system settings, keyboard and pressed the "+" key?

---

### Post by riderplus on 2012-12-27
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1045914](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1045914) This one...of course I went to System Settings, Keyboard, and pressed +. But the layout button doesn't show up in the top panel.

---

### Post by squakie on 2012-12-27
Am I assuming correctly that you want the layout to show as per my attachments?  I'm using 12.10.  I go to system settings/keyboard, then highlight the key layout even if it is the only one, then just click the little keyboard icon in the bottom left set of icons on the screen.  Are you saying that icon doesn't show?

---

### Post by riderplus on 2012-12-27
Firstly, there is no problem in Unity DE (and you are using Unity, I am using GNOME 3, as you could have noticed if you had accessed that bug report link I've posted) and absolutely no problem in Gnome Classic DE for Ubuntu 12.10 when it comes to showing the keyboard layout indicator in the top panel. Secondly, it's the Keyboard Layout **Indicator** in the top panel in **GNOME 3** shell that I'm saying it doesn't show up (the "en" should show up in the top panel in GNOME 3 shell when multiple layouts are chosen, which allows one to switch to a different layout, be it "fr", i.e. French, or "ru", i.e. Russian).

---

### Post by squakie on 2012-12-27
Since the bug report (which I DID read) doesn't mention a solution that has worked for everyone on this problem, might I suggest you post there (in a new thread as mentioned in the thread) instead of posting here for support on something that is clearly broken?

And by the way - using Gnome Shell as indicated in the thread results in the same exact screen captures - not safe to assume.

---

### Post by riderplus on 2012-12-29
I also posted in that bug report. Now what? Wait for the GNOME 3 team to fix it? Maybe in 2013...

---

### Post by squakie on 2012-12-29
Unless you want to dig in and patch it yourself, the answer would be yes.  In the mean time, you still can change layouts, just not at the click of a button on the task bar.

---

### Post by riderplus on 2012-12-31
Well, not even that...GNOME 3.7.3 on 12.10 crashes when I try to change the Keyboard Layout via System Settings...it doesn't open the Layout Options  when I switch to it in Keyboard Settings...the same behaviour if I click on Region & Language - nothing opens., just an advice to send the crash report to Ubuntu. How cool is that?

---

### Post by grahammechanical on 2012-12-31
The release notes for Ubuntu 12.10 Gnome Remix has this to say under Known Issues:

> Keyboard layout doesn't show in GNOME Shell top bar (1045914). You can use the GNOME3 PPA to get the updated System Settings which fixes this.

It does not fix it in my Gnome Remix but I have changed it into 13.04 Gnome Remix and it is very unstable now. Closing an application/utilty window will freeze the desktop.

And, yes, we have no choice but to wait for Gnome to fix many things. All the Ubuntu developers can do is pass the bug reports upstream and wait and see.

Regards.

[https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10")

---

### Post by riderplus on 2013-01-06
GNOME 3.7.3 does not crash anymore, because I started using xorg-edges ppa. But the Keyboard Layout Indicator is still not there. I'm wondering how long does it take to fix such a stupid bug.

---

### Post by riderplus on 2013-01-08
I upgraded to 13.04 and the Indicator reappeared, now the issue is this: the Romanian Layouts (as they are 8) are THE SAME, there is NO difference between Romanian, Romanian (standard), Romanian (cedilla), Romanian (standard cedilla) etc. It's only one Layout no matter if I change to standard or cedilla. This is totally ERRONEOUS. What is wrong with the GNOME 3 developers? GNOME 3 has become regressive. 

To be more sarcastic, I have to point out another thing: Unity DE has no Keyboard Layout Indicator in Ubuntu 13.04. That's right! They managed to bring back the Indicator for gnome shell, and failed to keep the one in Unity DE. This is simply fantastic, surreal or whatever you want to call it! Why are they stuck in such minor issues? Amazing!

---

