---
title: "DVD app."
date: 2011-09-21
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2011-09-21
Is there an application I can watch DVD's on, without having to be a Master Programmer to set it up?:mad:

I mean, seriously! Last night, I wanted to watch a movie. Tried Movie Player, didn't work (said it was missing some plugin, but, when I tried to install it, couldn't find it), then I installed Dragon Player, which didn't work either. Ended up having to watch it on my laptop, under Windows 7.](*,)

In case it makes a difference, I'm using 10.04 LTS, 

Help, please?
Thanks in advance. :)

---

### Post by arochester on 2011-09-21
[https://help.ubuntu.com/community/Medibuntu#Playing_Encrypted_DVDs](https://help.ubuntu.com/community/Medibuntu#Playing_Encrypted_DVDs)

---

### Post by MG&amp;TL on 2011-09-21
Try VLC. That seems to work for anything (almost-in fact I believe that's the point of it), and you can get it in software-centre.

Are you struggling with setting the software up, or playing anything with said software?

---

### Post by tgm4883 on 2011-09-21
[http://www.fluendo.com/shop/product/fluendo-dvd-player/](http://www.fluendo.com/shop/product/fluendo-dvd-player/)

I believe it is available in the software centre

---

### Post by anewguy on 2011-09-21
Try installing the libdvdcss package in the package manager.


dave ;)

---

### Post by Inodoro Pereyra on 2011-09-21
Thanks everybody for the replies.
I installed VLC, and worked perfectly out of the box.:D

Dammit, I love Ubuntu, but, when it comes to installing stuff, it's so far behind Windows, it's not even funny.

---

### Post by jtarin on 2011-09-21
> **Inodoro Pereyra said:**
> Thanks everybody for the replies.
I installed VLC, and worked perfectly out of the box.:D

Dammit, I love Ubuntu, but, when it comes to installing stuff, it's so far behind Windows, it's not even funny.
Actually IMO it's the other way around.....Windows will allow you to install anything....whether it's harmful or not to your computer. Once you understand package management in your preferred distribution, it's a piece of cake. You can even learn to compile and package your own software.

---

### Post by jtarin on 2011-09-21
> **anewguy said:**
> Try installing the libdvdcss package in the package manager.


dave ;)+1 for encrypted DVD's

---

### Post by Inodoro Pereyra on 2011-09-21
> **jtarin said:**
>  Once you understand package management in your preferred distribution, it's a piece of cake. You can even learn to compile and package your own software.

I'm pretty sure you're right, but that's precisely the point. Some people just don't have the time -or the will- to "learn" how to install a package. Not everyone who uses a computer needs to be a software expert, just like you don't need  to be a mechanics engineer to drive a car. As much as I hate Windows, I have to admit at least they understand that. 

As per installing things that may be harmful to your compute, I guess you might. Meanwhile, in Ubuntu, not even the apps that come prepackaged work properly, or, in some cases, at all (Movie Player and Rythmbox being 2 prime examples). I rather take the risk.

---

### Post by tgm4883 on 2011-09-21
> **Inodoro Pereyra said:**
> I'm pretty sure you're right, but that's precisely the point. Some people just don't have the time -or the will- to "learn" how to install a package. Not everyone who uses a computer needs to be a software expert, just like you don't need  to be a mechanics engineer to drive a car. As much as I hate Windows, I have to admit at least they understand that. 

As per installing things that may be harmful to your compute, I guess you might. Meanwhile, in Ubuntu, not even the apps that come prepackaged work properly, or, in some cases, at all (Movie Player and Rythmbox being 2 prime examples). I rather take the risk.

Rhythmbox isn't a default app and movie player works great for me. Or maybe you mean you can't play DVD's out of the box, which IIRC you can't do on Windows either.

---

### Post by mikewhatever on 2011-09-21
> **Inodoro Pereyra said:**
> I'm pretty sure you're right, but that's precisely the point. Some people just don't have the time -or the will- to "learn" how to install a package. Not everyone who uses a computer needs to be a software expert, just like you don't need  to be a mechanics engineer to drive a car. As much as I hate Windows, I have to admit at least they understand that. 

As per installing things that may be harmful to your compute, I guess you might. Meanwhile, in Ubuntu, not even the apps that come prepackaged work properly, or, in some cases, at all (Movie Player and Rythmbox being 2 prime examples). I rather take the risk.

That's nonsense. You don't have to understand how the package manager works to install packages.

For example:

1. Open the Software Center.

2. Search for VLC.

3, Click the Install button.

Which of the above steps seems difficult?

---

### Post by Inodoro Pereyra on 2011-09-21
> **tgm4883 said:**
> Rhythmbox isn't a default app and movie player works great for me. Or maybe you mean you can't play DVD's out of the box, which IIRC you can't do on Windows either.

Well, rhythmbox IS installed on my system, and I didn't install it, so I guess it came with it. I'd think it makes sense that apps that come prepackaged out of the box, should work out of the box. Otherwise, why are they there to begin with?
BTW: you don't remember correctly. All I had to do, last night, on a 100% fresh Windows installation, was insert the DVD, click OK, and play.

> **mikewhatever said:**
> That's nonsense. You don't have to understand how the package manager works to install packages.

For example:

1. Open the Software Center.

2. Search for VLC.

3, Click the Install button.

Which of the above steps seems difficult?

That is exactly what I did with VLC, and it worked perfectly from the get go, thank you. 
That is **also** exactly what I did last night with the Dragon Player, and it didn't, at all. 
Meanwhile, before that, I had to spend more than an hour reading through each app in the software center , that was in any way related to DVDs, and, if it hasn't been suggested here, I'd have never installed VLC, just because whomever wrote all the tech mumbo jumbo in its description, somehow thought typing "DVD player" was not worth the effort. Does that sound simple (or efficient) to you?

---

### Post by mikewhatever on 2011-09-21
Unfortunately, DVDs are a special case because those that designed the technology went out of their ways to make it difficult for the user to just play them. AFAIK, on Windows, a special application is used called WinDVD (there is LinDVD as well). Due to legal pitfalls, Ubuntu can't provide an easy access to the needed software, and so the user must go through hoops of getting stuff from Medibuntu.

However, the above has nothing to do with the ease of installation. Generally, installing software in Ubuntu is much easier then in Windows, thanks to the repositories and the Software Center.

---

### Post by jtarin on 2011-09-21
> **tgm4883 said:**
> rhythmbox isn't a default app and movie player works great for me. Or maybe you mean you can't play dvd's out of the box, which iirc you can't do on windows either.+1 :p

---

### Post by alphacrucis2 on 2011-09-21
> **Inodoro Pereyra said:**
> Well, rhythmbox IS installed on my system, and I didn't install it, so I guess it came with it. I'd think it makes sense that apps that come prepackaged out of the box, should work out of the box. Otherwise, why are they there to begin with?
BTW: you don't remember correctly. All I had to do, last night, on a 100% fresh Windows installation, was insert the DVD, click OK, and play.



That is exactly what I did with VLC, and it worked perfectly from the get go, thank you. 
That is **also** exactly what I did last night with the Dragon Player, and it didn't, at all. 
Meanwhile, before that, I had to spend more than an hour reading through each app in the software center , that was in any way related to DVDs, and, if it hasn't been suggested here, I'd have never installed VLC, just because whomever wrote all the tech mumbo jumbo in its description, somehow thought typing "DVD player" was not worth the effort. Does that sound simple (or efficient) to you?

VLC is the probably most common player on windows too. At least among those who realise there is something else other than Windows Media Player out there.

---

### Post by Inodoro Pereyra on 2011-09-22
> **mikewhatever said:**
> Unfortunately, DVDs are a special case because those that designed the technology went out of their ways to make it difficult for the user to just play them. AFAIK, on Windows, a special application is used called WinDVD (there is LinDVD as well). Due to legal pitfalls, Ubuntu can't provide an easy access to the needed software, and so the user must go through hoops of getting stuff from Medibuntu.

However, the above has nothing to do with the ease of installation. Generally, installing software in Ubuntu is much easier then in Windows, thanks to the repositories and the Software Center.

It's not just with the DVDs. Some time ago, I spent days trying to install 2 different programs (Emc2 and ReplicatorG). Finally, I ended giving up on them. For some time, I've been going crazy, trying several different ways to install Tor and Polipo on a flash drive. Even after opening several threads here about it, and spending dozens of hour on it, I still couldn't make it work. 

Meanwhile, before using Ubuntu, I'd been using Windows since 3.11. I **NEVER** installed any app or program that hurt my computer, and, especially with Windows 7, once you go through all the copyright stuff, everything is plug and play. Installing Tor and Polipo takes less than 20 minutes, and it **works**. 
Right now, the only thing that keeps me hooked on Ubuntu is its much higher speed on old hardware, but, to be honest, the rest is starting to annoy the hell out of me.

> **alphacrucis2 said:**
> VLC is the probably most common player on windows too. At least among those who realise there is something else other than Windows Media Player out there.

Maybe. I didn't even know about VLC until last night. But the fact remains that, good or bad, the Windows Media Player works, and the Ubuntu Movie player doesn't.

---

### Post by alphacrucis2 on 2011-09-22
> **Inodoro Pereyra said:**
> It's not just with the DVDs. Some time ago, I spent days trying to install 2 different programs (Emc2 and ReplicatorG). Finally, I ended giving up on them. For some time, I've been going crazy, trying several different ways to install Tor and Polipo on a flash drive. Even after opening several threads here about it, and spending dozens of hour on it, I still couldn't make it work. 

Meanwhile, before using Ubuntu, I'd been using Windows since 3.11. I **NEVER** installed any app or program that hurt my computer, and, especially with Windows 7, once you go through all the copyright stuff, everything is plug and play. Installing Tor and Polipo takes less than 20 minutes, and it **works**. 
Right now, the only thing that keeps me hooked on Ubuntu is its much higher speed on old hardware, but, to be honest, the rest is starting to annoy the hell out of me.



Maybe. I didn't even know about VLC until last night. But the fact remains that, good or bad, the Windows Media Player works, and the Ubuntu Movie player doesn't.

It does as long as you install libdvdcss2 as explained in the community docs.

[URL="https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs"]https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs
[/URL]

---

### Post by jtarin on 2011-09-22
> **Inodoro Pereyra said:**
>  But the fact remains that, good or bad, the Windows Media Player works, and the Ubuntu Movie player doesn't.

When you have an app that is troublesome run it from the terminal as to see error output.

---

### Post by Inodoro Pereyra on 2011-09-22
> **jtarin said:**
> When you have an app that is troublesome run it from the terminal as to see error output.

How do I do that?:confused:

---

### Post by tgm4883 on 2011-09-22
> **Inodoro Pereyra said:**
> <snip>
Meanwhile, before using Ubuntu, **I'd been using Windows since 3.11**. 

<snip>

Maybe. **I didn't even know about VLC until last night.** But the fact remains that, good or bad, the Windows Media Player works, and the Ubuntu Movie player doesn't.

I find these two sentences highly suspicious

---

### Post by MG&amp;TL on 2011-09-22
Step 1. Find out what the terminal command for something is. In this case, 

```
vlc
```

Step2. Open a terminal and type the command.

Step3. Watch the pretty startup messages and system errors.

---

### Post by mikewhatever on 2011-09-22
> **Inodoro Pereyra said:**
> It's not just with the DVDs. Some time ago, I spent days trying to install 2 different programs (Emc2 and ReplicatorG). Finally, I ended giving up on them. For some time, I've been going crazy, trying several different ways to install Tor and Polipo on a flash drive. Even after opening several threads here about it, and spending dozens of hour on it, I still couldn't make it work. 

I've never heard of those applications. Are they for Windows only?

> Meanwhile, before using Ubuntu, I'd been using Windows since 3.11. I **NEVER** installed any app or program that hurt my computer, and, especially with Windows 7, once you go through all the copyright stuff, everything is plug and play. Installing Tor and Polipo takes less than 20 minutes, and it **works**. 
Right now, the only thing that keeps me hooked on Ubuntu is its much higher speed on old hardware, but, to be honest, the rest is starting to annoy the hell out of me.


Never tried installing those as well. It's been fun chatting with you. Use what works best for you.
Good luck.

---

### Post by Inodoro Pereyra on 2011-09-22
> **tgm4883 said:**
> I find these two sentences highly suspicious

I'm sure you do. I'm also sure you think your statement is terribly important to me.
Unfortunately, you're dead wrong in both cases.

But, most important, I fail to see how any of that has anything to do with the topic being discussed here.

> **MG&TL said:**
> Step 1. Find out what the terminal command for something is. In this case, 

```
vlc
```.

Well, I can tell you one thing: the terminal command for the movie player is NOT "movie player".:lol::lol:

> **mikewhatever said:**
> I've never heard of those applications. Are they for Windows only?

Nope. Emc2 is Linux only. ReplicatorG is supposed to work on either OS.

[http://linuxcnc.org/content/view/21/4/lang%2Cen/]("http://linuxcnc.org/content/view/21/4/lang%2Cen/")

[http://replicat.org/](http://replicat.org/)

> **mikewhatever said:**
> Never tried installing those as well. It's been fun chatting with you. Use what works best for you.
Good luck.

Thank you, same here.
There's a tutorial for Tor and Polipo, written by Bodhizazen, that is so good, so clear, that even I could follow it without any major problem. But, even after following it to the letter, in both Lubuntu and Ubuntu, it just doesn't work.

---

