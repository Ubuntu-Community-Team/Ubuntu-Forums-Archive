---
title: "change text color in terminal"
date: 2016-02-20
forum: New to Ubuntu
---

### Post by flex567 on 2016-02-20
How can I change text color for terminal text permanently?

---

### Post by howefield on 2016-02-20
Profile Preferences > Colours would be the easy way ?

---

### Post by claracc on 2016-02-20
You will find the answer viewing the help in your terminal and choosing personalizad colour scheme in personalizing appearance, colour schemes. It is exhaustively and clearly explained.

In short, you have to select in terminal, edit ---> profile preferences---> colours. You can change the background colour too.

---

### Post by PopsTheSailor on 2016-06-25
A bit of an old thread but hoping someone can answer this. When editing the colour preferences via the menu options, I couldn't find any way to change the colours for folders. They are using a green text and green shading and I would like to make them easier to read. How do I customize to that level without installing any apps.

---

### Post by &amp;KyT$0P# on 2016-06-25
@PopsTheSailor please post a screenshot of what you would like changed

---

### Post by PopsTheSailor on 2016-06-25
How do I insert an image? There's an option in my forum editor to insert an image but it then asks for a URL. I've never added a picture to a post before.

---

### Post by QDR06VV9 on 2016-06-25
> **PopsTheSailor said:**
> How do I insert an image? There's an option in my forum editor to insert an image but it then asks for a URL. I've never added a picture to a post before.

Bottom right you will see go advanced...and from there at the top you will see a Paper Clip use that to upload your image.
See Screenshot

---

### Post by PopsTheSailor on 2016-06-25
OK, found the paper clip. Here's the image, actually 2 images. All that stuff highlighted in green are folders (directories). Index.html is the only file. I'd like to remove the green highlighting and change the font to a different colour. The second screen shot is the profile preferences / colours tab. I don't see anything that lets me pick colours and backgrounds for folders.

[ATTACH=CONFIG]269780[/ATTACH]

[ATTACH=CONFIG]269781[/ATTACH]

---

### Post by yetimon_64 on 2016-06-25
> **PopsTheSailor said:**
> OK, found the paper clip. Here's the image, actually 2 images....
[ATTACH=CONFIG]269780[/ATTACH]

<snip 2nd image>

Only one of the images have been attached successfully, the first is a broken/invalid link here.

You have mentioned "folders" a couple of times now. eg >  I don't see anything that lets me pick **colours and backgrounds for folders**. Are you trying to change the text colour or background colour of folders in nautilus from the terminal ? The orignal question here seems to be more about changing the colour of the text in the terminal itself not of changing nautilus backgrounds or text from the terminal.

---

### Post by &amp;KyT$0P# on 2016-06-25
> **yetimon_64 said:**
> Are you trying to change the text colour or background colour of folders in nautilus from the terminal ...
... or the color of the cwd shown in the Terminal prompt, or something else?

---

### Post by vasa1 on 2016-06-25
> **yetimon_64 said:**
> ...
You have mentioned "folders" a couple of times now. eg  Are you trying to change the text colour or background colour of folders in nautilus from the terminal ? The orignal question here seems to be more about changing the colour of the text in the terminal itself not of changing nautilus backgrounds or text from the terminal.

+1

@ PopsTheSailor, This is a classic case of thread hijacking. Please start a new thread with a descriptive title and make it clear what exactly you want.

*And after you upload an image here, please visit your thread again and check that the image you uploaded does indeed convey meaningful information*.

---

### Post by uRock on 2016-06-25
I think this may be what PopsTheSailor is talking about.
[ATTACH=CONFIG]269783[/ATTACH]

---

### Post by &amp;KyT$0P# on 2016-06-25
That is controlled by the environment variable LS_COLORS

[Guide to the color numbers]("http://ascii-table.com/ansi-escape-sequences.php")

---

### Post by vasa1 on 2016-06-26
> **uRock said:**
> I think this may be what PopsTheSailor is talking about.
[ATTACH=CONFIG]269783[/ATTACH]
If that is the case then,
```
dircolors -p |less
```just to see what is what followed by```
dircolors -p > ~/.dircolors
```
after which using trial and error to change values or comment/uncomment lines should do it. As always, backing up ~/.dircolors would help.

---

### Post by uRock on 2016-06-26
Here are my settings for terminal and all of the folders show in the same color as everything else. My previous screenshot was from a VM install.

[ATTACH=CONFIG]269784[/ATTACH][ATTACH=CONFIG]269785[/ATTACH]

---

### Post by PopsTheSailor on 2016-06-26
You all all close. Trying again the picture from the broken link. It shows OK in my reply. It's the green shading I want to get rid of. Again, Index.html is a file. All the other ones are folders. This is in the terminal and not Nautilus. 

[ATTACH=CONFIG]269794[/ATTACH]

---

### Post by vasa1 on 2016-06-26
If you go the .dircolors route, the fix is as simple as looking for the line that looks like this:```
DIR 00;32
```and making sure that you have nothing after ";32" or whatever value you have.

Just something from ~.dircolors:> # Below are the color init strings for the basic file types. A color init
# string consists of one or more of the following numeric codes:
# Attribute codes:
# 00=none 01=bold 04=underscore 05=blink 07=reverse 08=concealed
# Text color codes:
# 30=black 31=red 32=green 33=yellow 34=blue 35=magenta 36=cyan 37=white
# Background color codes:
# 40=black 41=red 42=green 43=yellow 44=blue 45=magenta 46=cyan 47=white
#NORMAL 00 # no color code at all
#FILE 00 # regular file: use no color at all
RESET 0 # reset to "normal" color
DIR 00;32 # directory .................................................
LINK 00;36 # symbolic link. (If you set this to 'target' instead of a
 # numerical value, the color is as for the file pointed to.)
MULTIHARDLINK 00 # regular file with more than one link

Please note that I don't use gnome-terminal so if that's what you're using your results maybe different!

---

### Post by &amp;KyT$0P# on 2016-06-26
In the default color scheme that green background means the directory is world-writable.  If this is intentional, and you still don't want the green background (or would prefer some other coloring to notify you), these are the two entries you want to change:
```
STICKY_OTHER_WRITABLE 30;42 # dir that is sticky and other-writable (+t,o+w)
OTHER_WRITABLE 34;42 # dir that is other-writable (o+w) and not sticky
```

If you're not using default color scheme just search the dircolors for 42 to find the entries to change.

---

### Post by PopsTheSailor on 2016-06-26
Well, I fixed it well enough. I found a system theme that changed the colors to something I can use. 

Odd, I don't have a .dircolors folder. When I run the command 
dircolors -p > ~/.dircolors

it comes back blank. I'm on Ubuntu 15.10 Wiley with the Mate UI. When I use the command lsb_release -a, I get the following

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

Anyway, I'm going to make this as solved because I went into Mate's Menu > Appearance > Theme and selected TraditionalOK and it removed the shading.

Just realized I can't mark it as solved because I wasn't the OP.

---

