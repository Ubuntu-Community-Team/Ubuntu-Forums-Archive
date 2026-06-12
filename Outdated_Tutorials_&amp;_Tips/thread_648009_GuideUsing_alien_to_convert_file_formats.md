---
title: "Guide:Using alien to convert file formats"
date: 2007-12-23
forum: Outdated Tutorials &amp; Tips
---

### Post by speeddemon8803 on 2007-12-23
This is in no way to be a complete guide to Alien..it is only meant to get you started.

1. You must enable all repositories in the Ubuntu Repositories by going to the System tab..then clicking Administration and then Software sources. Click all the check marks except Source Code.

2.Click close

3.Fire up Terminal by going to applications->Accessories->terminal

4.When terminal opens up type in sudo apt-get update

5.Type in sudo apt-get install alien

6.Type in sudo apt-get upgrade

I know..I went through a lot of steps above to get you to the point of just installing alien when I could have just given you alien with 1 and 5..but I wanted the software repositories and files to be updated before installing so there was really no chance that it WOULDNT install.

Alien is now installed.

To use alien to convert file formats:

Go to terminal and type in sudo alien oldfile.rpm newfile.deb. 

Example that I have:sudo alien flash-plugin-9.0.115.0-release.i386.rpm flash-plugin_0.0.115.0-1_i386.deb



Alien can be used to convert to MANY file formats, WAY more than I can possibly list here so dont think that it is only used for rpm to deb conversion...you can convert tgz to deb or tgz to rpm or ANYTHING honestly.

Please be warned that alien sometimes DOES NOT work...its very buggy at best

Potential problems may include:
conflicts with libraries
libraries not completely installed.
numerous other problems.

Examples of problem:
[https://lists.ubuntu.com/archives/ubuntu-users/2005-June/038765.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-June/038765.html)

Do not let the above stray you from installing or even using alien, but just use the above as a precaution.

Please also take a look at this page
[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

Thank you and have a wonderful day! ):P

---

### Post by brennydoogles on 2007-12-23
looks great!

---

### Post by bodhi.zazen on 2007-12-23
Thank you speeddemon8803 for this how-to.

I am going to move this to the tips and tutorials section.

IMO, alien should be used as a last resort rather then converting .rpm at whim.

In general, it is best to install from the Ubuntu repositories first, (don't forget to enable your repos if needed [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)).

Second choice is to install from source.

[list][*]Read the README[*]Install build-essential[*]./configure --prefix=/usr && make && sudo make install[*]consider checkinstall[/list]

If all else fails and you *must have* the package, consider alien.

From the Ubuntu alien wiki page :

> Alien converts a RPM package file into a Debian package file or alien can install a RPM file directly. This is not the recommended way to install software packages in Ubuntu. If at all possible, install packages from Ubuntu's repositories using Add/Remove, apt-get, or the Synaptic Package Manager. Package dependency conflicts may occur when attempting to install RPM packages. The Synaptic Package Manager may be able to fix or remove any broken packages.

---

