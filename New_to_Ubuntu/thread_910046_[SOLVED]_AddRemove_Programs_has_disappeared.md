---
title: "[SOLVED] Add/Remove Programs has disappeared"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Timmeh02 on 2008-09-04
I previously had "add/remove programs" on the bottom of the Applications menu but it has now disappeared.  I have checked the users and groups in system administration and I can't check the box that gives administrator privileges.  I have logged into each users profile on the system (family members) and none of them will allow me to check the box that gives a user administrator privileges.   I'm only guessing that you need that check box ticked to be able to add or remove things on the system.  Is there any way of recovering the add/remove programs function, or a way of becoming the system administrator, thanks.  Timmeh02.

---

### Post by canthus13 on 2008-09-04
Right-click the applications menu, click edit menus.  Make sure Applications is highlighted in the left column of the window that pops up.  Scroll the right column to the bottom, and make sure that Add/Remove is checked.  Close the window.  It *should* be there now.

--Me

---

### Post by Nepherte on 2008-09-04
If the entry got somehow deleted, you can simply recreate it in the menu editor (alacarte). The command line to start add/remove programs is:
```
/usr/bin/gnome-app-install
```

---

### Post by Timmeh02 on 2008-09-04
> **canthus13 said:**
> Right-click the applications menu, click edit menus.  Make sure Applications is highlighted in the left column of the window that pops up.  Scroll the right column to the bottom, and make sure that Add/Remove is checked.  Close the window.  It *should* be there now.

--Me

Okay, went through those steps and I can see the check box for add/remove, but when I go to check it, it bounces me out and goes back to blank.

---

### Post by Nepherte on 2008-09-04
Just check it and close the menu editor (even if it turned to unchecked again, just leave it). I have that behavior with some items as well, but they end up showing anyhow. At least for me they do.

---

### Post by Timmeh02 on 2008-09-04
> **Nepherte said:**
> If the entry got somehow deleted, you can simply recreate it in the menu editor (alacarte). The command line to start add/remove programs is:
```
/usr/bin/gnome-app-install
```

Hi, that opened up the package manager, thanks for that.  I got this message in terminal window:

tim@tim-desktop:~$ /usr/bin/gnome-app-install
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:123: GtkWarning: Unable to locate theme engine in module_path: "aurora",
  self.icons = gtk.icon_theme_get_default()

** (gnome-app-install:17495): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1255: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
tim@tim-desktop:~$ tim@tim-desktop:~$ /usr/bin/gnome-app-install
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:123: GtkWarning: Unable to locate theme engine in module_path: "aurora",
  self.icons = gtk.icon_theme_get_default()

** (gnome-app-install:17495): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1255: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
tim@tim-desktop:~$ 

I ALSO NOTICE THAT THERE NO LONGER APPEARS TO BE "SYNAPTIC" IN THE MENU ITEMS.  

Any suggestions on where that might have gone,  I'm having suspicions about certain teenagers fiddling around with things on me.  No administrator on my user anymore, no SYNAPTIC and no add/remove package manager all of a sudden.  It's amazing what they can achieve in one day.

---

### Post by Timmeh02 on 2008-09-04
> **Nepherte said:**
> Just check it and close the menu editor (even if it turned to unchecked again, just leave it). I have that behavior with some items as well, but they end up showing anyhow. At least for me they do.

Well I guess it's just my luck that when I check it and close, the item is still not appearing on the menu list.  Doh!

---

### Post by Nepherte on 2008-09-04
How about creating the missing entries yourself? Does that help? You can open synaptic with:
```
gksudo synaptic
```

---

### Post by Timmeh02 on 2008-09-04
> **Nepherte said:**
> How about creating the missing entries yourself? Does that help? You can open synaptic with:
```
gksudo synaptic
```

Error window appears:

Failed to run synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by Dougie187 on 2008-09-04
Does your account have administrative privileges? Is it the one you created when you installed the computer

---

### Post by Timmeh02 on 2008-09-04
There seems to be a problem with the administration of the users that have been created on the system.  I was originally the administrator, but my kids have added themselves on too.  I suspect that may have changed the settings, I am now unable to check the box that gices administrative priveleges. When I go to update the users and I try to check the box that gives me admin preveleges, it will not allow me to update.  There is also a user called 'root' which I am unable to access.

---

### Post by Dougie187 on 2008-09-04
Can you post the output of
```
cat /etc/group
```

---

### Post by Timmeh02 on 2008-09-04
> **Dougie187 said:**
> Can you post the output of
```
cat /etc/group
```

Could you please tell me how to create that text window inside a post, I am unable to paste in the result of that terminal window. It tells me there are too many images.  Thanks for stepping this through for me. :)

---

### Post by Dougie187 on 2008-09-04
To make a nice text box inside of a post just put a code block around it. Code blocks are prefaced by "[ code ]" (without the spaces and quotes) and followed by "[ /code ]" again without the spaces and quotes.

To copy and paste the text from a terminal to a post, select all the text you want to copy and push Ctrl+Insert. Then to paste it click where you want to paste and hit Shift+Insert.

Another way you could get it so you can copy and paste, is type this is a terminal
```
cat /etc/group > ~/Desktop/GroupInfo
```

