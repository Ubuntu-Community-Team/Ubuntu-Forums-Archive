---
title: "Ubuntu Login Issue"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by tad214 on 2008-05-21
**Hello, i would like to say first of all, that i got my ubuntu 8 [COLOR="DarkOrange"]installed[/COLOR], wooohoooo, and it is [COLOR="Red"]awesome[/COLOR]. Now my issue, i was logging in just fine in the beginning, and now, it keeps telling me [COLOR="Red"]wrong username or password[/COLOR]. I have even went into the terminal and typed sudo passwd and changed it then rebooted, and still, it tells me the same. It [COLOR="Lime"]will not [/COLOR]let me login for anything. Any suggestions on how to fix this? Thanks in advance for any available help. Dale**

---

### Post by pdtpatrick on 2008-05-21
Are you able to log in as root? Check your passwd file and ensure your username is in there.. then i would delete the username and add it again.. restart and try logging in.

---

### Post by tad214 on 2008-05-21
Well, when i change it using sudo passwd, it says it was changed succesfully. But when i go to login, it tells me wrong user or password. I am very new to ubuntu, so how do i go and check for the username?

---

### Post by tad214 on 2008-05-21
Is there anyone else that can help me resolve this issue?

---

### Post by tad214 on 2008-05-21
**Bump!!!**

---

### Post by sam_delta on 2008-05-21
try logging in with the user: "root" and the password you set while sudo pasword

remember that the password and username are case sensitive, so make sure your typing with the correct case

sam

---

### Post by james_vanb on 2008-05-21
Try this:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by tad214 on 2008-05-21
Hi, i tried the root for username, and it said the system administrator can not login from that screen. However, when i boot to the terminal in recovery mode, it ask for password, and i entered it, and it accepted it just fine. So, there must be a problem with the username portion. Is there a command to reset the username? Thanks again. Dale

---

### Post by anotherdisciple on 2008-05-21
I don't think ubuntu lets root login that way... sorry.

---

### Post by tad214 on 2008-05-21
So, what do i need to do now to fix this?

---

### Post by tad214 on 2008-05-21
Anyone else know what i can try or need to do? I am missing my ubuntu badley.

---

### Post by pdtpatrick on 2008-05-21
maybe we are not understanding you properly.. first of all im guessing you are using another computer to get onto the forum?

what init mode are you working in? 3 or 2? 

Im guessing you can only work via text terminal? when your system boots using the text based .. and you get the screen that says login .. what login are you using? root right?

---

### Post by tad214 on 2008-05-21
No, i have a dual boot with win xp. Like i said, i am all new to ubuntu. I am not sure about the mode thing 3 or 2? The best that i can explain it is as follows: I cannot login from normal boot screen. It says invalid user or password. So, i rebooted it in recovery mode, typed in sudo passwd and it accepted it. So, i would guess that the problem lies in the username portion. How or what do i type in to get the terminal only, that will ask for username and password? I tried logging in using root at the main login screen and it would not accept it. If my explanations is not detailed enough, please ask me what you need to know, because i really won't to get out of this bill gates box, and get back into ubuntu. Thanks again.

---

### Post by pdtpatrick on 2008-05-21
i hear you - well i mistakenly wiped out my windows pc - good thing i have a backup so now im stuck with ubuntu so i guess i have to use it which i love anyway.

When you get to the graphic login screen - press ctrl + alt + backspace.. that should kill X windows.. it would take you to the text login.. btw - ive noticed on my ubuntu when i first installed it, it didnt ask for root password so i had to go in an unlock the account and create a password for it. 

However if you cant log in via the terminal being root or anything else.. while in recovery mode, i would add a user using the useradd command.. and then create a password for the user .. if it accepts your settings.. restart the computer and try logging as the user you just created.. then once you are in, unlock the root account and create your password. Then add yourself to the sudoers account and modify the account that wasnt working. 

Does that make sense or should i explain better?

---

### Post by tad214 on 2008-05-21
If anyone has any further questions about my issue, please feel free to ask, because i really want to get back on ubuntu. Thanks again guys.

---

### Post by Sirhanz on 2008-05-21
OK, if you boot into recovery mode or if you can somehow get to a terminal line a simpler way do so. At the terminal enter ```
sudo adduser username
```. Replace username with your desired username, fill out the questions then accept changes and reboot. Seeing as you don't have an active login name you may need to login as root in the terminal using su, and then omit sudo from the code listed above. Hope this helps.

---

### Post by pdtpatrick on 2008-05-21
try this - 

sudo useradd username -p userpassword

if that accepts then restart and login as those .. by default, ubuntu locks the root so you going to have to use sudo to do your dirty work.. 

sudo -i should unlock your root previledges.. but make sure to lock it up after you are done by typing

sudo passwd -L root

---

### Post by tad214 on 2008-05-21
Ok, thank you guys. I will try this and let you know the results. Thanks again. Dale

---

### Post by stchman on 2008-05-21
> **tad214 said:**
> **Hello, i would like to say first of all, that i got my ubuntu 8 [COLOR="DarkOrange"]installed[/COLOR], wooohoooo, and it is [COLOR="Red"]awesome[/COLOR]. Now my issue, i was logging in just fine in the beginning, and now, it keeps telling me [COLOR="Red"]wrong username or password[/COLOR]. I have even went into the terminal and typed sudo passwd and changed it then rebooted, and still, it tells me the same. It [COLOR="Lime"]will not [/COLOR]let me login for anything. Any suggestions on how to fix this? Thanks in advance for any available help. Dale**

You can try this: (assume your username is tad214

```
sudo passwd tad214
```

Of course replace your tad214 with your true username.

---

### Post by tad214 on 2008-05-23
**Hello everyone, sorry i got delayed on getting back with you. [COLOR="DarkOrange"]Good news[/COLOR], the ideas you gave me worked like a charm. I am on ubuntu as we speak. Thank you so much. I do have one other question, and im not sure if i can ask it here, or start a new thread. How can i uninstall ubuntu, and still keep kubuntu. I like it a whole lot better because of the graphics and the AWESOME games it has for it? thanks again everyone for saving me!!!! Dale**

**P.S. Is it using that much more space if i just keep it on here? I just hate to have to switch back and forth. :lolflag:**

---

### Post by tad214 on 2008-05-23
***Anyone?***

---

### Post by Raccoon1400 on 2008-05-23
> **anotherdisciple said:**
> I don't think ubuntu lets root login that way... sorry.

It can if you enable it in system > admin > login window > security

or, If you can't access the DE to set this, create a new user with "adduser" and delete it after. There is probably a textfile somewhere that can be edited to allow root login.

Can you login in terminal?

---

### Post by tad214 on 2008-05-24
Thank you, i got the login issue fixed, thanks to you guys. How can i uninstall ubuntu, and still keep kubuntu. I like it a whole lot better because of the graphics and the AWESOME games it has for it? thanks again everyone for saving me!!!! Dale
 
 P.S. Is it using that much more space if i just keep it on here? I just hate to have to switch back and forth.

---

### Post by tad214 on 2008-05-24
**Anyone?**

---

### Post by tad214 on 2008-05-24
I may not be doing this right. two questions in one thread, so i will start a new thread. Dale

---

### Post by Witling on 2008-05-24
At the risk of being obvious, you do know that Linux, unlike soe other operating systems,  considers the name Ted different from ted? Have you tried variations on capitalization?

---

