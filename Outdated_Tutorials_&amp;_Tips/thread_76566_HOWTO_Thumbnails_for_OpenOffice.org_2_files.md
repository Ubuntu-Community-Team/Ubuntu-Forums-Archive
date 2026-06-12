---
title: "HOWTO: Thumbnails for OpenOffice.org 2 files"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by minio on 2005-10-15
This also works for OOo1 files created or altered with OOo2. Beacuse OOo2 saves thumbnail of document into created file all what is needed is to extract the image a save it with right name :)
So first create file named ooo2-thumbnailer in /usr/bin 
```
sudo gedit /usr/bin/ooo2-thumbnailer
```
and put in it following code 
```
#!/usr/bin/python
# released into the public domain http://creativecommons.org/licenses/publicdomain
import zipfile
import sys
import gnomevfs

inURL=gnomevfs.get_local_path_from_uri(sys.argv[1])
outURL=sys.argv[2]

zip=zipfile.ZipFile(inURL,mode="r")
picture=zip.read("Thumbnails/thumbnail.png")
thumbnail=open(outURL,"w")
thumbnail.write(picture)
thumbnail.write("/n")
zip.close()
thumbnail.close()

```
and save the file.
Now we need to make it executable
```
sudo chmod +x /usr/bin/ooo2-thumbnailer
```

The next step is to tell Gnome how to use this thumbnailer. So create file ooo2.schemas in /usr/share/gconf/schemas
```
sudo gedit /usr/share/gconf/schemas/ooo2.schemas
```
and paste in it following code
```
<gconfschemafile>
    <schemalist>

        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.text/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.text/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.text/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.text/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
     

        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.spreadsheet/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.spreadsheet/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.spreadsheet/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.spreadsheet/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
	<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.graphics/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.graphics/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.graphics/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.graphics/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
	<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.formula/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.formula/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.formula/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.formula/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.presentation/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.presentation/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.presentation/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.presentation/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.writer/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.writer/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.writer/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.writer/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
     

        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.calc/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.calc/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.calc/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.calc/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.draw/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.draw/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.draw/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.draw/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
	
	<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.math/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.math/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.math/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.math/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
	<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.impress/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.impress/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.impress/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.impress/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>

    </schemalist>
</gconfschemafile>

```
and save it.
Now there are two ways to start gnome to use this thumbnailer
1) reboot
2) tell gnome to read this file:
```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/ooo2.schemas
```
and restart nautilus
```
killall -9 nautilus
```

---

### Post by sethmahoney on 2005-10-15
Awesome howto, works perfectly!  Anyone know if there's a quick/easy way to add a small icon or watermark over the thumbnail?

---

### Post by OttoDestruct on 2005-10-15
Could someone provide a screenshot to show the finished product?

---

### Post by NeTo on 2005-10-16
[QUOTE=OttoDestruct]Could someone provide a screenshot to show the finished product?[/QUOTE]

Here's a shot of my homework, two Writer files: one with images, and the other one with formulas.

If you decide to try out the thumbnails and don't like the results afterwards, you can roll back by deleting the two files:```

sudo rm /usr/bin/ooo2-thumbnailer
sudo rm /usr/share/gconf/schemas/ooo2.schemas

```

And then restart Gnome (or nautilus, following minio's instructions).

Btw, thank you minio for the how-to :KS. The only downside I notice is that Ooo2 generates thumbnails with transparent backgrounds, so they don't look that good if you have set a background in nautilus.

---

### Post by jd_ on 2005-10-30
Excellent :)
Thanks.

---

### Post by Muffe on 2005-10-31
I have followed the instructions perfectly, and I still can't get this to work. Every file is in the right place with the right owner and permissions. Does anyone have a hint?

---

### Post by minio on 2005-10-31
One of following steps should help
1) open gconf-editor and go to desktop->gnome->thumbnailers check if there ar e folders like "application@vnd.oasis.opendocument.graphics","application@vnd.sun.xml.impress" and similar. then check if key "command" in these folders contains correct path to thumbnailer (it should be /usr/bin/ooo2-thumbnailer %u %o) and if is enable checked.

2)try to delete entire ~/.thumbnails/fail directory and restart nautilus

3)check if those files you want to be thumbnailed were created with OOo2.

4)open one file with file-roller and look if there is Thumbnails directory some older betas of OOo2 used Thumbnail directory instead

---

### Post by Muffe on 2005-10-31
found the mistake. I executed this command:

```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/ooo2.schemas
```

as root, not my usual user.

---

### Post by Haegin on 2005-11-02
SCHWEET! Works great - any chance this can be incorporated into dapper with an option to turn it off sumwhere? Its definatly an improvement and I can't see how a load of open office file logos are any better in any way except maybe that they tell you what file format it is in. Maybe if you could get a little overlay on each if it is possible (I doubt its easy if I understand how you are doing it correctly)

Brilliant anyway...

---

### Post by magnusbb on 2005-11-03
Nice one!

I am very picky, but try this:

Using the GNOME Templates system in Nautilus, put an empty OpenOffice document (a template) in the /home/user/Templates folder, right-click on your desktop and look inside your "Create Document" menu. The icon for the document will now reflect the empty document, resulting in the icon of a "blank sheet".

:) 

I suppose it can be fixed in some way.

---

### Post by minio on 2005-11-03
Well this should solve the problem with templates, delete the old one /usr/bin/ooo2-thumbnailer
```
sudo rm /usr/bin/ooo2-thumbnailer
```

then crate new one ```
sudo gedit /usr/bin/ooo2-thumbnailer
```
and put in this code instead of the one in the first post```
#!/usr/bin/python
# released into the public domain http://creativecommons.org/licenses/publicdomain

import zipfile
import sys
import os
import gnomevfs

inURL=gnomevfs.get_local_path_from_uri(sys.argv[1])
outURL=sys.argv[2]
nothumbURL=os.getenv("HOME")+"/Templates"
nothumbList=nothumbURL.split(os.sep)
inList=inURL.split(os.sep)

if inList[1]==nothumbList[1] and inList[2]==nothumbList[2] and inList[3]!=nothumbList[3]:
	zip=zipfile.ZipFile(inURL,mode="r")
	picture=zip.read("Thumbnails/thumbnail.png")
	zip.close()
	thumbnail=open(outURL,"w")
	thumbnail.write(picture)
	thumbnail.write("/n")
	thumbnail.close()

```
and save it
Then delete thumbnails of those files in Teplates directory (thumbnails are in ~/thumbnails you will have to find them by eye or delete entire ~/thumbnails directory)
restart nautilus
```
killall -9 nautilus
```

It doesn't work 100% because if you put in Templates directory some file which was already thumbnailed it will keep its thumbnail...

I am also trying to figure out how to add overlay on thumbnails, and turn them  to white background insteaad of transparent one. Once I figure it out I will update the first post :)

---

### Post by KillerKiwi on 2005-11-04
This version put in a white background as well as overlay an Ooo2 icon :)

Screen Shot 
[http://img492.imageshack.us/img492/2827/screenshot5dl.png]("http://img492.imageshack.us/img492/2827/screenshot5dl.png")

```

#!/usr/bin/python

import zipfile
import sys
import os
import gnomevfs
from PIL import Image, ImageEnhance

# Alter these varibles to change thumbnail look
BaseIconPath = "/usr/share/icons/hicolor/48x48/apps/" # Change this path to alter icons

# Opacity of the icon
IconOpacity = 0.8
# Color of the background
BackgroundColor = "white"

