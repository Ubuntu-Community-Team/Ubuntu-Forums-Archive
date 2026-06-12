---
title: "Final Question From Old-Newbie:  Bloated home/.../cache files (U18)"
date: 2020-11-19
forum: New to Ubuntu
---

### Post by kagesan on 2020-11-19
My HD capacity is 1 TB. There are two maverick files hogging 2/3 of my HD memory capacity in the home/.../cache folder:  One hog-file @ 14 GB; the other @ 598 GB or 642 GB* (see note below).  Anything blindly hogging 70-ish % of memory is a critical issue, so any effective steerage on the subject is appreciated.

A few informational items follow in the event that any of them help with offering guidance:

ITEM 1
*Note on differing memory size file listings:  
Right click on file name / Properties shows the largest hog-file as 642 GB.  But the size of that same file in the terminal mode list shows it as 598 GB (go figure - I have no idea why).

ITEM 2
Beyond those two large maverick files, the next largest file / folder in the cache folder is the mozilla folder with 24 MB.  All others occupy only nominal memory. In other words, I run a minimalist system, use minimal apps / packages, and use it for only a handful of common, barebones activities. 

ITEM 3
I *once* ran the system backup (BackUp) app-package but have since deleted the backup folder that it created.  I don't think that would create this kind of separate, "maverick" file-hog issue, but I'm not certain about that.

ITEM 4
My home folder is encrypted... although I'm not well-enough informed to know if that could affect / create hog files.

ITEM 5
The only other potentially related info / issue I can think of is that I do NOT have synaptic package manager (SPM) loaded on my system.  I mention this because SPM would allow me to elect some mem-space saving options, like "Delete downloaded packages after installation".  But I run clean / update / upgrade in terminal mode DAILY, and I check for updates / upgrades via the Update package 3 x WEEKLY to make sure I haven't missed one.  And I use BleachBit in minimalist "sissy-mode" daily as well.  Finally, I have already run:
```

sudo apt-get autoremove && sudo apt-get autoclean

``` 
in terminal as a self-check - with no effect on the hog files.

ITEM 6
Terminal command line file size listing is dumped below (both hog files in bold text).


/


```

du -hs /home/zz/.cache/*

8.0K    /home/zz/.cache/babl
16K     /home/zz/.cache/calibre
4.0K    /home/zz/.cache/deja-dup
12K     /home/zz/.cache/event-sound-cache.tdb.7eb01efc1029485ca95efaf7a9ca5abf.x86_64-pc-linux-gnu
52K     /home/zz/.cache/evolution
48K     /home/zz/.cache/fontconfig
8.0K    /home/zz/.cache/gegl-0.3
4.0K    /home/zz/.cache/gnome-screenshot
5.9M    /home/zz/.cache/gnome-software
752K    /home/zz/.cache/gstreamer-1.0
24K     /home/zz/.cache/ibus
4.0K    /home/zz/.cache/ibus-table
4.0K    /home/zz/.cache/libgweather
896K    /home/zz/.cache/mesa_shader_cache
26M     /home/zz/.cache/mozilla
4.0K    /home/zz/.cache/rhythmbox
4.0K    /home/zz/.cache/shotwell
1.3M    /home/zz/.cache/thumbnails

[B]14G     /home/zz/.cache/tmp5p8EdOqsXYu2QIGM0icS3bPOXCVepFds0w01gu04kwxMttz7.YhzgPoK3t8VipyyHa2Bxnsdk1lIcRMmDJFs6BAHIpxX1zKi_7dfLO83dfIO1fedjxJCClxJEWBc8w5b9zRNKhf8uSsFuA_MLEXzc3FtLRPUEkAIhv_UGhAX8QjSQLsyYLYisOQmINpfKNAFxrpFkED7ZP1oAU-0Rk2YLNzSyKVwzA9-VnXA4ydp.5g8RXloVIW1iSzvM2s
[/B]
**598G    /home/zz/.cache/tmpGleIFfx6vED5dEFb90Vv-WyUvYImLuA7EM1zy61VVSLA4fFfh0u7SldkmQDj3Zzgn42gE.4GPfGfxgn9lfKJ-s1B2eJC4xcJgViMFzKu5QvvbUjX.yABcZKQs1FL6sZkMHbdv3Sm9X4Ac2pCwIl6bK2nYq3Q0-1jJpDDCryy_2_nH5Wg_zk7uVk17AVHgKkOuddtE-Zg4BlUvHLy.NsC4lR-dkZdjt_srJYmP2nvegnkJVh1inDXUHCD6-y**

8.0K    /home/zz/.cache/totem
4.0K    /home/zz/.cache/ubuntu-report
12K     /home/zz/.cache/update-manager-core
352K    /home/zz/.cache/wallpaper
20K     /home/zz/.cache/yelp
4.0K    /home/zz/.cache/zeitgeist-vacuum.stamp

```

