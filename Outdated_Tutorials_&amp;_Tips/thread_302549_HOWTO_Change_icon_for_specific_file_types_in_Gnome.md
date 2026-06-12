---
title: "HOWTO: Change icon for specific file types in Gnome"
date: 2006-11-18
forum: Outdated Tutorials &amp; Tips
---

### Post by lllSpylll on 2006-11-18
This works in Gnome 2.16.1, which is the default version used in Ubuntu Edgy.

I spent several hours looking for a way to so this, but everything I found on google was for old versions of gnome and didn't seem to work anymore.

It turns out that it's very simple to do this so here's the guide step-by-step:


How to change the icon for a specific file type in Gnome
--------------------------------------------------------

1) Go to the folder where your icon theme is installed. Mine is in ~/.icons/Vista-Inspirate_1.0

2) Look for a subfolder called "mimetypes". In the case of Vista Inpirate (the icon theme I use), there is no such folder so I had to create one. I created mine in "48x48/mimetypes" so the full path of the folder is ~/.icons/Vista-Inspirate_1.0/48x48/mimetypes

3) Inside this folder, copy the icon/image you want to use for a specific file type. In my case, I wanted to create an icon for Mathematica notebooks which have extension "*.nb" so I renamed my png picture to the following: gnome-mime-application-mathematica.png. The name depends on the mime type you are trying to change so look for the mime type of your file and name it accordingly.

4) Log out and log back in so that your icons are refreshed. Now all the files with the specific extension you changed (*.nb in my case) have the correct icon.


That's it!

Enjoy your new icons...

---

### Post by pdietric on 2006-11-19
Where did you get that Mathematica icon from or did you create one of your own?

Thanks, Peter

---

### Post by lllSpylll on 2006-11-21
I made my own icon using Export in Mathematica. :)

---

### Post by Rui Pais on 2006-11-22
](*,) ](*,) ](*,) 
Uauu! I had managed to get Mathematica icons once changing a lot of  text config files referring to mime types and app to deals with nb extensions... a perfect nightmare that i could never repeat successfully on recent gnome versions.

And it was so easy after all... Many, many thanks lllSpylll.

May i give one or two suggestions? A nice thing is to add good scaled icons to all sizes mimetypes folder, so when you change the size of view (e.g. pressing ctrl +) it won't look bad or unfocused. I start to add a png with 128x128 to 128x128/mimetype/ and then scale it with gimp to 96x96 and save it on 96x96/mimetypes and so on.

A nice way to get a good nb-file icon is simply edit the file mimetype/gnome-fs-regular.png and add over it a mathematica icon/image and save it, of course, as gnome-mime-application-mathematica.png. That will make it distinct of an icon from a launcher and will be better integrated with the rest of the icons theme.

For those who don't have the artistic vein for Mathematica or Gimp, you can check [wolfram's graphics gallery]("http://gallery.wolfram.com") and search for nice images to use as icons.


Again thanks,

---

### Post by lllSpylll on 2006-11-22
Very nice suggestions.

Basically, as Rui Pais suggested, you can add icons for all sizes, using the same strategy.

Very nice indeed.

Thanks Rui :)

---

### Post by Carlos Santiago on 2006-11-23
There is one thing that I am not understanding.
From what is posted, the gnome will recognize the files with the name gnome-mime-application-mathematica.png as the icon for the *.nb files.
Where is this relation between the file extentions and the icon file names? For example, If I want to use some icon for the files with extention '*.foo', what name should I give to the icon picture file?
Other related question, where do I define the application that opens (by default) the files with a specific extention?
Thank you

---

### Post by jamesrose on 2006-11-23
Anybody know any good links for icons?

Apart from gnome-look or kde-look.


Thanks.

---

### Post by stalefries on 2006-11-23
I would also like to know how to associate mime-types. [Fontforge]("http://fontforge.sf.net") fonts immediately some to mind.

---

### Post by KillerKiwi on 2006-11-23
It's a bit tricker than replace a file ;)

Heres the spec

