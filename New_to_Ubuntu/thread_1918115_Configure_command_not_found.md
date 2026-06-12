---
title: "Configure: command not found"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by krmadh on 2012-01-31
Hi,

I need to install one "**AUTO 2000**" : continuation and bifurcation software.

The manual says- type **configure** to check your system for required compilers and libraries.

I have installed Ubuntu 11.10 (my laptop is a 64 bit processor so I took the amd64 image). When I open the terminal window, it says-
' to run a command as administrator (user "root"), use "sudo <command>".

So after I enter the location where my software installation folder is I tried the following commands and the [COLOR=DarkOrchid]errors[/COLOR] I get are as follows-


[LIST=1]
[*]for '**sudo configure**' - [COLOR=DarkOrchid]sudo: configure: command not found[/COLOR]
[*]for '**./configure**' - [COLOR=DarkOrchid]bash: ./configure: Permission denied[/COLOR]
[*]for '**sudo ./configure**' - [COLOR=DarkOrchid]sudo: ./configure: command not found[/COLOR]
[*]for '**configure**' - [COLOR=DarkOrchid]configure: command not found[/COLOR]
[*]for '**.configure**' - [COLOR=DarkOrchid].configure: command not found[/COLOR]
[/LIST]

I do not know much about all these. I have tried all these commands I found in the internet. I need to install this software soon. Hope I get help here.

Thank you.

---

### Post by Double.J on 2012-01-31
Hi there, 

You were right the second time, it is 
```
./configure
```

Have you decompressed the tarball and entered the resulting directory. For example, say you downloaded a file called auto.2000.tar.bz2, then it would be
```
cd Downloads
tar xvjf auto.2000.tar.bz2
cd auto.2000
./configure
```

Hope it helps!

---

### Post by wyliecoyoteuk on 2012-01-31
Have you got a compiler installed?
It is not installed by default.
check in synaptic for GCC

---

### Post by sandyd on 2012-01-31
> **krmadh said:**
> Hi,

I need to install one "**AUTO 2000**" : continuation and bifurcation software.

The manual says- type **configure** to check your system for required compilers and libraries.

I have installed Ubuntu 11.10 (my laptop is a 64 bit processor so I took the amd64 image). When I open the terminal window, it says-
' to run a command as administrator (user "root"), use "sudo <command>".

So after I enter the location where my software installation folder is I tried the following commands and the [COLOR=DarkOrchid]errors[/COLOR] I get are as follows-


[LIST=1]
[*]for '**sudo configure**' - [COLOR=DarkOrchid]sudo: configure: command not found[/COLOR]
[*]for '**./configure**' - [COLOR=DarkOrchid]bash: ./configure: Permission denied[/COLOR]
[*]for '**sudo ./configure**' - [COLOR=DarkOrchid]sudo: ./configure: command not found[/COLOR]
[*]for '**configure**' - [COLOR=DarkOrchid]configure: command not found[/COLOR]
[*]for '**.configure**' - [COLOR=DarkOrchid].configure: command not found[/COLOR]
[/LIST]

I do not know much about all these. I have tried all these commands I found in the internet. I need to install this software soon. Hope I get help here.

Thank you.
Add
```

chmod +x configure
```before the second one.

If that still doesn't work for some odd reason,
```

/bin/bash ./configure
```Sometimes needs a little kick to get it running. Not sure why, but it works, so I don't complain.

---

### Post by krmadh on 2012-01-31
I already have the auto folder. Had unzipped it in another monitor long back.

---

### Post by krmadh on 2012-01-31
I tried  the last suggestion and the result is shown below too. So does this mean GCC is already installed? But still configure wouldn't work?
[COLOR=Green]
~/auto/2000$ sudo /bin/bash ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking for g95... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking how to get verbose linking output from ... configure: WARNING: compilation failed

