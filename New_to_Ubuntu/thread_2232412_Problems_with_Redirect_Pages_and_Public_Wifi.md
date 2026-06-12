---
title: "Problems with Redirect Pages and Public Wifi"
date: 2014-07-01
forum: New to Ubuntu
---

### Post by john257 on 2014-07-01
Hello,

I am using an IBM Thinkpad T42 with Lubuntu 14.04 installed. Wireless is working very well at home with WPA2 encryption. However, I notice that when I take the laptop out to a place like Panera or Whole Foods to use their wifi I cannot connect. 

I am pretty sure that I know that the redirect page required to login is the cause of this. On Windows or Mac OS X, the redirect page comes up, I hit login, and then I am connected to the Internet. I am not saying this to say anything negative about Linux. I greatly enjoy Linux's benefits. I am just trying to give a reasonably clear description of the problem. 

I have two questions. 

First, if I wanted to learn more about the cause of this problem, where could I read more about it? Searches on Google to find out how such redirect pages work have been fruitless. I am guessing that they make use of some piece of Javascript. 

Second, what practical steps can I take to address this problem? I saw a thread on elsewhere about this that suggested switching to the Broadcom STA driver. However, I do not want to do this if this is the wrong driver for me to use. I am in the midst of other work and a migraine; so, if I have not been clear about anything, my apologies.

John

---

### Post by grahammechanical on 2014-07-01
Does that Thinkpad have a Broadcom wireless adapter? If it does not then installing the Broadcom STA driver would make things worse. What is more, you say that wireless is working fine. So, why mess around with wireless drivers? Is the Thinkpad able to detect the WiFi access points? So, wireless is working. I do not see how changing the driver would solve this.

Regards.

---

### Post by squakie on 2014-07-02
Do those networks show in network manager and can you connect from there?

---

### Post by squakie on 2014-07-02
BTW - is the wireless built-in or a USB dongle?

Please post back the output of the following:

If internal:

lspci | grep Network

If USB:

lsusb

That should help us identify you wireless adapter.

As far as the can't log in thing, what exactly does you do, and what does it say?  Be as detailed as possible.

---

### Post by bart14 on 2014-10-06
Hello,
I think i'm facing the same problem.

I have the ability to connect to my internetprovider via WIFI on different locations (café, station,...).
In windows I just select the wireless network from my provider and when I then open IE it automatically goes to an inlogpage of my provider.
In Ubuntu it works the same way (with chrome).
(Sometimes I does'nt work from the first try and then I have to enter the URL of my provider to get to the inlogpage.).
I installed Lubuntu 14.04 on an older laptop. When I click on the network icon, I see several possible wireless connections. One of which is my internet provider.
I click on it. I then open firefox: no automatic rerouting to the inlogpage of my internet provider (I get a no connection error). Even when I type in the URL of the provider directly into the adress bar.So: normally (windows / ubuntu) there is some limited internet access to the login page of my provider (and when logged in I have complete interent access).
In Lubuntu: I get no access at all.
Is this Lubuntu related? Am I missing some setting?
Or is this Firefox related? 

Thanks for any advice.
Bart

---

### Post by Vladlenin5000 on 2014-10-06
Have you tried with Chrome/Chromium already in that Lubuntu?
Indeed, many of those "walled gardens" were designed for IE although usually they also work with other browsers in Windows/Mac. Some, unfortunately, don't properly handle requests with a Mozilla/Linux header. Other browsers and simply a Firefox addon forcing it to report itself as coming from Windows - similar to those required for a famous video streaming service, not so long ago - might work.

---

### Post by bart14 on 2014-10-18
Thank you for the suggestion, and sorry voor the delay but only every now and then I try working on that old laptop.

Google chrome is not an easy one. As I have no internet access on that older laptop,  I have to download the ubuntu version on an other computer which isn't all the easy. Google just installs chrome on you windows system even if you click the download button for ubuntu/linux. There's no obvious way to get the installation file. Google just seems to think that they know best, and if you click any download button we just install the right version for you.

But somehow I managed to get the google-chrome-stable_current_i386.deb file.

I transferred it to the desktop of Lubuntu. Dubbelclicked and then the package installer gave the message:  Error:  [FONT=Courier New]dependency is not satisfiable [/FONT]libappindicator1.
I tried some solutions to get chrome installed through googling, but no success.

Bart

---

### Post by Vladlenin5000 on 2014-10-18
You can install Chromium directly from your Lubuntu Software Center. It's the same as Chrome minus Goggle's proprietary code (Google uses Chromium as a base for Chrome).

Obs.: It's just a suggestion. I'm not sure it works for your specific purpose -and- you should contact the IT department and let then know about the difficulties you're experiencing.

---

### Post by bart14 on 2014-10-24
Thank you for your reply.
Would installing through the software center work as I have no internet access?

I also tried installing midori browser but I get the same type of problem:  Error:  [FONT=Courier New]dependency is not satisfiable [/FONT]... .

I just try to install Lubuntu on an older laptop -> The IT department = me. ;-).

Thanks for any further suggestions.

---

### Post by bart14 on 2014-10-24
Some additional information.
To recap: In Lubuntu if I click on the two small computer screens icon in the right corner, I can see several wireless options. One of them is my service provider, ic click it. Normally the browser is opened automatically or if not, if I open the browser I get redirected to a login page (I think the correct term is 'Captive Portal'?). Yet on lubuntu I get cannot connect to server from Firefox.

Additional info: If I open Lubuntu > Preferences > Network Connections, in that dialog box only 'ethernet wiredconnection 1' is shown? 
1/ Should the wireless connection be already visible in that box too? Or only after login in via the login page (in which I don't succeed).
2/ I can click to add a wireless connection. But I need the fill in things like SSID, MODUS,... . Which I never had to do on my other computers. 

Thanks.

---

