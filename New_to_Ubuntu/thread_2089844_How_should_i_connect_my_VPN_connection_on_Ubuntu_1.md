---
title: "How should i connect my VPN connection on Ubuntu 12.04?"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by grafuar on 2012-11-30
I am trying to install Ubuntu 12.04 but when I get to a certain part it  says that I need  an internet connection to install some third-party  software. Now I have tried  to setup my connection but so far I have  been unsuccessful. On my windows laptop, I would just simply enable my  LAN connection, then I would open rasphone.exe dialer and type my username  and password and start the VPN connection but in Ubuntu, I have tried to  do the same thing in the VPN tab but it wont connect. I have also  googled this problem but did not find anything helpful. I hope you help  me solve my problem. Thanks. :(

---

### Post by critin on 2012-11-30
It's always best to install with an ethernet wired connection.  Plug an ethernet wire in your modem to computer for a sure internet connection.   Play with the VPN later.

Are you on dial-up internet?  If so, did you choose to install third party software during the install?  Unclick that option so you don't download any updates during the install.  You shouldn't need internet if you're not updating at the same time.

---

### Post by 2F4U on 2012-11-30
You may need to install VPN plugins according to this community documentation:

[https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient)

Another option would be to install without third-party software in the first place. This can also be done after Ubuntu is installed and configured.

---

### Post by grafuar on 2012-12-01
@critin Yes . I am on dial up internet. But I really dont know what I am supposed to do. I mean I've got this cable that I plug into my PC. I've got this* Broadcom 570x Gigabit* Integrated *Controller *cable (This is an ethernet connection, hopefully? :-k).  Then I check but the internet doesn't connect.   

@2F4U:  Thanks for the link. But you know what, the truth is, I've already  installed Ubuntu once without installing any third-party software. The  result was that when i opened my computer, all I could see was the one  "Untitled" folder sitting at the corner of my screen. No Ubuntu menu or  any other taskbars whatever. My screen was almost completely empty. I  knew right away that there was something wrong. Sp i decided to  reinstall with the third-party software button enabled. And thats how  I've ended up here. :confused:

---

### Post by critin on 2012-12-05
It's been too long since I used dialup, so I have no experience with it.   I googled and found some info, this is the newest link I found in a quick search--you might find something newer.  I don't know if this was solved but it does have some suggestions.

[http://ubuntuforums.org/showthread.php?t=1981550](http://ubuntuforums.org/showthread.php?t=1981550)

You will need to have an internet connection in order to download updates while installing, so if you can't configure the dialup connection, don't try to download any updates. They can all be updated after the connection is established.

I wonder if one of those USB wireless internet dongles would work?  I haven't used those either.  

The empty desktop really sounds like a graphic card issue.  You'll need help from a user who knows how to deal with that.

Good luck!

---

### Post by vpnbud on 2012-12-10
"No desktop" sounds quite strange. May be you have server version of Ubuntu?

May you should download Ubuntu for desktop: 
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

How to setup PPTP VPN on Ubuntu desktop: 
[URL="https://seed4.me/pages/setup/vpn-ubuntu"]https://seed4.me/pages/setup/vpn-ubuntu
[/URL] 

----------
Good luck!

---

### Post by grafuar on 2012-12-12
Thanks for the help guys!! 
I really appreciate it. I'll try out those links you've suggested and see how things roll!:D

---

### Post by asifnaz on 2012-12-12
are you trying to connect to a windows network..?

---

