---
title: "No Sound :("
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Telrunn on 2008-10-02
2 Issues (actually 3 if you include the fact I'm new at this O_o)

The sound works fine, I can play the sample video's and music, I can even put in a music CD and it works fine.

Problem 1: I have a few mp3 files on my JetFlash thumb drive, when I try of get to them, the first thing that pops up is this message.
"Count not mount JetFlash TS8GJFV"

Problem 2: I can not bring up any Store bought movies to watch, no message, just nothing happens. Yet the CD for ubuntu works just fine.

I'm using Ubuntu 7.10 on an Acer Aspire 3000 notebook, with currently a dead network card, so any downloadable update will have to be on my XP machine or 2000 machine, put on my thumb drive and brought over that way.

At 57 you'd think I'd pick lawn bowling for a challenge but nnnoooooo I had to pick Linux, lol but it's all fun :)

Sincerely & Respectfully
 Telrunn

PS: I have gone through the forums for about almost an hour, I could not find anything close to my issue. If this issue is posted somewhere else, I apologize ahead of time.

---

### Post by Michael.Godawski on 2008-10-02
hey Telrunn,

for the first issue have a look at this older forum thread.

[LIST]
[*][http://www.linuxforums.org/forum/peripherals-hardware/16001-usb-memory-stick-unrecognised.html](http://www.linuxforums.org/forum/peripherals-hardware/16001-usb-memory-stick-unrecognised.html)
[/LIST]
It is basically the manual approach to mount a usb stick. If you have any questions regarding the terminal commands just ask.

---

### Post by Telrunn on 2008-10-02
Thanks for the quick reply, and the link has gotten me in the right direction.

When I went into terminal I tried the "mkdir /mnt/jetflash" my response was Permission denied, which has me scratching my bald head as I know I'm logged in as Admin.

I'll look around on my notebook for a bit to see what I'm doing wrong.

Thanks Michael

---

### Post by Dark006 on 2008-10-02
Just a guess, but try putting the word "sudo" (no quotes) before mkdir.

---

### Post by Crafty Kisses on 2008-10-02
What are the results of this command?
```
lspci
```

---

### Post by Telrunn on 2008-10-02
the result was

[sudo] password for xxxxxxx:



xxxxx = my user name, but will not allow me to do anything beyond that

---

### Post by niteshifter on 2008-10-02
> **Telrunn said:**
> the result was

[sudo] password for xxxxxxx:



xxxxx = my user name, but will not allow me to do anything beyond that

Go ahead and type the same password you use to log in with, it does not echo the characters to the screen.

---

### Post by Telrunn on 2008-10-02
my entery:

sudo mkdir /mnt/jetflash


sudo - I use my password, the result I got was that my password: command not found

---

### Post by niteshifter on 2008-10-02
Hi,

Ok, let's do this. In the example below the user name is dlk and the  password will be "password" and highlighted in red. The {Enter} is the Enter key press:
```
dlk@dlk-lt-1420:~$ sudo mkdir /mnt/jetflash
[sudo] password for dlk:[COLOR="Red"]password[/COLOR]{Enter}
dlk@dlk-lt-1420:~$ 
```

That the system responded with your password as command not found implies this happened:
```
[sudo] password for dlk:{Enter}[COLOR="Red"]password[/COLOR]{Enter}
```

When you see this:
```
[sudo] password for dlk:
```
type your password in (the characters typed will not appear) then press Enter.

---

### Post by munchkinmunchkin on 2008-10-02
Don't know if this is relevant, but I had problems with sound when I installed 8.04.

The problem, I couldn't have a YouTube page playing with sound, and have Totem movie playing with sound at the same time, as only one application would have sound.

The solution which works, I changed all the sound options in System >> Preferences >> Sound, to ALSA.

Don't know if it's the best course of action, but everything is fine now.

---

