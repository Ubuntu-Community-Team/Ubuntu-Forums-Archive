---
title: "PATH and Variable (Environment) Setting"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by joecommon6758 on 2008-04-22
Hey Everbody

I am trying to install MIZAR on Ubuntu. The Readme file tells me the following:

--------------------------------------------------------------------

2. Installing the system

   The script 'install.sh' unpacks the Mizar system to specified directories.
In most cases it is enough to call

./install.sh

and then answer three questions about the place where files should be copied.

There are two options that may be used with this script:

./install.sh --default
runs the script in non-interactive mode (see below for default directories),

./install.sh --nodialog
always runs the script in plain mode (without 'dialog' utility)
getting input directly from STDIN (useful for writing scripts).

When run in interactive mode, first you must provide a name of a directory 
where you want to install Mizar executables (default is /usr/local/bin). 
Make sure this directory is in your PATH variable.

Then you will be prompted to choose a directory for Mizar shared files
(default is /usr/local/share/mizar). 

NOTE: After the installation you must set a variable MIZFILES to point to this 
directory. Otherwise, the system will not find the database correctly. 

Finally you will be asked about a directory where Mizar documentation files
should be placed (default is /usr/local/doc/mizar). 

----------------------------------------------------------------------

I used the --default mode for the installation.
Can anyone explain me how to 'make sure this directory is in my PATH variable' and how to 'set a variable MIZFILES'?

Thanks, 
Joe

---

### Post by PriceChild on 2008-04-22
It already is in a standard ubuntu install.
```
echo $PATH
```Will return something like:```
/home/pricechild/bin:/usr/local/sbin:**/usr/local/bin**:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

---

### Post by conjur3r on 2008-04-22
To create an environment variable for your current session:
# export MIZFILES="/usr/local/share/mizar"

Print it to confirm
# echo $MIZFILES

---

### Post by Nepherte on 2008-04-22
If you want to have the variable every time you log in with your account, open the .bashrc file in your home folder and add a new line with the export command at the end of the file.

---

### Post by joecommon6758 on 2008-04-22
Thank you so much!

---