# Two types of icons Ubuntu and Ooo2
#iconPreFix = "openofficeorg-20-" # Ooo2 Stock
iconPreFix = "ooo-" # Ubuntu

"""
Open Document Types
================
	Text 				.odt 	
	Spreadsheet 		.ods 
	Presentation 		.odp 
	Drawing 			.odg 
	Chart 			.odc
	Formula 			.odf 
	Database 			.odb 
	Image 			.odi 
	Master Document	.odm
"""

# Nicked from http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/362879
def reduce_opacity(im, opacity):
    """Returns an image with reduced opacity."""
    assert opacity >= 0 and opacity <= 1
    if im.mode != 'RGBA':
        im = im.convert('RGBA')
    else:
        im = im.copy()
    alpha = im.split()[3]
    alpha = ImageEnhance.Brightness(alpha).enhance(opacity)
    im.putalpha(alpha)
    return im

inURL=gnomevfs.get_local_path_from_uri(sys.argv[1])
outURL=sys.argv[2]
nothumbURL=os.getenv("HOME")+"/Templates"
nothumbList=nothumbURL.split(os.sep)
inList=inURL.split(os.sep)

if inList[1]==nothumbList[1] and inList[2]==nothumbList[2] and inList[3]!=nothumbList[3]:
	zip=zipfile.ZipFile(inURL,mode="r")
	picture=zip.read("Thumbnails/thumbnail.png")
	zip.close()
	thumbnail=open(outURL,"w")
	thumbnail.write(picture)
	thumbnail.write("/n")
	thumbnail.close()

	# Get File Extension    
	fileExtension = inURL[ len(inURL)-3 :].lower()

	# Select Document Type
	iconFile = "writer"
	if fileExtension == "ods":
		iconFile = "calc"
	elif fileExtension == "odp":
		iconFile = "impress"
	elif fileExtension == "odg":
		iconFile = "draw"
	elif fileExtension == "odp":
		iconFile = "calc"
	elif fileExtension == "odf":
		iconFile = "math"
	elif fileExtension == "odi":
		iconFile = "draw"
	elif fileExtension == "odi":
		iconFile = "template"

	thumbnail = Image.open(outURL).convert("RGBA")

	# Load icon
	icon = Image.open(BaseIconPath + iconPreFix+ iconFile +".png").convert("RGBA")
	icon = reduce_opacity(icon, IconOpacity)
	# Create new img with white bg
	final = Image.new("RGB", (thumbnail.size[0],thumbnail.size[1]), BackgroundColor)
	# Add thumbnail
	final.paste(thumbnail, None, thumbnail)
	# Add icon
	x = final.size[0] - icon.size[0]
	y = final.size[1]-icon.size[1]
	w = x + icon.size[0]
	h = y + icon.size[1]
	final.paste(icon, (x,y,w,h), icon)
	# Save thumbnail
	final.save(outURL, "PNG")

```

Do **sudo gedit /usr/bin/ooo2-thumbnailer** and paste in the above code

**Edited**
Added abiltiy to add fade to icon

---

### Post by Muffe on 2005-11-05
Very nice... I have not tested it, but the screenshot does look very good.

---

### Post by varunus on 2005-11-05
I see that the new script uses the hicolor folder...ew, hicolor icons...

Couldn't you modify it to pull the user's current theme directory?  And then, if that doesn't have OOO icons, fall back to hicolor?  I know this is easy in C using gtk icon theme functions, but I don't know python...

---

### Post by minio on 2005-11-05
[QUOTE=KillerKiwi]This version put in a white background as well as overlay an Ooo2 icon :)
[/QUOTE]

Works really good :) Thanks :) But could you make the icon somewhat transparent? (I think aplha around 0.2 woud be the best) I would do it myself if i  know how to use PIL module but i have almost no experience with it (i think that this module hates me :) ). Good work anyway :)

---

### Post by minio on 2005-11-05
[QUOTE=varunus]I see that the new script uses the hicolor folder...ew, hicolor icons...

Couldn't you modify it to pull the user's current theme directory?  And then, if that doesn't have OOO icons, fall back to hicolor?  I know this is easy in C using gtk icon theme functions, but I don't know python...[/QUOTE]

This is something what I can do but i don't understand why. If you want change  used icons then change the path to them. Thumbnails, once generated, are virtually forever so if i would make them follow current theme then, if you change icon theme, you will have thumbnails with old icons for old files and thumbnails with new icons for new ones and it would be a mess (believe me i've tried it).

---

### Post by KillerKiwi on 2005-11-05
Edited my post to include ability to add fade to icons

---

### Post by Haegin on 2005-11-06
Nice - I like it alot. The icon in the corner helps alot - this should definatly be in by default - i cant think of any way the original icon is better.

---

### Post by minio on 2005-11-06
Ok i rewrote the code once again. It should work (at least it seems to work for me...:))
I've splitted the code into few functions and added KillerKiwi code. I've also changed icon name resolution, detection of ~/Templates directory and made it to do nothing if there is no thumbnail in file. Any comments (also about coding style) and requests are welcome :) especially from KillerKiwi, since half of the work is his.
```
#!/usr/bin/env python

import gnomevfs
import os
import sys
import zipfile
from PIL import Image, ImageEnhance

# Alter these varibles to change thumbnail look
ICON_PATH_BASE = "/usr/share/icons/hicolor/48x48/apps/" # Change this path to alter icons
ICON_PREFIX = "ooo-" #Ubuntu icons
#ICON_PREFIX="openofficeorg-20-" #OOo2 stock icons
ICON_OPACITY = 0.6 #Opacity of the icon (between 0.0 and 1.0)
THUMBNAIL_BACKGROUND_COLOR = "white" # Color of the background

in_file_path = gnomevfs.get_local_path_from_uri(sys.argv[1])
out_file_path = sys.argv[2]
path_without_thumbs = os.getenv("HOME")+"/Templates" 
	
def get_icon(thumbnail_size):
	icon_names={"formula":"math","graphics":"draw","presentation":"impress","spreadsheet":"calc","text":"writer"}
	#Get file mimetype
	file_mime_type=gnomevfs.get_mime_type(in_file_path)
	#Get last part of mimetype name.
	application_name=file_mime_type.split(".")[-1]	
	try:
		#For OOo2 files we have to find icon name in icon_names
		icon_name=icon_names[application_name]
	except:
		#But for OOo1 files it is equal to icon name (without prefix).
		icon_name=application_name
	#Load icon
	icon = Image.open(ICON_PATH_BASE+ICON_PREFIX+icon_name +".png").convert("RGBA")
	#Set it's opacity
	icon = set_icon_opacity(icon,ICON_OPACITY)
	#And set it's position in thumbnail
	icon_posx=thumbnail_size[0]-icon.size[0]
	icon_posy=thumbnail_size[1]-icon.size[1]
	icon_width=thumbnail_size[0]
	icon_height=thumbnail_size[1]
	return {"image":icon,"position":(icon_posx,icon_posy,icon_width,icon_height)}	

def get_basic_thumbnail():
	#Find out if the file is not in Templates directory
	if in_file_path.find(path_without_thumbs)!=0:
		try:
			#Extract thumbnail from OOo file and save it
			zip=zipfile.ZipFile(in_file_path,mode="r")
			picture=zip.read("Thumbnails/thumbnail.png")
			zip.close()
			thumbnail=open(out_file_path,"w")
			thumbnail.write(picture)
			thumbnail.write("/n")
			thumbnail.close()
			#Open saved thumbnail
			image=Image.open(out_file_path).convert("RGBA")
			return {"suceeded":True,"image":image,"size":(image.size[0],image.size[1])}
		
		except:
			return {"suceeded":False}
	else:
		return {"suceeded":False}

