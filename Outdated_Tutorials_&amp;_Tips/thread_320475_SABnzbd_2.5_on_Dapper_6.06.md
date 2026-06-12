---
title: "SABnzbd 2.5 on Dapper 6.06"
date: 2006-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by jtt1560 on 2006-12-17
Here is a script to install SABnzbd from source on Dapper 6.06

**1)** Paste this code into your terminal window: 

```

sudo apt-get install libbz2-dev zlib1g-dev

sudo apt-get install g++
sudo apt-get install make
sudo apt-get install par2

mkdir ~/.SABnzbd
mkdir ~/Desktop/SABInstall_Files
cd ~/Desktop/SABInstall_Files
wget http://www.python.org/ftp/python/2.4.3/Python-2.4.3.tgz
wget http://download.cherrypy.org/cherrypy/2.2.1/CherryPy-2.2.1.tar.gz
wget http://surfnet.dl.sourceforge.net/sourceforge/cheetahtemplate/Cheetah-1.0.tar.gz
wget http://effbot.org/downloads/elementtree-1.2.6-20050316.tar.gz
wget http://sabnzbd.sourceforge.net/yenc-0.3.tar.gz
wget http://kambing.vlsm.org/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.5.4-0.1_i386.deb
wget http://superb-east.dl.sourceforge.net/sourceforge/sabnzbd/SABnzbd-0.2.5.tar.gz

sudo dpkg -i unrar_3.5.4-0.1_i386.deb

tar -xzvf Python-2.4.3.tgz
tar -xzvf CherryPy-2.2.1.tar.gz
tar -xzvf Cheetah-1.0.tar.gz
tar -xzvf elementtree-1.2.6-20050316.tar.gz
tar -xzvf yenc-0.3.tar.gz
tar -xzvf SABnzbd-0.2.5.tar.gz

```

**2) Change in this code <YOURUSERNAME> to your Ubuntu login name**
and then paste it in your terminal window.
```

cd ~/Desktop/SABInstall_Files/Python-2.4.3
./configure --prefix=/home/<YOURUSERNAME>/.SABnzbd
make && make install

```
**3) **Now copy and paste the rest of the code in the terminal window.

```

cd ~/Desktop/SABInstall_Files/CherryPy-2.2.1
~/.SABnzbd/bin/python setup.py install

cd ~/Desktop/SABInstall_Files/Cheetah-1.0
~/.SABnzbd/bin/python setup.py install

cd ~/Desktop/SABInstall_Files/elementtree-1.2.6-20050316
~/.SABnzbd/bin/python setup.py install

cd ~/Desktop/SABInstall_Files/yenc-0.3
~/.SABnzbd/bin/python setup.py install

cd ~/Desktop/SABInstall_Files/SABnzbd-0.2.5
mkdir ~/.SABnzbd/sabnzbd
cp -R SABnzbd.ini.sample SABnzbd.py sabnzbd/ templates/ ~/.SABnzbd/sabnzbd
cd ~/.SABnzbd/sabnzbd
mv SABnzbd.ini.sample SABnzbd.ini

cd ~/.SABnzbd/sabnzbd
chmod +x SABnzbd.py
mkdir ~/.SABnzbd/sabnzbd/nzb
mkdir ~/.SABnzbd/sabnzbd/nzb/backup
chmod -R +x ~/.SABnzbd/sabnzbd/sabnzbd

```

**4) **Finish it up

Edit files located in /home/<YOURUSERNAME>/.SABnzbd/sabnzbd
Now edit your SABnzbd.py

Change the first line in SABnzbd.py
#!/usr/bin/python -OO
to
#!/home/<YOURUSERNAME>/.SABnzbd/bin/python -OO

Now edit your SABnzbd.ini
example:
## location of your log directory, "" to disable logging
    log_dir = "/home/<YOURUSERNAME>/.SABnzbd/sabnzbd/templates"

SABnzbd will not run unless the directories are correctly edited. **DO NOT USE** the same directory for downloaded files and completed files. They must be different. Make sure to set a directory for the log files. If you have a problem look at the log file in the same directory to see what the error is. It will be easily fixed if there is a configuration problem. The log file is great at telling you why the program did not run. 

**RUN IT**
cd ~/.SABnzbd/sabnzbd
./SABnzbd.py -d -f SABnzbd.ini

