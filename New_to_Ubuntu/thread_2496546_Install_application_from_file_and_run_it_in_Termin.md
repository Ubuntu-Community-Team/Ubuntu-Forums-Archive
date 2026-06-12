---
title: "Install application from file and run it in Terminal"
date: 2024-04-02
forum: New to Ubuntu
---

### Post by danielkotzer on 2024-04-02
[COLOR=#0C0D0E][FONT=-apple-system][FONT=var(--theme-post-body-font-family][FONT=inherit]I'm new to Ubuntu, and I want to install blender on Linux from *.tar.xz file I have downloaded from the blender.org, but I just can't make it work. If I install blender from the Repository, it works but it is an older version - 3.6.2. I have noticed that when you install the blender package from the repository, the main files are copied to /usr/shared/blender, the shortcut file - blender.desktop is placed in /usr/shared/applications and the file the execution file is placed in /usr/bin/ so it seems you can't just uncompressed the *.tar.xz to /usr/local/blender and double click the shortcut file, yet the instruction for installing on Linux, on Blender.org are to uncompressed it to usr/local/.[/FONT]
[FONT=inherit]I have 2 questions but they might be interrelated:[/FONT]

[LIST=1]
[*]What should I do to make version 4 installed from the downloaded file it work by clicking on the shortcut file, like it works when I install blender from the repository?
[*]Even the version I installed from the repository will not run from the Terminal with ./blender, or /usr/bin/blender, even though it does run by double clicking /usr/bin/blender file, or the blender.desktop file, so it is not missing dependencies, so if I want to run it from Terminal with command line, what should I do?
[/LIST]
[/FONT]
[/FONT][/COLOR]

---

### Post by Dennis N on 2024-04-02
/usr/bin is a location automatically searched for applications, so you just type **blender** in the terminal and it should start.

---

### Post by danielkotzer on 2024-04-03
Hi,
I open a Terminal window and try all these commands:
blender
./blender
./usr/bin/blender
/usr/bin/blender

all I get is: "no such file or directory"
though a file by the name blender is in /usr/bin/ and if I double click it with the mouse not in Terminal it runs the blender app fine.

so I open a Terminal window from within the folder /usr/bin/ where the file is located, and run ./blender, I get this message:
error while loading shared libraries: libdl.so cannot open shared object no such file or directory.

so you might think a library is missing -- a dependency is missing, but then why does the app run if I double click the shortcut, or the execution file in usr/bin/ ?? it is the same system, with the same libraries installed, and the installation was from the Repository, so it was done automatically the way it should be, why would anything be missing?

---

### Post by coffeecat on 2024-04-03
Support, not chat. *Thread moved to **New to Ubuntu** sub-forum.*

---

### Post by ActionParsnip on 2024-04-03
What is in the newer version that you need over the 3.6.2 version?

---

### Post by Impavidus on 2024-04-03
For most software, the version is frozen when the corresponding version of Ubuntu is released. So Ubuntu 23.10 has Blender 3.6 and Ubuntu 24.04 will have Blender 4.0. It's expected to be released this month; you can install it already, but it's not guaranteed to be entirely stable.

Blender 4.0, as distributed directly from the website, may have different dependencies than version 3.6 as distributed from the Ubuntu repos. It depends on how it was compiled. I don't see a libdl.so in the repos for 23.10 or 24.04.

/usr/local/ is the proper place to install things manually.

---

### Post by Dennis N on 2024-04-03
The archive is **blender-4.1.0-linux-x64.tar.xz**
probably sitting in Downloads.

What I would try:

I would first extract the contents of the archive (to Downloads).

The result should be a folder named **blender-4.1.0-linux-x64** 

Copy that folder to **/usr/local/bin**. Steps:
In terminal cd to Downloads, then
```
sudo cp -r blender-4.1.0-linux-x64 /usr/local/bin
```
Then open **/usr/local/bin/blender-4.1.0-linux-x64** in Files (the file manager), double click on **blender** and see if it starts.

---

### Post by danielkotzer on 2024-04-04
4.0.2
but the point is not the new version as much as it is the fact that I can only install from the repository, I want to be able to install from file.

---

### Post by danielkotzer on 2024-04-04
> **Dennis N said:**
> The archive is **blender-4.1.0-linux-x64.tar.xz**
probably sitting in Downloads.

What I would try:

I would first extract the contents of the archive (to Downloads).

The result should be a folder named **blender-4.1.0-linux-x64** 

Copy that folder to **/usr/local/bin**. Steps:
In terminal cd to Downloads, then
```
sudo cp -r blender-4.1.0-linux-x64 /usr/local/bin
```
Then open **/usr/local/bin/blender-4.1.0-linux-x64** in Files (the file manager), double click on **blender** and see if it starts.

I did it but still getting the error when double clicking the blender executable file, or the shortcut, file or directory not found, after it asks me if I want to make it executable and I say yes but then comes the error again.

---

### Post by danielkotzer on 2024-04-04
> **Impavidus said:**
> For most software, the version is frozen when the corresponding version of Ubuntu is released. So Ubuntu 23.10 has Blender 3.6 and Ubuntu 24.04 will have Blender 4.0. It's expected to be released this month; you can install it already, but it's not guaranteed to be entirely stable.

Blender 4.0, as distributed directly from the website, may have different dependencies than version 3.6 as distributed from the Ubuntu repos. It depends on how it was compiled. I don't see a libdl.so in the repos for 23.10 or 24.04.

/usr/local/ is the proper place to install things manually.
OK I can wait for the new version of ubuntu, but I would like to be able to install from file, also I would like to be able to run applications from Terminal. I am slowly moving from windows, and want to know how to work with Ubuntu just as I was working with Windows.

---

### Post by Dennis N on 2024-04-04
> **danielkotzer said:**
> OK I can wait for the new version of ubuntu, but I would like to be able to install from file, also I would like to be able to run applications from Terminal. I am slowly moving from windows, and want to know how to work with Ubuntu just as I was working with Windows.

O.K, other suggestions: I think either of these will work for you and be ready to use after install.

(1) Install blender as a snap application. You get version 4.1, like the downloaded version.
```
sudo snap install blender
```

(2) You can also Install blender as a Flatpak application. You also get version 4.1
Before you can use a Flatpak, you need to install Flatpak support for Ubuntu.  See directions at [Setup Flatpak]("https://flathub.org/setup")
Once it's setup, install blender with:
```
flatpak install flathub org.blender.Blender 
```

Continue to post #13 **&#8595;** where I tested installing the downloaded blender-4.1.0-linux-x64.tar.xz file.

---

### Post by Impavidus on 2024-04-05
You can download some executable on Linux and install it, like the normal method on Windows, but on Linux that's considered the method of last resort. Or second last, before compiling from source. It's harder, you have to handle dependencies and upgrades manually, there are no rules so you have to understand how Linux works before you can do it comfortably, there's more risk of malware. That's a big difference between Linux and Windows. I suggest you get used to it.

The preferred method to install applications is from the official repositories. In the past that was only deb packages, now there are other styles too. The snap packages have been mentioned. Those tend to be more recent and have no (or at least few) dependencies, but are significantly locked down, inefficient in disk space use or download size and slow to start. There's also flatpak. Deb packages are more efficient in disk space than your typical Windows program. I stick to deb packages, but the people behind Ubuntu push snap. Then you can add third-party repositories (people often talk about PPAs); less secure, but still with automatic updates. Only after that come executables downloaded from websites and compiling from source.

---

### Post by Dennis N on 2024-04-05
I followed my own proposed steps in post #7 and Blender launched as expected with a double-click. So that should work if done as shown.

Now, to get a launcher for the program:

The included .desktop file isn't going to work without these changes:

1) copy the desktop file provided with the application to ~/.local/share/applications

