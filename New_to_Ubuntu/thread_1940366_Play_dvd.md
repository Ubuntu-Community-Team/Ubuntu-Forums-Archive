---
title: "Play dvd"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by dwhite on 2012-03-13
I've checked for the past several days how to get dvds to play in lubuntu 11.10 and i've reached an impass.  i have installed the following:

[LIST]
[*]lubuntu-restricted-extras
[*]medibuntu-keyring
[*]apport-hooks-medibuntu
[*]libdvdcss2
[*]libdvdread4
[/LIST]

but i can't get MPlayer work

I had linux mint installed on the same system last week and played dvds without any trouble so i know it's not my hardware.

any suggestions would be appreciated, thanks

---

### Post by Perfect Storm on 2012-03-13
Mplayer properly requires that you install windows 32/64 codecs.

Install non-free-codecs

---

### Post by andrew.46 on 2012-03-13
Can you play your dvd from the commandline using the following syntax:

```
mplayer dvd://1
```

and post the command and full terminal output here? This should give some hints as to what is going on...

**edit** corrected syntax :(.

---

### Post by doctorzeus on 2012-03-13
Personally I'm not a fan of mplayer, I by far prefer vlc on all operating systems (it comes pre-bundled with every single video codec and is fairly lightweight):

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by Rodney9 on 2012-03-13
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by dwhite on 2012-03-14
thanks for the suggestions, i have downloaded vlc using synaptic pkg manager (following directions on vlc website suggested by doctorzeus as that seemed very promising (when i had linux mint installed that was the player that had worked))

it is not working in this case, i can open the disk and it loads the title into the playlist but when i try to play it title gets bold for a second or so the disk starts to spin up and then abruptly stops.

if there are any diagnostic test i can run i would gladly run it, thanks in advance for any help

i've attached a screen shot from vlc showing the codec details if that helps

---

### Post by andrew.46 on 2012-03-14
> **dwhite said:**
> if there are any diagnostic test i can run i would gladly run it, thanks in advance for any help

Well, there was this suggestion:

[http://ubuntuforums.org/showpost.php?p=11762354&postcount=3](http://ubuntuforums.org/showpost.php?p=11762354&postcount=3)

:).

---

### Post by dwhite on 2012-03-14
> **andrew.46 said:**
> Well, there was this suggestion:

[http://ubuntuforums.org/showpost.php?p=11762354&postcount=3](http://ubuntuforums.org/showpost.php?p=11762354&postcount=3)

:).

hi, yes sorry about that, i keep getting the following (see screenshot) error, thought it was me making an error so i was a little hesitant to post, thanks.:)

ahh here is the info you were looking for..had to put into two separate screenshots hope they are legible.

---

### Post by andrew.46 on 2012-03-14
Oops my fault, I have supplied bad syntax! Correct is:
```

mplayer dvd://1
```

My apologies :)

---

### Post by dwhite on 2012-03-14
> **andrew.46 said:**
> Oops my fault, I have supplied bad syntax! Correct is:
```

mplayer dvd://1
```My apologies :)


thanks, i edited my previous post with the screenshots, didn't want to bump my post if i didn't have to. :D

---

### Post by waynefoutz on 2012-03-14
put this in the terminal, then reboot. 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

any player will work after that from the GUI,like it's supposed to, I promise you.

---

### Post by dwhite on 2012-03-14
> **waynefoutz said:**
> put this in the terminal, then reboot. 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```any player will work after that from the GUI,like it's supposed to, I promise you.

does this command install libdvdread4?  if so i think it is already installed, see attached synaptic screenshot

---

### Post by waynefoutz on 2012-03-14
> **dwhite said:**
> does this command install libdvdread4?  if so i think it is already installed, see attached synaptic screenshot

there's more to it than that. libdvdread4 will let you play home burnt dvds, that's about it. The above command will enable restricted formats, meaning commercial dvds. 

see:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

You need to reboot after for it to take effect.

---

### Post by dwhite on 2012-03-14
> **waynefoutz said:**
> there's more to it than that. libdvdread4 will let you play home burnt dvds, that's about it. The above command will enable restricted formats, meaning commercial dvds. 

see:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You need to reboot after for it to take effect.


Thanks for all the help, i ran the command, rebooted and still won't play dvd, i also tried with vlc player and no luck there either, i think i have a serious problem here.

thanks again, i have to get to sleep so i won't be trying anything else tonight, thinking i just might reinstall ubuntu, i wonder if i can run the LXDE desktop in ubuntu i like it very much and one of the main reasons i'd like to stay with lubuntu

ciao,

doug

---

### Post by waynefoutz on 2012-03-14
> **dwhite said:**
> Thanks for all the help, i ran the command, rebooted and still won't play dvd, i also tried with vlc player and no luck there either, i think i have a serious problem here.

thanks again, i have to get to sleep so i won't be trying anything else tonight, thinking i just might reinstall ubuntu, i wonder if i can run the LXDE desktop in ubuntu i like it very much and one of the main reasons i'd like to stay with lubuntu

ciao,

doug


Yeah, you can do that. Also, if you had success with Linux Mint, they just released a new LXDE version a few days ago.

---

### Post by dwhite on 2012-03-14
> **waynefoutz said:**
> Yeah, you can do that. Also, if you had success with Linux Mint, they just released a new LXDE version a few days ago.


Thanks, i'll definitely check that out.

thanks again

---

### Post by dwhite on 2012-03-16
well still trying to get this to work (need to play dvd's on this system for work) switched out lubuntu for xubuntu to see if that helped, installed all the packages needed too play restricted format dvd's, tried mplayer, vlc, and parole and no luck.

finally downloaded and ran```
 regionset
```, and set to region 1 (north america) now dvd's start to play but choppy and pixelated, so i'm hopeful.


thanks again, 
  

after reboot ```
regionset
```  command seems to have solved the problem

---

