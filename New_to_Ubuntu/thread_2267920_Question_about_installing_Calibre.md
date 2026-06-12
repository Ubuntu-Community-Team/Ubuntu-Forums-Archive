---
title: "Question about installing Calibre"
date: 2015-03-04
forum: New to Ubuntu
---

### Post by penny3 on 2015-03-04
I was thinking of installing this program and notice that the website states: 'You must have xdg-utils, wget and python &#8805; 2.6 installed on your system before running the installer.' I installed Ubuntu last week. Are these systems part of the normal Ubuntu platform or should I do a search and make sure they are installed? Can I assume that if I tried downloading this program, if I didn't have them installed the OS would simply give me an error message? Sorry for the questions and being too timid to just 'go ahead and try it' but I'm afraid I am of the old school of 'better to ask a question and look like an idiot than assume and prove it.'

---

### Post by sandyd on 2015-03-04
> **penny3 said:**
> I was thinking of installing this program and notice that the website states: 'You must have xdg-utils, wget and python &#8805; 2.6 installed on your system before running the installer.' I installed Ubuntu last week. Are these systems part of the normal Ubuntu platform or should I do a search and make sure they are installed? Can I assume that if I tried downloading this program, if I didn't have them installed the OS would simply give me an error message? Sorry for the questions and being too timid to just 'go ahead and try it' but I'm afraid I am of the old school of 'better to ask a question and look like an idiot than assume and prove it.'

Few things
- Normally, you can install calibre through Ubuntu Software Center.
- However, sometimes the version in the repos is broken (I am running KDE Plasma 5 beta and Calibre doesn't seem to like it :|). It's outdated sometimes as well.

**Testing to see if version in repos work:**
Install Calibre using Ubuntu Software Center and see if you can open it.
If it cannot be opened, uninstall it with the command below:
```

sudo apt-get purge calibre
```

**Install using calibre script**
The script mentions that it requires xdg-utils, wget and python.

Lets check if their installed
```

sandyd@sandyd-mobile:~$ dpkg -l | grep -i 'xdg-utils\|wget\|python2.7 '
ii  python2.7                                     2.7.8-10ubuntu1                                        amd64        Interactive high-level object-oriented language (version 2.7)
ii  wget                                          1.15-1ubuntu1.14.10.1                                  amd64        retrieves files from the web
ii  xdg-utils                                     1.1.0~rc1-2ubuntu8                                     all          desktop integration utilities from freedesktop.org
```
According to dpkg, they are installed.
The command dpkg -l lists all packages that are installed on the system.

If something is not installed, you can either
[LIST]
[*]a) Do an apt-cache search to see what the program name is
```

sandyd@sandyd-mobile:~$ apt-cache search wget
devscripts - scripts to make the life of a Debian Package maintainer easier
texlive-latex-extra - TeX Live: LaTeX additional packages
[COLOR="#FF0000"]wget - retrieves files from the web[/COLOR]
abcde - A Better CD Encoder
apt-mirror - APT sources mirroring tool
apt-zip - Update a non-networked computer using apt and removable media
axel - light download accelerator - console version
axel-dbg - light download accelerator - debugging symbols
axel-kapt - light download accelerator - graphical front-end
filetea - Web-based file sharing system
getdata - management of external databases
libcupt3-0-downloadmethod-wget - flexible package manager -- wget download method
puf - Parallel URL fetcher
pwget - downloader utility which resembles wget (implemented in Perl)
snarf - A command-line URL grabber
wput - tiny wget-like ftp-client for uploading files

```

Above, I have found the package name is 'wget'. This can be done for any other package as well.
[*]b) Use [http://packages.ubuntu.com](http://packages.ubuntu.com) to search.
[/LIST]

After you've found the package name, use the command
```

sudo apt-get install *packagename*
```
to install the package.

You can add multiple package names, separated by spaces.

Now that everything is installed, we can run the installer
```

sudo -v && wget -nv -O- https://raw.githubusercontent.com/kovidgoyal/calibre/master/setup/linux-installer.py | sudo python -c "import sys; main=lambda:sys.stderr.write('Download failed\n'); exec(sys.stdin.read()); main()"

```

Hope that helps,

---

### Post by Bucky Ball on 2015-03-04
As mentioned above, ALWAYS best to look in the Software Centre first. The version in there is fully supported and should work and will be updated. Only if that doesn't work start using a third-party PPA.

When you install via the Software Centre, all dependencies will be dragged in (i.e. the dependencies you mention you need to have installed) by installing the program you are installing, whether it be Calibre or something else. For a better look 'behind the scenes' at what goes on and what dependecies are being installed, install Synaptic Package Manager and install Calibre via that. Right click Calibre after you've searched>properties>have a look at what it is going to drag in when you install.

Good luck.

---

### Post by JeQhdMD on 2015-03-04
Good info from Sandyd . . . 

IF you're running Ubuntu with the standard Unity desktop - - Calibre will install and run fine from the Ubuntu Software Center.   It's a full-featured e-reader program and may take a little time to fully learn.  At first, just go with the "generic" when the setup wizard asks for your preferences.

By the way . . . the main lesson (from this thread) should be you don't go around the web finding software to install.   Always go to the official repositories (the Ubuntu Software Center) FIRST and 99% of the time, those programs will run fine on your system.   Later on, you can learn a few additional ways to install software.

---

### Post by penny3 on 2015-03-05
Thank you all for your great help here! Sandyd - your post was extremely informative and I learned a few more things from it.  Bucky and JeQhMD, thanks for the head up re Software Applications. I had taken a look in there and couldn't find it the first time around just by clicking the various sub-menus. This time I typed in the 'Calibre' in the search button and, of course, there it was. Also you have inadvertently answered another niggly thing for me. Quite a few times I have noticed in the various threads that I have been reading that a certain number of people seem to advocate always installing a program via commands from the terminal if possible. I may well have misunderstood what I was reading but it seemed to me that the jist was that, if there was a way to install a program via code, then that was preferable than using the Software Application. I probably didn't understand. 

I will take your advice as, for me, it is much easier to let the system download a program anyway!  Again - thank you all for your great response.

---

### Post by Bucky Ball on 2015-03-05
Installing from the Software Centre of Synpatics is pretty much EXACTLY the same as installing in a terminal. When you choose to install a program with SC or Synaptics, it is basically a front-end for the code. 

Say you install Calibre from SC or Synaptics. Either of them will issue the terminal code:

```
sudo apt-get install calibre
```

... behind the scenes. SC, Synaptics, terminal: makes NO difference. ;)

---

