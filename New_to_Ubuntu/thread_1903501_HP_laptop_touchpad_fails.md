---
title: "HP laptop touchpad fails"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by Muscogulus on 2012-01-02
I installed Ubuntu 11.0.4 for the first time on an HP Pavilion DV6000. The version is now 11.0.10. The touchpad does not work with either version. 

There were no touchpad issues when the laptop ran Windows Vista. The touchpad worked during installation, but failed the moment the login screen appeared. It also failed when I rebooted from the install disc. 

I cannot move the cursor at all and I cannot enter text or select a text field with the keyboard. 

I wiped the drive and installed on a single partition. The hard drive is healthy. 

I followed the steps described at[Debugging Touchpad Detection]("https://wiki.ubuntu.com/DebuggingTouchpadDetection"). I found the documentation confusing and internally contradictory, but did establish that the problem is *definitely* not a bug in the kernel and *probably* not a bug in X server. However, the command 

```
xinput --list
```

gives the result **Unable to connect to X server**

Using a USB mouse I am able to log in and use the OS normally. But the installation is crippled without the touchpad. 

I made the mistake of posting this query to a thread flagged as [SOLVED], where it died. I am now feeling vexed and am about ready to give up on Ubuntu.

---

### Post by lechien73 on 2012-01-02
Hi,

Sorry to hear about the frustration. I have heard that, on some installations, the touchpad is disabled on startup.

To check this, please press Alt+F2 and type:

```
dconf-editor
```

in the command field.

When dconf-editor is open, navigate to: **org -> gnome -> settings-daemon -> peripherals -> touchpad**

If the box with the label **touchpad-enabled** is unchecked, then check it. If that was the problem, then it should now work without having to reboot.

---

