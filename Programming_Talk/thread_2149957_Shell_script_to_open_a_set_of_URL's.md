---
title: "Shell script to open a set of URL's"
date: 2013-05-30
forum: Programming Talk
---

### Post by sravs448 on 2013-05-30
I want to open a set of URL's in shell script and get the return status.
I tried gnome-open and xdg-open, but no luck
```

 xdg-open http://www.google.com
-bash: xdg-open: command not found


 gnome-open http://www.google.com
Error showing url: There was an error launching the default action command associated with this location.
```

---

### Post by sanderj on 2013-05-30
wget?
lynx?
curl?

---

### Post by Lars Noodén on 2013-05-30
xdg-open should be there in /usr/bin.  What version of Ubuntu are you trying this in?  What about trying the full path, /usr/bin/xdg-open?

---

### Post by Habitual on 2013-06-01
```
xdg-open http://www.google.com
```works here but I'm not on Ubuntu, but that doesn't matter, I think.
please run ```
whereis xdg-open 
``` in a terminal and report the output.

output:
```
xdg-open http://www.google.com && echo $?
0
```

---

### Post by Cheesehead on 2013-06-01
In Ubuntu, /usr/bin/xdg-open in provided by the xdg-utils package. Make sure that's installed.

---

### Post by localhost8080 on 2013-06-02
you could do something like the following (not tested but should work)
put all the urls in a text file, one per line called my.file

make a bash script, chmod +x the file and after putting the following in it run it form a command line

#/bin/sh
cat my.file | while read URL ; do
	echo "fetching $LINE"
        wget $LINE
done

---

