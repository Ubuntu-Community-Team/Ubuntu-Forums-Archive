---
title: "[SOLVED] MS Core fonts problem"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-05-10
Ok, from what I have read, all I need to do to get the Microsoft Core Fonts is to ```
sudo apt-get install msttcorefonts
``` and logout/login

I have done that, but they are not to be found anywhere -- not in firefox, not in System>Preferences>Appearance and not in OpenOffice.  Where the heck are they and how do I use them?

---

### Post by Joeb454 on 2008-05-10
What does the terminal output when you do this command (and have entered your password) ?

---

### Post by H.Callahan on 2008-05-10
> **Joeb454 said:**
> What does the terminal output when you do this command (and have entered your password) ?
I'm not sure you want to see all of this.  The output overran my terminal buffer.  But the last part of it is:
```
Location: http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--16:59:16--  http://prdownloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--16:59:17--  http://downloads.sourceforge.net/corefonts/courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./courie32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://ufpr.dl.sourceforge.net/sourceforge/corefonts/courie32.exe [following]
--16:59:17--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
           => `./courie32.exe'
Resolving ufpr.dl.sourceforge.net... 200.17.202.1
Connecting to ufpr.dl.sourceforge.net|200.17.202.1|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646,368 (631K) [application/x-msdos-program]

100%[====================================>] 646,368      313.84K/s             

16:59:20 (312.93 KB/s) - `./courie32.exe' saved [646368/646368]

--16:59:20--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
           => `./georgi32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--16:59:20--  http://prdownloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--16:59:21--  http://downloads.sourceforge.net/corefonts/georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./georgi32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://umn.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe [following]
--16:59:21--  http://umn.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
           => `./georgi32.exe'
Resolving umn.dl.sourceforge.net... 128.101.240.209
Connecting to umn.dl.sourceforge.net|128.101.240.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392,440 (383K) [application/octet-stream]

100%[====================================>] 392,440      634.22K/s             

16:59:22 (632.39 KB/s) - `./georgi32.exe' saved [392440/392440]

--16:59:22--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
           => `./impact32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--16:59:22--  http://prdownloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--16:59:23--  http://downloads.sourceforge.net/corefonts/impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./impact32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://puzzle.dl.sourceforge.net/sourceforge/corefonts/impact32.exe [following]
--16:59:23--  http://puzzle.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
           => `./impact32.exe'
Resolving puzzle.dl.sourceforge.net... 195.141.111.5
Connecting to puzzle.dl.sourceforge.net|195.141.111.5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 173,288 (169K) [application/octet-stream]

100%[====================================>] 173,288       10.64K/s    ETA 00:00

16:59:43 (12.97 KB/s) - `./impact32.exe' saved [173288/173288]

--16:59:43--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe
           => `./times32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--16:59:44--  http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./times32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--16:59:44--  http://downloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./times32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://superb-east.dl.sourceforge.net/sourceforge/corefonts/times32.exe [following]
--16:59:44--  http://superb-east.dl.sourceforge.net/sourceforge/corefonts/times32.exe
           => `./times32.exe'
Resolving superb-east.dl.sourceforge.net... 209.160.66.130
Connecting to superb-east.dl.sourceforge.net|209.160.66.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=superb-east.dl.sourceforge.net [following]
--16:59:45--  http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=superb-east.dl.sourceforge.net
           => `./times32.exe?download&failedmirror=superb-east.dl.sourceforge.net'
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=superb-east.dl.sourceforge.net [following]
--16:59:45--  http://downloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=superb-east.dl.sourceforge.net
           => `./times32.exe?download&failedmirror=superb-east.dl.sourceforge.net'
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://optusnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe [following]
--16:59:45--  http://optusnet.dl.sourceforge.net/sourceforge/corefonts/times32.exe
           => `./times32.exe'
