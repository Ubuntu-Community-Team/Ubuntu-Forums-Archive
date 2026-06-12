---
title: "hexcat - free software?"
date: 2008-01-10
forum: Programming Talk
---

### Post by yurimxpxman on 2008-01-10
Today, I stumbled upon a nifty tool called `hexcat`. I was very interested in it, so I downloaded the source code with apt-get.

Much to my dismay, it was not released under the GPL. This may not be such a problem since the copyright states that it can be freely distributed under the condition that the copyright message stays in tact, and this set my mind at ease for a moment.. until I found the file "src/data.bin".

AFAICT, the source code to this program is not included anywhere in the tarball. Is hexcat free software?

---

### Post by CptPicard on 2008-01-10
> **yurimxpxman said:**
> 
AFAICT, the source code to this program is not included anywhere in the tarball. Is hexcat free software?

Not in the sense of the GPL, but I think the license is quite explicit in granting distribution rights as long as the single condition is fulfilled, so where's the problem?

---

### Post by yurimxpxman on 2008-01-10
> **CptPicard said:**
> Not in the sense of the GPL, but I think the license is quite explicit in granting distribution rights as long as the single condition is fulfilled, so where's the problem?

What exactly do you mean by "not in the sense of the GPL"? Are you saying "it's free software, just doesn't use the license", or that as long as it can be legally distributed, it's ok?

After rereading the copyright info again, I realised that it does not explicitly grant permission for others to modify it.

---

### Post by CptPicard on 2008-01-10
If you look at it from the Stallman-style ideological angle, no it is not free software "in the sense of the GPL", because the idea of the GPL is to keep the source open and allow modification based on it.

So it's free as in beer but not as in speech, although the license is as permissive as they get... you just don't get the source with it.

---

### Post by yurimxpxman on 2008-01-10
> **CptPicard said:**
> If you look at it from the Stallman-style ideological angle, no it is not free software "in the sense of the GPL", because the idea of the GPL is to keep the source open and allow modification based on it.

So it's free as in beer but not as in speech, although the license is as permissive as they get... you just don't get the source with it.

I wasn't ever referring to "free as in beer". Perhaps I should have stated this specifically.

If it's not completely free software, I suppose I'll write a free version licensed under the GPLv3 :)

---

### Post by CptPicard on 2008-01-10
> **yurimxpxman said:**
> I wasn't ever referring to "free as in beer". Perhaps I should have stated this specifically.


Well, if you know the difference, it should be obvious it's not ideologically free software, no? ;)

---

### Post by yurimxpxman on 2008-01-10
Silly me.. data.bin is merely a binary of the provided source code.

---

### Post by CptPicard on 2008-01-10
Interestingly, it probably still isn't properly free software, as the source isn't "liberated" perpetually by putting it and its derivatives under the GPL.

Of course, there is probably nothing that keeps you from just sticking GPL on top of the source should you choose to modify it... I wonder what would happen if GPL would conflict with some other branch of the same source that was closed by Micr^H^H some evil corporate hacker?

---

### Post by ghostdog74 on 2008-01-10
> **yurimxpxman said:**
> Today, I stumbled upon a nifty tool called `hexcat`. I was very interested in it, so I downloaded the source code with apt-get.

Much to my dismay, it was not released under the GPL. This may not be such a problem since the copyright states that it can be freely distributed under the condition that the copyright message stays in tact, and this set my mind at ease for a moment.. until I found the file "src/data.bin".

AFAICT, the source code to this program is not included anywhere in the tarball. Is hexcat free software?

what can hexcat do that your current tool sets in your system cannot?

---

### Post by yurimxpxman on 2008-01-10
> **ghostdog74 said:**
> what can hexcat do that your current tool sets in your system cannot?

It's the only hex viewer I know of that doesn't use ncurses. I like the fact I can pipe the data to and from applications. Then again, that doesn't do a *whole* lot of good since it can't modify the data.

I suppose it's more of a novelty than anything (eg, displaying block devices and stdin)

---

### Post by ghostdog74 on 2008-01-10
I use kde, so I have one called khexedit.  If you want command line hex viewer, you can try hexdump

---

### Post by engla on 2008-01-10
Is it the same as the debian [hexcat package]("http://packages.debian.org/sv/etch/hexcat")? If so, it is free software.

It sounds like that hexcat does the same job as the ubiquitous xxd utility.

---

### Post by yurimxpxman on 2008-01-10
> **engla said:**
> 
It sounds like that hexcat does the same job as the ubiquitous xxd utility.


Indeed it does. I'm surprised I've never heard of that tool before. I like it better than hexcat. Thanks! :)

---

