---
title: "Settings files in Home directory and installation/uninstallation of applications"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-01-24
In Windows, when installing an application, you choose where to install it, but not every file related to the program is installed in that directory (it may create data outside of the directory in specified location on the C drive, for example). When you run the uninstaller of the program, registries, files in the AppData, cache, and other "crap" are left behind, which are not only redundant and take up space, but can conflict with a newer version of the program if you want to reinstall it. Even though this is the recommended way to remove a program you don't want (for the average user), the ideal method would be to run an application designed to identify all these leftover crap of a program to be uninstalled so that the system remains clean and optimized. You *definitely *do not want to find the application folder and just delete it.

For applications installed as packages in Linux, do remove and purge commands 100% remove all files installed/pertain to the program? I know that these two commands don't remove config files in the Home directory, but are there ways to 100% remove all relevant files *including *the config files of the Home directory? (I know that Linux has no registries, but are there miscellaneous files produced during installation or are left behind outside of the application folder?

Is the best method of removing *any* manually installed applications that are not from packages (from website) to merely delete the application folder? If I specify a directory for the application to be installed in, will all files related to the application be installed in the specified directory (as opposed to installing stuff in addition locations like in Windows' AppData, etc.?). Oracle Java's website says that to uninstall JDK that is installed manually from their website you just delete the JDK directory.

Do all applications have only a single file that contains the settings of the application, either in where the application is installed or in the Home directory? Specifically, for Firefox, I configured the settings of the browser as well as the settings of the addons. If I were to reformat the root partition and leave the home partition as-is, will all the settings of the addons, open tabs, etc. stay the same? 

How to update manually installed applications (from website)? Do I have to download the newer version from the website every time, overwriting the old directory and expecting the newer version to use the settings file of the previous version?

Is it safe to remove pre-installed applications that I don't use that come with Kubuntu? Ex. instant messenger program.

Any recommendations for a powerful package manager, or is Muon for Kubuntu good enough?

---

### Post by deadflowr on 2015-01-24
That's a ton of questions, and it's best to post one.
(Simply because too many questions make it hard to know what the core question is)

But having said that 
> Do all applications have only a single file that contains the settings of the application, either in where the application is installed or in the Home directory? Specifically, for Firefox, I configured the settings of the browser as well as the settings of the addons. If I were to reformat the root partition and leave the home partition as-is, will all the settings of the addons, open tabs, etc. stay the same? 
Yes, specifically because Firefox keeps all settings per user, locally per user, inside the home folder.(inside the .mozilla folder)
(Some apps have a file for configurations and others have their own folders.)
> How to update manually installed applications (from website)? Do I have to download the newer version from the website every time, overwriting the old directory and expecting the newer version to use the settings file of the previous version?

Of course, if you manually install a package, and it does not have it's own update configuration in place, (ala it adds a ppa or it's own repo, like google-chrome does) then you would have to manually re-install the newer version. Simple as that.

---

### Post by the3dman on 2015-01-25
> **garycheng12 said:**
> 
Is it safe to remove pre-installed applications that I don't use that come with Kubuntu? Ex. instant messenger program.


Yes it is safe to remove some of the pre-installed apps like the IM software. If you don't know what the program or package does though, it would be best to look it up before removing it to make sure it is not needed.

---

### Post by garycheng12 on 2015-01-25
Thanks for the information. I am using Kubuntu and want to download qBittorrent. When i choose Linux, I have to specify a distro for the binary package (binary package is the same thing as downloading packages from repository, meaning it can be automatically updated and altered using commands like remove and purge, right?): Ubuntu, Debian, and other options are available. I know that Ubuntu is Debian-based and Kubuntu is Ubuntu-based, but do I choose Ubuntu, Debian, or just choose the source tarball (which I prefer not to do as the package manager will not include it for automatic updates) because I need a binary package specifically for Kubuntu?

---