Resolving optusnet.dl.sourceforge.net... 211.29.132.142
Connecting to optusnet.dl.sourceforge.net|211.29.132.142|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=optusnet.dl.sourceforge.net [following]
--16:59:46--  http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=optusnet.dl.sourceforge.net
           => `./times32.exe?download&failedmirror=optusnet.dl.sourceforge.net'
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=optusnet.dl.sourceforge.net [following]
--16:59:46--  http://downloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=optusnet.dl.sourceforge.net
           => `./times32.exe?download&failedmirror=optusnet.dl.sourceforge.net'
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://switch.dl.sourceforge.net/sourceforge/corefonts/times32.exe [following]
--16:59:47--  http://switch.dl.sourceforge.net/sourceforge/corefonts/times32.exe
           => `./times32.exe'
Resolving switch.dl.sourceforge.net... 130.59.138.20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=switch.dl.sourceforge.net [following]
--16:59:47--  http://prdownloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=switch.dl.sourceforge.net
           => `./times32.exe?download&failedmirror=switch.dl.sourceforge.net'
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=switch.dl.sourceforge.net [following]
--16:59:47--  http://downloads.sourceforge.net/corefonts/times32.exe?download&failedmirror=switch.dl.sourceforge.net
           => `./times32.exe?download&failedmirror=switch.dl.sourceforge.net'
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://puzzle.dl.sourceforge.net/sourceforge/corefonts/times32.exe [following]
--16:59:47--  http://puzzle.dl.sourceforge.net/sourceforge/corefonts/times32.exe
           => `./times32.exe'
Resolving puzzle.dl.sourceforge.net... 195.141.111.5
Connecting to puzzle.dl.sourceforge.net|195.141.111.5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 661,728 (646K) [application/octet-stream]

100%[====================================>] 661,728       10.73K/s    ETA 00:00

17:00:44 (14.30 KB/s) - `./times32.exe' saved [661728/661728]

--17:00:44--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
           => `./trebuc32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--17:00:45--  http://prdownloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./trebuc32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--17:00:45--  http://downloads.sourceforge.net/corefonts/trebuc32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./trebuc32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://umn.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe [following]
--17:00:45--  http://umn.dl.sourceforge.net/sourceforge/corefonts/trebuc32.exe
           => `./trebuc32.exe'
Resolving umn.dl.sourceforge.net... 128.101.240.209
Connecting to umn.dl.sourceforge.net|128.101.240.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 357,200 (349K) [application/octet-stream]

100%[====================================>] 357,200      660.36K/s             

17:00:46 (658.34 KB/s) - `./trebuc32.exe' saved [357200/357200]

--17:00:46--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
           => `./verdan32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--17:00:47--  http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./verdan32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--17:00:47--  http://downloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./verdan32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://heanet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe [following]
--17:00:47--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
           => `./verdan32.exe'
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/sourceforge/corefonts/verdan32.exe [following]
--17:00:48--  http://prdownloads.sourceforge.net/sourceforge/corefonts/verdan32.exe
           => `./verdan32.exe'
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe [following]
--17:00:48--  http://downloads.sourceforge.net/sourceforge/corefonts/verdan32.exe
           => `./verdan32.exe'
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://superb-east.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe [following]
--17:00:48--  http://superb-east.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
           => `./verdan32.exe'
Resolving superb-east.dl.sourceforge.net... 209.160.66.130
Connecting to superb-east.dl.sourceforge.net|209.160.66.130|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=superb-east.dl.sourceforge.net [following]
--17:00:48--  http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=superb-east.dl.sourceforge.net
           => `./verdan32.exe?download&failedmirror=superb-east.dl.sourceforge.net'
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=superb-east.dl.sourceforge.net [following]
--17:00:48--  http://downloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=superb-east.dl.sourceforge.net
           => `./verdan32.exe?download&failedmirror=superb-east.dl.sourceforge.net'
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://superb-west.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe [following]
--17:00:48--  http://superb-west.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
           => `./verdan32.exe'