load your webbrowser and goto the following address:
[http://127.0.0.1:8080/sabnzbd/](http://127.0.0.1:8080/sabnzbd/)

---

### Post by KeithWatson on 2007-02-15
Thanks for this very well written guide.  I just followed it in Edgy 6.10 and everything works great.

I am a bit of a newbie, and I ran into a roadblock that I thought I might document to help others with my limited experience.  After following the guide above when I tried to run SABnzbd it still did not work.  Eventually I realized that maybe I should make the file SABnzbd.ini executable so I typed the line below into terminal and everything works perfectly now.

**sudo chmod +x SABnzbd.ini**

Also, I just realized that I could just copy the two lines that make SABnzb run into a text file and save it to my desk top.  Now when I double click that file I am prompted to either display or run in terminal.  There may be a better way to accomplish this, but at least now I don't have to type those two lines every time.

---

### Post by felker2 on 2007-02-18
In the ~/.SABnzbd/sabnzbd I created some directories:

 mkdir log
 mkdir download
 mkdir complete
 mkdir cache

I then edited the directory settings in SABnzbd.ini. The result:

[email]sander@kubuntu:~/.SABn[/email]zbd/sabnzbd$ grep _dir SABnzbd.ini

    web_dir = "/home/sander/.SABnzbd/sabnzbd/templates"
    download_dir = "/home/sander/.SABnzbd/sabnzbd/download"
    complete_dir = "/home/sander/.SABnzbd/sabnzbd/complete"
    nzb_backup_dir = ""
    cache_dir = "/home/sander/.SABnzbd/sabnzbd/cache"
    log_dir = "/home/sander/.SABnzbd/sabnzbd/log"
    dirscan_dir = ""


Via the webinterface I configured the newsserver, and then everything worked!


BTW: I think

     ./configure --prefix=/home/<YOURUSERNAME>/.SABnzbd

can be issued as

     ./configure --prefix=/home/`whoami`/.SABnzbd

The same for changing directory to /home/<YOURUSERNAME>/.SABnzbd/sabnzbd : 

    cd /home/`whoami`/.SABnzbd/sabnzbd 

or just 

    cd ~/.SABnzbd/sabnzbd

---

### Post by roppedoez on 2007-02-19
hello, 
i've got the problem that when i try to start with ./SABnzbd.py -d -f SABnzbd.ini, i get the error: Can't write to logfile.
what did i wrong? i placed the log directory here: ~/news/log
i followed all instructions from: [http://drbyte.wiki.xs4all.nl/index.php?title=drbyte:Community_Portal#Installation_SABnzbd](http://drbyte.wiki.xs4all.nl/index.php?title=drbyte:Community_Portal#Installation_SABnzbd)

and modified the SABnzb.ini, filled in all directories that were asked, and created them all in ~/news

can somebody help?
thanks

---

### Post by felker2 on 2007-02-19
@roppedoez:

Does the directory ~/news/log exist (as SABnzbd does *not* create directories)?

And if the directory does exist, have you tried filling out the complete path in SABnzbd.ini, so without the ~?

---

### Post by roppedoez on 2007-02-19
okay that seems to work... SABnzbd won't start yet, but it's progress;) 
maybe somebody can help with this problem? a logfile used to be handy, but i think i'm not experienced enough to track down the problem. somebody got an idea?

i now have the following log:
```
2007-02-19 21:13:17,190::INFO::--------------------------------
2007-02-19 21:13:17,191::INFO::SABnzbd v0.2.5
2007-02-19 21:13:17,191::INFO::Initializing SABnzbd v0.2.5
2007-02-19 21:13:17,191::DEBUG::FAIL_ON_CRC -> False
2007-02-19 21:13:17,191::DEBUG::CREATE_GROUP_FOLDERS -> False
2007-02-19 21:13:17,192::DEBUG::DO_FILE_JOIN -> True
2007-02-19 21:13:17,192::DEBUG::DO_UNZIP -> True
2007-02-19 21:13:17,192::DEBUG::DO_UNRAR -> True
2007-02-19 21:13:17,192::DEBUG::DO_SAVE -> False
2007-02-19 21:13:17,193::DEBUG::PAR_CLEANUP -> True
2007-02-19 21:13:17,193::DEBUG::CLEANUP_LIST -> []
2007-02-19 21:13:17,193::DEBUG::UMASK -> 493
2007-02-19 21:13:17,193::DEBUG::SEND_GROUP -> False
2007-02-19 21:13:17,193::DEBUG::CREATE_CAT_FOLDERS -> False
2007-02-19 21:13:17,194::DEBUG::CREATE_CAT_SUB -> False
2007-02-19 21:13:17,194::INFO::DOWNLOAD_DIR: /home/roppedoez/news/download
2007-02-19 21:13:17,194::INFO::COMPLETE_DIR: /home/roppedoez/news/complete
2007-02-19 21:13:17,194::INFO::NZB_BACKUP_DIR: /home/roppedoez/news/nzbbackup
2007-02-19 21:13:17,195::INFO::CACHE_DIR: /home/roppedoez/news/cache
2007-02-19 21:13:17,195::INFO::dirscan_dir: 
2007-02-19 21:13:17,195::INFO::BANDWITH_LIMIT: 0.0
2007-02-19 21:13:17,195::INFO::schedlines: []
2007-02-19 21:13:17,196::INFO::dirscan_opts: 1
2007-02-19 21:13:17,196::INFO::top_only: True
2007-02-19 21:13:17,196::INFO::auto_sort: False
2007-02-19 21:13:17,196::INFO::[sabnzbd] Loading data for bytes.sab from /home/roppedoez/news/cache/bytes.sab
2007-02-19 21:13:17,197::INFO::[sabnzbd] Loading data for queue.sab from /home/roppedoez/news/cache/queue.sab
2007-02-19 21:13:17,198::INFO::_yenc module... found!
2007-02-19 21:13:17,198::INFO::celementtree module... NOT found!
2007-02-19 21:13:17,198::INFO::par2 binary... found!
2007-02-19 21:13:17,199::INFO::rar binary... found!
2007-02-19 21:13:17,199::INFO::unzip binary... found!
2007-02-19 21:13:17,202::INFO::Starting SABnzbd v0.2.5
2007-02-19 21:13:17,204::DEBUG::[sabnzbd] Starting postprocessor
2007-02-19 21:13:17,206::DEBUG::[sabnzbd] Starting assembler
2007-02-19 21:13:17,216::DEBUG::[sabnzbd] Starting downloader
2007-02-19 21:13:17,217::INFO::Starting web-interface
2007-02-19 21:13:22,449::ERROR::Failed to start web-interface
Traceback (most recent call last):
  File "./SABnzbd.py", line 307, in main
    cherrypy.server.start()
  File "/home/roppedoez/.SABnzbd/lib/python2.4/site-packages/cherrypy/_cpserver.py", line 72, in start
    Engine.start(self)
  File "/home/roppedoez/.SABnzbd/lib/python2.4/site-packages/cherrypy/_cpengine.py", line 104, in start
    self._start()
  File "/home/roppedoez/.SABnzbd/lib/python2.4/site-packages/cherrypy/_cpserver.py", line 79, in _start
    self.start_http_server()
  File "/home/roppedoez/.SABnzbd/lib/python2.4/site-packages/cherrypy/_cpserver.py", line 99, in start_http_server
    wait_for_free_port(host, port)
  File "/home/roppedoez/.SABnzbd/lib/python2.4/site-packages/cherrypy/_cpserver.py", line 252, in wait_for_free_port
    raise cherrypy.NotReady("Port not free.")
NotReady: Port not free.
2007-02-19 21:13:22,452::INFO::SABnzbd shutting down...
2007-02-19 21:13:22,452::DEBUG::Stopping downloader
2007-02-19 21:13:22,457::INFO::[downloader] Shutting down
2007-02-19 21:13:22,457::DEBUG::Stopping assembler
2007-02-19 21:13:22,461::INFO::[assembler] Shutting down
2007-02-19 21:13:22,461::DEBUG::Stopping postprocessor
2007-02-19 21:13:22,465::INFO::[nzbqueue] Saving queue
2007-02-19 21:13:22,465::INFO::[sabnzbd] Saving data for queue.sab in /home/roppedoez/news/cache/queue.sab
2007-02-19 21:13:22,466::INFO::[sabnzbd] Saving data for bytes.sab in /home/roppedoez/news/cache/bytes.sab
2007-02-19 21:21:16,314::INFO::--------------------------------
2007-02-19 21:21:16,315::INFO::SABnzbd v0.2.5
2007-02-19 21:21:16,315::INFO::Initializing SABnzbd v0.2.5
2007-02-19 21:21:16,315::DEBUG::FAIL_ON_CRC -> False
2007-02-19 21:21:16,316::DEBUG::CREATE_GROUP_FOLDERS -> False
2007-02-19 21:21:16,316::DEBUG::DO_FILE_JOIN -> True
2007-02-19 21:21:16,316::DEBUG::DO_UNZIP -> True
2007-02-19 21:21:16,317::DEBUG::DO_UNRAR -> True
2007-02-19 21:21:16,317::DEBUG::DO_SAVE -> False
2007-02-19 21:21:16,317::DEBUG::PAR_CLEANUP -> True
2007-02-19 21:21:16,317::DEBUG::CLEANUP_LIST -> []
2007-02-19 21:21:16,318::DEBUG::UMASK -> 493
2007-02-19 21:21:16,318::DEBUG::SEND_GROUP -> False
2007-02-19 21:21:16,318::DEBUG::CREATE_CAT_FOLDERS -> False
2007-02-19 21:21:16,319::DEBUG::CREATE_CAT_SUB -> False
2007-02-19 21:21:16,319::INFO::DOWNLOAD_DIR: /home/roppedoez/news/download
2007-02-19 21:21:16,319::INFO::COMPLETE_DIR: /home/roppedoez/news/complete
2007-02-19 21:21:16,320::INFO::NZB_BACKUP_DIR: /home/roppedoez/news/nzbbackup
2007-02-19 21:21:16,320::INFO::CACHE_DIR: /home/roppedoez/news/cache
2007-02-19 21:21:16,320::INFO::dirscan_dir: 
2007-02-19 21:21:16,321::INFO::BANDWITH_LIMIT: 0.0
2007-02-19 21:21:16,321::INFO::schedlines: []
2007-02-19 21:21:16,321::INFO::dirscan_opts: 1
2007-02-19 21:21:16,322::INFO::top_only: True
2007-02-19 21:21:16,322::INFO::auto_sort: False
2007-02-19 21:21:16,322::INFO::[sabnzbd] Loading data for bytes.sab from /home/roppedoez/news/cache/bytes.sab
2007-02-19 21:21:16,323::INFO::[sabnzbd] Loading data for queue.sab from /home/roppedoez/news/cache/queue.sab
2007-02-19 21:21:16,325::INFO::_yenc module... found!
2007-02-19 21:21:16,325::INFO::celementtree module... NOT found!
2007-02-19 21:21:16,325::INFO::par2 binary... found!
2007-02-19 21:21:16,325::INFO::rar binary... found!
2007-02-19 21:21:16,326::INFO::unzip binary... found!
2007-02-19 21:21:16,330::INFO::Starting SABnzbd v0.2.5
2007-02-19 21:21:16,334::DEBUG::[sabnzbd] Starting postprocessor
2007-02-19 21:21:16,418::DEBUG::[sabnzbd] Starting assembler
2007-02-19 21:21:16,419::DEBUG::[sabnzbd] Starting downloader
2007-02-19 21:21:16,420::INFO::Starting web-interface
2007-02-19 21:21:21,671::ERROR::Failed to start web-interface
Traceback (most recent call last):
  File "./SABnzbd.py", line 307, in main
    cherrypy.server.start()
  File "/home/roppedoez/.SABnzbd/lib/python2.4/site-packages/cherrypy/_cpserver.py", line 72, in start
    Engine.start(self)
  File "/home/roppedoez/.SABnzbd/lib/python2.4/site-packages/cherrypy/_cpengine.py", line 104, in start
    self._start()
  File "/home/roppedoez/.SABnzbd/lib/python2.4/site-packages/cherrypy/_cpserver.py", line 79, in _start
    self.start_http_server()
  File "/home/roppedoez/.SABnzbd/lib/python2.4/site-packages/cherrypy/_cpserver.py", line 99, in start_http_server
    wait_for_free_port(host, port)
  File "/home/roppedoez/.SABnzbd/lib/python2.4/site-packages/cherrypy/_cpserver.py", line 252, in wait_for_free_port
    raise cherrypy.NotReady("Port not free.")
NotReady: Port not free.
2007-02-19 21:21:21,672::INFO::SABnzbd shutting down...
2007-02-19 21:21:21,672::DEBUG::Stopping downloader
2007-02-19 21:21:21,673::INFO::[downloader] Shutting down
2007-02-19 21:21:21,673::DEBUG::Stopping assembler
2007-02-19 21:21:21,674::INFO::[assembler] Shutting down
2007-02-19 21:21:21,674::DEBUG::Stopping postprocessor
2007-02-19 21:21:21,674::INFO::[nzbqueue] Saving queue
2007-02-19 21:21:21,675::INFO::[sabnzbd] Saving data for queue.sab in /home/roppedoez/news/cache/queue.sab
2007-02-19 21:21:21,675::INFO::[sabnzbd] Saving data for bytes.sab in /home/roppedoez/news/cache/bytes.sab
```

---

### Post by felker2 on 2007-02-19
@roppedoez:

That's an easy one:

2007-02-19 21:13:17,217::INFO::Starting web-interface
2007-02-19 21:13:22,449::ERROR::Failed to start web-interface
<snip>
raise cherrypy.NotReady("Port not free.")
NotReady: Port not free.

So ... I bet you have already something running on port 8080. Change that port in SABnzbd.ini to something else (8888, 9090 or something else), and retry.

And: keep reading the log.

---

### Post by felker2 on 2007-02-19
I now discover the unrar-functionality is not working: the rar's are just sitting there in the directory complete/

"Enable Unrar: Enable built-in unrar functionality." is "yes", as can be seen in the ini:

```
    ## Enable/disable unraring
    ## 0 = Disabled
    ## 1 = Enabled
    enable_unrar = 1
```

And even the log says so:

```
2007-02-19 22:16:40,508::DEBUG::DO_UNZIP -> True
2007-02-19 22:16:40,509::DEBUG::DO_UNRAR -> True        <<<----
2007-02-19 22:16:40,509::DEBUG::DO_SAVE -> False
2007-02-19 22:16:40,509::DEBUG::PAR_CLEANUP -> True
```

And unrar is on my system:

```
$ which unrar
/usr/bin/unrar
```

The logging in the webinterface says:

```
2007-02-19 22:16:39	Tblabla.nzb	False
	

Stage Par2
    [PAR-INFO] Tblabla: => Verified in 509.4s, all files correct
    [DEL-INFO] Tblabla: => Deleted 2 file(s)

2007-02-19 20:01:20
```



So: Tips why unrar is not happening?

---

### Post by roppedoez on 2007-02-19
okay, i restarted my computer, and tried again.  the same problems, but another logfile:
```
2007-02-19 23:32:58,642::INFO::--------------------------------
2007-02-19 23:32:58,642::INFO::SABnzbd v0.2.5
2007-02-19 23:32:58,642::INFO::Initializing SABnzbd v0.2.5
2007-02-19 23:32:58,643::DEBUG::FAIL_ON_CRC -> False
2007-02-19 23:32:58,643::DEBUG::CREATE_GROUP_FOLDERS -> False
2007-02-19 23:32:58,643::DEBUG::DO_FILE_JOIN -> True
2007-02-19 23:32:58,643::DEBUG::DO_UNZIP -> True
2007-02-19 23:32:58,644::DEBUG::DO_UNRAR -> True
2007-02-19 23:32:58,644::DEBUG::DO_SAVE -> False
2007-02-19 23:32:58,644::DEBUG::PAR_CLEANUP -> True
2007-02-19 23:32:58,644::DEBUG::CLEANUP_LIST -> []
2007-02-19 23:32:58,645::DEBUG::UMASK -> 493
2007-02-19 23:32:58,645::DEBUG::SEND_GROUP -> False
2007-02-19 23:32:58,645::DEBUG::CREATE_CAT_FOLDERS -> False
2007-02-19 23:32:58,645::DEBUG::CREATE_CAT_SUB -> False
2007-02-19 23:32:58,645::INFO::DOWNLOAD_DIR: /home/roppedoez/news/download
2007-02-19 23:32:58,646::INFO::COMPLETE_DIR: /home/roppedoez/news/complete
2007-02-19 23:32:58,646::INFO::NZB_BACKUP_DIR: /home/roppedoez/news/nzbbackup
2007-02-19 23:32:58,646::INFO::CACHE_DIR: /home/roppedoez/news/cache
2007-02-19 23:32:58,646::INFO::dirscan_dir: 
2007-02-19 23:32:58,647::INFO::BANDWITH_LIMIT: 0.0
2007-02-19 23:32:58,647::INFO::schedlines: []
2007-02-19 23:32:58,647::INFO::dirscan_opts: 1
2007-02-19 23:32:58,647::INFO::top_only: True
2007-02-19 23:32:58,648::INFO::auto_sort: False
2007-02-19 23:32:58,648::INFO::[sabnzbd] Loading data for bytes.sab from /home/roppedoez/news/cache/bytes.sab
2007-02-19 23:32:58,672::INFO::[sabnzbd] Loading data for queue.sab from /home/roppedoez/news/cache/queue.sab
2007-02-19 23:32:58,676::INFO::_yenc module... found!
2007-02-19 23:32:58,676::INFO::celementtree module... NOT found!
2007-02-19 23:32:58,676::INFO::par2 binary... found!
2007-02-19 23:32:58,676::INFO::rar binary... found!
2007-02-19 23:32:58,676::INFO::unzip binary... found!
2007-02-19 23:32:58,679::INFO::Starting SABnzbd v0.2.5
2007-02-19 23:32:58,680::DEBUG::[sabnzbd] Starting postprocessor
2007-02-19 23:32:58,680::DEBUG::[sabnzbd] Starting assembler
2007-02-19 23:32:58,681::DEBUG::[sabnzbd] Starting downloader
2007-02-19 23:32:58,700::INFO::Starting web-interface

```
maybe there is a problem in this line?: ```
2007-02-19 23:32:58,676::INFO::celementtree module... NOT found! 
```

---

### Post by felker2 on 2007-02-20
My log also says:

```
[email]sander@kubuntu:~/.SABn[/email]zbd/sabnzbd/log$ grep -i elementtree *
SABnzbd.log.4:2007-02-18 21:23:55,161::INFO::celementtree module... NOT found!
[email]sander@kubuntu:~/.SABn[/email]zbd/sabnzbd/log
$
```

and apparantly that doesn't need to be a problem: SABnzbd is running on my system.

So: what happens if you try to connect to your SABnzbd using your webbrowser? What makes you think things are not yet OK?

With
```
ps -ef | grep -i sabnzb
```

you can see whether SABnzbd is still running

---

### Post by roppedoez on 2007-02-20
well maybe i don't understand it well, but it seems that when i open my browser there is something wrong with the starting process of SABnzb
the steps i take:

1
```
roppedoez@roppedoez-desktop:~$ ps -ef | grep -i sabnzb
1000      5984  5966  0 23:28 pts/0    00:00:00 grep -i sabnzb

roppedoez@roppedoez-desktop:~$ ps -ef | grep -i sabnzb
1000      5990  5966  0 23:28 pts/0    00:00:00 grep -i sabnzb
```

2
```
roppedoez@roppedoez-desktop:~/.SABnzbd/sabnzbd$ ./SABnzbd.py -d -f SABnzbd.ini
```

3
when i go to [http://127.0.0.1:8080/sabnzbd/](http://127.0.0.1:8080/sabnzbd/) in my webbrowser i get the error: 
```
500 Internal error

The server encountered an unexpected condition which prevented it from fulfilling the request.

Powered by CherryPy 2.2.1

```

4
```
roppedoez@roppedoez-desktop:~/.SABnzbd/sabnzbd$ ps -ef | grep -i sabnzb
1000      6013     1  0 23:29 ?        00:00:00 /home/roppedoez/.SABnzbd/bin/python -OO ./SABnzbd.py -d -f SABnzbd.ini
1000      6067  5966  0 23:30 pts/0    00:00:00 grep -i sabnzb
```

---

### Post by roppedoez on 2007-02-20
i get in my browser the menu, were i can fill in my username and password for the webinterface, but after filling in correctly i get the error:
```
500 Internal error

The server encountered an unexpected condition which prevented it from fulfilling the request.

Powered by CherryPy 2.2.1
```

Okay, maybe i've got something wrong in my .ini

do i have to fill in something by:
```
## host we should listen on, leave "" for localhost
host = ""
```

this is my SABnzb.ini (at **** i fill in my information of my newsserver): 
```
__version__ = 016

[misc]
    ## host we should listen on, leave "" for localhost
    host = ""
    
    ## port we should listen on
    port = 8080
    
    ## username for the web-interface
    username = "roppedoez"
    
    ## password for the web-interface
    password = "****"
    
    ## web file dir for (custom) Cheetah templates and the default.css file
    web_dir = "/home/roppedoez/news/webdir"
    
    ## dir to put downloads to, won't be created automatically
    download_dir = "/home/roppedoez/news/download"
    
    ## dir to put completed downloads to, won't be created automatically
    complete_dir = "/home/roppedoez/news/complete"
    
    ## If specified, .nzbs fetched by postid (or added by the dirscanner) will 
    ## be backed up to this readable/writeable dir
    nzb_backup_dir = "/home/roppedoez/news/nzbbackup"
    
    ## dir to store cache and cookie files, windows users should
    ## leave this at .
    cache_dir = "/home/roppedoez/news/cache"
    
    ## location of your log directory, "" to disable logging
    log_dir = "/home/roppedoez/news/log"
    
    ## dirscan directory
    ## SABnzbd will consume everything in that dir
    ## while trying to add it to the queue
    dirscan_dir = ""
    
    ## Scheduling options
    ## Syntax: minute hour day action
    ##         1st argument must be 0-59 (minute)
    ##         2nd argument must be 0-24 (hour)
    ##         3rd argument must be 1-7 (day) or *
    ##         4th argument must be resume or pause
    ##
    ## e.g schedlines = 0 7 * pause, 0 21 * resume 
    ##     to pause SABnzbd at 7:00 and resume operation at 21:00
    schedlines = ,
    
    ## default options for dirscan added items
    ## 0 = None
    ## 1 = +Repair
    ## 2 = +Unpack
    ## 3 = +Delete
    dirscan_opts = 1
    
    ## Enable/disable filejoining
    ## 0 = Disabled
    ## 1 = Enabled
    enable_filejoin = 1
    
    ## Enable/disable unraring
    ## 0 = Disabled
    ## 1 = Enabled
    enable_unrar = 1
    
    ## Enable/disable unzipping
    ## 0 = Disabled
    ## 1 = Enabled
    enable_unzip = 1
    
    ## Enable/disable periodic queue saving
    ## 0 = Disabled
    ## 1 = Enabled
    ## Enable this on unstable systems
    enable_save = 0
    
    ## Enable/disable
    ## 0 = Disabled
    ## 1 = Enabled
    ## Enable to cleanup par2 files 
    ## (only if verifiying/repairing succeded)
    enable_par_cleanup = 1
    
    ## should we failover on yenc crc errors
    ## 0 = no
    ## 1 = yes
    fail_on_crc = 0
    
    ## should we download to group folders? 
    ## (i.e /my/download/dir/alt.bin.whatever/somepost/)
    ## 0 = no
    ## 1 = yes
    create_group_folders = 0
    
    ## bandwith limit
    ## 0 == ignore
    ## Slowdown factor, try values between 0.01 and 1.0.
    bandwith_limit = 0
    
    ## Cleanup List
    ## List of file_extensions that should be deleted
    ## Example: ".nfo," or ".nfo, .sfv"
    cleanup_list = ,
    
    ## Only get articles from topmost collection
    ## Enable for less memory usage
    ## Disable for more efficient downloading
    ## 0 = Disabled
    ## 1 = Enabled
    top_only = 1
    
    ## Automatically sort by average age
    ## 0 = No
    ## 1 = Yes
    auto_sort = 0
    
    ## Send group command before requesting articles
    ## 0 = No
    ## 1 = Yes
    send_group = 0
    
    ## Article cache limit
    ## 0 = Disable Cache
    ## -1 = Unlimited cache
    ## >0 = Maximum memory (in bytes) to use for cache
    cache_limit = 0
    
    ## Umask to use for directories/files
    umask = 755
    
[logging]
    ## max size of SABnzbd.log (in bytes)
    max_log_size = 5242880
    
    ## how many backups of SABnzbd.log to keep around
    log_backups = 5
    
    ## enable cherrypy logging
    ## 0 = no
    ## 1 = yes
    enable_cherrypy_logging = 1
    
## Fill in your servers here
## If your server doesn't need password auth set
## username and password to ''
## fillserver field must be 0 for non-fillservers (>0 otherwise)
[servers]
#    [[server 0]]
#       host = ****
#       port = 119
#       username = ****
#       password = ****
#       connections = 3
#       fillserver = 0
#    [[server 1]]
#  	host = news.myfillserver.com
#  	port = 119
#  	username = ""
#  	password = "" 
#  	connections = 8
#       fillserver = 1

## www.newzbin.com support
[newzbin]
    username = ""
    password = ""
    
    ## Place downloads into newzbin.com category folders
    ## 0 = No
    ## 1 = Root category only
    ## 2 = Root category + subcategory
    create_category_folders = 0
```

---

### Post by felker2 on 2007-02-21
I solved the not-unrarring problem by selecting the U-option for each file-in-donwload.

---

### Post by disturbedite on 2007-02-21
i'm trying this app out since i couldn't get hellanzb to do crap.  i'm on kubuntu 7.04 herd 4.  i did everything according to the tutorial (except i installed python 2.5, and i installed the other dependencies from the repos--problem?) and i get this when trying to launch sabnzb with ./SABnzbd.py -d -f SABnzbd.ini:

Traceback (most recent call last):
  File "./SABnzbd.py", line 37, in <module>
    import cherrypy
ImportError: No module named cherrypy

i have the python-cherrypy 2.2.1-3ubuntu1 package installed and it says that this version of cherrypy is backwards compatible with version 2.0

can anyone suggest a solution please?

---

### Post by pirothezero on 2007-03-02
Thank you so much for this copy and paste install. I been fightting with hellanzb for the last two weeks on mismatches and thrown exceptions, everything went wrong after i upgraded. No matter what I did it would still error out eventually or stall on a download and never finish it. This has made me one hell of a happy camper.

---

### Post by pirothezero on 2007-03-02
> **disturbedite said:**
> i'm trying this app out since i couldn't get hellanzb to do crap.  i'm on kubuntu 7.04 herd 4.  i did everything according to the tutorial (except i installed python 2.5, and i installed the other dependencies from the repos--problem?) and i get this when trying to launch sabnzb with ./SABnzbd.py -d -f SABnzbd.ini:

Traceback (most recent call last):
  File "./SABnzbd.py", line 37, in <module>
    import cherrypy
ImportError: No module named cherrypy

i have the python-cherrypy 2.2.1-3ubuntu1 package installed and it says that this version of cherrypy is backwards compatible with version 2.0

can anyone suggest a solution please?

Only thing I can think of is that when you were pasting lines over you may have forgotten a line. May double check and try the install of each package again, making sure that when the terminal looks finish to look at the prompt and make sure there isnt a left over instruction ready to be sent.

---

### Post by baersaerk on 2007-03-06
roppedoez, i think you got the exact same problem as i had, it got nothing to do with

```
    
## host we should listen on, leave "" for localhost
    host = ""
```

what i did according to the guide was the following

```
Now edit your SABnzbd.ini
example:
## location of your log directory, "" to disable logging
log_dir = "/home/<YOURUSERNAME>/.SABnzbd/sabnzbd/templates"
```

wich I understand from actually reading the .ini is wrong, so i created a dir named log and pointed my log files to that location instead, and from looking at the files in templates i understood that it was the html and stuff for the actuall homepage, and back at the ini i found 

```

    ## web file dir for (custom) Cheetah templates and the default.css file
    web_dir = "/home/roppedoez/news/webdir"

```

wich i pointed at something like ~/.SABnzbd/sabnzbd/templates/, i dont know what you got in your webdir, but it gotta be a bunch of files with html in them and the default.css. 

dont remember the exact names now, me beeing at work and all, but i think you understand the solution.

The error for me was that it didnt find the code for the homepage, and i think you got the same problem, even if you dont maybe someone else followed the example to a tee and got the same error.

Except for the faulty example (i think) the guide was extremely good, and i looked for something like it for ages, or at least a couple of days =)

gl and hope it works :)

