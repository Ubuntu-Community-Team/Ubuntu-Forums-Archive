---
title: "error message when trying to install"
date: 2015-03-09
forum: New to Ubuntu
---

### Post by scott91 on 2015-03-09
hello everyone, im trying to install unbuntu and during the install process im getting the error message saying 'cannot retrieve the install file .../wubi-14.04-rev286.log. can you help tell me what this means, is it an issue with my laptop or the software? the log message appears during the install process, i get past the file extraction but i dont get much further. any help is welcome, cheers. :)

---

### Post by newb85 on 2015-03-09
Welcome to Ubuntu and the forums!

How are you trying to install Ubuntu?  The use of Wubi (the Windows Ubuntu installer) is *very* strongly discouraged, as it is no longer supported.  Or perhaps I've misinterpreted that message, and you're doing it correctly from bootable install media.

---

### Post by ajgreeny on 2015-03-09
There is no point trying to use wubi any more as support and development has been removed from it, and will not work in many newer computers; UEFI or GPT partitions stop it from being of use and you will not find any forum members who can help you with this.  Wubi was never intended to be anything other than a way to check if your hardware would run Ubuntu, not as a real dual boot method.

I recommend that you do a partitioned installation and forget wubi entirely.

See [http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by Mark Phelps on 2015-03-09
WUBI was used to install Ubuntu from inside Windows, and at first, it did that from the CD.  But later, it was changed to require downloading the WUBI image online and installing from that.  WUBI support was dropped after Ubuntu 12.04, and as folks have mentioned, is strongly discouraged now.

---

### Post by hakuna_matata on 2015-03-09
Hello scott91,

welcome to the forums.

> **scott91 said:**
> 'cannot retrieve the install file .../wubi-14.04-rev286.log. can you help tell me what this means, is it an issue with my laptop or the software?
First of all, this means that you use Wubi. Wubi is not recommended and it is not really officially supported. So it is better to avoid it. 

It is possible to analyze the reason for the error message with your file **wubi-14.04-rev286.log** in the Windows temp folder (**%temp%** or something like **\Users\YourName\AppData\Local\Temp**), but IMHO it is only helpful if you use Wubi.

---

### Post by mörgæs on 2015-03-10
Now we have four more or less similar answers to the question. 

Thanks but please let's give the thread some rest until original poster returns so we don't drown him in advice.

---

### Post by scott91 on 2015-03-10
wow, thanks for all the help. im a relative novice when it comes to this kind of thing so all the help is appreciated. im dying to try anything apart from windows 8 which is whats installed on my pc which can be extremely irritating at times and ubuntu has been highly rated by a friend of mine. im gonna try follow some of the advice and have a look at other threads and try install it properly this time. cheers.

---

### Post by scott91 on 2015-03-10
might be time to admit that i have no clue what im doing. think it might be a good idea to ask my IT literate friend to help before i go losing all my data by doing something which im unsure how to do properly.

---

### Post by sudodus on 2015-03-10
Backing up all the data you don't want to lose is a good start. 'Tough guys never backup their data. They do the job twice instead' ;-)

Installing operating systems and editing partitions are risky operations, so it is a good idea to get help from your IT literate friend.

---

