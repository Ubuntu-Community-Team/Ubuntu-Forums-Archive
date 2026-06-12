---
title: "How to uninstall unwanted/unneccessary packages?"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by Houmie on 2012-06-04
It is often said that Windows has an expiry date like a bottle of milk and this is due the mess it happens when you install/uninstall a bad software, and how it affects the registry.

After 6 weeks working with Ubuntu I finally messed it kind of up.

I followed this link below to install the latest ATI drivers and in my infinite wisdom I didn't take the easier more straight forward (alternative) route and went hardcore with building packages.  Even though I have followed every step, it didn't work for me and I ended up removing and purging the ATI driver and take the second route, which finally worked without a fuss.

[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-in-12-04-lts](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-in-12-04-lts)


So now I have ended up with all these weird packages that I installed on the way to compile the drivers, which I don't even need anymore. 

```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper
sudo apt-get install debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
sudo apt-get install ia32-libs
sudo apt-get install ia32-libs-multiarch 
sudo apt-get install i386 lib32gcc1  
sudo apt-get install libc6-i386
```

Can I simply remove this bloat like this:

sudo apt-get remove xxx

or would this affect my system? Is there still hope?

Thank you,

---

### Post by Shadius on 2012-06-04
[Click Here]("https://help.ubuntu.com/community/AptGet/Howto#Removal_commands")

You could probably do: 
```
sudo apt-get purge <package_name>
```

as that removes the package as well as the configuration files. 

I usually run:
```
sudo apt-get autoclean
```

and 
```
sudo apt-get clean
```

and I use the
```
du -sh /var/cache/apt/archives
```

to compare before and after to see how much space I've gained.

---

### Post by cortman on 2012-06-04
Just one more command:

```
sudo apt-get autoremove
```

---

### Post by Shadius on 2012-06-04
> **cortman said:**
> Just one more command:

```
sudo apt-get autoremove
```

Oh yes, forgot that one. :)

---

### Post by coffeecat on 2012-06-04
Why bother? Unless you are really tight for hard drive space, they won't be doing any harm, and they certainly won't be slowing the system down. Also - if you really want to uninstall unwanted apps and libraries, make sure they aren't still needed. A handful of the apps you list come with a default install of Ubuntu, so even if you think you installed them, you didn't. They were already there. wget for one is not an app I would want to uninstall, but you may or may not need it.

And - if you do try a sudo apt-get purge, you may find that some of those libraries are dependencies of other apps you have installed. Proceed with caution and if you do try to purge all or some of those packages and get a message saying that apt-get wants to uninstall other stuff, stop there and post the message so that people can advise.

---

### Post by Houmie on 2012-06-04
Hey guys,

Thank you very much for the help.

I went to the Software center the removed each one one by one.
Does Software center do a apt-get purge or apt-get remove by default?

I have removed the following packages:
```
build-essential cdbs fakeroot dh-make debhelper
ia32-libs, ia32-libs-multiarch, lib32gcc1, libc6-i386

```

I didn't remove the following packages, as it warned me about not removing debconf, I got scared left the rest of them. Well I read their description and didn't understand what they do, so I left them there.

```
debconf, libstdc++6, dkms, libqtgui4, wget, execstack, libelfg0, dh-modaliases
```


If anyone knows if I should remove any of those mentioned above,m please let me know,

Thanks,

---

### Post by cortman on 2012-06-04
> **Houmie said:**
> Hey guys,

Thank you very much for the help.

I went to the Software center the removed each one one by one.
Does Software center do a apt-get purge or apt-get remove by default?

I have removed the following packages:
```
build-essential cdbs fakeroot dh-make debhelper
ia32-libs, ia32-libs-multiarch, lib32gcc1, libc6-i386

```

I didn't remove the following packages, as it warned me about not removing debconf, I got scared left the rest of them. Well I read their description and didn't understand what they do, so I left them there.

```
debconf, libstdc++6, dkms, libqtgui4, wget, execstack, libelfg0, dh-modaliases
```


If anyone knows if I should remove any of those mentioned above,m please let me know,

Thanks,

You don't want to delete those. And even if they aren't actively being used, like coffeecat said, they're not going to slow down your system.

---

### Post by linuxman94 on 2012-06-04
EDIT: Didn't see Coffeecat's post :)

You really don't need to remove those packages as they take up minimal space on the hard drive.  

One thing you must remember is that Linux is NOT Windows.  It does not get bloated quite as easily.  That said, if you install a lot of programs then it will.  The only reason you would need to remove those packages is if you have minimal disk space.

Also, what issue were you having with building the AMD Drivers?  I've dealt with them in the past and have not had any problems.

---

### Post by Houmie on 2012-06-04
Oh right, when I was still writing my post when coffeecat posted his reply. No problem I won't touch them anymore. 

I hope you agree with the ones I have already removed. If it was stupid, please let me know and I install them back in.

Yeah I guess its still the Windows attitude in me fearing to bloat the system. :) I need some more time to get used to it.

@linuxman94

I have followed every step there. After a reboot though the ATi card wasn't recognized 100%, since fglrxinfo was giving me some weird information.

The display didn't get properly detected and got lost after each reboot. (see screenshot below)

[http://askubuntu.com/questions/146380/ati-catalyst-video-drivers-in-12-04-lts-cant-rotate](http://askubuntu.com/questions/146380/ati-catalyst-video-drivers-in-12-04-lts-cant-rotate)

Installing from the script without doing packages worked like a charm for me though.

---

