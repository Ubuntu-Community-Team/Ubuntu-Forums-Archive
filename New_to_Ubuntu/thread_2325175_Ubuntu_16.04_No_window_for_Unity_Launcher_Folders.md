---
title: "Ubuntu 16.04 No window for Unity Launcher Folders"
date: 2016-05-19
forum: New to Ubuntu
---

### Post by Dave_Ballard on 2016-05-19
I am a brand new Ubuntu user. I installed the 16.04 distribution and wanted to modify the launcher to contain folders. A bit of Google searching pointed me to the Unity Launcher Folders package. I installed it, but when launching it the icon appeared in the launcher without the pop up window needed to use it. I even installed Gdebi and reinstalled the deb package with that. Still no window. I tried several Google searches looking for the problem. I did not find anything useful from the searches. 

I then tried installing the drawers package but that had the same problem (No window for use).

The following is from my syslog file. I do not know if this is related to the problem or not but thought I should include it.

My thanks to anyone who can help.

May 19 13:29:11 W2VK systemd[1]: Started Hostname Service.
May 19 13:29:12 W2VK gnome-session[1289]: Nautilus-Share-Message: Called "net usershare info" but it failed: Failed to execute child process "net" (No such file or directory)
May 19 13:29:13 W2VK org.gtk.vfs.Daemon[1173]: ** (process:2333): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
May 19 13:29:13 W2VK org.gtk.vfs.Daemon[1173]: ** (process:2328): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
May 19 13:29:16 W2VK org.gtk.vfs.Daemon[1173]: ** (process:2333): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
May 19 13:29:33 W2VK org.gnome.zeitgeist.SimpleIndexer[1173]: ** (zeitgeist-fts:1701): WARNING **: Unable to get info on application://nautilus-autostart.desktop

---

### Post by CantankRus on 2016-05-19
unity-launcher-folders works here on 16.04.
I downloaded the latest deb file from [**_[COLOR="#B22222"]HERE[/COLOR]_**]("https://launchpad.net/~asukhovatkin/+archive/ubuntu/unity-launcher-folders/+files/unity-launcher-folders_14.09.5_all.deb") <-----This is a direct download link to deb file from authors ppa.
Are you using it correctly ...[**_[COLOR="#B22222"]youtube video[/COLOR]_**]("https://www.youtube.com/watch?v=Hlvl0OaMtH0")

Try opening from a terminal...
```
unity-launcher-folders
```
I get some gtk errors but configuration window still opens.

---

### Post by Dave_Ballard on 2016-05-20
Thanks for the response.

Re the video: Yes, I saw the video before I installed the package. It didn't help since I don't get the app window to use.

Re starting from the terminal: Thanks for the idea, I hadn't thought of trying that. Here is the result.

Traceback (most recent call last):
  File "/usr/bin/unity-launcher-folders", line 46, in <module>
    import unity_launcher_folders
  File "/usr/lib/python2.7/dist-packages/unity_launcher_folders/__init__.py", line 21, in <module>
    from gi.repository import Gtk, Gdk, GdkPixbuf, Pango, Gio
ImportError: No module named gi.repository

Based on this result, I am guessing that I need to install a package. You may have gotten the missing module as a dependency when you installed other packages after your 16.04 install which is why it works for you. I may try installing the python-gobject package since google lists that as a cure for a missing gi module (Not gi.repository module).

I tried installing from the developer's PPA, but that install still didn't fix the problem. I will use Gdebi to reinstall the developer's package to see if that will resolve any missing dependencies.

---

### Post by CantankRus on 2016-05-20
I have **python-gobject** which is a dependency of various applications I have installed (glipper kupfer pluma pulseaudio-dlna python-appindicator screenkey y-ppa-manager).
I also have **python-gobject-2** installed.
Both installed from official repos.
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] apt-cache policy python-gobject**
python-gobject:
  Installed: 3.20.0-0ubuntu1
  Candidate: 3.20.0-0ubuntu1
  Version table:
 *** 3.20.0-0ubuntu1 500
        500 http://ftp.iinet.net.au/pub/ubuntu xenial/universe amd64 Packages
        500 http://ftp.iinet.net.au/pub/ubuntu xenial/universe i386 Packages
        100 /var/lib/dpkg/status
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] apt-cache policy python-gobject-2**
python-gobject-2:
  Installed: 2.28.6-12ubuntu1
  Candidate: 2.28.6-12ubuntu1
  Version table:
 *** 2.28.6-12ubuntu1 500
        500 http://ftp.iinet.net.au/pub/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by CantankRus on 2016-05-21
Did some testing from a live Xenial cd and this is how I got it to run.
Installed unity-launcher-folders.
Then...
```
sudo apt install python-gobject python-pil
```

Edited /usr/lib/python2.7/dist-packages/unity_launcher_folders/generateIcon.py ....
```
gksudo gedit /usr/lib/python2.7/dist-packages/unity_launcher_folders/generateIcon.py
```

Change line #17..
```
import Image
```

to 
```
from PIL import Image
```

---

### Post by Dave_Ballard on 2016-05-22
Thanks CantankRus. I haven't checked the thread for a day or two but when I did, I found your last post. I had installed python.gobject and received the error about the PIL Image module missing. I followed the commands in your post and now have a Tools folder and an Office folder in my launcher. :D:D

To summarize, Xenial Xerus has releases of Python packages but not the basic ones. Installing them solved the problem. (Drawers now works as well). I noticed that I now get the warning that the version to be used is not specified, but I think that is just a warning.

Thanks again. I am marking the thread as solved.

---

### Post by ajmalj on 2016-10-16
> **CantankRus said:**
> Did some testing from a live Xenial cd and this is how I got it to run.
Installed unity-launcher-folders.
Then...
```
sudo apt install python-gobject python-pil
```

Edited /usr/lib/python2.7/dist-packages/unity_launcher_folders/generateIcon.py ....
```
gksudo gedit /usr/lib/python2.7/dist-packages/unity_launcher_folders/generateIcon.py
```

Change line #17..
```
import Image
```

to 
```
from PIL import Image
```

Thanks it worked!:D

---

### Post by mazoerkam on 2017-03-06
thaks for me also

---

### Post by saiunuk on 2017-04-07
A simple question: How many Drawers you can have? Is there any limit?

For example, I made 4 drawers, and when I'm trying to add one more, it doesn't appear in the launcher :(

[IMG]https://c2.staticflickr.com/4/3736/33850821556_4c742e66b5_b.jpg[/IMG]

ps. Great piece of software, and I think it should be included in Ubuntu distro by default.

---

