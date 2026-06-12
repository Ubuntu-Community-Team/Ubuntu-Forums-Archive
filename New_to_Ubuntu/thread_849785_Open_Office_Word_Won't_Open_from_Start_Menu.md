---
title: "Open Office Word Won't Open from Start Menu"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by aqalicious on 2008-07-04
For a while now I've only been able to get into Open Office via the command line; if I try to open it through the start menu I get the following message:
[B]
Failed to execute child process "/usr/share/icons/hicolor/48x48/apps/ax-applet.png" (Permission denied)[/B]

It is a relatively minor problem - I can still use the program after all - but I'd like to fix it, or at least understand what is wrong...:confused:

I tried following the file path in Nautilus, thinking I could change the permissions, but it tells me I can't do so because "you're not the owner." 

I searched around the forums but couldn't find anything directly relevant to this question.  At one point I tried reinstalling Open Office, and also upgrading from "Feisty Fawn" to "Hardy Heron," but it didn't fix this problem.

Could anyone help me understand this?

(BTW I think the problem likely originated when I was following some of the exercises in "**Ubuntu for Non-Geeks, 2nd Edition**," but it was a while before I discovered the problem and now I'm not even sure what caused it, or even if it was actually something I changed.)

Arthur

---

### Post by coolaj86 on 2008-07-04
In synaptic (in the Administration menu under System) you can 'purge' your OpenOffice.org installation and then reinstall it. Some customized settings may be lost if you choose to purge rather than uninstall.

It sounds that you may have a permissions problem from the message it gave. If so, the simpler fix may be:
sudo chmod a+r /usr/share/icons/hicolor/48x48/apps/ax-applet.png

---

### Post by aqalicious on 2008-07-04
> **coolaj86 said:**
> In synaptic (in the Administration menu under System) you can 'purge' your OpenOffice.org installation and then reinstall it. Some customized settings may be lost if you choose to purge rather than uninstall.

It sounds that you may have a permissions problem from the message it gave. If so, the simpler fix may be:
sudo chmod a+r /usr/share/icons/hicolor/48x48/apps/ax-applet.png

Thanks for your reply.  

I tried entering the command you gave, but that didn't fix the problem.

Then I tried going into Synaptic and "marking for complete removal" (is that what you mean by "purging?") Open Office - writer, then reinstalling it.  That didn't change anything either.  

Did you mean for me to completely remove every "Open Office" file and then reinstall them all, or just the "writer" ones?

All the other Open Office programs (Gnucash, database etc.) open properly from the start menu - it's only the word processor that won't open.

cheers,
Arthur

---

### Post by coolaj86 on 2008-07-04
did you actually apply the 'complete removal' option?

Try this too:
Right-click Edit Menus on the Applications Menu
Navigate to Office
Right-click Properties on the OpenOffice.org Write icon and make sure that it has the right image (click on it and navigate to it if you can) and that it executes the command "ooffice -writer %U"

---

### Post by ChameleonDave on 2008-07-04
Please, it is called **Writer**, not **Word**.

---

### Post by aqalicious on 2008-07-04
> **coolaj86 said:**
> Try this too:
Right-click Edit Menus on the Applications Menu
Navigate to Office
Right-click Properties on the OpenOffice.org Write icon and make sure that it has the right image (click on it and navigate to it if you can) and that it executes the command "ooffice -writer %U"

Hey, that fixed the problem!  Thanks so much for your help.  :)

The 'command' that was in the field you directed me to was: "/usr/share/icons/hicolor/48x48/apps/ax-applet.png"

I'm not sure how it got there, but I'm sure my non-geekiness had a *lot* to do with it...:(

Thanks again.  :)

cheers,
Arthur

---

### Post by aqalicious on 2008-07-04
> **ChameleonDave said:**
> Please, it is called **Writer**, not **Word**.

Sorry. Proper nomenclature noted.

cheers,
Arthur

---

### Post by coolaj86 on 2008-07-05
@ChameleonDave

It's called Word Processor in the Ubuntu Menu, not Writer
OpenOffice.org **Word** Processor

So our friend here wasn't that far off the mark.

@aqalicious

You're welcome

:-D

---

### Post by ChameleonDave on 2008-07-05
> **coolaj86 said:**
> @ChameleonDave

It's called Word Processor in the Ubuntu Menu, not Writer
OpenOffice.org **Word** Processor

So our friend here wasn't that far off the mark.

@aqalicious

You're welcome

:-D

It's not a matter of how "far off the mark" he was.

It's called OpenOffice.org Writer; and if the wrong words are used in forum thread titles, they are less useful for people searching for information later.

---

