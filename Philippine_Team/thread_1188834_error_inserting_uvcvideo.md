---
title: "error inserting uvcvideo"
date: 2009-06-16
forum: Philippine Team
---

### Post by Script Warlock on 2009-06-16
8.04
lsusb......Bus 001 Device 017: ID 046d:09a4 Logitech, Inc.

pusoicafe@Ubuntu-Server:~$ sudo modprobe -r uvcvideo
pusoicafe@Ubuntu-Server:~$ sudo modprobe uvcvideo
WARNING: Error inserting videodev (/lib/modules/2.6.24-24-generic/kernel/drivers/media/video/videodev.ko): Invalid module format
FATAL: Error inserting uvcvideo (/lib/modules/2.6.24-24-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)

logitech quickcam E2500/3500
any ideas?

---

### Post by loell on 2009-06-16
in jaunty, same result?

---

### Post by Script Warlock on 2009-06-16
sa server lang kc nagdagdag pa ako ng dalawang usb cam para maging apat na security cam ko. kala ko kc plug and play to logitech na binili error tuloy pagreload ng uvc video nawagting nuon ko sa setup da.

sa laptop ok magkaparehas kc ng driver ang builtin webcam sa laptop at logitech uvc gamit.

pagkatpos nagdownload sa uvc mercurial install reboot tapos reload uvc dun na nag error so transfer ko sa isang butas ng usb ganun pa rin

---

### Post by loell on 2009-06-16
try compiling newer uvc driver versions in your 8.04 , not sure if it doesn't need newer kernels though.

---

### Post by Script Warlock on 2009-06-16
nyahahhaa it worked!!! andami na pala bagong patch sa uvc kaya pala, now i know..haiz karaan man diay to akong nagamit abi ko mao na to, eto lang pala solution sa 8hrs kulikot sa webcam...completo na yehehey salamat boss loell....

$ sudo modprobe -r uvcvideo
$ sudo modprobe uvcvideo
$ luvcview
$
$ kita ko na mukha ko hahhhahahaha

---

### Post by loell on 2009-06-16
really!? 

that was fast, ;)


ok.. no probs..

---

### Post by Script Warlock on 2009-06-16
aaaarrrrggg...eto na naman pls help 

sudo /etc/init.d/apache2 force-reload 
Syntax error on line 4 of /etc/apache2/conf.d/zoneminder.conf:
Invalid command 'php_flag', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!

---

### Post by Script Warlock on 2009-06-16
eto yung laman ng zoneminder.conf:

Alias /zm /usr/share/zoneminder

<Directory /usr/share/zoneminder>
  php_flag register_globals off
  Options Indexes FollowSymLinks
  <IfModule mod_dir.c>
    DirectoryIndex index.php
  </IfModule>
</Directory>

---

### Post by Script Warlock on 2009-06-16
i manage to solve the by:

sudo a2enmod php5

sudo apache2ctl restart

firefox browser:

[http://localhost/zm](http://localhost/zm)

TADA!!!!...

---

### Post by whitegourd on 2009-09-30
This helped me out.  Thanks Script Warlock!

---

