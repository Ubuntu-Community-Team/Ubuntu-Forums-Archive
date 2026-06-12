---
title: "trouble installing Xerox Workcenter 7428"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by brunoscunha on 2011-11-03
Hi

I'm having a hard time trying to connect to a Xerox Workcenter 7428 at work.
I've downloaded and installed the XeroxPrinterPkgXPXX_WC7425_2009_01_26.tgz and XeroxLinuxi386XPXX_4.30.09.tgz
and still can't find the correct printer model on the printer list.
Some help please.

Thank you

PS: I'm using 11.10

---

### Post by Azdour on 2011-11-03
Hi,

I had a similar problem yesterday with a Canon printer. I installed it but it never appeared in the list of printers. In the end I found it had installed the ppd for the printer under /usr/share/ppd. Maybe you can find your Xerox ppd there as well?

---

### Post by brunoscunha on 2011-12-16
No, nothing that can help is there :(

---

### Post by Azdour on 2011-12-16
Hi,

Having taken a look in XeroxPrinterPkgXPXX_WC7425_2009_01_26.tgz it does not contain a ppd for the 7428, the nearest one I can see is the 7425.

I also stumbled across [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/616556](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/616556).

Look at post number 2, it contains a ppd. When I looked in the ppd it says:

```
*Product: "(WorkCentre 7425/7428/7435)"
```

Maybe you could try to install the printer by using this ppd?

---

### Post by wademac on 2012-11-20
FYI anybody with this issue PPD is on the website here is the link.. the [Generic PPD]("http://www.support.xerox.com/support/workcentre-7425-7428-7435/file-download/enus.html?operatingSystem=winxp&fileLanguage=en&&associatedProduct=built-in-controller--wc7435-&contentId=110697&from=downloads&viewArchived=false") works great :)

[http://www.support.xerox.com/support/workcentre-7425-7428-7435/downloads/enus.html?associatedProduct=built-in-controller--wc7435-&operatingSystem=winxp](http://www.support.xerox.com/support/workcentre-7425-7428-7435/downloads/enus.html?associatedProduct=built-in-controller--wc7435-&operatingSystem=winxp)

---