checking for Fortran libraries of ... 
checking for dummy main to link with Fortran libraries... none
checking for Fortran name-mangling scheme... configure: error: cannot compile a simple Fortran program
See `config.log' for more details.
[/COLOR]

---

### Post by oldos2er on 2012-01-31
Looks like this software is expecting a fortran compiler. Did you check the README and/or INSTALL files for a list of dependencies?

---

### Post by krmadh on 2012-01-31
And then I checked that too and this is what it says. What does this mean?

[COLOR=Green]auto/2000$ sudo /bin/bash ./config.log
./config.log: line 1: This: command not found
./config.log: line 2: running: command not found
./config.log: line 4: It: command not found
./config.log: line 5: generated: command not found
./config.log: line 7: $: command not found
Usage: hostname [-v] [-b] {hostname|-F file}         set host name (from file)
       hostname [-v] [-d|-f|-s|-a|-i|-y|-A|-I]             display formatted name
       hostname [-v]                                 display host name

       {yp,nis,}domainname [-v] {nisdomain|-F file}  set NIS domain name (from file)
       {yp,nis,}domainname [-v]                      display NIS domain name

       dnsdomainname [-v]                            display dns domain name

       hostname -V|--version|-h|--help               print info and exit

Program name:
       {yp,nis,}domainname=hostname -y
       dnsdomainname=hostname -d

Program options:
    -s, --short            short host name
    -a, --alias            alias names
    -i, --ip-address       addresses for the host name
    -I, --all-ip-addresses all addresses for the host
    -f, --fqdn, --long     long host name (FQDN)
    -A, --all-fqdns        all long host names (FQDNs)
    -d, --domain           DNS domain name
    -y, --yp, --nis        NIS/YP domain name
    -b, --boot             set default hostname if none available
    -F, --file             read host name or NIS domain name from given file

Description:
   This command can get or set the host name or the NIS domain name. You can
   also get the DNS domain or the FQDN (fully qualified domain name).
   Unless you are using bind or NIS for host lookups you can change the
   FQDN (Fully Qualified Domain Name) and the DNS domain name (which is
   part of the FQDN) in the /etc/hosts file.
uname: extra operand `='
Try `uname --help' for more information.
uname: extra operand `='
Try `uname --help' for more information.
uname: extra operand `='
Try `uname --help' for more information.
uname: extra operand `='
Try `uname --help' for more information.
./config.log: line 19: /usr/bin/uname: No such file or directory
/bin/uname: invalid option -- 'X'
Try `/bin/uname --help' for more information.
./config.log: line 22: /bin/arch: No such file or directory
/usr/bin/arch: invalid option -- 'k'
Try `/usr/bin/arch --help' for more information.
./config.log: line 24: /usr/convex/getsysinfo: No such file or directory
./config.log: line 25: hostinfo: command not found
./config.log: line 26: /bin/machine: No such file or directory
./config.log: line 27: /usr/bin/oslevel: No such file or directory
./config.log: line 28: /bin/universe: No such file or directory
./config.log: line 30: PATH:: command not found
./config.log: line 31: PATH:: command not found
./config.log: line 32: PATH:: command not found
./config.log: line 33: PATH:: command not found
./config.log: line 34: PATH:: command not found
./config.log: line 35: PATH:: command not found
./config.log: line 36: PATH:: command not found
./config.log: line 43: configure:1512:: command not found
./config.log: line 44: configure:1528:: command not found
./config.log: line 45: configure:1538:: command not found
./config.log: line 46: configure:1782:: command not found
./config.log: line 47: 5: Bad file descriptor
./config.log: line 48: syntax error near unexpected token `Ubuntu/Linaro'
./config.log: line 48: `gcc (Ubuntu/Linaro 4.6.1-9ubuntu3) 4.6.1'
[/COLOR]

---

### Post by rgreener25 on 2012-01-31
try sudo chmod 777 configure then ./configure

---

### Post by oldos2er on 2012-01-31
> **krmadh said:**
> And then I checked that too and this is what it says. What does this mean?

auto/2000$ sudo /bin/bash ./config.log


You're compiling this in your home folder, right? Don't use 'sudo' unless you absolutely need to, it changes ownership of files needlessly in this case.

config.log is most likely a text file you can view with nano or gedit.

---

### Post by sandyd on 2012-01-31
> **oldos2er said:**
> You're compiling this in your home folder, right? Don't use 'sudo' unless you absolutely need to, it changes ownership of files needlessly in this case.

config.log is most likely a text file you can view with nano or gedit.
my bad.
Thats a typo.
I normally compile in a build folder, so im used to using sudo.

---

### Post by drmrgd on 2012-01-31
It looks like you definitely need Fortran to run this.  Also, I'm not sure if there's a need for you to run the 2000 version specifically.  There is a newer version available from Source Forge that is well documented (had a hard time finding specific documents on the 2000 version).  Anyway, check it out here:

[http://indy.cs.concordia.ca/auto/#documentation]("http://indy.cs.concordia.ca/auto/#documentation")

Also, as Ann suggested, look in the Auto2000 folder for any file called "README" or "INSTALL" or some such.  It should say how to install the program and what dependencies are required to get a successful compilation.

---

### Post by krmadh on 2012-01-31
> **rgreener25 said:**
> try sudo chmod 777 configure then ./configure

I think I do not have a fortran compiler. I tried this and this is the result-
[COLOR=Green]
~/auto/2000$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking for g95... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking how to get verbose linking output from ... configure: WARNING: compilation failed

checking for Fortran libraries of ... 
checking for dummy main to link with Fortran libraries... none
checking for Fortran name-mangling scheme... configure: error: cannot compile a simple Fortran program
See `config.log' for more details.[/COLOR]

