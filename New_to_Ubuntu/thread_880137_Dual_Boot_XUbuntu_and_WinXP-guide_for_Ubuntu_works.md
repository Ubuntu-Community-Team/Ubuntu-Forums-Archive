---
title: "Dual Boot XUbuntu and WinXP-guide for Ubuntu works?"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Bart_D on 2008-08-04
Well, I was attempting to install Ubuntu on a system already having a stable install of Win XP.  After hunting through for this some months ago, I had found a website that went through the process BUT I couldn't find that same site this time.  From my rather PAINFUL past experiences at dual booting, I knew it would be very....well, uncomfortable.  BUT THEN, I found this amazing(atleast it appears that way) set of instructions.  What a tremendous help this would have been some months ago.....

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

**QUESTIONS: **
1.  Anyways, I will be hoping to install **[COLOR="SlateGray"]X[/COLOR]****[COLOR="Sienna"]Ubuntu[/COLOR]** and I was wondering if this guide would work **[COLOR="Red"]IDENTICALLY[/COLOR]** for **[COLOR="SlateGray"]X[/COLOR]****[COLOR="Sienna"]Ubuntu[/COLOR]** as well?  If not, what changes would I need to make to adapt the guide for **[COLOR="SlateGray"]X[/COLOR]****[COLOR="Sienna"]Ubuntu[/COLOR]**?

2.  The system currently has 2 partitions...I think that both are NTFS.  One has WinXP, the other is what I would like to use for **[COLOR="SlateGray"]X[/COLOR]****[COLOR="Sienna"]Ubuntu[/COLOR]**.  Would I need to format the second partition PRIOR to attempting to install **[COLOR="SlateGray"]X[/COLOR]****[COLOR="Sienna"]Ubuntu[/COLOR]**?  If so, what format would I require to use for the partition and would it need to be primary?

---

### Post by Paqman on 2008-08-04
> **Bart_D said:**
> 
**QUESTIONS: **
1.  Anyways, I will be hoping to install **[COLOR="SlateGray"]X[/COLOR]****[COLOR="Sienna"]Ubuntu[/COLOR]** and I was wondering if this guide would work **[COLOR="Red"]IDENTICALLY[/COLOR]** for **[COLOR="SlateGray"]X[/COLOR]****[COLOR="Sienna"]Ubuntu[/COLOR]** as well?  If not, what changes would I need to make to adapt the guide for **[COLOR="SlateGray"]X[/COLOR]****[COLOR="Sienna"]Ubuntu[/COLOR]**?


Xubuntu is the same system as Ubuntu, just with a lightweight desktop environment. So almost everything is the same. Certainly installation requires the same process. 

> 
2.  The system currently has 2 partitions...I think that both are NTFS.  One has WinXP, the other is what I would like to use for **[COLOR="SlateGray"]X[/COLOR]****[COLOR="Sienna"]Ubuntu[/COLOR]**.  Would I need to format the second partition PRIOR to attempting to install **[COLOR="SlateGray"]X[/COLOR]****[COLOR="Sienna"]Ubuntu[/COLOR]**?  If so, what format would I require to use for the partition and would it need to be primary?

First of all, partitioning isn't compulsory any more. You can now use Wubi to install Ubuntu onto one of your NTFS partitions.

If you do want to partition, you can allow the installer to do it for you. If you delete one the partitions using the LiveCD then pick "Use largest continuous free space" during the installation process it'll be automatic.

If you really want to do it manually, you'd create a large Ext3 partition for the system, plus another small partition (same size as your RAM) formatted as swap.

---

### Post by Bart_D on 2008-08-04
Hey, thanks for the reply.  I really appreciate the help.

> **Paqman said:**
> ...partitioning isn't compulsory any more. You can now use Wubi to install Ubuntu onto one of your NTFS partitions.

If you do want to partition, you can allow the installer to do it for you. If you delete one the partitions using the LiveCD then pick "Use largest continuous free space" during the installation process it'll be automatic.

If you really want to do it manually, you'd create a large Ext3 partition for the system, plus another small partition (same size as your RAM) formatted as swap.

