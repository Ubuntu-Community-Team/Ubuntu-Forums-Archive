---
title: "[SOLVED] Uninstall a program via terminal"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by drakeman007 on 2008-10-20
Hello, probably this is a dumb question i know, but im new in ubuntu world and generally  in linux world, i want to remove the openoffice 2.4 that comes with ubuntu 8.04 lts but i want to learn to do most things via command line, i tried with command "sudo dpkg -r openoffice" and with "sudo apt-get remove openoffice" but in both i got a message "couldnt find the package openoffice" or "warning: ignoring reuqest to remove openoffice wich isnt installed", i know that is maybe because im putting the wrong name but how i can identify the name of the package installed? can anyone help me with this little question please!!!

thanks to all guys!

---

### Post by Titan8990 on 2008-10-20
You were on the right track, just had the incorrect package name:


sudo apt-get remove --purge openoffice.org


edit: also to search packages:

apt-cache search openoffice


The search is always made as if it were: *openoffice*

The search also includes the descriptions of the packages.

And most likely you will need this after removal:

sudo apt-get autoremove

---

### Post by Harisz750 on 2008-10-20
it shows those errors because it isn't just openoffice.... you should tell it which version it is..  2.4

---

### Post by fizzatbeyond on 2008-10-20
You are right in the howto, however you'll need to know the actual package name.  You can find this out by typing:
apt-cache search openoffice.org (this will give you a LONG list and not all are installed)

although in cases like this I prefer aptitude but the syntax is the same:
aptitude search openoffice.org

With aptitude it will by default tell you if it is installed.

Or even better,
aptitude search ~iopenoffice.org

This will only list the installed programs that meet the criteria of "openoffice.org"

---

### Post by drakeman007 on 2008-10-20
Thanks Guys to your help, i think i found the solution to find the packages installed via command line, 
i put
dpkg -l | grep packagename ( in this case, openoffice)

and it list the openoffice packages and now i have to uninstall one by one!! thanks for your help guys!

---

### Post by Poadrim on 2009-10-15
Hi! I have kinda a the same problem, I installed a whole bunch of program (sound editing) with the terminal and let terminal download and install all the necessary files. And now my PC wont start to desktop. I type in my password and press enter, the log in sound plays and a blue screen appears and nothing happens, I can however open terminal and open program with that, but is there away to unstall all sound editing program with the same way I installed it? Just type something and it will unstall automatically? Or do I need to unstall one-by-one?

---

