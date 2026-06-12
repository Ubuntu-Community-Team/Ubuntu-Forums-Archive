---
title: "No menus/toolbars showing"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by toonamitom on 2012-12-19
Hi,
I'm using a newly purchased laptop to try Ubuntu. Because I don't want to risk anything with my machine, I'm using Virtualbox. So I downloaded Ubuntu tonight and installed it in VB, but now that it's installed, I can't use it. No toolbar is displaying. All that's on my screen is the wallpaper. Help, please?

Furthermore, an even stranger problem is happening. After a few minutes of "use" (i.e. me fiddling with trying to take a screenshot and it disabling the function by capturing my keyboard) the VM turns off. Shuts down without reason.

Below is a picture of the screen in scaled view. It looks the same in full screen view. Just to clarify: I can use the Virtualbox menu-- it's the Ubuntu menu that isn't displaying.

[IMG]http://i.imgur.com/1Nz4E.png[/IMG]

---

### Post by sahabcse on 2012-12-19
Click alt+F2.

If you get a terminal, run


sudo apt-get install gnome desktop

---

### Post by toonamitom on 2012-12-19
> **sahabcse said:**
> Click alt+F2.

If you get a terminal, run


sudo apt-get install gnome desktop

Hm, it didn't work. I'm going to reinstall it with more RAM. Maybe something went wrong during the install.

---

### Post by zombifier25 on 2012-12-19
Have you installed the Guest Additions and enable "3D acceleration" in your guest? Instructions: [http://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-virtualbox/22745#22745](http://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-virtualbox/22745#22745)

---

### Post by toonamitom on 2012-12-19
> **zombifier25 said:**
> Have you installed the Guest Additions and enable "3D acceleration" in your guest? Instructions: [http://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-virtualbox/22745#22745](http://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-virtualbox/22745#22745)

I tried that. Still nothing :/

Edit: Also, a window comes up telling me "the application Compiz has closed unexpectedly."

---

### Post by toonamitom on 2012-12-19
> **sahabcse said:**
> Click alt+F2.

If you get a terminal, run


sudo apt-get install gnome desktop

I got a terminal open with another shortcut-key ctrl-alt-t but when I ran the command I got the attached error.

Edit: I googled around did sudo apt-get update first, and then tried to install gnome desktop and it said 
"ubuntu-desktop is already the newest version."

Edit x2: If anyone reads this, my problem was with Compiz and Unity. I tried reinstalling them but was given the error that my hardware wasn't supported. So I ditched Unity and installed the gnome-session-fallback. Details here: [http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-gnome-session-fallback](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-gnome-session-fallback)

Cheers

---

### Post by pqwoerituytrueiwoq on 2012-12-19
i suggest you try a live cd/usb and see if it works, Virtualbox is not a good way to test hardware compatibility

---

### Post by sahabcse on 2012-12-19
May I know your laptop configuration?

---

### Post by toonamitom on 2012-12-20
> **sahabcse said:**
> May I know your laptop configuration?

HP ENVY m6 Notebook PC
Intel Core i5-3210M CPU @ 2.5GHz
8GB RAM, 64-bit OS

I followed a number of leads on Google but none of the solutions helped. Anyway, Unity over the classic Gnome desktop isn't that much of a loss I'm guessing, and I use Windows primarily.

---

