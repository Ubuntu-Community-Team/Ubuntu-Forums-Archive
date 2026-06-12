---
title: "HOWTO: Create a script to right click an image and set as wallpaper..."
date: 2005-07-21
forum: Outdated Tutorials &amp; Tips
---

### Post by audax321 on 2005-07-21
I hate Gnome's wallpaper changer only because you have to add images to it manually. I think it would be so much better if it functioned like a music player and just indexed all the images in a given directory instead. So, I thought to myself, why not put Nautilus's thumbnails to good use and just use it as a wallpaper changer. To do this I wrote a very simple script that sets an image as wallpaper and put it in the Scripts folder.

STEP 1: Open up terminal.

STEP 2: Go to the Nautilus Scripts folder:

```

cd ~/.gnome2/nautilus-scripts

``` 

STEP 3: Create a text document here and name it:

```

gedit "Set as Wallpaper"

```

STEP 4: Stick the following inside of the text document, depending on how you want to set up the wallpaper:

**METHOD 1: Simple script with no user interaction...** 

```

#!/bin/sh

# Sets selected image as Gnome background:

image="$(pwd)/$1"

if [ -f "$image" -a -r "$image" ]; then
	gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$image"
	gconftool-2 -t str --set /desktop/gnome/background/picture_options "stretched"
fi

```

The above code uses "stretched" to fill the screen with the image. Other options include "centered" to center the image, "tiled" to tile the image, and "scaled" to scale the image until either the vertical or horizontal edges reach the end of the screen.

**METHOD 2: Simple script with user interaction...** 

```

#!/bin/sh

# Sets selected image as Gnome background:

image="$(pwd)/$1"

if [ -f "$image" -a -r "$image" ]; then
	stretched_option="FALSE"
	centered_option="FALSE"
	scaled_option="FALSE"
	wallpaper_option="FALSE"
	
	case $(gconftool-2 --get /desktop/gnome/background/picture_options) in
		"stretched" )
			stretched_option="TRUE"
		;;

		"centered" )
			centered_option="TRUE"
		;;

		"scaled" )
			scaled_option="TRUE"
		;;

		"wallpaper" )
			wallpaper_option="TRUE"
		;;
	esac

	image_option=$(zenity --title="How would you like the image displayed?" --list --list-text="Please choose how to display '$1' or press CANCEL to exit." --radiolist --column "Item" --column "Types" --column "Description" "$stretched_option" "Fill Screen" "Stretch the image to fill the screen." "$centered_option" "Centered" "Center the image on the screen." "$scaled_option" "Scaled" "Scale the image without stretching." "$wallpaper_option" "Tiled" "Tile the image on the screen.")

	if [ "$image_option" != "" ]; then
		gconftool-2 -t str --set /desktop/gnome/background/picture_filename "$image"

		case "$image_option" in
			"Fill Screen" )
				gconftool-2 -t str --set /desktop/gnome/background/picture_options "stretched"
			;;

			"Centered" )
				gconftool-2 -t str --set /desktop/gnome/background/picture_options "centered"
			;;

			"Scaled" )
				gconftool-2 -t str --set /desktop/gnome/background/picture_options "scaled"
			;;
		
			"Tiled" )
				gconftool-2 -t str --set /desktop/gnome/background/picture_options "wallpaper"
			;;
		esac
	fi
fi

``` 

Method 2 requires that you have zenity installed (which it should be since it is required by ubuntu-desktop) and will actually prompt you to determine how you would like the image displayed. In my opinion this way is much nicer since you have more options.

STEP 5: Save and exit gedit as well as terminal.

STEP 6: Open nautilus and navigate to: ~/.gnome2/nautilus-scripts

STEP 7: Right click on the script that you created and go to Properties. Next, go to the Permissions tab and do the following:

```

Check all the boxes for Read
Check the top checkbox (owner) for Write
Check all the boxes for Execute

```

That's it... now you can right-click on any image inside of Nautilus, go to the Scripts menu, and Set as Wallpaper! If you look at how the script sets the background image you'll notice you could also write other scripts that change settings in the Gnome Configuration Editor.

 :)

---

### Post by lorenzo on 2005-07-21
Thanks! Very interesting.

The only error: I have to set "executable" for my user under permission preferences to make it appear under the right click menu.

Ciao,
Lo

---

### Post by audax321 on 2005-07-21
Thats what I meant when I wrote check off all the boxes for execute. But I guess I can see how that can be misread so I changed it to check all the boxes for execute.  :)

---

### Post by Sam on 2005-07-21
There is also an another way to set an image as wallpaper. Drag 'n drop an image (with the mouse middle button!) to the desktop, and you'll have a menu with the option 'Set as background'.

---

### Post by audax321 on 2005-07-21
[QUOTE=Sam]There is also an another way to set an image as wallpaper. Drag 'n drop an image (with the mouse middle button!) to the desktop, and you'll have a menu with the option 'Set as background'.[/QUOTE]

Nice, I never noticed that... I've been looking for a way to get that Copy Here, Move Here... menu to come up. Never thought to use the middle mouse button :) 

But, the set as wallpaper in the middle click menu doesn't set the picture options flag to stretched. It just sets it to "wallpaper" which tiles the wallpaper by default. Then wallpaper that is bigger than your screen resolution gets clipped off.

Also, as a side note, in the script above the word "stretched" can be changed to these others as well:

> 
"centered" (to center the wallpaper)

"stretched" (to fill the screen with the wallpaper)

"scaled" (to fill the screen with the wallpaper, but filling stops as soon as one edge of the wallpaper reaches the edge of the monitor.. e.g., it will stretch an image until either the top and bottom or left and right reach the monitor edge)

"wallpaper" (to tile the wallpaper)


---

### Post by audax321 on 2005-07-21
Adding a second method to implement the script where the user is prompted using zenity asking how to display the image. A lot cleaner, but requires that zenity is installed (which it should be since it is required by ubuntu-desktop) :)

---

### Post by Sam on 2005-07-21
Just a little note, you can make the script executable with the terminal instead of using the properties window in nautilus (steps 6+7):
```
$ chmod +x ~/.gnome2/nautilus-scripts/Set\ as\ Wallpaper
```

---

### Post by audax321 on 2005-07-24
Just updated method 2 so that now when you right click an image to set as wallpaper the dialog that pops up will automatically select your current setting. So if your current wallpaper is set to centered and you right click and set as wallpaper a new image, the dialog will have the centered radio button selected.

---

