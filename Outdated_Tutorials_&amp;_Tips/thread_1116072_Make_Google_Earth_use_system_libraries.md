---
title: "Make Google Earth use system libraries"
date: 2009-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by RATM_Owns on 2009-04-04
Idea from here: [http://forums.gentoo.org/viewtopic-t-735431.html](http://forums.gentoo.org/viewtopic-t-735431.html)

Step 1: Install Google Earth

Step 2: Paste this in google-earth-libraries.sh:
```
#!/bin/bash 
 
cd /opt/googleearth 
 
find . -maxdepth 1 -type f -regex '^\./lib.*so\..*' -printf '%f\n' | while read lib 
do 
        echo "Searching for $lib ..." 
        find /lib /usr/lib/ -name "$lib" \ 
                -exec echo -n "Replacing $lib with {} ... " \; \ 
                -exec ln -fs '{}' "$lib" \; \ 
                -exec echo "OK" \; 
done
```

Step 3. Run the script.
```
sudo sh google-earth-libraries.sh
```

You are now the proud owner of an extra 19MB!

---

