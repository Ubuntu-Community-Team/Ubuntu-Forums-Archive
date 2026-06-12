---
title: "Connecting two computers using ethernet port/wire"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Canis familiaris on 2008-05-22
Hi there
I want to connect my Ubuntu Desktop PC to an HP Notebook with Windows XP Pro. All I have an ethernet wire and ethernet ports on both the computers. Is there any way that I could network the two PCs and share data among them.
Thanks in advance

---

### Post by spiderbatdad on 2008-05-22
Shouldn't be too much trouble. You need a "cross-over" cable...which consists of two separate methods on each end: A and B. Then XP has to be set up for networking. I did this 5-6 years ago, and had some issues ( I can;t remember) but did eventually resolve them. Not sure what Linux config will be necessary for the networking...most likely smbfs.

Found a picture:

---

### Post by Canis familiaris on 2008-05-22
> **spiderbatdad said:**
> Shouldn't be too much trouble. You need a "cross-over" cable...which consists of two separate methods on each end: A and B. Then XP has to be set up for networking. I did this 5-6 years ago, and had some issues ( I can;t remember) but did eventually resolve them. Not sure what Linux config will be necessary for the networking...most likely smbfs.

What is a "cross-over" cable? I only have an ethernet wire.

---

### Post by spiderbatdad on 2008-05-22
Found a picture....added it to previous post.
You can try to make your own...I need a magnifying glass to see closely enough that all wire ends get pushed in far enough.
I don't know any other method for networking with just a cable.

---

### Post by signseeker on 2008-05-22
A cross-over cable allows you to simply hook to (only)two PCs up together using ethernet ports. 

If using standard cable you need an ethernet hub. 

Personally I prefer the second method.

---

### Post by Canis familiaris on 2008-05-22
So I couldn't connect the two PCs using just two ethernet ports and an ethernet wire?

---

### Post by Canis familiaris on 2008-05-22
bump

---

### Post by spiderbatdad on 2008-05-22
Why bump a thread that has been answered?
You can connect two computers with an ethernet cable. To share data the cable has to be configured as a crossover, as shown in the picture above. Either make the cable, or purchase one. A switch or hub would be ideal, then you would not use the crossover method, just a straight patch cable.

---

### Post by rbc on 2008-05-22
You can if:
-you have 1 GB connections, or
-you have, as signseeker pointed out, a hub or a switch in between them.
Crossover cable is the same as ethernet cable but four of the eight wires are in different positions at one end, then at the other end, as spiderbatdad's picture shows. So, you can buy a hub, buy crossover cable, or if you have a crimper and a plug, make it yourself

---

### Post by scouser73 on 2008-05-22
Here's a picture of what a Crossover Cable looks like.

I hope it's of use to you.

[IMG]http://img237.imageshack.us/img237/897/use20for20all20crossovede9.jpg[/IMG]

---

### Post by Paqman on 2008-05-22
> **Anurag_panda said:**
> So I couldn't connect the two PCs using just two ethernet ports and an ethernet wire?

You can get a crossover adaptor that turns your regular ethernet cable into a crossover one. You should be able to pick one up off eBay for peanuts, or else go to your local electronics store.

---

### Post by jimv on 2008-05-22
A "crossover" cable is an ethernet cable that has the send and receive wires swapped on one end, so the send wires on one end go into the receive wires on the other end.  A regular ethernet cable has the send wires on one end going into the send wires on the other end, which is fine if you're connecting your computer to a hub or router,but doesn't work with two computers.  It's like two cars trying to drive in opposite directions on a one lane road.

---

### Post by cetheriel on 2008-07-19
say, i have the right cable. i do have it.
and i have a ubuntu 7.10 laptop and a 8.04.1 desktop.
how do i connect both with ethernet?

---

