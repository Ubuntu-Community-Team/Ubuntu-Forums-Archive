---
title: "Upgrade to Ubuntu 12.04"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Jeff.Smith on 2012-04-21
I cant seem to upgrade to 12.04. I have the checkbox checked to inform me of all ubgrades to Ubuntu and it isn't showing up in the upgrade manager. Is this some sort of bug?

---

### Post by tmaranets on 2012-04-21
12.04 isn't released fully yet. It should be coming out in a week or so. You can download the final beta if you want to.[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2]("https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2")

---

### Post by jerrrys on 2012-04-21
sudo do-release-upgrade -d

---

### Post by Jeff.Smith on 2012-04-21
> **tmaranets said:**
> 12.04 isn't released fully yet. It should be coming out in a week or so. You can download the final beta if you want to.[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2]("https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2")

Still, I should be able to upgrade to 12.04 according to the [Help Wiki]("https://help.ubuntu.com/community/PreciseUpgrades"). I've followed the directions and it's still not showing up. Am I missing something?

---

### Post by critin on 2012-04-21
> **Jeff.Smith said:**
>     Still, I should be able to upgrade to 12.04 according to the [Help Wiki]("https://help.ubuntu.com/community/PreciseUpgrades"). I've followed the directions and it's still not showing up. Am I missing something?        

Are you running 11.10 or 10.04?
The upgrade option won't become visible on the update page until the version is released, I believe.

---

### Post by kansasnoob on 2012-04-21
Someone posted the wiki info early :redface:

If you absolutely can't wait open the terminal and run:

```
update-manager -d -c
```

**NO sudo needed!**

But if things blow up don't complain ;)

---

### Post by Jeff.Smith on 2012-04-21
> **jerrrys said:**
> sudo do-release-upgrade -d

That did it. Still doesn't show up in the upgrade manager, don't know if that is some sort of bug or what. Thanks.

---

### Post by jerrrys on 2012-04-21
I removed update-manager and replaced it with Synaptic Package Manager

sudo apt-get install synaptic

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9)

---

### Post by critin on 2012-04-21
> **jerrrys said:**
> I removed update-manager and replaced it with Synaptic Package Manager

sudo apt-get install synaptic

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9)


Why?

---

### Post by Frogs Hair on 2012-04-21
> **Jeff.Smith said:**
> That did it. Still doesn't show up in the upgrade manager, don't know if that is some sort of bug or what. Thanks.

Your user info says 11.04 , in that case you would only be able to upgrade to 11.10. That option should have been offered in October.

---

### Post by jerrrys on 2012-04-21
> **critin said:**
> Why?

How many post do you see about broken update-manager vs synaptic package manager :)

---

### Post by Jeff.Smith on 2012-04-21
> **Frogs Hair said:**
> Your user info says 11.04 , in that case you would only be able to upgrade to 11.10. That option should have been offered in October.


Yeah, I noticed my info indicating that I am still in 11.04. However it is wrong. Regrettably I'm not sure how to change it. I'm downloading 12.04 right now though.

---

### Post by jerrrys on 2012-04-21
> **Frogs Hair said:**
> Your user info says 11.04 , in that case you would only be able to upgrade to 11.10. That option should have been offered in October.

If thats the case do

sudo do-release-upgrade

---

### Post by Jeff.Smith on 2012-04-21
> **jerrrys said:**
> How many post do you see about broken update-manager vs synaptic package manager :)

I'll keep that in mind. Thanks for your help.

---

### Post by critin on 2012-04-21
> **jerrrys said:**
> How many post do you see about broken update-manager vs synaptic package manager :)

In this case it wasn't update manager error.  ;)

---

### Post by jerome1232 on 2012-04-21
> **jerrrys said:**
> How many post do you see about broken update-manager vs synaptic package manager :)

:roll:

Before or after they removed it from the default install?

That's kind of like saying Enlightenment is a better DE because I see more people here with Unity problems than I do with Enlightenment problems posting in the Ubuntu forums.

---

### Post by jerrrys on 2012-04-22
> **critin said:**
> In this case it wasn't update manager error.  ;)

> **jerome1232 said:**
> :roll:

Before or after they removed it from the default install?

That's kind of like saying Enlightenment is a better DE because I see more people here with Unity problems than I do with Enlightenment problems posting in the Ubuntu forums.

the question was **WHY** ;) and no jerome its not like saying that at all since thats what you said, not I :P

Edit: almost forgot, I removed the software center too :)

---

### Post by critin on 2012-04-22
> **jerrrys said:**
> the question was **WHY** ;) and no jerome its not like saying that at all since thats what you said, not I :P

Edit: almost forgot, I removed the software center too :)


:p  I won't even ask why again, but I'd sure like to know.  I like pictures and info explaining what I'm looking at.  lol

---

