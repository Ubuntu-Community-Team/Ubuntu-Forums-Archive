---
title: "[SOLVED] Gedit:  Ctrl-F doesn't invoke search."
date: 2008-07-13
forum: New to Ubuntu
---

### Post by freak42 on 2008-07-13
Hello

I have a strange problem. Gedit stopped accepting the shortcut ctrl-f to open a search box to search text. In the menu (Search->Find) the shortcut is not present anymore, however other shortcuts seem unaffected and also work.

Unfortunately I don't know when this change happened, it used to work before. I also do not recall changing any settings related to gedit.

My System is Ubuntu 8.04, Gedit 2.22.3

Any help is appreciated.

---

### Post by kestrel1 on 2008-07-13
Do you still have find on the tool bar?

---

### Post by freak42 on 2008-07-13
> **kestrel1 said:**
> Do you still have find on the tool bar?

Yes, it is still on the toolbar.

---

### Post by kestrel1 on 2008-07-13
Does the toolbar version work?

---

### Post by freak42 on 2008-07-13
> **kestrel1 said:**
> Does the toolbar version work?

Yes the toolbarverison (as well as the menu version) work as usual.

I really cannot see anything different in Gedit apart from the one missing shortcut. Everything else seems absolutely normal (and working as usual).

---

### Post by kestrel1 on 2008-07-13
Don't know if this will help but you could try removing gedit & then re-installing it.
To remove type the following in a terminal:
```
sudo apt-get remove gedit
```
& to re-install type:
```
sudo apt-get install gedit
```
As I say, not sure if it will help, but might be worth trying.

---

### Post by freak42 on 2008-07-13
reinstalling gedit didn't help :-( ctrl-f is still not doing what it is supposed to.

---

### Post by kestrel1 on 2008-07-14
Sorry about that.
Does pressing CTRL + F on the desktop open up the file browser search window? & does CTRL + F work in other apps?

---

### Post by freak42 on 2008-07-14
> **kestrel1 said:**
> Sorry about that.
Does pressing CTRL + F on the desktop open up the file browser search window? & does CTRL + F work in other apps?

yes it brings up the file browser search on the desktop (hey, I didn't know about that one, TY!)

and it works as usual in other apps (eclipse, pidgin, firefox,..)

---

### Post by kestrel1 on 2008-07-14
Not sure what else to suggest at the moment. I will have a look at my system & see if anything sticks out, but I wouldn't hold your breath :)
There may be a setting in gconf-editor though. If you want to look yourself type this in a terminal:
```
gconf-editor
```
If you make any changes though, make sure you write the location down & what you changed.

---

### Post by freak42 on 2008-07-14
> **kestrel1 said:**
> Not sure what else to suggest at the moment. I will have a look at my system & see if anything sticks out, but I wouldn't hold your breath :)
There may be a setting in gconf-editor though. If you want to look yourself type this in a terminal:
```
gconf-editor
```
If you make any changes though, make sure you write the location down & what you changed.

I couldn't find a setting that seemed relevant for my problem.

Anyhow, I appreciate your help efforts.
Many thanks for your time!

and maybe... one day... ctrl-f search comes back the same way it disappeared ;-)

---

### Post by spydon on 2008-07-14
Try this then:
```
sudo apt-get remove --purge gedit
```
and then
```
sudo apt-get install gedit
```

The config file might have still been the same when you reinstalled the last time so this might work.

---

### Post by freak42 on 2008-07-14
I just came across an interesting hint.

If I invoke gedit with root rights (gksudo gedit)
then the ctrl-f search shortcut is there as nothing ever happened.

It must be a user-setting somewhere. I just don't know where :-(

---

### Post by kestrel1 on 2008-07-14
This got me thinking.
Not sure if this will work.
try to uninstall gedit as described by Spydon with the --purge option, but before re-installing go to the following folder in your home directory.
.gconf/apps/ & delete the gedit-2 folder that is there. You will need to go to View & select Show Hidden Folders or press CTRL + H when you are in your home folder to see the .gconf folder. Then try to re-install gedit & see if that does it.

---

### Post by freak42 on 2008-07-14
yes that did it.. I could literally see in the search menu that the ctrl-f shortcut behind search reappeared!

exact steps I used (for anyone with the same problem):

```

 sudo apt-get remove --purge gedit
rm -r ~/.gconf/apps/gnome-settings/gedit/
rm -r ~/.gconf/apps/gedit-2/
 sudo apt-get install gedit ubuntu-desktop

```
note: ubuntu-desktop seems to be a metapackage that depends on gedit on ubuntu, that got uninstalled when removing gedit.

