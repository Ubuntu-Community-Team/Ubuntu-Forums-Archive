---
title: "gtkdialog for bash scripts"
date: 2008-08-15
forum: Programming Talk
---

### Post by glantucan on 2008-08-15
Hello all

I'm trying to code a front-end for several image and video editing tools with bash. My goal is to build a sort of suite for photographic workflow and for stop-motion animation production. That's it, but it's not so short to do it.

At the moment I'm just trying to:
[LIST=1]
[*] Select a few raw files from nautilus and open a dialog which allows to preview the jpg image embeded in them (this is done via ufraw)
[*] Choose the file I want to use as "template" open it with ufraw, develop the "digital film" and apply all those settings to all previously selected images using ufraw-batch and save them all as jpg or png.
[*] Post-process the images through ImageMagick using a dialog which allows basic image manipulation like brighness, contrast, hue, saturation etc. control thorugh ImageMagick
[/LIST] 
That's enough for the beginning. 
Of course I could use gimp for all those things, but what I want is a batch processing utility. Gimp has its scripting capabilities, but if I have to learn I prefer to extend my bash knowledge than trying to learn the script-fu *alien* syntax :P. And of course ImageMagick seems to do its job very well and it's well documented.

What I would not imagine is my main problem to come from gtkdialog that at the beginnig looked so promising, and now is giving me such a headache.

Step 1 listed above it's done if I use a external program to do the job of previewing. But I invested a lot of trial and error on getting the image preview on a pixmap widget. The point here is that I don't want to save the image preview to the hard disk, so I'm using pipes all the time. 

Currently I use this, redirecting the output of *ufraw* to the Imagemagick tool *display*
```
ufraw-batch --create-id=also --out-type=jpeg --output=- --size=400 --embedded-image $1 | display - 
```
How could I insert it directly on the pixmap widget directly without saving it?.

Step 2 is almost done and has nothing to do with gtkdialog

Step 3 is just not started, because I can't find a way to make faders for adjusting *convert*(ImageMagick) parameters.

This is test script I'm working with
```
#!/bin/bash

archivos=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS


#function ChannelPreview {
#ufraw-batch --create-id=also --out-type=jpeg --output=- --size=400 --embedded-image $1 | convert - -channel B -separate - | display -
#}

# This generates the tags needed to feed the table with the file names 
archItems=$(echo $archivos | sed -e "s_[^ ]*_<item>&</item>_g" )

export MAIN_DIALOG="
 <vbox>
   <table>
       <height>150</height><width>550</width>
       <variable>TABLE</variable>
       <label>Choose a file to start</label>
       $archItems
	<action>~/bin/__istDs2jpeg_THESE_actions.sh preview \$TABLE &</action>
   </table>
   <hbox>
   <button ok></button>
   <button cancel></button>
  </hbox>
 </vbox>"

gtkdialog --program=MAIN_DIALOG
unset MAIN_DIALOG
#clear
exit 0 

```

Some weird things I don't understand:
[LIST]
[*] I can't call in any way I know a local (I mean inside this script) function from an <action> tag. That's the reason the ChannelPreview function is commented out; but I can call a function inside another script with no problem !!!!!?????
[*] As you can see variable syntax like $archItems is accepted in some places but inside <action> I had to use \$TABLE. Is it because the first one is defined in the bash part of the script and the latter is defined inside the xml for the gtkialog?
[/LIST]

I can't find any good tutorial, manual or reference on gtkdialog. The documentation just sucks (sorry, but it's the truth) and it is not complete at all. I tried all my googling knowledge to find almost nothing. So I hope someone can help me if it is using it.

](*,)

Thanks 

Glantucan

---

### Post by yabbadabbadont on 2008-08-15
According to the website, the first line of your bash script *must be*:```
#! /usr/bin/gtkdialog -e
```

Did you try that?

Edit: I see what you mean about the lack of documentation.  I think I may have mis-interpreted the bash example when I made my initial comment above.  :oops:

---

### Post by glantucan on 2008-08-15
Sorry for the misunderstanding. The script is working.
Aditionally, I forgot to include this helper script, which for now only have a function:
```
#/bin/bash
function preview {
ufraw-batch --create-id=also --out-type=jpeg --output=- --size=400 --embedded-image $1 | display -title $1 -
}
```
And also to say that the main script is intended to be used as a nautilus script, which you execute from the context menu when some files are selected.