ps. i'm on edgy

---

### Post by frolle on 2007-04-23
I am getting this error. Can anybody tell me how to avoid it?

[email]kristian@kristian-desktop:~/.SABn[/email]zbd/sabnzbd$ ./SABnzbd.py -d -f SABnzbd.ini
Traceback (most recent call last):
  File "./SABnzbd.py", line 44, in ?
    from sabnzbd.interface import *
  File "/home/kristian/.SABnzbd/sabnzbd/sabnzbd/interface.py", line 39, in ?
    from Cheetah.Template import Template
ImportError: No module named Cheetah.Template
[email]kristian@kristian-desktop:~/.SABn[/email]zbd/sabnzbd$

---

### Post by phenest on 2007-05-07
Someone please help me here. I get this same error message with a lot of things I try to install (never done this sort of stuff before).
```
steve@dimension:~$ cd ~/Desktop/SABInstall_Files/Python-2.4.3
steve@dimension:~/Desktop/SABInstall_Files/Python-2.4.3$ sh ./configure --prefix=/mnt/home/steve/.SABnzbd
checking MACHDEP... linux2
checking EXTRAPLATDIR... 
checking for --without-gcc... no
checking for --with-cxx=<compiler>... no
checking for c++... c++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... configure: error: cannot run C++ compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.

```

