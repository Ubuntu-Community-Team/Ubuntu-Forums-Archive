---
title: "I'm frustrated (monitor and remote login)"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Styler93gsx on 2008-08-11
I have been working at this for about 4 days.  My problems are proubably some of the easiest to fix.  I'm a firm believer in search first, search search search and more search.  I have searched for 4 days.  I'm very frustrated.  What I have. 

HP a310e with a dell, with a dell 1704fpt, Maxtor 500gb external hard drive.  I have installed xubuntu successfully.  I'm on the internet fine.  I have updated software. I have installed envy and installed the video drivers for the Geforece4 MX internal graphics card.  When I plug my dell monitor in I default to 640 x 480.  If I plug my old huge *** gatway monitor it will go to 1280 X 1024 the flat panel will not everything is HUGE and using it becomes an annoyance.  

I have a new macbook, I can see my server in finder but I cannot login in.  It says my password is wrong.


For these two problems I have tried proubably about 20 different approaches to solving these problems.  I have reinstalled about 7 or 8 times (mostly after I screwed something up so bad the server wouldn't start or half the screen be missing or screen be flickering.



I post a lot in automotive forums and try my best to ask a question after a diligent effort to solve the problem on my own.  I'm online right now on aim if you think you could help.  


(Losi Trinity)  with a space is my aim name T

---

### Post by cgkades on 2008-08-11
to prevent giving you advice that you have already tried, can you list the different approaches?

---

### Post by Styler93gsx on 2008-08-11
I am new to linux.  Well actually 4 days new to even a command line.  If I tried to explain to you what I have done it would be like me trying to give directions in a foreign city in a foreign language.  I could probably name a few programs and what not, but not really what I've done.  I will try to explain as best I can.

I have installed a fresh install right now I've updated and on the gateway monitor.  Not to concerned with the monitor at this point.  I have gone into user accounts and played with the settings a bunch and restarted a bunch to try to get the accounts to function.  it says I have different users.  But when I go to login from my network on a separate computer (macbook)  I see the server but I can login as a guest, but when I change to registered user and type in my login and password it says wrong password.  I've gone in and reset I don't know haw many times to no avail.  About 4-5 installs of the operating system ago I actually could log into it and what fixed it then was to some command (passwd)  I don't remember exactly found in during my search quest).  I found it on a how to but I've found a lot of them and not sure exactly what I need.  I could login but and change stuff but it wasn't exactly what I wanted.

Goal is to have it be my home media server.  Files, movies, pics, print server.

---

### Post by cgkades on 2008-08-11
What have you set up on your ubuntu machine that you are trying to access? Have you set up a file server? A ssh server? a samba share?

---

### Post by linux_tech on 2008-08-11
Link: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
press esc key if necessary to get to boot menu
First, you have to reboot into recovery mode.

From the boot menu, select recovery mode
type
ls /home

To reset the password, type
passwd username
(where username is the username you want to reset)

You'll then be prompted for a new password
(use one that you can remember)

You'll be prompted to retype the password. Do so and hit Enter again.

Now the password should be reset. Type
reboot
to reboot your computer.

---

### Post by cgkades on 2008-08-11
well if you can log into your computer you shouldnt need to do the password reset.

You need a service to connect to. Like SSH, http, or samba. if you know which one of those you are trying to connect to you can narrow down your password problem. oh and you were correct, the command to change your password is passwd

---

### Post by Styler93gsx on 2008-08-11
I installed samba.  

Just tried to login and it says /home/stacy1 and asking me if I want to login with the /(root) directory as home directory. I remember making this directory last night during one of the how to's (making a backup copy in case I mess something up). I guess I did.  Now what do I do.

I"m assuming I need to point it at my origional home directory


How do I do that.  Should be stacy not stacy1

---

### Post by Styler93gsx on 2008-08-11
User's $HOME/.dmrc file is being ignored.  This prevents teh default session and language from being saved.  File should be ownedby user and have 644 permissions.  User's $HOMEdirectory must be owned by users and not writable by other users.

---

### Post by cgkades on 2008-08-11
For this I'd have to be on my actual computer, which unfortinutatly I'm not. If you're still having this issue in a few hours, I should be home (traffic depending), and I can try to resume helping you. But for now try googling "setting up samba in linux" or "setting up samba in ubuntu"

---

### Post by Styler93gsx on 2008-08-11
now I can't even login on the server itself.  Forces me to a terminal.  I can login through the terminal. 


Is there command to set all permissions back to default and start over

---

### Post by cgkades on 2008-08-11
your ubuntu machine forces you into a terminal when booting?

---

### Post by Styler93gsx on 2008-08-11
YES
put in user name and password an it gave me the response I just typed three replys up.


only way to login now is through the failsafe terminal

I have logged now and am looking at failsafe terminal with root permissions

---

### Post by Styler93gsx on 2008-08-11
Just to clarify it is xubuntu I don't know if that makes a difference to you.

---

### Post by cgkades on 2008-08-11
ok enter this, and paste the output
```

cd /home
ls -al
cd [your user name here]
ls -al

```

---

### Post by cgkades on 2008-08-11
> **Styler93gsx said:**
> Just to clarify it is xubuntu I don't know if that makes a difference to you.

Is there are reason you chose this instead of ubuntu? just wondering.

---

### Post by Styler93gsx on 2008-08-11
That is a lot to type I'll type it if I have to.  I have no way of pasting it.  I'm on the internet through my macbook.

---

### Post by Styler93gsx on 2008-08-11
It says I have an xcession error when I try to login.

---

### Post by cgkades on 2008-08-11
just paste the line with your username ex.
drwxr-xr-x 65 brett       brett       4096 2008-08-11 14:08 brett

---

### Post by Styler93gsx on 2008-08-11
Now I can't login through the GUI.  Says my home directory doesn't exist, do I want to use the roots home directory.

---

