---
title: "How to search for files in Xubuntu / XFCE with just Thunar and a Bash script"
date: 2006-07-12
forum: Outdated Tutorials &amp; Tips
---

### Post by lapsey on 2006-07-12
[SIZE="4"]The preferred tool for searching is now Catfish.[/SIZE] Many thanks go to Kalikiana for coding it.

**v0.1 stable is now in the [Feisty Universe repository.](http://packages.ubuntu.com/feisty/utils/catfish),** so it's as simple as `sudo apt-get install catfish`. Newer versions are [here.](http://software.twotoasts.de/?page=catfish)

> **LKRaider said:**
> It searches using several backends like find, (s)locate, doodle, tracker and beagle (whichever are available).

Good thing it is light and fits perfectly on Xfce (see screenshots).


It is best integrated with thunar as a custom action, so I nicked a script from JasonValdron that will do this automatically - [download that here](http://ubuntuforums.org/attachment.php?attachmentid=29800&d=1176679051)

to install it, go to the folder you saved it in and paste the following commands.

```
chmod +x integrate-catfish.sh ; ./integrate-catfish.sh
```

dont forget to restart thunar to have it show up


-----------------------------


[SMALL]edit: deleted old solution in case of confusion[/small]

---

### Post by fridaythe14th on 2006-07-24
Cool howto! although I'm too lazy for that. :/

If you like me have switched from ubuntu to xubuntu and just want a search gui fast without any tweaking or scripting:
Install the package "gnome-utils" which includes the mentioned "gnome-search-tool". Then search from Applications -> Accessories -> Search for Files.

The package also includes the dictionary and screenshot utils from ubuntu among others.

---

### Post by mrazster on 2006-07-25
Tried it works perfectly..or *almost* perfectly.
I didn't have the uca.xml file by some reason..but I created it...and then added the last line..the one with the </actions>.
Didn't show up anything in the context menu...however when adding the search-script it self to *Thunar > Edit > Configure Custom actions* everything works great.

THNX.

---

### Post by greenstar on 2006-08-02
> **mrazster said:**
> I didn't have the uca.xml file by some reason..but I created it...and then added the last line..the one with the </actions>. Ditto.

I followed the instructions exactly and it didn't work.

I had to manually add it to *Thunar > Edit > Configure Custom actions.* Then I tried to use the search script, but the screenshot below shows that I get a Thunar window at /home/brandon instead of the search dialog as you show.



Any ideas?

Greenstar

---

### Post by lapsey on 2006-08-09
> **greenstar said:**
> Any ideas?

Sorry about that. I think this is because of missing settings in the Configure Custom Action dialog.

I have bolded the important parts.


--- *Thunar* ------------------------------
Edit > Configure Custom Actions

Edit or Add a custom action..

In tab 'Basic'..
Name: Search for Files
Description: Search this folder for files
Command: **bash ~/.bash-scripts/search-for-files %f**
Icon: /usr/share/icons/Tango/scalable/actions/search.svg

In tab 'Appearance Conditions'..
File Pattern: *****
Appears if selection contains: **Directories**
--------------------------------------------------------


This means the custom action only appears if you have selected and right-clicked a directory. When multiple folders are selected, only the first one is searched.


The "Search for Files: Look in Folder" is actually a function:
If no (existing) folder path is passed to the script, it will open a dialogue with which to select the folder to search.
This is so you can launch it independantly of a file manager (but it will still need a file manager to open the location of a found file).

---

### Post by DirtDawg on 2006-08-17
EDIT: If you don't feel like the rigamarol, you can use this quick-n-easy method, but lapsey's script works *much* better. See two posts down from this if you can't find the uca.xml file mentioned in the HowTo.

I installed the gnome-utils packages with synaptic (about 8MB for me).

Next I opened Thunar (Applications>>FileManager), then opened the command editor (Edit>>Configure Custom Actions) and added a new custom action.

I put the follwing info in the Basic Tab:
```

Name: Search for Files
Description: Start file search here
Command: gnome-search-tool --path %f
icon: /usr/share/icons/Tango/scalable/actions/search.svg

```

Then in the appearance Tab I left "File Pattern:" as "*" and left only the "Directories" box checked.

Close Thunar then start it back up. Right click on a folder to search.

---

### Post by DirtDawg on 2006-08-17
Nevermind. There's a better way to do this. See next post.

---

### Post by DirtDawg on 2006-08-17
When I followed the HowTo, I got an error that ~/.config/Thunar/uca.xml did not exist. The missing uca.xml file was located at /etc/xdg/Thunar/uca.xml instead.

If this is the case on your computer as well, use these commands:
```
 sudo cp /etc/xdg/Thunar/uca.xml /etc/xdg/Thunar/uca.xml.old 
```
then:
```
 sudo mousepad /etc/xdg/Thunar/uca.xml 
```

and follow the rest of the instructions accordingly. 

This trick is totally sweet. Thanks again lapsey!

---

### Post by LKRaider on 2006-08-18
Really great ([COLOR="LemonChiffon"]small[/COLOR]) script! :D

I am currently fiddling with it (I already translated it to my language, pt-BR) and was thinking about adding an option for using slocate instead of find (specially useful if searching on large folders).

I will post here if I can make a patch for that :)


EDIT: okay, I figured the bash scripting part... I'm just missing a way to include an option checkbox in the zenity dialog :\
(Is that even possible?)

---

### Post by lapsey on 2006-08-18
> **LKRaider said:**
> Really great ([COLOR="LemonChiffon"]small[/COLOR]) script! :D

I am currently fiddling with it (I already translated it to my language, pt-BR) and was thinking about adding an option for using slocate instead of find (specially useful if searching on large folders).

I will post here if I can make a patch for that :)


