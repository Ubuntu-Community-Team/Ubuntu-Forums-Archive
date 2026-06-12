---
title: "installing programs, rpm files vs tar.gz files?"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by stupidquestion on 2012-07-31
I want to install a program, and the download page for Unix Binary Releases has various .rpm files (for RedHat CentOS, and "development") and .tar.gz files (for Solaris Sparc, Cygwin, MinGW), or the source if the "system is not on the list". Which should be used for Ubuntu?

And this is a really dumb question but, my box is using Ubuntu Server, no GUI, so how do I download the binary files from the URL I see?

the program is:
[http://www.imagemagick.org/script/binary-releases.php](http://www.imagemagick.org/script/binary-releases.php)

---

### Post by electricmaster on 2012-07-31
I believe you would have to go for tar.gz. Ubuntu is Debian based, so if at all possible, go for .deb because .deb is the easiest, but you should be able to use .tar.gz, it's just more complicated.

---

### Post by Elfy on 2012-07-31
Generally you want a deb

First port of call should be software-centre/synaptic/apt - see if there is one in the repos - imagemagick is in fact there.

Open your software centre and search for it.

Have a look here also

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

You can also check here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Ubun2to on 2012-07-31
.RPM files are used by Red Hat based distros. Ubuntu is based on Debian, so it uses .DEB files.
If possible, use .DEB files.
If there are no .DEB files, you might have to use a .TAR.GZ file (aka "tarballs"). These are more complicated, but will usually work, regardless of the distro you are using.

---

### Post by audiomick on 2012-07-31
There is this

[https://help.ubuntu.com/community/RPM/AlienHowto]("https://help.ubuntu.com/community/RPM/AlienHowto")

I have not tried it, but I believe it works ok most of the time.

---

### Post by drmrgd on 2012-07-31
> **Elfy said:**
> Generally you want a deb

First port of call should be software-centre/synaptic/apt - see if there is one in the repos - imagemagick is in fact there.

Open your software centre and search for it.

Have a look here also

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

You can also check here [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

+1 

It's always in your best interest to check the repositories for the packages you want before trying to compile from source.  Since you are on a server with no GUI, though, you'll want to use the apt-get utility to get and install the package (unless of course you install and prefer to use Synaptic Package Manager).  In addition to the links that Elfy provided, you might find this informative:

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by Mark Phelps on 2012-07-31
I have tried convering rpms to debs myself, and it only works rarely.  You should use debs wherever possible.

---

### Post by stupidquestion on 2012-07-31
> **drmrgd said:**
> +1 

It's always in your best interest to check the repositories for the packages you want before trying to compile from source.  Since you are on a server with no GUI, though, you'll want to use the apt-get utility to get and install the package (unless of course you install and prefer to use Synaptic Package Manager).  In addition to the links that Elfy provided, you might find this informative:

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Thanks, using apt-get is what I did. In order to use "imagick" I also had to get php-pear, libmagickwand-dev and libmagickcore-dev, etc.

---

### Post by levlaz on 2012-07-31
If you do end up using the tar.gz the typically way to install them is to. 

1. Download and extract the tar.gz file 
2. ./configure 
3. make 
4. make install 

The configure step will ensure you have met all of the dependencies and the make step compiles the software from source. 

Sometimes the files come with install scripts.. in that case you need to make the file executable and then run the script.

---

