---
title: "Asks for password on startup even though it's set to automatically authenticate"
date: 2023-02-22
forum: New to Ubuntu
---

### Post by supermax666 on 2023-02-22
Hello
I set my computer to automatically authenticate so it won't ask for a password on startup and it worked as expected. After a day or two, I disabled automatically screen locking, which was set to 15 minutes, so that it wouldn't ask for a password after a long time of inactivity. This also worked as expected but since I did this, it now asks for password on startup.

I'm attaching screencaps of the settings. Thank you.

---

### Post by TheFu on 2023-02-22
Are you using the key chain/ring manager?  [https://itsfoss.com/ubuntu-keyring/](https://itsfoss.com/ubuntu-keyring/)  What does the actual password request dialog look like?

BTW, the images are too small to read ( for me).  Usually it is best to copy/paste text, though this time does make sense.

---

### Post by MAFoElffen on 2023-02-23
Please post the contents of
```

grep 'ExecStart' /etc/systemd/system/getty@tty1.service.d/override.conf
grep 'ExecStart' /etc/systemd/system/getty.target.wants/getty@tty1.service
grep 'ExecStart' /lib/systemd/system/getty@.service

```
if autologin is enbled, we are going to see something like this: (With 'myusername' being the name of the user logged in by autologin.)
```

ExecStart=-/sbin/agetty --noissue --autologin myusername %I $TERM

```
If autologin is disbled, it is going to look like this:
```

ExecStart=-/sbin/agetty -o '-p -- \\u' --noclear %I $TERM

```

---

### Post by supermax666 on 2023-02-24
```
[FONT=monospace][COLOR=#000000]grep: /etc/systemd/system/getty@tty1.service.d/override.conf: No such file or directory [/COLOR]
[COLOR=#ff5454]**ExecStart**[/COLOR][COLOR=#000000]=-/sbin/agetty -o '-p -- \\u' --noclear %I $TERM [/COLOR]
[COLOR=#ff5454]**ExecStart**[/COLOR][COLOR=#000000]=-/sbin/agetty -o '-p -- \\u' --noclear %I $TERM[/COLOR]
[/FONT]
```

so auto login is off...

---

### Post by MAFoElffen on 2023-02-25
Two ways to do this... Easiest is to go to Settings > Users > Unlock > Toggle "Autologin"

Or the Manual way, with is
```

sudo systemctl edit getty@.service

```
Which will open nano with a template file, with instructions, that starts out with these first 6 lines:
```

### Editing /etc/systemd/system/getty@.service.d/override.conf
### Anything between here and the comment below will become the new contents of of the file



### Lines below this comment will be discarded

```
Change the blank lines between "Anything between here" and "Lines below this comment..." to include the new code... Like this
```

### Editing /etc/systemd/system/getty@.service.d/override.conf
### Anything between here and the comment below will become the new contents of of the file
[COLOR=#ff0000][Service]
ExecStart=
ExecStart=-/sbin/agetty --noissue --autologin myusername %I $TERM
Type=idle
[/COLOR]
### Lines below this comment will be discarded

```
...Indicated in RED, substituting your User Name for where it says myusername

---

### Post by supermax666 on 2023-02-27
The easy way doesn't work, my Users setting doesn't have an Unlock section =([IMG]https://ubuntuforums.org/attachment.php?attachmentid=291843&stc=1[/IMG]
I was following manual mode but was unsure how to save the file in the end. I thought I should just override it but didn't know the command to do it either. I think "append" would be what I wanted but I didn't understand what the key command for that was. It said M-A. Can you help me through that? Thank you [=

---

### Post by MAFoElffen on 2023-02-27
The editor used by that is 'nano', so <Cntrl><O> saves, and <Cntrl><X> exits...

---

### Post by TheFu on 2023-02-27
> **MAFoElffen said:**
> The editor used by that is 'nano', so <Cntrl><O> saves, and <Cntrl><X> exits...

Perhaps he needs to be using **sudoedit**?  To edit system files, use sudoedit.  System files are any that aren't in your HOME directory or on external storage ... usually mounted under /media/ somewhere.

There are 50 different editors on Linux. nano is the default for most system things, but if there was a GUI, then that isn't nano being used and it is unlikely to be able to modify any system files without configuring it for use with sudoedit.

---

### Post by MAFoElffen on 2023-02-28
@TheFu -
In systemd:
```

sudo systemctl edit getty@.service

```
That starts a process... It checks if an override file already exists for the named service (getty@.service)... If it does, then it opens that file in the default editor. If not, then it creates an override directory (/etc/systemd/system/getty@.service.d/) and opens a service template file, which if edited, and saved, then creates the override file (/etc/systemd/system/getty@.service.d/override.conf)... Notice I said, if edited in the right spot. If you abandon it, by not saving, or not having the inserted text in the correct place in that template, then it does not create the directory nor the file.

If you create with 'sudoedit', then you would first have to manually ensure that the file did not exist already, then manually create directory /etc/systemd/system/getty@.service.d/... then create /etc/systemd/system/getty@.service.d/override.conf...

There is a method to that madness that is already in place for a reason. It's a systemd thing.

---

### Post by TheFu on 2023-02-28
> **MAFoElffen said:**
>  
```

sudo systemctl edit getty@.service

``` 

Learn something new every day!  I'd have used 'locate' with grep.
```
$ locate getty |grep service
/etc/systemd/system/getty.target.wants/getty@tty1.service
/usr/lib/systemd/system/console-getty.service
/usr/lib/systemd/system/container-getty@.service
/usr/lib/systemd/system/getty-static.service
/usr/lib/systemd/system/getty@.service
/usr/lib/systemd/system/serial-getty@.service
/usr/lib/systemd/system/getty.target.wants/getty-static.service

```
This assumes I understand what's necessary, which clearly I do not. ;)

---

