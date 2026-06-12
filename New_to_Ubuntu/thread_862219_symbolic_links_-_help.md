---
title: "symbolic links - help"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by dioltas on 2008-07-17
Ok this might be a bit stupid, but anyway.

I'm using hardy, and I have 2 users on my computer, me and my brother.

I wanted to allow him access to my music, so I just created a symbolic link to my music folder in his music folder, and gave him permissions to read write all files in my music folder. That worked fine.

Then I wanted to have his music in my library aswell, so I just created another symbolic link in my Music folder to his.
The problem is, now in rhythmbox it adds all the files in my Music folder into my library, all the files in my brother's through the second symbolic link, then all my music again through the first symbolic link. So I have doubles of all files in rhythmbox.

[COLOR="Blue"]So my question is, is there anyway I can change the permissions of a symbolic link so that a user cannot access it but still be allowed to access the directory it points to?[/COLOR]

Sorry for the long confusing post. It's not a major problem, just an annoyance.

---

### Post by Inxsible on 2008-07-17
Just offhand...you can make his symbolic links in a different folder....so when you access his music folder...you will not get to his symbolic links..

Same way you can have you symbolic links in a different folder.

Dont know if that is something that you would consider.

---

### Post by dioltas on 2008-07-17
Yea, I suppose I'll have to do something like that.
What I was trying to do was a bit ridiculous really I suppose, wanted to have my music folder inside his music folder, and vice versa.

My best option would probably be to just have a shared music directory between all users. I wonder if there's somewhere I can change something so that a users default music folder would be /home/Music instead of /home/username/Music... Thanks for the help

---

### Post by Inxsible on 2008-07-17
> **dioltas said:**
> Yea, I suppose I'll have to do something like that.
What I was trying to do was a bit ridiculous really I suppose, wanted to have my music folder inside his music folder, and vice versa.

My best option would probably be to just have a shared music directory between all users. I wonder if there's somewhere I can change something so that a users default music folder would be /home/Music instead of /home/username/Music... Thanks for the help+1 to the shared music folder.

I always have my multimedia in a shared drive so any of my OSes can have access to it.

Also..putting it in a different partition altogether would be a better option. Something like /mnt/Shared which can have different folders like Music Movies or what have you. Just give rw permission to the group (audio - mebbe) and add yourself and your brother as members of that group

---

