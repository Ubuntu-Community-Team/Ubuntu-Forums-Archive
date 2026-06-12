---
title: "HOWTO: Random abstract desktop wallpaper, using evolvotron"
date: 2009-10-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Rob-e on 2009-10-09
**[SIZE="5"]How to set up a automatically changing randomly generated wallpaper[/SIZE]**

[SIZE="4"]**Introduction**[/SIZE]
If you have ever used the program 'evolvotron' you know it can make you cool abstract pictures, but what you may not know is it has a command line interface that can be used to make cool looking pictures.  When you combine that power with cron (a utility to run programs on a schedule) you can make yourself a fresh wallpaper every hour automatically.

**This will only work on Ubuntu (or other gnome desktops) not Kubuntu or Xubuntu (non gnome users see note below)**

[SIZE="4"]Step 1: Install evolvotron[/SIZE]
1. Go to Applications > Accessories > Terminal
2. In the black box type (or paste):
```
sudo apt-get install evolvotron
```

3. Press enter, type your password and wait for it to finish installing.

[SIZE="4"]Step 2: Set up the script that changes the wallpaper[/SIZE]
1. Open gedit by going to Applications > Accessories > Text Editor
2. Paste this into the document:
```
#!/bin/bash
evolvotron_mutate -g > evolved.xml
# set your resolution here -v-
evolvotron_render -v -s 1024 768 evolved_bg.ppm < evolved.xml
rm evolved.xml
gconftool-2 --type String --set /desktop/gnome/background/picture_filename "$(pwd)/evolved_bg.ppm"
```

3. (optional) Edit the file so it has your screen resolution instead of "1024 768"
3. Save the file in your home folder as "evolvotron_bg"
4. Close gedit
5. Go back to terminal and type (or paste):
```
chmod +x evolvotron_bg
```

[SIZE="4"]Step 3: Make sure the script is working (optional)[/SIZE]
In the terminal window type:
```
./evolvotron_bg
```

It should render you a new image and set it as the wallpaper, if it doesn't then something is wrong and the next steps won't fix it.

[SIZE="4"]Step 4: Set up cron to run the script every so often[/SIZE]
1. In the terminal window type:
```
crontab -e
```

- If it asks about what editor to use press 3 and enter to use nano
2. Use the arrow keys and scroll to the bottom of the file, and on a new line paste:
```
30 * * * * ~/evolvotron_bg
```

- This will change the background once every hour on the 30 minute mark.
3. Press 'ctrl x', press Y, and press enter to save the file.


That's it!  your wallpaper should change at the middle of every hour.

[SIZE="4"]Notes:[/SIZE]
- It will take a few seconds of your cpu being maxed out to render the image, this may interrupt some games.

- If you get a lot of backgrounds you don't like you could add an icon to the panel and set the command to "~/evolvotron_bg" to change the image with a click.

- Any suggestions are welcome, and if someone knows how to change the wallpaper in the kde world that would be nice to know

- For non gnome users: The last line of the script is the only reason this requires gnome, but if you delete the last line, and set your wallpaper to "~/evolved_bg.ppm" the image file will be updated and the wallpaper should be updated too (depending on DE)

---

### Post by Roanoke on 2009-10-10
Cool! I've never come across evolvotron before. As an aside, if you set the background image as ~/.wallpaper.png (as I do), any changes to ~/.wallpaper.png will be shown on the background, so you can shave an extra line off of the shell script.

---

### Post by Rob-e on 2009-10-11
> **Roanoke said:**
> Cool! I've never come across evolvotron before. As an aside, if you set the background image as ~/.wallpaper.png (as I do), any changes to ~/.wallpaper.png will be shown on the background, so you can shave an extra line off of the shell script.

You are right, I assumed it wouldn't update until a log off/on, though I will leave it since it changes the picture on the first run, though I will add a note for non-gnome users.  Thanks for the tip, and I'm glad you like it!

---

### Post by Roanoke on 2009-10-11
And another thing: Does it take time to build complexity? All I'm getting is two colors at most. If I'm lucky.

---

### Post by Rob-e on 2009-10-11
> **Roanoke said:**
> And another thing: Does it take time to build complexity? All I'm getting is two colors at most. If I'm lucky.

I'm not sure but I think it is just random, sometimes you get a pattern or cool waves but it is usually mostly a solid color or 2, There may be a way to take an original xml file and mutate from it, but I don't know for sure.

---

### Post by Roanoke on 2009-10-11
Okay, so I found a method to get more complex wallpapers.
First, execute the original script, but comment out/remove the line that deletes evolved.xml.
```

#!/bin/bash
evolvotron_mutate -g > evolved.xml
# set your resolution here -v-
evolvotron_render -v -s 1024 768 evolved_bg.ppm < evolved.xml

```

Then, modify and execute the script like so.
```

#!/bin/bash
evolvotron_mutate -g > evolved.xml < temp.xml
# set your resolution here -v-
evolvotron_render -v -s 1024 768 evolved_bg.ppm < evolved.xml

```

Finally, modify the script to this:
```

#!/bin/bash
evolvotron_mutate -g > temp.xml < temp.xml
# set your resolution here -v-
evolvotron_render -v -s 1024 768 evolved_bg.ppm < temp.xml

```
You can also remove evolved.xml. After this, the designs will get complex because it is building and mutating the same file rather than starting from scratch.

Unfortunately, this doesn't completely remove the problem of just a solid color being rendered. Maybe someone else can help?

---

### Post by Rob-e on 2009-10-12
Interesting, although I do keep getting mainly blank ones too.

I don't know what you do/don't know but the lines in the script are just commands that are run, so you don't need to modify the file and run it, you can just paste lines in terminal.  So to get the same result (I assume) I just ran these commands:
```

evolvotron_mutate -g > evolved.xml
evolvotron_mutate -g > temp.xml < evolved.xml
evolvotron_mutate -g > temp.xml < temp.xml

```

And then the script can be modified to:
```

#!/bin/bash
evolvotron_mutate -g > temp.xml < temp.xml
# set your resolution here -v-
evolvotron_render -v -s 1024 768 evolved_bg.ppm < temp.xml

```


but none of that does what you think it does since evolvotron_mutate has the -g flag which "Specifies that no function should be  read  from  standard  input.  The output function is created at random."  So it is just random anyway.  If I remove the -g, though, I get an error, so I don't know what's going on with that.

---

