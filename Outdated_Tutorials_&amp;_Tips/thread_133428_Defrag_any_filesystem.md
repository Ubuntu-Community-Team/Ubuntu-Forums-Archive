---
title: "Defrag any filesystem"
date: 2006-02-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Sevoma on 2006-02-20
Well, this isn't really a defrag. It sorts files on the file system by size, and it does make the fragmentation go down by a lot. Someone who had a reiserfs partition for a year with 30%(!) fragmentation had it go down to 5%.

Anyway, here are the tools. Please- don't give me credit for them. I did not make them.

This is the script for checking fragmentation:
```

#!/usr/bin/perl -w

#this script search for frag on a fs
use strict;

#number of files
my $files = 0;
#number of fragment
my $fragments = 0;
#number of fragmented files
my $fragfiles = 0;

#search fs for all file
open (FILES, "find " . $ARGV[0] . " -xdev -type f |");

while (defined (my $file = <FILES>)) {
        #quote some chars in filename
        $file =~ s/!/\\!/g;
        $file =~ s/#/\\#/g;
        $file =~ s/&/\\&/g;
        $file =~ s/>/\\>/g;
        $file =~ s/</\\</g;
        $file =~ s/\$/\\\$/g;
        $file =~ s/\(/\\\(/g;
        $file =~ s/\)/\\\)/g;
        $file =~ s/\|/\\\|/g;
        $file =~ s/'/\\'/g;
        $file =~ s/ /\\ /g;
        #nb of fragment for the file
        open (FRAG, "filefrag $file |");
        my $res = <FRAG>;
        if ($res =~ m/.*:\s+(\d+) extents? found/) {
                my $fragment = $1;
                $fragments+=$fragment;
                if ($fragment > 1) {
                        $fragfiles++;
                }
                $files++;

        } else {
                print ("$res : not understand for $file.\n");
        }
        close (FRAG);
}
close (FILES);

print ( $fragfiles / $files * 100 . "% non contiguous files, " . $fragments / $files . " average fragments.\n");

```


And this is the script for defraging:
```

#!/bin/sh
# defrag v0.06 by Con Kolivas <kernel@kolivas.org
# Braindead fs-agnostic defrag to rewrite files in order largest to smallest
# Run this in the directory you want all the files and subdirectories to be
# reordered. It will only affect one partition.
cd /home

trap 'abort' 1 2 15

renice 19 $$ > /dev/null

abort()
{
	echo -e "\nAborting"
	rm -f tmpfile dirlist
	exit 1
}

fail()
{
	echo -e "\nFailed"
	abort
}

declare -i filesize=0
declare -i numfiles=0

#The maximum size of a file we can easily cache in ram
declare -i maxsize=`awk '/MemTotal/ {print $2}' /proc/meminfo`
(( maxsize-= `awk '/Mapped/ {print $2}' /proc/meminfo` ))
(( maxsize/= 2))

if [[ -a tmpfile || -a dirlist  ]] ; then
	echo dirlist or tmpfile exists
	exit 1
fi

# Sort in the following order:
# 1) Depth of directory
# 2) Size of directory descending
# 3) Filesize descending

echo "Creating list of files..."

#stupid script to find max directory depth
find -xdev -type d -printf "%d\n" | sort -n | uniq > dirlist

#sort directories in descending size order
cat dirlist | while read d;
do
	find -xdev -type d -mindepth $d -maxdepth $d -printf "\"%p\"\n" | \
		xargs du -bS --max-depth=0 | \
		sort -k 1,1nr -k 2 |\
		cut -f2 >> tmpfile
	if (( $? )) ; then
		fail
	fi

done

rm -f dirlist

#sort files in descending size order
cat tmpfile | while read d;
do
	find "$d" -xdev -type f -maxdepth 1 -printf "%s\t%p\n" | \
		sort -k 1,1nr | \
		cut -f2 >> dirlist
	if (( $? )) ; then
		fail
	fi
done

rm -f tmpfile

numfiles=`wc -l dirlist | awk '{print $1}'`

echo -e "$numfiles files will be reordered\n"

#copy to temp file, check the file hasn't changed and then overwrite original
cat dirlist | while read i;
do
	(( --numfiles ))
	if [[ ! -f $i ]]; then
		continue
	fi

	#We could be this paranoid but it would slow it down 1000 times
	#if [[ `lsof -f -- "$i"` ]]; then
	#	echo -e "\n File $i open! Skipping"
	#	continue
	#fi

	filesize=`find "$i" -printf "%s"`
	# read the file first to cache it in ram if possible
	if (( filesize < maxsize ))
	then
		echo -e "\r $numfiles files left                                                            \c"
		cat "$i" > /dev/null
	else
		echo -e "\r $numfiles files left - Reordering large file sized $filesize ...                \c"
	fi

	datestamp=`find "$i" -printf "%s"`
	cp -a -f "$i" tmpfile
	if (( $? )) ; then
		fail
	fi
	# check the file hasn't been altered since we copied it
	if [[ `find "$i" -printf "%s"` != $datestamp ]] ; then
		continue
	fi

	mv -f tmpfile "$i"
	if (( $? )) ; then
		fail
	fi
done

echo -e "\nSucceeded"

rm -f dirlist

```


