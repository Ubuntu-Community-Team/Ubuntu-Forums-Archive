---
title: "[SOLVED] Trying to setup Network Printer but no joy"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by rlogan on 2008-04-22
Hi all

I am hoping someone may be able to help me get the network printer up and running. It has given me grief on and off for a little while but never really decided to work at it. Time has come to get this machine printing. I have attempted to get this working from quite a few different guides but never got there.

The setup is two machines linked via a router on ethernet cabling. One machine has a printer plugged into USB which has printer sharing set to on. But no matter what I seem to do I cannot get this machine to see the printer on the other. The machine hosting the printer is currently on Gutsy and the machine that I wish to setup the network printer has just been upgraded to Hardy.

Have also attempted on a couple of occasions to setup network shares but never really persisted.

Any help greatly appreciated.

---

### Post by nicedude on 2008-04-22
This is link for how to share printer in hardy

[http://www.funnestra.org/ubuntu/hardy/#ipp](http://www.funnestra.org/ubuntu/hardy/#ipp)

---

### Post by rlogan on 2008-04-22
Thanks for the reply !!!

It looks like a good how to !!!

The only prob is that on the client machine when I select the printing options in the menus, the selected option takes either like 10-20 mins to load or it just does nothing. I have tried typing these commands from the CLI but to no avail.

Thoughts ???

---

### Post by steveneddy on 2008-09-28
Try this.

In your browser, type the address:

[COLOR=Blue]**127.0.0.1:631**[/COLOR]

hit Enter

Find the **Server** tab and press it.

Click the 

**Show Printers shared by other systems.**

On the machine with the printer attached, perform the same steps but instead check the 

**Share published printers connected to this system**

Restart both machines.

This should solve your issue.

---

### Post by engtg on 2008-09-28
Description: HP
Location: Network
Printer Driver: HP PhotoSmart C5100 Foomatic/hpijs, hpijs 2.8.2
Printer State: idle, accepting jobs, published.
Device URI: socket://192.168.1.100:9100 

This example is for HP printer
Device URI: is for your network Printer you will need to find out what your address is for your printer.  I guess what you mean by network printer that it connected to your router.  Instead of one computer which will be left on or turn on for another computer to printer from it.

---

### Post by rlogan on 2008-11-04
Thanks everyone, have started playing around with the cups interface as suggested. No definite success but some promising results.

Thanks heaps
Richard

---

### Post by rlogan on 2008-11-05
Using the Cups interface seems to have done the trick, thanks everyone who helped it is appreciated.

Now how do I close this thread ?

Cheers

Richard

---

