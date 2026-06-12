---
title: "Why Ubuntu use swap memory instead of physical memory?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by sharks on 2008-05-20
I have 1.25 gb of ram. It uses only 32% ram and uses 78% of swap memory.Why Ubuntu use swap memory instead of physical memory? I have allocated 256mb for swap.

---

### Post by tamoneya on 2008-05-20
can you post the result of ```
free -m
```This will give us a better sense of what is going on as well as being very accurate.

---

### Post by diaa on 2008-05-20
May be you can [reduce swappiness]("http://lifehacker.com/software/feature/slim-down-and-speed-up-linux-333798.php")

---

### Post by iaculallad on 2008-05-20
> **sharks said:**
> I have 1.25 gb of ram. It uses only 32% ram and uses 78% of swap memory.Why Ubuntu use swap memory instead of physical memory? I have allocated 256mb for swap.

Here's an article to let you better understand [Linux Swap]("http://www.linux.com/feature/121916") space.

---

### Post by sdennie on 2008-05-20
78% of 256M of swap isn't very much memory.  Unless you are frequently seeing applications cause lots of disk activity for seemingly benign operations (indicating that it's swapping stuff back into RAM), I'd say that what you described is fairly normal.

---

### Post by c-shadow on 2008-05-25
I'm noticing the same problem for some time now...
3 GB RAM, running gutsy. Two users always logged in (wife and me), with standard apps like firefox, thunderbird, azureus,... After a couple of days ubuntu starts swapping, i guess it moves inactive pages out of RAM and the preformance suffers, especially if I don't switch users for a while. After searching through the forums tried setting the swappiness to 0 and later even installed preload. 
Today started Virtualbox - still need windows for some things (512 MB allowed in Vbox) and this is the result of free -m:
```

 uptime
 19:59:55 up 22 days, 21:17,  3 users,  load average: 1.03, 1.09, 1.22

 free -m
             total       used       free     shared    buffers     cached
Mem:          3043       2952         90          0          7       1188
-/+ buffers/cache:       1756       1286
Swap:         2047       1999         48

```
1.2 GB free and almost 2 in swap!?
Tried to switch users...hard drive goes crazy :) Only to find that almost every program of second user is swapped out...
Switched users, closed some of the programs (including azureus and virtualbox), gone through all of the programs so they could be loaded back from the swap and this is the result, still 1.6 GB in swap:
```

free -m
             total       used       free     shared    buffers     cached
Mem:          3043       2674        368          0         19       1454
-/+ buffers/cache:       1200       1842
Swap:         2047       1635        411

```
Closed some more programs and got the swap usage to 1 GB.
Is there any way to make the sistem use all available RAM before swapping?
By first reducing the cache and buffers?

---

### Post by sdennie on 2008-05-25
c-shadow: Those symptoms sounds like some app you are running has a bad memory leak.  I would see if anything on the system is using huge amounts of RAM.

---

### Post by skymera on 2008-05-25
htop shows it better

```
 sudo apt-get install htop 
``` It's worth it.

Open terminal and type htop.

That will show what apps are using what memory in %

---

### Post by markbuntu on 2008-05-25
I have 3g of ram and never see swap being used, never. In fact, ram use never gets past about 1.1g. Even while watching video in youtube or dvd player and streaming in rythmbox at the same time with compiz running on a big desktop.

I an using hardy 8.04 386i and amd64 alternately
AMD athlon64 3800+ 3g ram ATI 3650 1g ram

For sure something c=shadow is running has a memory leak or he is running something in debug mode. Some stack is just growing and growing and growing... I am surprised it has not leaked into the system area are and crashed the whole shootin match. But this just shows how good the ram allocation and protection scheme has gotten. It used to happen all the time in the early linux versions and every version of windows...

---

### Post by sdennie on 2008-05-25
c-shadow: The other possibility is that you are using something that really does need a huge amount of memory and so it starts swapping out the other users memory.  That would explain why even with swappingness=0, you are showing lots of swap but also lots of cache.  One place where I've seen this happen is when compiling really gigantic C++ files.

---

