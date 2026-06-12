---
title: "Download and playback google videos"
date: 2006-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by faizan on 2006-01-06
Hey,
I've been wanting to download google videos for a long time and I've played around with this whole thing a lot. Yesterday, I finally managed to successfully accomplish the task!

I'm sharing this trick so you all can, if you want, do the same. Keep in mind that even though after following these steps the videos will play on your ubuntu box without a hitch, you wont be able to fast forward. If I figure out how that can be done, I'll update this post.

Firstly, we need to setup your computer/media-player for playing Google videos. Google uploads the videos in flash video (.flv) format. Even though Ubuntu doesnt have a FLV player like windows, I found that Totem lets you play .flv format videos with gstreamer installed.

Step 1
Make sure that you have Totem Movie Player installed. Goto Application -> Sound & Video. If you see "Totem Movie Player" listed, you can skip the first step. If you dont, open Terminal and enter the following command..

```
sudo apt-get install totem
```

Step 2
Totem (and other media players) work on a specific sound engine. Many ubuntu users have the "Xine" engine installed with totem since Automatix installs Totem-xine. Since the plugin I found works with gstreamer, we need to remove xine and install gstreamer. Installing gstreamer will automatically remove xine. So enter this in the terminal to install gstreamer (do this even if you arent sure whether you have gstreamer or xine installed):

```
sudo apt-get install totem-gstreamer
```

Step 3
Now we need to make sure that all gstreamer plugins are installed. Enter this in the Terminal

```
sudo apt-get install gstreamer0.8-plugins
```

That sets up your Ubuntu machine and gets it ready to play those Google Videos. Now we must download them. Npte that I found a couple of websites on the net that automate this process for you but I'm not sure if those are gonna last or if those are reliable so I'll teach you the direct method to do this. Its fairly simple.

Google shadows the urls of the videos it uploads so we just need to "unhide" them. Goto video.google.com and search for the video you want. Click on the video. When the video opens in Firefox, goto View on the Menubar and hit Ctrl+U. You can also goto View on the Firefox Menubar and click Page Source. This lets you see the source of the page. Now hit Ctrl+F. This brings up the search. Type in "videourl". Copy everything after the = sign till the semicolon (;)

Now, in the address bar, type in 

```
javascript:unescape("paste-what-you-copied-here")
```
Hit enter. Firefox will now display the real url of the video. Copy that and paste it in the address bar and hit enter. Download manager should now show up. Save the video to disk. When its downloaded, rename it with a .flv extension. This step is not that necessary tho. Then open the video using totem and enjoy!

Hope this helps

Faizan

---

### Post by M4gi on 2006-02-06
Or You can try with [this]("http://my.opera.com/Magi/homes/files/googlevid-descargar.user.js") Greasemonkey script. Didn't test it in FX, but in Opera works great. This script ads download video link on page. ;)

---

### Post by ice60 on 2006-02-06
i find the easiest way is to click where it says download. since this howto was written google video has changed abit.

---

### Post by raggamuffin on 2006-03-10
i have some .flv from a next site that i can't get to play in totem (or any other media player)...

i have all the aforementioned packages installed, but all totem gives me is an error message, "Could not determine type of stream"...


any ideas/suggestions on how to get playback...or convert .flv to a decent format?...

---

### Post by ixus_123 on 2006-03-11
Thanks - this is useful for those videos that google doesn't have a download button for

---

### Post by Steve S. on 2006-05-27
The same type of concept works for youtube videos as well, and they don't usually give the option to download.

I can replay flv files in totem, but no sound, and can't play the flv files in any other media player (mplayer is the preferred one).  Any ideas on this?

---

### Post by adamkane on 2006-05-27
videodownloader firefox extension.

---

### Post by Stroganoff on 2006-05-28
VLC can play *.flv videos.

---

### Post by Steve S. on 2006-05-28
I tried the Firefox extension before this, but I tried it again, adamkane.  I get the same error message:
> Firefox could not install this item because of a failure in Chrome Registration.  Please contact the author about this problem.

Any ideas?

Thanks for the tip on VLC, Stroganoff, never tried it before even though I've had it, and it seems to be a pretty good player.  However, when I try to play that file, it doesn't play it and the gui usually shuts down.  When played from comand line, I get:
> [00000281] access_file access error: seeking too far

Any ideas?

---

### Post by Steve S. on 2006-05-28
...and as far as the chrome registration thing goes, I checked out [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) but I already am running firefox 1.5 so it shouldn't apply, should it?

