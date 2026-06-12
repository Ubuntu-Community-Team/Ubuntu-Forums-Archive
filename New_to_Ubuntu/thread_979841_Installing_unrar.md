---
title: "Installing unrar"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by GL541 on 2008-11-12
Hi, so I'm trying to install the unrar-free package. I've downloaded these three files:

	unrar-free_0.0.1+cvs20060609-1.diff.gz
	unrar-free_0.0.1+cvs20060609-1.dsc
	unrar-free_0.0.1+cvs20060609.orig.tar.tar

... and I've managed to extract the .tar one, giving me a directory called 'unrar-0.0.1'. Inside that, there are some installation instructions, which aren't working for me.

```
...The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source CODE and type `./configure' to configure the package for your system....  

```

I'm not entirely sure where this `source CODE' is, but when I `cd' to `unrar-0.0.1' and type ./configure, I get

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

I'll try to upload that `config.log' file if I can. It's rather long. <-- Edit: Looks like I can't upload files, well not to worry!

The other two files aren't behaving very well at all, I'm afraid. The .diff.gv one opens in Archive manager, which gives me the command line output
```
gzip: /media/USB DISK/unrar-free_0.0.1+cvs20060609-1.diff.gz: not in gzip format

```

Don't tell me .diff.gz is yet another type of archive for which I need to install yet another package!

Meanwhile, when I double-click the .dsc file, I'm told it's executable but when I select Run nothing happens. And when I select Display, I get a dialogue box asking me to select the `Original file for unrar-free_0.0.1+cvs20060609-1.dsc', followed invariably by an error message about not being able to find any valid signatures.

Any advice would be most welcome. :)

---

### Post by Joeb454 on 2008-11-12
You should just be able to run ```
sudo apt-get install unrar-free
```

---

### Post by tuxxy on 2008-11-12
As Joeb says install it from the repos, also unrar-free is included with ubuntu-restrcited-extras I think which should be installed on any new system imo as it includes flash, java, unrar, codecs etc

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Duck2006 on 2008-11-12
Load it from your Synaptic Package Manager.

System >> Administration >> Synaptic Package Manager

---

### Post by oldos2er on 2008-11-12
"checking for C compiler default output file name... configure: error: C compiler cannot create executables"

 You need to install the package build-essential in order to compile source code.

---

### Post by GL541 on 2008-11-13
Thanks all for the replies.

> **oldos2er said:**
> "checking for C compiler default output file name... configure: error: C compiler cannot create executables"

 You need to install the package build-essential in order to compile source code.

Ok, so I've downloaded the files

    *  [build-essential_11.1.dsc]
    * [build-essential_11.1.tar.gz]

... but how do I install this package? Won't I just get the same error again: "C compiler cannot create executables"? :-k

---

### Post by Simian Man on 2008-11-13
As others said, use the package manager, don't fight it!  Don't try to install tarballs if you do not have to.

---

### Post by zvacet on 2008-11-13
```
sudo apt-get install build-essential
```

---

### Post by tarps87 on 2008-11-13
If you have the internet of the computer do as Joeb454 said ```
sudo apt-get install unrar-free
```
If you have the internet of another computer all the packages can be found at [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
They are all .deb file so it a click and install process.
Is there any reason you are trying to compile the code?

---

### Post by GL541 on 2008-11-13
> **tarps87 said:**
> If you have the internet of the computer do as Joeb454 said ```
sudo apt-get install unrar-free
```
If you have the internet of another computer all the packages can be found at **[http://packages.ubuntu.com/](http://packages.ubuntu.com/)**
They are all .deb file so it a click and install process.


Yeah, I don't have the internet on that computer. At that address all I find are the same files I mentioned above.

> Is there any reason you are trying to compile the code?I just want to extract some rar's.

---

### Post by tarps87 on 2008-11-13
Follow this link:
[http://packages.ubuntu.com/intrepid/unrar-free](http://packages.ubuntu.com/intrepid/unrar-free)
at the bottom of the page there is a small table titled "Download unrar-free"
if you have a 32bit install download the i386 one if it is 64bit download the amd64 one, if you aren't sure which version go for the 32bit download. Now select a download mirror, the file should end with .deb, double click this and click install

This is assuming you are using Ubuntu 8.10 if you are using Ubuntu 7.04 use this link:
[http://packages.ubuntu.com/hardy/unrar-free](http://packages.ubuntu.com/hardy/unrar-free)

---

