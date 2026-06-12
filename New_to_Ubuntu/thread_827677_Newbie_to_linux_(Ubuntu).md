---
title: "Newbie to linux (Ubuntu)"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-06-13
Hi all,

  i am absolutely  a newbie to Ubuntu. i have installed Ubuntu 8.04 in my box (512MB RAM, 80GB HDD, Intel duo processor, ATI graphics driver) just a week. i would love to learn linux commands, basics especially. Please suggest me where i start from scratch. i wanna learn both commands as well as architecture of linux (ubuntu) and of course all stuffs related to ubuntu - linux.

  Another clarification i need is i have activated my internet connection (TATA vsnl, via modem with login credentials) as specified in [http://help.ubuntu.com/](http://help.ubuntu.com/) and i gave "YES" for connecting at start up. how can i disable this feature so that i can manually connect to internet whenever i want to and i can disconnect the same. i tried sudo poff dsl -provider but it says "cannot find PPPo and no connnection stopped". please help me in this regard.

  I am in need to learn flash programming also for my official purpose. suggest me a suitable path for this please.

  I am grateful to you guys if you clarify me the above things. Moreover am very eager to learn things related to linux - ubuntu.

Thanks in advance

---

### Post by FAJALOU on 2008-06-13
Well welcome welcome :)  .  You learn alot of commands basically as you go along, especially from different tutorials to get something here or there to work.  

here's some videos to help: [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

this is a good one too.
basically to install a package from terminal:
sudo apt-get install <packagename>
to find a package:
sudo apt-cache search <packagekeyword>


Learning the directories: [http://www.elvenware.com/charlie/linux/LinuxDirs.html](http://www.elvenware.com/charlie/linux/LinuxDirs.html)
(side note googling linux directories is helpful to see all the different directories etc.).

Good luck and feel free to ask questions.  O and welcome to Ubuntu :)

---

### Post by balachandarlinks on 2008-06-13
Welcome to Ubuntu ............Try to google for materials..u ll find a lot....Install wine so that u can use macromedia flash in linux....

---

### Post by golgo13 on 2008-06-13
welcome
there is loads of stuff out there to solve most problems
this ubuntu search engine is helpful
[http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

---

### Post by kdcoetzee on 2008-06-13
Welcome to the World of Ubuntu...

[Ubuntuguide.org]("http://ubuntuguide.org")
[www.psychocats.net]("http://www.psychocats.net/")
[www.ubuntugeek.com]("http://www.ubuntugeek.com/")
 
Here is my fav Ubuntu sites. they will help you setting up Ubuntu and help fix problems you may confront.

And of course [ubuntuforums.org]("http://ubuntuforums.org")
the chance that someone else already had the same problem as you is good.

---

### Post by lisati on 2008-06-13
> **FAJALOU said:**
> 

here's some videos to help: [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

Possibly typo on the page: I think it means complEmenting.......or did the page designer mean to say something nice?

---

### Post by mailtwogopal on 2008-06-13
hi all,

  will definitely look into all the links u guys gave and also google it. thanks to all of u guys replied. many more thanks in advance too.

---

### Post by hyper_ch on 2008-06-13
it is adviced to use a descriptive thread title that reflects the content of the question and not a generic "noob here" or "help needed".

Furthermore, for multiple unrelated problems it is also adviced to open seperate threads so that they can be answered individually and you can mark them individually as "solved" - once they are.

---

### Post by acidsolution on 2008-06-13
Your search about ubuntu  ends here so always visit Ubuntu forums . This is pool of excellent people always ready help .
Post any queries or problem you will certainly get answer.

---

### Post by KaliVoid on 2008-06-13
Hi & Welcome

to disconnect from the internet just type
```
sudo poff
```

a good site to read before you start linux tutorials is [Linux is Not Windows]("http://linux.oneandoneis2.org/LNW.htm")

Have Fun

---

### Post by mailtwogopal on 2008-06-13
hi kalivoid,

  i tried "sudo poff" and it worked. thanks. but the thing is how to turn it on i tried the following commands but it dint work.

 1. sudo pon
 2. sudo pon dsl -provider 

i dont know why sudo poff works and sudo pon is not. kindly correct me, i feel am wrong at some point in turning on the internet connection again. thanks in advance.

 what i did atlast i used "sudo pppoeconf" and configured again and i gave connect at startup again as previously it was. please help.

---

### Post by KaliVoid on 2008-06-13
Hi

u did it right but with a space.
"dsl-provider" with no spaces.
```
sudo pon dsl-provider
```

---

### Post by mailtwogopal on 2008-06-13
hi kalivoid,

  it worked buddy. thanks a lot. i love to be in this forum.

---

### Post by avtolle on 2008-06-13
Since you are a new user, may I suggest keeping a notebook of "things that worked" for reference in the future, together with any "How Tos", etc. you use to install things. This will give a valuable reference in the future.

---

### Post by mailtwogopal on 2008-06-13
hi avtolle,

  Thanks! am already using that right from day 1 of installation.

---

