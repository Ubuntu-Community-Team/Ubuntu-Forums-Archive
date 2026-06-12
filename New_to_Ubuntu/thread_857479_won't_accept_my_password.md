---
title: "won't accept my password"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by stickman51 on 2008-07-12
Hello, group. Forgive me but I just d/l and installed Ubuntu on a laptop with Vista and am confused. Now I have the option of booting into Vista or Ubuntu. That's fine.

I ran Firefox but cannot get online. This computer is always online, wirelessly via my router, a DSL connection. In the File menu, I removed the checkmark from "Work Offline" but that did not work. I realize this is my ignorance only. Probably need to change a setting somewhere. Any advice please?

---

### Post by avtolle on 2008-07-12
What wireless card are you using? In the terminal (Applications>>Accessories>>Terminal) do```
lspci
``` and post the output here.

---

### Post by WinterMadness on 2008-07-12
> **stickman51 said:**
> Hello, group. Forgive me but I just d/l and installed Ubuntu on a laptop with Vista and am confused. Now I have the option of booting into Vista or Ubuntu. That's fine.

I ran Firefox but cannot get online. This computer is always online, wirelessly via my router, a DSL connection. In the File menu, I removed the checkmark from "Work Offline" but that did not work. I realize this is my ignorance only. Probably need to change a setting somewhere. Any advice please?


you're gonna have to install your wireless drivers.
you can use a wired connection to download the files you need

---

### Post by TSS on 2008-07-12
In the upper right hand corner of Ubuntu you should see a little computer, near the date and time.  If you click on it, you should see a list of wireless networks.  If you do not, then your wireless card was not recognized by Ubuntu.  Alternitivly, go to System > Adminisration > Network.  There is a button that says Unlock, click that and type in your password.  There should be a Wireless Connection listed.  If not, then same problem as above, your wireless card was not recognized by Ubuntu.

If your wireless card was not recognized by Ubuntu, you still might be able to fix it!  We need to know what type of wireless card you have.  Go to Applications > Accessories > Terminal.  Then type:
```
lspci
```

And post the results here!

---

### Post by stickman51 on 2008-07-12
THANKS for all those fast replies. This little icon in the top-right corner did not work for me so I tried the other option. So now I see, in part:
To run a command................
See "man sudo_root..........
kenlaninga@kenlaninga-laptop:~$ 1spci
bash: 1spci: command not found
kenlaninga@kenlaninga-laptop:~$

---

### Post by TSS on 2008-07-12
It looks like you typed a 1 instead of an L.  The command starts with an L (lowercase).
And when you post your lspci output, make sure you put [CODE] tags around it!

---

### Post by stickman51 on 2008-07-12
Yes, I had typed a number one instead of lower case letter L. So now I have a huge long list of stuff that makes no sense to me. Does this line help?
[00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge]
Not sure about "code tags." Hope this is what you mean.

---

### Post by TSS on 2008-07-12
We need to know what your wireless card is.  It should be listed in the output of lspci.  Also, you can just google for your laptop post a link to the specs?

---

### Post by stickman51 on 2008-07-12
This looks to me like it might be the one you need:
[06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (re v 01]

I find my laptop at
[http://www.canadacomputers.com/index.php?do=ShowProduct&cmd=pd&pid=013175&cid=896.645](http://www.canadacomputers.com/index.php?do=ShowProduct&cmd=pd&pid=013175&cid=896.645)
if that helps....

---

### Post by TSS on 2008-07-12
I believe your wireless card is Atheros AR5005G, which I believe is supported by madwifi drivers:
[http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

I'm pretty sure that is enabled with a default install, but try:
```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

---

### Post by stickman51 on 2008-07-12
TSS, I assume you mean for me to type that line where earlier I typed that "lspic" thingy. I did but it is not accepted. It says:
[bash: syntax error near unexpected token '(']

---

### Post by TSS on 2008-07-12
That is the correct place to type it... did you forget the dollar sign?

---

### Post by RATM_Owns on 2008-07-12
Try this.
```
sudo apt-get install linux-restricted-modules-`uname -r`
```

---

### Post by stickman51 on 2008-07-12
I had not missed the $ sign, so used the line given by RATM. That results in:
[[sudo]password for kenlaninga:
Sorry, try again.
[sudo] password for kenlaninga;
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-restricted-modules-uname -r
kenlaninga@kenlaninga-laptop:~$]

where I added the [] at start and end.

Not being much help, am I....

---