If I use the so called event driven aproach (I don't even know what that means) as in the web page examples I get this error message
```
sh: source: not found

** ERROR **: GtkDialog: Could not find the dialog description in the environment variable 'MAIN_DIALOG'.
aborting...
Aborted

```

Which is a documented but unsolved bug ([https://bugs.launchpad.net/ubuntu/+source/gtkdialog/+bug/177093](https://bugs.launchpad.net/ubuntu/+source/gtkdialog/+bug/177093))
I can live without event driven scripts as far as I don't know what they are :guitar: (Of course I'm kidding, curiosity was always a must for me)

But, to be more concise, **I really  need to:**
- Learn How to make a fade control
- Understand the thing about variables
- Find a way to pipe the preview image to pixmap widget
- Just to rest in peace I would like to understand why I can't call a local function from an action, but I can call a function on another script.

Thanks for the quick response

---

### Post by glantucan on 2008-08-16
From [**[SOLVED] want to create link to ramdisc**]("http://ubuntuforums.org/showpost.php?p=5507295&postcount=3"):
 > here is what i have been told and i have tried it and it works

If you just want to link to it (and not create a whole new vfs mountpoint) the easy way is to do the following from the command line:

cd /media
sudo ln -s /dev/shm ramdisk

That will create a symbolic link. From there, you can make a bookmark in nautilus by clicking and dragging the location to the sidebar.

now in my nautilus i can see a directory called "ramdisc" and its all good!

So I could save to ram the jpg files created by ufraw and read them easily from the gtkdialog xml part of the script, using a var for the file name.

But this is just a workaround. There must be a way to do it with pipes.
Grrrr! Being a self-learning guy can be tough!

---

### Post by glantucan on 2008-08-16
Oh! Fantastic!:mad:

Now I can load the temp images in the pixmaps (as they have finally a file name)
But I can't find a way to update the pixmap when clicking in another element of the table.

From [http://xpt.sourceforge.net/techdocs/language/gtkdialog/gtkde02-GtkdialogExamples/single/](http://xpt.sourceforge.net/techdocs/language/gtkdialog/gtkde02-GtkdialogExamples/single/)
For example [http://xpt.sourceforge.net/techdocs/language/gtkdialog/gtkde02-GtkdialogExamples/ar01s06.html](http://xpt.sourceforge.net/techdocs/language/gtkdialog/gtkde02-GtkdialogExamples/ar01s06.html)
I got that you can use actions to refresh the content of a named widget through its variable name. But this does not work for the pixmap widget.
More Grrrr for today.

I'm going to eat something, update this later...:confused:

UPDATE--
Here is the code. You need ufraw and gtkdialog installed.

I changed a little the script for easy testing. Now it reads input files from the command line.
It uses functions in another script, cause as I posted before it can't reach functions in the same script form the XML.

```
#!/bin/bash

archivos=$* 

ln -s /dev/shm ramdisk
tempdir="$(pwd)/ramdisk"

archItems=`echo $archivos | sed -e "s_[^ ]*_<item>&</item>_g"` 

export MAIN_DIALOG='
<window title="Digital Develop">
 <vbox>
   <text>
	<label>Choose a picture</label>
	<input>echo $archivos</input>
   </text>
   <table>
       <height>150</height><width>550</width>
       <variable>TABLE</variable>
       <label>"Choose a file to start"</label>
       '$(echo $archivos | sed -e "s_[^ ]*_<item>&</item>_g")'
	<action>~/bin/develop_functions.sh previewgtk $TABLE </action>
	[COLOR="Red"][B]<action>refresh:IMAGE</action>
	<action>refresh:IMAGE_NAME</action> [/B][/COLOR]
	
   </table>
   <text>
        <variable>[COLOR="Red"]IMAGE_NAME[/COLOR]</variable>
        <input>echo $TABLE</input>
   </text>
   <frame Pixmap from File>
      <pixmap>
	<variable>[COLOR="Red"]IMAGE[/COLOR]</variable>
        <input file>ramdisk/temp.jpg</input>
      </pixmap>
	
    </frame>

   <hbox>
  <button ok></button>
  <button cancel></button>
  </hbox>
 </vbox>
</window>'

gtkdialog --program=MAIN_DIALOG
unset MAIN_DIALOG
#clear
exit 0 
```

Here is the develop_functions.sh script:
```

#!/bin/bash
function previewgtk {
  rm ramdisk/temp.jpg
  ufraw-batch --overwrite --create-id=also --out-type=jpeg /
       --output=ramdisk/temp.jpg --size=400 --embedded-image $1

}

```
Refreshing IMAGE_NAME works, the text box gets updated.
Refreshing IMAGE doesn't work, the pixmap doesn't get updated.

Yes, I surrender,... for now. I will use display command till I get some feedback.

Is there anyone who can help? [-o<
This thread it's becoming like a personal diary :rolleyes:

---

### Post by glantucan on 2008-08-16
Another surprise I found today. 

You can include any command in an action tag. Theoretically it starts a subshell to execute it. So, if I include:
```
<action>~/bin/develop_functions.sh zoom $Res_x </action> 
``` 
It should execute *zoom* function inside *~/bin/develop_functions.sh* script passing it the *$Res_x* variable.

Well the problem is that this variable is not defined inside the exported gtkdialog xml definition, then it won't find it. Why?

Main script:
```
#!/bin/bash

archivos=$* 

Res_x=`xvidtune -show | sed 's/"\(.*\)x.*/\1/'`
Res_y=`xvidtune -show | sed 's/.*x\(.*\)".*/\1/'`
echo "Detected resolution is $Res_x x $Res_y"

ln -s /dev/shm ramdisk
tempdir="$(pwd)/ramdisk"

archItems=`echo $archivos | sed -e "s_[^ ]*_<item>&</item>_g"` 

export MAIN_DIALOG='
<window title="Digital Develop">
 <vbox>
   <text>
	<label>Choose a picture to open with ufraw</label>
	<input>echo $archivos</input>
   </text>
   <table>
       <height>150</height><width>550</width>
       <variable>TABLE</variable>
       <label>"Choose a file to start"</label>
       '$(echo $archivos | sed -e "s_[^ ]*_<item>&</item>_g")'
	<action>~/bin/develop_functions.sh preview $TABLE &</action>	
   </table>
   <frame Opciones>
	<button>
   		<label>Zoom Preview</label>
   		<action>~/bin/develop_functions.sh zoom $Res_x </action>
   	</button>
   </frame>
   <hbox>
   <button ok></button>
  <button cancel></button>
  </hbox>
 </vbox>
</window>'

gtkdialog --program=MAIN_DIALOG
unset MAIN_DIALOG
#clear
exit 0 
```

And the helper **develop_functions.sh**
```
#!/bin/bash

function preview {
  #ufraw-batch --create-id=also --out-type=jpeg --output=- --size=400 --embedded-image $1 
  # | display -geometry 400x300+700+0 -title $1 -
  [COLOR="DarkGreen"]# I resigned to use the ramdisk trick to avoid writing to disk. The pipe
  # did not work with the display's -remote option [/COLOR]

  ufraw-batch --create-id=also --overwrite --out-type=jpeg --output=ramdisk/temp.jpg /
          --size=400 --embedded-image $1 
  display -geometry 400x300+700+0 -title $1 -remote ramdisk/temp.jpg
}

function zoom() {
  [COLOR="DarkGreen"]# gtkdialog doesn't have rangebox or spinboxes (right? they are not documented at least)
  # so I will use Xdialog for this. Having different kind of windows isn't nice but should do the job.[/COLOR]
  ZOOM=`Xdialog 2>&1 --title "Tamaño de Previsualización" /
     --rangebox "cambia el tamaño por favor:" 8 24 400 **$1** 400` 	

  case $? in
    0)
      echo "maxSize set to $ZOOM.";;
    1)
      echo "Cancel pressed.";;
    255)
      echo "Box closed.";;
  esac

} 
```

Now, if I change 
```
Res_x=`xvidtune -show | sed 's/"\(.*\)x.*/\1/'`
```
for 
```
[COLOR="Red"]export[/COLOR] Res_x=`xvidtune -show | sed 's/"\(.*\)x.*/\1/'`
```
Then it works. I'm missing the point here too.

---

### Post by airtonix on 2008-08-21
Here is what i can help you with : the 'export' command there makes variables global, making them available to pretty much any process running on your computer.

And as far as I know, variables defined inside a script are only locally available to the current script.

So, considering that some of the action taking place in your efforts here are spawning extra 'terminals' as it were...then it means that the variables you define are out of scope or not in the locally available pool of variables.

hope i made sense.

My suggestion would be to take the variables you need through out all your various scripts and make them global.

---

### Post by dtmilano on 2008-08-21
You should take a look at [autoglade]("http://autoglade.sf.net") that definetly will simplify using GUIs from your scripts.
Some of the [tutorials]("http://autoglade.wiki.sourceforge.net/autoglade+tutorial+-+first+steps") available include examples similar to what you are trying to accomplish, for example using Nautilus Actions.
autoglade-0.4 was just released, you can see some of the [new features with screenshots]("http://codtech.com/wiki/index.php/Autoglade").

---

### Post by glantucan on 2008-08-21
I've been pretty busy trying to plan same parts of my little project and make the work. I had a lot of help at [GoblinX forum of the cave tutorial on gtkdialog]("http://forum.goblinx.com.br/viewtopic.php?t=786&postdays=0&postorder=asc&start=0&sid=46cf14d035634c498768971227901636"). And I don't have many things very clear yet, but trying to answer...
 
> **airtonix said:**
> Here is what i can help you with : the 'export' command there makes variables global, making them available to pretty much any process running on your computer.
[...]
My suggestion would be to take the variables you need through out all your various scripts and make them global.
Yes I know and that's the reason I don't like it. I don't want my scripts to mess with environment variables. 

Anyhow, I think the problem is that i don't understand very well the quoting syntax in gtkdialog's XML. THere is a difference between having the window XML exported single quoted and double quoted. I can't specify more because I made so many different tests that I can't remember.
Now I'm just trying to figure out what is the best tool for each part. For now my bet is bash for scripting, ufraw for raw digital development, Imagemagick for postproducing the images and gtkdialog or other for the GUI (even combined with son C or C# for some specific dialogs like the gamma curve tool if its not supported by gtkdialog or the like)
> **dtmilano said:**
> You should take a look at autoglade that definetly will simplify using GUIs from your scripts.
Some of the tutorials available include examples similar to what you are trying to accomplish, for example using Nautilus Actions.
autoglade-0.4 was just released, you can see some of the new features with screenshots. 

Yes, I will have a more careful look at it, sounds promising.
But for now the part I'm more concerned with is to get the gamma curve gtk widget working (That doesn't seem possible with autoglade either) guess I'll have to refresh some C knowledge.

Thanks anyway :)

---

