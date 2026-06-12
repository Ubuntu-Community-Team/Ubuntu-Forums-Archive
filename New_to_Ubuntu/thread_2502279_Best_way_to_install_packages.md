---
title: "Best way to install packages"
date: 2024-11-08
forum: New to Ubuntu
---

### Post by joepesci2 on 2024-11-08
Hi everyone.
Im a new Ubuntu user and i have some questions about installing packages.
What would be the best way to install software?
I have read in some places that its better to use apt, but in other places i have seen that its better to download the deb from the official website of each software.

If i install it from apt, will it automatically update to the new versions when i will do apt upgrade-update or do i would have to add the repositories?

If i install it from the .deb, would it update in the future or would i would have to download the deb again?

Thank you very much and sorry if the questions are stupid.

---

### Post by ajgreeny on 2024-11-08
You should certainly, particularly a new user of Ubuntu, steer well away from searching for and installing .deb packages from anywhere other than the Ubuntu repositories.

Anything installed from the Ubuntu repos will be guaranteed secure and will update with the normal software updates whether you use the command line, sudo apt update/upgrade or the GUI version which i have never bothered with.

As you become more acquainted with Linux and Ubuntu, there may be a very few things that have to be installed by other methods but don't concern yourself with them yet; just continue using the repos and ask again here if you find something you installed not working.

---

### Post by joepesci2 on 2024-11-08
> **ajgreeny said:**
> You should certainly, particularly a new user of Ubuntu, steer well away from searching for and installing .deb packages from anywhere other than the Ubuntu repositories.

Anything installed from the Ubuntu repos will be guaranteed secure and will update with the normal software updates whether you use the command line, sudo apt update/upgrade or the GUI version which i have never bothered with.

As you become more acquainted with Linux and Ubuntu, there may be a very few things that have to be installed by other methods but don't concern yourself with them yet; just continue using the repos and ask again here if you find something you installed not working.

Hi ajgreeny!
Do you mean that if i install Firefox with apt, in the future it will be updated to new versions when i will do apt update-upgrade?
Do updates take longer to arrive or is there some inconvenience?

And finally, is it necessary to add repositories to Ubuntu to update the software or isnt necessary?

Thank you very much for your patience and kindness.

---

### Post by Dennis N on 2024-11-08
Ubuntu 24.04 LTS comes with a software store application called "App Center" (see image) where you can find software by category or searching. Just search for "App Center" in the Overview Screen, accessed by Windows Key (aka Super Key).

You can install using the terminal, but you must know the package name of the software.

Ubuntu automatically updates some software (like Firefox), and provides security updates, but most software stays at the version that comes with the original Ubuntu install.

The repositories are automatically configured for your system when you install. No need to deal with that.

---

### Post by vanadium on 2024-11-08
The answer to your question is very simple: never download deb files. Install software using apt. This installs software packaged and tested for your distribution, and will automatically update if security issues are fixed. There will, however, not be updates to possible newer major versions of the software, except then for Firefox (which, however, is nowadays installed using a different system, "snap"). 

You can also use the graphical tool to safely install software. Ubuntu now has two different systems to install software: the newer "snap" system, and the traditional APT system. The software tool will prefer snap-packaged versions if available, but you can always select the apt version yourself if you prefer (and if available).

From the command line, software distributed using the traditional APT system is installed through the command "apt". For software distributed using the snap framework, "snap"  is the command.

---

### Post by joepesci2 on 2024-11-08
> **Dennis N said:**
> Ubuntu 24.04 LTS comes with a software store application called "App Center" (see image) where you can find software by category or searching. Just search for "App Center" in the Overview Screen, accessed by Windows Key (aka Super Key).

You can install using the terminal, but you must know the package name of the software.

Ubuntu automatically updates some software (like Firefox), and provides security updates, but most software stays at the version that comes with the original Ubuntu install.

The repositories are automatically configured for your system when you install. No need to deal with that.

> **vanadium said:**
> The answer to your question is very simple: never download deb files. Install software using apt. This installs software packaged and tested for your distribution, and will automatically update if security issues are fixed. There will, however, not be updates to possible newer major versions of the software, except then for Firefox (which, however, is nowadays installed using a different system, "snap"). 

You can also use the graphical tool to safely install software. Ubuntu now has two different systems to install software: the newer "snap" system, and the traditional APT system. The software tool will prefer snap-packaged versions if available, but you can always select the apt version yourself if you prefer (and if available).

From the command line, software distributed using the traditional APT system is installed through the command "apt". For software distributed using the snap framework, "snap"  is the command.

Ive installed Ubuntu with minimum software, only installed the desktop environment.
Ive then installed Firefox using apt:

If Firefox releases a new version in a while, will it automatically update when i will do apt update-upgrade?
How do i know which software i will need to add a repository to the Ubuntu archive?

Sorry if im repetitive or these are silly questions, but i like to establish the knowledge and basic operation well. 

Thank you for your help and tips.

---

### Post by grahammechanical on 2024-11-08
> What would be the best way to install software?
 
In my opinion with Linux there is no best way and no worst way. Just alternative ways of doing things. 

Updating the operating system is different from updating applications. On Ubuntu there are only a few applications that are regularly upgraded during the life support period of any Ubuntu version. Those that I can think of are Firefox; Thunderbird and Libreoffice. There may be others but they do not come to mind.

Most applications that are part of the default installation of Ubuntu are only upgraded when we move on to the next version of Ubuntu.

As for updating the operating system in Ubuntu there are three ways to do this. By the terminal

```
sudo apt update
sudo apt upgrade
sudo snap refresh
```

Running the Software and Updates utility. That is the front end for running those three commands. Or open App Centre and select Manage. That will reveal what Snap packages are ready to be updated. It also says: Debian package updates are handled by the Software Updater.

There are different ways of installing software. As explained above the new user should install applications through the App Center. That will offer mainly Snap packaged application but the search can be expanded to include Debian (deb) packaged applications. The App Centre provides the user with some measure of confidence that the applications do not have any malicious code in them. The same is true when we use the terminal to install those same applications.

```
sudo apt install <package name>
```

Both App Centre and apt install/update/upgrade access the same Ubuntu software repositories. There are other methods of installing software. They can be complicated to use and in some cases the software is downloaded with the user accepting a measure of security risk.

Oh, by the way, software that is deb packaged will run on Ubuntu but software that is rpm packaged will not run on Ubuntu. Redhat and Fedora use rpm packaged applications. Some other distributions also do the same.

Regards

---

### Post by grahammechanical on 2024-11-08
> How do i know which software i will need to add a repository to the Ubuntu archive?

Trying installing the package using apt and if your OS has not enabled the appropriate repository then you will get an error message.

