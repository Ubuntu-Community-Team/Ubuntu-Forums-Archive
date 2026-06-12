---
title: "Ruby expert help needed with mp4ize script"
date: 2008-10-10
forum: Programming Talk
---

### Post by martynp on 2008-10-10
Hi All,

Is there a Ruby expert out there that can help to modify this script:

[http://thomer.com/howtos/mp4ize](http://thomer.com/howtos/mp4ize)

to show:

a) A percentage complete number/progress bar

b) time remaining

This is a brilliant script for converting avi to mp4 for the ipod and iphone but it isn't very forthcoming with it's progress. When you run it you get an output at the command line showing you things like file size, bit rate, and time (in seconds). You can check a little higher to see the length of the avi in hours and minutes, convert it to seconds and then you will know roughly when the conversion will finish by comparing the calculated number with the string on the command line. This so cries out for a percentage complete/time remaining indicator!

I am competent with Linux but not in programming and was wondering if any kind soul could either modify or supply the code required to produce what I would like.

Thanks so much in advance!

Martyn

---

### Post by airscex on 2008-10-11
&#20135;&#21697;&#20445;&#40092;,[&#33073;&#27687;&#21058;](http://www.dggrmy.com/tuoyangji/)&#24110;&#20320;&#25163;!

---

### Post by martynp on 2008-10-13
Sorry to bump... but still would love to see if this is possible?

Many Thanks

---

### Post by unutbu on 2008-10-13
martynp, I don't know Ruby. So the output is not pretty. But if you change
```

            elsif line.match(/time=([^\s]+)/)
              time = $1.to_f

```
to
```

            elsif line.match(/time=([^\s]+)/)
              time = $1.to_f
	      percent = (time/duration)*100
	      printf "%2g ", percent
            end

```
I think you'll get the percent completed.

---

### Post by Stochastic on 2008-10-13
You'll probably find more ruby experts over in the Programming Talk section of these forums.  Would you like this thread moved there?

---

### Post by martynp on 2008-10-13
Hi,

ubutnu........... thank for the effort but this threw up numerous errors!

Stochastic....... yes please, I guess I posted in the wrong section. Please move this thread and I will hope for answer from there.

Thanks

---

### Post by unutbu on 2008-10-13
Below is my copy of mp4ize. It seems to work on my system. (ruby version 1.8.6).

Would you please run it on yours and post the error messages?

---

### Post by martynp on 2008-10-13
Thanks for your reply.......

This is what I have done......

I open /usr/local/bin as root and open mp4ize in text editor. I then insert your lines (or replace with the whole of your script), save the file and close the editor.

If i then try to use the script it hangs just before encoding begins.. giving the standard error of 'can't figure out aspect ratio' and exits.

So, if go back into the script (as root again) and remove your lines of code the thing STILL fails as above. I can only get mp4ize to work again by dowloading a fresh copy.

I presume I CAN edit ruby scripts in the text editor. Am I corrupting the file or something? It certainly seems strange.

I can see that your code SHOULD work but am having trouble getting there.

Many Thanks,

Martyn

---

### Post by unutbu on 2008-10-13
Okay, let's test to make sure it has nothing to do with the editor.

Please download the script from my previous post again. Save it in your home directory as mp4ize.txt
Then type

```

sudo cp /usr/local/bin/mp4ize /usr/local/bin/mp4ize.bak
sudo mv ~/mp4ize.txt /usr/local/bin/mp4ize
sudo chown root:root /usr/local/bin/mp4ize
sudo chmod +x /usr/local/bin/mp4ize

```
Does it work now?

---

### Post by martynp on 2008-10-13
Hi again,

It sure does work.......... stupid GUI editors LOL 

Here is the output:

8.004470 frame= 4987 q=5.0 size=    6642kB time=207.7 bitrate=62.0kbits/s

The percentage is shown at the start!

Great Job.... I'll put some stress on it over the next few days but I sure this is fine! Great little enhancement and thanks for your time and effort!

Regards,

Martyn

---

### Post by syb0rz on 2010-09-14
This is a progress bar GUI for mp4ize for iPod video conversion or ffmpeg in general. This is my first bash script, and there are a couple of problems, but for the most part it works. This gets info from ffmpeg about the file and uses the ffmpeg vstats_file output to track conversion progress and displays a zenity progress bar.

Recommendations:
Ubuntu 10.04
ffmpeg 0.6 [[http://www.ffmpeg.org/download.html]](http://www.ffmpeg.org/download.html])
mp4ize ruby script [[http://thomer.com/howtos/ipod_video.html]](http://thomer.com/howtos/ipod_video.html]) link at the bottom

Setup:
1) Copy this code into /usr/local/bin/Convert-to-MP4
1.a) Edit your mp4ize script on line 39 to: ```
DEFAULT_ARGS = "-f mp4 -y -vcodec xvid -maxrate 1000 -qmin 3 -qmax 5 -g 300 -acodec aac -vstats_file .ffout.txt" 
```
2) sudo chmod +x /usr/local/bin/Convert-to-MP4
3) Ubuntu 10.04: Right click a video file, select properties, select 'Open With' tab, select Add, select 'Use a custom command', type Convert-to-MP4 and save your changes.
3.a) Repeat step 3 for any filetype you need
4) You can now right-click any file in Ubuntu 10.04 and convert without a terminal.

Convert-to-MP4 script:

```

#!/bin/bash
#Check for other instances
if [ "$(pidof ffmpeg)" ]
then
	zenity --error --text="Another instance of ffmpeg is already running."
	exit
fi

#Clean old log
rm .ffout.txt &

#Get file info from ffmpeg
fullpath="$1"
filepath=${fullpath%/*}
filename=${fullpath##*/}
extension=`echo $filename | awk -F . '{print $NF}'`
basefile=`basename "$filename" .$extension`
duration=( $(ffmpeg -i "$1" 2>&1 | sed -n "s/.* Duration: \([^,]*\), start: .*/\1/p") )
fps=( $(ffmpeg -i "$1" 2>&1 | sed -n "s/.*, \(.*\) tbr.*/\1/p") )
hours=( $(echo $duration | cut -d":" -f1) )
minutes=( $(echo $duration | cut -d":" -f2) )
seconds=( $(echo $duration | cut -d":" -f3) )
total_frames=( $(echo "(($hours*3600+$minutes*60+$seconds)*$fps)-20" | bc | cut -d"." -f1) )

#Check if .mp4 file already exists
if [ -e "$filepath/$basefile.mp4" ]
then
	zenity --error --text="$basefile.mp4 already exists."
	exit
fi

#Run conversion with -vstats_file .ffout.txt in your ffmpeg options, here its built into mp4ize
mp4ize "$1" &

#Call zenity progress bar
(
until [ $percentage == 99 ] ; do
	#Calculate percentage from ffmpeg output
	current_frame=( $(tail -1 .ffout.txt | grep frame= | gawk '{print $2}') )
	percentage=( $(echo "scale=2; ($current_frame/$total_frames)*100" | bc) )
	echo $percentage
	#If progress bar is cancelled kill ffmpeg and delete unfinished file
	#HELP: This sometimes doesn't work...
	if [ -z "$(pidof zenity)" ] ; then
		#HELP: How do I kill just this one instance/pid?
		#Otherwise, we can only kill this one-at-a-time.
		killall mp4ize
		sleep 1
		rm "$filepath/$basefile.mp4"
		exit
	fi
done
) | zenity --progress --percentage=0 --text="$filename" --title="Converting to MP4 for iPod" --width=400 --height=100

```

---

