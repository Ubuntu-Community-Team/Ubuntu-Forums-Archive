---
title: "HOWTO: View NFO files"
date: 2005-10-28
forum: Outdated Tutorials &amp; Tips
---

### Post by ow50 on 2005-10-28
[SIZE="4"]**Update 2007-08-16:**

Visit the new home page of NFO Viewer. This HOWTO is now obsolete.
[http://home.gna.org/nfoview/](http://home.gna.org/nfoview/)[/SIZE]


NFO files are "ASCII-art" with the cp437 codepage, which includes a lot line- and block characters. To view the "ASCII-art" of NFO files correctly, it is enough to use the right encoding and font. As you might not want to set your normal text editor for those settings or perhaps your normal text editor is too slow to start, you can use a separate application written by me for viewing NFO files. Unlike text editors, NFOview will also allow you to click on links that appear in the text. This HOWTO will will walk you through setting that up.

The application I have written is very simple. It is not an editor, just a viewer. A text view widget in a window. No menubar, no toolbar, no statusbar, no buttons. Should be as fast as it gets with Python and GTK.

Screenshot with some random NFO file:
[[IMG]http://img492.imageshack.us/img492/839/ssnfoview7bn.th.png[/IMG]](http://img492.imageshack.us/my.php?image=ssnfoview7bn.png)

**Part 1: Setting up nfoview**

**1.1** Install packages "python" and "python-gtk2" if you don't have them already.

**1.2** Get the Lucida Console P font
```
cd ~/.fonts && wget http://home.online.no/~aageli/luconP.ttf
```
Lucida Console P has support for all the cp437 codepage characters. monospace font works as well, but it doesn't have all the characters.

**1.3** Download the nfoview script
[http://users.tkk.fi/~otsaloma/scripts/nfoview](http://users.tkk.fi/~otsaloma/scripts/nfoview)

Put it for example in ~/bin or some place that's in your $PATH and give it execute permissions.

**1.4** Test it
```
nfoview file.nfo
```

**1.5** Edit the settings in file ~/.nfoview if needed.

**Part 2: Setting up file-associations**

This section works at least in GNOME and should probably work in any desktop encironment that adheres to the FreeDesktop.org standards. In the instructions, just replace Nautilus with your preferred filemanager if you don't use GNOME.

**2.1** Add a mime-type for NFO files.

```
gedit ~/.local/share/mime/packages/Override.xml
```
Make the file look the following (but don't remove other possible entries you might have):
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">

<mime-type type="text/x-extension-nfo">
	<comment>NFO document</comment>
	<glob pattern="*.nfo"/>
</mime-type>

</mime-info>
```

*Note: I'm not sure if that should best be "text/x-extension-nfo" or "application/x-extension-nfo" or perhaps something else.*

**2.2** Rebuild the mime-type database. The changes should be instant-applied, but if not try logging out and logging back in.
```
update-mime-database ~/.local/share/mime
```

**2.3** Right click an NFO file in Nautilus. The mime-type should now be "text/x-extension-nfo".

**2.4** Add a desktop file.

```
gedit ~/.local/share/applications/nfoview.desktop
```
Paste the following. Fix the path on the "Exec" line and add translations if you wish.
```
[Desktop Entry]
Encoding=UTF-8
Name=NFOview
Comment=View NFO files
MimeType=text/x-extension-nfo;
Exec=/home/osmo/bin/nfoview
Type=Application
Terminal=false
NoDisplay=true
```

**2.5** Right click an NFO file in Nautilus. You should now see an entry "Open with NFOview". If not, right click and go to Properties ->  Open with -> Add -> Use other command.

**2.6** Set a mime-type icon.

Place your preferred icon in your icon theme's folder as "scalable/mimetypes/gnome-mime-text-x-extension-nfo.png". You might need to refresh the icons by for example changing your icon theme to something else and then changing it back.

*Notes: Using the "scalable" directory will change the icon for 32x32 and 48x48 icons with GNOME 2.16 default icon theme. The most elegant way to add custom icons indepedent of the icon theme you're currently using would probably be to create a new icon theme with your custom icons and have that inherit whatever icon theme you wish to use.*

---

### Post by bionnaki on 2005-10-29
works great!

here's a screenshot of my custom colors/size:

[IMG]http://www.psidonia.net/host/Screenshot.png[/IMG]

and here's a site with all the color codes, if anyone
needs it: [http://www.webdiner.com/annexe/hexcode/hexcode.htm](http://www.webdiner.com/annexe/hexcode/hexcode.htm)

been looking for a decent nfo viewer on linux
for quite awhile - finally!

---

### Post by Lukano on 2005-10-29
I didn't see any existing directories for mime stuff for my default user in breezy - so although I created them as per the directions above, I can't seem to get gnome to recognize the association for nfo's.  Any suggestions or alternate locations I might look to set the mime type?

---

### Post by ow50 on 2005-10-29
[QUOTE=Lukano]I didn't see any existing directories for mime stuff for my default user in breezy - so although I created them as per the directions above, I can't seem to get gnome to recognize the association for nfo's.  Any suggestions or alternate locations I might look to set the mime type?[/QUOTE]
Do you mean the steps I numbered as 2.1 and 2.2?
If yes, the path should be correct as far as I know. I am no expert on mime-types, I have just experimented and found the above to work. There is of course a global directory /usr/share/mime, but you should rather add custom mime-types to your home folder.

---

### Post by bionnaki on 2005-10-29
I just right-clicked on a .nfo file & changed the assocation in properties>open with. "add" & pointed to the script. works everytime.

---

### Post by Lukano on 2005-10-29
[QUOTE=bionnaki]I just right-clicked on a .nfo file & changed the assocation in properties>open with. "add" & pointed to the script. works everytime.[/QUOTE]

Well I got it working with the /usr/share instead of /home/user/ path.

---

### Post by Parkotron on 2005-10-30
Believe it or not, I created a similar program for Windows a couple years ago and it too was named *nfoview*. I guess coming up with interesting and original program names is harder than one might expect.

Mine doesn't hold a candle to yours, however. It used the command line to display the file and the arrow keys to scroll. Anyway, I just thought the coincidence was interesting.

---

### Post by rwabel on 2005-10-30
that's a nice nfo viewer, thanks

---

### Post by pmj on 2005-10-30
I've been using this script for a couple of months now. It's neat, but I've often wished I knew Python so I could fix a few things.

As can be seen in the screenshot bionnaki posted, there are thin white lines beneath every line of text. It looks exactly the same for me. In Hoary there were no lines in exactly this way that I can remember, at least not with the font I used (I can't remember if I switched fonts because of this issue or because of some other reason) but there, in Hoary, I had the problem that if I scrolled up, usually in a jerky way, the white lines would appear.

Curious about how difficult it would be to create an nfo viewer I made a GUI in Glade and it had no issues with white lines. So this might be an issue with just your script or with Python. But since I'm a terrible coder I didn't manage to make more than a pretty GUI with a preloaded nfo.

It would be great if this script could be improved to fix the strange white line problem, and perhaps even get some basic checking of height and width of the nfo to set a window of correct proportions, as well as fix the output of badly done and damaged files, such as when there are empty lines at the end or when every other line empty. These files aren't common, but I get them every now and then.

Oh, and if anyone's interested in getting rid of the thick border around the window, find the line window.set_border_width(12) and change 12 to 0.

Edit: Making the cursor invisible would be great too. Anyone know how?

---

### Post by ow50 on 2005-10-30
[QUOTE=pmj]As can be seen in the screenshot bionnaki posted, there are thin white lines beneath every line of text....[/QUOTE]
That is a font and font size issue. With the default font size in the script (9) and the default font (Lucida Console P) I don't get these lines, as you can see the screenshot in my first post. Once I deviate from the size of 9, I get those borders on all sides of all blocks. You could try other fonts if you have problems. I don't see any way this could be a code issue.

[QUOTE=pmj]It would be great if this script could be improved to fix the strange white line problem, and perhaps even get some basic checking of height and width of the nfo to set a window of correct proportions, as well as fix the output of badly done and damaged files, such as when there are empty lines at the end or when every other line empty. These files aren't common, but I get them every now and then.[/QUOTE]
Your suggestions are worth considering. I'll look into it. I have just gone with the simplest possible, as can be seen from the length of the script.

[QUOTE=pmj]Oh, and if anyone's interested in getting rid of the thick border around the window, find the line window.set_border_width(12) and change 12 to 0.[/QUOTE]
The 12 pixel border is a GNOME HIG issue, hence my choice to go with that.

[QUOTE=pmj]Edit: Making the cursor invisible would be great too. Anyone know how?[/QUOTE]
Probably
text_view.set_editable(False)

---

### Post by bionnaki on 2005-10-30
thin white lines? I dont think I get those...everything is looking damn fine ;)

---

### Post by pmj on 2005-10-30
[QUOTE=bionnaki]thin white lines? I dont think I get those...everything is looking damn fine ;)[/QUOTE]
In your case the lines are purple as that's the color of your background. Notice that in the picture in the OP all characters/blocks fit together perfectly.

---

### Post by bionnaki on 2005-10-30
Op?

---

### Post by pmj on 2005-10-30
[QUOTE=ow50]That is a font and font size issue. With the default font size in the script (9) and the default font (Lucida Console P) I don't get these lines, as you can see the screenshot in my first post. Once I deviate from the size of 9, I get those borders on all sides of all blocks. You could try other fonts if you have problems. I don't see any way this could be a code issue.[/QUOTE]

Thank you for the reply. I guess I just have to find a winning combination of font and size.

---

### Post by mykey on 2005-10-30
@ ow50

.. nice howto - I appreciate the parts about mime-types and icon settings - thank you agein ;)

---

### Post by ow50 on 2005-10-30
Updated based on pmj's suggestions:
[LIST]
[*]Window size is now determined automatically. You get to define its maximum size.  It's a bit experimental, because I had to define a "random extra" parameter, which I set at 64 pixels. There's a chance that with some other GTK2 theme it should be greater.
[*]If either all even or all odd lines are blank, they're discarded.
[/LIST]

Couple other minor changes: etched in shadow for the text view and Commodore 64 colors by default.

Edit:
One more update: blank lines at the end of the file are now discarded as well.

---

### Post by pmj on 2005-10-30
Just wanted to say thank you one more time. The new features seems to work perfectly.

---

### Post by bionnaki on 2005-10-30
yeah, for real. 
I've been looking for a nfo viewer on linux
for about 2 years now.

do you have any more cool scripts?

---

### Post by minio on 2005-10-30
About those white lines benath (or above?) each line. If you want to get rid of them then you could add line```
text_view.set_pixels_above_lines(-1)
``` just before line containing ```
text_buffer = text_view.get_buffer()
```
Or play with font size and type :)

---

### Post by Syphin on 2005-10-30
Thanks for the script, works perfectly with the edit suggested by minio. :D

---

### Post by ow50 on 2005-10-30
Updated to fix the line spacing issue.

[QUOTE=minio]```
text_view.set_pixels_above_lines(-1)
```[/QUOTE]
Thanks minio. That does indeed solve the vertical line problem. Don't know how I missed that myself. The font size still seems to effect the horizontal spacing, or the lack of it, between characters.

[QUOTE=bionnaki]do you have any more cool scripts?[/QUOTE]
The ones I considered to be somewhat universally useful without too much customization are at
[http://koti.mbnet.fi/~ots/scripts/](http://koti.mbnet.fi/~ots/scripts/)

---

### Post by mustang on 2005-10-31
Thank you sir. I've been looking for something exactly like this.

---

### Post by dude2425 on 2005-11-01
About the icon, if you just put it into the hicolor theme instead of making a new one or anything, you will have it in EVERY theme due to inheritance. Great time saver incase you have no definite choice in icons and are always changing your mind.

---

### Post by bionnaki on 2005-11-02
how?

---

### Post by ow50 on 2005-11-02
[QUOTE=bionnaki]how?[/QUOTE]
The hicolor icon theme is in /usr/share/icons/hicolor, so the following commands should do it
```
cd /usr/share/icons/hicolor/48x48/mimetypes/
sudo wget http://koti.mbnet.fi/~ots/img/gnome-mime-text-x-extension-nfo.png
```

---

### Post by minio on 2005-11-03
Because I like thumbnails more then icons I've created thumbnailer for Gnome. You have to have text/x-extension-nfo mime type defined (as it's described in the first post) to make thumbnailer work.

So first download the attached archieve and extract both files from it. Now if you want your thumbnails to have other colors then black and white open the nfo-thumb in gedit or other text editor and change BG_COLOR and FONT_COLOR to what you like and save the file. Then copy the nfo-thumb to /usr/bin and make it executable, by typing (from directory where the extracted files are):```
sudo cp nfo-thumb /usr/bin/
sudo chmod +x /usr/bin/nfo-thumb
``` then copy nfo-thumbnail.schemas to /usr/share/gconf/schemas by typing```
sudo cp nfo-thumbnail.schemas /usr/share/gconf/schemas/
```
Then tell Gnome to load it ```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/nfo-thumbnail.schemas
``` and restart nautilus ```
killall -9 nautilus
```.
Now if you open some directory with nfo file you should see its thumbnail like those in attached picture :)


And you need Lucida ConsoleP font installed

---

### Post by minio on 2005-11-03
If anyone downloaded nfothumb.tar.gz file in the time between i posted previous post and this post please download it again and use the new nfo-thumb file instead of old one. There was a bug which prevented some files from being thumbnailed.

---

### Post by recover89 on 2006-02-05
Hi!
Great nfoviewer!
I've made an nfoviewer as well, but it was in Windows, and it was suprisingly called called nfoViewer, with the uppcase V :-D
Anyway, I would like to request a feature, it would be nice if URLs could be hyperlinked. :cool:
Thanks once again :)

---

### Post by ow50 on 2006-02-05
[QUOTE=recover89]Anyway, I would like to request a feature, it would be nice if URLs could be hyperlinked.[/QUOTE]
Done. This added two new settings: BROWSER and URL_COLOR. I chose not to change the mouse pointer when hovering over an URL, because that is quite slow. Just click with the caret pointer and the URL should open. BROWSER defaults to "gnome-open" which should pick up your default GNOME browser. You can change it "firefox" or whatever you like. Hope it works.

Other changes since the last time I posted in this thread:
* Control+W closes window
* Down and up arrows work for scrolling

[http://koti.mbnet.fi/~ots/scripts/nfoview](http://koti.mbnet.fi/~ots/scripts/nfoview)

---

### Post by skatedawe on 2006-03-25
I've trid , but i can't get it to run. 

 How is the process of making the script running and getting the program to pop-up? I CTRL + C / CTRL + V to a file name nfoview in like /home/skatedawe/nfoview/nfoview . Then i chmoded it to 777. When i graphically clicked on it nothing happens after gnome "run". Totally silence...

 What now?  ](*,)

---

### Post by ow50 on 2006-03-26
[QUOTE=skatedawe]I've trid , but i can't get it to run.[/QUOTE]
You don't run nfoview by itself. It's not an application where you'd get to open a file with an open dialog. It's just a script where you'll need to give the NFO file as an argument.

At the command line
```
/home/skatedawe/nfoview/nfoview /path/to/some/nfofile.nfo
```
To be able to double-click NFO files in your filebrowser, follow the instructions in the first post.

---

### Post by skatedawe on 2006-03-26
I know, thx anyway.

 hmm. I've followed the guide on the first steps, the others i don't care about...

 To my problem;

 Bash cannot find the command to start "nfoview", the line in my .bash_profile where the problem should be is this;

 ```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then 
    export PATH=~/bin:"${PATH}" 

fi
```

 I have a folder ~/bin (the script is laying in the folder too) and it doesnt work... But if i type this at the terminal;
   
```
export PATH="${HOME}/bin:${PATH}"
```

 It starts.. :)

 But how can i fix it so that bash recognize it when i start up a new terminal. :confused: 

 I've add a new line at the bottom with,  export PATH="${HOME}/bin:${PATH}"
 at /etc/profile . 
 
 It doesnt seems to work in any way. I've restarted X, but it shouldnt be something with that. plz help.

---

### Post by ow50 on 2006-03-26
I have in my ~/.bashrc
```
export PATH=$PATH:~/bin
```
After changing that all you need to do is start a new gnome-terminal and it should work.

---

### Post by skatedawe on 2006-03-26
yeah, that made it.

 Thank you so much. Gl with this project , if there is anything left to do.
 
 To have some packages for this "program" would be very nice! :)

---

### Post by mucha on 2006-04-03
I got this dialog everytime i want to open a nfofile, and simply doubleclick on it. Is there a way to remove this?

[IMG]http://www.astmatic.net/screen-nfoview.png[/IMG]

---

### Post by ow50 on 2006-04-03
[QUOTE=mucha]I got this dialog everytime i want to open a nfofile, and simply doubleclick on it. Is there a way to remove this?[/QUOTE]
You have probably copied the NFO file from your windows partition or then you have acquired it in a package packed on Windows. This would cause the NFO file to have execute permissions, which is not right. So, change the file permissions and the dialog will go away. If you don't want to see the dialog for executable files either, there's a setting in the Nautilus preferences dialog.

---

### Post by mucha on 2006-04-03
Thanks that did it :)

---

### Post by graigsmith on 2006-04-06
also if you just download the font, you can set gedit's font to that, and nfo files work perfectly.

---

### Post by Nitemare on 2006-09-03
EXCELENT application and EXCELENT tutorial, thank you very much (I learned things about mimetype that I didn't know)
Thank you again, good work!

---

### Post by notch on 2006-09-28
The download link for the nfoview script is broken. Could someone please post a working one.

---

### Post by Tyler Oderkirk on 2006-09-28
Here's a working link to the script: [http://users.tkk.fi/~otsaloma/scripts/nfoview]("http://users.tkk.fi/~otsaloma/scripts/nfoview")

The old URL was [http://koti.mbnet.fi/~ots/scripts/nfoview](http://koti.mbnet.fi/~ots/scripts/nfoview) In case anyone is curious how I found it...

First I tried looking in 
[http://koti.mbnet.fi/~ots/scripts/](http://koti.mbnet.fi/~ots/scripts/) 
Nothing there so I tried 
[http://koti.mbnet.fi/~ots/](http://koti.mbnet.fi/~ots/) which had a README file which pointed to the new site.

BTW you can find all kinds of interesting things by "climbing" up a directory tree.

---

### Post by ow50 on 2006-09-30
I relocated the script as my koti.mbnet.fi web space will probably disappear soon.

I have cleaned up the code for nfoview and made it use a configuration file, ~/.nfoview. By default the configuration file looks like
```
bg_color=#ffffff
browser=gnome-open
fg_color=#000000
font=Lucida ConsoleP,monospace 9
icon=gnome-status
url_color=#0000ff
vurl_color=#ff00ff
```
Note that the icon uses just a name, like desktop files. A path won't be accepted. The font is a font string, documented [here](http://www.pygtk.org/pygtk2reference/class-pangofontdescription.html#constructor-pangofontdescription).

There's a version number in the script. I just bumped it to 0.1.1 for adding "monospace" as a backup font in the default configuration.

---

### Post by ow50 on 2006-09-30
Because of using a configuration file, a minimalist can consider NFOview now an application instead of a script. I'll probably evetually register a project at [Gna!](http://gna.org/) and release it on a wider scale. That would also make debian packaging quite easy.

---

### Post by skatedawe on 2006-11-22
It would be great and i think many would be very glad.

I had the old script i think, cause it didnt work with amd64, but now it works.

Maybe my script is old. I hope you edit your first post whenever you are updating it, if. 

thanks for your work anyways.

---

### Post by tee2 on 2006-11-28
mega bump lol

I'm trying to configure the mime types but I'm stuck.

Apparently ~/.local/share/mime/packages/Override.xml doesn't exist nor does the directory its supposed to reside in. I see that this thread was made during a previous version of Ubuntu so I guess things have changed in Ubuntu since then. Where is the file that I need to edit?

---

### Post by tee2 on 2006-11-29
bump

---

### Post by tee2 on 2006-11-30
bump, help please.

---

### Post by pavel_kbc on 2006-12-01
can you plesae post for 6.10 edgy?

---

### Post by tee2 on 2006-12-02
bump

---

### Post by tee2 on 2006-12-02
bump

---

### Post by cor2y on 2006-12-12
Ok for those struggling with this in Dapper what you need to do is manually create the folders where the xml file is supposed to be then with gedit paste in the commands from the tutorial and save.
So with Nautilus Ctrl+H to show hidden files find your way to the .local folder in your home directory  then navigate through creating new folders where necessary.
And thats then solved.

---

### Post by MattiJ on 2007-03-30
I love it! plz make a package

---

### Post by KaroSHiv0n on 2007-04-23
Just wanted to say thank you for this! i have been looking for a nfo viewer ever since i moved to linux, i think i now officially have *everything* i need :)

---

### Post by alaswat on 2007-05-05
Love it, but ma thumbnails view as like with waves, but no problem!
before knowing that script i've been seeing the .nfo making
```

cat name-of-file.nfo

```
with western IBM charset encoding, but better this way

---

### Post by ow50 on 2007-08-15
> **ow50 said:**
> I'll probably evetually register a project at [Gna!](http://gna.org/) and release it on a wider scale. That would also make debian packaging quite easy.
...almost a year later:
[http://home.gna.org/nfoview/](http://home.gna.org/nfoview/)

If you followed this HOWTO, you may need to unfollow it. The mime-type is now text/x-nfo instead of text/x-extension-nfo.

---

### Post by cor2y on 2007-10-21
A bit late and dollar short but thanks for the update and also does it support thumbnails now?

---

### Post by taisao on 2007-11-02
how do I change the background and foreground color?
I have tried going to this section and change the hex color code but it doesn't take effect:
_nfoview_ file
```
class conf(object):

    """Configuration variables."""

    background_color = "#000000"
    browser = ""
    font = "Andale Mono,monospace 9"
    foreground_color = "#ffffff"
    pixels_above_lines = -1
    pixels_below_lines = 0
    url_color = "#0000ff"
    visited_url_color = "#ff00ff"
```

and is it possible to give this application a icon, when right clicking a nfo file I see the option *open with nfoview* with just a blank icon (default) which doesn't looks good.

---

### Post by Dirty Ole on 2007-11-05
> **taisao said:**
> how do I change the background and foreground color?
I have tried going to this section and change the hex color code but it doesn't take effect:
_nfoview_ file
```
class conf(object):

    """Configuration variables."""

    background_color = "#000000"
    browser = ""
    font = "Andale Mono,monospace 9"
    foreground_color = "#ffffff"
    pixels_above_lines = -1
    pixels_below_lines = 0
    url_color = "#0000ff"
    visited_url_color = "#ff00ff"
```

and is it possible to give this application a icon, when right clicking a nfo file I see the option *open with nfoview* with just a blank icon (default) which doesn't looks good.

Install it with the script provided in the package from the website. NFO Viewer then shows up in the 'Open With' Dialog with an icon (a bulb).

---

### Post by jdarias on 2008-02-01
Hello. Been having a lot of trouble with the installation of 1.1 in gutsy.
The installer creates two files called 
nfoview.desktop.in
nfoview.xml.in 

But it fails because it looks for 
nfoview.desktop
nfoview.xml

renaming these files work, but then again, this message appears:
```

updating mime database in '/usr/share/mime'
* Error in type 'text/x-nfo'
*   (in /usr/share/mime/packages/nfoview.xml):
*   Unknown freedesktop.org field '_comment'.

```
Is this release broken?

---

### Post by dustoashes on 2008-04-20
I'm pretty new to Ubuntu and I would need help with installing the tar.gz I've downloaded from the site. I don't quite understand the install document... :oops:

---

### Post by Gfy on 2008-10-02
I use these steps to install nfoview on Mint 5 or Ubuntu 8.04.

Download the tar from the website and extract it:

```
tar -xzvf nfoview-1.2.tar.gz
cd nfoview-1.2/
```

Make sure you have the necessary packages installed:

```
sudo apt-get install python gettext intltool xfonts-terminus xfonts-terminus-oblique
```

Install nfoview:

```
sudo ./setup.py install
```

Probably you get these errors:

running install
running build
running build_py
running build_scripts
running install_lib
Traceback (most recent call last):
  File "./setup.py", line 235, in <module>
    "sdist_gna": SDistGna,},)
  File "/usr/lib/python2.5/distutils/core.py", line 151, in setup
    dist.run_commands()
  File "/usr/lib/python2.5/distutils/dist.py", line 974, in run_commands
    self.run_command(cmd)
  File "/usr/lib/python2.5/distutils/dist.py", line 994, in run_command
    cmd_obj.run()
  File "./setup.py", line 84, in run
    install.run(self)
  File "/usr/lib/python2.5/distutils/command/install.py", line 510, in run
    self.run_command(cmd_name)
  File "/usr/lib/python2.5/distutils/cmd.py", line 333, in run_command
    self.distribution.run_command(command)
  File "/usr/lib/python2.5/distutils/dist.py", line 994, in run_command
    cmd_obj.run()
  File "/usr/lib/python2.5/distutils/command/install_lib.py", line 95, in run
    outfiles = self.install()
  File "./setup.py", line 153, in install
    assert text.count(string) == 1
AssertionError

Edit the setup file to uncomment the failed asserts.

```
vim ./setup.py
type :153
type i
type #
type :156
type i
type #
press Esc
type :wq
```

Install nfoview:

```
sudo ./setup.py install
```

Right click an nfo file and choose Open With -> Open with Other Application
Use a custom command: nfoview

Set font size to Terminus 8 and the color scheme to White on Black.

---

### Post by Clancy_s on 2009-01-14
> **Gfy said:**
> I use these steps to install nfoview on Mint 5 or Ubuntu 8.04.

Thanks, I used your guide with one minor change to install it on Ubuntu 8.10 (64 bit): the current nfo is 1.2.**1** so I added the .1 to the end of all the nfo names.

Install ran with no errors and .nfo viewer now appears as the default on my 'open with' menu for .nfo files. :)

---

### Post by Voorhees1979 on 2009-01-16
I dont see the point of this. You just double click an nfo file and it will open anyway.

---

### Post by quadrispro on 2009-03-17
nfoview will be available for Ubuntu 9.04

[http://packages.ubuntu.com/jaunty/nfoview](http://packages.ubuntu.com/jaunty/nfoview)

---

### Post by binbash on 2009-03-17
> **Voorhees1979 said:**
> I dont see the point of this. You just double click an nfo file and it will open anyway.

Yah i agree

---

### Post by Jaymoon on 2009-05-04
a simple:

```
sudo apt-get install nfoview
```

does the trick now...

(Using Ubuntu 9.04)

---

### Post by razor101 on 2010-11-14
> **Jaymoon said:**
> a simple:

```
sudo apt-get install nfoview
```

does the trick now...

(Using Ubuntu 9.04)

Yeah, same, with Ubuntu 10.10 - and even through the Ubuntu Software Center now... :)

---

