---
title: "Ink levels for Epson Stylus DX4000 ?"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by gorby928 on 2011-10-29
Hi all
Does anyone know of an application that will show me my ink levels for my Epson Stylus DX4000 ?
I have cups+gutenprint driver installed and that doesnt support ink levels.
I also tried epson inkjet printer -escpr 1.1.0-1lsb3.2(seiko epson corporation LSB3.2) and that doesnt show ink levels either?
Im low on ink but which one is anyones guess :confused:

---

### Post by Mark Phelps on 2011-10-29
I would recommend either mtink or ink, but I've installed both in 11.10 and, unlike in 11.04 where they both work great, NEITHER of them work in 11.10.

---

### Post by ajgreeny on 2011-10-29
> **Mark Phelps said:**
> I would recommend either mtink or ink, but I've installed both in 11.10 and, unlike in 11.04 where they both work great, NEITHER of them work in 11.10.
Do you know if that is due to the change to to gnome/gtk3, or is it just the ongoing problem of successfully running mtink?

It always took me some time to get mtink to work in previous versions of ubuntu, even after adding myself to the lp group (I think it was lp), and it seemed always to take many attempts to get communication between the printers and mtink, though once it was made, it worked brilliantly.

I don't have any Epson machines to test it now, but I'm just curious, for future reference.

---

### Post by verymadpip on 2011-10-29
escputil worked well for me in 10.10.  Install it & run: sudo escputil -i -r /dev/usb/lp0
It may be worth a shot.

I dodged 11.04 so I can't comment on that.

Unfortunately escputil isn't working for me in 11.10.  It tells me there is no such file or directory.  If I change the command a little (leave out "usb") it tells me the resource is temporarily unavailable.

Not such a happy camper today :(

---

### Post by gorby928 on 2011-10-30
Hello again,
Well I installed mtink & mtinkc (them came together) and it seems to work :p thank you all.I also downloaded **escputil** to see what that was like but I cant find it even when the software centre tells me its installed ? Thanks once again:p

---

### Post by arvevans on 2012-01-18
**mtink**, **mtinkc**, and **ttink** all seem to be broken if you have a USB connected printer.  They only let you talk to serial or parallel port printers.
[B]
escputil[/B] appears to work in 11.10 with my Epson CX7400 all-in-one connected via USB.  For later model printers you do have to use the "-u" option.

---

### Post by Mark Phelps on 2012-01-18
mtink DOES work in 11.10, even for USB-connected printers.

It's just that with 11.10, you have to load a kernel module -- one that was loaded by default in previous Ubuntu versions.

Sorry, not at my Linux box, so I don't have that info, but I will check later tonight and update this thread.

---

### Post by Mark Phelps on 2012-01-18
The mods closed my other thread, so I can't update it as promised ...

What is needed to get mtink to work with an Epson printer connected via USB is the following:
1) open a terminal and enter "sudo modprobe usblp"
2) edit the file /etc/modules and add a line containing "usblp" (without the quotes)
3) Reboot

After that, mtink will work.

---

### Post by linubun on 2012-02-20
> **Mark Phelps said:**
> The mods closed my other thread, so I can't update it as promised ...

What is needed to get mtink to work with an Epson printer connected via USB is the following:
1) open a terminal and enter "sudo modprobe usblp"
2) edit the file /etc/modules and add a line containing "usblp" (without the quotes)
3) Reboot

After that, mtink will work.


hello, sorry for my English.
 I am new to linux and I can not see the ink level of Epson Stylus DX4450.
 Click "sudo modprobe usblp" in the terminal and nothing happens.
 If I edit according to step 2) and restart mtink does not recognize the port.
 Someone could tell me how to fix it?
 thank you very much
SO linux mint12 64bits

---

### Post by hybenz on 2012-02-20
> **Mark Phelps said:**
> mtink DOES work in 11.10, even for USB-connected printers.

It's just that with 11.10, you have to load a kernel module -- one that was loaded by default in previous Ubuntu versions.

Sorry, not at my Linux box, so I don't have that info, but I will check later tonight and update this thread.
mtink does not seem to work in all USB-connected printers..

[[FONT=Trebuchet MS][SIZE=1][COLOR=White]ink[/COLOR][/SIZE][/FONT]]("http://www.inkjetsuperstore.com/")_______
:KS:KS:KS

---

### Post by philinux on 2012-02-20
> **Mark Phelps said:**
> The mods closed my other thread, so I can't update it as promised ...

What is needed to get mtink to work with an Epson printer connected via USB is the following:
1) open a terminal and enter "sudo modprobe usblp"
2) edit the file /etc/modules and add a line containing "usblp" (without the quotes)
3) Reboot

After that, mtink will work.

