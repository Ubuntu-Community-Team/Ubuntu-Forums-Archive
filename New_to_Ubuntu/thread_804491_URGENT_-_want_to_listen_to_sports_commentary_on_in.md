---
title: "URGENT - want to listen to sports commentary on internet!"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by furoido on 2008-05-23
Urgent request! Desperately want to listen to live match commentary on the BBC's website, but it doesn't seem to want to load up (just says 'transfering data from bbc.co.uk')...can anyone help we with a solution?

Actually, I have noticed this always happens when I try to watch videos or listen to commentary on websites...

---

### Post by mjwhitfield on 2008-05-23
have you installed the mozilla-mplayer from the repo's?  Always worked for me on the BBC sites.

---

### Post by starcannon on 2008-05-23
This page will help loads:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and be sure to get the restricted-extras from the synaptic package manager as well.

And as mjwhitfield said, mplayer and its mozilla plugin are very useful for these sorts of things as well.

GL let us know how it turns out.

---

### Post by guildofghostwriters on 2008-05-23
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I followed this carefully and can stream audio from the BBC with firefox without any problems. I listened to the whole of the last test (well, the few rainless patches) fine - it's as if the cakes are there in the room with me!

---

### Post by Stefanie on 2008-05-23
do you want to listen to bbc radio? this works on my computer, but i had to download and install realplayer, in this thread you can find how to do this: [http://ubuntuforums.org/showthread.php?t=782774](http://ubuntuforums.org/showthread.php?t=782774)

i just have to click on "listen live", select the radio station and wait a few secs. i also have mozilla-mplayer installed, but i don't know if this is really necessary.

---

### Post by furoido on 2008-05-23
Downloaded Mplayer and I can see it in my applications...but when I try to launch it from the BBC, nothing happens (I just get that whirly wheel on my pointer..)

Mind you with the kiwiws already on 57/0, not sure i want to listen to the commentary!!

---

### Post by furoido on 2008-05-23
Also tried to install realplayer, but when i tried to install the mozilla plugins, i got this message...


andrew@andrew-desktop:~/Desktop$ rm RealPlayer11GOLD.bin
andrew@andrew-desktop:~/Desktop$ cp /opt/real/RealPlayer/mozilla/nphelix.so ~/.mozilla/plugins/nphelix.so && cp /opt/real/RealPlayer/mozilla/nphelix.xpt ~/.mozilla/plugins/nphelix.xpt
cp: cannot stat `/opt/real/RealPlayer/mozilla/nphelix.so': No such file or directory

---

### Post by guildofghostwriters on 2008-05-23
Follow the post I linked to in my previous post - I've used it a number of times for different installs of Gutsy and Hardy and have had multimedia web streaming up and running in no time and without any problems. I'll make it even easier by pasting the link in again so you don't have to scroll up...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by Stefanie on 2008-05-23
> **furoido said:**
> Also tried to install realplayer, but when i tried to install the mozilla plugins, i got this message...


andrew@andrew-desktop:~/Desktop$ rm RealPlayer11GOLD.bin
andrew@andrew-desktop:~/Desktop$ cp /opt/real/RealPlayer/mozilla/nphelix.so ~/.mozilla/plugins/nphelix.so && cp /opt/real/RealPlayer/mozilla/nphelix.xpt ~/.mozilla/plugins/nphelix.xpt
cp: cannot stat `/opt/real/RealPlayer/mozilla/nphelix.so': No such file or directory

i didn't need those plugins. first i installed mozilla-mplayer from the repos, then i downloaded realplayer and installed it by running the bin-file.  that was the only thing i needed to do, maybe you can click on "run realplayer as standalone" or something like that. if that doesn't work i guess you should follow guildofghostwriters's link...

---

