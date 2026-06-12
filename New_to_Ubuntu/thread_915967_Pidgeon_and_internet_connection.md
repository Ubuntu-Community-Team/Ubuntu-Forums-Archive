---
title: "Pidgeon and internet connection"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by misswham on 2008-09-10
I noticed 2 weeks ago that when using pidgin it disconnects itself sometimes and i have to open it up again also i will send a response and the poeple on the other end are getting it 10 secs later or some not at all.  I also have been suffering from internet connection loss but my light on my modem is still solid. I also have a hard time now connecting to pidgin.  Like today I had to open it up and close it a couple of times before it connected and it finally did then when I closed it for an hour and opened it back up it wouldnt.  It just said connecting.  Now my friends list is there but it never fully connected.  I called comcast and they ran test and said my modem is getting signal.  I went and exchanged it anyway, got a new one and the same thing is happening, I have also bypassed the router and have changed all ethernet cords.  So i dont know what is going on but this just started 2 weeks ago.  Does this ring a bell with anyone?

---

### Post by pzs on 2008-09-10
Pidgin stopped connecting for me recently. I fixed it by doing Edit Account, selecting the Advanced tab and selecting "Use HTTP Method". Don't know if this will help you, but might be worth a try.

---

### Post by misswham on 2008-09-10
i went to advanced and when i clicked http it asked me for host and port i dont know what to do from there.

---

### Post by misswham on 2008-09-10
i just changed the gnome proxy to no proxy.  what is proxy and did i do something that will mess it up?

---

### Post by acidsolution on 2008-09-10
use no proxy option 
this helped me :)

---

### Post by misswham on 2008-09-10
i changed everything to no proxy.  i will see if this works.  Does anyone have any ideas on the internet connection?

---

### Post by pzs on 2008-09-11
The server and port depends on the kind of account you're using. For MSN (on my system, at least) it's:

server: messenger.hotmail.com
port: 1863

---

### Post by barbedsaber on 2008-09-11
my advice
ditch pidgin
try empathy
```
sudo apt-get install empathy
```

pidgin is getting more and more outdated, it works for some people, but excessive lag, and network dropouts made me switch.
I am not *telling* you that this will solve all your problems, but empathy (or something else) might just become your new favorite IM client.
Don't want to switch? by all means, wait for help here, it should be around withing the next few minutes.

---

### Post by misswham on 2008-09-11
Hi. I just installed empathy and it says no accts configured.  to add a new acct you first have to install a backend for each protocol you want to use.  

i dont know what this is.

can u tell me what a backend is and how do i install it.  i have 2 yahoo id's, one aim, one msn and one google.

---

### Post by misswham on 2008-09-11
can anyone help me with the installation>

---

### Post by essexite on 2008-10-26
> **misswham said:**
> can u tell me what a backend is and how do i install it.  i have 2 yahoo id's, one aim, one msn and one google.

```
sudo apt-get install telepathy-butterfly telepathy-gabble telepathy-haze
```
Or, for *all* available protocols support:
```
sudo apt-get install telepathy-core
```

---

