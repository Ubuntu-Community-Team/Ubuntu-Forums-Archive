---
title: "wireless connection, lifebox not detected any more"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by mkornig on 2012-03-21
Hi there,

Back at home I have a Lifebox which allows for wireless internet connection. Yesterday it worked fine: I switched on the lifebox, after a short time my system detected it (along with a dozen of other routers/modems in the area where I live), I selected it and typed in the lengthy password/code and then I surfed as usual.

But today my system doesn't detected my lifebox any more (although it's switched on). My system doesn't detected any of the other routers in the building that where active yesterday either.

It sounds stupid, doesn't it? I think I may have messed up the network configuration?

Any help on this would be appreciated.
Martin

---

### Post by Ms. Daisy on 2012-03-22
It's never popular, but start with the simple stuff.  Is the lifebox (did you mean livebox?) attached properly, all cords firmly plugged in? 

If everything is plugged in & on, then find out what's the output of:

```
ifconfig
```

---

### Post by mkornig on 2012-04-05
Thanks Ms Daisy,

Yes it's a livebox from Orange. And it seems to be proerly wired.

My laptop doesn't detect any wireless sources. Not my livebox. No other ones although a live in a residential area and the other day it detected more than 10 different sources. Now it's zero. So I think the probhlem is not linked to my livebox but to my computer.

Please find the response to the ifconfig command in the file attached.

Martin

---

### Post by mkornig on 2012-04-20
I still haven't been able to sort out this Internet problem. It's kind of frustrating. I close this thread. It doesn't seem to lead anywhere. 

Cheers, Martin

---

### Post by Ms. Daisy on 2012-04-20
Sorry I couldn't help.

Did you see this page? I did a Google search, Orange must be very popular in France-
[http://assistance.orange.fr/utiliser-votre-livebox-avec-un-ordinateur-equipe-de-linux-51.php](http://assistance.orange.fr/utiliser-votre-livebox-avec-un-ordinateur-equipe-de-linux-51.php)
My French sucks so I had to translate it LOL.  It doesn't appear that they like Linux much, but it is supposed to work.

And that leads to a French Linux forum that may be better suited to help you.
[http://entraide.orange.fr/assistance/messages/repondus/83/internet-utiliser-depanner-linux.html](http://entraide.orange.fr/assistance/messages/repondus/83/internet-utiliser-depanner-linux.html)

bonne chance!

---

### Post by Dumpy Dumpster on 2012-04-20
Before you rush off....
Put [http://192.168.1.1/](http://192.168.1.1/) into your browser and this will open your Livebox settings.  The password is 'admin'.  Ensure that you have Wi-Fi enabled under Services.  I use a Livebox in France and it has no probems connnecting with Linux (Mint and Lubuntu)

---

### Post by mkornig on 2012-04-24
@msdaisy: I don't live in France any more. My problem doesn't have to do anything with Orange, I believe.

---

### Post by mkornig on 2012-04-24
@dumpy: I don't think my problem is related to settings of my livebox. Internet connexion is fine when I use a wire. And sometimes (1 out of 10?) wireless works as well.

I may be repeating my self, but the problem seems to be linked to my computer which often does not connect any other wireless sources around at all. How do I make my computer detect anything?

---

### Post by Ms. Daisy on 2012-04-24
It's likely you're missing a wireless driver for the Orange device, or you've got the wrong one.  I gave you the links to the orange forum because they're probably more familiar with the details than folks here.

---

### Post by wildmanne39 on 2012-04-24
Hi, please post the output of the following commands and I will try to help you:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Ms. Daisy on 2012-04-24
Wildmanne39 to the rescue!!!
:KS:KS:KS

---

### Post by GaryTheCat on 2012-04-25
Silly question but have you tried pressing the WiFi pairing button on the back of the LiveBox?

That should help.

G

---

### Post by GaryTheCat on 2012-04-25
Actually, no it won't - just ignore me!:lolflag:

---

