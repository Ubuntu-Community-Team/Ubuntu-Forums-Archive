---
title: "Script to convert flac to mp3"
date: 2013-03-25
forum: Programming Talk
---

### Post by AmbiguousOutlier on 2013-03-25
My first script.

I know this script has been made a hundred times before. However I have quite specific needs and all the scripts out there would only convert files within your current directory. And I want to convert a lot of files, in lots of different directories, plus I'm constantly adding CD's to my collection. So I wanted a script that would scan my flac folder and mirror it in my mp3 folder, whenever I added a new flac file it would update my mp3 folder. I also have folder art for every album and artist and so I also wanted to copy these files over if they haven't been already. 

Next step is to automate the script so it runs every night.   

```
#!/bin/bash
###############################################################################################################
# Author :	RhysGM
# Title  : 	automated flac2mp3
# Date   :	25-Mar-2013
# Version:	1.0
# Description;
# Incrementally convert all flac files in a directory including all subdirectories to mp3 and copy to a 
#  mirrored directory. Also copies folder.jpg# Prerequisites;
# sudo apt-get install lame flac id3 
###############################################################################################################

# flac_loc is starting location, "flac" needs to be part of folder name, mp3's will be created in the same 
# folder structure with flac subsituted for mp3

flac_loc="/home/berry/flac_music/"  	

# Creates counters to display progress
flac_files=$(find $flac_loc -name '*.flac' | wc -l)
mp3_files=$(find $(echo $flac_loc | sed -e 's/flac/mp3/g') -name '*.mp3' | wc -l)
process=$(($flac_files - $mp3_files))
count=0	
echo $flac_files "flac files found," $mp3_files "mp3 files found, estimated" $process "files to be processed"

# mp3 loop, check if mp3 exists, convert flac to mp3 in new location, copy id3 tags
while read -r -d $'\0' i; do

	mp3_loc=$(echo $i | sed -e 's/flac/mp3/g')
 
	if [ -f "$mp3_loc" ]
	then 	
		echo "$mp3_loc exists"
	else 
		count=$(( $count + 1))
		artist=$(metaflac "$i" --show-tag=artist | sed s/artist=//g)
		title=$(metaflac "$i" --show-tag=title | sed s/title=//g)
		album=$(metaflac "$i" --show-tag=album | sed s/album=//g)
		genre=$(metaflac "$i" --show-tag=genre | sed s/gnere=//g)
		track=$(metaflac "$i" --show-tag=tracknumber | sed s/tracknumber=//g)
		moddate=$(metaflac "$i" --show-tag=date | sed s/date=//g)
		albumartist=$(metaflac "$i" --show-tag=albumartist | sed s/albumartist=//g)

		mp3_path="${mp3_loc%/*}"
		mkdir "$mp3_path"

		flac -c -d "$i" | lame -m j -q 0 --vbr-new -V 0 -s 44.1 - "$mp3_loc"
		id3 -t "$title" -T "${track:-0}" -a "$artist" -A "$album" -y "$moddate" -g "$genre" "$mp3_loc"

		echo $count "file(s) of" $process "completed"
	fi
done < <(find $flac_loc -name '*.flac' -print0)

# jpg loop, check if jpg exists, copy jpg
while read -r -d $'\0' j; do

	jpg_loc=$(echo $j | sed -e 's/flac/mp3/g')

	if [ -f "$jpg_loc" ]
	then 	
		echo "$jpg_loc exists"
	else 
		cp "$j" "$jpg_loc"
	fi
done < <(find $flac_loc -name 'folder.jpg' -print0)

```

---

### Post by Cheesemill on 2013-03-25
If you just want a copy of all of your flac files in mp3 format then take a look at mp3fs.

It creates a virtual mp3 directory which mirrors your flac directory, but without taking up any space. Whenever you access anything in the mp3 directory it is transcoded on the fly. I've been using this for years on my server with great results.

