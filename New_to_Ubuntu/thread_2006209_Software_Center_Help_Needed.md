---
title: "Software Center Help Needed"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by Balmung4500 on 2012-06-18
Ok when I try to load the software center it freezes at this point

[IMG]http://i97.photobucket.com/albums/l203/evermore666/Screenshotfrom2012-06-18194516.png[/IMG]

When I try the same thing from the terminal I get this.

```
2012-06-18 19:29:52,468 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-06-18 19:29:53,194 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-06-18 19:29:53,541 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 146, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:The package skype needs to be reinstalled, but I can't find an archive for it.
2012-06-18 19:29:56,933 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1343, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1273, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 149, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 168, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 240, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 491, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 266, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 430, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 419, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 124, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 317, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 212, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 263, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'

```
Is there any one who can help me out.

---

### Post by afixane on 2012-06-18
```
sudo apt-get purge software-center
sudo apt-get install software-center
```

---

### Post by Balmung4500 on 2012-06-18
i tried that again and it still did not work

---

### Post by Immolatus on 2012-06-19
It might be possible to reinstall the software center using synaptic. I prefer to just use synaptic or just apt-get in terminal anyhow.

to install synaptic package manager in a terminal....open one....then do:

sudo apt-get install synaptic


also, when a software is removed it's config files are not alway removed as well so if you remove the software center to reinstall it you'll want to remove it's config files as well or you're stuck with the same problem again. I say this because that last error in your list looks like it came from a config file.

hope this helps.

---

### Post by Balmung4500 on 2012-06-19
```
balmung@Evermore-PC:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package skype needs to be reinstalled, but I can't find an archive for it.
balmung@Evermore-PC:~$ synaptic
The program 'synaptic' is currently not installed.  You can install it by typing:
sudo apt-get install synaptic
```

---

### Post by Immolatus on 2012-06-19
try:

sudo dpkg install -f

to clear the broken package
then

sudo apt-get update

then

sudo apt-get upgrade

then 

sudo apt-get install synaptic

P.S. The "apt" part is for Aptitude, the program that actually does the installations wich works with dpkg wich builds the packages.

---

### Post by Balmung4500 on 2012-06-19
```
balmung@Evermore-PC:~$ sudo dpkg install -f
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
```

---

### Post by NikTh on 2012-06-19
The correct command is 
```
sudo apt-get install -f 
```

If nothing happen , try to reinstall skype.. download it from here --> [http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/) [COLOR=Red]be careful[/COLOR] to download the correct arch 32bit(i386) or 64bit(amd64) and install it. 

Also you can try these commands 
```
sudo dpkg --configure -a 
sudo update-software-center
```

---

### Post by Balmung4500 on 2012-06-19
still nothing

```
balmung@Evermore-PC:~$ sudo dpkg --configure -a
[sudo] password for balmung: 
balmung@Evermore-PC:~$ sudo update-software-center
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 169, in <module>
    result = rebuild_database(pathname)
  File "/usr/share/software-center/softwarecenter/db/update.py", line 1043, in rebuild_database
    cache.open()
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 243, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 146, in open
    self._depcache = apt_pkg.DepCache(self._cache)
SystemError: E:The package skype needs to be reinstalled, but I can't find an archive for it.

```
I can't reinstall skype-ubuntu_4.0.0.7-1_i386.deb with out software center

But I DLed the skype static dl and it runs fine

---

### Post by NikTh on 2012-06-19
> **Balmung4500 said:**
> 
I can't reinstall skype-ubuntu_4.0.0.7-1_i386.deb with out software center


Yes you can. 
```
sudo dpkg -i skype-ubuntu_4.0.0.7-1_i386.deb
```;)

---

### Post by HiImTye on 2012-06-19
```
sudo apt-get purge skype; sudo apt-get update; sudo apt-get install skype
```
skype is in the repos so try this

---

### Post by Balmung4500 on 2012-06-20
as you can see i have the file.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219967&stc=1&d=1340165571[/IMG]

