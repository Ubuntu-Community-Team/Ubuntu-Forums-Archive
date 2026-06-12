---
title: "gnome-keyring:: couldn't connect to...pkcs11"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by MickW on 2013-02-13
Hi All

Newbie here!  

Just installed Lubuntu 12.10 on an old HP pc and so far I love it!

Had a little problem though and would like to ask for some help... yesterday I couldn't boot so I looked around on line and found a way to repair the fault using the live CD and a command in the terminal which worked and got me back up and running okay except for the fact that I can't seem to run Pan newsreader.  When I try to start the program in the Terminal I get this error message:

WARNING: gnome-keyring:: couldn't connect to: /run/user/*/keyring-15CAgg/pkcs11: No such file or directory
GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name news.pan.NZB was not provided by any .service files
**
ERROR:pan-tree.cc:80:GtkTreeIter PanTreeStore::get_iter(const PanTreeStore::Row*): assertion failed: (row)
Aborted (core dumped)

I would be very grateful for any suggestions on how to sort this problem out!

TIA

MickW

ps obviously without the smilies!!!

---

### Post by DuckHook on 2013-02-13
> **MickW said:**
> Hi All

Newbie here!  

Just installed Lubuntu 12.10 on an old HP pc and so far I love it!

Had a little problem though and would like to ask for some help... yesterday I couldn't boot so I looked around on line and found a way to repair the fault using the live CD and a command in the terminal which worked and got me back up and running okay except for the fact that I can't seem to run Pan newsreader.  When I try to start the program in the Terminal I get this error message:

```
WARNING: gnome-keyring:: couldn't connect to: /run/user/*/keyring-15CAgg/pkcs11: No such file or directory
GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name news.pan.NZB was not provided by any .service files
**
ERROR:pan-tree.cc:80:GtkTreeIter PanTreeStore::get_iter(const PanTreeStore::Row*): assertion failed: (row)
Aborted (core dumped)
```I would be very grateful for any suggestions on how to sort this problem out!

TIA

MickW

ps obviously without the smilies!!!

Welcome to the forums. Hope that you will find Lubuntu an enjoyable experience.

