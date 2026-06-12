---
title: "Script to list package changes"
date: 2006-09-11
forum: Outdated Tutorials &amp; Tips
---

### Post by fo0b4er on 2006-09-11
Hi!  A little while ago I wanted to know what packages I had installed and removed form my original install of (x)ubuntu.  I am sure that there is a much, much better way to do this, but since I couldn't find it I wrote this simple shell script.  I am posting it here so that it will hopefully be usefull to other people.

To use it all you have to do is go to [this]("http://cdimage.ubuntu.com/") site, navigate to the download page for your OS version, and download the .manifest file for your version.  So, for example, I use xubuntu 6.06.1, so I need the file "xubuntu-6.06.1-desktop-i386.manifest".  Then you just run the script with:
```
./changes.sh [.manifest file]
``` 
and it will output a list of package names with a "-" or "+" before them, meaning that you have removed or installed that package since you installed your OS.  You might want to redirect the output of the script into a text file so it is easier to read (add " > something.txt" to the end of the command above).  One small problem is that it compares your current system to what the liveCD version has, so if it says for example "-gparted", that is probably NOT because you have removed it, but because it was used by the liveCD but not automatically installed with the OS.  If anyone knows how to fix this please post it here!  I hope this helps someone!

---

