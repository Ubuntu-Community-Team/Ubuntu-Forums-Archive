---
title: "[SOLVED] Applications Menu Is GONE!"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by noorez on 2008-10-12
HELP!

My applications menu seems to have disappeared! When I click on the applications button nothing comes up. The places and System menu are still there.

I believe this happened after I right-clicked and selected edit-menus. After nothing came up I opened terminal and typed alacarte and got this result:

/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

After seeing this I tried to click on the Applications menu to see it and nothing came up.

Anyone know what to do?!!

---

### Post by aeiah on 2008-10-12
first thing to do is to see if you can just re-add the menu. right click on your panel, select 'Add to Panel...' and select it from the list. either the menu bar or main menu items. drag it to somewhere on your panel and see if that one works.

---

### Post by aeiah on 2008-10-12
if that doesnt work (which it probably wont), then navigate to your applications.menu config file and have a look at it. in nautilus, go to your home directory, show hidden files and folders (by pressing ctrl+h) and go to .config/menus/ and see whats there. you should see applications.menu and also some aplications.menu.undo-## files. the one with the greatest number is the most recent. you could either:

1. compare applications.menu and applications.menu.undo-## manually, see what's corrupted in applications.menu and type it out

2. simply overwrite applications.menu with one of the undo files. the undo files may be out of date though because it doesnt seem to be a true backup of changes or anything.

either way, be sure to backup your applications.menu file just in case.

you could also copy and paste your applications.menu file here and someone might be able to spot what is corrupted and rebuild it for you

---

### Post by noorez on 2008-10-12
The applications.menu is empty.....0 bytes......
and there is no other applications menu undo files...

---

### Post by aeiah on 2008-10-12
oh dear :p

perhaps someone who has a relativley new install (mine has all kinds of **** on it) will be able to post theirs, or you could grab one off your installation cd.

if you want to try using mine, here it is:
```

<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>System</Name>
		<Include>
			<Filename>gconf-editor.desktop</Filename>
		</Include>
		<AppDir>/home/USERNAME/.local/share/applications</AppDir>
		<Include>
			<Filename>gdmflexiserver.desktop</Filename>
		</Include>
		<Include>
			<Filename>alacarte-made-3.desktop</Filename>
		</Include>
		<Exclude>
			<Filename>ubuntu-tweak.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>kde-konsole.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>automatix2.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>kde-yakuake.desktop</Filename>
		</Exclude>
	</Menu>
	<Menu>
		<Name>Accessories</Name>
		<Include>
			<Filename>file-roller.desktop</Filename>
		</Include>
		<AppDir>/home/USERNAME/.local/share/applications</AppDir>
		<Exclude>
			<Filename>avant-window-navigator.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>tilda.desktop</Filename>
		</Exclude>
	</Menu>
	<Menu>
		<Name>Internet</Name>
		<Exclude>
			<Filename>tsclient.desktop</Filename>
		</Exclude>
		<AppDir>/home/USERNAME/.local/share/applications</AppDir>
		<Exclude>
			<Filename>evolution-mail.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>nmapfe.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>sun-java6-javaws.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>ekiga.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>mldonkey-gui.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>skype.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>transmission.desktop</Filename>
		</Exclude>
	</Menu>
	<Menu>
		<Name>Multimedia</Name>
		<Exclude>
			<Filename>totem.desktop</Filename>
		</Exclude>
		<AppDir>/home/USERNAME/.local/share/applications</AppDir>
		<Exclude>
			<Filename>rhythmbox.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>gnome-sound-recorder.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>xcdroast.desktop</Filename>
		</Exclude>
		<Include>
			<Filename>gnome-volume-control.desktop</Filename>
		</Include>
		<Include>
			<Filename>alacarte-made.desktop</Filename>
		</Include>
		<Exclude>
			<Filename>dvdshrink.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>elisa.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>gxine.desktop</Filename>
		</Exclude>
		<Include>
			<Filename>mandvd.desktop</Filename>
		</Include>
		<Exclude>
			<Filename>winff.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>xine.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>xvidcap.desktop</Filename>
		</Exclude>
		<Include>
			<Filename>alacarte-made-6.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Development</Name>
		<Include>
			<Filename>python2.5.desktop</Filename>
		</Include>
		<AppDir>/home/USERNAME/.local/share/applications</AppDir>
		<Include>
			<Filename>alacarte-made-5.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>Other</Name>
		<Exclude>
			<Filename>kde-khotkeys.desktop</Filename>
		</Exclude>
		<AppDir>/home/USERNAME/.local/share/applications</AppDir>
		<Exclude>
			<Filename>kde-keyboard.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>kde-keyboard_layout.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>gnome-screensaver-lock.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>gnome-session-kill.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>Keyboard.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>Keyboard Layout.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>doom3.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>doom3-dedicated.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>Search.desktop</Filename>
		</Exclude>
	</Menu>
	<Menu>
		<Name>Games</Name>
		<Include>
			<Filename>alacarte-made-1.desktop</Filename>
		</Include>
		<Exclude>
			<Filename>gnotravex.desktop</Filename>
		</Exclude>
		<AppDir>/home/USERNAME/.local/share/applications</AppDir>
		<Exclude>
			<Filename>gtali.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>gnobots2.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>gnibbles.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>gnotski.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>iagno.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>glines.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>dreamchess-fullscreen.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>glchess.desktop</Filename>
		</Exclude>
		<Include>
			<Filename>alacarte-made-2.desktop</Filename>
		</Include>
		<Include>
			<Filename>alacarte-made-4.desktop</Filename>
		</Include>
		<Exclude>
			<Filename>gnomine.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>blackjack.desktop</Filename>
		</Exclude>
		<Exclude>
			<Filename>sol.desktop</Filename>
		</Exclude>
		<Include>
			<Filename>freecell.desktop</Filename>
		</Include>
		<Include>
			<Filename>alacarte-made-7.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>wine-wine</Name>
		<Menu>
			<Name>wine-Programs</Name>
			<DirectoryDir>/home/USERNAME/.local/share/desktop-directories</DirectoryDir>
		</Menu>
	</Menu>
</Menu>

```

be sure to do a 'find and replace' and replace 'USERNAME' with your username. it occurs 8 times but its best to just do it automatically with gedit

---

### Post by noorez on 2008-10-12
Solved problem. Can't believe I didn't see it before....the answer came to me when u mentioned fresh install...

I created a new temp user and I copied over their applications.menu over my own and I got the menu back!!

---

### Post by aeiah on 2008-10-12
aha! so simple. glad i got you on the right track.

---

