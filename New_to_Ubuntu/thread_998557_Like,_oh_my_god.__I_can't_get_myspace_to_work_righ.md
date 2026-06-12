---
title: "Like, oh my god.  I can't get myspace to work right."
date: 2008-11-30
forum: New to Ubuntu
---

### Post by w.g.hanna on 2008-11-30
Seriously - when I try to find freinds by shool, I get to a screen that shows me everyone from that school, but there is a box at the top that lets me narrow the results.  after i pick things like graduation year and age, i click a box at the lower left hand corner that says "update". the button changes color to indicate its been pressed but nothing happens.  

i've tried it in firefox, epiphany, and the one with the japanese name.  none work.  

Any ideas? 

PS this isn't the only myspace feature that doesn't work exactly right.  if you use the chat feature in windows, you can open up another user's profile in another window from the chat room.  doesn't  work in ubuntu.

---

### Post by hardyn on 2008-11-30
do you need flash / java jre ?

try installing flash from the adobe web site.

jre can be found through the repos.

---

### Post by linux_tech on 2008-11-30
If you installed 8.1 and havn't yet updated multimedia- java, video streaming, etc then this will help get web media going 

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

---

### Post by HittingSmoke on 2008-12-01
> **w.g.hanna said:**
> Seriously - when I try to find freinds by shool, I get to a screen that shows me everyone from that school, but there is a box at the top that lets me narrow the results.  after i pick things like graduation year and age, i click a box at the lower left hand corner that says "update". the button changes color to indicate its been pressed but nothing happens.  

i've tried it in firefox, epiphany, and the one with the japanese name.  none work.  

Any ideas? 

PS this isn't the only myspace feature that doesn't work exactly right.  if you use the chat feature in windows, you can open up another user's profile in another window from the chat room.  doesn't  work in ubuntu.

Ever since Flash 10 I havent been able to upload photos using the Flash based installer. I have to use the HTML form and upload one at a time and I take a lot of pictures on trips so it's a real pain.

---

### Post by o.besner on 2008-12-01
Adobe released a 64-bit version of Flash like 2 weeks ago and it rocks. That might solve it if it's a flash issue. 

If it's java, try OpenJDK6. It works flawlessly for me, and I can't say the same for JRE.

---

### Post by hardyn on 2008-12-02
JRE is simply java runtime environment... open JDK (java development kit) would contain a JRE (java runtime environment)

---

