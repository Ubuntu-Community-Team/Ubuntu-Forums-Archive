---
title: "Could it be that firewall blocks Skype?"
date: 2013-02-21
forum: New to Ubuntu
---

### Post by Newbeatontheblock on 2013-02-21
Hi i have bought an old pc secondhand from the net. It is an ACER ASPIRE 5538G AMD ATLON 64
I have installed Ubuntu on it as Windows 7 was really slow en working not all. Ubuntu is working just super, just lovin this OS more and more each day. But Skype is not working.It freezes my pc

I installed both 32 and 64 bits Skype installed them and removed them several times but each time i start skype the application does nt let me even sign in... My pc freezes ... And i need to do a cold reboot /

As i see it this could be a

Hardware related to the network card that could have been damaged a bit as wireless does not work properly i have to reconnect 5 times to wifi a day. Other pc notebooks have no issues here


Software related ... But where to go ? I have tried many tricks on this that google has given me but none seem to work 

or Maybe it has to do with a firewall settings?
I have been playing around with ufw a bit and must admit that maybe i m not skilled enough to do this...

Any suggestions on this one ?

Thanks in advance

---

### Post by offgridguy on 2013-02-21
It sounds more like hardware.  You could disable the firewall just to try that though.
```
sudo ufw disable
```
When you restart your computer it will be disabled, if you want to
reverse it.
```
sudo ufw enable
```
I really don't think the firewall is the problem though, but this
will verify or eliminate that possibility.

---

### Post by Newbeatontheblock on 2013-02-21
> **offgridguy said:**
> It sounds more like hardware.  You could disable the firewall just to try that though.
```
sudo ufw disable
```
When you restart your computer it will be disabled, if you want to
reverse it.
```
sudo ufw enable
```
I really don't think the firewall is the problem though, but this
will verify or eliminate that possibility.


Hey Thanks for update. I have tried it but skype is still freezin my pc. Thanks anyway....

---

### Post by Newbeatontheblock on 2013-02-23
Hi could it be that Apache which k  installed a few weeks ago is blocking skype?   And this causes my pc to freeze each time i start skype ?


Google told me that skype and Apache work on the same ports

I guess i can only find out to uninstall wamp but how can i do this via the command line

?

I m on my way to a solution for this 

i guess

---

### Post by HermanAB on 2013-02-23
Freeze your PC as in totally unresponsive to keyboard and mouse pointer?  Yes Skype can do that.

Try downloading the latest "static" version from the Skype web site.

---

### Post by haqking on 2013-02-23
[https://support.skype.com/en/faq/FA148/which-ports-need-to-be-open-to-use-skype-for-windows-desktop](https://support.skype.com/en/faq/FA148/which-ports-need-to-be-open-to-use-skype-for-windows-desktop)

Ignore the mention of it being on a window desktop. same ports.

Though it being blocked by the firewall wont cause it to freeze and leave your machine unresponsive.

Make sure you have latest version, there have been some people having issues with x64 but works fine on my system.

---

### Post by Newbeatontheblock on 2013-02-25
Thanks guys for your replys

I m gonna remove skype and then try to install the static version
and or the latest version ...See what works then i ll stop troubleshooting...This Should be the fix as this is probably not related to my hardware 

although i have to reconnect sometimes  to LAN network It
works good enough downloading torrents and all works Superquick when max 3 hosts are on my Wireless Lan  so...
Only when my mams  & dads and bro's go online with Ipad en and Iphones in combination with 2 other pcs and one imac it disconnects ....which makes me conclude that this is not fysical layer  hardware related issue...

Thanks already for all the tips and advice...

---

