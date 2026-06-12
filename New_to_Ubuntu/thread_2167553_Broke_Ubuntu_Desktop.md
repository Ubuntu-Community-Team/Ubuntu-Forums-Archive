---
title: "Broke Ubuntu Desktop?"
date: 2013-08-14
forum: New to Ubuntu
---

### Post by clementchiew on 2013-08-14
I decided to dabble around with desktop environments recently and I think Unity is not taking very well. I installed Gnome 3 (along with its weird display manager), Cinnamon and LXDE and then tested them (using apt-get install). When when I logged into Unity, it started to freeze almost every time I clicked on the launcher or just about anything. Also, right-clicking the desktop does  not bring up the context menu anymore. So I tried removing them using apt-get remove. oddly, I managed to remove cinnamon and gnome 3 but not LXDE. the terminal says there are no more packages installed when I use apt-get remove lubuntu-desktop but i still can boot in lubuntu desktop. and in fact, LXDE is not freezing up like Unity. Oh and one more thing, all the desktop environments are still available to boot into when i click at the ubuntu icon (but of course, i can log into Unity and LXDE). Help me please. I just wanted to test stuff and messed up things I don't know. Here are the commands I used:

sudo apt-get install gnome-shell
sudo apt-get install cinnamon
sudo apt-get install lubuntu-desktop

sudo apt-get remove gnome-shell
sudo apt-get remove cinnamon
sudo apt-get remove lubuntu desktop

---

### Post by TheFu on 2013-08-14
The best way to test out a new DE is by creating a new account and testing only inside that. The concern is that settings are used for slightly different things between each DE and sometimes, similar settings can cause a conflict.

So, to get out of DE-testing jail, create a new user account and use that for just 1 of the DEs.  You can search and find the settings for each DE under the HOME for each user.

---

### Post by mastablasta on 2013-08-14
> **clementchiew said:**
> I sudo apt-get remove gnome-shell
sudo apt-get remove cinnamon
sudo apt-get remove lubuntu desktop


wrong way. here is how you return to gnome (example): [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

what now? it might be good to somehow remove all desktop completely and then install the one you want.

another option is reinstall (with no formating).

---

### Post by clementchiew on 2013-08-15
thanks. I believe reformatting is always the last option. :D I shall try fixing it with that link.

---

### Post by mastablasta on 2013-08-15
reinstall of the OS can be doen without reformating. leaving data intact.

---

### Post by PocketDog on 2013-08-15
Everyone's done it. I was clearing out all of my unwanted DEs recently, and I removed gnome-session which, of course, killed unity. Next time I logged in I had a login to a recovery console and that was it.
 I had a couple of minutes of panic before I realised what I'd done

---

### Post by TheFu on 2013-08-15
> **PocketDog said:**
> Everyone's done it. I was clearing out all of my unwanted DEs recently, and I removed gnome-session which, of course, killed unity. Next time I logged in I had a login to a recovery console and that was it.
 I had a couple of minutes of panic before I realised what I'd done

You act like wiping Unity is a bad thing? ;)
Just be ready to run either another DE or a pure WM if that happens.

```
$ sudo apt-get install lxde
```
can make everything better, but you still might want to login using a new account. You can take over the old account or mv all the data over easily, just avoiding the DE settings.

---

### Post by clementchiew on 2013-08-16
how?

---

### Post by clementchiew on 2013-08-16
I feel like keeping LXDE actually. much better performance even if my computer isn't really that weak. how do i move the data while avoiding the DE settings?

---

### Post by clementchiew on 2013-08-16
Sounds like my situation here. Then how did you fix it?

---

### Post by TheFu on 2013-08-16
> **clementchiew said:**
> I feel like keeping LXDE actually. much better performance even if my computer isn't really that weak. how do i move the data while avoiding the DE settings?

From the new account, 
* mv all the data from the old account over (use **sudo** then **chown**)
* start using it.

I would type something like this into a terminal:

```
cd
sudo mv ~oldaccount/* ~/
sudo chown -R newaccount.newaccount *

```
This will leave all hidden directories - which is where settings are stored - alone.  A hidden file and hidden directory is just a file or directory that begins with a . (period).

If you want to understand what those commands are doing, read the man page for each - **man sudo**   and **man chown** are good reading. Understanding about man pages is a critical skill.  99.9999% of commands are documented in this way. At first, quickly reading a man page took me some time. Then something clicked and there really isn't anything better for understanding the tools on your computer.  You can even use google to find man pages, but those may not be for the exact version of the tool installed on your system. Beware.

---

