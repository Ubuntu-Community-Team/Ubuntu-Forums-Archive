---
title: "RAM requirement  conflict"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2008-05-21
I really am an absolute beginner :KS because I haven't even installed V8.04 yet.   

The reason why?   Well I checked the system requirements in [www.ubuntu.com/products/whatisubuntu/desktopedition](www.ubuntu.com/products/whatisubuntu/desktopedition) and found it said it needed  at least 256MB RAM, so since 256 MB is exactly what my Acer Aspire 3628 notebook has,  I went ahaead and downloaded the 699 MB .iso file, burned a CD from it,  and tried booting from it.  

The opening menu appeared and I used it to check my CD integrity was OK,  and my memory was OK, so then I went on to test V8.04from the CD without installing it.   No joy :confused:  After a couple of minutes' loading my screen went blank,  HD activity ceased,  and all I could do was switch off and reboot.

Tried again,  this time to install.   Again no joy :confused:  After a couple of minutes' loading my screen went blank,  and all activity ceased.   

Finally after another reboot,  I found a text display telling me that the minimum RAM requirement is 384 MB.  Evidently neither the demonstration system nor the installation files could complete their loading into my 256MB RAM.   

Problem explained,  but if [www.ubuntu.com/products/whatisubuntu/desktopedition](www.ubuntu.com/products/whatisubuntu/desktopedition) had stated the minimum RAM requirement correctly, I wouldn't have wasted nearly all night struggling to download that V8.04 .iso file;  I'd either have opted for a different version or I'd have gone out to buy some more RAM.   The published system requirement does seem to be a rather serious understatement.

My Windows XP seems to manage OK with 256MB RAM,  and I'd always understood that Linux makes more efficient use of hardware than Windows,   hence my surprise and confusion here!:confused:

---

### Post by sdennie on 2008-05-21
I believe that you can run Ubuntu with 256M of memory but, it probably causes problems with the Live CD installer.  I would try downloading the alternate installer (it's text based but, works just fine).

---

### Post by housam on 2008-05-21
Ubuntu is exhausting a lot of RAMs. some times it reach to a 600 MB . its better to upgrade your RAM ( 512 - 1GB ).

---

### Post by misfitpierce on 2008-05-21
384MB is what I would have to run Ubuntu from LIVECD. Use Alternate disc to install otherwise but 384MB atleast is good to use to run Ubuntu as well as it is a bit over minimum and would make a bit better with apps etc. Otherwise i'd say try Xubuntu or fluxbox on Ubuntu aka Fluxbuntu for pre-compiled Ubuntu using fluxbox which is very light on resources.

---

### Post by Sleepy-zz-John on 2008-05-31
Many thanks for the helpful replies.  I can now report that I've been able to install it successfully from the text based alternate installer without any increase in my 256MB RAM,  and all seems to be working OK,  though I do concede it would probably benefit from a RAM upgrade,  just like my Win XP would. :)

---

### Post by quinnten83 on 2008-05-31
I'm suprised your winxp even runs with that little RAM.

---

### Post by jordanmthomas on 2008-05-31
> **quinnten83 said:**
> I'm suprised your winxp even runs with that little RAM.
Nah, XP runs fine with 256 MB of RAM, especially if you work on it a little to get rid of unnecessary junk.  Same goes for Linux.  I can get Linux to use far less and be more functional, but when I boot up XP it only uses about 46 MB of RAM.

---

### Post by Sleepy-zz-John on 2008-05-31
It's obviously somewhat debateable what the minimum RAM requirement for actually running V8.04 is,   but for anyone intending to perform the standard graphical installation it's clear that 256MB just won't do.   So I go back to my OP para 6 about the stated system requirements being misleading.   

I maintain there needs to be some reference in [http://www.ubuntu.com/products/whatiwbies](http://www.ubuntu.com/products/whatiwbies) ...desktopedition to the graphical installation's need for a minimum 384MB,  otherwise some unsuspecting newbies like me are going to waste their time and their CDRs burning .iso discs that won't install. 

Then against the text based alternate installer download, it would be useful to have a note explaining how this can work with only 256 MB.

These notes would then permit downloaders to make a more informed choice about what they download. 

I'm very much a newbie;  ought I to post this point elsewhere on the forum,  or is someone who can edit the download pages likely to pick it up from this thread here?

---

### Post by nick_h on 2008-05-31
> ought I to post this point elsewhere on the forum
It might be worth posting in the Installation & Upgrades section, but I'm not too sure how to got about reporting problems with documentation or the website.

You are right that the [Desktop Edition](http://www.ubuntu.com/products/whatisubuntu/desktopedition) page suggests a minimum of 256M whereas [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/) suggests a minimum of 384M.  This could mislead newbies.

---

### Post by avtolle on 2008-05-31
I first freely admit that carefully parsing words, phrases, whatever is integral to my profession. In looking at the second link in nick_h's post *supra*, it is clear that 384 MB is needed to install with the graphical installer, not to run a desktop version. When one scrolls down to the alternate iso discussion, it is clear that a desktop (GUI) version, if one will, will run on 256 MB, and suggests use of the alternate iso for installation, with a *caveat* that low memory systems will not do well (here, interpretation is needed to ascertain "low memory" means <256 MB, IMO). So, I don't find it misleading, but that's just my opinion.

---

### Post by nick_h on 2008-05-31
At the bottom of the page that I linked to it says:
> At least 256 MB of RAM is required to run the desktop install CD.
Doesn't this imply that this is the requirement for the graphical installation?
On the download page I could see why a newbie might not check the box for the alternate desktop install CD.

---

### Post by avtolle on 2008-05-31
I'm not arguing that it should not be stated more clearly; one of the problems I see (now that I've placed myself back, as nearly as I can, to a newbie) is that while the statement you quote is accurate, it does not give a newbie the information that the "Live CD", for lack of a better statement, is not the desktop install CD to which reference is being made. However, when one fully reads the download page, one can ascertain the difference. Again, it should and can be made more clear so folks like the OP don't find themselves in the same predicament. Perhaps we are doing a service for those lurking and reading here, by pointing this out. :-)

---

### Post by nick_h on 2008-05-31
> Perhaps we are doing a service for those lurking and reading here, by pointing this out.
Yes, hopefully we are.

I think just an extra comment next to the check the box for the alternate desktop install CD would help users with low memory.  Something along the lines of "Select this option if you have less than 384M memory".  Not all users will look at the download page.

Does anyone know where to submit such suggestions?  Launchpad perhaps?

---

### Post by cariboo on 2008-05-31
I've got xubuntu installed on a Mac G3 with 256MB of ram, it works but it sure is slower than I'm used to, it seemed to take about 10 minutes to bring up a desktop with the liveCD and it took a while to get it installed. I'm using it for a dhcp server in my shop and it works great for that.

Jim

---

### Post by Sleepy-zz-John on 2008-05-31
Just to add my ***genuine newbie*** take again here,  while [http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/) certainly does point out the minimum 384MB memory reqirement for a graphical installation,  I never saw that page until Avtolle pointed it out on here.    I reached [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and did just glance at the note which says "Check here if you need the alternate desktop CD..." but ignored it because there was nothing there to indicate why it might be better for me to choose text-based installation.  Of course with hindsight I know why,  but at the time I didn't,  so I just steamed ahead on the standard graphical route.  

So I still maintain there's a need to insert a cautionary note somewhere along that standard graphical route to warn newbies like myself that they're either going to need at least 384 MB or they should download the alternate text-based .iso.       It's not obvious otherwise.

---

