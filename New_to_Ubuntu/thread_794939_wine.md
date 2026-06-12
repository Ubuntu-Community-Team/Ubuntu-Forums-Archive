---
title: "wine"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by lil_bunny on 2008-05-15
ok iv just downloaded some virtual world software and when i click it it trys to open it with wine it seems to go through the process but then never gets past please wait a few moments while application starts ...

does this mean i just cant be run through wine or use at all with ubuntu the system requirments is for windows xp / 2000 but it hought thats what wine was for???:confused:

---

### Post by Xiong Chiamiov on 2008-05-15
Wine is by no means perfect.  Don't expect to be able to run everything that's built for Windows.

Do us a favor and launch wine from the terminal and post what it says.
```

cd ~/.wine/drive_c/Program\ Files/
cd [to the specific directory where the program is located]
wine [name of application]

```

---

### Post by ZabiGG on 2008-05-15
Hi ;)

Wine is kind of tricky...

May I suggest you open this link:

[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)
(it's a special Google version that looks only in Ubuntu-related content)

and search like this (include the quotation marks)

wine "name of the application you're having trouble with"
(the quotations keep the app name together if it's more than one word, so it returns content with this specific phrase instead of the individual words scattered all around.

Odds are you're not the first person to experience a problem with this application, and I don't know wine enough to help you more specifically.

Have a great day,

---

### Post by master5o1 on 2008-05-15
By virtual world software do you mean:

a) Virtualisation of an Operating System.
b) A "virtual world" game (ie. The Sims, Civilisation, SimCity).
c) Other (explain?)

For a) You can always use VirtualBox or VMware for your virtualisation.
For b) Civilisation can be ~replaced~ by FreeCiv game. The Sims and SimCity.. um :S
For c) well I'll just have to wait and see...


Edit: Or do you mean something from [Virtual World Software Ltd.]("http://www.virtualworlds.info/")?

---

### Post by lil_bunny on 2008-05-15
tried the google thing it cant find it

It's A i think lol

---

### Post by Xiong Chiamiov on 2008-05-15
Option A is to install one operating system inside of another.  Is that what you're doing?  Could you provide us a link to the site where you found the software you're trying to install?

---

### Post by lil_bunny on 2008-05-15
downloaded virtual box , and im baffled with it how do i use it

---

### Post by master5o1 on 2008-05-15
What's the filename and where did you get it from? (And what is it used for?)

---

### Post by Xiong Chiamiov on 2008-05-15
> **lil_bunny said:**
> downloaded virtual box , and im baffled with it how do i use it
If you didn't, you should install virtualbox through apt:
```

sudo aptitude install virtualbox-ose

```
See the link in my sig.

---

### Post by lil_bunny on 2008-05-15
[http://www.redlightcenter.com/](http://www.redlightcenter.com/)  saw it on the tv :) , UtherverseSetup.exe is the name.

---

### Post by master5o1 on 2008-05-15
> **Xiong Chiamiov said:**
> If you didn't, you should install virtualbox through apt:
```

sudo aptitude install virtualbox-ose

```
See the link in my sig.
^for the Open Source Edition (OSE)

And if you want USB support in Virtualbox you have to go here and get the Closed Source Edition
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

The .deb file  you download can be installed by double clicking (single if KDE) :)


Then you have to go and `make` the USB work:
[http://ubuntuforums.org/showpost.php?p=4809586&postcount=5](http://ubuntuforums.org/showpost.php?p=4809586&postcount=5)

This is one of my posts in another Virtualbox thread...



Hope it helps.

---

### Post by Xiong Chiamiov on 2008-05-15
Oh, ok, *that* kind of virtual software.  You're talking something close to Option B, but not really.
I wouldn't really expect it to work well in wine, looking at it.  And from their faq:
> 
Do you have a MAC or UNIX version of the software?

No we do not offer a MAC or UNIX version of this software. Because of the lack of demand and extreme expense in creating such versions, we have no plans of providing a MAC or UNIX version anytime in the near future, if ever. We recommend buying a PC for about $500 from Dell to run this software if you really want it.


---

### Post by master5o1 on 2008-05-15
> **lil_bunny said:**
> [http://www.redlightcenter.com/](http://www.redlightcenter.com/)  saw it on the tv :) , UtherverseSetup.exe is the name.


Yup... That only needs Virtualbox if you have a spare copy of Windows to run it through..and even then the 3D graphics that it requires is not gonna let the software run.

---

### Post by lil_bunny on 2008-05-15
ergh im not even gonna bother now , ill just wait until the playstation virtual world comes out lol

thanks for all your help though:)

---

### Post by master5o1 on 2008-05-15
I would have attempted to get it running on my system but it is 450mb and I don't really feel like using up all that bandwidth XD.

I would have if I was over my 10gb limit (I'm at 8gb out of 5gb so don't want to go over the 10gb otherwise +$10 to bill)

---

### Post by master5o1 on 2008-05-15
Rule of thumb: Anything that REQUIRES high specs will likely not work in WINE, and almost definitely not work in VM.

* CPU > 2ghz (solo/dual).
* 3D graphics
* ram > 512mb
Almost definite to not work.

---

