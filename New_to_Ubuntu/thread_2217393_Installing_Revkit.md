---
title: "Installing Revkit"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by Karthik_sudhir on 2014-04-17
I am trying to install a software called RevKit in ubuntu. This is the requirements shown :


REQUIREMENTS
  You need the following packages (by distribution):

  Ubuntu, Mint Linux: (for the Python Interface Ubuntu 9.10 or higher is required)
  $ sudo apt-get install build-essential cmake python-dev ipython python-qt4 python-numpy

  openSUSE:
  $ sudo zypper install gcc-c++ cmake python-devel IPython python-qt4 python-numpy

  Fedora:
  $ sudo yum install wget gcc-c++ cmake python-devel ipython PyQt4 numpy

  Further packages which are not available in the
  distrubition's package manager (as e.g. CUDD or PUMA)
  are downloaded and installed automatically from the bootstrap script.
  Boost is also required and will be downloaded and installed by default.
  If you prefer using the distributions boost version, please have a look at the RevKit users manual.

SE LINUX ENFORCING SETTING (for Fedora users only)
  You need to disable SE Linux enforcing to run RevKit in
  a python shell. There are two ways to do this, temporarily
  or permanently.

  Temporarily:
  $ sudo /usr/sbin/setenforce 0

  Permanently:
  Change "enforcing" to "disabled" in "/etc/selinux/config" and reboot.

I need help regarding interpreting this requirements and what i should do regarding it.

---

### Post by westie457 on 2014-04-17
In the terminal run ```
[COLOR=#000000] sudo apt-get install build-essential cmake python-dev ipython python-qt4 python-numpy
```
then install Revkit.

You should not need to do anything else to install. Any problems post back here. 

Definitely post back if there are errors.

ps Welcome to the Forum.[/COLOR]

---

### Post by jennifer_pinto on 2014-04-17
Here are some of the requirements which has to be fullfiled in order to run Revkit:


[LIST]
[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]Xubuntu 	9.10 64bit for the Host OS[/SIZE][/FONT][/COLOR]
[LIST]
[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]NO 		DUAL BOOT[/SIZE][/FONT][/COLOR]
[/LIST]
[/LIST]

[LIST]
[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]abandoned 		Dell Vostro 1700 laptop[/SIZE][/FONT][/COLOR]
[LIST]
[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]this 		machine is close to the specs of a similar Vista machine I 		frequently use for Revit remotely from the office.[/SIZE][/FONT][/COLOR]
[/LIST]

[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]stock 	processor (1.8Ghz Intel Core 2 Duo E8000?)[/SIZE][/FONT][/COLOR]
[LIST]
[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]I'm  		unsure of the EXACT processor product code, but I do not think this 	 	chip fully supports hardware virtualization (VT-X) which means that 		I  am POSSIBLY not using the processor to its fullest potential with 		 both cores.[/SIZE][/FONT][/COLOR]
[/LIST]

[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]3Gb 	Kingston ram[/SIZE][/FONT][/COLOR]
[LIST]
[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]This 		upgrade was done as a quick fix before the original user was given 		a newer replacement system.[/SIZE][/FONT][/COLOR]
[/LIST]

[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]Windows 	XP Pro 32bit[/SIZE][/FONT][/COLOR]
[LIST]
[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]It  		was my first choice to run 64bit, but I believe a lack of hardware 		 virtualization was failing me (FOR THIS PARTICULAR PROCESSOR CHIP.)[/SIZE][/FONT][/COLOR]
[/LIST]

[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]Revit 	Architecture 2010[/SIZE][/FONT][/COLOR]
[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]VirtualBox[/SIZE][/FONT][/COLOR]
[LIST]
[*][COLOR=#ff0000][FONT=Arial, sans-serif][SIZE=2]This 		is my virtualization software to create the virtual Windows XP 		enviroment[/SIZE][/FONT][/COLOR]
[/LIST]
[/LIST]

Matching to all these requirements will lead to a successfull configuration of Revkit.

If then too problem persist go for this perticular command before installation in Run:

[COLOR=#000000]sudo apt-get install build-essential cmake python-dev ipython python-qt4 python-numpy

then there should no problem atall in configuration.
[/COLOR]

---

### Post by abhishek-agar2 on 2014-05-17
i have also been trying to install revkit and i ran the above instruction, however am still getting lots of errors. please can u go through the following question link and the corresponding comments and solve my problem? 
[http://askubuntu.com/questions/465703/how-to-install-revkit](http://askubuntu.com/questions/465703/how-to-install-revkit)

---

### Post by westie457 on 2014-05-19
@ abhishek-agar2
I got your PM asking for more help. Never having installed revkit I assumed that the response I posted would be enough. However after your message I have tried to install revkit.

So far I have run through the suggestions on the link you posted. On my system I have got to the stage where this file 'fmi/core.hpp' is missing.
Obviously, my Google abilities are not quite good enough to get past this as I have only got 3 hits and no solution yet. I will keep trying and let you know of any progress

Edit...
Just had a successful run of ./make.py build.

Got this far by deleting the revkit folder and starting over.
During the ./make.py bootstrap stage got an error about bzlib.h not found so installed ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install libbz2-1.0 libbz2-dev libbz2-ocaml libbz2-ocaml-dev
``` ran ./make.py bootstrap again, this completed and then ran ./make.py build. This also completed with no errors.[/FONT][/COLOR]

---

### Post by abhishek-agar2 on 2014-05-28
i ran that command line but i am still getting this error in the bootstrap command.

abhishek@Abhishek:~/Desktop/revkit-1.3$ ./make.py bootstrap
init
Wed May 28 16:54:06 IST 2014 /home/abhishek/Desktop/revkit-1.3/scripts/bootstrap param: 
process required programs
done
build directory: /home/abhishek/Desktop/revkit-1.3/build
dependencies directory /home/abhishek/Desktop/revkit-1.3/dependencies
fatal: unable to connect to github.com:
github.com: Name or service not known

Cloning into 'installer'...
cmake version 2.8.11.2
your cmake is up-to-date
Building dependencies
/home/abhishek/Desktop/revkit-1.3/scripts/bootstrap_functions: line 15: ./build: No such file or directory
/home/abhishek/Desktop/revkit-1.3/scripts/bootstrap: line 216: quote_error: command not found
abhishek@Abhishek:~/Desktop/revkit-1.3$ 

plz help

---

### Post by westie457 on 2014-06-12
All of these commands need to be run.```
sudo apt-get install zlib1g-dev
sudo apt-get install libbz2-1.0 libbz2-dev libbz2-ocaml libbz2-ocaml-dev
sudo apt-get install build-essential cmake python-dev ipython python-qt4 python-numpy git
```

After a failure you should run the ./make.py clean command to reset the 'revkit-1.3 directory.
Even after installing the above packages it is hit and miss on getting a complete build of the 'boostrap'. I have had one complete build of the bootstrap only to have the ./make.py build command fail with an error (boost/tuple/tuple.hpp not found). Am still trying to work around this situation.

I hope you have more success than me.

---

