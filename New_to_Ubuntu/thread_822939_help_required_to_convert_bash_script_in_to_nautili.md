---
title: "help required to convert bash script in to nautilis script please"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by stinger30au on 2008-06-08
this program

[http://gaffitter.sourceforge.net/](http://gaffitter.sourceforge.net/)

will allow you to get the best fit of your data to fit cd or dvd

and if you use this script from terminal it will collect the data and send it to k3b

[http://gaffitter.sourceforge.net/files/gaffitter-k3b](http://gaffitter.sourceforge.net/files/gaffitter-k3b)

id really like if someone know how to modify the code as it stands so it can make 2 scripts. one script would be to create 700 meg cd the other would make 4.3 gig dvds spanned.

once the scripts are made we can add those to our nautilus scripts folder, and with a bit of luck we can use nautilus to scroll round our hdds and right click on any directory and select the script to create either 702meg cd or 4.3 gig dvd and let k3b do its work with out using the shell.

can anyone help?

thanks

---

### Post by Xiong Chiamiov on 2008-06-09
The script I see there has flags to allow either CD- or DVD-fitting, among other things.  I take it, however, that you would prefer to have two separate scripts, rather than one?

Without actually running it myself, I believe that you can leave the bottom part the same:
```

# check GAFF_OPTS
[ -z "$GAFF_OPTS" ] && usage

# Run GAFFitter and feed K3B
(echo -n "$FILES" | tr $DELIM '\n' | $GAFFITTER - $SEARCH_METHOD $GAFF_OPTS $ITER \
     --hs --dw $DELIM; echo) | grep -v ^$ | while read -r l; 
 do 
   # call K3B
   echo "$l" | tr -d '\n' | xargs -d $DELIM $K3B $K3B_OPTS; 
   # print selected files to console, one per line
   echo "$l" | tr $DELIM '\n';
 done

```
Before that, you need to initialize the variables.  The first one of these is for CD, the second being DVD.
```

GAFF_OPTS="-t 702 -m --bs 2048"
SEARCH_METHOD=""
K3B_OPTS="--datacd"
ITER=""
FILES=""

```
```

GAFF_OPTS="-t 4482 -m --bs 2048"
SEARCH_METHOD=""
K3B_OPTS="--datadvd"
ITER=""
FILES=""

```

---

### Post by stinger30au on 2008-06-09
thanks will try it out very shortly

---

### Post by stinger30au on 2008-06-09
here is the modified version just for the 702 Mb Cd

#!/bin/bash
# Paths
GAFFITTER="gaffitter"
K3B="k3b"

GAFF_OPTS="-t 702 -m --bs 2048"
SEARCH_METHOD=""
K3B_OPTS="--datacd"
ITER=""
FILES=""


# check GAFF_OPTS
[ -z "$GAFF_OPTS" ] && usage

# Run GAFFitter and feed K3B
(echo -n "$FILES" | tr $DELIM '\n' | $GAFFITTER - $SEARCH_METHOD $GAFF_OPTS $ITER \
     --hs --dw $DELIM; echo) | grep -v ^$ | while read -r l; 
 do 
   # call K3B
   echo "$l" | tr -d '\n' | xargs -d $DELIM $K3B $K3B_OPTS; 
   # print selected files to console, one per line
   echo "$l" | tr $DELIM '\n';
 done



----------------------------------------------------------------------------------------------------


and here is the modified one for the 4.3 gig dvd


#!/bin/bash

# Paths
GAFFITTER="gaffitter"
K3B="k3b"

GAFF_OPTS="-t 4482 -m --bs 2048"
SEARCH_METHOD=""
K3B_OPTS="--datadvd"
ITER=""
FILES=""


# check GAFF_OPTS
[ -z "$GAFF_OPTS" ] && usage

# Run GAFFitter and feed K3B
(echo -n "$FILES" | tr $DELIM '\n' | $GAFFITTER - $SEARCH_METHOD $GAFF_OPTS $ITER \
     --hs --dw $DELIM; echo) | grep -v ^$ | while read -r l; 
 do 
   # call K3B
   echo "$l" | tr -d '\n' | xargs -d $DELIM $K3B $K3B_OPTS; 
   # print selected files to console, one per line
   echo "$l" | tr $DELIM '\n';
 done


----------------------------------------------------------------------------------------------------


i have set the permissions on these scripts so i can run them using Nautilus scripts.

if i start nautilus up and select a directory and right click on it and select with one of these scripts, a white box flashes up so fast on my screen i cant see what it says and then it closes again.

how ever if i use shell to navigate to the nautilus scripts directory and run either of the scripts i get this appear on my terminal

:~/.gnome2/nautilus-scripts$ ./4.3Gig-dvd
tr: missing operand after `\\n'
Two strings must be given when translating.
Try `tr --help' for more information.
> Could not read: --dw
> [Ignoring] file/dir: --dw

> Error: No input to process


i get the same error if i run the script for the 702Mb Cd as well. i assume it gives this error from terminal as i have not told it what directory to look at.

is there any way i can make the bash script pause at the end so i can read the screen rather then it open and close so fast i cant read it, as im sure it is saying it has an error.

---

