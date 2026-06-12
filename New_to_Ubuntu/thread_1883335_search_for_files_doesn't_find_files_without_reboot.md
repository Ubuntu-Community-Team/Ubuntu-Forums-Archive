---
title: "search for files doesn't find files without reboot."
date: 2011-11-18
forum: New to Ubuntu
---

### Post by beew on 2011-11-18
I have done an experiment on Ubuntu 11.10, I installed a program with synaptic and downloaded a file with firefox and then use "search for file" to look for them immediately after the installation and the download, nothing turned up . The installed program should have a lot of files with the name in different directories, whereas the downloaded one is sitting right there in my Downloads folder staring at me. Waited a bit and tried a few more times still nothing. But after rebooting and searched again and they all turned up.

I repeated the experiment with Natty and search for files located all the pieces without rebooting.

Is there a way to fix this annoying behaviour? It seems that it is impossible to try anything simple in OO without stumbling on some bugs. :(

---

### Post by Diametric on 2011-11-19
I'm a bit confused - I thought synaptic was removed in 11.10.  Also, could you clarify "I installed a program with synaptic and downloaded a file with firefox"

The same file, different files? Sorry if I'm missing what you're saying...just trying to understand what happened.

---

### Post by beew on 2011-11-19
> **Diametric said:**
> I'm a bit confused - I thought synaptic was removed in 11.10.  Also, could you clarify "I installed a program with synaptic and downloaded a file with firefox"

The same file, different files? Sorry if I'm missing what you're saying...just trying to understand what happened.

Hi,

Synaptic is indeed removed but it is just one "sudo apt-get install synaptic" away, it is the first thing I installed when I set up my system, it is a much better package management tool than the Software Center.

There are many files, one set of files come from installing a program from synaptic, so there are many files scattered in different directories like /usr/bin/, /usr/share/applications etc, all sharing the same key word (name of program). Then there is a separate file I downloaded with Firefox and placed it in ~/Downloads.

I tried two separate searches, one for the files associated with the program, using the name of the program as the key word and searched in File systems, a second one uses the name of the downloaded file as the key to search in /home/username  and both failed without reboot.

Now there is a second thing that I discovered, which I haven't mentioned in OP , that is, even after reboot, if I search in File Systems the files in my home directory wouldn't turn up. This is not the case in Natty.

---

### Post by beew on 2011-11-20
Bump!

---

### Post by beew on 2011-11-21
So no one experiences this problem??

Ok, try another thing. Put any file in a sub-directory of home (say Downloads, or even Desktop, right in front of your eyes)  and try to search for it by searching  in "File systems". In all previous Ubuntus the file will turn up  since "File Systems" is supposed to include everything. But in 11.10 apparently it wouldn't find the file. The file will only turn up if you search in home. Is this a bug or do I need to set some options?

---

### Post by beew on 2011-11-22
Does this again after the updates, still the same.

I dumped a file in my desktop, searched for it in File Systems, couldn't find it. Reboot, search again then it found it.

---

### Post by d2btoo on 2011-11-22
> **beew said:**
> So no one experiences this problem??

Ok, try another thing. Put any file in a sub-directory of home (say Downloads, or even Desktop, right in front of your eyes)  and try to search for it by searching  in "File systems". In all previous Ubuntus the file will turn up  since "File Systems" is supposed to include everything. But in 11.10 apparently it wouldn't find the file. The file will only turn up if you search in home. Is this a bug or do I need to set some options?

Unable to confirm **"... In all previous Ubuntus the file will turn up  since "File Systems" is supposed to include everything. But in 11.10..."**

I'm presently using lucid, and these happens in here too.

Also I don't get your point !!?? gnome-search uses both [COLOR="red"]locate[/COLOR] and [COLOR="Red"]find[/COLOR] tool to perform it's action, I'm sure you know the difference.

In case of doubt do **man locate** and you can always update the index-database manually without waiting for it to happen on next reboot.

HTH
d2b

---

### Post by beew on 2011-11-22
> **d2btoo said:**
> Unable to confirm **"... In all previous Ubuntus the file will turn up  since "File Systems" is supposed to include everything. But in 11.10..."**

I'm presently using lucid, and these happens in here too.

Also I don't get your point !!?? gnome-search uses both [COLOR=red]locate[/COLOR] and [COLOR=Red]find[/COLOR] tool to perform it's action, I'm sure you know the difference.

In case of doubt do **man locate** and you can always update the index-database manually without waiting for it to happen on next reboot.

HTH
d2b

In Lucid and Maverick you need to open the gconf-editor  (go to applications > gnome-search tool, though I can't remember exactly)  and uncheck the box "quick search". Once you do that it works as expected. In Natty it just works. 

My point is that something that is supposed to work doesn't I can of course locate things from the terminal, but the genome-search tool should work.

If something that is supposed to work in  Lucid and it doesn't work for you you should post a thread here (in case you need to set some options, as is the case here) or file a bug report, rather than asking me what the point is.

---

### Post by d2btoo on 2011-11-22
Oh! are you actually saying that in prev. ubuntus we can disable "quick search", if we wish, but can't do it any more in 11.10 ..... is that it?

If so I misunderstood , sorry!

soooo much things changed in 11.10, as it seems, good luck!
d2b

---

### Post by beew on 2011-11-22
> **d2btoo said:**
> Oh! are you actually saying that in prev. ubuntus we can disable "quick search", if we wish, but can't do it any more in 11.10 ..... is that it?

If so I misunderstood , sorry!

soooo much things changed in 11.10, as it seems, good luck!
d2bBut in 11.04 you don't need to disable anything. I thought they finally fixed it! :( 

In 11.10 the problem is not exactly like in Lucid and Maverick. In Lucid and Maverick if you don't disable "quick search" then search doesn't work AT ALL, period. But once you do, it works as good as it can be. In 11.10 it seems to work partially without having to disable things but 1) you have to narrow down the search to some subdirectories and  2) reboot after you modify the contents of the directories in question.

