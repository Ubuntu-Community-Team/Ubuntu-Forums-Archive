---
title: "[SOLVED] Hardy Not Updating"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by melrom on 2008-06-09
Something funky is going on with updates on my system. If I use the Update Manager and click check, it says that it's Downloading 21 of 21, but then when it's reading the state information, it just says my system is up-to-date. But I haven't gotten the new kernel update and my Firefox is still the Beta [I could do this manually, yes]. 

Popping 
```

apt-get update; apt-get upgrade

```

only helped to find five updates that were all basically to AWN, and it was able to download and update those, but these other 21 that it's finding but not actually letting me see are aggravating me, and I can't figure out what's going on.

Any help is much appreciated.

---

### Post by _sphinx_ on 2008-06-09
You can try the following command:
```
sudo apt-get dist-upgrade
```

---

### Post by cdtech on 2008-06-09
I would try to clean up the local apt repository of your retrieved packages with "apt-get clean" and then resync the package index with "apt-get update" and see if that gets you going. If not we can try something else here.

Hope that helps........

---

### Post by melrom on 2008-06-09
unfortunately, that did not help. :(

---

### Post by sam_delta on 2008-06-09
which server are you downloading from??? try changing to the main server, go into synaptic then settings>repositories, then download from: select 'main server'
check if that helps
just wondering, your using 32 or 64 bit ubuntu?

sam

---

### Post by cdtech on 2008-06-09
Did you check your System > Administration > Software Sources? And have a look in your System > Administration > Synaptic Package Manager; clear out your "not installed (residual config)", just high lite one and hit ctrl +a for all, then right click and select remove. I found that I've had issues with the "not installed (residual config)" keeping the system from updating.

---

### Post by melrom on 2008-06-09
hm, i did that, but it still won't update. =(

---

### Post by cdtech on 2008-06-09
Did what? Change the location of the sources? Delete the residuals?

---

### Post by melrom on 2008-06-09
Deleted the residuals.

---

### Post by melrom on 2008-06-09
> **sam_delta said:**
> which server are you downloading from??? try changing to the main server, go into synaptic then settings>repositories, then download from: select 'main server'
check if that helps
just wondering, your using 32 or 64 bit ubuntu?

sam


Main Server is already selected.

32-bit.

---

### Post by cdtech on 2008-06-09
I just re read your post. You want to see the kernel upgrade then using the GUI use the following command:

```
gksu "update-manager -c"
```

&#8220;-c&#8221; switch tells it to look for upgrades for all.

---

### Post by melrom on 2008-06-09
> **cdtech said:**
> I just re read your post. You want to see the kernel upgrade then using the GUI use the following command:

```
gksu update-manager -c
```

“-c” switch tells it to look for upgrades for all.


Sorry, this says -c is not an option?

---

### Post by cdtech on 2008-06-09
Just fixed the quotes, sorry for that...

---

### Post by melrom on 2008-06-09
hm, nothing happened [other than the Update Manager popping up]. I have to go out now. I will check back in later. Thanks for all the help that you did give!

---

### Post by cdtech on 2008-06-09
Then the updates aren't listed in the repositories yet. If you want them you'll have to install the deb package.

Sorry.....

---

### Post by sam_delta on 2008-06-09
> **cdtech said:**
> Then the updates aren't listed in the repositories yet. If you want them you'll have to install the deb package.

Sorry.....
yes they are, ive updated every day for the last few days, including 2 kernel updates (*-17 and *-18 ), also, i got firefox rc1 today, all from main server

sam

---

### Post by melrom on 2008-06-09
exactly. i know i *should* be getting them, but i'm not.

---

### Post by melrom on 2008-06-09
any thoughts? =\

---

### Post by cdtech on 2008-06-09
I just did an update for the Firefox. Here is my sources.list so you can compare. I can't really think of anything else other than old cache, which you said you cleared through synaptic package manager.

Hope this helps.....

```
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe main restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main universe multiverse restricted

deb http://us.archive.ubuntu.com/ubuntu/ hardy-security universe main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-security multiverse

deb http://apt.wicd.net hardy extras
```

---

### Post by sam_delta on 2008-06-10
hey i just came up with something
open synaptic, then click on settings>repositories, then in the window that opens, select the "updates" tab, make sure that all options are properly selected (important updates, recommended updates and pre-released updates )

sam

---

### Post by melrom on 2008-06-10
> **sam_delta said:**
> hey i just came up with something
open synaptic, then click on settings>repositories, then in the window that opens, select the "updates" tab, make sure that all options are properly selected (important updates, recommended updates and pre-released updates )

sam

thanks. they are. i checked. :(

---

### Post by SteveHillier on 2008-06-10
Can I tag along please.

I am having the same problem as Melrom.
I get popup saying updates available but when I go to install I get the update manager window greyed out and nothing happens.

I have followed all the commands listed in this post to no avail.

What I also get when running in terminal is a message saying "Cannot resolve host Hardy".

Now this might be the issue.  This machine was first loaded with Feisty.  I upgraded to Gutsy.  No problems.  On the upgrade to Hardy I decided I should change the host name and went through that process.

The other thing I did after the upgrade was to add another user as a domain user for my Win 2003 domain.  I have no problems running either user so I cannot see that as contributory.

I know I could start all over again with a clean install but I don't really want to.

---

### Post by melrom on 2008-06-10
> **SteveHillier said:**
> Can I tag along please.

I am having the same problem as Melrom.
I get popup saying updates available but when I go to install I get the update manager window greyed out and nothing happens.

I have followed all the commands listed in this post to no avail.

What I also get when running in terminal is a message saying "Cannot resolve host Hardy".

Now this might be the issue.  This machine was first loaded with Feisty.  I upgraded to Gutsy.  No problems.  On the upgrade to Hardy I decided I should change the host name and went through that process.

The other thing I did after the upgrade was to add another user as a domain user for my Win 2003 domain.  I have no problems running either user so I cannot see that as contributory.

I know I could start all over again with a clean install but I don't really want to.


Steve-

Try out this thread for the "cannot resolve host" problem:

[http://ubuntuforums.org/showthread.php?t=820621](http://ubuntuforums.org/showthread.php?t=820621)

I know the initial problem is not the same, but the fix should work for you.

---

### Post by SteveHillier on 2008-06-10
Thanks to melrom for pointing me in the direction to fix the host name issue.

Now onto the rest.......

BFN
Steve

---

### Post by SteveHillier on 2008-06-10
> **melrom said:**
> Try out this thread for the "cannot resolve host" problem:

[http://ubuntuforums.org/showthread.php?t=820621](http://ubuntuforums.org/showthread.php?t=820621)

I know the initial problem is not the same, but the fix should work for you.

melrom, you are a star.  Fixing the host name has now allowed my updates to perform properly.

As I had also run through the other commands in this thread I cannot be certain that fixing the host name is the sole factor but it is certainly the one that when I fixed this everything else worked.

Thank you for your help.

---

### Post by melrom on 2008-06-10
No problem! :) I'm glad everything is working for you again!

---

### Post by sam_delta on 2008-06-10
hey, just wondering, are you behind a proxy server??
sam

---

### Post by melrom on 2008-06-12
> **sam_delta said:**
> hey, just wondering, are you behind a proxy server??
sam

no.

i still can't solve my issue. i'm all out of ideas. looks like i might have to reinstall Hardy. ](*,)

---

### Post by ibuclaw on 2008-06-12
[Check out this site Melrom.]("https://launchpad.net/ubuntu/+archivemirrors") Not all repositories are up-to-date, some are a few days, a week or a fortnight behind.

Use the site to check the status of the mirror that you are tied to (as found in your **/etc/apt/sources.list** file).

If your's just so happens to be one of the ones that are behind, switch to an up-to-date one (I think just plain **[http://archive.ubuntu.com](http://archive.ubuntu.com)** is the "Main" main mirror. It's situated in the Isle of Man, so it may not be a quick download for you).

Other than that, make sure that you haven't got any apt-pinnings preventing you from downloading any updates.
```

if [ -e /etc/apt/preferences ]; then cat /etc/apt/preferences; fi

if [ -e /var/lib/synaptic/preferences ]; then cat /var/lib/synaptic/preferences; fi

```
Ideally, there shouldn't be any output from the above two lines if you wish to have the most up to date system, but have a look for a line that says "**Package: ***", if a string of output is echo'd.

[EDIT]
Also, give aptitude a shot at your problem. It gives you a nice ncurses layout and you can see what is doing what.
Just type in ```
aptitude
```in the terminal and the app will start.

Check whether or not there are any upgradable packages, and Press "**G**" to go to the Pending Menu, if there are any outstanding package adjustments to be upgraded/removed/etc.

Regards
Iain

---

### Post by melrom on 2008-06-16
Well Iain, as it turns out, running those two lines of code gave no output and aptitude didn't have any updates for me either. =O

If I use the website you give me, do I have to go and get every single thing and update it? I don't even know what needs to be updated...

What should I do??

--> There's also only about a gig left of space on my Ubuntu partition. Could there be something going on with that??

---

### Post by avtolle on 2008-06-16
Changing to the main server in Software Sources, then reloading the sources, won't require you to go to every single thing.... It will merely change the repositories from the site you currently use to the main mirror; update manager should take care of the rest.

Of somewhat more import is the size of the partition. While approximately a gig should not result in a problem, I don't know just what you are going to end up with insofar as size of total updates is concerned. How big is the Ubuntu partition?

---

### Post by melrom on 2008-06-16
Guys! Checked again and got 260 new updates! Not sure what happened! BUT SO GLAD IT'S RESOLVED!!

---

