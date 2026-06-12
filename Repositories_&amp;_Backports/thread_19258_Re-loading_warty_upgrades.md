---
title: "Re-loading warty upgrades"
date: 2005-03-11
forum: Repositories &amp; Backports
---

### Post by kenironside on 2005-03-11
I have looked through the FAQ's and forums but couldn't find an answer to this question.

I have installed warty on a PC and it downloaded loaded 105Mb of updates. Now I want to install warty on another PC but I would like to avoid another 105Mb download.

Can I save the 105Mb of updates on a CD or make it available on the network so that the new PC can use these files rather than download them? All these PC's are on a network.

Where does warty/apt store downloaded packages? It looks to be in /var/cache/apt/archives. Could I copy this to the new PC and do something to get apt to pick these up?

I have see a post which give instructions on how to add a directory to the apt repositories.  [http://ubuntuforums.org/showthread.php?t=16797](http://ubuntuforums.org/showthread.php?t=16797) "Adding a directory to the sources lists". Are these instructions valid for what I want to do?

Thanks, Ken

---

### Post by bored2k on 2005-03-11
[QUOTE=kenironside]I have looked through the FAQ's and forums but couldn't find an answer to this question.

I have installed warty on a PC and it downloaded loaded 105Mb of updates. Now I want to install warty on another PC but I would like to avoid another 105Mb download.

Can I save the 105Mb of updates on a CD or make it available on the network so that the new PC can use these files rather than download them? All these PC's are on a network.

Where does warty/apt store downloaded packages? It looks to be in /var/cache/apt/archives. Could I copy this to the new PC and do something to get apt to pick these up?

I have see a post which give instructions on how to add a directory to the apt repositories.  [http://ubuntuforums.org/showthread.php?t=16797](http://ubuntuforums.org/showthread.php?t=16797) "Adding a directory to the sources lists". Are these instructions valid for what I want to do?

Thanks, Ken[/QUOTE]
 Yes copying those files the old school way will work.  [http://ubuntuguide.org/#backuprestoredownloadedrepositoriescache](http://ubuntuguide.org/#backuprestoredownloadedrepositoriescache)

---

### Post by krusbjorn on 2005-03-11
my guess is that if you copy the package files to /var/cache/apt/archives on the comp you wanna update, and then do an "apt-get upgrade", apt-get will check for the packages before downloading them, and since they are there, it will install them :P

---

### Post by kenironside on 2005-03-11
" Yes copying those files the old school way will work. http://ubuntuguide.org/#backupresto...positoriescache"

Thanks, I don't know why I didn't see that section.

Regards, Ken

---

### Post by bored2k on 2005-03-11
[QUOTE=kenironside]" Yes copying those files the old school way will work. http://ubuntuguide.org/#backupresto...positoriescache"

Thanks, I don't know why I didn't see that section.

Regards, Ken[/QUOTE]
 Welcome to the Forums btw.

---

