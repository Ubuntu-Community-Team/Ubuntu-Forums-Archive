---
title: "Gmail not connecting in Ubuntu"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by niceguy123 on 2008-06-06
I'm working in Firefox and have 3 computers (two Ubuntu and one XP)on a router with a DSL line. After upgrading to Hardy 8.04 and some twiking I have firefox 2 on one box and FF 3 on the other.

Problem: Gmail won't load on ether Ubuntu-FF boxes (but, on the XP-FF it does). 

Any ideas?

---

### Post by iaculallad on 2008-06-06
Can you ping gmail.com on your terminal? Are you able to load other webpages aside from gmail?

---

### Post by niceguy123 on 2008-06-06
> **iaculallad said:**
> Can you ping gmail.com on your terminal? Are you able to load other webpages aside from gmail?


This seems really strange. I can access google, but can't reach gmail (on this computer, at the same time I can access gmail from and XP on the same network).

```
ping: unknown host http://mail.google.com

```

---

### Post by sayakb on 2008-06-06
Remove **http:// **and ping again.

---

### Post by niceguy123 on 2008-06-06
> **LinuxIsInnovation said:**
> Remove **http:// **and ping again.

OK, Now it's filling a page of terminal and still going.

```
PING googlemail.l.google.com (209.85.137.18) 56(84) bytes of data.
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=1 ttl=245 time=81.5 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=2 ttl=245 time=83.1 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=3 ttl=245 time=83.2 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=4 ttl=245 time=84.3 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=5 ttl=245 time=82.3 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=6 ttl=245 time=83.4 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=7 ttl=245 time=83.5 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=8 ttl=245 time=88.4 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=9 ttl=245 time=82.7 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=10 ttl=245 time=83.8 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=11 ttl=245 time=83.9 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=12 ttl=245 time=83.0 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=13 ttl=245 time=84.1 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=14 ttl=245 time=82.1 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=15 ttl=245 time=84.2 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=16 ttl=245 time=82.2 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=17 ttl=245 time=81.4 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=18 ttl=245 time=84.3 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=19 ttl=245 time=82.6 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=20 ttl=245 time=82.4 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=21 ttl=245 time=83.8 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=22 ttl=245 time=85.9 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=23 ttl=245 time=84.9 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=24 ttl=245 time=82.0 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=25 ttl=245 time=86.0 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=26 ttl=245 time=82.2 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=27 ttl=245 time=82.2 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=28 ttl=245 time=83.4 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=29 ttl=245 time=82.4 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=30 ttl=245 time=81.5 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=31 ttl=245 time=83.3 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=32 ttl=245 time=82.7 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=33 ttl=245 time=83.5 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=34 ttl=245 time=86.8 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=35 ttl=245 time=83.7 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=36 ttl=245 time=82.8 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=37 ttl=245 time=82.1 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=38 ttl=245 time=83.2 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=39 ttl=245 time=82.3 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=40 ttl=245 time=84.4 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=41 ttl=245 time=83.5 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=42 ttl=245 time=85.5 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=43 ttl=245 time=82.4 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=44 ttl=245 time=102 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=45 ttl=245 time=83.5 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=46 ttl=245 time=84.9 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=47 ttl=245 time=109 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=48 ttl=245 time=112 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=49 ttl=245 time=84.1 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=50 ttl=245 time=83.2 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=51 ttl=245 time=81.3 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=52 ttl=245 time=83.4 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=53 ttl=245 time=82.5 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=54 ttl=245 time=82.2 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=55 ttl=245 time=81.6 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=56 ttl=245 time=86.0 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=57 ttl=245 time=83.8 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=58 ttl=245 time=84.9 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=59 ttl=245 time=83.0 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=60 ttl=245 time=84.1 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=61 ttl=245 time=84.1 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=62 ttl=245 time=94.6 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=63 ttl=245 time=84.3 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=64 ttl=245 time=83.4 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=65 ttl=245 time=82.5 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=66 ttl=245 time=82.6 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=67 ttl=245 time=82.7 ms
64 bytes from mg-in-f18.google.com (209.85.137.18): icmp_seq=68 ttl=245 time=82.8 ms

```

---

### Post by doorman on 2008-06-06
I had the same problem.

My solution was to change from http to https, so instead of the address

```
http://mail.google.com
```

you type in this one:

