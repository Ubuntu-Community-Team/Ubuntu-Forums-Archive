---
title: "Flash probem"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Tex786 on 2008-10-02
Hi,

I installed Flash with out any problem but after a day when i try to go into full screen in Firefox the browser goes away. I then have to restart.

I am thinking to myself that I need to uninstall flash but I don't know how to do that.

Can someone help me with this?

---

### Post by neurostu on 2008-10-02
I have the same problem... flash crashes my browser about 30% of the time... I haven't gotten around to fixing the problem but its wicked annoying when it happens.

---

### Post by Therion on 2008-10-02
Have either/both of you tried removing Gnash?  

I had the same issue until I uninstalled Gnash player entirely.  

Just use Synpatic, search on "gnash", and remove it.

---

### Post by alienexplorers on 2008-10-02
Go to your .mozilla filode and go in the plugins folder and delete the plugin.

---

### Post by Tex786 on 2008-10-02
> **Therion said:**
> Have either/both of you tried removing Gnash?  

I had the same issue until I uninstalled Gnash player entirely.  

Just use Synpatic, search on "gnash", and remove it.

Could you tell me more about this gnash?

I have only been on ubuntu for only 6 months, so i don't know much.

could you tell me for the sake of knowing how to remove flash? I ran flash in terminal to install it but hae no clue how to remove it.

Thanks

---

### Post by Tex786 on 2008-10-02
> **alienexplorers said:**
> Go to your .mozilla filode and go in the plugins folder and delete the plugin.

I tryed that but did not see where it would allow me to remove flash. I installed it in terminal. Would it be any different? 

When i first pulled up youtube in firefox after my install it did nt give me the average 3 things to pick to enable flash. I had to go to the adobie website and download it.

---

### Post by SunnyRabbiera on 2008-10-02
> **Tex786 said:**
> Could you tell me more about this gnash?

I have only been on ubuntu for only 6 months, so i don't know much.

could you tell me for the sake of knowing how to remove flash? I ran flash in terminal to install it but hae no clue how to remove it.

Thanks

you are better off using the repositories to install packages.
the repositories can be accessed under system> administration> synaptic.
the repositories are like a library of packages, no more need for endless fishing.
now where your terminal installed flash I have no idea but typically its a bad idea to not use packages that are not in the repositories.
If you want to know how this stuff works just ask.

---

### Post by Tex786 on 2008-10-02
> **SunnyRabbiera said:**
> you are better off using the repositories to install packages.
the repositories can be accessed under system> administration> synaptic.
the repositories are like a library of packages, no more need for endless fishing.
now where your terminal installed flash I have no idea but typically its a bad idea to not use packages that are not in the repositories.
If you want to know how this stuff works just ask.

I agree about the Synaptic Package Manager. Its just that I don't know what to click when i am in the manager. There are a lot of things with names that I have no clue what to do with.

when it came to Cairo Dock in the S.P.M. there was no problem but when I try to get something else there seems to be a problem with flash. 

So what do I need to click on to get a flash package in S.P.M.?

Thanks for the help

---

### Post by kansasnoob on 2008-10-02
I'm assuming this is 8.04 Hardy Heron, if not don't do this!

I absolutely agree with using Synaptic to remove gnash. Just go to System > Administration > Synaptic Package Manager. Then type gnash in the search window, you'll see this:

[ATTACH]87037[/ATTACH]

Make sure they're all "unticked".

Also while you're in synaptic make sure you have sun-java6-* installed. Just type sun-java6 in the search window and you'll see several sun-java6-*** packages. I install all EXCEPT sun-java6-doc & sun-java6-source.

Now, just yesterday I tried this with no other changes and it worked (I gave it a fairly rigorous test):

First remove flashplugin-nonfree either using synaptic or:

```
sudo apt-get remove --purge flashplugin-nonfree
```

If you've installed the flashplugin from any other source (tar.gz, .deb, etc.) do this in terminal:

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

NOTE: be patient, it may take a minute to run. You'll know it's done when you see the prompt:

> lance@lance-desktop:~$ 

Of course you're not Lance :)

Now we're going to install the Flash 10 Release Candidate. This is a .deb so it's easy (but it's for Hardy only):

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

When you're all done you'll have to close and reopen Firefox.

BTW, I also recommend installing flashblock and adblock-plus which are both in synaptic.

---

### Post by Therion on 2008-10-02
> **kansasnoob said:**
> I'm assuming this is 8.04 Hardy Heron, if not don't do this!

I absolutely agree with using Synaptic to remove gnash. Just go to System > Administration > Synaptic Package Manager. Then type gnash in the search window, you'll see this:

Make sure they're all "unticked". ...
Thanks for the assist!






/KS Native, btw (Overland Park)

---

### Post by Tex786 on 2008-10-02
> **kansasnoob said:**
> I'm assuming this is 8.04 Hardy Heron, if not don't do this!

I absolutely agree with using Synaptic to remove gnash. Just go to System > Administration > Synaptic Package Manager. Then type gnash in the search window, you'll see this:

[ATTACH]87037[/ATTACH]

Make sure they're all "unticked".

Also while you're in synaptic make sure you have sun-java6-* installed. Just type sun-java6 in the search window and you'll see several sun-java6-*** packages. I install all EXCEPT sun-java6-doc & sun-java6-source.

Now, just yesterday I tried this with no other changes and it worked (I gave it a fairly rigorous test):

First remove flashplugin-nonfree either using synaptic or:

```
sudo apt-get remove --purge flashplugin-nonfree
```

If you've installed the flashplugin from any other source (tar.gz, .deb, etc.) do this in terminal:

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

NOTE: be patient, it may take a minute to run. You'll know it's done when you see the prompt:



Of course you're not Lance :)

Now we're going to install the Flash 10 Release Candidate. This is a .deb so it's easy (but it's for Hardy only):

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

When you're all done you'll have to close and reopen Firefox.

BTW, I also recommend installing flashblock and adblock-plus which are both in synaptic.



Dude its working great now!:D

thanks

---

