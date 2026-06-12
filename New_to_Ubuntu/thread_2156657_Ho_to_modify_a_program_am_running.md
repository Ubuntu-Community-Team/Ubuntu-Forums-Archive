---
title: "Ho to modify a program am running ?"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by Innernet on 2013-06-22
Hi.
Am using a program "linSSID" that displays the signal strenght of WiFi channels on range.
It is now set for autoexecuting at startup, but:
-Is requesting my 'authentication' password to run, and
-It needs then to click on the "Run" button.

How can these two actions be changed to be not required, so it just runs automatically ?

I suppose the program lines could be edited, but do not enough on how to find/bring them to screen and what parts to edit and then save the altered program.

Please guide me in simple terms, am not an expert.

---

### Post by Lars Noodén on 2013-06-22
I can't find the program in the Ubuntu repostories, did you download it from somewhere else?

Be that  as it may, if you know the path to the program, you can make a special entry for it in /etc/sudoers  
For example if the program is in /usr/local/bin then you could add the following line to [url=
https://help.ubuntu.com/community/Sudoers]sudoers[/url]

```

%innernet   ALL=(ALL) NOPASSWD: /usr/local/bin/linssid ""

```

That assumes that the program name is linssid and that it takes no parameters when run.  

You can edit /etc/sudoers with nano

```

sudo cp -i /etc/sudoers /etc/sudoers.orig
sudo nano -w /etc/sudoers

```

---

### Post by Innernet on 2013-06-22
Thanks.
The program linSSID 2.0 for i386 was downloaded from here, and works well :

[http://sourceforge.net/projects/linssid/](http://sourceforge.net/projects/linssid/)

---

### Post by Lars Noodén on 2013-06-22
It looks like a useful program.  I really needed a program like that last month.

You can try modifying sudoers as above but use the path */usr/bin/linssid* instead.

---

### Post by ajgreeny on 2013-06-22
You could also try command ```
sudo chmod u+s /usr/bin/linssid
```which will allow you as user to run the executable.

This is a trick that is needed to allow a user to run executables such as vnstat as user rather than root in conky.

---

### Post by warsev on 2013-06-23
Hi, I'm the developer of LinSSID.

LinSSID is not normally run with 'root' priviliges. I deemed that too risky. I don't want beta quality code continuously running on my machine, and hopefully you don't either. LinSSID itself NEVER runs with root privileges unless the user launches it with root priviliges; which is highly discouraged. Instead, LinSSID askes for a password and uses it ONLY to launch instances of tried-and-true system utilities like iw and iwlist. That's much safer.

An 'autorun at launch' preference could be added to eliminate the need to click the 'run' button. Or perhaps LinSSID could accept a command line argument to autorun. I'll noodle on that.

Leaving LinSSID running continuously is not such a great idea. First, it keeps the WiFi chipset running in scan mode which takes quite a bit of time during which the chipset can't be servicing other requests. Second, it can burn up a chipset. I had it happen to a dongle yesterday during some testing. Scan mode seems to take a lot of power, and the thermal design of most dongles is not so hot (pardon the pun).

A final note: Please download releases of LinSSID only from [the project page on sourceforge]("http://sourceforge.net/projects/linssid/") or from [the ppa on launchpad]("https://launchpad.net/~wseverin/+archive/ppa"). Versions from other sources could possibly be modified to include malicious code.

---

### Post by Innernet on 2013-06-23
Thanks for your guidance and good performing program, Warren.

If at some point refinements are implemented, real-time data speed monitoring in each direction would be on my wish list.  :)

---

