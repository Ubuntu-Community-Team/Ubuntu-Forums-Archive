---
title: "Ibex update"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by nnjond on 2008-10-30
Hi,

Should I have received an Ibex notification yet? -And will it appear in add or remove?

thanks

---

### Post by hellion0 on 2008-10-30
It won't be in Add/Remove, it'll be in Update Manager.

If you have your Software Sources (that's in the System menu, I believe) set to show "Normal Releases", then when you open Update Manager, a notification will appear in it telling you something along the lines of "New distribution version 8.10 is available", assuming 8.10's been released.

---

### Post by Piraja on 2008-10-30
The final release is not out yet, I think. Will be some time today. In a few hours or any time soon, you will be able to upgrade from Hardy (I presume you're waiting to do that?) by doing

[INDENT]Alt+F2
update-manager -d
[/INDENT]
I'm not sure if there will be an automated notification of the upgrade. Could be.

---

### Post by taavi on 2008-10-30
Right now it shows for me:

Is it ready or RC?

---

### Post by hellion0 on 2008-10-30
I just checked on my laptop, and it doesn't show that Intrepid's ready to be upgraded to yet. The RC's been out, but not the proper release that I know of.

---

### Post by bumanie on 2008-10-30
The Canonical site says 8.10 is available now.

---

### Post by alwez_loner on 2008-10-30
It seems to still coming soon... Though i would really advice people to be patient... That's why i'm going to upgrade on Sunday.

---

### Post by kernelhaxor on 2008-10-30
> **taavi said:**
> Right now it shows for me:

Is it ready or RC?

I think that might be the final version!  May be they haven't released on the web yet and as we know it will be out very soon.

---

### Post by Laibcoms on 2008-10-30
> **bumanie said:**
> The Canonical site says 8.10 is available now.


Where did you read that?  It still says "Coming Soon" regardless if I force-refresh the main site as well as the download site.  Any direct link to your source?

---

### Post by bumanie on 2008-10-30
I made an error Very sorry to everyone.

---

### Post by hyper_ch on 2008-10-30
I'd also recommend to download the alternate install cd through bittorrent once it's released. You can upgrade using that one by enabling the cd again in the sources.

That way you (a) will faster download and (b) take pressure off the servers.

---

### Post by justchange on 2008-10-30
Okay, mate, I'm one of those "Absolute Beginners" this forum is named for... what the heck are you talking about?
> I'd also recommend to download the alternate install cd through bittorrent once it's released. You can upgrade using that one by enabling the cd again in the sources.

I can guess that using the Update Manager will provide a painless upgrade, but add to the server load, right?
However, it's not clear that upgrading through a CD will be an equally smooth path. And, why the "alternate install" CD? If that requires any knowledge of command-line work, it seems to me to fall outside the "absolute beginner" realm... without guidance. Am I missing anything?
Plus, it isn't clear to me what you mean by > enabling the cd again in the sources. Can you help with that?
Thanks.

---

### Post by hyper_ch on 2008-10-30
it is equally smooth.. packages are the same and you start the update manager as you would for an "online" upgrade. ONly that you will also have added the CD as repository and then it will not download the packages from the net but from the cd.

You can enable it in synaptic again.

---

### Post by Twilight in Zero on 2008-10-30
You don't actually need to use the command line. Just download the Alt CD, burn it, and insert it while still in Ubuntu. I'm not sure about the process from here until the actual upgrade, but the CD will become a package source in the Software Sources window.

Then you can use update-manager, and it will use the packages from the CD.

Also, I'd imagine you could use the desktop CD too.

EDIT: I was totally wrong. Inserting the Alt CD while in Ubuntu will present a dialog that will allow you to upgrade from the CD. You can't use the desktop CD.

---

### Post by Lerxst51 on 2008-10-30
Just a heads up, 8.10 has been released, it just hasn't been shown on the Ubuntu website. If you look in the releases site, the .isos are not RC anymore:

[http://releases.ubuntu.com/8.10/](http://releases.ubuntu.com/8.10/)

---

