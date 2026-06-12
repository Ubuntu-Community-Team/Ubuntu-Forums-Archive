---
title: "problem merging repositories list"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by AlexenderReez on 2008-10-13
the last update give me this-->
```
[ reez @ alexendeRReez : /home/reez/Desktop ] sudo apt-get update   [ 07:13:44 ]
[sudo] password for reez: 
Hit http://archive.ubuntu.com hardy-backports/restricted Packages              
Hit http://archive.ubuntu.com hardy-backports/main Packages                    
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages              
Hit http://archive.ubuntu.com hardy-backports/universe Packages                
Fetched 800kB in 1min49s (7307B/s)                                             
[B][COLOR="Red"]Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.[/COLOR][/B]

how can i correct this error?


```

---

### Post by fooman on 2008-10-13
tried to post this earlier,  but the forums were down for awhile...

been seeing this quite a bit lately.  you will need to edit your /etc/apt/sources.list file and find any references to "harty" and change them to "hardy".  ...seems to be misspelled there somehow.

open the file for editing as root:

```
gksudo gedit /etc/apt/sources.list
```

when it opens,  click on "find" in the toolbar.  in the "search for" box that pops up, type: harty

click find.

wherever it finds a harty in the file...change it to hardy.

you should be set after that.

---

