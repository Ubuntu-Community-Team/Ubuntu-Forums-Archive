---
title: "Running .exe through the open window ;)"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by pmq on 2008-06-11
Hi everyone,

I've run into a challenge. I have a dual boot with xp and ubuntu gutsy gibbon. Soon i will change completely to ubuntu. 
As you may be aware, when you do have a dual setup, in ubuntu you can access your windows files (my documents, program files etc) through an open window as such (the drive which sits on the desktop) which says <size.GB> Media.
I have wine installed for ubuntu also.

Now the little challenge i have is to run a program fill .exe, using wine, through this media drive. Is this possible?
Or for a program to work with wine do i have to install it through wine?

Thanks

pmq

---

### Post by KingTermite on 2008-06-11
I have VERY LITTLE experience with Wine, but I think it has its own little file system. It seems you should be able to copy the exe over and run it from a command line in wine.

---

### Post by Grishka on 2008-06-11
it's generally better in most cases to install software under Wine, as it then install all necessary .dlls and such, but certain software may work by just running it with Wine from the drive where they were installed in Windows.

---

### Post by twright on 2008-06-11
it might work but sometimes it doesn't

---

### Post by Joeb454 on 2008-06-11
I think you would have to install it in Wine.

It's like if you dual-booted XP & Vista, you wouldn't be able to install something in XP and run it from Vista (or the other way round for that matter).

So basically - yes you need it installed in Wine :)

---

### Post by pmq on 2008-06-11
I was able to naviage to the media drive sda1, and then to the program files folder and program i wanted to run, however nothing happened :(

Thanks for your input everyone. I think it would be interesting to find a way to get this to work, it would save alot of time having to re-install programs through wine if they are already in your media drive.

pmq

---

### Post by Duck2006 on 2008-06-11
> **twright said:**
> it might work but sometimes it doesn't

+1 It depends on the program as "Joeb454" posted it may have to be installed under wine. Not all win programs will run under wine you may need some thing like cross over or do it in a virtualbox or vmware.

---

### Post by Joeb454 on 2008-06-11
I think the fact this is unable to work, is due to registry settings.

As I'm sure you know, Windows uses a registry - and naturally, Wine can't use this registry :)

---

### Post by pmq on 2008-06-11
> **Joeb454 said:**
> I think the fact this is unable to work, is due to registry settings.


And there is no way to replicate this in a directory in wine for the registry?

---

### Post by Joeb454 on 2008-06-11
I don't think so.

I do believe Wine has it's own "registry" though I don't know how it works, and I highly doubt you could make it a shortcut to the Windows registry.

---

### Post by pmq on 2008-06-11
Ok, thanks for the education guys. You've all been very helpful. :)

---

### Post by Grishka on 2008-06-11
> **Joeb454 said:**
> I don't think so.

I do believe Wine has it's own "registry" though I don't know how it works, and I highly doubt you could make it a shortcut to the Windows registry.

yes, it does. it works just like in Windows. to see it, just run regedit.

---

### Post by pmq on 2008-06-11
> **Grishka said:**
> yes, it does. it works just like in Windows. to see it, just run regedit.


Unfortunately im sure it only works for programs installed through wine, there would be no way to copy already installed registry files from windows into wine?

---

