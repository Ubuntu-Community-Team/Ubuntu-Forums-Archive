---
title: "HOWTO&quot; Compile and install Gimmie 0.2.0!"
date: 2007-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by stalefries on 2007-01-18
Edit: WOW! I'm surprised how popular this has become. I want to thank everyone who has helped out while I was away.

_[SIZE=4]**Prologue**[/SIZE]_
This is a guide to download, compile, and install the new version of Gimmie. You can read about Gimmie [here]("http://beatnik.infogami.com/Gimmie"), it's pretty cool.

**[SIZE=3]*Disclaimers*[/SIZE]**
Note: there is no support for this guide (I'll try my best, but no promises), and the guide is to be used at your own risk. 

I want to stress that Gimmie is very much in a beta state, so don't be surprised if it crashes once a day. 

This guide has been tested on an Edgy 32-bit install, although it should work on any platform, since Gimmie written in python.

[SIZE=3]**[COLOR=Red]WARNING[/COLOR]**[/SIZE]: I also want to stress that it is a bad idea to use .deb's made by someone else. Really, it's not hard to compile software. Also, checkinstall .deb's are not meant to be used to install applications. Checkinstall is solely intended to be useful when you want to uninstall gimmie. Again, please do not use someone else's .deb's (unless they are provided by Ubuntu, of course.)

_**[SIZE=4]Preparation[/SIZE]**_
Before you start, hold up your right hand, and repeat after me:
I, (your name), do solemnly swear that upon completion of this HOWTO will submit any and all bugs I encounter to [http://bugzilla.gnome.org](http://bugzilla.gnome.org), unless the bug already exists, at which point I will contribute any additional information possible.

First, download Gimmie.
```
wget http://www.beatniksoftware.com/gimmie/releases/gimmie-0.2.1.tar.gz
```Note: There is a new version available, 0.2.6, but I haven't tested this procedure with it yet. Most likely, it should work fine. 
Release notes:
- [0.2.6]("http://lists.beatniksoftware.com/pipermail/gimmie-list-beatniksoftware.com/2007-March/000038.html")
- [0.2.5]("http://lists.beatniksoftware.com/pipermail/gimmie-list-beatniksoftware.com/2007-March/000019.html")
-[ 0.2.4]("http://lists.beatniksoftware.com/pipermail/gimmie-list-beatniksoftware.com/2007-March/000013.html")
- [0.2.3]("http://lists.beatniksoftware.com/pipermail/gimmie-list-beatniksoftware.com/2007-February/000006.html")
To get the latest version instead, do: ```
wget http://www.beatniksoftware.com/gimmie/releases/gimmie-0.2.6.tar.gz
```Then, install all the dependencies and tools needed. This wasn't done on a clean install, I'll update the dependencies if any are reported.
```
sudo aptitude install build-essential checkinstall libgnomecupsui1.0-dev  python-gnome2-dev python2.4-dev libgnomevfs2-dev libgnomevfs2-0 python-gnome2-desktop-dev 
libgnomecups1.0-dev
```Now you need to check if you have a file in your home folder called ".gtk-bookmarks". Run the following command in you home folder
```
ls -a | grep .gtk-bookmarks
```If it doesn't show .gtk-bookmarks, do the following:
```
touch ~/.gtk-bookmarks
``` Now, change to the directory where you downloaded Gimmie and unpack it, then go to the gimmie directory. I'm assuming you downloaded to the Desktop.
```
cd ~/Desktop
tar -zxvf gimmie-0.2.1.tar.gz
cd gimmie-0.2.1
```Now, this is the fun part. Here we make sure we have everything necessary, compile the software (actually, I think it just moves stuff around, you don't really compile Python programs), and then install the files in the proper places.
```
./configure --prefix=/usr
make
sudo checkinstall
```Hopefully you now have passed through without any errors. 
Now, right-click your panel and click "Add to panel". Scroll down to the Utilities section and add Gimmie. Huzzah! You're done!

[SIZE=4]_**Tips**_[/SIZE]
Here are some gconf settings that you may adjust. You can modify them using gconf-editor. They reside in /apps/gimmie/. I'm not sure how you create that folder if it doesn't exist for you. However, the folder will probably be empty. You can create the following keys and modify their values.

autohide (boolean): True will autohide the top bar (either the menu buttons, or the icons -- dependent on swapbar key), false will show always (default)
click_policy (string): Choose from the following options:
 * single - single click in menus
 * double - double click in menus
 * nautilus - follow nautilus settings
clockapplet (boolean): True will show the clock as an applet.  False will show the clock next to the computer text.
gmail_keyring_token (integer):  Do not modify this!  This is used to find your gmail details stored in your keyring.
swapbar (boolean): True will reverse the position of the two parts - the buttons and the icons.  False is the default.
vertical (boolean): True will make the bar vertical and place it on the left side of your screen. False is the default. I do not know if there is a way to move it to the right side.

Extra tip: If you have a keyboard shortcut set for your Applications menu, and you remove it after getting Gimmie, you can still use that shortcut. The menu will pop up wherever your mouse is!

---

### Post by Virtual DarKness on 2007-01-19
Hi, thanks a lot for the guide! Works also with the 0.2.1 version :)

Just one thing: you can avoid the last step doing ./configure --prefix=/usr that should be good using checkinstall ;)

bye,
Giovanni.

---

### Post by Cheizzz on 2007-01-19
I followed your instructions on installing gimmie, and thank your very much for that: it's installed! 

However, it refuses to play. I can get gimmie on the gnome-panel but when i click one of the four buttons on it, it does nothing, only seemingly launching a window, as i can see in my taskbar. So, no gimmie for me :(

Can you help me out? I'd love to give some console output, but how do run an panel applet in the console? I tried $gimmie --run-in-window as i have seen somewhere in an ubuntu system panel forum, but no luck, same unlogical mumbojumbo as just running $gimmie. 
If im wrong, and its not mumbojumbo, ask for my CLI output.

Oh, another thing: you should list "python2.4-dev" as a dependency

---

### Post by stalefries on 2007-01-19
Thanks, Virtual Darkness and Chiezzz. I'll add those fixes now.

---

### Post by stalefries on 2007-01-19
Cheizzz, that sounds odd, but I have no idea on how to fix it. I'd file a bug on bugzilla.gnome.org .

---

### Post by Old Pink on 2007-01-19
.deb file created for those who prefer not to install from source. :)

---

### Post by Cheizzz on 2007-01-19
Okay, more "buggy" news. 
It seems my problems have somehow to do with my use of AIGLX + Compiz.
If I use attempt to use Gimmie when It's turned on I get the issue described above.
But when I turn Compiz off through Gandalfn's exquisite helper program, and then use Gimmie it actually works!

Could this information be helpfull?

---

### Post by hind3nburg on 2007-01-19
i can't get that debian to work. it's not listed as an available panel when i installed it.

---

### Post by Lord Illidan on 2007-01-19
The debian is made for feisty, so it might not work on Edgy, it did not work under mine..

Still, I downloaded and compiled the code as per your instructions, and man this is cool, better than USP or Slab even.

---

### Post by stalefries on 2007-01-19
Chiezzz, that's very helpful information. Please, go file a bug about it, including all the information you think could be useful. Architecture, ubuntu version, compiz/aiglx version, etc.

---

### Post by jbus on 2007-01-19
I compiled it and the applet works fine, but regular mode doesn't work for me. Anyone else have this problem?

> Traceback (most recent call last):
  File "/usr/local/bin/gimmie", line 51, in ?
    gimmie.gimmie.main(sys.argv[1:])
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie.py", line 87, in main
    load_it()
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie.py", line 82, in <lambda>
    load_it = lambda: _load_gimmie_bar(topics)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie.py", line 41, in _load_gimmie_bar
    gimmie_bar = GimmieBarDock(topics, gravity, autohide_anchors=autohide, swapbar=swapbar)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_bar.py", line 20, in __init__
    self.layout(edge_gravity, self.edge_window, swapbar)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_bar.py", line 91, in layout
    running_list = self.make_running_list(edge_gravity, topic)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_bar.py", line 45, in make_running_list
    running = TopicRunningList(running_source, edge_gravity)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 273, in __init__
    self._reload(source)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 326, in _reload
    self.add_item(i, target_height)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 294, in add_item
    running = RunningItemTile(i, target_height, self.gravity)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 73, in __init__
    self._reload(item)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 125, in _reload
    self.icons = self._load_icons(item, self.target_height)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 80, in _load_icons
    icon = item.get_icon(target_height)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_file.py", line 90, in get_icon
    self.get_mimetype() or "",
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_file.py", line 143, in get_mimetype
    return self.ensure_file_info().mime_type
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_file.py", line 56, in ensure_file_info
    self.vfs_info = gnomevfs.get_file_info(vfs_uri)
NotFoundError: File not found

---

### Post by stalefries on 2007-01-19
Hind3nburg: Are you referring to Old Pink's Debian package? I would suggest compiling it yourself. It's really fast (and i have a really old processor, 500mhz), and it's not hard at all.

And of course, remember what your mom told you: don't put a lot of trust in third-party .deb's/repositories.

---

### Post by Lord Illidan on 2007-01-19
> **jbus said:**
> I compiled it and the applet works fine, but regular mode doesn't work for me. Anyone else have this problem?
Yep, me too.

---

### Post by stalefries on 2007-01-19
jbus: How did you start gimmie?

---

### Post by IndigoMontoya on 2007-01-19
I successfully compiled it from source and receive this in a "bug buddy" window when I run it:

```
Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Traceback (most recent call last):
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_util.py", line 718, in do_reload
    for line in file(self._bookmarks_path):
IOError: [Errno 2] No such file or directory: '/home/spruce/.gtk-bookmarks'

```

Also, when I run it from the console this is output:

```
spruce@spruce-laptop:~$ gimmie 
/usr/local/lib/python2.4/site-packages/gimmie/gimmie_util.py:925: GtkWarning: Unable to locate theme engine in module_path: "pixmap",
  icon_theme = gtk.icon_theme_get_default()
Traceback (most recent call last):
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_util.py", line 718, in do_reload
    for line in file(self._bookmarks_path):
IOError: [Errno 2] No such file or directory: '/home/spruce/.gtk-bookmarks'


(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

** (bug-buddy:24548): WARNING **: Couldn't load icon for Open Folder

```

I guess I should also point out I am running Beryl.  any thoughts?

---

### Post by ogryn on 2007-01-19
> **IndigoMontoya said:**
> I successfully compiled it from source and receive this in a "bug buddy" window when I run it:

```
Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Traceback (most recent call last):
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_util.py", line 718, in do_reload
    for line in file(self._bookmarks_path):
IOError: [Errno 2] No such file or directory: '/home/spruce/.gtk-bookmarks'

```

Also, when I run it from the console this is output:

```
spruce@spruce-laptop:~$ gimmie 
/usr/local/lib/python2.4/site-packages/gimmie/gimmie_util.py:925: GtkWarning: Unable to locate theme engine in module_path: "pixmap",
  icon_theme = gtk.icon_theme_get_default()
Traceback (most recent call last):
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_util.py", line 718, in do_reload
    for line in file(self._bookmarks_path):
IOError: [Errno 2] No such file or directory: '/home/spruce/.gtk-bookmarks'


(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(bug-buddy:24548): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

** (bug-buddy:24548): WARNING **: Couldn't load icon for Open Folder

```

I guess I should also point out I am running Beryl.  any thoughts?

I got past the first one by just creating a blank file with that name.  I get the second one as well though.

---

### Post by Belathor on 2007-01-19
I get that same error. I also have beryl installed, but I'm currently in Metacity.

---

### Post by ogryn on 2007-01-19
I just got past the vfs error by installing:
```
sudo aptitude install libgnomevfs2-dev libgnomevfs2-0
```

Then re-running the ./configure, make, checkinstall process

---

### Post by ogryn on 2007-01-19
After installing python-libgmail, and clicking the GMail button in Gimmie Panel, I get the following crash...

```
Memory status: size: 92332032 vsize: 0 resident: 92332032 share: 0 rss: 34607104 rss_rlim: 0
CPU usage: start_time: 1169249120 rtime: 0 utime: 346 stime: 0 cutime:316 cstime: 0 timeout: 30 it_real_value: 0 frequency: 2

Backtrace was generated from '/usr/bin/gimmie'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210181968 (LWP 5923)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7f5134b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb70451b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7e4fc53 in strlen () from /lib/tls/i686/cmov/libc.so.6
#5  0x08084a6a in PyString_FromString ()
#6  0xb63a02e5 in initgnomekeyring ()
   from /usr/lib/python2.4/site-packages/gtk-2.0/gnomekeyring.so
#7  0x080b8ab0 in PyEval_EvalFrame ()
#8  0x080b8d94 in PyEval_EvalFrame ()
#9  0x080b8d94 in PyEval_EvalFrame ()
#10 0x080b8d94 in PyEval_EvalFrame ()
#11 0x080b8d94 in PyEval_EvalFrame ()
#12 0x080b8d94 in PyEval_EvalFrame ()
#13 0x080b8d94 in PyEval_EvalFrame ()
#14 0x080b8d94 in PyEval_EvalFrame ()
#15 0x080ba4b9 in PyEval_EvalCodeEx ()
#16 0x08101f71 in PyClassMethod_New ()
#17 0x08058c27 in PyObject_Call ()
#18 0x0805e4f4 in PyClass_IsSubclass ()
#19 0x08058c27 in PyObject_Call ()
#20 0x080b395c in PyEval_CallObjectWithKeywords ()
#21 0x080590d0 in PyObject_CallObject ()
#22 0xb7cca967 in init_gobject ()
   from /var/lib/python-support/python2.4/gtk-2.0/gobject/_gobject.so
#23 0xb7c6b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#24 0xb7c7bb93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#25 0xb7c7d418 in g_signal_emitv () from /usr/lib/libgobject-2.0.so.0
#26 0xb7cc0959 in init_gobject ()
   from /var/lib/python-support/python2.4/gtk-2.0/gobject/_gobject.so
#27 0x080b901a in PyEval_EvalFrame ()
#28 0x080b8d94 in PyEval_EvalFrame ()
#29 0x080ba4b9 in PyEval_EvalCodeEx ()
#30 0x08101f71 in PyClassMethod_New ()
#31 0x08058c27 in PyObject_Call ()
#32 0x0805e4f4 in PyClass_IsSubclass ()
#33 0x08058c27 in PyObject_Call ()
#34 0x080b395c in PyEval_CallObjectWithKeywords ()
#35 0x080590d0 in PyObject_CallObject ()
#36 0xb7cca967 in init_gobject ()
   from /var/lib/python-support/python2.4/gtk-2.0/gobject/_gobject.so
#37 0xb7c6b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#38 0xb7c7bb93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#39 0xb7c7d418 in g_signal_emitv () from /usr/lib/libgobject-2.0.so.0
#40 0xb7cc0959 in init_gobject ()
   from /var/lib/python-support/python2.4/gtk-2.0/gobject/_gobject.so
#41 0x080b901a in PyEval_EvalFrame ()
#42 0x080b8d94 in PyEval_EvalFrame ()
#43 0x080ba4b9 in PyEval_EvalCodeEx ()
#44 0x08101f71 in PyClassMethod_New ()
#45 0x08058c27 in PyObject_Call ()
#46 0x080b395c in PyEval_CallObjectWithKeywords ()
#47 0x080590d0 in PyObject_CallObject ()
#48 0xb7cca967 in init_gobject ()
   from /var/lib/python-support/python2.4/gtk-2.0/gobject/_gobject.so
#49 0xb7c6b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#50 0xb7c7bb93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#51 0xb7c7d0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#52 0xb7c7d279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#53 0xb78a28e3 in gtk_toggle_button_toggled ()
   from /usr/lib/libgtk-x11-2.0.so.0
#54 0xb78a2958 in gtk_toggle_button_toggled ()
   from /usr/lib/libgtk-x11-2.0.so.0
#55 0xb7c78b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#56 0xb7c69fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#57 0xb7c6b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#58 0xb7c7c02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#59 0xb7c7d0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#60 0xb7c7d279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#61 0xb770f093 in gtk_button_clicked () from /usr/lib/libgtk-x11-2.0.so.0
#62 0xb78a26b8 in gtk_toggle_action_new () from /usr/lib/libgtk-x11-2.0.so.0
#63 0xb7c78b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#64 0xb7c69fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#65 0xb7c6b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#66 0xb7c7c02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#67 0xb7c7d0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#68 0xb7c7d279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#69 0xb770f123 in gtk_button_released () from /usr/lib/libgtk-x11-2.0.so.0
#70 0xb770f181 in gtk_button_released () from /usr/lib/libgtk-x11-2.0.so.0
#71 0xb77deb00 in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
#72 0xb7c69fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#73 0xb7c6b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#74 0xb7c7c1e3 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#75 0xb7c7ce7f in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#76 0xb7c7d279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#77 0xb78f25f8 in gtk_widget_get_default_style ()
   from /usr/lib/libgtk-x11-2.0.so.0
#78 0xb77d7ef3 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#79 0xb77d90f7 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#80 0xb76627ea in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#81 0xb7bf6802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#82 0xb7bf97df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#83 0xb7bf9b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#84 0xb6dc2a23 in bonobo_main () from /usr/lib/libbonobo-2.so.0
#85 0xb6dc0c89 in bonobo_generic_factory_main_timeout ()
   from /usr/lib/libbonobo-2.so.0
#86 0xb6dc0d13 in bonobo_generic_factory_main ()
   from /usr/lib/libbonobo-2.so.0
#87 0xb7080ad1 in panel_applet_factory_main_closure ()
   from /usr/lib/libpanel-applet-2.so.0
#88 0xb70fb9f0 in initgnomeapplet ()
   from /usr/lib/python2.4/site-packages/gtk-2.0/gnomeapplet.so
#89 0x080b901a in PyEval_EvalFrame ()
#90 0x080b8d94 in PyEval_EvalFrame ()
#91 0x080ba4b9 in PyEval_EvalCodeEx ()
#92 0x080ba527 in PyEval_EvalCode ()
#93 0x080ddb1a in PyRun_FileExFlags ()
#94 0x080ddd07 in PyRun_SimpleFileExFlags ()
#95 0x08055cc2 in Py_Main ()
#96 0x08055132 in main ()

Thread 1 (Thread -1210181968 (LWP 5923)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7f5134b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb70451b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7e4fc53 in strlen () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0x08084a6a in PyString_FromString ()
No symbol table info available.
#6  0xb63a02e5 in initgnomekeyring ()
   from /usr/lib/python2.4/site-packages/gtk-2.0/gnomekeyring.so
No symbol table info available.
#7  0x080b8ab0 in PyEval_EvalFrame ()
No symbol table info available.
#8  0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#9  0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#10 0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#11 0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#12 0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#13 0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#14 0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#15 0x080ba4b9 in PyEval_EvalCodeEx ()
No symbol table info available.
#16 0x08101f71 in PyClassMethod_New ()
No symbol table info available.
#17 0x08058c27 in PyObject_Call ()
No symbol table info available.
#18 0x0805e4f4 in PyClass_IsSubclass ()
No symbol table info available.
#19 0x08058c27 in PyObject_Call ()
No symbol table info available.
#20 0x080b395c in PyEval_CallObjectWithKeywords ()
No symbol table info available.
#21 0x080590d0 in PyObject_CallObject ()
No symbol table info available.
#22 0xb7cca967 in init_gobject ()
   from /var/lib/python-support/python2.4/gtk-2.0/gobject/_gobject.so
No symbol table info available.
#23 0xb7c6b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#24 0xb7c7bb93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#25 0xb7c7d418 in g_signal_emitv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#26 0xb7cc0959 in init_gobject ()
   from /var/lib/python-support/python2.4/gtk-2.0/gobject/_gobject.so
No symbol table info available.
#27 0x080b901a in PyEval_EvalFrame ()
No symbol table info available.
#28 0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#29 0x080ba4b9 in PyEval_EvalCodeEx ()
No symbol table info available.
#30 0x08101f71 in PyClassMethod_New ()
No symbol table info available.
#31 0x08058c27 in PyObject_Call ()
No symbol table info available.
#32 0x0805e4f4 in PyClass_IsSubclass ()
No symbol table info available.
#33 0x08058c27 in PyObject_Call ()
No symbol table info available.
#34 0x080b395c in PyEval_CallObjectWithKeywords ()
No symbol table info available.
#35 0x080590d0 in PyObject_CallObject ()
No symbol table info available.
#36 0xb7cca967 in init_gobject ()
   from /var/lib/python-support/python2.4/gtk-2.0/gobject/_gobject.so
No symbol table info available.
#37 0xb7c6b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#38 0xb7c7bb93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#39 0xb7c7d418 in g_signal_emitv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#40 0xb7cc0959 in init_gobject ()
   from /var/lib/python-support/python2.4/gtk-2.0/gobject/_gobject.so
No symbol table info available.
#41 0x080b901a in PyEval_EvalFrame ()
No symbol table info available.
#42 0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#43 0x080ba4b9 in PyEval_EvalCodeEx ()
No symbol table info available.
#44 0x08101f71 in PyClassMethod_New ()
No symbol table info available.
#45 0x08058c27 in PyObject_Call ()
No symbol table info available.
#46 0x080b395c in PyEval_CallObjectWithKeywords ()
No symbol table info available.
#47 0x080590d0 in PyObject_CallObject ()
No symbol table info available.
#48 0xb7cca967 in init_gobject ()
   from /var/lib/python-support/python2.4/gtk-2.0/gobject/_gobject.so
No symbol table info available.
#49 0xb7c6b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#50 0xb7c7bb93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#51 0xb7c7d0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#52 0xb7c7d279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#53 0xb78a28e3 in gtk_toggle_button_toggled ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#54 0xb78a2958 in gtk_toggle_button_toggled ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#55 0xb7c78b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#56 0xb7c69fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#57 0xb7c6b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#58 0xb7c7c02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#59 0xb7c7d0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#60 0xb7c7d279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#61 0xb770f093 in gtk_button_clicked () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#62 0xb78a26b8 in gtk_toggle_action_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#63 0xb7c78b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#64 0xb7c69fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#65 0xb7c6b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#66 0xb7c7c02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#67 0xb7c7d0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#68 0xb7c7d279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#69 0xb770f123 in gtk_button_released () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#70 0xb770f181 in gtk_button_released () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#71 0xb77deb00 in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#72 0xb7c69fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#73 0xb7c6b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#74 0xb7c7c1e3 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#75 0xb7c7ce7f in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#76 0xb7c7d279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#77 0xb78f25f8 in gtk_widget_get_default_style ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#78 0xb77d7ef3 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#79 0xb77d90f7 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#80 0xb76627ea in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#81 0xb7bf6802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#82 0xb7bf97df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#83 0xb7bf9b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#84 0xb6dc2a23 in bonobo_main () from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#85 0xb6dc0c89 in bonobo_generic_factory_main_timeout ()
   from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#86 0xb6dc0d13 in bonobo_generic_factory_main ()
   from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#87 0xb7080ad1 in panel_applet_factory_main_closure ()
   from /usr/lib/libpanel-applet-2.so.0
No symbol table info available.
#88 0xb70fb9f0 in initgnomeapplet ()
   from /usr/lib/python2.4/site-packages/gtk-2.0/gnomeapplet.so
No symbol table info available.
#89 0x080b901a in PyEval_EvalFrame ()
No symbol table info available.
#90 0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#91 0x080ba4b9 in PyEval_EvalCodeEx ()
No symbol table info available.
#92 0x080ba527 in PyEval_EvalCode ()
No symbol table info available.
#93 0x080ddb1a in PyRun_FileExFlags ()
No symbol table info available.
#94 0x080ddd07 in PyRun_SimpleFileExFlags ()
No symbol table info available.
#95 0x08055cc2 in Py_Main ()
No symbol table info available.
#96 0x08055132 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

??

---

### Post by Kobalt on 2007-01-19
Man that Gimmie thing is great... It has to be the future of Gnome's menu, totaly... In four menus you've got quick access to anything you need fast, and to everything. 
BRAVO! 

Question : is the GMail buton for enabling Google talk (contact list I suppose) or to act as a GMail notifier / previewer ?

Keep up the good work lads.

---

### Post by IndigoMontoya on 2007-01-19
After touching ~/.gtk-bookmarks and running gimmie I get the following:

```
Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Traceback (most recent call last):
  File "/usr/local/bin/gimmie", line 51, in ?
    gimmie.gimmie.main(sys.argv[1:])
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie.py", line 87, in main
    load_it()
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie.py", line 82, in <lambda>
    load_it = lambda: _load_gimmie_bar(topics)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie.py", line 41, in _load_gimmie_bar
    gimmie_bar = GimmieBarDock(topics, gravity, autohide_anchors=autohide, swapbar=swapbar)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_bar.py", line 20, in __init__
    self.layout(edge_gravity, self.edge_window, swapbar)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_bar.py", line 91, in layout
    running_list = self.make_running_list(edge_gravity, topic)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_bar.py", line 45, in make_running_list
    running = TopicRunningList(running_source, edge_gravity)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 273, in __init__
    self._reload(source)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 326, in _reload
    self.add_item(i, target_height)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 294, in add_item
    running = RunningItemTile(i, target_height, self.gravity)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 73, in __init__
    self._reload(item)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 125, in _reload
    self.icons = self._load_icons(item, self.target_height)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 80, in _load_icons
    icon = item.get_icon(target_height)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_file.py", line 90, in get_icon
    self.get_mimetype() or "",
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_file.py", line 143, in get_mimetype
    return self.ensure_file_info().mime_type
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_file.py", line 56, in ensure_file_info
    self.vfs_info = gnomevfs.get_file_info(vfs_uri)
NotFoundError: File not found

```

I have also run:
```
sudo aptitude install libgnomevfs2-dev libgnomevfs2-0
```

as previously suggested.  For those of you with a .gtk-bookmarks file, what is in it?

---

### Post by ogryn on 2007-01-19
> **IndigoMontoya said:**
> After touching ~/.gtk-bookmarks and running gimmie I get the following:

```
Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Traceback (most recent call last):
  File "/usr/local/bin/gimmie", line 51, in ?
    gimmie.gimmie.main(sys.argv[1:])
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie.py", line 87, in main
    load_it()
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie.py", line 82, in <lambda>
    load_it = lambda: _load_gimmie_bar(topics)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie.py", line 41, in _load_gimmie_bar
    gimmie_bar = GimmieBarDock(topics, gravity, autohide_anchors=autohide, swapbar=swapbar)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_bar.py", line 20, in __init__
    self.layout(edge_gravity, self.edge_window, swapbar)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_bar.py", line 91, in layout
    running_list = self.make_running_list(edge_gravity, topic)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_bar.py", line 45, in make_running_list
    running = TopicRunningList(running_source, edge_gravity)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 273, in __init__
    self._reload(source)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 326, in _reload
    self.add_item(i, target_height)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 294, in add_item
    running = RunningItemTile(i, target_height, self.gravity)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 73, in __init__
    self._reload(item)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 125, in _reload
    self.icons = self._load_icons(item, self.target_height)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 80, in _load_icons
    icon = item.get_icon(target_height)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_file.py", line 90, in get_icon
    self.get_mimetype() or "",
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_file.py", line 143, in get_mimetype
    return self.ensure_file_info().mime_type
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_file.py", line 56, in ensure_file_info
    self.vfs_info = gnomevfs.get_file_info(vfs_uri)
NotFoundError: File not found

```

I have also run:
```
sudo aptitude install libgnomevfs2-dev libgnomevfs2-0
```

as previously suggested.  For those of you with a .gtk-bookmarks file, what is in it?

Did you do the:
```

./configure
make
checkinstall

```
process again as well?

---

### Post by IndigoMontoya on 2007-01-19
> **ogryn said:**
> Did you do the:
```

./configure
make
checkinstall

```
process again as well?

I had not after touching the .gtk-bookmarks file.  I did not think it would make a difference.  BUT I was wrong.  I just re did the ./configure; make; checkinstall; process and got it working.  

It does still give the vfs error, but that is alright.  I will play more and see if everything else is working.  

I have beryl running so people with that should be able to get this working (I know there is some talk about it maybe being part of the problem).

---

### Post by mikeyrb on 2007-01-19
I also have this issue.  However, this may be of additional help to problem solving:

** (bug-buddy:9952): WARNING **: Couldn't load icon for Open Folder

I get that at the end of similar to what IndigoMontoya pasted.  The applet works, but I want the actual gimmie app to work.

---

### Post by IndigoMontoya on 2007-01-19
> **mikeyrb said:**
> I also have this issue.  However, this may be of additional help to problem solving:

** (bug-buddy:9952): WARNING **: Couldn't load icon for Open Folder

I get that at the end of similar to what IndigoMontoya pasted.  The applet works, but I want the actual gimmie app to work.

Silly thought Mikey:

Do you have any folders open?  Try closing them.  If that is the problem perhaps it is as simple as the icon it is looking for not being there.

---

### Post by mikeyrb on 2007-01-19
Nope, no folders open.  I was hoping that was it earlier, but then I saw no open folders.

---

### Post by IndigoMontoya on 2007-01-19
Well I was just playing around and it crashed after a while, and I looked at my command line and saw the error you posted.  Interesting.  

I have noticed that the program tries to run in any directory, but only if I am in the directory I "compiled" it in will it run without crashing. 

 Does anybody know where I can get a list of command line options?  Or which files to edit to manipulate settings?

---

### Post by mikeyrb on 2007-01-19
Interesting, that works for me too.

The crash happens somewhere between these two:

 *** Reloading TopicRunningList: Opened Documents
 *** Reloading TopicRunningList: Active Conversations

---

### Post by mikeyrb on 2007-01-19
Interesting.  After it worked fine in the compiled folder, I ran it as root (which of course crashed because of dbus), but now it seems to just run.  Weird.  Not sure if it was the initial run, or a sudo run.

---

### Post by saracen on 2007-01-19
Will someone make a .deb for edgy and put it up

---

### Post by mikeyrb on 2007-01-20
Here you go.  This is the deb that resulted after running checkinstall.  Hopefully that works for you... (I don't know enough about packages beyond installing them!)

If you look further down this page, I have a newer svn build which may fix some issues.

---

### Post by searayman on 2007-01-20
i got this error when tryign to run it, or put it into the panel:

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Traceback (most recent call last):
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_util.py", line 718, in do_reload
    for line in file(self._bookmarks_path):
IOError: [Errno 2] No such file or directory: '/home/mike/.gtk-bookmarks'

---

### Post by mikeyrb on 2007-01-20
Hmm... if it hardcoded my home directory, then you will have to compile it yourself.  Otherwise, if your username is also "mike" then you just need to create that file.

EDIT: was that from the package I attached above, or did you compile it yourself?

---

### Post by IndigoMontoya on 2007-01-20
> **searayman said:**
> i got this error when tryign to run it, or put it into the panel:

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Traceback (most recent call last):
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_util.py", line 718, in do_reload
    for line in file(self._bookmarks_path):
IOError: [Errno 2] No such file or directory: '/home/mike/.gtk-bookmarks'


To get around this I created the (empty) file .gtk-bookmarks by:

```
touch ~/.gtk-bookmarks
```
then go back into the extracted directory and re run:

```
./configure
make
checkinstall
```

---

### Post by victor_hr on 2007-01-20
> **searayman said:**
> i got this error when tryign to run it, or put it into the panel:

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Traceback (most recent call last):
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_util.py", line 718, in do_reload
    for line in file(self._bookmarks_path):
IOError: [Errno 2] No such file or directory: '/home/mike/.gtk-bookmarks'
Run:
touch ~/.gtk-bookmarks
and try to put gimmie into the pannel again.

---

### Post by GuessWhy on 2007-01-20
I got error when trying to run gimmie from DEB, or put it into the panel:

> 
Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_gaim.py", line 318, in do_reload
    blist_doc = parse(self.blist_path)
  File "/usr/lib/python2.4/site-packages/_xmlplus/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.4/site-packages/_xmlplus/dom/expatbuilder.py", line 926, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.4/site-packages/_xmlplus/dom/expatbuilder.py", line 207, in parseFile
    parser.Parse(buffer, 0)
ExpatError: not well-formed (invalid token): line 605, column 26


---

### Post by searayman on 2007-01-20
ok i got gimmie aplle let to work but now when i try to run the gimmie command to get gimmie bar to work i get this:


Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Traceback (most recent call last):
  File "/usr/local/bin/gimmie", line 51, in ?
    gimmie.gimmie.main(sys.argv[1:])
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie.py", line 87, in main
    load_it()
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie.py", line 82, in <lambda>
    load_it = lambda: _load_gimmie_bar(topics)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie.py", line 41, in _load_gimmie_bar
    gimmie_bar = GimmieBarDock(topics, gravity, autohide_anchors=autohide, swapbar=swapbar)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_bar.py", line 20, in __init__
    self.layout(edge_gravity, self.edge_window, swapbar)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_bar.py", line 91, in layout
    running_list = self.make_running_list(edge_gravity, topic)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_bar.py", line 45, in make_running_list
    running = TopicRunningList(running_source, edge_gravity)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 273, in __init__
    self._reload(source)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 326, in _reload
    self.add_item(i, target_height)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 294, in add_item
    running = RunningItemTile(i, target_height, self.gravity)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 73, in __init__
    self._reload(item)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 125, in _reload
    self.icons = self._load_icons(item, self.target_height)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 80, in _load_icons
    icon = item.get_icon(target_height)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_file.py", line 90, in get_icon
    self.get_mimetype() or "",
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_file.py", line 143, in get_mimetype
    return self.ensure_file_info().mime_type
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_file.py", line 56, in ensure_file_info
    self.vfs_info = gnomevfs.get_file_info(vfs_uri)
NotFoundError: File not found

---

### Post by IndigoMontoya on 2007-01-20
try running gimmie from the same directory that you compiled it in.  I had the same problem and that solved it.  I don't know why it works though....

---

### Post by mikeyrb on 2007-01-20
I checked out the trunk from the gimmie svn, and packaged that up.  They patched the gtk-bookmarks issue (according to commit comments).  Hopefully they did other stuff too!

EDIT: woops... the package became screwed up and is listed as "trunk" in synaptic.  I'll paste a new one in a later thread.

---

### Post by Kobalt on 2007-01-21
Great !! 
You need to completely remove gimmie with command line (sudo make unsinstall && sudo make clean) and Synaptic in order to install that deb though. But I can confirm it's working very well...

---

### Post by Stevi on 2007-01-21
I installed gimmie today from a deb (gimmie_0.2.1-1_i386.deb). When I click the first button in the gimmie-bar (in german it's called "rechner", maybe "computer" in english) I get the following error:

```
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_applet.py", line 421, in do_button_press_event
    self._show()
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_applet.py", line 426, in _show
    self.topic_win = self.topic.get_topic_window()
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_applet.py", line 356, in get_topic_window_mod
    self.topic_window = TopicWindowMod(self)
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_applet.py", line 265, in __init__
    self._find_first_button()
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_applet.py", line 299, in _find_first_button
    items = source.get_items()
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_base.py", line 183, in get_items
    self.do_reload()
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_computer.py", line 72, in do_reload
    items.sort(key=lambda o: o.get_name().lower())
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 6-8: invalid data

```
Any ideas how to solve the problem? Refering to the last line I think it has something to do with utf8!?

---

### Post by mikeyrb on 2007-01-21
In the po folder, there are translation files.  I'm guessing you are using the de.po (Deutsch).  See if switching to a different language file helps.  I don't know how you do that, but if all else fails, just rename another one to de.po.  See if that helps?

---

### Post by Stevi on 2007-01-21
Thx for your reply but I can't find the files you are talking about. I looked in usr/share/locales and some other places. Where can I find these files?

My idea was to change from utf8 to ISO-8859-1 or something like that. But I don't know how to do that!?!?

---

### Post by mikeyrb on 2007-01-21
Guess I didn't know how the language files worked!  They are stored in /usr/share/locale/de/LC_MESSAGES as gimmie.mo (for Deutsch).  They must be compiled, as they are no longer the text files that were in the source.  I guess you will either have to compile from scratch or try switching in a file from a different directory.  Or possibly contact the dev's for gimmie.  I don't know enough about it to be able to wade through the code.  My guess is that there's something in that language file that it isn't liking.

---

### Post by Stevi on 2007-01-21
Mmhhh, I tried nearly everything.
Compiling as described in the first post of this thread -> same error
Installing using gimmie_0.2.1+**svn**070120-1_i386.deb -> same error
Changing german gimmie.mo to english gimmie.mo -> same error, but in english ;)
```
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 6-8: invalid data
```

---

### Post by XVampireX on 2007-01-21
This is what I'm getting when trying to compile:

[http://www.pastebin.ca/324028](http://www.pastebin.ca/324028)

---

### Post by mikeyrb on 2007-01-21
Is that the result of running make install?  If so, make sure you are running as the root user, probably using sudo.

---

### Post by puccaso on 2007-01-21
ok a few questions
how do we change the code for gimmi so that the gmail access allows access to gmail DOMAIN accounts (user@mydomain.com via gmail hosted service)

what is friendster and how do i make it work?
in the documents pane - how do i enable access too
downloads
attatchments
important email
and photos?

do i have to change my directories around or created hardlinks to them or what??

---

### Post by mikeyrb on 2007-01-22
Anyone who installed my svn package will see it listed as "trunk" in synaptic.  That's no good.
I made a new one with recent SVN changes.  It is untested, but now has the proper name :)

EDIT: in this build... the "keep around" for Computer appears not to work.

EDIT: I think I'll just remove my svn builds, you can wait for new releases and follow directions on page 1.  It's good for you :)

---

### Post by mikeyrb on 2007-01-22
So in the new build, it appears like they have done some work so you can now "keep around" folders to open in Nautilus.  However, they did break the "keep around" for applications, people, and computer.  This appears to be from a new API that was implemented, but not yet updated.  Before I had issues with the buttons above the icons disappearing under windows (at least with Beryl, not tested without), but that appears to work better now... not sure if that's just luck, or source change.

---

### Post by BOBSONATOR on 2007-01-22
Great how to! Worked perfect!

very useful tool,, but one thing, can i change the colors of the tabs?

---

### Post by mikeyrb on 2007-01-22
I have not tried it, but I think modifying the following lines will change the color:

```
    def get_hint_color(self):
        return gtk.gdk.color_parse("lightgreen")
```

That is a sample from gimmie_documents.py.  You will find similar in gimmie_applications.py and gimmie_people.py.

---

### Post by stalefries on 2007-01-22
mikeyrb, I really want to thank you for picking up my slack. I have no idea on a lot of this stuff, but you keep on answering each problem really quick. If I could, i would give you a barnstar, but that's just on Wikipedia.

---

### Post by Wes24 on 2007-01-23
> I have not tried it, but I think modifying the following lines will change the color:

Yep it does, see screenshot.

---

### Post by IndigoMontoya on 2007-01-23
Is it necessary to "recompile" the program after editing the files?   I assume not, but figured Id ask before getting started.

thanks

---

### Post by puccaso on 2007-01-23
how do I enable the other buttons? downloads attatchments etc??

---

### Post by mikeyrb on 2007-01-23
I just tried the modification of color and it required no recompile.

The downloads button is currently pretty simple.  It checks for files in the ~/Downloads directory.  If there are any, it will display them (and enable the button).  That means, currently, for it to be useful, you must have a Downloads directory and you must place your downloads there.  I haven't yet looked through the source for the other buttons.

---

### Post by Stevi on 2007-01-23
> **Stevi said:**
> Mmhhh, I tried nearly everything.
Compiling as described in the first post of this thread -> same error
Installing using gimmie_0.2.1+**svn**070120-1_i386.deb -> same error
Changing german gimmie.mo to english gimmie.mo -> same error, but in english ;)
```
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 6-8: invalid data
```
No it works. I just had to reinstall Edgy ;)

---

### Post by BOBSONATOR on 2007-01-23
Guys, i love this thing, but its crashing often.

---

### Post by mikeyrb on 2007-01-24
Yes, it does seem to crash often.  I have noticed that it tends to crash more when I have liferea open.  Maybe because of windows coming and going quickly, not sure.  Gaim occasionally does it.  I have been using it crash free for the past 4-6 hours I think.

---

### Post by IndigoMontoya on 2007-01-24
> **stalefries said:**
> Check if you have a file in your home folder called ".gtk-bookmarks". Note that the dot means it is normally hidden, so you may have to show hidden files to see if it exists. 

To make this line simplier, perhaps change it to

```
ls -a |grep .gtk-bookmarks
```  If there is no output then go to the touch line.  Just a silly suggestion.

---

### Post by mikeyrb on 2007-01-25
Here are some gconf settings that you may adjust.  You can modify them using gconf-editor.  They reside in /apps/gimmie/.  I'm not sure how you create that folder if it doesn't exist for you.  However, the folder will probably be empty.  You can create the following keys and modify their values.

autohide (boolean): True will autohide the top bar (either the menu buttons, or the icons -- dependent on swapbar key), false will show always (default)
click_policy (string): Choose from the following options:
 * single - single click in menus
 * double - double click in menus
 * nautilus - follow nautilus settings
clockapplet (boolean): True will show the clock as an applet.  False will show the clock next to the computer text.
gmail_keyring_token (integer):  Do not modify this!  This is used to find your gmail details stored in your keyring.
swapbar (boolean): True will reverse the position of the two parts - the buttons and the icons.  False is the default.
vertical (boolean): True will make the bar vertical and place it on the left side of your screen.  False is the default.  I do not know if there is a way to move it to the right side.

Modifications to these keys will take effect instantly.  The only issue I had was that my tray icons and clock disappeared during the reload.  Once I had modified to my satisfaction, I simply restarted gimmie and they returned.  Have fun!

---

### Post by stalefries on 2007-01-25
IndigoMontoya (great name), mikeyrb, thanks, I'll add those two suggestions to the howto.

---

### Post by serlex on 2007-01-26
```
No package 'gtk+-2.0' found
No package 'pygtk-2.0' found
No package 'pygobject-2.0' found
No package 'gnome-python-desktop-2.0' found
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'glib-2.0', required by 'libgnomecups', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GIMMIE_CFLAGS
and GIMMIE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

Edit: Fixed, missing python packages

---

### Post by mikeyrb on 2007-01-26
May I assume you have done this step?
> sudo aptitude install build-essential checkinstall libgnomecupsui1.0-dev  python-gnome2-dev python2.4-dev 
libgnomevfs2-dev libgnomevfs2-0 python-gnome2-desktop-dev

---

### Post by forteller on 2007-01-31
I've done every step, but when I get to ./configure, I get the same error as serlex
```
checking for GIMMIE... configure: error: Package requirements (gtk+-2.0 >= 2.6
                  pygtk-2.0 >= 2.6
                  pygobject-2.0 >= 2.6
                  gnome-python-2.0 >= 2.10
                  gnome-python-desktop-2.0 >= 2.10
                  libgnomecups-1.0 >= 0.2.2) were not met:

No package 'gtk+-2.0' found
No package 'pygtk-2.0' found
No package 'pygobject-2.0' found
No package 'gnome-python-desktop-2.0' found
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'glib-2.0', required by 'libgnomecups', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GIMMIE_CFLAGS
and GIMMIE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by stalefries on 2007-02-01
forteller, it seems you have not installed all the required -dev packages.

---

### Post by mikeyrb on 2007-02-06
From the gimmie mailing list:

> This new release includes the following features and bug fixes:

   Version 0.2.3, February 6, 2007
   * Fix crash opening People pane (bug #404909)
   * Support different panel layouts (Markus Jonsson)
   * Favorite items get a heart
   * GTK 2.10 RecentManager support (James Bowes)
   * Install Gimmie icons from Drew Kerr
   * Remove devel package dependencies
   * "All Favorites" support in Computer
   * Fix bug with missing .gtk-bookmarks file
   * Give applet transparent background (Christian Hammond)
   * Support for running uninstalled build

You can download it here:

   [http://www.beatniksoftware.com/gimmie/releases/gimmie-0.2.3.tar.gz](http://www.beatniksoftware.com/gimmie/releases/gimmie-0.2.3.tar.gz)
   md5sum: 294b9aa65247dc1f467424d15b1c247c
   size: 573KB

---

### Post by stalefries on 2007-02-07
I'll update the howto soon, thanks mikeyrb.

---

### Post by kobewan on 2007-02-09
Missing the following dependency:

libgnomecups1.0-dev

---

### Post by stalefries on 2007-02-11
kobewan: thanks, I'll add it.

---

### Post by skenagle on 2007-02-11
Hey there, ive installed Gimme, and i can run it through the command line...
(as an application)

but it does not appear in my gnome panel options as an "add to panel" optiion when i go to look.

Is there a way to add it manually? or do i somehow have to refresh?

i am going to do a restart just in case...

If it works after that ill update this post, if not .. any ideas?


thank you.:guitar:

---

### Post by stalefries on 2007-02-12
Did you do ```
./configure --prefix=/usr
``` or did you do it without the prefix part?

---

### Post by ounn on 2007-02-20
Hi

Does anyone managed a way to create folders (or whatever it is) under gconf? I want to gimmie single-click bu i have not that keys.

Thanks

ounn

---

### Post by Jehu on 2007-02-26
On Dapper i get this error, while starting:
```
marco@sid:~$ gimmie
Traceback (most recent call last):
  File "/usr/bin/gimmie", line 57, in ?
    import gimmie.gimmie
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie.py", line 12, in ?
    from gimmie_applications import ApplicationsTopic
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_applications.py", line 9, in ?
    import gnomedesktop
ImportError: No module named gnomedesktop

marco@sid:~$

```

---

### Post by stalefries on 2007-02-26
ounn: I wouldn't know, try checking the documentation on that.

Jehu: you need the python bindings for gnomedesktop. Unfortunately, I'm on Dapper, so I wouldn't know what package you need. try doing ```
sudo apt-cache search python gnomedesktop
``` and install any packages that seem logical. If you're unsure of which package to install, post what that command outputs here, and we can help you out.

---

### Post by yigal.weinstein on 2007-03-10
here is an awsome idea brought to reality.  I use beryl for productivity purposes - see through, gathering applications together, etc. are really great features, here come the but while I like functional bling in a gui, Gimmie is a superior idea for organizing highly used applications, documents, etc. into a useful app..  This is what I want more than anything - usability.

I use the command line a lot.  Gimmie at present doesn't seem to know what documents, applications I have used with the command line.  Is there a way to make it keep these documents, applications in its database?  

Thank you

---

### Post by stalefries on 2007-03-11
yigal.weinstein: as far as I know, not yet. But, as always, you're welcome to help! :)

---

### Post by yigal.weinstein on 2007-03-12
what information does gimmie use for storing its information?  If it is pretty simple then using bash history for finding specific application and documents used could be an idea.  This is a long time project but its worth it.  :guitar:

It may have been posted previously but gimmie is at version 0.2.4 :)

---

### Post by stalefries on 2007-03-12
yigal.weinstein: I wouldn't know (I'm not a developer), but you can have a glance at the source code. It's all in Python.

Thanks for the notification, I'll add that there's 0.2.4 available.

---

### Post by yigal.weinstein on 2007-03-17
0.2.5 is out.

---

### Post by stalefries on 2007-03-20
Thanks, updated the first post.

---

### Post by Stevi on 2007-03-23
[0.2.6 is out](http://beatnik.infogami.com/Gimmie)

---

### Post by stalefries on 2007-03-23
Gah, when will they stop!?! :D

---

### Post by arteq on 2007-03-24
I compiled latest 0.2.6 version and get crash when click Library

```
Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Traceback (most recent call last):
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 386, in do_clicked
    self.topic_win = self.topic.get_topic_window()
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_base.py", line 377, in get_topic_window
    self.topic_window = TopicWindow(self)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_topicwin.py", line 1131, in __init__
    self._add_toolbar_items()
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_topicwin.py", line 1155, in _add_toolbar_items
    for i in self.topic.get_toolbar_items(self.tooltips):
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_documents.py", line 396, in get_toolbar_items
    btn = PlacesMenuButton(tooltips)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_documents.py", line 283, in __init__
    self.set_menu(PlacesMenu())
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_documents.py", line 246, in __init__
    for item in device_source.get_items():
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_base.py", line 219, in get_items
    for i in self.get_items_uncached():
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_computer.py", line 217, in get_items_uncached
    yield DriveItem(drive)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_computer.py", line 106, in __init__
    raise ValueError, "Cannot find URI to open for drive '%s'" % drive
ValueError: Cannot find URI to open for drive '<gnomevfs.Drive object (GnomeVFSDrive) at 0xaf852
```

---

### Post by stalefries on 2007-03-24
arteq, please file a bug [here]("http://bugzilla.gnome.org/simple-bug-guide.cgi"). I'm not sure if any developers watch this thread.

---

### Post by embeemb on 2007-03-27
Worked perfectly for me until I did >  ./configure --prefix=/usr/local

and got 

> [checking for XML::Parser... configure: error: XML::Parser perl module is require d for intltool

Any idea how to get around that bit?

---

### Post by ayoli on 2007-04-01
> **arteq said:**
> I compiled latest 0.2.6 version and get crash when click Library

```
Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Traceback (most recent call last):
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 386, in do_clicked
    self.topic_win = self.topic.get_topic_window()
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_base.py", line 377, in get_topic_window
    self.topic_window = TopicWindow(self)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_topicwin.py", line 1131, in __init__
    self._add_toolbar_items()
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_topicwin.py", line 1155, in _add_toolbar_items
    for i in self.topic.get_toolbar_items(self.tooltips):
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_documents.py", line 396, in get_toolbar_items
    btn = PlacesMenuButton(tooltips)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_documents.py", line 283, in __init__
    self.set_menu(PlacesMenu())
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_documents.py", line 246, in __init__
    for item in device_source.get_items():
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_base.py", line 219, in get_items
    for i in self.get_items_uncached():
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_computer.py", line 217, in get_items_uncached
    yield DriveItem(drive)
  File "/usr/local/lib/python2.4/site-packages/gimmie/gimmie_computer.py", line 106, in __init__
    raise ValueError, "Cannot find URI to open for drive '%s'" % drive
ValueError: Cannot find URI to open for drive '<gnomevfs.Drive object (GnomeVFSDrive) at 0xaf852
```

this is a know bug, fixed in svn rev 389:
```
--- trunk/gimmie/gimmie_computer.py	2007/03/22 00:44:46	385
+++ trunk/gimmie/gimmie_computer.py	2007/03/22 20:22:15	389
@@ -103,7 +103,8 @@
                     uri = volume.get_activation_uri()
                     break
             else:
-                raise ValueError, "Cannot find URI to open for drive '%s'" % drive
+                raise ValueError, "Cannot find URI to open for drive '%s'" % \
+                      drive.get_display_name()
 
         Item.__init__(self,
                       uri=uri,
@@ -214,7 +215,10 @@
         yield self.cd_burner
 
         for drive in self.vol_monitor.get_connected_drives():
-            yield DriveItem(drive)
+            try:
+                yield DriveItem(drive)
+            except ValueError:
+                pass
 
 
 class PrinterItem(Item):
```
cheers.

---

### Post by Stevi on 2007-04-14
Does anybody know why there are no gimmie updates in the repos? On my machine it still crashes from time to time and for this reason I would like to see gimmie 0.2.6 in the final Feisty.

---

### Post by stalefries on 2007-04-15
> **Stevi said:**
> Does anybody know why there are no gimmie updates in the repos? On my machine it still crashes from time to time and for this reason I would like to see gimmie 0.2.6 in the final Feisty.
Stevi: I doubt they'll put it in the repos for Feisty now, it's only a few days from release. It seems that 0.2.4 is in [feisty universe]("http://packages.ubuntu.com/feisty/gnome/gimmie"), so you may want to talk to the maintainer of that package whom I believe to be Daniel Holblach; [email]daniel.holbach@ubuntu.com[/email].

---

### Post by donut_irl on 2007-04-25
sorry about the stupid question
I should be able to figure this out but can't ... too much feisty&twinview&beryl lately ... :(

ok so
> ./configure --prefix=/usr gives me the following
<blah.....>
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers
>

i've done all the apt-get stuff ?

---

### Post by donut_irl on 2007-04-26
never mind

after sleep and google i fixed it by adding the Pyrex packages in synaptic

:)

---

### Post by Wokm4n on 2007-04-28
I'm still getting this error :S

[INDENT][I]checking for headers required to compile python extensions... not found
configure: error: could not find Python headers[/I][/INDENT]

I also installed all required packages, I also checked the packages for 0.2.4 in universe and installed all.. I installed all the Pyres packages but no results

I hope someone can help me fix this :confused:

---

### Post by jk-pc on 2007-04-28
Hello..

I had the same problem and had a look around synaptic...

There is a new python-dev package in feisty.. make sure that you have the latest python-dev (sudo apt-get install python-dev) installed.. 
If you install this package it installs the latest python-dev1.5 package for you.. (which is the one we really want I guess...)

Maybe the howto on the first page should be updated to reflect this changed dependency?

(edit)
mhhh... now I can compile it, but checkinstall doesnt want to create and install a deb for me:

> dpkg: error processing /home/jk-pc/linux/gimmie-0.2.6/gimmie_0.2.6-1_i386.deb (-
-install):
 trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is a
lso in package libgconf2-4
(/edit)

jk-pc

---

### Post by json684 on 2007-04-30
Can anyone tell me whats wrong with my install? When I run make after configure I get this:

```
Making all in po
make[2]: Entering directory `/home/jayson/gimmie-0.2.6/po'
file=`echo ar | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ar.po
/bin/sh: -o: not found
make[2]: *** [ar.gmo] Error 127
make[2]: Leaving directory `/home/jayson/gimmie-0.2.6/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jayson/gimmie-0.2.6'
make: *** [all] Error 2

```

---

### Post by json684 on 2007-04-30
so I fixed my problem. You need gettext installed so that the variable gmsgfmt gets set correctly. But now I am having the same problem as jk-pc

```
dpkg: error processing /home/jk-pc/linux/gimmie-0.2.6/gimmie_0.2.6-1_i386.deb (-
-install):
trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is a
lso in package libgconf2-4
```

Any ideas?

---

### Post by foundation on 2007-05-01
After running the ./configure line it goes through all this stuff than hits this error:

```
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

```

All the right packages are installed as well. : (

---

### Post by ayoli on 2007-05-01
try :
```
sudo aptitude install python-dev
```
should do the trick ;)

---

### Post by unabatedshagie on 2007-05-01
I'm having problems getting this to work.

installed all the dependency's and configured, made and checkinstalled. However if I view the log at the end of the procedure it says there have been errors.

```
Selecting previously deselected package gimmie.
(Reading database ... 154623 files and directories currently installed.)
Unpacking gimmie (from .../gimmie_0.2.6-1_i386.deb) ...
dpkg: error processing /home/alex/gimmie-0.2.6/gimmie_0.2.6-1_i386.deb (--instal
l):
 trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is a
lso in package libgconf2-4
Errors were encountered while processing:
 /home/alex/gimmie-0.2.6/gimmie_0.2.6-1_i386.deb
```Anyone have any ideas on what the problem could be?

---

### Post by foundation on 2007-05-05
> **ayoli said:**
> try :
```
sudo aptitude install python-dev
```
should do the trick ;)Worked, weird, thought I had that installed. D: Thanks ayoli.

I'm having another error so instead of trying to continue on the setup from here what's the easiest way to remove all temp/installed/whatever files related to Gimmie (But not the dependencies I've downloaded) so I can start over ?

---

### Post by FaceLeg on 2007-05-20
This applet looks wonderful.  I haven't had it running for more than a minute without it crashing to the ground though...

I have tried versions 0.2.6, 0.2.5 and 0.2.4 - they all crash.  :(

I used sudo make uninstall & sudo make clean when changing versions.

I have installed v 0.2.6 again.  This is the output when 'gimmie' is run in a console:

```
faceleg@faceleg-desktop:~$ gimmie
 *** Reloading TopicRunningList: Running Applications
 *** Reloading TopicRunningList: Opened Documents
 *** Reloading TopicRunningList: Active Conversations
 *** Reloading TopicRunningList: Computer Running Source
Introspect error: The name net.sf.gaim.GaimService was not provided by any .service files

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed
 !!! Error loading Tomboy notes: [Errno 2] No such file or directory: '/home/faceleg/.tomboy'
 *** Window class matches launcher command: nautilus == nautilus --no-desktop --browser %U
 *** Window class matches launcher command: firefox-bin == firefox %u
 *** Reloading TopicRunningList: Running Applications
 *** Reloading TopicRunningList: Opened Documents
 *** Reloading TopicRunningList: Active Conversations
 *** Window class matches launcher command: nautilus == nautilus --no-desktop --browser %U
 *** Window class matches launcher command: firefox-bin == firefox %u
 *** Reloading TopicRunningList: Computer Running Source
 *** Window class matches launcher command: nautilus == nautilus --no-desktop --browser %U
 *** Window class matches launcher command: firefox-bin == firefox %u
 *** Reloading TopicRunningList: Running Applications
 *** Reloading TopicRunningList: Opened Documents
 *** Reloading TopicRunningList: Active Conversations
 *** Window class matches launcher command: nautilus == nautilus --no-desktop --browser %U
 *** Window class matches launcher command: firefox-bin == firefox %u
 *** Reloading TopicRunningList: Computer Running Source

```

This doesn't crash.  Though gimmie looks pretty enough on its own, I need it to be functional as well.  This is the Bug Buddy output when I press Library:

```
Distribution: Ubuntu 6.10 (edgy)
Gnome Release: 2.16.1 2006-10-02 (Ubuntu)
BugBuddy Version: 2.16.0

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 386, in do_clicked
    self.topic_win = self.topic.get_topic_window()
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_base.py", line 377, in get_topic_window
    self.topic_window = TopicWindow(self)
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_topicwin.py", line 1131, in __init__
    self._add_toolbar_items()
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_topicwin.py", line 1155, in _add_toolbar_items
    for i in self.topic.get_toolbar_items(self.tooltips):
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_documents.py", line 396, in get_toolbar_items
    btn = PlacesMenuButton(tooltips)
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_documents.py", line 283, in __init__
    self.set_menu(PlacesMenu())
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_documents.py", line 246, in __init__
    for item in device_source.get_items():
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_base.py", line 219, in get_items
    for i in self.get_items_uncached():
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_computer.py", line 217, in get_items_uncached
    yield DriveItem(drive)
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_computer.py", line 106, in __init__
    raise ValueError, "Cannot find URI to open for drive '%s'" % drive
ValueError: Cannot find URI to open for drive '<gnomevfs.Drive object (GnomeVFSDrive) at 0xae8eee14>'

```

Here is the terminal output when I press People -> Google:

```
faceleg@faceleg-desktop:~$ gimmie
 *** Reloading TopicRunningList: Running Applications
 *** Reloading TopicRunningList: Opened Documents
 *** Reloading TopicRunningList: Active Conversations
 *** Reloading TopicRunningList: Computer Running Source
Introspect error: The name net.sf.gaim.GaimService was not provided by any .service files

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:4936): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed
 !!! Error loading Tomboy notes: [Errno 2] No such file or directory: '/home/faceleg/.tomboy'
 *** Window class matches launcher command: nautilus == nautilus --no-desktop --browser %U
 *** Window class matches launcher command: firefox-bin == firefox %u
 *** Reloading TopicRunningList: Running Applications
 *** Reloading TopicRunningList: Opened Documents
 *** Reloading TopicRunningList: Active Conversations
 *** Window class matches launcher command: nautilus == nautilus --no-desktop --browser %U
 *** Window class matches launcher command: firefox-bin == firefox %u
 *** Reloading TopicRunningList: Computer Running Source
 *** Window class matches launcher command: nautilus == nautilus --no-desktop --browser %U
 *** Window class matches launcher command: firefox-bin == firefox %u
 *** Reloading TopicRunningList: Running Applications
 *** Reloading TopicRunningList: Opened Documents
 *** Reloading TopicRunningList: Active Conversations
 *** Window class matches launcher command: nautilus == nautilus --no-desktop --browser %U
 *** Window class matches launcher command: firefox-bin == firefox %u
 *** Reloading TopicRunningList: Computer Running Source
Error showing url: The location or file could not be found.
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_gui.py", line 386, in do_clicked
    self.topic_win = self.topic.get_topic_window()
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_base.py", line 377, in get_topic_window
    self.topic_window = TopicWindow(self)
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_topicwin.py", line 1131, in __init__
    self._add_toolbar_items()
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_topicwin.py", line 1155, in _add_toolbar_items
    for i in self.topic.get_toolbar_items(self.tooltips):
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_documents.py", line 396, in get_toolbar_items
    btn = PlacesMenuButton(tooltips)
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_documents.py", line 283, in __init__
    self.set_menu(PlacesMenu())
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_documents.py", line 246, in __init__
    for item in device_source.get_items():
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_base.py", line 219, in get_items
    for i in self.get_items_uncached():
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_computer.py", line 217, in get_items_uncached
    yield DriveItem(drive)
  File "/usr/lib/python2.4/site-packages/gimmie/gimmie_computer.py", line 106, in __init__
    raise ValueError, "Cannot find URI to open for drive '%s'" % drive
ValueError: Cannot find URI to open for drive '<gnomevfs.Drive object (GnomeVFSDrive) at 0xae8eee14>'


** (bug-buddy:4999): WARNING **: Couldn't load icon for Open Folder
faceleg@faceleg-desktop:~$ gimmie
 *** Reloading TopicRunningList: Running Applications
 *** Reloading TopicRunningList: Opened Documents
 *** Reloading TopicRunningList: Active Conversations
 *** Reloading TopicRunningList: Computer Running Source
Introspect error: The name net.sf.gaim.GaimService was not provided by any .service files

(gimmie:5027): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:5027): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:5027): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:5027): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:5027): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:5027): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:5027): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed

(gimmie:5027): libgnomevfs-CRITICAL **: gnome_vfs_uri_ref: assertion `uri != NULL' failed
 !!! Error loading Tomboy notes: [Errno 2] No such file or directory: '/home/faceleg/.tomboy'
 *** Window class matches launcher command: nautilus == nautilus --no-desktop --browser %U
 *** Window class matches launcher command: firefox-bin == firefox %u
 *** Reloading TopicRunningList: Running Applications
 *** Reloading TopicRunningList: Opened Documents
 *** Reloading TopicRunningList: Active Conversations
 *** Window class matches launcher command: nautilus == nautilus --no-desktop --browser %U
 *** Window class matches launcher command: firefox-bin == firefox %u
 *** Reloading TopicRunningList: Computer Running Source
 *** Setting source: <OnlineBuddySource object (gimmie+gimmie_base+Item) at 0xae9287ac>
 !!! Error accessing Gaim2 D-BUS interface.  Is Gaim2 running?
 *** Window class matches launcher command: nautilus == nautilus --no-desktop --browser %U
 *** Window class matches launcher command: firefox-bin == firefox %u
 *** Reloading TopicRunningList: Running Applications
 *** Reloading TopicRunningList: Opened Documents
 *** Reloading TopicRunningList: Active Conversations
 *** Window class matches launcher command: nautilus == nautilus --no-desktop --browser %U
 *** Window class matches launcher command: firefox-bin == firefox %u
 *** Reloading TopicRunningList: Computer Running Source
 *** Setting source: <GmailSource object (gimmie+gimmie_base+Item) at 0xae928824>

** (bug-buddy:5056): WARNING **: Couldn't load icon for Open Folder
"/usr/bin/gimmie": not in executable format: File format not recognized


```

And Bug Buddy's:

```
Distribution: Ubuntu 6.10 (edgy)
Gnome Release: 2.16.1 2006-10-02 (Ubuntu)
BugBuddy Version: 2.16.0

Memory status: size: 102920192 vsize: 0 resident: 102920192 share: 0 rss: 30154752 rss_rlim: 0
CPU usage: start_time: 1179669694 rtime: 0 utime: 401 stime: 0 cutime:372 cstime: 0 timeout: 29 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gimmie'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210124624 (LWP 5027)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7f5f34b in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb67a51b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7e5dc53 in strlen () from /lib/tls/i686/cmov/libc.so.6
#5  0x08084a6a in PyString_FromString ()
#6  0xb49b62e5 in initgnomekeyring ()
   from /usr/lib/python2.4/site-packages/gtk-2.0/gnomekeyring.so
#7  0x080b8ab0 in PyEval_EvalFrame ()
#8  0x080b8d94 in PyEval_EvalFrame ()
#9  0x080b8d94 in PyEval_EvalFrame ()
#10 0x080b8d94 in PyEval_EvalFrame ()
#11 0x080b8d94 in PyEval_EvalFrame ()
#12 0x080b8d94 in PyEval_EvalFrame ()
#13 0x08100170 in PyDescr_NewMember ()
#14 0x080b5409 in PyEval_EvalFrame ()
#15 0x08100170 in PyDescr_NewMember ()
#16 0x080b5409 in PyEval_EvalFrame ()
#17 0x08100170 in PyDescr_NewMember ()
#18 0x08097f0e in PyType_Ready ()
#19 0x08058c27 in PyObject_Call ()
#20 0x080b395c in PyEval_CallObjectWithKeywords ()
#21 0x080590d0 in PyObject_CallObject ()
#22 0xb7cd3b0a in init_gobject ()
   from /var/lib/python-support/python2.4/gtk-2.0/gobject/_gobject.so
#23 0xb7c16dd6 in g_source_get_current_time () from /usr/lib/libglib-2.0.so.0
#24 0xb7c16802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#25 0xb7c197df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#26 0xb7c19b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#27 0xb77f9574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#28 0xb7b07d90 in init_gtk ()
   from /var/lib/python-support/python2.4/gtk-2.0/gtk/_gtk.so
#29 0x080b8ab0 in PyEval_EvalFrame ()
#30 0x080ba4b9 in PyEval_EvalCodeEx ()
#31 0x080b86ea in PyEval_EvalFrame ()
#32 0x080ba4b9 in PyEval_EvalCodeEx ()
#33 0x080ba527 in PyEval_EvalCode ()
#34 0x080ddb1a in PyRun_FileExFlags ()
#35 0x080ddd07 in PyRun_SimpleFileExFlags ()
#36 0x08055cc2 in Py_Main ()
#37 0x08055132 in main ()

Thread 1 (Thread -1210124624 (LWP 5027)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7f5f34b in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb67a51b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7e5dc53 in strlen () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0x08084a6a in PyString_FromString ()
No symbol table info available.
#6  0xb49b62e5 in initgnomekeyring ()
   from /usr/lib/python2.4/site-packages/gtk-2.0/gnomekeyring.so
No symbol table info available.
#7  0x080b8ab0 in PyEval_EvalFrame ()
No symbol table info available.
#8  0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#9  0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#10 0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#11 0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#12 0x080b8d94 in PyEval_EvalFrame ()
No symbol table info available.
#13 0x08100170 in PyDescr_NewMember ()
No symbol table info available.
#14 0x080b5409 in PyEval_EvalFrame ()
No symbol table info available.
#15 0x08100170 in PyDescr_NewMember ()
No symbol table info available.
#16 0x080b5409 in PyEval_EvalFrame ()
No symbol table info available.
#17 0x08100170 in PyDescr_NewMember ()
No symbol table info available.
#18 0x08097f0e in PyType_Ready ()
No symbol table info available.
#19 0x08058c27 in PyObject_Call ()
No symbol table info available.
#20 0x080b395c in PyEval_CallObjectWithKeywords ()
No symbol table info available.
#21 0x080590d0 in PyObject_CallObject ()
No symbol table info available.
#22 0xb7cd3b0a in init_gobject ()
   from /var/lib/python-support/python2.4/gtk-2.0/gobject/_gobject.so
No symbol table info available.
#23 0xb7c16dd6 in g_source_get_current_time () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#24 0xb7c16802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#25 0xb7c197df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#26 0xb7c19b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#27 0xb77f9574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#28 0xb7b07d90 in init_gtk ()
   from /var/lib/python-support/python2.4/gtk-2.0/gtk/_gtk.so
No symbol table info available.
#29 0x080b8ab0 in PyEval_EvalFrame ()
No symbol table info available.
#30 0x080ba4b9 in PyEval_EvalCodeEx ()
No symbol table info available.
#31 0x080b86ea in PyEval_EvalFrame ()
No symbol table info available.
#32 0x080ba4b9 in PyEval_EvalCodeEx ()
No symbol table info available.
#33 0x080ba527 in PyEval_EvalCode ()
No symbol table info available.
#34 0x080ddb1a in PyRun_FileExFlags ()
No symbol table info available.
#35 0x080ddd07 in PyRun_SimpleFileExFlags ()
No symbol table info available.
#36 0x08055cc2 in Py_Main ()
No symbol table info available.
#37 0x08055132 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

I would really love to get this going - if anyone can help I would greatly appreciate it!  

Thanks in advance, Mike.

Oh, and if it is relevant, I am using beryl.

---

### Post by Stevi on 2007-06-01
Did you try [this .deb](http://www.getdeb.net/app.php?name=Gimmie)?

---

### Post by unabatedshagie on 2007-06-02
That deb file installs on my machine but if I click on Linux or Library it crashes. Doesn't matter if I'm using the panel version or the stand-alone version.

---

### Post by searayman on 2007-06-04
how can i get pidgin to work with this instead of gaim?

---

### Post by MadOsborn on 2007-06-08
> **unabatedshagie said:**
> That deb file installs on my machine but if I click on Linux or Library it crashes. Doesn't matter if I'm using the panel version or the stand-alone version.

Same thing here. Except that i'm compiled and instaled from source.

And the "Notification Area" disappear when Gimmie Crashses.

Any news about this bug?

---

### Post by FuturePilot on 2007-06-13
Will this run on Dapper? I got it to compile but it's not showing up when I go to Add to Panel.

---

### Post by FuturePilot on 2007-06-13
Ok, I got it to show up when I go to Add To Panel but it crashes every time I try to add it.:(

---

### Post by Benedolt on 2007-06-24
Good morning, everyone!

I am trying to compile Gimmie 0.2.7 from source and followed this howto closely. Everytime I turn to "make" though, it fails with the following error:

```

make[3]: Leaving directory `/home/myself/bin/gimmie/gimmie-0.2.7/gimmie'
make[2]: Leaving directory `/home/myself/bin/gimmie/gimmie-0.2.7/gimmie'
Making all in po
make[2]: Entering directory `/home/myself/bin/gimmie/gimmie-0.2.7/po'
file=`echo ar | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ar.po
/bin/sh: -o: not found
make[2]: *** [ar.gmo] Error 127
make[2]: Leaving directory `/home/myself/bin/gimmie/gimmie-0.2.7/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/myself/bin/gimmie/gimmie-0.2.7'
make: *** [all] Error 2

```

The crux seems to be the " /bin/sh: -o: not found" and the following error 127... Does anyone have an idea what's going wrong?

---

### Post by Unnicknamed on 2007-06-26
> **Benedolt said:**
> Good morning, everyone!

I am trying to compile Gimmie 0.2.7 from source and followed this howto closely. Everytime I turn to "make" though, it fails with the following error:

```

make[3]: Leaving directory `/home/myself/bin/gimmie/gimmie-0.2.7/gimmie'
make[2]: Leaving directory `/home/myself/bin/gimmie/gimmie-0.2.7/gimmie'
Making all in po
make[2]: Entering directory `/home/myself/bin/gimmie/gimmie-0.2.7/po'
file=`echo ar | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ar.po
/bin/sh: -o: not found
make[2]: *** [ar.gmo] Error 127
make[2]: Leaving directory `/home/myself/bin/gimmie/gimmie-0.2.7/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/myself/bin/gimmie/gimmie-0.2.7'
make: *** [all] Error 2

```

The crux seems to be the " /bin/sh: -o: not found" and the following error 127... Does anyone have an idea what's going wrong?

Try to install gettext, it worked for me. Then configure and make again.

---

### Post by Benedolt on 2007-06-27
Thanks a lot, Unnicknamed! Gimmie is compiling just fine now.
The applet doesn't show up in the "Add to panel" dialog though. How did you fix this, FuturePilot?

Any suggestions?

---

### Post by jusmurph on 2007-06-27
Installed Fine, Added it to the panel, Clicked the Linux Button and i get the following error:
Edit: Programs and People Work Fine so far... just the Linux button and the Library are a no go.


```
Distribution: Ubuntu 7.04 (feisty)
Gnome Release: 2.18.1 2007-04-11 (Ubuntu)
BugBuddy Version: 2.18.1

System: Linux 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64
X Vendor: The X.Org Foundation
X Vendor Release: 70200000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Glossy
Icon Theme: glass-icons

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0



----------- .xsession-errors (35 sec old) ---------------------
	   if (!g_thread_supported ()) g_thread_init(NULL);
	as very first thing in its main() function. Please file a bug
	against this application.
Launched application : 7249
md5sum: ubuntu-7.04-desktop-i386.iso: No such file or directory
(npviewer.bin:7784): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
(npviewer.bin:7784): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so: wrong ELF class: ELFCLASS64
Launched application : 12370
(avant-window-navigator:5955): GLib-GObject-WARNING **: gsignal.c:1741: instance `0x69e090' has no handler with id `46'
(avant-window-navigator:5955): GLib-GObject-WARNING **: gsignal.c:1741: instance `0x69e090' has no handler with id `47'
--------------------------------------------------
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/gimmie/gimmie_applet.py", line 516, in do_button_press_event
    self._show()
  File "/usr/lib/python2.5/site-packages/gimmie/gimmie_applet.py", line 521, in _show
    self.topic_win = self.topic.get_topic_window()
  File "/usr/lib/python2.5/site-packages/gimmie/gimmie_applet.py", line 393, in get_topic_window_mod
    self.topic_window = TopicMenu(self)
  File "/usr/lib/python2.5/site-packages/gimmie/gimmie_applet.py", line 181, in __init__
    TopicView.__init__(self, topic)
  File "/usr/lib/python2.5/site-packages/gimmie/gimmie_topicwin.py", line 926, in __init__
    self.sidebar = Sidebar(topic)
  File "/usr/lib/python2.5/site-packages/gimmie/gimmie_topicwin.py", line 860, in __init__
    self.add_sources()
  File "/usr/lib/python2.5/site-packages/gimmie/gimmie_topicwin.py", line 873, in add_sources
    for source in self.topic.get_sidebar_source_list():
  File "/usr/lib/python2.5/site-packages/gimmie/gimmie_base.py", line 311, in get_sidebar_source_list
    self.do_reload()
  File "/usr/lib/python2.5/site-packages/gimmie/gimmie_computer.py", line 736, in do_reload
    source_list.append(AdministrationSource())
  File "/usr/lib/python2.5/site-packages/gimmie/gimmie_computer.py", line 492, in __init__
    self.do_reload()
  File "/usr/lib/python2.5/site-packages/gimmie/gimmie_computer.py", line 495, in do_reload
    self.system_settings_menu_source = self.system_settings_menu_tree.get_toplevel_flat_source()
AttributeError: 'NoneType' object has no attribute 'get_toplevel_flat_source'
```

---

### Post by jusmurph on 2007-06-28
> **Benedolt said:**
> Good morning, everyone!

I am trying to compile Gimmie 0.2.7 from source and followed this howto closely. 
There is a 0.2.7?

What does that change? This looks like a very nice program, when it starts hitting stability.

---

### Post by Benedolt on 2007-06-28
> **jusmurph said:**
> There is a 0.2.7?

What does that change? This looks like a very nice program, when it starts hitting stability.

0.2.7 has some bug fixes and a slightly changed layout. Tarballs and release notes are here: [http://www.beatniksoftware.com/gimmie/Download](http://www.beatniksoftware.com/gimmie/Download)

Did anyone have a tip on why gimmie doesn't show up in my "Add to Panel" menu?

---

### Post by jusmurph on 2007-06-28
Nice, 0.2.7 Fixed my above bug!

---

### Post by unabatedshagie on 2007-06-28
> **Benedolt said:**
> 0.2.7 has some bug fixes and a slightly changed layout. Tarballs and release notes are here: [http://www.beatniksoftware.com/gimmie/Download](http://www.beatniksoftware.com/gimmie/Download)

Did anyone have a tip on why gimmie doesn't show up in my "Add to Panel" menu?Doesn't appear in mine either, I thought I had somehow messed up the installation.

---

### Post by gloscherrybomb on 2007-07-02
^ Also wondering how I get it to show up in the panel menu. Works with my current older version.

---

### Post by erwall on 2007-07-02
Enable universe repos

sudo aptitude install gimmie

Worked great for me.

---

### Post by LordMau on 2007-08-26
I'm also trying to compile 0.27 here.

I had to add python2.5-dev as that was the detected python version.

At the checksinstall stage, I get this from the log:

```
 trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is a
lso in package libgconf2-4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
```

Suggestion to fix this? Thanks

---

### Post by Benedolt on 2007-08-26
> **LordMau said:**
> I'm also trying to compile 0.27 here.

I had to add python2.5-dev as that was the detected python version.

At the checksinstall stage, I get this from the log:

```
 trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is a
lso in package libgconf2-4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
```

Suggestion to fix this? Thanks

LordMau, checkinstall doesn't really work with 0.2.7. Just install it the classic way with "sudo make install".

---

### Post by LordMau on 2007-08-30
Thanks will try that. In the meantime though I bit the bullet and got a deb at Getdeb. Seems ok for now.

But I need to change my file manager to thunar though. Any idea how to change gimmie default? It calls nautilus and overwrites my desktop as I'm using xfce.

Thanks.

EDIT:
awww gimmie's messing with my xfce session. Although I can lauch it as a panel applet, the thing is duplicate starting my autostarted programs, and starting its dock during cold starts. Man I was loving its design but if this behaviour is hardwired for now (looks like it assumes too much it's on a gnome environment) I have to pass on using it.

---

### Post by dennus on 2007-08-30
Guys!

I want to remove GIMMIE, but.. I don't know how to. When I use "sudo make uninstall" in a terminal screen I get a message saying there is no line (or command). Anyway, do I need to enter this in a particular directory?

---

### Post by dustigroove on 2007-09-02
[FONT=Arial][SIZE=2][COLOR=Black]> **dennus said:**
> Guys!

I want to remove GIMMIE, but.. I don't know how to. When I use "sudo make uninstall" in a terminal screen I get a message saying there is no line (or command). Anyway, do I need to enter this in a particular directory?


Yes, you should do this from the directory that contains the Gimmie source files.
[/COLOR][/SIZE][/FONT]

---

### Post by dennus on 2007-09-03
Okay, this is what I did;

sudo apt-get remove gimmie
and then
sudo apt-get autoremove

Before this didn't work, but it did now.

---

### Post by 1337455 10534 on 2007-11-10
Grr.
Gimmie looked cool, but it never loaded into teh system tray!
Unisntalling directions needed badly, nothhing works.
Where is teh exe located??

---

### Post by 1337455 10534 on 2007-11-10
I removed everything I could find (and shredded it too!) about Gimmie, and its still there!!!!!!
Restarting X...

---

### Post by kortez on 2008-07-18
Just in case nobody noticed 0.28 is out.
Anywho....
Does anybody know how to make gimmie look like this? [http://www.flickr.com/photos/26671354@N05/2504137368/]("http://www.flickr.com/photos/26671354@N05/2504137368/")
Apparently "it could be implemented without too much fuss."

I just found out that this is related to something larger
[https://wiki.ubuntu.com/Artwork/Incoming/Long_Term_Vision]("https://wiki.ubuntu.com/Artwork/Incoming/Long_Term_Vision")
[https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Gimmie-Human]("https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Gimmie-Human")

---

