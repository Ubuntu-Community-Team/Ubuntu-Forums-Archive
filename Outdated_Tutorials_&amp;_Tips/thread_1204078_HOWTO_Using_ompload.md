---
title: "HOWTO: Using ompload"
date: 2009-07-04
forum: Outdated Tutorials &amp; Tips
---

### Post by loomsen on 2009-07-04
Hello everyone.

With this little writeup I will introduce those of you who didn't stumble upon ompload yet to this nice, free (free of everything!) filehoster.

It's free, unmoderated, accountless and basically accessible from everywhere throughout your OS.

**What is ompload?** 
> Omploader is a place to put your files, without all the browser clogging junk that you find at most sites.


[B]
Why would I want it / need it?[/B]
> Omploader is **anonymous and free** for **EVERYONE** to use.
So no privileges for subscriptors and thus no ads at all - 
in fact, it's not even moderated at all, you _cannot_ register an account neither.
Just get uploader script and you're ready to go.
PLUS: You may upload WHATEVER you want up to a filesize of stunning [COLOR="DarkRed"]!_1 GB_![/COLOR]

Here's some sample output of the basic CLI (=command line interface, editor's note for the newer users)

> 
[COLOR="DarkRed"]docter[~][/COLOR] ompload tmp.text 
Progress for 'tmp.text'
######################################################################## 100.0%
Omploaded 'tmp.text' to [http://omploader.org/vMXgzZQ](http://omploader.org/vMXgzZQ)
Success.
[COLOR="DarkRed"]docter[~][/COLOR] 


That's it, that's all!

[COLOR="SeaGreen"]
[SIZE="5"]STEP 1. Prepare[/SIZE]
NOTE: I will show how to install the basic command line uploader to ~/bin/ompload. In order to use it, please ensure that ~/bin is in your $PATH environment. 
If you want to have it systemwide ( - THIS IS: if you have multiple user accounts for example - ) 
you will probably want to choose another install directory instead - 
/usr/local/bin/ - should be the choice in this case
[/COLOR]

To check environment ( <== Only if you want to go with ~/bin )
```

echo $PATH | grep $(whoami)

```
You should see something similar to this:
[[img]http://www.ubuntu-pics.de/thumb/17761/shot_16_8rYnV4.png[/img]](http://www.ubuntu-pics.de/bild/17761/shot_16_8rYnV4.png)


[COLOR="Navy"][SIZE="5"]STEP 2[/SIZE]

Get the script, make it executable and place it somewhere inside a $PATH directory
```

wget http://omploader.org/ompload && chmod +x ompload

## == Now either install to ~/bin !_NOT_! using sudo == ##
install ompload ~/bin/ompload
## == OR == For systemwide support == ##
sudo install ompload /usr/local/bin

```
[/COLOR]

[COLOR="DarkOrange"][SIZE="5"]STEP 3
Enjoy :D[/SIZE]
[/COLOR]


To get you going, here are a script to integrate ompload with gnome / nautilis. You'll need to have zenity installed, so run
```
sudo aptitude install zenity ruby curl
```

Here's the right-click-context script. You may either chose one or more files to upload at once.
Save this Script under 
```
~/.gnome2/nautilus-scripts/Upload2Ompload
```
and make it executable with 
```
chmod +x ~/.gnome2/nautilus-scripts/Upload2Ompload
```
to integrate with nautilus.

[color=darkred]
## =======  CURRENT: ======= ##
## ===================== ## [/COLOR]
```

#!/bin/bash
set +x
## generate a basuc desription:
#==AUTHOR
# written by: Norbert Varzariu <loomsen@googlemail.com>	
#==START
# Basic and simple file uploader, can upload multiple files
# uses zenity to Output the resulting downloadlink
# 
# copy/place/install to "$HOME/.gnome2/nautilus-scripts" 
# to integrate with nautilus' context
# requires ompload to be installed. You can accomplish this by doing
# 
#*     wget http://omploader.org/ompload -O ~/bin/ompload*
#*     chmod +x ~/bin/ompload* 
#
#==END

## Constants:
	PROGNAME=$(basename $0)
	VERSION="0.0.2"
## Check for needed pkges
	__DEPS="ruby curl zenity"

	for i in $__DEPS; do 
		[[ "`which $i`" != "" ]] && continue || { echo -e "$i not found, please install" && exit 1;}
	done
## Check for ompload itself
	_uploader=$(which ompload 2>/dev/null)
		[[ $_uploader ]] && continue || { zenity --error --text="$0: ompload not found, please download and install first.";exit 1;}

## DoIt
	zenity  --info --text="`$_uploader $@`"  100 125
	unset _uploader __DEPS
	exit $?

```


## == [COLOR="Sienna"]OBSOLETE:[/COLOR] == ##
```

#!/bin/sh
#PROGNAME=$(basename $0)
#VERSION="0.0.1"
##_uploader=$(which ompload)
##_output=$($_uploader "$@")
##zenity --info --text="$(echo $_output)" 50 75 
##unset _uploader _output
##exit $?	

```


Rightklick on any file will give you 
[[img]http://www.ubuntu-pics.de/thumb/17762/shot_18_V51weX.png[/img]](http://www.ubuntu-pics.de/bild/17762/shot_18_V51weX.png)
and then this:
[[img]http://www.ubuntu-pics.de/thumb/17763/shot_20_jul4H3.png[/img]](http://www.ubuntu-pics.de/bild/17763/shot_20_jul4H3.png)


Another Goodie: 
Desktop icon to drag and drop any file onto it:
[color=darkred]*edit*
To make the desktop icon work you'll have to place another copy of my script above in ~/bin (or, as explained above, somewhere else inside your path)[/color]

```

#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Name=omp
Exec=Upload2Ompload
Icon=/usr/share/pixmaps/gnome-ftp.png
```

Save it as omp.desktop and place it on your desktop. rightklick the icon and choose stretch icon to increase accessibility and enjoy :)

Simply drag and drop whatever you want to upload onto your icon and you'll get a information window with your downloadlink in no time

[[img]http://www.ubuntu-pics.de/thumb/17764/shot_21_6i021H.png[/img]](http://www.ubuntu-pics.de/bild/17764/shot_21_6i021H.png)

Allright, that's it. Not many explanations, not much to do wrong, just good, clean and fast fun.

[COLOR="Red"]NOTE: I think I should mention again that there are NO accounts on ompload, so if you're looking for _safe_ online storage, this isn't quite what you're looking for probably.

HINT: However, if you save your downloadlinks all to a log file for instance, you're not only doing yourself a favor, but also decrease the server load, so this is probably something to consider.[/COLOR]

---

### Post by jpeddicord on 2009-07-07
Approved, and thank you for your tutorials & tips contribution. To those that might have problems with this, I emphasize this bit from the original post: > NOTE: I think I should mention again that there are NO accounts on ompload, so if you're looking for _safe_ online storage, this isn't quite what you're looking for probably.

---

### Post by asilvan on 2009-07-08
I get the next error...
```
asilvan@eudyptes:~$ ompload myfile.test
/usr/bin/env: ruby: No existe el fichero ó directorio
```

so i install ruby
```
sudo apt-get install ruby
```

and then..
```
asilvan@eudyptes:~$ ompload myfile.test
Error: curl missing or not in path.  Cannot continue.

Usage:  ompload [-h|--help] [options] [file(s)]
  -q, --quiet     Only output errors and warnings
  -u, --url       Only output URL when finished
  -f, --filename  Filename to use when posting data
                  from stdin

  You can supply a list of files or data via stdin (or both)

  This script requires a copy of cURL in the path.

```
so, i install curl...

```
sudo apt-get install curl
```

and then....
[B]
IT WORKS![/B]

I think you should add this 2 requeriments before the installation...


(my english sucks, sorry)

---

### Post by loomsen on 2009-07-09
Thanks, corrected above.

---

### Post by loomsen on 2009-07-16
Updated.

---

### Post by loomsen on 2010-01-28
Major Bugfixes.

---

### Post by droid8622 on 2010-02-07
exactly what i need!!Thanx

---

### Post by loomsen on 2010-02-13
> **droid8622 said:**
> exactly what i need!!Thanx

Glad you like it :)

---

### Post by itsyou on 2010-08-19
this script is awesome!
ompload is working fine in terminal :D

but the nautilus script gives no info

---

### Post by itsyou on 2010-08-28
cmon... no idea?

---

