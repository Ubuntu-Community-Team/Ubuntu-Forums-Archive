---
title: "error with tor"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by viswanathan on 2008-05-13
```
maplye@maplye-desktop:~$ tor
May 13 11:21:29.743 [notice] Tor v0.1.2.19. This is experimental software. Do not rely on it for strong anonymity.
May 13 11:21:29.745 [notice] Initialized libevent version 1.3e using method epoll. Good.
May 13 11:21:29.745 [notice] Opening Socks listener on 127.0.0.1:9050
May 13 11:21:29.745 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
May 13 11:21:29.745 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
May 13 11:21:29.745 [err] Reading config failed--see warnings above.
maplye@maplye-desktop:~$ 

```

guys this is what i get when in rum tor in terminal and even i cant install torbutton for firefox 3 beta five

---

### Post by zenwalker on 2008-05-13
Try to change the default port which its trying to get connected or else see if a tor is already running using ps -e cmd.

---

### Post by viswanathan on 2008-05-13
```
6105 ?        00:00:44 pidgin
 6111 ?        00:05:36 firefox
 6414 ?        00:00:06 tor
 6431 ?        00:00:00 privoxy
 7801 ?        00:00:00 gnome-terminal
 7803 ?        00:00:00 gnome-pty-helpe
```

sir tor is aldredy running but how do i enable this for fire fox 3 i dnt think there exits torbutton for firefox3b5 what to do sir

---

### Post by Xiong Chiamiov on 2008-05-13
Torbutton just makes things easier; it's not really necessary.

You can change the proxy options in edit -> preferences -> advanced -> network -> setting (at least in FF2).

---

### Post by viswanathan on 2008-05-13
sir i m totally noob to networking and proxys all i wanted to do is to hide my ip well any other way to hide ip rather than tor coz torbutton not workng for firefox3b5

---

### Post by Xiong Chiamiov on 2008-05-13
Is there any particular reason why you want to hide all of your HTTP traffic?  It can be a security risk, actually, if you run secure traffic through TOR, since your traffic can be sniffed.

If you know what port you set TOR up to run on, then that's what you put in the Firefox prefs.  Have you tried [this]("https://help.ubuntu.com/community/TOR") or [this]("http://www.ubuntugeek.com/tag/tor-ubuntu")?

---

### Post by viswanathan on 2008-05-13
> Is there any particular reason why you want to hide all of your HTTP traffic? 

when i was going through the book greyhat hacking there was a topic about exploiting ur comp through the ip adresses well even the precise location of where do u stay can be located using ip addresses sir wldnt it be better if u run anonymously wldnt it be a safer way coz im really scared after reading those articles in the book :-(

---

### Post by viswanathan on 2008-05-13
sir here is what i did ```
sudo apt-get install tor privoxy
sudo gedit /etc/privoxy/config
Added this line including the period at the end   forward-socks4a / localhost:9050 .

 logfile logfile 
jarfile jarfile "commented these lines "

then restarted privoxy   sudo /etc/init.d/privoxy restart

```

then went to mozilaa addons there i coldnt find torbutton for firefox3 earlier versions were not compatible

---

### Post by luvinit on 2008-05-13
Foxyproxy can be used instead of torbutton on firefox 3.

---

### Post by IamAcoconut on 2008-05-20
You don't need any freaking button unless you really need to switch fast beetween tor and direct connection. I personally use another browser (Epiphany) for non-torified traffic. Then I'm still being able to surf anonymously at the same time via FF.
Read what was posted: [https://help.ubuntu.com/community/TOR#head-9d5260df072c4b2bd99043d7de81a644965a2ad3](https://help.ubuntu.com/community/TOR#head-9d5260df072c4b2bd99043d7de81a644965a2ad3)
This is the basic info on Tor sites, and in 'man tor' :mad:

---

