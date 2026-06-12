---
title: "Choosing updates"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by Oxyris on 2012-08-07
I'm a bit afraid of breaking my machine because I've heard some people have had that problem after updating. How safe is it to just let update manager install all available updates? I currently have 300+ updates waiting and I've just been going through them and installing the ones that I know what they do. Some of them, like one of the linux kernal updates say to install a different one instead (linux-generic-pae-meta-package versus linux-generic-pae(new install)) and others are updates for applications I don't have (bunch of updates for Evolution; I'm using Thunderbird).

---

### Post by CharlesA on 2012-08-07
I just let it install all updates. I have only had a problem once and that was fixed before a reboot.

---

### Post by mcduck on 2012-08-07
You will never get updates for applications you don't have, so every update really is for somehting you have installed now.

Also the rules for updating a package in Ubuntu are pretty strict, updates are only provided to fix security issues and more serious bugs. Because of this it's highly recommended to just install all the available updates.

It's really, really rare for normal updates coming from Ubuntu's official repositories to break anything, they are pretty thoroughly tested. So unless you are using third-party repositories there should be no reason to worry about anything breaking.

(the most common reason I've seen anybody having troubles after updates are those who have manually installed proprietary graphics card drivers directly from AMD or nVidia's website instead of using the versions form Ubuntu's repositories. In that case updating the kernel requires you to reinstall the driver as well. And of course updating to new Ubuntu *release version* can cause problesm, but that's completely different thing that just installing the normal updates)

---

### Post by kd5mkv on 2012-08-07
I have seen (Not Authenticated) in the update window. Because these are not 
from trusted sources. If you run programs from the Ubuntu trusted sources, repository,synaptic and canonical supported you should not have to worry about updates. Your system requires system and security updates to keep things running properly, remember Ubuntu was made to be user-friendly.

---

### Post by centaurusa on 2012-08-07
> **Oxyris said:**
> I'm a bit afraid of breaking my machine because I've heard some people have had that problem after updating. How safe is it to just let update manager install all available updates?

It is highly unlikely that Update Manager will break your Ubuntu installation - however, it can happen - very occasionally.  (See, for example: [http://linuxnorth.wordpress.com/2012/03/31/in-praise-of-backups/](http://linuxnorth.wordpress.com/2012/03/31/in-praise-of-backups/))  The safe thing to do is to maintain an up-to-date disk image of your system before any major updates.  Then, if things go south, you can reload the earlier image and be back in business in minutes.

Also, you aren't receiving updates for apps. that you don't have (i.e. Evolution).  It is more likely that you have installed, and are using, Thunderbird without uninstalling Evolution.  Because Evolution remains installed, Update Manager continues to pump out updates (just in case you want to go back to using this mail client [grin]).

---

### Post by Oxyris on 2012-08-07
Well thanks you all for the help and suggestions. Updating and nothing seems out of whack yet so I'll keep confident on updating.:)

---

### Post by d4m1r on 2012-08-07
Unfortunetly, there is no easy way to ignore updates on Ubuntu so if you do get prompt to install updates for things you don't want or even have, either you install them now and get rid of them or you'll just be prompt to update them in the future....Why we get those updates at all, I'm not sure, but it may be someone to do with decencies being left over after removing the main application package....

---

### Post by mcduck on 2012-08-08
> **d4m1r said:**
> Unfortunetly, there is no easy way to ignore updates on Ubuntu so if you do get prompt to install updates for things you don't want or even have, either you install them now and get rid of them or you'll just be prompt to update them in the future....Why we get those updates at all, I'm not sure, but it may be someone to do with decencies being left over after removing the main application package....

The thing is, *you will never get updates* for things you don't have installed.

The update mechanism only looks for new versions of packages you already have on your machine.If you don't want those updates you should uninstall the packages the updates are for.

---

### Post by Peripheral Visionary on 2012-08-08
I'm pretty paranoid about updates, especially kernel updates. I feel like "it ain't broke, so why fix it!"

I reluctantly allow only critical security updates and nothing else. I still see "*broken after update*" threads in these forums far too frequently to be comfortable allowing anything but critical updates.

---

### Post by d4m1r on 2012-08-08
> **mcduck said:**
> The thing is, *you will never get updates* for things you don't have installed.

The update mechanism only looks for new versions of packages you already have on your machine.If you don't want those updates you should uninstall the packages the updates are for.

I meant like getting an update for thunderbird-xxxx but not having thunderbird installed...It should be smart enough to NOT check for updates for the dependencies if the main package isn't installed....

---

### Post by Frogs Hair on 2012-08-08
I have been installing/testing proposed updates since 10.04 without any problems and I update daily for this reason . I don't suggest waiting until there are 300 updates because if problems do arise it is harder isolate the offending package.

The further Ubuntu gets from release date the more updates there will be when installed. The first thing I do when installing Ubuntu     is install all updates prior to any tweaking or video driver installation even if there are hundreds.

---

### Post by audiomick on 2012-08-08
> **d4m1r said:**
> .It should be smart enough to NOT check for updates for the dependencies if the main package isn't installed....

It doesn't. As McDuck has already said twice, the system only looks for updates of packages that are actually installed. If you are getting updates for thunderbird, it is installed, even if you think it isn't. The only thing that might possibly occur that makes it look like this isn't true is if there is a package from one program that has been installed as a dependency from another. 

I suppose it is also possible that de-installing may have left an orphaned package that then might be getting updated. I believe this can be solved by using the purge command, and I believe the janitor has a function for removing orphaned packages. Be careful with the janitor, though. It has been known to want to remove stuff that is still needed. Have a close look at what it wants to do.

---

### Post by mcduck on 2012-08-08
> **d4m1r said:**
> I meant like getting an update for thunderbird-xxxx but not having thunderbird installed...It should be smart enough to NOT check for updates for the dependencies if the main package isn't installed....

If you get update for package thunderbird-xxx then you mst have thunderbird-xxx installed,.

The package management doesn't work with a concept of programs, but packages instead. And if you have a certain aåckage installed, the only reasonable choise for the package manager is to assume you actually want to have that packge, and therefore you should also get updates for it.

If you have extra packages you don't want, just uninstall them and you don't need to worry about updating them any more. PLus you'll of course save some disk space.

*apt-get autoremove* and *deborphan* are handy tools for uninstalling packages that were installed as dependencies of something and the original package that brought them along has already been removed.

---

