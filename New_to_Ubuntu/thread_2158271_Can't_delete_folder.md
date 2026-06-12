---
title: "Can't delete folder?"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by Paradoxicated on 2013-06-28
Hello Everyone.  As you may know I am having trouble with getting Flash to work on my Xubuntu 12.04 Google Chrome.  I have googled and found a solution, but it requires deleting the PepperFlash folder under chrome.  But when I right-click the PepperFlash folder, delete is grayed out.
Screenshot:
[IMG]http://i.imgur.com/SVpbISh.png[/IMG]

After doing more googling, I ended up putting this in the Terminal:

```
chown $USER -R /opt/google/chrome/PepperFlash
```
but the terminal said: 
```
user@ubuntu:~$ chown $USER -R /opt/google/chrome/PepperFlashchown: changing ownership of `/opt/google/chrome/PepperFlash/libpepflashplayer.so': Operation not permitted
chown: changing ownership of `/opt/google/chrome/PepperFlash/manifest.json': Operation not permitted
chown: changing ownership of `/opt/google/chrome/PepperFlash': Operation not permitted
user@ubuntu:~$ 
```

Please help!  My goal is to delete the PepperFlash folder.  By the way, in the PepperFlash folder's properties, it says it's owner is root.

 - Paradoxicated

---

### Post by MidnightGrey on 2013-06-28
try
```
 sudo rm -rf /opt/google/chrome/PepperFlash

```
while chrome is not running.

edit:
you cannot delete it because the folder is root. root trumps user. you also cannot chown it because it is root (again root trumps user).
to remove it you need to do it as root.
**sudo **(or **s**uper **u**ser **do**) means "do this command as root user"

---

### Post by Impavidus on 2013-06-28
You need sudo to delete files owned by root. Open a terminal and start the file manager with```
gksu thunar
```Then do whatever you need to do and close the file manager as soon as you're done, as leaving file managers with root permission open is rather dangerous.

---

### Post by snowpine on 2013-06-28
Never delete system folders owned by root!
You should uninstall properly using the Software Manager.

Generally speaking, I advise against googling and following random how-to's from some guy's blog. Always follow the official Ubuntu documentation and use trusted tools such as the Software Center.

---

### Post by MidnightGrey on 2013-06-28
> **snowpine said:**
> Never delete system folders owned by root!
You should uninstall properly using the Software Manager.

Generally speaking, I advise against googling and following random how-to's from some guy's blog. Always follow the official Ubuntu documentation and use trusted tools such as the Software Center.

well in this case, deleting pepper flash seems relatively safe (and isolated)

---

### Post by Paradoxicated on 2013-06-28
So I'm gonna do what post #3 said.

Thanks for everyone's help, I'll update in a sec.

---

### Post by Paradoxicated on 2013-06-28
I deleted it (by using post #3), but Chrome still has the "Could not load shockwave flash" message.

Help anyone?

---

### Post by MidnightGrey on 2013-06-28
reinstall chrome.

---

### Post by Paradoxicated on 2013-06-28
I reinstalled.  Flash still didn't work.  I deleted PepperFlash.  Still doesn't work.

---

