---
title: "BASH: Killing the parent script if the child process fails"
date: 2010-07-23
forum: Programming Talk
---

### Post by prupert on 2010-07-23
Hi

I have a script that updates FFmpeg and x264 (you can find it here: [http://code.google.com/p/x264-ffmpeg-up-to-date/](http://code.google.com/p/x264-ffmpeg-up-to-date/)). I am trying to add better error checking to it, so that when something goes wrong with the building of FFmpeg or x264 the user gets some useful information and the script stops.

The way the script currently works, is that it runs the actual building of x264 and FFmpeg as a forked child process, to provide a nice progress indicator, keep the output clean and to allow the script to work on various version of Ubuntu and Linux Mint.

I have simple error checking in each stage of the forked child process, that gives a message if any part of the process fails. However, I don't know how to halt the parent process (the main script) if the child process fails, because the progress indicator gets in the way.

Here is a heavily edited version of the script to show where I am at the moment:


```
lucid_x264 ()
{
apt-get -y remove ffmpeg x264 libx264-dev 2> $LOG >> $LOG
if [ $? = 1 ];then
	echo "x264: error remove old versions"
	exit
fi
cd "$INSTALL"/x264
if [ $? = 1 ];then
	echo "x264: error navigating to x264 directory"
	exit
fi
#rest removed
}
#install ffmpeg
lucid_ffmpeg ()
{
cd "$INSTALL"/ffmpeg
if [ $? = 1 ];then
	echo "ffmpeg: error navigating to directory"
	exit
fi
make -j $NO_OF_CPUCORES distclean 2>> $LOG >> $LOG
if [ $? = 1 ];then
	echo "ffmpeg: error running make distclean"
	exit
fi
#rest removed
}
echo "script started" > $LOG
echo "Now running the update."
echo "Lets roll!"
echo "Now updating x264."
"$DISTRO"_x264 || error "Sorry something went wrong, please check the $LOG file." &
PID=$!
#this is a simple progress indicator
while ps |grep $PID &>/dev/null; do
	echo -n "."
	echo -en "\b-"
	sleep 1
	echo -en "\b\\"
	sleep 1
	echo -en "\b|"
	sleep 1
	echo -en "\b/"
	sleep 1
done
echo -e "\bDone"

echo "x264 updated."
echo
echo "Now updating ffmpeg."
"$DISTRO"_ffmpeg || error "Sorry something went wrong, please check the $LOG file." &
PID=$!
#this is a simple progress indicator
while ps |grep $PID &>/dev/null; do
	echo -n "."
	echo -en "\b-"
	sleep 1
	echo -en "\b\\"
	sleep 1
	echo -en "\b|"
	sleep 1
	echo -en "\b/"
	sleep 1
done
echo -e "\bDone"

echo "ffmpeg updated."
echo
echo "That's it, all done."
```

Anyone any idea how to get the forked child process to kill the parent, so it doesn't carry on, if the child process fails???

Cheers

---

