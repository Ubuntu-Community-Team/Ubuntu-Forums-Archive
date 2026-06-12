---
title: "Administrative Password"
date: 2017-07-02
forum: New to Ubuntu
---

### Post by jamesyboy55 on 2017-07-02
So a friend of mind told me about this computer and he helped me set it up. I've been using it a lot recently. Last night the power went out at my house (my computer wasn't on) but now I can't access the wifi, I always get this message "Network Service Discovery Disabled". In order to fix this problem I need to use an administrative password. I never set one up and I don't know how to change it or even figure out what it is. If anyone can help me out I'd really appreciate it!

---

### Post by deadflowr on 2017-07-02
Do you enter a password when you login?
Try that one.

---

### Post by jamesyboy55 on 2017-07-02
I did try that one, wouldn't work.

---

### Post by RobGoss on 2017-07-02
Do you have a WiFi password when you login to your home network? might be as simple as resetting your router

---

### Post by deadflowr on 2017-07-02
open a terminal and run 
```
id
```
post back what you see.

---

### Post by jamesyboy55 on 2017-07-02
I'll try that and get back to you.

---

### Post by jamesyboy55 on 2017-07-02
I don't know how to upload a picture so I'll post what came up 

```
uid=1000(odroid) gid=1000(odroid) groups=1000(odroid),4(adm),20(dialout),24(cdrom),27(sudo),30(dip),44(video),46(plugdev)115(lpadmin),116(lightdm)
```

---

### Post by QIII on 2017-07-02
Hello!

Actually, it is best not to attach an image when dealing with terminal commands and results.  Please copy the entire output and post it to the Forums between code tags:

1.  Click the # sign above the text input box, place your cursor between the code tags that appear and paste your text.

2.  Paste your text, highlight it and click the # sign.

3.  Type [noparse]```
[/noparse] before you type or paste your text and [noparse]
```[/noparse] after you type or paste your text.  The square brackets are required.

Thanks!

---

### Post by jamesyboy55 on 2017-07-02
Resetting it didn't work

---

### Post by deadflowr on 2017-07-02
What exactly is happening when you enter your password?
(And does the box you enter the password into look something like this:
[ATTACH=CONFIG]275840[/ATTACH]
or does it look like something else.

---

### Post by jamesyboy55 on 2017-07-02
I'm trying to edit the fil /etc/default/avahi-daemon as root:
I enter the code: gksu gedit /etc/default/avahi-daemon and add the line (Code): AVAHI_DAEMON_DETECT_LOCAL=0
But, before I can do that I need to enter the password and when I enter the password "xxxxxxxxx" something pops up for half a second and it's too fast for me to read.

---

### Post by jamesyboy55 on 2017-07-02
And I do see that box

---

### Post by deadflowr on 2017-07-02
Is gedit installed?
What happens if you use another text editor, like the command line alternative nano:
```
sudo nano /etc/default/avahi-daemon
```
does that also fail.
(press ctrl + X then Y for yes then enter to exit to save changes and exit in nano)

Also, if the password was wrong it would bounce back with a try again in the password box:
[ATTACH=CONFIG]275842[/ATTACH]

---

### Post by oldos2er on 2017-07-02
Please NEVER post any passwords here.

---

### Post by jamesyboy55 on 2017-07-02
That did work, i need to change the code: AVAHI_DAEMON_DETECT_LOCAL=1
To AVAHI_DAEMON_DETECT_LOCAL=0

---

### Post by deadflowr on 2017-07-02
If what I gave you worked (assuming nano),
then run it again and just navigate down to the line (use the keyboards up,down,left,right arrow keys),
then delete the 1 and put 0 in it's place. (just use the backspace key to delete/erase)

Then run the ctrl +X to save and exit.

---

### Post by johndough2 on 2017-07-03
Hi

Perhaps your friend knows the admin password.

your user value of 1000 means you are just a user, as am I.  However when I start a root terminal and put in the password I am elevated to uid=0(root) gid=0(root) groups=0(root) which is probably where you need to be.

I have a user password ******###  and a root/admin password *####**************  you need the same. 

As it was a power cut is the router reverting to basic settings and the WiFi is actually switched off.  Can you be sure the WiFi is working by using a phone or similar?

So please split this into 2 parts proving there is a WiFi to connect to  and then getting admin access to connect yours.

---

### Post by deadflowr on 2017-07-03
In Ubuntu any user in the sudo group is an admin outright.
Very rare need to ever change to root directly in Ubuntu.

From a post above it seems running the gksu gedit command simply flashed something on the screen and then nothing.
A bad password would have simply reloaded the gksu password box with a try again message.
So it seems to be a problem launching the gedit program rather than an admin password kerfuffle.

---

### Post by coffeecat on 2017-07-03
> **johndough2 said:**
> your user value of 1000 means you are just a user, as am I.

@johndough2, with respect, you are misunderstanding something, and also missed an important piece of information the OP provided in post #7.

First - in Ubuntu, the first created user has a uid of 1000, and is an administrative account by default. The UID=1000 account is not "just a user" - it is an administrative account. Unless an administrator of the system does something silly, ill-advised, or just simply irregular with the sudoers file. But we know that this is not the case here, because in post #7 the OP shows that they are in the sudo group -which means that they are an administrator - period. Just as  deadflowr says in the previous post to mine. 

Which means that their login password for the UID=1000 account **is** their administrative password. 

> **johndough2 said:**
> However when I start a root terminal...

I'm going to be more blunt here. Please don't tell a newcomer, still finding their way around, to do something both unnecessary and bad practice (for a newcomer) such as enabling the root account. That's for people who really know what they are doing. Both you and the OP may benefit from reading this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by johndough2 on 2017-07-04
> **coffeecat said:**
> @johndough2, with respect, you are misunderstanding something, and also missed an important piece of information the OP provided in post #7.

First - in Ubuntu, the first created user has a uid of 1000, and is an administrative account by default. The UID=1000 account is not "just a user" - it is an administrative account. Unless an administrator of the system does something silly, ill-advised, or just simply irregular with the sudoers file. But we know that this is not the case here, because in post #7 the OP shows that they are in the sudo group -which means that they are an administrator - period. Just as  deadflowr says in the previous post to mine. 

Which means that their login password for the UID=1000 account **is** their administrative password. 





I'm going to be more blunt here. Please don't tell a newcomer, still finding their way around, to do something both unnecessary and bad practice (for a newcomer) such as enabling the root account. That's for people who really know what they are doing. Both you and the OP may benefit from reading this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


**_*I missed scrolling across to the right and reading "27 sudo"*_**

---

