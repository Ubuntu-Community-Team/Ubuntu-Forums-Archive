---
title: "Flashplugin-nonfree installation stalls"
date: 2006-06-07
forum: Repositories &amp; Backports
---

### Post by jemt on 2006-06-07
Greetings :)

'apt-get install flashplugin-nonfree' seems to work - but when it starts downloading Flash from Macromedia, nothing more happens. I've tried it 4 times now over the last 45 minutes. No result.

I have heard it should be possible to change the server which flashplugin-nonfree fetches the flash plugin from - but I'm not sure how. Can anyone help me ?

---

### Post by arizonagroovejet on 2006-06-07
Yeah sorry scrub my reply sin cei failed to read your question properly before replying.

---

### Post by johnc4510 on 2006-06-07
It's possible that their servers are down, or very busy. It should work, so try again in an hour or so. If it doesn't post back here.

---

### Post by alamba on 2006-06-07
Well don't have an answer to your question, but I got this working by downloading flash tar.gz file from macromedia site and then following their writeup on installation for firefox/mozilla.

A

---

### Post by jemt on 2006-06-12
Thanks guys :)

---

### Post by dr.drake on 2006-06-17
[QUOTE=jemt]Greetings :)

'apt-get install flashplugin-nonfree' seems to work - but when it starts downloading Flash from Macromedia, nothing more happens. I've tried it 4 times now over the last 45 minutes. No result.
[/QUOTE]

same problem here, it has happened before as discussed in this CLOSED thread: [http://www.ubuntuforums.org/showthread.php?t=181298&highlight=flashplugin-nonfree](http://www.ubuntuforums.org/showthread.php?t=181298&highlight=flashplugin-nonfree) 
it describes the problem a bit better (why did it get closed?)

> ...that got to the point of configuring then just sat there. For over a half hour. I closed synaptic and there was a notification of new updates. When I click on the icon, it tells me to **run "dpkg --configure -a."** This gets to the same point as synaptic then stalls. Now I'm at a point where I can't do anything. If I try to remove the package, it says that it is unable to get a lock on the administration directory. What should be my next step?

when I tried the there given solution of ** sudo apt-get -f install**, I got: > sudo apt-get -f install
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail                                  able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc                                  ess using it?

it is starting to get really annoying, because I was setting up a system for somebody, and I'm stuck now, not being able to use apt-get install , synaptic or adept to install stuff any more....

please Help!!

---

### Post by dr.drake on 2006-06-17
ok, I finally got the "lock" off by doing this:
```
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a

```
then I went to adept and unistalled flashplugins-nonfree and all is fine (apart from flash)

---

### Post by spitfireinc on 2006-06-17
Type this in terminal:

[COLOR="DarkRed"]sudo dpkg --purge wdm[/COLOR]

Then remove the flash player by going to synaptic package manager.

For installing, I suggest downloading the player from the macromedia website and install it manually. Its pretty easy.

---

### Post by keaton on 2006-06-18
I'm having a similar problem- I try to download it automatically, (clicking on "install this plugin",) I try to download the Flashplugin-nonfree, and I even try downloading it directly from Macromedia as the tar.gz file. Nothing. It stops downloading at a random point, 10-90%. I've tried it on a previous install and this new one, and I had in on a seperate internet connection even, back at my old place. Is anyone else having trouble with this? Nothing wrong with my computer or downloading, it just seems like a problem with Macromedia. Right now the download for it shows 0.1 KB/sec, but I doubt it's doing even that. I've left it on for over 24 hours, and still gets only to 90%. Thanks for any help on this.

---

### Post by dr.drake on 2006-06-24
i tried again 2 days later and it worked, but I did change my repos with this site:;
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

eric

---

