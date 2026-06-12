---
title: "Copying script from one PC to another"
date: 2015-08-28
forum: New to Ubuntu
---

### Post by tom171 on 2015-08-28
I have a script file and wanted to switch versions of Ubuntu.  I created the script in Xubuntu and ran it from the desktop as an executable.  I wanted to try Ubuntu because the system seemed slow on Xubuntu.  I copied the script to a flash drive using sudo cp command and copied it to the new desktop with the same sudo cp command.  But now my script won't run as an executable and when I go to permissions, everything is greyed out.  I can't check 'run as executable'.  Anyone know what might cause this and how to correct it without recreating the file?  Any help is appreciated

---

### Post by jason_gibson2 on 2015-08-28
Since you used sudo it is now owned by root. Open a terminal and change the permissions or change the owner. Sudo should be used very limited, almost never for doing something as simple as copying to a flash drive or back into your system.


To change the permissions...
```
sudo chmod 755 script
```

To change the owner and group...
```
sudo chown user:user /path/to/script
```

where user is the user you want it on and path to script is the script itself.

If Xubuntu was slow then Ubuntu will be slower as it has more graphical effects going on. If you want faster I suggest Lubuntu.

---

### Post by HermanAB on 2015-08-28
$ sudo chown yourusername: scriptname
$ sudo chmod 754 scriptname
$ ./scriptname

---

