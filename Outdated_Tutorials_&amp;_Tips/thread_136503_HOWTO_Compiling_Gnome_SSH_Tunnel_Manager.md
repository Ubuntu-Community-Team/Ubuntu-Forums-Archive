---
title: "HOWTO: Compiling Gnome SSH Tunnel Manager"
date: 2006-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Roderik on 2006-02-26
At work we work through a lot of ssh tunnels to our servers. But is was quite a hassle to keep al the tunnels up and running, remembering the right ports etc etc. So i went searching for a gui to manage all of this. (offcourse i found one, otherwise i wouldn't be typing this)

gSTM aka Gnome SSH Tunnel Manager from [http://gstm.sourceforge.net/](http://gstm.sourceforge.net/)

Unfortunatly there were no .deb's available and i could't find it in the repositories.

So i compiled it myself, and here is how, maybe it is of use for someone.

```

sudo apt-get install checkinstall libgnomeuimm-2.6-dev libgnomeuimm-2.6-1c2
wget http://surfnet.dl.sourceforge.net/sourceforge/gstm/gstm-0.3.tar.gz
tar vxzf gstm-0.3.tar.gz
cd gstm-0.3
./configure
make 
sudo checkinstall

```

that was it, now you can start it with "gstm" from the cli, and there is a .desktop file somewhere too :)

the deb my checkinstall created can be found at: [http://www.vanderveer.be/gstm-0.3_0.3-1_i386.deb](http://www.vanderveer.be/gstm-0.3_0.3-1_i386.deb)

---