when i tried sudo dpkg -i skype-ubuntu_4.0.0.7-1_i386.deb
i got this

```
balmung@Evermore-PC:~$ sudo dpkg -i skype-ubuntu_4.0.0.7-1_i386.deb
dpkg: error processing skype-ubuntu_4.0.0.7-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 skype-ubuntu_4.0.0.7-1_i386.deb

```Update:


I tried this 
sudo apt-get purge skype; sudo apt-get update; sudo apt-get install skype <--- This Worked
sudo apt-get purge software-center; sudo apt-get update; sudo apt-get install software-cente[FONT=Ubuntu]r <---This did not[/FONT] ```
balmung@Evermore-PC:~$ sudo apt-get purge software-center; sudo apt-get update; sudo apt-get install software-center
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.umd.edu_ubuntu_dists_precise_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
Ign http://mirror.umd.edu precise InRelease
Ign http://mirror.umd.edu precise-updates InRelease                            
Ign http://mirror.umd.edu precise-backports InRelease                          
Ign http://mirror.umd.edu precise-security InRelease                           
Hit http://mirror.umd.edu precise Release.gpg                                  
Hit http://mirror.umd.edu precise-updates Release.gpg                          
Hit http://mirror.umd.edu precise-backports Release.gpg                        
Hit http://mirror.umd.edu precise-security Release.gpg                         
Hit http://mirror.umd.edu precise Release                                      
Hit http://mirror.umd.edu precise-updates Release                              
Get:1 http://packages.medibuntu.org precise InRelease [7,096 B]                
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://archive.canonical.com precise InRelease                             
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://archive.ubuntu.com precise InRelease                                
Hit http://mirror.umd.edu precise-backports Release                            
Hit http://mirror.umd.edu precise-security Release                             
Hit http://mirror.umd.edu precise/restricted Sources                           
Hit http://mirror.umd.edu precise/main Sources                                 
Hit http://mirror.umd.edu precise/multiverse Sources                           
Hit http://mirror.umd.edu precise/universe Sources                             
Hit http://mirror.umd.edu precise/main i386 Packages                           
Ign http://archive.getdeb.net oneiric-getdeb InRelease                         
Hit http://mirror.umd.edu precise/restricted i386 Packages                     
Hit http://mirror.umd.edu precise/universe i386 Packages                       
Hit http://mirror.umd.edu precise/multiverse i386 Packages                     
Hit http://mirror.umd.edu precise/main TranslationIndex                        
Ign http://packages.medibuntu.org precise InRelease                            
Hit http://mirror.umd.edu precise/multiverse TranslationIndex                  
Hit http://mirror.umd.edu precise/restricted TranslationIndex                  
Hit http://mirror.umd.edu precise/universe TranslationIndex                    
Hit http://mirror.umd.edu precise-updates/restricted Sources                   
Hit http://mirror.umd.edu precise-updates/main Sources                         
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.ubuntu.com precise Release.gpg                              
Hit http://mirror.umd.edu precise-updates/multiverse Sources                   
Hit http://mirror.umd.edu precise-updates/universe Sources                     
Hit http://mirror.umd.edu precise-updates/main i386 Packages                   
Hit http://mirror.umd.edu precise-updates/restricted i386 Packages             
Hit http://mirror.umd.edu precise-updates/universe i386 Packages               
Hit http://mirror.umd.edu precise-updates/multiverse i386 Packages             
Hit http://mirror.umd.edu precise-updates/main TranslationIndex                
Hit http://mirror.umd.edu precise-updates/multiverse TranslationIndex          
Hit http://mirror.umd.edu precise-updates/restricted TranslationIndex          
Hit http://mirror.umd.edu precise-updates/universe TranslationIndex            
Hit http://mirror.umd.edu precise-backports/main Sources                       
Hit http://mirror.umd.edu precise-backports/restricted Sources                 
Hit http://mirror.umd.edu precise-backports/universe Sources                   
Hit http://mirror.umd.edu precise-backports/multiverse Sources                 
Hit http://mirror.umd.edu precise-backports/main i386 Packages                 
Hit http://mirror.umd.edu precise-backports/restricted i386 Packages           
Hit http://mirror.umd.edu precise-backports/universe i386 Packages             
Hit http://mirror.umd.edu precise-backports/multiverse i386 Packages           
Hit http://mirror.umd.edu precise-backports/main TranslationIndex              
Hit http://mirror.umd.edu precise-backports/multiverse TranslationIndex        
Hit http://mirror.umd.edu precise-backports/restricted TranslationIndex        
Hit http://archive.canonical.com precise Release                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://mirror.umd.edu precise-backports/universe TranslationIndex          
Hit http://mirror.umd.edu precise-security/restricted Sources                  
Hit http://mirror.umd.edu precise-security/main Sources                        
Hit http://mirror.umd.edu precise-security/multiverse Sources                  
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.ubuntu.com precise Release                                  
Hit http://mirror.umd.edu precise-security/universe Sources                    
Hit http://mirror.umd.edu precise-security/main i386 Packages                  
Hit http://mirror.umd.edu precise-security/restricted i386 Packages            
Hit http://mirror.umd.edu precise-security/universe i386 Packages              
Hit http://mirror.umd.edu precise-security/multiverse i386 Packages            
Hit http://mirror.umd.edu precise-security/main TranslationIndex               
Hit http://mirror.umd.edu precise-security/multiverse TranslationIndex         
Hit http://mirror.umd.edu precise-security/restricted TranslationIndex         
Hit http://mirror.umd.edu precise-security/universe TranslationIndex           
Hit http://mirror.umd.edu precise/main Translation-en                          
Hit http://mirror.umd.edu precise/multiverse Translation-en                    
Hit http://mirror.umd.edu precise/restricted Translation-en                    
Hit http://mirror.umd.edu precise/universe Translation-en                      
Hit http://mirror.umd.edu precise-updates/main Translation-en                  
Hit http://mirror.umd.edu precise-updates/multiverse Translation-en            
Ign http://packages.medibuntu.org precise/free Sources/DiffIndex               
Hit http://mirror.umd.edu precise-updates/restricted Translation-en            
Hit http://mirror.umd.edu precise-updates/universe Translation-en              
Hit http://mirror.umd.edu precise-backports/main Translation-en                
Hit http://mirror.umd.edu precise-backports/multiverse Translation-en          
Hit http://mirror.umd.edu precise-backports/restricted Translation-en          
Hit http://mirror.umd.edu precise-backports/universe Translation-en            
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://mirror.umd.edu precise-security/main Translation-en                 
Hit http://mirror.umd.edu precise-security/multiverse Translation-en           
Hit http://mirror.umd.edu precise-security/restricted Translation-en           
Hit http://mirror.umd.edu precise-security/universe Translation-en             
Hit http://archive.getdeb.net oneiric-getdeb Release.gpg                       
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://archive.ubuntu.com precise/restricted Sources                       
Ign http://packages.medibuntu.org precise/non-free Sources/DiffIndex           
Hit http://archive.getdeb.net oneiric-getdeb Release                           
Ign http://packages.medibuntu.org precise/free i386 Packages/DiffIndex         
Ign http://packages.medibuntu.org precise/non-free i386 Packages/DiffIndex     
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Hit http://archive.getdeb.net oneiric-getdeb/games Sources                     
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en_US           
Ign http://archive.canonical.com precise/partner Translation-en       
Hit http://packages.medibuntu.org precise/free Sources                
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://packages.medibuntu.org precise/non-free Sources                     
Hit http://packages.medibuntu.org precise/free i386 Packages
Hit http://packages.medibuntu.org precise/non-free i386 Packages
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-en_US           
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Fetched 7,096 B in 8s (843 B/s)                                                
W: GPG error: http://packages.medibuntu.org precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/Release  Unable to find expected entry 'game/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/mirror.umd.edu_ubuntu_dists_precise_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
```The skype thing is gone but no change in the Software Center

