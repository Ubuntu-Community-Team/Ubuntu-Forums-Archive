---
title: "Emails &amp; updating"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by gary65plus on 2012-10-16
Hi I'm gary65plus,
I new to Ubuntu and I want to find a new email.  I only want one email add. and bring all my contacts to it.    I don't want to import emails from other email providers.   Any suggestions  or ideas.   I have used Yahoo, Hotmail, Gmail,  and I don't really care for any to them.
  Also I am using Ubuntu 11.??  is there an advantage to updating to 12.04?   If there is how do I update to it and not lose any of my info on my compter??
Thanks

---

### Post by Warprunner on 2012-10-16
> **gary65plus said:**
> Hi I'm gary65plus,
I new to Ubuntu and I want to find a new email.  I only want one email add. and bring all my contacts to it.    I don't want to import emails from other email providers.   Any suggestions  or ideas.   I have used Yahoo, Hotmail, Gmail,  and I don't really care for any to them.
  Also I am using Ubuntu 11.??  is there an advantage to updating to 12.04?   If there is how do I update to it and not lose any of my info on my compter??
Thanks

I have used Thunderbird. It has alot of functionality. If you just want a fast Email program that grabs from say Gmail, I have been using Geary. PRetty quick but still hasn't hit a 1.0 release. HAven't found any issues with it yet though.

:guitar:

---

### Post by Frogs Hair on 2012-10-16
GMX allows importing contacts only , but I think one of your existing accounts should be able to do this as well. I'm not clear as weather you are looking for a new email provider or an email client like Thunderbird,Evolution, ext.    [http://www.gmx.com/](http://www.gmx.com/)

---

### Post by SWGraphics291 on 2012-10-16
I use Thunderbird and its pretty good. You can do a lot of stuff like import contacts, get add-ons and you can change the priority of a message.

---

### Post by jerrrys on 2012-10-16
12.04 is an LTS release and will be supported for five years.

You say that you are running 11.  I assume that to mean 11.10.  If thats the case you are already running gnome3 and the upgrade should be painless, but with upgrades there is always a risk involved.  11.10 is supported till april 2013, so you have plenty of time to decide.  If you want to do it, [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

sudo apt-get dist-upgrade

And then follow the instructions in the link below.

[http://www.ubuntugeek.com/upgrade-ubuntu-11-10-oneiric-ocelot-to-ubuntu-12-04-lts-precise-pangolin-desktop.html](http://www.ubuntugeek.com/upgrade-ubuntu-11-10-oneiric-ocelot-to-ubuntu-12-04-lts-precise-pangolin-desktop.html)

---

### Post by DuckHook on 2012-10-16
You don't mention what e-mail client you are already using. What is it that you are unhappy with? It may help those making recommendations to know what you don't like and then we can narrow down the range of recommendations.

---

### Post by gary65plus on 2012-10-17
I'll be honest with you,  I don't know what you mean by an email client??  I use Safe-mail.net, as of now..but I'm not satisfied with it.   I only want one email add.  and not import email  from from other email addresses.   Like I said I have used Yahoo, Hotmail and Gmail and really don't care for them..
Thanks

---

### Post by gary65plus on 2012-10-17
I had a screen on my computer that said an upgrade available,  so I decided to do it.  It took forever and when it came to the point where it wanted to restart the computer,  I clicked on it.   When it restarted Ubuntu never booted up or anything??  Absolutely Nothing...  I tried for an hour but got nothing.   So then I tried down loading Ubuntu 12.04  after downloading it from a CD.  the Ubuntu booted up,  only problem was there was nothing I could do,  alot of screen gibberish.  So I tried 2 other UBuntu 12.04 Disks from differnent sources, all with the same results.  So I went back to Ubuntu 11.10 and it worked.  Don't have the slightest idea what the problem was...  
This morning After reading the post here on the forum,  I went to the    Ubuntu software  application and selected Thunderbird email and it said it down loaded.  Butt, I can't find it>>>   
Also I want to go back to the classic Ubuntu tool bar at the top of the page,  how do I do that??  The one now is on the left side of the screen....  Help.   :0)

---

### Post by jerrrys on 2012-10-17
It sounds like you are on the unity desktop.  If you want to switch back to classic open a terminal and ..

sudo apt-get install gnome-session-fallback

Then log into the classic desktop at boot up (login window, click on top right icon).

---

### Post by gary65plus on 2012-10-17
Thanks I'll try that,

---

