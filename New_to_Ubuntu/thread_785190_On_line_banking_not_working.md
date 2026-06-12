---
title: "On line banking not working"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by timswait on 2008-05-07
I've just loaded xubuntu 8.04 onto a laptop and now I can't access on line banking (Natwest -here [http://www.natwest.com/tools/general/nwolb_browsers/index.asp]("http://www.natwest.com/tools/general/nwolb_browsers/index.asp")). It's really important to me that I can use the online banking, so what's the best way round this? It says it supports Firefox version 1.5 and 2.0 in windows, and the version in Linux I'm using is 3.0b5, would downgrading to an earlier version work?
BTW, I've used other online banks, which do work with Ubuntu, it only seems to be Natwest with the problem :(

---

### Post by Joeb454 on 2008-05-07
Natwest does work (I have the same bank) Search the Firefox plugins for something called User Agent Switcher. Install that and then change it to Internet Explorer 7 from the Tools menu in Firefox when you are on the page - then reload.

It should load then - this is how I access the online banking :)

---

### Post by timswait on 2008-05-07
Cheers dude, sorted!:)

---

### Post by hrod beraht on 2008-05-07
Unfortunately it happens where a website will look strictly for Firefox 2 and if you've got a newer/higher version, it won't compute.

Generally, it's just sloppy programming. I would definitely mention it to your bank.

In the meantime, you can change the User Agent from within Firefox - no outside app needed.

Type **about:config** in the address bar.
Type **useragent** in the filter bar.
You will see a line that looks something like: general.useragent.extra.firefox   default   string   Firefox/3.0b5
Just change the 3.0b5 part to 2.0 and your bank should accept it. You shouldn't have to do any kind of work-around, but until your bank gets on the ball...

And while the other suggestion of the User Agent Switcher add-on will work too, what is problematic is using Firefox on Linux and all the while you are telling the web that you are using Internet Explorer on Windows. Is that really the best way to go? If you do use the User Agent Switcher add-on, please create a new entry that shows Firefox 2 on Linux. Don't pretend to be Windows! There are enough sloppily constructed Windows-specific web sites out there already. Why encourage them further?

Bob

---

### Post by Steel Lord on 2008-05-07
Hmm...similar problem with Ulster Bank.

The banks are probably waiting for the final release Firefox 3.0 so that they can be sure of security. Which is fair enough. I'm comfortable just booting up windows to check the dire state of my finances in the mean time.

---

### Post by tjwoosta on 2008-05-07
with the user agent switcher add-on it will work, but you have to make sure to change the user agent back afterward because i have noticed that firefox will keep continuously freezing up if you leave it on internet explorer user agent

also with the user agent switcher add-on you can switch to Internet Explorer, Firefox, or Opera agents

---

### Post by t0p on 2008-05-07
This problem of online banking sites not working properly for linux/firefox is an artificial problem - a problem created by the banks for no good reason.

A great many banks around the world insist that you use Internet Explorer to access their services.  But this is often down to sloppy website coding - a properly-formed website should work for any browser.  And sometimes I suspect that the banks insist on Internet Explorer because of vested interests they have in Microsoft and the proprietary software market in general.

This is an area where the combined might of Linux users can make a difference.  We should all insist that our banks allow us to service our accounts no matter what operating system or browser we run.  And if the bank fails to take heed, move your account - take your business to a bank that actually gives a fig.

Unfortunately, I can't tell you which banks operate fine with Linux/Firefox.  But I'm sure some of you must know of some fine, upstanding banks.  So tell us who they are!!

---

### Post by upthelum on 2008-05-07
I use Netscape Navigator which works fine with Bank of Scotland, but the support for Navigator has stopped so i will probably have to move back to Firefox at some point. I only stopped using it after an update slowed it down terribly.

---

### Post by timswait on 2008-05-08
Lloyds TSB and Britannia building society both work fine with Linux/Firefox 3. :)

---

