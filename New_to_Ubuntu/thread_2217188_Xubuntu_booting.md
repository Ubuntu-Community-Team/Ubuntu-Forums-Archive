---
title: "Xubuntu booting"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by cchardonnens on 2014-04-16
Hi I want it to try Xubuntu and did a instal using the terminal with my ubuntu and typed this command " sudo apt-get install xubuntu-desktop "
 the install went on  but when I rebooted  it show xubuntu screen  and change to ubuntu login and when I shut it down it does with xubuntu screen where did i go wrong?
thanks 
Claude

---

### Post by kurt18947 on 2014-04-16
I have Ubuntu-gnome installed and added XFCE4 (not XFCE-desktop).  I see the same thing, the XFCE splash screen on shutdown while using gnome-shell so I'm not sure you did anything wrong.  It may just be how it works.

---

### Post by cchardonnens on 2014-04-16
What I like to do is try the xubuntu and see the difference  so far it give me xubuntu splash screen and   keep directing me to Ubuntu login

---

### Post by nerdtron on 2014-04-16
So what do you want to do? You want the original Ubuntu login screen and splash screen?
```
sudo dpkg-reconfigure lightdm
```
or try it with xfwm4 or kdm if using lightdm fails.
basically you'll be asked to change which login screen you want to choose.

---

### Post by coldcritter64 on 2014-04-16
> **cchardonnens said:**
> What I like to do is try the xubuntu and see the difference  so far it give me xubuntu splash screen and   **keep directing me to Ubuntu** login

When you come to where the Ubuntu log-in is selected, try clicking the logo beside "Ubuntu", it should offer you other selections for logging in to on a drop down menu. 

Xfce should be selectable from this menu, you need to change the session, done once the log in screen should then "remember" your new selection, xfce.

---

### Post by cchardonnens on 2014-04-16
Thanks, that is working. What would be the command if I want to unistall Xubuntu ?

---

### Post by coldcritter64 on 2014-04-16
> **cchardonnens said:**
> Thanks, that is working. What would be the command if I want to unistall Xubuntu ?

```
sudo apt-get remove xubuntu-desktop
```

**or **

```
sudo apt-get purge xubuntu-desktop
```

will remove xubuntu-desktop. Using the purge option also removes any left over system config files for the package. 

xubuntu-desktop, being a meta-package, once removed may leave behind a lot of packages no longer needed. If any unneeded packages are left behind and the terminal or update manager show them for auto-removal, use in a terminal.

```
sudo apt-get autoremove
```to them clean out. At this stage you should be back to your original state.

---

### Post by cchardonnens on 2014-04-16
Thanks a bunch

---

### Post by cchardonnens on 2014-05-07
I done it but still the xubuntu splash screen comes on when i boot and shut down

---

### Post by coldcritter64 on 2014-05-22
> **cchardonnens said:**
> I done it but still the xubuntu splash screen comes on when i boot and shut down

Sorry that I missed this post for so long. If you still have the xubuntu splash screen and want to get the ubuntu one back you need to run a couple of commands to update initramfs. "initramfs" has entries in it to show the plymouth boot screen, as plymouth (the splash screen) operates prior to the OS being fully loaded.

First run the command in terminal
```
sudo update-alternatives --config default.plymouth
```
Then input the number for Ubuntu as listed in the output and press enter.

Next run the command,
```
sudo update-initramfs -u
```
That will update the currently used kernel; If you have more than one kernel you need to change this for,
 ```
sudo update-initramfs -u -k all
```
will redo all your installed kernels at once.

Reboot the machine, but note the xubuntu screen will show on the way out, Ubuntu splash will show on the way back in as the new initramfs is used.
I don't know how I missed your last post, once again sorry for the long delay in responding. 

Regards, coldcritter64.

---

