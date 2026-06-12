---
title: "HOWTO: Custom Icons on the Desktop"
date: 2005-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by BLTicklemonster on 2005-11-19
My first How to, please be nice if I totally dweeb this up, lol. No wiki yet, just testing the waters.

How to create custom icons on your desktop (if you want to do such a thing) for programs that you normally can only launch from the command line, or if you just want to customize your icons because you can.


If you are one of those people who would rather have a desktop icon to use when launching a program that you installed that can only be launched from the terminal, there is a way to do this.


You need to be familiar with the "take a screenshot of your desktop" button. It is under System in your toolbar. I'd drag it to the quick launch section of the toolbar so as to have easier access to it for now. 

Let's say you have installed Hydrogen (from terminal, 

```
sudo apt-get update
```

 , then 

```
sudo apt-get hydrogen
``` 

if you want it, it's a cool drum machine thingy that I have no idea how to use, but want to learn if anyone knows how, please pm me) and the only way you can run it is from terminal... or there's other programs that you can only run from the terminal (hydrogen might already be in my Applications if I reboot or log out and back in, I don't know, but follow me on this anyway without belittling me, mkay?).

Be sure you have gimp installed, too. You can get it from the synaptic package manager under System>Administration>Synaptic Package Manager just scroll to it in the top left hand screen and click on it, mark it for installation, then install it. Of course it's probably already installed in Applications>Graphics...

Now, from the terminal (Applications>Accessories>Terminal) type the program name you want to launch, if it was hydrogen, then type hydrogen but know exaclty where your take screenshots button is! When you press enter to launch your program, get your mouse pointer over the screenshot button real quick, and the instant the splash screen comes up, press the screenshot button.

This will bring up a window showing the screenshot and asking you where to save it. See that the splash screen is displayed correctly (your timing may be off a bit so you may have to do this a couple of times) then save the image to your desktop.

You can close hydrogen, or whatever you ran now.

Right click on the screeny file that's now on your desktop, and chose open with gimp.

Now that the image is open, you will have several windows open, too; the image itself, another called Layers, Channels, etc. and one called The Gimp. Click on the one called The Gimp, then chose the Select Rectangular Regions function (top left, dotted looking rectangle thing), 

[img]http://www.hawkwinds.com/tickle/custom-icons/selectrec.png[/img]

and go to the image window, now draw a rectangle around the part of the image you want as your icon (close as you can get to the edges of what you want),

[img]http://www.hawkwinds.com/tickle/custom-icons/selected.png[/img]

go to edit, then click copy, then go to edit again, and click paste as new. You will now have a new image of what you want as your icon. 

[img]http://www.hawkwinds.com/tickle/custom-icons/new.png[/img]

Save this to your desktop as icontemplate.png so you can go back fresh if something goes awry.

(this next section deals with making an icon with a transparent background, skip it and go to the section on resizing if you don't want to do this)

Now go back to The Gimp, and click on select contiguous regions (third thing to the right from the dotted rectangle thing, it looks like a wand with a yellow thingy on the end of it) 

[img]http://www.hawkwinds.com/tickle/custom-icons/contiguous.png[/img]

look down in the same window and you will see "Fuzzy Select". (any of you who are more familiar with Gimp, hop right in when you see me doing things the hard way now!) I'd set the Threshold at around 20 for now.

Go back to your image, and click on the blue background (for this example, Im using the drumming penguin from hydrogen), 

[img]http://www.hawkwinds.com/tickle/custom-icons/contselected.png[/img]

right click it, and go to edit, then click "clear", or just press ctrl+k. You ought to see a checkerboard design pop up instead of the blue. 

[img]http://www.hawkwinds.com/tickle/custom-icons/ctrlk.png[/img]

Muahaa, we're on our way now! Now do this again and again to the blue background until it is all gone. If you find that too much of the image is removed when you click clear, then go to edit, and undo until you are back where you want to be. Change the threshold to a lower number. Then again, if it's not taking enough, chose a higher number.

Now that you have all the background removed, you want to resize it. I find that at the resolution I run my desktop at, if I choose 112 X *, the the icon isn't too big, nor too small. You decide what you want. The way to do this resizing is to click, in the tool bar in the window that holds your icon image, Image>Scale Image, then chose 112, and press enter. 

[img]http://www.hawkwinds.com/tickle/custom-icons/scale.png[/img]

Normally the second dimension will change, too. If not, the click the chain that links the two numbers. See if your image looks the right size. if not click edit and undo and try again.

Now you can save your new icon. But first you must have priveleges to save in pixmaps, so lets open terminal, and type

```
cd /usr/share/pixmaps
```

```
sudo chown yourname /usr/share/pixmaps
```

enter your password, and you are good to go, so close the terminal

Now save the image by clicking File>Save as and type the name you want for the icon, like hydrogen.xpm (you can type the extension instead of clicking select file type (by extension) and it will understand what you are doing) now click on Browse for other folders, and then click in the left hand window on File System, then in the right window, click usr, then share, then pixmaps. Click save, when asked the alpha threshold you want, the default is okay, but being the button pushing slider sliding tweaker I am, I always slide it all the way to the right, lol. Click okay, then it will save it for you.

Now you can create a launcher for your desktop. I'm doing this in breezy using gnome, so it may be different for you if you aren't sorry if you can't get it right, but if so, and you figure it our, hop in and tell us what you did, mkay?

Now you want to close the gimp, so go to the The Gimp window and close it, you don't have to save anything you did, so you can disgard changes. Now right click on your desktop somewhere, and click on create launcher. In the top section, type a name for you launcer, like Hydrogen, then you can put what you want in the other spaces, but under command, put what you have to enter in terminal to launch the program. For hydrogen, type in 

hydrogen

then click on the No Icon button, scroll down to your icon, double click it. I don't know any better about all this, so I always click on the Run in Terminal box, then click okay.

You now have an icon on your desktop that you can use to launch your program. 

You can use Gimp to create a drop shadow to give you icon a cool 3d look. I can get into this later, or someone else can show us, either way. 

I hope that this is helpful to any of you who like the ease of desktop icons. I'm sure others out there are abhored at this, they must realize that some ubuntu users are going to be the casual types who aren't concerned with the command line. Hey, it's okay for them to be like this! We want them to feel comfortable with ubuntu, right? 

I'll post images to go with all this at a later date so it will be easier. I hope this is detailed enough for anyone to follow without imagery, though.

Here are some I've made:

[img]http://www.hawkwinds.com/tickle/customicons.jpg[/img]

You can remove the launcher name by right clicking it, and pressing enter or delete while the text is highlighted, the click on the desktop somewhere and the text no longer appears. Or just don't name the launcher in the first place probably.. that just now occured to me, so I'm not sure... probably have to put something, so try pressing the space bar?

I hope I covered all the bases, and that any newcomers can follow this easily enough to get it right the first time. I really want to help anyone who is new to linux and ubuntu so that they have as easy a transition to ubuntu as possible. 

Ticklemonster.

(okay time for you pros to set me right, so please hop in and help me before I mess anybody up! and thank you if you do!)

---

### Post by BLTicklemonster on 2005-11-20
lol so far so good... no one has shredded this post.

---

### Post by benplaut on 2005-11-20
[QUOTE=BLTicklemonster]lol so far so good... no one has shredded this post.[/QUOTE]

shred shred shred shred!!!!

good post, but the problem is, 99% of programs have icons available somewhere :rolleyes:

---

### Post by BLTicklemonster on 2005-11-20
Good point, but say my kid sees your avatar and demands, no DEMANDS that I make it her launch icon for something.

:cool: 

custom icons.

---

### Post by linkunderscore on 2005-11-30
[QUOTE=BLTicklemonster]Good point, but say my kid sees your avatar and demands, no DEMANDS that I make it her launch icon for something.

:cool: 

custom icons.[/QUOTE]


You tell your kid to quit being a little brat and send her to her room. :smile: 
 :P 

Its an excellent how to but I don't really have the need for it. I learned some about gimp though :)

---

### Post by psoleko on 2005-11-30
[QUOTE=BLTicklemonster]Good point, but say my kid sees your avatar and demands, no DEMANDS that I make it her launch icon for something.

:cool: 

custom icons.[/QUOTE]

Good thing your kid didn't see Ben's old avatar. It was a very Ubuntu cookie monster. I don't think he'd mind it being a launch icon though :razz:

Not a bad howto at all.

---

### Post by ekravche on 2005-12-04
pretty cool. Thanx for the howto

---

### Post by Yed Ied on 2009-05-07
Great post, too bad you don't know about our global environment.

---

### Post by sb92075 on 2009-05-09
Minor nit.
```

sudo apt-get hydrogen

```

should actually be
```

sudo apt-get install hydrogen

```

---

### Post by mit10 on 2009-08-12
ummm... ticklemonster, I think I love you! anyways, just want to say this was a great tutorial and learned a bunch from it. Thanks!

---

