---
title: "How can I access External harddisk true console ?"
date: 2009-01-26
forum: Programming Talk
---

### Post by hoboy on 2009-01-26
I have an external harddisk that I can see "Name:41,2 GB Media", I have some files that I want to run how do I get to it in the console ?

---

### Post by Zugzwang on 2009-01-27
> **hoboy said:**
> I have an external harddisk that I can see "Name:41,2 GB Media", I have some files that I want to run how do I get to it in the console ?

I'm afraid that your question is not well-defined. You want to "run" files, so they are executables? It is not defined what it means to get a "disk into the console".

This is also the wrong forum since this one is about programming. 

I'll guess what you mean. If you run Ubuntu, there's a "Places" menu in the bar at (probably) the top of your screen. Your disk should be listed. Choose it from the menu. Then Nautilus opens and the disk is mounted. Then type "df" on the console. It shows you all mounts (in the column "mounted on"). One of it is your disk. Use the "cd" command to switch to that directory and you are "on the disk". Is this what you want?

---

### Post by Sand &amp; Mercury on 2009-01-27
Once you've mounted it you can access it by navigating to /media/ from your root directory.

Type 'dir' and you'll see your drive in there as a directory in there (usually 'disk' or something like that)

---