Save it to your home directory or /usr/bin as fragchk and defrag.
Chmod +x fragchk defrag
They MUST be run as root.
sudo fragchk
sudo defrag

Use this at your own risk, as it can be dangerous on your filesystem!

Known bugs:
Will not work with files with ( or ) in the name. I think it just will skip them.

*NOTE: It only makes a real difference when your fragmentation is greater than 3 percent.

Enjoy, Sevoma

---

### Post by Djartklom on 2006-02-21
I suppose this tutorial means that there is no GUI app that handles file fragmentation in Ubuntu?  I'm just wondering.

---

### Post by Ninnghizidha on 2006-02-21
Why shall i defrag a filesystem, that doesn'T need to be defragged? :-k I don't get it ....

Ninn;

---

### Post by simon_is_learning on 2006-02-21
I think I have ext3 (i chosed default in installation) . 

Since I'm new I do alot of installing and uninstalling apps. 

Is It necessary to defrag an ext2 or ext3 partition. Becouse i thought that they worked as NTFS?

---

### Post by Sevoma on 2006-02-21
[QUOTE=Ninnghizidha]Why shall i defrag a filesystem, that doesn'T need to be defragged? :-k I don't get it ....

Ninn;[/QUOTE]

Even file systems such as ext3 and reiserfs become fragmented overtime. Even though it is not as bad as ntfs or fat32, it still happens.

There is a commercial software for ext2&3 file systems called O&O Defrag for linux. [http://www.oo-software.com/en/products/oodlinux/index.html](http://www.oo-software.com/en/products/oodlinux/index.html)

---

### Post by stalefries on 2006-02-21
0% fragmentation. All right on this end!

---

### Post by gord on 2006-02-21
you really don't need to defrag an ext3 system, even if for example a single file got horribly fragmented (say for a game or som't that needed to be as quick as possible), you'd be better off moving it to another filesystem and then moving it back.

and it should be noted, as with any low-level disc opperations, a backup of (at least)important files should be made first.

---

### Post by bikeboy on 2006-02-21
From what I've been told, the main linux filesystems don't fragment to any significant degree as long as there is plenty of free space on the disk. You may start to run into problems if your disk gets full.

---

### Post by BobSongs on 2006-02-22
I didn't choose Ext2 or Ext3, but Reiser. Will this work with Reiser too?

---

### Post by Sevoma on 2006-02-22
[QUOTE=BobSongs]I didn't choose Ext2 or Ext3, but Reiser. Will this work with Reiser too?[/QUOTE]

Yes it will work with reiserfs. It works with any type.

_____________________

Some people do not have as much free space. Some do not have and extra harddrive to move files around on. 
I do a lot of compiling and transcoding so my harddrive does a lot of work. Over time it gets fragmented so I use this.
It may not be for everyone but it works for me.

---

### Post by clawhound on 2006-02-22
If you look at the script, it:

- copies a fragmented file to /temp (which is on another partition)
- verifies stuff
- copies the file back again to its original location

This technique works with any file system. 

You can get the same effect by:
- cp $1 $2
- rm $1
- mv $2 $1

I am not sure how well this would work on a full file system with large files. Getting big, empty chunks under those conditions is a bit of a trick.

