---
title: "Move file with fast copy and zenity progress"
date: 2011-07-22
forum: Outdated Tutorials &amp; Tips
---

### Post by gasparov on 2011-07-22
Hi,
  this script is launched as
```
sh zenity-move.sh SOURCE DEST
```

io can also add the -z (gzip) or -j (bzip2) if you prefer to transfer files with compression.

It uses Fast Copy (from gentoo-wiki)

> cp uses character by character copy. Using the kernel pipes support, we could copy files block by block. tar converts the directories recursively into a single stream.At one end we create a single stream out of source directories and at other end we extract this stream and put it in the destination directory. The transfer between the two ends is by means of pipes.

tar -c src1/ src2/ | tar -C dest/ -xv

This is not necessarily faster, but is much more flexible. Note that ext2, ext3 and most modern Linux file systems have a capability called 'sparse files'. This is used to store large files with lots of zeroed content in an efficient manner. Most of the time you should not care about this, but certain programs make extensive use of this feature (e.g. net-p2p/mldonkey). You should be careful when copying sparse files using this method, as your disk usage can explode.Whereas the cp utility does handle sparse files automatically, tar does not. Sparse files in the source directory will be stored in full representation on the destination directory, unless the -S flag is used on the left hand side of the pipe. 

You will have a progress bar, elapsed time, ETA, data rate.

Stats are not precise because often the data rate can change a lot, for example if you transfer files between you hard disk to your usb storage key you'll probably see a high rate at the beginning that gets lower and stabilize on the correct value.
It is a work in progress because there are some bugs: when you hit cancel the tar processes are not killed because I still have to find out where the heck the exit code goes cause it seems i lose it.

```
###############################################
This script can be launched as: 
1)sh zenity-move.sh SOURCE DEST 
or
2)sh zenity-move.sh [-j|-z] SOURCE DEST 

1) moves files from directory SOURCE to DEST
2) same as 1 but using bzip2 (-j) or gzip (-z)

made by gasparov gas7119@gmail.com
###############################################
#! /bin/sh
TAR_OPTS=""
while getopts ":jz" opt; do
  case $opt in
    j)
      TAR_OPTS="-j"
      ;;
    z)
      TAR_OPTS="-z"
      ;;
    \?)
      echo "Invalid option: -$OPTARG" >&2
      exit 1
      ;;
    :)
      echo "Option -$OPTARG requires an argument." >&2
      exit 1
      ;;
  esac
done
shift $(($OPTIND - 1))
SOURCE=`echo "${1}" | sed -e "s/\/*$//" `
DEST=`echo "${2}" | sed -e "s/\/*$//" `
START=$(date +%s)
DEST2="$DEST"/"tmp.move123"
mkdir -p "$DEST2"
fullsize="$(du -bs $SOURCE | awk '{print $1}')"
size="0"
(      
	while [ "$size" != "$fullsize" ] ; do
		sleep 2
		if [ -a "$DEST2" ]  
			then
				size="$(du -bs "$DEST2" | awk '{print $1}')"
				progress="$(echo $size $fullsize | awk '{print 100*$1/$2}')"
				echo $progress
				NOW=$(date +%s)
				elapsed=$(($NOW - $START))		
				if [ "$elapsed" -gt 10 ] ; then
					if [ "$size" > 0 ] ; then
						TIME="$(($elapsed*$fullsize/$size))"
						TO="$((($size)/($elapsed*1024*1024)))"		
					fi 
					ETA2=$(($TIME - $elapsed))
					if [ "$ETA2" -lt 120 ] ; then
						ETA_output="$ETA2 sec"
					else
						ETA_output="$(($ETA2/60)) min"
					fi 
					if [ "$elapsed" -lt 120 ] ; then
						elapsed_output="$elapsed sec"
					else
						elapsed_output="$(($elapsed/60)) min"
					fi 

					echo "# Time: $elapsed_output  -  ETA: $ETA_output          Rate:$TO MB/s"
				else
					echo "# Waiting for stats"
				fi
		



		else
				echo 100
				echo "# FINISHED"
		fi
	done
)| zenity --progress --title="Moving from $SOURCE to $DEST" --auto-kill --percentage=0 & 
(cd "$SOURCE" && tar "$TAR_OPTS" -cf - *)|(cd "$DEST2" && tar "$TAR_OPTS" -xBpf -)
if [ "$?" = 1 ] ; then
        exit 0
	echo $?	
fi
mv "$DEST2"/* "$DEST"
rmdir "$DEST2"
notify-send -u normal -t 10000 "Transfer finished"
```

You can also find this script [on my blog]("http://www.lucagasperini.com/blog/2011-move-files-with-zenity-progress-bar/") with the pastebin iframe, have a look here or on my blog for updates, and if you have suggestions/modifications

Hope you like it :popcorn:

---

