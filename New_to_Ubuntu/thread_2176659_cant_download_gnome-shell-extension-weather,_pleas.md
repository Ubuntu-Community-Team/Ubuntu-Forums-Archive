---
title: "cant download gnome-shell-extension-weather, please help"
date: 2013-09-25
forum: New to Ubuntu
---

### Post by keCAtMd on 2013-09-25
Error: Requiring GWeather, version none: Typelib file for namespace 'GWeather' (any version) not found

Stack trace:
  @/usr/share/gnome-shell/extensions/weather-extension@xeked.com/prefs.js:37
  Application<._getExtensionPrefsModule@/usr/share/gnome-shell/js/extensionPrefs/main.js:84
  [email]wrapper@/usr/share/gjs-1.0/lang.js[/email]:213
  Application<._selectExtension@/usr/share/gnome-shell/js/extensionPrefs/main.js:99
  [email]wrapper@/usr/share/gjs-1.0/lang.js[/email]:213
  Application<._extensionSelected@/usr/share/gnome-shell/js/extensionPrefs/main.js:119
  [email]wrapper@/usr/share/gjs-1.0/lang.js[/email]:213
  Application<._selectExtension@/usr/share/gnome-shell/js/extensionPrefs/main.js:110
  [email]wrapper@/usr/share/gjs-1.0/lang.js[/email]:213
  Application<._extensionsLoaded@/usr/share/gnome-shell/js/extensionPrefs/main.js:219
  [email]wrapper@/usr/share/gjs-1.0/lang.js[/email]:213
  [email]_emit@/usr/share/gjs-1.0/signals.js[/email]:124
  ExtensionFinder<._extensionsLoaded@/usr/share/gnome-shell/js/misc/extensionUtils.js:178
  [email]wrapper@/usr/share/gjs-1.0/lang.js[/email]:213
  [email]done@/usr/share/gnome-shell/js/misc/fileUtils.js[/email]:33
  @/usr/share/gnome-shell/js/misc/fileUtils.js:51
  [email]onNextFileComplete@/usr/share/gnome-shell/js/misc/fileUtils.js[/email]:21
  [email]main@/usr/share/gnome-shell/js/extensionPrefs/main.js[/email]:276
  @<command line>:1
________________________

when I did :  sudo apt-repository ppa:gnome-shell-extensions
 this happned after a while.

  During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/lib/python3.3/threading.py", line 639, in _bootstrap_inner
    self.run()
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 141, in run
    self.add_ppa_signing_key(self.ppa_path)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 212, in add_ppa_signing_key
    ppa_info = get_ppa_info_from_lp(owner_name, ppa_name)
  File "/usr/lib/python3/dist-packages/softwareproperties/ppa.py", line 105, in get_ppa_info_from_lp
    import pycurl
ImportError: No module named 'pycurl'


____________

everything is up to date, and I have been able to install other extensions

thanks in advance //gustav

---

### Post by peertje on 2013-09-25
At first I would say you need to install Gweather first. 

But on second thought, perhaps what you're trying to achieve can be done using indactor-weather which is available from the Ubuntu Store.

---

### Post by kurt18947 on 2013-09-25
It's a shame the extensions.gnome.org web site isn't working for this but it isn't, at least for 13.10.  Sooo..... here's what I did:

```


Add the PPA *ppa:gnome-shell-extensions* to your source list, update the package list and install *gnome-shell-extension-weather*:

sudo add-apt-repository ppa:gnome-shell-extensions
sudo apt-get update
sudo apt-get install gnome-shell-extension-weather

```


[https://github.com/Neroth/gnome-shell-extension-weather](https://github.com/Neroth/gnome-shell-extension-weather)

---

### Post by keCAtMd on 2013-09-26
Reading package lists... Done
gus@gus-Lenovo-IdeaPad-U260:~$ sudo apt-get install gnome-shell-extensions-weather
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-shell-extensions-weather

---

### Post by deadflowr on 2013-09-26
Did you try adding the ppa again?(Using the correct line add-apt-repository, instead of apt-repository)
Then the command should be
```
sudo apt-get install gnome-shell-extension-weather
```
not gnome-shell-extension**s**-weather.

For further clarifications, You Ubuntu version is always helpful.

---

