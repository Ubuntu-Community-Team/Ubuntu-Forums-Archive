---
title: "A few questions"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by Cmiller2 on 2013-03-29
Hello Ubuntu Community,

This is Cmiller, and I have a few questions. Someone recently suggested I open a terminal and type in this command: **sudo apt-get update && install ubuntu-restricted-extras**. And I did just that, correctly.

Okay so here are my questions:

1.) What does "sudo" and "apt-get" mean.

2.) When I enter this command in my terminal, what exactly telling my computer to do?

3.) What's "ubuntu-restricted-extras?"

4.) After I entered the command I get messages like, "Ign" and "Hit" <link>. What do those mean? "Ign" and "Hit"

Also I am have a quaint problem with what to do next. At the very end of it all, I received the following message in the terminal:

**install: missing destination file operand after `ubuntu-restricted-extras'**

What does that mean? And what went wrong? Can someone explain all this to me? What do I so I can successfully complete this task.

Kind Regards,

Cmiller

---

### Post by sudodus on 2013-03-29
Welcome to the Ubuntu Forums :-)

I think the command should be like this

```
sudo apt-get update && [COLOR=#ff0000]sudo apt-get[/COLOR] install ubuntu-restricted-extras
```

sudo gives you adminstation privileges

apt-get manages updates, upgrades and installing new packages

ubuntu-restricted-extras contains non-free software (I think mainly used to play multimedia).

---

### Post by MrSlugInfinite on 2013-03-29
Can't really help you with your terminal questions, but maybe you could try and install restricted extras through the ubuntu software center? Here is the description straight from there.
> 
Installing this package will pull in support for MP3 playback and decoding, support for various other audio formats(GStreamer plugins), Microsoft fonts, Flash plugin, LAME(to create compressed audio files), and DVD playback.


---

### Post by coffeecat on 2013-03-29
@Cmiller2, the ubuntu-restricted-extras package installs the Microsoft core fonts as well as multimedia stuff and this causes a slight complication when done from the terminal. When you run the corrected terminal syntax that sudodus has given you, and when the process gets to the part where it installs the core fonts, you have to agree to a EULA, but you cannot use the mouse to click on OK in the terminal. Simply use the tab key to highlight OK and then press ENTER. The installer will then download files containing the fonts and install them for you.

---

### Post by grahammechanical on 2013-03-29
> [COLOR=#000000]When I enter this command in my terminal, what exactly telling my computer to do?[/COLOR]

Be careful what you ask for on this forum. You may get information overload. :)

> apt-get is the command-line tool for handling packages, and may be considered the user's "back-end" to other tools using the APT library. Several "front-end" interfaces exist, such as synaptic and aptitude.

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)

The Ubuntu Software Centre is also a front-end for apt-get. I guess that "ign" = ignore. When the link to a package file cannot be accessed and "hit" means that the link has been accessed.

Regards.

---

### Post by Cmiller2 on 2013-03-29
Okay I did as you guys said, and entered the "correct" terminal syntax. I'd have to say everything went a lot smoother. But I'm just curious, why did the person suggest I do that? He never said why. What's the significance? Was it important?

And what are MSCoreFonts?

Regards,

Cmiller

---

### Post by coffeecat on 2013-03-29
> **Cmiller2 said:**
> But I'm just curious, why did the person suggest I do that? He never said why. What's the significance? Was it important?

It was good advice, in my opinion. At least as far as installing ubuntu-restricted-extras is concerned. There are a number of things that cannot be included in a default installation for licensing reasons, and ubuntu-restricted-extras gives you many of these: multimedia codecs, flash and MS core fonts. This package is on my routine install list for every time I do a fresh install of Ubuntu.

> **Cmiller2 said:**
> And what are MSCoreFonts?

[http://en.wikipedia.org/wiki/Core_fonts_for_the_Web](http://en.wikipedia.org/wiki/Core_fonts_for_the_Web)

---

### Post by The Cog on 2013-03-29
Why would he suggest that you install the restricted extras? Well, I don't know what your original problem was. But restricted extras package includes a lot of useful things such as codecs for playing multimedia and some fonts. These are restricted in that the copyright owners don't allow free distribution in the way other Linux stuff does. 

As an example, the extra microsoft true-type fonts must be downloaded from microsoft and you must agree to their license terms (hence the prompt in the middle of the install procedure). In case you don't know, the fonts are different shapes for text in word processing such as arial and times new roman. Yes, people claim copyright on the shapes of letters.

---

### Post by Cmiller2 on 2013-03-29
Thanks everyone. The information you all provided gave me a little bit more understanding on how Linux works. There is still much for me to learn, but its nice to know there is lots of help available. So thanks.

By the way, does this Forum have a FAQ? I always like to refer to one of those before starting anything. If so, can I get the link?

Regards,

Cmiller

---

### Post by oldos2er on 2013-03-29
"Ign" means the package list for that particular repository ([https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)) hasn't been updated since the last time "sudo apt-get update" was run. "Hit" means it has.

---

### Post by The Cog on 2013-03-30
> By the way, does this Forum have a FAQ? 
Not really. But most forums have a few "sticky" threads that are stuck at the top of the page, don't get buried under later posts. These can be very useful.

---

