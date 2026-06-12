---
title: "help to recover my login password"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by munezz on 2012-03-25
It seems to be getting a habit now........I used a long password for login in Ubuntu 11.10 and decided to make it short for convenience..............so i simply went to system settings and typed my new password but it did not affect the "Change" button and i also turned the password "On" to "Off"(it was stupid idea]](*,).............................so now the thing is i don't need a password to Login but every time i need to install new programs it asks for a password.....................................and one more thing the new password nor the old password seem to log in.

help :confused:

---

### Post by winh8r on 2012-03-25
You can set your password like this:

Hold down the shift key and start your machine

when you see the GRUB MENU screen, select the entry nearest the top which has (Recovery Mode) displayed beside it

A blue screen will open

navigate down the menu using the arrow keys on your keyboard and 

select "Drop to Root Shell Prompt"

When this opens

enter the following:


```
passwd munezz
```

or whatever your username on the machine is.


You will be prompted to enter a new UNIX password

Then again to confirm it (you will not see any text as you type so type carefully.)

Follow the rest of the steps on screen and confirm.

You have now set your password.

enter the following

```
updatedb
```

enter the following

```
shutdown -r now
```

and the machine will shutdown and reboot and you should be able to login normally.

Hope this helps.

---

### Post by Gone fishing on 2012-03-25
The above post won't quite work as when you drop down to a root shell it asks for a password. 

You can get round this by editing the grub recovery mode. Click e to edit and change the line that reads ```
ro recovery modeset
``` to read ```
rw init=/bin/bash 
```and then when it boot it will drop you down to a root shell without a password

PS I don't use Wubi so it might be a little different

---

### Post by munezz on 2012-03-25
> **winh8r said:**
> You can set your password like this:

Hold down the shift key and start your machine

when you see the GRUB MENU screen, select the entry nearest the top which has (Recovery Mode) displayed beside it

A blue screen will open

navigate down the menu using the arrow keys on your keyboard and 

select "Drop to Root Shell Prompt"

When this opens

enter the following:


```
passwd munezz
```or whatever your username on the machine is.


You will be prompted to enter a new UNIX password

Then again to confirm it (you will not see any text as you type so type carefully.)

Follow the rest of the steps on screen and confirm.

You have now set your password.

enter the following

```
updatedb
```enter the following

```
shutdown -R now
```and the machine will shutdown and reboot and you should be able to login normally.

Hope this helps.


Thanxx for the information it worked fine..........except the "-R" is actually "-r" for "shutdown -r now" 

cheers):P

---

### Post by winh8r on 2012-03-25
Glad to hear you got it working again, apologies for the typo! (I have corrected it in the original now)

Good luck.

---

### Post by munezz on 2012-03-26
> **winh8r said:**
> Glad to hear you got it working again, apologies for the typo! (I have corrected it in the original now)

Good luck.

what's the difference between Keyring Password and the Regular Password

---

### Post by Agnosticvigor on 2012-03-26
I'm a new user to Ubuntu. As such I am illiterate to its use. However, I am an avid learner and can hopefully pick up this OS easily. Having issues such as the one above discourages me from its use. I tried the above steps and received a message something along the lines of authentication error      password unchanged. Any help would be appreciated if needed I can try again and copy the message word for word then repost it. Please, any help would be appreciated.



I just went back to access the grub menu and take down the message it gives when I enter the commands listed above. I can't access the grub menu now. I hold shift key and start my computer and it just starts as normal. I can't figure it out.

---

### Post by munezz on 2012-03-26
> **Agnosticvigor said:**
> I'm a new user to Ubuntu. As such I am illiterate to its use. However, I am an avid learner and can hopefully pick up this OS easily. Having issues such as the one above discourages me from its use. I tried the above steps and received a message something along the lines of authentication error      password unchanged. Any help would be appreciated if needed I can try again and copy the message word for word then repost it. Please, any help would be appreciated.

I'm a new user too so I can be of little help, so did u also loose ur password like i did cause the commands may work only for the given situation..................it worked fine for me............again I'm a new user too.

---

### Post by Agnosticvigor on 2012-03-26
No I didn't lose mine I just turned it off. I don't have a reason to have a password so it was kind of an inconvenience. It is still asking me for a password when I want to install a program but it isn't my original password that it wants.

---

### Post by munezz on 2012-03-26
> **Agnosticvigor said:**
> No I didn't lose mine I just turned it off. I don't have a reason to have a password so it was kind of an inconvenience. It is still asking me for a password when I want to install a program but it isn't my original password that it wants.

Why don't you turn it on again and see if it lets you install any new programs.................if it still doesn't work then better PM to some Ubuntu pro...............Good Luck.

---

### Post by Agnosticvigor on 2012-03-26
> **munezz said:**
> Why don't you turn it on again and see if it lets you install any new programs.................if it still doesn't work then better PM to some Ubuntu pro...............Good Luck.

It will not let me turn it back on. I have to unlock it first and I am unable to do that.

---

### Post by munezz on 2012-03-27
> **Agnosticvigor said:**
> It will not let me turn it back on. I have to unlock it first and I am unable to do that.

just try this path....................it might be of some help.
[http://askubuntu.com/questions/10642...utomatic-login]("http://askubuntu.com/questions/106428/how-to-disable-automatic-login")

---

### Post by dfreer on 2012-03-27
> **winh8r said:**
> 
You have now set your password.

enter the following

```
updatedb
```



I'm not really sure why you would include this command. All this does is update the locate database used for searching the file system. It has nothing to do with passwords.

---

