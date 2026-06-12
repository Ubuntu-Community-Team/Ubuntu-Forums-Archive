---
title: "Easy way to install programs"
date: 2014-04-06
forum: New to Ubuntu
---

### Post by DreddTrekkiter on 2014-04-06
Hi peeps

Right, so I'm know my way around Windows XP pretty damn well - not to toot my own trumpet or anything - and one thing I don't like about all types of Linux - I've tried 4 types so far, and am using Lubuntu at this moment - is the complexity of installing programs that aren't in the Software Centre, for example, I'm a Java programmer and my favourite editor is Eclipse [www.eclipse.org]("http://www.eclipse.org") but Eclipse isn't on the Software Centre so I have to go to Eclipse.org and download the Linux installation pack. It downloads an archive. 

Now, I've found several different ways of installing something:

Software Centre - Sometimes it doesn't have the package I want

To download the archive and go to properties and set it to executable - It usually comes up with a message saying "Could not open archive" or something like that

To go to the terminal and use the sudo command which usually says that it can't find the file!

So could someone please tell me a hopefully foolproof way of installing a package?

Thanks in advance,

DreddTrekkiter

---

### Post by 23dornot23d on 2014-04-06
This works for me ...........

[B]sudo apt-get install eclipse-platform

[IMG]http://i.minus.com/iFlBR5V8OwuTy.png[/IMG]
[/B]

---

### Post by Warren Hill on 2014-04-06
Are you sure eclipse is not in the software centre it is in Ubuntu.  I haven't checked Lubuntu but I think it uses the same repositories so should be there.

It won't be the latest version however.  If you want the latest version see this question on AskUbuntu: 

[How to install Eclipse?]("http://askubuntu.com/q/26632/107450")

---

### Post by Ubi_one_2014 on 2014-04-06
did you go to:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

and create the sources u want?

eventually a file is created.

open a terminal, and type

sudo kate /etc/apt/sources.list, and copy the file into that, after removed all lines
save it

in a terminal, do
su - [enter]

apt-get update && apt-get dist-upgrade
[enter]

afterwards, click Y or J to apply the updates

.deb files are normally installed by
sudo dpkg -i filename.deb
[enter]

sometimes u have to do
apt-get -f install, to install dependencies

---

### Post by buzzingrobot on 2014-04-06
> **DreddTrekkiter said:**
> 
Software Centre - Sometimes it doesn't have the package I want

To download the archive and go to properties and set it to executable - It usually comes up with a message saying "Could not open archive" or something like that...


Eclipse is in the Ubuntu repositories.

In Linux, a file that ends with an extension like "...tar.gz" is an archive, and nothing else.  Traditional, typical, use is to package source code files along with generic scripts to compile that source and, if successful, copy the resulting binaries to the correct locations in the file system. While that amounts to "installation", and there is often an "install.sh" script in the archive, it is not intended for end users. (Installing binaries that way also does an end run around the software on your system that tracks what has been installed and makes things like easy updates and dependency resolution possible. That software does not know those binaries are there.)

Windows software can often be packed into a single, simple, archive that can be expanded into its own folder and executed because Windows will allow libraries and other files needed by an application -- its dependencies -- to be installed multiple times in multiple locations.  This has updating and security implications.

Linux deals with these dependencies differently.  Applications share a single copy of the file they are dependent on.  For example, when you use the Software Center application to install Application X, it knows what else Application X requires to execute successfully.  It checks your system to determine how many of those dependencies are already installed, and then it installs Application X and all its other dependencies.

Later, when you ask Software Center to install an application that requires the same dependencies as Application X, it won't install any of them, because they are already on your system.

Archives -- aka Packages -- intended for installation on Ubuntu use the file extension '.deb". If you manipulate their properties, they can be associated with an application that will install them via a click.  (Note that not all ".deb" packages are for Ubuntu.)

---

### Post by ibjsb4 on 2014-04-06
> Software Centre - Sometimes it doesn't have the package I want

Maybe you just need a better way to do a package search.  Instead of the software-center, I use [Synaptic Package Manager]("https://apps.ubuntu.com/cat/applications/synaptic/"), it shows 58 eclipse packages.

[ATTACH=CONFIG]251768[/ATTACH]

---

### Post by grumblebum2 on 2014-04-06
> **Ubi_one_2014 said:**
> did you go to:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

and create the sources u want?

eventually a file is created.

open a terminal, and type

sudo kate /etc/apt/sources.list, and copy the file into that, after removed all lines
save it

in a terminal, do
su - [enter]

apt-get update && apt-get dist-upgrade
[enter]

afterwards, click Y or J to apply the updates

.deb files are normally installed by
sudo dpkg -i filename.deb
[enter]

sometimes u have to do
apt-get -f install, to install dependencies
So you really think that's an easy way to install programs by telling a new user to overwrite **/etc/apt/sources.list** and giving a few 
code lines one of which includes kate which he probably doesn't even have installed anyway.
All your doing is causing more confusion.
:rolleyes:

---

### Post by ibjsb4 on 2014-04-06
> **grumblebum2 said:**
> So you really think that's an easy way to install programs by telling a new user to overwrite **/etc/apt/sources.list** and giving a few 
code lines one of which includes kate which he probably doesn't even have installed anyway.
All your doing is causing more confusion.
:rolleyes:

yup

---

### Post by oldos2er on 2014-04-06
> **Ubi_one_2014 said:**
> did you go to:
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

and create the sources u want?

eventually a file is created.

open a terminal, and type

sudo kate /etc/apt/sources.list, and copy the file into that, after removed all lines
save it

in a terminal, do
su - [enter]

apt-get update && apt-get dist-upgrade
[enter]

afterwards, click Y or J to apply the updates

.deb files are normally installed by
sudo dpkg -i filename.deb
[enter]

