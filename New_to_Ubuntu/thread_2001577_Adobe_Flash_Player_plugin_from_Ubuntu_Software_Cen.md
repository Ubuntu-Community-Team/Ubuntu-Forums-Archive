---
title: "Adobe Flash Player plugin from Ubuntu Software Center"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Bob Saget on 2012-06-11
I am trying to install it, among other things since I just started Ubuntu this morning.  It's stuck at around 75% saying "Applying Changes"  It has been that way for the past hour, and I can not cancel it to let my other queued items start installing.  I am in need of some help with this as I really can't wait for the other items which are software updates and an antivirus program.

---

### Post by fantab on 2012-06-11
Flashplayer plugin takes a bit of time to install. If nothing happens restart Ubuntu and try again.

But first you must: Open TERMINAL or Ctrl+Alt+T and run the following command:

```
$ sudo apt-get update
```

---

### Post by Bob Saget on 2012-06-11
it says "command not found" heh.   Should I just go ahead and restart ubuntu?

---

### Post by forrestcupp on 2012-06-11
Were you trying to install it from the Software Center? Sometimes when you install proprietary software from the Software Center, it gives you a window where you have to click a button to accept its license agreement. But for some reason, it pops that window up *behind* the installation window where you can't even see it. So you have to move windows around to see the license agreement so you can accept it and finish the installation.

A lot of times when you're installing proprietary software and the installation stops at a late percentage for a long time, that's what it is.

---

### Post by David Andersson on 2012-06-11
> **fantab said:**
> 
```
$ sudo apt-get update
```

> **Bob Saget said:**
> it says "command not found" heh. 

If it said "bash: $: command not found", then try again without an initial "$".

---

### Post by Bob Saget on 2012-06-11
I restarted Ubuntu and that cleared it all out.  I then found google chrome has flash built-in, so as long as I use chrome, I can't think of anywhere else I'd need it.  Thanks for the support though.  I shall now continue my adventure  through linux.  It's a breath of fresh air from Windows, for sure.

---

### Post by Oesipower on 2012-06-11
> **Bob Saget said:**
> I am trying to install it, among other things since I just started Ubuntu this morning.  It's stuck at around 75% saying "Applying Changes"  It has been that way for the past hour, and I can not cancel it to let my other queued items start installing.

I have the exact same problem. I could ignore it, but when i want to update ubuntu, it always gets stuck with downloading flash player...
So now it's impossible for me to update ubuntu...
I already ran "sudo apt-get update" and restarted the computer, but it's still not working -.-

---

### Post by deadflowr on 2012-06-11
I always just install the package Ubuntu-restricted-extras. It installs a bunch of stuff including flash,mp3, and other close-source media codecs. Like forrestcupp said, pay attention cause at some point you might need to answer a question during the install.
After that, if you have any problems running flash in firefox, just go to the addon place for firefox and add flash-aid. Flash-aid will check and fix any issues firefox has with your flash components.

---

### Post by Oesipower on 2012-06-11
The funny thing is, that flash player works now, but the more serious problem i have is that i can't update, because it always gets stuck, because it wants do download flash player for some reason. I have already installed flash player manually, but ubuntu still tries to install it, although it's already working. The problem is: Flash is working and updating not. So, how can I delete flash player and install it the right way or stop ubuntu from trying to install flash player when updating?

---

### Post by fballem on 2012-06-11
Assuming that you use Chrome and you are happy with it, then flash will work. There is another option for those who use Firefox. If you open Firefox, then Tools | Add-ons, you can install the Flash-aid add-on.

Once installed, it will remove the existing Flashplayer if any, and correctly install the flash player from the Adobe website.

I've been using this for the better part of a year and it has proven very reliable. If Adobe releases an update (which isn't often these days) then Flash-Aid will alert you and allow you to install the update.

Just in the interest of providing another option.

---

### Post by deadflowr on 2012-06-11
> **Oesipower said:**
> The funny thing is, that flash player works now, but the more serious problem i have is that i can't update, because it always gets stuck, because it wants do download flash player for some reason. I have already installed flash player manually, but ubuntu still tries to install it, although it's already working. The problem is: Flash is working and updating not. So, how can I delete flash player and install it the right way or stop ubuntu from trying to install flash player when updating?

You should start your own thread as your problems are different from the OP's. You manually installed flash. The OP can't get the flash-plugin installation working right.Two different problems.

---

