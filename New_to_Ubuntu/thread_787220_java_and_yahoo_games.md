---
title: "java and yahoo games"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by jwftm33 on 2008-05-08
[I] need some help with java and yahoo games I have downloaded jre and when i go to yahoo games and join a spades room it will let me join the table, but as soon as I leave the table I am no longer in the room and it says A. Applet ygames_applet bail. Can anyone tell me why it is doing this. I am not sure what to do. Any help would be appreciated. :(

---

### Post by lesergi on 2008-05-08
Do you install jre from official ubuntu repositories?

---

### Post by nowshining on 2008-05-08
how did u exactly insall the jre?

did u create a folder in ur home folder then cd to it, issue the commands from the site directions for linux, and then symlink it from the folder to the firefox .mozilla folder?

if all fails and u correctly insalled it, then delete the java cache - see my site in my sig (Ubuntu/Kubuntu Gatherings) for more info.

---

### Post by jwftm33 on 2008-05-08
I installed java from the terminal it was somthing like sun-java6 -install jsun-java6-jre or somthing i can get into yahoo spades and play a game but as soon as i leave the table i get a Applet ygames applet bail message and have to re enter room to go to another table to play a game.

---

### Post by lesergi on 2008-05-09
If java works for a time and after fails, like says nowshining delete java cache. If not work, I think it'll be a web bug, you must email to responsable.

Bye!

---

### Post by Lori Whitty on 2008-06-16
I'm having the exact same problem when trying to play canasta on Yahoo...has anyone solved this yet????

---

### Post by jamesstansell on 2008-06-16
If your browser is using the gcjwebplugin that may be the cause of your problem.  Try uninstalling the icedtea-gcjwebplugin package and then running this command (as seen at [http://ubuntuforums.org/showpost.php?p=5187747&postcount=3](http://ubuntuforums.org/showpost.php?p=5187747&postcount=3))
```
sudo apt-get install sun-java6-plugin && sudo update-java-alternatives -s java-6-sun
```

---

### Post by avtolle on 2008-06-16
But be aware that if you are using the AMD 64 version, there is no 64 bit plugin for sun java for firefox. I would suggest your going to the 64 bit forum for further discussion of this, and (IIRC) some things to try to do to get the 32 bit version of java and the plugin going under your 64 bit installation.

---

### Post by stchman on 2008-06-16
> **jwftm33 said:**
> [I] need some help with java and yahoo games I have downloaded jre and when i go to yahoo games and join a spades room it will let me join the table, but as soon as I leave the table I am no longer in the room and it says A. Applet ygames_applet bail. Can anyone tell me why it is doing this. I am not sure what to do. Any help would be appreciated. :(

I am going to assume you are using Hardy.

If you are using 32 bit do this.
```

sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

64 bit use this.
```
sudo apt-get -y install icedtea-java7-jdk icedtea-java7-jre icedtea-java7-plugin
```


This should do the trick.

---

### Post by Lori Whitty on 2008-06-18
I have the same problem playing Yahoo canastain ubuntu hardy.  This fix didn't help...sorry...hope someone figures this out soon!

---

### Post by alzie on 2008-06-18
I don't play at yahoo but I do play at pogo and I was having issues.

I followed the directions here : [http://ubuntuforums.org/showthread.php?t=784384](http://ubuntuforums.org/showthread.php?t=784384)

Basically I removed java with synaptic and then installed sun java 5 and most of my difficulties with pogo were solved.

I don't know if this will help in your case tho :(

---

### Post by Lori Whitty on 2008-06-18
THANK YOU VERY MUCH alzie!!!  Removing Sun Java 6 in Synaptics and then installing Sun Java 5 worked PERFECTLY!  I no longer get that applet bail error when playing Yahoo games.  Thanks again!  :)  You're help was GREATLY appreciated!

---

### Post by Pjotr123 on 2008-06-18
Peculiar. I play a lot of chess on Yahoo Games, and I have Sun Java 6. No problems whatsoever.

---

