---
title: "Messed up my memory using bleachbit"
date: 2014-06-11
forum: New to Ubuntu
---

### Post by frogwarrior on 2014-06-11
I used bleachbit (a program for wiping out useless cached files, histories and other wastes of space) to clean up my system, but I accidentally ticked the experimental memory section this time. It crashed midway, now I can't get back into Ubuntu, I'm on a Windows 7 partition now. In the GRUB menu, theres a "memory test" option, I ran that and got a lot of error messages but it was taking hours so I didn't let it go to completion.   What happens is the Ubuntu login screen will come up normally, but when I log in I get a black screen. So I hit CTRL + ALT + F1 to get into the command line, and everything seems to work fine in there, until I start to load unity. If I type startx, I get a bunch of error messages taking about invalid key tokens or something like that. If I run unity, I get other error messages telling me it can't load the memory or something like that.   Since I'm using Windows 7 fine right now, I'm guessing I haven't actually damaged the hardware but I don't feel like reinstalling Ubuntu right now, can you give me any tips on how to diagnose and/or fix memory related problems like this? I don't understand how it works at all, I thought memory was RAM, just some rapidly readable/writable volatile memory thats used to perform operations, I don't see how there could be any problems with it. Could it be that bleachbit created a lock that prevents other linux programs from using the RAM? Also, those memory tests in the GRUB menu, are they simply for diagnosing, or do they fix problems too?

---

### Post by Frogs Hair on 2014-06-11
The function is a memory and swap cleaner and BB doesn't write much more about it on the website . [COLOR=#000000]CTRL + ALT + F1  takes you to a TTY session and under normal conditions [/COLOR] [COLOR=#000000]CTRL + ALT + F7 returns to the desktop from TTY. You might try just to see what if any errors occur .  I would suggest using the BB Forum. [/COLOR]http://bleachbit.sourceforge.net/forum

---

### Post by frogwarrior on 2014-06-12
When I log into a guest session, it tells me there is 0 memory available. When I go into TTY session, I can mount the encrypted home directory with ecryptfs-mount-private, but when I just run man bleachbit, I get an error message talking about some directory called ~/GhYUsHSb or something like that. There are 2 files in that directory, but they're large files whatever they are. If I cd to the directory and run ls, it stalls and nothing happens, I have to just exit it with CTRL + C. I can't run most of the bleachtest jobs, It keeps telling me theres no space available on the harddrive. I installed Ext2Fsd on Windows so I can look at my linux partitions, and heres what it shows me:
[IMG]http://i.gyazo.com/bae58e0bd948a4b9a3e98b3295b3f403.png[/IMG]
the F: is my linux partition and its telling me that there is only 95Gb out of 96Gb left. I tried deleting a few things it didn't change anything. For some reason my linux partition only has 1.22Gb of free space left:
[IMG]http://i.gyazo.com/636238b8eb25199add209c1b58b26838.png[/IMG]
bleachbit is supposed to free space up so I don't know whats going on here. I have a 6Gb SWAP partition, could it be that something has completely overloaded the SWAP partition, and now its taking memory from my primary partition? I'm thinking that ~/GhHG6Lb (or whatever) directory is where bleachbit formed a temporary SWAP file, and since bleachbit crashed halfway though, it didn't delete this SWAP file. There are some more things I can delete, I'll see if that frees up enough memory to solve this problem.

One pain in the ass is that I can only access these tty sessions, if I try to run any GUI programs it won't work. I installed a CLE browser, but its pretty crap. Is there a practical way I can access these forums through the command line?

If I go into the properties of my linux parition, heres what it says:
[IMG]http://i.gyazo.com/1579de9e89a3c04359406a26cfd821f2.png[/IMG]
so I have way more capacity than I'm using. I don't know what the issue is. I'm considering deleting this ~/GhH4ByU folder, I don't know what it does though so I don't want to go breaking anytihing.

UPDATE: I just found this thread: [http://bleachbit.sourceforge.net/forum/after-execution-root-cant-sign-user-account](http://bleachbit.sourceforge.net/forum/after-execution-root-cant-sign-user-account)

I forgot to mention I ran bleachbit as root, sounds like this guy has the exact same issue I have. Someone in the thread said that if your disk space is full, you need to locate a file with a long name and delete it. He said its located in /, but this GhH4ByU directory is located in my home folder. I'm gonna delete it and see what happens, hope I don't get locked out of my ecrypted home directory, but I'll take the risk.

---

### Post by frogwarrior on 2014-06-12
It worked. I just needed to sudo -i, then ran ls -l and saw a massive file with a ridiculously long filename in the / directory. I backed it up to be safe, then deleted it, now everythings working fine.

---