### Post by c-shadow on 2008-05-26
Yesterday (I'm GMT+1 so it's 6:30am here) I ran swapoff/swapon, it took the sistem a minute or two to clear the swap and the sistem was quite responsive then.
```

 free -m
             total       used       free     shared    buffers     cached
Mem:          3043       2930        112          0         29        972
-/+ buffers/cache:       1928       1114
Swap:         2047          0       2047

```
Then after running virtualbox (winxp) first time:
```

 free -m
             total       used       free     shared    buffers     cached
Mem:          3043       2954         88          0          4        463
-/+ buffers/cache:       2487        556
Swap:         2047          5       2042

```

And second time (hardy):
```

 free -m
             total       used       free     shared    buffers     cached
Mem:          3043       2954         88          0          2        412
-/+ buffers/cache:       2539        503
Swap:         2047         52       1994

```
immediately 52 megs of swap usage...hm...plenty of cache...could preload have something to do with that?

Here is the current partial output of top, sorted by VIRT column:
```

top - 06:31:12 up 23 days,  7:49,  4 users,  load average: 0.49, 0.70, 0.69
Tasks: 200 total,   3 running, 197 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.6%us,  3.7%sy,  0.0%ni, 78.2%id,  0.0%wa,  0.2%hi,  0.3%si,  0.0%st
Mem:   3116304k total,  3002876k used,   113428k free,    11360k buffers
Swap:  2096472k total,    53708k used,  2042764k free,   735800k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                        
14151 alen      15   0 1286m 116m  16m S    1  3.8   1:03.45 java                                                                           
 3833 alen      15   0  437m 209m  22m S   26  6.9 331:27.85 firefox-bin                                                                    
18819 root      15   0  407m 396m 9252 S    0 13.0 577:59.51 Xorg                                                                           
 2931 elly      15   0  389m 318m 7068 S    0 10.5   3:59.41 evince                                                                         
14186 alen      15   0  321m  45m  10m S    0  1.5  21:56.02 gnome-panel                                                                    
11303 root      15   0  315m 284m  12m S   10  9.3   1118:06 Xorg                                                                           
18621 elly      15   0  299m 162m  14m S    1  5.3  48:06.24 firefox-bin                                                                    
11627 elly      15   0  285m 215m  19m S    0  7.1   0:08.32 nautilus                                                                       
31862 elly      18   0  201m  88m  12m S    0  2.9  14:05.77 thunderbird-bin                                                                
13362 alen      15   0  182m  82m  21m S    0  2.7   2:08.58 thunderbird-bin                                                                
18917 elly      15   0  167m  27m 9356 S    0  0.9   5:49.67 gnome-panel                                                                    
13468 alen      15   0  159m  81m  18m R    1  2.7   7:51.72 amule                                                                          
11633 alen      15   0  101m  33m  21m S    0  1.1   0:08.82 nautilus                                                                       
20609 alen      15   0 99404  36m 7660 S    0  1.2  37:25.86 skype                                                                          
21519 alen      15   0 87236  16m 6544 R    2  0.5   8:07.60 gnome-terminal                                                                 
14274 alen      25   0 84400 9.8m 6408 S    0  0.3   0:05.44 trashapplet                                                                    
13486 alen      15   0 82928  27m  10m S    0  0.9   0:06.69 pan                                                                            
18994 elly      15   0 79236 8660 5368 S    0  0.3   0:01.84 trashapplet                                                                    
14327 alen      18   0 73788 9564 5332 S    0  0.3   0:08.33 mixer_applet2                                                                  
19012 elly      15   0 70096 9536 5552 S    0  0.3   0:01.75 mixer_applet2                                                                  
14277 alen      20   0 60744 5960 4276 S    0  0.2   0:00.27 evolution-alarm                                                                
 1416 alen      15   0 60616 4948 2248 S    0  0.2   0:00.57 evolution-data-                                                                
18849 elly      16   0 58920 9592 6388 S    0  0.3   1:07.48 x-session-manag                                                                
14375 alen      15   0 51376  17m  12m S    0  0.6   0:00.73 gedit 

```

