---
title: "[SOLVED] typing &amp;quot;top&amp;quot; in terminal says 3 users, I am the only one"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Dutch70 on 2008-06-26
here is the first part of the output...

top - 18:50:33 up  3:39,  3 users,  load average: 0.02, 0.09, 0.12
Tasks: 138 total,   1 running, 137 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us,  0.5%sy,  0.0%ni, 98.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2067360k total,   987296k used,  1080064k free,    13736k buffers
Swap:  2096440k total,        0k used,  2096440k free,   429832k cached

why does it say 3 users? I am the only person that touches my computer?

 and while we're at it, when I open system monitor, it says that it is sending info to someone/something. How can I find out what is being sent, who it is sent to, and then maybe stop it? Or should I say, What am I misunderstanding here?...lol

---

### Post by sisco311 on 2008-06-26
```
who
```presumably you have 2 terminals open (you are logged in in 2 terminals) + GUI = 3

---

### Post by avtolle on 2008-06-26
Generally, with one user top will show two; root and USERNAME (your username on the computer). Along the left side, the name of each user is shown alongside the processes being run for each. Check the user names, and see if somehow, you are logged in twice as two separate users. 

On system monitor, there are packets being sent out (small ones) every so often, which I believe are for the purpose of determining whether the internet connection is still open, or the network is still up.

---

### Post by Dutch70 on 2008-06-26
Thanks sisco311, and avtolle,  and I'll skip the jokes about "who" you aren't an owl, you're a penguin. which I really like your lil penguin, looks like I feel. Def. a code I'll never forget now. lol
 I rebooted and now it shows 2 users, so, thats cool, still wish I knew how to check the info that is being sent. 
 No big deal, but my concerns are...is it some of the non-free stuff I have installed or just like you said, bout the internet connection.

 I'll go ahead and mark this solved, because for the most part it is. but if anyone wants to add to the info that is here please do so

---

### Post by sdennie on 2008-06-26
> **Dutch70 said:**
> Thanks sisco311, and avtolle,  and I'll skip the jokes about "who" you aren't an owl, you're a penguin. which I really like your lil penguin, looks like I feel. Def. a code I'll never forget now. lol
 I rebooted and now it shows 2 users, so, thats cool, still wish I knew how to check the info that is being went. 
 No big deal, but my concerns are...is it some of the non-free stuff I have installed or just like you said, bout the internet connection.

 I'll go ahead and mark this solved, because for the most part it is. but if anyone wants to add ot the info that is here please do so

You might be able to see what some of this traffic is using tcpdump.  Try:

```

sudo tcpdump -i any

```

---

### Post by NT4usB on 2008-06-26
iirc, netstat works in Linux... If not, there's a Linux equivalent.
Should show all the IPs connected to your machine.
If you have a hardware firewall (router) enable logging and you can see it there too.

---

### Post by Dutch70 on 2008-06-26
Ok "good stuff" this too "tcpdump -i any"(kinda scary),

 I am using a wireless router, and this PC is on the wireless adapter end. But, as much as I have read about that, being a noob to pc's in general. never really understood, still dont, but I have a lot more places to search now...lol, wish I knew how to search/find the info I'm looking for better. guess all things come with time though.

---

### Post by NT4usB on 2008-06-26
Searching these forums is about the best way to find stuff.
Pretty much everything that's ever been asked and answered is here somewhere. I find Google does a better job than the boards search engine. Type:
site:ubuntuforums.org [searchword] [searchword]
In the Google search window. Now you can use modifiers like quotes, +, -, etc., to focus your searches.
[http://www.google.com/search?num=50&hl=en&q=site%3Aubuntuforums.org++tcpdump+%22wireless+router%22&btnG=Search](http://www.google.com/search?num=50&hl=en&q=site%3Aubuntuforums.org++tcpdump+%22wireless+router%22&btnG=Search)

---

### Post by Dutch70 on 2008-06-27
"Now you can use modifiers like quotes, +, -, etc., to focus your searches."
oops that was a quote! 

 yeah, thats what I have to learn more about...and man pages

---