[http://khenriks.github.com/mp3fs/](http://khenriks.github.com/mp3fs/)
[http://www.blisshq.com/music-library-management-blog/2010/05/17/easy-flac-to-mp3-mirroring-with-mp3fs/](http://www.blisshq.com/music-library-management-blog/2010/05/17/easy-flac-to-mp3-mirroring-with-mp3fs/)

---

### Post by AmbiguousOutlier on 2013-03-25
Sounds interesting, but I want my complete music directory in mp3 format so I can copy to a usb flash drive and use in my car and to an SD card for my tablet. Although I would question why you need it done on the fly, why would you willing use an mp3 when you have a flac file sitting there. I need to because the computer in my car doesn't support flac and there is not enough room on the tablet for all my flac files.

---

### Post by Cheesemill on 2013-03-25
That is exactly what you use mp3fs for.

My original CD rips live in /mnt/data/music/flac and additionally I have it all in mp3 format in /mnt/data/music/mp3.
My mp3 directory is only used to share files across the network to devices that don't support flac, or for copying music to portable devices.

The only difference between my setup and yours is that your mp3 files take up additional space on your hard drive and you have to manually keep your directories in sync, but mine don't take up any space ***at all*** and are always in sync (due to the use of mp3fs).

For example...
```
rob@raring:/mnt/data/music$ ls
total 8.0K
drwxr-xr-x 19 rob users 4.0K Feb 12 15:48 flac
drwxr-xr-x 19 rob users 4.0K Feb 12 15:48 mp3
rob@raring:/mnt/data/music$ 
rob@raring:/mnt/data/music$ 
rob@raring:/mnt/data/music$ ls "flac/Katy B/On a Mission/"
total 379M
-rw-r--r-- 1 rob users 32M Feb  8 18:37 01 Power on Me.flac
-rw-r--r-- 1 rob users 27M Feb  8 18:37 02 Katy on a Mission.flac
-rw-r--r-- 1 rob users 42M Feb  8 18:37 03 Why You Always Here.flac
-rw-r--r-- 1 rob users 27M Feb  8 18:37 04 Witches Brew.flac
-rw-r--r-- 1 rob users 21M Feb  8 18:37 05 Movement.flac
-rw-r--r-- 1 rob users 29M Feb  8 18:37 06 Go Away.flac
-rw-r--r-- 1 rob users 26M Feb  8 18:37 07 Disappear.flac
-rw-r--r-- 1 rob users 26M Feb  8 18:37 08 Broken Record.flac
-rw-r--r-- 1 rob users 26M Feb  8 18:37 09 Lights On.flac
-rw-r--r-- 1 rob users 30M Feb  8 18:37 10 Easy Please Me.flac
-rw-r--r-- 1 rob users 25M Feb  8 18:37 11 Perfect Stranger.flac
-rw-r--r-- 1 rob users 74M Feb  8 18:37 12 Hard to Get.flac
rob@raring:/mnt/data/music$ 
rob@raring:/mnt/data/music$ 
rob@raring:/mnt/data/music$ ls "mp3/Katy B/On a Mission/"
total 106M
-rw-r--r-- 1 rob users 8.2M Feb  8 18:37 01 Power on Me.mp3
-rw-r--r-- 1 rob users 7.0M Feb  8 18:37 02 Katy on a Mission.mp3
-rw-r--r-- 1 rob users  11M Feb  8 18:37 03 Why You Always Here.mp3
-rw-r--r-- 1 rob users 6.4M Feb  8 18:37 04 Witches Brew.mp3
-rw-r--r-- 1 rob users 5.2M Feb  8 18:37 05 Movement.mp3
-rw-r--r-- 1 rob users 6.9M Feb  8 18:37 06 Go Away.mp3
-rw-r--r-- 1 rob users 6.9M Feb  8 18:37 07 Disappear.mp3
-rw-r--r-- 1 rob users 6.4M Feb  8 18:37 08 Broken Record.mp3
-rw-r--r-- 1 rob users 6.5M Feb  8 18:37 09 Lights On.mp3
-rw-r--r-- 1 rob users 7.5M Feb  8 18:37 10 Easy Please Me.mp3
-rw-r--r-- 1 rob users 6.2M Feb  8 18:37 11 Perfect Stranger.mp3
-rw-r--r-- 1 rob users  29M Feb  8 18:37 12 Hard to Get.mp3
rob@raring:/mnt/data/music$ 
rob@raring:/mnt/data/music$ 
rob@raring:/mnt/data/music$ 

```

Even though they appear to be normal files, none of the music in my mp3 directory actually exists on the hard drive. Mp3fs makes it look like it does but it is transcoding the flac files into mp3's on the fly when you access them.


Although this method has served me well for many years I think its time is nearly up. My new car ***does*** accept flac files :)
[http://ubuntuforums.org/showthread.php?t=2127519](http://ubuntuforums.org/showthread.php?t=2127519)

---

### Post by Vaphell on 2013-03-25
few things:

```
flac_files=$(find **$flac_loc** -name '*.flac' | wc -l)
mp3_files=$(find **$(echo $flac_loc | sed -e 's/flac/mp3/g')** -name '*.mp3' | wc -l)
mp3_loc=$(echo **$i** | sed -e 's/flac/mp3/g')

```

if it can have spaces, wrap it up in "". If for whatever reason you had 2 spaces next to each other, they would get compressed to 1. I know you have the dir hardcoded but adding quotes costs you nothing and in case you even wanted to make the script parametrized you would be good to go right off the bat against any directory name you can throw in.

simple substitutions like these can and should be done without resorting to external programs (which mean additional overhead).
if you want to trim something from the right side you can use ${variable%pattern}, eg
```
mp3_loc=${i%flac}mp3
```
(you even use this feature to get *mp3_path*) or use replacement ${variable/pattern/replacement}, eg
```

mp3_loc=${i/%flac/mp3}    # additional % forces the pattern to much at the very end
mp3_files=$(find "${flac_loc//flac/mp3}" -name '*.mp3' | wc -l)  # // equivalent to sed s//**/g**

```
[http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html](http://www.gnu.org/software/bash/manual/html_node/Shell-Parameter-Expansion.html)

Be more precise with your find-and-replace's. Your sed would substitute not only the extension (flac$) but every other 'flac' there is. It would be ok with your hardcoded dir, not so much with files (you have no guarantee you'll always have files that have no flac in their name).

*[I]find -name '*.flac' | wc -l*[/I] is not really reliable if you want to count files. Newline is a totally legit character to be used in filenames and it would easily throw your script off.
use something like this instead
```
find "$flac_loc" -name '*.flac' -printf "x" | wc -c
``` 
Another way to keep the list of files with their count for free would be to use arrays.

```
while read -rd $'\0' f; do
  flac_files+=( "$f" ) # array of file paths
done < <(find $flac_loc -name '*.flac' -print0)

echo ${**#**flac_files[@]} # array size

for f in "${flac_files[@]}"; do echo "$f"; done # use array elements
for(( i=0; i<${#flac_files[@]}; i++; )); do echo "${flac_files[i]}"; done # C-style for loop to do the same
```


You can use *-iname* (case insensitive) just in case you have .FLAC files (they wouldn't match '*.flac' pattern)


any text in integer mode (( )) is assumed to be a variable name, so in most cases you don't really need $
```
process=$(($flac_files - $mp3_files))
process=$((flac_files - mp3_files)) # that's ok too.
```

---

### Post by AmbiguousOutlier on 2013-03-26
Thanks Vaphell for all your help. 


```
# input and output locations for flac and mp3 files
flac_loc="/home/berry/flac_music/"
mp3_loc=$(echo "$flac_loc" | sed -e 's/flac/mp3/g')
```
I was using sed as I needed to substitute flac for mp3 within the middle part of the dir. So I have three parts base directory / music folders / music file. I've decided to set the base directories in the beginning, I'm assuming there might be some cost savings rather than doing it everytime within the loop. I can then use pattern substitution for the file extension.  

```
# Creates counters to display progress
flac_count=find "$flac_loc" -iname '*.flac' -printf "x" | wc -c
mp3_count=find "$mp3_loc" -iname '*.mp3' -printf "x" | wc -c
process=$((flac_count - mp3_count))
count=0	
echo $flac_count "flac files found," $mp3_count "mp3 files found, estimated" $process "files to be processed"
```
I'm using your counting method and I think it does look a little cleaner. Plus predefining the mp3 location eliminates some substitutions. 

```
# mp3 loop, check if mp3 exists, convert flac to mp3 in new location, copy id3 tags
while read -r -d $'\0' flac_file; do

	mp3_file="${flac_file%.flac}.mp3"
 
	if [ -f "$mp3_file" ]
	then
		echo "$mp3_file" exists
	else
		count=$((count + 1))
		artist=${(echo $(metaflac "$flac_file" --show-tag=artist))#*=}
		title=${(echo $(metaflac "$flac_file" --show-tag=title))#*=}
		album=${(echo $(metaflac "$flac_file" --show-tag=album))#*=}
		genre=${(echo $(metaflac "$flac_file" --show-tag=genre))#*=}
		track=${(echo $(metaflac "$flac_file" --show-tag=tracknumber))#*=}
		moddate=${(echo $(metaflac "$flac_file" --show-tag=date))#*=}
		albumartist=${(echo $(metaflac "$flac_file" --show-tag=albumartist))#*=}

		mp3_path="${mp3_file%/*}"
		mkdir "$mp3_path"

		flac -c -d "$flac_file" | lame -m j -q 0 --vbr-new -V 0 -s 44.1 - "$mp3_file"
		id3 -t "$title" -T "${track:-0}" -a "$artist" -A "$album" -y "$moddate" -g "$genre" "$mp3_file"

		echo $count "file(s) of" $process "completed"
	fi
done < <(find $flac_loc -iname '*.flac' -print0)

# jpg loop, check if jpg exists, copy jpg
while read -r -d $'\0' jpg_flac; do

	jpg_mp3="$mp3_loc${jpg_file#$flac_loc}"

	if [ -f "$jpg_mp3" ]
	then
		echo "$jpg_mp3 exists"
	else
		cp "$jpg_flac" "$jpg_mp3"
	fi
done < <(find $flac_loc -iname 'folder.jpg' -print0)
```
I've tried to replace sed with pattern substitution to be on the safer side as I have 1,000's of files and I'm sure there could be conflicts. 

*jpg_mp3="$mp3_loc${jpg_file#$flac_loc}"* not sure if this is the best way to convert "/home/berry/flac_music/sub folder/folder.jpg" to "/home/berry/mp3_music/sub folder/folder.jpg" 

I haven't tested this script yet as I'm at work, so have probably got a couple syntax errors. Assuming it does work next step is to run it on my samba share. I'm sure that wont cause me any headaches.

---

### Post by schragge on 2013-03-26
> **RhysGM said:**
> 
```
# input and output locations for flac and mp3 files
flac_loc="/home/berry/flac_music/"
mp3_loc=$(echo "$flac_loc" | sed -e 's/flac/mp3/g')
```
With bash, you can do substitution in the middle, too
```

flac_loc='/home/berry/flac_music/'
mp3_loc="${flac_loc/flac/mp3}"

```

---

### Post by AmbiguousOutlier on 2013-03-26
So what is better substitution by ${//} or sed?

---

### Post by schragge on 2013-03-26
Shell substitution is done by the shell itself. It spares you a sed invokation, a pipe, and a command substitution. So it is definitely better. But it is more limited than sed. In this particular case, where you substitute a fixed substring with another fixed substring, there is no need going the sed route.

---

### Post by Vaphell on 2013-03-26
just like schragge said, if it's a relatively trivial substitution and you can do it with parameter expansion, do it. Parameter expansion is pretty much for free.
Use sed when you need fullblown regular expressions or solution in pure bash is simply too complex. Standard expansion doesn't really deal with things like 'any sequence of digits' which is trivial in regexes.

bash can be made to support slightly more powerful syntax of patterns where +, * and ? work like in regexes.

```
$ **shopt -s extglob**
$ x=abcdefabcdef
$ echo "$x" | sed -r 's/([bcd])+/-/g'
a-efa-ef
$ echo ${x//+([bcd])/-}
a-efa-ef
```

---