[COLOR=Black]Any idea where can I get fortran compiler from? I am trying via Ubuntu Software [/COLOR]Center..in development tools. There was one GNU octave. Clicked on it and now it says its in progress. Any idea if this will help? Or is there any other website from where I can obtain the fortran installer?

---

### Post by krmadh on 2012-01-31
> **oldos2er said:**
> Looks like this software is expecting a fortran compiler. Did you check the README and/or INSTALL files for a list of dependencies?


Yes it requires a fortran compiler. 
I tried-

[COLOR=Green]/$ yum install gcc-gfortran
The program 'yum' is currently not installed.  You can install it by typing:
sudo apt-get install yum
/$ sudo apt-get install yum
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/COLOR]

---

### Post by oldos2er on 2012-01-31
```
apt-cache search fortran compiler
``` gives quite a few hits. I'd try ```
sudo apt-get install gfortran
``` first.

---

### Post by drmrgd on 2012-02-01
> **krmadh said:**
> Yes it requires a fortran compiler. 
I tried-

[COLOR=Green]/$ yum install gcc-gfortran
The program 'yum' is currently not installed.  You can install it by typing:
sudo apt-get install yum
/$ sudo apt-get install yum
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/COLOR]

Please look in your Auto2000 folder for a directory called 'doc'.  In the newer version I mentioned above, there is such a folder and there are instructions there on how to install the software, including all the dependent packages you need (and there's more than a couple!) and where you might get them.  From the documentation regarding Fortran:

> 1.1.1 Installation on Linux/Unix
A free Fortran 95 compiler, Gfortran, is shipped with most recent Linux distributions, or can
be obtained at [http://gcc.gnu.org/wiki/Gfortran](http://gcc.gnu.org/wiki/Gfortran). The following packages (and their dependencies) are recommended for Fedora:
 Python: python-matplotlib-tk and ipython.
 PLAUT04: SoQt-devel. For SoQt versions older than 1.5.0, to see pictures of stars, the
earth and the moon instead of white blobs, compile simage from source (see [www.coin3d](www.coin3d).
org; needs libjpeg-devel).
 PLAUT: xterm.
 GUI94: lesstif-devel or openmotif-devel.
 manual: LATEX(tetex or texlive) and transg.
and the following for Ubuntu and Debian:
 Python: python-matplotlib and ipython.
 PLAUT04: SoQt (libsoqt-dev or libsoqt4-dev) and libsimage-dev.
 PLAUT: xterm
 GUI94: lesstif2-dev or libmotif-dev.
 manual: LATEX(tetex or texlive) and transg.
Other distributions may have packages with similar names.
If you need to compile and install one of the above PLAUT04 libraries from the source code
available at the above web site, and you nd that, after that, PLAUT04 still does not work then
you might need to adjust the environment variable LD LIBRARY PATH to include the location of
these libraries, for instance /usr/local/lib.

So, Ann's instinct is correct, and you should install gfortran.  Their instructions seem to be geared more toward Fedora.  However, there should be similar packages available for Ubuntu.  A quick Ubuntu repository search using the Software Center or the web would serve you well here.  You can use this link to help you look for Ubuntu specific packages:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by krmadh on 2012-02-15
> **drmrgd said:**
> It looks like you definitely need Fortran to run this.  Also, I'm not sure if there's a need for you to run the 2000 version specifically.  There is a newer version available from Source Forge that is well documented (had a hard time finding specific documents on the 2000 version).  Anyway, check it out here:

[http://indy.cs.concordia.ca/auto/#documentation](http://indy.cs.concordia.ca/auto/#documentation)

Also, as Ann suggested, look in the Auto2000 folder for any file called "README" or "INSTALL" or some such.  It should say how to install the program and what dependencies are required to get a successful compilation.

[COLOR=Purple]Hi all,

I finally installed AUTO. I installed the latest version as suggested :) it really had a better manual. I needed to install many other things before like FORTRAN 99 etc.

My main problem was all the additional packages Ubuntu installs only via the Ubuntu software center (needs Internet). In order to access the Internet I am using, user ID and password is required, which obviously the Ubuntu will not know. Hence it was getting stuck!!

So with the help of a computer Engineer, we managed to give the required proxy setting for Ubuntu software center to access. That solved the problem :)

Anyway thanks to all of you. I did learn stuff regarding LINUX in this process.

[/COLOR]

---

