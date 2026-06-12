---
title: "Joox.net download script"
date: 2007-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Ramzi on 2007-06-20
Well i was watching some clips from [http://joox.net]("http://joox.net") and i wanted to download all the videos in a category so i wrote this little bash script to do it for me :) Now i understand it is ugly, i wrote it at 04:00 AM after a few sleepless nights so don't blame me =) Well here it is:

```

#!/bin/bash
echo -n "Enter category number, the number behind http://joox.net/cat/ : "
read n
wget http://joox.net/cat/$n 
grep "<a href\=\"\.\/cat\/[[:digit:]][[:digit:]][[:digit:]]\/id\/" $n > numbers
rm $n
cat numbers | cut -d/ -f5 | cut -d\" -f1 > list
cat numbers | cut -d/ -f5 | tr -d \" > rename
rm numbers
cat list | awk '{for(i=1;i<=NF;i++) print "http://video.stage6.com/" $i "/.divx"}' > download
rm list
wget -N -nd -erobots=off -w5 -i download
rm download

```

You just enter the number of the category you want downloaded and that's it, it downloads all the videos in the directory where the script is and creates a file named **rename** that just contains the names of the downloaded files with the names of the videos so you can rename them. If anyone has a better idea for renaming them please tell me.

---

### Post by tzulberti on 2007-06-20
Sorry, but it didnot work for me... I have just tried it, and the following error appears:
Enter category number, the number behind [http://joox.net/cat/](http://joox.net/cat/) : 288
--05:54:18--  [http://joox.net/cat/288](http://joox.net/cat/288)
           => `288'
Resolving joox.net... 85.227.187.226
Connecting to joox.net|85.227.187.226|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [   <=>                                                                                                                     ] 8,576         16.66K/s

05:54:19 (16.61 KB/s) - `288' saved [8576]

--05:54:19--  [http://grep/](http://grep/)
           => `index.html'
Resolving grep... failed: Name or service not known.
Warning: wildcards not supported in HTTP.
--05:54:19--  [http://%3Ca%20href%5C=%22%5C.%5C/cat%5C/](http://%3Ca%20href%5C=%22%5C.%5C/cat%5C/)[[:digit:]][[:digit:]][[:digit:]]%5C/id%5C/
           => `index.html'
Resolving <a href\="\.\... failed: Name or service not known.
--05:54:19--  [http://288/](http://288/)
           => `index.html'
Resolving 288... 0.0.1.32
Connecting to 288|0.0.1.32|:80... failed: Invalid argument.

FINISHED --05:54:19--
Downloaded: 8,576 bytes in 1 files
No URLs found in download.

---

### Post by Ramzi on 2007-06-20
I checked everything and i can't seem to find the problem, I'm guessing that maybe you somehow accidentally copied html code or some unwanted characters. I attached the script separately so try to download it and see if anything changes. Hope it works this time =)

---

### Post by tzulberti on 2007-06-20
Now it seem that it works..
I register myself to see if that is the problem...

THANKS...

---

