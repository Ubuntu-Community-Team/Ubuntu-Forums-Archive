---
title: "Ibex and openoffice 3"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Harvs on 2008-10-30
Hi

I thought the upgrade to 8.10 included openoffice 3? I've done the upgrade, and it's still 2.4....
Cheers

---

### Post by LowSky on 2008-10-30
nope it came out too late for IBEX

its very easy to install though

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by Harvs on 2008-10-30
Ah, OK.

Many thanks for the link.

---

### Post by american.swan on 2008-10-30
Not helpful YET.

I used the deb files to upgrade to OO3.  For a few days I could use OO3.  That is what it said I was using.  Then I upgraded to Ibex and that broke my OO3 and after some "fixing" got 2.4 working again.  I added OO3 to my sources as this threads link said to do and tried upgrading and it says I have dependency problems that it refuses to fix, upgrade aborted. 

SO to put it frankly, what the hell do I do now?

openoffice.org-base-core:
 Depends: libstlport4.6ldbl  but it is not installable
 Depends: ure but it is not going to be installed

PLEASE HELP

Are my repositories messed up?  What the hell is wrong?  Why won't this work?
Forcing version doesn't even help.  I'm at my wits end.  This SHOULDn't be this hard.  I want to throw my computer out the window out of frustration.  There are some serious packaging conflicts.  What really pisses me off is when it tells me a dependent package won't be installed.  What kind of stupidity is that?  Sense when does Ubuntu tell a user what it can and can't do.  I'm the freakin' boss and this stupid machine is telling me it won't install what it needs to just to piss me off.   

Seriously, it's not the linux / open source way for a computer to say it can't do something.

---

### Post by american.swan on 2008-10-30
Bump  

help!!!!

---

### Post by american.swan on 2008-10-30
BUMP!!!  

I am never going to update without cause again.  This is absolutely stupid.

PLEASE HELP!! 

What do I do to get OO3 working...at this point I tried uninstalling OO2.4 so now I don't have any OO3 and I still can't find out to get OO3 install.

There are some SERIOUS problems with naming conventions or something.

THis is a disaster.

---

### Post by sayems on 2008-10-30
$ sudo gedit /etc/apt/sources.list

## Openoffice.org
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

$ sudo apt-get update

It should solve all your SERIOUS problem.

---

### Post by ad_267 on 2008-10-30
Remove all your previously installed open office packages first.

---

### Post by american.swan on 2008-10-30
> **ad_267 said:**
> Remove all your previously installed open office packages first.

Ok.  I'll try that.  I'll try un-installing all openoffice packages.  At this point sadly, I probably would have to do that one package at a time. 

Do you have any suggestion on how I could quickly do this?

---

### Post by ad_267 on 2008-10-30
> **american.swan said:**
> Ok.  I'll try that.  I'll try un-installing all openoffice packages.  At this point sadly, I probably would have to do that one package at a time. 

Do you have any suggestion on how I could quickly do this?

Open up a terminal and do:
```
sudo apt-get remove openoffice.org*
```

Then do a check in synaptic to make sure you got everything.

---

### Post by scradock on 2008-10-30
> **american.swan said:**
> Ok.  I'll try that.  I'll try un-installing all openoffice packages.  At this point sadly, I probably would have to do that one package at a time. 

Do you have any suggestion on how I could quickly do this?

I would suggest using Synaptic. Search on Openoffice, mark any installed packages to remove, then Apply.

---

### Post by hyper_ch on 2008-10-31
don't bump threads within 24h. It's not polite towards everybody else who also seeks advice.

---

