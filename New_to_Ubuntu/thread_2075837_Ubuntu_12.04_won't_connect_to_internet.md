---
title: "Ubuntu 12.04 won't connect to internet"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by Cinnamonbun23 on 2012-10-24
I'm having a problem connection to the internet on Ubuntu 12.04. I've dual booted my Toshiba laptop that can pre-installed with windows 7 with ubuntu using wubi. My internet connects to my router just fine but when i boot up ubuntu it connects to internet for a couple of minutes then it disconnects from my router. Can somebody please help me 

Thanks in advance

---

### Post by TheFu on 2012-10-24
To help, we need facts and data.
* what hardware are you using?  'lshw' or 'lspci' or 'lsusb'
* what specific driver(s) are you using?  'lsmod'
* is your connection wired or wifi?
* what do the log files show? These are in /var/log/ with names syslog and messages
* what do the router logs show?

Facts and data, please.

---

### Post by critin on 2012-10-24
> **Cinnamonbun23 said:**
> I'm having a problem connection to the internet on Ubuntu 12.04. I've dual booted my Toshiba laptop that can pre-installed with windows 7 with ubuntu using wubi. My internet connects to my router just fine but when i boot up ubuntu it connects to internet for a couple of minutes then it disconnects from my router. Can somebody please help me 

Thanks in advance

Does it work in Windows?  Is it (internet) on when you boot up, or do you turn it on afterwards?
Have you tried resetting the modem/router?  Turning off (power off) the machine, router, modem, waiting a minute, then turning it back on in reverse order?

---

### Post by Cinnamonbun23 on 2012-10-28
Internet works fine in windows but whenever I boot up ubuntu the  internet will work for about 10 maybe 15 minutes then it disconnects and  it ask me for the wep key and I enter it and it never reconnects. No I haven't tried resetting my router but I can try and respond back.

---

### Post by cellarweasel on 2012-10-28
So Cinnamonbun23 that sounds to me like it is a programming problem. Just open Terminal and copy and paste: 
sudo <answer with your password>
lshw 
lspci
lsusb
lsmod

Then copy and paste the output into a document like in gedit. 


* what hardware are you using? 'lshw' or 'lspci' or 'lsusb'
* what specific driver(s) are you using? 'lsmod'

just like what TheFu listed off as ways to get to the bottom of driver bugs. You don't need to know what any of the junk those commands spew means. Just let us know so that we can tell what is inside your laptop. 

P.S. This is unfortunatly the most diffucult part of using the linux kernel and it's ironic because it's always the first thing that happens to people. It happened to me three years ago. I didn't start actually liking any linux distro until I got a desktop. 

-cellarweasel

---

### Post by Cinnamonbun23 on 2012-10-28
Ok so i tried resetting my router and i still can't pick up wireless internet from my router or a wired connection but I was able to pick up an wifi connection from my neighbor who doesn't have a password on their connection. I'm not sure if that helps. I'll go try that sudo make thing and report back

---

### Post by Cinnamonbun23 on 2012-10-29
ok so i did the sudo thing in the terminal and since I get no internet on ubuntu i had to take a picture of the command info. If you have problems seeing the pictures let me know and I'll try and enhance them or I'll actually type out all the info.

the commands I entered where lshw, lspci, lsusb and lsmod
if you need anymore information let me know and I had to upload 2 sets of pics 

Thanks

---

### Post by Cinnamonbun23 on 2012-10-29
this contains the rest of the lshw stuff and the lspci and lsusb stuff and one page of the lsmod

---

### Post by Cinnamonbun23 on 2012-10-29
this is the last page of the lsmod. Sorry if this is all scattered I didn't know how else I could get the info on here since internet's not working.

---