I was trying to do something similar with Metisse, but I don't know what's going on (or not going on, as the case may be).

---

### Post by Arumite on 2007-08-07
GREAT SCRIPT!!!

Up until I saw your post I had no idea that you could use the terminal that way.  I just recently set-up this linux box im on and am still getting used to Ubuntu 7.04.  I tried hellanzb but it was a real pain to install.  I had to try your guide a few times before I got it right, but it is very user friendly.  My problem is this...  505 error when trying to run the webpage.  Error log below.  I matched it up to some of the other posts and found this one difference, but am having no luck finding a solution on google.

```
2007-08-06 23:45:47,333::INFO::schedlines: []
2007-08-06 23:45:47,333::INFO::dirscan_opts: 1
2007-08-06 23:45:47,334::INFO::top_only: True
2007-08-06 23:45:47,334::INFO::auto_sort: False
2007-08-06 23:45:47,334::INFO::[sabnzbd] Loading data for bytes.sab from /home/arumite/SABnzbd/cache/bytes.sab
2007-08-06 23:45:47,334::INFO::[sabnzbd] /home/arumite/SABnzbd/cache/bytes.sab missing
2007-08-06 23:45:47,335::INFO::[sabnzbd] Loading data for queue.sab from /home/arumite/SABnzbd/cache/queue.sab
2007-08-06 23:45:47,335::INFO::[sabnzbd] /home/arumite/SABnzbd/cache/queue.sab missing
2007-08-06 23:45:47,337::INFO::_yenc module... found!
2007-08-06 23:45:47,337::INFO::celementtree module... NOT found!
2007-08-06 23:45:47,337::INFO::par2 binary... found!
2007-08-06 23:45:47,338::INFO::rar binary... found!
2007-08-06 23:45:47,338::INFO::unzip binary... found!
2007-08-06 23:45:47,343::INFO::Starting SABnzbd v0.2.5
```

