---
title: "Root access by default...How do I grant it?"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by LinuxUser666 on 2013-06-06
Hello fellow Ubuntu users. I am running on Ubuntu 12.04 LTS with Xfce4 DE and I would like to have root access all the time and I am aware of all the risks that might bring.
I am also familiar with the "sudoers" file in /etc directory, it says that I must edit it with visudo somehow to grant me all-the-time-root access.
Few questions: 
How should I edit it to grant myself root by default?
I MUST edit it with "visudo" or can I use something else?
Can I revert it back and how? 

Thank you, my regards to you.

):P

---

### Post by overdrank on 2013-06-06
Maybe this can help[_ RootSudo_]("https://help.ubuntu.com/community/RootSudo")

---

### Post by matt_symes on 2013-06-06
Hi

> I would like to have root access all the time

Why ?

Kind regards

---

### Post by slickymaster on 2013-06-06
That's normally not a good idea and you should consider very carefully before doing it. If you have a number of commands which normally require sudo you can type ```
sudo -i
``` before the first command then exit after the last to avoid repeatedly typing sudo. To run a GUI application with root privileges just open the terminal and enter```
 gksu
``` or ```
gksudo
``` followed by the name of your program. As you can see it is almost never necessary to enable the root login.

With that said, to enable the root unlimited passwordless access to root privileges open a terminal window and run the follwoing command:
```
sudo visudo
```and add the folowing line:```
your_user_name   ALL = NOPASSWD: ALL
```

---

### Post by whatthefunk on 2013-06-06
Thats a bad idea.  For somethings, you definitely do not want to be root.  Is it so hard to type "sudo"?

---

### Post by LinuxUser666 on 2013-06-06
Ok 1st of all thanks to slickymaster for your informations regarding the given matter at hand, you are very kind.
2nd of all its nobody's concern why do i need root access on my own computer, although I respect the concern, but as I said I am aware of risks, hazzards and so on.
3rd of all whatthefunk, its not hard to type sudo, its hard to type in the password, 'cause I am lazy...sometimes.

Thank you, my regards.

---

### Post by coffeecat on 2013-06-06
> **LinuxUser666 said:**
> 2nd of all its nobody's concern why do i need root access on my own computer,

That may be so, but it is our concern when things are posted here which can mislead inexperienced users into doing inappropriate things. You are not the only person to be reading and acting on advice posted here. There will be many silent surfers, both forum members and guests who arrive by means of a google search, reading this thread. Which is why we have a forum policy:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

> The goal is to educate new users.

Our "line in the sand" is with tutorials or posts that show people how to LOG IN to a graphical desktop (gnome, KDE, etc) as root. This is completely inappropriate and unnecessary.

---

### Post by matt_symes on 2013-06-06
Hi

> 2nd of all its nobody's concern why do i need root access on my own computer

I'm just interested in why you need it and i don't.

Kind regards

---

### Post by Rebelli0us on 2013-06-06
> **LinuxUser666 said:**
> Ok 1st of all thanks to slickymaster for your informations regarding the given matter at hand, you are very kind.
2nd of all its nobody's concern why do i need root access on my own computer, although I respect the concern, but as I said I am aware of risks, hazzards and so on.
3rd of all whatthefunk, its not hard to type sudo, its hard to type in the password, 'cause I am lazy...sometimes.

Thank you, my regards.

It's **your** computer and it's your right to decide how much security you want/need. If you don't want to be forced to login 100 times a day:

```
sudo visudo
```

Then add a new line at **the end of the file**:

```
<YOUR USER NAME>    ALL=(ALL)NOPASSWD: ALL
```

That will be the last time you'll be asked for a password.

---

### Post by matt_symes on 2013-06-06
Hi

> It's **your** computer and it's your right to decide how much security you want/need

Of course it's their right to weaken the security of their computer as much as they want, just as it is their right to leave the front door open while going shopping.

It's hardly best practice though.

Kind regards

---

### Post by Zill on 2013-06-06
> **matt_symes said:**
> ...Of course it's their right to weaken the security of their computer as much as they want, just as it is their right to leave the front door open while going shopping...
...and, by disabling a major Linux security feature, it just makes it more likely that this will be yet another spambot PC "owned" by some kid on the other side of the world. ;-)

---

### Post by lisati on 2013-06-06
> **Zill said:**
> ...and, by disabling a major Linux security feature, it just makes it more likely that this will be yet another spambot PC "owned" by some kid on the other side of the world. ;-)

Exactly. It probably wouldn't hurt to check your IP address on blacklists from time to time, just to make sure that this hasn't already happened.

Most of the information needed can be found in the already mentioned page @ [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by 3rdalbum on 2013-06-06
Laziness is an extremely terrible reason to disable a security system. It's not 1998 anymore where the worst thing you can get is a Word macro virus.

---

### Post by coffeecat on 2013-06-07
Indeed, and since the OP has received some good advice....

Thread closed.

---

