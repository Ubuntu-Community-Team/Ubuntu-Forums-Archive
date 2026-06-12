---
title: "Is eclipse CDT to slow or my computer can handle it?? or what?"
date: 2007-06-18
forum: Programming Talk
---

### Post by hecato on 2007-06-18
I have spected to work with eclipse in my new comuter, but like the anterior one it take to much time to display the window when you do -> after a member or a not member (hand error), it only take to much time, even beryl show in grey the Eclipse Window!!!!!

Im doing some work trought the tutorials of ogre... dont know if it is becaus it is a large project.... but in afct now Im wanting to trash eclipse and return back to codeblocks :S... I really have wanted to use Eclipse for first time (Eclipse always look like a step far than my specs... lol)... but is it like a NO NO!!!!!

> tyoc@pcbase:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping        : 2
cpu MHz         : 1809.054
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3620.95
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping        : 2
cpu MHz         : 1809.054
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 3618.25
clflush size    : 64
> 
tyoc@pcbase:~$ cat /proc/loadavg 
0.29 0.16 0.10 1/136 6296> tyoc@pcbase:~$ cat /proc/meminfo 
MemTotal:      2075004 kB
MemFree:       1525768 kB
Buffers:         30192 kB
Cached:         243960 kB
SwapCached:          0 kB
Active:         351104 kB
Inactive:       155672 kB
HighTotal:     1178496 kB
HighFree:       685992 kB
LowTotal:       896508 kB
LowFree:        839776 kB
SwapTotal:     1534168 kB
SwapFree:      1534168 kB
Dirty:              44 kB
Writeback:           0 kB
AnonPages:      232704 kB
Mapped:          79072 kB
Slab:            20224 kB
SReclaimable:     9024 kB
SUnreclaim:      11200 kB
PageTables:       2140 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   2571668 kB
Committed_AS:   587784 kB
VmallocTotal:   114680 kB
VmallocUsed:     62532 kB
VmallocChunk:    46580 kB
> 
tyoc@pcbase:~$ cat /proc/version
Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 >  OpenGL vendor string: NVIDIA Corporation
  OpenGL renderer string: GeForce 8800 GTS/PCI/SSE2
  OpenGL version string: 2.1.1 NVIDIA 100.14.09
 Using 100.14.09 drivers....

---

### Post by omschaub on 2007-06-18
Not entirely following your posts, but let me give you my experience with Eclipse (Since I use it daily in Ubuntu).

-  Beryl is great eye candy, but I find it gets in the way of programs that use a lot of popups (like Eclipse's auto help).  Not saying they are not compatible, but in my experience, it gets in the way -- that is, it slows things down.  Now I do not have an 8800, but a measly 7600.. so YMMV

-  Edit eclipse.ini and give eclipse a little more starting and max ram.

-  Probably the worst thing that can happen to Eclipse (again, this is just my experience) is that it goes into the pagefile.  The swapping there with this program is HORRID.  I find Eclipse almost unusable once it has been swapped in.  If you see your swapfile being used, do a quick sudo swapoff -a, sudo swapon -a to get Eclipse out of there.

-  I use Java 6.  This will probably get me trolled/flamed here, but I do and it works and it works fast for me -- faster than 5 or 1.4.

In the best case scenario, with everything working at FULL speed on my comp, which is very similar to yours, I find Eclipse in Linux to be about half as fast as in Windows.  Just the nature of the beast :(  I use Ubuntu at home and Windows version at work.  I have tried some of the new version releases and they seem to be getting better, but it will take a while for it to become a final release and even longer to make in into the repository.

I know this is not entirely what you wanted, but it is at least some info.  
-Cheers-

---

### Post by gvoima on 2007-06-18
I hope you did some forum searching, but try [_this_]("http://ubuntuforums.org/showthread.php?t=201378&highlight=eclipse+java") if it works.

Helped for me.

---

### Post by hecato on 2007-06-18
In fact it is not that it opens slow, I also have done the update alternatives before, becasue I know tht you need to do it before hand with sudo update-alternatives --config java, also if before return you hit 2 times TAB it will show what things starting with the actual prefix are for change the alternatives... javah, javap, ...

What Im talking about is about CDT plugin, it apear that for a large project like ogre it get terribly slow!!! being uneditable, even put a 0.3 will stop the answer from the IDE like about 10 sec or more!!!!!!


I know that codeblocks can do the work (or aparently do the work of autocomplete very fast, tought dont know if it cover all the functions taht CDT can provide...) I also will give it a shoot to netbeans... I spect that it will not be worse than eclipse for C/C++. In fact I remember that codeblocks worked just fine, only that I wanted to go with eclipse CDT.


In any case, with the extra manual modifications (the gedit ones) it open somewhat a little more fast, but the problem about autocompletion and write 0.3 still there...


Also I will put a video, you will say me if it is the normal time for answer of the editor???

[http://video.tleyotlocelocoatl.googlepages.com/CDT_1.avi](http://video.tleyotlocelocoatl.googlepages.com/CDT_1.avi) you see it is the same behaviour with or without beryl!!!!


Paste is very fine, the anterior code above what Im editing is from the tut...

the configuration of the project is:[LIST=1]
[*]  that **ogrejune2007** is ogre by itself ./bootstrap, ./configure (enabling GLX) the make I do it inside eclipse (is the same than from command line)
[*]**ogretut0** and **ogretut1** is a copy paste of the tutorial 0.. and it worked, in the include dirs, are added paths to **/usr/local/OGRE**, **/usr/local/CEGUI** and **/usr/local/OIS**, also there is a reference to the workspace "**${workspace_loc:/ogrejune2007/Samples/Common/include}**" where there is some clases in .h files for help setup the example and tutorials applications.[/LIST]Dont know if is because the size of the ogre project that it gets to slow...

this is ogrejune2007
> 
The selected PDOM contain 1278 files, 14061 macros, 31452 symbols
57563 references, 14919 declarations, 23277 definitions.this is ogretut0
> 
The selected PDOM contain 368 files, 2020 macros, 6645 symbols
21149 references, 3886 declarations, 4690 definitions.this is ogretut1
> 
The selected PDOM contain 368 files, 2020 macros, 12538 symbols
30531 references, 7206 declarations, 7897 definitions.

---

