---
title: "Can't install softwares."
date: 2008-05-01
forum: New to Ubuntu
---

### Post by manojks on 2008-05-01
Guys, I just installed Ubuntu 7.10 on my system but whenever I try to check any checkbox to install a software, This (see attached image) shows up.

---

### Post by OffAxis on 2008-05-01
It's not picking up your internet connection.
Are you connected?

what's 
```
ifconfig
``` give you?

---

### Post by OffAxis on 2008-05-01
form a command line you can also try
```
sudo apt-get update

```
(it does the same thing as the 'Reload' button)
and it'll print an error message to the console.

---

### Post by manojks on 2008-05-01
No, its picking up the Internet Connection. I can browse using Firefox.

---

### Post by Paqman on 2008-05-01
> **manojks said:**
> No, its picking up the Internet Connection. I can browse using Firefox.

Try the command line update given above, it'll spit our more informative error messages.

---

### Post by manojks on 2008-05-01
Sorry. But what are these command lines and how to use them. I'm a complete noob.

---

### Post by dje on 2008-05-01
Just checking.... but have you clicked the 'Refresh button' when that box comes up?
And to enter those commands go to Applications >> Accessories >> Terminal

dje

---

### Post by nisarg on 2008-05-01
There are lot of guides and blogs around that you be of help. 
Heres one: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Got to give it a good search ..

---

### Post by manojks on 2008-05-01
Thanks. I'll see if it works.

---

### Post by Cap'n Redbeard on 2008-05-01
[FONT="Times New Roman"]Hi Folks,

Similar problem to manojks' above.

Updated from Gutsy to Hardy four days ago. This little machine will connect to 'tinternet (it does the apt-get update fine) but apt-file hasn't worked since midnight (30/4/8).

> [SIZE="1"]redbeard@Redbeard-desktop:~$ sudo apt-file update
Can't get [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz) (404)
Can't get [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz) (404)
Can't get [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Contents-i386.gz) (404)
Can't get [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Contents-i386.gz) (404)
Can't get [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Contents-i386.gz) (404)
Can't get [http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz) (404)
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz) (404)
redbeard@Redbeard-desktop:~$ [/SIZE]


What am i doing wrong ?  :confused:

[/FONT]

---

### Post by manojks on 2008-05-01
Sorry but it didn't work> the same thing shows up.

---

### Post by OffAxis on 2008-05-01
What error message pops up when you run
```
sudo apt-get update
```
from the terminal command line (Applications >> Accessories >> Terminal
)?

---

### Post by manojks on 2008-05-01
This is what I get:


Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Reading package lists... Done

---

### Post by manojks on 2008-05-01
Well guys, the problem has been solved. Just checked some boxes [here]("http://files.myopera.com/manojks/files/sc2.png").

---

### Post by SunnyRabbiera on 2008-05-01
yeh, well you might be having issues thanks to the server overloads with the demand for hardy.

---

### Post by Spoken on 2008-05-01
sudo apt-get update in terminal

weird how its not picking up your connection.

---

### Post by Paqman on 2008-05-02
> **Cap'n Redbeard said:**
> [FONT="Times New Roman"]
What am i doing wrong ?  :confused:

[/FONT]
Probably nothing. It's reporting 404 errors for trying to contact the repositories. Same as when you get a 404 error when trying to connect to a website with your browser. It just means your PC hasn't made a connection to the remote server.

Check your internet connection. If that's ok, check your repos in Software Sources. Try a different country's server and reload.

---

### Post by Cap'n Redbeard on 2008-05-02
Cheers for the suggestion Paqman,

> Check your internet connection. If that's ok, check your repos in Software Sources. Try a different country's server and reload. 

i'm a beginner - what are "repos" ?

To try a different country's server, do i comment out the UK URL's and un-comment somebody elses in apt/atc/sources.list ?

---

