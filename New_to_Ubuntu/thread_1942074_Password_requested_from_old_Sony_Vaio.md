---
title: "Password requested from old Sony Vaio"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by PepaPerth on 2012-03-16
Hi, 

I recycled a 2008 Sony Vaio VGN-NR37G-S which came originally with Vista

In 2011, asked a technician to uninstall Vista and install Ubuntu 11.04. Everything worked fantastic and forgot about it because had a happy 11 years old enjoying his "new" laptop. 

However, the system asks for password every time that you want to do something. And we don't have any password and my installing friend/technician has no idea about it. 

Then, how have been using it since we installed 11.04? 

Well, when system starts it opens all the programs and that's fine. 

When asks for a password i.e. when you leave it unattended in stand by we simply go and Restart the computer using the commands at the menu and in <30 seconds we are on the main menu again.

My son use the laptop for games and now wants to download another browser i.e. Chromium to play against himself. But there is no way that we can download/install/uninstall anything because we need to authorise it with the unknown/unexistent password. 

How can we overcome this? 

I have a CD of 11.10 in case that installing a new version helps, but still will ask me for password...

The other "solution" would be to have another browser in 10.04 but we just have Firefox...

Thanks

Nicolas (NZ)

---

### Post by MG&amp;TL on 2012-03-16
Hi! You probably just need to reset your password, although I'm a little confused about your multiple versions...

Hold shift immediately after bootup to get to a black/purple screen  (grub). Select "Ubuntu blah-deblah, kernel blah, (Recovery Mode)".  Select "root prompt", then type:
```

passwd <username> 
```replacing <username> with your username, (exactly, and case-sensitive), then enter a password twice. (you can't see it).

After that, reboot, and use your new password. 

If you need help with that, give us a shout. :)

---

### Post by PepaPerth on 2012-03-16
Ok, thanks for this, so followed your steps and I am at

GNU GRUB version 1.99~rc1-13ubuntu3 
I chose
Ubuntu, with Linux 2.6.38-8-generic (recovery mode)

then 
Recovery Menu

root  Drop to root shell prompt

root@sony-VGN-NR37G-S:~#passwd<Sony> then did Enter and 

bash:syntax error near unexpected token "new line"

tried again with the same
root@sony-VGN-NR37G-S:~#passwd<Sony> then did Enter and

bash: Sony: No such file or directory

I also wrote the password after <Sony> and actually I can see it...

So I'm stuck here, sorry!

Nicolas (NZ)

---

### Post by MG&amp;TL on 2012-03-16
Ah, sorry...if your username is "Sony", just write:

```
passwd Sony
```

-it's just my way of putting attention to a bit of code, is <>.

---

### Post by PepaPerth on 2012-03-16
ok, did

passwd Sony

Enter

passwd: user "Sony" does not exist

---

### Post by MG&amp;TL on 2012-03-16
Okay, what does:

```
ls /home
```show?

(I'm basically trying to find what you username is.)

---

### Post by PepaPerth on 2012-03-16
did it again

passwd Sony 123321 

(I still can see the password) 
and then brought me a number of options

-a
-d

etc

tried a few of them but no result...

---

### Post by MG&amp;TL on 2012-03-16
Okay, I need to see the output of:

```
ls /home
```to know your username. Then I can help you. :)

Btw, the options are the help screen, you're meant to type "passwd  user", then return, then it will prompt you for passwords.

---

### Post by garyed on 2012-03-16
Just get to a terminal & type:
```
whoami
```
that will give you your user name
Hopefully you have sudo priviliges.

---

### Post by MG&amp;TL on 2012-03-16
Yes, but we're at a root prompt. I was hoping to spare the OP having to boot again. whoami at root will give...root. :)

---

### Post by PepaPerth on 2012-03-16
Slowly I'm getting it...

root@sony-VGN-NR37G-S:~# ls /home
sony

(and she wrote sony in a lovely blue!)

so I assume that the username is actually sony, right?

---

### Post by PepaPerth on 2012-03-16
password updated successfully!!! 

vivaaaa!!

now let's see if actually works, stay tuned!

...

---

### Post by PepaPerth on 2012-03-16
Aaaaand...IT DID!

Thanks friends from the forum!!

(this is Esteban's Dad back again...he left when a friend came to invite him to play at the park ;-)

Greetings from New Zealand!

---

### Post by MG&amp;TL on 2012-03-17
No problem, hope your son enjoys his chrome. :)

---

