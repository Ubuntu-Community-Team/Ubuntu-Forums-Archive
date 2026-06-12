---
title: "Locating a file on a HDD ( /media/)"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by Rebel Yellow on 2012-02-21
I am quite new to Ubuntu as I installed the operating system last night on my laptop. I was surprised to see how smooth the transition was even though I made the big jump and decided to use it as my only OS. Prior to my installation, I have backed most of my files on an external hard drive so I could restore my media libraries to what they once were.

Now the problem I am experiencing, is that the hdd seems to be located in /media/, however when I start my my e-book management software and want to direct it to a folder on my external HDD, I cannot seem to find said /media/ folder. Is it located somewhere in Home?

I'm really sorry if this sounds like a silly question, but I am really clueless about ubuntu and linux in general. ( Perhaps I should actually buy a E-book on the subject ! )

---

### Post by roelforg on 2012-02-21
Read the first line of my signature

Finding is easy, open a terminal.
Run (replace <filename> with the filename you're searching for):
```

find /media | grep "<filename>"

```
Ignore the first 2 sections between the / and / (e.g media and the mount name from your hdd) the rest should be the path to the filename on your hdd.

---

### Post by JC Cheloven on 2012-02-21
> **Rebel Yellow said:**
>  Now the problem I am experiencing, is that the hdd seems to be located in /media/, 
Yes, an external usb disk will be mounted most likely under /media

> however when I start my my e-book management software and want to direct it to a folder on my external HDD, I cannot seem to find said /media/ folder. Is it located somewhere in Home?

Could you please clarify what is that software, and where are you running it from? Sorry if I didn't understand, but I'd expect you to be running a program as [Calibre]("http://calibre-ebook.com/") from within ubuntu to manage your ebook libraries and physical connection. Is that the case?

---

