---
title: "Sharing a USB HD with XP"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by nimsu on 2008-11-03
I have a USB drive connected to my ubuntu box. I want to share the drive so I can copy movies from my Win XP machine to the USB drive while it's connected to the ubuntu box. How can I do so?

If I right click on the drive, there is no share option

I tried creating a folder in the drive and sharing that, but I get some samba errors

---

### Post by dustman on 2008-11-04
Hello!

If I understood what you're asking, you should mount the windows share on the Ubuntu machine using samba, then just copy the movies you like from the windows machine to the USB stick...:confused: why would you like to do that? Or are you trying to use the USB stick as a proxy between the two computers?

Cheers,

Radu

---

### Post by superprash2003 on 2008-11-04
have you enabled file sharing in windows?[http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_august13.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_august13.mspx)

---

### Post by nimsu on 2008-11-04
> **dustman said:**
> Hello!

If I understood what you're asking, you should mount the windows share on the Ubuntu machine using samba, then just copy the movies you like from the windows machine to the USB stick...:confused: why would you like to do that? Or are you trying to use the USB stick as a proxy between the two computers?

Cheers,

Radu

well it's not a usb stick.. it's a 500 GB external hard drive. so i have the hd connected to my ubuntu machine and will be downloading movies (legally of course) to my xp machine and then want to copy/move them over to the ubuntu machine

---

### Post by deearar on 2008-11-04
How is the USB drive formatted? NTFS?

---

### Post by nimsu on 2008-11-04
> **deearar said:**
> How is the USB drive formatted? NTFS?

fat32

---

### Post by dustman on 2008-11-05
Well, you must have samba installed on your Ubuntu box to do something like that. 
```
sudo apt-get install samba
sudo apt-get install smbfs

```
Note: you can mount the windows share in a folder (usually in /media/put_here_what_name_u_want). That's why you need the smbfs package.
Once you have installed samba, you have to use the "Create a small home of office network" wizard available in windows xp (you can find a video tutorial [[COLOR="Blue"]here[/COLOR]]("http://www.revver.com/video/861756/creating-a-home-or-small-office-network/")). After that, you should be able to see your windows xp machine from your Ubuntu box. Share the movies on your windows machine, and copy them to the USB hdd connected to your Ubuntu box.

If you want to do it the other way around (share some data on your Ubuntu box and copy the data using the windows machine, you have to share (right click on the folder you want to share, then press "Share") the folder from Ubuntu.

Cheers!

Radu

---

