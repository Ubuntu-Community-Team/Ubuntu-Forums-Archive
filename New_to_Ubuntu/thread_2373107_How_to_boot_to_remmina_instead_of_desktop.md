---
title: "How to boot to remmina instead of desktop ??"
date: 2017-10-03
forum: New to Ubuntu
---

### Post by am.steen on 2017-10-03
I am working on thin client for windows Terminal servers
I use remmina and it works well but each time ubuntu starts
ask for user and password and run desktop then remmina.

I need to [COLOR=#0000ff]boot ubuntu to remmina direct[/COLOR] without asking for 
[COLOR=#0000ff]user and password[/COLOR] and [COLOR=#0000ff]without desktop[/COLOR].

Also if possible [COLOR=#ff0000]shutdown ubuntu on closing remmina[/COLOR].

Thanks in advance.

---

### Post by Kirboosy on 2017-10-03
Welcome to the forums! :D

Lets get a few basic things cleared up.

1. What version of Ubuntu are you running?
2. You can shutdown Ubuntu based off of a script. I would suggest looking at this [thread]("https://ubuntuforums.org/showthread.php?t=929972&page=2") 

Hope that helps!
~Caboose

---

### Post by am.steen on 2017-10-04
First Off all thanks for your concern

1. My [COLOR=#000000]version of Ubuntu is :  
[/COLOR]                                     **[COLOR=#ff0000]Ubuntu 16.04.1 LTS[/COLOR]****[COLOR=#ff0000]                                              Code name: xenial[/COLOR]**
[COLOR=#000000]with remmina installed on it.[/COLOR]
Sorry For less details as I am new to [COLOR=#000000]Ubuntu.

Thanks in advance[/COLOR]

---

### Post by Kirboosy on 2017-10-04
Alright lets take a stab at this.

_**Setup Automatic Login**_
1. Launch the settings app and go to User Accounts.
2. Click the Unlock option at the top-right side and type in your password.
3. Click on the user you want to set up auto-login for.
4. Toggle the Automatic Login switch to the On setting.
5. Click Lock to save the changes.

_**Automatic Starting Remmina**_
1. Open a terminal and run the following command
```
nano remmina
```
2. Copy and paste the following
```

#!/bin/bash
remmina && init 0
exit 0

```
3. Save and exit by pressing Control + X.
4. "Save modified buffer (Answering "No" WILL DESTROY CHANGES) ?" Y
5. "File Name to Write: remmina" Enter Key
6. Run the following command in terminal
```
sudo chmod +x remmina
```
7. On the Ubuntu Dash type in "Startup Applications"
8. Click "Add" to create a new startup entry
```
Name: Remmina
    Command: <Browse to the script you just created>
    Comment: <Optional, nothing here required>
```
9. Click Add to save the change

Reboot the computer to test the changes

Hope that helps!
~Caboose

---

### Post by am.steen on 2017-10-05
Many thanks to Mr. [COLOR=#000000]Caboose885

I do as you say and it works but the desktop still there.
I need to add a new desktop file that starts remmina instead of desktop 

[/COLOR][COLOR=#000000]Is this possible ??
[/COLOR][COLOR=#000000]
I do some search and I found these folders on my ubuntu
[/COLOR]

/usr/share/lightdm/guest-session/skel/.config/autostart
/home/orangepi/.config/lxsession/LXDE/autostart
/etc/xdg/autostart
/etc/xdg/openbox/autostart
/etc/xdg/lxsession/LXDE/autostart

But I do not know which one the system start with ??
[COLOR=#000000]



[/COLOR]

---

### Post by Kirboosy on 2017-10-10
Perhaps this thread would be of use: [Start Ubuntu without a desktop environment but start an X application]("https://askubuntu.com/questions/310671/start-ubuntu-without-a-desktop-environment-but-start-an-x-application")

---