If anything, you should sort files by size, and begin by shoving the small files about. They will fit into the small places easiest. The big files are more likely to get refragmented, so you worry less about them.

---

### Post by Greeface on 2006-02-23
How would you check how fragmented your file system is?

---

### Post by Sevoma on 2006-02-24
[QUOTE=Greeface]How would you check how fragmented your file system is?[/QUOTE]

It is in my post... It finds average fragmentation of files.

---

### Post by Greeface on 2006-02-24
Ah, okay.   Thanks, that helps.

---

### Post by daredevil on 2006-03-01
A graphical tool would be handy

---

### Post by jason.b.c on 2006-08-18
```
#!/usr/bin/perl -w

#this script search for frag on a fs
use strict;

#number of files
my $files = 0;
#number of fragment
my $fragments = 0;
#number of fragmented files
my $fragfiles = 0;

#search fs for all file
open (FILES, "find " . $ARGV[0] . " -xdev -type f |");

while (defined (my $file = <FILES>)) {
        #quote some chars in filename
        $file =~ s/!/\\!/g;
        $file =~ s/#/\\#/g;
        $file =~ s/&/\\&/g;
        $file =~ s/>/\\>/g;
        $file =~ s/</\\</g;
        $file =~ s/\$/\\\$/g;
        $file =~ s/\(/\\\(/g;
        $file =~ s/\)/\\\)/g;
        $file =~ s/\|/\\\|/g;
        $file =~ s/'/\\'/g;
        $file =~ s/ /\\ /g;
        #nb of fragment for the file
        open (FRAG, "filefrag $file |");
        my $res = <FRAG>;
        if ($res =~ m/.*:\s+(\d+) extents? found/) {
                my $fragment = $1;
                $fragments+=$fragment;
                if ($fragment > 1) {
                        $fragfiles++;
                }
                $files++;

        } else {
                print ("$res : not understand for $file.\n");
        }
        close (FRAG);
}
close (FILES);

print ( $fragfiles / $files * 100 . "% non contiguous files, " . $fragments / $files . " average fragments.\n");

```

```
#!/bin/sh
# defrag v0.06 by Con Kolivas <kernel@kolivas.org
# Braindead fs-agnostic defrag to rewrite files in order largest to smallest
# Run this in the directory you want all the files and subdirectories to be
# reordered. It will only affect one partition.
cd /home

trap 'abort' 1 2 15

renice 19 $$ > /dev/null

abort()
{
	echo -e "\nAborting"
	rm -f tmpfile dirlist
	exit 1
}

fail()
{
	echo -e "\nFailed"
	abort
}

declare -i filesize=0
declare -i numfiles=0

#The maximum size of a file we can easily cache in ram
declare -i maxsize=`awk '/MemTotal/ {print $2}' /proc/meminfo`
(( maxsize-= `awk '/Mapped/ {print $2}' /proc/meminfo` ))
(( maxsize/= 2))

if [[ -a tmpfile || -a dirlist  ]] ; then
	echo dirlist or tmpfile exists
	exit 1
fi

# Sort in the following order:
# 1) Depth of directory
# 2) Size of directory descending
# 3) Filesize descending

echo "Creating list of files..."

#stupid script to find max directory depth
find -xdev -type d -printf "%d\n" | sort -n | uniq > dirlist

#sort directories in descending size order
cat dirlist | while read d;
do
	find -xdev -type d -mindepth $d -maxdepth $d -printf "\"%p\"\n" | \
		xargs du -bS --max-depth=0 | \
		sort -k 1,1nr -k 2 |\
		cut -f2 >> tmpfile
	if (( $? )) ; then
		fail
	fi

done

rm -f dirlist

#sort files in descending size order
cat tmpfile | while read d;
do
	find "$d" -xdev -type f -maxdepth 1 -printf "%s\t%p\n" | \
		sort -k 1,1nr | \
		cut -f2 >> dirlist
	if (( $? )) ; then
		fail
	fi
done

rm -f tmpfile

numfiles=`wc -l dirlist | awk '{print $1}'`

echo -e "$numfiles files will be reordered\n"

#copy to temp file, check the file hasn't changed and then overwrite original
cat dirlist | while read i;
do
	(( --numfiles ))
	if [[ ! -f $i ]]; then
		continue
	fi

	#We could be this paranoid but it would slow it down 1000 times
	#if [[ `lsof -f -- "$i"` ]]; then
	#	echo -e "\n File $i open! Skipping"
	#	continue
	#fi

	filesize=`find "$i" -printf "%s"`
	# read the file first to cache it in ram if possible
	if (( filesize < maxsize ))
	then
		echo -e "\r $numfiles files left                                                            \c"
		cat "$i" > /dev/null
	else
		echo -e "\r $numfiles files left - Reordering large file sized $filesize ...                \c"
	fi

	datestamp=`find "$i" -printf "%s"`
	cp -a -f "$i" tmpfile
	if (( $? )) ; then
		fail
	fi
	# check the file hasn't been altered since we copied it
	if [[ `find "$i" -printf "%s"` != $datestamp ]] ; then
		continue
	fi

	mv -f tmpfile "$i"
	if (( $? )) ; then
		fail
	fi
done

echo -e "\nSucceeded"

rm -f dirlist
```


