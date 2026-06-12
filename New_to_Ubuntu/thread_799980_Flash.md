---
title: "Flash"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Benjamin1992 on 2008-05-19
Hi everybody!

I'm new in this forum, and new with Linux. I've just installed the new version of Ubuntu, and I have a few problems.
I first couldn't see any (adobe, shockwave) flash video, and then I've installed a temporary Plug-in. I got a stupid Play-button with each video I tried to play, and the sound doesn't work. So I thought to install flash from the website of adobe, and the install was completed but nothing has changed. I was looking for the Plug-in, but I couldn't found it, and I couldn't remove any Plug-in (so I don't know it's possible).
I also don't know anymore which Plug-in it was.

I want you to ask if anybody knows the problem, and knows what I have to do.

Thanks!

Kind regards,
Benjamin

---

### Post by FuturePilot on 2008-05-19
That's probably Gnash that's giving you problems. Try uninstalling it
```
sudo apt-get remove --purge mozilla-plugin-gnash
```
Then install the Adobe Flash
```
sudo apt-get install flashplugin-nonfree
```

Then restart Firefox.

---

### Post by Benjamin1992 on 2008-05-19
I get the message that mozilla-plugin-gnash isn't installed, so I can't remove it :S
And the flash version that you give, is it non-free or is it just the name ?
Thanks for the quick response! 

greets,
Benjamin.
EDIT: is it possible that because I've the Dutch version of Ubuntu, the program has another name?

---

### Post by FuturePilot on 2008-05-19
Hmmm, maybe it's swfdec. Try
```
sudo apt-get remove --purge swfdec-mozilla
```

The nonfree just means that it's not open source.

---

### Post by Benjamin1992 on 2008-05-19
Man thank you!
The playbutton has disappeared, and the movie loads much faster (that was also a problem, the movies didn't play how they had to).
But the sound doesn't work yet. With other movies I play in firefox, the sound works (so that's not the problem), only with flash (I check it with youtube) the sound doesn't work. Do you know how I can solve this?

greets,
Benjamin
and thank you for your quick responses!!

---

### Post by SunnyRabbiera on 2008-05-19
alright I understand you got regular flash installed correct?
Are you using a AMD64 computer/kernel?

---

### Post by Benjamin1992 on 2008-05-19
Hi,

Yes, I've installed it, following the instructions of FuturePilot.
But I don't know the answer to your other question, how can I know that? :$

greets,
Benjamin and thanks!

---

### Post by SunnyRabbiera on 2008-05-19
you should get kernel information by using the system monitor, located under system under administration labeled as "system monitor"
you can find out information about your kernel in the first tab, it will also give you the name of your processor.

---

### Post by Benjamin1992 on 2008-05-19
This is what I saw:
**Ubuntu**
...
Kernel Linux 2.6.24-16-generic

---

### Post by SunnyRabbiera on 2008-05-19
alright so you are using the generic kernel then.
What browser are you using?

---

### Post by Benjamin1992 on 2008-05-19
Hm I forgot to mention that,sorry :)
Firefox 3 Beta 5 (standard on Ubuntu 8.04 :( )

---

### Post by SunnyRabbiera on 2008-05-19
> **Benjamin1992 said:**
> Hm I forgot to mention that,sorry :)
Firefox 3 Beta 5 (standard on Ubuntu 8.04 :( )

there might be your issue, firefox 3 is still beta so this might be one of your issues.
But if you need to I can give you instructions to install firefox 2, its easy enough to install.

---

### Post by Benjamin1992 on 2008-05-19
That would be nice :) thanks!

---

### Post by SunnyRabbiera on 2008-05-19
alright first do you have any bookmarks or anything you wish to save?
I suggest you save them as installing firefox 2 requires you removing the hidden mozilla directory.
If i remember right firefox 3 has a export option in it, I downgraded to firefox 2 myself so I am unsure about that bit...
I think the export option in firefox 3 is under bookmarks, with the organize bookmarks option.
there should be the exporter right there in plain view labeled as "import bookmarks" or something, and when you click it it will list to export bookmarks.

---

### Post by Benjamin1992 on 2008-05-19
Bookmarks are saved ...

---

### Post by SunnyRabbiera on 2008-05-19
alight.
First thing I want you to do is to open up synaptic, synaptic is an advanced package manager, and [this guide here]("http://monkeyblog.org/ubuntu/installing/") can give you the bases on how to use it.
Now this part is important, once you get synaptic up and running mark the firefox 3 package for complete removal and then mark the firefox 2 packages for installation.
that guide should give you the bases on how to use synaptic, its very easy to use.
after you install firefox 2 you will have to remove your hidden mozilla directory, open up your home directory and hit ctrl+h to unhide your hidden files and then send the mozilla folder to the trash bin.

---

### Post by billgoldberg on 2008-05-19
1) [http://linuxowns.wordpress.com/2008/04/29/hardy-heron-sound-problems/](http://linuxowns.wordpress.com/2008/04/29/hardy-heron-sound-problems/)

(mighty cause firefox to become unstable with flashcontent)

or 2)

[http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/](http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/)

---

### Post by Benjamin1992 on 2008-05-19
Thanks! Because of the comment of billgoldberg I did not have to delete firefox 3, and install firefox 2. The sound works great now.
But thanks for the instructions, maybe I can use it if I discover other problems with firefox 3!

greets,
Benjamin

---

