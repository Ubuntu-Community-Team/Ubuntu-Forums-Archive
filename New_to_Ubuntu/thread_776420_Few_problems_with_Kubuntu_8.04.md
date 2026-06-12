---
title: "Few problems with Kubuntu 8.04"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by browny254 on 2008-04-30
Hi, I just installed Kubuntu 8.04 KDE 4 version and I have a few small problems/questions that Im not sure how to get around.

These are probably pretty simple things, but stuff I want to change to get things set up how I like it.

1 - In the System Setting I cant work out how to edit options as an admin. In 7.10 I thought there was a button down the bottom but I dont have it there now so I cant do stuff like change the clock settings.

2 - How do I move the widgets in the main panel? I like having this down the left side of my screen but all the widgets need rearranging. In 7.10 there was an unlock option which allowed you to do it, now Im not sure how.

3 - The volume control wheel on my laptop doesnt work, this is probably due to my laptop, a Toshiba A200 - it had lots of problems getting sound to work at all in 7.10 so even having sound now is a big improvement, but if there is a simple way to get this working it would be nice.

4 - Similar problem as above in that it could be due to my laptop, but I have no horizontal scroll on my touchpad.

5 - Does Compiz work out of the box? From what I saw on the release info it looked like it did. I didnt have it on 7.10 so I havent used it before so it may be there and I just dont know how to use it yet...any advice?

I guess thats all for the moment, Ill probably find a few more things after using it more than half an hour...thanks for any help you can give.

---

### Post by doorknob60 on 2008-04-30
The main problem your having is that you're using KDE 4.0 (KDE devs don't want to call it KDE4 until 4.1, and I agree), which is still super buggy (a lot worse experiences for me than you have), but KDE 3 version is very stable, and Compiz works out of the box in it, and you can edit system settings as admin and all that good stuff. KDE 4.0 has no official support right now, and TBH, it's just not ready for everyday usage yet. If I were you, I'd just scrap KDE 4.0 for now until it gets more stable. Try this if you want to:

(To install stable KDE 3.5)
```
sudo aptitude install kubuntu-desktop
```

And if you want to remove KDE 4, use this:

```
sudo apt-get purge kdelibs5 && sudo apt-get autoremove
```

Sorry if you really want to keep KDE 4, but you probably won't get it working stable until a later release.

---

### Post by iSplicer on 2008-04-30
I agree. KDE4 is still very much in development stage and is very buggy and unstable, you will be hard pressed to get that stuff working properly. I suggest you reboot into recovery mode and install kde 3.5

---

### Post by browny254 on 2008-04-30
hmm ok, I didnt realise KDE 4 is that buggy. I would have thought those things i mentioned would have worked in it thought because they are pretty basic...I was expecting the underneath to be not quite right and hoped this wouldnt affect me much.

heres to another day of downloading...

---

### Post by Zralou on 2008-04-30
Kubuntu 8.04 (Hardy Heron) is available for download in two versions at the moment.  The standard Kubuntu with KDE 3.5, or the experimental KDE 4.  Depending on which one you downloaded, will determine which version of KDE you have.

Edit :::Sorry!!, just noticed you said in your original post that you had downloaded KDE 4, my mistake:::

Sara Lou

---

