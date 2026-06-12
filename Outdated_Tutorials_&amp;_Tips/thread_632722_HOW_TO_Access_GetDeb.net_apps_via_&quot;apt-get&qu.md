---
title: "HOW TO: Access GetDeb.net apps via &quot;apt-get&quot; &amp; Synaptic"
date: 2007-12-05
forum: Outdated Tutorials &amp; Tips
---

### Post by hackle577 on 2007-12-05
[SIZE="4"]UPDATE: This apparently does *not* work in Hardy. If you somehow get it to function, PM me. Thanks![/SIZE]

[COLOR="Red"]NOTE: The GetDeb does not follow packaging guidelines quite as strictly as the official repos do, meaning that these applications may be a little less stable than apps from official Ubuntu sources. On the other hand, you will be able to get useful packages before they would regularly become available in Ubuntu. It's probably wise not to do this unless you know precisely what it is you are doing.[/COLOR]

This guide will allow you to install and automatically update [GetDeb.net]("http://www.getdeb.net/") applications through "apt-get" and Synaptic Package Manager. The process was converted to a regular Ubuntu guide from [Picpak's version for Xubuntu]("http://xubuntu.wordpress.com/2007/08/05/howto-access-getdebnet-packages-through-apt-getsynaptic/").

[SIZE="4"]1.[/SIZE] Open your /etc/apt/sources.list in a text editor.

```
gksudo gedit /etc/apt/sources.list
```

[SIZE="4"]2.[/SIZE] At the end of the file, add these lines.

```
# GetDeb.net Repository
deb http://ubuntu.org.ua/ getdeb/
```

[SIZE="4"]3.[/SIZE] Save the file and close it.

[SIZE="4"]4.[/SIZE] Now refresh your software sources.

```
sudo apt-get update
```

[SIZE="4"]5.[/SIZE] Now you should be able to get updates for programs from GetDeb, and install GetDeb programs from within Synaptic. Ubuntu will warn you that packages installed or updated using the GetDeb repo cannot be authenticated. If you're sure you want to install them anyway, just click OK.

-------------------

[SIZE="4"]To Undo:[/SIZE] Simply open up your sources.list again, remove the two GetDeb lines you inserted in Step 2, and then run Step 4 again. However, this only removes GetDeb from your list of software repos, it will not undo updates to your programs. 

[COLOR="Red"]Support for undoing changes to programs is NOT offered by the author of this guide.[/COLOR]

(Tested on Ubuntu 7.10 64-bit.)

---

### Post by Bossieman on 2007-12-24
Thanks! Worked perfectly. :guitar:

---

### Post by smartboyathome on 2007-12-24
I remember seeing this EXACT same guide on a blog on Google.

---

### Post by picpak on 2007-12-24
> **smartboyathome said:**
> I remember seeing this EXACT same guide on a blog on Google.

I know, huh? I think it was...[mine!](http://xubuntu.wordpress.com/2007/08/05/howto-access-getdebnet-packages-through-apt-getsynaptic/)

I don't mind, though, because he states in his post that it's from the blog and changed for Gnome.

---

### Post by foureight84 on 2007-12-25
lol yea i found that on google a while back [http://xubuntu.wordpress.com/2007/08/05/howto-access-getdebnet-packages-through-apt-getsynaptic/](http://xubuntu.wordpress.com/2007/08/05/howto-access-getdebnet-packages-through-apt-getsynaptic/)

---

### Post by hackle577 on 2007-12-25
Yeah, sorry if it seems like I stole it. It wasn't in the forums though, and I couldn't find a specific author's name to give credit to.

I've added your name to the OP, picpak.

---

### Post by picpak on 2007-12-25
> **hackle577 said:**
> Yeah, sorry if it seems like I stole it. It wasn't in the forums though, and I couldn't find a specific author's name to give credit to.

I've added your name to the OP, picpak.

Oh, I don't mind -- let the guide be spread around as far as an audience as possible -- but it's not as if you took complete responsibility for the guide. Like I said, the original was linked to in the post.

Merry Christmas btw! :guitar:

---

### Post by kahlil88 on 2008-02-10
For the sake of curiosity, how do you add the GetDeb repo from within Synaptic?

---

### Post by hackle577 on 2008-02-10
> **kahlil88 said:**
> For the sake of curiosity, how do you add the GetDeb repo from within Synaptic?

[LIST=1]
[*]Open Synpatic.
[*]Click Settings > Repositories.
[*]Select the Third-Party Software tab.
[*]Click Add.
[*]Enter "deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/" into the box and click Add Source.
[*]Click Close.
[*]Click Reload.
[/LIST]

Then to update you'd want to run System > Administration > Update Manager.

---

### Post by exploder on 2008-02-10
Thanks for sharing this!

---

### Post by nonly1n on 2008-02-25
> **hackle577 said:**
> [LIST=1]
[*]Open Synpatic.
[*]Click Settings > Repositories.
[*]Select the Third-Party Software tab.
[*]Click Add.
[*]Enter "deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/" into the box and click Add Source.
[*]Click Close.
[*]Click Reload.
[/LIST]

Then to update you'd want to run System > Administration > Update Manager.

was just wondering when it comes to a time for upgrading wont this somehow get in the way...

---

### Post by Sahtor on 2008-02-25
ubuntu.org.ua is reported as attack site by Firefox/mozilla/google??

---

### Post by hackle577 on 2008-02-25
> **nonly1n said:**
> was just wondering when it comes to a time for upgrading wont this somehow get in the way...

Honestly, I don't know. I always do a fresh install when a new release comes out, so I have never actually upgraded *per se*.

---

### Post by kahlil88 on 2008-05-18
> **hackle577 said:**
> [SIZE="4"]UPDATE: This apparently does *not* work in Hardy. If you somehow get it to function, PM me. Thanks![/SIZE]
The problem is not with Hardy, [http://ubuntu.org.ua/getdeb](http://ubuntu.org.ua/getdeb) is an empty directory. Does anyone know of a working source?

---

### Post by uqbar on 2008-05-26
The problem is: why is it working in Gutsy and not in Hardy?
Something has changed in the way the URL gets computed. The point is: what?

---

### Post by uqbar on 2008-05-26
The problem is: why is it working in Gutsy and not in Hardy?
Something has changed in the way the URL gets computed. The point is: what?

---

### Post by frediE on 2008-06-05
just wondering if anyone has figured out getdeb.net in Hardy?  ohhh how i miss it.

---

### Post by frediE on 2008-07-09
New versions of wonderful software and i am missing them. ohhh poor us.  :(

---

### Post by Martje_001 on 2008-07-09
> **uqbar said:**
> The problem is: why is it working in Gutsy and not in Hardy?
Something has changed in the way the URL gets computed. The point is: what?
I you want to find out, go to synaptic and select a package from getdeb.net. Then go to File --> Create script to download packages. Save it, and post it here.

---

### Post by blonder on 2008-07-09
getdeb via apt-get for hardy would be so great ;)

---

### Post by frediE on 2008-07-09
Looks like it is broke in Gutsy also... i tried the locations i know of...
 deb [http://mirrors.dotsrc.org/](http://mirrors.dotsrc.org/) getdeb/
 deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/


i was on a live cd (don't have any Gutsy installs left) but i don't think that should matter.

404 not found on the Packages.gz

---

### Post by frediE on 2008-07-09
i contacted getdeb... not sure if it will help.  maybe they are working on a not-official official repo.  :-)

---

### Post by RATM_Owns on 2008-07-09
> **Martje_001 said:**
> I you want to find out, go to synaptic and select a package from getdeb.net. Then go to File --> Create script to download packages. Save it, and post it here.
For me, this is the contents.
```
#!/bin/bash
```
Completely useless.

---

### Post by frediE on 2008-07-24
I spoke with one of the getdeb maintainers and he mentioned they were "not providing any repository for our packages."

I let him know how great it would be to have one however we do appreciate the work they are currently doing.

soooo.... it sounds like we need someone with a site to setup a repo.  any super admins out there?

---

### Post by Martje_001 on 2008-07-25
> **frediE said:**
> I spoke with one of the getdeb maintainers and he mentioned they were "not providing any repository for our packages."

I let him know how great it would be to have one however we do appreciate the work they are currently doing.

soooo.... it sounds like we need someone with a site to setup a repo.  any super admins out there?
I could create a system which downloads the packages and put them online.. the only problem is; I don't have a fast server with much bandwidth.. Anyone?

---

### Post by Vadi on 2008-07-27
The point of *not* having a repository for getdeb.net is because *every* application that they do will get updated with yours.

You might as well enable -proposed and -backports for the same effect :)

---

### Post by frediE on 2008-09-04
look what i found today!!!!  thanks tombuntu!
deb mirror://www.getdeb.net/playdeb-mirror/hardy/// hardy/


the playdeb mirror looks like it is just for games but is there anything we can extract for the rest of our fabulous getdeb software?

---

### Post by Vadi on 2008-09-04
Sorry, but that would be a bad idea and make Ubuntu developers unhappy too. What you can do is go to System - Administration - Software Sources - Updates, and enable "hardy-backports". That'll help you get more updated software.

---

### Post by frediE on 2008-09-19
I understand about the backports and how they work... but Getdeb adds additional packages that are not in the standard repos.  They have a nice collection of software and now..........  IT'S ALIVE!!!   

try to re-enable the "deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/" it appears to be working now.  :-)

YIPPEE!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Vadi on 2008-09-19
Backports are the official Ubuntu thing, while getdeb website is the latest software.

If your computer breaks from the getdeb repository, don't blame it on getdeb, because the repository is going against getdeb's permission to make the mirror.

---

### Post by frediE on 2008-09-19
I agree 100% and it should be noted for anyone else also.  Be very careful when adding additional repo's.

---

### Post by Arthur Millar on 2008-11-08
I am getting a authentication error and cant update anything from get deb
Hardy 8.04
cant install libpoppler_glib3 on hardy missing gtk2.0-0 but it is installed?

---

### Post by Vadi on 2008-11-08
Get applications from [http://www.getdeb.net/](http://www.getdeb.net/) directly. It has a search bar top-right.

---