**Edit - Here is my INI
```

__version__ = 016



[misc]

    ## host we should listen on, leave "" for localhost

    host = ""

    

    ## port we should listen on

    port = 8080

    

    ## username for the web-interface

    username = ""

    

    ## password for the web-interface

    password = ""

    

    ## web file dir for (custom) Cheetah templates and the default.css file

    web_dir = "/home/arumite/.SABnzbd/sabnzbd/templates"

    

    ## dir to put downloads to, won't be created automatically

    download_dir = "/home/arumite/SABnzbd/download"

    

    ## dir to put completed downloads to, won't be created automatically

    complete_dir = "/home/arumite/SABnzbd/complete"

    

    ## If specified, .nzbs fetched by postid (or added by the dirscanner) will 

    ## be backed up to this readable/writeable dir

    nzb_backup_dir = "/home/arumite/SABnzbd/backup"

    

    ## dir to store cache and cookie files, windows users should

    ## leave this at .

    cache_dir = "/home/arumite/SABnzbd/cache"

    

    ## location of your log directory, "" to disable logging

    log_dir = "/home/arumite/SABnzbd/log"

    

    ## dirscan directory

    ## SABnzbd will consume everything in that dir

    ## while trying to add it to the queue

    dirscan_dir = "/home/arumite/SABnzbd/dirscan"

    

    ## Scheduling options

    ## Syntax: minute hour day action

    ##         1st argument must be 0-59 (minute)

    ##         2nd argument must be 0-24 (hour)

    ##         3rd argument must be 1-7 (day) or *

    ##         4th argument must be resume or pause

    ##

    ## e.g schedlines = 0 7 * pause, 0 21 * resume 

    ##     to pause SABnzbd at 7:00 and resume operation at 21:00

    schedlines = ,

    

    ## default options for dirscan added items

    ## 0 = None

    ## 1 = +Repair

    ## 2 = +Unpack

    ## 3 = +Delete

    dirscan_opts = 1

    

    ## Enable/disable filejoining

    ## 0 = Disabled

    ## 1 = Enabled

    enable_filejoin = 1

    

    ## Enable/disable unraring

    ## 0 = Disabled

    ## 1 = Enabled

    enable_unrar = 1

    

    ## Enable/disable unzipping

    ## 0 = Disabled

    ## 1 = Enabled

    enable_unzip = 1

    

    ## Enable/disable periodic queue saving

    ## 0 = Disabled

    ## 1 = Enabled

    ## Enable this on unstable systems

    enable_save = 0

    

    ## Enable/disable

    ## 0 = Disabled

    ## 1 = Enabled

    ## Enable to cleanup par2 files 

    ## (only if verifiying/repairing succeded)

    enable_par_cleanup = 1

    

    ## should we failover on yenc crc errors

    ## 0 = no

    ## 1 = yes

    fail_on_crc = 0

    

    ## should we download to group folders? 

    ## (i.e /my/download/dir/alt.bin.whatever/somepost/)

    ## 0 = no

    ## 1 = yes

    create_group_folders = 0

    

    ## bandwith limit

    ## 0 == ignore

    ## Slowdown factor, try values between 0.01 and 1.0.

    bandwith_limit = 0

    

    ## Cleanup List

    ## List of file_extensions that should be deleted

    ## Example: ".nfo," or ".nfo, .sfv"

    cleanup_list = ,

    

    ## Only get articles from topmost collection

    ## Enable for less memory usage

    ## Disable for more efficient downloading

    ## 0 = Disabled

    ## 1 = Enabled

    top_only = 1

    

    ## Automatically sort by average age

    ## 0 = No

    ## 1 = Yes

    auto_sort = 0

    

    ## Send group command before requesting articles

    ## 0 = No

    ## 1 = Yes

    send_group = 0

    

    ## Article cache limit

    ## 0 = Disable Cache

    ## -1 = Unlimited cache

    ## >0 = Maximum memory (in bytes) to use for cache

    cache_limit = 0

    

    ## Umask to use for directories/files

    umask = 755

    

[logging]

    ## max size of SABnzbd.log (in bytes)

    max_log_size = 5242880

    

    ## how many backups of SABnzbd.log to keep around

    log_backups = 5

    

    ## enable cherrypy logging

    ## 0 = no

    ## 1 = yes

    enable_cherrypy_logging = 1

    

## Fill in your servers here

## If your server doesn't need password auth set

## username and password to ''

## fillserver field must be 0 for non-fillservers (>0 otherwise)

[servers]

#    [[server 0]]

#       host = *******

#       port = 119

#       username = 
******
#       password = ******

#       connections = 4

#       fillserver = 0

#    [[server 1]]

#  	host = news.myfillserver.com

#  	port = 119

#  	username = ""

#  	password = "" 

#  	connections = 8

#       fillserver = 1



## www.newzbin.com support

[newzbin]

    username = ""

    password = ""

    

    ## Place downloads into newzbin.com category folders

    ## 0 = No

    ## 1 = Root category only

    ## 2 = Root category + subcategory

    create_category_folders = 0


```
you'll notice that it says the bytes.sab and the queue.sab files are missing.  I tried creating dummy documents in the directory, but that didn't fix it either.  All the 5 -6 results I got from google resulted in foreign language posts.

 I am running amd64 btw.  Only change that I noticed was replacing the _i386.deb package with _amd64.deb.  After that everything installed oh so smoothe like.