2) add symbolic link named 'blender' in /usr/local/bin to target the real executable in the blender-4.1.0-linux-x64 folder.
How to make the symbolic link:
In terminal, cd to /usr/local/bin
Run this command:
[FONT=Courier New]sudo ln -s blender-4.1.0-linux-x64/blender blender[/FONT]

3) copy the blender.svg file to /usr/share/icons

Now blender appears in the Activities Overview (see image) and also in the Applications Menu under Graphics.

Any questions?

---

### Post by MAFoElffen on 2024-04-05
I don't get it.

Members have explained in details, the expanded understanding of these instructions: [https://docs.blender.org/manual/en/latest/getting_started/installing/linux.html](https://docs.blender.org/manual/en/latest/getting_started/installing/linux.html)

Also from their own instructions, they mention that the best, and easiest way to install Blender is to install it from the Distribution Repo's, and their own reasoning why that is "best":
> 
Install from Package Manager

Some Linux distributions may have a specific package for Blender in their repositories.

Installing Blender via the distribution&#8217;s native mechanisms ensures consistency with other packages on the system and may provide other features (given by the package manager), such as listing of packages, update notifications and automatic menu configuration. Be aware, though, that the package may be outdated compared to the latest official release, or not include some features of Blender. For example, some distributions do not build Blender with Cycles GPU rendering support, for licensing or other reasons.

If there is a specific package for your distribution, you may choose what is preferable and most convenient, otherwise, the official binary is available on blender.org.

That seems fairly straight forward.

---

### Post by danielkotzer on 2024-04-06
> **Dennis N said:**
> I followed my own proposed steps in post #7 and Blender launched as expected with a double-click. So that should work if done as shown.

Now, to get a launcher for the program:

The included .desktop file isn't going to work without these changes:

1) copy the desktop file provided with the application to ~/.local/share/applications