# Nicked from http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/362879
def set_icon_opacity(icon,opacity):
	#Returns an image with reduced opacity.
	assert opacity >= 0 and opacity <= 1
	if icon.mode != 'RGBA':
		icon = icon.convert('RGBA')
	else:
		icon = icon.copy()
	alpha = icon.split()[3]
	alpha = ImageEnhance.Brightness(alpha).enhance(opacity)
	icon.putalpha(alpha)
	return icon

thumbnail=get_basic_thumbnail()
if thumbnail["suceeded"]:
	background=Image.new("RGB", thumbnail["size"], THUMBNAIL_BACKGROUND_COLOR)
	icon=get_icon(thumbnail["size"])
	thumbnail=thumbnail["image"]
	# Add thumbnail
	background.paste(thumbnail, None, thumbnail)
	# Add icon
	background.paste(icon["image"],icon["position"],icon["image"])
	# Save thumbnail
	background.save(out_file_path,"PNG")
```

---

### Post by XDevHald on 2005-11-06
Well done, it does work very clean in Dapper Drake :)

Excellent!

---

### Post by henriquemaia on 2005-11-06
Worked great!

Thanks!

---

### Post by KillerKiwi on 2005-11-07
Nice one minio :)

Heres another one, grabs the icon from the current gnome theme instead...
Not really sure what the deal is with the mime types I've got
[LIST]
[*]gnome-mime-application-vnd.oasis.opendocument.text
[*]ooo-writer
[*]gnome-mime-application-vnd.stardivision.writer
[*]openofficeorg-20-writer
[*]gnome-mime-application-vnd.sun.xml.writer
[*]ximian-openoffice-writer
[*]ooo_writer
[/LIST]
Any idea which one is the 'correct' one? My monies on the oasis one.


```

#!/usr/bin/env python

import gnomevfs
import gtk
import os
import sys
import zipfile
from PIL import Image, ImageEnhance

# Alter these varibles to change thumbnail look
ICON_USE_CURRENT_THEME = True
# If not using current theme then use this path
ICON_PATH_BASE = "/usr/share/icons/hicolor/48x48/apps/" # Change this path to alter icons
ICON_PREFIX = "ooo-" #Ubuntu icons
#ICON_PREFIX="openofficeorg-20-" #OOo2 stock icons

ICON_OPACITY = 0.6 #Opacity of the icon (between 0.0 and 1.0)
THUMBNAIL_BACKGROUND_COLOR = "white" # Color of the background
# Prefix for using mime types
ICON_MIME_PREFIX = "gnome-mime-application-"

in_file_path = gnomevfs.get_local_path_from_uri(sys.argv[1])
out_file_path = sys.argv[2]
path_without_thumbs = os.getenv("HOME")+"/Templates" 
	
def get_icon(thumbnail_size):
	icon_names={"formula":"math","graphics":"draw","presentation":"impress","spreadsheet":"calc","text":"writer"}
	#Get file mimetype
	file_mime_type=gnomevfs.get_mime_type(in_file_path)
	#print file_mime_type
	#Get last part of mimetype name.
	application_name=file_mime_type.split(".")[-1]	
	try:
		#For OOo2 files we have to find icon name in icon_names
		icon_name=icon_names[application_name]
	except:
		#But for OOo1 files it is equal to icon name (without prefix).
		icon_name=application_name
	#Load icon
	if ICON_USE_CURRENT_THEME:
		icon_name = ICON_MIME_PREFIX+ file_mime_type.split("/")[1]
		icon = get_current_theme_icon( icon_name )
	else:
		icon = Image.open(ICON_PATH_BASE+ICON_PREFIX+icon_name +".png").convert("RGBA")
	#Set it's opacity
	icon = set_icon_opacity(icon,ICON_OPACITY)
	#And set it's position in thumbnail
	icon_posx=thumbnail_size[0]-icon.size[0]
	icon_posy=thumbnail_size[1]-icon.size[1]
	icon_width=thumbnail_size[0]
	icon_height=thumbnail_size[1]
	return {"image":icon,"position":(icon_posx,icon_posy,icon_width,icon_height)}	

def get_basic_thumbnail():
	#Find out if the file is not in Templates directory
	if in_file_path.find(path_without_thumbs)!=0:
		try:
			#Extract thumbnail from OOo file and save it
			zip=zipfile.ZipFile(in_file_path,mode="r")
			picture=zip.read("Thumbnails/thumbnail.png")
			zip.close()
			thumbnail=open(out_file_path,"w")
			thumbnail.write(picture)
			thumbnail.write("/n")
			thumbnail.close()
			#Open saved thumbnail
			image=Image.open(out_file_path).convert("RGBA")
			return {"suceeded":True,"image":image,"size":(image.size[0],image.size[1])}
		
		except:
			return {"suceeded":False}
	else:
		return {"suceeded":False}

# Nicked from http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/362879
def set_icon_opacity(icon,opacity):
	#Returns an image with reduced opacity.
	assert opacity >= 0 and opacity <= 1
	if icon.mode != 'RGBA':
		icon = icon.convert('RGBA')
	else:
		icon = icon.copy()
	alpha = icon.split()[3]
	alpha = ImageEnhance.Brightness(alpha).enhance(opacity)
	icon.putalpha(alpha)
	return icon

# Convert GTK pixbuf to PIL Image
def convert_pixbuf_to_image(pb):
	assert(pb.get_colorspace() == gtk.gdk.COLORSPACE_RGB)
	dimensions = pb.get_width(), pb.get_height()
	stride = pb.get_rowstride()
	pixels = pb.get_pixels()
	mode = pb.get_has_alpha() and "RGBA" or "RGB"
	return Image.frombuffer(mode, dimensions, pixels,"raw", mode, stride, 1)

# Get the icon from the current GTK theme
def get_current_theme_icon( icon ):
	theme = gtk.icon_theme_get_default()
	#print theme.list_icons()
	pixbuf_icon = theme.load_icon(icon, 46, 0)
	return convert_pixbuf_to_image(pixbuf_icon)

thumbnail=get_basic_thumbnail()
if thumbnail["suceeded"]:
	background=Image.new("RGB", thumbnail["size"], THUMBNAIL_BACKGROUND_COLOR)
	icon=get_icon(thumbnail["size"])
	thumbnail=thumbnail["image"]
	# Add thumbnail
	background.paste(thumbnail, None, thumbnail)
	# Add icon
	background.paste(icon["image"],icon["position"],icon["image"])
	# Save thumbnail
	background.save(out_file_path,"PNG")


