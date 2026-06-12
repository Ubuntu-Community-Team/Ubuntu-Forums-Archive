---
title: "[howto] Usability tweaks"
date: 2008-11-17
forum: Outdated Tutorials &amp; Tips
---

### Post by bash on 2008-11-17
**About**

After installing a new vanilla Ubuntu, there are always quite a number of things I start changing. Things like the theme, add/remove programs and especially these little details that in my view should have been added since a long time to the default Ubuntu. Things like thumbnails previews for OOo documents, being able to use other video players than totem to preview video documents and so on.

There I tried to make a guide of usability tweaks and how to apply them. If anybody happens to have other fancy little convenience additions, be sure to post them and I'll add them to the post. My goal is to create a comprehinsive guide on the small tweaks and improvements that can make life or in this case using Ubuntu easier and more confortable. So far all these instructions are for either Ubuntu 8.04 or 8.10 or both. So please contribute.



***Ubuntu 8.04 & 8.10***

**Thumbnail preview for OpenOffice documents**

This will add a nice thumbnail previews of the OOo documents (.odt, .odp, ...) in Nautilus. Just like it happens for PDF documents or videos. It is a modification and combination of [minio's](http://ubuntuforums.org/showpost.php?p=413714&postcount=1) and [KillerKiwi's](http://ubuntuforums.org/showpost.php?p=466348&postcount=12) scripts. It also adds a white background to each thumbnail but no extra overlay icon. 

First create file named ooo2-thumbnailer in /usr/bin:

```
gksudo gedit /usr/bin/ooo2-thumbnailer
```

And copy in the following code:

```
#!/usr/bin/python

import zipfile
import sys
import os
import gnomevfs
from PIL import Image, ImageEnhance

# Color of the background
BackgroundColor = "white"

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

	thumbnail = Image.open(outURL).convert("RGBA")

	# Create new img with white bg
	final = Image.new("RGB", (thumbnail.size[0],thumbnail.size[1]), BackgroundColor)
	# Add thumbnail
	final.paste(thumbnail, None, thumbnail)
	# Save thumbnail
	final.save(outURL, "PNG")
```

Save and close the file. Then make it executable:

```
sudo chmod +x /usr/bin/ooo2-thumbnailer
```

Next create second file:

```
gksudo gedit /usr/share/gconf/schemas/ooo2.schemas
```

And add the following:

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

Now save and close the file. The last step will be to tell GNOME to read the file and restart nautilus:

```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/ooo2.schemas
```

```
killall -9 nautilus
```

Now you should be all set and have fancy little thumbnails.



**Using Mplayer to create thumbnail previews for videos**

If you don't happen to have Totem installed you normally miss out on the neat little thumbnail previews for video files in Nautilus. If you use Mplayer instead though you no longer have to miss out. You can get Mplayer to generate all those thumbnails for you. Just follow these steps.

First of lets make sure we have all the needed packages installed

```
sudo apt-get install mplayer imagemagick
```

Next up we need to download the mplayer thumbnails script and install it:

```
wget http://me2030581.googlepages.com/mplayer-video-thumb-1.3-3.tar.bz2
tar -xf mplayer-video-thumb-1.3-3.tar.bz2
cd mplayer-video-thumb-1.3-3
chmod +x setup.sh
sudo ./setup.sh
./gconf.sh
cd ~
```

Now mplayer should create video previews for you. If you happen to have failed preview icons, just delete those so that mplayer can recreate them:

```
rm -rf $HOME/.thumbnail/fail/
```



**Making QT applications use GTK+ themes**

*Note for Ubuntu 8.04: If you use Ubuntu 8.04 you will have to enable the Ubuntu-Backports repository and update to Qt 4.4. What backports are, how to activate them and if they are for you, you can find out here: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)*

One of the developers at Trolltech create this fancy little QT Style that allows you to use GTK themes for QT applications. Now no longer will the QT programs look alien on your desktop, but blend in smoothly with your other GTK+ applications. Sadly it is not (yet?) available in the repositories, so we have to compile it ourselves.

First off lets install all the needed packages:

```
sudo apt-get install subversion build-essential checkinstall libqt4-dev libgtk2.0-dev qt4-qtconfig
```

After we need to get the code, compile it:

```
svn co svn://labs.trolltech.com/svn/styles/gtkstyle
cd gtkstyle
qmake && make
sudo make install
```

*Note: For those that know and want to use checkinstall, you of course also can do that instead of make install*

