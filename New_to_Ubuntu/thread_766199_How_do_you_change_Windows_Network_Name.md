---
title: "How do you change Windows Network Name"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Michl on 2008-04-25
Now that samba sharing has changed I don't know how to
change the Windows Network name.  In Hardy the default
name is WORKGROUP, but my original setup used another
name so now I have two Windows networks.  I'd like to
change Workgroup to the other name.  It's not a major
problem because they all show-up in the Network,but
it isn't tidy.

---

### Post by yaztromo on 2008-04-25
Edit the samba configuration file via the terminal

```
sudo nano /etc/samba/smb.conf
```

Scroll down to the line that looks something like this

```
workgroup = MSHOME
```

and change MSHOME to whatever you like. Now hit ctrl-x and press y.

Finally restart samba ```
sudo /etc/init.d/samba restart
```

---

### Post by LandisTwo on 2010-03-10
> **yaztromo said:**
> Edit the samba configuration file via the terminal
```
sudo nano /etc/samba/smb.conf
```Scroll down to the line that looks something like this
```
workgroup = MSHOME
```and change MSHOME to whatever you like. Now hit ctrl-x and press y.
Finally restart samba ```
sudo /etc/init.d/samba restart
```

A huge Thank you (&#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;) for a little, simple and clear HowTo,
&#1051;&#1072;&#1085;&#1076;&#1080;&#1089; (Landis)

<!-- EDIT -->
BUT.....
the restart command did not work in ubuntu 9.10...
I found that there is by default an /etc/samba/smb.conf file but 'Samba' is not installed in 9.10..
You have to go> Applications> Ubuntu Software Center> Get Free Software [type in samba to narrow choices] Install Samba..... Then at the console prompt, restart command above Will Work!

&#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;!
Landis.

<!--EDIT-->
BUT....
This lets you 'Share' folders, but to 'browse' a windows network ('workgroup') you also need to install (you may have noticed it in the list while installing Samba) smb4k.

Landis.

<!-- EDIT-->
  NOPE!
Still can't 'browse' for the one, the only, the last windows system on my network.... : (

Landis.

<!-- EDIT-->
Was able to Access last ms system (win xp pro) by...
Places> Location> in location (address bar or location bar type: smb://genworkstation [enter - return] (where 'genworkstation' is the NetBEUI (WINS) (mine) name of Your computer... There she blows! Full Access has been Accomplished.

&#1051;&#1072;&#1085;&#1076;&#1080;&#1089;.
Landis Reed (Lunar)

---