### Post by nerdtron on 2015-01-25
Although Ubuntu and Debian uses deb packages, they are not compatible. So if you are installing software for your Kubuntu, you can download the Ubuntu deb package. It will also work for Kubuntu since Ubuntu and Kubuntu are the same (just different GUI).

Be sure to download the correct deb package for your current version, i.e. 14.04 or 12.04 deb package.

Also, why do you need to manually download a package? Is it not available from the software center?

---

### Post by deadflowr on 2015-01-25
> **garycheng12 said:**
> Thanks for the information. I am using Kubuntu and want to download qBittorrent. When i choose Linux, I have to specify a distro for the binary package (binary package is the same thing as downloading packages from repository, meaning it can be automatically updated and altered using commands like remove and purge, right?): Ubuntu, Debian, and other options are available. I know that Ubuntu is Debian-based and Kubuntu is Ubuntu-based, but do I choose Ubuntu, Debian, or just choose the source tarball (which I prefer not to do as the package manager will not include it for automatic updates) because I need a binary package specifically for Kubuntu?
 
Unless the Debian package adds a 3rd party repository to your software sources, neither it nor a tarball will automatically update, or update via the update manager.
Chances are, that if you install a 3rd party deb, then it probably won't have any packages in the default repositories. And if the package isn't in the repos, then how could it update...

In terms of choosing a .deb package, some are generic; meaning they'll run on any system be it Debian, Ubuntu, mint, or other. And some are very specific; meaning not only will they only run on one system, sometimes they'll only run on one release(it might run on Ubuntu 12.04, but not Ubuntu 14.04, as an example)
So it's important to look at what it says when downloading the package, and whether it specifies a particular system or not.

(Also less important, but still important, is figuring out how old the package is. 
Over the years thousands of people have created debian packages and released them into the wild..
So there are tons of old and out-dated packages, which if you tried to install, won't.
Or if you actually could install them might not gel well with the current system design.)

Hope some of this makes sense...

Oh and also, if you are going to compile and install from source, use [checkinstall]("https://help.ubuntu.com/community/CheckInstall")
it makes maintenance easier.

---

### Post by garycheng12 on 2015-01-25
> **nerdtron said:**
> Although Ubuntu and Debian uses deb packages, they are not compatible. So if you are installing software for your Kubuntu, you can download the Ubuntu deb package. It will also work for Kubuntu since Ubuntu and Kubuntu are the same (just different GUI).

Be sure to download the correct deb package for your current version, i.e. 14.04 or 12.04 deb package.

Also, why do you need to manually download a package? Is it not available from the software center?

Coming from Windows, users have the mindset of always updating their programs to the latest version. I'm still trying to wrap my head around the idea of having applications that are more stable but generally behind that are packaged and accessed through the software center for specific distros such as Kubuntu, as opposed to manually downloading the latest version of an application from the website that is deemed to be buggier because it was not specifically designed for Kubuntu 14.04, for example.


It might be nit-picky, but there are several applications that I use that are available in both Windows and Linux and it would be awkward for the application on Windows to have a feature that is not yet (or will never be present) in the Linux version because no one packages it specifically for Kubuntu 14.04.


Not sure if this is a good mindset to have--I would be happy to be taught what kind of a mindset an experienced Linux user would have.


Thanks for the info guys, I'll look into it.

---

### Post by oldos2er on 2015-01-25
If you're new to Linux it's probably best to stick with the programs available in the repositories for now. You could open a konsole and copy/paste ```
sudo apt-get update && sudo apt-get install qbittorrent
``` As it happens there is a PPA (Personal Package Archive, a repository separate from the officially maintained ones) with somewhat newer builds of qbittorrent available: [URL="https://launchpad.net/~qbittorrent-team/+archive/ubuntu/qbittorrent-stable"]https://launchpad.net/~qbittorrent-team/+archive/ubuntu/qbittorrent-stable

[/URL]
The advantages of using a PPA are that the package will be upgraded along with system upgrades, and you can install, remove, or find out information about it through your package manager; Muon, if you prefer.

---

