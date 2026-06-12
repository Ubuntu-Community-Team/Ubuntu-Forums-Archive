---
title: "How can I run C script file"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by piyawat on 2008-04-27
Dear helpers,

Now I use ubuntu 7.10 desktop via VMware player. How can I run below script in the terminal? This file name is "MakeChannelState.scr" 

I type "MakeChannelState.scr" in the terminal it said that:
bash: MakeChannelState.scr: command not found

Thanks.

********************** MakeChannelState.scr*********************
#!/bin/tcsh -f

# Extremely simple script to create the initial channel state file.

if( $#argv < 3 ) then
    echo "usage: $0 <StreamNetworkFile> <InitialDepth> <Output Date String: MM.DD.YYYY.hh.mm.ss>"
else    	

set StreamNetworkFile = ${argv[1]}
set InitialDepth = ${argv[2]}
set OutputDate = ${argv[3]}
shift   

# Set the width for each channel class (numbered 1,2,3,...,n):

set width = 1.5,2.,3.,5.,2.,5.,7.5,10.,15.

awk -v W=$width 'BEGIN{ split( W, WARRAY, "," );}{LENGTH = $4; VOL = WARRAY[$5]*LENGTH*$InitialDepth; print $1, VOL;}' $StreamNetworkFile >! ../modelstate/Channel.State.$OutputDate

endif

***********************************************************

---

### Post by cyb3rd4wn on 2008-04-27
try this:

chmod +x MakeChannelState.scr
.MakeChannelState.scr


or 
chmod +x MakeChannelState.scr
./MakeChannelState.scr

---

### Post by piyawat on 2008-04-27
Dear helpers,

I try to run below script in terminal by typing "MakeChannelState.scr" but it said "command not found"

Thanks.
*********** MakeChannelState.scr *****************
#!/bin/tcsh -f

# Extremely simple script to create the initial channel state file.

if( $#argv < 3 ) then
    echo "usage: $0 <StreamNetworkFile> <InitialDepth> <Output Date String: MM.DD.YYYY.hh.mm.ss>"
else    	

set StreamNetworkFile = ${argv[1]}
set InitialDepth = ${argv[2]}
set OutputDate = ${argv[3]}
shift   

# Set the width for each channel class (numbered 1,2,3,...,n):

set width = 1.5,2.,3.,5.,2.,5.,7.5,10.,15.

awk -v W=$width 'BEGIN{ split( W, WARRAY, "," );}{LENGTH = $4; VOL = WARRAY[$5]*LENGTH*$InitialDepth; print $1, VOL;}' $StreamNetworkFile >! ../modelstate/Channel.State.$OutputDate

endif
***************************************************

---

### Post by master5o1 on 2008-04-27
Try running ./MakeChannelState.scr as the './' denotes that it is in the current folder that you are in

(ie. cd to the folder that the *.scr file is in, then run ./*.scr where *=name)

---

### Post by piyawat on 2008-04-27
> **piyawat said:**
> Dear helpers,

I try to run below script in terminal by typing "MakeChannelState.scr" but it said "command not found"

Thanks.
*********** MakeChannelState.scr *****************
#!/bin/tcsh -f

# Extremely simple script to create the initial channel state file.

if( $#argv < 3 ) then
    echo "usage: $0 <StreamNetworkFile> <InitialDepth> <Output Date String: MM.DD.YYYY.hh.mm.ss>"
else    	

set StreamNetworkFile = ${argv[1]}
set InitialDepth = ${argv[2]}
set OutputDate = ${argv[3]}
shift   

# Set the width for each channel class (numbered 1,2,3,...,n):

set width = 1.5,2.,3.,5.,2.,5.,7.5,10.,15.

awk -v W=$width 'BEGIN{ split( W, WARRAY, "," );}{LENGTH = $4; VOL = WARRAY[$5]*LENGTH*$InitialDepth; print $1, VOL;}' $StreamNetworkFile >! ../modelstate/Channel.State.$OutputDate

endif
***************************************************

1

---

### Post by Joeb454 on 2008-04-27
Please do not create [duplicate threads]("http://ubuntuforums.org/showthread.php?t=770309") it is against Forum Policy.

Besides - somebody will help you as soon as they can, you just need to be patient :)

---

### Post by piyawat on 2008-04-27
Sorry, for duplicate threads. I really don't want to. Coz this is my first post then I just try to see if my post is work properly. 

Thank you very much I will try your suggestion.

---

### Post by piyawat on 2008-04-27
I try
chmod +x MakeChannelState.scr
./MakeChannelState.scr

It said:
bash: ./MakeChannelState.scr: /bin/tcsh: bad interpreter: No such file or directory

Please kindly suggest..

---

### Post by master5o1 on 2008-04-27
is the MCS.scr (abreviated) file in your 'home' directory?

If not, cd to that directory and then run the commands. If yes, then check spelling.

Also, I remember that with some things, you may need to go like this:
sh ./file.sh instead of just ./file.sh, however I do not know about C scripts.

That said, it may have to be run as "tcsh ./MakeChannelState.scr"

> bad interpreter: No such file or directory

Although looking at this I think the /bin/tcsh interpreter file does not exist :(

---

### Post by master5o1 on 2008-04-27
[http://www.kitebird.com/csh-tcsh-book/tcsh.txt](http://www.kitebird.com/csh-tcsh-book/tcsh.txt)

> TCSH(1)							  TCSH(1)


NAME
       tcsh  - C shell with file name completion and command line
       editing

SYNOPSIS
       tcsh [-bcdefFimnqstvVxX] [-Dname[=value]] [arg ...]
       tcsh -l


Assumption is that it is run as 'tcsh ./file'

---

### Post by Joshua Netterfield on 2008-04-27
Tcsh is not installed by default. In a terminal, run

```
sudo apt-get install tcsh
```

Hope this helps....

---

### Post by master5o1 on 2008-04-27
```
jason@meinDell:/bin$ tcsh
The program 'tcsh' is currently not installed.  You can install it by typing:
sudo apt-get install tcsh

```

Just found out a problem on my machine: tcsh not installed.

so run
```
tcsh
```

and see if you match my error above. then run

```
sudo apt-get install tcsh
```

---

### Post by master5o1 on 2008-04-27
```
jason@meinDell:/bin$ tcsh
The program 'tcsh' is currently not installed.  You can install it by typing:
sudo apt-get install tcsh

```

Just found out a problem on my machine: tcsh not installed.

so run
```
tcsh
```

and see if you match my error above. then run

```
sudo apt-get install tcsh
```

---