Many thanks to you both for helping me solve this annoying and obscure problem!
I still have no idea how this happened in the first place.

---

### Post by kestrel1 on 2008-07-15
Glad that got you sorted. It may have been a corruption within the users gedit folder or a full purge that sorted it. Either way you got there.

---

### Post by freak42 on 2008-07-15
oh no!

I was wrong again. It is still not working as intended :-( .
I can't believe it.

ctrl-f is still not opening the search window by default.
What is happening now, is that when in the menu search -> find is highlighted (selecting withouth pressing a button) and THEN I press ctrl-f this shortcut is assigned to the command (so afterwards ctrl-f works to search; that's what I actually saw, when I said I could literally see the ctrl-f text show up in the menu).

However this is not retained across closing and reopening gedit.

It kinda looks like I can assign custom shortcuts this way in gedit (I also can assign other shortcuts for any of the menu commands this way.) However these settings are lost once it is closed again.

What is going on here?

---

### Post by kestrel1 on 2008-07-15
If you create another user, are they affected in the same way. I know you said root was OK, but I wonder if this is really user specific.

---

### Post by freak42 on 2008-07-15
kestrel,

I didn't try another user (because I don't have one (yet)), but instead I tried something else first:

I rsynched all of root's files in root's home directory. Then I opened gedit (as root) changed the search shortcut and closed gedit. Afterwards I rsynched again (using -var , with this I could see which files were changed in the meantime (I'm sure there are better ways, but it worked).

I got a list of files:
```
.recently-used.xbel
.gconf/apps/gedit-2/preferences/ui/statusbar/%gconf.xml
.gconfd/saved_state
.gnome2/accelsgedit
.gnome2/gedit-2

```

then I looked into all these files and sure enough 
.gnome2/accelsgedit looks like it keeps all the shortcuts.
Here's a snippet of it:
```
; gedit GtkAccelMap rc-file         -*- scheme -*-
; this file is an automated accelerator map dump
;
; (gtk_accel_path "<Actions>/GeditWindowActions/EditRedo" "<Shift><Control>z")
; (gtk_accel_path "<Actions>/LanguagesActions/haskell" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchGoToLine" "<Control>i")

```

and sure enough the only line that didn't start with a ; was the line 
```
(gtk_accel_path "<Actions>/GeditWindowActions/SearchFind" "<Control>f")

```

I put a ; in front of it, started gedit.. assigned the ctrl-f shortcut to search... closed... the file showed the promising line with the shortcut (as above) and sure enough wenn I reopened gedit it still worked.

So now I think this thing is really fixed for good.

**So in short for anyone browsing this thread: the shortcut settings for gedit are located in :~/.gnome2/accelsgedit**
(There is another file I found that looked similar: ~/.gnome2/accels/gedit (maybe these are the defaults, I don't know)

Many thanks again,kestrel, for your help and patience in this whole matter, it is much appreciated!

---

### Post by kestrel1 on 2008-07-16
I must admit, I looked in the .gnome2 folder but never noticed that file. A bit strange that it changed in the first place though :confused:
Still, good for you to actually sort it out yourself. Well done you =D>=D>

---

### Post by tinatinka on 2009-03-05
freak42!

got pretty much the same problem. ctrl-s happened to start the search function instead of saving the current file... while starting gedit as the root, this problem doesn't occur.

could you list all the commands that solved the problem? i'm an ubuntu beginner, not sure whether i might figure it out all by myself..

thanks

---

### Post by freak42 on 2009-03-05
Hi 

maybe you can post here the output of the file
~/.gnome2/accelsgedit


you can try this:
hit alt+F2 and type in the window
gedit ~/.gnome2/accelsgedit

then copy and paste into the ubuntu forum editor

---

### Post by yen on 2009-04-29
Hello, 
I have a similar problem. There are certain shortcuts that don't work in gedit. The most needed is the ctrl+s key. By pressing this gedit does the same when pressing ctrl+i, i.e. it opens a window GoToLine.

I've already tried everything that was proposed in this thread (except for "rsynched" since I don't know how to do it).

The accelsgedit file seems to be ok. The relevant line has no syntax errors and looks as the same as other lines. There ist also another file in folder ~/.gnome2/accels. The name ist gedit and it has the same content as accelsgedit.

The difference to other posts with similar problems is that the problem remains when I open gedit as root. Beside root there are 2 more users (a and b) on may system. The problem described here refer to one of the users (a) and to the root. I have no problems with gedit when I'm logged in as the second (b) user (which has the same rights as the a-user).

Here's the accelsgedit file:

```
; gedit GtkAccelMap rc-file         -*- scheme -*-
; this file is an automated accelerator map dump
;
; (gtk_accel_path "<Actions>/GeditWindowActions/EditRedo" "<Shift><Control>z")
; (gtk_accel_path "<Actions>/LanguagesActions/haskell" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetActionGroupToplevel/FilterMenuAction" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchGoToLine" "<Control>i")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchFindNext" "<Control>g")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSensitiveActionGroup/DirectoryOpen" "<Control>o")
; (gtk_accel_path "<Actions>/FileBrowserPluginSingleSelectionExtra/OpenTerminal" "")
; (gtk_accel_path "<Actions>/LanguagesActions/css" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FileRevert" "")
; (gtk_accel_path "<Actions>/LanguagesActions/dtd" "")
; (gtk_accel_path "<Actions>/LanguagesActions/docbook" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FilePageSetup" "")
; (gtk_accel_path "<Actions>/LanguagesActions/chdr" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Edit" "")
; (gtk_accel_path "<Actions>/LanguagesActions/eiffel" "")
; (gtk_accel_path "<Actions>/LanguagesActions/diff" "")
; (gtk_accel_path "<Actions>/LanguagesActions/awk" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/DocumentsNextDocument" "<Control><Alt>Page_Down")
; (gtk_accel_path "<Actions>/GeditWindowActions/FileCloseAll" "<Shift><Control>w")
; (gtk_accel_path "<Actions>/LanguagesActions/sql" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchFind" "<Control>f")
; (gtk_accel_path "<Actions>/LanguagesActions/scheme" "")
; (gtk_accel_path "<Actions>/GeditSpellPluginActions/ConfigSpell" "")
; (gtk_accel_path "<Actions>/LanguagesActions/libtool" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/EditCopy" "<Control>c")
; (gtk_accel_path "<Actions>/LanguagesActions/pascal" "")
; (gtk_accel_path "<Actions>/LanguagesActions/perl" "")
; (gtk_accel_path "<Actions>/LanguagesActions/vbnet" "")
; (gtk_accel_path "<Actions>/LanguagesActions/rpmspec" "")
; (gtk_accel_path "<Actions>/LanguagesActions/objc" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/EditPreferences" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FilePrintPreview" "<Shift><Control>p")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/FileOpenURI" "<Control>l")
; (gtk_accel_path "<Actions>/LanguagesActions/nemerle" "")
; (gtk_accel_path "<Actions>/LanguagesActions/forth" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FileSaveAll" "<Shift><Control>l")
; (gtk_accel_path "<Actions>/GeditWindowActions/ViewHighlightMode" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchIncrementalSearch" "<Control>k")
; (gtk_accel_path "<Actions>/GeditQuitWindowActions/FileQuit" "<Control>q")
; (gtk_accel_path "<Actions>/GeditWindowActions/FileClose" "<Control>w")
; (gtk_accel_path "<Actions>/LanguagesActions/ruby" "")
; (gtk_accel_path "<Actions>/GeditSpellPluginActions/AutoSpell" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Documents" "")
; (gtk_accel_path "<Actions>/LanguagesActions/latex" "")
; (gtk_accel_path "<Actions>/LanguagesActions/gtkrc" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/ViewSidePane" "F9")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Tools" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchFindPrevious" "<Shift><Control>g")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/View" "")
; (gtk_accel_path "<Actions>/LanguagesActions/m4" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/HelpAbout" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Help" "")
; (gtk_accel_path "<Actions>/LanguagesActions/erlang" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSensitiveActionGroup/DirectoryRefresh" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/DocumentsMoveToNewWindow" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/HelpContents" "F1")
; (gtk_accel_path "<Actions>/LanguagesActions/dpatch" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSingleMostSelectionActionGroup/DirectoryNew" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/File" "")
; (gtk_accel_path "<Actions>/LanguagesActions/vala" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetActionGroup/FilterHidden" "")
; (gtk_accel_path "<Actions>/LanguagesActions/ocl" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSingleSelectionActionGroup/FileRename" "")
; (gtk_accel_path "<Actions>/LanguagesActions/gettext-translation" "")
; (gtk_accel_path "<Actions>/LanguagesActions/xml" "")
; (gtk_accel_path "<Actions>/LanguagesActions/verilog" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/EditSelectAll" "<Control>a")
; (gtk_accel_path "<Actions>/LanguagesActions/objective-caml" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FileSaveAs" "<Shift><Control>s")
; (gtk_accel_path "<Actions>/LanguagesActions/js" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FileSave" "<Control>s")
; (gtk_accel_path "<Actions>/LanguagesActions/php" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchClearHighlight" "<Shift><Control>k")
; (gtk_accel_path "<Actions>/GeditSpellPluginActions/CheckSpell" "<Shift>F7")
; (gtk_accel_path "<Actions>/DocumentsListActions/Tab_1" "<Alt>2")
; (gtk_accel_path "<Actions>/DocumentsListActions/Tab_0" "<Alt>1")
; (gtk_accel_path "<Actions>/LanguagesActions/vhdl" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/EditDelete" "")
; (gtk_accel_path "<Actions>/LaunchpadIntegration/LaunchpadAppTranslate" "")
; (gtk_accel_path "<Actions>/LanguagesActions/idl" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/FileNew" "<Control>n")
; (gtk_accel_path "<Actions>/GeditWindowActions/DocumentsPreviousDocument" "<Control><Alt>Page_Up")
; (gtk_accel_path "<Actions>/GeditWindowActions/SearchReplace" "<Control>h")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/ViewStatusbar" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/EditUndo" "<Control>z")
; (gtk_accel_path "<Actions>/LanguagesActions/changelog" "")
; (gtk_accel_path "<Actions>/LanguagesActions/cpp" "")
; (gtk_accel_path "<Actions>/LaunchpadIntegration/LaunchpadAppBugs" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetActionGroup/FilterBinary" "")
; (gtk_accel_path "<Actions>/LanguagesActions/msil" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/ViewToolbar" "")
; (gtk_accel_path "<Actions>/LanguagesActions/java" "")
; (gtk_accel_path "<Actions>/LanguagesActions/octave" "")
; (gtk_accel_path "<Actions>/GeditDocInfoPluginActions/DocumentStatistics" "")
; (gtk_accel_path "<Actions>/LanguagesActions/ini" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSelectionActionGroup/FileMoveToTrash" "")
; (gtk_accel_path "<Actions>/LanguagesActions/haskell-literate" "")
; (gtk_accel_path "<Actions>/LanguagesActions/python" "")
; (gtk_accel_path "<Actions>/LanguagesActions/lua" "")
; (gtk_accel_path "<Actions>/LanguagesActions/boo" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/ViewBottomPane" "<Control>F9")
; (gtk_accel_path "<Actions>/LaunchpadIntegration/LaunchpadAppInfo" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSelectionActionGroup/FileDelete" "")
; (gtk_accel_path "<Actions>/LanguagesActions/r" "")
; (gtk_accel_path "<Actions>/LanguagesActions/pkgconfig" "")
; (gtk_accel_path "<Actions>/LanguagesActions/yacc" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/EditCut" "<Control>x")
; (gtk_accel_path "<Actions>/LanguagesActions/texinfo" "")
; (gtk_accel_path "<Actions>/LanguagesActions/ada" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/EditPaste" "<Control>v")
; (gtk_accel_path "<Actions>/LanguagesActions/html" "")
; (gtk_accel_path "<Actions>/FileBrowserWidgetSingleMostSelectionActionGroup/FileNew" "<Control>n")
; (gtk_accel_path "<Actions>/GeditTimePluginActions/InsertDateAndTime" "")
; (gtk_accel_path "<Actions>/LanguagesActions/d" "")
; (gtk_accel_path "<Actions>/LanguagesActions/c" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/FileOpen" "<Control>o")
; (gtk_accel_path "<Actions>/LanguagesActions/c-sharp" "")
; (gtk_accel_path "<Actions>/GeditWindowActions/FilePrint" "<Control>p")
; (gtk_accel_path "<Actions>/LanguagesActions/sh" "")
; (gtk_accel_path "<Actions>/LanguagesActions/makefile" "")
; (gtk_accel_path "<Actions>/GeditWindowAlwaysSensitiveActions/Search" "")
; (gtk_accel_path "<Actions>/LanguagesActions/tcl" "")
; (gtk_accel_path "<Actions>/LanguagesActions/gap" "")
; (gtk_accel_path "<Actions>/LanguagesActions/fortran" "")
; (gtk_accel_path "<Actions>/FileBrowserPluginExtra/SetActiveRoot" "")
; (gtk_accel_path "<Actions>/LanguagesActions/desktop" "")
```

Do you have any suggestions?

Thank you in advance, 

yen

---

### Post by freak42 on 2009-04-29
this file looks fine to me?
did you make sure to include the file from root or user a and not user b?

oh and btw... not many people might look at this thread, since it is marked as solved..

---

