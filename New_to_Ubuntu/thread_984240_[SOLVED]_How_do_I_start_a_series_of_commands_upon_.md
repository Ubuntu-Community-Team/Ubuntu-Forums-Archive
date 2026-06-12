---
title: "[SOLVED] How do I start a series of commands upon login, is there an alternative to &amp;quot;"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by hovzio on 2008-11-16
Hi, I've been playing around with various synaptic-mouse settings with the synclient command. The mouse has been quite a pain but I have finally figured out all the necessary settings (Its a bunch on this toshiba) to make it less jumpy, stop when I'm typing and so forth. The problem is that all this is reset when I boot.

I am aware that I could manually add all these commands under System->Sessions but thats not really what I'm looking for. I know in kde you have an .autostart directory that you you can throw a shell scripts into and all are run at startup.

So, Is there such a directory in Gnome?

If not is it acceptable to source a script containing all the necessary commands in ~/home/.profile? (I think this may work but am not sure if this is the proper way to go about it.)

Any info/help is very appreciated, Thank You :)

---

### Post by binbash on 2008-11-16
/etc/rc.local ???? but this depends.what command do you want to use ? (you can give a couple samples only)

---

### Post by hovzio on 2008-11-16
Well I need to start the syndaemon, 

syndaemon -i 1 -d -t -d

The rest are just commands like:

synclient AccelFactor=00121566
synclient MaxSpeed=0.145879
" "       MinSpeed=0.0607829

Theres an awful lot of those, I'm looking to put it in a script.

EDIT:I kind of want it user defined so I don't know about puting it in /etc/rc*. Nevertheless I would really like to know (understand) how one would go about doing that. Thanks

---

### Post by binbash on 2008-11-16
yes you can.But it is better to make them as a bash script and add only that.

---

### Post by hovzio on 2008-11-16
> **binbash said:**
> yes you can.But it is better to make them as a bash script and add only that.



Yes I can ..What? I don't understand. I suppose you mean the sourcing it option. Wouldnt it have to be an executable script for this? And where would I add this script?

---

### Post by binbash on 2008-11-16
#!/bin/bash
command1
as
aa
a
aa
vsvsvs

Then save it (filename.sh), then chmod +x filename.sh

then you can move it to /usr/bin .add the command to rc.local

example : 

save it as filename.chmod it
sudo cp /asdasd/filename /usr/bin
chmod 755 /usr/bin/filename

add filename to rc.local

---

### Post by hovzio on 2008-11-16
Cool!!!! So I can execute the scripts that are in my ~/bin at startup by puting the commands in /etc/rc.local?  Thats exactly what I was looking for, many, many thanks. I just recently started learning about init and the /etc/init.d/, rc1-6.. and that kinda ties it all up. :KS

---

