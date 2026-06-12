---
title: "Brightness &amp; Lock settings not working"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by Curtis6767 on 2012-10-21
Did the upgrade to 12.10 this past Thursday and all my settings appear to have been saved, even my monitor settings for which I selected "Never" turn off.

However, after about 15minutes of inactivity my screen goes black and I have to move the mouse to get it to turn on.

I never had this problem when playing around with 12.10 from Alpha 1 through Beta 2.

What am I missing?

Thanks

---

### Post by NikTh on 2012-10-21
Hi , 
maybe this is related to gnome-screensaver and not Brightness & lock. 

Open a terminal and run this command 

```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
``` 

And see if your problem solved.

Thanks

---

### Post by Curtis6767 on 2012-10-21
NikTH,

Using the Unity interface so would this still apply?

Thanks

---

### Post by NikTh on 2012-10-21
Command is correct. Just tested in my VB Quantal. If will solve your problem , you will see it. (after 15 minutes of inactivity) 

Thanks

---

### Post by Curtis6767 on 2012-10-21
> **NikTh said:**
> Command is correct. Just tested in my VB Quantal. If will solve your problem , you will see it.

Thanks

Okay, thanks.

Get back later after running command and then waiting 15mins or so to see what happens.

---

### Post by Curtis6767 on 2012-10-21
> **NikTh said:**
> Hi , 
maybe this is related to gnome-screensaver and not Brightness & lock. 

Open a terminal and run this command 

```
gsettings set org.gnome.desktop.screensaver idle-activation-enabled false
```And see if your problem solved.

Thanks

I ran the command but nothing happened. Just went right back to the prompt. I waited anyway but 10mins later monitor went black.

I restarted the computer and ran the command again and again nothing happened and just went right back to the prompt.

Do I need to put  *sudo apt-get *in front of the command?

Or is this just not going to work?

Thanks

---

### Post by Curtis6767 on 2012-10-21
I went into Brightness & Lock and changed "Never" to "1 hour."

Still turns off after 10mins so this feature appears to be completely disabled on my system.

Thanks

---

### Post by ttbek on 2013-01-20
This definitely seems to be a bug, I haven't had a chance to test solutions yet though.  The two main ones I have seen are to do as the first respondent suggested and the second is the run:
 xset -s off
  which should turn off the screensaver.  If I open up the dconf Editor and the Brightness and Lock settings I can see that toggling Lock on and off toggles the corresponding org.gnome.desktop.screensaver lock-enabled setting, but changing Turn screen of when inactive for: to Never or to a time does not make any change to the org.gnome.desktop.screensaver idle-activation-enabled setting.  Running the command should have changed that setting for you (but as you said, there is no feedback on the command line that it was changed successfully.  You can check the current value with:
 gsettings get org.gnome.desktop.screensaver idle-activation-enabled

---

### Post by ttbek on 2013-01-21
Sorry, I need to correct myself, the command is xset s off not xset -s off.  This seems to have worked for me, I tried the other solution first and saw no change in behaviour.

---

### Post by ttbek on 2013-01-21
Nevermind, it's still not working for me either, it did it again overnight... this one is really obnoxious.

---

### Post by ttbek on 2013-01-21
Alright, after some further exploring, xset s off is the correct thing to do, but running that command does not allow for the setting to persist through a reboot.  There are two good options for setting this command, the first is for just your user, and the second is for all users, the second option requires root access.  

1.) Create a file in your home directory called .xprofile with the contents: 
xset s off
or append it to the end of the .xprofile file if it already exists, the default permissions on the file are fine, no need to muck about with adding the executable tag or anything.  

2.) Backup your xorg.conf:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
Add the following to the xorg.conf file (located in /etc/X11/): 
Section "ServerFlags"
    Option "BlankTime" "0"
EndSection

To add this, you can open the file using: 
gksudo gedit /etc/X11/xorg.conf
just add that text at the end and click save then exit gedit.  
If you already have a ServerFlags section in your xorg.conf, then you can just add the Option line in there.  
If you mess up your xorg.conf file, you will now have a backup that you can restore from the command line using sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf
If you forgot to back it up, you can delete the broken one: 
sudo rm /etc/X11/xorg.conf
and a new one should be generated for you on the next boot.  

Sources: 
[http://manpages.ubuntu.com/manpages/precise/en/man5/xorg.conf.5.html](http://manpages.ubuntu.com/manpages/precise/en/man5/xorg.conf.5.html)
[https://wiki.ubuntu.com/X/Config/SessionStartup](https://wiki.ubuntu.com/X/Config/SessionStartup)
[http://manpages.ubuntu.com/manpages/precise/en/man1/xset.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/xset.1.html)
Chat in channel #Ubuntu on the freenode server with jrib on 1/21/2013 (I believe there are searchable logs of the channel).

---

