---
title: "HOWTO: Easily modify dependencies of a .deb file"
date: 2007-12-10
forum: Packaging and Compiling Programs
---

### Post by Loevborg on 2007-12-10
Save the following script as "videbcontrol", ```
chmod +x
``` it and put it in your path. Then by calling:

```

videbcontrol foo.deb

```

you can edit the "Depends:" line. The resulting .deb file is written to foo.modified.deb in the current directory.

```

#!/bin/bash

if [[ -z "$1" ]]; then
  echo "Syntax: $0 debfile"
  exit 1
fi

DEBFILE="$1"
TMPDIR=`mktemp -d /tmp/deb.XXXXXXXXXX` || exit 1
OUTPUT=`basename "$DEBFILE" .deb`.modfied.deb

if [[ -e "$OUTPUT" ]]; then
  echo "$OUTPUT exists."
  rm -r "$TMPDIR"
  exit 1
fi

dpkg-deb -x "$DEBFILE" "$TMPDIR"
dpkg-deb --control "$DEBFILE" "$TMPDIR"/DEBIAN

if [[ ! -e "$TMPDIR"/DEBIAN/control ]]; then
  echo DEBIAN/control not found.

  rm -r "$TMPDIR"
  exit 1
fi

CONTROL="$TMPDIR"/DEBIAN/control

MOD=`stat -c "%y" "$CONTROL"`
vi "$CONTROL"

if [[ "$MOD" == `stat -c "%y" "$CONTROL"` ]]; then
  echo Not modfied.
else
  echo Building new deb...
  dpkg -b "$TMPDIR" "$OUTPUT"
fi

rm -r "$TMPDIR"

```

PS: Thanks to [http://ubuntuforums.org/showthread.php?t=110458](http://ubuntuforums.org/showthread.php?t=110458)

---

### Post by K.Mandla on 2007-12-20
Moved to Packaging and Compiling Programs.

---

### Post by tears.of.angels on 2008-05-28
thanks! this is exactly what i've been looking for.

i've been using ruby-ripper (i think i got the deb from getdeb.net) and one of the dependencies is gedit while i'm using medit. changing this allowed me to get rid of gedit!

---

### Post by motin on 2008-08-14
Thanks a million! This made it dead easy to get the debian liblinuxsampler package to install successfully in Ubuntu (where libgig is called libgig6 for some reason).

I modified it slightly to make it easier to use another editor than vi:
Also, I prefer to call it edit-deb-control.sh...

```
#!/bin/bash

EDITOR=gedit

if [[ -z "$1" ]]; then
  echo "Syntax: $0 debfile"
  exit 1
fi

DEBFILE="$1"
TMPDIR=`mktemp -d /tmp/deb.XXXXXXXXXX` || exit 1
OUTPUT=`basename "$DEBFILE" .deb`.modfied.deb

if [[ -e "$OUTPUT" ]]; then
  echo "$OUTPUT exists."
  rm -r "$TMPDIR"
  exit 1
fi

dpkg-deb -x "$DEBFILE" "$TMPDIR"
dpkg-deb --control "$DEBFILE" "$TMPDIR"/DEBIAN

if [[ ! -e "$TMPDIR"/DEBIAN/control ]]; then
  echo DEBIAN/control not found.

  rm -r "$TMPDIR"
  exit 1
fi

CONTROL="$TMPDIR"/DEBIAN/control

MOD=`stat -c "%y" "$CONTROL"`
$EDITOR "$CONTROL"

if [[ "$MOD" == `stat -c "%y" "$CONTROL"` ]]; then
  echo Not modfied.
else
  echo Building new deb...
  dpkg -b "$TMPDIR" "$OUTPUT"
fi

rm -r "$TMPDIR"
```

---

### Post by Pablo12 on 2009-08-25
This script rocks!!  What else can I say, many thanks.

---

### Post by 23dornot23d on 2010-06-26
Nice well written script .... I like it ..... ty ..... ;)

---

### Post by fluffnik on 2010-08-18
Many thanks!

My version is called "nanodebcontrol"  :)

---

### Post by Losergamer04 on 2010-10-23
I just wanted to say thanks!

---

### Post by Danielaus on 2010-11-07
Thanx guys!! Great script!
I just needed it to edit a deb from a ppa with a typo in the dependencies!
YEAH! ;)

I also edited motin version to create the deb file in the current directory and using the name-version from the control file

