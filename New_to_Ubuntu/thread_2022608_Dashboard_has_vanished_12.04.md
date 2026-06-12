---
title: "Dashboard has vanished 12.04"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by Tahinimoon on 2012-07-11
Today when I logged in:
1. My Dashboard is gone. 
2. All I have is my desktop background and the saved text folders I work with.
3. I can right click to change my desktop back ground and get to 'all settings'.
4. I can't get to my dash board however. 
5. At the moment i am logged in to a 'guest' session - there I can access the net, dashbaord etc, but I can't access any thing else - I understand that this is because I'm logged in on a guest session. 

What have I done? 
How can I fix this?

---

### Post by nothingspecial on 2012-07-11
Press Ctrl-Alt-F1 and log into to your account

type ```
unity --reset
```

followed by
```

sudo service lightdm restart
```

and see if that fixes it.

---

### Post by Tahinimoon on 2012-07-11
I tried that - it doesn't work - gives error reading.

Am I doing it correctly?
1. While in 'guest session' I pressed Ctrl-Alt-F1 - followed the prompts and added the lines. it initialises some things then stops as if waiting for me to do something else. 
2. I tried logging in as i normally would - and did the same things you suggested, but still no result. 
3. I am doing something wrong but don't know what?

So frustrating not knowing what I'm doing. :{

---

### Post by nothingspecial on 2012-07-11
> **Tahinimoon said:**
> 

What have I done? 


Can you think of any settings you may have changed before this happened?

---

### Post by Tahinimoon on 2012-07-11
Well, last night I did notice something odd - When I tried shut down my pc instead of shutting down it took me back to the log in screen instead of shutting down. So I logged back in and out a few times until I finally logged into a guest session and shut down from there.

---

### Post by Tahinimoon on 2012-07-11
Isn't there some way that I can just create a 'new' login and obtain access to all my info from new.  Mm.. hard to explain : So for eg: turn a guest session into my new login system? Something like that?

---

### Post by raja.genupula on 2012-07-11
> **nothingspecial said:**
> Press Ctrl-Alt-F1 and log into to your account

type ```
unity --reset
```followed by
```

sudo service lightdm restart
```and see if that fixes it.

@OP  >   While in 'guest session' I pressed Ctrl-Alt-F1 -see you have to login as with your username not as guest . after login do as our friend said . i mean

type ctrl+alt+F1

```
untiy --reset
sudo restart lightdm 
```If in case of errors try to remind the error lines only and post them here ,
:)

---

### Post by Tahinimoon on 2012-07-11
I tried it after logging in correctly to my oem.  Wish I could post a screen shot but I can't so:

This is what is says: - not 'exactly' word for word
WARNING: No display variables set - setting to 0
unity-panel service: no process found
checking settings need to be migrated.....no
checking internal files need to be migrated....no
backend : gconf
Integration: true
Profile: default
Adding Plugin:
Initialising core options - done
initialising composite - done
initialising opengl - done
initialising wobbly - done              (lolled at this one - sounds like my pc at the moment)
-



and there it stops

---

### Post by Tahinimoon on 2012-07-11
Not sure if this makes any difference: But my system info is
Processor - Intel Core 2 CPU
GeForce 7300GT graphics card
Nvidia Driver version: 295.40

---

### Post by arpanaut on 2012-07-11
As I recall, 295.40 will not run unity properly.
Have you run updates since install?

That should update your driver to 295.49 and you should good to go.
Log into Unity-2D run upgrade manager or in a terminal run:

```
sudo apt-get update && sudo apt-get upgrade
```Do a restart then try to login to regular Unity session.
If that doesn’t fix things there are other steps that can be taken.

Edit:
If using the terminal for this, because of kernel updates you may need to run:
```
sudo apt-get dist-upgrade
```

to get all the updates and to get the driver to install properly.

---

### Post by NikTh on 2012-07-11
_First thing : _Try **arpanaut's** suggestion about upgrade . 


> **Tahinimoon said:**
> Isn't there some way that I can just create a 'new' login and obtain access to all my info from new.  Mm.. hard to explain : So for eg: turn a guest session into my new login system? Something like that?

Yes you can do that. 
From Virtual Terminal (Ctrl+alt+F1) login with username & password. Create a new user with these commands 
```
sudo service lightdm stop
sudo adduser newuser
sudo passwd newuser
sudo service lightdm start
```Then login from new user and go to User Accounts and promote to administrator. Copy-paste all your personal data from old user and you will be ok.
***newuser** = whatever username you like.

---

### Post by Tahinimoon on 2012-07-12
Thanks for all the suggestions, after trying them out unsuccessfully, I eventually resorted to attempting to create a new user -got stuck on various hitches when it came to copy pasting from old user to new user as some files needed permissions etc. However, to summarize - At some point after trying to create the necessary permissions I had to restart my pc, I logged into my old user account just to check it one more time - and it was working!!!! I do not understand how, or what it is that i did. I do not know whether to be thrilled or concerned. :} I am perplexed. 

1. One thing I did notice was that the last time I checked  my Nvidia Driver version: was 295.40 but now it says it is version  302.17? Is that good or bad?

2. I don't want to open a new ticket - but I was wondering - is there something i can do to back up important things in case of another serious or more serious issue. Things like emails that i have received, mail contacts and bookmarks etc? I don't have an external harddrive to save things on. So am hoping for some other solution - is there one?

---

### Post by NikTh on 2012-07-12
> **Tahinimoon said:**
>  
1. One thing I did notice was that the last time I checked  my Nvidia Driver version: was 295.40 but now it says it is version  302.17? Is that good or bad? Good. Cause driver 295.40 had reported as problematic.

> **Tahinimoon said:**
>  2. I don't want to open a new ticket - but I was wondering - is there something i can do to back up important things in case of another serious or more serious issue. Things like emails that i have received, mail contacts and bookmarks etc? I don't have an external harddrive to save things on. So am hoping for some other solution - is there one?

I think Ubuntu has integrated utility for that. Click on Dashboard(now that works!) and write **backup**

Glad you correct this 
:)

---

### Post by Tahinimoon on 2012-07-14
> **NikTh said:**
> Good. Cause driver 295.40 had reported as problematic.



I think Ubuntu has integrated utility for that. Click on Dashboard(now that works!) and write **backup**

Glad you correct this 
:)
Thanks, will try the backup suggested. And close this thread. :}

---

