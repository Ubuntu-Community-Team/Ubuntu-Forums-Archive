---
title: "[SOLVED] Removing Google Earth"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by wahoobob on 2008-06-17
I tried to install.deb file from Google and it didn't run properly.  I then tried to uninstall, but the error came back that there was no working uninstall file:confused: in /opt/google-earth/ ..............
I don't know how to (or if I should) delete the entire folder and when I tried the command it said I was not allowed.  Is there a terminal command or some delete that I can use to start over and try the Google Earth form the synaptic repositories (or someplace)?  Is Google Earth working well in Hardy or should we wait for an update?

---

### Post by hyper_ch on 2008-06-17
how did you try to uninstall it? where did you get the .deb from?

---

### Post by _sphinx_ on 2008-06-17
Ok I don't know where did you got the .deb file for Google Earth but check this link
[http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)
This should download .bin for Google Earth most probably on Desktop. So in terminal type:
```
chmod +x <downloaded file name>
sudo ./<downloaded file name>
```
this should install the google earth for you. To run it type in the terminal:
```
google-earth
```OR
```
googleearth
``` I don't know which of them, but one of them should work.

---

### Post by wahoobob on 2008-06-18
> **_sphinx_ said:**
> Ok I don't know where did you got the .deb file for Google Earth but check this link
[http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin)
This should download .bin for Google Earth most probably on Desktop. So in terminal type:
```
chmod +x <downloaded file name>
sudo ./<downloaded file name>
```
this should install the google earth for you. To run it type in the terminal:
```
google-earth
```OR
```
googleearth
``` I don't know which of them, but one of them should work.
Will this install it over the existing google-earth that isn't working and (hopefully) give me an unistall that could work? or install in a new place?  If it doesn't work can I just delete the files and the folder (somehow) and not screw up the system since there is no registry (shudder).  What is the most powerful delete command that I can use to get to the offending program?  Thanks in advance...

---

### Post by wahoobob on 2008-06-18
> **hyper_ch said:**
> how did you try to uninstall it? where did you get the .deb from?
I got it from going to the Google site and downloading the debian package.

---

### Post by stchman on 2008-06-18
> **wahoobob said:**
> I tried to install.deb file from Google and it didn't run properly.  I then tried to uninstall, but the error came back that there was no working uninstall file:confused: in /opt/google-earth/ ..............
I don't know how to (or if I should) delete the entire folder and when I tried the command it said I was not allowed.  Is there a terminal command or some delete that I can use to start over and try the Google Earth form the synaptic repositories (or someplace)?  Is Google Earth working well in Hardy or should we wait for an update?

You can get GE from Medibuntu.

Install Medibuntu repos this way:

[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

Once the repo is installed do this in a terminal.

```
sudo apt-get update
sudo apt-get install googleearth
```

To remove GE do this.

```
sudo apt-get autoremove googleearth
```

---

### Post by wahoobob on 2008-06-18
For some reason I can't accept the final <OK> in the setup.  My keyboard does not get any response.  When I try to run the program no earth shows up.  when I try to remove with autoremove... It wants me to dpkg --configure -a.  What's going on?  I would be happy to be rid of this program now.....

---

### Post by sdowney717 on 2008-06-18
sudo dpkg --configure -a && sudo apt-get -f install

run this
install google earth from ubuntu repositories since it has been tested and more likely to work.

[http://10xforce.blogspot.com/2007/09/dpkg-was-interrupted-you-must-manually.html](http://10xforce.blogspot.com/2007/09/dpkg-was-interrupted-you-must-manually.html)

---

### Post by Duck2006 on 2008-06-18
Download the GoogleEarth.bin from the web site and install it with.

cd ~/Desktop
sh GoogleEarthLinux.bin

---

### Post by hyper_ch on 2008-06-19
> **wahoobob said:**
> For some reason I can't accept the final <OK> in the setup.  My keyboard does not get any response.  When I try to run the program no earth shows up.  when I try to remove with autoremove... It wants me to dpkg --configure -a.  What's going on?  I would be happy to be rid of this program now.....

Tried the TAB-Key?

---

### Post by wahoobob on 2008-06-19
> **hyper_ch said:**
> Tried the TAB-Key?
yes, I tried tab and space and about everything else.  I suppose the message that I get is because I am not recorded as having agreed to their non-open source restrictions, but I am _trying_ to agree.  This should teach me to stay away from non-open source anything and to use the ubuntu tested software if I'm not ready for heavy lifting in the terminal.

---

### Post by wahoobob on 2008-06-19
> **sdowney717 said:**
> sudo dpkg --configure -a && sudo apt-get -f install

run this
install google earth from ubuntu repositories since it has been tested and more likely to work.

[http://10xforce.blogspot.com/2007/09/dpkg-was-interrupted-you-must-manually.html](http://10xforce.blogspot.com/2007/09/dpkg-was-interrupted-you-must-manually.html)
if I run "sudo dpkg --configure -a && sudo apt-get -f install" will that make the program  available to uninstall (autoremove?)? or will I need to install from the repositories to get an autoremove to work?

---

### Post by decoherence on 2008-06-19
> if I run "sudo dpkg --configure -a && sudo apt-get -f install" will that make the program uninstall first?

Your package database is screwed up which is probably why you're having problems. Running "sudo dpkg --configure -a && sudo apt-get -f install" will repair the database.

During the fix, Google Earth may finish installing. If not, grab it from the repository as was suggested.

If you continue to have problems, post the output under "Details" here (of course!)

---

### Post by _sphinx_ on 2008-06-19
If your Google earth application is opening and no earth is showing up you can try.
```
sudo googleearth
```
Read this:
[http://ubuntuforums.org/showthread.php?t=817055&highlight=sudo+googleearth](http://ubuntuforums.org/showthread.php?t=817055&highlight=sudo+googleearth)

---

### Post by wahoobob on 2008-06-19
> **Duck2006 said:**
> Download the GoogleEarth.bin from the web site and install it with.

cd ~/Desktop
sh GoogleEarthLinux.bin
*I think that is where this all started*.  I just want to get rid of the **Google Earth **program now.  In the course of trying to get it to work I installed it from different sources hoping to correct the previous install and now the autoremove won't work and the folder is restricted to root so I don't know how to trash it (or if this is a good idea..)

---

### Post by Duck2006 on 2008-06-19
> or will I need to install from the repositories to get an autoremove to work?

Try uninstalling it from reopitories and then try install it again. I tryed installing from repositories and it never worked for me, so i installed it with the bin file and it work great for me.




Edit: to install the *.bin you don't have to be root.

---

### Post by wahoobob on 2008-06-19
> **decoherence said:**
> Your package database is screwed up which is probably why you're having problems. Running "sudo dpkg --configure -a && sudo apt-get -f install" will repair the database.

During the fix, Google Earth may finish installing. If not, grab it from the repository as was suggested.

If you continue to have problems, post the output under "Details" here (of course!)
I'll try that tonight when I get off this ******* M$ machine here at work.

---

### Post by wahoobob on 2008-06-19
> **sdowney717 said:**
> sudo dpkg --configure -a && sudo apt-get -f install

run this
install google earth from ubuntu repositories since it has been tested and more likely to work.

[http://10xforce.blogspot.com/2007/09/dpkg-was-interrupted-you-must-manually.html](http://10xforce.blogspot.com/2007/09/dpkg-was-interrupted-you-must-manually.html)
Ok - now it works, but only when I am in the terminal and go "sudo googleearth".  I will look for a fix for this or try to remove the program.  Thanks for yur help.

---