If you had told us that you installed Ubuntu as the Essentials I would not have wasted my time explaining about the App Centre and Software & Updater. You only have the terminal to install software.

Next question: How do I find out what repositories have been enabled using only the terminal? I have no idea.

Regards

---

### Post by joepesci2 on 2024-11-08
> **grahammechanical said:**
> In my opinion with Linux there is no best way and no worst way. Just alternative ways of doing things. 

Updating the operating system is different from updating applications. On Ubuntu there are only a few applications that are regularly upgraded during the life support period of any Ubuntu version. Those that I can think of are Firefox; Thunderbird and Libreoffice. There may be others but they do not come to mind.

Most applications that are part of the default installation of Ubuntu are only upgraded when we move on to the next version of Ubuntu.

As for updating the operating system in Ubuntu there are three ways to do this. By the terminal

```
sudo apt update
sudo apt upgrade
sudo snap refresh
```

Running the Software and Updates utility. That is the front end for running those three commands. Or open App Centre and select Manage. That will reveal what Snap packages are ready to be updated. It also says: Debian package updates are handled by the Software Updater.

There are different ways of installing software. As explained above the new user should install applications through the App Center. That will offer mainly Snap packaged application but the search can be expanded to include Debian (deb) packaged applications. The App Centre provides the user with some measure of confidence that the applications do not have any malicious code in them. The same is true when we use the terminal to install those same applications.

```
sudo apt install <package name>
```

Both App Centre and apt install/update/upgrade access the same Ubuntu software repositories. There are other methods of installing software. They can be complicated to use and in some cases the software is downloaded with the user accepting a measure of security risk.

Oh, by the way, software that is deb packaged will run on Ubuntu but software that is rpm packaged will not run on Ubuntu. Redhat and Fedora use rpm packaged applications. Some other distributions also do the same.

Regards


Hi grahammechanical! I understand that Ubuntuss own patches and operating system updates are done with the update and upgrade.
My question is more focused on other "non-essential" programs such as Discord, Steam, Obsidian, etc.

Thank you for your help and kindness.

---

### Post by joepesci2 on 2024-11-08
> **grahammechanical said:**
> Trying installing the package using apt and if your OS has not enabled the appropriate repository then you will get an error message.

If you had told us that you installed Ubuntu as the Essentials I would not have wasted my time explaining about the App Centre and Software & Updater. You only have the terminal to install software.

Next question: How do I find out what repositories have been enabled using only the terminal? I have no idea.

Regards

I have installed Ubuntu with the minimum, but the applications app does appear.

Thanks for your help!

---

### Post by TheFu on 2024-11-08
> **joepesci2 said:**
> Ive installed Ubuntu with minimum software, only installed the desktop environment.
Ive then installed Firefox using apt:

If Firefox releases a new version in a while, will it automatically update when i will do apt update-upgrade?
How do i know which software i will need to add a repository to the Ubuntu archive?

Sorry if im repetitive or these are silly questions, but i like to establish the knowledge and basic operation well. 

Thank you for your help and tips.

If you use apt (or any apt-based front-end) to install debian packages, then, yes, update/upgrade will get the version for the OS you are running, updated for security issues and sometimes for new features.  However, the goal of any "release" is stability, so don't expect new features for 99% of the packages, just bug fixes and security updates.

Now, Canonical has also decided to "help us" migrate to using snap packages. They do this for firefox, chromium, thunderbird, and a few other things.  For those things, using **apt install** will pull a tiny .deb file that forces the snap version of the package to be installed.  This can be desirable or terrible, depending on your needs and the specific package.

By default, snaps packaged software checks for updates 4x every day.  It is possible to change the period and delay checking, but as we all know, the tyranny of the default is a real thing.

I patched once a week, usually on Saturday mornings, so my systems are stable and ready for work all the other days.  About once every 3-5 yrs, something bad will happen with one of these patched upgrades, so I'd rather not waste time on Monday trying to solve a stupid issue. I want my computers to earn money and help me deal with clients.  I've found how to use some snap commands to delay snap updates to happen only on Saturdays.  Sadly, at 12:01am, Saturday, any snap packages are queued up to go and hunt for updates.  It messes with my system backups.  The snap interface doesn't allow finer control, sadly. I could do some network blocking outside of snapd, to get what I want, but that's a little more effort than I can justify.

