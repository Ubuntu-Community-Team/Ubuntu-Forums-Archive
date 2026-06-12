---
title: "HOWTO: A one-click way to download and play a series of video files from a web site"
date: 2008-04-01
forum: Outdated Tutorials &amp; Tips
---

### Post by chochem on 2008-04-01
If you've ever come across a web page with downloadable video content in several bite-sized clips, you're probably tired of the click-watch-click-watch-etc. routine. Even if you've got a download extension like downthemall or flashgot, you've still got to build the playlist. I have come up with a simple solution for this problem. Presented with such a page, you'll simply click the FlashGot icon, the downloads will start and when they're done, a VLC instance will pop up with all the downloaded files in the playlist.

(And never you mind 'where' one might encounter such pages... [:-p]("http://www.youtube.com/watch?v=eWEjvCRPrCo"))

[IMG]http://img371.imageshack.us/img371/4881/fg2gl6.png[/IMG]

This solution requires you to have the FlashGot extension in Firefox, a small download tool called axel (it's faster than wget) and VLC (though most video players can probably do just as well - you'll need to change the final line in the script to match).

Click [here]("apt:vlc") to get VLC and [here]("apt:axel") to get axel (by way of the repos - note the apt: links). To get FlashGot go to  [Firefox add-ons]("https://addons.mozilla.org/en-US/firefox/addon/220") and install the extension.

Copy-paste the following script and save it somewhere appropriate, like a script folder in your home directory (no need for it to be PATH'ed)
```
#! /bin/bash
# fg - a one-click way to download and play multiple video files
# by chochem

# download and log progress functions
axeldl () {
axel -o "$randomdir" "$url" && echo done >> "/tmp/fgprogress${randomnumber}"
}
xtaxeldl () {
xterm -e axel --alternate -o "$randomdir" "$url" && echo done >> "/tmp/fgprogress${randomnumber}"
}

# set universal variables
ufile="$*"
randomnumber=${RANDOM}

# get list of files from flashgot's [UFILE] parameter
randompl="/tmp/fgpl${randomnumber}"
cat "$ufile" | grep -E -e 'avi$|mpg$|wmv$|mov$' > "$randompl"

# create directory structure
if [ ! -d /tmp/playlists ]; then mkdir /tmp/playlists; fi
randomdir="/tmp/playlists/${randomnumber}"
mkdir "$randomdir"

# download files into directory structure
i=0
cat "$randompl" | while read url; do
	axeldl &
done

# run a loop waiting for all files to have downloaded
# when they are, run vlc with repeat-all set
totalcount=$(cat "$randompl" | wc -l)
while [ 1 ]; do
	donecount=$(cat "/tmp/fgprogress${randomnumber}" | wc -l)
	if [ $donecount -eq $totalcount ]; then
		vlc --loop "$randomdir"
		exit
	else
		sleep 1s
	fi
done

```
and allow everybody to run it by entering the following into a terminal:
```
chmod a+x [location and name of script, e.g. /home/user/bin/fg]
```

By default you'll not get any indication that anything's happening before it's done and VLC pops up - if you're on a slow connection and the silent wait bothers you, you can have axel report progress in a smal terminal window by changing the "axeldl &" line (line 29) to "xtaxeldl &".

[IMG]http://img525.imageshack.us/img525/2397/fg3fo8.png[/IMG]

Now we just need to configure FlashGot. Add the FlashGot icon to your navigation toolbar (right-click it and choose customize), click it so you get the dropdown menu, and choose 'More Options'. We need to set the script as a download manager for FlashGot, so in the 'General' tab, click 'Add' under 'Download Manager', enter an appropriate name, e.g. fgscript, and locate the script file by browsing to it. The 'Command line arguments template' value is what FlashGot passes of information to the script. Replace "[ URL ]" with "[UFILE]" and click OK. Note that the dropdown menu has fg set as the default way of using FlashGot but you can easily change it to act as a more general mass download handler by switching to e.g. wget or curl.

And that's it. Try it out by going [here]("http://www.linux.com/articles/114150"), and start FlashGot by clicking the icon in the navigation bar. (Despite there being three links in the article, there's only one file, so that's what you should get). Hope you enjoy.

---

### Post by chochem on 2008-04-03
I've altered the script so the downloads will run in parallel instead of one-after-the-other which certainly seems to have sped things up considerably. Less clicking, less waiting, more uhm whatever... :D

---