KageSan

- Message Ends -

---

### Post by deadflowr on 2020-11-19
You can delete those cache files without causing any irreversible harm to the system.
Worst that can happen is programs that cached data will be slower to load various aspects.

I would delete the two wild files you see and then watch to see if anything new appears.
I would also watch my activities to see if anything I do causes or creates these files.

Also,
Apt and synaptic and any other package management utility have no bearing on anything in the home directory.
So that's not a problem or related to this issue you have.

---

### Post by kagesan on 2020-11-19
Wow... fast *and* concise.  And your steerage on apt/synaptic is something I'll burn in memory.

I'll only follow-up in this thread if something goes *boom* when I delete those two hog files.  That aside...

Humble thanks - bowing at the waist, knees and ankles (which really hurts).

KageSan

- Message Ends -

---

### Post by poorguy on 2020-11-19
I have a question.

What does this terminal command do.

```

du -hs /home/zz/.cache/*


```


Thanks

---

### Post by DuckHook on 2020-11-19
> **poorguy said:**
> What does this terminal command do.

```

du -hs /home/zz/.cache/*


```
```
duckhook@Zeus:~$  man du
```
```
DU(1)                                            User Commands                                            DU(1)

NAME
       du - estimate file space usage

SYNOPSIS
       du [OPTION]... [FILE]...
       du [OPTION]... --files0-from=F

DESCRIPTION
       Summarize disk usage of the set of FILEs, recursively for directories.

       Mandatory arguments to long options are mandatory for short options too.

       -0, --null
              end each output line with NUL, not newline

       -a, --all
              write counts for all files, not just directories

       --apparent-size
              print  apparent  sizes, rather than disk usage; although the apparent size is usually smaller, it
              may be larger due to holes in ('sparse') files, internal fragmentation, indirect blocks, and  the
              like

       -B, --block-size=SIZE
              scale  sizes  by SIZE before printing them; e.g., '-BM' prints sizes in units of 1,048,576 bytes;
              see SIZE format below

       -b, --bytes
              equivalent to '--apparent-size --block-size=1'

       -c, --total
              produce a grand total

       -D, --dereference-args
              dereference only symlinks that are listed on the command line

       -d, --max-depth=N
              print the total for a directory (or file, with --all) only if it is N or fewer levels  below  the
              command line argument;  --max-depth=0 is the same as --summarize

       --files0-from=F
              summarize  disk  usage of the NUL-terminated file names specified in file F; if F is -, then read
              names from standard input

       -H     equivalent to --dereference-args (-D)

       -h, --human-readable
              print sizes in human readable format (e.g., 1K 234M 2G)

       --inodes
              list inode usage information instead of block usage

       -k     like --block-size=1K

       -L, --dereference
              dereference all symbolic links

       -l, --count-links
              count sizes many times if hard linked

       -m     like --block-size=1M

       -P, --no-dereference
              don't follow any symbolic links (this is the default)

       -S, --separate-dirs
              for directories do not include size of subdirectories

       --si   like -h, but use powers of 1000 not 1024

       -s, --summarize
              display only a total for each argument

       -t, --threshold=SIZE
              exclude entries smaller than SIZE if positive, or entries greater than SIZE if negative

       --time show time of the last modification of any file in the directory, or any of its subdirectories

       --time=WORD
              show time as WORD instead of modification time: atime, access, use, ctime or status

       --time-style=STYLE
              show times using STYLE, which can be: full-iso, long-iso, iso, or +FORMAT; FORMAT is  interpreted
              like in 'date'

       -X, --exclude-from=FILE
              exclude files that match any pattern in FILE

       --exclude=PATTERN
              exclude files that match PATTERN

       -x, --one-file-system
              skip directories on different file systems

       --help display this help and exit

       --version
              output version information and exit

       Display  values  are  in  units  of  the  first available SIZE from --block-size, and the DU_BLOCK_SIZE,
       BLOCK_SIZE and BLOCKSIZE environment variables.  Otherwise, units default  to  1024  bytes  (or  512  if
       POSIXLY_CORRECT is set).

       The  SIZE argument is an integer and optional unit (example: 10K is 10*1024).  Units are K,M,G,T,P,E,Z,Y
       (powers of 1024) or KB,MB,... (powers of 1000).

PATTERNS
       PATTERN is a shell pattern (not a regular expression).  The pattern ? matches any one character, whereas
       *  matches  any  string (composed of zero, one or multiple characters).  For example, *.o will match any
       files whose names end in .o.  Therefore, the command

              du --exclude='*.o'

       will skip all files and subdirectories ending in .o (including the file .o itself).

AUTHOR
       Written by Torbjorn Granlund, David MacKenzie, Paul Eggert, and Jim Meyering.

REPORTING BUGS
       GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
       Report du translation bugs to <https://translationproject.org/team/>

COPYRIGHT
       Copyright ©  2018  Free  Software  Foundation,  Inc.   License  GPLv3+:  GNU  GPL  version  3  or  later
       <https://gnu.org/licenses/gpl.html>.
       This  is free software: you are free to change and redistribute it.  There is NO WARRANTY, to the extent
       permitted by law.

SEE ALSO
       Full documentation at: <https://www.gnu.org/software/coreutils/du>
       or available locally via: info '(coreutils) du invocation'

GNU coreutils 8.30                               September 2019                                           DU(1)

```
It's very useful for determining which files are hogging your HDD/SSD.