EDIT: okay, I figured the bash scripting part... I'm just missing a way to include an option checkbox in the zenity dialog :\
(Is that even possible?)

it would require another dialog, which i think would be one too many.

however.. if: slocate is faster than find and can return the same information as *find -printf* allows... then slocate should replace find :)

also, if you want to post the translation I will try to incorporate it using localisation: [http://www.tldp.org/LDP/abs/html/localization.html](http://www.tldp.org/LDP/abs/html/localization.html)

---

### Post by LKRaider on 2006-08-18
> **lapsey said:**
> it would require another dialog, which i think would be one too many.

however.. if: slocate is faster than find and can return the same information as *find -printf* allows... then slocate should replace find :)

also, if you want to post the translation I will try to incorporate it using localisation: [http://www.tldp.org/LDP/abs/html/localization.html](http://www.tldp.org/LDP/abs/html/localization.html)

Sounds like great idea, the translation :)


Meanwhile, I did a [gtkdialog]("http://linux.pte.hu/~pipas/gtkdialog/") version for me including the slocate option. Check the screenshot below.
While you can do more complex window layouts with gtkdialog, it isn't very good to work with it. I am thinking a python version would be much better then...

About slocate: the problem with it is that it relies on a database of your files that is updated only daily, so newly created files won't show up. But it is very useful for doing searches on the whole disk, for instance.
Also, it looks for the search keyword on the whole path, not only on the filename. But I guess it could be filtered somehow.

[CENTER][[img]http://img154.imageshack.us/img154/6546/screenshotfw9.th.png[/img]](http://img154.imageshack.us/my.php?image=screenshotfw9.png)[/CENTER]


Attached are the translated version of your script, and also my gtkdialog version if you want to take a look (maybe specially on the slocate function?)

---

### Post by Emanuel Felipe on 2006-09-28
Nice work.. ty ;)

---

### Post by jordoex on 2006-10-27
This should automatically be in Xubuntu, instead of having to config a script.

---

