---
title: "HOWTO: Load Firestarter (Firewall) when session starts."
date: 2005-04-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Nano on 2005-04-13
These two simple steps will allow you to start Firestarter (Firewall) automatically right after you login. (Only for Gnome.)

My system is entirely in Spanish so some translations might not be correct.

First of all, since Firestarter requires sudo privileges to be started, we will add it to /etc/sudoers:

```

export EDITOR=gedit && sudo visudo

```

and add the following string at the bottom:

```

username ALL=NOPASSWD:/usr/sbin/firestarter

```

where "username" is YOUR OWN user name.

Now let's add it to the session.
Open "System->Preferences->Sessions" and click the tab "Start up programs" (the last). 
Click the "Add button" and add the following string:

```

gksudo /usr/sbin/firestarter

```

This is all. Next time you start

---

### Post by XDevHald on 2005-04-13
If you log out of X and notice it says: **"You must have root privilages to run FireStarter" **then you need to se the order for the program to run in. 


Do this by going to:

System > Preferences > Sessions > Startup Programs 

And set the order of it to **20**. If this doesn't work, check your User Group privilages and see if you're set in the **admin **also known as **adm **in your user groups settings.

Great work Nano! helped a lot :D

---

### Post by pseudonym on 2005-04-16
You would do this only to autoload the Firestarter GUI upon login, right? Because according to the Firestarter documentation ('Persistence of the Firewall') it should load during bootup and run 'in the background'. A message about starting Firestarter appears during startup, plus you can run 'sudo /etc/init.d/firestarter status' to check that it's running. Unless it's not running the way it should if you don't have the GUI enabled?....

---

### Post by Nano on 2005-04-16
[QUOTE=pseudonym]You would do this only to autoload the Firestarter GUI upon login, right? Because according to the Firestarter documentation ('Persistence of the Firewall') it should load during bootup and run 'in the background'. A message about starting Firestarter appears during startup, plus you can run 'sudo /etc/init.d/firestarter status' to check that it's running. Unless it's not running the way it should if you don't have the GUI enabled?....[/QUOTE]
 That's right, it's to load the Firestarter GUI.
I always run it minimized to monitor when I have recurring hits from suspicious ips in order to black list them.

---

### Post by bored2k on 2005-04-18
Note: for those wanting to start FS minimized, add this to ur sessions startup:
gksudo /usr/sbin/firestarter --start-hidden (instead of gksudo /usr/sbin/firestarter)

[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

---

### Post by NateC on 2005-04-19
I simply use "sudo firestarter" and it starts up fine with no problems when I login.

---

### Post by optik on 2005-06-12
Huh.... Isnt that a tad insecure? Making it so that your user doesnt have to use a pass for sudo?

---

### Post by bored2k on 2005-06-12
[QUOTE=optik]Huh.... Isnt that a tad insecure? Making it so that your user doesnt have to use a pass for sudo?[/QUOTE]
 No. You're just making firestarter not use sudo. Everything else still needs it.

---

### Post by Lunde on 2005-07-01
[QUOTE=pseudonym]You would do this only to autoload the Firestarter GUI upon login, right? Because according to the Firestarter documentation ('Persistence of the Firewall') it should load during bootup and run 'in the background'. A message about starting Firestarter appears during startup, plus you can run 'sudo /etc/init.d/firestarter status' to check that it's running. Unless it's not running the way it should if you don't have the GUI enabled?....[/QUOTE]
 The internet connection sharing does not work until the gui is started. Strange...

---

### Post by mulperi on 2005-08-26
Isn't firestarted actually only a GUI for iptables?

I read somewhere that by modifying the kernel you could get pop-up windows when some application tries to "call home" in the background. Does anyone have a clue on how to do this?

//mulperi

---

### Post by squid on 2005-10-14
Hello ubuntu freaks ;)

I think that my firestarter does not work!!!

I have tried all the ways you post here but...i get the error all the time.... 

my username name is science and is on science group... i have tried to put this username to admin groups but still the same errros :(

Some times when i login to gnome i get no error but when i see gnome sessions i see this :

see the attached file.

[www.datalabs.ws/Screenshot.jpg](www.datalabs.ws/Screenshot.jpg)

is this normal ?

Anything else to try?

THanks for your time ;)

---

