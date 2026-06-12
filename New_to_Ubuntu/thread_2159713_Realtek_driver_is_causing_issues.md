---
title: "Realtek driver is causing issues"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by Coffed on 2013-07-04
I recently purchased a ZyXel NWD2205 Wireless N USB Adapter for my system because it was missing a WLAN card.
It went smoothly on my win7 OS, but apparently I haf to install the rtl8192CU driver for my ubuntu OS. So I searched for it and found the firmware-realtek package which should include said driver.

After I've installed the firmware-realtek package from this link[SUP]1[/SUP], many applications and features of ubuntu stopped working.
So far, I've noticed that the command 'sudo' no longer works (gives no output at all), the app nautilus no longer starts and the network settings cannot be accessed anymore.

As soon as I click on 'network' in System Settings, the program freezes for a short moment and gives me the error message "The System network services are not compatible with this version".

Before I installed the package, everything worked fine. I've also had the exact same problem before. I solved it by reinstalling the entire system.

But now, I don't really want to reinstall everything again. Has anyone a solution, a tip or even the same problem? I would be glad for answers.

[1] -> [http://packages.debian.org/sid/firmware-realtek](http://packages.debian.org/sid/firmware-realtek)

[I]Additional information
OS: Ubuntu 13.04
Architecture: i386
Everything else works. If you need more information about my system, feel free to ask.
A photo, taken from my iPad camera, of the current situation can be found here: [https://www.dropbox.com/s/6ll5q2wjgyreovt/2013-07-04%2011.18.45.jpg](https://www.dropbox.com/s/6ll5q2wjgyreovt/2013-07-04%2011.18.45.jpg)


[/I]P.S: Sorry for the bad language, but I'm swiss and english is not my primary language.

---

### Post by coldraven on 2013-07-04
I don't know the answer but it may help if you change the title of the post. Maybe "Realtek driver breaks system" and add tags "Realtek" "Network" and so on.

---

### Post by Coffed on 2013-07-11
[FONT=arial][COLOR=#222222]Alright, so here's an update:

I have reinstalled the system once more and am now avoiding this driver.
For some reason, the exact same thing happened on my laptop, which runs on ubuntu 13.04 64-bit and has a working wlan card, as soon as I plugged in the adapter.

Therefore my problem has been "solved". However, I will avoid this adapter and its driver to prevent further issues. The fun thing is: The live-usb installer detected the adapter but could not connect to any wireless networks because a 'hardware switch' is blocking it.

My advice: Do NOT install the driver unless you know what you're doing. (Or maybe I was just too stupid to correctly install it)

P.S: Thank you for your reply, coldraven![/COLOR][/FONT]

---

