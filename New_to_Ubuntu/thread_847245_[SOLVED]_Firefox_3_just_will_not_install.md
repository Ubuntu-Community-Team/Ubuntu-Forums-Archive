---
title: "[SOLVED] Firefox 3 just will not install"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by nicknormal on 2008-07-02
Hi.
I've tried just about everything I can think of, or know, to install Firefox 3!
I'm on Ubuntu 8.04.
I've downloaded the .tar.bz direct from the mozilla site; I've tried installing it via Synaptic package manager; I've tried via apt-get in terminal. Nothing works!

I've attached a screenshot, all I get is this error window. If i hit restart, the error window keeps popping up. Don't know what to do. I've spent well over 2 hours reading threads, trying terminal commands. I absolutely cannot get Firefox 3 to install!

do you gurus have any further advice? or can I do something to give you a more-detailed error message?

thanks,
Nick

---

### Post by bumanie on 2008-07-02
FF3 was part of 8.04 updates about a fortnight ago, it should've installed then. If you have not had the update go to update manager and get it to check for updates. You should not need to install independantly.

---

### Post by nicknormal on 2008-07-02
my update manager says my system is up to date, but FF3 is nowhere to be found at the moment. if i COMPLETELY uninstall v2, and install v3, I get that error window.

---

### Post by aysiu on 2008-07-02
Go to System > Administration > Software Sources and enable (I think it's the second or third tab) the proposed updates, then click Reload when prompted.

Then go to System > Administration > Update Manager and check for updates. Install *only* the Firefox update (none of the other updates).

This should give you Firefox 3 final.

Afterwards going back to Software Sources and disable the proposed updates repositories.

---

### Post by kevmitch on 2008-07-02
There might be something in your old firefox 2 profile that's causing it to hiccup. Try starting the profile manager with

```
firefox firefox -ProfileManager
```

and creating a new profile. 

If that doesn't work, you can try moving your old profile out of the way temporarily

```
mv ~/.mozilla ~/.mozilla.bak
```

and try to start firefox again

---

### Post by kansasnoob on 2008-07-02
> **aysiu said:**
> Go to System > Administration > Software Sources and enable (I think it's the second or third tab) the proposed updates, then click Reload when prompted.

Then go to System > Administration > Update Manager and check for updates. Install *only* the Firefox update (none of the other updates).

This should give you Firefox 3 final.

Afterwards going back to Software Sources and disable the proposed updates repositories.

My Sotware sources looks like this and I've had no trouble getting stable FF3 updates:

[ATTACH]76150[/ATTACH]

[ATTACH]76151[/ATTACH]

[ATTACH]76152[/ATTACH]

---

### Post by nicknormal on 2008-07-02
aysiu,
none of that worked. it wouldn't find or list anything related to firefox as an available update!

kevmitch,
did both. all i could accomplish was having to make a new profile. i still get that error window!

kansasnoob,
yes i saw your images in another post. none of that seems to assist me though!

I really don't know what to do.

In synaptic package manager I can completely untick everything firefox related (see image below). Even then I still have an icon in /usr/bin for 'firefox'. there's also a folder at /opt/firefox - even though I've told synaptic to completely remove everything!

then if i fresh install, i STILL get that bloody error window!

in /usr/bin i have 3 firefox icons: firefox, firefox.ubuntu and firefox-3.0

if i double-click each of those, i'm asked if i want to display its contents or run, if i hit run, for the first i get that error window; the other two, firefox v3 actually runs!! I'm typing from it right now. but if i simply go to Applications->Internet->Firefox web browser I get that darned error window! I want to fix that!

hha. I don't know what else I can type or do! My install seems completely EFFed up!

---

### Post by nicknormal on 2008-07-02
in Terminal, if i type 'firefox' i get this error:

(crashreporter:6045): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

if i type 'firefox-3.0' it launches

does that error help any?

thanks!

---

### Post by bumanie on 2008-07-02
Look in synaptic at the broken packages and see if FF3 may have not completely downloaded. You will have to look at the boxes on the left - can't remember which one is for broken packages, presently on a windows computer, so i can't check.

---

### Post by aysiu on 2008-07-02
Can you paste these commands in the terminal and post the output back here? ```
ls /usr/bin/firefox -l
ls /opt
```

---

### Post by goforlinux on 2008-07-02
I had a problem kind of the same what i did was go back to an older edition of firefox and update gradually to version 3 idk it seemed to work?

---

### Post by nicknormal on 2008-07-10
> **aysiu said:**
> Can you paste these commands in the terminal and post the output back here? ```
ls /usr/bin/firefox -l
ls /opt
```

hi aysiu,
sorry so long to respond, had a J4 vacation (FF3 still doesn't work! hah!)

anyhow I get these terminal replies:

ls /usr/bin/firefox -1
/usr/bin/firefox

ls /opt
firefox  flash32  picasa  sunbird  sunbird-0.3a2.en-US.linux-i686.tar.bz2

does that help any?

cheers,
NN

---

### Post by aysiu on 2008-07-10
Please copy and paste the commands. Do not retype them. Less room for error. Less work.

It's an *-l*, not a *-1*

---

### Post by nicknormal on 2008-07-11
subtle.

ls /usr/bin/firefox -l
lrwxrwxrwx 1 root root 20 2006-12-22 11:30 /usr/bin/firefox -> /opt/firefox/firefox


ls /opt
firefox  flash32  picasa  sunbird  sunbird-0.3a2.en-US.linux-i686.tar.bz2

thanks for your assistance aysiu. cheers!
Nick

---

### Post by aysiu on 2008-07-11
Okay. This is what I want you to do.

1. Close all instances of Firefox, including any crash windows.

2. Paste this command into the terminal to get a fresh profile while backing up your old profile: ```
mv ~/.mozilla ~/.mozilla.backup
```

3. Let's get you a fresh sources.list, too, just to be safe: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
gksudo gedit /etc/apt/sources.list
``` In the new Gedit window that opens, paste this in: ```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hardy universe
deb-src http://archive.ubuntu.com/ubuntu hardy universe

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted

deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe

deb http://archive.ubuntu.com/ubuntu hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy multiverse

# deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

# deb http://archive.canonical.com/ubuntu hardy partner

# deb http://packages.medibuntu.org/ hardy free non-free 
``` Then save and exit Gedit.

Let's make sure we get updates on what's available: ```
sudo apt-get update
``` 4. Let's remove the Mozilla version of Firefox. ```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
``` 5. Let's remove Firefox 2 ```
sudo apt-get remove firefox-2
``` 6. Let's make sure Firefox 3 is installed ```
sudo apt-get install firefox-3.0
``` 7. Now let's launch Firefox and see what's up: ```
firefox &
```

---

### Post by nicknormal on 2008-07-23
aysiu,

thanks so much. I now have FF3 running.

However, I have encountered another bug of sorts: I am the sudo account on this machine; I share it with a coworker. his FF3 launches via Applications->Internet->Firefox without a hitch. when I do this, it says 'Starting Firefox Web...' on the taskbar, but then that disappears. if in terminal, and I type 'firefox' I get the same instance. 'firefox &' only works to launch FF3 if I have previously typed in my sudo password.

is there a way to fix that link so simply clicking the icon will launch FF3 for me (sudo)?

and thanks again. it is working, it is faster, it is more secure. wow. thanks!

---

### Post by nicknormal on 2008-07-23
additionally if i close the instance of terminal that launched FF3, FF3 closes.

---

### Post by billgoldberg on 2008-07-23
Hover you mouse above applications and right-click it.

Select "edit menu".

Search for the firefox mention.

Edit it and in the command box put "firefox &".

Close the app and try again.

--

I'm not on gnome right now, so I can't be more detailed.

---

### Post by aysiu on 2008-07-23
> **nicknormal said:**
> 
However, I have encountered another bug of sorts: I am the sudo account on this machine; I share it with a coworker. his FF3 launches via Applications->Internet->Firefox without a hitch. when I do this, it says 'Starting Firefox Web...' on the taskbar, but then that disappears. What command is in the menu item for Firefox? Right-click on the menu and select *Edit Menu*, navigate to the menu item, and double-click it to see the command. > if in terminal, and I type 'firefox' I get the same instance. 'firefox &' only works to launch FF3 if I have previously typed in my sudo password. Does it resolve to the next line or just hang? In other words, do you see this? ```
username@ubuntu:~$ firefox


``` or do you see this? ```
username@ubuntu:~$ firefox
username@ubuntu:~$
``` And what do you mean about *firefox &* working only if you type your sudo password? So you see this? ```
username@ubuntu:~$ firefox &
password:
``` You actually get prompted for a password to launch Firefox?

---

### Post by decoherence on 2008-07-23
quick tip... since we're in the terminal anyway he can also do this to find out the firefox command.

```
grep Exec ~/.local/share/applications/firefox.desktop
```

nice, clean, copy/paste-able output...

---

### Post by nicknormal on 2008-07-23
hi aysiu,

> **aysiu said:**
> What command is in the menu item for Firefox? Right-click on the menu and select *Edit Menu*, navigate to the menu item, and double-click it to see the command.

firefox %u

is the command field.

> **aysiu said:**
> You actually get prompted for a password to launch Firefox?

I'll attempt to clarify:

clicking Applications->Internet->Firefox Web Browser gives me the taskbar "Starting Firefox Web..." which subsequently disappears.

if in terminal, and NOT logged in as sudo, my terminal reads
```
nicknormal@normalbox:~$
```

if here i type 'firefox' nothing happens, i merely get another terminal line.

if here i type 'firefox &' i get this just now:
```
[1] 7201
nicknormal@normalbox:~$
```
(note: the 4-digit number is always different)
(this does not launch firefox)

at this point, if i type 'sudo -s' and enter my sudo password, I am returned with:
```
root@normalbox:~#
```

if here, i type 'firefox' it launches firefox3 but does not produce another line in terminal, it simply blinks cursor on the next line. it doesn't give me further terminal command in other words.

if as root@normalbox:# i type 'firefox &' it gives me
```
[1] 7341
root@normalbox:~#
```
and launches firefox3 and gives me another line of terminal from which to enter another command.

thus, to clarify, i do not get PROMPTED for a password to launch firefox, but seem to only be able to launch firefox from terminal after entering my sudo password!

thanks again for your assistance.

cheers,
Nick

---

### Post by aysiu on 2008-07-23
I think having run ```
sudo -s
``` has screwed up something with your permissions.

If you ever need to run a root terminal, run ```
sudo -i
``` And if you ever need to launch Firefox as root (which you should never need to, now that you're using the repositories version), run ```
gksudo firefox
```

The problem is that *sudo -s* gives you a root login but uses your user environment. *sudo -i*, on the other hand, gives you a root login but uses root's environment.

So probably something in your home directory changed ownership to root when you were making changes or launching Firefox from the *sudo -s* terminal.

Try pasting these commands in the terminal (close all instances of Firefox first, and do not log in as *sudo -s* or *sudo -i*; just use your normal login): ```
sudo chown -R nicknormal:nicknormal /home/nicknormal
firefox &
``` Then see if Firefox launches.

---

### Post by nicknormal on 2008-07-23
aysiu,

that has done it!

firefox now launches from the applications menu, from the panel icon, and from terminal without a hitch.

i can say to this point that i can actually interpret your terminal commands, but it's not yet my aptitude to come up with those commands, so this has helped me better understand some operations.

you can officially consider this thread closed!

THANKS!
nick

---

### Post by aysiu on 2008-07-23
Glad it worked out for you.

Next time you see someone recommend the use of ```
sudo -s
``` make sure to break out [the wet noodle.](http://www.diclib.com/cgi-bin/d1.cgi?l=en&base=amslang&page=showid&id=3592)

---

