---
title: "unable to type in file browser to get to quick navigate to a file"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by rache1111 on 2008-08-21
Hi,

I used be able to type text into the file browser in ubuntu and a little window would show up showing what I have typed. It would also navigate to the file that is closest in name to the letters I type.

However, I don't get that textbox anymore in file browser when I type. Any suggestions?

Thanks,

---

### Post by philinux on 2008-08-21
It works for me but you have to click on any folder first.

---

### Post by rache1111 on 2008-08-21
> **philinux said:**
> It works for me but you have to click on any folder first.

That doesn't seem to be the problem

---

### Post by philinux on 2008-08-21
Odd.

Have you changed any settings recently?

Maybe reinstall nautilus might fix it.

---

### Post by rache1111 on 2008-08-21
> **philinux said:**
> Odd.

Have you changed any settings recently?

Maybe reinstall nautilus might fix it.

I just reinstalled my system yesterday and it was working fine. What I might have changed is I accidentally changed the access modes for all the files in my home directory. I first removed all the execute access for all the files, and I run into problems accessing any file, then I added back the execute permissions to the files and file access was fine again.

I am not sure if that is what caused the problem though.

Here is ls -la for my home directory if that indeed does matter:
```

total 392
drwxr-xr-x 49 sedi  sedi   4096 2008-08-21 11:25 .
drwxr-xr-x  4 root root  4096 2008-08-20 12:58 ..
drwx------  3 sedi  sedi   4096 2008-08-20 18:01 .adobe
drwxr-xr-x  2 sedi  sedi   4096 2008-08-20 21:30 backup
-rw-------  1 sedi  sedi   3143 2008-08-21 08:53 .bash_history
-rw-r--r--  1 sedi  sedi    220 2008-08-20 12:58 .bash_logout
-rw-r--r--  1 sedi  sedi   2940 2008-08-20 12:58 .bashrc
-rw-r--r--  1 sedi  sedi  95369 2008-06-17 16:58 bookmarks.html
drwxr-xr-x  3 sedi  sedi   4096 2008-08-20 13:01 .cache
drwx------  2 sedi  sedi   4096 2008-08-20 19:27 .chewing
drwx------  3 sedi  sedi   4096 2008-08-20 19:26 .compiz
drwxr-xr-x  6 sedi  sedi   4096 2008-08-20 18:37 .config
drwxr--r--  2 sedi  sedi   4096 2008-08-20 18:36 Desktop
drwxr--r--  2 sedi  sedi   4096 2008-08-19 23:23 diary
-rw-------  1 sedi  sedi     28 2008-08-21 08:41 .dmrc
drwxr--r--  2 sedi  sedi   4096 2008-08-20 13:01 Documents
drwxr--r--  3 sedi  sedi   4096 2008-08-21 10:57 downloads
drwxr--r--  3 sedi  sedi   4096 2008-08-17 18:05 drivers
-rw-------  1 sedi  sedi     16 2008-08-20 13:01 .esd_auth
drwxr-xr-x  7 sedi  sedi   4096 2008-08-21 00:17 .evolution
lrwxrwxrwx  1 sedi  sedi     26 2008-08-20 12:58 Examples -> /usr/share/example-content
drwxr-xr-x  2 sedi  sedi   4096 2008-08-20 19:26 .fontconfig
drwx------  5 sedi  sedi   4096 2008-08-21 08:41 .gconf
drwx------  2 sedi  sedi   4096 2008-08-21 11:21 .gconfd
-rw-r-----  1 sedi  sedi      0 2008-08-21 00:05 .gksu.lock
drwx------ 12 sedi  sedi   4096 2008-08-21 00:17 .gnome2
drwx------  2 sedi  sedi   4096 2008-08-20 13:01 .gnome2_private
drwx------  2 sedi  sedi   4096 2008-08-21 08:41 .gnupg
drwxr-xr-x  2 sedi  sedi   4096 2008-08-20 13:01 .gstreamer-0.10
-rw-r--r--  1 sedi  sedi    100 2008-08-21 09:02 .gtk-bookmarks
dr-x------  2 sedi  sedi      0 2008-08-21 08:41 .gvfs
-rw-------  1 sedi  sedi   2181 2008-08-21 08:41 .ICEauthority
drwxr-xr-x  2 sedi  sedi   4096 2008-08-20 17:42 .icons
-rw-------  1 sedi  sedi     51 2008-08-20 21:49 .lesshst
drwxr-xr-x  3 sedi  sedi   4096 2008-08-20 13:01 .local
drwx------  3 sedi  sedi   4096 2008-08-20 18:01 .macromedia
drwx------  3 sedi  sedi   4096 2008-08-20 13:01 .metacity
drwxr-xr-x  4 sedi  sedi   4096 2008-08-20 17:30 .mozilla
drwxr--r--  2 sedi  sedi   4096 2008-08-20 13:01 Music
drwxr-xr-x  3 sedi  sedi   4096 2008-08-21 00:17 .nautilus
-rw-r--r--  1 sedi  sedi      8 2008-08-20 20:05 new file
-rwxrw-rw-  1 sedi  sedi      0 2008-08-20 20:05 new file~
drwxr--r--  2 sedi  sedi   4096 2008-08-20 22:21 notes
drwx------ 10 sedi  sedi   4096 2008-08-20 20:29 .opera
drwxr--r--  2 sedi  sedi   4096 2008-08-19 16:51 PDF
drwxr--r--  2 sedi  sedi   4096 2008-08-20 13:01 Pictures
-rw-r--r--  1 sedi  sedi    586 2008-08-20 12:58 .profile
drwxr--r--  2 sedi  sedi   4096 2008-08-20 13:01 Public
drwxr-xr-x  2 sedi  sedi   4096 2008-08-20 13:05 .pulse
-rw-------  1 sedi  sedi    256 2008-08-20 13:01 .pulse-cookie
drwx------  5 sedi  sedi   4096 2008-08-20 19:26 .purple
drwxr-xr-x  2 sedi  sedi   4096 2008-08-20 20:25 .qt
-rw-r--r--  1 sedi  sedi  10971 2008-08-21 10:31 .recently-used.xbel
drwx------  4 sedi  sedi   4096 2008-08-20 20:08 .scim
drwx------  4 sedi  sedi   4096 2008-08-20 19:19 .Skype
drwx------  2 sedi  sedi   4096 2008-08-20 13:01 .ssh
-rw-r--r--  1 sedi  sedi      0 2008-08-20 17:18 .sudo_as_admin_successful
drwxr--r--  2 sedi  sedi   4096 2008-08-20 13:01 Templates
-rw-r--r--  1 sedi  sedi      0 2008-08-21 11:25 test
drwxr-xr-x  2 sedi  sedi   4096 2008-08-20 17:42 .themes
drwx------  4 sedi  sedi   4096 2008-08-20 17:51 .thumbnails
drwxr-xr-x  2 sedi  sedi   4096 2008-08-20 17:18 .update-manager-core
drwx------  2 sedi  sedi   4096 2008-08-20 13:01 .update-notifier
drwxr--r--  2 sedi  sedi   4096 2008-08-20 13:01 Videos
drwxr-xr-x  3 sedi  sedi   4096 2008-08-20 17:50 .vlc
drwxr-xr-x  4 sedi  sedi   4096 2008-08-21 11:06 .wine
-rw-------  1 sedi  sedi    121 2008-08-21 08:41 .Xauthority
drwxr-xr-x  2 sedi  sedi   4096 2008-08-20 19:25 .xinput.d
-rw-r--r--  1 sedi  sedi   1531 2008-08-20 14:07 xorg.conf
-rw-r--r--  1 sedi  sedi   1475 2008-08-20 21:57 xorg.conf.1
-rw-r--r--  1 sedi  sedi  29464 2008-08-21 11:06 .xsession-errors
```

---

### Post by rache1111 on 2008-08-21
Well I rebooted and this problem seemed to go away. Unfortunately it came back after a while.

It took a while until I could determine what have caused this problem on my machine. To reproduce it:

1. open up nautilus file browser and start typing. A little text box should pop up on the bottom right side of the window
2. navigate to a different work space; the little text box should move over there with you
3. don't do anything, wait a few seconds until the textbox disappears
4. navigate back to the original workspace where you opened up nautilus and try typing in something, the textbox would not appear anymore.


The only way to solve this problem seems to be logging off and logging back on.

Can some confirm that this also happen on their machine?

Thanks!

---

### Post by pauper on 2008-08-21
I can't confirm, though I'm running 2.20.0 version.

```
gconf-editor
```

apps/nautilus/preferences/search_bar_type: search_by_text

Could you do search with Ctrl-s (or Edit--Select Pattern)? Make sure you use
"*" wild card if whole name isn't typed in.

---

### Post by rache1111 on 2008-08-21
Thanks for your feedback pauper.  I am using version 2.22.3, I wonder if this is the problem.

---

