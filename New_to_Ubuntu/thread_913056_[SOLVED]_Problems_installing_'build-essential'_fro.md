---
title: "[SOLVED] Problems installing 'build-essential' from disk"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by mmmmm_PIE on 2008-09-07
Hey!
New to Ubuntu/Linux and having some basic problems. Thanks in advance for any help!

I'm trying to install the C++ compiler apparently packaged with the OS in 'build-essential' (sudo apt-get install build-essential) but running into problems. During the process, it seems Linux attempts to access libraries at ca.archive.ubuntu.com and fetch a number of somethings... all these attempts fail, and the installation halts.

The error message suggests I run apt-get update, but when I try, I am informed that I was 'unable to lock the list directory'.

Where do I go from here.

---

### Post by Shazaam on 2008-09-07
When you see the "lock" message (while updating) it usually means you have more than 1 update program running at a time (Auto-Update, Synaptic, apt-get from the terminal). Close all but one.
You can go to Software Sources and temporarily uncheck everything but the entry for your cdrom if you aren't connected to the internet. Or you can ignore the unreachable (failed to fetch) errors. You will still be able to use the livecd.

---

### Post by Sycron on 2008-09-07
> **mmmmm_PIE said:**
> 
The error message suggests I run apt-get update, but when I try, I am informed that I was 'unable to lock the list directory'.

 You must ```
sudo apt-get update
```. Are you connected to Internet?

---

### Post by mmmmm_PIE on 2008-09-07
^Editing Software Sources worked like a charm, Thanks!

---

### Post by Sycron on 2008-09-07
> **mmmmm_PIE said:**
> ^Editing Software Sources worked like a charm, Thanks!

You're welcome.

---

### Post by Shazaam on 2008-09-07
Don't forget to re-enable them.

---

