---
title: "HOW-TO: Take screenshot w/ thumbnail"
date: 2005-04-11
forum: Outdated Tutorials &amp; Tips
---

### Post by dude2425 on 2005-04-11
I've been wanting to post this for some time now, but never really got around to doing it, or remember it for that matter, till now. I just wanted to post it before I forget it again.
 
First, copy and paste the following into a random text editor:
```
#!/bin/bash
NOW=`date '+%m_%d_%Y_%M_%S'`
FNAME=screenshot${NOW}
EXT=png
if [ -d $HOME/screenshots ]
then
    cd $HOME/screenshots
else
    mkdir $HOME/screenshots
    cd $HOME/screenshots
fi
sleep 5
import -window root ${FNAME}.${EXT}
convert -resize 320x240 ${FNAME}.${EXT} ${FNAME}_thumb.${EXT}
if [ -d $HOME/screenshots/thumbs ]
then
    mv screenshot${NOW}_thumb.${EXT} thumbs/
else
    mkdir thumbs/
    mv screenshot${NOW}_thumb.${EXT} thumbs/
fi

```
(Remember the cariage return at the end)
 
Now save that as something like '/usr/local/bin/screenshot'
 
Go into gconf-editor, then nav on to '/apps/metacity/keybinding_cammands/cammand_screenshot' and assign the value of 'screenshot' or '/usr/local/bin/screenshot' whichever you prefer.
 
Now you should be able to take a quick screenshot of your desktop, and have it saved to ~/screenshots, and a thumbnail saved to ~/screenshots/thumbs
 
Remember, this is my very first ever shell script, and I'm sure this could have been more efficient, but it work's fine for me. I only did this because I didn't like the gnome screenshot thing, and I needed a thumbnail for my image.
Have fun with it
 
UPDATE:
I was just searching around the net when I found this on O'Reilly, basicly it takes a screenshot with a thumbnail, but also allows you to upload it to a server taking out the hardest part of taking a screenshot.
[http://hacks.oreilly.com/pub/h/3181]("http://hacks.oreilly.com/pub/h/3181")
 
I havent tested it myself yet as I have no server to upload anything to, but it's here if anybody wants it.
 
UPDATED: Changed '/usr/bin' to '/usr/local/bin'

---

### Post by Juippisi on 2005-04-12
It seems that this shellscript uses ImageMagick, yo can get it by typing "sudo apt-get install imagemagick"

But really nice howto and it works :)

---

### Post by kuleali on 2005-04-12
Nice howto

---

### Post by dude2425 on 2005-04-12
Whoops, I'm sorry, I could have sworn IM was installed by default. I don't remember having to install it extra myself, but synaptic's history says different. My fault.

---

### Post by macewan on 2005-04-12
nice

hell of a time saver too

thanks

---

### Post by vnbuddy2002 on 2005-04-12
Or if you don't want to install ImageMagick, you can just simply use GIMP.

Run "GIMP Image Editor", go to "File > Acquire > Screenshot"
 :grin:

---

### Post by crane on 2005-04-17
I cannot for the life of me get my screenshots to work. Everything seems to be bound right but the printscreen key does nothing. 
Anyone have any ideas?

---

### Post by Fab on 2005-04-18
there seems to be something wrong with this script or my comp :P
if i hit the print button, it will make a screenshot, but the windows on the screenshot are in a different z-order then they really are
e.g.: i got a nautilus window above my desktop, above the nautilus a gaim convo, above the gaim a firefox window. i hit print, and i get the nautilus above the gaim window Oo

---

### Post by derrick1985 on 2005-04-18
That worked perfectly!

Thanks.

One problem I did have, I sudo nano and copied/pasted what you had there and saved it as /usr/bin/screenshot When I went to use it the first time, I got a permission error, so I sudo chmod 777 /usr/bin/screenshot and it worked fine the next time.

Thanks again.

---

### Post by Fab on 2005-04-18
ah, i do now know why :) it takes a short amount of time till the screenshot is actually taken, and in the meanwhile i always went to the nautilus window to check the screenshots, argh

---

### Post by o0f on 2005-05-01
[QUOTE=Fab]ah, i do now know why :) it takes a short amount of time till the screenshot is actually taken, and in the meanwhile i always went to the nautilus window to check the screenshots, argh[/QUOTE]
 sleep 5
changed to sleep 0 works fine.
great script i LOVE you for it.
removed the line to create dir also. My screenshot folder will flourish with them =D.
great for ss whores.

---

### Post by angrykeyboarder on 2005-05-01
[QUOTE=vnbuddy2002]Or if you don't want to install ImageMagick, you can just simply use GIMP.

Run "GIMP Image Editor", go to "File > Acquire > Screenshot"
 :grin:[/QUOTE]

For a quick and dirty transaction like this, nothing beats ImageMagick.

Besides, it's a ***very*** small program.....

---

### Post by Nob on 2005-05-01
or just use tupe **gnome-screenshot** in command line..

besides, this script works just fine

---

### Post by dude2425 on 2005-05-18
I used the `sleep 5` so I can prepare my screenshots kinda like a camera on a timer. Feel free to change it to 0, or even remove it if you wanted to. I originaly made it for my own lazyness, and then I realized *Hay, other people are lazy too, maybe they'll like this as much as I did.

I love scripts, they just make everything so much easier once you've got them to work.

---

### Post by cdk on 2005-06-12
[QUOTE=Fab]ah, i do now know why :) it takes a short amount of time till the screenshot is actually taken, and in the meanwhile i always went to the nautilus window to check the screenshots, argh[/QUOTE]
 wicked m8!  it still works and its a great time saver!

cheers,

---

### Post by boborosso on 2005-12-02
[QUOTE=dude2425]

Now save that as something like '/usr/bin/screenshot'

[/QUOTE]

Hello from a debianist. Debian people recommend to put your own stuff in /usr/local/bin instead, since /usr/bin is managed by the packaging system. 

If ubuntu is different, then pay no attention to the above, but I really think it's not.

---

### Post by dude2425 on 2005-12-02
Actually, I think that's where I had mine. I can't remember why I typed /usr/bin instead of /usr/local/bin
"The longer lasting brain fart. Now with new lemony smell"
 
I'll change the orriginal post.

---

### Post by j8a on 2007-12-11
Your advice about GIMP was simple, easy.. excellent

---

