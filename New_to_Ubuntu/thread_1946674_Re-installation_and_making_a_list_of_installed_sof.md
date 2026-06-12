---
title: "Re-installation and making a list of installed software"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by GeordieJedi on 2012-03-25
Hi all.

OK, I'm going to install 11.10 and I'd like to make a list of all the programmes and apps
that I've installed so-far. (To make it easier to re-install them afterwards).

So-far (I think I've made a correct list by doing the folowing in a terminal) =

```

dpkg --get-selections > installed_apps_01.txt

```

However I prefaced that command with sudo.

E.G.

```

sudo dpkg --get-selections > installed_apps_01.txt

```

and saved it to my home folder.

Now, is this enough? Was putting sudo in-front wise?
Will this enable me to run the next line of code to re-install all of the apps?


Thanks in advance for any help or advice.

---

### Post by zombifier25 on 2012-03-25
As far as I know, sudo in front of that particular command doesn't make any difference.

---

### Post by d4m1r on 2012-03-25
How big is your text file by the way?

I am looking to do the same thing but I am NOT interested in knowing each package installed by name, only applications. Which do you get by doing that?

---

### Post by Bobhuber on 2012-03-25
> **GeordieJedi said:**
> Hi all.

OK, I'm going to install 11.10 and I'd like to make a list of all the programmes and apps
that I've installed so-far. (To make it easier to re-install them afterwards).

So-far (I think I've made a correct list by doing the folowing in a terminal) =

```

dpkg --get-selections > installed_apps_01.txt

```However I prefaced that command with sudo.

E.G.

```

sudo dpkg --get-selections > installed_apps_01.txt

```and saved it to my home folder.

Now, is this enough? Was putting sudo in-front wise?
Will this enable me to run the next line of code to re-install all of the apps?


Thanks in advance for any help or advice.
Some of the apps will not be compatible with the new version. Use the list as reference and install them manually so you know whats going on. You will also remove all the collected STUFF you have and don't need anymore. In other words a clean install.

---

### Post by presence1960 on 2012-03-25
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by oldfred on 2012-03-26
I have used dpkg to reinstall all my apps with every new clean install.

From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade


But I find I am reinstalling apps no longer required. I was reinstalling python2.5. Now with so many changes you really need to review & edit list. It will not install apps totally obsoleted, nor reinstall apps already installed. But will reinstall OpenOffice or other apps that have now been replaced with totally other apps.

List with explanations of programs, not for reinstall
dpkg -l > ~/installed_programs.txt
Top level applications:
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

---

### Post by Kevin McCready on 2012-03-26
I did a clean reinstall recently. I just keep a list then 

```
sudo apt-get update
sudo apt-get install <each package separately>
```

It's getting a bit long now, but still much faster than anything I ever did with the old bloated expensive slow legacy operating system (OBESLOPS). If someone knows a quicker way, let us know.

My extra list for Lubuntu is:
Dolphin (File Manager, but can't wipe out slow PCManFM unfortunately)
gnome-media ( for mplayer. I had to install PulseAudio Volume Control and then select Sound Recorder)
libreoffice-writer (closer to Microsoft word functionality and much better than abiword)
ibus-pinyin (for chinese - it needed tweaking)
thunderbird (for email - Sylpheed was a dog - sorry guys)
clipit (so that stuff cut to clipboard buffer is available after I quit the application)

---

### Post by oldfred on 2012-03-27
I save my list in a script. Some I install first just to make sure I have them before I run my dpkg. It does not install twice so it is not an issue.

I save my updates to a script, have commented out a lot, have added some things I think I may want with comments and just added my own notes. 
Copy attached which you can customize with your apps.

---