```

---

### Post by BLTicklemonster on 2005-11-07
I don't get it. I already see thumbnails.

---

### Post by minio on 2005-11-07
KillerKiwi:I have no idea either. I would say oasis and stardivision.writer but it is a blind shot. I have one more idea how to change the code so I'll try to do it till end of week.


BLTicklemonster: Huh? Do you have clean breezy install or do you have custom OOo2?

---

### Post by timczer on 2005-11-07
Is there a way to get thumbnails to show up for documents saved in openoffice with excel or word extensions?

---

### Post by KillerKiwi on 2005-11-07
The all knowing wiki knows :)

[http://en.wikipedia.org/wiki/OpenDocument#File_types](http://en.wikipedia.org/wiki/OpenDocument#File_types)

**application/vnd.oasis.opendocument.text**
which Im pretty sure maps to the icon
**gnome-mime-application-vnd.oasis.opendocument.text**

Which is what the code I posted is using, much 'better' as opendocument is not just openoffice.

> Is there a way to get thumbnails to show up for documents saved in openoffice with excel or word extensions?
Not using this method, as far as i know ms formats do not include a thumbnail.  You could create one on the fly some how but that would be very slow

Kiwi

---

### Post by Zxaos on 2005-11-08
[QUOTE=minio]Ok i rewrote the code once again. It should work (at least it seems to work for me...:))[/QUOTE]

I found that this code doesn't work in Breezy, but the previous code (post 12) did.

---

### Post by minio on 2005-11-09
[QUOTE=Zxaos]I found that this code doesn't work in Breezy, but the previous code (post 12) did.[/QUOTE]
So this is strange, because I have breezy and it works for me. What do you get if you try run it from terminal? To run it from terminal put there something like this: ```
ooo2-thumbnailer file:///home/yourhome/path_to_some_OOo2_file /home/yourhome/Desktop/img.png
```

---

### Post by magnusbb on 2005-11-09
When I run this command on my up-to-date Breezy system, using your code from post #12, I get the following output:

File "/usr/bin/ooo2-thumbnailer", line 21
    icon_names={"formula":"math","graphics":"draw","presentation":"impress","spreadsheet":"calc","text":"writer"}
             ^
IndentationError: expected an indented block

---

### Post by minio on 2005-11-10
Corrected. There should be a tab at the start of line 21. I wonder where I lost it. Thanks magnusbb for noticing.

---

### Post by KillerKiwi on 2005-11-12
[http://www.flyn.org/projects/nautilus_thumbnailers/index.html](http://www.flyn.org/projects/nautilus_thumbnailers/index.html)

This will create thumbnails for word files but you need Abiword installed

---

### Post by UbuWu on 2005-11-16
[QUOTE=Human Prototype]SCHWEET! Works great - any chance this can be incorporated into dapper with an option to turn it off sumwhere?[/QUOTE]

Probably yes: I filed this bug: [http://bugzilla.ubuntu.com/show_bug.cgi?id=19715](http://bugzilla.ubuntu.com/show_bug.cgi?id=19715) and almost immediately got a positive respons on it from Sebastien Bacher... :KS

---

### Post by adam.tropics on 2005-11-18
How would you go about extending this to include html and other online documents? Works great at the moment though, don't get me wrong, just that I had a bit of an idea for a different take on bookmarks, which would need this!

---

### Post by MichaëlVD on 2006-02-28
[QUOTE=UbuWu]Probably yes: I filed this bug: [http://bugzilla.ubuntu.com/show_bug.cgi?id=19715](http://bugzilla.ubuntu.com/show_bug.cgi?id=19715) and almost immediately got a positive respons on it from Sebastien Bacher... :KS[/QUOTE]

Is this still a planned feature?

---

### Post by Mellon on 2006-02-28
yay ;)  is working

---

### Post by mmcmonster on 2006-06-18
Can anyone give me a pointer on how to create a schema for something other than an oasis-document file?

I want to create thumbnails in nautilus for .cbr / .cbz files based on the first image in the files. (.cbr files are just in RAR format, while .cbz files are in ZIP format)  The archives will just be a collection of .jpg image files.

---

### Post by minio on 2006-06-18
It's simple first you need mime type for your files. All mime types are stored under /usr/share/mime. For cbz it is "application/x-cbz" for cbr it's "application/x-cbr" (if you don't believe me look in /usr/share/mime/application :) ) but in schema you will use it as "application@x-cbz" and "application@x-cbr"

For schema itself look into /usr/share/gconf/totem-video-thumbnail.schemas and evince-thumbnailer.schemas in the same directory. You will get an idea. 

I don't know what for the "%s" is but "%u" is URL of thumbnailed file and "%o" is URL of png image which will be used as thumbnail. So to make thumbnail you basicaly need to crate a png from %u file and copy it to %o . In your case extract the jpg image, convert it to png and save it as %o.  

Notice that "%u" URL you will get in form "file:///pathtofile" so  you need to strip first 7 letters of this URL before it's useable. 

I hope this helped you :)

---

### Post by KillerKiwi on 2006-06-18
%s is the max image size ;)

---

### Post by mmcmonster on 2006-06-20
Thanks a lot, guys.  Also, thanks go out to the folks at comp.lang.python, who helped me write the python code that follows.

Here is the code to create thumbnails for .cbz sequential image archives (usually associated with comical or comix in linux or cdisplay on MSWindows).

```

sudo gedit /usr/bin/comical-thumbnailer

``` 
```

#!/usr/bin/python

import zipfile
import sys
import gnomevfs
import Image
import StringIO

inURL=gnomevfs.get_local_path_from_uri(sys.argv[1])
outURL=sys.argv[2]

zip=zipfile.ZipFile(inURL,mode="r")
jpeglist=[x for x in zip.namelist() if '.jp' in x]
try:
  picture=zip.read(jpeglist[0])
except IndexError:
  print 'No jpeg found'

zip.close() #close the file, since we no longer have need of it
image = Image.open(StringIO.StringIO(picture)) # create image object from file-like object
image.thumbnail((128,128),Image.ANTIALIAS) #create the thumbnail
image.save (outURL, "PNG") #output the file in the proper format

``` 
```

sudo chmod a+rx /usr/bin/comical-thumbnailer

``` 
```

sudo gedit /usr/share/gconf/schemas/comical.schemas

``` 
```

<gconfschemafile>
    <schemalist>
        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@x-cbz/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@x-cbz/enable</applyto>
            <owner>comical-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@x-cbz/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@x-cbz/command</applyto>
            <owner>comical-thumb</owner>
            <type>string</type>
            <default>/usr/bin/comical-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
    </schemalist>
</gconfschemafile>

``` ```

gconftool-2 --install-schema-file /usr/share/gconf/schemas/comical.schemas

