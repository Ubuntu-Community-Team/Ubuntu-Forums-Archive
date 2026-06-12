---
title: "rtorrent ffmpeg Script"
date: 2010-05-18
forum: Programming Talk
---

### Post by domzz on 2010-05-18
I wonder how hard this would be to script... download torrent using rtorrent, wait for torrent to download, convert video, reupload torrent to rtorrent. Would this be a bash script?

---

### Post by domzz on 2010-05-18
Here is a sample auto downloading.

[http://craig.backfire.ca/pages/computers/tv](http://craig.backfire.ca/pages/computers/tv)

---

### Post by domzz on 2010-05-18
[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Movecompletedtorrents](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Movecompletedtorrents)

Move completed torrents 

When the torrent finishes, it executes "mv <base_path> ~/Download/" and then sets the destination directory to "~/Download/". (0.8.4+) 

system.method.set_key = event.download.finished,move_complete,"execute=mv,-u,$d.get_base_path=,~/Download/;d.set_directory=~/Download/"


Can I change this to something like:
system.method.set_key = event.download.finished,"ffmpeg -i some_movie.avi -f mp4 -vcodec xvid -maxrate 1000 \
       -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac \
       -s 320x180 -padtop 30 -padbottom 30 \
       -ab 128 -b 400 some_movie.mp4",
move_complete,"execute=mv,-u,$d.get_base_path=,~/Download/;d.set_directory=~/Download/"

---

### Post by domzz on 2010-05-19
I need a bash script that will.
So here is what I made so far.

1. Convert video files to iPhone format
2. MV converted video to new directory (with domain.com attached to it)
4. Copy a NFO file (from another directory) and add some conversion information
5. Delete old directory
torrent stuff (rtorrent)
6. Make a torrent file out of new converted video directory

```
#!/bin/bash
# ffmpeg and mencoder script
# Grab thumb from avi, start encoding to ITU h264 using mencoder, ffmpeg is doing thumb processing

# Bash script for operating system Ubuntu 8.10 
# packages used : FFMPEG, MENCODER ,MPLAYER ENCODING ENGINE
# VIDEO CODEC ITU H264 AUDIO MP3


# Written by FakeOutdoorsman and updated by mysoogal and modified by Domzz
# Attribution-Noncommercial 3.0 Unported
# http://creativecommons.org/licenses/by-nc/3.0/deed.en
# trackback http://ubuntuforums.org/showthread.php?t=960627

# Location of source videos READ this !!! add your user name !
sourcelocation="/var/www/videos/"
# Extension of source videos
sourceext="avi,mpg,mpeg,mov,rmvb,rm,ogm,4v

#http://thomer.com/howtos/ipod_video.html
find ${sourcelocation} -iname "*${sourceext}" -exec mp4ize {}.mp4
# Check to see if videos were encoded, then delete source vids and shutdown
if [ -e "${sourcelocation}/*.avi" ] && [ -e "${sourcelocation}/*.mp4]; then
	# Delete videos	
	rm ${sourcelocation}/*.avi
	rm ${sourcelocation}/*.mpeg
	rm ${sourcelocation}/*.mov
	rm ${sourcelocation}/*.mpg
	rm ${sourcelocation}/*.txt
	rm ${sourcelocation}/*.nfo
	#copys a txt file from my directory to sources directory
	cp /home/admin/file.txt ${sourcelocation}
	#moves directory
	mv ${sourcelocation} /home/admin/${sourcelocation}_domain.com
	#builds the torrent file using: http://claudiusmaximus.goto10.org/cm/torrent.html
	#http://www.torrent-invites.com/tutorials/52022-putty-complete-tutorial.html
	cd /home/admin
	mktorrent -v -p -a http://tracker.url -o ${sourcelocation}_domain.com.torrent ${sourcelocation}_domain.com
else
	echo "Encoding FAILED"
fi

exit
```

---

### Post by domzz on 2010-05-19
I need a bash script that will.
So here is what I made so far.

1. Convert video files to iPhone format
2. MV converted video to new directory (with domain.com attached to it)
4. Copy a NFO file (from another directory) and add some conversion information
5. Delete old directory
torrent stuff (rtorrent)
6. Make a torrent file out of new converted video directory

```
#!/bin/bash
# ffmpeg and mencoder script
# Grab thumb from avi, start encoding to ITU h264 using mencoder, ffmpeg is doing thumb processing

# Bash script for operating system Ubuntu 8.10 
# packages used : FFMPEG, MENCODER ,MPLAYER ENCODING ENGINE
# VIDEO CODEC ITU H264 AUDIO MP3


# Written by FakeOutdoorsman and updated by mysoogal and modified by Domzz
# Attribution-Noncommercial 3.0 Unported
# http://creativecommons.org/licenses/by-nc/3.0/deed.en
# trackback http://ubuntuforums.org/showthread.php?t=960627

# Location of source videos READ this !!! add your user name !
sourcelocation="/var/www/videos/"
# Extension of source videos
sourceext="avi,mpg,mpeg,mov,rmvb,rm,ogm,4v

#http://thomer.com/howtos/ipod_video.html
find ${sourcelocation} -iname "*${sourceext}" -exec mp4ize {}.mp4
# Check to see if videos were encoded, then delete source vids and shutdown
if [ -e "${sourcelocation}/*.avi" ] && [ -e "${sourcelocation}/*.mp4]; then
	# Delete videos	
	rm ${sourcelocation}/*.avi
	rm ${sourcelocation}/*.mpeg
	rm ${sourcelocation}/*.mov
	rm ${sourcelocation}/*.mpg
	rm ${sourcelocation}/*.txt
	rm ${sourcelocation}/*.nfo
	#copys a txt file from my directory to sources directory
	cp /home/admin/file.txt ${sourcelocation}
	#moves directory
	mv ${sourcelocation} /home/admin/${sourcelocation}_domain.com
	#builds the torrent file using: http://claudiusmaximus.goto10.org/cm/torrent.html
	#http://www.torrent-invites.com/tutorials/52022-putty-complete-tutorial.html
	cd /home/admin
	mktorrent -v -p -a http://tracker.url -o ${sourcelocation}_domain.com.torrent ${sourcelocation}_domain.com
else
	echo "Encoding FAILED"
fi

exit
```

---

### Post by domzz on 2010-05-19
Really important... anyone?

---

### Post by domzz on 2010-05-19
Im not sure if I should do 

	rm ${sourcelocation}/*.avi
	rm ${sourcelocation}/*.mpeg
	rm ${sourcelocation}/*.mov
	rm ${sourcelocation}/*.mpg
	rm ${sourcelocation}/*.txt
	rm ${sourcelocation}/*.nfo

or if there is a quicker way

---

### Post by domzz on 2010-05-19
I changed it a bit further


```
#!/bin/bash
# ffmpeg and mencoder script
# Grab thumb from avi, start encoding to ITU h264 using mencoder, ffmpeg is doing thumb processing

# Bash script for operating system Ubuntu 8.10 
# packages used : FFMPEG, MENCODER ,MPLAYER ENCODING ENGINE
# VIDEO CODEC ITU H264 AUDIO MP3


# Written by FakeOutdoorsman and updated by mysoogal and modified by Domzz
# Attribution-Noncommercial 3.0 Unported
# http://creativecommons.org/licenses/by-nc/3.0/deed.en
# trackback http://ubuntuforums.org/showthread.php?t=960627

# Location of source videos READ this !!! add your user name !
sourcelocation="/home/domz/torrents/"
# Extension of source videos
sourceext="avi,mpg,mpeg,mov,rmvb,rm,ogm,4v"
# Wait while any other ffmpeg processes are running
while [ -n "$(ps -ef | egrep "ffmpeg|HandBrakeCLI" | grep -v grep)" ];
do
        echo -e "\n[$(date +%b\ %d\ %Y:\ %H:%M:%S)]\nFound another instance of HandBrake or ffmpeg running, pausing 5 minutes..."
        sleep 300
done
#http://thomer.com/howtos/ipod_video.html
find ${sourcelocation} -iname "*${sourceext}" -exec HandBrakeCLI -i {} -o ${}.mp4  -e x264 -q 0.589999973773956 -a 1 -E faac -B 128 -R 48 -6 dpl2 -f mp4 -X 480 -m -x level=30:cabac=0:ref=2:mixed-refs:analyse=all:me=umh:no-fast-pskip=1
# Check to see if videos were encoded, then delete source vids and shutdown
if [ -e "${sourcelocation}/*.avi" ] && [ -e "${sourcelocation}/*.mp4]; then
	# Delete videos	
	for ext in avi mpeg mov mpg txt nfo; do rm ${sourcelocation}/*.$ext; done	
	#copys a txt file from my directory to sources directory
	cp /home/domz/file.txt ${sourcelocation}
	#moves directory
	mv ${sourcelocation} /home/admin/${sourcelocation}_domain.com
	#http://www.torrent-invites.com/tutorials/52022-putty-complete-tutorial.html
	cd /home/domz
	mktorrent -v -p -a http://tracker.url -o {sourcelocation}_domain.com.torrent /home/domz/torrents
else
	echo "Encoding FAILED"
fi

exit
```

---

### Post by domzz on 2010-05-19
Can anyone tell me how to convert inside my subdirectories instead of main dir?

like 

Main Dir
    -Sub Dir1
    -Sub Dir2

I want the script to execute on each subdirectory.

---

### Post by domzz on 2010-05-19
Can anyone help plz?

---

### Post by domzz on 2010-05-19
I need my script to:
Go to each subdirectory of and convert avi/mpeg etc to MP4.

/home/domz/torrents
[INDENT][COLOR="Red"]->Subdirectory1[/COLOR][/INDENT]
[INDENT][COLOR="Red"]->Subdirectory2[/COLOR][/INDENT]
etc

-I got the AVI part working, but it converts and [COLOR="red"]names the files .avi.mp4[/COLOR]

Then I want to check if it has convert, if it has it moves mp4 to new folder, adds a text file (static file) to that folder and deletes the whole subdirectory, makes a torrent with mktorrent. 

Then it goes to the next directory.




```
#!/bin/bash
# ffmpeg and mencoder script
# Go to main dir, check for subdir, grab avi, convert with handbrake, mv file to new directory, delete old directory, make torrent out of new directory.


# Written by FakeOutdoorsman and updated by mysoogal and modified by Domzz
# Attribution-Noncommercial 3.0 Unported

# Location of source videos READ this !!! add your user name !

sourcelocation=
sourcedir="/home/domz/torrents"

# Extension of source videos
sourceext="avi"

# Wait while any other ffmpeg processes are running
while [ -n "$(ps -ef | egrep "ffmpeg|HandBrakeCLI" | grep -v grep)" ];
do
        echo -e "\n[$(date +%b\ %d\ %Y:\ %H:%M:%S)]\nFound another instance of HandBrake or ffmpeg running, pausing 5 minutes..."
        sleep 300
done

#http://thomer.com/howtos/ipod_video.html

find ${sourcedir} -iname "*${sourceext}" -exec HandBrakeCLI -i {} -o {}.mp4  -e x264 -q 0.589999973773956 -a 1 -E faac -B 128 -R 48 -6 dpl2 -f mp4 -X 480 -m -x level=30:cabac=0:ref=2:mixed-refs:analyse=all:me=umh:no-fast-pskip=1 \;
# Check to see if videos were encoded, then delete source vids

if [ -e "${sourcedir}/*.avi" ] && [ -e "${sourcedir}/*.mp4]; then
	# Delete videos	
	for ext in avi mpeg mov mpg txt nfo; do rm ${sourcelocation}/*.$ext; done	
	#copys a txt file from my directory to sources directory
	cd /home/domz/${sourcelocation}
	cp /home/domz/file.txt ${sourcelocation}
	#if [ -x file.txt ]
	#then
    		# linecnt=$(awk 'END {print NR - 1}' ${file})
     		#sed -n "1,${linecnt}p" ${file} > /tmp/$$
    		# echo "your new text" >> /tmp/$$
     		#echo "exit 0" >> /tmp/$$
     		#cat /tmp/$$ > ${file}
    		# rm /tmp/$$
	#fi
	#moves directory
	mv ${sourcelocation} /home/domz/{}
	#http://www.torrent-invites.com/tutorials/52022-putty-complete-tutorial.html
	cd /home/domz/watch
	mktorrent -v -p --announce=http://pmtorrents.com:2710/b1d1d1f932973605d3d751fda21c1749/announce --output={}.torrent ${}
else
	echo "Encoding FAILED"
fi

exit
```

---

### Post by lisati on 2010-05-19
Please do not start multiple threads on the same question.

I have merged your threads.

---

### Post by cariboo on 2010-05-20
I have a real problem with this whole thread, the op is talking about downloading media via rtorrent, converting them to an iphone compatible format, then seeding the same media via rtorrent. It sounds like piracy to me.

Thread closed.

---

