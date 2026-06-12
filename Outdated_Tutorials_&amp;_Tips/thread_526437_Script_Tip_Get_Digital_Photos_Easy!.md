---
title: "Script Tip: Get Digital Photos Easy!"
date: 2007-08-15
forum: Outdated Tutorials &amp; Tips
---

### Post by viajador on 2007-08-15
Hi there!

If you use a digital camera, you've probably wondered why import software (both in Ubuntu and XP) gets to be so rigid. They choose the folders name, they choose the amount of pictures per folder: and they never choose what I would like them to. I finally got around this problem writing down a little script that uses gphoto2.

So, what do I want? Something that, when I plug in my camera, will:

**1)** imports all my files;
**2)** creates folders acording to the date of the file and the type of file (AVI or JPG);
**3)** sends the files to the desired folders.

So, first things first: the necessary software. I use gphoto2 for this and it works great. Install it from Synaptic or from the command line:
```
sudo apt-get install gphoto2
```

Third: create a new file in a folder of your choice and copy+paste this code into it:

**Note:** I'm assuming that you already have folders where to put photos and videos.
```

#! /bin/bash

gphoto2 -P          # The -P option gets all your files from your 
                         # camera, both pictures and videos

JPGS="*.JPG"
AVIS="*.AVI"

# Creating folders and moving JPG files

for file in $JPGS
do
mkdir /home/<username>/<folder_where_you_keep_your_pictures>/"`date -r $file +%Y%m`"
mv $file /home/<username>/<folder_where_you_keep_your_pictures>/"`date -r $file +%Y%m`"
done

# Creating folders and moving AVI files

for file in $AVIS
do
mkdir /home/<username>/<folder_where_you_keep_your_videos>/"`date -r $file +%Y%m`"
mv $file /home/<username>/<folder_where_you_keep_your_videos>/"`date -r $file +%Y%m`"
done

echo "Done, Boss!"

```

Save the file with an easy to remember name, like GET_DIGI_FILES. 
Make the file executable:
```
sudo chmod +x GET_DIGI_FILES
```

Give it better permissions:
```
sudo chmod 777 GET_DIGI_FILES
```

Now, for the finale, you have at least three options:

**OPTION A**

You keep the file near you at all times and double click on it every time you plug your camera;

**OPTION B**

You copy your file to this very nice folder:
```
sudo cp GET_DIGI_FILES /usr/local/bin
```

**Note:** You can't copy it by dragging it using a windows explorer of some sort, since you'll need root permitions to write on this folder.

And now, you can simply open a console window everytime you plug your camera and type:
```
GET_DIGI_FILES
```

**OPTION C**

My choice!

Follow option B above, but add it an extra. Go to **System > Preferences > Movable Media** and select the **Camera** folder. There is a space there where you can write down a command for the computer to perform everytime a camera is plugued. Write the name of your file there and, from now on, you're all set for an automatic, friendly and organized importation scheme!

**Notes on the script:**

**1)** This script creates folders that look like 200608 for files that are dated from August, 2006. I like it this way, but you can change it! See that "`date -r $file +%Y%m`" bit of the code? That decides your folder's name. You can change it as you like! Try change it to %Y-%m to get a 2006-08 folder. Explore the date command options and do it as you like it best.

**2)** When the mkdir command tries to create a folder that already exists (which will happen, since I take more than one picture a month!), it will output an error: *the folder already exists*... go figure! The script proceeds on moving the file there anyway, so the actual problem is more an aesthetic one. It can be corrected with an IF structure (basically, if the folder already exists, than just move the damn file!). I didn't try and clean the error out of the script because it doesn't bother me - I'm not looking at the command as the script runs, so I just care if the files went to the correct folders. But, of course, you can clean it if you like.

Well, that's all! Hope you enjoy it. Please don't beat me up if this is too simple or too confusing or too both! I'm a Linux newb and this is my first kind-of-a-tutorial to something.

Até à próxima :)

---

