---
title: "Ubuntu 14.04 w Wine boot after power off ?"
date: 2015-05-25
forum: New to Ubuntu
---

### Post by Greg Mueller on 2015-05-25
For my weather computer....

Currently running XP on my weather computer (it's on 24/7). 
If I'm away from home and the power goes off, I have the BIOS set to reboot when the power comes back on and that starts XP and an app called **WUHU** which uploads data to Weather Underground.
One of the guys on the Yahoo **WUHU Users Group** says he can run WUHU under **Wine**.

So can Ubuntu 14.04 running Wine, be configured to start **Ubuntu-Wine-WUHU** automatically after the mains power has gone down and comes back up?

This is the only thing holding me back from the switch over to Ubuntu on that computer.

---

### Post by Vladlenin5000 on 2015-05-25
As a general rule, anything less than gold isn't worth trying. WUHU is silver... [https://appdb.winehq.org/objectManager.php?sClass=application&iId=13653](https://appdb.winehq.org/objectManager.php?sClass=application&iId=13653)
However, your own tests are what should matter (for you). Perhaps the guy who told you it can run uses only a subset of functions that happens to work fine under Wine. Hopefully those are the same functions you also need and no others.

I recommend you really test it before anything else. Then, if satisfied, it shouldn't be that hard to make it run on boot.

---

### Post by Greg Mueller on 2015-05-25
It's a very simple program at best. Just an uploader of info brought in to the computer on Comm 1 and out using a network cable to the router and on to Weather Underground

The real deal is that when I install my new weather station, I can use a program written for Linux. So if I can get this working I can graduate up at the right time.

---

### Post by grahammechanical on 2015-05-25
Ubuntu has a utility called startup applications (search for it in the Dash). That will let you set an application to start when Ubuntu loads. In theory the same command that launches this application under wine should also work in launching it as a startup application.

When we run an application under wine we do not launch wine and then launch the application. We just click an icon which runs a command and the application launches. So, it should work but it is not something that I have tested.

Regards.

---

### Post by Greg Mueller on 2015-05-25
Good info. thanks.

---

### Post by grahammechanical on 2015-05-25
Install Wine through the Ubuntu Software Centre and we get three utilities, Configure Wine; Uninstall Wine Software & Winetricks. Of all things we use Uninstall Wine Software to install the Windows application. That utility will give us an Add/Remove dialog with an Install button that leads to another dialog which will let us browse to the setup.exe file.

The installation of the application will put an icon on the desktop that will launch the application. Right click the icon and select properties and we can find out the command that is being used to launch the application and that is the command that should be used in Startup Applications.

Regards.

---

### Post by sandyd on 2015-05-25
You may also want to consider running it in a VM if it does not work with WINE. I've never tried it in virtualbox, but with virt-manager (KVM), you can map a physical COM port to a VM.

---

### Post by Greg Mueller on 2015-05-25
Thanks again
I am waiting for parts for the new (to me) computer which should arrive in the next few days and I can set it all up.
Once I get it running I can swap out computers. I don't want the weather station "down" and I hate being under pressure to make it go, specially when I don't know what I'm doing.
Hopefully the old XP system will keep on for just a bit longer.
[URL="http://www.datilcam.com/"]
Weather Page[/URL]

---

### Post by tristan16 on 2015-05-25
Ubuntu can indeed be configured to run Wine programs on startup. In the dash, search for Startup Applications. Add a new startup application with this code:

```
wine /start.exe
```

Replace "/start.exe" with the path to your program's executable file. After saving the entry, the program should now run automatically when the user logs in.

I use this for a program called BoincTasks. The main window of the program isn't visible until I click the icon again, but the program still launches on startup. You'll need to enable automatic login on your computer, otherwise the program won't start until someone logs in.

---

### Post by Greg Mueller on 2015-05-25
Neat!

I'll try it

Thanks!

---

