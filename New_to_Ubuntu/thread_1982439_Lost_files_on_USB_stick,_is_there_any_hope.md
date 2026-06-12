---
title: "Lost files on USB stick, is there any hope?"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by Houmie on 2012-05-18
Hi,

I have a Patriot USB stick. These types of usb stick are quite fast but a bit exotic.  Ubuntu recognized it and I began moving a document folder to it to transfer it to another laptop.

I got some error messages regarding mount and everything was abrupted. I had even to restart Ubuntu to be able inserting any new USB stick to it.

Now t says 111 MB are used, but I cant see anything.  Is there a way to fix this? Linux has usually always a solution. Just wondering :(

Many Thanks,

---

### Post by Skara Brae on 2012-05-18
Uhh, in February I had the same "tragedy" happening to me - an USB stick full with files lost - due to a crappy USB hub, but I was able to get about 95% of them back with a demo of a program (whew!).

However, it was in Windows XP.

---

### Post by Houmie on 2012-05-18
So there is nothing on Ubuntu then?

What was that Windows program called?

---

### Post by Skara Brae on 2012-05-18
Houmie, my apologies - I've been going through 10 CD-r's and 2 DVD-r's, but I don't seem to have saved the demo program.

And I can't remember the name... :oops:
Piriform's "Recuva" found nothing on the USB drive (so, the demo program was not Recuva).

It was a demoversion that made me wait 5 seconds after every retrieval of a file. I found it via Google and it looked like the best one. It took me hours to get back most of my files.

Google gives results; do none help you out?

Is this of any help? [https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")
-- It says it's only Ubuntu 7/8. Is there no such info for 9/10/11/12?

Here is another link: using a Live CD:
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/]("http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/")

I am sorry, Houmie: I am no Ubuntu expert. Someone smarter will have to help you.

---

### Post by Skara Brae on 2012-05-18
"DiskDigger".

[http://diskdigger.org/]("http://diskdigger.org/")

That was it. But like I said, the demo version makes you wait 5 seconds after every recovered file.

---

### Post by Houmie on 2012-05-18
Hey,

Thank you very much for your kind help.

An older free windows version is still offered here:

[http://www.portablefreeware.com/index.php?id=1477](http://www.portablefreeware.com/index.php?id=1477)

But the cool thing is the latest version is free for Linux.
However it requires Mono.  Unfortunately Mono isn't part of Ubuntu 12.04 any longer. Hence its a hassle to install.

Recuva seems to be more intuitive by the way. It worked better than diskdigger and its freeware.

---

### Post by rmjones85 on 2012-05-18
try scalpel

type "apt-get isntall scalpel" (without the quotes) in your favorite search engine
and you'll find everything you need to know.

---

### Post by Eagle7261 on 2012-05-19
> **rmjones85 said:**
> try scalpel

type "apt-get isntall scalpel" (without the quotes) in your favorite search engine
and you'll find everything you need to know.

close...
for those more noob than I
This would actually be the 'Terminal' (Ctrl+Alt+T to open) command, not google search.

the line would be:
(with spelling corrected)

sudo apt-get install scalpel

---

### Post by jtarin on 2012-05-19
How was the stick formatted?

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

---