```

---

### Post by ephman on 2006-06-20
hello,

i've tried this HOWTO step by step word for word a couple times and no go.  for some reason i still get the plain icon?  any help would be so appreciated.

thanks,
ephman

---

### Post by HerrEkberg on 2006-06-21
[QUOTE=mmcmonster]Thanks a lot, guys.  Also, thanks go out to the folks at comp.lang.python, who helped me write the python code that follows.

Here is the code to create thumbnails for .cbz sequential image archives (usually associated with comical or comix in linux or cdisplay on MSWindows).
[/QUOTE]

I suspected it was to be used for comic book archives when I saw it on comp.lang.python. :)

Comix also includes a comic book thumbnailer (in later versions) called comicthumb, written by Christoph Wolk who is a regular on these forums I believe.  It is in essence very much like the one you have written, but it supports RAR and tar archives as well and has some other nice features. You can check it out if you want.

Lazy link: [http://comix.sourceforge.net/](http://comix.sourceforge.net/)

---

### Post by minio on 2006-06-21
You should make your own howto about your thumbnailer otherwise it will be lost

---

### Post by minio on 2006-06-21
[QUOTE=ephman]hello,

i've tried this HOWTO step by step word for word a couple times and no go.  for some reason i still get the plain icon?  any help would be so appreciated.

thanks,
ephman[/QUOTE]
Well first look in gconf-editor if thumbnailer is properly installed and enabled. If so try remove "~./thumbnails/fail" directory and restart nautilus. Right now i have no more ideas.

---

### Post by mmcmonster on 2006-06-22
[HerrEkberg]("http://www.ubuntuforums.org/member.php?u=62443"), thanks for the info.  No need to reinvent the wheel, right. :-)

I'll take a look at it and see about extracting it so that people that don't use comix can still use the thumbnailer.

---

### Post by edemark on 2006-06-22
Hi all I have just tried out this thumbnailing option for OO it is great and I wanted to thank to all who let me have this feature on my Drapper Drake. The only one thing that I would like to find out if there was any possibilitiy to make a transparent thumbnail. It would be so nice on my desktop

thanks again to all of you it is really nice

---

### Post by ephman on 2006-06-25
[QUOTE=minio]Well first look in gconf-editor if thumbnailer is properly installed and enabled. If so try remove "~./thumbnails/fail" directory and restart nautilus. Right now i have no more ideas.[/QUOTE]

i noticed something.  when i'm in a root nautilus shell i get the thumbnails, but not when i'm under my username.  so something is working, but i'm not sure how to get it running not in root.  any help would be awesome!

thanks,
ephman

---

### Post by minio on 2006-06-27
[QUOTE=ephman]i noticed something.  when i'm in a root nautilus shell i get the thumbnails, but not when i'm under my username.  so something is working, but i'm not sure how to get it running not in root.  any help would be awesome!

thanks,
ephman[/QUOTE]
Try running ```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/ooo2.schemas
``` as user

---

### Post by ephman on 2006-06-28
[QUOTE=minio]Try running ```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/ooo2.schemas
``` as user[/QUOTE]

Hi,

i tried and i get this.  thank you for helping.

ephman@wintermute:~$ gconftool-2 --install-schema-file /usr/share/gconf/schemas/ooo2.schemas
I/O error : Permission denied
I/O warning : failed to load external entity "/usr/share/gconf/schemas/ooo2.schemas"
Failed to open `/usr/share/gconf/schemas/ooo2.schemas': Permission denied
ephman@wintermute:~$

i'm sure it's something simple i'm not doing.

thanks,
ephman

---

### Post by joakim2 on 2006-06-28
[QUOTE=ephman]Hi,

i tried and i get this.  thank you for helping.

ephman@wintermute:~$ gconftool-2 --install-schema-file /usr/share/gconf/schemas/ooo2.schemas
I/O error : Permission denied
I/O warning : failed to load external entity "/usr/share/gconf/schemas/ooo2.schemas"
Failed to open `/usr/share/gconf/schemas/ooo2.schemas': Permission denied
ephman@wintermute:~$

i'm sure it's something simple i'm not doing.

thanks,
ephman[/QUOTE]

Before running gconftool-2 --install-schema-file run 'sudo chmod 644 /usr/share/gconf/schemas/ooo2.schemas'

---

### Post by ephman on 2006-06-28
[QUOTE=joakim2]Before running gconftool-2 --install-schema-file run 'sudo chmod 644 /usr/share/gconf/schemas/ooo2.schemas'[/QUOTE]

thanks.  got past the permissions issue.  but still no go in user, works fine in root.  i've read this howto cover to cover and tried it all.

thanks,
ephman

---

### Post by anchises on 2006-07-29
---

---

### Post by dj chainz on 2007-09-11
I just discovered this forum topic and am wondering WHY this isn't part of the default ubuntu installation already?  One of Vista's "amazing" features is document previews in the icons - I really hope this gets noticed and included with the OpenOffice package for Gutsy Gibbon!

---

### Post by dj chainz on 2007-10-05
Should I report this upstream, e.g. to the GNOME desktop site or the nautilus bugs?

---

### Post by rtg on 2007-10-28
Thunar thumbnailer: 
[http://myrtg.blogspot.com/2007/10/thunar-opendocument-thumbnailer.html](http://myrtg.blogspot.com/2007/10/thunar-opendocument-thumbnailer.html)

unpack *thunar-vfs-odf-thumbnailer-1.desktop* file to */usr/share/thumbnailers*
and *thunar-vfs-odf-thumbnailer-1* to /usr/lib/thunar

---

### Post by bean77 on 2007-11-21
This was the perfect How To-I liked that you added the "why" in addition to the "how to".

Thanks for taking the time to help out your fellow users.

---

### Post by mauri76 on 2008-03-18
I'm trying to obtain the same result in kde, but it won't work.

Anyone has an idea?

Thanks!

---

### Post by KillerKiwi on 2008-03-18
KDE / konqurer needs a compiled module,

You can do it if you know some c++

check out
 
[http://developer.kde.org/documentation/library/3.2-api/kio/html/classThumbCreator.html](http://developer.kde.org/documentation/library/3.2-api/kio/html/classThumbCreator.html)

---

### Post by mauri76 on 2008-03-19
> **KillerKiwi said:**
> KDE / konqurer needs a compiled module,

You can do it if you know some c++

check out
 
[http://developer.kde.org/documentation/library/3.2-api/kio/html/classThumbCreator.html](http://developer.kde.org/documentation/library/3.2-api/kio/html/classThumbCreator.html)

I'm not able to do such a thing.

But I can't understand the reason why it worked since last reinstallation of kubuntu.

---

### Post by MES5464 on 2008-07-30
I love this!

Anything Vista can do Ubuntu can do better!
Ubuntu can do anything better than Vista!

Not can Ubuntu do this, but it could before Vista could!

Ubuntu rocks!

Congratulations to the creators of these scripts. Thank you very much.
Congratulations to Nautilus for making such a talented application.
Congratulations to Ubuntu for bring all these things to my desktop!

Ubuntu rocks!

---

### Post by shankar.svs on 2008-08-16
Thanks... Worked Perfectly... :)

---

### Post by TexJoachim on 2008-10-14
I just installed OpenOffice.org 3 and removed OpenOffice.org 2.
Now no new thumbnails are created. I can see the old ones fine, but new and changed documents get the default icon again.

What do I need to change to get the thumbnails back?

Regards,

Joachim

---

### Post by quanumphaze on 2008-10-17
> **TexJoachim said:**
> I just installed OpenOffice.org 3 and removed OpenOffice.org 2.
Now no new thumbnails are created. I can see the old ones fine, but new and changed documents get the default icon again.

What do I need to change to get the thumbnails back?

Regards,

Joachim

It works fine *for me* in OpenOffice 3

I have uninstalled OOo2 (you can't install the desktop integration deb with 2 still there) and just followed the thumbnail guide, replacing every occurrence of ooo2 with ooo3.

You may just have to remove the schemas to work. (Find out how first.)

---

### Post by quanumphaze on 2008-10-18
I revoke my previous statement. It worked but after a reboot it stopped.

If I reinstall the schemas ```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/ooo3.schemas
``` it will work after restarting Nautilus. I'll see later if it occurs again after tonight's reboot tomorrow.

---

### Post by mauri76 on 2008-11-24
It won't work with ooo3 & Ubuntu 8.04

---

### Post by mauri76 on 2008-12-03
No one has any idea? :sad:

---

### Post by rolfkleef on 2009-01-21
works for me now: Ubuntu 8.04LTS with OpenOffice 3

trying it out from the command line helped find what went wrong:
```
ooo2-thumbnailer file:///home/me/testdoc.odt test.png
```

I had to change the icon prefix in the thumbnailer script, I looked in my:

ICON_PATH_BASE = "/usr/share/icons/hicolor/48x48/apps/"

and saw that the icons started with a different prefix

not: ICON_PREFIX = "ooo-" #Ubuntu icons
but: ICON_PREFIX = "openofficeorg3-" #Ubuntu icons

---

### Post by MaxIBoy on 2009-02-08
Doesn't work for me.
Ubuntu 8.04
Openoffice 3.1
This version of the thumbnailer script: [http://ubuntuforums.org/showpost.php?p=471766&postcount=19](http://ubuntuforums.org/showpost.php?p=471766&postcount=19)
Replaced ooo2 with ooo3 in the script and schema file (even in the comments,) and in their filenames. 
Applied that fix to change "ooo-" to "openofficeorg3-" which was mentioned above.

To aid in debugging, I ran strace on that test operation
```
maxtothemax@maxtothemax-laptop:~$ strace -o style.txt ooo3-thumbnailer file:///home/maxtothemax/Documents/aareview.odt test1.png

