---
title: "Confused about the version I'm running"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by kidoxer on 2013-01-23
My question concerns my mother's computer. After she managed to kill WinXP (virus) that came pre-installed on her Dell I decided that she will be safer with Ubuntu and it'll be easier for me to have at least some control over her system, even though I'm far from being Linux expert. 

Since we live on different continents I had to install the new OS remotely which turned up to be pretty easy with LiveCD + reverse VNC (Gitso). 

This installation has been working fine for a few years and we have successfully connected several accessories (scanner, printers, 3G modem, camera etc.). Because of her network connection I keep using the reverse VNC to connect and remotely control her computer.

I believe we've started with Ubuntu 8.10 or 9.04 and since then we have been successively upgrading to newer versions using the Update Manager. At some point I decided that we won't keep upgrading because of the risks involved. Her needs are not very sophisticated and as the old saying goes: "If it ain't broken..."

Unfortunately I forgot on which version we have stopped our upgrading adventure and when the question arose I got confused:

- when I check in System > About Ubuntu it says:
"You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012."

- when I run cat /etc/lsb-release; uname -a , I get the following:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux xxxxx-desktop 2.6.35-32-generic #68-Ubuntu SMP Tue Mar 27 17:01:54 UTC 2012 i686 GNU/Linux
```


Should I treat that system as 11.04 or 10.10? Did the upgrade process went wrong or is it just some kind of inconsistency on version reporting? Should I fix this and if so, how do I do that?

---

### Post by d4m1r on 2013-01-23
[https://help.ubuntu.com/community/CheckingYourUbuntuVersion](https://help.ubuntu.com/community/CheckingYourUbuntuVersion)

[http://askubuntu.com/questions/150917/what-terminal-command-check-the-version-of-ubuntu-that-you-have](http://askubuntu.com/questions/150917/what-terminal-command-check-the-version-of-ubuntu-that-you-have)

^Between the 2 options (UI, About/Help Tab vs command line lsb), I would assume the command line is more trustworthy. Also, you can try to upgrade from update manager and see what version it tries to install? You can cancel it before it does anything as well...

---

### Post by kidoxer on 2013-01-27
> **d4m1r said:**
> Also, you can try to upgrade from update manager and see what version it tries to install? 

Thanks for your suggestions. The above seemed as the best option. This installation definitely thinks it's 10.10 since it has tried to upgrade to 11.04.

---

