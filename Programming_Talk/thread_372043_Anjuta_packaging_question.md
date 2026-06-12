---
title: "Anjuta packaging question"
date: 2007-02-27
forum: Programming Talk
---

### Post by AsGF2MX on 2007-02-27
I have an application I have written using C and from using vi, I switched to using Anjuta. It has made it really easy to package stuff (tar ball) but I have a problem:

When the user gets the package, they have to get it then do:

```

./configure
sudo make install

```

However, I need to provide a few shell scripts in order for the program to be of any use (copied to /usr/local/bin or whatever and removed when uninstalled). In addition to that, I require the installer to make a few changes to some system files and accordingly undo the changes when uninstalled.

How can I accomplish this with ease?

---

### Post by j_g on 2007-02-27
You can put shell commands in a makefile. Put the lines of your "install bash script" under an "install" section, much like you probably have a "clean" section that calls the shell command rm.

Then after the guy does the make command, he'll follow it up with a:

make -install

to run your install script, and "install" your application.

You'll also put an uninstall section too, with the bash script that does the uninstall. The guy will have to keep your makefile around so that he can do:

make -uninstall

But a better idea would probably be to create an rpm or Debian Package of your binaries so a guy who doesn't really know how to use dev tools can easily install/uninstall your package using some GUI oriented tools like debi. You can put install and uninstall scripts in the package, and notate them as such.

---

### Post by AsGF2MX on 2007-02-28
Thanks for the info, I am actually using the autoconf tools and I'm going to have to look for the parameters. As for .debs and stuff, they will come pretty soon.

---

### Post by j_g on 2007-02-28
> I am using the autoconf tools

My condolences.

I found the auto stuff to be so unusable that I didn't bother with any of them except make. I write a very, very simple makefile for each project, and just open a command line and issue "make".

I never bothered to add any install or uninstall commands to the makefile. I also didn't bother with autoconfigure to generate a configure-generated makefile for every possible variant of Linux out there. I made a makefile that works on Ubuntu, and probably any other debian based distro.  I figure that if someone is going to compile/link the software himself, then he can manually edit the makefile to suit his system if necessary, and manually install/uninstall the resulting binaries on his system.

For those folks who don't want to compile/link the stuff, I made an RPM file containing the binaries. The RPM format is a _lot_ saner than the autotools stuff. All you need is one RPM " specification file", and the various sections (make, install, uninstall) are fairly straightforward. Then I used a program called Alien to convert the RPM file to a Deb file. (I did it this way, rather than make a Debian Package, because the Debian package format, much like the autotools, appears to have been designed by someone who was on LSD). Of course, this deb file will probably only work on Ubuntu and other similiar debian distros, but what the hell, I don't see the need to support many distros. In fact, it would be good thing for the majority of these "distros du jour" to just disappear altogether, so we can all concentrate upon standardizing (rather than further bastardizing) Linux.

---

### Post by AsGF2MX on 2007-03-02
Thanks for the info, I have got everything rolling with the automake and stuff (the answer to my question was actually to add dist_ in front of the scripts I want to distribute) but I'm taking up your advice on RPMs and Debs. The problem is I truthfully have no idea where to begin with the RPMs or debs. Looking at the debs, it looks like a three tiered system - scary. RPMs seem to be a single spec file.

Right now, the package is downloadable and usable as is.

tar -xvf pkgname.tar.gz
./configure
sudo make install

This compiles and copies over one program to /usr/local/bin and a few sh scripts to the same folder. I honestly don't want to meddle with the automake stuff if I can and I am also using an SVN so I would like to make this easily manageable as well.

Where do I begin?

---

### Post by j_g on 2007-03-03
[http://www.rpm.org/max-rpm](http://www.rpm.org/max-rpm) will tell you all you need to know.

Since you're packaging your own stuff, forget all this stuff about "pristine sources" and "patches". Your sources are already "pristine" because you're the guy who made them.

If you want to skip a lot of the introductory stuff, and just get to a simple example, you can skip to the section 11 (Building packages -- a simple example). This one section is all you really need to know if you're just packaging a basic executable (and support files).

NOTE: Ubuntu seems to install the RPM package under /usr/src/rpm which is different than on a redhat system, so the docs may refer to a different install directory.

The basic steps are:

1) Pack all your source files in a tar file. Copy this to /usr/src/rpm/SOURCES. (You may need to use the su command from a command prompt to give yourself adminstration rights to copy to this dir).
2) Write your rpm spec file. Name it something like myspec-0.1.spec (assuming your app's version is 0.1). Copy it to /usr/src/rpm/SPECS.
3) Open a command prompt. CD to /usr/src/rpm/SPECS and type:

