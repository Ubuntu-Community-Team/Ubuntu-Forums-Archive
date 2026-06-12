---
title: "HOWTO: Make and restore apt cache backups"
date: 2006-03-20
forum: Outdated Tutorials &amp; Tips
---

### Post by htinn on 2006-03-20
I like to clean install a lot so I tend to burn my packages onto CDR. This spares me the trouble of having to download them over and over. If there's a simpler way to do this, I'd love to be informed.

Anyway, here's the way I currently do it:

1) Make a new folder somewhere in your Home folder.
2) Create this script file there called "apt-copy.sh":

```
#!/bin/sh
# Make a local copy of files from the apt cache
# except for files you list in "exclude.txt".

for FILE_NAME in `ls /var/cache/apt/archives/*.deb`
do {
  BASE_NAME=`basename $FILE_NAME`
  if ! grep -s $BASE_NAME exclude.txt >/dev/null 2>&1
  then {
    cp -v -u -p $FILE_NAME .
    echo $BASE_NAME >>exclude.txt
  }
  fi
}
done

# change %3a back to :
rename -v 's/%3a/:/' *%3a*
```

3) Make this script an executable (chmod +x apt-copy.sh).
4) Any time you do a major update, you can make a local copy of your files by running this script (./apt-copy.sh).
5) Remember to hang on to the "apt-copy.sh" and "exclude.txt" files if you move the files out of this folder.

Later on, when you want to restore all these packages, you simply do this:

1) sudo apt-get install dpkg-dev
2) Create a folder in your Home folder called "archive", then make a "binary" folder and "source" folder within the archive folder.
3) Put the binary packages you want to restore into the "binary" folder and the source packages you want to restore into the "source" folder.
4) Create this script file in the "archive" folder and call it "scan.sh":

```
#!/bin/sh
dpkg-scansources source /dev/null | gzip -9c > source/Sources.gz
dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz
```

5) Make it executable (chmod +x scan.sh).
6) Once you have all the packages you want to use, run this script (./scan.sh).
7) To use the packages, add the following to your "/etc/apt/sources.list" at top of the file (sudo gedit /etc/apt/sources.list):

```
deb file:/home/htinn/archive binary/
deb-src file:/home/htinn/archive source/
```

Replace "htinn" with whatever user name you're using.

8) sudo apt-get update
9) Install your packages (using Synaptic or apt-get).

---

### Post by ergosteur on 2008-03-17
For those wondering, there's a handy little tool called aptoncd. It's in gutsy/universe.

[http://packages.ubuntu.com/gutsy/aptoncd](http://packages.ubuntu.com/gutsy/aptoncd)

---

