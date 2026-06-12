---
title: "Make xsplash use gdm's/your background image automatically."
date: 2009-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by vexorian on 2009-11-09
So, you figured out how to change gdm's background image, but that splash logo thingie still uses the unlikebably  black with lighting background... You may change it manually by editing  gdm's PreSession and Init  scripts, but really ? Doing that whenever you update gdm's or your background is going to be tiresome, so... Here we go:

So, first back your scripts up:
```

sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.back.date 
sudo cp /etc/gdm/PreSession/Default
 /etc/gdm/PreSession/Default.back.date 

```

 open Init:

```

sudo gedit /etc/gdm/Init/Default

```

Inside this file, you'll find these lines:
```

if [ -x '/usr/bin/xsplash' ];
then
        /usr/bin/xsplash --background $WALLPAPER --daemon
fi

```
Change them with:

```

if [ -x '/usr/bin/xsplash' ];
then
	# Extract the gdm wallpaper filename
	WALLPAPER=$(sudo -u gdm gconftool-2 --get /desktop/gnome/background/picture_filename)
        /usr/bin/xsplash --background $WALLPAPER --daemon
fi

```
Save and close gedit

Now, also edit Presesion

```

sudo gedit /etc/gdm/PreSession/Default

```

You'll find the same lines, change accordingly. Save and close.

These changes will barely make it so the splash uses gdm's background image during init and during log in. But, it may make more sense to you to show the user's background instead during log in. This is possible, but will only work well if the user's background is set to take the whole screen, edit PreSession/Default, and instead of the lines above, use these:

```

if [ -x '/usr/bin/xsplash' ];
then
	# Extract the user's wallpaper filename
	# This will only work in Presession        
	WALLPAPER=$(sudo -u $USER gconftool-2 --get /desktop/gnome/background/picture_filename)
        /usr/bin/xsplash --background $WALLPAPER --daemon
fi

```

---