Firstly, a helpful observation: by enclosing output in code tags, you make it much easier to read. Just highlight the output and use the code button (hash (#) mark) at top of box. I've done so in my reply and you can see that the output is much easier to parse and the smilies are gone.

Re: gnome-keyring

This is a known and very irritating bug in the default Lubuntu install. I have filed a bug report on it with Launchpad. If you would also file one, the developers may assign it higher fix priority.

The workaround/fix is [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/1077289").

---

### Post by MickW on 2013-02-14
xxx

---

### Post by MickW on 2013-02-14
Hi DuckHook

Thanks for the posting tips and the link - I am enjoying my Lubuntu experience so far but tbh I am contemplating a move across to Ubuntu as I feel like I might be missing out on a few goodies!

btw how do I file a bug report on Launchpad?!

So I followed the instructions i.e. 

1. Do:


 sudo apt-get install libpam-gnome-keyring
 
2. Logout

3. Login

but the expected pop-up for unlocking the default keyring did not  materialise and I still can't open Pan. Oddly enough I set up another  use profile with administrator privileges and it opens up okay when I  log in to that profile?!!

Any other suggestions would be really welcomed

All the best

MickW

---

### Post by DuckHook on 2013-02-14
If you will be installing another flavour, then it makes no sense trying to fix this one.

Regarding that move: although Ubuntu does indeed have more goodies (I use it myself), it requires a reasonably modern box with much higher minimal HW specs, else you won't enjoy the experience. If your HW is beyond a certain age, it won't even run. Among Linux enthusiasts, the increased power requirements from Lubuntu to Ubuntu is well known. So before installing, you must make sure that your HW can handle it. In terms of practical functionality, Lubuntu is capable of running everything Ubuntu can. What's lacking is the eye-candy like spinning desktop cubes and fading windows--all of which are 3-D special effects. You mention that you are running all of this on an "old HP PC". Without knowing details, it is impossible to tell, but I would recommend a minimum of duo core CPU, 2GB RAM, 3-D video chip with discrete 512 MB Video RAM to run Ubuntu. If your system does not meet these standards, I don't think you will be happy with the performance.

---

### Post by MickW on 2013-02-14
Well this old machine is nowhere near that spec so I guess I'll stick with Lubuntu for the time being - it is doing everything I need it to do (well it was) so I ain't complaining - just the newsreader issue really!!!

Also doesn't Ubuntu come with freenet already configured and ready to go?  That would be the only other thing I would like to get up and running.

MW

---

### Post by DuckHook on 2013-02-14
Back to fixing your Pan login, then.

1. Do:```
sudo apt-get update
sudo apt-get install seahorse
```...to get Seahorse, the wrapper GUI app that manages passwords and keys.

2. Find and open Seahorse. It will not be called Seahorse in your system menu, but "passwords and keys".

3. Under passwords, there should now be two keyrings: one called Login, the other called default. If no default, then we must create one. If exists, then does Pan Newsreader show up on right side pane?

4. If not, File>New> and choose "Stored Password"

5. In resulting dialogue box, make sure Keyring is "default", description is "Pan Newsreader" and Password is your password. Double check and if everything is correct, click "Add".

6. Close all windows. Logout/login.

Post back with results.

---

### Post by cmathisson on 2013-02-16
Hi I have the same problem but it show up when i try to start weechat-curses (ncurses IRC client). I have tried all the steps you provided to solve the problem this far but I still get the same error message.

chris@chris-Aspire-5230:~$ weechat-curses
WARNING: gnome-keyring:: couldn't connect to: /run/user/chris/keyring-Ktb00t/pkcs11: No such file or directory

I have installed libpam-gnome-keyring
but didn't get any message when I logged in again.

then I tried with installing seahorse.
when i opened "passwords and keys" I only had the Login key, so i added the default one, sat it to default and added the password and checked unlock at boot, still not working :/

anything more i could try?

/Chris

---

### Post by DuckHook on 2013-02-16
> **cmathisson said:**
> anything more i could try?
 
Are you operating weechat in a terminal or under one of the other full ttys?

---

### Post by MickW on 2013-02-17
Hi DuckHook

Thanks for the message

Just downloaded the Seahorse application but I can't find it anywhere on the system!!!

Sorry am a bit new to this  :rolleyes:

---

### Post by cmathisson on 2013-02-17
I run weechat in the terminal on my computer :)

MickW: look for "passwords and keys" in your preferences meny

---

### Post by DuckHook on 2013-02-19
Sorry for the slow response. Don't know what happened, but never got notified of your responses and I unsubscribe from threads if I don't see activity in the last 48 hrs.

I may be chasing the wrong car here. Please see [this]("http://ubuntuforums.org/showthread.php?t=2065461") thread, especially last post #7.

---

### Post by MickW on 2013-02-21
Hi DuckHook

I don't know what Openbox is or how to use it...

I tried editing** /etc/xdg/autostart/gnome-keyring-pkcs11.desktop** by appending *;LDXE* to it, and this might have worked (it seems to have solved the problem for lots of others), but I don't have write permissions.  Is there a way you could tell me to create the necessary permissions to give this a go?

Thanks and regards

MickW

---

### Post by DuckHook on 2013-02-21
A brief background on use of sudo/gksudo:

One of the best features of Linux over other OSes is that you operate in a lower security level for daily use. Therefore you (or malicious SW) cannot change system files without taking deliberate steps to elevate your security level. This is one of the reasons Linux doesn't need anti-virus. Since everything in the /etc directory is a system file, you need to temporarily elevate your security level to root in order to change any of its files. We do this with the sudo command, or its graphical equivalent, gksudo. Simply by prepending this additional command to your desired command will invoke the app with root privileges, and this will allow you to make the changes you want. So, if using the command line editor,```
sudo nano /etc/xdg/autostart/gnome-keyring-pkcs11.desktop
```If using the graphical editor,```
gksudo leafpad /etc/xdg/autostart/gnome-keyring-pkcs11.desktop
```For more info on Ubuntu security, [this]("https://wiki.ubuntu.com/BasicSecurity") is a worthwhile read. For more advanced info, try [this]("http://ubuntuforums.org/showthread.php?t=510812").

---

### Post by cmathisson on 2013-02-22
it seams like the problem is solved :D,

I am trying to get a program to auto start, when i stumbled upon:
preferences => Desktop session settings
and in the list I found that "Certificate and key storage" wasent checked so i checked it and did a reboot now everything is working

so the steps that seams to help:

sudo apt-get install libpam-gnome-keyring
and check "Certificate and key storage" in preferences => Desktop session settings

thanks for all help

---

### Post by DuckHook on 2013-02-22
> **cmathisson said:**
> it seams like the problem is solved :D,

I am trying to get a program to auto start, when i stumbled upon:
preferences => Desktop session settings
and in the list I found that "Certificate and key storage" wasent checked so i checked it and did a reboot now everything is working

so the steps that seams to help:

sudo apt-get install libpam-gnome-keyring
and check "Certificate and key storage" in preferences => Desktop session settings

thanks for all help

Your problem may not have been with pkcs. I'm happy that you solved your problem, but in future, it is a good idea to start your own thread for exactly this reason. Happy Ubuntuing!

---

### Post by MickW on 2013-03-05
tried the edit but no workee!

did I mention that I could get pan to start in a newly created user profile?

---

