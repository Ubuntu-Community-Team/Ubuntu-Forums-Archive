---
title: "Create speedtest script and database"
date: 2016-09-13
forum: Programming Talk
---

### Post by cazz on 2016-09-13
hi
about 3 years ago I did create a very basic bash script that use wget.
But I was stupid and not save the code and I have no idea where it is.
So now I need help to create it a new one (Maybe even better)

when I was looking around I did find this pages that look familiar that I did use

[http://lifehacker.com/how-to-test-your-internet-speed-with-a-terminal-command-1364123567](http://lifehacker.com/how-to-test-your-internet-speed-with-a-terminal-command-1364123567)

[http://blog.ashurex.com/2012/04/16/measuring-download-speed-linux-command-line/](http://blog.ashurex.com/2012/04/16/measuring-download-speed-linux-command-line/)

With that code I can easy get the info that I need but now I like to put it in a database

so I need to put the **000KB/s** into a varable and I'm not sure how to get just that

in the database I going to use timestamp (I was thinking to use MySQL) and then use google chart to create a nice view how the the download speed is
I think that is a easy for me but when I'm not sure how to get the download speed to a varable, then I have problem.

---

### Post by spjackson on 2016-09-13
Here's a starter for you to improve upon.
```

#!/bin/bash

wget http://example.com/some-uri > temp.log 2>&1

# search the log for the word 'saved' and extract the contents from
# within the parentheses.
speed=$(grep saved temp.log | sed 's/^.*(//' | sed 's/).*//')
echo Speed is "$speed"


```

---

### Post by Habitual on 2016-09-13
I use
```
wget -O - [https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py](https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py) | python
```

database? never thought about it.

---

### Post by cazz on 2016-09-13
mm my idea is like this
I have a Linux server centrally in the network 
I also going to have a old laptop with Linux (To bad raspberry pi does not have 1000 Ethernet)
both have the script point it each other and download a 300Mb file to see the speed of download.

the laptop is going to run every 15 min all the time until I say stop and everytime it have download the file it going to send the information to Linuxserver to collect all the info I need and create a chart 
Then I have info about how fast the upload and the download is from the place I have the laptop.

I hope you all understand what I'm trying to do :D

---

### Post by Habitual on 2016-09-13
I misunderstood, sorry.

---

