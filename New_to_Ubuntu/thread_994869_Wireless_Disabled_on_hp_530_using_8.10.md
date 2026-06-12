---
title: "Wireless Disabled on hp 530 using 8.10???"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-11-27
People having hp 530 will know that there is a little button for WLAN, which when active gives out a nice blue glow.

When i had 8.04, when i pressed the button, wireless would get enabled but there was no light or the blue light did not work but the wireless did.

Now on 8.10 when i press the button, nothing happens. In the connection manager i keep getting that the wireless is disabled..

any1 know why?? is this a 8.10 problem?

The blue light works perfectly in windows

---

### Post by Michael.Godawski on 2008-11-27
It would be good to know what your wlan card is; so please post the results of these commands:

```
iwconfig
lspci
sudo lshw -C network
```

You perhaps might have to install your wlan drivers with ndiswrapper but let's see first.

... and there are some bugs on launchpad for hp530 dealing with wlan.

---

### Post by faraz_k86 on 2008-11-27
im on my other PC no so I will upload the outputs later. But the driver is installed and is an Inter PRO wireless card.

But I would like to update. Today when I turned on Ubuntu, the WLAN was already activated and that nice blue light was working and was ON. I even conneted to the Internet via my WLAN and browsed and downloaded.

I was happy that it started working. I shut down my laptop and the start it again after a couple of hours but this time the WLAN was acting as usual, i.e. not working, showing as deactivated..


Whats up with that?

---

### Post by oOarthurOo on 2008-11-27
If you find that it is not working, right-click on the network-manager icon in your system tray and uncheck enable networking. Then right-click again and enable networking. Give it about a minute and see if you're wireless comes up.

If not, right-click disable networking again, press your wireless (blue) button once, then right-click enable networking and wait another minute.

Sometimes they just get out of sync somehow. If this voodoo actually resolves your problem, you should disable your wireless from now on using network manager, instead of pressing the button. Right-click, uncheck 
'enable wireless'.

---