```
https://mail.google.com
```

That did the trick for me

---

### Post by sayakb on 2008-06-06
Delete /home/yourusername/.mozilla/firefox/profiles.ini and try again. Also in firefox, press Ctrl+Shift+Del and clear the cache.

---

### Post by niceguy123 on 2008-06-06
> **LinuxIsInnovation said:**
> Delete /home/yourusername/.mozilla/firefox/profiles.ini and try again. Also in firefox, press Ctrl+Shift+Del and clear the cache.

Is that the same as ```
mv ~/.mozilla/firefox ~/.mozilla/firefox.backup
```
'cause I just did that for something else and its not helping me here.

In anycase, I went to home/myusername and found no .mozilla folder there.

---

### Post by sayakb on 2008-06-06
Press Ctrl+H.. You will find the .mozilla folder there ;)

---

### Post by niceguy123 on 2008-06-06
Thanks, I did that > **LinuxIsInnovation said:**
> Press Ctrl+H.. You will find the .mozilla folder there ;)

and that

```
Delete /home/yourusername/.mozilla/firefox/profiles.ini and try again. Also in firefox, press Ctrl+Shift+Del and clear the cache.
```

and even restarted FF but, still no gmail.

---

### Post by niceguy123 on 2008-06-06
This diffinally seems to be a Ubuntu (and not FF) problem. I totaly removed FF2 and anything that had to do with it via synapatic package manager and then added FF3. Same problem. Then I added epiphany and tryed there. The same - no gmail!

I've been trying to download Opera from the site and having a hard time with that too.

---

### Post by sayakb on 2008-06-06
Have you installed the restricted extras package? (though it isn't quite needed for Gmail)
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by niceguy123 on 2008-06-06
> **LinuxIsInnovation said:**
> Have you installed the restricted extras package? (though it isn't quite needed for Gmail)
```
sudo apt-get install ubuntu-restricted-extras
```

Done, but still no gmail. :confused:

---

### Post by avtolle on 2008-06-06
Hmm, seems like there might be a problem with your ability to reach the router with the Ubuntu boxes. I note that the XP box is hooked to the router by a cable; have you tried to hook one of your Ubuntu machines to the router with a cable and tried to access gmail that way?

EDIT: Sorry, misread your first post. I'd still try to use a wired connection with the Ubuntu box to see if you can get to gmail that way.

---

### Post by SlappyPappy on 2008-06-06
I'm a religious Gmail, Calendar, Google Docs guy and never a problem getting in on my system. 

Can't tell you what you're doing wrong. Keep at it, you'll figure it out!  :)

---

### Post by niceguy123 on 2008-06-06
> **avtolle said:**
> Hmm, seems like there might be a problem with your ability to reach the router with the Ubuntu boxes. I note that the XP box is hooked to the router by a cable; have you tried to hook one of your Ubuntu machines to the router with a cable and tried to access gmail that way?

EDIT: Sorry, misread your first post. I'd still try to use a wired connection with the Ubuntu box to see if you can get to gmail that way.

They're all conected to the router by wire. I am able to browse websites on the Ubuntu (which two days ago was feisty 7.04 and worked with gmail too). But, I can reach gmail now. I can view other google sites. 

1. The phisical wire and DSL conections have not changed.
2. Ubuntu has been upgraded to Hardy 8.04
3. I can access the internet and browse websites, but not gmail.
4. I have tried with another browser with the same results.
5. gmail comes up on an XP computer wired to the same DSL line and router.

:confused:

---

### Post by avtolle on 2008-06-06
Thank you for resolving my misunderstanding. I'm confused as to why you are having that difficulty with gmail as well. I've no problems from 8.04 and FF3 getting there at all. I'll ponder, and if anything useful occurs to me, will be back; meanwhile, there surely is someone who can help you.

---

### Post by django0909 on 2008-06-06
Can you view gmail on the ubuntu boxes in html-only mode? If so, you might have a problem with the javascript side of things. Is javascript set up properly?

---

### Post by ne0h on 2008-06-06
Try:
[http://64.233.171.83/](http://64.233.171.83/)

---

### Post by django0909 on 2008-06-06
That just brings up google.com for me.

---

### Post by ne0h on 2008-06-06
I'm having the exact same problem with another site not gmail.com, I tried that site's IP and worked.

---

