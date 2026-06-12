---
title: "copying file"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Matt26 on 2008-06-11
i am trying to copy a file from one directory to another.

the file is called firefox-3.0-gnome-support and it is located in the usr/share/doc directory

i want to copy it to the home/matthew/Documents directory

how do i do this?

thanks.

---

### Post by _sphinx_ on 2008-06-11
```
cp /usr/share/doc/<filename> /home/matthew/Documents/
```

This should do it.

---

### Post by pedro_orange on 2008-06-11
```
mv /usr/share/doc/firefox-3.0-gnome-support ~/matthew/Documents/
```

~ == home

---

### Post by saj0577 on 2008-06-11
> **pedro_orange said:**
> mv /usr/share/doc/firefox-3.0-gnome-support ~/matthew/Documents/

For that command I think you would need sudo.
He wants to copy not move anyway.


Saj

---

### Post by _sphinx_ on 2008-06-11
I think you won't be able to use "mv".

---

### Post by saj0577 on 2008-06-11
> **_sphinx_ said:**
> I think you won't be able to use "mv".

Nope, you would not without sudo. But there is no need to move it so just use copy. :)

Saj

---

### Post by andrewski on 2008-06-11
> **Matt26 said:**
> i am trying to copy a file from one directory to another.

the file is called firefox-3.0-gnome-support and it is located in the usr/share/doc directory

i want to copy it to the home/matthew/Documents directory
If your intention is to save this for reading later, might I suggest creating a symlink/shortcut to that folder? You can do that one of two ways:

[LIST=1]
[*]```
ln -s /usr/share/doc/firefox-3.0-gnome-support ~/Documents/Firefox\ Documentation
```
[*]In Nautilus, browse to /usr/share/doc, right-click on firefox-3.0-gnome-support and select "Make link".
[/LIST]
Also, you could just bookmark Mozilla's website in Firefox or Epiphany for web browsing. ;) But I assume you've thought of this.

Hope this helps!

---

### Post by Matt26 on 2008-06-11
thanks for the suggestions- i was planning to do a copy initially, but a move would probably be the better way to do it since i plan on deleting the file from it's source when i'm done anyways- would the mv command that was suggested be the best way to do this?  thanks.

---

### Post by durand on 2008-06-11
> **pedro_orange said:**
> ```
mv /usr/share/doc/firefox-3.0-gnome-support ~/matthew/Documents/
```

~ == home

Oh and thats not right either. Even if you wanted to mv, ~ goes to /home/username, not just home as you said so you would just need:

```
 mv /usr/share/doc/firefox-3.0-gnome-support ~/Documents/
```

---

### Post by durand on 2008-06-11
> **Matt26 said:**
> thanks for the suggestions- i was planning to do a copy initially, but a move would probably be the better way to do it since i plan on deleting the file from it's source when i'm done anyways- would the mv command that was suggested be the best way to do this?  thanks.

Uhh, why? It would be reinstalled when firefox is updated anyway...

---

### Post by powerpleb on 2008-06-11
Or as I learned today; if you are in the destination directory:
```
user@host:~/Documents$ sudo mv /path/file .
```

---

### Post by pedro_orange on 2008-06-11
> **durand said:**
> Oh and thats not right either. Even if you wanted to mv, ~ goes to /home/username

Thanks! I thought ~ just meant home.
Doing an echo ~ proved you correct!

```
pedro@pedro-laptop:~$ echo ~
/home/pedro
pedro@pedro-laptop:~$ 

```

---

### Post by andrewski on 2008-06-11
> **durand said:**
> Uhh, why? It would be reinstalled when firefox is updated anyway...
Yes, I question your intentions here also. Generally, touching any file outside of /home is a bad idea. Editing files in /etc is to be done carefully, but doing pretty much anything in /usr is unnecessary, since all of those files are managed by the package system.

What's your goal?

---

### Post by durand on 2008-06-11
> **pedro_orange said:**
> Thanks! I thought ~ just meant home.
Doing an echo ~ proved you correct!

```
pedro@pedro-laptop:~$ echo ~
/home/pedro
pedro@pedro-laptop:~$ 

```

Hmm..so I guess ~ is a bash alias, cool [IMG]http://www.durand.zephyrhosting.net/dump/smileys/glasses-cool.png[/IMG]

[QUOTE=powerpleb]Or as I learned today; if you are in the destination directory:
Code:
user@host:~/Documents$ sudo mv /path/file .
[/QUOTE] Thanks for sharing that! I've always wondered how you referenced the current directory.

---

### Post by _sphinx_ on 2008-06-11
> **durand said:**
> Hmm..so I guess ~ is a bash alias, cool [IMG]http://www.durand.zephyrhosting.net/dump/smileys/glasses-cool.png[/IMG]

 Thanks for sharing that! I've always wondered how you referenced the current directory.
I want to add something, It may not be related to the post. [dot] refers to the current directory and [dot][dot] refers to the parent directory. That's why we do cd [dot][dot] to go to the uåer directory and with cd [dot] we remain in our present directory.

---

### Post by durand on 2008-06-11
Interesting...

---

### Post by Matt26 on 2008-06-11
> **andrewski said:**
> Yes, I question your intentions here also. Generally, touching any file outside of /home is a bad idea. Editing files in /etc is to be done carefully, but doing pretty much anything in /usr is unnecessary, since all of those files are managed by the package system.

What's your goal?

first, i completely understand the risk(s) associated with touching files that are outside the home directory- i'm aware of the potential impact that certain actions can have on the system's performance/stability.

second, my goal here is a long-winded explanation at best (see the thread below). i figured instead of going through the process of explanation (which i really didn't feel was necessary) i would just ask the question (considering it's a simple one, regardless of the situation) and hopefully figure out what to do- although i know some users may not understand what they are working with and how it affects other things within the system, i don't believe it is necessary to automatically send out a disclaimer to challenge people's actions with their own computers (in applicable cases) and make them aware of what they are potentially doing to their system (when in fact they may be fully aware of such things).

i only mention this because it seems to me that any time i post to the forum looking for assistance with an issue (which has been a great help thus far) that has any bearing on system files/settings, it is flagged as 'do not touch' and 'you must know this first'- i understand the intent here, but to me it seems to be a bit clouded in assumption and possibly unnecessary guidance.

(and as i write this i realize that i have this thread posted in the Absolute Beginner Talk group which i imagine implies my novice nature- true to a degree- but this group always seems to be the most responsive and helpful one for me!)

thanks for everyones suggestions, it is very much appreciated.

[http://ubuntuforums.org/showthread.php?t=825170](http://ubuntuforums.org/showthread.php?t=825170)

---

### Post by andrewski on 2008-06-11
> **Matt26 said:**
> (and as i write this i realize that i have this thread posted in the Absolute Beginner Talk group which i imagine implies my novice nature- true to a degree- but this group always seems to be the most responsive and helpful one for me!)
Sounds like you answered your own question; I definitely spoke that way based on this forum. I guess I should've looked at your post count, sorry! :p

---