### Post by harryc on 2006-11-05
I just set this script up and it works great as user. Is there any reason why this would not work while running Thunar as root? What would change in the howto? It would be very convenient to search for a root owned file then once found you could immediately edit it with mousepad as root(for example.

---

### Post by kalikiana on 2006-11-06
Wow, the new script looks better than the first one - although I'd like to have it in one file. Is that possible? 

OR is the by any chance somebody with Gtk/C-knowledge who'd like to make this a thunar plugin? I would do it myself, but I have until now no idea how Gtk works.

---

### Post by wo.anderer on 2006-11-07
Thanks for that lapsey and DirtDawg. Works nicely. Now we just need the search box built into thunar :)

---

### Post by kalikiana on 2006-11-07
I just got a chat with an xfce developer and he said that currently Thunar won't allow a real search plugin. So we'll have to wait until the plugin interface is more complex.

---

### Post by Comendante on 2006-11-08
I followed the inscrutions but It doen't work. When I open "Search for Files" in contest menu, it's any reactions. I have Xfce 4.4 Rc1.

---

### Post by lapsey on 2006-11-25
**Bump for new version!!**



> **LKRaider said:**
> Attached are the translated version of your script, and also my gtkdialog version if you want to take a look (maybe specially on the slocate function?)

Thanks. I really would prefer a better interface than Zenity but the GTKDialog version doesn't seem to work with edgy. Python is probably a good idea but I have little time these days. 

slocate is cool but it is both too inaccurate and only adds complexity to the current interface. I would use it otherwise.

I have included your translation with the script so that you can use it, translated, straight away. Thanks a lot for that!

> **harryc said:**
> I just set this script up and it works great as user. Is there any reason why this would not work while running Thunar as root? What would change in the howto? It would be very convenient to search for a root owned file then once found you could immediately edit it with mousepad as root(for example.

No reason why not. As root is considered a different user, you will need to make the custom action again, except with the full path to the script. Maybe the command could have 'gksudo' in front of it. If the script is run with root privs (sudo search-for-files), the find command should also have root privs.
But, as it is a simple script I am aiming installation at the typical user. Something like this doesn't have to be in /bin. 
The way I see it, if you need to search for root-owned files, you will most likely know how to do all of this yourself.

> **kalikiana said:**
> I just got a chat with an xfce developer and he said that currently Thunar won't allow a real search plugin. So we'll have to wait until the plugin interface is more complex.

I look forward to that day. There is a lot of promise in Thunar , as long as it is lightweight.




> **Comendante said:**
> I followed the inscrutions but It doen't work. When I open "Search for Files" in contest menu, it's any reactions. I have Xfce 4.4 Rc1.

Try the instructions again. I hope I have made things clearer.

---

### Post by kalikiana on 2006-11-25
[COLOR="Gray"]As the new version is out, I translated it to German and Spanish. I hope that somebody will like them.

Sadly the script is not ideal, in fact you might need to remove the '@euro' from the end of the filename.[/COLOR]

EDIT: Please use the file in the newer post of mine instead.

---

### Post by lapsey on 2006-11-25
> **kalikiana said:**
> As the new version is out, I translated it to German and Spanish. I hope that somebody will like them.

Sadly the script is not ideal, in fact you might need to remove the '@euro' from the end of the filename.

Ok, I have modified the script to look for the closest equivalent language file.

If the exact locale file is not there, it will look for:
aa_AA.BBB*
aa_AA*
aa*

in that order. So if you don't have that particular variation on the language, you can use something similar that might work

an example:
if your locale is zh_TW.euctw
it will look for 'search-for-files_locale.zh_TW.euctw'
if that doesnt exist it will look for anything beginning with 'search-for-files_locale.zh_TW'
if that doesnt exist it will look for anything beginning with 'search-for-files_locale.zh' (and will match zh_CN.gbk, which may be similar enough to use)
(and of course if that doesnt exist it falls back to english)

this is because some languages, like chinese, have many different locales
> 
zh_CN
zh_CN.gb18030
zh_CN.gbk
zh_CN.utf8
zh_HK
zh_HK.utf8
zh_TW
zh_TW.euctw
zh_TW.utf8
ja_JP.eucjp
ja_JP.utf8
ko_KR.euckr
ko_KR.utf8 



I have also made other (significant) changes, which will hopefully be the last to this horrible script for some time. :P see first post

---

### Post by kalikiana on 2006-11-25
I have slightly changed the translations and shortened the filenames now that  languages are better handled.

So it's German and Spanish.

---

### Post by Wapush on 2006-11-26
Hi !

Thank you very much for your search script !
it work very well with Thunar on Debian Etch and Xfce4.

I join a French translation, fr_CA for French-Canada :)

