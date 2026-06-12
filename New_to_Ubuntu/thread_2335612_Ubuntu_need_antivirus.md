---
title: "Ubuntu need antivirus ?"
date: 2016-08-30
forum: New to Ubuntu
---

### Post by dkm171 on 2016-08-30
Dear admin & support team or friends

Ubuntu 16.04 needs antivirus software ?

and 

Indian Language Telugu available on Ubuntu 16.04 ?

---

### Post by howefield on 2016-08-30
> **dkm171 said:**
> Ubuntu 16.04 needs antivirus software ?

Have a read here and decide for yourself, or ask supplementary questions if needed.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

> Indian Language Telugu available on Ubuntu 16.04 ?

Looks like it.. as per attached screenshot.

---

### Post by dkm171 on 2016-09-01
**Dear  **[[COLOR=#990303]howefield[/COLOR]]("https://ubuntuforums.org/member.php?u=186490")[COLOR=#000000] 

thanks for your answer

1. 
I understand antivirus using for Ubuntu 16.04, but comodo anitvirus not available for Ubuntu 16.04, this comodo anitvirus supports Ubuntu 12.04 only. i dont know this software works on Ubuntu 16.04.

2.
How to download telugu language and also all other languages on Ubuntu 16.04




[/COLOR]

---

### Post by howefield on 2016-09-01
> **dkm171 said:**
> I understand antivirus using for Ubuntu 16.04, but comodo anitvirus not available for Ubuntu 16.04, this comodo anitvirus supports Ubuntu 12.04 only. i dont know this software works on Ubuntu 16.04.

Comodo will give you a dependency issue in 16.04.

Probably better to choose another vendor but would be good to know if you need on demand scanning or if you also need scanning in the background (on access).

> How to download telugu language and also all other languages on Ubuntu 16.04

System Settings > Language Support > Install/Remove Languages, scroll down to the required language option and click apply, should be enough to do it.

---

### Post by dkm171 on 2016-09-01
> **howefield said:**
> Comodo will give you a dependency issue in 16.04.

Probably better to choose another vendor but would be good to know if you need on demand scanning or if you also need scanning in the background (on access).



System Settings > Language Support > Install/Remove Languages, scroll down to the required language option and click apply, should be enough to do it.



Telugu not visible on my "Languages Support"  English are there only, other languages not available, for why ?

---

### Post by howefield on 2016-09-01
> **dkm171 said:**
> Telugu not visible on my "Languages Support"  English are there only, other languages not available, for why ?

Have you clicked on the Install/Remove Languages button ?

---

### Post by dkm171 on 2016-09-01
> **howefield said:**
> Have you clicked on the Install/Remove Languages button ?

Yes, i clicked, but it is display only English !

I will send you a screenshot, but how ?

---

### Post by howefield on 2016-09-01
> **dkm171 said:**
> I will send you a screenshot, but how ?

Use the paperclip icon to attach the image to your posting (name it 01.png or something like that - it may not post otherwise). The paperclip icon is only available in the Advanced editor, so don't use the Quick Reply window.

---

### Post by dkm171 on 2016-09-01
[ATTACH=CONFIG]270951[/ATTACH]

---

### Post by howefield on 2016-09-01
What is the output of..

```
apt-cache search language-pack | grep "Telugu"
```

Also I am assuming that since installing Ubuntu you have updated it, if you haven't...

```
sudo apt update
```
```
sudo apt upgrade
```

---

### Post by dkm171 on 2016-09-01
please see the Image,

[ATTACH=CONFIG]270952[/ATTACH]

---

### Post by howefield on 2016-09-01
Tip : It is usually better to copy paste output from a terminal and post the text between code tags rather than an image, it is easier for others to read. :)

Something looks odd with your sudo apt update, especially with you not getting a return with the package search.

What is the output from

```
cat /etc/apt/sources.list
```

PS. The output form the package search for Telugu should be something like..

```
hugh@xenial-laptop:~$ apt-cache search language-pack | grep "Telugu"
language-pack-gnome-te - GNOME translation updates for language Telugu
language-pack-gnome-te-base - GNOME translations for language Telugu
language-pack-te - translation updates for language Telugu
language-pack-te-base - translations for language Telugu
hugh@xenial-laptop:~$
```

---

### Post by dkm171 on 2016-09-01
> **howefield said:**
> Tip : It is usually better to copy paste output from a terminal and post the text between code tags rather than an image, it is easier for others to read. :)

Something looks odd with your sudo apt update, especially with you not getting a return with the package search.

What is the output from

```
cat /etc/apt/sources.list
```

PS. The output form the package search for Telugu should be something like..

