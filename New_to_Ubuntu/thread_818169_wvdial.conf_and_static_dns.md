---
title: "wvdial.conf and static dns?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Loranga on 2008-06-04
How do I setup wvdial.conf to use static DNS:s?
I know that DNS:es should be configured in wvdial.conf like:

```

dns1 = 1.2.3.4
dns2 = 100.110.120.130

```

but how do I then deactivate the use of DNS which is acquired via the ISP?

---

### Post by spiderbatdad on 2008-06-04
I'm not familiar with putting dns in wvdial.conf, in fact it generally isn't done in ubuntu/linux.
The file /etc/resolv.conf contains dns info as a list

nameserver xx.xxx.xx
nameserver xx.xxx.xx
nameserver xx.xxx.xx

---

### Post by Loranga on 2008-06-04
The /etc/resolv.conf gets overwritten each time I start wvdial, with the DNS settings wvdial receives from my ISP when I connect.

---

### Post by ruffEdgz on 2008-06-04
I've searched around and I can't find anything that would help you set the DNS staticly. After reading some articles, it seems that the configuration of that file wouldn't accept

```

dns1 = xxx.xxx.xx.xx

```

Here are some links I read:

[http://linux.about.com/od/commands/l/blcmdl5_wvdialc.htm](http://linux.about.com/od/commands/l/blcmdl5_wvdialc.htm)
[http://linux.die.net/man/5/wvdial.conf](http://linux.die.net/man/5/wvdial.conf) (this is the same thing as the About.com page)
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)
[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)
[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)

Sorry :(

---

### Post by spiderbatdad on 2008-06-04
Do you have "auto dns" as an option in the wvdial.config file?

EDIT: apparently it is on by default. Try: Auto_DNS = no

---

### Post by Loranga on 2008-06-04
Unfortunately, Auto_DNS = no does not work. (Is it a syntax error perhaps?)

Another "weird" thing is that my original /etc/resolv.conf is moved to 
/etc/resolv.conf.pppd-backup and a new /etc/resolv.conf is created.
When I Ctrl-C wvdial.conf , it re-replaces everything back to the initial setting.

---

### Post by spiderbatdad on 2008-06-04
It may be a syntax error. I no longer have wvdial in use. It sholud be configured just like any of the other options, ie. Carrier_Check...
I thought that was the syntax...You could also try Auto_Dns = off


EDIT: ok looks like the syntax is to leave out the underscore: Auto DNS = Off

(possibly No)

---

### Post by 8200 on 2009-01-28
Hi Loranga!

Have you finally found a solution?

I have got the same problem.

Thank you

Regards
Arthur

---

### Post by nidelius on 2009-02-17
Edit /etc/dhcp3/dhclient.conf

Add or replace a line
```

Code:
prepend domain-name-servers your.name.server.ipaddr;

```

---

### Post by gnuchanux on 2009-03-22
OK. I've lost lot of hair pulling when I try-fail to set static DNS against wvdial. It took me so long & so many experiments to fix this.

Here's what I did to get rid of the dynamic DNS.

I edited the file:
/etc/ppp/peers/wvdial

And commented the line
usepeerdns

for total noobs: just add # before usepeerdns to make it look like
#usepeerdns

Now wvdial won't ask pppd to get namesrever addresses using the option usepeerdns. So whatever the DNS addresses you mention on the file
/etc/resolv.conf
will remain unharmed by dialing process.

PS:
adding
Auto DNS = off 
in
/etc/wvdial.conf
should work according to my knowledge extracted from wvdial man page. However the man page is vague & that option simply doesn't make things right.

---

### Post by frankvw on 2009-09-05
> **gnuchanux said:**
> OK. I've lost lot of hair pulling when I try-fail to set static DNS against wvdial. It took me so long & so many experiments to fix this.

I'm still in the hair-pulling stage, and I don't have much hair left, so things are getting a bit worrying at this point. :-)

> **gnuchanux said:**
> 
I edited the file:
/etc/ppp/peers/wvdial

And commented the line
usepeerdns


That line did not occur in my wvdial.conf so I cannot comment it out. I tried 'usepeerdns = no' but to no avail. I have wvdial 1.60 and its default behavior now seems to be to use the ISP's DNS and clobber whatever I put in /etc/resolv.conf... :(

> **gnuchanux said:**
> 
adding Auto DNS = off in /etc/wvdial.conf

...didn't do anytihng for me either.

Suggestions, anyone? My DNS settings keep getting clobbered... :(


// FvW

---

### Post by GeorgeVita on 2009-09-06
Hi **frankvw**, can you try: ```
gksudo gedit /etc/ppp/peers/wvdial
``` and make it like: ```

name wvdial
noauth
nodefaultroot
noreplacedefaultroute

```
(above data came from terminal command: **man pppd**)

Regards,
George

---

### Post by cdinz on 2009-11-12
Well here is how I resolved the problem...

1) > gksudo gedit /etc/ppp/peers/wvdial
and then comment out the usepeerdns line
> #usepeerdns
If it is not there add it...


2)Next edit the wvdial.conf file
> sudo gedit /etc/wvdial.conf
and add this line:
> Auto DNS = off


3)Next edit the resolv.conf file
> gksudo gedit /etc/resolv.conf
and add ur DNS servers
> 
nameserver 208.67.222.222
nameserver 208.67.220.220

---

### Post by qwertz333 on 2010-05-13
To make it work on my laptop, I did EXACTLY the same as cdinz, (which did not work at first). What made it work in the end was following another suggestion mentioned in this thread:

I uncommented the line

#prepend domain-name-servers 127.0.0.1;

and changed it to:

prepend domain-name-servers 208.67.222.222,208.67.220.220;


After this final change, my DNS worked again and [http://www.opendns.com/welcome/](http://www.opendns.com/welcome/) confirmed that I was using the OpenDNS servers.

Many thanks to everyone who shared their suggestions and experiences in this thread, you saved me a lot of time!:popcorn:

---

