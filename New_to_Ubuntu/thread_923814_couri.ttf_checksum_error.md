---
title: "couri.ttf: checksum error"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Nebicanezer on 2008-09-18
So I have had ubuntu 8.04 64bit version on my machine now for 3 days, loving every single bit of it!  However this is getting rather annoying to say the least.  I have tried to install msttcorefonts from the terminal countless times and it has always given me a "checksum" error on couri.tff from the courie32.exe cabinet.  Any assistance would be greatly apreciated, because now with every apt-get I do it's always trying to download the msttcorefonts and failing on the couri.tff

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--18:51:55--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--18:51:56--  [http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
           => `./andale32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--18:51:56--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198,384 (194K) [application/octet-stream]

100%[====================================>] 198,384       48.69K/s    ETA 00:00

18:52:01 (48.57 KB/s) - `./andale32.exe' saved [198384/198384]

--18:52:01--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
           => `./arialb32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--18:52:01--  [http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
           => `./arialb32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://kent.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe) [following]
--18:52:01--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe)
           => `./arialb32.exe'
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168,176 (164K) [application/octet-stream]

100%[====================================>] 168,176       78.22K/s             

18:52:04 (77.96 KB/s) - `./arialb32.exe' saved [168176/168176]

--18:52:04--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
           => `./arial32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net) [following]
--18:52:05--  [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net)
           => `./arial32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 216.34.181.60
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://mesh.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/arial32.exe) [following]
--18:52:05--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
           => `./arial32.exe'
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=mesh.dl.sourceforge.net) [following]
--18:52:06--  [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=mesh.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=mesh.dl.sourceforge.net)
           => `./arial32.exe?download&failedmirror=mesh.dl.sourceforge.net'
Reusing existing connection to prdownloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: [http://switch.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/arial32.exe) [following]
--18:52:06--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
           => `./arial32.exe'
Resolving switch.dl.sourceforge.net... 130.59.138.20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=switch.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=switch.dl.sourceforge.net) [following]
--18:52:06--  [http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=switch.dl.sourceforge.net](http://prdownloads.sourceforge.net/corefonts/arial32.exe?download&failedmirror=switch.dl.sourceforge.net)
           => `./arial32.exe?download&failedmirror=switch.dl.sourceforge.net'
Connecting to prdownloads.sourceforge.net|216.34.181.60|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://belnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe) [following]
--18:52:07--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
           => `./arial32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... failed: Connection timed out.
Giving up.

--18:52:12--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/arial32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/arial32.exe)
           => `./arial32.exe'
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554,208 (541K) [application/octet-stream]

100%[====================================>] 554,208        7.41K/s    ETA 00:00

18:52:54 (13.05 KB/s) - `./arial32.exe' saved [554208/554208]

--18:52:54--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/comic32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/comic32.exe)
           => `./comic32.exe'
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246,008 (240K) [application/octet-stream]

100%[====================================>] 246,008       69.90K/s    ETA 00:00

18:52:58 (69.67 KB/s) - `./comic32.exe' saved [246008/246008]

--18:52:58--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/courie32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/courie32.exe)
           => `./courie32.exe'
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646,368 (631K) [application/octet-stream]

100%[====================================>] 646,368        6.89K/s    ETA 00:00

18:53:55 (11.19 KB/s) - `./courie32.exe' saved [646368/646368]

--18:53:55--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe)
           => `./georgi32.exe'
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392,440 (383K) [application/octet-stream]

100%[====================================>] 392,440       82.99K/s    ETA 00:00

18:54:00 (81.76 KB/s) - `./georgi32.exe' saved [392440/392440]

--18:54:00--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/impact32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/impact32.exe)
           => `./impact32.exe'
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173,288 (169K) [application/octet-stream]

100%[====================================>] 173,288       81.08K/s             

18:54:02 (80.86 KB/s) - `./impact32.exe' saved [173288/173288]

--18:54:02--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/times32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/times32.exe)
           => `./times32.exe'
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661,728 (646K) [application/octet-stream]

100%[====================================>] 661,728       10.32K/s    ETA 00:00

18:55:01 (11.09 KB/s) - `./times32.exe' saved [661728/661728]

--18:55:01--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe)
           => `./trebuc32.exe'
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357,200 (349K) [application/octet-stream]

100%[====================================>] 357,200       82.30K/s    ETA 00:00

18:55:06 (82.07 KB/s) - `./trebuc32.exe' saved [357200/357200]

--18:55:06--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe)
           => `./verdan32.exe'
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351,992 (344K) [application/octet-stream]

100%[====================================>] 351,992       70.56K/s    ETA 00:00

18:55:11 (70.40 KB/s) - `./verdan32.exe' saved [351992/351992]

--18:55:11--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe)
           => `./webdin32.exe'
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185,072 (181K) [application/octet-stream]

100%[====================================>] 185,072       66.75K/s             

18:55:14 (66.61 KB/s) - `./webdin32.exe' saved [185072/185072]

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
arialb32.exe: library not compiled to support large files.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
arial32.exe: library not compiled to support large files.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
comic32.exe: library not compiled to support large files.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
courie32.exe: library not compiled to support large files.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
couri.ttf: checksum error
  extracting fontinst.exe

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by pytheas22 on 2008-09-18
Probably the couri.ttf file happened to get corrupted when you downloaded it the first time, and apt-get caches packages for a while, so when you keep trying to reinstall the fonts, it's using the original package, which contains the corrupted file.

You should be able to clear the cache by typing:
```

sudo apt-get clean
```

---