I really don't understand how to save these two files to **/usr/.bin** or **/home**.......

Could someone please explain this further for those of us who don't fully understand linux-speak...???   ](*,)

---

### Post by kerry_s on 2006-08-18
I ran that fragchk on my test box, i see there's an error on line 14 of the script
```
user@Box1:~$  sudo fragchk
Use of uninitialized value in concatenation (.) or string at /usr/bin/fragchk li
ne 14.
0.354071825998988% non contiguous files, 1.00606980273141 average fragments.

```
here's line 14
```
open (FILES, "find " . $ARGV[0] . " -xdev -type f |");
```

which "." should i remove to fix the error?

---

### Post by jdong on 2006-08-18
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

Here's my Python version. It's a bit more feature-complete and sane, in that it won't try to kill itself getting 3 fragments out of a 40GB file :)


Honestly, sometimes I run it and have it nuke 10000+ fragments, and the system feels just the same.

Defragging a Linux filesystem is simply a waste of time :)

---

### Post by Perfect Storm on 2006-08-18
I agree with Jdong.

The only case where it might be useful if you have a server where the harddisc is completly stuffed and there's very little space left, with eg. pictures and the like for around some years. Then it will be handy. 
For normal user? no.

---

### Post by jdong on 2006-08-18
Also, if you have some FAT32 drives (I don't know if NTFS-3G will safely defrag, but I wouldn't try it), it may be useful.

Something else to consider about fragmentation is, there's a big difference between:

**AAAAA**BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB**AAAAAA**

and

**AAAAA**B**AAAAA**


I have a feeling that when Linux filesystems fragment, the pieces are much closer together than similar fragmentation on Windows. That may explain why defragging doesn't get much back in terms of performance. With a modified filefrag backend, we should be able to measure the "radius of fragmentation", if you're serious about writing a worthwhile defragger.


Another point to keep in mind is that you could make free space **more** fragmented by the repeated attempts to copy fragmented files, which could cost you gravely in write performance.

---

### Post by jason.b.c on 2006-08-18
> **jdong said:**
> [http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

Here's my Python version. It's a bit more feature-complete and sane, in that it won't try to kill itself getting 3 fragments out of a 40GB file :)

 :)

Thanks man , I'll give it a shot...

---

### Post by tagra123 on 2006-10-09
I don't have windows dual booting anymore but use vmware instead and defrag from windows cannot work over the network so I defrag those old fat32 partitions using linux.

Not very elegant but works effectively.

Here's what I use to defrag the fat32 filesystems:

 ```
tar czvfC /tmp/some_fat32_filesystem.tgz /media/some_fat32_filesystem .
 rm -fr /mnt/some_fat32_filesystem/*
 tar xzvfC /tmp/some_fat32_filesystem.tgz /media/some_fat32_filesystem
```

---

### Post by marco999 on 2007-01-01
I updated the program so now it is called superdefrag for the description and you will find it in an attachment to my post. This is for all the folks who are annoyed that it wants to update the package via synaptic.

P.S This was my first Deb file compilation :D  Enjoy

[http://ubuntuforums.org/showthread.php?t=169551&page=4]("http://ubuntuforums.org/showthread.php?t=169551&page=4")

Now the command is superdefrag instead of defrag to run.
marco999

---

