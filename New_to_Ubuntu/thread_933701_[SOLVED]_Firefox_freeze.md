---
title: "[SOLVED] Firefox freeze"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Georgia boy on 2008-09-29
Hi. I noticed that I had to force Firefox to quit a few times  while at the music.download.com. 
After listening to a song then try to go back to the other sections it would freeze and I would have to force quit and then go back again. This would happen if I had downloaded a song or just checking out some of the others. 

Any ideas? I noticed it Sunday night and this morning. I mean this site has some great Independant music all free and leagal. Also some of the known artist will throw a freebe for the taking once in a while. 

Jusw was wondering if anyone else has noticed this. 

Thanks

Tom

---

### Post by baruch60610 on 2008-09-29
I've had Firefox freeze on me quite often.  You might want to take a look at whatever add-ons you've got going.  Often the problem isn't with Firefox itself, but with some add-on that goes berserk.  You can try to disable them all, then enable them one by one, to see which one(s) cause problems.  Then you could either get rid of the offending add-on, or just disable it before going to the download site that causes the problems.

Otherwise, you might look at how much memory Firefox is using.  There are ways to reduce this, which you can Google (firefox memory management, for example).  Often if the memory use is high, Firefox gets extremely sluggish and seems to have stopped.

---

### Post by Crafty Kisses on 2008-09-29
It could be a resource issue, while Firefox is open go into Terminal and type the following:
```
top
```
Post the results here.

---

### Post by Georgia boy on 2008-09-30
Here is what I got when I went to the Terminal. Maybe I did it wrong. First time I've been to the Terminal. 

thomas@Thriller:~$  code:top
bash: code:top: command not found
thomas@Thriller:~$

I had the Noscript and ADP. Got rid of the Noscript. Still using the ADP.

Thanks
Tom

---

### Post by rybaxs on 2008-09-30
just "top"

   top

user@user-desktop:/$top

---

### Post by rybaxs on 2008-09-30
i've encountered that problem before.. try to reinstall your Firefox. Thats my remedy when my firefox got crazy.. hope it works..

---

### Post by Georgia boy on 2008-09-30
5377 root      20   0  103m  17m 7004 S    1  0.8   1:36.13 Xorg               
 5746 thomas    20   0 28472 5888 3380 S    0  0.3   0:15.58 pulseaudio         
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.30 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.28 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.06 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.06 kblockd/1          
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       


Here' what I could copy. Hope I got it all. Nothing else would copy. 

Could the music.download.com site also be a factor in this? It happened a couple of times this morning also. Just wondering. Downloaded some more free MP3's this morning. Got that one from Theory of a Deadman about "Just say Goodby". Real good song and group, plus about 6 more songs.  Like that site, free and legal downloads. 

I don't seem to recall problems with any other site. I could try in the morning when I get back on again at some other sites, but so far I have only seen that happening on the music.download.com site. That's why I was also throwing the question about maybe the site itself might be causing a freeze.

Any ideas on that also?

Thanks for the great help and suggestions!!!
Tom

---

### Post by rybaxs on 2008-10-02
you need to kill them by typing the PID

did u see the blinking cursor? 

press K
then type the PID number then enter

to exit.. press Ctrl+Z

---

### Post by Georgia boy on 2008-10-02
Please explain what you mean by kill them by typing the PID. I'm new at this. 
Are you talking about the terminal?

Thanks
Tom

---

### Post by Ryadt on 2008-10-02
Installing flashblock will block all unnecessary flash. This might help decrease the cpu usage of firefox.

---

### Post by kansasnoob on 2008-10-02
Look at my post #7 here:

[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)

---