---

### Post by poorguy on 2020-11-19
Hello DuckHook,


Interesting explanation of each character and what it does.
I'm going to have to study on this a little.

I've used this command to check left over cache.


[SIZE=1]```


du -ah /var/cache/apt/archives


```[/SIZE]


Thanks

---

### Post by kagesan on 2020-11-20
> **deadflowr said:**
> You can delete those cache files without causing any irreversible harm to the system. (snip) 

I did run into a small issue, _*but not because I followed your advice*_.  Thought I'd describe what happened in case it helps others.

I _wiped_ (bleachbit-wipe + overwrite) rather than _deleted_ (Ubuntu native) the two large files.

I know... that was NOT your instruction:  you said delete, not wipe.  But leaving two huge maverick files on disk in unused mem (the effect of a delete) and hoping for a _possible_ overwrite someday just didn't sit well with me, since I don't know what was in those files. And deleting the files then wiping free mem takes literally hours on my system (maybe an insufficient RAM issue - see below).

In any case, I bleachbit-wiped + overwrote the smaller file (14 GB) successfully / without incident.  But wiping the larger file (642 GB) permanently stalled the bleachbit app after wiping about 90% of it (I checked the residual file size afterward).  So I used variants of the **ps** and **kill** terminal commands to list and kill the bleachbit app's running processes, then restarted bleachbit and wiped the remaining (10%) file fragment - which was successful. No issues since then, and no similar maverick files have re-appeared in the home/cache folder.

(I could have just re-booted the system as a "panic work-around" for the stalled bleachbit app, but I figured that might be asking for trouble - today's OS and hardware combos sometimes respond very badly to that.)

I have fairly high-end RAM, but only 16 GB of it.  So unless otherwise informed, I will (arbitrarily) assume that wiping a file occupying 70-ish % of my 1 TB hard disk probably puts more demands on 16 GB of RAM than it can handle - maybe 32 or 64 GB would do the job, but that's just a SWAGuess.

Finally, I suspect there exists some techno-math-based method to estimate how much RAM you need in order to _avoid_ this kind of scenario, but if that's true, I don't currently know where to find it - something I'll add to my Techno-Things To Do List.

Thanks again for such a fast and concise comeback.

KageSan

- Message Ends -

---

### Post by GhX6GZMB on 2020-11-20
I suspect your web browser. If you inadvertently changed the maximum cache size there, it will bloat to infinity. Check your browser settings.

---

### Post by kagesan on 2020-11-20
> **ml9104 said:**
> I suspect your web browser. If you inadvertently changed the maximum cache size there, it will bloat to infinity. Check your browser settings.

Thanks very much, but I'm a complete putz on this subject.  So this isn't much of a response, but here it is:

- I just checked my browser cache settings for the first time - I've never even looked them before now, and I've never changed them.  
- I've had my present system for two months, and have yet to even open about:config until just now (for this post)
- My browser wasn't even open when I ran the wipe (if that's even pertinent to the point you're making).
- I *manually* clear *all* recent browser history before shutting it down 
- In addition to the item above, I have my browser set to clear ALL cache on closing it.
- I run bleachbit to clear cache (in the browser and just about everywhere else) several times daily.
- I don't have the foggiest idea of how to assess any of the 25 listed browser cache settings or how to decide which of them need to be changed, if any.

I could post all 25 browser.cache.* settings / line items in a code block if you're willing to look at it.  If not - no harm, no foul.  But absent that, I wouldn't touch this brand of maniacal code bloat (in the firefox browser) on my own with a ten foot pole until I took a vacation for 3 days to study the subject.

Back to you.

KageSan

- Message Ends -

---

### Post by kagesan on 2020-11-22
... and judging by the deafening silence, I'm apparently not alone in that sentiment.  :)

---

