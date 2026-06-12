---
title: "[SOLVED] Trash basket will not empty. What to do???"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by suomalainen on 2008-11-28
Ubunteros,

I got trash in my trash bin which will not delete/empty no matter what I do.... See attached picture.

Any suggestions?

Could this be a bug?

---

### Post by hyper_ch on 2008-11-28
what does the error message on that picture return?

---

### Post by suomalainen on 2008-11-28
Do you mean this? See attached pic please....

---

### Post by hyper_ch on 2008-11-28
Why don't you tell me what error it reports?

---

### Post by suomalainen on 2008-11-28
I did. I'm showing you what I'm seeing...

---

### Post by hyper_ch on 2008-11-28
You just want to tell me a solution to your problem - but you just seem to refuse to try and comprehend what is wrong.

---

### Post by suomalainen on 2008-11-28
Huh? I don't tell anyone in this forum I have a solution to my problem.... I just provide factual evidence (screen snaphots) as to what I see and ask others for comment...

Why you have problem with that?

---

### Post by iKonaK on 2008-11-28
Try drag and drop to desktop and then change parmissions or go to "/home/user/.local/share/Trash/files" and change the permissions from there. :)

---

### Post by collinp on 2008-11-28
If you need to get your trash clean, now, run this:
```
rm -rf ~/.local/share/Trash/files
```That should remove everything in the Trash directory... should. If it is owned by someone else (ex. root) then it wont be able to. In that case, you will need to run this:
```
sudo rm -rf ~/.local/share/Trash/files
```
That will clear anything out of the Trash, regardless of whom it is owned by.

---

### Post by iKonaK on 2008-11-28
> **Hellow said:**
> If you need to get your trash clean, now, run this:
```
rm -rf ~/.local/share/Trash/files
```That should remove everything in the Trash directory... should. If it is owned by someone else (ex. root) then it wont be able to.

[LIST]
[*]only the user can delete a file to his trash folder, if it would been root it would had his own trash.
[*]just in case if suomalainen wants to try the command, shoud also wana try putting sudo before rm, it wouldn't matter what permisions were :)
[/LIST]
@[Hellow]("http://ubuntuforums.org/member.php?u=440413") i haven't noticed you edit :)

---

### Post by suomalainen on 2008-11-28
iKonaK & Hellow,

THANK YOU VERY MUCH FOR UNDERSTANDING MY POST STRAIGHT OUT THE GATE!!!

I gave:

sudo rm -rf ~/.local/share/Trash/files

a try first and that deleted everything as I wanted... Apparently, there was a .bin file that had certain levels of permission set that no matter what I did nothing would empty my waste basket...

But the code worked.

I work a lot between between windows and Ubuntu files so I imagine I will run into this again. But having Your code will save the day. Especially, when dealing with 1TB size data files.

Thanks Again!!!

P.S.
I sent you both Thank Yous too....

---

### Post by drs305 on 2008-11-28
suomalainen,

I just came upon this post. Trash has ways of appearing in strange places. I wrote something about trash bins that explains how to find and delete most of it:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

If you have your problem resolved would you please mark it Solved via the Thread Tools link near the top right of the original post. Thank you.

---

### Post by suomalainen on 2008-11-28
Thanks DRS305!

---

