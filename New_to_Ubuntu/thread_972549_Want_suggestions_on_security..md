---
title: "Want suggestions on security."
date: 2008-11-05
forum: New to Ubuntu
---

### Post by fullerama on 2008-11-05
As a new Ubuntu user, I'd like some input from more experienced people on security issues.

Are there any recommended programs to use for anti virus, malware, spyware, etc?

Your thoughts on what steps I should take to protect my computer and data are greatly appreciated.

And thanks to those who have responded to other dumb questions I've had as I enter the world of Ubuntu.  This is a great forum.

---

### Post by Paqman on 2008-11-05
There's a really good [secuirty thread](http://ubuntuforums.org/showthread.php?t=510812) written by Bodhi.Zazen over in the security forum.

In short:
[list]
[*] You already have a good firewall installed
[*] You don't need special anti-virus software
[*] Stay current with security updates
[*] Learn about file permissions
[*] Pick a strong user password
[*] Get all your software from the repos
[*] Be smart about using the internet
[*] Enjoy!
[/list]

---

### Post by Zzl1xndd on 2008-11-05
In my opinion a Virus/spyware/malware program is not needed.

Ubuntu has a good firewall built in if you would like to configure it I would recomend Firestarter. (you can get it from the add/remove)

---

### Post by kevdog on 2008-11-05
Firestarter is moving to be replaced with ufw and gufw (GUI for ufw).  If I were a beginner I would move to the ufw solution.

---

### Post by Thirtysixway on 2008-11-05
If you're going to be opening up anything like ssh or ftp to the world, I'd suggest getting the program "fail2ban".  It will ban IP addresses trying to break into your system, but this is probably not needed on a desktop system only a server system.

---

### Post by lovinglinux on 2008-11-05
If you are going to open ports for certain types of services, specially p2p, I would recommend [[COLOR="Red"]**moblock**[/COLOR]]("http://moblock-deb.sourceforge.net/") + [[COLOR="Red"]**mobloquer**[/COLOR]]("http://mobloquer.foutrelis.com/").

Using mobloquer gui to control moblock is very easy. 

You can find more info and support [[COLOR="Red"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=803183").

Moblock has also scripts for inserting and removing iptables rules when respectively starting/stopping the application. So, if you learn [[COLOR="Red"]**how to create your iptables rules**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=159661") you can use moblock to handle them and forget about gufw or Firestarter.

EDIT: I forgot to mention [[COLOR="Red"]**NoScript**[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/722") and [[COLOR="Red"]**AdBlockPlus**[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/1865") for Firefox.

---

### Post by fullerama on 2008-11-06
As usual, a wealth of information. Thank you all so much.

---

### Post by ./. on 2008-11-06
Tiger is definitely worth installing as it performs a check for compromises in system security.  Although some of its output can be confusing, it also serves as a good way to learn more about computer security.

---