```
#!/bin/bash

EDITOR=nano

if [[ -z "$1" ]]; then
  echo "Syntax: $0 debfile"
  exit 1
fi

DEBFILE="$1"
TMPDIR=`mktemp -d /tmp/deb.XXXXXXXXXX` || exit 1
#OUTPUT=`basename "$DEBFILE" .deb`.modfied.deb
OUTPUT="."

#if [[ -e "$OUTPUT" ]]; then
#  echo "$OUTPUT exists."
#  rm -r "$TMPDIR"
#  exit 1
#fi

dpkg-deb -x "$DEBFILE" "$TMPDIR"
dpkg-deb --control "$DEBFILE" "$TMPDIR"/DEBIAN

if [[ ! -e "$TMPDIR"/DEBIAN/control ]]; then
  echo DEBIAN/control not found.

  rm -r "$TMPDIR"
  exit 1
fi

CONTROL="$TMPDIR"/DEBIAN/control

MOD=`stat -c "%y" "$CONTROL"`
$EDITOR "$CONTROL"

if [[ "$MOD" == `stat -c "%y" "$CONTROL"` ]]; then
  echo Not modfied.
else
  echo Building new deb...
  dpkg -b "$TMPDIR" "$OUTPUT"
fi

rm -r "$TMPDIR"
```

---

### Post by roobie on 2011-01-26
Beautiful! Made my life _that_ much easier!

Nice one! Thanks a lot! :KS

---

### Post by vambo on 2011-05-05
What a damned useful little script! Many Thanks.

---

### Post by ricky06181993 on 2011-05-26
I am completely new to ubuntu and need to know what exactly i need to do to change the dependency in boxee from "libxmlrpc-c3" to "libxmlrpc-c3-0".

Thanks in advance for any help,
Ryan.

---

### Post by derSoldat on 2011-05-27
Registered just to say thanks! This script did exactly what I needed.

---

### Post by emanhossny on 2011-06-24
Hello All,
I'm new to linux & have the problem "dependency is not satisfiable libxmlrpc-c3"
So plz, tell me how can I solve it?

---

### Post by princej88 on 2011-07-06
awesome script. Thanks!

---

### Post by ccsalway on 2011-08-12
Im getting:
 
$sudo: videbcontrol: command not found
 
 
Im running Ubuntu server 11.04

---

### Post by archman on 2011-08-21
> **ccsalway said:**
> Im getting:
 
$sudo: videbcontrol: command not found
 
 
Im running Ubuntu server 11.04

Your script is not in PATH, but you don't have to add it. Just cd to the location containing that script and issue "./scriptname ...".

---

### Post by mrgoodknife on 2011-10-08
I've got some questions, because I'm a straight up n00b and downloaded Ubuntu only because it was the best of the "free" options since my copy of windows apparently lost its legitimacy when I did a clean install. I'm trying to turn this computer into a media center, so if someone could basically explain this to me step-by-step, I would greatly appreciate it.

---

### Post by helpdeskdan on 2011-11-20
Thanks!  I was leary - 4 year old scripts rarely work, but this did exactly what I needed to get boxee to ignore my libvdpau1 problem.  Only one slight modification on line 31 - vim is better than vi.  ;-)  

As for mrgoodknife, it is frowned upon to post unrelated questions in forums.  Start a new thread to ask your question.  Better yet, ask Google, who knows all.

---

### Post by japzone on 2012-03-04
Found this script and it's well made. My only gripe is that I hate **vi**, just isn't intuitive for me. So I just made a quick modification.  It will now open with **gedit** instead and wait for you to save and hit enter before continuing.

*(Note: If you have problems opening the script try "bash debcontrol" in the directory of the script. Should execute the script even if it's not +x tagged)*
```
#!/bin/bash
#modded by japzone

if [[ -z "$1" ]]; then
  echo "Syntax: $0 debfile"
  exit 1
fi

DEBFILE="$1"
TMPDIR=`mktemp -d /tmp/deb.XXXXXXXXXX` || exit 1
OUTPUT=`basename "$DEBFILE" .deb`.modfied.deb

if [[ -e "$OUTPUT" ]]; then
  echo "$OUTPUT exists."
  rm -r "$TMPDIR"
  exit 1
fi

dpkg-deb -x "$DEBFILE" "$TMPDIR"
dpkg-deb --control "$DEBFILE" "$TMPDIR"/DEBIAN

if [[ ! -e "$TMPDIR"/DEBIAN/control ]]; then
  echo DEBIAN/control not found.

  rm -r "$TMPDIR"
  exit 1
fi

CONTROL="$TMPDIR"/DEBIAN/control

MOD=`stat -c "%y" "$CONTROL"`
gedit "$CONTROL"
read -p "Press any key once you've finished editing and saved"

if [[ "$MOD" == `stat -c "%y" "$CONTROL"` ]]; then
  echo Not modfied.
else
  echo Building new deb...
  dpkg -b "$TMPDIR" "$OUTPUT"
fi

rm -r "$TMPDIR"
```

---

### Post by BFris on 2012-07-07
Dude, you totally rock! :guitar:

I used this to modify GuitarPro6, which is 32bit and can now be installed on Linux! Who says nobody pays for stuff on Linux?

Very, very cool. Thanks man.

---

