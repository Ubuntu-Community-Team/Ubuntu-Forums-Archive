---
title: "looking for correct sudo command to install skype"
date: 2017-04-30
forum: New to Ubuntu
---

### Post by johnny7oak on 2017-04-30
hi, I want the correct sudo command to install skype for linux 64...

file name is "skypeforlinux-64.deb"  I have it in my downloads directory but I am getting a message:
> 
jonathan@Johnny7oak:~$ sudo install skypeforlinux-64.deb
install:  missing destination file after operand 'skypeforlinux-64.deb'
try 'install --help' for more information

I kind of want to be able to answer the phone here on this computer while on line.  I have a Google voice number, but I really don't think that's going to help much.  That just leaves voice mail, and I can call them back at the number I parked.

---

### Post by Adam_GUI on 2017-04-30
cd to your downloads directory in terminal.
Then, "sudo dpkg -i skypeforlinux-64.deb"

---

### Post by johnny7oak on 2017-04-30
well i am sure that would have worked but apparently it is packaged for i386 and not AMD64... kind of bites.

---

### Post by oldrocker99 on 2017-04-30
Skype is in the repositories; no need to download it separately:```
sudo apt install skype
```.

---

### Post by johnny7oak on 2017-04-30
okay now I got another issue with this sudo apt install:

> package skype is not available, but is referred to by another package. this may mean that the package is missing, has been obsoleted, or is only available from another source

E: Package 'skype' has no installation cannidate


Does this mean the package is the same as the install file?

---

### Post by yetimon_64 on 2017-05-01
> Does this mean the package is the same as the install file?                 Same package but when manually installed from the .deb file it will not be automatically kept up to date by the system; if the same package is in the repos it is best to use it from there, as is the case with skype, so it is always kept up to date. However you need to enable the canonical partners repo to have it available for installation with the command given by oldrocker99. 

To do so go to dash and search for "software and updates" and open it. On the "Other Software" tab tick (enable) "Canonical Partners" this will give you access to the skype package. Then let software and updates complete (update the new settings **Edit:** you may have to press a button called "reload" if it is offered to you) and then close it go back to the terminal and try the command oldrocker99 gave you again; skype should install without any problems with the Canonical Partners repo enabled.

---

### Post by howefield on 2017-05-01
> **johnny7oak said:**
> hi, I want the correct sudo command to install skype for linux 64....

If you are installing the beta Skype package downloaded from the Skype website and are using Ubuntu 16.04 or later you can use..

```
sudo apt install ~/Downloads/skypeforlinux-64.deb
``` 

In other words, you missed the word "apt" from your initial command. You also need the full path, ie ~/Downloads/skypeforlinux-64.deb (or whatever the path is to where you have stored the file)

The installation would put the correct repository information into your system so that Skype would be kept updated and current.

Sometimes I've seen the authentication key not install along with the repository source information, if that happens all you need to do is..

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1F3045A5DF7587C3
```

---

### Post by alejandrofig on 2017-05-01
Since Ubuntu 10.04 (Lucid Lynx), **Skype** **is** part of the Canonical partner repository. To install **Skype** add the Canonical Partner Repository. You can do this by running the **command**  
   sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner 
   Then install **Skype** via the Software-Center or via the Terminal.  
   sudo apt-get update && sudo apt-get install skype

---

### Post by johnny7oak on 2017-05-01
> lsb-release-sc: command not found
lsb-release-sc: command not found
error: need a single repository as argument

okay so this is what I get... I tried the fist apt key adv, still does not unpack skype.

what I got for the unpack was:
> 

reading package lists... Done
Building dependency tree
Reading state information... Done
E: unable to locate package skypeforlinux-64.deb
E: couldn't find any package by glob 'skypeforlinux-64.deb'
E: couldn't find any package by regex 'skypeforlinux-64.deb'

---

### Post by Impavidus on 2017-05-01
I think you missed a space in that command. But it's even simpler than that. Go to "software & updates", click "other software" and click the checkbox for "canonical partners". Or something very similar to that, as it varies a bit by version, flavour and language settings. Then I think skype should be available from the repositories.

---

