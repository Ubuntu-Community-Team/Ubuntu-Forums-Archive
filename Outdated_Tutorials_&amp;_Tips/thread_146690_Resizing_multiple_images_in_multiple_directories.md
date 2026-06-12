---
title: "Resizing multiple images in multiple directories"
date: 2006-03-18
forum: Outdated Tutorials &amp; Tips
---

### Post by JGJones on 2006-03-18
Greetings all, I had a bunch of photo's in many directories that I wanted to put into a new directory and resize ready for uploading to an online gallery webiste.

My folders are arranged as this:

<year>-<month>-<month name> and then in the directories in increasing order sorted by date of creation, files are named <month>-<year>-###.jpg etc
 ### being the number that they increase in date of creation.

Anyway I wanted to go into each directory, copy all files to a new "webfriendly" folder created in that folder and then resize all files to width of 1024 and so on.

Now with quite a lot of files this would take ages and so I decided it was a good time to learn about scripting in linux :)

This is what I have created:

```

#!/bin/sh

for i in *; do 

cd "$i";
echo $i; #show which directory is being worked on
mkdir webfriendly;

#  Rename files from *.JPG to *.jpg if any before we move them

	for f in *.JPG; do

		base=`basename "$f" .JPG`
		mv "$f" "$base".jpg

	done


cp *.jpg webfriendly/;
cd webfriendly;

# this resize images to have a width of 1024 but aspect ratio is kept since 
# height can change
mogrify -resize 1024 *.jpg; 

cd ..;
cd ..;
done

```

I thought in interest of "open source" I'll share this and perhaps some nice folks can show where I can improve this little script?

For example I realise there are a few areas where the script would fail:

[LIST=1][*]this depends on all images being of in the "wide" format and not "on its side" [*]Change of directories - if there is a file in it, the for i in * would include that and then because of cd "$i" not working but cd .. does, it'll go back up a level wrongly[*]err there was one other I thought of but I forgot :)
[/LIST]

By the way, for this to work you need the imagemagick tools so either fire up Synaptic and search for imagemagick and install or do this in console:

sudo apt-get install imagemagick

Many thanks

---

