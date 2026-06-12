---
title: "wvdial Verizon dial-up connection"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by jaredssix on 2008-10-10
Hey all,
I am using wvdial to obtain a connection with Verizon dial-up, and not connecting. My modem appear to be functioning, as it dials my IP number and communicates (apparently one-sidedly) with the IP. My terminal relays that there are authentication issues. The numbers and passwords are the same as those entered into a resident Macintosh, and the Mac connects no problem. 

Any ideas?

---

### Post by phidia on 2008-10-10
You need to open a terminal and enter this: > sudo pppconfig
That creates files and users for ppp to work correctly.

For more details see the Ubuntu [dial up wiki]("https://help.ubuntu.com/community/DialupModemHowto").

---

### Post by jaredssix on 2008-10-10
Thanks for the quick response.

What's peculiar is that the terminal interface tells me my password is bad, though I know that it is not. I have tried logging in without a password, to no avail. I have tried curly and straight brackets around the password, and no space preceding the password.

Ultimately, I don't know how to communicate this password to the IP.

---

### Post by phidia on 2008-10-10
You mean the password to your ISP correct? Also instead of wvdial try to get and install gnome-ppp that package is available from the repos, but if you are not connecting with ubuntu...

After setting up ppp with pppconfig try using "pon" to connect and "poff" to disconnect.
pppconfig sets up your password and all the files you should need to connect.

---

### Post by jaredssix on 2008-10-10
Okay, I am connected! Thanks for the tips. Sadly, with my hsf Dell modem I can't exceed 3 kB/sec. That's even slow in a text-based browser!

I'll keep digging, and thanks for your help.

---

### Post by phidia on 2008-10-10
> **jaredssix said:**
> Okay, I am connected! Thanks for the tips. Sadly, with my hsf Dell modem I can't exceed 3 kB/sec. That's even slow in a text-based browser!

I'll keep digging, and thanks for your help.

I believe that there's a guide for that modem in the Ubuntu wiki.

---

### Post by jaredssix on 2008-10-10
For everyone(who lives out in the sticks like me)'s info, I installed a Linuxant hsf driver for my Dell's dial up modem. Understanding that different phone lines do make a difference, the FREE version ran my modem at <3Kbps. The licensed version (available through the Linuxant site for $20 US) boosted my signal to <9 Kbps. 

Lynx, anyone?

---