[http://standards.freedesktop.org/shared-mime-info-spec/shared-mime-info-spec-latest.html](http://standards.freedesktop.org/shared-mime-info-spec/shared-mime-info-spec-latest.html)

and an example (not completly correct but you get the idea)

```

<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
	<mime-type type="application/msword">
		<comment>MS Word Files</comment>
		<glob pattern="*.doc"/>
	</mime-type>
</mime-info>

```

Save in ```
~/.local/share/mime/packages/ms-word-files.xml
```

Then run ```
update-mime-database ~/.local/share/mime/
```

Note using file magic is usually a better idea then file extensions see the spec for more detail

---

### Post by lllSpylll on 2006-11-27
To Carlos Santiago,


I think your first question was answered by KillerKiwi.
For the second question, the answer is simple:

Right click on the file and choose "Open with Other Application..."
Then select the application you want to open that kind of file.

You can select the default application by right clicking the file and choosing Properties -> Open With


I hope this helps.

---

### Post by artships on 2006-12-03
You make it sound so easy, and it was under breezy, but it hasn't under edgy.

I'm trying to associate an icon, [gnome-mime-video-ty.png]("http://artships.com/gnome-mime-video-ty.png"), with tystreams.  I've edited /usr/share/mime/packages/freedesktop.org.xml to include:

  <mime-type type="video/ty">
    <comment>Tivo transport stream</comment>
    <acronym>TY</acronym>
    <expanded-acronym>Tystream</expanded-acronym>
    <glob pattern="*.ty"/>
  </mime-type>

Executed: sudo update-mime-database /usr/share/mime

Sure enough, nautilus describes Doctor Who-Rose.ty as:

Type: Tivo transport stream
MIME type: video/ty

I put my icon in ~/.icons/Nuovo/24x24/mimetypes as gnome-mime-video-ty.png, and in gnome-theme-manager->Theme Details->Icons I selected Dropline Nuovo, noticing when I did that the folder icons in nautilus changed to the distinctive yellow icons. (Note: Dropline Nuovo "Inherits=gnome".)

The icon associated with *.ty files is, however, the gnome one that looks like /usr/share/icons/gnome/32x32/mimetypes/video-x-generic.png, to which gnome-mime-video.png is symlinked. It is the same icon associated with Doctor Who-Rose.ty.vob, described in nautilus as:

Type: MPEG video
MIME type: video/mpeg

What do I have to name my icon to get nautilus to use it for tystreams?

---

### Post by quanta on 2008-05-23
> **lllSpylll said:**
> 
...

1) Go to the folder where your icon theme is installed. Mine is in ~/.icons/Vista-Inspirate_1.0


hi lllSpylll,

I am using Fedora 9
There is nothing in ~/.icons folder:
```

$ ls -la ~/.icons
total 12
drwxrwxr-x   2 quanta quanta 4096 2007-12-22 04:35 .
drwx------ 107 quanta quanta 4096 2008-05-23 23:09 ..

```

I have followed your way except for manipulate with /usr/share/icons folder, but not succeed.

I found the [[COLOR="Blue"]topic[/COLOR]]("http://ubuntuforums.org/showthread.php?p=551423").
Nothing in ~/.local/share/mime/packages folder except for Override.xml.

I have inserted some code like below:
```
        <mime-type type="application/x-chm2">
		<comment>chm document</comment>
		<glob pattern="*.chm"/>
	</mime-type>

```
In /usr/share/mime/packages/freedesktop.org.xml, I changed:
```
<mime-type type="application/x-chm">
    <comment>CHM document</comment>
    <acronym>CHM</acronym>
    <expanded-acronym>Compiled Help Modules</expanded-acronym>
    <glob pattern="*.chm"/>
  </mime-type>

```
to:
```
<mime-type type="application/x-chm2">
    <comment>CHM document</comment>
    <acronym>CHM</acronym>
    <expanded-acronym>Compiled Help Modules</expanded-acronym>
    <glob pattern="*.chm"/>
  </mime-type>

```
after that I copied kchmviewer icon to: /usr/share/icons/Fedora/48x48/mimetypes and renamed it to gnome-mime-application-x-chm2.png, logout and login back but nothing happen. Everything icons of *.chm file not change.

Is there any other way to change file type icon?

---

### Post by nooblot on 2008-07-05
so is there a better & easier way to achieve this in the "latest and greatest" Gnome 2.22.2 ???

---

### Post by dangermouse28 on 2008-09-11
I figured it out!!!

Check out the How-To here:

[http://ubuntuforums.org/showthread.php?t=916847](http://ubuntuforums.org/showthread.php?t=916847)

---

### Post by wolterh on 2008-12-28
There is a gui for making this mimes called assogiate. You can download it from the Add/Remove... application tool.

---

### Post by nathanpc on 2009-05-25
Thanks very much now i can use my custom icons for Ruby, Ruby on Rails and Java!!!!!


Thanks For All,
 Nathan Paulino Campos

---

### Post by sdaau on 2011-01-29
Hi all,

Thanks for all the suggestions - especially for:

> **woli said:**
> There is a gui for making this mimes called assogiate. 

I installed it under Lucid, and wanted to add icons for *.v (which doesn't have associated) and *.vhdl (which has standard association as a text/source file). First, I created a mimetype for *.v as 'text/source', and my icons as '/usr/share/icons/icon-verilog.png' and '/usr/share/icons/icon-vhdl.png' -- and tried to assign these as default icons via assogiate. Assogiate would show the icons in its window, but nautilus would **not** apply them at all (even after logout / sudo service gdm restart)!

Then I copied these icons as ~/.icons/gnome-mime-application-x-verilog.png and ~/.icons/gnome-mime-application-x-vhdl.png and tried to assign these as default icons - still no dice!

Finally, I changed the parent type of verilog from 'text/source' to 'Multipurpose file' - and finally (after logout) the icons DID show in nautilus - even *without* an explicit "default icon" link via assogiate! Did the same for the vhdl - since vhdl is already 'text/source' in standard, I simply added another mime-type, same name (x-vhdl), just under a 'Multipurpose file' parent type (so it becomes 'application/x-vhdl') - and the *.vhdl files showed the new icon in Nautilus as well (again, after logout or gdm restart).

Thanks again to everyone for this thread, 

Cheers!

References:

[LIST]
[*] [[gnome] Change icon for all files of a certain type? - Ubuntu Forums]("http://art.ubuntuforums.org/showthread.php?p=6889792")
[*] [[SOLVED] Changing default Icon 4 one file type? - Ubuntu Forums]("http://georgia.ubuntuforums.org/showthread.php?p=8598178")
[*] [[SOLVED] MIME type defines and icons... - Ubuntu Forums]("http://art.ubuntuforums.org/showthread.php?p=8605385")
[*] [[SOLVED] How do I assign a new icon to a file type - Ubuntu Forums]("http://art.ubuntuforums.org/showthread.php?p=8295920")
[/LIST]

EDIT 28 Feb: After a few reboots, I realized that VHDL icon doesn't show anymore: on right-click/Properties, Nautilus would show 'VHDL document (text/x-vhdl)' as 'Type'. Then I first made an appropriate copy of the icon:
```

cp ~/.icons/gnome-mime-application-x-vhdl.png ~/.icons/gnome-mime-text-x-vhdl.png

``` 
... but that, on its own, didn't seem to help.. 

Then, I went to 'assogiate' (Applications/System Tools/File Types Editor), and there, opened up the 'Text and Source Code' entry for 'text/x-vhdl'; and in there, under 'Related Types' tab, I simply added the previously made 'application/x-vhdl' under 'Aliases'; as soon as that passed, icons for .vhdl files reappeared after simply refreshing the directory view in Nautilus :)

---

### Post by Meneer Jansen on 2011-06-15
Changing an associated icon in Gnome is a **nightmare**. Pfffffff. Here's what worked for me. Notice that:
[LIST]
[*]I use Gnome 2.30 (Ubuntu Lucid).
[*]The icon theme that I use did not have "mime types" associated w/ it.
[/LIST]
Most methods on the internet, and in this forum (i.e. Assogiate), assume that the icon theme that you use is "complete" in the sense that it has an direcory called "mimetype" in */usr/share/icons/your_icon_theme*. Mine did not. So nothing seemed to work for me. 

What worked for me in the end was:
[LIST]
[*]Check mimetype w/ right mouse button in Nautilus (click: "properties -> type"). Example: *application/pdf*.
[*]Create a folder called "mimetypes" in *'/usr/share/icons/your_icon_theme/scalable/'* if it does not exists yet.
[*]Place icon in that dir. Make sure it has the right filename! Example for PDF: gnome-mime-application-pdf.svg
[*]And the hat trick:
```

$ sudo gtk-update-icon-cache /usr/share/icons/my_icon_theme/
[sudo] password for user: 
gtk-update-icon-cache: Cache file created successfully.

```
[/list]
No need to re-log-in or restart Nautilus. Just click on 'Refresh' button and if you're lucky the right icon will pop up.

---

### Post by Meneer Jansen on 2011-06-15
Made a little shell script that works for me. See my post above. Do you like it?

```

#!/bin/bash
# Shell script to change the associated icon of a mimetype (= an application) in Gnome 2.30.
# This script is writtn for Ubuntu because it uses 'sudo'.

# 1. Give Theme name:
echo "Type in the (icon) Theme name that u use in Gnome:"
echo "   Hint: use 'gnome-appearance-properties' to determine your icon thme."
read themename
echo " "

# Path to icons:
location="/usr/share/icons/$themename/scalable"

# 2. Give location/name of icon to copy:
echo "Give location and name of icon to copy."
echo "   Hint: use the command 'locate' to locate a nice icon for ya and"
echo "   copy/paste it into this console"
read iconname
echo " "

# 3. Give mimetype-icon name"
echo "Type in the name that the mimetype icon should get."
echo "   Hint: use Nautilus' file properties dialog screen to determine"
echo "   the proper filename."
echo "   Example: the (mime)type of a PDF file is: application/pdf."
echo "   So the Gnome icon name of that mimetype is: gnome-mime-application-pdf.svg."
read mimetype_iconname
echo " "

# 4. If not exist, then create folder "mimetypes""
folder="$location/mimetypes"
if [ -d $folder ]; then 
        echo "Not gonna create directory 'mimetypes' because it already exists. See"
	echo "output of ls:"
	ls $folder
	else 
	echo "No folder called 'mimetypes' found. Gonna create it:"
	sudo mkdir $location/mimetypes
	sleep 3
fi

# 5. List data:
clear
echo --------------------------------------------------- 
echo "Theme name:"
echo "   $themename"
echo "Path to theme:"
echo "   $location"
echo "Name of icon to copy:"
echo "   $iconname"
echo "The icon name you chose for the icon:"
echo "   $mimetype_iconname"
echo ----------------------------------------------------
echo " "
echo "Press CTRL-C to abort! Else: press the Any key."
read blabla

# 6. Copy icon to theme dir.
sudo cp $iconname $location/mimetypes/$mimetype_iconname

# 7. Now update Gnome's icon database:
sudo gtk-update-icon-cache /usr/share/icons/$themename

```

---

