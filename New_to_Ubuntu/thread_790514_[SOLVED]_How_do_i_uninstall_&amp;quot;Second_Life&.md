---
title: "[SOLVED] How do i uninstall &amp;quot;Second Life&amp;quot;?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by opendevlite on 2008-05-11
i got this game in getdeb.net

the game worked fine, but the graphics is just to slow for my graphics card, so i decided to uninstall it

How do i uninstall it?

---

### Post by diablo75 on 2008-05-11
Have you tried Synaptic Package Manager?  I'd do a search in Synaptic for "second" and then scroll through the results until you see second life in there.  I've never installed Second Life with a deb.  But I have downloaded a tar.gz before that would extract to a folder and I'd just double click on the executable in there to run the game.  I think it was a .run file.... been a while.

Anyway, Synaptic is located in System>Administration>Synaptic Package Manager.

---

### Post by Joeb454 on 2008-05-11
I think you may be able to remove it by running ```
sudo dpkg -r secondlife
``` or something along those lines - from a terminal :)

---

### Post by opendevlite on 2008-05-11
> **Joeb454 said:**
> I think you may be able to remove it by running ```
sudo dpkg -r secondlife
``` or something along those lines - from a terminal :)

after entering the code this is the message

dpkg - warning: ignoring request to remove secondlife which isn't installed.

---

### Post by Joeb454 on 2008-05-11
Hmm, did you check synaptic as well?

---

### Post by opendevlite on 2008-05-11
> **Joeb454 said:**
> Hmm, did you check synaptic as well?

Yes, i can see "secondlife-install" in synaptic, but i'm afraid something might go wrong, because it might just be the install file

---

### Post by Joeb454 on 2008-05-11
I think if you mark that for complete removal it should be ok. It shouldn't break anything either

---

### Post by philinux on 2008-05-11
Just mark it for complete removal then click apply.

---

### Post by opendevlite on 2008-05-11
> **Joeb454 said:**
> I think if you mark that for complete removal it should be ok. It shouldn't break anything either

This is the description when i click on "secondlife-install"

This package does not include the game which would be illegal
It will download the game from the secondlife site and install it
The game size is 50 MBs, it will take some time to download and install

when i click on properties on "secondlife-install" it only has 545kb file size, i'm confused

---

### Post by Joeb454 on 2008-05-11
Is there anything in /usr/bin or something. I'm not 100% sure where the files would be kept

---

### Post by opendevlite on 2008-05-11
bump

---

### Post by diablo75 on 2008-05-11
> **philinux said:**
> Just mark it for complete removal then click apply.

+1

The reason it says, "This will download blahbity blah blah blah" is because the description is written specifically for people who haven't installed it, which you already have.

So seconding the above post, check it off for complete removal, and click apply.  You will not break anything.

---

### Post by opendevlite on 2008-05-12
I emailed the author of "secondlife-install" in synaptic and he replied to me and said "removing it (secondlife-install) from synaptic will do it" so i did what he told me and it worked.

I did a search for files named "second" again and everything was gone.

Thanks by the way to all the people who replied.

---

### Post by Joeb454 on 2008-05-12
Glad you got this sorted :) Please mark your thread as solved (yes it's back!)

It's in thread tools at the top of this page :)

---

### Post by Hastor on 2010-05-28
[SIZE=3]I just downloaded SL and found, just as the original poster, my graphics card is just not up 
to snuff. I decided to delete all files I knew pretained to second life (.tar and the ones I got off download) and I checked synaptic to see if there was any lurking bits of SL still slinking through my computer and I cam up with nothing. Even though it seems like its all gone I've got a lurking feeling that my installation would have put it in some place I wasn't aware of. Trying to remedy this I ran " [/SIZE]sudo dpkg -r secondlife "[SIZE=3]. I ended up getting the message "dpkg: status database area is locked by another process". This only made feel worse about the whole "second life is still somewhere on my computer" deal. Any ideas how to get this thing off once and for all? Thanks.[/SIZE]

---

### Post by Nikola Georgiev on 2011-05-17
What if I just shift+delete the folder?

---

