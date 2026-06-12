---
title: "setup language pack hangs"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by TJCIB on 2008-07-30
I have a fresh install of Gutsy.
I downloaded the updates and started to install them.  When setting up the language-pack-en-base is just hangs.  I stopped it, went and tried dpkg --configure -a and here is the output.  Been stuck here for about 45 minutes

```

library@lab4:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
library@lab4:~$ sudo dpkg --configure -a
Setting up language-pack-en-base (1:7.10+20080205) ...
Generating locales...
  en_AU.UTF-8... 

```

any suggestions?
I know the package isn't bad, because I use apt-cacher and it just went through on another computer which I used the same install CD.

---

### Post by drs305 on 2008-07-30
```

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by TJCIB on 2008-07-30
```
sudo dpkg --configure -a
```

this hangs the exact same way.  That was the example I pasted was the output of this command.  I can't get to the other two you suggested.

---

### Post by drs305 on 2008-07-30
Yes, sorry I overlooked that. I remember working a language problem that hung the install of someone else but it was a while back. I'll do a search and see if I can come up with something.

Added: Found the post but the OP reinstalled before he corrected the problem...

Try this if you can use sudo at all:
```

sudo apt-get purge language-support-en
sudo apt-get install language-support-en

```

---

### Post by TJCIB on 2008-07-30
I'm probably heading that way.  At least it was a fresh install to begin with, nothing lost but time...

If anyone else has a suggestion, I'm more than open...I would like to learn how to fix stuff beyond "reinstall"...i've got that method down!

---

### Post by TJCIB on 2008-07-31
I tried your suggestion of purging the language support, but get the same message 
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

it seems that apt won't work as long as there is an interrupted dpkg.

Anyone know how to reset this, except by using the given command, which doesn't work, just hangs.

---

### Post by drs305 on 2008-07-31
Okay, let's try to isolate the bad package.

Export the current dpkg info, make a backup before editing, then open with gedit (or your editor of choice):
```

dpkg --get-selections >~/Desktop/bad-install 
cp ~/Desktop/bad-install ~/Desktop/bad-install.bak
gedit ~/Desktop/bad-install

```

1. Look for the language-pack-gnome-**XX** listings. Either change the entry from "**install**" to "**deinstall**" (preferred) or delete the line.
2. Save the file.
3. Export the revision back to the dpkg:
```

sudo dpkg --clear-selections
sudo dpkg --set-selections <~/Desktop/bad-install 	
sudo apt-get -u dselect-upgrade

```

See if that clears the language pack problem.

---

### Post by TJCIB on 2008-07-31
alrighty...that helped!

I tried that, language pack set up.  Then it got hung on avahi-daemon. So I tried the same thing with avahi, then it got hung up on cupsys...

Somewhere in fiddling I almost removed the entire system and got a nice message asking if I really wanted to do that...it was quite polite.

so then I did
```
sudo dpkg --clear-selections
sudo apt-get clean
sudo apt-get -f install
```

and as I'm speaking all of those stupid packages I mentioned up top got configured and the rest of the updates are installing...

Thanks for the direction, couldn't have done it without your help...

---

