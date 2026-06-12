---
title: "[SOLVED] Installing FireFox RC1"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by gnrathon on 2008-05-23
FINALLY the Mozilla FireFox Release Candidate is out! <(^_^<)

But there is a problem, I have Ubuntu 8.04 64bit and I want to update my FireFox Beta 5 to the Release Candidate but it won't update through FireFox i have no idea where to go from there......

I have downloaded the Release Candidate from Mozilla's website. but i have no idea what to do with it.....

---

### Post by Bodsda on 2008-05-23
after youve downloaded it in a terminal type

```
 cd /path/to/folder/firefox 
```

then run it with

```
 ./firefox 
```

---

### Post by sharks on 2008-05-23
what r the files in the folder there? is there a bin file or .configure file?

---

### Post by gnrathon on 2008-05-23
> **sharks said:**
> what r the files in the folder there? is there a bin file or .configure file?

none of the sort my friend

---

### Post by gnrathon on 2008-05-23
> **Bodsda said:**
> after youve downloaded it in a terminal type

```
 cd /path/to/folder/firefox 
```

then run it with

```
 ./firefox 
```

okay this worked but how do i make the shortcuts for my desktop and the top Panel?

oh and none of my plugins were working either

---

### Post by sharks on 2008-05-23
Right click on the desktop and select create launcher and type firefox-3.0

---

### Post by gnrathon on 2008-05-23
did this and it just launches the old version of FireFox
should i remove the old version?

---

### Post by sharks on 2008-05-23
if u want to keep ur addons keep the old one.

---

### Post by gnrathon on 2008-05-23
wil all my data get deleted along w/ it
how do i keep it?

---

### Post by sharks on 2008-05-23
copy .mozilla . it has ur preference.

---

### Post by gnrathon on 2008-05-23
lol
be more specific
where is it?

---

### Post by Maestro23 on 2008-05-23
> **gnrathon said:**
> lol
be more specific
where is it?

Hidden directory in your home directory.

/home/username

ls -a

Should see .mozilla

---

### Post by sharks on 2008-05-23
its in the home foler. its hidden. is this enough and useful?

---

### Post by Bubba64 on 2008-05-23
> **gnrathon said:**
> FINALLY the Mozilla FireFox Release Candidate is out! <(^_^<)

But there is a problem, I have Ubuntu 8.04 64bit and I want to update my FireFox Beta 5 to the Release Candidate but it won't update through FireFox i have no idea where to go from there......

I have downloaded the Release Candidate from Mozilla's website. but i have no idea what to do with it.....

now I have a 32 bit so I don't know if this will work but here is a blog that tells you the launchpad repository link for a straight download. when I did it on both of my computers it overwrote the Hardy version and kept all the add ons, plugins and bookmarks.
[http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/](http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/)
The only problem was with my Thunderbird email not hyperlinking fro email but I fixed this with the configuration editor.

---

### Post by gnrathon on 2008-05-23
yeah except i dont see it
i have view hidden folders enabled

nvr mind!!
found it!!!!
okay so after removal and evrything
where do i put the folder?
in the same place?

---

### Post by gnrathon on 2008-05-23
> **Bubba64 said:**
> now I have a 32 bit so I don't know if this will work but here is a blog that tells you the launchpad repository link for a straight download. when I did it on both of my computers it overwrote the Hardy version and kept all the add ons, plugins and bookmarks.
[http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/](http://blog.rosanegra.org/2008/05/20/how-to-install-firefox-3-rc1-on-ubuntu-hardy/)
The only problem was with my Thunderbird email not hyperlinking fro email but I fixed this with the configuration editor.

whats the exact code you used
i cant seem to figure it out

---

### Post by gnrathon on 2008-05-23
phwew!!!
GOT IT!!!

Thanks for all the Help Everyone!!!!!!

---

### Post by Maestro23 on 2008-05-23
Good deal man.  Please mark this thread "Solved".

---

### Post by Bubba64 on 2008-05-23
> **gnrathon said:**
> whats the exact code you used
i cant seem to figure it out

What I do or did was pasted that launchpad address into the 3rd party of software sources which is in synaptic or system-administration-software sources. If you open up software sources then third party then add to paste that address in then add then close it will reload your repositories and you will see a update icon on the top panel click and install. Butmake sure you remove the original download and make sure this is a 64 bit compatible situation. I suspect launchpad will give you the right program but I don't know if the pasted address is different for 32 or 64 bit, be careful. You got it let us know if you used the launchpad with 64 bit or just installed the Mozilla package.

---

### Post by gnrathon on 2008-05-23
> **Bubba64 said:**
> What I do or did was pasted that launchpad address into the 3rd party of software sources which is in synaptic or system-administration-software sources. If you open up software sources then third party then add to paste that address in then add then close it will reload your repositories and you will see a update icon on the top panel click and install. Butmake sure you remove the original download and make sure this is a 64 bit compatible situation. I suspect launchpad will give you the right program but I don't know if the pasted address is different for 32 or 64 bit, be careful. You got it let us know if you used the launchpad with 64 bit or just installed the Mozilla package.

yeah everything worked fined
no problems at all

---

