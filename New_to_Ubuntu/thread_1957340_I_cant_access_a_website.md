---
title: "I cant access a website"
date: 2012-04-12
forum: New to Ubuntu
---

### Post by abnordude on 2012-04-12
Tamilwire is that website......


[http://mp3.tamilwire.com/](http://mp3.tamilwire.com/)


I dunno what is the reason, but I can access it on my phone.
However I cant access it through any of the browsers in my computer...

Help me please.....

---

### Post by 2F4U on 2012-04-12
No problem here. What version of Ubuntu and what browser do you use? Can you access other web sites?

---

### Post by abnordude on 2012-04-12
I use debian squeeze...

---

### Post by tea for one on 2012-04-12
> **abnordude said:**
> I use debian squeeze...

Does Debian Squeeze use Firefox?

As a suggestion to troubleshoot the problem, can you boot up a live CD of Ubuntu and try to visit the site using a wired connection?

The live CD will not have mp3 codecs installed but I am curious to ascertain if the site is accessible?

---

### Post by abnordude on 2012-05-08
> **tea for one said:**
> Does Debian Squeeze use Firefox?

As a suggestion to troubleshoot the problem, can you boot up a live CD of Ubuntu and try to visit the site using a wired connection?

The live CD will not have mp3 codecs installed but I am curious to ascertain if the site is accessible?


Well.....sorry for the late answer.......But i'm currently on arch linux.....and i am unable to access that website (means not able to access on both debian and arch)......M gonna try with the ubuntu live disc.....

---

### Post by CharlesA on 2012-05-08
> **abnordude said:**
> Well.....sorry for the late answer.......But i'm currently on arch linux.....and i am unable to access that website (means not able to access on both debian and arch)......M gonna try with the ubuntu live disc.....
Are you able to ping the site by hostname? That would help narrow down if it's a DNS issue or not.

---

### Post by abnordude on 2012-05-08
> **CharlesA said:**
> Are you able to ping the site by hostname? That would help narrow down if it's a DNS issue or not.

could you explain how to do this?

---

### Post by CharlesA on 2012-05-08
> **abnordude said:**
> could you explain how to do this?
Open a terminal and run:

```
ping -c 4 mp3.tamilwire.com
```

---

### Post by SeijiSensei on 2012-05-08
Can you or other friends in India access that site from Windows?  Maybe there's region-blocking at work?  It opens fine in my browser from here in the US.

This sounds like it might be pertinent!
[http://www.thinkdigit.com/forum/technology-news/154166-kolkata-court-orders-isps-block-music-pirating-sites.html](http://www.thinkdigit.com/forum/technology-news/154166-kolkata-court-orders-isps-block-music-pirating-sites.html)

tamilwire.com is in the list here:
[http://idigid.wordpress.com/2012/03/16/the-indian-music-industry-is-blocking-104-music-websites-we-have-the-list/](http://idigid.wordpress.com/2012/03/16/the-indian-music-industry-is-blocking-104-music-websites-we-have-the-list/)

Maybe your phone provider isn't toeing the line.

---

### Post by abnordude on 2012-05-09
> **CharlesA said:**
> Open a terminal and run:

```
ping -c 4 mp3.tamilwire.com
```


I get this....

ping: unknown host mp3.tamilwire.com

---

### Post by CharlesA on 2012-05-09
DNS problem and/or it is being blocked.

---

### Post by jockyburns on 2012-05-09
Does sound like it's being blocked by your ISP.

---

### Post by abnordude on 2012-05-09
> **jockyburns said:**
> Does sound like it's being blocked by your ISP.

But i've downloaded songs from that website...there was no prob then....also it was the same ISP.....have I changed something??? is that the problem?

---

### Post by |{urse on 2012-05-09
Whelp I'm currently browsing that site with no problems via proxy in Mumbai. Sounds like some nice admin blocked you or your specific IP range for whatever reason. (try a proxy if you're feelin froggy?) Fully loving the music in the chat section. I would not recommend this site to windows users, it smells naughty. :)

---

### Post by abnordude on 2012-05-12
> **|{urse said:**
> Whelp I'm currently browsing that site with no problems via proxy in Mumbai. Sounds like some nice admin blocked you or your specific IP range for whatever reason. (try a proxy if you're feelin froggy?) Fully loving the music in the chat section. I would not recommend this site to windows users, it smells naughty. :)

And how do i do that?

---

### Post by jockyburns on 2012-05-12
You could try accessing the site via [www.hidemyass.com](www.hidemyass.com) 
Go there first then you'll see a window in which to enter the site you want to go to. Here in the UK some ISP's have been ordered to block Piratebay, but people can still access the site via hidemyass. 
Simples

---

### Post by abnordude on 2012-06-07
> **jockyburns said:**
> You could try accessing the site via [www.hidemyass.com]("http://www.hidemyass.com") 
Go there first then you'll see a window in which to enter the site you want to go to. Here in the UK some ISP's have been ordered to block Piratebay, but people can still access the site via hidemyass. 
Simples

Totally cool....
Now I'm able to access the website....

Thanks....

Big Help.....

Also thanks to everyone who has helped....

---

### Post by MisterGaribaldi on 2012-06-07
Obviously this has been solved, but I just wanted to toss this out for what it's worth (probably not much, I guess)...

A number of years ago, I had a local dial-up ISP which, at some point, decided to block all of the other local ISP's home pages. They were a pretty "meh" ISP anyhow.

---

