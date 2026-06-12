---
title: "HowTo: Converting Images (PNG to JPG)"
date: 2008-08-12
forum: Outdated Tutorials &amp; Tips
---

### Post by lukjad on 2008-08-12
**Please note, that any corrections or other tips that may be given in the responses that follow this HowTo will be included if they are useful. Credit will be given to the author(s). You will not be forced to read through pages and pages of comments to find out why something doesn't work. (If you wish to read it out of interest, you certainly may.)**

[SIZE="5"][CENTER]Converting Images From One Format to Another[/CENTER][/SIZE]

[SIZE="3"]Prologue: [/SIZE]

For a lot of people, file size is a big issue. The PNG format uses  lossless data compression which is useful in many cases. However, if you wish to send a file quickly or there is a limit on the file size permitted to be sent, sometimes you may wish to use a smaller file format. Here is a tutorial to show you how to do so using the Terminal.

For this tutorial, I will assume that you are saving your screenshot, at least initially, on your desktop.


[SIZE="4"]Step 1: Take your screenshot and save it.[/SIZE]

I'm guessing you knew that one. ;)  

[SIZE="4"]Step 2: Open the Terminal.[/SIZE]

The terminal can be found at Applications->Accessories->Terminal. 

Now type in the following command:

```
convert 
```
Make sure that there is a space after the word convert.

[SIZE="4"]Step 3: Drag 'n' Drop the Image[/SIZE]

Drag and drop the image to the Terminal and drop it there. The path to the image and the image name with the file extension name should appear. 

```
yourusername@home:~$ convert '/home/yourusername/Desktop/Convert/Screenshot.png'
```

[SIZE="4"]Step 4: Renaming the Screenshot or Image[/SIZE]

Before you put the name you want to call your new image there are some things you need to do first. 

Let's say that the original image or screenshot was called "Screenshot.png" and you want your new one to be in the JPG format and called "How Take a Screenshot" you need to do one of three things.

[INDENT]Choice 1 (Recommended)[/INDENT]
The quickest and easiest way to rename your file is to give it no spaces. If you need to have more than one word, simply use underscores_to_space_out_your_words. You can later rename the image to have spaces instead of underscores.

[INDENT]Choice 2 (Not recommended)[/INDENT]

If that's not what you want, you can just save it with the same name and rename it later.

[INDENT]Choice 3 (Really, really not recommended)[/INDENT]

If you really are a glutton for punishment, you can to use the backward slash (\) usually found on top of the Return or Enter key. 

This\ is\ how\ you\ use\ the\ backward\ slashes. 
When you type a word that will be followed by a space, you need to put a backward slash right next to it and **then** put the space. 

If you are using this approach and get this error message, you most likely missed a backward slash.

```
yourusername@home:~$ convert '/home/lukjad007/Desktop/Screenshot.png' How\ to\ take\ a Screenshot.jpg
convert: unable to open image `How to take a': No such file or directory.
```

[SIZE="5"]**Caution!**[/SIZE]

Please make sure that there is a space between the word "convert" and the '/home/yourusername/... or else you will get an error similar to this one:
```
bash: convert/home/yourusername/NewImageName.jpg: No such file or directory
```

[SIZE="3"]Last note[/SIZE]

And that's all there is to converting an image from one format to another. Or, you can always use GIMP and the "Save As..." feature.

---

### Post by Mahyar on 2010-03-20
Or just open the file with the default programme (Eye of Gnome) and 'save as' and change the file extension to .jpg.

---

