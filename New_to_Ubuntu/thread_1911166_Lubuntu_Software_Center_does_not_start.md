---
title: "Lubuntu Software Center does not start"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by FFabian on 2012-01-18
Hi

I just installed Lubuntu 11.10 (from an USB stick I made with unetbootin) and installed the LSC using the instructions in the One Stop Thread. Unfortunately it does not start when clicking on the icon in the menu. Then I followed [_these_]("https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds") instructions in the wiki (start via terminal, weird errors, rm -r /home/youruser/.config/lsc ) but it doesn't help. 

FYI thats the code the terminal shows when starting lsc:

```
fabian@fabian-meenee:~$ lubuntu-software-center

(lubuntu-software-center:4118): Gtk-WARNING **: Theme parsing error: gtk-buttons.css:159:10: Expected valid border

(lubuntu-software-center:4118): Gtk-WARNING **: Theme parsing error: gtk-bars.css:102:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:4118): Gtk-WARNING **: Theme parsing error: gtk-bars.css:117:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:4118): Gtk-WARNING **: Theme parsing error: gtk-bars.css:134:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:4118): Gtk-WARNING **: Theme parsing error: gtk-bars.css:153:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:4118): Gtk-WARNING **: Theme parsing error: gtk-bars.css:165:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:4118): Gtk-WARNING **: Theme parsing error: gtk-bars.css:175:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:4118): Gtk-WARNING **: Theme parsing error: gtk-bars.css:186:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:4118): Gtk-WARNING **: Theme parsing error: gtk-bars.css:198:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:4118): Gtk-WARNING **: Theme parsing error: gtk-bars.css:208:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:4118): Gtk-WARNING **: Theme parsing error: gtk-bars.css:218:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:4118): Gtk-WARNING **: Theme parsing error: gtk-bars.css:223:16: Themeing engine 'adwaita' not found

(lubuntu-software-center:4118): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
Opening config file
Traceback (most recent call last):
  File "/usr/bin/lubuntu-software-center", line 35, in <module>
    mainfunc()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 671, in lscmain
    app = LscControl()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 49, in __init__
    self.ui = UI.Gui(self.on_selected_category, threadingops.get_categories())
  File "/usr/lib/python2.7/dist-packages/LSC/threadingops.py", line 85, in get_categories
    cat_parser.readfp(cat)
  File "/usr/lib/python2.7/ConfigParser.py", line 316, in readfp
    self._read(fp, filename)
  File "/usr/lib/python2.7/ConfigParser.py", line 471, in _read
    line = fp.readline()
AttributeError: 'bool' object has no attribute 'readline'
```



Is there something I could do now?

Thanks

---

### Post by Rex Bouwense on 2012-01-18
After you received these errors, you entered 
```
rm -r /home/youruser/.config/lsc
```
Then what happened?

---

### Post by FFabian on 2012-01-18
I replaced "youruser" with "fabian" (my username), so I entered:

```
rm -r /home/fabian/.config/lsc
```

There was no result as far as I can see - no output in terminal:

```
fabian@fabian-meenee:~$ rm -r /home/fabian/.config/lsc
fabian@fabian-meenee:~$
```

But he apparently deleted the folder lsc - I checked that in the file manager.

---

### Post by Rex Bouwense on 2012-01-18
Now, all you have to do according to the help instructions is to start the Lubunu Software Center from the menu or chose run and type in Lubuntu-Software-Center and it should rebuild itself.  The instructions do say that it will take a while.  Have you done that yet?

---

### Post by FFabian on 2012-01-19
Yes, same as before. Thats why I started the thread - the solution in the wiki didn't work for me. LSC does not start. Terminal shows weird errors. LSC directory gets rebuild but it does not start.

---

### Post by Rex Bouwense on 2012-01-19
Run 
```
sudo apt-get update
sudo apt-get upgrade
```
in the LXterminal

---

### Post by FFabian on 2012-01-19
Yeah! It works. After installing some updates it starts now (still producing some weird errors in terminal but who cares). 
Thanks for your help.

---

### Post by MG&amp;TL on 2012-01-19
> **FFabian said:**
> Yeah! It works now. After installing some updates it runs (still producing some weird errors in terminal but who cares)

Thanks for your help.

Yeah, sorry about this, launchpad takes ages to build, otherwise we would've got it out sooner.

LSC is still technically experimental, so if it breaks, it sohuld be back up shortly. :D

---

### Post by Rex Bouwense on 2012-01-19
> **FFabian said:**
> Yeah! It works. After installing some updates it starts now (still producing some weird errors in terminal but who cares). 
Thanks for your help.
I checked my own stuff and it was a little screwed up so I updated and it was back on target.  That was why I told you to update.  Glad it worked.:popcorn:

---

