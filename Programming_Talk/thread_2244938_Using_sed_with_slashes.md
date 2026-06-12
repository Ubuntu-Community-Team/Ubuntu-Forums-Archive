---
title: "Using sed with slashes"
date: 2014-09-19
forum: Programming Talk
---

### Post by The_Weaver on 2014-09-19
I'm trying to replace a directory location with the relative location in a number of playlists  ie replace "../home/keith/Music/Songs" with "..". After a bit of research I think sed could be useful. 

I think the following command is what I what to use :

find /home/keith/Music/Songs/Playlists -type f -readable -writable -exec sed -i "s#../home/keith/Music/Songs#..#g"{} \;

but it fails since I'm using slashes.

Any suggestions?

Thanks

---

### Post by steeldriver on 2014-09-19
You appear to be handling the slashes sensibly (i.e. using a # as the sed delimiter instead) 

However you should replace the leading .. with \.\. or [.][.] to make it match literal dots - else it will match any two characters

How exactly is it failing? Can you post a minimal example?

---

### Post by Vaphell on 2014-09-19
does it really start with ..? /home/user/.....  looks like an absolute path and .. shouldn't make sense

---

### Post by nerdtron on 2014-09-19
Have you tried encasing the sed parameters in single quotes?

Also have you tried escaping the slashes with backslashes?

---

### Post by CaptainMark on 2014-09-20
Are you not able to use the dirname command for this, its been a while since I used it but it was included in a standard install

---

### Post by The_Weaver on 2014-09-20
I've removed the leading .. as it was an absolyet path and not required, and relasied I was missing a space before the {}. So the command now is:

find /home/keith/Music/Songs/Playlists -type f -readable -writable -exec sed -i "s#/home/keith/Music/Songs#..#g" {} \;

and it worked.

Many thanks

---

### Post by steeldriver on 2014-09-20
Ah good - for the record, it's a lot easier to spot things like missing space if you post commands between [CODE] markup tags

---