---

### Post by beew on 2011-11-23
Bump!

---

### Post by beew on 2011-11-26
Still doesn't work. Does anybody actually use the gnome-search-tool?

---

### Post by The Cog on 2011-11-26
I gave up on that search tool several years ago. I got as far as posting a screenshot of two nautilus windows, one showing the file in my home folder and one showing a search failing to find it. Nobody had a solution. 

I did wonder if the problem was that if you had a separate home partition and specified to search the entire filesystem, it only searched the / partition, skipping other mounted partitions like /home. But I never bothered to test this idea.

You can use **locate** filename, but this uses a database that is only updated daily (or after a reboot). The command "sudo updatedb" tells it to do a disk scan and update the database immediately. Hmm, as a thought, if your search uses that database, sudo updatedb might be what you're looking for.

---

### Post by beew on 2011-11-26
Ok. Problem solved!!!

 Install gconf-editor, then go to apps > gnome-search-tool and check "disable quick search" so it is the same solution that worked for 10.10 and 10.04. But what got me so frustrated is that 1) I don't remember having to do this in 11.04 and 2) gconf-editor is not even installed in 11.10 and I didn't know that it still works.,--isn't it replaced by the dconf-editor??

Hi, the cog,

Thanks for the suggestions and the reply, --it is frustrating to ask a seemingly simple question and keep bumping the thread while no one even come by to say a "me too!", so thank you and I mean it!

I knew those things already, what really bothers me is that Ubuntu is supposed to be user friendly and when a new user sees "search for files" he/she would expect it to work just as in Windows, it is a very basic function after all, so what is in the minds of the packagers to include this tool, but screw up the setting so that it doesn't work even though it should, and moreover the tool to adjust the setting to make it work is not even installed??

---

### Post by AeroMac on 2011-12-23
Your solution worked for me too!

Thanks for this discussion. This has been bothering me for a while.

---

### Post by ppeterb on 2011-12-28
Search for Files should find all target files. Period! Anything less is simply a bad system. Narrowing the search should can (and should) be easy to do but not the default. This topic is not solved!

---

