---
title: "firefox is slow as bananas..."
date: 2008-11-08
forum: New to Ubuntu
---

### Post by fignig on 2008-11-08
i dont' know why but when i upgraded to 8.10, everything is slower. especially firefox, it's slow as shiz. anyone know anything to alleviate this problem?

---

### Post by DrDagostino1 on 2008-11-08
I recently upgraded to 8.10 also but didn't like it because everything was too glitchy and buggy. I also had the problem of a few applications being very slow. I downgradded(reinstalled) to Hardy again and everything was fixed! I think the problem is 8.10 and I am going to wait a little while to upgrade again so that some of the bugs get fixed. There might also be another fix for this but I can't remember it. You had to delete some file and firefox would get faster but I don't know now.

---

### Post by metallicamike on 2008-11-08
i think it was cert8.db in ur profile folder

---

### Post by fignig on 2008-11-08
> **DrDagostino1 said:**
> I recently upgraded to 8.10 also but didn't like it because everything was too glitchy and buggy. I also had the problem of a few applications being very slow. I downgradded(reinstalled) to Hardy again and everything was fixed! I think the problem is 8.10 and I am going to wait a little while to upgrade again so that some of the bugs get fixed. There might also be another fix for this but I can't remember it. You had to delete some file and firefox would get faster but I don't know now.

is there a way of reinstalling w/o losing the files i currently have now? b/c i don't want to have to d/l everything again. b/c i don't have another way to save them.

---

### Post by fignig on 2008-11-08
> **metallicamike said:**
> i think it was cert8.db in ur profile folder

so i'm just suppose to delete this file?

---

### Post by DrDagostino1 on 2008-11-09
There is no actual way to downgrade without losing everything. The way I did it was to backup my home user folder and reinstall, wiping out everything. If you do this all your data will be lost except your the stuff in your home folder. That means all your settings and programs will be lost.

I wouldn't recommend this method if you have a lot of stuff installed or if you don't have a few hours to manually reinstall all your programs.

But if you really can't live with firefox being that slow, then you could reinstall. But if you can live with it for a little while, there may be an update that fixes it. Also, someone else here might know of a better way.

All I know is that when I did this EVERYTHING seemed to run better and faster. All the bugs and glitches I had went away.

---

### Post by fignig on 2008-11-09
> **DrDagostino1 said:**
> There is no actual way to downgrade without losing everything. The way I did it was to backup my home user folder and reinstall, wiping out everything. If you do this all your data will be lost except your the stuff in your home folder. That means all your settings and programs will be lost.

I wouldn't recommend this method if you have a lot of stuff installed or if you don't have a few hours to manually reinstall all your programs.

But if you really can't live with firefox being that slow, then you could reinstall. But if you can live with it for a little while, there may be an update that fixes it. Also, someone else here might know of a better way.

All I know is that when I did this EVERYTHING seemed to run better and faster. All the bugs and glitches I had went away.

well the reason i upgraded was to fix the flash problem which hasn't been fixed yet. and it seems like it won't be fixed any time soon. but i do have a lot of programs, and files that go over 50gb. it's gonna be hard to save everything, and i don't think that's possible w/o having an external hd which i don't have. so i guess i'm gonna have to live w/ these problems, and it makes me sad.

---

### Post by DrDagostino1 on 2008-11-09
That is a lot of stuff and I'm guessing in about a month there should be enough fixes out to run smoothly.
Also, what is wrong with your flash player? I had a problem with my flash player as well and found that installing the lastest flash player fixed it.

---

### Post by Crafty Kisses on 2008-11-09
It could be a RAM issue, while Firefox is running, run the following command in the Terminal:
```
top
```
Then you can see how much resources Firefox is taking up.

---

### Post by kansasnoob on 2008-11-09
I had the same problem just today. What I had to do was delete the .mozilla folder in Home > Show Hidden, **but you'll lose everything in Firefox doing that!**

The only thing I wanted to keep was my bookmarks so I found the .mozilla by going to Home > View > Show Hidden > .mozilla > firefox > 8random#.default > places.sqlite. Then I right clicked the places.sqlite and "pasted" it to desktop so I could replace it after removing .mozilla and restarting Firefox which then creates a new .mozilla. Yes that means reconfiguring everything in Firefox!

Note: 8random#.default is just that 8 random figures followed by .default. The 8 random figures are always different!

I must be out for a while, maybe a few hours, and this may also dump your Thunderbird mail if that's what you use, not sure, so you should look into that!

I also had to reinstall flash and restricted extras by:

```
sudo apt-get --purge remove adobe-flashplugin
```

Then:

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

Then restarting Firefox by going to File > Quit, and then starting Firefox.

If any of this is less than perfectly clear please wait for additional help!

---

### Post by fignig on 2008-11-09
> **kansasnoob said:**
> I had the same problem just today. What I had to do was delete the .mozilla folder in Home > Show Hidden, **but you'll lose everything in Firefox doing that!**

The only thing I wanted to keep was my bookmarks so I found the .mozilla by going to Home > View > Show Hidden > .mozilla > firefox > 8random#.default > places.sqlite. Then I right clicked the places.sqlite and "pasted" it to desktop so I could replace it after removing .mozilla and restarting Firefox which then creates a new .mozilla. Yes that means reconfiguring everything in Firefox!

