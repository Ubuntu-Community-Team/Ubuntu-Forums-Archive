---
title: "Install and mount a JungleDisk"
date: 2007-02-03
forum: Outdated Tutorials &amp; Tips
---

### Post by pauwl on 2007-02-03
Right, got the installation done on a clean Ubuntu 6.10 machine.
For those of you who want a mounted drive, here's what you need to do:

+++++++++++++++++++++++++++++++++

goto [http://www.jungledisk.com](http://www.jungledisk.com)
Download JungleDisk for linux

Extract the files to your HOME drive

Open a terminal window, run the following:

sudo ln -s /usr/lib/libcrypto.so.0.9.8 /usr/lib/libcrypto.so.0.9.7
sudo ln -s /usr/lib/libssl.so.0.9.8 /usr/lib/libssl.so.0.9.7

Now configure the JungeDisk by running './jungledisk'
The two important keys you need here are:

Access Key: <<You get this from Amazon when you've created an account on S3>>
Secret Access Key: <<You also get this from Amazon>>

If you want to encrypt your files, you'll need to add the AWS key in another tab.

You're now ready to test it all out.
* To connect to your Jungle Disk in KDE, just open a Konquerer window and type "webdav://localhost:2667/".
* In GNOME select "Connect to Server" under the "Places" menu. Set the Service type to "WebDAV (HTTP)". Enter "localhost" for the server and "2667" for the port.

You'll be able to add & edit most things, but sometime (e.g. with GIMP), it doesn't work by double-clicking, and you get an error that the file cannot be found. For this, you need to mount the drive....

So now we do that. First of all, if you made a connection to the WebDAV, unmount it (from the file explorer, right-click it, and select UNMOUNT)

Create a directory under your home directory called 'MyJungleDisk'
Now we need to add some stuff in the /etc/fstab file.
Open a terminal window.
type 'sudo -i'
This gives you a terminal in ROOT mode.
type 'gedit /etc/fstab'
Add the following line to the /etc/fstab file...
[http://localhost:2667](http://localhost:2667) /home/<my user name here>/MyJungleDisk davfs nolocks,user,noaskauth 0 0

Now, this will mount, but won't work unless jungledisk is running, so... I need to add './jungle' to my automatic startup.
In Gnome I go to System..Preferences..Sessions, and in the 'Startup Programs' tab I add '/home/<my user name here>/jungledisk'

Now you need 'davfs2' installed. Go to the Synaptic packet manager, search for 'davfs2', and you'll see it appear. Mark for installation, and install.

Reboot...and...

You're off, a mount should show up on your desktop. Have fun!



KNOWN ISSUES:
I've noticed in Gnome, the Jungledisk tray icon does not show on the normal panel, but just below it (top left of screen for me). Strange.
At each reboot you'll also get : 'Deleted stale lock file '/home/<my user name here>/JungleDiskMonitor'.' as an error. This is because jungledisk doesn't shut down properly, but is 'forced' to when you re-boot. Maybe it a workaround will come....

---

### Post by tashazo on 2007-03-06
thanks for this guide.
I followed it except I made a directory "jungledisk" under /mnt/
and used that for the line in fstab.
It didn't work.
I have davfs2 installed as well as the startup.  When I rebooted jungledisk was running but no mounted folder showed on my desktop.
Do I really need to create a separate folder IN HOME?  Or is it that I have to configure jungledisk to put the data there?  I'm surely missing something.
I don't think I understand mounting well...  I don't understand the empty directory thing.

---

### Post by tashazo on 2007-03-06
when I use:

mount.davfs [http://localhost:2667](http://localhost:2667) /mnt/MOUNTPOINT -o nolocks

to manually mount the volume (I put my dir 'jungledisk' for 'mountpoint'), the volume shows up on my desktop but I cannot access any of the files when I click on it (error message) with "Sorry, couldn't display all the contents of "jungledisk"."
Any ideas?

---

### Post by sricketts on 2008-09-30
Thanks for the instructions. They worked fine on one of my ubuntu desktops... then on the other one, running 
```
./jungledisk
```
does not start the configuration. It just terminates without any output.

Any suggestions?

Thanks,
Scott

---

### Post by Crafty Kisses on 2008-09-30
Nice tutorial, thanks! :D

---

### Post by sricketts on 2008-10-06
> **sricketts said:**
> Thanks for the instructions. They worked fine on one of my ubuntu desktops... then on the other one, running 
```
./jungledisk
```
does not start the configuration. It just terminates without any output.


Whoops, that should have been ./junglediskmonitor -- configuration successful.

---

### Post by koset on 2008-12-30
Works like a champ! Thanks!

---

### Post by alkh3myst on 2010-01-09
Does this also work in 9.10? Here, have some popcorn...:popcorn:

---

