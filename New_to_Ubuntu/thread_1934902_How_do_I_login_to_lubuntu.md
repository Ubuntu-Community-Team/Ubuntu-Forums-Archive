---
title: "How do I login to lubuntu"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by Brandon Rea on 2012-03-03
Ok, I installed Xubuntu 11.10 on my Toshiba Satalite C50 dual booted with windows 7. After that I eventually installed the KDE desktop and the Lubuntu Desktop after KDE.  When I rebooted the boot screen said lubuntu instead of Xubuntu and the login screen is now the lubuntu login screen instead of the xubuntu one. 

Here is my problem, I can't seen to get past the Lubuntu login screen. I type my username and password in and it just resets the fields and does nothing. I even tried logging into a guest session.

I'm not sure if this is a problem or if I am just not loving in the right way.

Sorry if I am a bit confusing, I am new to Ubuntu

---

### Post by Brandon Rea on 2012-03-03
Sorry lol logging* instead of loving (I am typing on an iPod so bear with my spelling and grammar mistakes.)

---

### Post by surfer on 2012-03-03
can you still log in to a terminal? (hit ctrl-alt-f1, you should get a password prompt without window manager; ctrl-alt-f7 should bring you back to the window manager)

---

### Post by MG&amp;TL on 2012-03-03
Press Ctrl-Alt-F1, then login using the text-based interface. Type the following code:

```
sudo dpkg-reconfigure lxdm
```

Then select the lightdm login option at the curses interface.

Then type:

```
sudo service lightdm restart
```

And normal service should be resumed.

---

### Post by Brandon Rea on 2012-03-03
When I try to login with terminal it tells me that my password is incorrect even know I have had the same one for a month now. I am beginning to think that I am typing my username in wrong (username is "Brandon Rea") I even tried using a _ instead of a space and all other possible usernames like "brandonrea" "BrandonRea" "brandon_rea" Brandon_Rea" with no luck.

---

### Post by maniandram on 2012-03-03
Maybe you have forgetten your password?
:popcorn::KS:popcorn::KS:popcorn::KS:popcorn::KS

---

### Post by arochester on 2012-03-03
How many times have you rebooted and logged in? Your username is usually your first name in lower case only. If your first name is Brandon, and Rea is your last name then your username would normally be: brandon

The way of changing your Desktop Environment is normally on the same screen where you input your user name and password. There should be something at the bottom labelled "Session". There you can choose KDE, Xfce or LXDE.

---

### Post by Brandon Rea on 2012-03-03
No, I am absolutely sure of my password because It is the exact same one I use to login to my iPod and Windows 7 and I use those daily. I Was hoping it would be as simple as me accedentally leaving caps lock on but nope. 

Also when I installed Xubuntu with Wubi, in the Wubi installer is said that my username would be "brandonrea" but when I have been logging in to Xubuntu before the lubuntu installation it displays my username as "Brandon Rea" 

I have tried to log in using both and no luck.

---

### Post by winh8r on 2012-03-03
Okay, after a small experiment where I created a new user account "Brandon Rea", I found that Ubuntu has automatically shortened your username to ```
brandonr
```.

This is because you chose a username with a space in the middle, your username will still show up as Brandon Rea on the login menu but in order to login via the console/terminal you will need to use ```
brandonr
``` as your username.

Hope this helps you.

---

### Post by Brandon Rea on 2012-03-03
I have rebooted many times before the KDE installation and a few more times before the LXDE installation. 

I tired brandon and Brandon neither work

---

### Post by Brandon Rea on 2012-03-03
brandonr does not work :(

---

### Post by winh8r on 2012-03-03
Even when you try to login through the recovery mode console?

If that is the case then I think  maybe you are entering the wrong password.


You can change the password from the recovery mode 

navigate down the menu to the root shell prompt

enter

```
sudo passwd brandonr
```

and enter a new password 
enter it again to confirm and it will tell you if it has been successfully done.

make sure you write down your password exactly as you type it in.

then 

enter 

```
reboot now
```

---

### Post by Brandon Rea on 2012-03-03
I will try it, but recovery mode is very slow and freely for me. When I type something into the console it takes about a minute or two for it to even show up on the screen

---

### Post by Brandon Rea on 2012-03-03
It says "User brandonr does not exist" My problem is still that I can't figure out what my username is

---

### Post by Brandon Rea on 2012-03-03
When I type this

sudo passwd Brandon Rea

It gives my an option list, what am I supposed to do from here?

The list says

Options:
-a, --all
-d, --delete
-e, --expire 
-h, --help
-k, --keep-tokens
-i, --inactive INACTIVE

-l, --lock
-n, --mindays MIN_DAYS

-q,  --quiet
-r,  --repository REPOSITORY
-s, --status
-u, --unlock
-w, --warndays WARN_DAYS
-x, --maxdays MAX_DAYS

---

### Post by Brandon Rea on 2012-03-03
Oh well, I just uninstalled it and am going to reinstall Xubuntu. I have everything backed up on another hdd anyways.  Thank for the help though

---

### Post by bcbc on 2012-03-03
A bit late to the table... but Wubi uses your windows login as your user description and that is what is presented when you login to Ubuntu (not your user name). Your username is whatever you typed in when running wubi.exe.

e.g. Windows name "John", wubi will default that to username "john" but it will still present "John" when you login. If you decided to change "john" to "jill" in the Wubi screen, it will set up the user account as "jill" with description "John" and you'll be prompted with "John" at login.

Assuming you never use the terminal, you might forget that John was jill, and then you won't be able to login from a terminal.

If you forget you can boot recovery mode and enter:
```
ls /home
```
That will list all the users.

Edit:
I was trying to give an example so I set my real name to "Bing Crosby" and that's what I see logging in, as well as in the top right of the desktop. From a terminal I can see this with:
```
bcbc@ubuntu:~$ getent passwd bcbc
bcbc:x:1000:1000:Bing Crosby:/home/bcbc:/bin/bash
```

---

