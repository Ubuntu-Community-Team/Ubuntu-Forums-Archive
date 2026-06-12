---
title: "Linux System from source"
date: 2006-12-28
forum: Programming Talk
---

### Post by rekahsoft on 2006-12-28
Hi all, i was just wondering how i would go about building a linux system directly from source (like i mean like DIRECTLY from source no distro to start or anything, just a blank harddisk). This is what i think i would do (correct any problems with a good explaination):
1. Build gcc for my architecture
2. Build the linux kernel for my architecture
3. Build X-server for my architecture
4. Install graphics driver (fglrx for me)
5. Configure X-server
6. Build software that i would like
7. Configure

I know the list is far from complete. One thing i do not know is how to make it a debain system (use .deb) or Redhat system (use .rpm). Also is there a way to use both? cause that would be really neat :)

P.S: What all goes together to make a linux system

---

### Post by ZylGadis on 2006-12-28
[http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

---

### Post by po0f on 2006-12-28
[Gentoo](http://www.gentoo.org/), for something a little less hardcore than LFS.

---

### Post by rekahsoft on 2006-12-28
Thanks :) i will not be trying a source install until i have a test machine :)

---

### Post by amo-ej1 on 2006-12-29
You missed 'a' bootloader in you initial list. Having a kernel is nice but you'll need something to tell you bios where the find it and have it kickstarted from there.

---

### Post by rekahsoft on 2006-12-29
> **amo-ej1 said:**
> You missed 'a' bootloader in you initial list. Having a kernel is nice but you'll need something to tell you bios where the find it and have it kickstarted from there.

oops, thanks for the additive

---

### Post by derby007 on 2006-12-30
If u are going ahead with this: why not keep a log of everything u do : & build a nice little how-to for others to follow........ I was thinking of doing the same but i probably havent the time/patience, 
maybe this book might come in handy, then maybe u already have some Linux material at your disposal...

Running Linux, 5th Edition 
By Matthias Kalle Dalheimer, Matt Welsh 
............................................... 
Publisher: O'Reilly 
Pub Date: December 2005 
Pages: 972

---

### Post by rekahsoft on 2006-12-30
> **derby007 said:**
> If u are going ahead with this: why not keep a log of everything u do : & build a nice little how-to for others to follow........ I was thinking of doing the same but i probably havent the time/patience, 
maybe this book might come in handy, then maybe u already have some Linux material at your disposal...

Running Linux, 5th Edition 
By Matthias Kalle Dalheimer, Matt Welsh 
............................................... 
Publisher: O'Reilly 
Pub Date: December 2005 
Pages: 972

i have seen this book before and was thinking of buying it but i have to buy some other books first...i do have the Linux from Source book downloaded (it is a free download) and i am getting a test machine ready to do a source install. I will surely post my notes, comments, and how i did it when the time comes. (Note: it might take me a while to have the system up and running and have the time to do the source install).

---