```
hugh@xenial-laptop:~$ apt-cache search language-pack | grep "Telugu"
language-pack-gnome-te - GNOME translation updates for language Telugu
language-pack-gnome-te-base - GNOME translations for language Telugu
language-pack-te - translation updates for language Telugu
language-pack-te-base - translations for language Telugu
hugh@xenial-laptop:~$
```


no information, empty display

---

### Post by howefield on 2016-09-01
OK, load up the Software & Updates application and from the Ubuntu Software tab, check off all except the Source code option.

I'd suggest also going into the Other Software tab and place a check against the Canonical Partners option but again, not the source code option although the Canoncial Partners repository may not be of interest to you, so that one is up to you. It has no bearing on what we are doing here.

Then close out and you should be prompted to Reload the software sources, do that and then at the terminal..

```
sudo apt update
```
```
sudo apt upgrade
```

---

### Post by dkm171 on 2016-09-01
> **howefield said:**
> OK, load up the Software & Updates application and from the Ubuntu Software tab, check off all except the Source code option.

I'd suggest also going into the Other Software tab and place a check against the Canonical Partners option but again, not the source code option although the Canoncial Partners repository may not be of interest to you, so that one is up to you. It has no bearing on what we are doing here.

Then close out and you should be prompted to Reload the software sources, do that and then at the terminal..

```
sudo apt update
```
```
sudo apt upgrade
```


Yeah, its working
thank you

and

how to set my screen resolution 1600x900, please tell me,

---

### Post by howefield on 2016-09-01
> **dkm171 said:**
> Yeah, its working
thank you

Cool, you are welcome. So you now have the option to install your language preference ?

> how to set my screen resolution 1600x900, please tell me,

It is usually better to stick with one topic per thread. If you have a separate question to this thread I'd suggest starting a thread in the *[Hardware]("https://ubuntuforums.org/forumdisplay.php?f=332")* forum with as much information as you can post including your machine specifications, particularly the graphics card.

And just to conclude this thread (asuming you are done with the language install issue) if you need an "on demand" anti virus application I'd suggest ClamAV which is in the Ubuntu repositories and if you need an "on access" scanner I'd suggest you look at Sophos.

---

### Post by dkm171 on 2016-09-01
> **howefield said:**
> Cool, you are welcome. So you now have the option to install your language preference ?


It is usually better to stick with one topic per thread. If you have a separate question to this thread I'd suggest starting a thread in the *[Hardware]("https://ubuntuforums.org/forumdisplay.php?f=332")* forum with as much information as you can post including your machine specifications, particularly the graphics card.



ok, 


> 

And just to conclude this thread (asuming you are done with the language install issue) if you need an "on demand" anti virus application I'd suggest ClamAV which is in the Ubuntu repositories and if you need an "on access" scanner I'd suggest you look at Sophos.



1. Telugu language downloaded, its working successfully and how to type text in telugu language as text file or Libre Office ?

2. ok i will try this ClamAV, if i any questions i will ask you for this !

---

### Post by howefield on 2016-09-01
> **dkm171 said:**
> Telugu language downloaded, its working successfully and how to type text in telugu language as text file or Libre Office ?

Assuming that you have it as an option in the panel language indicator (as per image) - Super + Spacebar keys should toggle through the available options..  

>  ok i will try this ClamAV, if i any questions i will ask you for this !

Cool, good luck.

---

### Post by dkm171 on 2016-09-01
> **howefield said:**
> Assuming that you have it as an option in the panel language indicator (as per image) - Super + Spacebar keys should toggle through the available options..  



Cool, good luck.



There is no swap button for languages on Top Bar Position !

---

### Post by howefield on 2016-09-01
> **dkm171 said:**
> There is no swap button for languages on Top Bar Position !

No, that's correct, there is no swap button - all you have to do is click on the language option that you want to use, or as I indicated use the keyboard shortcut Super + Spacebar keys to toggle through them. (*Super being the "Windows" key, usually to the left of the Alt key*).

---

### Post by dkm171 on 2016-09-01
> **howefield said:**
> No, that's correct, there is no swap button - all you have to do is click on the language option that you want to use, or as I indicated use the keyboard shortcut Super + Spacebar keys to toggle through them. (*Super being the "Windows" key, usually to the left of the Alt key*).


Swap button means a language changing icon will appear on top bar position ! but, this is not available on my computer !

---

### Post by howefield on 2016-09-01
> **dkm171 said:**
> Swap button means a language changing icon will appear on top bar position ! but, this is not available on my computer !

<Shrug>

Not sure what you mean, the language changing icon is present in your set up, it is visible in the screenshot that you uploaded earlier. In any event, as said already a couple of times, the keyboard short of Super + Spacebar keys will toggle through the language inputs.

---