---

### Post by Arumite on 2007-08-07
^^^^^^^^^^^^^^

YAY! I got it working.  Now however my connection speed remains at 0.  it shows the file queued, but it is not downloading

---

### Post by Arumite on 2007-08-07
^^^^^^^^^^^^^^

Fixed that too.  For some reason even though I pre-entered the news server info directly into the .ini, I still had to manually add it in throught the web-browser.

Thanks for a great guide!!!  and forum!!!

---

### Post by nosscire on 2007-08-28
Hopefully this thread isn't too old to get some help from :)

Followed the guide, but can't get it to work. When i run ./SABnzbd.py -d -f SABnzbd.ini i don't get any errors, accually nothing seam to happen at all.
However, I did try not putting anything into the log directory tag, and then i get an error about that, so i guess something's wrong.

Here's my ini file.

```
__version__ = 016



[misc]

    ## host we should listen on, leave "" for localhost

    host = ""

    

    ## port we should listen on

    port = 8080

    

    ## username for the web-interface

    username = ""

    

    ## password for the web-interface

    password = ""

    

    ## web file dir for (custom) Cheetah templates and the default.css file

    web_dir = "/home/simon/.SABnzbd/sabnzbd/templates"

    

    ## dir to put downloads to, won't be created automatically

    download_dir = "/home/simon/tmp"

    

    ## dir to put completed downloads to, won't be created automatically

    complete_dir = "/home/simon/downloads"

    

    ## If specified, .nzbs fetched by postid (or added by the dirscanner) will 

    ## be backed up to this readable/writeable dir

    nzb_backup_dir = ""

    

    ## dir to store cache and cookie files, windows users should

    ## leave this at .

    cache_dir = ""

    

    ## location of your log directory, "" to disable logging

    log_dir = "/home/simon/log"

    

    ## dirscan directory

    ## SABnzbd will consume everything in that dir

    ## while trying to add it to the queue

    dirscan_dir = "/home/simon/nzb"

    

    ## Scheduling options

    ## Syntax: minute hour day action

    ##         1st argument must be 0-59 (minute)

    ##         2nd argument must be 0-24 (hour)

    ##         3rd argument must be 1-7 (day) or *

    ##         4th argument must be resume or pause

    ##

    ## e.g schedlines = 0 7 * pause, 0 21 * resume 

    ##     to pause SABnzbd at 7:00 and resume operation at 21:00

    schedlines = ,

    

    ## default options for dirscan added items

    ## 0 = None

    ## 1 = +Repair

    ## 2 = +Unpack

    ## 3 = +Delete

    dirscan_opts = 3

    

    ## Enable/disable filejoining

    ## 0 = Disabled

    ## 1 = Enabled

    enable_filejoin = 1

    

    ## Enable/disable unraring

    ## 0 = Disabled

    ## 1 = Enabled

    enable_unrar = 1

    

    ## Enable/disable unzipping

    ## 0 = Disabled

    ## 1 = Enabled

    enable_unzip = 1

    

    ## Enable/disable periodic queue saving

    ## 0 = Disabled

    ## 1 = Enabled

    ## Enable this on unstable systems

    enable_save = 1

    

    ## Enable/disable

    ## 0 = Disabled

    ## 1 = Enabled

    ## Enable to cleanup par2 files 

    ## (only if verifiying/repairing succeded)

    enable_par_cleanup = 1

    

    ## should we failover on yenc crc errors

    ## 0 = no

    ## 1 = yes

    fail_on_crc = 0

    

    ## should we download to group folders? 

    ## (i.e /my/download/dir/alt.bin.whatever/somepost/)

    ## 0 = no

    ## 1 = yes

    create_group_folders = 0

    

    ## bandwith limit

    ## 0 == ignore

    ## Slowdown factor, try values between 0.01 and 1.0.

    bandwith_limit = 0

    

    ## Cleanup List

    ## List of file_extensions that should be deleted

    ## Example: ".nfo," or ".nfo, .sfv"

    cleanup_list = ,

    

    ## Only get articles from topmost collection

    ## Enable for less memory usage

    ## Disable for more efficient downloading

    ## 0 = Disabled

    ## 1 = Enabled

    top_only = 1

    

    ## Automatically sort by average age

    ## 0 = No

    ## 1 = Yes

    auto_sort = 0

    

    ## Send group command before requesting articles

    ## 0 = No

    ## 1 = Yes

    send_group = 0

    

    ## Article cache limit

    ## 0 = Disable Cache

    ## -1 = Unlimited cache

    ## >0 = Maximum memory (in bytes) to use for cache

    cache_limit = 0

    

    ## Umask to use for directories/files

    umask = 755

    

[logging]

    ## max size of SABnzbd.log (in bytes)

    max_log_size = 5242880

    

    ## how many backups of SABnzbd.log to keep around

    log_backups = 5

    

    ## enable cherrypy logging

    ## 0 = no

    ## 1 = yes

    enable_cherrypy_logging = 1

    

## Fill in your servers here

## If your server doesn't need password auth set

## username and password to ''

## fillserver field must be 0 for non-fillservers (>0 otherwise)

[servers]

    [[newshosting]]

       host = *********

       port = 119

       username = ******

       password = ***********

       connections = 8

       fillserver = 0

#    [[server 1]]

#  	host = news.myfillserver.com

#  	port = 119

#  	username = ""

#  	password = "" 

#  	connections = 8

#       fillserver = 1



## www.newzbin.com support

[newzbin]

    username = ""

    password = ""

    

    ## Place downloads into newzbin.com category folders

    ## 0 = No

    ## 1 = Root category only

    ## 2 = Root category + subcategory

    create_category_folders = 0

```

