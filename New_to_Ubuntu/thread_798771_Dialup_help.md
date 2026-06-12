---
title: "Dialup help"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by altonbr on 2008-05-18
Is there are more help for Dialup users than this page/script? [https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)

I have a client that needs dial-up enabled but that script doesn't give us any useful information.

---

### Post by shifty_powers on 2008-05-18
what modem is he using? is it an external one, or one that is internal?

(winmodem's are software modems and notoroiusly a pin in the *** in linux ;))

---

### Post by altonbr on 2008-05-18
I'm not even sure what modem they're using. It's internal and came with the PC and Vista pre-loaded. I wiped them to Ubuntu and this has been the only problem thus far.

---

### Post by HotShotDJ on 2008-05-18
> **altonbr said:**
> I'm not even sure what modem they're using. It's internal and came with the PC and Vista pre-loaded. I wiped them to Ubuntu and this has been the only problem thus far.
There is really nothing to be done until you are able to identify the modem.  ScanModem will get you that information.

---

### Post by spiderbatdad on 2008-05-18
probably going to need to buy an external modem.
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

[http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.debianadmin.com/setting-up-dial-up-connection-in-ubuntu.html)

and this useful guide:[http://www.aboutdebian.com/modems.htm](http://www.aboutdebian.com/modems.htm)

---

### Post by HotShotDJ on 2008-05-18
> **spiderbatdad said:**
> probably going to need to buy an external modem.
While this may, indeed, be the case, the advice is somewhat premature.  Some internal modems can, and do, work just fine in Linux.  Others, unfortunately, do not and never will.  Until we learn what the output of ScanModem is, we have no way of telling if altonbr's client is one of the luck or unlucky ones.

---

### Post by spiderbatdad on 2008-05-18
> **HotShotDJ said:**
> While this may, indeed, be the case, the advice is somewhat premature.  Some internal modems can, and do, work just fine in Linux.  Others, unfortunately, do not and never will.  Until we learn what the output of ScanModem is, we have no way of telling if altonbr's client is one of the luck or unlucky ones.

```
lspci
```
will identify the modem. not aware of any softmodems in windows pc's that aren't "winmodems" and while some can be tweaked with a great deal of work, to operate feebly, it isn't worth the effort.

---

### Post by altonbr on 2008-05-18
ScanModem said that their was no fix for the modem.

I'll have to get the direct output for you guys, including lspci.

That's why I was hoping there was more than just ScanModem else it looks like it's back to Vista, or purchasing an external modem.

---

### Post by HotShotDJ on 2008-05-18
> **altonbr said:**
> ScanModem said that their was no fix for the modem.In that case, there really is nothing more to be done other than purchasing an external modem for your client.

@spiderbatdad: lspci may or may not list a softmodem.  I know on my laptop, while ScanModem found it, lspci did not.  Also, with the drivers provided by Dell for my softmodem (Conexant HDA)... it works perfectly with only the effort of installing the deb provided by the manufacturer.  Of course, result will vary across different vendors and MANY, if not MOST soft-modems are garbage.  But the blanket statement that "while some can be tweaked with a great deal of work, to operate feebly, it isn't worth the effort" is really not correct

---

### Post by spiderbatdad on 2008-05-18
> **HotShotDJ said:**
> In that case, there really is nothing more to be done other than purchasing an external modem for your client.

@spiderbatdad: lspci may or may not list a softmodem.  I know on my laptop, while ScanModem found it, lspci did not.  Also, with the drivers provided by Dell for my softmodem (Conexant HDA)... it works perfectly with only the effort of installing the deb provided by the manufacturer.  Of course, result will vary across different vendors and MANY, if not MOST soft-modems are garbage.  But the blanket statement that "while some can be tweaked with a great deal of work, to operate feebly, it isn't worth the effort" is really not correct
It is my opinion. And it is correct.

---