@vor:
I'm also suspecting some memory leaks, azureus (java) gives some strange readings here. Firefox also uses huge amounts of RAM but it's normal since we both have many tabs opened and some extensions installed. Is it normal for xorg to use this much memory? I use dual screen setup with nvidia, LCD TV as a secondary screen, no compiz or anything similar running.
Also had some problems with gutsy in the beginning with nautilus crashing on secondary screen or hogging the CPU when users logged off- confirmed bugs on launchpad...eventually the updates took care of those. 
Will see in a while now how it goes, any advice in tracing the problem?

@skymera: htop is nice, but a little confusing - multiple entries for a single process, threads i guess?

@markbuntu:
Not running anything in debug mode...how do you do that anyway?

---

### Post by sdennie on 2008-05-27
c-shadow: My guess is the primary problem is azureus (java).  I'm not an expert on these matters but, if it's causing java to mmap a ton of stuff (which it appears to be doing), the kernel may not be pleased and swap useful stuff do disk when azureus (java) claims too many pages of memory.  Anyone more knowledgeable is welcome to tell me I have no idea what I'm talking about but, my advice would be: Don't use azureus.  Transmission works quite well but, if you want a hardcore torrent client, check out rtorrent.

---

### Post by Arthur Archnix on 2008-05-27
Isn't preload more of a dapper feisty kind of app? I think using preload with these newer versions might be causing some problems. Swappiness=0 means its off, right? It shouldn't use any swap. It should just get rid of the oldest stuff in ram to make room for newer requests. Just some random thoughts.

---

### Post by sdennie on 2008-05-27
Preload could be the problem too.  I've never used it but, if it's forcing stuff into the cache, it's possible that it's doing so at the expensive of user memory.

---

### Post by hyper_ch on 2008-05-27
rtorrent isn't only for hardcore people... rtorrent is for all that need good torrent capabilities and don't want to hog the system ;)

But I agree, azureus is a bitch with regard to system hogging. kTorrent is probably closes to azureus, transmission should be lighter and rTorrent is command line based... it's nice that you can control rtorrent from everywhere through a ssh connection.

---

### Post by sdennie on 2008-05-27
screen + rtorrent + fileserver == The finest torrent client available to humanity.  ;)

---

### Post by Arthur Archnix on 2008-05-27
Deluge.. always the last girl at the torrent party asked to dance. But take her home and I guarantee she won't disappoint you. The version in Hardy is fine, but if you're on Gutsy just use the version on their website, not in the repos.

---

### Post by c-shadow on 2008-05-28
> **Arthur Archnix said:**
> Deluge.. always the last girl at the torrent party asked to dance. But take her home and I guarantee she won't disappoint you. The version in Hardy is fine, but if you're on Gutsy just use the version on their website, not in the repos.


tried deluge...it's very buggy, some private trackers even banned deluge because of bugs related with ratio reporting. Also azureus is the only client I found that doesn't fragment downloaded files on my ext3 partition. I even posted some results regarding that problem on deluge forum.

[http://forum.deluge-torrent.org/viewtopic.php?f=7&t=2825&st=0&sk=t&sd=a&hilit=compact+allocation](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=2825&st=0&sk=t&sd=a&hilit=compact+allocation)

---

### Post by Arthur Archnix on 2008-05-28
Wow.. thanks for the link. Time to learn r-torrent.

---

### Post by hyper_ch on 2008-05-28
use rtorrent in conjucntion with screen. here's a screen howto:  [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

Here's the guide that made me start using rtorrent:  [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

Here's my howto for installing rtorrent from SVN:  [http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron](http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron)
(I recommend using svn because the new version has quite a few things more that the current version in the repos doesn't have. Additionally you can easily patch rtorrent to be able to throttle individual torrents when using the svn version)

---

### Post by divyad on 2011-10-13
i am aslo facing same problrm, having 4 GB RAM ,bcoz of that problrm system goes hangon and i am not able to access my applicatin
 
free -m
 
total used free shared buffers cached
Mem: 4056 3926 130 0 2 13
-/+ buffers/cache: 3910 146
Swap: 1482 1482 0

---

### Post by oldos2er on 2011-10-13
Closed. Please start a new thread for your question.

---

