---
title: "[SOLVED] Upgrading Wine?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Muffinabus on 2008-05-27
I have absolutely NO CLUE how to upgrade Wine.  I have it installed via Synaptic, and it gave me version 0.9.59 when 0.9.60 has been out for a month or two now.  Do I have to uninstall my current version and manually install the binary packages, or how does that work?

I was on the downloads page for Wine, I was going to make an attempt at getting the 1.0 release candidate 2, when it told me to type this in terminal:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

Which resulted in the following error:

```
gpg: no valid OpenPGP data found.
```

I feel kind of dumb failing on the *first step* of downloading the latest version, and I honestly don't think I did anything wrong, lol.

If someone could guide me into how I can install Wine 1.0-rc2 or 1.0-rc1, or even anything above my current version, I would greatly appreciate it.

---

### Post by Paqman on 2008-05-27
> **Muffinabus said:**
> 
I feel kind of dumb failing on the *first step* of downloading the latest version, and I honestly don't think I did anything wrong, lol.


You haven't, they've given you bad instructions. Possibly the link is wrong. Send them an email.

---

### Post by EXCiD3 on 2008-05-27
> **Muffinabus said:**
> I have absolutely NO CLUE how to upgrade Wine.  I have it installed via Synaptic, and it gave me version 0.9.59 when 0.9.60 has been out for a month or two now.  Do I have to uninstall my current version and manually install the binary packages, or how does that work?

I was on the downloads page for Wine, I was going to make an attempt at getting the 1.0 release candidate 2, when it told me to type this in terminal:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```Which resulted in the following error:

```
gpg: no valid OpenPGP data found.
```I feel kind of dumb failing on the *first step* of downloading the latest version, and I honestly don't think I did anything wrong, lol.

If someone could guide me into how I can install Wine 1.0-rc2 or 1.0-rc1, or even anything above my current version, I would greatly appreciate it.

That step is not actually all that vital. Basically PGP is a way for you to verify the authenticity of the source you are downloading from. If you leave this out, you will be warned that it has not been verified but everything will still work the same. Just make sure you add the Wine repositories using the command listed next.```
*sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```*

---

### Post by Muffinabus on 2008-05-27
> **EXCiD3 said:**
> That step is not actually all that vital. Basically PGP is a way for you to verify the authenticity of the source you are downloading from. If you leave this out, you will be warned that it has not been verified but everything will still work the same. Just make sure you add the Wine repositories to your sources.list and everything should be fine.

Hmm, okay, haha.  So I think their servers are down right now, can anyone verify that?

```
Resolving wine.budgetdedicated.com... failed: Name or service not known.
```

---

### Post by inportb on 2008-05-27
I remember having trouble with that last night. But it looks like the servers have been on and off.

---

### Post by EXCiD3 on 2008-05-27
> **Muffinabus said:**
> Hmm, okay, haha.  So I think their servers are down right now, can anyone verify that?

```
Resolving wine.budgetdedicated.com... failed: Name or service not known.
```

If you've already run that command you can just jump over to [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/) and download the deb there and install it with either GDebi or dpkg. I was able to download it from there...but im on a windows machine right now so i cant see what "apt-get install wine" does.:(

---

### Post by Muffinabus on 2008-05-27
> **EXCiD3 said:**
> If you've already run that command you can just jump over to [http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/) and download the deb there and install it with either GDebi or dpkg. I was able to download it from there...but im on a windows machine right now so i cant see what "apt-get install wine" does.:(

Nope, Firefox won't load the page either.

---

### Post by EXCiD3 on 2008-05-27
Huh...anyways i can download it and attach it to the forums for you. Which version do you need 32 or 64? (I'm on dialup so it might take a few :P)

---

### Post by Paqman on 2008-05-27
> **Muffinabus said:**
> Nope, Firefox won't load the page either.

Works for me.

---

### Post by Muffinabus on 2008-05-27
32 bit, thanks.  I don't know why it's not working for me though.  Odd...

---

### Post by adobrakic on 2008-05-27
Yeah, works for me also. If you want me to upload it, Excid, since you have dial up, i wouldn't mind

---

### Post by EXCiD3 on 2008-05-27
> **Muffinabus said:**
> 32 bit, thanks.  I don't know why it's not working for me though.  Odd...

Gah its 8mb...Anyone else care to do the honors? Also you probably wont be able to upload it to the forums directly, rapidshare or megaupload it instead.

---

### Post by adobrakic on 2008-05-27
here you go:
[http://sharebee.com/7e2453d2](http://sharebee.com/7e2453d2)

---

### Post by EXCiD3 on 2008-05-27
lol thanks...would hvae taken me a couple days ;)

---

### Post by Muffinabus on 2008-05-27
Cool, thanks for all the help guys :3

---

### Post by adobrakic on 2008-05-27
> **EXCiD3 said:**
> lol thanks...would hvae taken me a couple days ;)

haha no problem, i understand, i recently got broadband. :x

> Cool, thanks for all the help guys :3 

No problem, could you mark the thread solved please. By using Thread Tools at the top.
:]

---

### Post by EXCiD3 on 2008-05-27
no problem at all, just here to help :)

> **adobrakic said:**
> haha no problem, i understand, i recently got broadband. :x



No problem, could you mark the thread solved please. By using Thread Tools at the top.
:]
I've been looking everywhere but it seems that im just far enough out in the country dialup is the best i can do without spending outrageous amounts per month :(

---

