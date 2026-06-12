---
title: "Deleting &quot;Extract To...&quot; path in ARK?"
date: 2020-05-31
forum: New to Ubuntu
---

### Post by Butthead on 2020-05-31
Not a life or death question, but does anyone on the forum here know how to delete an unwanted "Extract To..." path in ARK?  I looked all over in the ARK program, and can't figure out how it's done.  Thanks for any assistance concerning this!

---

### Post by mastablasta on 2020-06-01
perhaps in a hidden directory in home with settings for ARK ? just a guess.

---

### Post by Butthead on 2020-06-01
I guess that could be true...

Can't seem to find anything in any of the menus.  Even under "configure ARK" in the Settings menu where you think it would most sensibly be.

Anyway, thanks for the suggestion on where to start looking. ):P

---

### Post by mastablasta on 2020-06-02
another folder that could hold configurations:

/etc/config/

---

### Post by Butthead on 2020-06-02
> **mastablasta said:**
> another folder that could hold configurations:

/etc/config/

Hmm, maybe I'm stupid, but I don't even see a "config" sub-directory under /etc. :confused:

This is a strange Zareason assembled PC running Kubuntu 18.04.:?

Guess I'll have to "whereis" Ark and see what comes up. :sad:

Thanks for the help anyway. :guitar:

---

### Post by Butthead on 2020-06-02
Or just learn to live with a /home/petey/Documents/ folder under Ark. ](*,)

That'll teach me to be so obsessive.  :oops:

---

### Post by CatKiller on 2020-06-02
It's probably kept in ~/.config/arkrc.

---

### Post by Butthead on 2020-06-03
> **CatKiller said:**
> It's probably kept in ~/.config/arkrc.

Thank you very much, that was the fix. ):P

---

### Post by Butthead on 2020-06-05
> **mastablasta said:**
> perhaps in a hidden directory in home with settings for ARK ? just a guess.

Now for another stupid question that's been bothering me since then.  Why would they have hidden settings files for a program such as Ark anyway? :confused:

---

### Post by CatKiller on 2020-06-06
> **Butthead said:**
> Now for another stupid question that's been bothering me since then.  Why would they have hidden settings files for a program such as Ark anyway? :confused:

Why wouldn't they? 

Programs need to store user preferences *somewhere*, and plain text files are understood by pretty much everything ever. On the other hand, no one wants to have to scroll through a bajillion settings files when they're looking for a picture of their goldfish or whatever.

---

### Post by mastablasta on 2020-06-06
it's the same on Windows. you need to choose to view hidden files to see config.sys setup.ini and similar files.
as explained you don't need to always see them but when you do, they are there for you (hit "Left Alt + ." to see hidden files in Dolphin)

---

### Post by Butthead on 2020-06-06
> **CatKiller said:**
> Why wouldn't they? 

Programs need to store user preferences *somewhere*, and plain text files are understood by pretty much everything ever. On the other hand, no one wants to have to scroll through a bajillion settings files when they're looking for a picture of their goldfish or whatever.

But to make the config files actually "hidden" (i.e. where you have to add special characters such as "~" and "." just to be able to view them through the command line (or click on the "show hidden files" box in Dolphin just to see them) doesn't make that much sense to me.:confused:

I mean we're not talking about serious encryption software here where someone hacking it could spell trouble for someone, just your basic run of the mill compression/decompression programs. :rolleyes:

---

### Post by CatKiller on 2020-06-06
> **Butthead said:**
> But to make the config files actually "hidden" (i.e. where you have to add special characters such as "~" and "."

Files starting with a . being hidden started as a bug, but it was handy so it was kept.

> just to be able to view them through the command line

*ls -a* will show them on the command line, too, if you're interested.
> (or click on the "show hidden files" box in Dolphin just to see them) doesn't make that much sense to me.:confused:

There's *loads* of them. It defaults to not showing them because they're kind of annoying for normal usage. You can always tell it to show them and it will remember, and then after a while you'll get annoyed and turn them off again. I, personally, find that keeping them hidden and then using Ctrl-L to go to the location that I'm interested in (usually .steam, occasionally .config or .local) works best for me.

---

### Post by Butthead on 2020-06-07
> **CatKiller said:**
> Files starting with a . being hidden started as a bug, but it was handy so it was kept.

Hmm, handy in what way?  Computers being flung across the room? :-? 

> **CatKiller said:**
> *ls -a* will show them on the command line, too, if you're interested.

That's good to know. Thanks! :guitar:

> **CatKiller said:**
> There's *loads* of them. It defaults to not showing them because they're kind of annoying for normal usage. You can always tell it to show them and it will remember, and then after a while you'll get annoyed and turn them off again. I, personally, find that keeping them hidden and then using Ctrl-L to go to the location that I'm interested in (usually .steam, occasionally .config or .local) works best for me.

I probably just got to get used to Ubuntu again, spending too much time in Android (which can be a PITA trying to figure out how to accomplish things many times in there too).  As always, appreciate your fantastic help! =d>

---

### Post by mastablasta on 2020-06-08
> **Butthead said:**
> Hmm, handy in what way?  Computers being flung across the room? :-? 


i am not sure how far into Ubuntu or Kubuntu you are, but i have quite a few stuff installed now. and turning hidden files on shows me over 130 folders in /home. just a bunch of configurations and profiles i don't need to constantly see as well as folders i do use. turning that off reduced the amount of folders to 38. which is still plenty, but very manageable.

---

### Post by Butthead on 2020-06-08
> **mastablasta said:**
> i am not sure how far into Ubuntu or Kubuntu you are, but i have quite a few stuff installed now. and turning hidden files on shows me over 130 folders in /home. just a bunch of configurations and profiles i don't need to constantly see as well as folders i do use. turning that off reduced the amount of folders to 38. which is still plenty, but very manageable.

Well, I only show (since you made me curious) 36 hidden files in my /home directory, so I guess that makes me far from a power user. :eek: ;)

But yeah, I can see in your (and other Linux aficionados) case that having hidden files (especially 100s of them) makes a lot of sense. :guitar:

I still have issues with Ark configuration files being hidden though. :icon_frown:

---

### Post by CatKiller on 2020-06-08
> **Butthead said:**
> I still have issues with Ark configuration files being hidden though. :icon_frown:

Why should just that one be visible? 

The file itself *isn't* hidden, just the directory it's in.

---

### Post by Butthead on 2020-06-09
> **CatKiller said:**
> Why should just that one be visible? 

The file itself *isn't* hidden, just the directory it's in.

I'm old and stupid.  OS'es should be KISS.  Especially finding configuration files you might want to edit. :-o 

What's the bet that both HAL-9000 and Skynet were running K/Ubuntu?  Probably both went rogue when the person using them were looking for a configuration file hidden somewhere. :rolleyes: :mad:

---

### Post by Butthead on 2020-06-09
I'm just being crotchety here, I REALLY do like K/Ubuntu based variants. :P

I still don't see the need to put a configuration file in a hidden directory though. :o

---

