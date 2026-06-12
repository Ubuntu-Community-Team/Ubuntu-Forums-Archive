---
title: "Firefox Launcher No Longer Works"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by omron123 on 2008-11-07
Hi All,

I am VERY new to the Linux world. I was trying to install various plugins featured on the "get multimedia support" section of Xubuntu desktop guide. After I downloaded them, the screen changed to installing, changes taking effect, or something along those lines, and then it went gray and froze (much like MS windows does). I waited on it for a while, but eventually I grew fed up and restarted. When I logged back in, a window popped up which said something like "you do not have the authority to make changes" or something like that. Then I went to click on the firefox launcher icon and nothing happened. Again I tried to restart, but the problem remains, although the "you do not have the authority to make changes" message wasn't displayed. Can anyone tell me what happened/ how to fix this problem?

Thanks!

---

### Post by Yuki_Nagato on 2008-11-07
First, lets make sure Firefox still exists.

In a terminal,

```

cd /usr/bin
firefox

```

This should launch the actual Firefox application.  If that does not work, you have problems.

But you are new, so there should be other options.  Try rooting through XFCE's "start" menu to find the Firefox application and right clicking on it.  In "Properties" there should be some kind of command similar to "firefox" in the launcher.  If not, type it in.

What kind of system specs are you running?  If the computer was bought this century (meaning the BIOS are capable of running Linux easily.  They seemed to have changed in 2000) it should be able to support GNOME.  This is instead of XFCE.  Linux has many GUIs, and some are much easier on newbies.  GNOME and KDE are good to start with.  Either use Ubuntu straight up or Kubuntu.  XCFE, Enlightenment, and Blackbox are for people who like terminals and have little need for anything graphical.

Yes, I am suggesting you reinstall with either Ubuntu or Kubuntu.

---

### Post by jpeddicord on 2008-11-07
> **Yuki_Nagato said:**
> First, lets make sure Firefox still exists.

In a terminal,

```

cd /usr/bin
firefox

```


Just a nitpick: cd /usr/bin won't actually do anything; it's already on the system PATH. Run `which firefox` from any directory to see what I mean.

---

### Post by Yuki_Nagato on 2008-11-07
> **jacobmp92 said:**
> Just a nitpick: cd /usr/bin won't actually do anything; it's already on the system PATH. Run `which firefox` from any directory to see what I mean.

Not at all.  I was not considering the environmental variables.  Thank you.

---