sometimes u have to do
apt-get -f install, to install dependencies

Since Ubuntu doesn't enable the root account, *su -* won't work. kate is not installed in default Ubuntu, but gedit is.

---

### Post by ChiefWOTJ on 2014-04-06
What distro are you using? Eclipse should be in the repos.  If it is not showing in the software center, you may try doing an apt-cache search by typing 'apt-cache search java | grep eclipse'.  Once you see the application you want, you can just do an apt-get install that will pull in all the required dependencies including the default JDK.

---

### Post by DreddTrekkiter on 2014-04-29
Thanks guy's, this is a lot of answers!

Firstly, I must have not been using Software Centre correctly because I've just had a look and found Eclipse(embarrassing!).

Thanks to [COLOR=#000000]23dornot23d who gave me the correct sudo command for installing Eclipse.

To grumblebum2 you're absolutely right, sorry [/COLOR][COLOR=#000000]Ubi_one_2014,  no offence, but I didn't understand a single character of what you replied with :-(

But, not to be a complainer or anything but I was using Eclipse as an example because all of this, in my Windows opinion, isn't easy.
Isn't there a thing where I can just click a button, like you do on an EXE file in Windows, and it'll install it?

I mean, I've found .deb files fairly easy but the only application I've found in one of those is Google Chrome.

As Garfield and Oliver Twist said:

Please sir may I have some more answers?

Thanks again, 

DreddTrekkiter[/COLOR]

---

### Post by jeremy1138 on 2014-04-29
I'm far from being an expert in Ubuntu but, for me anyway, the best solution to installing software that isn't in the Ubuntu repositories is to find and add a ppa that includes the software I want.  That way the program installs and updates correctly.  I have always been under the impression that this is the 'Ubuntu way'.  Is that not correct?

By the way, there are .deb files that install similarly to what an .exe install file would in windows.  I don't think these update automatically however.  Someone please correct me if I'm wrong.

[edit]
I did some checking around and apparently some .deb files will add an entry in your software sources so the program can be kept up to date.  I guess this is not always the case however.  See this:

[http://askubuntu.com/questions/190140/do-deb-installed-apps-get-updates](http://askubuntu.com/questions/190140/do-deb-installed-apps-get-updates)

---

### Post by monkeybrain20122 on 2014-04-29
Eclipse doesn't need compile or install, it comes as a binary which you can just click and use. Download from its own website, extract the tarball to your home and go into the folder and click eclipse, that's it. Can't be easier.

 You can get it from the repo but chances are it is an older version and it will bring in a lot of depenencies.

---

### Post by buzzingrobot on 2014-04-29
> **DreddTrekkiter said:**
> [COLOR=#000000]
Isn't there a thing where I can just click a button, like you do on an EXE file in Windows, and it'll install it?

[/COLOR]

Software in Ubuntu's repositorities -- tens of thousands -- *is* packaged in .deb format and can be installed with a click. Applications like the Software Center and Synaptic simply avoid the inconvenience of making you do a separate download and a separate install by doing both at the same time, as well as locating, downloading and install any needed support packages (dependencies).

In a default Ubuntu installation, if you do download a .deb package intended for installation on Ubuntu -- like that Chrome package you mentioned -- and click on it, the Software Center application should open and offer to install it. You can use other applications to install .deb pacakges.  One called "gdebi" is popular. once gdbei is installed, you can affect the switch by right clicking on a .deb file and selecting 'Properties".

The command line equivalent is "sudo apt-get install <package_name>".  This will download the package, determine what the dependencies are, and download and install the lot. 

However the install is triggered, the same things happen. (A Linux system is, at heart, a multi-user system capable of supporting multiple simultaneous users running on *one* machine.  Hence, a user requires permission to alter any part of the filesystem apart from his or her own home directory.  That happens when you install new software. That's what the "sudo" is for: It tells the system that you want to temporarily acquire the authority to install the software.)

As a rule, the first place you should look for software is in Ubuntu's repositories. Software is also available in repositories called PPA's. These are not officially supported, so you are dependent on the person(s) posting that software for fixes, security updates, etc. 

Other Linux distributions use the .deb package format. You should avoid installing packages intended for those other systems.  If nothing else, file system layouts differ somewhat among distributions, so the installation instructions contained in the package may not work at all or work incorrectly.

Given Ubuntu's popularity, it is rare to come across software that has not been packaged for installation on Ubuntu.  The exception is commercial software whose vendors, if they release for Linux at all, often do it late.

As mentioned earlier, archive files -- typically ending in ".tar.gz" or some variation of ".zip" -- are not intended to be user installable packages.  They are collections of files -- archives -- bundled together for convenience. Their contents can be extracted, but that amounts to dumping the files into the current directory. Their targetted use is to archive source code.

---

### Post by monkeybrain20122 on 2014-04-29
> **buzzingrobot said:**
> 
In a default Ubuntu installation, if you do download a .deb package intended for installation on Ubuntu -- like that Chrome package you mentioned -- and click on it, the Software Center application should open and offer to install it. You can use other applications to install .deb pacakges.  One called "gdebi" is popular. once gdbei is installed, you can affect the switch by right clicking on a .deb file and selecting 'Properties".

.

BTW there is a gdebi bug in 14.04, it doesn't install dependencies automatically as it should (so have to run "sudo apt-get -f install" after running gdebi), I see a gdebi package in proposed updates so it is probably fixed.

---

### Post by buzzingrobot on 2014-04-29
> **monkeybrain20122 said:**
> BTW there is a gdebi bug in 14.04, it doesn't install dependencies automatically as it should (so have to run "sudo apt-get -f install" after running gdebi), I see a gdebi package in proposed updates so it is probably fixed.

Thanks!  Good to know.

---

