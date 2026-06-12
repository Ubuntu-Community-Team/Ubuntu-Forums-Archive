---
title: "leafpad buffer overflow highlight chinese conflict"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-10-09
I love the leafpad text editor because it handles massive files very quickly. 

A  few times a day on my chinese dictionary file, the ability to highlight  in leafpad suddenly fails. It happens in the find box as well as the  document.  I have to close the file and open it again.

I tried to file a bug but don't think I was successful. It was also a bug in versionn 17.

I haven't been able to find out where the log files are stored in lubuntu either.


I emailed the developer, as below, but he may not have received it:
leafpad ver 0.8.18.1 by Tarot Osuji
[email]tarot@freeshell.org[/email]
[email]tarot@sdf.lonestar.org[/email]
[http://tarot.freeshell.org/leafpad/](http://tarot.freeshell.org/leafpad/)
[http://www.twaren.net/](http://www.twaren.net/)
Lapo Calamandrei who did the artwork, very kindly told me he wasn't in touch with Tarot.

---

### Post by Kevin McCready on 2013-10-10
Somehow I think that the actual leafpad program needs to be tweaked (because when the problem happens, it doesn't happen to other apps). The ability to tweak an actual app at program level is one of the reasons I switched to linux. But, at the moment, it's beyond my skillset to do so. 

Anyway, up to this point I've managed to find (but am not confident I've found all leafpad files):
/root/.config/leafpad
/home/k/.config/leafpad
/usr/share/lubuntu/leafpad
/usr/share/menu/leafpad
/usr/share/doc/leafpad
/usr/bin/leafpad
/usr/share/applications/leafpad.desktop

sudo leafpad /root/.config/leafpad/leafpadrc 
password
I see the following:
Code:    
0.8.18.1
1364
714
Monospace 12
0
0
0
someone else's leafpadrc was
0.8.18.1
671
450
Monospace 12
1
0
0    
and it seems to be the line below "monospace 12" determines if wordwrap is on or not.

---

### Post by heir4c on 2013-10-10
To inform you:

If you have synaptic installed, than you can see all files that come with the install of leafpad in synaptic.
Open synaptic and go to "settings > preferences > 1st Tab  
There you mark the first line under 'appearance' (I think that's the English word for what there stand, I'm in the Dutch version) 
Than click "Apply". Now you see under the softwarelist many info about the packages. For te files look for the 4th Tab.

---

