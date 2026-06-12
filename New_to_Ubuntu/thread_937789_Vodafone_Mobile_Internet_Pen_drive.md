---
title: "Vodafone Mobile Internet Pen drive"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Lahlah on 2008-10-04
Hi,

I'm an absolute beginner in doing this so if anyone can help me and make it as simple as possible I would be very grateful.  Also if anyone else is trying to do this I'd appreciate a heads up as two heads are better than one.  

I uploaded ubuntu on an old laptop I got from my work and have signed up to Vodafone Mobile internet.  The thing works fine on my desk top (hence I'm speaking to you now).  But I can't get it to work on my Ubuntu laptop.  When I put the thing in it shows the pen fine, and what's on the disk fine.  But when you click on them to run it opens the items like a document, and just shows pages of script.  

Apparently you can get a Linux driver (?) for the pen drive, but if I down load this onto Ubuntu will it then mean the pen will work fine or will I have to do some additional tweakage?  

Last request:  Could I have the steps as simple as possible.  Please don't underestimate my neivety (sp?) in this.  I've downloaded stuff from the web before, but I don't understand it.  All I want it to do is work. 

Thanks
Lah x

---

### Post by gimlithedwarf on 2008-10-04
More likley than not the executable on the pen drive is a windows executable, you could try installing wine by going to add/remove and searching for wine. Failing that you should probably search vodafone's website for linux drivers.

---

### Post by Lahlah on 2008-10-04
Hi G, 

Thanks for the reply.  What do you mean by executable? Is that something I should be looking for on the pen, or something that's workable.  Ubuntu won't run any of the folders on the pen drive it just keeps opening them up and displaying them as readable script. 

thanks again

Lx

---

### Post by johnystevenson on 2008-10-04
also a newbie here and am very interested in where this post goes, as i plan to get the vodaphone pen drive in a few weeks.  Sorry i cant contribute any help

regards

jonhny

---

### Post by Lahlah on 2008-10-05
Cheers Johnny, it's nice to know my request isn't completely 'out there'.  

I've been on the Betavane website (which seems to be some sort of applications hub for vodafone) and left a message on their forum. And I've also been on the Vodafone website too, as of yet to no avail but I'll keep you posted.  I'm having some trouble in understanding the language as they're all pretty much talking techie. 


I've found wine on Ubuntu on the lap top but it won't let me download it.  Is this because it's not connected to the web?  

Cheers.

Nx

---

### Post by philinux on 2008-10-05
[http://forum.vodafone.co.uk/index.php?showtopic=6583](http://forum.vodafone.co.uk/index.php?showtopic=6583)

Seems like someone else had same problem.

---

### Post by Kevbert on 2008-10-05
I'd also be interested in this drive.  I've found what looks like a driver [[COLOR="Red"]here[/COLOR]]("https://forge.betavine.net/projects/vodafonemobilec/").  The only thing is it's in development.  Please post back on how you get on.
Cheers
Kevin.

---

### Post by Tomatz on 2008-10-05
ndiswrapper?

---

### Post by barbedsaber on 2008-10-05
you would be needing the new version of network manager. It allows connections through many of these 3G devices.
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/) the download link is on the right side, it should be a tar.somthing (I forgot what source packages are, oh the shame)

EDIT: never mind, the latest version isn't there, I know that it will be in 8.10 (intrepid ibex, to be realsed on the 30th of October) there has to be a way to get network manager 0.7 before then. hmm

---

### Post by Lahlah on 2008-10-05
I've downloaded Wine onto a pen drive from my windows computer.  I've put it into my Ubuntu lap top.  How do I get the package to download onto Ubuntu.  I've tried running it on auto run.  I've tried using the add/remove application but it keeps looking for it from the web which I don't have because I can't get my mobile pen drive to work.

Suggestions please!

Nx

---

### Post by gandaran on 2008-10-05
> **Lahlah said:**
> I've downloaded Wine onto a pen drive from my windows computer.  I've put it into my Ubuntu lap top.  How do I get the package to download onto Ubuntu.  I've tried running it on auto run.  I've tried using the add/remove application but it keeps looking for it from the web which I don't have because I can't get my mobile pen drive to work.

Suggestions please!

Nx
what type of wine package you have? is it a .deb? if it is and if you have transfered the package to ubuntu you just double click to install just like in windows

for the vodafone mobile pen you need to install the vmc-card-driver-linux package

---

### Post by Lahlah on 2008-10-05
No it's says tar.bz2.  Have I downloaded the wrong thing?

---

### Post by gandaran on 2008-10-05
> **Lahlah said:**
> No it's says tar.bz2.  Have I downloaded the wrong thing?
for a linux newbie don't install those type of packages, look always for .deb, you can get the wine .deb here [http://www.winehq.org/site/download](http://www.winehq.org/site/download)

sorry, you still need internet for this, find the wine package from hardy repos here [http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages)

---

### Post by Lahlah on 2008-10-05
Sorry to be a complete pain in the @$$ but where?  I've clicked the Ubuntu bit and it goes to another page which recommends going onto another page to down load then gets an error because the page doesn't exist.  Am I missing something completely here?

Nx

Hi, sorry! Just clicked onto your other link.  I've saved a copy, what do I do with it?

Nx

---

### Post by gandaran on 2008-10-05
> **Lahlah said:**
> Sorry to be a complete pain in the @$$ but where?  I've clicked the Ubuntu bit and it goes to another page which recommends going onto another page to down load then gets an error because the page doesn't exist.  Am I missing something completely here?

Nx

Hi, sorry! Just clicked onto your other link.  I've saved a copy, what do I do with it?

Nx
just double click to install, probably you'll get a missing dependencies error, which you'll have to get them from the same site and install them first

just one question, what do you want wine for? if it is to install the vodafone windows drivers, it won't work!

---

### Post by Lahlah on 2008-10-05
*screams quietly to self*.  Yeh that's what it's for.  If that won't work do you know what will?  There's alot of advice in here and I'm trying to sift through it.

---

### Post by gandaran on 2008-10-05
then get your  drivers here [https://forge.betavine.net/frs/?group_id=12&release_id=116](https://forge.betavine.net/frs/?group_id=12&release_id=116)

---

