---
title: "how can i install beautiful fonts (helvetica, etc) onto my computer?"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by hanzj on 2012-04-17
Hello,

We would like to download for free beautiful fonts being used online, such as Helvetica. What's the best way to install these fonts? And is there one package that contains a set of beautiful ones all together? 

My Gimp application has just mostly ugly fonts.

---

### Post by zombifier25 on 2012-04-17
If your fonts is a pure font file (not an installer), place it in /usr/share/fonts if you want the font to be available to all users, or in a folder named .fonts in your home directory if you want only you to use it.

---

### Post by QIII on 2012-04-17
I believe Helvetica is an MS font, and you can install it from Synaptic:

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

You can download fonts all over the web.

When you find something you like, download it and follow the steps under "Manual".

I keep mine in /usr/share/fonts

---

### Post by hanzj on 2012-04-17
QIII and zombifier25, thanks. installed  ttf-mscorefonts-installer package.

But I still don't see Helvetica in list of fonts within Inkscape (fresh start)
> sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ttf-mscorefonts-installer' instead of 'msttcorefonts'
The following NEW packages will be installed:
  ttf-mscorefonts-installer
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 34.9 kB of archives.
After this operation, 221 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/multiverse ttf-mscorefonts-installer all 3.3ubuntu3 [34.9 kB]
Fetched 34.9 kB in 2s (12.9 kB/s)                    
Preconfiguring packages ...
Selecting previously deselected package ttf-mscorefonts-installer.
(Reading database ... 162327 files and directories currently installed.)
Unpacking ttf-mscorefonts-installer (from .../ttf-mscorefonts-installer_3.3ubuntu3_all.deb) ...
Processing triggers for fontconfig ...
Setting up ttf-mscorefonts-installer (3.3ubuntu3) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2012-04-17 00:06:23--  [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2012-04-17 00:06:24--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe) [following]
--2012-04-17 00:06:24--  [http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe](http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/andale32.exe)
Resolving iweb.dl.sourceforge.net... 70.38.0.134, 2607:f748:10:12::5f:2
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198384 (194K) [application/x-msdos-program]
Saving to: `./andale32.exe'

     0K .......... .......... .......... .......... .......... 25% 68.3K 2s
    50K .......... .......... .......... .......... .......... 51%  226K 1s
   100K .......... .......... .......... .......... .......... 77%  335K 0s
   150K .......... .......... .......... .......... ...       100%  398K=1.2s

2012-04-17 00:06:26 (160 KB/s) - `./andale32.exe' saved [198384/198384]

--2012-04-17 00:06:26--  [http://downloads.sourceforge.net/corefonts/arialb32.exe](http://downloads.sourceforge.net/corefonts/arialb32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe) [following]
--2012-04-17 00:06:27--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe) [following]
--2012-04-17 00:06:27--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/arialb32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168176 (164K) [application/octet-stream]
Saving to: `./arialb32.exe'

     0K .......... .......... .......... .......... .......... 30% 75.0K 2s
    50K .......... .......... .......... .......... .......... 60%  286K 1s
   100K .......... .......... .......... .......... .......... 91%  120K 0s
   150K .......... ....                                       100%  358K=1.3s

2012-04-17 00:06:29 (126 KB/s) - `./arialb32.exe' saved [168176/168176]

--2012-04-17 00:06:29--  [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe) [following]
--2012-04-17 00:06:30--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://hivelocity.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://hivelocity.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe) [following]
--2012-04-17 00:06:30--  [http://hivelocity.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe](http://hivelocity.dl.sourceforge.net/project/corefonts/the%20fonts/final/arial32.exe)
Resolving hivelocity.dl.sourceforge.net... 74.50.101.106
Connecting to hivelocity.dl.sourceforge.net|74.50.101.106|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/octet-stream]
Saving to: `./arial32.exe'

     0K .......... .......... .......... .......... ..........  9% 66.3K 7s
    50K .......... .......... .......... .......... .......... 18%  200K 4s
   100K .......... .......... .......... .......... .......... 27%  267K 3s
   150K .......... .......... .......... .......... .......... 36%  262K 2s
   200K .......... .......... .......... .......... .......... 46%  175K 2s
   250K .......... .......... .......... .......... .......... 55%  181K 2s
   300K .......... .......... .......... .......... .......... 64%  448K 1s
   350K .......... .......... .......... .......... .......... 73%  152K 1s
   400K .......... .......... .......... .......... .......... 83%  161K 1s
   450K .......... .......... .......... .......... .......... 92%  166K 0s
   500K .......... .......... .......... .......... .         100%  188K=3.2s

2012-04-17 00:06:34 (168 KB/s) - `./arial32.exe' saved [554208/554208]

