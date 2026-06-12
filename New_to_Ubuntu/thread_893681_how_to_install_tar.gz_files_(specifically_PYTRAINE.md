---
title: "how to install tar.gz files (specifically PYTRAINER)"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by binobooks on 2008-08-18
Can someone give me a step by step walk through with what I need to do to install a program from the web in tar.gz file once I downloaded it from the web onto my desktop.  

I downloaded pytrainer-1.5.0.0.1.tar.gz .  What commands do I need to do now. I have Ubuntu 8.0.4 

Thank You

---

### Post by Tomosaur on 2008-08-18
> **binobooks said:**
> Can someone give me a step by step walk through with what I need to do to install a program from the web in tar.gz file once I downloaded it from the web onto my desktop.  

I downloaded pytrainer-1.5.0.0.1.tar.gz .  What commands do I need to do now. I have Ubuntu 8.0.4 

Thank You

Hi binobooks!

A .tar.gz file is a compressed file - like .zip.

If you double click the file, the archive manager should launch and allow you to extract the files inside (Alternatively, you could just right-click the file and select 'Extract').

From there - it really depends what's inside the file. Lots of the time, if a program you've downloaded comes in an archived format like this, it means you've downloaded the source code and will need to compile it.

However, I took a look at the PyTrainer website, and they actually give instructions on how to download the software for Ubuntu users: [http://pytrainer.e-oss.net/download.php](http://pytrainer.e-oss.net/download.php)

**Instructions**
1: Place the file you have downloaded into your home directory.
2: Open a terminal and type 'cd ~' to make sure you are in your home directory.
3: Type the following commands:
```

sudo apt-get install python2.5 python2.5-libxml2 python2.5-pysqlite2 python2.5-glade2 python2.5-gtk2
python-matplotlib python-soappy firefox python-soappy gpsbabel

tar zxvf pytrainer-1.5.0.0.1.tar.gz

cd pytrainer-1.5.0.0.1

python ./pytrainer.py

```

This should run pytrainer. If you want to create a launcher all you need to do is right click on your desktop and use 'python ~/pytrainer-1.5.0.0.1/pytrainer.py' as the command.

Hope that helps!

---

### Post by LTFC2020 on 2008-08-18
I think .tar.gz is for other linux users i.e. not ubuntu
did you get it from this page?
[http://pytrainer.e-oss.net/download.php](http://pytrainer.e-oss.net/download.php)

as there appears to be ubuntu downloads that can be run from the terminal

/etc/apt/sources.list

deb [http://www.e-oss.net/debian](http://www.e-oss.net/debian) ./

---

### Post by binobooks on 2008-08-18
I see those for ubuntu.. but none are for hardy.. I tried installing the gusty version and it did not work.  can't I go to the linux version and install a tar.gz file somehow.  I have come across this file before on another site and didn't know how to do it.  I want to know for future encounters as well.  Thanks

---

### Post by Nepherte on 2008-08-18
At the bottom of [http://pytrainer.e-oss.net/download.php](http://pytrainer.e-oss.net/download.php) are instructions that should work for you.

---

### Post by binobooks on 2008-08-18
That stuff doesn't work
nothing happens at any of those commands

---

### Post by LTFC2020 on 2008-08-18
yeah 8.04 sorry about that :rolleyes:

this should help

[http://monkeyblog.org/ubuntu/installing.html#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing.html#installing_a_package_manually)

---

### Post by binobooks on 2008-08-18
Is there not some standard commands for installing a tar.gz file... i have seen some but none take you step by step... alot skip steps.  I need to know what to do after I download the tar.gz package.  Thanks

---

### Post by Tomosaur on 2008-08-18
> **binobooks said:**
> That stuff doesn't work
nothing happens at any of those commands

Try the commands I just added to my post, they should work fine :)

---

### Post by binobooks on 2008-08-18
They don't work... the directions a a little confusing.. after I put input make.... it keeps on asking me for my email address which I enter but keeps on going in circles.

---

### Post by binobooks on 2008-08-18
Is the following your email address?
  binobooks@binobooks-desktop
Please confirm by pressing Return, or enter your email address.
[email]binobooks@gmail.com[/email]
A translation team for your language (es) does not exist yet.
If you want to create a new translation team for es, please visit
  [http://www.iro.umontreal.ca/contrib/po/HTML/teams.html](http://www.iro.umontreal.ca/contrib/po/HTML/teams.html)
  [http://www.iro.umontreal.ca/contrib/po/HTML/leaders.html](http://www.iro.umontreal.ca/contrib/po/HTML/leaders.html)
  [http://www.iro.umontreal.ca/contrib/po/HTML/index.html](http://www.iro.umontreal.ca/contrib/po/HTML/index.html)

Created ./locale/es/LC_MESSAGES/pytrainer_es.pot.
make[1]: Leaving directory `/home/binobooks/pytrainer-1.5.0.0.1'
make locale_eu
make[1]: Entering directory `/home/binobooks/pytrainer-1.5.0.0.1'
msginit -i ./messages.pot -l eu -o ./locale/eu/LC_MESSAGES/pytrainer_eu.pot
The new message catalog should contain your email address, so that users can
give you feedback about the translations, and so that maintainers can contact
you in case of unexpected technical problems.

Is the following your email address?
  binobooks@binobooks-desktop
Please confirm by pressing Return, or enter your email address.

---

### Post by binobooks on 2008-08-18
here is my terminal when I follow the instructions.  
> binobooks@binobooks-desktop:~$ pwd
/home/binobooks
binobooks@binobooks-desktop:~$ ls
Desktop                                Music
Documents                              MyDownloads
Examples                               picasa_2.7.3736-15_i386.deb
google-desktop-linux_current_i386.deb  Pictures
googleearth                            Public
google-earth                           pytrainer-1.5.0.0.1
GoogleEarthLinux.bin                   pytrainer-1.5.0.0.1.tar.gz
google-gadgets-for-linux-0.9.1         Templates
google-gadgets-for-linux-0.9.1.tar.gz  utube_1.7-1_i386.gtk.deb
google-repo-setup.sh                   Videos
linux_signing_key.pub
binobooks@binobooks-desktop:~$ ./configure
bash: ./configure: No such file or directory
binobooks@binobooks-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
binobooks@binobooks-desktop:~$ 



---

### Post by Tomosaur on 2008-08-18
That is meant for developers only, it turns out you don't need to compile pytrainer.

Go back to my post and just follow the instructions which I have added (not the link to the instructions). They work - as I have just used them myself to get pytrainer running.

There is no pre-set way to install .tar.gz files, because they are just archives. It's the same kind of thing as .zip file or a .rar file.

---

### Post by aysiu on 2008-08-18
I had no problem installing the Gutsy version in Hardy, but when I tried to run the program afterwards, I got this: ```
 pytrainer
Traceback (most recent call last):
  File "/usr/bin/pytr", line 38, in <module>
    from pytrainer.main import pyTrainer
  File "/usr/lib/python2.5/site-packages/pytrainer/main.py", line 38, in <module>
    from extensions.googlemaps import Googlemaps
  File "/usr/lib/python2.5/site-packages/pytrainer/extensions/googlemaps.py", line 19, in <module>
    import gtkmozembed
ImportError: No module named gtkmozembed
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_pytr.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/pytr", line 38, in <module>
    from pytrainer.main import pyTrainer
  File "/usr/lib/python2.5/site-packages/pytrainer/main.py", line 38, in <module>
    from extensions.googlemaps import Googlemaps
  File "/usr/lib/python2.5/site-packages/pytrainer/extensions/googlemaps.py", line 19, in <module>
    import gtkmozembed
ImportError: No module named gtkmozembed
``` Installing was as simple as downloading [this file](http://www.e-oss.net/ubuntu/gutsy/pytrainer_1.5.0.0.1-1_all.deb) and double-clicking it.

---

### Post by binobooks on 2008-08-18
Okay.. seems to start working... however, when I got to the last code, this is what I got.. 
> binobooks@binobooks-desktop:~/pytrainer-1.5.0.0.1$ python ./pytrainer.py
Traceback (most recent call last):
  File "./pytrainer.py", line 39, in <module>
    from pytrainer.main import pyTrainer
  File "/home/binobooks/pytrainer-1.5.0.0.1/pytrainer/main.py", line 38, in <module>
    from extensions.googlemaps import Googlemaps
  File "/home/binobooks/pytrainer-1.5.0.0.1/pytrainer/extensions/googlemaps.py", line 19, in <module>
    import gtkmozembed
ImportError: No module named gtkmozembed
binobooks@binobooks-desktop:~/pytrainer-1.5.0.0.1$ 


---

### Post by Tomosaur on 2008-08-18
> **binobooks said:**
> Okay.. seems to start working... however, when I got to the last code, this is what I got..

Ok that's easy enough to fix, just run thiscommand and then try running pytrainer again:

```

sudo apt-get install python-gnome2-extras

```

Pytrainer seems to suffer from some serious lack of documentation!

---

### Post by binobooks on 2008-08-18
Okay... great.. it loads up when I enter the last command into the terminal... however, I made the desktop launcher and put in exactly what you told me to... it will not launch from there... no error messages... just nothing happens.

---

### Post by binobooks on 2008-08-18
Also, for future reference, how do a place a file in my home directory... is my desktop my home directory?

---

### Post by Tomosaur on 2008-08-18
> **binobooks said:**
> Also, for future reference, how do a place a file in my home directory... is my desktop my home directory?

No, your home directory is different from your Desktop (more accurately speaking, your Desktop is a folder within your home directory).

To move a file from your desktop to your home directory, just open the home directory in a file browser (if you're using the Gnome desktop environment, just click 'Places', then 'Home Folder'). From there you can just drag and drop the file into your home folder.

The launcher instructions should work - but the instructions I gave would work only if the pytrainer directory was in your home directory (in the command line, the tilde character - '~' - signifies 'Home').

---

### Post by binobooks on 2008-08-18
I really appreciate all of your help.  I am learning so much.  I opened the home folder under the places tab and it showed both the tar.gz file and the regular pytrainer file in it .. does this mean the directory is there as well, how do I check.    I still can not open program with the launcher.  A few more questions.  If I eventually get it to work, can I put the program into the drop down applicatons heading on the toolbar? How would I go about removing the program (sudo apt-get remove pytrainer)?  Thanks again for your help.

---

### Post by binobooks on 2008-08-18
I tried the package install ... that was easy .. Thanks everybody for the help...

---

### Post by Tomosaur on 2008-08-18
> **binobooks said:**
> I really appreciate all of your help.  I am learning so much.  I opened the home folder under the places tab and it showed both the tar.gz file and the regular pytrainer file in it .. does this mean the directory is there as well, how do I check.    I still can not open program with the launcher.  A few more questions.  If I eventually get it to work, can I put the program into the drop down applicatons heading on the toolbar? How would I go about removing the program (sudo apt-get remove pytrainer)?  Thanks again for your help.

When you extract a directory, the actual archived directory isn't removed - so its normal to see both the archived file and the extracted directory - no need to worry about that :)

The launcher issue seems to be my mistake - apparently launchers don't recognise the tilde character, so you need to use the full path to the file. Let's say your user-name is 'fred', then rather than using the '~', you should use '/home/fred'

Just replace the 'fred' with whatever your username is, and it should work.

To include a launcher in the menu, just right click the 'applications' menu and choose 'edit menus'. It's then fairly self explanatory how to add a new menu item. When it asks you for the command, just use the same command in the launcher you just made.

Since you haven't actually 'installed' the software, all you need to do to get rid of it is to just delete the pytrainer directory, then remove the menu item manually.

---

### Post by muzzmackay on 2008-09-28
I have been following Binobooks problem and the brilliant help offered by Tomosaur. I have managed to install Pytrainer but have a slightly different output when I run it. Can you help ?

Traceback (most recent call last):
  File "./pytrainer.py", line 39, in <module>
    from pytrainer.main import pyTrainer
  File "/home/muzz/pytrainer-1.5.0.0.1/pytrainer/main.py", line 33, in <module>
    from recordgraph import RecordGraph
  File "/home/muzz/pytrainer-1.5.0.0.1/pytrainer/recordgraph.py", line 19, in <module>
    from gui.drawArea import DrawArea
  File "/home/muzz/pytrainer-1.5.0.0.1/pytrainer/gui/drawArea.py", line 19, in <module>
    import matplotlib
ImportError: No module named matplotlib

---

### Post by unutbu on 2008-09-28
muzzmackay, it looks like you need to install the package named python-matplotlib.

---