As Far as I can see, there
s no problem in here. All hep appriciated.

---

### Post by shamrock_uk on 2007-09-09
> **baersaerk said:**
> Helpful stuff

Just wanted to say thanks for posting, that fixed it for me! :)

---

### Post by AnalogRetentive on 2007-09-29
> **disturbedite said:**
> i'm trying this app out since i couldn't get hellanzb to do crap.  i'm on kubuntu 7.04 herd 4.  i did everything according to the tutorial (except i installed python 2.5, and i installed the other dependencies from the repos--problem?) and i get this when trying to launch sabnzb with ./SABnzbd.py -d -f SABnzbd.ini:

Traceback (most recent call last):
  File "./SABnzbd.py", line 37, in <module>
    import cherrypy
ImportError: No module named cherrypy

i have the python-cherrypy 2.2.1-3ubuntu1 package installed and it says that this version of cherrypy is backwards compatible with version 2.0

can anyone suggest a solution please?

> **frolle said:**
> I am getting this error. Can anybody tell me how to avoid it?

[email]kristian@kristian-desktop:~/.SABn[/email]zbd/sabnzbd$ ./SABnzbd.py -d -f SABnzbd.ini
Traceback (most recent call last):
  File "./SABnzbd.py", line 44, in ?
    from sabnzbd.interface import *
  File "/home/kristian/.SABnzbd/sabnzbd/sabnzbd/interface.py", line 39, in ?
    from Cheetah.Template import Template
ImportError: No module named Cheetah.Template
[email]kristian@kristian-desktop:~/.SABn[/email]zbd/sabnzbd$

I was getting a very similar error to both of you: that I didn't have zlib stuff. According to this link, it's because you didn't have [package] installed before configuring and compiling python, and re-running that step should fix it.

