---
title: "Clicking on the Network Monitor icon doesn't bring up wireless network list"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by SMM81 on 2008-10-05
I'm a beginner.  I have Ubuntu Hardy on my Dell Inspiron 6000.  Recently I've made some changes to my desktop theme and somehow the Network Monitor icon has changed and no longer brings up the list of networks when clicked on.  Rather it brings up a window "Connection Properties: eth1".  When I boot up, the wireless connection normally automatically connects to my wireless network.  However, sometimes it doesn't automatically connect and I don't know where to pick from the list.  I know it sees the network, but I can't simply bring up the list by clicking on the icon.  Your expert help is greatly appreciated!

Thanks

---

### Post by bhadotia on 2008-10-05
> **SMM81 said:**
> I'm a beginner.  I have Ubuntu Hardy on my Dell Inspiron 6000.  Recently I've made some changes to my desktop theme and somehow the Network Monitor icon has changed and no longer brings up the list of networks when clicked on.  Rather it brings up a window "Connection Properties: eth1".  When I boot up, the wireless connection normally automatically connects to my wireless network.  However, sometimes it doesn't automatically connect and I don't know where to pick from the list.  I know it sees the network, but I can't simply bring up the list by clicking on the icon.  Your expert help is greatly appreciated!

Thanks

Changing themes have no effect on network manager. Check your connection properties , Check to see if you have wireless switched on or not.

---

### Post by SMM81 on 2008-10-07
I've just reinstalled linux mint and the icon I want, the one with the four increasingly tall bars showing signal strength, is gone again, and when I add "system monitor" to the panel I get the icon with two computers (one behind the other) with a bar to the right going green when connected and red when not connected.  When I click on this icon, instead of seeing the list of wireless networks available I get a box with the drop down list consisting of "lo" and "eth1".  This is not what was there originally.  I have no idea what I could have done to lose the original icon.  This is somewhat annoying.  I like linux, but these quirks really frustrate my wife, who also uses our computer.

---

### Post by knattlhuber on 2008-10-07
Just to clear things up a bit
The thing you had there in the first place was the 'network-manager applet', which is different from what you just added is the Network Monitor. The latter doesn't have the same properties as the nw-manager applet.
I don't use the network-manager-applet myself so I'm not 100% sure how to bring it back up again but you could try <Alt> + F2 and then typing 'network-manager-applet' or 'nm-applet' (without the quotes). I'm currently not on an Ubuntu machine (plus being in a Stats class :)) so I can't check right now.
Hth a bit

EDIT: Here is an old thread that might help: [http://ubuntuforums.org/showthread.php?t=239178](http://ubuntuforums.org/showthread.php?t=239178)

---

### Post by aparigraha on 2008-10-07
WICD is a wireless network manager. A lot simpler to deal with according to a lot of people. Hve a look [here]("http://wicd.sourceforge.net/") for info, or [here]("http://wicd.sourceforge.net/download.php") to learn how to install it. I first installed it a month ago, and it is the easiest thing to handle wireless connections now.

but have a look here as well:
[http://ubuntuforums.org/showthread.php?t=940898]("http://ubuntuforums.org/showthread.php?t=940898")

---

### Post by knattlhuber on 2008-10-07
+1 for Wicd.

---

