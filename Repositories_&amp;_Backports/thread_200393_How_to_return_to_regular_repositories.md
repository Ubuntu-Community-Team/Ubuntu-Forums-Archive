---
title: "How to return to regular repositories?"
date: 2006-06-20
forum: Repositories &amp; Backports
---

### Post by hajk on 2006-06-20
I dabbled briefly into Xgl/Compiz, downloading a bunch of updated packages (like libcairo2, libglitz-glx1) from an alternative repository (not the regular Dapper main, restricted, multiverse, universe stuff). Now that I've decided not to continue with Xgl/Compiz at this time, I removed that alternative repository from my sources.list and did an apt-get update. The affected packages are now shown in Synaptic with status "local or obsolete".

I tried to remove some of them, only to get (in the case of libcairo2) a whole slew of dependent packages needing removal too  -- like the whole ubuntu desktop! That's clearly not my aim...

My question is: how can I revert those packages to the ones in the official Dapper repositories? (I already looked in my /var/cache... place for older packages, couldn't find them there). Any help appreciated.

---

### Post by pellgarlic on 2006-06-20
libcairo2 is part of dapper base install. look here: [http://packages.ubuntu.com/dapper/allpackages.en.txt.gz](http://packages.ubuntu.com/dapper/allpackages.en.txt.gz) for a list of default packages installed with dapper, and filter out those that should be there from those that shouldn't.

---

### Post by hajk on 2006-06-20
Thanks a lot, I was now able to get the version extensions for those packages. That enabled me to downgrade them to the original Dapper packages with apt-get.:grin:

---

### Post by Cable on 2006-06-21
How did you use apt-get to downgrade?  I'm trying to do the same exact thing (remove XGL/Compiz).  What packages did you need to downgrade specifically?  I have no idea how to figure that out...

---

### Post by hajk on 2006-06-21
[QUOTE=Cable]How did you use apt-get to downgrade?  I'm trying to do the same exact thing (remove XGL/Compiz).  What packages did you need to downgrade specifically?  I have no idea how to figure that out...[/QUOTE]

Use Synaptic and use Status to look at the Local and Obsolete packages. A number of them can be removed without dependency effects, like xserver-xgl. Others need to be downgraded: use the package list in
[http://packages.ubuntu.com/dapper/allpackages.en.txt.gz](http://packages.ubuntu.com/dapper/allpackages.en.txt.gz) to write down the correct version numbers, like "0.5.3-0ubuntu2" for libglitz1. Then just use

```
sudo apt-get install libglitz1=0.5.3-0ubuntu2
```

to downgrade, and similar for the other packages that need it. When done, enjoy the feeling of having an unadulterated Dapper installation again...:wink:

---

### Post by Cable on 2006-06-21
When I try to tell it to downgrade a package such as libgl1-mesa it says it also needs to remove ubuntu-desktop and kubuntu-desktop.  I don't want to remove those!  How can I downgrade without removing those?  Also, did you do anything *before* downgrading these packages?  I'm not really sure where to start with this process.  I have backups of the files I edited when installing XGL/Compiz.  Should I restore those first, then downgrade the packages or what?  Tell me the process that you went through to restore your system.

I'm also not sure what pacakges to look for when looking through the local/obsolete packages.  Lots of them have a couple of versions in there, but I know not all of those need to be downgraded.  How do I know which ones to downgrade and which ones not to?

I'm still rather green when it comes to Linux, so I kind of need guidance.  :-P  Thanks for your help!

---

### Post by hajk on 2006-06-21
Hey Cable, just follow the recipe I gave you. One other thing I did, although I don't think it matters, was to remove the offending packages from /var/cache/apt/archive.

The message you got about libgl1-mesa is because you tried to remove this package. You shouldn't do that, you should install the older package in the way I indicated (with the =<version> appended), which then also removes the newer package without complaint. OK?

---

### Post by Cable on 2006-06-21
What about the files I edited during the installation?  Should I restore my backups?  I understand what you're saying about the downgrading.  What I was asking was what packages are the ones that need downgrading?  I really have no idea how to figure out which specific packages I should downgrade.

I used [this]("http://www.compiz.net/viewtopic.php?id=389") guide to install XGL/Compiz.  Do I simply downgrade the specific packages in the apt-get line in that guide?  This line...
```

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

``` 
Or are there more packages than just those that I need to downgrade?  I'm just confused about the specific packages that need downgrading is all.

Also, I just tried typing in the apt-get line for downgrading libgl1-mesa, and it does indeed say that it needs to **remove** kubuntu-desktop, ubuntu-desktop, libgl1-mesa-dri, and x-window-system-core.  It says it will downgrade libgl1-mesa, but remove all four of the above packages.  This is what I typed in the terminal...
```

sudo apt-get install libgl1-mesa=6.4.1-0ubuntu8

``` 
Could you just post the packages (along with versions) that you downgraded to/removed?  That'd make things much easier.

---

### Post by hajk on 2006-06-21
[QUOTE=Cable] 
Could you just post the packages (along with versions) that you downgraded to/removed?  That'd make things much easier.[/QUOTE]

This is what you do: 

1. Edit /etc/apt/sources.list and remove the repositories that you loaded Xgl/Compiz packages from.
2. Open Synaptic and Reload (the same as apt-get update), then use Status to select the Local and Obsolete packages. The packages to be removed or downgraded are in this list -- remove them in Synaptic if you can do that without dependency problems, otherwise write them down including version number.
3. Open the dapper packages list in a terminal or in your browser, and look for these same packages there -- if the version number is different (lower, actually) then you need to downgrade. In that case write down the package name and version number, then proceed from there as in my previous post. Make sure to close Synaptic first.

---

### Post by reztho on 2006-06-25
Easier way...

At first sudo aptitude purge xserver-xgl compiz compiz-gnome gset-compiz

Now we will downgrade everything automatically:
Make a file called /etc/apt/preferences and put this inside:

Package: *
Pin: release o=Ubuntu
Pin-Priority: 1001

Save it and next run: 

sudo aptitude update
sudo aptitude upgrade
or sudo aptitude dist-upgrade

Now everything you have installed from other repositories will be downgraded to the versions of the official Ubuntu repositories you actually have setted up in /etc/apt/sources.list. Beware of this. So to stay updated again, remove the external Xgl/Compiz repositories from /etc/apt/sources.list, remove the /etc/apt/preferences file and sudo aptitude update & sudo aptitude upgrade again. The last thing to do is checking in Synaptic>Status>Local and Obsolete packages if there is something not needed and can be removed. This is a way. 

The other way is adding to /etc/apt/preferences file packages configuration lines as many as needed except the Xgl/Compiz ones and assign them the same pin-priority (1001), so aptitude will only downgrade the Xgl/Compiz packages automatically installed/updated at first without touching any other packages from other unofficial Ubuntu repositories you already have.

Example: I will add some configuration lines so the packages from Sevea's repositories don't be downgraded to the Ubuntu's ones.
- Run in a terminal: apt-cache policy
- I see:
 500 [http://seveas.theplayboymansion.net](http://seveas.theplayboymansion.net) dapper-seveas/all Packages
     release v=6.06,o=Seveas,a=dapper-seveas,l=Seveas,c=all
     origin seveas.theplayboymansion.net

So the way to do the thing is adding to /etc/apt/preferences one of these:
Package: *
Pin: release o=Seveas
Pin-Priority: 1001

or

Package: *
Pin: release a=dapper-seveas
Pin-Priority: 1001

or if there is no release information (this information is obtained from a Release file from the repository and there are repositories which haven't got the file):

Package: *
Pin: origin seveas.theplayboymansion.net
Pin-Priority: 1001

Run apt-cache policy again and you will see the Sevea's repository has the same priority as Ubuntu repositories.

If you want to know more about this: man apt_preferences and the official Debian APT HowTo: [http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

(and excuse me for my english)

---

### Post by mrgnash on 2006-07-12
Reztho, you are a life-saver :)

---

