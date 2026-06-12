---
title: "Export covers from amarok to album dirs (to ipod)"
date: 2006-01-27
forum: Programming Talk
---

### Post by otey on 2006-01-27
Hi to all 

I'm using amarok for my music, and gtkpod for my iPod. My iPod is 5th generation, and supports coverimages. But my coverimages is stored via amarok, in the folder **~/.kde/share/apps/amarok/albumcovers/large** using names like **0a04f8d1a982b56a6ac8950abaab78a0**. (some md5-hash, i guess)

I would like to export the pictures from the amarok folder to the album dir. I only know a tiny bit of shell script, but i was hoping that somebody would help me. 

My idea was to access the **~/.kde/share/apps/amarok/collection.db** to get information on which cover belong to which album. And where the album is located. Then copy it to "album_folder_path/cover.png". 

Then I can use gtkpod to upload the covers.. 

If somebody would give me a clue how to get going, maybe how to view the content of the collection.db, i would apreciate it.

Thanks in advance

---

### Post by otey on 2006-01-27
after looking at the amarok wiki pages I wrote a script to copy the coverimage (set in amarok) to the direktory of the playing song (in amarok)
```
#/bin/bash

## Settings
cover_filename="cover.png"

## script
if [ "$(dcop amarok player status)" == "2" ]; then

	current_song="$(dcop amarok player path)"
	album_dir=${current_song%/*.mp3}
	picture_source="$(dcop amarok player coverImage)"
	picture_target=$album_dir"/"$cover_filename
	album_name="$(dcop amarok player album)"
	artist_name="$(dcop amarok player artist)"

	if [ "$picture_source" != "$picture_target" ]; then 
		if [ "${picture_source%%/*nocover.png}" != "" ]; then
			cp "$picture_source" "$picture_target"
			echo -e "Cover copied: $artist_name - $album_name"
		else
			echo "No cover set!"	
		fi
	fi
fi
```

---

### Post by otey on 2006-01-28
Ok.. Made the script go trough the whole playlist, copy covers. 

Don't run it, with all files in the playlist. What i did was to add all my albums, then mark them all, and while holding ctrl I picked one song from every album. Then removed the other songs from the playlist. 

the script: 
```

#/bin/bash

## Settings
cover_filename="cover.png"


## script
while [ "$(dcop amarok player status)" == "2" ]; do
	current_song="$(dcop amarok player path)"
	album_dir=${current_song%/*.mp3}
	picture_source="$(dcop amarok player coverImage)"
	picture_target=$album_dir"/"$cover_filename
	album_name="$(dcop amarok player album)"
	
	if [ -f "$picture_target" ]; then
	  dcop amarok player next
	else
		if [ ${picture_source%%/*nocover.png} != "" ]; then
			cp "$picture_source" "$picture_target"
			echo "Cover copied: \"$album_name\""
		fi
	fi
done

```

---

### Post by TheIrishGuy on 2007-11-05
nice script guys, thumbs up here

i made a few minor changes

first off i have a hell of a lot of mp3s(50k+), and i dont really want to click anything other than "go" and walk away.

At the same time i want to be able to see some sort of progress so i added a number increment so i can actually see its doing something.
Number increment may seem unnecessary but is kinda handy. kind of like a progress bar as amarok will be left minimized :)

also added some inverted commas to avoid any dirty things like

