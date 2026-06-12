---
title: "cant mount network share but i can &quot;connect to server&quot;"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by hookitup on 2013-06-15
Hey Folks. 

So im not sure if anybody has asked this yet. i did a little looking around and couldnt find to much. but basically the title says it.

ubuntu 13.4 & 12.10

i am trying to connect to a network share (this is a windows file server). i have always been able to just run the command
 ```
sudo mount -t cifs //IPADDRESS/share /mnt/myshare -o username=user,password=passwd
``` 

and it would mount just fine and i can copy stuff and make directory and what not. now i recently messed with the server and changed a few settings and am no longer able to connect this way (also i went to the new 12.10 and also tried 13.4 so messing with server may not be the full cause). BUT i **_can_** connect if i open the file browser and go to "connect to server" . how is this different and why am i able to do it this way?

i took a look at the command ```
mount
```
to see what its mounting and how its mounting it and this is what it returns for it.
```
gvfsd-fuse on /run/user/cj/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=cj)
```

i ran an ```
ls
``` on /run/user/cj/gvfs/smb-share\:server\=IPADDRESS\,share\=share/ and see all my files on that share.


now if i try a ```
sudo cp blah blah blah
``` to that directory i get permission denied. but if i copy and past something trough the file browser it works fine.
a little confused why this is. how can i either mout this so i can do sudo cp or keep it how it is but copy to it through the terminal 



as a side note. i can run the command 
```
sudo mount -t cifs //IPADDRESS/share /mnt/myshare -o username=user,password=passwd
```
just fine in backtrack or kali or some other linux distros and have the file share mounted like i normally do . this is confusing me even more.


let me know your thoughts and questions
i appreciate the help

---

### Post by steeldriver on 2013-06-15
Do you get an error message when you try the manual cifs mount? 

I've seen a few posts recently suggesting cifs mounts now need an explicit [FONT=courier new]sec=ntlm[/FONT] or [FONT=courier new]sec=lanman [/FONT]option - see [https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/1113395](https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/1113395)

IIRC gvfs user-mounts are mode 500 i.e. only the owner (user) can even open them - you'd likely find that plain 'cp blah blah blah' (no sudo) would have worked

---

### Post by hookitup on 2013-06-15
hello steeldriver

thanks for the replay and wow yes i did a cp without sudo and success it copied it over. i totally didnt think of that.

and ok wow this just got super weird.

i just tried the mount again but on a different share and it worked. so weird. i then tried the mount again on the one share above and success .. im way confused. now about 5 minuets before i just tried this mounting on my ubuntu machine, i  turned on my Raspberry Pi and and tried to mount the share on that and successful first try no errors. 

does anybody think this would effect my ubutnu machine mounting ? like maybe my RS pie is like the backtrack/other OS's in a sense it can mount with no issue and that opens a portal of some sort through the windows permission/security and allows the ubuntu machine to connect?????

i may be thinking about this way to hard. time to reboot and see if we can recreate the same issue.

---

### Post by hookitup on 2013-06-15
soo weird. i reboot everything and still successful. well thanks for the help everybody

---