To finish off we just need to open the QT Config and set the style to GTK there (Don't forget to click "File" &#8594; "Save" or you settings won't be remembered).

*Note: The GTK style you set in qtconfig only works for QT applications (VLC, Virtualbox, ...) but does not change the style of KDE applications (KTorrent, ...).*



**Making programs running as root use your custom theme**

So you have changed your theme? Customized everything the way you like? And then you open some application running as root, Synaptic for example, and are greeted by an ugly grey something. Well it doesn't have to be that way. For only 9.95$ you can buy our new herbal ... nah but seriously, you can change it, so root applications also use your "custom" theme. It's pretty easy actually. Open a Terminal and run the following commands:

```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```

That was all. Close the Terminal and open a program requiring root and stare in awe at the awesomeness.



**Prettying up WINE**

Well some of us need or want to run Windows applications. Of course you could set up a VirtualMachine, but in most cases WINE represents the much simpler solution. Now the one nagging issue left are those fugly Windows 95 like WINE GUIs. Worry not dear sir (or madam) as there is a simple answer to your questions: Theme your WINE! So how do you do this you ask?

First of all we need to download a fitting theme. Luckily WINE is able to use the Visual Styles theme files. So all you need is a .msstyles theme file and you are set.

Now if you still using the default Ubuntu Theme I would recommend to download this theme for WINE:

[http://fioressj.deviantart.com/art/Human-for-Windows-37743373](http://fioressj.deviantart.com/art/Human-for-Windows-37743373) 

Some other nice choices of themes for WINE can be found here:

[http://wingnomexp.blogspot.com/search/label/Visual%20Styles](http://wingnomexp.blogspot.com/search/label/Visual%20Styles)

Whatever theme you decided to download, unpack it now. Next up we need to open the WINE configuration window. Either by browsing to "Applications" &#8594; "Wine" &#8594; "Configure Wine" or by typing "winecfg" in a terminal (Without the ""). 

In the WINE configuration menu go to the "Desktop-Integration" Tab and click on the "Install style" button. Select the .msstyle file you downloaded and click "Open". Now that you installed the new Style, all you need to do is select it from the "Styles" dropdown-list. From now all your WINE applications shine in a new light.




***Ubuntu 8.10***

**Fixing wrong icons in the "Places" menu**

If you change your Icon theme in Ubuntu 8.10 you will pretty soon notice that icons for the default folders (Audio, Video, ...) in the "Places" menu don't change correctly. That is pretty easy to solve. Just do the following:

> sudo rm -f /usr/share/icons/gnome/scalable/places/inode-directory.svg
sudo rm -f /usr/share/icons/gnome/32x32/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/24x24/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/22x22/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/16x16/places/inode-directory.png
sudo rm -f /usr/share/icons/gnome/icon-theme.cache
sudo gtk-update-icon-cache -qf /usr/share/icons/gnome

Log out and back in and the issue should be fixed.



***Ubuntu 8.04***

**Making VLC the default DVD player**

If you decided to use VLC instead of Totem as your default video player, you suddenly notice that when you inset a DVD, nothing happens. That is because the VLC package in Ubuntu 8.04 doesn't register itself as a DVD player. So we have to do this manually using a work-around.

We need to edit the following text file, so open by typing this in your Terminal:

```
gksudo gedit /etc/gnome/defaults.list
```

In the open Texteditor window we got to "Search" &#8594; "Replace" and replace the word "totem" with word "vlc" (both without the "") and press "Replace all". Now save and close the file and should now have VLC as our default DVD player.




**Thanks**

    * Thanks to minio for figuring out the original OOo thumbnailer ([Link]("http://ubuntuforums.org/showthread.php?t=76566"))
    * Thanks to mysticmatrix for his/her great tutorial on using mplayer to generate video previews ([Link]("http://ubuntuforums.org/showpost.php?p=3270013&postcount=3"))
    * Thanks to Ravinder Rathi for writing the great mplayer video thumbnailer script ([Link]("http://me2030581.googlepages.com/"))
    * Thanks to Jens at Trolltech for creating the great QT Style ([Link]("http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/"))

---

### Post by quanumphaze on 2008-11-22
Great post. Especially the root gtk theme, Win95 style is just really ugly.

You should keep adding more tweaks to the list as you come across them. You may just make the HowTo of the Week award.

---

### Post by bash on 2008-12-01
Updated the tutorial. Added how to fix wrong folder icons in 8.10, how-to theme WINE and updated some tips.

---

### Post by binbash on 2008-12-01
thanks for wine theme

---

