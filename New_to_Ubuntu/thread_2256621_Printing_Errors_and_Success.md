---
title: "Printing Errors and Success"
date: 2014-12-13
forum: New to Ubuntu
---

### Post by omaroe on 2014-12-13
I am new to CUPS to please bear with me. I am trying to make ubuntu, cups or whatever to send a comfirmation email whith succefull printing or when erros happen. Is this possible? Or I am pushing the boundaries too much -:)

---

### Post by charlie-potatoes-001 on 2014-12-31
Hello...

---

### Post by charlie-potatoes-001 on 2014-12-31
I am having trouble printing to my network printer.  Nothing seems to print.  Ubuntu says job has been sent to printer but nothing happens.  There is a cups error popping up from time to time but nothing I've done so far seems to help.  I can find the network printer and install it.  Still nothing prints.  I can type the network address into the browser and find it to test but I can not print from any Ubuntu window or program.  Any suggestion or help would be great.

---

### Post by Mike_Walsh on 2014-12-31
Hello, charlie-potatoes. (That's an unusual 'handle'...)

You're probably being being blocked by the firewall (that's assuming you've got it running). You'll need to open up port 631; this is the port that CUPS uses to communicate through, when it's being used for network printing.

If you've not already done so, I would recommend installing GUFW; this is an easy to use, graphical front-end for ufw (uncomplicated fire wall), which comes with Ubuntu. However, it's not turned on; it's off by default, so it needs turning on. This can be done in the terminal, using

```
sudo ufw enable
```

but it's easier to install gufw, as this makes it easier to set-up 'rules', as and when required.

```
sudo apt-get install gufw
```

Make sure you have your source repositories enabled, by going into Software & Updates (you can find this in the 'Dash', if you've not yet used it). Tick all the boxes, except for the Source Code ones, then re-load the cache when asked to at the end of the procedure.

These should help:-

[http://news.softpedia.com/news/Managing-the-Firewall-in-Ubuntu-14-04-LTS-Is-Fun-with-the-Gufw-Interface-431380.shtml](http://news.softpedia.com/news/Managing-the-Firewall-in-Ubuntu-14-04-LTS-Is-Fun-with-the-Gufw-Interface-431380.shtml)

[https://sites.google.com/site/easylinuxtipsproject/security#TOC-Firewall](https://sites.google.com/site/easylinuxtipsproject/security#TOC-Firewall)


Regards,

Mike. ;)

---

### Post by plucky on 2014-12-31
> **charlie-potatoes-001 said:**
> I am having trouble printing to my network printer.  Nothing seems to print.  Ubuntu says job has been sent to printer but nothing happens.  There is a cups error popping up from time to time but nothing I've done so far seems to help.  I can find the network printer and install it.  Still nothing prints.  I can type the network address into the browser and find it to test but I can not print from any Ubuntu window or program.  Any suggestion or help would be great.

Please tell us make and model of your printer.

Does it work with a USB connection?

---

### Post by charlie-potatoes-001 on 2015-01-02
I have installed gufw as you suggested.  I then entered :[COLOR=#0000FF][FONT=Arial]sudo ufw status verbose
 [/FONT][/COLOR][COLOR=#000000]and recieved :
 [/COLOR]Status: activeLogging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

However nothing seems to be printing I will include more info.
Printer Properties:
Samsung CLP-360 Series
socket://192.168.0.118:9100
Samsung CLP-350 Series PS
Printer state: Idle - Waiting for printer to finish.

---

