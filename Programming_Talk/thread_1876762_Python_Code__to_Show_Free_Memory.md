---
title: "Python Code  to Show Free Memory"
date: 2011-11-06
forum: Programming Talk
---

### Post by MickSulley on 2011-11-06
Hi,

I would like to create Python code to monitor the amount of free memory or swap space.  Is there any way to do this?

Thanks
Mick

---

### Post by Bachstelze on 2011-11-06
Define "monitor".

---

### Post by cgroza on 2011-11-06
Look at the code of other programs. They sure must be using an API.

---

### Post by ofnuts on 2011-11-06
> **MickSulley said:**
> Hi,

I would like to create Python code to monitor the amount of free memory or swap space.  Is there any way to do this?

Thanks
MickRead the pseudo-file /proc/meminfo

---

### Post by MickSulley on 2011-11-07
> Read the pseudo-file /proc/meminfo

Brilliant!  Just what I wanted.

The background is that I had an unfortunate incident with a server recently when it ran out of swap space.  I am looking for a way to send me an email before things get that bad.

Thanks for your help
Mick

---

### Post by ofnuts on 2011-11-07
> **MickSulley said:**
> Brilliant!  Just what I wanted.

The background is that I had an unfortunate incident with a server recently when it ran out of swap space.  I am looking for a way to send me an email before things get that bad.

Thanks for your help
MickUsually you have just a handful of suspects (server processes) and you can also get info about them in /proc/{pid}

---