Resolving superb-west.dl.sourceforge.net... 209.160.59.253
Connecting to superb-west.dl.sourceforge.net|209.160.59.253|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=superb-west.dl.sourceforge.net [following]
--17:00:49--  http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=superb-west.dl.sourceforge.net
           => `./verdan32.exe?download&failedmirror=superb-west.dl.sourceforge.net'
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=superb-west.dl.sourceforge.net [following]
--17:00:49--  http://downloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=superb-west.dl.sourceforge.net
           => `./verdan32.exe?download&failedmirror=superb-west.dl.sourceforge.net'
Reusing existing connection to downloads.sourceforge.net:80.
HTTP request sent, awaiting response... 302 Found
Location: http://optusnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe [following]
--17:00:49--  http://optusnet.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
           => `./verdan32.exe'
Resolving optusnet.dl.sourceforge.net... 211.29.132.142
Connecting to optusnet.dl.sourceforge.net|211.29.132.142|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=optusnet.dl.sourceforge.net [following]
--17:00:55--  http://prdownloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=optusnet.dl.sourceforge.net
           => `./verdan32.exe?download&failedmirror=optusnet.dl.sourceforge.net'
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=optusnet.dl.sourceforge.net [following]
--17:00:55--  http://downloads.sourceforge.net/corefonts/verdan32.exe?download&failedmirror=optusnet.dl.sourceforge.net
           => `./verdan32.exe?download&failedmirror=optusnet.dl.sourceforge.net'
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://nchc.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe [following]
--17:00:55--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/verdan32.exe
           => `./verdan32.exe'
Resolving nchc.dl.sourceforge.net... 211.79.60.17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 351,992 (344K) [application/x-msdownload]

100%[====================================>] 351,992      160.84K/s             

17:00:58 (160.58 KB/s) - `./verdan32.exe' saved [351992/351992]

--17:00:58--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
           => `./webdin32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://prdownloads.sourceforge.net/corefonts/webdin32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--17:00:58--  http://prdownloads.sourceforge.net/corefonts/webdin32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./webdin32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving prdownloads.sourceforge.net... 66.35.250.217
Connecting to prdownloads.sourceforge.net|66.35.250.217|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://downloads.sourceforge.net/corefonts/webdin32.exe?download&failedmirror=surfnet.dl.sourceforge.net [following]
--17:00:59--  http://downloads.sourceforge.net/corefonts/webdin32.exe?download&failedmirror=surfnet.dl.sourceforge.net
           => `./webdin32.exe?download&failedmirror=surfnet.dl.sourceforge.net'
Resolving downloads.sourceforge.net... 66.35.250.203
Connecting to downloads.sourceforge.net|66.35.250.203|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://jaist.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe [following]
--17:00:59--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/webdin32.exe
           => `./webdin32.exe'
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 185,072 (181K) [application/octet-stream]

100%[====================================>] 185,072      119.48K/s             

17:01:01 (119.18 KB/s) - `./webdin32.exe' saved [185072/185072]

Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
Couldn't get cwd: No such file or directory

```Oh, and yes, I entered my password.

---

### Post by aimpau on 2008-05-11
It should appear. Try logging out the log in. Also, make sure you have defoma installed.

---

### Post by H.Callahan on 2008-05-11
> **aimpau said:**
> It should appear. Try logging out the log in. Also, make sure you have defoma installed.

Been there, done that...

There was a message in the middle of the install (ascii graphics) saying something about deforma, but I checked and it IS installed.

---

### Post by shifty_powers on 2008-05-11
applications>add/remove

click on the filter to show all available applications

search for restricted

select ubuntu restricted extras

click apply

---

### Post by H.Callahan on 2008-05-12
Ok, I went to work on this problem this morning and all of a sudden the fonts are showing up.  This was without a logout/login or a restart.  

Do the fonts need to have time to initialize or something?

---

### Post by Kapitän Rotbart on 2008-05-12
It shouldn't require time to show up. Did you fix broken packages in Synaptic by any chance?

---

### Post by H.Callahan on 2008-05-12
Well, I uninstalled and reinstalled several times all with the same outcome.  Only after I left it alone for a couple of days, did it start working.  The definition of insanity is trying the same thing over and over again and expecting a different outcome.  Apparently, that is not true for computers.

](*,)

---

