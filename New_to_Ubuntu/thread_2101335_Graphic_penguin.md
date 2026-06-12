---
title: "Graphic penguin"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by misswham on 2013-01-04
Good morning.  I just downloaded ubuntu 12.04 and I recently saw a video about it on youtube and on the desktop this person had a penguin walking over the bottom of the screen.  How was that done?  I also saw a kubuntu 12.04 video and I see that they have widgets available and it has a bouncing ball that u can start on the screen but i really liked that penguin walking.  How can we OR can we do that with ubuntu 12.04?

---

### Post by zombifier25 on 2013-01-04
Is xpenguins what you're looking for? It's in the repo.

---

### Post by misswham on 2013-01-04
Im sorry but I dont know what repos are?  Im familiar with synaptic and the terminal but not sure what the repos are?  If someone tells me where to find them and how to install, Im pretty sure I will be able to do it because I had ubuntu yrs ago, I just got lazy when i started using mint.  I have been seeing the word repos everywhere on here and Im not actually sure what they are.  Also the windows are too big and I have to go to another desktop to click next or accept.  How can i correct this?

---

### Post by zombifier25 on 2013-01-04
The repo (short for repository) is where all of Ubuntu's softwares are hosted, and when you use Synaptic or apt-get, you're browsing the repo. So simply:
```
sudo apt-get install xpenguins
```
or use Synaptic to install the package.

---

### Post by audiomick on 2013-01-04
The "repos" are the "repositories". That is where apt-get, synaptic, the software centre, the update manager et al go to get the packages that they administrate.

Here is some info on the subject:
[http://en.wikipedia.org/wiki/Software_repository]("http://en.wikipedia.org/wiki/Software_repository")

Open the software centre or synaptic and search for xpenguin.

---

### Post by audiomick on 2013-01-04
> **misswham said:**
>  Also the windows are too big and I have to go to another desktop to click next or accept.  How can i correct this?

I think you should start a new thread for this with an appropriate title. The title of this thread wont attract anyone who thinks they can help with that problem.

---

### Post by misswham on 2013-01-04
I just installed xpenguin but where do i find it, what name am i looking for?>

---

### Post by boregard on 2013-01-04
okay, you will have to open terminal and type in xpenguins.

---

### Post by misswham on 2013-01-05
thanks.  i did that and the little penguins started going all over the place,  is there a way to go to a menu and make it one and bigger?

---

### Post by zombifier25 on 2013-01-05
Launch it like this:
```
xpenguins -t Big\ Penguins -n 1
```

---

