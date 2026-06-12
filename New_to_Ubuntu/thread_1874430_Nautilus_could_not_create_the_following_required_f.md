---
title: "Nautilus could not create the following required folders"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by jasonsmith504 on 2011-11-03
hey i have a toshiba portege m400-s5032 laptop. yesterday i tried to make a new owner profile for my laptop and i tried to delete my other profile. now my new user profile cannot connect to the internet and when i try to login my computer the profile i tried to delete auto logs in and i get these messages

then i get a message that says:

Could not update ICEauthority file /home/owner/.ICEauthority

it gives me the option to click CLOSE.

and when i do

another messege comes up that says:

There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

it gives me the option to click CLOSE

and when i do its just a empty background no pannel nothing just the purple default wallpaper.

a few moments later then another message


Nautilus could not create the following required folders: /home/owner/desktop,
/home/owner/.nautilus.

Before running nautilus. please create these folders or set permissions such that Nautilus can create them.

can somebody please help me solve this problem

---

### Post by gabrielsu on 2011-11-03
It's a little bit deep well

---

### Post by jasonsmith504 on 2011-11-03
huh

---

### Post by DustyMP on 2011-11-03
You should still be able to access the command line with a ctrl+alt+F6. Once there see if you can login with either your new or old account. From there you can follow the steps [detailed here]("http://askubuntu.com/questions/44107/disable-auto-login-from-the-cli") to get yourself squared away.

---

### Post by jasonsmith504 on 2011-11-03
can you please tell me how to fix it step by step

---

### Post by DustyMP on 2011-11-03
Sure! To keep from getting too lengthy I'll post the code and a brief explanation and if you want details just ask.

1. Boot the machine and wait for it to get done presenting you with error messages.
2. Press ctrl+alt+F6 and this should present you with a login for the terminal, or command line, or whatever you prefer to call it.
3. First let's log in with the new account. Enter the username, press enter, then the password. You aren't going to be able to see the password as you type it so take your time, and don't forget any capital letters you had entered.
4. If that works, you'll be presented with a prompt looking something like:

```
USERNAME@COMPUTER~$
```

5. Now we need to see if we can find the file that controls the autologin. Enter the following at the prompt:

```
cd /etc/gdm
```

This should change your prompt just a bit. It's telling you that  now you are in the /etc/gdm folder. Type:

```
ls | grep custom
```

You create the vertical line by pressing shift and the backslash key. The one above the ENTER key (on mine anyway). If you have any files/folders with "custom" in the name it will tell you. If not it will just print another prompt on the screen. Let me know which happens, and we'll go from there.

---

### Post by jasonsmith504 on 2011-11-03
it say 
custom.conf
$

---

### Post by DustyMP on 2011-11-03
Excellent. What we need to do is edit the contents so it no longer auto-logins. We'll do it with a program called vim that's like notepad in windows, but more advanced.

1. At the prompt type:

```
sudo vim custom.conf
```

And press enter. It will ask you to enter your password again. When you do so the program will start and we'll see the contents of that file. 

2. Using your arrow keys go down until you find the lines that look similar to:

```
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=false
TimedLogin=enzotib
AutomaticLogin=enzotib
TimedLoginDelay=30
DefaultSession=gnome

```

We are concerned about the one "AutomaticLoginEnable" and maybe even "TimedLogin". When you have found them press the insert key on your keyboard. If you look at the bottom-right of your screen you should see --INSERT-- telling you we are now editing the file. 

3. If either "TimedLoginEnable" or AutomaticLoginEnable" are set to "true" you'll want to erase that and type in "false". 

4. Now to save and exit. First press the escape key. --INSERT-- will disappear. Press shift+; and in the bottom-left you should get a colon. type in wq (initials for write / quit) and press enter. It will save the file and take you back to the command prompt.

5. Now to test. We will reboot your machine by entering:

```
sudo shutdown -r now
```

and entering the password if it asks you to. This is telling it to shutdown, restart, right now. When it boots you should be good to go. Let us know if you aren't.

---

### Post by jasonsmith504 on 2011-11-03
it say sudo: vim: command not found 
after i put in my password

---

### Post by DustyMP on 2011-11-03
No problem. We'll use another, very similar editor. Type:

```
sudo vi custom.conf
```

instead. Follow the other steps just the same.

---

### Post by westie457 on 2011-11-03
Hi run this in the terminal you have opened ```
sudo apt-get install vim
``` then follow the instructions provided earlier.

---

### Post by jasonsmith504 on 2011-11-03
ok

---

### Post by jasonsmith504 on 2011-11-04
> **DustyMP said:**
> Excellent. What we need to do is edit the contents so it no longer auto-logins. We'll do it with a program called vim that's like notepad in windows, but more advanced.

1. At the prompt type:

```
sudo vim custom.conf
```

And press enter. It will ask you to enter your password again. When you do so the program will start and we'll see the contents of that file. 

2. Using your arrow keys go down until you find the lines that look similar to:

```
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=false
TimedLogin=enzotib
AutomaticLogin=enzotib
TimedLoginDelay=30
DefaultSession=gnome

```

We are concerned about the one "AutomaticLoginEnable" and maybe even "TimedLogin". When you have found them press the insert key on your keyboard. If you look at the bottom-right of your screen you should see --INSERT-- telling you we are now editing the file. 

3. If either "TimedLoginEnable" or AutomaticLoginEnable" are set to "true" you'll want to erase that and type in "false". 

4. Now to save and exit. First press the escape key. --INSERT-- will disappear. Press shift+; and in the bottom-left you should get a colon. type in wq (initials for write / quit) and press enter. It will save the file and take you back to the command prompt.

5. Now to test. We will reboot your machine by entering:

```
sudo shutdown -r now
```

and entering the password if it asks you to. This is telling it to shutdown, restart, right now. When it boots you should be good to go. Let us know if you aren't.




thank you it worked but my new profile still doesnt have everything my old one had and i cannot scan for internet

---