--2012-04-17 00:06:34--  [http://downloads.sourceforge.net/corefonts/comic32.exe](http://downloads.sourceforge.net/corefonts/comic32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe) [following]
--2012-04-17 00:06:35--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe) [following]
--2012-04-17 00:06:35--  [http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe](http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/comic32.exe)
Resolving superb-dca2.dl.sourceforge.net... 209.61.193.20
Connecting to superb-dca2.dl.sourceforge.net|209.61.193.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246008 (240K) [application/octet-stream]
Saving to: `./comic32.exe'

     0K .......... .......... .......... .......... .......... 20% 71.9K 3s
    50K .......... .......... .......... .......... .......... 41%  125K 2s
   100K .......... .......... .......... .......... .......... 62% 1.91M 1s
   150K .......... .......... .......... .......... .......... 83%  144K 0s
   200K .......... .......... .......... ..........           100%  214K=1.7s

2012-04-17 00:06:38 (145 KB/s) - `./comic32.exe' saved [246008/246008]

--2012-04-17 00:06:38--  [http://downloads.sourceforge.net/corefonts/courie32.exe](http://downloads.sourceforge.net/corefonts/courie32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe) [following]
--2012-04-17 00:06:39--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe) [following]
--2012-04-17 00:06:39--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/courie32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646368 (631K) [application/octet-stream]
Saving to: `./courie32.exe'

     0K .......... .......... .......... .......... ..........  7% 40.6K 14s
    50K .......... .......... .......... .......... .......... 15% 68.4K 10s
   100K .......... .......... .......... .......... .......... 23% 66.5K 9s
   150K .......... .......... .......... .......... .......... 31% 86.3K 7s
   200K .......... .......... .......... .......... .......... 39% 94.3K 6s
   250K .......... .......... .......... .......... .......... 47% 89.3K 5s
   300K .......... .......... .......... .......... .......... 55% 69.4K 4s
   350K .......... .......... .......... .......... .......... 63% 99.4K 3s
   400K .......... .......... .......... .......... .......... 71%  126K 2s
   450K .......... .......... .......... .......... .......... 79%  131K 2s
   500K .......... .......... .......... .......... .......... 87%  109K 1s
   550K .......... .......... .......... .......... .......... 95%  107K 0s
   600K .......... .......... .......... .                    100% 96.1K=7.6s

2012-04-17 00:06:47 (82.7 KB/s) - `./courie32.exe' saved [646368/646368]

--2012-04-17 00:06:47--  [http://downloads.sourceforge.net/corefonts/georgi32.exe](http://downloads.sourceforge.net/corefonts/georgi32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe) [following]
--2012-04-17 00:06:48--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe) [following]
--2012-04-17 00:06:48--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/georgi32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392440 (383K) [application/octet-stream]
Saving to: `./georgi32.exe'

     0K .......... .......... .......... .......... .......... 13% 73.4K 5s
    50K .......... .......... .......... .......... .......... 26% 72.3K 4s
   100K .......... .......... .......... .......... .......... 39% 94.6K 3s
   150K .......... .......... .......... .......... .......... 52%  119K 2s
   200K .......... .......... .......... .......... .......... 65%  136K 1s
   250K .......... .......... .......... .......... .......... 78%  175K 1s
   300K .......... .......... .......... .......... .......... 91%  160K 0s
   350K .......... .......... .......... ...                  100%  195K=3.5s

2012-04-17 00:06:52 (111 KB/s) - `./georgi32.exe' saved [392440/392440]

--2012-04-17 00:06:52--  [http://downloads.sourceforge.net/corefonts/impact32.exe](http://downloads.sourceforge.net/corefonts/impact32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe) [following]
--2012-04-17 00:06:53--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe) [following]
--2012-04-17 00:06:53--  [http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe](http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/impact32.exe)
Resolving superb-dca2.dl.sourceforge.net... 209.61.193.20
Connecting to superb-dca2.dl.sourceforge.net|209.61.193.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173288 (169K) [application/octet-stream]
Saving to: `./impact32.exe'

     0K .......... .......... .......... .......... .......... 29% 73.0K 2s
    50K .......... .......... .......... .......... .......... 59%  226K 1s
   100K .......... .......... .......... .......... .......... 88%  255K 0s
   150K .......... .........                                  100%  471K=1.1s

2012-04-17 00:06:55 (148 KB/s) - `./impact32.exe' saved [173288/173288]

