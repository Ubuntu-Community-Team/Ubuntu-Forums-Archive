---
title: "Deleting a file/folder without being prompted &quot;if I'm sure?&quot;"
date: 2022-03-01
forum: New to Ubuntu
---

### Post by jmichaels29 on 2022-03-01
Ubnuntu 20.04 LTS using Unity environment.

As I have no programming knowledge, I posted this here. 
 
Curious if there is a way to right click on a file/folder and select "delete" without system asking "are you sure you want to permanently delete" said file/folder.

Perhaps someone could tell me what to type into terminal to change my environment so it would allow this.
 
Thanks in adavance...

---

### Post by mIk3_08 on 2022-03-01
> **jmichaels29 said:**
> Ubnuntu 20.04 LTS using Unity environment.
As I have no programming knowledge, I posted this here.
Curious if there is a way to right click on a file/folder and select "delete" without system asking "are you sure you want to permanently delete" said file/folder.
Perhaps someone could tell me what to type into terminal to change my environment so it would allow this.
Thanks in adavance...
In my Linux Ubuntu System, pressing the "Delete" button will go directly to trash bin without any pop up window notification to delete the file/folder or whatsoever. And also I can do a right click and "Move to Trash " without any pop up window notification to delete the item but by pressing the shift + delete button will do the pop up window delete notification asking me to permanently delete the item. so good luck and cheers.

---

### Post by uninvolved on 2022-03-01
I haven't played with Unity in a while, but memory says it used "Nautilus" 

In your preferences, do you have it set to automatically delete stuff instead of it moving it to the trash?

[IMG]https://i.imgur.com/m7LAfIo.png[/IMG]

A quick test says that I get a delete confirmation when

---

### Post by jmichaels29 on 2022-03-01
Hmmm,

I need to figure out how to find this type of general settings in Unity....

---

### Post by mIk3_08 on 2022-03-02
> **jmichaels29 said:**
> Hmmm,
I need to figure out how to find this type of general settings in Unity.... pressing the delete button on 20.04 LTS using unity environment will go directly to trash bin without any pop up window notification to delete the file/folder or whatsoever. good luck and cheers.

---

### Post by Impavidus on 2022-03-03
It's possible, I think.

I've done all my file management in the terminal since the first day I used a UNIX-like system. That was before I learned to program or used Ubuntu. The terminal doesn't ask for confirmation, unless you ask being asked (yes, that sounds silly, but may be useful when using aliases) or when the file is write-protected (and even then you won't be asked if you insist on not being asked). You can create custom actions in the file manager, which are just command you coukld run in a terminal too, so you can create a custom action that deletes a file without asking. Maybe there's a more direct way.

---

### Post by vanadium on 2022-03-05
IT is a setting of the file manager, which indeed used to be Nautilus in Unity. Even if it would be Nemo, you will find the option in the preferences.

---

### Post by QIII on 2022-03-05
The technical manner of accomplishing your wish aside, an important consideration is whether you would like such a default behavior to be removed.

I have been at this computer thing for 45 years.  I can't tell you how many times I have said "Oops!" (well, I've used saltier terms) after having disarmed such warnings.  I leave them all on now.

Bearing in mind that consideration, you are getting good advice.

---

### Post by DuckHook on 2022-03-05
> **Impavidus said:**
> It's possible, I think.

I've done all my file management in the terminal since the first day I used a UNIX-like system. That was before I learned to program or used Ubuntu. The terminal doesn't ask for confirmation, unless you ask being asked (yes, that sounds silly, but may be useful when using aliases) or when the file is write-protected (and even then you won't be asked if you insist on not being asked). You can create custom actions in the file manager, which are just command you coukld run in a terminal too, so you can create a custom action that deletes a file without asking. Maybe there's a more direct way.

> **QIII said:**
> The technical manner of accomplishing your wish aside, an important consideration is whether you would like such a default behavior to be removed.

I have been at this computer thing for 45 years.  I can't tell you how many times I have said "Oops!" (well, I've used saltier terms) after having disarmed such warnings.  I leave them all on now.

Bearing in mind that consideration, you are getting good advice.
In fact, I've turned ***ON*** confirmation so that I don't do this sort of thing without a chance at sober second thought:```
alias rm='rm -I'
```

I too have deleted important stuff with that saltier version of "Oops". I now safeguard against my own worst enemy (me) every chance I get.

---

