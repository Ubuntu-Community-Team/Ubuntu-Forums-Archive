---
title: "simple desktop-changing script"
date: 2009-09-20
forum: Programming Talk
---

### Post by flyingsliverfin on 2009-09-20
i know some very basic shell scripting, but how do i create a script that will change my desktop background every time i log in? i have about 5 different jpegs that i realy like so i want to have a diferent one each log in

dont just tell me right off, i want to figure something out myself. the only 2 things i want are: first, what is the command that will change the background. if there is none, what is the config file that has the background image location? the second thing is, how do i create simple for or while loop? i know some python and basic and java, but i dont know how to do it in scripting.

thx

---

### Post by kaibob on 2009-09-21
> **flyingsliverfin said:**
> ...dont just tell me right off, i want to figure something out myself. the only 2 things i want are: first, what is the command that will change the background. if there is none, what is the config file that has the background image location? the second thing is, how do i create simple for or while loop? i know some python and basic and java, but i dont know how to do it in scripting. 
thx
With Ubuntu, the desktop background is saved in the GConf database and can be viewed or changed with the GConf editor at the following key:

/desktop/gnome/background/picture_filename

You can change the value of this key with the command line as follows:

```
gconftool-2 --type str --set /desktop/gnome/background/picture_filename /path/to/file.jpg
```

If you simply want to rotate five backgrounds at boot, I'm not sure you would need a for or while loop, but you can find a good discussion of these at:

[http://mywiki.wooledge.org/BashGuide#BashGuide.2BAC8-TheBasics.2BAC8-TestsAndConditionals.Conditional_Loops_.28while.2C_until_and_for.29](http://mywiki.wooledge.org/BashGuide#BashGuide.2BAC8-TheBasics.2BAC8-TestsAndConditionals.Conditional_Loops_.28while.2C_until_and_for.29)

I have read reports of the GConf database being damaged when changed at the command line, so be sure to have a reliable backup.

---

### Post by falconindy on 2009-09-21
> **flyingsliverfin said:**
> how do i create simple for or while loop? i know some python and basic and java, but i dont know how to do it in scripting.
This should look familiar then...
```
while [[ condition ]]; do
    # stuff happens here
done
```

---

### Post by flyingsliverfin on 2009-09-23
maybe i should have asked for the basics first: how do i make a file execute at log-in?

---

### Post by kaibob on 2009-09-23
The easiest way is to use the Startup Programs tool:

*System > Preferences > Startup Applications > Add*

You can also do this by way of the crontab file with the @reboot option:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

[http://www.debianhelp.co.uk/crontab.htm](http://www.debianhelp.co.uk/crontab.htm)

---

### Post by flyingsliverfin on 2009-09-26
heh, im finding this  bit hard with  a language that i hardly know. is there any way to exceccute the command for changing the desktop background in python?

---

### Post by phrostbyte on 2009-09-26
```
os.system("<command goes here>")
```

---

### Post by flyingsliverfin on 2009-09-28
lol i just found an easier way to do it i think. it might take  a bit to test the idea though. ill let u know when i get it

---

### Post by flyingsliverfin on 2009-09-28
:lolflag:   that was really easy. i was mkaing it way to hard for myself: heres my script (though its written in python)

[PHP]

#! /usr/bin/python

import os
import random
shuffle = [0,1,2,3]

random.shuffle(shuffle) 

if shuffle[0] == 0:
	os.system("gconftool-2 --type str --set /desktop/gnome/background/picture_filename /home/joshua/Desktop/ALL/downloaded_wallpaper/a.jpg")
if shuffle[0] == 1:
	os.system("gconftool-2 --type str --set /desktop/gnome/background/picture_filename /home/joshua/Desktop/ALL/downloaded_wallpaper/k.jpg")
if shuffle[0] == 2:
	os.system("gconftool-2 --type str --set /desktop/gnome/background/picture_filename /home/joshua/Desktop/ALL/downloaded_wallpaper/j.jpg")
if shuffle[0] == 3:
	os.system("gconftool-2 --type str --set /desktop/gnome/background/picture_filename /home/joshua/Desktop/ALL/downloaded_wallpaper/d.jpg")

[/PHP]

the only problem now is that it always asks me the 'run in terminal' 'display'  etc pop-up every time... any way not to let it ask that on that specific script?

---

### Post by flyingsliverfin on 2009-09-28
actually that only works if i click on it manually.... i cant figure out whats wrong when i put it under startup  app's

---

### Post by renkinjutsu on 2009-09-28
did you put the script into one of your PATH directories? if not, you'll need to specify the full path to the executable in your startup settings..

/path/to/python/script

---

### Post by flyingsliverfin on 2009-09-28
i think i did...i put under 'command' /home/joshua/Desktop/ALL/scripts/desktop-changer.py

thatas the whole path

---

### Post by diesch on 2009-09-28
The shell script version is a bit shorter:

```

#!/bin/sh
gconftool-2 --type str --set /desktop/gnome/background/picture_filename "$(ls [COLOR=#000000][COLOR=#dd0000]/home/joshua/Desktop/ALL/downloaded_wallpaper/*.jpg[/COLOR][/COLOR]|sort -R| head -n1)"

```:-)

---

### Post by flyingsliverfin on 2009-09-29
!!

is there a way to make it stop asking me to run in terminal or whatever?

---

### Post by diesch on 2009-09-29
Nautilus always asks before executing a script. But you can create a starter for it on the desktop.

---

### Post by engla on 2009-09-29
> **flyingsliverfin said:**
> :lolflag:   that was really easy. i was mkaing it way to hard for myself: heres my script (though its written in python)

[PHP]

#! /usr/bin/python

import os
import random
shuffle = [0,1,2,3]

random.shuffle(shuffle) 

if shuffle[0] == 0:
	os.system("gconftool-2 --type str --set /desktop/gnome/background/picture_filename /home/joshua/Desktop/ALL/downloaded_wallpaper/a.jpg")
if shuffle[0] == 1:
	os.system("gconftool-2 --type str --set /desktop/gnome/background/picture_filename /home/joshua/Desktop/ALL/downloaded_wallpaper/k.jpg")
if shuffle[0] == 2:
	os.system("gconftool-2 --type str --set /desktop/gnome/background/picture_filename /home/joshua/Desktop/ALL/downloaded_wallpaper/j.jpg")
if shuffle[0] == 3:
	os.system("gconftool-2 --type str --set /desktop/gnome/background/picture_filename /home/joshua/Desktop/ALL/downloaded_wallpaper/d.jpg")

[/PHP]

the only problem now is that it always asks me the 'run in terminal' 'display'  etc pop-up every time... any way not to let it ask that on that specific script?

Just as an excercise, let's type this up a bit more Pythonic:

[PHP]
#!/usr/bin/python

import os
import random

backgrounds = os.listdir("/home/joshua/Desktop/ALL/downloaded_wallpaper/")
new_bkg = random.choice(backgrounds)

os.system("gconftool-2 --type str --set /desktop/gnome/background/picture_filename %s" % new_bkg)

[/PHP]

---

### Post by flyingsliverfin on 2009-09-29
listdir does what? (i sppose i can figure it out just by looking at the word but i dont want to mix myself up for next time)

Apart from that im a beginner at python :( i wish i werent. 

i like that word 'pythonic'

sorry if this all sounds a bit childish  (im only 13)

---

### Post by fiddler616 on 2009-09-29
> **flyingsliverfin said:**
> !!

is there a way to make it stop asking me to run in terminal or whatever?

The problem of making Python programs executable crops about every three months here. I think for your purposes you need to Google something along the lines of "chmod +x python", IIRC.

---

### Post by diesch on 2009-09-29
> **engla said:**
> Just as an excercise, let's type this up a bit more Pythonic:

[php]
#!/usr/bin/python

import os
import random

backgrounds = os.listdir("/home/joshua/Desktop/ALL/downloaded_wallpaper/")
new_bkg = random.choice(backgrounds)

os.system("gconftool-2 --type str --set /desktop/gnome/background/picture_filename %s" % new_bkg)

[/php]

new_bkg is just the file name, but you need the full path.

Without calling gconftool-2:

```

#!/usr/bin/env python

import os, os.path, random, gconf

bkg_dir = "/home/joshua/Desktop/ALL/downloaded_wallpaper/"
new_bkg = os.path.join(bkg_dir, random.choice(os.listdir(bkg_dir)))

gclient = gconf.client_get_default()
gval=gconf.Value(gconf.VALUE_STRING) 
gval.set_string(new_bkg)
gclient.set('/desktop/gnome/background/picture_filename', gval) 

```Time for advertising... ;-)

[http://www.florian-diesch.de/software/easygconf/](http://www.florian-diesch.de/software/easygconf/) makes accessing GConf easier:

```

#!/usr/bin/env python
import os, os.path, random, easygconf

bkg_dir = "/home/joshua/Desktop/ALL/downloaded_wallpaper/"
new_bkg = os.path.join(bkg_dir, random.choice(os.listdir(bkg_dir)))

gcd = easygconf.GConfDict('/desktop/gnome/background/')
gcd['picture_filename'] = new_bkg

```

---

### Post by flyingsliverfin on 2009-09-29
oh, u made that? cool :) did u write it? If u did, in what language?

sprechen sie den auch Deutsch?

---

### Post by engla on 2009-09-30
You got me there! Yeah I forgot the full path. Machen wir den Thread weiter komplett auf Deutsch? :-)

