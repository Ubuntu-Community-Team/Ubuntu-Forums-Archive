---
title: "Infrared (IRDA) Sync with Palm OS Devices HOWTO"
date: 2006-08-14
forum: Outdated Tutorials &amp; Tips
---

### Post by fheinsen on 2006-08-14
Three steps:

1. The most important step: Make sure that your computer's infrared (IR) port is enabled!  This is usually done by restarting your PC and hitting a key such as F2 to enter the setup screen *before* the PC starts booting up.  Also, make sure you set your Palm device to synchronize over its IR port!  The following instructions will not work if your PC and your Palm device are not properly configured.

2. Once you have confirmed that your computer's IR port is enabled and your Palm device is set to sync over IR, restart Ubuntu, login, open a terminal screen, and type the following in it:

```
sudo apt-get install irda-utils
sudo modprobe ircomm_tty
sudo echo ircomm_tty >> /etc/modules
``` 
3. Run your Palm sync utility (for example, if you synchronize with Evolution, you would click on Edit -> Synchronization Options) and set it to use '/dev/ircomm0' instead of '/dev/pilot' for communicating with your Palm device.

That's all there is to it.  You should now be able to point your Palm device to your computer's IR port and hit the sync button.  (This how-to has worked on a range of ThinkPad and Dell notebooks, but, as with all other how-to's in these forums, there can be no guarantee that it will work with your particular computer model.)[SIZE=2]
[/SIZE]

---

### Post by em3raldxiii on 2006-08-14
It should be noted that the key may not be F2 - some computers require hitting Del, F10, F11, F12.  There may be others.  Either way, you are entering your BIOS and finding your Infrared (IR) port settings and making sure that it's enabled.  Also note that just because you've enabled it doesn't mean it will work:  If you don't have an IR device, you're hooped.

---

### Post by marwal on 2006-10-02
i've got no ircomm_tty only ircomm-tty and
sudo echo ircomm-tty >>/etc/modules
gives permission denied

---

### Post by em3raldxiii on 2006-10-03
Mmm ... just a wild shot here, but have you tried to chmod your permissions on that file?

```

sudo chmod 777 /etc/modules

```

Note that this will make that file totally and completely unsecure.

Now do your echo command.

Finally, return the modules file back to it's original setting (232) which allows very limited access to the file, so as to prevent potential system vulnerabilities.

```

sudo chmod 232 /etc/modules

```

---

### Post by Carlos Santiago on 2006-11-14
In dual boot case, if it work on Windows you shoulnt need to check the BIOS, right?
Besides this BIOS check, I think I have tried all this commands (I am not with the laptop with me at the moment). 
I have an Acer TravelMate 4150, with a SMC IrCC Infrared port.

What I most need is to transfer files between mobile<->laptop via Infrared.
What program should I use?

I will try again today evening.
Thx for the HOWTO

---

### Post by funkenstein on 2007-01-19
[quote=em3raldxiii]sudo chmod 777 /etc/modules[/quote]
umm... yea, you probably want to do ```
sudo -s
echo ircomm_tty >> /etc/modules
exit
```

Ofcourse, this doesn't mean that it worked for me :confused:
ach well, carry on looking, ey?

---

### Post by bartman on 2007-01-24
Carlos Santiago:

I found on my notebook which also has an infrared solution by SMC that IR was already properly configured but that there was no program which would do the actual sending and receiving of files. After i installed **ircp** (short for InfraRed CoPy i guess) I have been able to send and receive files from and to my phone!

To see if infrared is already configured, try sending a file to your computer and after it fails run *$ cat /proc/net/irda/discovery* to see whether the computer actually picked up anything. Here's my output:```
bartman@nw8240:~$ cat /proc/net/irda/discovery
IrLMP: Discovery log:

nickname: F500 series, hint: 0x9124, saddr: 0x20e3865b, daddr: 0x00003791
```
You can even try pinging the device with *$ sudo irdaping <daddr>*.

This is how you use ircp:
* sending a file: *ircp <filename_to_send>*
* receiving a file: *ircp -r*

Thanks go to tedrogers for giving me a hint in a thread about [IRDA on IBM Thinkpads]("http://www.ubuntuforums.org/showpost.php?p=1753177&postcount=4").


If you want a graphical interface to ircp try ircp-tray ([ircp-tray homepage]("http://gro.clinux.org/projects/ircp-tray") with only source code for latest version 0.7, [official Chinese Gnome site]("http://www.gnome-cn.org/software/ircp-tray") with a .deb for version 0.6.1).
I haven't been able to get version 0.7 compiled but judging by the screenshot it provides a handy interface for our needs.

---

### Post by penno on 2007-02-17
Worked for me, thankyou!

Treo 650 <--> Asus W3N

---

