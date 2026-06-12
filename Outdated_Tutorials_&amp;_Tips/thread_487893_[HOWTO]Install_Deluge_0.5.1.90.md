---
title: "[HOWTO]Install Deluge 0.5.1.90"
date: 2007-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by cwood06 on 2007-06-29
[SIZE="5"][B]NEWS:
[/B][/SIZE]
[LIST]
[*]0.5.2 Released
[/LIST]
** .deb packages below**
[i386]("http://www.dipconsultants.com/ubuntu/feisty/deluge-torrent_0.5.2-1_i386.deb")
[AMD64bit]("http://www.dipconsultants.com/ubuntu/feisty/deluge-torrent_0.5.2-1_amd64.deb")

[CENTER]**My First tut. Hope you Enjoy!**[/CENTER]

**Installing**

First is to download deluge 

```
wget http://download.deluge-torrent.org/testing/deluge-0.5.1.90.tar.gz
```

Then unzip it...

```
tar -xvf deluge-0.5.1.90.tar.gz
```

Then download the dependencies...

```
sudo apt-get install g++ python-all-dev python-all python-dbus python-gtk2 python-xdg python-support libboost-dev libboost-thread-dev libboost-date-time-dev libboost-filesystem-dev libboost-serialization-dev libssl-dev zlib1g-dev
```

Now that we have all the dependencies, we can finnally install deluge...
Change to the Deluge Install Directory:

```
cd deluge-0.5.1.90
```

[RIGHT][Remeber Tab is your friend in the terminal][/RIGHT]

This will build deluge:

```
python setup.py build
```


Clean up the make 

```
 python setup.py clean
```

This will install it...

```
sudo python setup.py install
```

Now just type deluge and your ready to go!

**Troubleshooting**

if you get errors when loading deluge such as 

```
~/deluge-0.5.1.90$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG value: 1
Applying preferences
Starting DHT...
/usr/lib/python2.5/site-packages/deluge/core.py:770: DeprecationWarning: integer argument expected, got float
  PREF_FUNCTIONS[pref](self.get_pref(pref))
Traceback (most recent call last):
  File "/usr/bin/deluge", line 93, in <module>
    start_deluge()
  File "/usr/bin/deluge", line ...
```

do a 

```
 sudo rm -r ~/.config/deluge 
```

this will wipe your prefrences and start a new... so you will redo your ports if you finds bugs report them to deluge-torrent.org

Pic:
[IMG]http://i26.photobucket.com/albums/c143/cwood06/deluge.png[/IMG]

(Not sure if they have posted a .deb yet but this will help ya if you want the newest version for now.)

---

### Post by fontenot_1031 on 2007-07-01
ooh great.  I accidently killed the terminal (ctrl+c) when I was downloading the dependencies, I was about half way done with one of them.  Do you know how to remove them?  Nice tutorial btw.

---

### Post by dn* on 2007-07-01
Nice guide, but i get the following when i run 'deluge'

```
damien@alisa:~/deluge-0.5.1.90$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG value: 1
Applying preferences
Starting DHT...
/usr/lib/python2.5/site-packages/deluge/core.py:770: DeprecationWarning: integer argument expected, got float
  PREF_FUNCTIONS[pref](self.get_pref(pref))
Traceback (most recent call last):
  File "/usr/bin/deluge", line 93, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 67, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/usr/lib/python2.5/site-packages/deluge/interface.py", line 59, in __init__
    '%s %s'%(common.PROGRAM_NAME, common.PROGRAM_VERSION), common.CONFIG_DIR)
  File "/usr/lib/python2.5/site-packages/deluge/core.py", line 223, in __init__
    self.state = pickle.load(pkl_file)
  File "/usr/lib/python2.5/pickle.py", line 1370, in load
    return Unpickler(file).load()
  File "/usr/lib/python2.5/pickle.py", line 858, in load
    dispatch[key](self)
  File "/usr/lib/python2.5/pickle.py", line 1069, in load_inst
    klass = self.find_class(module, name)
  File "/usr/lib/python2.5/pickle.py", line 1124, in find_class
    __import__(module)
ImportError: No module named deluge

```

---

### Post by Mechanical on 2007-07-01
Installs but doesn't run for me either.

Removed this version and went back to the old one but now it doesn't work either.

Traceback (most recent call last):
  File "/usr/bin/deluge", line 31, in <module>
    import deluge, deluge.dcommon, deluge.delugegtk
ImportError: No module named dcommon

---

### Post by dn* on 2007-07-01
clearing the settings fixed it for me

```
sudo rm -r ~/.config/deluge
```

---

### Post by cwood06 on 2007-07-01
yea you might have to remove your settings deluge sitll has that bug thanks for the posts ill put it in the top post

---

### Post by cwood06 on 2007-07-01
> **fontenot_1031 said:**
> ooh great.  I accidently killed the terminal (ctrl+c) when I was downloading the dependencies, I was about half way done with one of them.  Do you know how to remove them?  Nice tutorial btw.

just redo the instal lcommand it will just skip the packages it already downloaded or installed if they are the newest versions

---

### Post by Mechanical on 2007-07-02
Thanks!  Removing the old settings worked perfectly.  I love the new blocklist feature of deluge along with the easy download upload limit in the tray on right click.  Thanks for the tutorial!

---

### Post by dn* on 2007-07-02
```
An error occured while trying to add the torrent. It's possible your .torrent file is corrupted.
```

anyone else getting this error when trying to add torrents? and does the add url button work for anyone?

---

### Post by smbm on 2007-07-04
Anyone know how to uninstall if installed this way? I ran:

```
python setup.py --help
```

and got (amongst other things)

```
  setup.py build      will build the package underneath 'build/'
  setup.py install    will install the package

```


Nothing about uninstalling when the final version comes out though.

Thanks in advance.

---

### Post by cwood06 on 2007-07-04
you can use the sudo apt-get remove deluge command to remove it

---

### Post by smbm on 2007-07-04
Even if I install from source? 

That doesn't seem usual.

---

### Post by cwood06 on 2007-07-04
it worked for me when i did it

---

### Post by smbm on 2007-07-04
Cool.

So ```
sudo python setup.py install
``` builds and installs a .deb package.

That is awesome.

(I'm easily impressed I guess)

I'm running it as I type.

---

### Post by cwood06 on 2007-07-05
no it doesnt make a .deb but i think it knows how to unistall it because its in the repos and iv installed it from other deluge.debs

---

### Post by lbelloq on 2007-07-08
Question>

How can I make Deluge the default Bittorrent application in Firefox and others?
Thanks in advance.

---

### Post by cwood06 on 2007-07-08
when a .torrent files pops up in firefox have it select a program

deluge is in the directory 

/usr/bin/deluge


then it will selcet it from then on

---

### Post by lbelloq on 2007-07-08
Many thanks, it worked perfectly.

---

### Post by odinb on 2007-07-14
what repository can this be found in?

---

### Post by cwood06 on 2007-07-14
none that i know of, if anyone knows please post

---

