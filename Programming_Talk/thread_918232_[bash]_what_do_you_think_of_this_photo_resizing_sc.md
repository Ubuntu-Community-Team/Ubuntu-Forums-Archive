---
title: "[bash] what do you think of this photo resizing script"
date: 2008-09-12
forum: Programming Talk
---

### Post by Rob-e on 2008-09-12
*****
EDIT:
I just thought I would let everyone know there is a much nicer resize and rotate program in the repository called nautilus-image-converter, it adds a resize and rotate option right to the right click menu on images.

```
sudo apt-get install nautilus-image-converter
```
*****


I basically just highly modified this guys script: [http://ubuntuforums.org/showthread.php?t=34705](http://ubuntuforums.org/showthread.php?t=34705)

it can resize to 3 predefined sizes (you could add more) and it asks to put the resized pics in a folder or rename them

its made to be put in the nautilus scripts directory:
~/.gnome2/nautilus-scripts/
and then its available on the right click menu, (dont forget chmod) just highlight some pics and right click and choose the script

edit: forgot to mention you must have imagemagick installed (in the repos)

what do you think?
and feel free to use/mod/etc


the main reason i made this is because my parents need something to do this, in windows they have been using photogadget, and this does the same thing


```
#!/bin/bash

# must have imagemagick installed
# doesnt work with spaces in filenames... yet

CURRENTLOCATION=`pwd`

SIZE=`zenity --list --title="Choose the thumbnail's size" --radiolist --column="Check" --column="Size" "" "320x240" "" "640x480" "" "800x600" "" "1024x768"`

if [ "${SIZE}" == "" ]; then    
	zenity --error --text="Size not defined by user.
	Please choose a size to use. "
	exit 1
fi

ACTION=`zenity --list --title="What would you like to do?" --radiolist --column="Check" --column="Choices" "" "Move pictures to resized folder" "" "Rename pictures"`
# zenity --file-selection --title="What would you like to do?" --directory --filename=resized
# could be used to use folder other than resized

if [ "${ACTION}" == "" ]; then    
zenity --error --text="Action not defined by user.
Please choose an action. "
exit 2
fi


if [ "${ACTION}" == "Move pictures to resized folder" ]; then

	mkdir resized/
	
	for file in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
		filename=$(basename "$file")
		convert -resize "${SIZE}" -quality 50 "$file" "$CURRENTLOCATION/resized/$filename"
	done
fi

if [ "${ACTION}" == "Rename pictures" ]; then
	for file in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
		strippedfilename=$(basename "$file" .jpg)
		convert -resize "${SIZE}" -quality 50 "$file" "$CURRENTLOCATION/$strippedfilename $SIZE.jpg"
	done
fi

zenity --info --text="All finished"

```

---

### Post by miegiel on 2010-02-21
Thanks :D It didn't work for me though, but with some effort I did manage to condense the script down to :
```
#!/bin/bash
#
# depends on imagemagick
	
for file in *.jpg ; do
#	resize to 800x800 or less maintaining aspect ratio
	convert -resize 800x800 "$file" "800.$file"
done

exit
```
Which is good enough for my purposes.

In case you're intrested, the errors I got running your script :
```
[: 14: 800x600: unexpected operator
[: 24: Rename pictures: unexpected operator
[: 35: Rename pictures: unexpected operator
[: 42: Rename pictures: unexpected operator
```

---

### Post by falconindy on 2010-02-21
Tip: If you add a Bash shebang, take advantage of it.

- Use double square brackets instead of single
- Use ${var##*/} instead of $(basename $var)

I also suspect that Nautilus's provided environment variables will not be friendly enough to handle spaces. You'll need to find another method. Regardless, using a 'for' loop will never deal with spaces properly.

---

### Post by Rob-e on 2010-07-09
I just thought I would let everyone know there is a much nicer resize and rotate program in the repository called nautilus-image-converter, it adds a resize and rotate option right to the right click menu on images.

```
sudo apt-get install nautilus-image-converter
```

---

### Post by geirha on 2010-07-09
You seem to have mastered the most important skill in shell scripting, namely quoting, though except for $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS. Obviously, (as falconindy also mentions) this is because those environment variables are broken by design; they can't safely contain a list of filenames.

Luckily, however, nautilus-scripts also passes the selected files as arguments to the script, which keeps each filename safely separated and not mangled together in a single string. So instead of 
```
for file in $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
```
just do
```

for file in "$@"; do
# or even just
for file; do
# run   help for   in an interactive bash shell to see why

```

Otherwise, as falconindy mentions, basename and dirname can be done more efficiently with parameter expansion, and the [ command should not be used in bash; rather use the [[ and (( keywords. And lastly, $(...) is preferred over `...`. See 
[http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)
[http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031)
[http://mywiki.wooledge.org/BashFAQ/082](http://mywiki.wooledge.org/BashFAQ/082)

@miegiel
Those errors you got look like dash error messages. Dash's [ command does not accept the == operator (only =), while bash's [ command accept both = and ==. While using the == operator with [ is bad practice, it works in bash, and the shebang points to bash, so the fault is really on you for trying to run a bash script with dash (or some other shell that is not bash).

---

