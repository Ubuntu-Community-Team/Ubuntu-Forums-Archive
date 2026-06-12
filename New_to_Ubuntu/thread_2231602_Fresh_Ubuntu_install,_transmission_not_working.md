---
title: "Fresh Ubuntu install, transmission not working"
date: 2014-06-26
forum: New to Ubuntu
---

### Post by pyriteparody on 2014-06-26
I just installed Ubuntu (Trusty), and I cannot get Transmission to actually download the torrents.

I've tried magnet links and regular, all with plenty of seeders, but Im unable to connect and download anything.

Im brand new. I appreciate any help. Thanks :)

---

### Post by LastDino on 2014-06-26
How are you downloading? Do you get message to ''open with'' from browser when you click on magnet link? 

You can also download torrent and then open it from transmission. Very similar to how you would do it in windows.

---

### Post by pyriteparody on 2014-06-26
Solved!

As soon as I closed Tor, Transmission started working.

I could add the torrent files to transmission, but then they just sit there all at 0% with labeled "stalled". When I click on the Properties button (for the individual file) and go to the Trackers tab the trackers are all labeled "Could not connect to tracker"

So I went to Preferences - Network and started playing around with testing new and random ports, but all of them displayed as "closed" when I would test it, including the default 51413.

Would this be a firewall issue? I didnt add an firewalls and after a google search I tried:
```
$ ufw status
Status: Inactive
```
So that led nowhere.

Then after another google search I tried this to check which ports were open on my computer:
```
$ sudo netstat --tcp --listening --programs
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:9151          *:*                     LISTEN      3942/tor        
tcp        0      0 *:51413                 *:*                     LISTEN      6552/transmission-g
tcp        0      0 Penny:domain            *:*                     LISTEN      1416/dnsmasq    
tcp        0      0 localhost:ipp           *:*                     LISTEN      871/cupsd       
tcp        0      0 localhost:9050          *:*                     LISTEN      3698/tor        
tcp        0      0 localhost:9150          *:*                     LISTEN      3942/tor        
tcp6       0      0 [::]:51413              [::]:*                  LISTEN      6552/transmission-g
tcp6       0      0 ip6-localhost:ipp       [::]:*                  LISTEN      871/cupsd   
```

Seeing this is what made me think to close Tor, and this time when I reopened Transmission it started to download the files finally. Doesnt make sense to me, since the only thing I have configured to Tor is Firefox, but then again Im brand new.

Fun detective work for me. Cant wait to learn about Ubuntu now :)

---

### Post by Bucky Ball on 2014-06-27
> **pyriteparody said:**
> 

Fun detective work for me. Cant wait to learn about Ubuntu now :)

Your on your way. Good find. Add it to your new archive of fixes (I use Zim myself, which you'll find in the repositories, i.e. Software Centre or Synaptic Package Manager, depending on your flavour and prefernce).

If you like detective work and Ubuntu, you're in the right place. Good luck. ;)

---

### Post by LastDino on 2014-06-27
Using Tor is basically using different nods & routing through them to access the web, so I'm not sure why you would be surprised to see torrent downloaded from tor enabled browser may find it difficult to connect to trackers using the program that is asking connections to your normal address.

Btw, if you want to use Tor effectively, never download anything from it or use add-ons that download things, incoming package will give away your exact address if you do so.

---