---

### Post by NikTh on 2012-06-20
> **Balmung4500 said:**
> The skype thing is gone but no change in the Software Center

Ok , then do 2 things . 

First , go to update manager > settings > other software and disable medibuntu repositories . 

Second go again to update manager > ubuntu software and change "Download from" , change the mirror to **main**. 

Run these commands in terminal and post here out put of the last  
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by Balmung4500 on 2012-06-20
```
W: GPG error: http://packages.medibuntu.org precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783 W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/oneiric-getdeb/Release  Unable to find expected entry 'game/source/Sources' in Release file (Wrong sources.list entry or malformed file)  E: Some index files failed to download. They have been ignored, or old ones used instead. Reading package lists... Error! E: Encountered a section with no Package: header E: Problem with MergeList /var/lib/apt/lists/mirror.umd.edu_ubuntu_dists_precise_main_i18n_Translation-en E: The package lists or status file could not be parsed or opened.
```Ok fixed this ^

still no software center


Hmm the skype think is back

```
balmung@Evermore-PC:~$ sudo apt-get install synaptic
[sudo] password for balmung: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package skype needs to be reinstalled, but I can't find an archive for it.
balmung@Evermore-PC:~$ sudo apt-get purge skype; sudo apt-get update; sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package skype needs to be reinstalled, but I can't find an archive for it.
Ign http://extras.ubuntu.com precise InRelease
Ign http://archive.ubuntu.com precise InRelease
Ign http://archive.ubuntu.com precise-updates InRelease
Ign http://archive.ubuntu.com precise-backports InRelease
Ign http://archive.ubuntu.com precise-security InRelease
Hit http://archive.ubuntu.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://archive.ubuntu.com precise-updates Release.gpg
Hit http://archive.ubuntu.com precise-backports Release.gpg
Hit http://extras.ubuntu.com precise Release
Hit http://archive.ubuntu.com precise-security Release.gpg
Hit http://extras.ubuntu.com precise/main Sources
Hit http://archive.ubuntu.com precise Release  
Hit http://archive.ubuntu.com precise-updates Release                 
Hit http://extras.ubuntu.com precise/main i386 Packages               
Ign http://extras.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise-backports Release
Hit http://archive.ubuntu.com precise-security Release                
Hit http://archive.ubuntu.com precise/main Sources                    
Hit http://archive.ubuntu.com precise/restricted Sources              
Hit http://archive.ubuntu.com precise/multiverse Sources              
Hit http://archive.ubuntu.com precise/universe Sources                
Hit http://archive.ubuntu.com precise/main i386 Packages              
Hit http://archive.ubuntu.com precise/restricted i386 Packages        
Hit http://archive.ubuntu.com precise/universe i386 Packages
Hit http://archive.ubuntu.com precise/multiverse i386 Packages
Hit http://archive.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Hit http://archive.ubuntu.com precise/universe TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted Sources
Hit http://archive.ubuntu.com precise-updates/main Sources
Hit http://archive.ubuntu.com precise-updates/multiverse Sources
Hit http://archive.ubuntu.com precise-updates/universe Sources
Hit http://archive.ubuntu.com precise-updates/main i386 Packages
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://archive.ubuntu.com precise-backports/main Sources
Hit http://archive.ubuntu.com precise-backports/restricted Sources
Hit http://archive.ubuntu.com precise-backports/universe Sources
Hit http://archive.ubuntu.com precise-backports/multiverse Sources
Hit http://archive.ubuntu.com precise-backports/main i386 Packages
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://archive.ubuntu.com precise-security/restricted Sources
Hit http://archive.ubuntu.com precise-security/main Sources
Hit http://archive.ubuntu.com precise-security/multiverse Sources
Hit http://archive.ubuntu.com precise-security/universe Sources
Hit http://archive.ubuntu.com precise-security/main i386 Packages
Hit http://archive.ubuntu.com precise-security/restricted i386 Packages
Hit http://archive.ubuntu.com precise-security/universe i386 Packages
Hit http://archive.ubuntu.com precise-security/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-security/main TranslationIndex
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex
Hit http://archive.ubuntu.com precise/main Translation-en
Hit http://archive.ubuntu.com precise/multiverse Translation-en
Hit http://archive.ubuntu.com precise/restricted Translation-en
Hit http://archive.ubuntu.com precise/universe Translation-en
Hit http://archive.ubuntu.com precise-updates/main Translation-en
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en
Hit http://archive.ubuntu.com precise-backports/main Translation-en
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_US
Hit http://archive.ubuntu.com precise-security/main Translation-en
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise-security/restricted Translation-en
Hit http://archive.ubuntu.com precise-security/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package skype needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by NikTh on 2012-06-20
Did you or did not download the skype .deb package from site ? 

Skype is also in Ubuntu repo's but you must activate  **Canonical Partners** . 
Go to Update manager > settings > other software and tick (activate) Canonical Partners. 
Then do again 
```
sudo apt-get update
sudo apt-get install --reinstall skype
```

---

### Post by Balmung4500 on 2012-06-20
```
sudo apt-get install --reinstall skype
```

did not work

---

### Post by NikTh on 2012-06-21
Then go to the place that you downloaded the .deb . If you downloaded to Downloads , open a terminal , connect (with cd command) and run dpkg -i. 
```
cd Downloads/
sudo dpkg -i skype-ubuntu_4.0.0.7-1_i386.deb
```after the installation complete try again 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update 
sudo apt-get install -f 
```