Then on your desktop you will have a file called GroupInfo that you can open with gedit by double clicking on it, then you can simply copy and paste from that.

---

### Post by Timmeh02 on 2008-09-04
```

tim@tim-desktop:~$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:tim,beck,kristi,admin
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:tim,beck,kristi,admin
fax:x:21:beck,kristi,admin
voice:x:22:
cdrom:x:24:tim,beck,kristi,admin
floppy:x:25:tim,beck,kristi,admin
tape:x:26:beck,kristi,admin
sudo:x:27:
audio:x:29:pulse,tim,beck,kristi,admin
dip:x:30:tim,beck,kristi,admin
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:tim,beck,kristi,admin
sasl:x:45:
plugdev:x:46:tim,beck,kristi,admin
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
dhcp:x:102:
syslog:x:103:
klog:x:104:
scanner:x:105:hplip,beck,kristi,admin
nvram:x:106:
fuse:x:107:tim,beck,kristi,admin
ssl-cert:x:108:
lpadmin:x:109:tim,beck,kristi,admin
crontab:x:110:
mlocate:x:111:
ssh:x:112:
avahi-autoipd:x:113:
gdm:x:114:
admin:x:1003:
pulse:x:116:
pulse-access:x:117:
pulse-rt:x:118:
messagebus:x:119:
avahi:x:120:
netdev:x:121:
polkituser:x:122:
haldaemon:x:123:
tim:x:1000:
beck:x:1001:
kristi:x:1002:
ntp:x:124:
tim@tim-desktop:~$ 

```

---

### Post by Dougie187 on 2008-09-04
Ok, so it looks like your not in the admin group. In fact, noone is.

I believe if you boot into recovery mode (by selecting it from grub) you should be able to edit this file.

If you boot into Recovery mode, they Press Alt+F2 and type
```
gksudo gedit /etc/group
```

Then find the line in the file that says 
```
admin:x:1003:
```

Assuming your username is tim, change the line to look like this
```
admin:x:1003:tim
```

If you want to add any other account names to the list of admins, just seperate then with a comma and append them to the end of the line. After you are done, save the file, and reboot back into your normal kernel. Now you should be able to do sudo commands.

---

### Post by Timmeh02 on 2008-09-04
> **Dougie187 said:**
> Ok, so it looks like your not in the admin group. In fact, noone is.

I believe if you boot into recovery mode (by selecting it from grub) you should be able to edit this file.

If you boot into Recovery mode, they Press Alt+F2 and type
```
gksudo gedit /etc/group
```

Then find the line in the file that says 
```
admin:x:1003:
```

Assuming your username is tim, change the line to look like this
```
admin:x:1003:tim
```

If you want to add any other account names to the list of admins, just seperate then with a comma and append them to the end of the line. After you are done, save the file, and reboot back into your normal kernel. Now you should be able to do sudo commands.

I am unable to get through this step, please see attached error message:

---

### Post by Dougie187 on 2008-09-04
> **Timmeh02 said:**
> I am unable to get through this step, please see attached error message:

You get this error after you boot back into recovery mode?

---

### Post by Timmeh02 on 2008-09-04
> **Dougie187 said:**
> You get this error after you boot back into recovery mode?

I may not have done this correctly. Could you please explain grub, and how I am meant to reboot correctly.  I only pressed Alt-F2 sorry.

---

### Post by Dougie187 on 2008-09-04
Sure, no problem.

When you turn on your computer you will get a grub message that says something like "Loading Grub, Press Esc for More Options"

At this point, you want to press Esc, and then select the top most option that has (Recovery Mode) In it.

The commands you will end up using will be a bit more complicated then I thought, because it has to be done on a command line.

After a little bit, you will get a blue box that has a couple of options like "Resume Normal Boot" and "Drop to a root terminal".

Select the option that has the Root Terminal in it. Now, you will probably want to write all of these commands down, because you will be in a terminal and not able to walk through this.

Anyways, once you get a terminal, type
```
nano /etc/group
```

Go down until you find the admin line, and change it as I said before, just simply add your username to the end of it line. Then press Ctrl+X to quit, and it will ask you if you want to save it, make sure you select Y to save. After you have saved the file, type exit, and then Resume Normal Boot. After this, try something with sudo and see if it works for you.

---

### Post by Timmeh02 on 2008-09-04
Thanks, I'm going in......

---

### Post by mc4100 on 2008-09-04
I'd also like to add that if you have trouble using the command line, then this can be done graphically using a LiveCD. In which case, Dougie187's original instructions would work, with a small change.
> **Dougie187 said:**
> Mount the root partition of your Ubuntu installation, press Alt+F2 and type
```
gksudo gedit /wherever-your-partition-is-mounted/etc/group
```

Then find the line in the file that says 
```
admin:x:1003:
```

Assuming your username is tim, change the line to look like this
```
admin:x:1003:tim
```

If you want to add any other account names to the list of admins, just seperate then with a comma and append them to the end of the line. After you are done, save the file, and reboot back into your normal kernel. Now you should be able to do sudo commands.

---

### Post by Timmeh02 on 2008-09-04
Thanks Dougie187, 

You have been a wonderful help.  The system has returned to normal.  I really appreciate your concise instructions.  Legend!

---

### Post by Dougie187 on 2008-09-04
No problem. Im glad you got it to work.

---

