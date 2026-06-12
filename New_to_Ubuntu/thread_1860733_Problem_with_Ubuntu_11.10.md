---
title: "Problem with Ubuntu 11.10"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Yash Pal on 2011-10-15
I was quite happy with Ubuntu 11.04; last night the computer asked me if I would like to upgrade to 11.10 (which was due for release). I went in for upgrade; now I cannot access the internet. There is no way to edit/restore the connection as all the items in the interface (G U I for internet) are dimmed. The bluetooth was not working but it did not present a nuisance.

Now the menu item 'enable wireless (connection?)' is totally blanked out (is dark)

With 11.04, the internet connection had come up of its own. I have a dual boot with windows 7 and had configured the internet wireless connection with windows and no configuration was done for Ubuntu 11.04.

Any hopes of restoring the internet?

---

### Post by garvinrick4 on 2011-10-15
First try a few things with wired in: run first line of code below
Now take wired out and see, if not reboot and see.
```
sudo apt-get install --reinstall network-manager
```
If that helps ok, if not what post outcome of below to see what card and driver you have.
```
lspci -nnk | grep -ii2 network
```

---

### Post by Yash Pal on 2011-10-17
Thank you very much garvinrick4. I am sorry I did not revert earlier.

I think the problem is that either the wireless/wire-in card is not being recognised or there is some bug in the new software which is not allowing the connection. (like bluetooth was not on in 11.04

No progress with[FONT=&quot] 'sudo apt-get install --reinstall network-manager'


I will try the alternative [/FONT][FONT=&quot](2nd suggestion) and come back.[/FONT][FONT=&quot] [/FONT]**[COLOR=red][FONT=&quot][/FONT][/COLOR]**

---

### Post by garvinrick4 on 2011-10-17
If you have not fixed yet you just might have a broadcom card like a lot of other users and it is fixable with 
a couple of lines of code or using synaptic to install drivers. Need to see outcome of second line of code 
given previously that tells what the card and drivers are so as to install the right drivers.  Or you can even
google your card and version of Ubuntu and will most likely get the fix in a lot of hits. It is just loading
the wrong driver and needs a bit of a fix to load correct driver. Next time you have a wireless problem
put that in your Title line and the users that specialize in Network cards and drivers will be on the thread
rather quickly.

---

### Post by Yash Pal on 2011-10-17
I am glad to tell you that the problem seems to have resolved itself. The internet connection came up of its own accord same as it had disappeared after upgrade.

A little while back I logged into Ubuntu and was asked password for wireless connection. I typed in half heartedly, expecting 'wireless disconnected'. But lo and behold 'connection established', perhaps because of all configuring done for wired and wireless connection.

garvinrick4, I thank you very much for the interest taken and I have copied to Writer your advice. I as a desktop user seldom try to customise, my interest is - my work should be done and looking into the OS is not my job. Fiddling with the OS is a momentous event for me and at that time I should have the advice handy.
Thanks once again.

---

