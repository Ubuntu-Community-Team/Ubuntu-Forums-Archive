---
title: "How to:  Create you own repo"
date: 2007-07-05
forum: Outdated Tutorials &amp; Tips
---

### Post by TheeMahn2003 on 2007-07-05
I run a [repo]("http://repoubuntusoftware.info") online, I got tired of manually updating it constantly and decided to write a nautilus script to do it for me.  Works great but progress bar currently does not work, it will tell you the folder you are indexing and the number of packages.  I will eventually fix the progress bar as well as detailed output of packages indexed.  The script automatically checks for an update on my server so when I fix it it will fix everyones :)  I thought I would "share" the wealth and post the script, source, howto and screen shot.

This can be used for both a webserver or as a local repo I will provide the details of setting each up.  I will revise this how to until it is perfect or near so.  So if you know of a easier way to do the same please post.  On to the Goodies:

**_Repo on a server_**

**Step 1** - install the script - open a terminal

```
cd ~/.gnome2/nautilus-scripts/
wget -c http://ubuntusoftware.info/scripts/Auto_Repo.sh
sudo chmod +x Auto_Repo.sh
```

if you would like additional scripts please paste the following:

```
#!/bin/bash
#Nautilus Scripts grabber Via TheeMahn
if [ ! -e "/usr/bin/zenity" ]; then
	sudo apt-get install -y zenity
fi

cd ~/.gnome2/nautilus-scripts/
wget -c http://ubuntusoftware.info/scripts/Nautilus_scripts.tar.gz 2>&1 | sed -u 's/.*\ \([0-9]\+%\)\ \+\([0-9.]\+\ [KMB\/s]\+\)$/\1\n# Downloading \2/' | zenity --width=400 --height=100 --progress --auto-close --title="Downloading Scripts..."
tar xvf Nautilus_scripts.tar.gz
rm Nautilus_scripts.tar.gz
sudo chmod +x *
##Grab scripts
sudo apt-get install -y --allow-unauthenticated nautilus-script-* nautilus-open-terminal lame

#enable them
nautilus-script-manager enable ConvertAudioFile
nautilus-script-manager enable Subversion
```

To get it to show up you will need to restart nautilus:

```
sudo killall nautilus
```

**Step 2** -  use it ;)
To utilize the script right click the folder containing your debs in my case /media/Storage/Feisty/ goto scripts and select Auto_Repo.sh it will inform you of the number of packages and location.  Depending on the number / size of of packages determines how long it takes, sorry no progress bar yet.  After it has completed there will be a file in that directory called Packages.gz <<- important file we will get back to that shortly.

**Step 3** - setup the repo
FTP into your webserver goto your local deb folder in my case /media/Storage/Feisty/ and upload all your debs.  After they are uploaded create a folder called **dists** on your webserver go into that folder and create a folder depending on target platform in my case **feisty**, edgy etc. go into that folder and create a **all** or i386 etc. go into that folder and upload your Packages.gz

Your repo is now setup ;)

**Using your shiny new repo**
Terminal:
```
sudo gedit /etc/apt/sources.list
```
add your repo to the end of the list as I have done with mine, please note replace my server with your server name as well as fiesty with edgy etc. if it is edgy based.
```
deb http://repoubuntusoftware.info/ feisty all
```

**Testing it out**
Terminal:
```
sudo apt-get update
```
you should see similar only with your server name:
```
Get:10 http://repoubuntusoftware.info feisty/all Packages [129kB]
```

You can now request packages from your repo ;)

If I get positive response to this post I will come back and finish local and show you a work around for release.gpg errors.

---

### Post by aboutTOpullmyhairout on 2007-07-28
maybe this post will help others it helped me. and is along the lines of what you have created here
[http://ubuntuforums.org/showthread.php?p=2100699](http://ubuntuforums.org/showthread.php?p=2100699)

if that post does not help you then i think i miss understood you question but i assume you want either a local repo or dvd's with repo on them

---

### Post by DC@DR on 2007-07-28
Nice HOWTO, thanks :-)

---

