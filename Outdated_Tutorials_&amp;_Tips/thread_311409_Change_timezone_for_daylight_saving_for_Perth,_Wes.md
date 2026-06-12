---
title: "Change timezone for daylight saving for Perth, Western Australia's"
date: 2006-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by indulis on 2006-12-02
This implements the daylight savings rules rushed into operation (grrr!) by the WA govt in late November for a change to daylight saving on Dec 3.  That's today!
[http://wa.gov.au/daylightsaving/](http://wa.gov.au/daylightsaving/)

Well, some of the chaos has started already this morning, with the local newspaper's printing presses out of action, so only a limited supply of the newpapers are out there this morning (I think the ones that were printed were done before the changeover).

Anyway, on to the howto...

[LIST=1]
[*] Download the customised Perth & West Australian daylight savings file *Perth* o say /tmp
[http://matt.ucc.asn.au/time/Perth]("http://matt.ucc.asn.au/time/Perth")
[*] Open a terminal window, and [FONT="Fixedsys"][COLOR="Blue"]sudo sh[/COLOR][/FONT]
[*] [FONT="Fixedsys"][COLOR="Blue"]cd /usr/share/zoneinfo/Australia[/COLOR][/FONT]
[*] [FONT="Fixedsys"][COLOR="Blue"]cp Perth Perth_pre_daylight_saving[/COLOR][/FONT]
[*] [FONT="Fixedsys"][COLOR="Blue"]cp West West_pre_daylight_saving[/COLOR][/FONT]
[*] [FONT="Fixedsys"][COLOR="Blue"]cp /tmp/Perth ./Perth[/COLOR][/FONT]
[*] [FONT="Fixedsys"][COLOR="Blue"]cp /tmp/Perth ./West[/COLOR][/FONT]
[*] As per the information at [http://matt.ucc.asn.au/time/README.txt]("http://matt.ucc.asn.au/time/README.txt")
you can check if it using [FONT="Fixedsys"][COLOR="Blue"]zdump -v Australia/Perth[/COLOR][/FONT] and [FONT="Fixedsys"][COLOR="Blue"]zdump -v Australia/West[/COLOR][/FONT]
[*] Now reboot, your system time should have updated itself (assuming you are using NTP time servers), or if not you will have to reset your clock manually.
[/LIST]

I tested this on Breezy, but it should work the same on pretty much any version of Ubuntu, or for that matter on linux.

The nice thing about the timezone fix is that it includes all the start/end dates for the next 3 years.  Thanks Matt.  [Thantt!]("http://www.bbc.co.uk/comedy/lookaroundyou/")

Nice to see the [WA University Computer Club]("http://www.ucc.asn.au/") is still there, I was once a president of the UCC! Famous or infamous, make up your own mind.

---

### Post by cpudney on 2006-12-04
G'day,

Works for me.

Thanks,
Chris.

---

### Post by jk- on 2006-12-17
> **indulis said:**
> 
[LIST]
[*] Now reboot, your system time should have updated itself (assuming you are using NTP time servers), or if not you will have to reset your clock manually.
[/LIST]


Or, instead of rebooting, just run ```
sudo tzconfig
``` and re-set your timezone to Australia/Perth (ie, answer 'y' to the first question).

---

### Post by austux on 2006-12-24
Works fine for me under Mandriva Linux 10.0, 2006, 2007.0. Thank you!

The timezone-setter tool is called tzselect.

---

