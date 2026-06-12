---
title: "Updating Ubuntu OS and other software"
date: 2018-03-22
forum: New to Ubuntu
---

### Post by waltd on 2018-03-22
Hi all, I'm a newbie and this is a newbie question.  I have a few questions about updating Ubuntu OS and other software. To update Ubuntu OS and other software, is there a difference between the Software Updater vs Ubuntu Software update tab?  Is one preferred over the other?  Also is there a notification that displays when software is ready to be updated, like a little notification icon?  Thank you for your assistance.  I appreciate it.

---

### Post by Geoffrey_Arndt on 2018-03-22
Well, not sure what you mean by "Ubuntu Software update tab" . . . . there is the Ubuntu Software icon in the launcher that looks like a folder with an A on it . . it's the Ubuntu Application Store to use a more newbie friendly term.   So, Ubuntu Software is one tool that is used to actually install new software (or remove software).    Another tool that does that is the program called "Synaptic Package Manager" (and it has more apps).   You actually use Ubuntu Software to install Synaptic.

But that isn't the same program that is used to check and advise if any software updates are available.   That icon looks like a circle with two arrows along the edge and an A in the middle.   That is the icon that pops up in the Launcher when a software update is available.    You just click on it and let it update your system with all new bug fixes, security updates, etc.

---

### Post by Impavidus on 2018-03-23
I don't use the Ubuntu Software update tab. I never use Ubuntu Software and I'm not sure it's actually installed on my computer. There are also update manager, synaptic and multiple command line tools you can use to update your system. It doesn't really matter which one you use. They differ on a few details, but all of them will install your updates and behind the scenes all of them use the same low level tools and get updates from the same sources.

---

### Post by col48 on 2018-03-23
I think this..> behind the scenes all of them use the same low level tools and get updates from the same sources.  from Impavidus is key and reassuring.  Each is blind to what method was used previously so you can switch with confidence.  When installing or removing software I use Synaptic (in Ubuntu 16.04) because that is what I am used to and its presentation suits the way my mind works.

As for notification, I get ```
[Software Update]
``` or something similar (can't recall the exact words) alongside the icons of running apps.  This is what Geoffrey_Arndt refers to. I *think* this only monitors supported software (items with the Ubuntu icon beside them in the Synaptic list), not ones originating from third parties.  If I click on it I get the screen which tells me what can be updated and the option to update immediately.  I do not have any automatic updating.

---

### Post by grahammechanical on 2018-03-23
May I add something that I think has not been covered?

If we go to System Settings and click Software & Updates & open the Updates tab. There you can set when the OS will check for updates. It can be set for Daily; Every two days; weekly; Every fortnight or never.

A notification will appear soon after the OS has done this check if there are any OS updates available.

Most default applications in Ubuntu do not get updates during to life of the Ubuntu version. Libreoffice & Firefox are two applications that do get updates. I think. I do not know of any others.

Regards

---

### Post by col48 on 2018-03-23
@grahammechanical

Thanks for adding this. Thunderbird updates, as well.

---

### Post by Mark Phelps on 2018-03-24
Ubuntu is not like MS Windows -- where you get routine updates for apps on a regular basis.

As mentioned, most apps are updated for a major release and not again, for the remainder of that release.  To get a new version, you have to upgrade to a new release of the OS.

There are a few rare exceptions, and folks have mentioned those.

There are also "ppa"s where some app are released using their own libraries, and updates to get released to those, from time to time --but that varies by individual app.

---

### Post by Impavidus on 2018-03-24
> **grahammechanical said:**
> 
Most default applications in Ubuntu do not get updates during to life of the Ubuntu version. Libreoffice & Firefox are two applications that do get updates. I think. I do not know of any others.
That means no new version of the application with new features. You may get major bug fixes and security fixes for most default applications.

Just in case anyone got confused.

---

