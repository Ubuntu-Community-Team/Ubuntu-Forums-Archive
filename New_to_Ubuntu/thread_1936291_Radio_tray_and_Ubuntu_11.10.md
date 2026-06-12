---
title: "Radio tray and Ubuntu 11.10"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by Warrenstreet on 2012-03-05
Hi all,

First post on here, but have been reading with interest for a while now.

I have installed Radio Tray but the app seems not to lunch. The icon on the app tray flashes for a few seconds after clicking it, but the application does not load

This is the result of radiotray &
Any clues?

Thanks
WS

warrenstreet@Theultimatelaptop:~$ radiotray &
[1] 5606
warrenstreet@Theultimatelaptop:~$ Loading configuration...
/home/warrenstreet/.local/share/radiotray/bookmarks.xml
/home/warrenstreet/.local/share/radiotray/config.xml
/usr/share/radiotray/config.xml
Traceback (most recent call last):
  File "/usr/bin/radiotray", line 15, in <module>
    radiotray.main(sys.argv[1:])
  File "/usr/lib/python2.7/dist-packages/radiotray/radiotray.py", line 37, in main
    RadioTray()
  File "/usr/lib/python2.7/dist-packages/radiotray/RadioTray.py", line 53, in __init__
    self.cfg_provider.loadFromFile()
  File "/usr/lib/python2.7/dist-packages/radiotray/XmlConfigProvider.py", line 35, in loadFromFile
    self.root = etree.parse(self.filename).getroot()
  File "lxml.etree.pyx", line 2942, in lxml.etree.parse (src/lxml/lxml.etree.c:54187)
  File "parser.pxi", line 1528, in lxml.etree._parseDocument (src/lxml/lxml.etree.c:79485)
  File "parser.pxi", line 1557, in lxml.etree._parseDocumentFromURL (src/lxml/lxml.etree.c:79768)
  File "parser.pxi", line 1457, in lxml.etree._parseDocFromFile (src/lxml/lxml.etree.c:78843)
  File "parser.pxi", line 997, in lxml.etree._BaseParser._parseDocFromFile (src/lxml/lxml.etree.c:75698)
  File "parser.pxi", line 564, in lxml.etree._ParserContext._handleParseResultDoc (src/lxml/lxml.etree.c:71739)
  File "parser.pxi", line 645, in lxml.etree._handleParseResult (src/lxml/lxml.etree.c:72614)
  File "parser.pxi", line 585, in lxml.etree._raiseParseError (src/lxml/lxml.etree.c:71955)
lxml.etree.XMLSyntaxError: Document is empty, line 1, column 1
^C
[1]+  Exit 1                  radiotray

---

### Post by ron999 on 2012-03-05
Hi
Look for the file "**config.xml**".
It is in here:-
/home/warrenstreet/.local/share/radiotray/config.xml

Rename the file "**config.xml.bak**".
Then launch radiotray (it should create a new version of config.xml file).
You may need to be root, so might need to use "gksudo nautilus" to rename that file.

---

### Post by Warrenstreet on 2012-03-06
I deleted the two files...
Result is below, which looks ok, but the app still does not start.
Any clues?


warrenstreet@Theultimatelaptop:~$ radiotray &
[1] 2592
warrenstreet@Theultimatelaptop:~$ Loading configuration...
/home/warrenstreet/.local/share/radiotray/bookmarks.xml
/home/warrenstreet/.local/share/radiotray/config.xml
/usr/share/radiotray/config.xml
PLS playlist decoder
M3U playlist decoder
ASX-familiy playlist decoder
XSPF playlist decoder
ASF playlist decoder
RAM playlist decoder
Using url timeout = 100

---

### Post by ron999 on 2012-03-06
> **Warrenstreet said:**
> ...which looks ok...

Yes, that's the correct response.:D
In my case it puts the radiotray icon/launcher on my top panel too.
Find out if your icon/launcher is being put somewhere that you can't see it.

---

### Post by Warrenstreet on 2012-03-06
Bho...
I cannot find it. I looks like it does not load it.
Is there any sort of task manager in ubuntu to see if the app is running?

---

### Post by ron999 on 2012-03-06
> **Warrenstreet said:**
> 
Is there any sort of task manager in ubuntu to see if the app is running?
Mine is "System Monitor".
Correct name is "gnome-system-monitor".

Command is:-
```
gnome-system-monitor
```

If you're not winning...
Uninstall radiotray
and 
Delete radiotray folder from /home/warrenstreet/.local/share/radiotray
Then install radiotray-v**0.7.2** deb from the website here ---> [http://radiotray.sourceforge.net/]("http://radiotray.sourceforge.net/")

---

### Post by Warrenstreet on 2012-03-07
Done, but the app still does not load!
I checked the system monitor

There is a radio tray process, it is sleeping and the waiting channel is poll_schedule_timeout

???

---

### Post by ron999 on 2012-03-07
Will v-0.7.2 play a station from command line:-
```
radiotray http://stream-sd.radioparadise.com:9000/rp_192.ogg
```

---

### Post by Warrenstreet on 2012-03-07
I can hear the live stream
I can also see the process, still in sleeping mode, in system monitor...

---

### Post by ron999 on 2012-03-07
> **Warrenstreet said:**
> 
I can also see the process, still in sleeping mode, in system monitor...
That's correct.:)
Now you need to hunt the icon/launcher.:D

---

### Post by Warrenstreet on 2012-03-07
I cannot find it, am I going nuts?

---

### Post by ron999 on 2012-03-07
> **Warrenstreet said:**
> I cannot find it
Top right-hand corner with my old-school Gnome desktop.

---

### Post by Warrenstreet on 2012-03-07
Switched to gnome 2 desktop, icon found!
Thanks a bunch!
WS

---

### Post by ron999 on 2012-03-07
Hi
It's a problem that RadioTray has with Unity desktop.
There's information out on Google.
It seems with Unity you need to edit the config.xml file (and save).
Change this:-
```
<option name="enable_application_indicator_support" value="false"/>
```
To this:-
```
<option name="enable_application_indicator_support" value="appindicator"/>
```

---

