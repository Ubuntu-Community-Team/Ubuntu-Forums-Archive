---
title: "[SCRIPT]: Install Flock Web Browser, the easy way"
date: 2006-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by fiendskull9 on 2006-12-11
Hey guys,

Im a flock user on all my OS's

and i had to tackle getting flock in ubuntu

i came up with an easy shell script, that does all the work for you

this gets version .0.7.8 for you

Ill try to keep up to date and upload the files to my server upon new releases

this is for **Intel x86** only!

```
#!/usr/bin/sh

echo "LETS GO!"
echo""
wget http://hyperedit.gottabrez.com/flock-0.7.8.en-US.linux-i686.tar.gz

tar -C /opt -xzvf flock-0.7.8.en-US.linux-i686.tar.gz

ln -s /opt/flock/flock /usr/bin/flock

rm flock-0.7.8.en-US.linux-i686.tar.gz
```

just add this to a file called *flock-me.sh*

and do

```
sudo chmod +x flock-me.sh
```

lastly, just

```
sudo sh flock-me.sh
```

enjoy

-clay

---

### Post by Ptero-4 on 2006-12-22
Nice sig fiend. But mine's updated for Windoze Waste.

---

### Post by ErikTheRed on 2007-01-02
/opt seems like an odd place to put flock, shouldn't it go along with where all the other apps are? Like /usr/share/apps/flock ?

---