```

The contents of the file are really big, so I'll attach the file. Scroll through to the bottom, that's where things get interesting.

---

### Post by MaxIBoy on 2009-02-08
FIXED! And new version of the code.


Seems I restored from a backup recently, and a couple of DVDs were coasters. The upshot is that I have quite a few zero-byte documents lying around. The script had no error checking for this.


Newly improved version:
```

# released into the public domain http://creativecommons.org/licenses/publicdomain
#!/usr/bin/python

import zipfile
import sys
import os
import gnomevfs
from PIL import Image, ImageEnhance

# Alter these varibles to change thumbnail look
BaseIconPath = "/usr/share/icons/hicolor/48x48/apps/" # Change this path to alter icons

# Opacity of the icon
IconOpacity = 0.8
# Color of the background
BackgroundColor = "white"

# Two types of icons Ubuntu and Ooo2
#iconPreFix = "openofficeorg-20-" # Ooo2 Stock
iconPreFix = "openofficeorg3-" # Ubuntu

"""
Open Document Types
================
    Text                 .odt     
    Spreadsheet         .ods 
    Presentation         .odp 
    Drawing             .odg 
    Chart             .odc
    Formula             .odf 
    Database             .odb 
    Image             .odi 
    Master Document    .odm
"""

# Nicked from http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/362879
def reduce_opacity(im, opacity):
    """Returns an image with reduced opacity."""
    assert opacity >= 0 and opacity <= 1
    if im.mode != 'RGBA':
        im = im.convert('RGBA')
    else:
        im = im.copy()
    alpha = im.split()[3]
    alpha = ImageEnhance.Brightness(alpha).enhance(opacity)
    im.putalpha(alpha)
    return im

inURL=gnomevfs.get_local_path_from_uri(sys.argv[1])
outURL=sys.argv[2]
nothumbURL=os.getenv("HOME")+"/Templates"
nothumbList=nothumbURL.split(os.sep)
inList=inURL.split(os.sep)

if inList[1]==nothumbList[1] and inList[2]==nothumbList[2] and inList[3]!=nothumbList[3]:
    try:
        zip=zipfile.ZipFile(inURL,mode="r")
        picture=zip.read("Thumbnails/thumbnail.png")
        zip.close()
        thumbnail=open(outURL,"w")
        thumbnail.write(picture)
        thumbnail.write("/n")
        thumbnail.close()

        # Get File Extension    
        fileExtension = inURL[ len(inURL)-3 :].lower()

        # Select Document Type
        iconFile = "writer"
        if fileExtension == "ods":
            iconFile = "calc"
        elif fileExtension == "odp":
            iconFile = "impress"
        elif fileExtension == "odg":
            iconFile = "draw"
        elif fileExtension == "odp":
            iconFile = "calc"
        elif fileExtension == "odf":
            iconFile = "math"
        elif fileExtension == "odi":
            iconFile = "draw"
        elif fileExtension == "odi":
            iconFile = "template"

        thumbnail = Image.open(outURL).convert("RGBA")

        # Load icon
        icon = Image.open(BaseIconPath + iconPreFix+ iconFile +".png").convert("RGBA")
        icon = reduce_opacity(icon, IconOpacity)
        # Create new img with white bg
        final = Image.new("RGB", (thumbnail.size[0],thumbnail.size[1]), BackgroundColor)
        # Add thumbnail
        final.paste(thumbnail, None, thumbnail)
        # Add icon
        x = final.size[0] - icon.size[0]
        y = final.size[1]-icon.size[1]
        w = x + icon.size[0]
        h = y + icon.size[1]
        final.paste(icon, (x,y,w,h), icon)
        # Save thumbnail
        final.save(outURL, "PNG")
    except:
        #encountered an invalid file or something
        pass #exit gracefully

