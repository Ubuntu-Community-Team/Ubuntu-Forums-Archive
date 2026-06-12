---
title: "Advanced File Search"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by andrewk8 on 2008-07-01
Linux newbie using Nautilus (Ubuntu 8.04) for file searches.

How can I perform advanced searches.  Examples include:
[LIST]
[*]limit search results to file names only
[*]limit search results to folder names only
[*]limit search results to files with the user execute bit enabled
[*]limit search results to files modified within a specific date range
[/LIST]
I know that you can sort search results, but I have a big disk and it can take quite a while to search.

---

### Post by llama320 on 2008-07-01
you can use tracker (Apps > Accessories > Tracker search tool) for this. But first you need to go to System > Preferences > Search & Indexing..

Under the General tab, check "Enable indexing," and you can also set the "index delay" time to something a little smaller than 45 secs. Then all you should have to do is restart X (though you may have to reboot..i'm not sure which)

Wait however long you set the index delay to, and then search for your favorite file and along the left side of tracker, you can specify how you want to sift through the info

Good Luck

EDIT: I was just rereading the last two bullets..and my solution doesn't really help for those, but it still applies to the first two at least :)

---

### Post by andrewk8 on 2008-07-01
I've never liked background indexing tools.  They slow down the system and can create some very large index databases.  In Windows XP, for example, I've set the "Indexing" service to a disabled state so that it never runs.

Windows Explorer actually has some very useful search filters (attached) and I was looking for a Linux equivalent.

---

### Post by Claus7 on 2008-07-01
Hello,

type ```
man find
``` and you will see even more choices than the ones you have written.
The combination of find with -exec option is very helpful. For example you can conbine it with the grep command and see on your screen the files which have a certain string in their name or search inside files for a certain string. Of course you can specify whether you are searching for a file or folder with the f and d options respectively. 

Regards!

---

### Post by ghostdog74 on 2008-07-01
use the command line find tool to search
> **andrewk8 said:**
> 
[LIST]
[*]limit search results to file names only

```

find /path -type f ......

```
> 
[*]limit search results to folder names only

```

find /path -type d ......

```
> 
[*]limit search results to files with the user execute bit enabled

```

find /path -type f -perm /u+x -ls ...

```
> 
[*]limit search results to files modified within a specific date range
[/LIST]
```

find /path -type f -mtime +90 ..... #more than 90 days

```

see the man page for details and examples.

---

### Post by sayakb on 2008-07-01
Catfish has a good GUI for find and locate:
```
sudo apt-get install catfish
```

---

### Post by DJ_Peng on 2008-07-02
Thanks for the Catfish recommendation. I'll have to check that out myself.

---

### Post by andrewk8 on 2008-07-02
'find' is powerful, but I was looking for a GUI tool.  I like the way Nautilus presents results, but I was looking for a way to filter the results on more than just the file name.

It looks like Catfish also depends on a separate database, just like Tracker.

Followup #1:  Are there any GUI tools that don't depend upon an external database (i.e. results directly from the filesystem)?

Followup #2:  What kind of performance hit can be expected from enabling indexing tools (e.g. Tracker)?

At work, I run a lot of finite element simulations which use a lot of memory, frequent disk updates with very large files.  At home I don't have a very fast machine or a lot of memory.  In both cases I've disabled the Windows Indexing Service because I've noticed a performance hit (e.g. increased memory usage leading to increased VM swapping and / or increased disk usage at inconvenient times).

---

### Post by llama320 on 2008-07-02
> **andrewk8 said:**
> Followup #2:  What kind of performance hit can be expected from enabling indexing tools (e.g. Tracker)?

I haven't really looked at the memory hit the Tracker takes from the system, but I know that Tracker has some preferences under "smart pausing" that allows you to (default>>) "automatically pause if indexing may degrade performance of other applications in active use" or "automatically pause all indexing when computer is in active use"

So (assuming it works correctly,) you can set tracker to only index while you're not actually doing anything

---

### Post by eapache on 2008-07-02
Tracker is pretty light on system resources. Even with all the options set to maximize performance it only takes up about 9 MB ram, which is less than most antivirus programs on Windows.

To make it more efficient, you can go under System->Preferences->Sessions and disable the tracker applet (don't disable tracker itself). The applet just provides access to pause functions etc. but if you have your options set up properly you shouldn't need it.

It may take slightly more than normal resources while building the initial index, but it shouldn't take much to keep it up-to-date. If you have a ton of files, I suggest running the initial index overnight.

Your mileage may vary.

---

### Post by carusoswi on 2008-07-13
> **LinuxIsInnovation said:**
> Catfish has a good GUI for find and locate:
```
sudo apt-get install catfish
```

Ok, I downloaded/installed Catfish.  Where do I find it in order to run it?  Checked my applications menu but did not find it.

Thanks.

I am looking to scan my system in search of a specific file for which I am looking.


Caruso

---

### Post by ghostdog74 on 2008-07-13
> **carusoswi said:**
> 
I am looking to scan my system in search of a specific file for which I am looking.


Caruso
if you are just going to do that, then just use find, what's wrong with it?
```

find /path -type f -name "myfile_to_search"

```

---

### Post by carusoswi on 2008-07-13
> **ghostdog74 said:**
> if you are just going to do that, then just use find, what's wrong with it?
```

find /path -type f -name "myfile_to_search"

```

What's wrong with it is that my searches do not return any results.
I downloaded a file this morning, and I know where it is and its name, but all my search attempts (I did find and try Catfish) come up emptry.

In the syntax that you gave, I assume I could use /media as the path, what goes in as the -type ??  or do I actually type in '-type f and -name' ??

Thanks for your help.  Sorry if I'm a bit dense.

I have an NTFS internal drive and a couple of external USB drives and would like to be able to search all of them.

Caruso

---

### Post by unutbu on 2008-07-13
Type 

```
man find
```

to read the manual on the find command. It will tell you what -type and -name flags do, and a lot more.

-type f means search only for files (rather than directories)
-name "my file" searches for files whose filename (without the path) is "my file". Note you need to enclose the name with quotes if the filename contains spaces. You can also use *: "*.txt" searches for filenames that end with .txt, for example.

If you have no clue what the name of the file is, but you know that you've downloaded the file within the last 10 minutes, you can also run
```

sudo find /  -mmin -10 | grep -v '^/sys' | grep -v '^/dev' | grep -v '^/proc' 
```

This will find all files on your system that has been modified in the last 10 minutes.


All these file searching tools are useful, but perhaps it would also be useful to have firmer control over where files end up when you download. If you use Firefox, you can go to Edit>Preferences, click on the Main tab and click the radio button "Always ask me where to save files". Then you will always be explicitly notified where downloaded files are being saved.

---

### Post by ghostdog74 on 2008-07-13
> **unutbu said:**
> Type 

If you have no clue what the name of the file is, but you know that you've downloaded the file within the last 10 minutes, you can also run
```

sudo find /  -mmin -10 | grep -v '^/sys' | grep -v '^/dev' | grep -v '^/proc' 
```


no need that much greps. 
```

find / \( -path /sys -o -path /dev -o -path /proc\) -prune -o -print

```

---

### Post by unutbu on 2008-07-13
> **ghostdog74 said:**
> no need that much greps. 
```

find / \( -path /sys -o -path /dev -o -path /proc\) -prune -o -print

```

There needs to be a space after /proc.
```
sudo find / \( -path /sys -o -path /dev -o -path /proc \) -prune -o -mmin 10 -print
```

---

### Post by carusoswi on 2008-07-14
> **unutbu said:**
> Type 

```
man find
```

to read the manual on the find command. It will tell you what -type and -name flags do, and a lot more.

-type f means search only for files (rather than directories)
-name "my file" searches for files whose filename (without the path) is "my file". Note you need to enclose the name with quotes if the filename contains spaces. You can also use *: "*.txt" searches for filenames that end with .txt, for example.

If you have no clue what the name of the file is, but you know that you've downloaded the file within the last 10 minutes, you can also run
```

sudo find /  -mmin -10 | grep -v '^/sys' | grep -v '^/dev' | grep -v '^/proc' 
```

This will find all files on your system that has been modified in the last 10 minutes.


All these file searching tools are useful, but perhaps it would also be useful to have firmer control over where files end up when you download. If you use Firefox, you can go to Edit>Preferences, click on the Main tab and click the radio button "Always ask me where to save files". Then you will always be explicitly notified where downloaded files are being saved.

Thanks for the additional info.  I will read up on the commands.
As for control over where file end up, I download everything to a dated directory on my second internal drive, and I know you can right click on the file in the Firefox download menu to open the 'containing folder'.  The file I'm looking for is a photo that my son sent me several months ago.  I've worked on it, printed it out, and now, he want's an enlargement.  I didn't rename it at the time (as I usually do) and, while I can access the original from his original email, I would like not to have to redo the work.

While I'm not that familiar with these terminal commands, I'm not afraid of the command line.  I'm still confused as to how the graphical setup works, however.  What good is the little hourglass if I can't find a file with it?  I purposely downloaded a file and now exactly where it is, but I still cannot use that graphical setup to locate the file.  That's why I wondered about how it is supposed to work.

Again, thank you for your most informative post.

Caruso

---

