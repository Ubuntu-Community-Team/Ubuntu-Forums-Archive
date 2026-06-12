---
title: "Noob needs help with..."
date: 2008-08-01
forum: New to Ubuntu
---

### Post by papabill on 2008-08-01
Having been a captive WinDoze user, I am unfamiliar with most of the ways to run programs in Linux (Ubuntu 8.04). I see that the programs I want are loaded, but cannot find the executables (or if I can find them, I don't know how to run them.)

Help????

---

### Post by dca on 2008-08-01
If it's GNOME Ubuntu, (not KDE Kubuntu) most apps install under the 'Applications' area of the main menu bar...
 
Which app in particular are we talking about?  All of them?

---

### Post by papabill on 2008-08-01
It's GNOME Ubuntu, and even though it says that phpbb and phpmysqladmin are loaded, I cannot find them or their GUI setup programs.

---

### Post by phidia on 2008-08-01
Some programs don't have menu shortcuts available. You can still open them by opening the terminal (Applications> Acessories> Terminal) and typing the program name or easier still press Alt + F2 and type the name in the box that pops up.

---

### Post by Vadi on 2008-08-01
Those programs run on a server, and are accessible via a browser... try going to "localhost" in firefox.

---

### Post by Paqman on 2008-08-01
In Linux, you don't need to find the executable to run the app. If it has a GUI it should have added itself to the menus. If not, just open a terminal and type in the name of the package. Linux is clever enough to launch it just from that.

---

### Post by michaelaly on 2008-08-01
PHPMySQLadmin is available under the 'Programming' menu. Go to System -> Preferences -> Menus and check the box next to 'Programming'. This enables the submenu and it will then display under 'Applications'.

PHPbb requires a web server(Apache), and is accessed through a browser, it does not have an executable(binary) file.

---

### Post by papabill on 2008-08-01
> **Vadi said:**
> Those programs run on a server, and are accessible via a browser... try going to "localhost" in firefox.

Nope, no go. But that's not unusual for the luck I'm having. Nothing there except an (empty) "apache2-default" directory.

---

### Post by papabill on 2008-08-01
> **michaelaly said:**
> PHPMySQLadmin is available under the 'Programming' menu. Go to System -> Preferences -> Menus and check the box next to 'Programming'. This enables the submenu and it will then display under 'Applications'.

Again, nope. Not there.

---

### Post by Vadi on 2008-08-01
Sorry, but I think you're confusing something here. I didn't even find "phpmysqladmin" in synaptic or add/remove.

Usually, you just launch progams from the "Applications" menu. Like Applications - Accessories - Calculator. Or Applications - Internet - Firefox Web Browser, and so on.

I hope that answers your questions on how to run the programs in Ubuntu.

---

### Post by papabill on 2008-08-01
> **Vadi said:**
> Sorry, but I think you're confusing something here. I didn't even find "phpmysqladmin" in synaptic or add/remove.

Goofy me!! :oops:

I meant "phpmyadmin'. I got it installed, but cannot figure out how to get to it to do anything. It also doesn't show up in the /var/www (public html) directory.

---

### Post by kansasnoob on 2008-08-01
"I installed it, but where did my program go?"

[http://monkeyblog.org/ubuntu/installing/#where_did_it_go](http://monkeyblog.org/ubuntu/installing/#where_did_it_go)

---

### Post by Vadi on 2008-08-01
Go to "http://localhost/phpmyadmin/" in firefox, that should work.

---

### Post by papabill on 2008-08-01
Great, thanks. That did it.

---

### Post by Vadi on 2008-08-01
No problem. In the future, I recommend googling "*problematic program name* ubuntu". Ubuntu forums have a lot of threads by now and you can pretty much find all solutions to your issues that way - in fact, I did just that for this and the first result gave that solution.

(you'll just save yourself a lot of time next time ;))

---