Oh, checked out:
[http://www.ubuntuforums.org/showthread.php?t=98266&highlight=Chrome+registration](http://www.ubuntuforums.org/showthread.php?t=98266&highlight=Chrome+registration)
and it was right, disabling the talkback option seemed to take care of the Chrome registration problem.

So, it seems the videodownloader ext. took.  Now, how do I use that? (nothing seems obvious to me...)

---

### Post by Steve S. on 2006-05-28
Got the videodownloader thing working, thanks to adamkane and the google search.

Now I just need to be able to play or convert the flv files.  Tips?  Hints?

---

### Post by Stroganoff on 2006-05-28
The windows build of VLC plays *.flv for sure. Nevermind, I just opened the file with Totem Movie Player - it works!

(Breezy + "Automatix")

---

### Post by Steve S. on 2006-05-28
You got totem to play with sound?  I can get it to play the flv files but I get no sound.  How did you get sound on those files?

---

### Post by paracetamolo on 2006-05-29
I have no sound too](*,)

---

### Post by bowsercake on 2006-05-30
I can get .flv to play in Totem but it skips (i think it's streaming?) and there is no sound.  I got the from youtube btw. (I tried VLC media player but that didn't work at all).

---

### Post by Steve S. on 2006-05-30
Hey, all,

Check out the results I posted on this one:
[http://ubuntuforums.org/showthread.php?t=139166](http://ubuntuforums.org/showthread.php?t=139166)

I used the downloader, then ran ffmpeg in comand line (pretty easy once you get the hang of it) and changed it to an mpeg.  Then you can play it on pretty much whatever...

Hope that helps.  If you come up with an easier/better way, please post.

---

### Post by simms on 2006-06-06
if anyone's interested, once you get your FLV support working, you can get fresh Reuters news footage via [http://today.reuters.com/rss/newsrss.aspx]("http://today.reuters.com/rss/newsrss.aspx"). 
just click on one of the feed buttons, grok the FLV file addresses in the output, and enjoy :wink:

---

### Post by dartakaum on 2006-06-06
[QUOTE=ice60]i find the easiest way is to click where it says download. since this howto was written google video has changed abit.[/QUOTE]

that was what i was going to say.

the funny stuff is thank god google don't have linux version of video.google, because  u can only download videos (*.avi) in linux.

---

### Post by Lunar_Lamp on 2006-08-02
I wrote the following script to enable the conversion of flv files to mpg files.  It's commented fairly heavily, so you should be able to see what's going on where.  At the moment it can only deal with 1 file at a time, but if people are interested I can try and make it deal with more than one.  Just save this file as /usr/bin/flvconvert and chmod +x it.  To use, just type flvconvert FILENAME.  It requires ffmpeg which is available in the repositories (I'm afraid I don't know where from as it was already installed on my laptop when I wanted to use it).

```
#!/bin/bash
#
# script written by Ed Hargin to convert flvs from places like youtube and googlevideos to mpg files.
#
# note to self: $1 = 'flv filename'
#
#   todo:
# - make the script able to deal with multiple files
# - enable input variable to be the url, and make the script find the correct url to download and then convert?

flv_file=$1

####################
# Convert Function #
####################
#this coverts the flv file specified ($1) to mpg

function convert {
	ffmpeg -i $flv_file -ab 56 -ar 22050 -b 500 -s 320x240 $name.mpg
}  

# Variables declared in above line (brackets are defaults used if option is omitted) 
#
# -ab = averate bitrate of music in kbit/s (default = 64)
# -ar = audio sampling frequency (default = 44100 Hz)
# -b  = video bitrate in kbit/s (default = 200 kb/s)
# -s  = set frame size (wxh) (default = 160x128)

###################
# Rename Function #
###################
#this function asks what you want to call the new file created, and acts accordingly.

rename ()
{
echo "By default the file will be named $flv_file.mpg - do you want to change this? (Y/N)"
read rename_answer
	if [ "$rename_answer" = "y" ];
		then echo "What do you want to call it? (.mpg will automatically be appended to the filename)"
		read name
		echo "Converting flv file to $name.mpg"

	else [ "$rename_answer" = "n" ];
		name=$flv_file.mpg
		echo "Converting file to $name"

	fi
}


#####################
# Deletion Function #
#####################
#this function asks if you want to delete the original file and acts accordingly.

function flvdelete {

	echo "Do you want to delete the original flv file? (Y/N)"

	read reply

	if [ "$reply" = "y" ];
 		then rm $flv_file
		echo "File deleted: $flv_file"  #should I build in some kind of detection of 'need to be root to delete'?

	elif [ "$reply" = "n" ];
 		then echo "Leaving file alone: $flv_file"

	fi
}

###############
# Main Script #
###############

rename ;
convert ;
flvdelete 

exit

```

---

### Post by Steve S. on 2006-08-02
Cool!  Thanks, Lunar_lamp.  But would you explain more in detail how to do this part:
> chmod +x it.

Thanks for the script!  It should make things much easier...

---

### Post by Cynical on 2006-08-02
Hes saying type the command 'chmod +x filename' so his script will be executable. And thanks for the script btw

---

### Post by Steve S. on 2006-08-02
> **Cynical said:**
> Hes saying type the command 'chmod +x filename' so his script will be executable. And thanks for the script btw

Rockin'.:D

---

### Post by wog on 2006-08-13
Clearly I don't understand quite yet how to set permissions properly.

I copy and pasted the script (thank you for the script)

I copied the script file to /usr/bin, which required sudo to accomplish.

and then I changed the permissions on the file:
```
chmod +x flvconvert
```

Yet when I try to use the command, I get permission denied.

What am I doing wrong?

---

### Post by lordsavant on 2006-08-13
> **wog said:**
> Clearly I don't understand quite yet how to set permissions properly.

I copy and pasted the script (thank you for the script)

I copied the script file to /usr/bin, which required sudo to accomplish.

and then I changed the permissions on the file:
```
chmod +x flvconvert
```

Yet when I try to use the command, I get permission denied.

What am I doing wrong?

You don't need to copy the file to your /usr/bin directory.  You can run it from anywhere.  If you must have it in your /usr/bin directory, though, you need to run the chmod command with super-user permissions (sudo).

---

### Post by wog on 2006-08-13
Okay, I did this in /usr/bin
```
sudo chmod +x flvconvert
```

It still doesn't work. I get permission denied.

Is there something else I need to do or does this indicate a more widespread problem than just permissions on a script file?

---

### Post by Lunar_Lamp on 2006-08-14
I don't know why that is happening, it seems strange - are you sure you are typing this exactly correctly?

```
cd /usr/bin
sudo chmod +x flvconvert
[your password when requested to enter it]
```

Anyway, if you don't want to investigate why this is may be happening, here is an alternate solution:

 - copy and paste the script I wrote into a blank document using gedit (or other editor of choice), and save it in your home directory.  I have a directory for scripts, so I save mine in ~/scripts (remember, you can use ~ to mean your home director).
 - open a terminal and cd to the directory you saved it in (e.g. cd ~/scripts)
 - to check you're in the right directory type "ls" to list the files in your current directory.
 - if you want to check that the script contains what you think it contains, type 'less flvconvert' which will display the contents of the file.  Use enter to scroll down, and 'q' to exit.
 - to make the script executable type 'chmod +x flvconvert'
 - to use the script you will have to type the full pathname of the script, i.e. /home/wog/scripts/flvconvert FILENAME

I hope this helps, but sorry, I can't think why you can't use 'sudo chmod +x FILE' in /usr/bin.  It seems very strange to me, but I'm pretty new to linux, so I'm not the best person to ask.

---

### Post by Steve S. on 2006-12-28
> **Lunar_Lamp said:**
> I wrote the following script to enable the conversion of flv files to mpg files.  It's commented fairly heavily, so you should be able to see what's going on where.  At the moment it can only deal with 1 file at a time, but if people are interested I can try and make it deal with more than one.  Just save this file as /usr/bin/flvconvert and chmod +x it.  To use, just type flvconvert FILENAME.  It requires ffmpeg which is available in the repositories (I'm afraid I don't know where from as it was already installed on my laptop when I wanted to use it).

```
#!/bin/bash
#
# script written by Ed Hargin to convert flvs from places like youtube and googlevideos to mpg files.
#
# note to self: $1 = 'flv filename'
#
#   todo:
# - make the script able to deal with multiple files
# - enable input variable to be the url, and make the script find the correct url to download and then convert?

flv_file=$1

####################
# Convert Function #
####################
#this coverts the flv file specified ($1) to mpg

function convert {
	ffmpeg -i $flv_file -ab 56 -ar 22050 -b 500 -s 320x240 $name.mpg
}  

# Variables declared in above line (brackets are defaults used if option is omitted) 
#
# -ab = averate bitrate of music in kbit/s (default = 64)
# -ar = audio sampling frequency (default = 44100 Hz)
# -b  = video bitrate in kbit/s (default = 200 kb/s)
# -s  = set frame size (wxh) (default = 160x128)

###################
# Rename Function #
###################
#this function asks what you want to call the new file created, and acts accordingly.

rename ()
{
echo "By default the file will be named $flv_file.mpg - do you want to change this? (Y/N)"
read rename_answer
	if [ "$rename_answer" = "y" ];
		then echo "What do you want to call it? (.mpg will automatically be appended to the filename)"
		read name
		echo "Converting flv file to $name.mpg"

	else [ "$rename_answer" = "n" ];
		name=$flv_file.mpg
		echo "Converting file to $name"

	fi
}


#####################
# Deletion Function #
#####################
#this function asks if you want to delete the original file and acts accordingly.

function flvdelete {

	echo "Do you want to delete the original flv file? (Y/N)"

	read reply

	if [ "$reply" = "y" ];
 		then rm $flv_file
		echo "File deleted: $flv_file"  #should I build in some kind of detection of 'need to be root to delete'?

	elif [ "$reply" = "n" ];
 		then echo "Leaving file alone: $flv_file"

	fi
}

###############
# Main Script #
###############

rename ;
convert ;
flvdelete 

exit

```

Oh, great job on the script!  It works great!   

FYI The first file converted was an old Saturday Night Live "commercial" skit: Happy Fun Ball.  Hilarious!

Thanks again!

---

