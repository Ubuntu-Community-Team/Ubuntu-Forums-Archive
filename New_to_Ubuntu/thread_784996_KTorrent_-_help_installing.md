---
title: "KTorrent - help installing"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Pechkin000 on 2008-05-07
Hi there,

I just switched to Ubuntu from windows and while I love the speed and stability I have to say I keep finding myslef banging my head on the wall a lot more often then I'like.

My current "project" is to try and install Ktorrent using apt get - so far I have not being able to even compile it let alone get to the install part.  I read through the compiling instructions on the Ktorrent site and did what it said - had to use apt-get to install the cmake - but then I get gcc error when I try and actually compile.

I dont know what I am doing wrong - ofcourse I dont really know what I am doing and I cant seem to find any help anywhere - so I decided to post - maybe someone can kindly walk me through this process.  I used to laugh at my friends who could not get their **** working in windows and always was the the one who got the calls to help - I thought hey how hard can linux be - but I just dont seem to get the very basics at this point no matter how much I read.  Please help. Whenever I find resolution to my problems its always a list of liness of bash script that i can replicate but dont quite understand so sometimes it works and sometimes it doesnt - I consider myslef an intelligent person - but holly **** - why is this so difficult :(

---

### Post by Xiong Chiamiov on 2008-05-07
KTorrent is available in the repos, so there's no need to compile it.  Just
```

sudo apt-get install ktorrent

```

---

### Post by lsmobrian on 2008-05-07
Sorry, I didnt understand from your post if you were learning how to install something from source or just to install ktorrent in general, but here is how to install ktorrent.  If you are running gnome instead of kde, you could find a better torrent client for gnome. transmission isnt bad and is installed by default

sudo apt-get install ktorrent

---

### Post by seshomaru samma on 2008-05-07
run this command:
```
sudo apt-get install ktorrent
```

EDIT: not quick enough

---

### Post by Xiong Chiamiov on 2008-05-07
I suppose I should give you the standard, "[How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")" link.

---

### Post by Pechkin000 on 2008-05-07
great thank you very much - and yes I am doing both first trying to install ktorrent specifically but more importantly trying to understand the process of compiling

thanks for quick replies!

Xiong Chiamiov: thanks for the link!  I dont know how I missed it

---

### Post by nowshining on 2008-05-07
u can download my torrent for 2.2.6 here: [http://www.mininova.org/tor/1384470](http://www.mininova.org/tor/1384470) & download it thru ktorrent 2.2.5 if u don't of course have 2.2.6 and are using Gutsy Gibbon.

let me know if it installs or not, it's a deb file for 2.2.6- for a 32bit computer. Again let me if it works for u or not.

also next time install

build-essential in the repos for compiling. :) this intalls gcc ,etc..

---

