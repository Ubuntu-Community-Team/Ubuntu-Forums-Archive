---
title: "Howto: Nmap 3.93 with gtk2 and fixed icon"
date: 2005-10-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Technoviking on 2005-10-24
Nmap and Nessus on my laptop are my best friends for keeping my Windows boxes at work secure. Nmap is the quickest way to search a subnet for any unusual open ports.

The version of Nmap that comes with Breezy is a little old, and also uses gtk1 (bleech). Another problem is that the menu icon does not launch nmap as a sudo privilege app, therefore nmap does not allow all its features to work.

Here are instructions for installing my Nmap 3.93 deb files, with gtk2 and fixed menu icon.

Changes 11/10/2005: 
[LIST]
[*]Rebuilt from Dapper source instead of Debian Sid source. Not making a backport since I do change the Dapper source to add the gtk2 patch.
[*]Added my copy of source.
[/LIST]

1. Get files
```

wget -c http://mikesplanet.net/deb/nmap_3.93-1~dmb_i386.deb
wget -c http://mikesplanet.net/deb/nmapfe_3.93-1~dmb_i386.deb
wget -c http://mikesplanet.net/deb/nmap-logo-64.png

```
2. Install Files
```

sudo dpkg -i nmap_3.93-1~dmb_i386.deb nmapfe_3.93-1~dmb_i386.deb

```
3. Copy Icon Pixmap
```

sudo cp nmap-logo-64.png /usr/share/pixmaps

```
4. Restart Gnome Panel
```

killall gnome-panel

```

The source can be found here:
```
wget -c http://mikesplanet.net/src/nmap_3.93-1~dmb.tar.gz
```
Let me know if you have any problems.

Mike

---

### Post by Yemoke on 2005-10-25
Nice dude, works like a charm :)

---

### Post by rth on 2005-10-25
No AMD64 package? ;)

---

### Post by Technoviking on 2005-10-25
[QUOTE=rth]No AMD64 package? ;)[/QUOTE]
No AMD64 processor:)

---

### Post by rth on 2005-10-25
You don't?!?!?!?!?!?!??!?! :eek:

---

### Post by Technoviking on 2005-11-10
[QUOTE=rth]No AMD64 package? ;)[/QUOTE]
You can build it from the source now.

Mike

---

### Post by Spudgun on 2005-11-11
Worked great, thanks.

---

### Post by Nimefurahi on 2005-12-04
Very nice, Mike.
Thanks!

---

### Post by viscount on 2005-12-14
aye, tanks mike 

you get a gold star

---

