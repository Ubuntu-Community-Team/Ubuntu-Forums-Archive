---
title: "Fetch daily-updated online image as wallpaper"
date: 2010-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Random Squires on 2010-10-22
Hello all,
just an itch I needed to scratch; there's an image on a website, and it is updated every day (happily using a regular format for its url). I want to fetch this image every day and set it as my desktop background. In my example, the image is the YouGov daily poll ratings for the UK, but I hope this will be helpful for others to adapt.

```
#!/bin/sh
mkdir $HOME/pollgrabber
cd $HOME/pollgrabber
date +%d --date="yesterday" > date
echo http://today.yougov.co.uk/sites/today.yougov.co.uk/files/550pxVotIntdategoeshere1010.jpg > templateurl
cat templateurl | sed "s/dategoeshere/`cat date`/" templateurl > url
wget $( cat "./url" ) -O today.png
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$HOME/pollgrabber/today.png"
gconftool-2 --type string --set /desktop/gnome/background/picture_options centre
```A quick run-through:

[LIST=1]
[*]Make a directory for the script to run in, just makes things tidier. Don't worry about running this again, if the folder's already there it doesn't matter.
[*]Change to that directory
[*]Find yesterday's date, i.e. if yesterday was 21st October, a file will be created containing the text 21.
[*]This url will be set as the template for the date to be substituted into
[*]Substitute the "date" file into the template url
[*]Use wget (a downloading tool) to fetch the image
[*]Use gconftool to set the image as the wallpaper
[*]Use gconftool to centre the wallpaper (optional, but probably a good idea with medium-low res images like this one)
[/LIST]
Hope someone finds this useful.

---

### Post by Dougle on 2011-08-15
I had a similar itch to scratch.

Here: [http://github.com/dougle/Remote-Desktop-Background-Sync](http://github.com/dougle/Remote-Desktop-Background-Sync)
I use cron to set the frequency and the URL etc

---

