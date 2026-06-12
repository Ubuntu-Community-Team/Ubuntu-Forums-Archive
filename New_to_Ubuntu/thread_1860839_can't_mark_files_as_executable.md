---
title: "can't mark files as executable"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by spikeyseth on 2011-10-15
I've dual booted Windows vista (shock horror) and Ubuntu 11.10 (yay!) and im trying to access some of my files that i used in vista, mainly my steam games, using wine, but i cant mark the steam.exe as executable so i cant open it with wine. help?
EDIT: i would also like to add that i can see the check box, i can click it, but after checking the box it immediately unchecks it

---

### Post by spikeyseth on 2011-10-15
also, im a bit new at this, how would i install steam to my ubuntu partition using wine? when i try to do that, it defaults to installing to the windows C:\ root, and i dont know how to get it to install to my home folder :(

---

### Post by westie457 on 2011-10-15
Hello and if nobody has already said it. Welcome to the Forum.

Have not used Wine for a while so any advice is going to be a bit sketchy.

Wine is in your /Home folder where you installed it. The C:\ drive is a folder also in Home and is following Windows naming conventions to remind users they are using a type of Windows environment.

To install things into Wine if I remember rightly you start Wine then go to Add/Remove. In that dialogue box navigate to the .EXE you want to use and double-click on it.

I also suggest that you check _[here]("http://appdb.winehq.org/")_ and also _[here]("http://www.wine-reviews.net/")_ for more info on what will run and under what version of Wine.

Hope this helps and Happy Ubuntuing.

---

### Post by spikeyseth on 2011-10-15
ahh! i get it now! thanks :)

---

### Post by Morbius1 on 2011-10-15
> I've dual booted Windows vista (shock horror) and Ubuntu 11.10 (yay!)  and im trying to access some of my files that i used in vista, mainly my  steam games, using wine, but i cant mark the steam.exe as executable so  i cant open it with wine. help?
EDIT: i would also like to add that i can see the check box, i can click  it, but after checking the box it immediately unchecks itYou cannot change Linux permissions on a Windows filesystem because a Windows filesystem has no Linux permissions bits to change.

Luckily, Wine doesn't care or can even determine if an exe file has a Linux executable bit set. That error message you receive isn't coming from Wine it's coming from something called cautious-launcher.

To fix this fix the file association:

Right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine

In the "Open With" tab mark the "wine"[COLOR=Black] [COLOR=Blue]**you added**[/COLOR] [/COLOR]as   the default ( from the Wine that's already selected) and every time  you run an exe it should select the wine without the cautious  launcher  script.

---

### Post by sadaruwan12 on 2011-10-15
Yes it's file permission issue to enable the execute bit you need the file to be in a linux partition not on a windows one 'cos windows file system doesn't know any thing about execute bit permission so you could do 2 things.

1. You could copy the file over to a linux partition and enable the execute bit.

2. Do as @Morbius1 tells you

---

### Post by spikeyseth on 2011-10-15
okay guys, thanks for the advice, will post back in a mo

---

### Post by spikeyseth on 2011-10-15
hmm, i cant find the "use a custom command" you specified, can i get a screenshot or somthing?

---

### Post by Morbius1 on 2011-10-15
A thousand apologies. I didn't see that you were running 11.10. The functionality for a user to easily create a custom file association has been removed in 11.10 probably because it was so easy to do.

When I have time I will see if there's an easy way in 11.10 but quite frankly I can't stand the UI of 11.10 so I try to avoide it as much as possile. In the mean time do what sadaruwan12 suggested or do it this way:

Open up a Terminal and type:
```
wine "path/to/exe/file"
```

---

### Post by nisargshah on 2012-06-12
> **sadaruwan12 said:**
> Yes it's file permission issue to enable the execute bit you need the file to be in a linux partition not on a windows one 'cos windows file system doesn't know any thing about execute bit permission.

You could copy the file over to a linux partition and enable the execute bit.

Gosh darn this was the answer I was looking for since months. Thanks a lot IT WORKED on my 11.10!

---