rpmbuild -ba myspec-0.1.spec

If all goes well, this should build your binaries in /usr/src/rpm/BUILD, copy them to where your .spec file specifies, and create a .rpm file that packages the binaries and info about where to install them.

4) CD to /usr/src/rpm/RPMS/i386. There you'll find your myspec-0.1-1.i386.rpm file. Run it through alien as so:

alien -k myspec-0.1-1.i386.rpm --scripts

And it will produce your .deb file. If you've installed debi, then you should be able to double-click on it to test the installation of your app with this .deb file.

About the .spec file. Assume you're creating an executable that will be named myprogram, and you'll want it installed in the /usr/bin directory. Your source code dir is called MySources, and you've packed it up in the tar file (named myprogram-0.1.tgz) as so. Assume your make file is placed in MySources dir as well.

 Your spec file will likely look something like this

Summary: My program that does something.
Name: myprogram
Version: 0.1
Release: 1
License: GPL
Group: Applications/Accessories
Source: [http://somewebpage.com/myprogram-0.1.tgz](http://somewebpage.com/myprogram-0.1.tgz)
Packager: My Name <myname@email.com>

%description
A program that does something.

%prep
%setup -n MySources

%build
cd $RPM_BUILD_DIR/MySources
make

%install
cd $RPM_BUILD_DIR/MySources
chmod 755 myprogram
cp myprogram /usr/bin/

%files
/usr/bin/myprogram

---

### Post by AsGF2MX on 2007-03-03
Thanks for the info, I tried it and the RPM builds ok but I do not know how to test it. However, following your example, quite literally, I have a major nuisance. The debian package, when uninstalled tries to remove "usr/local" and actually does remove my "/usr/local/bin" as it is an empty directory to begin with (this is where myprogram goes). How can I avoid this removal action?

The other little problem is that the email address on the deb package is wrong. Also do I need to provide different SPEC files for different architectures? Or is using NoArch going to work?

---

### Post by j_g on 2007-03-03
Well, the RPM file is pointless on a debian distro, since you've already created your deb file for that purpose. You'd test out the RPM package on a distro that uses RPM as it's "native" installation file format (rather than debian), such as Fedora or SUSE. (But note that you may need to alter your spec file's install section to reflect the file heirarchy of those distros, if they differ from Ubuntu in ways that affect your app's install. And you really should build the RPM on the distro for which you're making the RPM. In other words, it's not a good idea to make an RPM on your Ubuntu system, if you intend the RPM to be installed on Fedora).

The email address is supposed to be your own. The example I made has a "dummy" (ie, non-existent) email address. And of course, you should put your own name there.

I'm not aware of the minute details of how Ubuntu handles uninstallation of software, as far as directory creation/deletion are concerned. It would make sense to me that it would try to delete empty directories when software is uninstalled, if it also creates any directories when software is installed. As long as isn't deleting directories with stuff that isn't supposed to be deleted, I'm not sure if this is a cause for concern.

Yes, you may need to write different spec scripts for different distros/setups if your program may be affected by this. The .deb file you produced via alien should work on any reasonable (ie, not terribly hacked) Debian distro. But you can't assume that it will work on some non-Debian based distro. There could be differences in file hierarchy that require you to rewrite aspects of your spec file. But even if you don't have to alter the spec file itself, you should recreate the deb or rpm file on the particular distro you're targetting, if there is any doubt that it may not have the same file heirarchy or base OS support files you require.

Until Linux gets a real "install API", there's no real standardization for installation. You pretty much have to take each distro one at a time, and hope that the ones you're supporting all have enough similiarities so that you won't have a lot of headaches, work, and testing.

---

