---
title: "[SOLVED] default application for images"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by terrordrone on 2008-06-03
Hi

i have irfan view installed from wine, also its plugins

how do i make it my default image viewer

i user gutsy

thanks

---

### Post by sayakb on 2008-06-03
Right click on the image and select Properties. Click on the *Open With *tab and click Add button. Inflate *Use a custom command* and write there: **wine "~/.wine/drive_c/*path to irfanview executable*"**
(Please note the quotes) I assume that irfanview is in "~/.wine/drive_c/Program Files/Irfanview/" folder.
Remember, the folder path is case sensitive. Also, put it within double quotes.

---

### Post by terrordrone on 2008-06-03
> **LinuxIsInnovation said:**
> Right click on the image and select Properties. Click on the *Open With *tab and click Add button. Inflate *Use a custom command* and write there: **wine "~/.wine/drive_c/*path to irfanview executable*"**
(Please note the quotes) I assume that irfanview is in "~/.wine/drive_c/Program Files/Irfanview/" folder.
Remember, the folder path is case sensitive. Also, put it within double quotes.
i did that..
this is wat i added
wine "~/.wine/drive_c/Program Files/IrfanView"

then i select wine...

when i try to open the file, nothing happens

---

### Post by terrordrone on 2008-06-03
If i add

wine "~/.wine/drive_c/Program Files/IrfanView/i_view32.exe"

irfanview will launch but the image wont load in it

---

### Post by terrordrone on 2008-06-03
bump

---

### Post by derred on 2008-06-03
Open up a terminal and do the following

First make a scripts directory
```
mkdir scripts
```

now go into that directory
```
cd scripts
```

now we're going to make a new file
```
gedit iview
```

now paste the following program in the text file
```
#!/bin/bash
EXECUTE_STRING=$HOME"/.wine/drive_c/Program Files/IrfanView/i_view32.exe"
ROOT_DRIVE_MAPED_TO="z:"
WindowsFileName=${ROOT_DRIVE_MAPED_TO}`echo "$1" | sed 's/\//\\\/g'`
"$EXECUTE_STRING" "$WindowsFileName"
```

now save and exit gedit

once you are back in the terminal you can make the file executable
```
chmod +x iview
```

now you can exit the terminal

go to your pictures (of any format that you want to associate to irfan view) right click it, go to open with/open with other application

click on Use a custom command
click browse
go to the scripts folder we created and double click the iview file
where automatically inserted the '/home/USERNAME/scripts/iview' you have to add a space and %f

click open

---

### Post by terrordrone on 2008-06-03
> **derred said:**
> Open up a terminal and do the following

First make a scripts directory
```
mkdir scripts
```

now go into that directory
```
cd scripts
```

now we're going to make a new file
```
gedit iview
```

now paste the following program in the text file
```
#!/bin/bash
EXECUTE_STRING=$HOME"/.wine/drive_c/Program Files/IrfanView/i_view32.exe"
ROOT_DRIVE_MAPED_TO="z:"
WindowsFileName=${ROOT_DRIVE_MAPED_TO}`echo "$1" | sed 's/\//\\\/g'`
"$EXECUTE_STRING" "$WindowsFileName"
```

now save and exit gedit

once you are back in the terminal you can make the file executable
```
chmod +x iview
```

now you can exit the terminal

go to your pictures (of any format that you want to associate to irfan view) right click it, go to open with/open with other application

click on Use a custom command
click browse
go to the scripts folder we created and double click the iview file
where automatically inserted the '/home/USERNAME/scripts/iview' you have to add a space and %f

click open
thanks it works :D

---

### Post by Sbarton on 2008-06-03
Hi terrordrone, I also use Irfanview in Windows, have done for ages. You might want to look at 'Digikam', downloaded via synaptic. Once you have had a good look at it you will find a lot of similar features.
regards

---

### Post by terrordrone on 2008-06-03
> **Sbarton said:**
> Hi terrordrone, I also use Irfanview in Windows, have done for ages. You might want to look at 'Digikam', downloaded via synaptic. Once you have had a good look at it you will find a lot of similar features.
regards
ill have a look at that...

but irfan view is very fast, light , easy to use, many feature.. 
i have a soft corner for that software.. and i immensly respect that

will look at digikam too

---

### Post by yogo on 2008-06-03
I took a look at digikam, it required a lot of additional files to be installed as well. Anything real special about this app?

I use gthumb for a simple editor for cropping/resizing just general stuff in which I want the pic to open quickly.

When I need to do some graphic work, I use Fireworks or CS2.

---

### Post by Sbarton on 2008-06-04
terrordrone, like you I also find Irfanview light & fast and respect the author for the free software. However, now that I use Ubuntu more (the majority of time) I find that it makes sense to use the software that can be used without using 'wine'which can be a bit flaky with some programs.'Digikam'is just one of these.

yogo, with 'Digikam'it's just that after deciding to install this instead of using 'wine'and Irfanview which I was used to. I found lots of similarities and more, with some features of other graphics software (colour, enhancing,filters,transforming,decorating etc).I find it does what I want.
However, it may not be what someone else needs for their graphics work.
worth a look though.
regards

---

### Post by yogo on 2008-06-04
> **Sbarton said:**
> 

yogo, with 'Digikam'it's just that after deciding to install this instead of using 'wine'and Irfanview which I was used to. I found lots of similarities and more, with some features of other graphics software (colour, enhancing,filters,transforming,decorating etc).I find it does what I want.


Thanks for you reply, I think I will stick with gthumb, it has the basics I need when I am scaling pics for emailing etc....and it opens quick. F-spot did not do it for me.

When it comes to photo manipulation and graphic work I will stick to Fireworks and some times Gimp or CS2.

I have tried Gimp-shop but it has never worked for me other than adding a new splash screen, I still get multiple docks.

I may try it in HH but I fear it will be much the same as it seems to have been a dropped project.

---