Excellent , marvellous. How did you find that?
Epson r200 ink levels again on 11.10.

[edit] Except printer wont print now. :confused:
I used sudo rmmod usblp to get printer back.

---

### Post by linubun on 2012-02-20
I put this in the terminal and nothing happens.
 I do something wrong?
"nix@amd /etc $ sudo modprobe usblp
[sudo] password for nix: 
nix@amd /etc $ sudo rmmod usbl
ERROR: Module usbl does not exist in /proc/modules
nix@amd /etc $"
 
While the file is edited?
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
usblp

thanks for your answers

---

### Post by philinux on 2012-02-21
> **linubun said:**
> I put this in the terminal and nothing happens.
 I do something wrong?
"nix@amd /etc $ sudo modprobe usblp
[sudo] password for nix: 
nix@amd /etc $ sudo rmmod **[COLOR="Red"]usbl[/COLOR]**
ERROR: Module usbl does not exist in /proc/modules
nix@amd /etc $"
 
While the file is edited?
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
usblp

thanks for your answers

The steps to get this work around is this. 

Install mtink and gksu gedit /etc/group and add yourself to lp

You may have to logout login for the change to take place.

```
sudo modprobe usblp

```
Now that does not produce any output but now mtink should work and show ink levels but printing is now blocked.

```
sudo modprobe -r usblp
```
or sudo rmmod usblp and now printing is unblocked.

---

### Post by linubun on 2012-02-21
> **philinux said:**
> The steps to get this work around is this. 

Install mtink and gksu gedit /etc/group and add yourself to lp

You may have to logout login for the change to take place.

```
sudo modprobe usblp

```Now that does not produce any output but now mtink should work and show ink levels but printing is now blocked.

```
sudo modprobe -r usblp
```or sudo rmmod usblp and now printing is unblocked.


install mtink
gksu is already installed on my system according to the software manager
edit /etc/group: "lp:x:7:username"
reset
run in terminal "sudo modprobe usblp"
mtink run: >/dev/lp0> other printer
get the following message:
"communication problems with the printer ... etc".
run in terminal "sudo modprobe-r usblp"
mtink run and does not work
run "sudo rmmod usblp" and I returned the following error: "ERROR: Module usblp does not exist in /proc/modules
edit/etc/modules and add the line "usblp".
reset
mtink run and still not working.
As a workaround I installed windows xp in virtualbox and printer software to work properly.
Thanks for your interest

---

### Post by philinux on 2012-02-21
> **linubun said:**
> install mtink
gksu is already installed on my system according to the software manager
edit /etc/group: "lp:x:7:username"
reset
run in terminal "sudo modprobe usblp"
mtink run: >/dev/lp0> other printer
get the following message:
"communication problems with the printer ... etc".
run in terminal "sudo modprobe-r usblp"
mtink run and does not work
run "sudo rmmod usblp" and I returned the following error: "ERROR: Module usblp does not exist in /proc/modules
edit/etc/modules and add the line "usblp".
reset
mtink run and still not working.
As a workaround I installed windows xp in virtualbox and printer software to work properly.
Thanks for your interest
That should be a command.
```

gksu gedit /etc/group
``` and add yourself to lp

or just run

```
gksu mtink
```

---

### Post by linubun on 2012-02-21
> **philinux said:**
> That should be a command.
```

gksu gedit /etc/group
``` and add yourself to lp

or just run

```
gksu mtink
```

Terminal gksu gedit /etc/group
edit group: "lp:x:7:nameuser"
terminal respons:
(gedit:3108): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.LKAAAW': No such file or directory

(gedit:3108): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
gksu mtink: "problems with the printer communication..."
thanks

---

### Post by Mark Phelps on 2012-02-21
You need to create a file named .mtinkrc in your $Home directory, containing the following:

```
BROWSER: 
AUTODETECT: no
MINIHELP: yes
PRINTER: Stylus Photo R200
PORT: /dev/usb/lp0
```

Change the PRINTER to match your model and change the PORT to match yours.

Once you do that and reboot, enter "sudo mtink" in a terminal, and it will find the printer and display the ink levels.

Notice I used "sudo" not "gksu".

---

### Post by linubun on 2012-02-22
> **Mark Phelps said:**
> You need to create a file named .mtinkrc in your $Home directory, containing the following:

```
BROWSER: 
AUTODETECT: no
MINIHELP: yes
PRINTER: Stylus Photo R200
PORT: /dev/usb/lp0
```Change the PRINTER to match your model and change the PORT to match yours.

Once you do that and reboot, enter "sudo mtink" in a terminal, and it will find the printer and display the ink levels.

Notice I used "sudo" not "gksu".


Sorry, I do not get it to work.
 I would have to reinstall the system because I have changed many things and I am lost.
 Thank you very much for your answers

---

