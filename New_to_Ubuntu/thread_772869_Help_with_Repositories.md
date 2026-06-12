---
title: "Help with Repositories"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Kurosaki_Ichigo on 2008-04-28
Hi, Just a few questions on Ubuntu's repositories.

First In my package manager when i do a search for certain things such as Beryl, Automatix and fluxbox, I dont get any results!
I'm gussing this is because the default repository is not a very good one or no up to date.

So I would like to know which repository I should add (please give the address)

Second, every time a new version of Ubuntu comes out is there a new repository for each one that comes out?
If so, please could I have the address for the feisty fawn repository.

grateful for any help!

---

### Post by LaRoza on 2008-04-28
> **Kurosaki_Ichigo said:**
> Hi, Just a few questions on Ubuntu's repositories.

First In my package manager when i do a search for certain things such as Beryl, Automatix and fluxbox, I dont get any results!
I'm gussing this is because the default repository is not a very good one or no up to date.

So I would like to know which repository I should add (please give the address)

Second, every time a new version of Ubuntu comes out is there a new repository for each one that comes out?
If so, please could I have the address for the feisty fawn repository.

grateful for any help!
Beryl and Automatix are not active projects. Use the package manager and use Compiz-fusion.

---

### Post by ziggyw00t on 2008-04-28
Most of the repos you will ever need are already in your sources.list file. the easiest way to make sure you have all the repos being used is to go to -

System->Administration->Software Sources->enable proprietary and restricted

But like it was stated above, beryl and automatix are not active projects. C

---

### Post by Kurosaki_Ichigo on 2008-04-28
I am using package manager and I also recall finding automatix on the package manager (with which repository i do not know)

also for instance when i tried to get fluxbox I read somewhere that I need to add the ubuntu universe repository.

---

### Post by LaRoza on 2008-04-28
> **Kurosaki_Ichigo said:**
> I am using package manager and I also recall finding automatix on the package manager (with which repository i do not know)

also for instance when i tried to get fluxbox I read somewhere that I need to add the ubuntu universe repository.

Then add it.

Go to Applications->Add Remove and change it to "All available applications" and reload the package list.

---

### Post by Kurosaki_Ichigo on 2008-04-28
OK all of the repositories are ticked so why cant I at least find fluxbox.
The site to download it says use apt get but even that says that fluxbox does not exist when the website says it does

---

### Post by LaRoza on 2008-04-28
> **Kurosaki_Ichigo said:**
> OK all of the repositories are ticked so why cant I at least find fluxbox.
The site to download it says use apt get but even that says that fluxbox does not exist when the website says it does

Run:

```

sudo apt-get update && sudo aptitude install fluxbox

```

---

