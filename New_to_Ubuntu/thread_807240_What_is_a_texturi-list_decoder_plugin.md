---
title: "What is a text/uri-list decoder plugin?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by tea for one on 2008-05-25
I tried to listen to an audio clip from Amazon.co.uk and I received the following message:-

"The playback of this movie requires a text/uri-list decoder plugin which is not installed"

What is it?
Where does it come from?
How do you install it?
Is it safe to install?

I was trying to listen to an audio clip, but it was _not_ an audio clip from a movie, therefore the message is confusing?

It does seem that Ubuntu has certain difficulties with media content on the internet.

Specifically, I am referring to content that may need Realplayer to assist in the extraction of the content.

Any advice will be gratefully received but I suspect that this will be an unresolved difficulty.

---

### Post by Darkdelusions on 2008-05-25
When I went to amazon.co.uk and tried to play a random sample on the page I also ran into the same issue. It appears that amazon.co.uk uses Real Player 10 to stream it samples. 

You can install real player using the following instructions
> 
Install from prepackaged .deb file

This installation uses deb file packaged as part of debian-multimedia project (kudos to Christian Marillat).

open a terminal and type,

sudo apt-get install libstdc++5
wget -c [http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb](http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb)
sudo dpkg -i realplayer_10.0.8-0.1_i386.deb


---

### Post by tea for one on 2008-05-25
Thank you for your advice but I regret to report that it failed as follows:-

mark@mark:~$ sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@mark:~$ wget -c [http://www.debian-multimedia.org/poo...8-0.1_i386.deb](http://www.debian-multimedia.org/poo...8-0.1_i386.deb)
--22:00:47--  [http://www.debian-multimedia.org/poo...8-0.1_i386.deb](http://www.debian-multimedia.org/poo...8-0.1_i386.deb)
           => `poo...8-0.1_i386.deb'
Resolving [www.debian-multimedia.org](www.debian-multimedia.org)... 91.121.19.113
Connecting to [www.debian-multimedia.org|91.121.19.113|:80](www.debian-multimedia.org|91.121.19.113|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...8-0.1_i386.deb](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...8-0.1_i386.deb) [following]
--22:00:47--  [http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...8-0.1_i386.deb](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/poo...8-0.1_i386.deb)
           => `poo...8-0.1_i386.deb'
Resolving ftp.sunet.se... 194.71.11.69
Connecting to ftp.sunet.se|194.71.11.69|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:00:47 ERROR 404: Not Found.

mark@mark:~$ sudo dpkg -i realplayer_10.0.8-0.1_i386.deb

---

### Post by gnoob on 2009-11-22
the link was shortened.  click on it and search the site for real player and download that

---

### Post by sandyd on 2009-11-22
```

wget -c http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb
sudo dpkg -i Real*
sudo apt-get -f install 

```

---