---

### Post by fantab on 2012-06-21
First of all purge skype again. Then

sudo nautilus

Select file system and search for Skype... all the Skype folders will be listed... DELETE all of them. Close Nautilus. Open Home and Ctrl+H this reveals dot .files... DELETE .skype (notice the dot).

Now... follow what **NikTh** says in second code box. Except before you run update do : sudo apt-get clean

If you still get errors try change the server to MAIN (or any other) from Update Manager and repeat the above.

---

### Post by Balmung4500 on 2012-06-21
It worked Now i just need to make my computer to play dvd now that i have vlc

---

### Post by fantab on 2012-06-21
Do tell us how you got things working? List what steps helped you. Your solution may help someone with same issues. And also mark the thread as SOLVED.

---

### Post by mahajan on 2012-06-22
> **Immolatus said:**
> try:

sudo dpkg install -f

to clear the broken package
then

sudo apt-get update

then

sudo apt-get upgrade

then 

sudo apt-get install synaptic

P.S. The "apt" part is for Aptitude, the program that actually does the installations wich works with dpkg wich builds the packages.

dm@ubuntu:~$ apt-get purge software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic icedtea-netx-common
  icedtea-netx linux-headers-3.2.0-24-generic-pae
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  software-center*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4,346 kB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
dpkg: error: requested operation requires superuser privilege
W: Could not open file '/var/log/apt/term.log' - OpenLog (13: Permission denied)
E: Sub-process /usr/bin/dpkg returned an error code (2)



error is coming

---

### Post by Balmung4500 on 2012-06-22
This is what worked for me

> **fantab said:**
> First of all purge skype again. Then

sudo nautilus

Select file system and search for Skype... all the Skype folders will be  listed... DELETE all of them. Close Nautilus. Open Home and Ctrl+H this  reveals dot .files... DELETE .skype (notice the dot).

Now... follow what **NikTh** says in second code box. Except before you run update do : sudo apt-get clean

If you still get errors try change the server to MAIN (or any other) from Update Manager and repeat the above.


> **NikTh said:**
> Then go to the place that you downloaded the .deb . If you downloaded to Downloads , open a terminal , connect (with cd command) and run dpkg -i. 
```
cd Downloads/
sudo dpkg -i skype-ubuntu_4.0.0.7-1_i386.deb
```after the installation complete try again 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update 
sudo apt-get install -f 
```

---

