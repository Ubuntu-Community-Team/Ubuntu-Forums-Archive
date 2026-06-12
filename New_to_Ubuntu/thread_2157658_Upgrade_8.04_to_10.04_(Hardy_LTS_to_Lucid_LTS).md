---
title: "Upgrade 8.04 to 10.04 (Hardy LTS to Lucid LTS)"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by ollie5 on 2013-06-26
Hi,

I trying to upgrade from Ubuntu 8.04 Hardy to 10.04 Lucid.

I followed the guide found here - [https://help.ubuntu.com/community/EOLUpgrades/Hardy](https://help.ubuntu.com/community/EOLUpgrades/Hardy) - using the gnome terminal to initiate the upgrade.

However at the end of the process is just said 'No new release found'.

Can anyone help with steps to achieve the upgrade?  Is 10.04 the right upgrade to make or should I be upgrading to a newer version?

Thanks

---

### Post by kurt18947 on 2013-06-26
10.04 desktop is not longer supported, supported ended in April of this year.  Most people are pretty happy with 12.04 it seems as long as their hardware is up to the task. If a machine can run Windows XP well, it can run 12.04.  Xubuntu and Lubuntu also have followings who prefer more traditional desktops and may have older or less capable hardware.

---

### Post by Zill on 2013-06-26
ollie5:  Are you running the Desktop or the Server version?

If you are running the Desktop version then both 8.04 and 10.04 are both end-of-life and are no longer supported.

However, if you are running the Server version then 8.04 reached end-of-life on May 9, 2013 and 10.04 will reach e-o-l in April 2015.

So, while you *could* upgrade 8.04 to 10.04 *if* you are running the server version, you will only have a short period until you need to upgrade again.

With both Desktop and Server versions, the best advice is to do a "clean" upgrade directly to the current LTS (12.04) which will be supported until April 2017.  There have been many changes since 8.04 and so upgrading to 12.04 *via* 10.04 will likely cause many problems that will be eliminated with a "clean" install.

See [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by ollie5 on 2013-07-03
Thanks for the advice kurt18947 and Zill, 

So I tried performing the clean upgrade to 12.04 using the guide here - [https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade) - but had some problems.

First of all, the stages 'Remove obsolete packages' and 'Remove third party packages' - I marked the relevant packages as 'mark for complete removal' but every single one came up with the error message 'files list file for package `libxcb-shape0' is missing final newline'.  I tried doing them in a batch and just individually but either way it came up with that same error message.  So I was unable to remove any of the packages that the guide said should be removed.

Then the penultimate stage - 'perform the upgrade' - according to the synaptic package manager, the current version of Ubuntu I have installed is 1.102belmont3 and it says that that is the latest available version. So according to the synaptic package manager there is no upgrade?

Can anyone help, what can I do to achieve this upgrade?  Or is it possible to put 12.04 on a DVD and install it from there?  

Thanks

---

### Post by Zill on 2013-07-03
Firstly, it would be useful if you would advise if you are using the Desktop or the Server version.  In both cases, before attempting any upgrade, *always* ensure that you have good backups of your data saved away from the system being upgraded.  Things can (and do!) go wrong when performing major system surgery and so good backups are *essential*.
> **ollie5 said:**
> ...So I tried performing the clean upgrade to 12.04 using the guide here - [https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade) - but had some problems...
My apologies but my reference to a "clean upgrade" may have confused things slightly as I actually meant a "clean install".:oops:  This means that a new system is installed from scratch, ensuring that all your old config files etc automatically get deleted when the / directory is reformatted.  As *many* things have changed since 8.04 this really is the best solution.  You will then need to reconfigure your new system with your preferences and restore your backed-up data.
> **ollie5 said:**
> ...Can anyone help, what can I do to achieve this upgrade?  Or is it possible to put 12.04 on a DVD and install it from there?
To recap, backup your existing data and then download your required Desktop or Server iso from [http://www.ubuntu.com/download](http://www.ubuntu.com/download).  Check the [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") of your downloaded file *exactly* matches that in the [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes") list.  This ensures that your downloaded file is not corrupted.

Once you know you have a good download you can then burn this to DVD (or a USB stick) and boot from this.  I suggest you [Try Ubuntu before you install it]("http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install") as this will ensure that your hardware is compatible with this version of Ubuntu.  Note that that system requirements for the latest Ubuntu Desktop releases are far higher than those for 8.04 Hardy!

If all goes well then you can then proceed with [installing Ubuntu from the Live DVD]("http://www.ubuntu.com/download/desktop/install-desktop-latest").

---

### Post by mardybear on 2013-07-04
> **ollie5 said:**
> Hi,

I trying to upgrade from Ubuntu 8.04 Hardy to 10.04 Lucid.

I followed the guide found here - [https://help.ubuntu.com/community/EOLUpgrades/Hardy](https://help.ubuntu.com/community/EOLUpgrades/Hardy) - using the gnome terminal to initiate the upgrade.

However at the end of the process is just said 'No new release found'.

Can anyone help with steps to achieve the upgrade?  Is 10.04 the right upgrade to make or should I be upgrading to a newer version?

Thanks
Earlier this year i used my very old dapper installation CD to install dapper and then used Ubuntu's online repositories to upgrade jump from dapper to hardy and then again from hardy to lucid. So it is possible, although not likely recommended for a newbie. FYI - the system runs good and stable. I just wanted you to know it is possible - my notes are pasted below. As mentioned by another post, a fresh install of 12.04 is probably best though, since it's supported for quite some time. Personally, me still likes my old 10.04 systems best.

Good luck,

Marty

***************************************************

Install Marty's dapper 6.06 cd onto the hard drive like normal

To update the packages, which will then allow the update manager to show an upgrade to 8.04 hardy heron upgrade, add the following repository locations to etc/apt/sources.list:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted (or maybe just ...archive.ubuntu.com... - test and see)
deb-src-http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

....or try changing default sources.list pathways to 'old-releases' or 'archive'

****************************************************

When an Ubuntu release goes end-of-life, the repositories are moved to the old-releases.ubuntu.com server. So if you wish to continue (highly un-recommended due to the complete lack of security patches and bug fixes!) you can edit your software sources:

Code:

gksu gedit /etc/apt/sources.list

Change all of your software sources to [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)... for example change this:

Code:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main

to this:

Code:

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) lucid main

Doing so will allow you to install outdated and unsupported software from the outdated and unsupported end-of-life repositories.

******************************************************

additional helpful thread:

[http://ubuntuforums.org/showthread.php?t=1822086](http://ubuntuforums.org/showthread.php?t=1822086)

*******************************************************


How to upgrade post-end-of-life Dapper to Hardy

    Hey all,

    I'd seen a couple of people groaning that after Dapper went end-of-life they couldn't upgrade to Hardy. I just managed to work around this and get Dapper upgraded, so I'll document the required tricks here. These details might perhaps want to go in the EOLUpgrades wiki page.

    The problem
    -----------

    If you follow the instructions at [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) to upgrade Ubuntu 6.06 (Dapper) to 8.04 (Hardy), with /etc/apt/sources.list set only to refer to the old-releases server, the do-release-upgrade command will fail with the error "Getting upgrade prerequisites failed". This is because it believes being able to access dapper-backports at archive.ubuntu is vital to be able to upgrade.

    Even if sources.list does not mention archive.ubuntu.com this dependency will be re-inserted by the Hardy upgrade scripts and the upgrade will fail.

    The solution
    ------------

    DISCLAIMER: I've tried this trick on exactly *one* machine. Back up first.

    We must do two tricks to make the upgrade go right:

    1. Make sure the Hardy update script looks to old-releases.ubuntu.com instead of archive.ubuntu.com.

    2. Ensure that Hardy can get its packages during the upgrade; these *will* come from archive.ubuntu.com.

    The first trick is most difficult. When we run do-release-upgrade, the first thing it does is download the hardy upgrade scripts and run those. Run do-release-upgrade and watch it fail. Then do an ls -l in /tmp. You should find a very recently created directory with a random-looking name. If it contains a file called 'hardy', bingo -- this is where the Hardy scripts were downloaded.

    Supposing the hardy scripts were put in /tmp/aaaaaa. Edit /tmp/aaaaaa/prerequists-sources.dapper.list and change archive.ubuntu.com to old-releases.ubuntu.com.

    The second trick is we must have lines in /etc/apt/sources.list for *both* archive.ubuntu.com AND old-releases.ubuntu.com. This is because the update script will make an initial hardy sources list using this as a reference, just swapping out 'dapper' for 'hardy'. Dapper is only on old-releases, and hardy is only on archive, so we need to mention both so it works both before and after.

    With all this done, we kick off the upgrade by running:

    cd /tmp/aaaaaa (replacing 'aaaaaa' with the path the hardy scripts ended up in)
    ./hardy --mode=server --frontend=DistUpgradeViewText

    Hope this helps stragglers like me get their ancient distros somewhere near the present decade

    Chris 


***********************************************

 Re: How to upgrade post-end-of-life Dapper to Hardy

    @smowton, thanks for posting this workaround. It needs a couple of amendments to work with the desktop version of Dapper, so I thought I'd post these.

    1 - "sudo do-release-upgrade" fails with a "command not found" error. Which is interesting because do-release-upgrade is included in the desktop version of Natty that I'm posting from. It must only come with the server version of Dapper. I couldn't find which package the do-release-upgrade script comes with so that I could install it. Instead I opened update-manager which prompted me with "8.04.1 LTS is available". Clicking on upgrade started the upgrade process which predictably failed, but it produced the /tmp/tmp*** folder that the OP refers to and I was able to edit the /tmp/tmp*/prerequists-sources.dapper.list file.

    2 - You need to sudo -i to a root shell before running the /tmp/tmp***/hardy script in a GUI terminal. Running "sudo bash...." produces a series of errors.

    3 - You need to run "./hardy --mode=desktop --frontend=DistUpgradeViewText", not "./hardy --mode=server --frontend=DistUpgradeViewText" if you are running the desktop version. If you run --mode=server on the desktop version, the upgrade gets hopelessly lost in a labyrinth of dependency problems mostly involving python packages. Guess how I discovered that! (Note to self: next time, engage brain before running posted commands. )

    I must admit that this was not on a production system. Getting tired of the kneejerk "don't upgrade; do a fresh install" type posts that appear - I see that a couple have found their way into this thread - I've been doing some experimenting. Although I prefer to fresh install each release, the upgrades I have done have been successful. A recent working Jaunty all the way to a working Natty encouraged me to start where Ubuntu started - with the Warty Warthog. But I got stuck at Dapper. Many thanks once again. 

***********************************************


Re: How to upgrade post-end-of-life Dapper to Hardy

    In case you're coming late to the game as I did, the first post in this thread is still the way to go--I went 6.04>8.04->10.4->12.01 this morning, and the only part that was nonintuitive was the double-listing in the sources.list and resuming the do-upgrade script from its /tmp directory.

    Unlike other posters, i had no trouble with UUID's or grub. I did have the 10.4 update crash out near what I think was the end, and had to manually aptitude update; aptitude upgrade to uninstall all the junk that ended up hanging around thereafter, but I have yet to see any ill effects.

    luck++; 

***********************************************

---

### Post by Bucky Ball on 2013-07-04
Doesn't matter if it is 8.04 LTS server or desktop. You are running 8.04 LTS and they're both dead. Clean install 12.04 LTS. That is your answer.

---

### Post by Zill on 2013-07-04
> **Bucky Ball said:**
> Doesn't matter if it is 8.04 LTS server or desktop. You are running 8.04 LTS and they're both dead. Clean install 12.04 LTS. That is your answer.
Except that an "older" PC happily running 8.04 Desktop may well struggle to run 12.04 Desktop due to the far higher system requirements.  OTOH, due to the lack of a GUI and the associated eye-candy, the requirements for both Server versions are unlikely to be significantly different.

---

### Post by hamishmb on 2013-07-04
Upgrade to Lucid is a bad idea due to both 8.04 and 10.04 being out of support. Even if you successfully upgraded, you'd then need to upgrade again to 12.04. 
I'd recommend fresh install ubuntu 12.04 (or Lubuntu).

---

### Post by BBQdave on 2013-07-04
> **ollie5 said:**
> I trying to upgrade from Ubuntu 8.04 Hardy to 10.04 Lucid.

I offer, given most likely your hardware age; back up your data to a seperate drive and fresh install Xubuntu 12.04LTS :)

---