---

### Post by flyingsliverfin on 2009-09-30
Darf man das?

for you guys that cant read german: is it allowed to do a start a whole thread in english and then have it change compeltely to a different language?


maybe its  a stupid question, but ive been to forums where your only allowed to speak english

---

### Post by fiddler616 on 2009-09-30
German speakers: I recommend providing translations of what you said before somebody pulls out Google Translate and mangles it. This has happened before (between me and nvteighen, for one).

---

### Post by diesch on 2009-10-01
> **flyingsliverfin said:**
> oh, u made that? cool :) did u write it? If u did, in what language?


easygconf? Yes, I wrore it. Isn't anything fancy, just a few lines of Python to implement a dict-like interface for the GConf Python bindings. 



> **flyingsliverfin said:**
> 
sprechen sie den auch Deutsch?

Ja. Das habe ich schon als kleines Kind gelernt ;-)

---

### Post by diesch on 2009-10-01
> **flyingsliverfin said:**
> Darf man das?

Legal? Illegal? Scheißegal! ;-)

> **flyingsliverfin said:**
> 
for you guys that cant read german: is it allowed to do a start a whole thread in english and then have it change compeltely to a different language?


The Forum Rules say 
> 
Please try to write your posts in English. We have many users from many different countries that visit here.
But I guess we will not get banned immediately if we use some German ;-)

Using English for the important parts would be polite, though.

---

### Post by flyingsliverfin on 2009-10-02
lol.

---

