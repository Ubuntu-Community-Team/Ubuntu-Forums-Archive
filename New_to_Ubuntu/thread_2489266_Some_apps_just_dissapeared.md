---
title: "Some apps just dissapeared"
date: 2023-07-24
forum: New to Ubuntu
---

### Post by dragoselul on 2023-07-24
First of all I want to say that I am new to Ubuntu, but I am not new to bash.
I am a software engineering student, and I want to learn to use Linux since I heard is much easier to code in.
I installed a few IDEs and some languages (Java, JS and .NET). 
Everything fine, until later today I opened up my PC, and my drive wasn't mounting (a drive that I used as storage in Windows and is NTFS).
I installed ntfs-3g again and carried on with my work. Later today I randomly wanted to change the background and my settings app disappeared.
I want to know what causes those apps to just disappear, I don't know if other apps disappeared as well...
Thanks for reading this far. Have a good day :)

---

### Post by ian-weisser on 2023-07-24
What do your logs say about it?

---

### Post by ajgreeny on 2023-07-24
Was that NTFS disk used on Windows recently because Windows by default uses fast start, a hibernation state and not a "real" shutdown. This means any partition that is not properly unmounted will be unusable in Linux.

Also, if there is any repair needed on that partition's NTFS filesystem it will have to be carried out using Windows as there is no way to do it in Linux. NTFS is not appropriate as a filesystem to use in Linux if you can not use Windows to repair it when necessary.

---

