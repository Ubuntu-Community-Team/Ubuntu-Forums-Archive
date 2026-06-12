---
title: "Truewipe - Wipe a drive or file with random data"
date: 2008-04-13
forum: Programming Talk
---

### Post by PR0M37H3U5 on 2008-04-13
I wrote a bash script called Truewipe that will overwrite a file or device with random data from truecrypt. This is about 10x faster than trying to use data from /dev/urandom. It's also easier. My script automatically detects your version of Truecrypt and will work with both 4.3 and 5.1 Now I share it with the Internets. Have Fun!

- Note this script normally uses two other scripts I wrote: [[COLOR="DarkSlateBlue"]extractor[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4712387") to print it's help manual and [[COLOR="DarkSlateBlue"]randomkey[/COLOR]]("http://ubuntuforums.org/showthread.php?p=4712303") to generate random data. It will function without these and still be cryptographically secure.
Randomkey: [http://ubuntuforums.org/showthread.php?p=4712303](http://ubuntuforums.org/showthread.php?p=4712303)


```

#Wipe a partition with truecrypt.
#Uses random data provided by randomkey
#Written by PR0M37H3U5

print_usage() 
{ extractor -d -f $0 -t @manual@ ;}

hash=sha256sum

#Truecrypt Default Options
truehash='RIPEMD-160'
encryption='AES'

#Get Options
while getopts 'e:h:n:s:t:' OPTION
do
  case $OPTION in
  e)	encryption=$OPTARG;;
  h)	truehash=$OPTARG;;
  n)	wipes=$OPTARG;;
  s)	seed=$OPTARG;;
  t)    target=$OPTARG;;
  ?)	print_usage; exit 2;;
  esac
done
shift $(($OPTIND - 1))

#Alternate Options
if [ ! $target ]; then target=$1; fi
if [ ! $wipes ]; then 
	if [ $2 ]; then 
		wipes=$2
	else
		wipes=3
	fi
fi
if [ $3 ]; then seed=$3; fi

#Find an empty RamDisk and fill it with randomness
ramdisk=/dev/ram
nums=$(mount | grep /dev/ram | sed 's/ .*//' | sort -r | tr -d '\n''/dev/ram' )
if [ -z $nums ]; then nums="1"; fi	#if nums is empty, tr will bug
ramdisk+=`echo "9876543210" | tr -d $nums | head -c 1`

echo -n "Adding random data to Ram Disk $ramdisk..."
dd if=/dev/random bs=8 count=4 of=$ramdisk 2>/dev/null	  #First 32 bytes are from /dev/random
randomkey | dd bs=8 seek=4 of=$ramdisk 2>/dev/null		  #Next 32 bytes are from randomkey
dd if=/dev/urandom bs=64 count=2 of=$ramdisk seek=1 2>/dev/null #Next 64 bytes are from /dev/urandom
echo "Done"

#Get Truecrypt version
if [ "$(truecrypt --text 2>&1 | grep 'unrecognized option')" ]; then 
	version=$(truecrypt --version | head -n 1| sed 's/.* //')
else
	version=$(truecrypt -t --version | sed 's/.* //' )
fi

#Determine options for truecrypt call
version=$(echo $version | head -c 1)	#look only at the major number
if [ $version = "5" ]; then
	options="--text --volume-type="normal" --filesystem="none" --hash=$truehash --encryption=$encryption --keyfiles=''"
	randomsource="--random-source=$ramdisk"
elif [ $version = "4" ]; then
	options="--type 'normal' --overwrite --filesystem 'none' --hash $truehash --encryption $encryption --keyfile ''"
	randomsource="--random-source $ramdisk"
else
	echo "I have know idea if this will work for truecrypt versions other than 4.3 and 5.1"
	echo "If you want to try anyway, press enter, otherwise press Ctrl+c"
	read continue
	options="--type 'normal' --overwrite --filesystem 'none' --hash $truehash --encryption $encryption --keyfile ''"
	randomsource="--random-source $ramdisk"
fi


####Create encrypted volumes

#The First wipe uses /dev/random and prompts for additional randomness.
eval truecrypt $options \
	-p $(echo \
		$(dd if=/dev/random bs=8 count=2 2>/dev/null | $hash -b )\
		$(randomkey $seed) \
		| $hash | head -c 64) \
	--create $target
	#Password is 8*2*2=32 chars from /dev/random and 32 chars from randomkey
	#random source is the user
wipes=$(($wipes-1))

#Subsequent wipes use the ramdisk as a random source and do not prompt for anything
while [ $wipes -gt 0 ]; do
	echo "$wipes wipes remaining..."
	#after every wipe hash some of the last run with the ramdisk to keep it changing
	echo \
		$(dd if=$target bs=1K count=64 2>&1)\
		$(dd if=$ramdisk bs=128 count=2 2>&1)\
		| sha512sum -b \
		| dd bs=128 seek=1 of=$ramdisk 2>/dev/null
	
	eval truecrypt $options \
		-p $(echo \
			$(dd if=/dev/urandom bs=256 count=1 2>&1 | $hash)\
			$(dd if=$ramdisk bs=64 count=3 2>&1 | $hash)\
			$(randomkey $seed) \
			| $hash | head -c 64 \
			) \
		$randomsource --create $target
	#password is a 64 char hash of [256 bytes of urandom],[64*3 bytes of $ramdisk] and [randomkey]
	#random source is all of ramdisk
	wipes=$(($wipes-1))
done
echo -n "Wipe completed, cleaning up..."

#Cleanup
dd if=/dev/urandom of=$target bs=512 count=1 conv=notrunc 2>/dev/null	#destroy volume header
dd if=/dev/urandom of=$ramdisk bs=1K count=1 2>/dev/null	#destroy ramdisk
dd if=/dev/zero of=$ramdisk bs=1K count=1 2>/dev/null	        #zero it out

echo "Done"
exit 0

@manual@
Truewipe will overwrite a device or file with random data from truecrypt. 
This will cause UNRECOVERABLE DATA LOSS.

Usage:	truewipe [options] (device or file) (number of wipes)

Required:
	-t target
Optional:
	-e encryption (default AES)
	-h hash	      (default RIPEMD-160)
	-n wipes      (default 3)
	-s seed	- Random string of characters (not required)
	
Examples:
	#Wipe the first partition on the first hard drive 8 times.
	truewipe -t /dev/sda1 -n 8
	truewipe /dev/sda1 8

@manual@

```

If you want to see how this works without data loss change the eval  statements to echos and comment out the cleanup section.

---

### Post by mrsteveman1 on 2008-04-13
Thats a nice script, and definitely a needed function. I hate using urandom exclusively for wiping drives, though if i remember right, shred and the other one (in the repos) are a bit faster. Truecrypt is of course much faster so this is a great use of TC.

I read most of the script and i know bash fairly well, but this screen is giving me a headache. Are you wiping one pass or multiple passes?

It's been my understanding that one wipe with suitably random data is as good as anything, though more wipes only cost you time.

---

### Post by PR0M37H3U5 on 2008-04-13
> **mrsteveman1 said:**
> I read most of the script and i know bash fairly well, but this screen is giving me a headache. Are you wiping one pass or multiple passes?



$wipes is the number of wipes left. After each pass, $wipes is decremented until it reaches 0. If 
```
while [ $wipes -gt 0 ]
``` returns true, then the script will do another pass, decrement $wipes and check the value of $wipes again.

As an example you can specify 1 wipe with
truewipe /dev/sda1 1

> It's been my understanding that one wipe with suitably random data is as good as anything, though more wipes only cost you time.

This is the opinion of most people. However, some people don't feel safe with just 1 so you can specify as many wipes as you like. Right now, the default is 3 which meets government standards for secure data erasure.

---

### Post by LaRoza on 2008-04-13
> **PR0M37H3U5 said:**
> 
This is the opinion of most people. However, some people don't feel safe with just 1 so you can specify as many wipes as you like. Right now, the default is 3 which meets government standards for secure data erasure.

[http://en.wikipedia.org/wiki/National_Industrial_Security_Program](http://en.wikipedia.org/wiki/National_Industrial_Security_Program)

There is a bit more to it than that...

---

### Post by mrsteveman1 on 2008-04-13
Excellent :D

I do know some laws (maybe HIPPA or SOX?) require data to be destroyed in certain ways, so yea in that case multiple wipes may be required.

---

### Post by PR0M37H3U5 on 2008-04-13
Hey Guys, I've posted those two scripts that Truewipe uses:
Randomkey: [http://ubuntuforums.org/showthread.php?p=4712303](http://ubuntuforums.org/showthread.php?p=4712303)
Extractor: [http://ubuntuforums.org/showthread.php?p=4712387](http://ubuntuforums.org/showthread.php?p=4712387)

I have more stuff i've been working on that I want to share. I will continue to post in this forum unless someone tells me a better place to post all of these scripts I've been writing.:)

---

### Post by nanotube on 2008-04-14
> **PR0M37H3U5 said:**
> Hey Guys, I've posted those two scripts that Truewipe uses:
Randomkey: [http://ubuntuforums.org/showthread.php?p=4712303](http://ubuntuforums.org/showthread.php?p=4712303)
Extractor: [http://ubuntuforums.org/showthread.php?p=4712387](http://ubuntuforums.org/showthread.php?p=4712387)

I have more stuff i've been working on that I want to share. I will continue to post in this forum unless someone tells me a better place to post all of these scripts I've been writing.:)

nice scripts! :)

i'd suggest that, if you have quite a few things to post, you might set up some personal site somewhere where you can post your work, so that you can point to it and say "there's all the stuff i wrote". 

keep making posts here with the announcements, though. :)

---

### Post by Tuna-Fish on 2008-04-14
> **mrsteveman1 said:**
> 
It's been my understanding that one wipe with suitably random data is as good as anything, though more wipes only cost you time.

Depends on your definition for as good as anything. It has been shown that data that has been overwritten several times can be read by magnetic force microscopes. However, the work that has been done so far has really been more of a proof-of- concept, and as far as I know, large amounts of overwritten data has never been recovered from a modern HDD. 

In any case, at least the US government no longer accepts overwriting at all as a file sanitization method. This is more likely due to the fact that all modern disk drives silently remap sectors that have recoverable read errors than because the fed thinks that terrorists have MFM's.

Very interesting piece on the subject of data recovery in general, and of the many difficulties in recovering the actual user data even if the raw analog data can be recovered from the hd:

[http://www.actionfront.com/whitepaper/Drive-Independent%20Data%20Recovery%20Ver14Alrs.pdf](http://www.actionfront.com/whitepaper/Drive-Independent%20Data%20Recovery%20Ver14Alrs.pdf)

---

### Post by LaRoza on 2008-04-14
> **Tuna-Fish said:**
> 
In any case, at least the US government no longer accepts overwriting at all as a file sanitization method. This is more likely due to the fact that all modern disk drives silently remap sectors that have recoverable read errors than because the fed thinks that terrorists have MFM's.


I imagine that they are more concerned with other governments than terrorists...

---