```

---

### Post by Flimm on 2009-03-07
I've packaged this script for Jaunty, you can get it from [my PPA](https://launchpad.net/~flimm/+archive/ppa). (The package for Intrepid doesn't work, as the script relies on OpenOffice.org 3 icons, uploading it to my PPA was a mistake.)
I've also uploaded the code to [this bazaar branch](https://code.launchpad.net/~flimm/+junk/ooo-thumbnailer).
Could the authors of the script, release their code into the public domain or license it under the BSD license? The authors are of course [minio](http://ubuntuforums.org/member.php?u=2264), [KillerKiwi](http://ubuntuforums.org/member.php?u=23555) and [MaxIBoy](http://ubuntuforums.org/member.php?u=461522). I think the easiest way to do so would be for them to edit their previous posts in which they posted code and add at the top of the script:
```
# released into the public domain http://creativecommons.org/licenses/publicdomain
```.
As a package maintainer I have to care about copyright!

---

### Post by MaxIBoy on 2009-03-07
> **Flimm said:**
> I've packaged this script for Jaunty, you can get it from [my PPA]("https://launchpad.net/%7Eflimm/+archive/ppa"). (The package for Intrepid doesn't work, as the script relies on OpenOffice.org 3 icons, uploading it to my PPA was a mistake.)
I've also uploaded the code to [this bazaar branch]("https://code.launchpad.net/%7Eflimm/+junk/ooo-thumbnailer").
Could the authors of the script, release their code into the public domain or license it under the BSD license? The authors are of course [minio]("http://ubuntuforums.org/member.php?u=2264"), [KillerKiwi]("http://ubuntuforums.org/member.php?u=23555") and [MaxIBoy]("http://ubuntuforums.org/member.php?u=461522"). I think the easiest way to do so would be for them to edit their previous posts in which they posted code and add at the top of the script:
```
# released into the public domain http://creativecommons.org/licenses/publicdomain
```.
As a package maintainer I have to care about copyright!
I hereby release the code into the public domain (I'll also edit the script I posted to include the comment.)

Also, realize that there are two BSD licenses and they're not the same. So if you're going to release this under a BSD license, pick which one.

---

### Post by Flimm on 2009-03-08
> **MaxIBoy said:**
> I hereby release the code into the public domain (I'll also edit the script I posted to include the comment.)

Also, realize that there are two BSD licenses and they're not the same. So if you're going to release this under a BSD license, pick which one.
Thanks, that was quick! Public domain is easier for everyone, but the suggested BSD license is the one without the advertising clause and with the endorsement clause, here it is: (remember to replace <copyright holder's full name here>)
```
Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution. 
Neither the name of the <copyright holder's full name here> nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission. 

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE. 
```

---

### Post by KillerKiwi on 2009-03-08
Heres a new version tested for intrepid and jaunty

 - removed hardcoded icon paths
 - turned off icons by default

[https://code.launchpad.net/~killerkiwi2005/+junk/ooo-thumbnailer](https://code.launchpad.net/~killerkiwi2005/+junk/ooo-thumbnailer)

to build a deb
debuild -us -uc


How do we get this into ubuntu now ?

---

### Post by calc on 2009-03-08
> **KillerKiwi said:**
> Heres a new version tested for intrepid and jaunty

 - removed hardcoded icon paths
 - turned off icons by default

[https://code.launchpad.net/~killerkiwi2005/+junk/ooo-thumbnailer](https://code.launchpad.net/~killerkiwi2005/+junk/ooo-thumbnailer)

to build a deb
debuild -us -uc


How do we get this into ubuntu now ?

I think I am messaging you in the bug report on launchpad. :-)

I will be uploading it once a few issues are ironed out. One of them is that the names of the authors are still not in the file just their forum usernames...

---

### Post by calc on 2009-03-08
As I mentioned to KillerKiwi earlier to get this into Ubuntu we need the people's names and email addresses (minio, KillerKiwi, MaxIBoy) in the appropriate places in the files for copyright/licensing reasons. There are also a few other minor issues with the packaging that lintian shows after compiling.

This is the bug where I have documented a few other issues:

[https://bugs.launchpad.net/bugs/25827](https://bugs.launchpad.net/bugs/25827)

If we can get the information and packaging updated I may be able to get it into Ubuntu in time for Alpha 6, which is this Thursday, but that would require having it ready probably by tomorrow.

---

### Post by calc on 2009-03-08
Oh yea, also let me know which repo I should use between the Flimm and KillerKiwi bzr repos once the remaining issues have been resolved.

---

### Post by Flimm on 2009-03-09
Unfortunately, [minio](http://ubuntuforums.org/member.php?u=2264) doesn't seem to have logged in since January 25th, 2009, which means it might take some time for him to answer us, unless he regularly checks his email.
The reason why I changed /usr/bin/python to /usr/bin/env python2.5 was because gnomevfs refused to import under Jaunty unless I used python2.5. Have you tested it under Jaunty? Maybe an update has fixed it since Saturday.

---

### Post by calc on 2009-03-09
It seems to work when I just went into python directly and typed import gnomevfs...

---

### Post by Flimm on 2009-03-11
Due to issues raised in [bug 25827](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/25827), I've rewritten the code in bash. You can get the code from [this bazaar branch](https://code.launchpad.net/~flimm/+junk/bash-ooo-thumbnailer), or you can just install the attached .deb. I need it to be tested on Jaunty, as I've borked my Jaunty virtualbox installation, so do tell me if it works.

---

### Post by KillerKiwi on 2009-03-11
> **Flimm said:**
> Due to issues raised in [bug 25827](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/25827), I've rewritten the code in bash. You can get the code from [this bazaar branch](https://code.launchpad.net/~flimm/+junk/bash-ooo-thumbnailer), or you can just install the attached .deb. I need it to be tested on Jaunty, as I've borked my Jaunty virtualbox installation, so do tell me if it works.

Nice work you beat me to it :)

P.S did you update the bug as well ?

Confirm it works here on intrepid

---

### Post by KillerKiwi on 2009-03-11
Maybe should ditch the icon overlay for now and add back all the mimetypes.. so we can get this in ?

---

### Post by KillerKiwi on 2009-03-11
Also it dosnt work on jaunty!

---

### Post by Flimm on 2009-03-12
Could someone with Jaunty do some testing for me? Basically, post the output of the following commands, once you've downloaded and installed [the code](http://ubuntuforums.org/showpost.php?p=6878603&postcount=78).
First, create an OpenOffice.org document test.odt in your home directory.
```

unzip ~/test.odt Thumbnails/thumbnail.png -d ~/
totem-gstreamer-video-thumbnailer "~/Thumbnails/thumbnail.png" "~/thumbnail.png"
gnome-video-thumbnailer "~/Thumbnails/thumbnail.png" "~/thumbnail2.png"
ooo-thumbnailer ~/test.odt ~/thumbnail3.png

```
Then check to see if thumbnail.png , thumbnail2.png and thumbnail3.png are the correct thumbnails of the document, with a white rather than a transparent background.

---

### Post by calc on 2009-03-12
> **Flimm said:**
> Due to issues raised in [bug 25827](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/25827), I've rewritten the code in bash. You can get the code from [this bazaar branch](https://code.launchpad.net/~flimm/+junk/bash-ooo-thumbnailer), or you can just install the attached .deb. I need it to be tested on Jaunty, as I've borked my Jaunty virtualbox installation, so do tell me if it works.

Is there a particular reason the debian build system for the package still is setup for python? I would think it would only need to copy the bash script into the correct location and not actually need pycentral anymore?

---

### Post by Flimm on 2009-03-12
> **calc said:**
> Is there a particular reason the debian build system for the package still is setup for python? I would think it would only need to copy the bash script into the correct location and not actually need pycentral anymore?
No good reason, besides the fact that I know that system the best. Other non-python packages such as ubuntu-wallpapers use pycentral as well, so I'm not doing anything unheard of.

---

### Post by siafok on 2009-03-21
Hello. I have question. Does your thumbnailer not work with files with whitespace in their names?

---

### Post by Flimm on 2009-03-24
Well spotted, fixed it in the latest version.

---

### Post by minio on 2009-03-25
I just want all to know that **my** code that **I** posted in "HOWTO: Thumbnails for OpenOffice.org 2 files" thread is under public domain. 

Can't obviously speak for others.

---

### Post by jmdsdf on 2009-04-02
I noticed that the thumbnailer supports Open Office Spreadsheets (i.e. it will generate an preview image for an ODS file) but it doesn't get Nautilus to do this by default. Could you please add support for the vnd.oasis.opendocument.spreadsheet file type in the gconf schema? Oh yeah, the thumbnailer that I downloaded had /usr/bin/ooo-thumbnailer broken on line 33. Just change it to:
```

