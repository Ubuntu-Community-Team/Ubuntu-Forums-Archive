---
title: "*VLC Error when Installing and Playing"
date: 2017-08-13
forum: New to Ubuntu
---

### Post by lenchase1999 on 2017-08-13
Please, I keep having errors when playing video in VLC. Then I tried install VLC from terminal, and then I accidentally installed it also from Ubuntu store. I tried to delete it and tried to re-install it, but the result is that the video can not be played at all in VLC. Please help as soon as possible
[ATTACH=CONFIG]276388[/ATTACH][ATTACH=CONFIG]276389[/ATTACH]


Note: i just learned linux last month

---

### Post by ajgreeny on 2017-08-14
Can I get this right in my own mind; you have installed VLC from both the repositories and then from snap packages so probably have versions 2. and 3. installed; correct?

I have not yet botered with any snap packages but as I understand it, the two versions should be able to sit side by side without problems.
Is this a new OS installation or have you previously been able to use VLC siccessfully?

---

### Post by ClickXT on 2017-08-14
Hopefully I am understanding the OP correctly but...

I have had issues in the past with the snap package of VLC in the past (I won't even mess with snaps now due to it). 
I'd uninstall all VLC again and make sure you got any/all versions.
Then I'd try to install (the actual program) again from the Ubuntu Center. 

Do a complete search of your apps to make sure you got them all uninstalled before installing the new one.

---

### Post by sonicwind on 2017-08-14
I had problems months ago getting the Ubuntu Software Center version of VLC to work, so I tried the snap of it. It has worked fine for me. The command I used in terminal that works is:

```

sudo snap install &#8211;stable --classic vlc

```
I would uninstall all the other versons first although my understanding is the same as ajgreeny.

---

### Post by lenchase1999 on 2017-08-14
This started when I was playing a video, and then suddenly the video player changed to the default linux. Then  I checked, it turned out an error on VLC, and I tried to install it  again last week, but the result VLC can not even play any video. Today I tried to install it again, but even error and can not be installed

Here is the screenshoot : 
[https://1.bp.blogspot.com/-Jckk1VCTWiM/WZJE0d44x5I/AAAAAAAABbQ/80YGMGIb9Yk1Wf5xumqpNPfFEKffs__iACLcBGAs/s1600/Screenshot%2Bfrom%2B2017-08-15%2B07-38-00.png](https://1.bp.blogspot.com/-Jckk1VCTWiM/WZJE0d44x5I/AAAAAAAABbQ/80YGMGIb9Yk1Wf5xumqpNPfFEKffs__iACLcBGAs/s1600/Screenshot%2Bfrom%2B2017-08-15%2B07-38-00.png)
[https://4.bp.blogspot.com/-U-p4m6sWIiM/WZJEzSkHRXI/AAAAAAAABbM/xbIQ0HHnCrwtaBvx9i_fp-ULF-u2yjhfACLcBGAs/s1600/Screenshot%2Bfrom%2B2017-08-15%2B07-37-15.png](https://4.bp.blogspot.com/-U-p4m6sWIiM/WZJEzSkHRXI/AAAAAAAABbM/xbIQ0HHnCrwtaBvx9i_fp-ULF-u2yjhfACLcBGAs/s1600/Screenshot%2Bfrom%2B2017-08-15%2B07-37-15.png)

---

### Post by lenchase1999 on 2017-08-14
> **sonicwind said:**
> I had problems months ago getting the Ubuntu Software Center version of VLC to work, so I tried the snap of it. It has worked fine for me. The command I used in terminal that works is:

```

sudo snap install –stable --classic vlc

```
I would uninstall all the other versons first although my understanding is the same as ajgreeny.

It seems like it didnt work

SS:
[https://2.bp.blogspot.com/-lPUo-ZKdR-E/WZJE9mdy-DI/AAAAAAAABbU/NC2tdKjAgw4iHfGcvz4t-_ZLnVyMApmAgCLcBGAs/s1600/Screenshot%2Bfrom%2B2017-08-15%2B07-48-40.png](https://2.bp.blogspot.com/-lPUo-ZKdR-E/WZJE9mdy-DI/AAAAAAAABbU/NC2tdKjAgw4iHfGcvz4t-_ZLnVyMApmAgCLcBGAs/s1600/Screenshot%2Bfrom%2B2017-08-15%2B07-48-40.png)

---

### Post by vasa1 on 2017-08-14
Maybe worth stepping back a bit and post the complete output of *sudo apt-get update* and *sudo apt-get upgrade*.

---

### Post by lenchase1999 on 2017-08-14
> **ajgreeny said:**
> Can I get this right in my own mind; you have installed VLC from both the repositories and then from snap packages so probably have versions 2. and 3. installed; correct?

I have not yet botered with any snap packages but as I understand it, the two versions should be able to sit side by side without problems.
Is this a new OS installation or have you previously been able to use VLC siccessfully?

Yes, I've already installed VLC and it works fine, but there has been an error and do not know how to fix it.

Note: i just learned linux last month

---

### Post by lenchase1999 on 2017-08-14
> **vasa1 said:**
> Maybe worth stepping back a bit and post the complete output of *sudo apt-get update* and *sudo apt-get upgrade*.

Uhm, is this what you mean then what's next step?
[https://paste.ubuntu.com/25315904/](https://paste.ubuntu.com/25315904/)

---

### Post by lenchase1999 on 2017-08-15
**[SIZE=6][COLOR=#000000][FONT=arial black][SOLVED][/FONT][/COLOR][/SIZE]** I tried to delete old VLC ppa with Synaptic Package Manager and try to install again, then its work!
[ATTACH=CONFIG]276409[/ATTACH][ATTACH=CONFIG]276410[/ATTACH]

---