I'd rather not do it manually or using WUBI...my recollection of WUBI was installing Ubuntu INSIDE Windows, allowing the user to run it like any other Windows program.  I'd highly prefer to use the LIVE-CD only.  When I get to this screen(LIVE-CD),

[http://www.psychocats.net/ubuntu/images/installinghardyplus10.png](http://www.psychocats.net/ubuntu/images/installinghardyplus10.png)

I would prefer to select "Guided", thereby leaving the WinXP partition the same size that it is right now, BUT when I get to the above screen, [COLOR="DarkGreen"]would there by some way for me to select the **spare** NTFS partition(from the LIVE CD) for the Ubuntu install[/COLOR] **[COLOR="Red"]or[/COLOR]** [COLOR="Navy"]would the WinXP partition be the one that gets automatically selected for resizing in the manner shown in the picture[/COLOR]?  If the latter is the case, would WUBI be my only option?

---

### Post by Stan_1936 on 2008-08-04
You should just use a separate physical hard drive.  That way you can just swap in-and-out between Ubuntu and Windows.  That's what I have done.  This way you don't have to worry about partitions and primary/slave issues and, as you are finding out, it can be quite tricky.  I probably had worse luck than you but I managed to get a working system with an installation over the entire drive.

Infact if you do a solo install(use entire hard disk), you can even install an encrypted version of Ubuntu.  That, again, is what I've done.

---

### Post by Paqman on 2008-08-04
> **Bart_D said:**
> 
I'd rather not do it manually or using WUBI...my recollection of WUBI was installing Ubuntu INSIDE Windows, allowing the user to run it like any other Windows program.  


Only the Wubi installer/uninstaller itself runs within Windows. Once it has installed Ubuntu, you boot up into pure Ubuntu, just like any other install.

If you're not happy with that, then fair enough.

> 
when I get to the above screen, [COLOR="DarkGreen"]would there by some way for me to select the **spare** NTFS partition(from the LIVE CD)

Off the top of my head, I don't know. It may just pick the first drive.

If you partition manually, you can definitely specify exactly where to install Ubuntu. It's not as hard as you might think, either.

---

### Post by zvacet on 2008-08-05
@ **Bart_D**

>  Would I need to format the second partition PRIOR to attempting to install XUbuntu? If so, what format would I require to use for the partition and would it need to be primary?

I will recommend you to go with manual way following link you posted.It is not hard as it looks.Doind things that way give answer to your questions and some additionall things.Supose you choose manual way

1.you will delete NTFS partition wich you don´t need and on that free space you will install Ubuntu.Default format is ext3.Ubuntu can be installed on primary and extended partition.Some people install it on extended partition because you can have only 4 primary partitions.I don´t think that is your case so install it on primary.

2.Using manual way of install you can make separate home partition which you will find usefull later.Bacisly this is how your Ubuntu should look ( if you have enough free space)

1. root = ~10GB                             mountpoint /
2.swap = 2xram ( but if you have 2or more ram 2GB for swap is more then enough)
3. home = rest of your free space          mountpoint /home

Put swap on the end of disc.

---

### Post by kansasnoob on 2008-08-05
Psychocats is great, I use a lot of info from that site ........ definitely one of the best, but for a total noob, if you've done no partitioning at all, this just works:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=1)

Although I hate some of the recent changes to their Vista dual boot guides:(

---

### Post by Bart_D on 2008-08-05
Thanks for the suggestions.  Whew, that's a lot of information.  I am almost tempted to buy a new hard drive and swap in and out to avoid further complications.  I am(well, I was...several months ago) very comfortable with creating partitions and installing multiple versions of Ubuntu(Ubuntu/XUbuntu) on the same hard drive.  I used partition magic and had no problems with that at all.  The problem is that, back then, I had an empty disk to "play" with.i.e. I didn't care about any mistakes that I made.....I would just reformat the disk and start over.  Now, I don't want to lose the WinXP installation that I have on one of the disk's partitions so things become complicated.....I don't really have any room for error.

After having gone through the above replies, I am thinking of just deleting that spare partition, choosing the 3rd option(largest available space) and hoping that things go smoothly from there.i.e. it automatically installes Ubuntu in that free space, like Paqman said in the 2nd post of this thread.  I really hope that this option works because I would really like to avoid buying a hard drive.

---

