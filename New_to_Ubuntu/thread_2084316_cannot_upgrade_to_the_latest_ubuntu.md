---
title: "cannot upgrade to the latest ubuntu"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by 12katia34 on 2012-11-15
dear all,
I have been automatical messages to upgrade to the next ubuntu-version whenever I launched the internet during the last months.
I however cannot upgrade folllowing the offered path

this is what happends after typing in my sudo-password and fetching of some 100 files:

                                  ****
W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/luzid/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/luzid/partner/source/Sources)  404  Not Found [IP: 91.189.92.191 80] 
 , E:Some index files failed to download. They have been ignored, or old ones used instead. 

*****


Now as far as I know, I don't have a network problem since internt always works fine.
I have tried to upgrade via terminal using sudo apt-get upgrade and something was indeed upgraded and terminal tells me "done" now, but the next time on the internet I received an ubuntu end of life message indicating that I still am using the old outdatet version.


What now?
Thanks for helping.

---

### Post by raja.genupula on 2012-11-15
actually this is a temporary server down issue . to make it check just open the 
[http://archive.canonical.com/ubuntu/dists/luzid/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/luzid/partner/source/Sources)

URL from your browser . 

Its just server down .

here to solve this issue you got two options .
1. change to another server from update manager settings .

or

2. wait for sometime and the server will be up again .

---

### Post by quentinl on 2012-11-15
i upgraded using the software center
if you haven't already tried that you could have a look at settings and play with them a bit that is why there is a restore defaults button in case someone dose something there not

---

### Post by Paqman on 2012-11-15
> **12katia34 said:**
>                                  ****
W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/luzid/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/luzid/partner/source/Sources)  404  Not Found [IP: 91.189.92.191 80] 
 , E:Some index files failed to download. They have been ignored, or old ones used instead. 


This could be a typo in your sources.list file. The URL above refers to "luzid", but the correct code name for that release of Ubuntu is "lucid".

This URL works: [http://archive.canonical.com/ubuntu/dists/lucid/partner/source/](http://archive.canonical.com/ubuntu/dists/lucid/partner/source/)

To correct this open your sources list for editing by hitting Alt-F2 and typing:
```
gksudo gedit /etc/apt/sources.list
```
then do a find-and-replace swapping the word "luzid" for "lucid"

---

### Post by raja.genupula on 2012-11-15
> **Paqman said:**
> This could be a typo in your sources.list file. The URL above refers to "luzid", but the correct code name for that release of Ubuntu is "lucid".

This URL works: [http://archive.canonical.com/ubuntu/dists/lucid/partner/source/](http://archive.canonical.com/ubuntu/dists/lucid/partner/source/)

To correct this open your sources list for editing by hitting Alt-F2 and typing:
```
gksudo gedit /etc/apt/sources.list
```then do a find-and-replace swapping the word "luzid" for "lucid"


aah! thats great observation man . one letter changed everything here .

---

### Post by newb85 on 2012-11-15
Indeed.  "Luzid Lynx" might sound cooler, but it seems less functional.  ;)

---

### Post by andrew.46 on 2012-11-15
A little aside of the main question here: I have always been a big fan of using the little applet that pings all servers to find the one closest. I attach a screenshot for those who do not know this valuable feature.

---

### Post by 12katia34 on 2012-11-16
> **Paqman said:**
> This could be a typo in your sources.list file. The URL above refers to "luzid", but the correct code name for that release of Ubuntu is "lucid".

This URL works: [http://archive.canonical.com/ubuntu/dists/lucid/partner/source/](http://archive.canonical.com/ubuntu/dists/lucid/partner/source/)

To correct this open your sources list for editing by hitting Alt-F2 and typing:
```
gksudo gedit /etc/apt/sources.list
```then do a find-and-replace swapping the word "luzid" for "lucid"

This indeed has solved my problem.
THANK YOU!

---

