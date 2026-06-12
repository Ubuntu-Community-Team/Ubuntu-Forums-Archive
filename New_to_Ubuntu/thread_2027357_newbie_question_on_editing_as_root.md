---
title: "newbie question on editing as root"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by Vincent River on 2012-07-16
[FONT=Arial]Hello,[/FONT]
  
    [FONT=Arial]I have a newbie question. Using a description I found on the web I installed a WiFi adapter for which there are no Linux drivers by installing it with a wrapper. Everything went well until the very last step where I have to edit the file "/etc/modules" and add a line to that file. I understand that you can only do that as a superuser, but I'm not getting it to work. I tried the following:[/FONT]
  [FONT=Arial]
[/FONT]
  [FONT=Arial]When I type "sudoedit /etc/modules" I am asked for a password. After I enter the password for the only user account (which is of the "Administrator" type) I can edit the modules file. However when I try to save it the system proposes to save it as a temporary file with a different name. When I manually change that filename so it will overwrite "/etc/modules" I get a message "Error writing /etc/modules: Permission denied".[/FONT]
  [FONT=Arial]
[/FONT]
  [FONT=Arial]I tried to look it up in the manual [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)[/FONT]
[FONT=Arial]but I can't find where I go wrong. Any help will be appreciated.

[/FONT]
  [FONT=Arial][FONT=&quot]
[/FONT][/FONT]

---

### Post by steeldriver on 2012-07-16
I never use 'sudoedit' (in fact I didn't know it existed - it seems unnecessary) but I just confirmed my clean 12.04 VirtualBox installation does the same - I don't know if that's the desired behavior or it's a bug, however

```
sudo nano /etc/modules
```works as expected - try that instead

EDIT: it looks like it *is* the desired behavior - if you just save the temporary file as prompted (i.e. do NOT manually change it back to /etc/modules) then it automatically copies the tmp file back over the original and deletes the tmp file - from the man page:

```
If they have been modified, the temporary files are copied back to their  original location and the temporary versions are removed.
```

---

### Post by garyed on 2012-07-16
The first thing I would do as a safety precaution is backup any system file I;m about to edit:
```
sudo cp /etc/modules /etc/modules_bakup
```

Then try:
```
gksudo gedit /etc/modules
```
Gedit is a little easier working with for editing. 
If you still can't save the file you might have to change permissions.

---

### Post by Vincent River on 2012-07-17
Thank you; I managed to edit this file. Only thing is: somehow the WiFi adapter still doesn't work under Ubuntu, but obviously that is a different matter. I'll have to buy a new one, I guess.
Vincent

---

### Post by Elfy on 2012-07-17
> **Vincent River said:**
> Thank you; I managed to edit this file. Only thing is: somehow the WiFi adapter still doesn't work under Ubuntu, but obviously that is a different matter. I'll have to buy a new one, I guess.
Vincent

Try getting some help for the existing one first :)

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Give as much help as you can - [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

as an addendum to 

```
sudo nano /etc/modules
```

if you 

```
sudo nano -B /etc/modules
```

it will create a backup for you.

I believe that you can setup gedit to do the same.

---

### Post by jmfal on 2012-07-17
Welcome to Ubuntu

Take a look at this for your wireless problems

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

