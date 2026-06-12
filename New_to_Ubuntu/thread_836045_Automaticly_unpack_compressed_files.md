---
title: "Automaticly unpack compressed files?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by mb4guns on 2008-06-21
Not sure where to post this question, guess you can never go wrong in this forum.

I'm wondering if there is anyway to watch certain directory's for completed compressed files to have them automaticly unpacked .....

---

### Post by startherepodcast on 2008-06-21
You could of course write yourself a script to do it but I think you are better off just unpacking it manually by Right Clicking -> Extract here

---

### Post by master5o1 on 2008-06-21
Why automatic?

---

### Post by mb4guns on 2008-06-21
It's torrent related. Want to unpack and update my media server automaticly.

---

### Post by master5o1 on 2008-06-21
Two dirs:
~/shared/*.zip
~/media/

Pseudo:

if *.zip present in ~/shared then:
[figure out zip name] (happy.zip)
mkdir ~/media/happy
unzip happy.zip to ~/media/happy
rm ~/shared/happy.zip [when completed, delete zip]
else blah blah
end if
blah

(above pseudo doesn't handle the checking if complete)

Automation not always the best tool...
:P

---

### Post by master5o1 on 2008-06-21
If you can get md5 checksums with the torrent *.zip then you can probably check for completeness with that.

---

### Post by mb4guns on 2008-06-21
check this out:

```
#!/bin/bash

# Written by Nick Boldt, codeslave@ca.ibm.com
# $Id: unpack.sh.txt,v 1.1 2007-10-14 05:28:36 nickb Exp $

# settings: 
# default folder in which to unpack video; 
targDir=~/torrents/NEW-UNPACKED/; 
# default folder to move source folder when done unpacking
delDir=~/torrents/ZZ-DELETE/; 

function usage ()
{
  echo "";
  echo "Usage: $0 <sourceDir> \\";
  echo "                [targetDir ($targDir)] \\";
  echo "                [deleteDir ($delDir)]"; 
  echo "";
  exit;
}

if [[ $# -lt 1 ]]; then usage; fi

pushd $1; sourceDir=`pwd`;
if [[ $2 ]] && [[ -d $2 ]]; then targDir=$2; fi
if [[ $3 ]] && [[ -d $3 ]]; then delDir=$3; fi

rarFile=$(find $sourceDir -name "*part*1*rar");
if [[ ! $rarFile ]]; then rarFile=$(find $sourceDir -name "*.rar"); fi
if [[ ! $rarFile ]]; then echo "ERROR: Could not find *.rar in $sourceDir!"; popd; exit; fi

pushd $targDir;
echo "";
echo -n "Unrar $rarFile ...";
unrar e -inul $rarFile;
echo " done.";
echo "";
popd; popd;
echo "";
echo -n "Moving $sourceDir into $delDir ...";
mv $sourceDir $delDir;
echo " done.";
echo "";
```

---

