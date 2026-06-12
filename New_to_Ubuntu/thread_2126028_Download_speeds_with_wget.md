---
title: "Download speeds with wget"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by bentoman1974 on 2013-03-15
I've played around using wget to download a wide variety of files.  But when downloading flash videos from this one tube site, I get really slow speeds.  I've had this problem on 12.04, 12.10 and Mint 14 (all on the same machine).  Naturally I thought it was the site, but I tried the same downloads on my chromebook which dual boots to Chrubuntu (which I think is basically Ubuntu 12.04) and I got blazing fast speeds.  It's not really a huge deal, but it is sort of driving me nuts that I can't figure this out.  My 1st machine is more powerful then my chromebook, but the latter is newer.  Could this actually be hardware related?  Any insights would be greatly appreciated.

---

### Post by kuifje09 on 2013-03-15
I cannot answer your question, although I think the remote site is seeing who or what is downloading.
Just for curiosity,  do you use special options with wget, or just wget http:...   
Maybe wget on the chromebook is too new to be detected as a not browserwindow ?
Or it behaves just as a browser ?

I thought some sites are just throtteling the download speeds, but this shows something different, or a little inteligence.

---

### Post by bentoman1974 on 2013-03-15
> **kuifje09 said:**
> I cannot answer your question, although I think the remote site is seeing who or what is downloading.
Just for curiosity,  do you use special options with wget, or just wget http:...   
Maybe wget on the chromebook is too new to be detected as a not browserwindow ?
Or it behaves just as a browser ?

I thought some sites are just throtteling the download speeds, but this shows something different, or a little inteligence.

Thanks for the reply.  To answer your question I've used wget both alone and with other commands.  Namely I've used "limit-rate" when I need bandwidth for other things, but this is only on the chromebook as I never even reach speeds that need to be slowed on the other machine.  I've also used -P to change download locations but I'm assuming that neither of these commands would affect the download rate.  That's an interesting point about the chromebook being too new.  Along that same line, perhaps it might have something to do with the Chrubuntu install as well.

---

### Post by kuifje09 on 2013-03-15
I had just a few days ago also a problem downloading an demo song ( real demo ) from an american site.
I could play it, but not download it.  Then after a lot of trying at once it did when I started wget and refreshed the browser page.
Only wget did not do the job, it always stopped after a few percent.
It was realy silly to see this, But I think they also tried to stop downloading outside the browser apps.

Edit: even downloadhelper did not do it.

---

### Post by bentoman1974 on 2013-03-15
I too thought about using a different downloading method or program, but its sounding more and more like its the site.

---

### Post by tombert on 2013-03-16
Have you tried setting [COLOR=#000000][FONT=monospace]--limit-rate to zero? I can remember an old distro of mine that had a default value there ...[/FONT][/COLOR]

---

### Post by bentoman1974 on 2013-03-17
> **tombert said:**
> Have you tried setting [COLOR=#000000][FONT=monospace]--limit-rate to zero? I can remember an old distro of mine that had a default value there ...[/FONT][/COLOR]

That occured to me as well and I have tried it to no success.

---

### Post by bentoman1974 on 2013-03-17
Interestingly enough, I just tried to download the exact same files using the "downloadthemall" add-on in firefox and I was able to do so at full speed.  Now I'm really scatching my head.

---

### Post by kuifje09 on 2013-03-17
Sometimes things hapen from no reason to be found. Which is silly. But there is a reason for shure.
Only who is able to tell.  I also run into such things sometimes.

---