---

### Post by neo01 on 2006-11-30
so easy and so beautiful... i am running zenwalk 4.0 and it works great on it.

thank you very much...

---

### Post by metalface on 2006-12-28
This saved me much time and annoyance in my quest to locate and transcode/re-rip the few remaining .wma files in my library. thunar was great before, and even better with this addition. Many thanks!

---

### Post by SimonJones on 2007-02-06
I am having permission problems, I write perl scripts for web sites, some are executable.

When I click on them in the search the pane they execute rather than allow editing, how can I change this?

Thanks for a great script.

---

### Post by lapsey on 2007-02-06
> **SimonJones said:**
> I am having permission problems, I write perl scripts for web sites, some are executable.

When I click on them in the search the pane they execute rather than allow editing, how can I change this?

The command *filemanager filename* is being executed, so you can either change how your filemanager deals with these files; or you can use *search-for-files -p* to cause the script to open the parent folder instead of the file itself.

---

### Post by JasonValdron on 2007-03-09
Wow! This is really neat! Absolutely what I needed!! I use it often :) Thanks :) But for the installation, if you want something easier, you can check my Thunar script: [http://ubuntuforums.org/showthread.php?t=380602](http://ubuntuforums.org/showthread.php?t=380602) I've done a little install.sh that allows us to add entry to the User Custom Actions, it isn't really hard. :)

---

### Post by nullchina on 2007-03-14
> **lapsey said:**
> Title should read: 'search-for-files: Graphical search for any Desktop Environment and File Manager (GTK required)'

This script can be run from the command line, a custom application launcher, or whatever you like.
Later I will show how to run it from Thunar, as a custom action (so you can easily right-click and search multiple directories). Personally, I have Gnome, but I prefer to use this & thunar instead of the gnome search tool & nautilus.


**new version! 0.25**

[IMG]http://i65.photobucket.com/albums/h225/lapsey/maindialog.gif[/IMG]

**Features added:**
options as script arguments
**native language support** (when translation file is in same directory)
more compatible: can limit the number of results displayed
more usable: can redraw search results (-r). note: this could be slow depending on your hardware and the number of results
more flexible: can open parent folder instead of file (-p)
more searchable: can search multiple paths 
more sortable: now can sort by date
more legible: human-readable filesize

**also!** supports regular expressions! (except for /$ and ^/ ..)
and also allows searching of root-owned directories (well, at least on my system) 


Usage: search-for-files -pr -g *WxH* -l *N* -f *filemanager* *[path1] [...] [pathN]*

[IMG]http://i65.photobucket.com/albums/h225/lapsey/results.gif[/IMG]

**A note on translation:**
A brazilian portugese locale file ( UTF-8 ) is included with the script (thanks, LKRaider!!).
If you are using this as your language then it will translate automatically. Otherwise, if you want to make your own one, it should follow the same naming convention and be in the same directory as the script. `echo $LANG` to find your locale language and encoding.



[SIZE="4"]How to set it up[/SIZE]


[click here](http://ubuntuforums.org/attachment.php?attachmentid=20008) and save the file to your home directory (~). (the file is also attached at the end of this post)

Now copy and paste the following code into the Terminal to uncompress it, store it and make it executable.
```
if ! [ -e ~/.bash-scripts ] ; then mkdir ~/.bash-scripts ; fi
tar xvjf ~/search-for-files-v0.25.tar.bz2 -C ~/.bash-scripts/
chmod a+x ~/.bash-scripts/search-for-files*

```

then we need to install zenity, which draws the dialogs:
```
sudo apt-get install zenity
```



**Now it is ready to be used.** A quick test would be to open a terminal or Alt-F2, then enter `bash ~/.bash-scripts/search-for-files -r -l 100 -f thunar` or `bash ~/.bash-scripts/search-for-files -pr -l 500 -f nautilus ~/` 





[SIZE="3"]Thunar integration[/SIZE]

*Thunar > Edit > Configure Custom actions*

Click the appropriate button at the right of the window to add a custom action

In tab 'Basic'..
Name: *Search for Files*
Description: *Search this folder for files*
Command: *bash ~/.bash-scripts/search-for-files **-r** -l **250** -f **thunar** %F*
Icon: */usr/share/icons/Tango/scalable/actions/search.svg*
You may want to change the command yourself. Here, the window is set to redraw and displayed results are limited to (a memory-friendly) 250.
[IMG]http://i65.photobucket.com/albums/h225/lapsey/find-action-basic.gif[/IMG]


In tab 'Appearance Conditions'..
File Pattern: *** 
Appears if selection contains: *Directories*
[IMG]http://i65.photobucket.com/albums/h225/lapsey/find-action-conditions.gif[/IMG]

You'll need to open a new Thunar window for the custom action to show up.

Now all you need to do is (1) select the directory(ies) you want to search, (2) enter the search string and let it run. (3) Double-clicking an item or selecting one and hitting 'OK' will (4) open up that item or its parent directory. 

another shot of how it is supposed to work:
[[IMG]http://s65.photobucket.com/albums/h225/lapsey/th_searchguide.jpg[/IMG]](http://i65.photobucket.com/albums/h225/lapsey/searchguide.jpg)
thanks very much!  a very detailed howto!

---

### Post by SurR3AL on 2007-03-19
one problem....after i run a search and get multiple results, can i select multiple files from that list and drag them to another window? in my case i've stored all the fonts i collected in windows in multiple directories based on its name. so i did a search for *.ttf with this search script. works BEAUTIFULLY :D  but i cant select all the fonts and drag them to my ~/.fonts folder. got any ideas? :) thanks!

---

### Post by lapsey on 2007-03-20
> **SurR3AL said:**
> one problem....after i run a search and get multiple results, can i select multiple files from that list and drag them to another window? in my case i've stored all the fonts i collected in windows in multiple directories based on its name. so i did a search for *.ttf with this search script. works BEAUTIFULLY :D  but i cant select all the fonts and drag them to my ~/.fonts folder. got any ideas? :) thanks!

I'm afraid the app only lets you open the item or parent folder of the item, it is not integrated with the environment.

[kalikiana's beagle front end might allow you to do this, though.](http://software.twotoasts.de/?page=catfish)

Alternatively, you can always run this:

cd "the root of the windows fonts folder"
find -type f -name '*.ttf' | while read x; do mv $x ~/.fonts ; done

i advise you make a test folder first, though :)

---

### Post by LKRaider on 2007-03-24
People, check out [CatFish]("http://software.twotoasts.de/?page=catfish"). It searches using several backends like find, (s)locate, doodle, tracker and beagle (whichever are available).

Good thing it is light and fits perfectly on Xfce (see screenshots).

You can download an easily installable deb package from [GetDeb.net]("http://www.getdeb.net/app.php?name=catfish").

---

### Post by lapsey on 2007-04-15
> **LKRaider said:**
> People, check out [CatFish]("http://software.twotoasts.de/?page=catfish"). It searches using several backends like find, (s)locate, doodle, tracker and beagle (whichever are available).

Good thing it is light and fits perfectly on Xfce (see screenshots).

You can download an easily installable deb package from [GetDeb.net]("http://www.getdeb.net/app.php?name=catfish").

Agreed. v0.1 stable is in the feisty repos, so there is no reason not to now.


Attaching integration script for catfish: 

```
chmod +x integrate-catfish.sh ; ./integrate-catfish.sh
```

to run it

---

### Post by ptipton on 2007-05-16
When I run the integrate-catfish script I get the following message:
Cannot found uca.xml, please configure UCA, in Thunar. [Click Edit, Configure custom actions..., OK] or create it manually!
relative newbie and dont understand what to do here. 
Running Feisty Xubuntu
Thanks

---

### Post by ugm6hr on 2007-05-18
This is brilliant.  Thunar should come with a search function like this as a default in Xubuntu!

EDIT:
Catfish: newer .deb version (0.3a currently) available from [http://www.getdeb.net/search.php?keywords=catfish](http://www.getdeb.net/search.php?keywords=catfish)
This just needs double-click to install...

No need for integrate script either - easy enough to add manually with command (as Custom Action):
usr/bin/catfish --fileman=thunar --path=%f --hidden --method=find
Appear if: Directories / File pattern: *

---

### Post by joyride76 on 2007-09-06
Really Thanks you! 

From Italy....

Stefano

---

### Post by santiagoward2000 on 2007-12-13
Hi! Thank you for this!
Is there any way to get v.0.3 for Gusty? The link only has versions for Feisty. Do they work on Gusty?

---

### Post by Bwangster12 on 2007-12-13
I am not too familar with Xubuntu...

But I have the script on my desktop, Catfish installed... and when I enter the command into the Terminal, I get the following:

Checking for /home/USERNAME/.config/Thunar/uca.xml.....
Integrating Catfish into Thunar.....

Then I restart the laptop and/or check Thunar and don't notice anything.

---

### Post by santiagoward2000 on 2007-12-13
> **Bwangster12 said:**
> I am not too familar with Xubuntu...

But I have the script on my desktop, Catfish installed... and when I enter the command into the Terminal, I get the following:

Checking for /home/USERNAME/.config/Thunar/uca.xml.....
Integrating Catfish into Thunar.....

Then I restart the laptop and/or check Thunar and don't notice anything.

Hi!
You should get a **Search** option when you right-click a folder on thunar. Don't you get that?

---

### Post by Bwangster12 on 2007-12-13
Oh okay... well that was weird.  I guess it just need a computer restart or something.  It is working now.

Very cool.

---

### Post by fox-out on 2008-01-05
Catfish rules with Thunar. It's really useful! I hope developers of Thunar and Xubuntu will take care of File Searching in next releases. May be in Ubuntu 9.30 or 15.20...
Thank you!

---

### Post by feistybird on 2008-07-12
First of all, Thanks so much for the script, this is really useful!

I wonder if it is possible to make a custom actions that can 'Copy file path' (similar to 'copy link location' in firefox, that is when you right click on a file in Thunar, click 'copy file path', and the file path will be copied to the clipboard, so that I can paste the path such as '/usr/share/icons/xxx/xxx.svg' to my .desktop files.

---

### Post by Marran77 on 2008-07-31
Just want to say thanks... Very useful

---

### Post by glantucan on 2008-08-15
> **LKRaider said:**
> Sounds like great idea, the translation :)


Meanwhile, I did a [gtkdialog]("http://linux.pte.hu/~pipas/gtkdialog/") version for me including the slocate option. 

I know this is off topic but I'm sort of desperate to find  a good tutorial, howto, manual, forum about gtkdialog. Do you know of any?. 
I'm aware of:
[http://forum.goblinx.com.br/viewtopic.php?p=3418#3418](http://forum.goblinx.com.br/viewtopic.php?p=3418#3418)  which not complete and for event driven script (which don't work on my system because of a no solved bug)
Googling for hours did not show too much, just found some examples.
Any help appreciated

Thanks

---

### Post by the-larch on 2008-10-04
I keep getting Permission denied when I try to run this line and I don't know why. I add "sudo" before it.

```
chmod +x integrate-catfish.sh ; ./integrate-catfish.sh
```

---

### Post by WorkerSrb on 2010-09-10
Thank you my friend for this wonderful tutorial. It helped me a lot in daily file searches. Big thx!

---