--2012-04-17 00:06:55--  [http://downloads.sourceforge.net/corefonts/times32.exe](http://downloads.sourceforge.net/corefonts/times32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe) [following]
--2012-04-17 00:06:56--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe) [following]
--2012-04-17 00:06:56--  [http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe](http://softlayer.dl.sourceforge.net/project/corefonts/the%20fonts/final/times32.exe)
Resolving softlayer.dl.sourceforge.net... 74.86.229.28
Connecting to softlayer.dl.sourceforge.net|74.86.229.28|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661728 (646K) [application/octet-stream]
Saving to: `./times32.exe'

     0K .......... .......... .......... .......... ..........  7% 72.7K 8s
    50K .......... .......... .......... .......... .......... 15%  105K 6s
   100K .......... .......... .......... .......... .......... 23%  136K 5s
   150K .......... .......... .......... .......... .......... 30%  135K 4s
   200K .......... .......... .......... .......... .......... 38%  167K 3s
   250K .......... .......... .......... .......... .......... 46%  185K 3s
   300K .......... .......... .......... .......... .......... 54%  193K 2s
   350K .......... .......... .......... .......... .......... 61%  204K 2s
   400K .......... .......... .......... .......... .......... 69%  224K 1s
   450K .......... .......... .......... .......... .......... 77%  225K 1s
   500K .......... .......... .......... .......... .......... 85%  236K 1s
   550K .......... .......... .......... .......... .......... 92%  263K 0s
   600K .......... .......... .......... .......... ......    100%  257K=4.0s

2012-04-17 00:07:01 (161 KB/s) - `./times32.exe' saved [661728/661728]

--2012-04-17 00:07:01--  [http://downloads.sourceforge.net/corefonts/trebuc32.exe](http://downloads.sourceforge.net/corefonts/trebuc32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe) [following]
--2012-04-17 00:07:02--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe) [following]
--2012-04-17 00:07:03--  [http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe](http://superb-dca2.dl.sourceforge.net/project/corefonts/the%20fonts/final/trebuc32.exe)
Resolving superb-dca2.dl.sourceforge.net... 209.61.193.20
Connecting to superb-dca2.dl.sourceforge.net|209.61.193.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357200 (349K) [application/octet-stream]
Saving to: `./trebuc32.exe'

     0K .......... .......... .......... .......... .......... 14% 46.7K 6s
    50K .......... .......... .......... .......... .......... 28% 62.5K 5s
   100K .......... .......... .......... .......... .......... 43% 58.0K 4s
   150K .......... .......... .......... .......... .......... 57% 58.2K 3s
   200K .......... .......... .......... .......... .......... 71% 60.8K 2s
   250K .......... .......... .......... .......... .......... 86% 65.1K 1s
   300K .......... .......... .......... .......... ........  100%  118K=5.6s

2012-04-17 00:07:09 (62.3 KB/s) - `./trebuc32.exe' saved [357200/357200]

--2012-04-17 00:07:09--  [http://downloads.sourceforge.net/corefonts/verdan32.exe](http://downloads.sourceforge.net/corefonts/verdan32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2012-04-17 00:07:10--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe) [following]
--2012-04-17 00:07:10--  [http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe](http://iweb.dl.sourceforge.net/project/corefonts/the%20fonts/final/verdan32.exe)
Resolving iweb.dl.sourceforge.net... 70.38.0.134, 2607:f748:10:12::5f:2
Connecting to iweb.dl.sourceforge.net|70.38.0.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351992 (344K) [application/x-msdos-program]
Saving to: `./verdan32.exe'

     0K .......... .......... .......... .......... .......... 14% 65.3K 4s
    50K .......... .......... .......... .......... .......... 29%  254K 2s
   100K .......... .......... .......... .......... .......... 43% 91.1K 2s
   150K .......... .......... .......... .......... .......... 58%  132K 1s
   200K .......... .......... .......... .......... .......... 72%  131K 1s
   250K .......... .......... .......... .......... .......... 87%  111K 0s
   300K .......... .......... .......... .......... ...       100%  136K=3.0s

2012-04-17 00:07:14 (113 KB/s) - `./verdan32.exe' saved [351992/351992]

--2012-04-17 00:07:14--  [http://downloads.sourceforge.net/corefonts/webdin32.exe](http://downloads.sourceforge.net/corefonts/webdin32.exe)
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2012-04-17 00:07:14--  [http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://downloads.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe) [following]
--2012-04-17 00:07:15--  [http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe](http://cdnetworks-us-2.dl.sourceforge.net/project/corefonts/the%20fonts/final/webdin32.exe)
Resolving cdnetworks-us-2.dl.sourceforge.net... 174.35.19.12
Connecting to cdnetworks-us-2.dl.sourceforge.net|174.35.19.12|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185072 (181K) [application/octet-stream]
Saving to: `./webdin32.exe'

     0K .......... .......... .......... .......... .......... 27% 99.2K 1s
    50K .......... .......... .......... .......... .......... 55%  283K 1s
   100K .......... .......... .......... .......... .......... 82%  299K 0s
   150K .......... .......... ..........                      100%  424K=0.9s

2012-04-17 00:07:16 (196 KB/s) - `./webdin32.exe' saved [185072/185072]

andale32.exe: OK
andale32.exe: library not compiled to support large files.
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
arialb32.exe: OK
arialb32.exe: library not compiled to support large files.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
arial32.exe: OK
arial32.exe: library not compiled to support large files.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
comic32.exe: OK
comic32.exe: library not compiled to support large files.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
courie32.exe: OK
courie32.exe: library not compiled to support large files.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
georgi32.exe: OK
georgi32.exe: library not compiled to support large files.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
impact32.exe: OK
impact32.exe: library not compiled to support large files.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
times32.exe: OK
times32.exe: library not compiled to support large files.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
trebuc32.exe: OK
trebuc32.exe: library not compiled to support large files.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
verdan32.exe: OK
verdan32.exe: library not compiled to support large files.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
webdin32.exe: OK
webdin32.exe: library not compiled to support large files.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts


---

### Post by chamber on 2012-04-17
Helvetica is not a Microsoft font.  At least not anymore.

[http://www.microsoft.com/typography/fonts/default.aspx](http://www.microsoft.com/typography/fonts/default.aspx)

You have Arial which is as close to Helvetica as you will probably get.

[http://en.wikipedia.org/wiki/Helvetica](http://en.wikipedia.org/wiki/Helvetica)

> Monotype's Arial, designed in 1982, while different from Helvetica in some few details, has identical character widths, and is indistinguishable by most non-specialists. The characters C, G, R, Q, 1, a, e, r, and t are useful for quickly distinguishing Arial and Helvetica

---

### Post by hanzj on 2012-04-17
I see. Are there other beautiful fonts. We plan on making a nice logo, and the font will be a major part.

---

### Post by chamber on 2012-04-17
Find a font you like and use it.

---

### Post by SeijiSensei on 2012-04-17
Many of the best fonts used in print typography are proprietary and expensive. [ITC]("http://www.itcfonts.com/") is a well-known font foundry that might meet your needs.  If you're designing a logo for your company, especially one that will appear in print like on letterhead and the like, I strongly recommend meeting with a professional designer and seeing what it would cost to have a logo designed.  Back when I started a company in the mid-90's we spent about $3,000 to get a logo designed and stationery and business cards printed.  They used a proprietary font as well.

---

### Post by rewyllys on 2012-04-17
> **hanzj said:**
> Hello,

We would like to download for free beautiful fonts being used online, such as Helvetica. What's the best way to install these fonts? And is there one package that contains a set of beautiful ones all together? 

My Gimp application has just mostly ugly fonts.
You can use the Synaptic Package Manager to download the "texlive-fonts-recommended" package.  It includes, *inter alia*, Helvetica and my personal candidate for most beautiful font, Palatino.

---

### Post by hanzj on 2012-04-17
Wow. 214 MB to get texlive-fonts-recommended.

---

### Post by Mopar1973Man on 2012-04-17
I'm not sure if this helps but try this link for a mess load of fonts...
[http://www.themeworld.com/fonts/index.html](http://www.themeworld.com/fonts/index.html)

---

