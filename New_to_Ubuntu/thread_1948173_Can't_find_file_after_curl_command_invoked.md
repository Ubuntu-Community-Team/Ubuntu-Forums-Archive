---
title: "Can't find file after curl command invoked"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by jps2012 on 2012-03-27
I used the 'curl' command in bash to download a file. After watching it complete (according to the Terminal) I couldn't find it. I'm wondering if it actually downloaded (see the text below, from Terminal), and if it did, where it might have landed. My Firefox preferences are set to "download to Desktop." The file isn't on the Desktop, and it isn't in Downloads.

Here's the command I used (with the name/location of the PDF I wanted)

~$ curl -O 'http://yosemite.epa.gov/r10/water.nsf/NPDES+Permits/Sewage+S825/$FILE/503-032007.pdf'

Here's what the command and result looked like in Terminal (note that Terminal says 100% of the file has downloaded): 

~$ curl -O 'http://yosemite.epa.gov/r10/water.nsf/NPDES+Permits/Sewage+S825/$FILE/503-032007.pdf'
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  232k  100  232k    0     0  93612      0  0:00:02  0:00:02 --:--:--  104k

---

### Post by Krytarik on 2012-03-27
> **jps2012 said:**
> Here's the command I used (with the name/location of the PDF I wanted)

~$ curl **-O** 'http://yosemite.epa.gov/r10/water.nsf/NPDES+Permits/Sewage+S825/$FILE/503-032007.pdf'
Referring to your [other thread]("http://ubuntuforums.org/showthread.php?t=1948047"), there we are again, in the manpage department. :P
> **-O/--remote-name**               Write output to a local file named like the remote file we  get.               (Only  the file part of the remote file is used, the path is cut               off.)                The remote file name to use for saving  is  extracted  from  the               given URL, nothing else.                Consequentially,  the  file will be saved in the current working               directory. If you want the file saved in a different  directory,               make sure you change current working directory before you invoke               curl with the **-O/--remote-name** flag!Source: [http://manpages.ubuntu.com/manpages/oneiric/en/man1/curl.1.html](http://manpages.ubuntu.com/manpages/oneiric/en/man1/curl.1.html)

Regards.

---

### Post by jps2012 on 2012-03-27
Thanks, Krytarik. I really didn't know what -O meant. Now I do. It means (surprise) that in some cases the file isn't going to be named what I THINK it might be named, and it's therefore not going to be easy to find (unless there's some kind of bash command for 'give me the names of all the files I've downloaded in the last X minutes'). 

I just found the file. Contrary to what the manpage seems to be saying, it didn't download to the current directory (which was set for my home folder when I started the download).

It downloaded to a subdirectory of that directory (Documents). I'm not sure why that happened, but as long as the same thing happens consistently, I'll know where to look. 

Can you tell me if files are saved in different folders relative to their file type? In other words, would PDFs potentially download to one folder, but other file types would download to a different folder? 

I've noticed that when I use apt-get to download files, some are being downloaded to Downloads, but others (it seems) are going to the tmp folder.

---

### Post by Krytarik on 2012-03-28
> **jps2012 said:**
> I really didn't know what -O meant. Now I do. It means (surprise) that in some cases the file isn't going to be named what I THINK it might be named, and it's therefore not going to be easy to find ...

I just found the file. Contrary to what the manpage seems to be saying, it didn't download to the current directory ...
Actually, it works *exactly* as expected here:
```
[krytarik]:~$ mkdir Test
[krytarik]:~$ cd Test
[krytarik]:~/Test$ curl -O 'http://yosemite.epa.gov/r10/water.nsf/NPDES+Permits/Sewage+S825/$FILE/503-032007.pdf'
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  232k  100  232k    0     0   149k      0  0:00:01  0:00:01 --:--:--  175k
[krytarik]:~/Test$ ls
503-032007.pdf
[krytarik]:~/Test$
```> **jps2012 said:**
> I've noticed that when I use apt-get to download files, some are being downloaded to Downloads, but others (it seems) are going to the tmp folder.
You may mean "[wget]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/wget.1.html")", but that shouldn't apply to it either.

---

### Post by jps2012 on 2012-03-28
Krytarik: Thanks, but I wasn't asking if it worked for you the way you expected it to. I was asking HOW it worked. I'm not sure how I can learn from the statement (in essence) "I expected something, and I was correct in my expectation." 

I imagine there are all kinds of things you would expect, that happen in precisely the way you expect them to. Which is one of the reasons you're an expert, and I'm a beginner--why I have little knowledge, and therefore even less expectations. 

It's finding out what to expect (and WHY to expect it) that would help me (and other beginners, I suspect).

---

### Post by Krytarik on 2012-03-28
> **jps2012 said:**
> Krytarik: Thanks, but I wasn't asking if it worked for you the way you expected it to. I was asking HOW it worked. I'm not sure how I can learn from the statement (in essence) "I expected something, and I was correct in my expectation."
Ok, let me rephrase it for you then: "It worked according to its manpage." :P

---

