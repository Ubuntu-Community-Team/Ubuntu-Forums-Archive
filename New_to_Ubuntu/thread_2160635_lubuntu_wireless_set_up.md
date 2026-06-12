---
title: "lubuntu wireless set up"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by Wvren on 2013-07-07
Hey!

I'm an absolute Linux beginner (I know some very basic Unix terminal commands, but mostly the file/directory manipulation stuff) and I just installed lubuntu on my notebook. However, during the installation process and the startup process I was informed that my wireless card isn't installed. And when I log in, there're no wireless access points being picked up.

I ran lspci |grep Network and it yielded (I have no idea how to copy and paste from the terminal - if you could tell me, that'd be great!)

Network controller: Broadcom Corporation BCM4312 801.11b/g LP-PHY (rev 0 1)

Hopefully this helps!
Thanks very much in advance!


EDIT: I did a bit of rootling around on the net, and came across this instruction ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx))
sudo apt-get update
sudo apt-get install b43-fwcutter

I did this, and enabled the driver it installed and I'm now restarting. Hopefully this will work. Will report back in a few minutes.


[SIZE=5][B]EDIT: It worked! I recommend anyone with the same card going to the above link and following the instructions there.
Please mark this post as fixed! [/B][/SIZE]

---