Note: 8random#.default is just that 8 random figures followed by .default. The 8 random figures are always different!

I must be out for a while, maybe a few hours, and this may also dump your Thunderbird mail if that's what you use, not sure, so you should look into that!

I also had to reinstall flash and restricted extras by:

```
sudo apt-get --purge remove adobe-flashplugin
```

Then:

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

Then restarting Firefox by going to File > Quit, and then starting Firefox.

If any of this is less than perfectly clear please wait for additional help!

lose everything u mean like all of my bookmarks, and everything i've saved? and all of my private data? anyway to save any of these?

---

### Post by fignig on 2008-11-09
> **Codename said:**
> It could be a RAM issue, while Firefox is running, run the following command in the Terminal:
```
top
```
Then you can see how much resources Firefox is taking up.

firefox is  using like 1% of my cpu and like 13% of my memory. this surely shouldn't be bogging down firefox like this. b/c it's running noticeably slower than usually. aka, slower than 8.04

---

### Post by fignig on 2008-11-09
> **kansasnoob said:**
> I had the same problem just today. What I had to do was delete the .mozilla folder in Home > Show Hidden, **but you'll lose everything in Firefox doing that!**

The only thing I wanted to keep was my bookmarks so I found the .mozilla by going to Home > View > Show Hidden > .mozilla > firefox > 8random#.default > places.sqlite. Then I right clicked the places.sqlite and "pasted" it to desktop so I could replace it after removing .mozilla and restarting Firefox which then creates a new .mozilla. Yes that means reconfiguring everything in Firefox!

Note: 8random#.default is just that 8 random figures followed by .default. The 8 random figures are always different!

I must be out for a while, maybe a few hours, and this may also dump your Thunderbird mail if that's what you use, not sure, so you should look into that!

I also had to reinstall flash and restricted extras by:

```
sudo apt-get --purge remove adobe-flashplugin
```

Then:

```
sudo apt-get install --reinstall ubuntu-restricted-extras
```

Then restarting Firefox by going to File > Quit, and then starting Firefox.

If any of this is less than perfectly clear please wait for additional help!

btw Home > View > Show Hidden > .mozilla > firefox > 8random#.default > places.sqlite. not sure where the .mozilla folder is. b/c after home, is my username folder.

---

### Post by metallicamike on 2008-11-10
hit control+h, or go into view and hit show hidden files, then youll see it

---

### Post by metallicamike on 2008-11-10
> **fignig said:**
> so i'm just suppose to delete this file?

u could, it didnt seem to screw anything up when i tried it myself....

---

### Post by fignig on 2008-11-11
> **metallicamike said:**
> u could, it didnt seem to screw anything up when i tried it myself....

okay i'm gonna try this, wish me luck. i'll post back my results, and thanks if necessary

---

### Post by sdowney717 on 2008-11-11
try this
install the epiphany web browser.
It is a little faster than firefox anyway and you might notice a big speed improvement if firefox is acting weird.

I dont notice any issues with epiphany and flash works with it.

---

### Post by fignig on 2008-11-12
> **sdowney717 said:**
> try this
install the epiphany web browser.
It is a little faster than firefox anyway and you might notice a big speed improvement if firefox is acting weird.

I dont notice any issues with epiphany and flash works with it.

wtf i'm reporting you, wtf was that shiz? it just opened up this game screen....is this some kinda messed up joke?

---

### Post by sdowney717 on 2008-11-13
change your attitude or you wont get as far in life as you might have.

[http://projects.gnome.org/epiphany/](http://projects.gnome.org/epiphany/)

[http://www.freesoftwaremagazine.com/books/ubuntu_applications/epiphany](http://www.freesoftwaremagazine.com/books/ubuntu_applications/epiphany)

---

### Post by mkvnmtr on 2008-11-13
He said Epiphany Browser. Not the game. You installed the wrong thing. Look in Add/remove under internet. He is right the browser is much faster than Firefox on some things.

---

### Post by beercz on 2008-11-13
> **fignig said:**
> i dont' know why but when i upgraded to 8.10, everything is slower. especially firefox, it's slow as shiz. anyone know anything to alleviate this problem?
OK, try this:

Close Firefox.
[B]
Backup your /home/<username>/.mozilla directory!![/B]

Click Places->Search for files

Browse for the above .mozilla directory (right click on the dialog box and turn on the 'Show Hidden Files' checkbox).

In the 'Name contains' box, enter:

places.sqlite

And then click the Find button.

Move all found files to the wastebasket.

Close the find utility and restart firefox.

Good luck.

---

### Post by tipiglen on 2008-11-16
> Close Firefox.

Backup your /home/<username>/.mozilla directory!!
...
Move all found files to the wastebasket.

Close the find utility and restart firefox.

Thanks for that.  I hope it solves my serious slowdown and manic i/o problem.. 
[http://ubuntuforums.org/showthread.php?t=978842](http://ubuntuforums.org/showthread.php?t=978842)

Anyway, I was frightened it might blow my extensive bookmarks away, but they're all there and there's a brand new places.sqlite file, but not the 250Mbyte monster that's quietly sitting in the backup...History now has today and 'older than 6 days', but no yesterday....

Just what is in "places" anyway?

Thanks again, and specially if it solves the slowdowns..

Patient ed

---