if [ "`dirname $ifile`" != "${XDG_TEMPLATES_DIR:-$HOME/Templates}" ]; then
```

And you're set (notice the quotations, otherwise white space in the file names create problems). I tested this in Jaunty with no problems!

Further, would any agree that this would look better with the OpenOffice logo in the bottom right corner, similar to the way OpenOffice works under other operating systems?

---

### Post by cristianfere on 2009-06-04
Hello people, based on the script posted above, I created a new package with a modified version of the script, and add more formats in schemas.

Supported formats: odt, ods, odp, doc, xls, ppt and rtf.

For the new formats (doc, xls, ppt and rtf) the script uses the unoconv for conversion.

I like thumbnails in nautilus. We already have thumbnails for images, video and  preview of music. 

Why not for documents? This is a good feature request for future version of ubuntu. What do you think?

---

### Post by KillerKiwi on 2009-06-04
> **cristianfere said:**
> Hello people, based on the script posted above, I created a new package with a modified version of the script, and add more formats in schemas.

Supported formats: odt, ods, odp, doc, xls, ppt and rtf.

For the new formats (doc, xls, ppt and rtf) the script uses the unoconv for conversion.

I like thumbnails in nautilus. We already have thumbnails for images, video and  preview of music. 

Why not for documents? This is a good feature request for future version of ubuntu. What do you think?

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/25827](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/25827)

Trying really hard...

---

### Post by EnlistedSquire on 2009-08-15
@cristianfere,

Your package works great in Ubuntu 9.05. Thanks (I haven't tried any of the previous versions that have been posted because I've only just found this thread).

Once small thing though; The first time I open Nautilus, if I browse to a folder that contains files in OOO or MS Office format that haven't had their thumbnails generated yet, the first two or three thumbnails don't generate.

There is clearly something loading in the background so I guess it hasn't finished loading in time to catch the first couple of files.

So that this doesn't become a big problem I've set up a cron job to delete all the files from ~/.thumbnails/fail/gnome-thumbnail-factory/ every hour so they will hopefully get regenerated the next time I browse to that folder.

Cheers.

---

### Post by MES5464 on 2010-01-18
I have installed the ooo-thumbnailer package but Nautilus isn't using it to create the thumbnails. How do I cause Nautilus to start using the script?

---

### Post by Flimm on 2010-01-19
> **MES5464 said:**
> I have installed the ooo-thumbnailer package but Nautilus isn't using it to create the thumbnails. How do I cause Nautilus to start using the script?
I find that sometimes you have to log in and out again for changes to take effect.
There's a later version of ooo-thumbnailer in [this PPA](https://launchpad.net/~flimm/+archive/ooo-thumbnailer).

---

### Post by jesuisbenjamin on 2010-02-03
hi there,

i installed tried the early scripts which worked except for adding a white background to the thumbnails. Then i installed the packages proposed by Cristinafere on post [http://ubuntuforums.org/showpost.php?p=7402808&postcount=89](http://ubuntuforums.org/showpost.php?p=7402808&postcount=89) 
There is yet no white background to the ODT thumbnails. 

Should i do anything?

Thanks

---

### Post by jesuisbenjamin on 2010-02-03
Correction! it works after i re-save the file!

Thanks guys! This is cool stuff!

---

### Post by Flimm on 2010-05-07
[ronjouch](http://ubuntuforums.org/member.php?u=594169) pointed out to me that libgsf-bin does the same job as ooo-thumbnailer, plus it handles Microsoft Office documents that have thumbnails saved in their metadata. Unfortunately, OpenOffice.org doesn't save thumbnails in Word documents or Excel spreadsheets by default (see [this thread](http://user.services.openoffice.org/en/forum/viewtopic.php?f=15&t=13852&start=0)).

This means the only advantage ooo-thumbnailer has over libgsf-bin is that ooo-thumbnailer overlays a little OpenOffice.org icon in the lower right corner of the thumbnails.

---

### Post by Flimm on 2010-05-19
I've released version 0.3.1 of ooo-thumbnailer. Here are the new features:

[list][*]supports Microsoft Office documents, spreadsheets and presentations (2003 and 2007).
[*]supports OpenOffice.org templates
[*]generates thumbnails for Microsoft Office files, even if preview information had not been embedded in those files. This beats libgsf-bin.[/list]

You can get the new version from [this PPA](https://launchpad.net/~flimm/+archive/ooo-thumbnailer), and you can get the source code from the [launchpad project](https://launchpad.net/ooo-thumbnailer). Feedback welcome. :)

---

### Post by EnlistedSquire on 2010-05-20
Nice one, thanks.

---

### Post by EnlistedSquire on 2010-05-20
This new version seems to be a bit selective about what MS Office files it generates thumbnails for. All the ones I've tested are below the size limit in the config file. Is there any logging to be had?

---

### Post by Flimm on 2010-05-22
Indeed, it is selective, according to the settings in ~/.config/ooo-thumbnailer.conf.
```
# User options for ooo-thumbnailer file
OOOTHUMBNAILER_TIMEOUT=10 # in seconds
OOOTHUMBNAILER_UNOCONV_MAX_SIZE=8000000 # in bytes
```

If the file is taking more than 10 seconds to thumbnail, ooo-thumbnailer will automatically quit.

Microsoft Office files can be saved with or without a thumbnail ([see this page](http://windowstipsandfixes.blogspot.com/2010/01/missing-thumbnails-for-microsoft-office.html)) if you're using Office. Unfortunately, OpenOffice.org always saves office files without thumbnails (see [this bug](http://qa.openoffice.org/issues/show_bug.cgi?id=97370)).

The supported Microsoft Office file type are .doc, .docx, .xls, .xlsx, .ppt and .pptx.

If ooo-thumbnailer encounters an Office file without a thumbnail, it converts it to an OpenOffice.org file using unoconv and grabs the preview from that. This operation can take a long time, hence the time limit and the size limit.

If you want to disable the time and size limits, set the options to:```
OOOTHUMBNAILER_TIMEOUT=-1
OOOTHUMBNAILER_UNOCONV_MAX_SIZE=-1
```

If a file is still not being thumbnailed, try this on the command line:
```
ooo-thumbnailer document.doc preview.png 128
```
and [send me the output in a bug report](https://bugs.launchpad.net/ooo-thumbnailer/+filebug).

---

### Post by melT4 on 2010-05-22
Hi,
I just install this new version of ooo-thumbnailer. Thanks a lot, it's almost perfect to me. I have some office files that are not thumbnailed, but in general it's quite better than libgsf-bin.
Since you seems to be an advanced user concerning thumbnail, I have a question. Since my passage to Lucid, my ppt files are greyed and really hideous. [(Screenshot)]("http://db.tt/mRRjLo")
It's not related to your script, they appear like this since my re-installation, even if I cleared .thumbnails.
Thanks, if someone could help me...
Mel

---

### Post by Flimm on 2010-05-24
Hmm, that does look awful. I'm suspecting a bug in libgsf-bin. Try:
```
gsf-office-thumbnailer -i powerpoint.ppt -o out.png -s 128
```
And look at out.png.

---

### Post by melT4 on 2010-05-24
Thanks to you for interest in my problem.
I tried with 2 different ppt
One giving a grey thumbnail:

```
melanie@melanie-portable:/$ gsf-office-thumbnailer -i ~/Aires10jc_Tremblay_2010-02-16_VPA\ urea\ cycle.ppt -o ~/out.png -s 128

(gsf-office-thumbnailer:3037): GdkPixbuf-CRITICAL **: at_scale_size_prepared_cb: assertion `width > 0 && height > 0' failed

(gsf-office-thumbnailer:3037): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

One giving a OK thumbnail:
```
melanie@melanie-portable:/$ gsf-office-thumbnailer -i ~/Brown10jc_Tremblay_2010-04-29_3CPD\ colliculus.ppt -o ~/out.png -s 128
calling convert '/home/melanie/out.png.GAB6CV' +matte -thumbnail 128x128 png:'/home/melanie/out.png'

(gsf-office-thumbnailer:4801): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

I already tried a re-install of libgsf-bin, in case you ask. I could also add a precision : on my netbook (running also Lucid), I don't have this problem (with the same powerpoint files).
Thanks,
Mel

---

### Post by Flimm on 2010-05-25
Well, it looks like a bug in libgsf-bin I'm afraid, and I don't know what's causing it.

You might want to try reinstalling imagemagick as the second command calls _convert_ while the first one doesn't for some reason.

Another idea is to uninstall imagemagick completely, libgsf-bin doesn't depend on it, it only suggests it. ooo-thumbnailer does depend on imagemigick, but it might help pinpoint the source of the problem.

---

### Post by melT4 on 2010-05-25
Thanks.
Unfortunately it doesn't work. I'm still looking for a solution if someone found it...

---

### Post by daniele80 on 2011-02-05
I installed Libreoffice,
now ooo-thumbnailer does not work any more

---

