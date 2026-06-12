---
title: "kded4 100% cpu"
date: 2011-08-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jmacak on 2011-08-20
Hi

Testing out kubuntu on my ASUS 1000HE, alpha 3 works pretty good.  Last week or so updates have caused kded4 to use up about 100% cpu.

Anyone else seeing this?  

I reinstalled from yesterday's daily build and still see kded4 at 100%.

cheers

joe

---

### Post by elgordodude on 2011-08-20
Well it's an atom, so that won't help matters, but it shouldn't be that high that often.

Is it possible for you to run htop and take a screenshot? Or just see if you spot the culprit there.

---

### Post by jmacak on 2011-08-20
Hi


So, here's what htop is showing.

Looks like one of the updates, last week or so, caused this to start happening.  (I saw it immediately because I keep a cpu monitor at the top of the screen.)

cheers

joe

---

### Post by buzzmandt on 2011-08-20
that should be this, with fix coming:
[https://launchpad.net/ubuntu/oneiric/+source/ntrack/014+bzr312-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/ntrack/014+bzr312-0ubuntu2)

> Add link_ntrack-libnl_to_libntrack.patch: Link ntrack-libnl to libntrack
    as it uses symbols from that library. This caused kded4 to be unable to
    load the module and enter an infinite loop.

---

### Post by jmacak on 2011-08-20
> **buzzmandt said:**
> that should be this, with fix coming:
[https://launchpad.net/ubuntu/oneiric/+source/ntrack/014+bzr312-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/ntrack/014+bzr312-0ubuntu2)

Hi

Yes, sounds promising.  I'll keep an eye open for that update.

Thanks.

Joe

---

### Post by jmacak on 2011-08-20
Hi

Looks like maybe it's fixed?

I applied today's updates and kded4 no longer hogs cpu.

Thanks for your help.

cheers

joe

---

### Post by Geidrow on 2011-09-30
Could you please give detailed instructions to fix this - I did not understand what user should do with this :«Add link_ntrack-libnl_to_libntrack.patch: Link ntrack-libnl to libntrack»?
Thank you in advance

---

