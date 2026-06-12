---
title: "[SOLVED] Not able tot resset my password"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by bodie on 2008-08-29
:confused:Hy, i also forgotten my username and password.

I am reading al the threads about resetting with the 

[B]grub message, press the escape key. 
Select the option that says (recovery mode). 
Your PC will boot into a shell. Once you get a command prompt[/B] 

But when i enter the recovery mode the system reboot en give the folowing words;

[B]Give root password for maintenance
(or type control-D to continue):[/B]

On this point i can't write anything on the terminal???

Wat am i doing wrong? please help.

Greetings and all the best, ErikB.

---

### Post by Vivaldi Gloria on 2008-08-29
> **bodie said:**
> But when i enter the recovery mode the system reboot en give the folowing words;

[B]Give root password for maintenance
(or type control-D to continue):[/B]


1) What happens when you press CTRL+D when you see that message?

2) Which version of ubuntu are you using?

3) Have you changed the root password in the past?

---

### Post by bodie on 2008-08-29
When i type ctrl D it will reboot and i get the normal inlog screen of ubuntu.

It's version 7.10

The password is changed before my holiday, that is the reason i can't remeber it anymore.

---

### Post by bobnutfield on 2008-08-29
Follow the instructions on this link and you can change your password or add yourself as a new user with a password:

[http://www.ubuntu-unleashed.com/2007/09/recover-forgotten-ubuntu-password.html]("http://www.ubuntu-unleashed.com/2007/09/recover-forgotten-ubuntu-password.html")

---

### Post by nicedude on 2008-08-29
I was way off

---

### Post by Vivaldi Gloria on 2008-08-29
Another method. 


**Part 1**

You can find the pictures of this part at

[http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html](http://www.watchingthenet.com/ubuntu-guide-for-windows-users-reset-your-password-when-you-have-forgotten-it.html)

Press ESC at the grub prompt.

Press e for edit.

Highlight the line that begins kernel ………, press e

Go to the very end of the line, add 

```
rw init=/bin/bash
```

press enter, then press b to boot your system.

Your system will boot up to a passwordless root shell.

Don't look at that the rest of that web site & pictures anymore. Continue with the following:


**Part 2**

Type

```
cat /etc/passwd | cut -d: -f1
```

Find your username from the list.

Type in 

```
passwd <username>
```

Set your password.

Type in 

```
reboot
```

to restart.

---

### Post by Vivaldi Gloria on 2008-08-29
> **nicedude said:**
> I may be wrong but if what I gather is that you don't know your admin password then I think you may be sunk.

I couldn't understand that point also clearly. 

bodie, Have you changed your root/admin password?

There is a way to change the admin password using the live cd. I don't remember now. I'll try to find it.

---

### Post by nicedude on 2008-08-29
EDIT - Past comments removed due to them being wrong

I was wrong it is easy as windows.

I don't think I like that though as even though you could mount the disk with a live CD that isn't as good as being able to log in to someones account since they might have all sorts of email and internet site passwords set to enter automatically and thereby you could abuse their accounts etc. Where if you can only mount from live CD you could only copy the encrypted password files but I don't think it would be nearly as easy to use them to cause havoc with their various accounts.

I think I might have to research full disk encryption to nullify such tricks for my Ubuntu, but thanks for the tip about the site with how to do it as I am sure it will come in handy helping someone one day :-)

---

### Post by bodie on 2008-08-29
I tried the bobnutfield methode but i'm losing track, to tired.

I try tomorow the rest of the link, thanks so far and all the best!!!

Greetings ErikB.

---

### Post by bobnutfield on 2008-08-29
Strongly consider the method posted by Vivaldi Gloria.  It is easier, and just as effective.  I find it very good info to keep.

---

### Post by Vivaldi Gloria on 2008-08-29
Ok. I found the live cd method here:

[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

---

### Post by bodie on 2008-08-31
:guitar::lolflag:

Thanks for all the support to all, i'm speechless.

The help from gloria was perfect en i managed to break through the password.


You must remember indeed your username, ik was forgotten this too but it's easier to remember than both user and passwd!

So afther 4 hits i found (remember) it!

Special thanks to Gloria and al the best!! 

Greetings ErikB.

---

### Post by Vivaldi Gloria on 2008-08-31
You're welcome.

---

