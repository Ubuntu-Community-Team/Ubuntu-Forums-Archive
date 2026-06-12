---
title: "mswinurl - Those URL files from WinDozer"
date: 2006-12-23
forum: Outdated Tutorials &amp; Tips
---

### Post by psych787 on 2006-12-23
I have a huge number of .URL files on my drive since I have never used bookmarking... its so much more efficient to drop links into folders, and far more flexible.

Unfortunately, GNOME uses a different format and won't accept the windoze URL file under any circumstances. The only option is to open the URL file in a text editor and grab the url with copy --> paste. ](*,) 

So here's how to open that URL file automatically:

First create this script and name it url.sh:
```

#!/bin/bash

IFS=$'©'

FFOPENURL=$(grep -a -G URL=* $1)

firefox ${FFOPENURL#*=}

```
That will find the URL in the .URL file, and open firefox with it. To test it, try this in a terminal:
```

bash <dir>/url.sh <path to URL file>

```

Now enter these commands:
```

sudo cp <path to url.sh> /usr/bin
sudo sudo chmod ugoa+x /usr/bin/url.sh

```
Or anywhere else you want it to go. I prefer /usr/bin because its easy to remember. (PATH won't help us here however since this isn't exactly a command)

Finally its time to associate the [Internet Shortcut] or .URL file format in GNOME/Nautilus.
Right click on a .URL file and go to the "open with" tab. Associate it with this command:
```

bash /usr/bin/url.sh

```
If all goes well, you can now open the url file in FireFox.

If all doesn't go well (it didn't for me) you will get an error about insecure filetype... bla bla bla. If that happens, associate the file with a text editor and right click the file to get "open with bash".
Note: this quirk is not present in KDE!

Edit: Here are some keywords that might make this tutorial more searchable.
Microsoft Windows url file .url shell script interoperability internet shortcut how to plain text mswinurl bookmark microsoft windows

---

### Post by psych787 on 2007-07-13
Has anyone else actually used this? :confused:

---

### Post by Nebby on 2007-07-19
Yeah, I've got it working beautifully in Kubuntu.
Try this one:
[http://ubuntuforums.org/showthread.php?t=495131]("http://ubuntuforums.org/showthread.php?t=495131")

Note: as one of the lower posts said, the code should be changed from
```
chop($in);
```
to
```
chomp($in); 
```

---

### Post by psych787 on 2007-07-26
I saw that one... that was the thread that made me think no one was using this little script. (I posted there)

Thanks for the reply, glad to know it was useful :D.

---

### Post by lebrun on 2007-08-05
I've modified the script to open whatever browser you have configured as default in KDE:

```
#!/bin/bash
IFS=$'©'
FFOPENURL=$(grep -a -G URL=* $1 | tr '\r' '\n')
kfmclient openURL ${FFOPENURL#*=}
```

I also added a call to 'tr' to clean out windows-style line ends (character 0D)

I think in Gnome you have to use gnome-open instead of kfmclient, but I don't run Gnome.

---

### Post by psych787 on 2007-08-17
Great idea! I've been hunting for the tool to use KDE associations from the command line for weeks! Thanks! :biggrin:

---

### Post by tiggsy on 2008-05-12
This is great. Thanks for working this out.:KS

---

### Post by RATM_Owns on 2008-05-12
What would you do to open it in the current Firefox window in a new tab?

---

### Post by harmonysystems on 2008-09-05
psych787, thanks for this post. I followed your steps, and it worked perfectly the first time. Your help is much appreciated!

---

### Post by percivjr on 2008-12-01
Thanks for this. Some of my windoze shortcuts also had this in them, e.g.:

[DEFAULT]
BASEURL=http://www.....

My solution was to add a 'newline' to the grep regular expression:

```
#!/bin/bash
IFS=$'©'
FFOPENURL=$(grep -a -G ^URL=* $1 | tr '\r' '\n')
firefox  ${FFOPENURL#*=}
```

Note that I also deleted 'openURL' since it just seemed to open [www.openurl.com](www.openurl.com) !!

---

### Post by Endolith on 2009-03-25
I added a [more robust Python script]("http://launchpadlibrarian.net/20406796/mswinurl_launcher.py") in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-mime-data/+bug/185165"), and there is information on MIME type setup to make it work by default.

[http://gist.github.com/77635](http://gist.github.com/77635)

I don't know why this is taking so long to fix.

The only thing it's missing is to make the [InternetShortcut] magic word override the .url glob in the MIME setup.  I'm sure *someone *knows how to do this...

---

