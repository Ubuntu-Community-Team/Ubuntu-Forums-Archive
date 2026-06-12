---
title: "[SOLVED] emelfm install help"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by AnLGP on 2008-07-03
I downloaded and extracted the tarball.  I CD'd to the directory and did both make and make install like the readme says:

[http://emelfm.sourceforge.net/README](http://emelfm.sourceforge.net/README)

and I get these errors...


steve@linux:~/emelfm-0.9.2$ make
gcc -O2 -Wall `gtk-config --cflags` -DENABLE_NLS -DLOCALEDIR=\"/usr/local/share/locale\" -DPLUGINS_DIR=\"/usr/local/share/emelfm/plugins\" -DDOC_DIR=\"/usr/local/share/emelfm/docs\" -c emelfm.c
/bin/sh: gtk-config: command not found
/bin/sh: gcc: command not found
make: *** [emelfm.o] Error 127
steve@linux:~/emelfm-0.9.2$ make install
gcc -O2 -Wall `gtk-config --cflags` -DENABLE_NLS -DLOCALEDIR=\"/usr/local/share/locale\" -DPLUGINS_DIR=\"/usr/local/share/emelfm/plugins\" -DDOC_DIR=\"/usr/local/share/emelfm/docs\" -c emelfm.c
/bin/sh: gtk-config: command not found
/bin/sh: gcc: command not found
make: *** [emelfm.o] Error 127

I take it to mean that I dont have something installed that's needed to do that (gtk-config?) but is there any other way to install this?  please and thanks!

---

### Post by AnLGP on 2008-07-03
I looked for gtk-config and couldn't find it in synaptic but did find gcc.  I installed gcc and ran make/ make install and this popped out:

emelfm.c:326: warning: implicit declaration of function ‘g_strdup’
emelfm.c:327: error: ‘Config’ has no member named ‘bookmarks’
emelfm.c:327: error: ‘Config’ has no member named ‘bookmarks’
emelfm.c:328: error: ‘Config’ has no member named ‘bookmarks’
emelfm.c:328: error: ‘Config’ has no member named ‘bookmarks’
emelfm.c:329: error: ‘Config’ has no member named ‘bookmarks’
emelfm.c:329: error: ‘Config’ has no member named ‘bookmarks’
emelfm.c:330: error: ‘Config’ has no member named ‘bookmarks’
emelfm.c:330: error: ‘Config’ has no member named ‘bookmarks’
emelfm.c:333: warning: implicit declaration of function ‘read_user_commands_file
’
emelfm.c:336: warning: implicit declaration of function ‘add_user_command’
emelfm.c:342: warning: implicit declaration of function ‘read_toolbar_file’
emelfm.c:345: warning: implicit declaration of function ‘add_toolbar_button’
emelfm.c:354: warning: implicit declaration of function ‘read_keys_file’
emelfm.c:357: warning: implicit declaration of function ‘add_key_binding’
emelfm.c:374: error: ‘GDK_CONTROL_MASK’ undeclared (first use in this function)
emelfm.c:375: error: ‘GDK_SHIFT_MASK’ undeclared (first use in this function)
emelfm.c:397: warning: implicit declaration of function ‘read_plugins_file’
emelfm.c:412: error: ‘Config’ has no member named ‘right_startup_dir’
emelfm.c:413: error: ‘FileView’ has no member named ‘dir’
emelfm.c:413: error: ‘Config’ has no member named ‘right_startup_dir’
emelfm.c:413: error: ‘FileView’ has no member named ‘dir’
emelfm.c:415: error: ‘Config’ has no member named ‘left_startup_dir’
emelfm.c:416: error: ‘FileView’ has no member named ‘dir’
emelfm.c:416: error: ‘Config’ has no member named ‘left_startup_dir’
emelfm.c:416: error: ‘FileView’ has no member named ‘dir’
emelfm.c:420: error: ‘FileView’ has no member named ‘dir’
emelfm.c:420: error: ‘FileView’ has no member named ‘dir’
emelfm.c:422: error: ‘FileView’ has no member named ‘dir’
emelfm.c:422: error: ‘FileView’ has no member named ‘dir’
emelfm.c:429: error: ‘FileView’ has no member named ‘dir’
emelfm.c:429: error: too many arguments to function ‘change_dir’
emelfm.c:430: error: ‘FileView’ has no member named ‘dir’
emelfm.c:430: error: too many arguments to function ‘change_dir’
emelfm.c:431: error: ‘GTK_SORT_ASCENDING’ undeclared (first use in this function
)
emelfm.c:431: error: too many arguments to function ‘sort_list’
emelfm.c:432: error: too many arguments to function ‘sort_list’
emelfm.c:435: warning: implicit declaration of function ‘gtk_text_insert’
emelfm.c:435: warning: implicit declaration of function ‘GTK_TEXT’
emelfm.c:435: error: ‘App’ has no member named ‘output_text’
emelfm.c:435: error: ‘App’ has no member named ‘output_font’
emelfm.c:438: warning: implicit declaration of function ‘gtk_timeout_add’
emelfm.c:438: error: ‘update_status_bar’ undeclared (first use in this function)
emelfm.c:439: error: ‘Config’ has no member named ‘check_config_id’
emelfm.c:439: error: ‘check_config_files’ undeclared (first use in this function
)
emelfm.c:440: error: ‘Config’ has no member named ‘auto_refresh_enabled’
emelfm.c:441: error: ‘Config’ has no member named ‘auto_refresh_id’
emelfm.c:441: error: ‘auto_refresh’ undeclared (first use in this function)
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
emelfm.c:443: error: ‘Config’ has no member named ‘version’
make: *** [emelfm.o] Error 1

---

### Post by Zill on 2008-07-03
> **AnLGP said:**
> ...I take it to mean that I dont have something installed that's needed to do that (gtk-config?) but is there any other way to install this?  please and thanks!
Why not use the version in the repos:
[http://packages.ubuntu.com/hardy/emelfm]("http://packages.ubuntu.com/hardy/emelfm")
```
sudo apt-get install emelfm
```
or Synaptic if you want a GUI.

---

### Post by AnLGP on 2008-07-03
I'm running Debian and it's not in the packages.  I get "Sorry, try again."

---

### Post by Zill on 2008-07-03
There are likely to be different versions for each Ubuntu version.  I think you will need to find the right package for your distribution.  One of the Ubuntu deb versions *could* work but you may end up in "dependency hell" if you choose the wrong one!

I suggest you would be better off with the right version for your distribution so you may get better help from the Debian forums, rather than this one.  However, we do have a lot of clever folk reading this so you never know!

---

### Post by AnLGP on 2008-07-03
I'm willing to bet (as a non betting man) that I'll get the help here.  Ubuntu is based off of Debian so it's similar.

Thanks :)

---

### Post by AnLGP on 2008-07-03
It's a good thing I don't bet.  :lolflag:

---

### Post by kerry_s on 2008-07-03
emelfm is in etch, it's destined to be removed, it's gtk1 and pretty soon everything will be gtk2, little gtk1 support will be left. there is a port to gtk2, it's emelfm2:
[http://emelfm2.net/](http://emelfm2.net/)

the 7.10 deb should work for ya:
[http://lottalinuxlinks.com/files/emelfm2_0.3.6-1_i386.deb](http://lottalinuxlinks.com/files/emelfm2_0.3.6-1_i386.deb)

---

### Post by AnLGP on 2008-07-03
File Type: “Debian package”.

You have no application able to open “emelfm2_0.3.6-1_i386.deb”. You can download it instead.

---

### Post by kerry_s on 2008-07-03
> **AnLGP said:**
> File Type: &#8220;Debian package&#8221;.

You have no application able to open &#8220;emelfm2_0.3.6-1_i386.deb&#8221;. You can download it instead.

huh???

i going to assume you don't know how to install a deb locally.

download the deb, open a terminal and **cd** to where ever you have the deb, **ls** to check it's there, **su to root**> **dpkg -i em**(just hit tab to auto complete)

if it has dependency's you don't have installed> **apt-get -f install**
will install the missing or want to remove it if it's not installable.

---

### Post by AnLGP on 2008-07-03
steve@linux:~$ ls
2008-07-03-170837_1280x1024_scrot.png  downloads
2008-07-03-174708_1280x1024_scrot.png  emelfm-0.9.2
2008-07-03-191643_1280x1024_scrot.png  emelfm2_0.3.6-1_i386.deb
2008-07-03-214650_1280x1024_scrot.png  general_flyer.doc
2008-07-03-214659_1280x1024_scrot.png  jwm-svn.tar.bz2.part
2008-07-03-214725_1280x1024_scrot.png  JWM-Xfce.pet
backups                                MU
documents                              RegnumOnlineInstall_32.part
documents.txt                          temp

linux:/home/steve# cd emelfm2_0.3.6-1_i386.deb
bash: cd: emelfm2_0.3.6-1_i386.deb: Not a directory
linux:/home/steve# dpkg -i em
dpkg: error processing em (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 em
linux:/home/steve# dpkg -i emelfm2_0.3.6-1_i386.deb
Selecting previously deselected package emelfm2.
(Reading database ... 41021 files and directories currently installed.)
Unpacking emelfm2 (from emelfm2_0.3.6-1_i386.deb) ...
Setting up emelfm2 (0.3.6-1) ...
Processing triggers for man-db ...
Processing triggers for menu ...
linux:/home/steve# emelfm
bash: emelfm: command not found
linux:/home/steve# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  desktop-file-utils
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
linux:/home/steve# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  desktop-file-utils
The following packages will be REMOVED:
  desktop-file-utils
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 41122 files and directories currently installed.)
Removing desktop-file-utils ...
Processing triggers for man-db ...
linux:/home/steve# emelfm
bash: emelfm: command not found
linux:/home/steve# cd

I also tried opening a new terminal and doing "emelfm".  It said this

steve@linux:~$ emelfm
bash: emelfm: command not found

---

### Post by kerry_s on 2008-07-03
okay, don't panic it's installed.
use> emelfm2

---

### Post by AnLGP on 2008-07-03
YAY! :popcorn:

Have I told you you're AWESOME?!

---

### Post by kerry_s on 2008-07-03
> **AnLGP said:**
> YAY! :popcorn:

Have I told you you're AWESOME?!

:lolflag: glad you got it, i was just about out the door and thought i would give you 1 more check. i'm busy doing the kids school supply shopping list so i been in and out all day.

---