2) add symbolic link named 'blender' in /usr/local/bin to target the real executable in the blender-4.1.0-linux-x64 folder.
How to make the symbolic link:
In terminal, cd to /usr/local/bin
Run this command:
[FONT=Courier New]sudo ln -s blender-4.1.0-linux-x64/blender blender[/FONT]

3) copy the blender.svg file to /usr/share/icons

Now blender appears in the Activities Overview (see image) and also in the Applications Menu under Graphics.

Any questions?

I did everything you said, created a [COLOR=#000000]symbolic link, [/COLOR]but it will not work. 
Maybe my termux x11 proot-distro works different, though it runs blender from the repository of ubuntu when I double click it, it will not run the one I extract from file I downloaded from blender.org
and it will not run on Terminal. And snap and [COLOR=#000000][FONT=&quot]flatpak don't work on proot-distro
[/FONT][/COLOR]I really want to know how to install it because if I can't use [COLOR=#000000]*Cycles GPU rendering, and I want to have the latest version*[/COLOR]

---

### Post by Dennis N on 2024-04-06
> Maybe my termux x11 proot-distro works different
Sorry, I'm not familiar with this other than it is an android thing. Since everything you tried has failed, you may be correct in that it's something you can't do on your system.

---

### Post by TheFu on 2024-04-09
> **danielkotzer said:**
> OK I can wait for the new version of ubuntu, but I would like to be able to install from file, also I would like to be able to run applications from Terminal. I am slowly moving from windows, and want to know how to work with Ubuntu just as I was working with Windows.

Linux and Windows are completely different OSes.  *The Linux way* is different.  In general, downloading unpackaged programs outside the normal repos is not a beginner task. It can lead to all sorts of issues that don't become apparent for months.  

The same applies to downloading random .deb files, then force installing those, outside the repos for your specific version of Ubuntu.  In 3-6 months, you'll likely have an OS that cannot be patched due to dependency issues.

As you learn more and more, you'll better understand the installation instructions from the different software project teams.  Most of the time, they have an installer tool/script included with their distribution files.  I haven't looked at Blender in about a decade, so I don't know what their install or README says to do.  I'd be surprised if they expect you do copy individual files or directories around.  That wouldn't be very "linux-like".

However, every software project can create their own setup and install process, if they like. There's no single standard, once we step away from the normal Repos provided by Canonical.  There are a few more popular methods using a toolset called **autoconfig**.  This is mostly used by mature software project teams with code written in C or C++.  Different coding languages have their own local installation methods.  Python does it different from Java, which is different from NodeJS and Perl and Ruby.

All these non-Repo methods come with responsibilities since they effectively break/ignore the standard Ubuntu Repos, which will patch all applications, settings, programs, and the OS with 1 command.  This has been a key reason why I choose to run Ubuntu.  Easy patching that I get to control when it happens or I can prevent, when needed.

Before I consider getting a new version of any software, I consider how badly I need it and how it might break system stability and maintenance.  There's a hierarchy of my preferred installation types, based on what integrates and requires the least future effort and avoids future problems.  All new users seem to think a setup.exe is the best option. It isn't.  It is just about the worst option, actually.  With a setup.exe (or similar), the admin now has to look for updated versions of all software they install that way every time they patch.  I patch weekly.  If I allowed software like that to be installed at all, even just a few would become too much work to correctly maintain.  I'll stick with the repo version.

The very last way I want to install any software on any of my systems is by downloading source packages, setting up all the different external dependencies, compiling, linking, building documentation, interfaces,  and finally manually installing.  I certainly don't want to do that every week or even every month.  No thanks.

---

