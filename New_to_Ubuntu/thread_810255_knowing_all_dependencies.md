---
title: "knowing all dependencies"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by susiriss on 2008-05-28
Hello there,
          I want to install some software on my PC where I don't have an Internet connection. 

How can I get a list of all the dependent packages that are **not currently installed on my PC** so that I can download them from anywhere else and make a local repository and install them manually. 

         The problem is that some packages depend on others and so on. So I want to know exactly the list of packages I should download and bring home in order to make the software work. Is there a way to do this?

Thank You!

susiriss

---

### Post by sayakb on 2008-05-28
Search the package on [http://packages.ubuntu.com](http://packages.ubuntu.com)
You should get a list of dependent packages there.

---

### Post by Bigtime_Scrub on 2008-05-28
You should figure out the packages you want to install and look for them all ready to go. 

[http://packages.debian.org/stable/](http://packages.debian.org/stable/) (I think these will work) and of course [http://packagaes.ubuntu.com](http://packagaes.ubuntu.com).

You should see a list of stuff you want, just download them and save them on CD, DVD, or a USB drive and you're ready to go.

---

### Post by irrdev on 2008-05-28
I would recommend that you use [APTonCD]("http://aptoncd.sourceforge.net/"). This open source utility allows you to copy any installed packages on your internet computer onto a CD, for installation on another computer without an internet connection. APTonCD automatically resolves all the dependencies required, and includes them on the CD. This method is foolproof, and definitely easier to use than manually resolving the required dependencies and copying packages by hand. ;)

---

### Post by Nikitas350 on 2008-05-28
Mark the pachage you want from synaptic package manager and the go to file--->generate downloadable script. Run this script on an ubuntu machine and you will have all the packages you want. This can work and for updates automatically if you put the packages in /var/cache/apt/archives.

---

### Post by sayakb on 2008-05-28
> **Bigtime_Scrub said:**
> You should figure out the packages you want to install and look for them all ready to go. 

[http://packages.debian.org/stable/](http://packages.debian.org/stable/) (I think these will work) and of course [http://packagaes.ubuntu.com](http://packagaes.ubuntu.com).

You should see a list of stuff you want, just download them and save them on CD, DVD, or a USB drive and you're ready to go.

Debian packages might break ubuntu repositories. It is advised not to use debian resources on ubuntu.

---

### Post by susiriss on 2008-05-28
> **Nikitas350 said:**
> Mark the pachage you want from synaptic package manager and the go to file--->generate downloadable script. Run this script on an ubuntu machine and you will have all the packages you want. This can work and for updates automatically if you put the packages in /var/cache/apt/archives.

Hi Nikitas350,
               Your answer is the closest to what I expected. What if the software is currently not displayed in Package Manager? For example, I want to install VLC media player, which is already not there. Shall I install it wihtout the dependent packages and then follow the stpes you've mentioned selecting the broken VLC package..???

Thanks everybody !

---

### Post by joshedmonds on 2008-05-28
Open the Synaptic Package Manager, go to Settings -> Repository and tick all the boxes - then search for vlc.

---

### Post by sayakb on 2008-05-28
Here is a list of packages that depend on VLC: [http://packages.ubuntu.com/hardy/vlc](http://packages.ubuntu.com/hardy/vlc)

---

### Post by kpkeerthi on 2008-05-28
[VLC is in the repos.]("http://packages.ubuntu.com/search?keywords=vlc&searchon=names&suite=hardy&section=all")

If you want to generate a downloadable script for a package, the package should exist in the repo. Infact, the script will attempt to download the package files (.deb) from the package repository. So it can be done only for packages available in a repository.

---

### Post by susiriss on 2008-05-28
Aah I see.. Thanks joshedmonds and kpkeerthi. I guess this should work even if I am yet to try this out.

Thanks very much guys !

---

### Post by Nikitas350 on 2008-05-28
Try to use synaptic in order to fix the problem with vlc. Go to system ---> administration ----> synaptic package manager. Select custom filters (left and down) and then go to broken packages. Select them all and mark them for removal. Then click to the apply button. Then you can install again vlc and you will be able to "find" it on synaptic. Good luck....

---

### Post by sayakb on 2008-05-28
Alternatively, you could try
```
sudo apt-get install -f
```
from the terminal.

---

### Post by susiriss on 2008-05-28
Hello,
             The problem was even if I enabled all repositories in my PC (without Internet) I cannot see VLC listed there. The PC I make downloads from is not an Ubuntu one. I'll try with the method Nikitas350 mentioned last.

Thanks!

---

### Post by susiriss on 2008-05-30
If I remove the broken vlc package then it is still there in the Synaptic. However, when I try to select it for install to generate the download script as  Nikitas350 said, the Synaptic doesn't allow to do so and displays an error message.

             ???????

---

### Post by Nikitas350 on 2008-05-31
What error message? Can you post it here? Also you can change easily the script to work in windows using this way 
1) Download wget for windows from this link [http://users.ugent.be/~bpuype/cgi-bin/fetch.pl?dl=wget/wget.exe](http://users.ugent.be/~bpuype/cgi-bin/fetch.pl?dl=wget/wget.exe)
2) Delete the first line of the script
3) Replace "wget" to "wget.exe" (in the script)
4) Add ".bat" in the end of the filename of your script and put it on the directory you have wget.
Now it should run in windows...

---

### Post by lipidicman on 2008-06-02
So.  I have been using aptoncd.  However the latest CD I created requires the previous one to install.  Why might this be?  I told my internet connected machine to make an aptonCD and selected all packages.  However it will not install unless I have added the previous cd (one I made before adding a few wanted packages) to the sources on my fresh Hardy at home (with no internet)

Hope that is clear, and thanks in advance

---

### Post by susiriss on 2008-06-03
Hi Nikitas350,

This is the error message I'm getting.

```
Could not mark all packages for installation or upgrade

The following packages have unresolved dependencies. Make sure that all required repositories are added and enabled in the preferences.

vlc:

Package vlc has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
```

I have enabled all the repositories. Note that this error messages come from my PC (without Internet )

---

### Post by Nikitas350 on 2008-06-04
Try the folowing commands:
sudo aptitude remove -f vlc
sudo dpkg --configure -a
Then try to install again vlc. If this fails post the output of the command "gedit /etc/apt/sources.list" ...

---