line 21: [: !=: unary operator expected


```

#/bin/bash


## Settings
cover_filename="cover.png"
cover_number=0



## script
while [ "$(dcop amarok player status)" == "2" ]; do
	current_song="$(dcop amarok player path)"
	album_dir=${current_song%/*.mp3}
	picture_source="$(dcop amarok player coverImage)"
	picture_target=$album_dir"/"$cover_filename
	album_name="$(dcop amarok player album)"
	cover_number=$((cover_number+1))
	
	if [ -f "$picture_target" ]; then
	  	dcop amarok player next
	else
		if [ "${picture_source%%/*nocover.png}" != "" ]; then
			cp "$picture_source" "$picture_target"
			echo $cover_number " Cover copied: \"$album_name\""
			dcop amarok player next
		else
			echo $cover_number " No cover set!"
			dcop amarok player next	
		fi
		
	fi
done


```

i wreckon it will take a couple of hours, but its worth it!

---

### Post by smartbei on 2007-11-05
Many thanks guys! I was looking for something just like this.

---

### Post by geirha on 2007-11-05
I made a script to do this myself, but I can't seem to find it again. I managed to put together the query I used to query the amarok database with though:
```
SELECT DISTINCT CONCAT('~/.kde/share/apps/amarok/albumcovers/large/',MD5(LOWER(CONCAT(artist.name,album.name)))), tags.dir
FROM album, artist, tags WHERE album.id=tags.album AND artist.id=tags.artist

```

while amarok is running, you can run the query through dcop: ```
 dcop amarok collection query "SELECT DISTINCT CONCAT('~/.kde/share/apps/amarok/albumcovers/large/',MD5(LOWER(CONCAT(artist.name,album.name)))), tags.dir
FROM album, artist, tags WHERE album.id=tags.album AND artist.id=tags.artist"
```

As you probably see, if you know a little sql, the covers are stored to a file in ~/.kde/share/apps/amarok/albumcovers/large/ with the md5sum of artist name+album name in lower case. So if you have the album David Bowie - Aladdin Sane, the cover will be stored as ```
$ echo -n "david bowiealaddin sane"|md5sum
f73bc66afee49e43fffdea0e194cc2fc  -

```

There's a special case for albums which have several (various) artists though, if I remember correctly, the cover names are only made from the md5sum of the album name in such cases.

Hope this helps.

---

### Post by TheIrishGuy on 2007-11-05
latest copycover script now works

you can download it from here

[http://www.kde-apps.org/content/show.php/CopyCover+(amaroK+Script)?content=22517](http://www.kde-apps.org/content/show.php/CopyCover+(amaroK+Script)?content=22517)

once it has copied the images into the destination folders you can use the below script to apply album covers to the folders in Nautilus


[http://ubuntuforums.org/showpost.php?p=2359786&postcount=18](http://ubuntuforums.org/showpost.php?p=2359786&postcount=18)

in order to use this script you need to either change the script or rename the png files to folder.png

i got this from a nice person in #bash in irc.ubuntu.com

test it first (echo)
```

find . -name "*.png" | while read file; do echo mv "$file" "${file%/*}/cover.png"; done

```

once your sure
```

find . -name "*.png" | while read file; do mv "$file" "${file%/*}/cover.png"; done

```

---

### Post by dannyboy79 on 2009-07-14
> **TheIrishGuy said:**
> latest copycover script now works

you can download it from here

[http://www.kde-apps.org/content/show.php/CopyCover+(amaroK+Script)?content=22517](http://www.kde-apps.org/content/show.php/CopyCover+(amaroK+Script)?content=22517)

once it has copied the images into the destination folders you can use the below script to apply album covers to the folders in Nautilus


[http://ubuntuforums.org/showpost.php?p=2359786&postcount=18](http://ubuntuforums.org/showpost.php?p=2359786&postcount=18)

in order to use this script you need to either change the script or rename the png files to folder.png

i got this from a nice person in #bash in irc.ubuntu.com

test it first (echo)
```

find . -name "*.png" | while read file; do echo mv "$file" "${file%/*}/cover.png"; done

```

once your sure
```

find . -name "*.png" | while read file; do mv "$file" "${file%/*}/cover.png"; done

```

i had luck with this website instruction here: [http://www.64bitjungle.com/ubuntu/batch-export-amarok-album-art-to-the-albums-containing-directory/](http://www.64bitjungle.com/ubuntu/batch-export-amarok-album-art-to-the-albums-containing-directory/)

---

