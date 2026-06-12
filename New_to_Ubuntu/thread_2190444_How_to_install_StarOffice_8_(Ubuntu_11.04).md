---
title: "How to install StarOffice 8 (Ubuntu 11.04)"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by federicodemaria on 2013-11-27
I've downloaded the software in a .zip folder, and I've not been able to install it. 
It's in /home/user/downloads

I've followed the instructions at 
[http://ubuntuforums.org/showthread.p...ght=staroffice](http://ubuntuforums.org/showthread.p...ght=staroffice)
[https://help.ubuntu.com/community/StarOffice](https://help.ubuntu.com/community/StarOffice)
or watching the video 
[http://www.youtube.com/watch?v=iBQtKTnMppE](http://www.youtube.com/watch?v=iBQtKTnMppE)
Didin't manage. 

First, I've failed to install 'alien' (I had a problem of Unmet dependencies). 
Tried with aptitude but I failed too. 
[http://ubuntuforums.org/showthread.php?t=1739760](http://ubuntuforums.org/showthread.php?t=1739760) 
Tried to solve problem with Unmet dependecies, but didn't manage too 
[http://ubuntuforums.org/showthread.php?t=1934266](http://ubuntuforums.org/showthread.php?t=1934266)

I've used Ubuntu and Open Office for years now, but as I work a lt on documents, I wanted to try StarOffice. 

Thank you for your kind help 

Best, 
f

My Ubuntu: 
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

---

### Post by philinux on 2013-11-27
The problems you're getting is because 11.04 reached end of life for support on Oct/28/2012.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Also staroffice is also discontinued as of 2011.

[http://en.wikipedia.org/wiki/StarOffice](http://en.wikipedia.org/wiki/StarOffice)

---

### Post by federicodemaria on 2013-11-27
So, what I should do, is to update to a newer Ubuntu release and StarOffice version, right? 

Thanks
f

---

### Post by philinux on 2013-11-27
> **federicodemaria said:**
> So, what I should do, is to update to a newer Ubuntu release and StarOffice version, right? 

Thanks
f

Star office is dead. Ubuntu now uses Libreoffice.  The choice you have is to install an LTS 12.04 or the latest ubuntu 13.10. Both come preinstalled with Libreoffice.

[http://en.wikipedia.org/wiki/LibreOffice](http://en.wikipedia.org/wiki/LibreOffice)

---

### Post by federicodemaria on 2013-11-27
Got it now. I'm already using LibreOffice and is working fine, but some times I need more advanced features that -at the moment- only Office offers. 
For example: 
- Compatibility with .docx: if I use track changes in libre office, they don't get saved. Thus, I have to change it into .doc 
- Excel's pivot table: the one in LibreOffice is very basic. 
- etc.

Therefore, I now have Dual Boot with Windows (and Office). I had also try to run Office in Ubuntu with Wine, but never manage to do so. It might be easier now with LTS 12.04 or the latest ubuntu 13.1.

Thanks for your suggestions

Best, 
f

---

### Post by philinux on 2013-11-27
Unfortunately even with the latest libreoffice some docx documents get squished and format really bad. Only alternative is windows office for those. That's why I dual boot win 7.

---

### Post by su:bhatta on 2013-11-27
Actually you can try WPS, also known as Kingsoft Office Alpha12, it is compatible with docx files.
I am using it for a month now, and I no longer go back to LibreOffice.


You can get the deb file of Kingsoft office from here: [http://wps-community.org/download.html](http://wps-community.org/download.html)

---

### Post by philinux on 2013-11-27
I'll try that with a particularly bad formatted docx in libre office.

---

### Post by kurt18947 on 2013-11-27
Where does Softmaker Office rank these days for MSO file compatibility?  At one time it was supposed to be very good.

---

### Post by federicodemaria on 2013-11-28
Thanks, I'll try this... any alternative to Windows and Office is welcome

---

### Post by river2 on 2013-12-02
@[**[COLOR=#000000]kurt18947[/COLOR]**]("http://ubuntuforums.org/member.php?u=1447222") 	 

I use SoftMaker Office for Linux at home, and Microsoft Office at the office: compatibility between those two office suites is very good, it works faithfully in both directions.

@[**[COLOR=#000000]federicodemaria[/COLOR]**]("http://ubuntuforums.org/member.php?u=693014")

I can highly recommend SoftMaker Office not only for its compatibility, but it has many other merits, too. If you want to try it out, you can start with SoftMaker FreeOffice, that's a free office suite you get at freeoffice.com/en with less features and templates as SoftMaker Office. However, its in my opinion much better than LibreOffice, or Kingsoft, these have too many quirks.

---