There are reasons why I only use LTS releases: [https://blog.jdpfu.com/2010/07/29/why-i-use-a-linux-desktop](https://blog.jdpfu.com/2010/07/29/why-i-use-a-linux-desktop)  --- it is a bit old, but still relevant.  Package management and easy maintenance is a key reason why I've been using Linux a very long time.  More important than any GUI, at least to me.

The summary of my preferred order to choose to install programs is this:
[LIST=1]
[*]repo, 
[*]snaps, 
[*]PPAs, 
[*]source, 
[*]deb files
[/LIST]

More discussion on each
 
[LIST]
[*] Always start with using the Distro packaged solutions first. APT.
[*] Next, look for a trusted PPA and use that. PPAs integrate into the normal OS  patching and a trusted PPA would provide updates as needed when dependent  packages are updated.
[*] Next would be a Snap/Flatpak/AppImage package. There are some downsides and   upsides to using these. Canonical seems to think our computers are  smartphones with 1 storage device and I suppose for that situation, Snaps  aren't THAT bad. But they don't allow local control and people using more  storage are likely to bang their head's into storage access restrictions.
[*] Next would be a .deb/.rpm file. This will most likely break package  dependencies and in 3-6 months, 1 package can prevent other important core  packages from being updated. This is commonly known as "RPM Hell", but "APT   Hell" would better fit on Ubuntu. There are 2 solutions for APT Hell. Remove  the original .deb file that was manually installed OR do a fresh -  clear-field - nuked-from-orbit - OS install.
[*] Next would be using source code. This assumes it is a compiled language. For  some small script programs (python/GoLang/Perl/Bash), that work in highly  dynamic ways and need updating weekly, it would be preferred to use the  original script install/update method and not the .deb file or snap or PPA or  even Canonical Repos. But for larger projects with multiple dependencies and  compiles, best to avoid manually installation, since this means you've just   accepted the need to redo this at least monthly for as long as the system  uses that program. All to stay patched and current.

[/LIST]

I think that list handles most situations. There can be exceptions, but those really need to be avoided by people who cannot fully commit to maintaining their systems.

Snagged that from a LUG presentation I did a few years ago.

---

### Post by joepesci2 on 2024-11-08
> **TheFu said:**
> If you use apt (or any apt-based front-end) to install debian packages, then, yes, update/upgrade will get the version for the OS you are running, updated for security issues and sometimes for new features.  However, the goal of any "release" is stability, so don't expect new features for 99% of the packages, just bug fixes and security updates.

Now, Canonical has also decided to "help us" migrate to using snap packages. They do this for firefox, chromium, thunderbird, and a few other things.  For those things, using **apt install** will pull a tiny .deb file that forces the snap version of the package to be installed.  This can be desirable or terrible, depending on your needs and the specific package.

By default, snaps packaged software checks for updates 4x every day.  It is possible to change the period and delay checking, but as we all know, the tyranny of the default is a real thing.

I patched once a week, usually on Saturday mornings, so my systems are stable and ready for work all the other days.  About once every 3-5 yrs, something bad will happen with one of these patched upgrades, so I'd rather not waste time on Monday trying to solve a stupid issue. I want my computers to earn money and help me deal with clients.  I've found how to use some snap commands to delay snap updates to happen only on Saturdays.  Sadly, at 12:01am, Saturday, any snap packages are queued up to go and hunt for updates.  It messes with my system backups.  The snap interface doesn't allow finer control, sadly. I could do some network blocking outside of snapd, to get what I want, but that's a little more effort than I can justify.

There are reasons why I only use LTS releases: [https://blog.jdpfu.com/2010/07/29/why-i-use-a-linux-desktop](https://blog.jdpfu.com/2010/07/29/why-i-use-a-linux-desktop)  --- it is a bit old, but still relevant.  Package management and easy maintenance is a key reason why I've been using Linux a very long time.  More important than any GUI, at least to me.

The summary of my preferred order to choose to install programs is this:
[LIST=1]
[*]repo, 
[*]snaps, 
[*]PPAs, 
[*]source, 
[*]deb files 
[/LIST]

More discussion on each
 
[LIST]
[*] Always start with using the Distro packaged solutions first. APT. 
[*] Next, look for a trusted PPA and use that. PPAs integrate into the normal OS  patching and a trusted PPA would provide updates as needed when dependent  packages are updated. 
[*] Next would be a Snap/Flatpak/AppImage package. There are some downsides and   upsides to using these. Canonical seems to think our computers are  smartphones with 1 storage device and I suppose for that situation, Snaps  aren't THAT bad. But they don't allow local control and people using more  storage are likely to bang their head's into storage access restrictions. 
[*] Next would be a .deb/.rpm file. This will most likely break package  dependencies and in 3-6 months, 1 package can prevent other important core  packages from being updated. This is commonly known as "RPM Hell", but "APT   Hell" would better fit on Ubuntu. There are 2 solutions for APT Hell. Remove  the original .deb file that was manually installed OR do a fresh -  clear-field - nuked-from-orbit - OS install. 
[*] Next would be using source code. This assumes it is a compiled language. For  some small script programs (python/GoLang/Perl/Bash), that work in highly  dynamic ways and need updating weekly, it would be preferred to use the  original script install/update method and not the .deb file or snap or PPA or  even Canonical Repos. But for larger projects with multiple dependencies and  compiles, best to avoid manually installation, since this means you've just   accepted the need to redo this at least monthly for as long as the system  uses that program. All to stay patched and current. 
[/LIST]

I think that list handles most situations. There can be exceptions, but those really need to be avoided by people who cannot fully commit to maintaining their systems.

Snagged that from a LUG presentation I did a few years ago.




Lets say i will install Obsidian via apt.
If Obsidian releases a new version of their software in a few months, will it also update to that new version by running apt update/upgrade? Once i install Obsidian for the first time via APT, does it automatically add the Obsidian PPA or would i have to add it manually later?

I have read your post carefully and i see that APT is definitely your favorite method, however i cant find any reason or argument for using Snap.
It seems that even Flatpak would go way before Snap.
Is there any advantage to using Snap? maybe there is but i cant see it.

I dont really like having some applications via apt, some via snap, some via .deb... I mean, if everything can be done effectively, safely and consistently via APT, i think that would be great.

Thank you very much for your help and kindness.

---

### Post by TheFu on 2024-11-08
> **joepesci2 said:**
> Lets say i will install Obsidian via apt.
If Obsidian releases a new version of their software in a few months, will it also update to that new version by running apt update/upgrade? Once i install Obsidian for the first time via APT, does it automatically add the Obsidian PPA or would i have to add it manually later?

Depends on what a "new version" means.  It is contains bug fixes or security patches, then the version would change from 1.5.3 --> 1.5.4 and that would get updated.  OTOH, if the updates are for new "features", then no, it wouldn't.  Feature updates usually happen in 1.5.3 -->  1.6.x  OR 1.5.3 --> 2.0.0 upgrades.   Remember, the goal is for the software to be stable and NOT to add any new features.

If you want new features, then you'll need either a flatpak or a snap or a PPA or the source code or a compatible .deb from someone on the internet which may or may not have nefarious extra code.

> **joepesci2 said:**
> I have read your post carefully and i see that APT is definitely your favorite method, however i cant find any reason or argument for using Snap.
It seems that even Flatpak would go way before Snap.
Is there any advantage to using Snap? maybe there is but i cant see it.
I'm not a fan of snaps or flatpaks for the most part. They are bloated, slow, have _**constraints that cannot be removed.**_ You can read in long threads in these forums about all the reasons snaps may not be great for everyone. I've never used a flatpak and don't have any interest.  

I use **AppImages** for a few things. These are un-constrained, single-file, tools what are also bloated, slow, and contain, in theory, all the required dependencies for a program to run.  AppImages don't get in my way like snaps and flatpaks do.  They don't automatically update either.  To update an appimage, assuming it doesn't have self-updating built-in, I have to go and file the location of the appimage to see what's there.

> **joepesci2 said:**
> 
I dont really like having some applications via apt, some via snap, some via .deb... I mean, if everything can be done effectively, safely and consistently via APT, i think that would be great.

I don't either, but I also enjoy the flexibility that different options provide.  Be careful about the source for any programs you allow to run on your computer.  That's the main warning.

We already are trusting Canonical. We run there OS. We use their repos.  We have assurances that the software in those repos that we get are actually reviewed and built without "extras" by people with reputations to maintain.

Some PPAs are great, but not all of them.  I only trust PPAs from reputable sources OR from the project team who created the software to begin with.  For example, if I want to run Nextcloud and use a PPA, I'll use the PPA from the Nextcloud team, not "Joe's PPA of assorted curiosities".  Reputation matters. For firefox, I use the Mozilla PPA, not "Stevo's Greatest Hits PPA".

The same goes for Snaps, Flatpaks, AppImages.  The source of the package matters.  If I post a setup.exe on my website and say it is safe, nobody should believe me.  We are entirely too trusting, especially if someone seems nice.

There are always going to be software that isn't in the Canonical Repos.  I write code and have some programs that will never been in Canonical's repos for a number of reasons.  Some of those reasons are technical, but the main reason is political.  Until the projects are popular enough, there's little reason for Canonical to include my software.  Plus, I don't make deb packages for it and have no plans to ever do so.  Having flexibility and control is why my suggested order of preference for installing software is in the order it is in.  Snaps remove much of the control I want for almost everything.  I have found 1 specific snap that I mostly like as a snap, not in any other installation method.  It is some server software that I use many times a day.  All the other snap packages, I would happily do without.  In fact, I'd like to only have 1 snap package on only 1 of my systems and never, ever, worry that some other snap might be installed - ever.

---

### Post by joepesci2 on 2024-11-08
> **TheFu said:**
> Depends on what a "new version" means.  It is contains bug fixes or security patches, then the version would change from 1.5.3 --> 1.5.4 and that would get updated.  OTOH, if the updates are for new "features", then no, it wouldn't.  Feature updates usually happen in 1.5.3 -->  1.6.x  OR 1.5.3 --> 2.0.0 upgrades.   Remember, the goal is for the software to be stable and NOT to add any new features.

If you want new features, then you'll need either a flatpak or a snap or a PPA or the source code or a compatible .deb from someone on the internet which may or may not have nefarious extra code.


I'm not a fan of snaps or flatpaks for the most part. They are bloated, slow, have _**constraints that cannot be removed.**_ You can read in long threads in these forums about all the reasons snaps may not be great for everyone. I've never used a flatpak and don't have any interest.  

I use **AppImages** for a few things. These are un-constrained, single-file, tools what are also bloated, slow, and contain, in theory, all the required dependencies for a program to run.  AppImages don't get in my way like snaps and flatpaks do.  They don't automatically update either.  To update an appimage, assuming it doesn't have self-updating built-in, I have to go and file the location of the appimage to see what's there.



I don't either, but I also enjoy the flexibility that different options provide.  Be careful about the source for any programs you allow to run on your computer.  That's the main warning.

We already are trusting Canonical. We run there OS. We use their repos.  We have assurances that the software in those repos that we get are actually reviewed and built without "extras" by people with reputations to maintain.

Some PPAs are great, but not all of them.  I only trust PPAs from reputable sources OR from the project team who created the software to begin with.  For example, if I want to run Nextcloud and use a PPA, I'll use the PPA from the Nextcloud team, not "Joe's PPA of assorted curiosities".  Reputation matters. For firefox, I use the Mozilla PPA, not "Stevo's Greatest Hits PPA".

The same goes for Snaps, Flatpaks, AppImages.  The source of the package matters.  If I post a setup.exe on my website and say it is safe, nobody should believe me.  We are entirely too trusting, especially if someone seems nice.

There are always going to be software that isn't in the Canonical Repos.  I write code and have some programs that will never been in Canonical's repos for a number of reasons.  Some of those reasons are technical, but the main reason is political.  Until the projects are popular enough, there's little reason for Canonical to include my software.  Plus, I don't make deb packages for it and have no plans to ever do so.  Having flexibility and control is why my suggested order of preference for installing software is in the order it is in.  Snaps remove much of the control I want for almost everything.  I have found 1 specific snap that I mostly like as a snap, not in any other installation method.  It is some server software that I use many times a day.  All the other snap packages, I would happily do without.  In fact, I'd like to only have 1 snap package on only 1 of my systems and never, ever, worry that some other snap might be installed - ever.



Thank you very much for your messages, i found them very interesting and educational.

I would like to clarify that when im talking about installing a .deb, im not talking about any .deb that i will find on internet.
I am referring to the .deb that Firefox, Obsidian, Libreoffice offer on their websites... that is, .deb that are offered by official pages and companies that you trust and that you know will not contain anything malicious.

Likewise, when i m talking about PPA add-ons, im talking about official and legal repositories, such as those of Firefox and any other official and trustworthy company.

Perhaps i didnt make this clear at the beginning and it seemed that i was referring to any repository or .deb that you will find out there.

Again, i thank you for your messages, i look forward to your response.

---

### Post by TheFu on 2024-11-08
Not all Debs are equal.  If you download .deb files and install them, be prepared to get into "APT Hell" where you can't patch your system anymore because dependencies cannot be resolved.  You've been warned.

Ubuntu is just different enough that sometimes Debian versions of software break, or worse, break the APT dependencies of the system.

---

### Post by grahammechanical on 2024-11-08
Do you know what a PPA is?

> PPAs have not undergone the same process of validation as regular ubuntu packages. End users install PPAs at their own risk.

> Subsequently, installing a PPA should be considered to be a low-security  alternative as compared to the main repository, but marginally higher  security than simply installing software at random from the internet. As  part of adding a PPA, you trust the developer to not only install  packages, but also to allow them to provide ongoing updates.

Regards






[https://help.ubuntu.com/community/PPA](https://help.ubuntu.com/community/PPA)

---

### Post by ian-weisser on 2024-11-08
> **joepesci2 said:**
> 
I would like to clarify that when im talking about installing a .deb, im not talking about any .deb that i will find on internet.
I am referring to the .deb that Firefox, Obsidian, Libreoffice offer on their websites... that is, .deb that are offered by official pages and companies that you trust and that you know will not contain anything malicious.


Going to the Obsidian website to download an "official" Obsidian .deb is EXACTLY what we mean by "find on the internet"
Maybe it will work with your release of Ubuntu. Maybe it won't.
If it doesn't work, ask wherever you got it from for support.
If you want to know about their updates, you must ask them.


> **joepesci2 said:**
> 
Likewise, when i m talking about PPA add-ons, im talking about official  and legal repositories, such as those of Firefox and any other official  and trustworthy company.


PPAs are not "official" Ubuntu software.
PPAs are not an official repository. Their original purpose is testing.
If you add an "official" LibreOffice PPA, we might be able to help. We might not.
If it doesn't work, ask The Document Foundation for support.
If you want to know about their updates, you must ask The Document Foundation.

If you add LibreOffice from the Ubuntu Repos (apt) or the LibreOffice Snap, those are tested for compatibility with releases of Ubuntu.
We can help with those...though, since they are tested, few such support question arise.

---

### Post by guiverc on 2024-11-09
My preference is to use the default version in Ubuntu repositories... being a desktop user. 

One reason for doing it that way, is if I break my system due to problem/mistake, I know I can pretty quickly *non-destructively* re-install it and continue working...

I talk about the *non-destructive re-install* [here ]("https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533"), as that install method is something I use myself.

eg. I'm using Ubuntu *development* release currently; which is an *unstable* system where problems can occur from time to time... last time was August 2023 when two of my five screens became dark (*no image*) due to a kernel change.. Strange things like that can happen on *unstable*, so I monitored it, next day the issue was present on the *daily* so it was bug report with my install being mentioned... Within a week the issue was resolved on the *dailies*, however the issue remained on my installed system.. and I couldn't find a *fix* to my installed system... thus when bored of it, I just  *non-destructively* re-installed the system...   This involved ensuring my backup of data was good, then just re-install from the latest *daily*, reboot & then confirm the system worked as I expected... ie. my data AND *manually installed* apps were all there....   I was back fully operational in under 15 minutes.

It's an *easy fix* option as I see it, as I like being able to re-install and system, not lose my data, and have my *manually installed* or *additional apps* auto-reinstall automatically.

The install method I'm talking about assumes its Ubuntu repository software, and I've actually had it re-install *snap* packages too (*but also had it fail to install snap packages, unsure of why its not always reliable as I've not detected the pattern*), but I know it won't work with *flatpak*, *appimage*, and no QA is done with any 3rd party software.

Some issues with the type of install were detected in QA of *noble* (24.04), which haven't been fixed yet, so the install method isn't available on ISOs using `ubuntu-desktop-installer` for 24.04 & 24.10, but it still works on ISOs using the `calamares` installer..  and the hope is the bug in ubuntu-desktop-provision will get fixed, thus forced format can be removed allowing it to with ubuntu-desktop-installer too.

---

### Post by joepesci2 on 2024-11-09
> **TheFu said:**
> Not all Debs are equal.  If you download .deb files and install them, be prepared to get into "APT Hell" where you can't patch your system anymore because dependencies cannot be resolved.  You've been warned.

Ubuntu is just different enough that sometimes Debian versions of software break, or worse, break the APT dependencies of the system.

Hi TheFu! How are you? Thank you very much for the information.
Now its clear to me, must try to avoid installing directly via .deb at all costs. Thank you very much.


> **grahammechanical said:**
> Do you know what a PPA is?


Regards


[https://help.ubuntu.com/community/PPA](https://help.ubuntu.com/community/PPA)

Hi grahammechanical! Yes, i have an idea of &#8203;&#8203;what a PPA is, but i have seen that trusted companies like Firefox and similar also have PPA repositories, so it made me think that these types of PPAs would be reliable and more secure.
But it has become clear to me that its best not to add any kind of independent PPA to Ubuntu.
The problem will be if there is some software that is not in Ubuntus own repositories.

Thank you very much for all the information and for your time.

---

### Post by joepesci2 on 2024-11-09
> **ian-weisser said:**
> Going to the Obsidian website to download an "official" Obsidian .deb is EXACTLY what we mean by "find on the internet"
Maybe it will work with your release of Ubuntu. Maybe it won't.
If it doesn't work, ask wherever you got it from for support.
If you want to know about their updates, you must ask them.




PPAs are not "official" Ubuntu software.
PPAs are not an official repository. Their original purpose is testing.
If you add an "official" LibreOffice PPA, we might be able to help. We might not.
If it doesn't work, ask The Document Foundation for support.
If you want to know about their updates, you must ask The Document Foundation.

If you add LibreOffice from the Ubuntu Repos (apt) or the LibreOffice Snap, those are tested for compatibility with releases of Ubuntu.
We can help with those...though, since they are tested, few such support question arise.



Hi ian-weisser! How are you? Thank you very much for the information, thanks to you and other colleagues, it has become clear to me that we must try to avoid installing from outside APT at all costs.

The "problem" may come when that software isnt in the official Ubuntu repositories.

Thank you very much.

---

### Post by joepesci2 on 2024-11-09
> **guiverc said:**
> My preference is to use the default version in Ubuntu repositories... being a desktop user. 

One reason for doing it that way, is if I break my system due to problem/mistake, I know I can pretty quickly *non-destructively* re-install it and continue working...

I talk about the *non-destructive re-install* [here ]("https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533"), as that install method is something I use myself.

eg. I'm using Ubuntu *development* release currently; which is an *unstable* system where problems can occur from time to time... last time was August 2023 when two of my five screens became dark (*no image*) due to a kernel change.. Strange things like that can happen on *unstable*, so I monitored it, next day the issue was present on the *daily* so it was bug report with my install being mentioned... Within a week the issue was resolved on the *dailies*, however the issue remained on my installed system.. and I couldn't find a *fix* to my installed system... thus when bored of it, I just  *non-destructively* re-installed the system...   This involved ensuring my backup of data was good, then just re-install from the latest *daily*, reboot & then confirm the system worked as I expected... ie. my data AND *manually installed* apps were all there....   I was back fully operational in under 15 minutes.

It's an *easy fix* option as I see it, as I like being able to re-install and system, not lose my data, and have my *manually installed* or *additional apps* auto-reinstall automatically.

The install method I'm talking about assumes its Ubuntu repository software, and I've actually had it re-install *snap* packages too (*but also had it fail to install snap packages, unsure of why its not always reliable as I've not detected the pattern*), but I know it won't work with *flatpak*, *appimage*, and no QA is done with any 3rd party software.

Some issues with the type of install were detected in QA of *noble* (24.04), which haven't been fixed yet, so the install method isn't available on ISOs using `ubuntu-desktop-installer` for 24.04 & 24.10, but it still works on ISOs using the `calamares` installer..  and the hope is the bug in ubuntu-desktop-provision will get fixed, thus forced format can be removed allowing it to with ubuntu-desktop-installer too.


Hi guiverc! Thank you very much for all the information and for sharing your experience.
Although im a new Ubuntu user and many things are still unclear to me, i found it very interesting.

I would like you to elaborate a little more on your experience in August 2023, how you solved it, the steps to follow...

If you think this isnt the right thread for it, we can make another thread.

Thank you very much for the information and have a nice day.

---

### Post by guiverc on 2024-11-09
> **joepesci2 said:**
> 
I would like you to elaborate a little more on your experience in August 2023, how you solved it, the steps to follow...


I'm not sure what you're after... My posts says I'm on the *development* release, which most of the time is Lubuntu... The *development* release is where all work occurs, and thus it changes regularly, and things can go wrong, meaning problems can be encountered, which is why it's referred to as ***unstable***.

I update my system at least three times per day, thus hoping I get fewer updates on any particular update, as if problems occur, I have fewer packages to explore as to the possible cause. I'm currently running Lubuntu 25.04 with the [LXQt 2.1 desktop]("https://lxqt-project.org/release/2024/11/05/release-lxqt-2-1-0/"), the desktop itself was only packaged about three days ago in this case, though thus far I've not noticed any problems.

In my example, on reboot I noted two of my five displays were black in that they were getting no images from the PC... three of the displays connected to one video card were still working, but the two connected to one card were gone.  As my updates get packages BEFORE the daily ISOs are created, I waited until those packages I was running hit the next *daily* ISO, and tested it on a newer zsync'd (or updated) ISO, the reason for this was that my own machine had my own configs that were heavily modified, where the *daily* ISO contained none of those modified configs... so when it encountered the same issue, I knew it was related to changed code & not my configs...

In the following days, the problem continued; however in time the *daily* ISOs no longer had the issue when booted on my hardware, but my installed system was still suffering with only three of my five displays functional... so I went search for what was different (hadn't updated etc) on my installed system versus the newly built ISOs I was testing when I tried the daily ISOs... After a number of days looking for it, I wanted my system back to fully-operational, so gave up looking & just re-installed the system, meaning the issue was overwritten by a new install.

The install was described in the link I provided, ie. 

- the installer notes my installed packages (those the system marks as '*manually-installed*', or those I'd installed myself)
- erase system directories
- installs the system from the installation media
- then downloads the noted earlier 'manually installed' packages I had on my system from Ubuntu repositories (ie. *why I prefer using Ubuntu repository software*)
- asks me to reboot; all of which did NOT alter any config/data file on my system...

ie. on reboot; my expectation is my system operates just as it did before; as if nothing occurred...  Sure if I go look in `/var/log/installer/mediainfo` it'll show the install media wasn't whatever ISO I'd originally used, but showed the date I mentioned (20230829 OR 29th August daily), and the dates of files in the system directories all show the day/time I re-installed, ie. metadata on the file-system & some system files show a new install, but as far as I'm concerned the system acts as if it wasn't re-installed; but my wanted aim was I would have 5 displays back functional - which is what I got...

The re-install did not require me to touch any of my backups, nor restore any file...  I achieved what I wanted; a *non-destructive *re-install of the system, in effect all system code was erased & replaced by code from the ISO I'd installed from, or re-downloaded from Ubuntu repositories, and none of my configs/data was touched.

If you're wanting to understand it; I'll suggest you re-read the *askubuntu* link I provided, or if you need more, follow the link there back to a Lubuntu testcase exploration, as it was a testcase Lubuntu tested for from 19.04 thru 24.04, and in the Lubuntu link I tried to explain it for other Quality Assurance testers.

---

### Post by Dennis N on 2024-11-09
> The "problem" may come when that software isnt in the official Ubuntu repositories.
Yes and more software is now being packaged by their developers only in a "universal" format such as Flatpak. To have a .deb or .rpm package, a human maintainer must be found.

Personally I use quite a few Flatpak. I find they are as good as the .deb version. Just a fast. The applications do need to have the supporting runtimes installed which will take up additional space. But the runtimes are shared, so many Flatpak applications can use the same runtime. 

On an LTS install, which can be used (with Pro support) for 10 years, you may want newer versions of some software at some point. Flatpak is the answer to that. 

At some point in your Linux education, I suggest you look into Flatpaks. Full explanations of everything Flatpak can be found on the Internet. For example, [Flatpak.org]("https://flatpak.org/")

I pick Flatpaks over Snaps, but I do use the Firefox snap in Ubuntu. It used to be slow in launching, but no more. In some cases, a snap package may be the only way to get something. I would use it if that were the case.

---

### Post by joepesci2 on 2024-11-09
> **guiverc said:**
> I'm not sure what you're after... My posts says I'm on the *development* release, which most of the time is Lubuntu... The *development* release is where all work occurs, and thus it changes regularly, and things can go wrong, meaning problems can be encountered, which is why it's referred to as ***unstable***.

I update my system at least three times per day, thus hoping I get fewer updates on any particular update, as if problems occur, I have fewer packages to explore as to the possible cause. I'm currently running Lubuntu 25.04 with the [LXQt 2.1 desktop]("https://lxqt-project.org/release/2024/11/05/release-lxqt-2-1-0/"), the desktop itself was only packaged about three days ago in this case, though thus far I've not noticed any problems.

In my example, on reboot I noted two of my five displays were black in that they were getting no images from the PC... three of the displays connected to one video card were still working, but the two connected to one card were gone.  As my updates get packages BEFORE the daily ISOs are created, I waited until those packages I was running hit the next *daily* ISO, and tested it on a newer zsync'd (or updated) ISO, the reason for this was that my own machine had my own configs that were heavily modified, where the *daily* ISO contained none of those modified configs... so when it encountered the same issue, I knew it was related to changed code & not my configs...

In the following days, the problem continued; however in time the *daily* ISOs no longer had the issue when booted on my hardware, but my installed system was still suffering with only three of my five displays functional... so I went search for what was different (hadn't updated etc) on my installed system versus the newly built ISOs I was testing when I tried the daily ISOs... After a number of days looking for it, I wanted my system back to fully-operational, so gave up looking & just re-installed the system, meaning the issue was overwritten by a new install.

The install was described in the link I provided, ie. 

- the installer notes my installed packages (those the system marks as '*manually-installed*', or those I'd installed myself)
- erase system directories
- installs the system from the installation media
- then downloads the noted earlier 'manually installed' packages I had on my system from Ubuntu repositories (ie. *why I prefer using Ubuntu repository software*)
- asks me to reboot; all of which did NOT alter any config/data file on my system...

ie. on reboot; my expectation is my system operates just as it did before; as if nothing occurred...  Sure if I go look in `/var/log/installer/mediainfo` it'll show the install media wasn't whatever ISO I'd originally used, but showed the date I mentioned (20230829 OR 29th August daily), and the dates of files in the system directories all show the day/time I re-installed, ie. metadata on the file-system & some system files show a new install, but as far as I'm concerned the system acts as if it wasn't re-installed; but my wanted aim was I would have 5 displays back functional - which is what I got...

The re-install did not require me to touch any of my backups, nor restore any file...  I achieved what I wanted; a *non-destructive *re-install of the system, in effect all system code was erased & replaced by code from the ISO I'd installed from, or re-downloaded from Ubuntu repositories, and none of my configs/data was touched.

If you're wanting to understand it; I'll suggest you re-read the *askubuntu* link I provided, or if you need more, follow the link there back to a Lubuntu testcase exploration, as it was a testcase Lubuntu tested for from 19.04 thru 24.04, and in the Lubuntu link I tried to explain it for other Quality Assurance testers.

Hi guiverc! You can be sure that i will listen to you and read carefully and with interest what you have told me.
Thank you very much for sharing your experience and information.

---

### Post by joepesci2 on 2024-11-09
> **Dennis N said:**
> Yes and more software is now being packaged by their developers only in a "universal" format such as Flatpak. To have a .deb or .rpm package, a human maintainer must be found.

Personally I use quite a few Flatpak. I find they are as good as the .deb version. Just a fast. The applications do need to have the supporting runtimes installed which will take up additional space. But the runtimes are shared, so many Flatpak applications can use the same runtime. 

On an LTS install, which can be used (with Pro support) for 10 years, you may want newer versions of some software at some point. Flatpak is the answer to that. 

At some point in your Linux education, I suggest you look into Flatpaks. Full explanations of everything Flatpak can be found on the Internet. For example, [Flatpak.org]("https://flatpak.org/")

I pick Flatpaks over Snaps, but I do use the Firefox snap in Ubuntu. It used to be slow in launching, but no more. In some cases, a snap package may be the only way to get something. I would use it if that were the case.

Good afternoon Dennis! However, in this same thread i read comments that are not very favorable to Snap and Flatpak, this puts us in a difficult situation hahaha

What do you think?
Thank you very much for your message.

---

### Post by joepesci2 on 2024-11-09
Hi everyone. I have been trying to install both Brave browser and Obsidian.

Instructions for installing Brave:
[https://brave.com/linux/](https://brave.com/linux/)

Instructions for installing Obsidian:
[https://obsidian.md/download](https://obsidian.md/download)

As you can see, neither of them are available to install via APT, which makes me not quite sure what to do.
What do you think about this?

Honestly, given my lack of knowledge, this is all quite frustrating.
Sorry if i repeat myself too much or if these are stupid or obvious questions.
Thanks to everyone for your help.

---

### Post by 1fallen on 2024-11-09
> **joepesci2 said:**
> Hi everyone. I have been trying to install both Brave browser and Obsidian.

Instructions for installing Brave:
[https://brave.com/linux/](https://brave.com/linux/)

Instructions for installing Obsidian:
[https://obsidian.md/download](https://obsidian.md/download)

As you can see, neither of them are available to install via APT, which makes me not quite sure what to do.
What do you think about this?

Honestly, given my lack of knowledge, this is all quite frustrating.
Sorry if i repeat myself too much or if these are stupid or obvious questions.
Thanks to everyone for your help.

Nothing wrong with either of the 2 choices you show For Brave or Obsidian (appimage) 
There is no dumb questions we weren't born knowing any of this, only Dumb replies. ;)

---

### Post by joepesci2 on 2024-11-09
> **1fallen said:**
> Nothing wrong with either of the 2 choices you show For Brave or Obsidian (appimage) 
There is no dumb questions we weren't born knowing any of this, only Dumb replies. ;)

So you think the best way to run Obsidian is through an appimage?
However Brave doesnt allow this option, what would you do?

Thank you very much for your help and empathy.

---

### Post by ajgreeny on 2024-11-09
In fact, if you look more carefully at the instructions for installing Brave you will see tat you first have to add the repositories for Brave to your sources and then you do actually install it with apt.

Obsidian you will see is an appimage so is not really installed at all, it is simply a single executable file like an archive with all necessary dependencies, as already described before in this thread.

---

### Post by 1fallen on 2024-11-09
Install brave the way it was meant to be installed, you will need those instructions as presented in the link.

Those folks (Brave) know what they are doing,  and will keep you updated with fix's along with new features.

Not all PPA's are bad for our systems, but that takes time for you to get to place where you trust any outside sources you add to the mix.

The Obsidian as a debian.deb is all ready discussed very well here. :)

---

### Post by joepesci2 on 2024-11-09
> **ajgreeny said:**
> In fact, if you look more carefully at the instructions for installing Brave you will see tat you first have to add the repositories for Brave to your sources and then you do actually install it with apt.

Obsidian you will see is an appimage so is not really installed at all, it is simply a single executable file like an archive with all necessary dependencies, as already described before in this thread.

> **1fallen said:**
> Install brave the way it was meant to be installed, you will need those instructions as presented in the link.

Those folks (Brave) know what they are doing,  and will keep you updated with fix's along with new features.

Not all PPA's are bad for our systems, but that takes time for you to get to place where you trust any outside sources you add to the mix.

The Obsidian as a debian.deb is all ready discussed very well here. :)



My question came because in this same thread many colleagues have commented that its not advisable to add external repositories to the official Ubuntu ones.
They have also recommended installing .deb packages directly.

Obviously im a real novice in all this and i like to listen to and follow the advice of experts.
But im a bit dizzy with so much information.
I hope you will excuse my repetition.

Thank you very much.

---

### Post by 1fallen on 2024-11-09
My question is Do you trust the folks that created Brave? >>> I do!

It's all about trust I run 3 or PPA's for many years now, BUT I became familiar with them read about them (the one I add that is) some are poorly maintained so they they help in adding a mistrust if you will.

A slow row is advisable until you get your sea legs underneath you.....Just takes time.

---

### Post by joepesci2 on 2024-11-09
> **1fallen said:**
> My question is Do you trust the folks that created Brave? >>> I do!

It's all about trust I run 3 or PPA's for many years now, BUT I became familiar with them read about them (the one I add that is) some are poorly maintained so they they help in adding a mistrust if you will.

A slow row is advisable until you get your sea legs underneath you.....Just takes time.

I understand what you mean.
But beyond your answer, this is where the core of my thread is.
Im clear that apt is the best, the safest, the least corrupt.
But many programs are not in APT, if everything else (snap, flatpak, .deb...) has some disadvantage, isnt this a huge handicap for Linux?

It isnt a malicious question, its a sincere question with total humility.

---

### Post by Dennis N on 2024-11-09
> **joepesci2 said:**
> I read comments that are not very favorable to Snap and Flatpak, this puts us in a difficult situation hahaha
What do you think? Thank you very much for your message.
I don't see the difficulty. Usually you stick to the Ubuntu repository software for most applications which are installed with your installation, or added later using the App Center, Gnome Software, by a terminal command, or the venerable Synaptic Package Manager. 

You may not need anything else, but eventually you will read about an application you might want to try and use, but there is no .deb file yet and may not be for a long time if ever. So you use one of the other package types - Flatpak, Snap, AppImage. Or you may just want a newer version of an application than the one provided with your installation. 

Do some investigation outside of this forum. Ask Google "What are the pros and cons of using flatpak applications?"  You get a generated summary, plus a lot of links to visit. Spend some time reading. And try a few Flatpaks yourself for a while, then decide.

---

### Post by joepesci2 on 2024-11-10
> **Dennis N said:**
> I don't see the difficulty. Usually you stick to the Ubuntu repository software for most applications which are installed with your installation, or added later using the App Center, Gnome Software, by a terminal command, or the venerable Synaptic Package Manager. 

You may not need anything else, but eventually you will read about an application you might want to try and use, but there is no .deb file yet and may not be for a long time if ever. So you use one of the other package types - Flatpak, Snap, AppImage. Or you may just want a newer version of an application than the one provided with your installation. 

Do some investigation outside of this forum. Ask Google "What are the pros and cons of using flatpak applications?"  You get a generated summary, plus a lot of links to visit. Spend some time reading. And try a few Flatpaks yourself for a while, then decide.

Hi Dennis, how are you?
For you, these may be silly or simple questions, but for me, as a new Linux user, they are more complicated and difficult questions.
Im not saying this with any malice, i just wanted to clarify this and apologize if im being very repetitive.

My questions come from the fact that, thanks to the help and colleagues on the forum, i have understood that installing outside of APT has its complications and contraindications, so its always advisable to install from APT.
And as i said before, that's where the problem comes in, when a software isnt in the APT repository.
I wouldnt like to try any apt hell, or any similar problem.

Anyway, as you said, i will read more information about FLATPAK, APPIMAGE, etc.

Thank you very much for your help and messages.
I hope you understand my newbie questions. Greetings!

---

### Post by Dennis N on 2024-11-10
> My questions come from the fact that, thanks to the help and colleagues on the forum, i have understood that installing outside of APT has its complications and contraindications, so its always advisable to install from APT.
yes, the Ubuntu Repositories are usually the 1st option. In years of use, I haven't had any noteworthy problems or concerns from installing and using Flatpaks. The links I gave lay out the pros and cons for you. You then need to see for yourself and decide. Would you buy a used car without a test drive?

---

### Post by joepesci2 on 2024-11-10
> **Dennis N said:**
> yes, the Ubuntu Repositories are usually the 1st option. In years of use, I haven't had any noteworthy problems or concerns from installing and using Flatpaks. The links I gave lay out the pros and cons for you. You then need to see for yourself and decide. Would you buy a used car without a test drive?

You are right and i understand what you mean.
I will definitely investigate and try things out.
I will also have to use a .deb for some software, because there isnt APT installation or alternative through Flatpak or Snap, so i will have to download the .deb from the manufacturers official website.

Thank you very much for your time and help.

---

### Post by Dennis N on 2024-11-10
> I will also have to use a .deb for some software, because there isnt APT installation or alternative through Flatpak or Snap, so i will have to download the .deb from the manufacturers official website.

Realize that:

A .deb file NOT from the Ubuntu Repository may not install on your system because the dependencies are not available in the Ubuntu repository or are not the correct version needed. This is more likely if your Ubuntu is older, like 20.04.

The Apt Center should be in a minimal install. I did a minimal install of Ubuntu 24.04 and it was included. It is a snap package, so you should already have your first snap. The newest App Center version is supposed to install .deb files for you. I haven't tested that out. 

About AppImages: AppImages are not 100% self-contained. They also rely on libraries that the packager assumes will be on any Linux distro. For example, my AppImage of LibreOffice will not run on Ubuntu as-is, because the libfuse2 library is needed and not included. Once you install that, it works.

---

### Post by hifron on 2024-11-10
some appimages could be automatically refreshed upon start(electron build could do that) and there are also unofficial apps with GUI for that, but maybe electron needs gateway addons like stripe to its app-menus so donations or other methods could be more easy to monetize according salesman or appmaker choice or sales policies acquired or delegated.

But problem is also there is some service needed for check-in for problems with appimages or refuse to install, download or update them(from where(and with own hosting?)) and that's not so common with provider selection for that if any or some policies built-in...

I cannot simply make download all packages and verify them with some service of my choice or delegate it for some consumer association...

and therefore there is no matlab in flathub or snap or appimage... or any commercial viable product... or any .deb with clickable install with deb repo automatically added because making server with such repo is headache, but maybe not so hard to implement, but maybe hard to admin or hard to invent outside debian world :)

---

### Post by joepesci2 on 2024-11-13
> **1fallen said:**
> Nothing wrong with either of the 2 choices you show For Brave or Obsidian (appimage) 
There is no dumb questions we weren't born knowing any of this, only Dumb replies. ;)

> **ajgreeny said:**
> In fact, if you look more carefully at the instructions for installing Brave you will see tat you first have to add the repositories for Brave to your sources and then you do actually install it with apt.

Obsidian you will see is an appimage so is not really installed at all, it is simply a single executable file like an archive with all necessary dependencies, as already described before in this thread.



Good afternoon! Im taking advantage of this thread to ask you a question regarding the installation of Brave or any other app that needs to add a repository.

Once i add the repositories and install Brave, i must keep those repositories so that it continues to apply updates, etc. Right?
If i delete them once Brave is installed, i assume it wont update anything, is that correct?


And i would also like to know if there is any way to know which repositories to trust.
For example, we know that Brave is something serious and there isnt much doubt in its repositories, but is there any tip or trick to be more secure?

Thank you very much for your help and your time.

---

### Post by ian-weisser on 2024-11-13
> **joepesci2 said:**
> 
Once i add the repositories and install Brave, i must keep those repositories so that it continues to apply updates, etc. Right?
If i delete them once Brave is installed, i assume it wont update anything, is that correct?


That is accurate. Kudos for understanding the difference between a software package vs. the source of that package.

> **joepesci2 said:**
> 
And i would also like to know if there is any way to know which repositories to trust.
For example, we know that Brave is something serious and there isnt much  doubt in its repositories, but is there any tip or trick to be more  secure?


Trust is always a personal judgement. You must investigate a source and decide for yourself if you trust their software on their system.
You are already doing it: You trusted Ubuntu enough to try it. You trust us enough to ask our advice.

Security is a set of good habits.

---

### Post by joepesci2 on 2024-11-13
> **ian-weisser said:**
> That is accurate. Kudos for understanding the difference between a software package vs. the source of that package.



Trust is always a personal judgement. You must investigate a source and decide for yourself if you trust their software on their system.
You are already doing it: You trusted Ubuntu enough to try it. You trust us enough to ask our advice.

Security is a set of good habits.


Hi Ian! Im learning step by step. :lolflag:

And i understand what you mean, you should always analyze the repositories you want to add and where they come from.
Make sure they are trustworthy and offer guarantees, such as Flatpak/Flathub, Brave, etc.

Thank you very much for your contribution.

---

### Post by 1fallen on 2024-11-13
> **ian-weisser said:**
> 
Security is a set of good habits.

Very well said....:KS
We can be our own worst enemy.

---

### Post by joepesci2 on 2024-11-13
> **1fallen said:**
> Very well said....:KS
We can be our own worst enemy.

I totally agree.

At first i didnt know or trust Flathub at all, for example.
But after doing some research and reading your opinions, i think its a reliable repository and you can add without any problems.
As long as you install verified applications and those whose developers are verified.

Thank you very much for your contribution.

---

### Post by 1fallen on 2024-11-13
Thanks for being a part of the community!

---

### Post by joepesci2 on 2024-11-13
> **1fallen said:**
> Thanks for being a part of the community!

Thank you all for all your help!

---

