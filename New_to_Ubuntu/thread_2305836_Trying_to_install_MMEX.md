---
title: "Trying to install MMEX"
date: 2015-12-09
forum: New to Ubuntu
---

### Post by ericj2 on 2015-12-09
New to Linux, but learning. I have a lot now set up on a dual boot machine (actually 3 of them).

Still very muddy on the syntax for a lot of things, but muddling along.

Today I tried to install MMEX (Money Manager EX) which i have used in the Windows environment but is part of my migration to Ubuntu.

I followed the instructions using the terminal mode and it seemed everything was working until the end when I got this error:

"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 mmex : Depends: libwxgtk2.9-0-unofficial (>= 2.9.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages."

Anyone know if/how to correct this with a newbie explanation?

Appreciate any help

---

### Post by grahammechanical on 2015-12-09
To fix a broken package situation we run the recommended command

```
sudo apt-get install -f
```

and we see what that does. Where did you get the application from? Here?


[URL="http://www.moneymanagerex.org/download#LinuxInstall"]http://www.moneymanagerex.org/download#LinuxInstall

[/URL]Does it download a deb package? What installation instructions are you following? And what version of Ubuntu are you using?

Regards.

---

### Post by ericj2 on 2015-12-09
Yes I got it there, running Ubuntu 14.04

I will try your  suggested command shortly. Unlike Windows where I always knew what was  being downloaded and where I am still unfamiliar with the Linux file  structure or where things get downloaded to using the terminal window.

Was  pretty familiar with MS-DOS and Windows but want to get away from MS if  I can. With Windows I never downloaded anything to the default location  and I knew what was going on with my files but not so much here  although I do see where "most" of my programs/apps are going. I see  where I can get the .deb file but not sure how to deal with it other  than download it.

Thanks for the help!

---

### Post by ericj2 on 2015-12-09
This is what I tried to install it:

To install mmex on Ubuntu Linux:
 [INDENT] sudo apt-get install python-software-properties
 [/INDENT] Stable release:
 [INDENT] sudo apt-add-repository ppa:mmex-developers/mmex-stable
sudo apt-get update && sudo apt-get install mmex
 [/INDENT]

---

### Post by ericj2 on 2015-12-09
This is the result of 
sudo apt-get install -f
"The following packages were automatically installed and are no longer required:
  kde-l10n-engb libx11-6:i386 libxau6:i386 libxcb1:i386 libxdmcp6:i386
  libxext6:i386 linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
Use 'apt-get autoremove' to remove them."

Thanks again, I guess I could remove what is listed... since it isn't working?

---

### Post by Geoffrey_Arndt on 2015-12-10
Just a general note - - until you learn the ropes better - - it's best to avoid PPA's or websites other than the official repos (repositories) of Ubuntu (for your specific version (e.g., Trusty 14.04.xx, or Wily 15.10.xx)).   

Once these extra repos (PPA - personal package archives) are added, they can destabilize your system to some extant.    For example, IF upgrading via the web to the next release (LTS 16.04), unless you disable those PPA's, they tend to nuke the upgrade.

Also, LOT's of resources online to explain the Linux (really Unix) filesystem.   Check out Youtube for many intuitive vids.

---

### Post by ericj2 on 2015-12-10
> **Geoffrey_Arndt said:**
> Just a general note - - until you learn the ropes better - - it's best to avoid PPA's or websites other than the official repos (repositories) of Ubuntu (for your specific version (e.g., Trusty 14.04.xx, or Wily 15.10.xx)).   

Once these extra repos (PPA - personal package archives) are added, they can destabilize your system to some extant.    For example, IF upgrading via the web to the next release (LTS 16.04), unless you disable those PPA's, they tend to nuke the upgrade.

Also, LOT's of resources online to explain the Linux (really Unix) filesystem.   Check out Youtube for many intuitive vids.

Thanks for the advice, I'm trying to explore Ubuntu to see if I can move from Windows so I will probably take some risks although I am no newbie to computers/programming, etc. not very familiar with Linux.

I've been using MMEX in windows for a few years and may instead see if I can successfully export from the one I am using in Windows and import the data into Homebank under Linux. Seems like it might work. I wish there were more packages in the repositories.

Today I will be getting a new laptop in which I plan to do the major experimenting cause if it gets messed up I don't much care. I have 3 desktops and a laptop now that I use regularly.

Unfortunately although I have a youtube channel with almost 2 million views, where I live there is no cable or DSL so I have satellite Internet with limited bandwidth and can't watch but so much on youtube.

Thanks for your info though I appreciate it. I see on the MMEX message board a lot of other people have had the same issue I had.

---

### Post by CantankRus on 2015-12-10
You can install mmex from a ppa which also includes the required dependencies.
```
sudo add-apt-repository ppa:dwrj87/mmex-test
sudo apt-get update
sudo apt-get install mmex
```
[ATTACH=CONFIG]266083[/ATTACH]


As stated by Geoffrey_Arndt, take care when using ppas.
After installing the package I want I usually open software sources...
```
software-properties-gtk --open-tab 1
```
and disable the ppa and then re-enable every so often to check for an update.

Make yourself familiar with [**_[COLOR="#B22222"]ppa-purge[/COLOR]_**]("http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html")
I also use the gui application [**_[COLOR="#B22222"]Y PPA MANAGER[/COLOR]_**]("http://www.webupd8.org/2010/11/y-ppa-manager-easily-search-add-remove.html") to easily manage, search and purge added ppas.
[ATTACH=CONFIG]266084[/ATTACH]

---

### Post by ericj2 on 2015-12-11
Thanks, much appreciated!

---

