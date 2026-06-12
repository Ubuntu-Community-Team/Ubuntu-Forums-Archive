---
title: "A simple program to check if a webpage has been updated?"
date: 2007-03-26
forum: Outdated Tutorials &amp; Tips
---

### Post by bashologist on 2007-03-26
Description:
[INDENT]A simple python script that when first run downloads a webpage for each url in a file, then each time after it's run checks the old file for changes. If there's a change detected it opens firefox! Execute the program with a "-v" option for more output.[/INDENT]

To setup the script from your bash terminal:
[INDENT]**mkdir ~/.checkurls; nano ~/.checkurls/checkurls.py**
Copy and paste the below code in the file and save it with **ctl+x** then **y** then **Enter**
**sed -i "s/\$USER/$USER/g" ~/.checkurls/checkurls.py**
Link to the file with **sudo ln -s ~/.checkurls/checkurls.py /usr/bin/checkurls**
**sudo chmod a+x /usr/bin/checkurls; nano ~/.checkurls/urls.txt**
Then enter some urls seperated by newlines into the file and you're done! It's not too hard, only takes a few seconds. n_n
[/INDENT]

Script:
```
#!/usr/bin/env python
import os, sys, urllib
savepath = '/home/$USER/.checkurls/'

errormsg = '%s: %s: No such file or directory'
urlspath = savepath + 'urls.txt'
for path in savepath, urlspath:
	if not os.path.exists(path):
		print errormsg % (__file__, path)
		sys.exit(0)
urlfile = open(urlspath, 'r').readlines(); urlstring = ''
for url in urlfile:
	if not 'http://' in url:
		url = 'http://' + url
	url = url.replace('\n', '')
	filename = url.replace('/', '%2f')
	if '-v' in sys.argv:
		print '%s: %s ...' % (__file__, url)
	if not os.path.isfile(savepath + filename):
		urllib.urlretrieve(url, savepath + filename)
	filelines = open(savepath + filename, 'r').readlines()
	urllines = urllib.urlopen(url).readlines()
	if not filelines == urllines:
		open(savepath + filename, 'w').writelines(urllines)
		urlstring += '"' + url + '" '

if urlstring:
	os.popen('firefox ' + urlstring)
else:
	if '-v' in sys.argv:
		print '%s: nothing for today' % __file__
```

Making the script run when your computer starts:
[INDENT][[IMG]http://img171.imagevenue.com/loc490/th_42266_screen2_122_490lo.jpg[/IMG]](http://img171.imagevenue.com/img.php?image=42266_screen2_122_490lo.jpg)[/INDENT]

---

### Post by bashologist on 2007-07-11
GTK-CHECKURLS(1)

Manual:
```
GTK-CHECKURLS(1)                 User Commands                 GTK-CHECKURLS(1)

NAME
       gtk-checkurls - check web pages for changes

SYNOPSIS
       gtk-checkurls [ --check ] [ --edit ]

DESCRIPTION
       Notify  the  user  when  a  web page changes to make their life easier. Keyboard
       shortcuts for managing URLs and the ability to add multiple URLs  simultaneously
       makes adding and editing very easy.

OPTIONS
       -c --check
              Check URLs.

       -e --edit
              Edit URLs.

AUTHOR
       Written by Ben Dover

REPORTING BUGS
       Report bugs to <bashologist@gmail.com>.

gtk-checkurls 1.5                  July 2007                   GTK-CHECKURLS(1)
```
Tutorial1:
[INDENT][[IMG]http://img135.imagevenue.com/loc213/th_94592_tutorial1_122_213lo.jpg[/IMG]](http://img135.imagevenue.com/img.php?image=94592_tutorial1_122_213lo.jpg)[/INDENT]
Tutorial2:
[INDENT][[IMG]http://img170.imagevenue.com/loc471/th_94599_tutorial2_122_471lo.jpg[/IMG]](http://img170.imagevenue.com/img.php?image=94599_tutorial2_122_471lo.jpg)[/INDENT]
Included Files:
```
usr/
usr/bin/
usr/bin/gtk-checkurls.py
usr/share/
usr/share/menu/
usr/share/menu/gtk-checkurls
usr/share/man/
usr/share/man/man1/
usr/share/man/man1/gtk-checkurls.1.gz
usr/share/applications/
usr/share/applications/gtk-checkurls.desktop
usr/share/pixmaps/
usr/share/pixmaps/gtk-checkurls.png
usr/bin/gtk-checkurls
```

---

### Post by Ter Rymon on 2008-12-26
How do I get this script to run every ten minutes... I teach online and need to check message boards throughout the day. 

Sorry, I'm new to Ubuntu and linux.  I managed to install this deb package and added the script to startup.  

Give details if you can...

Any help appreciated.

---

### Post by deadowl on 2008-12-27
> **Ter Rymon said:**
> How do I get this script to run every ten minutes... I teach online and need to check message boards throughout the day. 

Sorry, I'm new to Ubuntu and linux.  I managed to install this deb package and added the script to startup.  

Give details if you can...

Any help appreciated.
```
crontab -e
```
type in the file:
```
*/10 * * * * /path/to/script
```

Refer to: [http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

---

### Post by Ng Oon-Ee on 2008-12-27
> **Ter Rymon said:**
> How do I get this script to run every ten minutes... I teach online and need to check message boards throughout the day. 

Sorry, I'm new to Ubuntu and linux.  I managed to install this deb package and added the script to startup.  

Give details if you can...

Any help appreciated.
Just to mention, if you're using firefox there's plugins that perform a similar duty. The one I'm currently using is called "Update Scanner". Give it a try, from the official addons.mozilla.com site, you may find it useful. Serves a slightly different purpose from this script here, may be more to your liking.

---