[http://www.zope.org/Members/beacon/install_instructions](http://www.zope.org/Members/beacon/install_instructions)
(This section: "Other Notes: ImportError: No module named zlib")

This makes perfect sense for me, because I accidentally missed this line from the original post when doing my install:

```
apt-get install libbz2-dev zlib1g-dev
```

So I ran the above code, and then re-ran the ./configure and make lines, and viola! problem solved!

---

### Post by cchester on 2007-10-07
> **jtt1560 said:**
> Here is a script to install SABnzbd from source on Dapper 6.06

**1)** Paste this code into your terminal window: 

```

sudo apt-get install libbz2-dev zlib1g-dev

sudo apt-get install g++
sudo apt-get install make
sudo apt-get install par2

mkdir ~/.SABnzbd
mkdir ~/Desktop/SABInstall_Files
cd ~/Desktop/SABInstall_Files
wget http://www.python.org/ftp/python/2.4.3/Python-2.4.3.tgz
wget http://download.cherrypy.org/cherrypy/2.2.1/CherryPy-2.2.1.tar.gz
wget http://surfnet.dl.sourceforge.net/sourceforge/cheetahtemplate/Cheetah-1.0.tar.gz
wget http://effbot.org/downloads/elementtree-1.2.6-20050316.tar.gz
wget http://sabnzbd.sourceforge.net/yenc-0.3.tar.gz
wget http://kambing.vlsm.org/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.5.4-0.1_i386.deb
wget http://superb-east.dl.sourceforge.net/sourceforge/sabnzbd/SABnzbd-0.2.5.tar.gz

sudo dpkg -i unrar_3.5.4-0.1_i386.deb

tar -xzvf Python-2.4.3.tgz
tar -xzvf CherryPy-2.2.1.tar.gz
tar -xzvf Cheetah-1.0.tar.gz
tar -xzvf elementtree-1.2.6-20050316.tar.gz
tar -xzvf yenc-0.3.tar.gz
tar -xzvf SABnzbd-0.2.5.tar.gz

```

**2) Change in this code <YOURUSERNAME> to your Ubuntu login name**
and then paste it in your terminal window.
```

cd ~/Desktop/SABInstall_Files/Python-2.4.3
./configure --prefix=/home/<YOURUSERNAME>/.SABnzbd
make && make install

```
**3) **Now copy and paste the rest of the code in the terminal window.

```

cd ~/Desktop/SABInstall_Files/CherryPy-2.2.1
~/.SABnzbd/bin/python setup.py install

cd ~/Desktop/SABInstall_Files/Cheetah-1.0
~/.SABnzbd/bin/python setup.py install

cd ~/Desktop/SABInstall_Files/elementtree-1.2.6-20050316
~/.SABnzbd/bin/python setup.py install

cd ~/Desktop/SABInstall_Files/yenc-0.3
~/.SABnzbd/bin/python setup.py install

cd ~/Desktop/SABInstall_Files/SABnzbd-0.2.5
mkdir ~/.SABnzbd/sabnzbd
cp -R SABnzbd.ini.sample SABnzbd.py sabnzbd/ templates/ ~/.SABnzbd/sabnzbd
cd ~/.SABnzbd/sabnzbd
mv SABnzbd.ini.sample SABnzbd.ini

cd ~/.SABnzbd/sabnzbd
chmod +x SABnzbd.py
mkdir ~/.SABnzbd/sabnzbd/nzb
mkdir ~/.SABnzbd/sabnzbd/nzb/backup
chmod -R +x ~/.SABnzbd/sabnzbd/sabnzbd

```

**4) **Finish it up

Edit files located in /home/<YOURUSERNAME>/.SABnzbd/sabnzbd
Now edit your SABnzbd.py

Change the first line in SABnzbd.py
#!/usr/bin/python -OO
to
#!/home/<YOURUSERNAME>/.SABnzbd/bin/python -OO

Now edit your SABnzbd.ini
example:
## location of your log directory, "" to disable logging
    log_dir = "/home/<YOURUSERNAME>/.SABnzbd/sabnzbd/templates"

SABnzbd will not run unless the directories are correctly edited. **DO NOT USE** the same directory for downloaded files and completed files. They must be different. Make sure to set a directory for the log files. If you have a problem look at the log file in the same directory to see what the error is. It will be easily fixed if there is a configuration problem. The log file is great at telling you why the program did not run. 

**RUN IT**
cd ~/.SABnzbd/sabnzbd
./SABnzbd.py -d -f SABnzbd.ini

load your webbrowser and goto the following address:
[http://127.0.0.1:8080/sabnzbd/](http://127.0.0.1:8080/sabnzbd/)

Hi,

I followed everythng you said with no errors along the way but when I run your last line that starts "load your web browser" it just returns to the command line with the directory I am in no error message or anything.

I noticed you said to do this for someone else ps -ef | grep -i sabnzb so I ran it and this was my result  chris    17290  6143  0 01:45 pts/1    00:00:00 grep -i sabnzb hope this helps you in helping me figure this out.

I have hellanzb installed correctly and it works so do I need to have it running to use the SABnzbd GUI?

Thanks for any help on this. Oh I am using fiesty.

---

### Post by rascalli on 2007-10-07
do you have a browser installed than ?

---

### Post by cchester on 2007-10-07
Yes I have firefox installed. Oh and I am doing this in linux just to clarify since I see this is for windows to.

Thanks for any more help.

---

### Post by felker2 on 2007-10-27
Cool: the instruction still works for Ubuntu 7.10 Gutsy Gibbon!

I had requested for introducing a package SABnzbd in Ubuntu 7.10, but after some work was done on that it was bounced because of license issues. :(

BTW: the notation on [http://ubuntuforums.org/archive/index.php/t-320475.html]("http://ubuntuforums.org/archive/index.php/t-320475.html") introduces some strange spaces in the URL/filenames. Avoid that page and use [http://ubuntuforums.org/showthread.php?t=320475]("http://ubuntuforums.org/showthread.php?t=320475")

---

### Post by felker2 on 2007-12-26
With the new SABnzbd+ / SABnzbdplus 3.0 on Ubuntu / Kubuntu 7.10 things have become very easy. The commands below are all that's needed. Make sure "universe" is enabled in package management.

> 
sudo apt-get install python-cherrypy python-cheetah python-elementtree python-yenc python-celementtree python-feedparser unrar unzip par2

wget [http://surfnet.dl.sourceforge.net/sourceforge/sabnzbdplus/sabnzbd-0.3.0rc4.zip](http://surfnet.dl.sourceforge.net/sourceforge/sabnzbdplus/sabnzbd-0.3.0rc4.zip)
unzip sabnzbd-0.3.0rc4.zip
cd sabnzbd-0.3.0rc4/
python SABnzbd.py


Just configure the newsserver in the SABnzbd webGUI and everything is OK.

HTH

---

### Post by Distortedgamer on 2008-06-20
There is a way to start it from the command line. I found it once, but can't find it now. Can anyone help me and let me know how to START the program???

*EDIT* 

Nevermind I figured it out. I was in  the ~/.sabnzbd folder and not the folder with all of the actual .py files in it. I feel embarrassed :(

---

