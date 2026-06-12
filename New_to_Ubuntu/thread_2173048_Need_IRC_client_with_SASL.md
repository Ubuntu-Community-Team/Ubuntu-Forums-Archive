---
title: "Need IRC client with SASL"
date: 2013-09-07
forum: New to Ubuntu
---

### Post by daal on 2013-09-07
Hi, Yes I have seen the freenode list and for Ubuntu (12.04 or any) thre is no client I can find with SASL built in and the scripts on line dont work. 

AFAIK.  Alas.

In that list many are for other platforms, exclusively. Others take scrips, as I mentioned.
There are a few that seem more like project than completed works that do not specify platform, that I know of, and I cant see how to install.

Confession: I only install with apt-get.

In addition I tried irssi but it seems to have a GUI version I have to do :some stuff" I don't understand and thus cant follow. And that's before I try to install the separate script for SASL.

I am pretty lost here. I should tell you why I need SASL. My internet supply comes through my phone and since freenode finds that less than secure, I have to authenticate with SASL. 

Thanks.

---

### Post by rai_shu2 on 2013-09-07
Actually, [this]("http://freenode.net/sasl/sasl-xchat.shtml") is probably your best bet.

---

### Post by oldos2er on 2013-09-08
irssi supports sasl: [http://ubuntuforums.org/showthread.php?t=1010780](http://ubuntuforums.org/showthread.php?t=1010780)

---

### Post by andrew.46 on 2014-02-08
> **oldos2er said:**
> irssi supports sasl: [http://ubuntuforums.org/showthread.php?t=1010780](http://ubuntuforums.org/showthread.php?t=1010780)

Indeed it does but looks like at the moment there is[ a small issue with sasl authentication with Freenode]("http://blog.freenode.net/2014/02/turbulence/") in that only PLAINTEXT is supported and not BLOWFISH. For irssi this means:

```

/script load cap_sasl.pl
/sasl set Freenode <primary-nick> <password> **[COLOR="#FF0000"]PLAIN[/COLOR]**
/sasl save
/save

```

is required at least for the next little while rather than **[COLOR="#FF0000"]DH-BLOWFISH[/COLOR]**. Should not be a big drama as this occurs over an SSL connection but it is a *slight* decrease in security. Not sure how other irc clients need their settings adjusted....

---

