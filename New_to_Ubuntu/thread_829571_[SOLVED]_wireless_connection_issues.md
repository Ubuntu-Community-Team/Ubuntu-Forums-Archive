---
title: "[SOLVED] wireless connection issues"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by kavmac on 2008-06-14
hello,

i just purchased a hp dv0000 (dv9894ca) laptop, and got my hardy partition up and running today.  i followed the tutorial [here]("http://ubuntuforums.org/showthread.php?t=769990&highlight=dv9000") to get my network card configured.  all is well, except when i actually go to enter my passcode for our wireless internet.  i know that the passcode is the right one, as my vista partition and my psp both connect nicely.  infact, i was able to make a connection to it for a whole 5 minutes, and during that time i would either have a strong connection or 0% connection...  after i completely lost that connection, i keep getting the message when i hover over the little connection animation that it's waiting for the network key...  any idea how i could actually get the connection to complete?  oh, and is there a way, once the wireless connection is stable, to have hardy remember the security info so it doesn't have to be entered each and every time?

thanks :)

---

### Post by kavmac on 2008-06-15
*bump*

---

### Post by sam_delta on 2008-06-15
what drivers/method you followed to install the drivers? also, which wireless card does your computer have, you can check by posting the output of the command
```
lspci
``` open it at applications>accesories>terminal , type the command, and post the output

sam

---

### Post by vikramaditya on 2008-06-15
Hi, Kav :)

I was getting error messages from the Gnome **Network Manager** during restart & shutdown in Hardy, so I googled a bit and found herds of folks who've dumped Network Manager in favor of **Wicd** - _especially_ for wireless connection problems (mine's wired, so no issue on that count).

Anyway, I installed Wicd & it "just works".  No more stinkin' Network Manager error messages, either. :)  There are a number of more-or-less helpful tutorials available via google.  Sorry, but I don't recall which one turned the key for me!

---

### Post by sam_delta on 2008-06-15
mis post,,,,, any admin can delete this post please?

---

### Post by Lacrimstein on 2008-06-15
So wait: You are able to connect, but the connection is extremely unstable? If you are unable to connect at all, and you are using WEP, try choosing the WEP Hex encryption instead of ASCII. And to answer your second question, I think it is remembered automatically although I'm not sure, since I use wicd as well.

---

### Post by kavmac on 2008-06-15
i was able to connect once.  but only once.  i'm in vista right now so i can't get the output of that command... but i've got a broadcom somethin somethin (i'll check when i get up in the morning and have a wired connection again).  i gave the link for the instructions i found, i'll give it again :)  
[http://ubuntuforums.org/showthread.php?t=769990&highlight=dv9000](http://ubuntuforums.org/showthread.php?t=769990&highlight=dv9000)

i'll look into wicd tomorrow as well.  i read a little bit about it earlier, but from my lack of sleep lately i was having trouble following and molding it to my own situation...



thanks for all of the suggestions!  i'll come bearing some more info in 9 hours or so :)

---

### Post by sam_delta on 2008-06-15
alright, to install wicd, you just type
```
sudo apt-get install wicd
```

make sure you have a wired connection to install
it will appear under applications>internet>wicd i believe

sam

---

### Post by kavmac on 2008-06-15
okay, so i installed wicd this morning.  it found our network, i entered the key.  and it tries to obtain an ip address, but never succeeds.  wired is working great (as per usual).  so i'm still stuck on the whole obtaining a wireless connection...

haha maybe it helps if i select the proper type of encryption key to enter.... and here i thought i got enough sleep last night!

got it working!



thanks everyone for your assistance!

---

### Post by sam_delta on 2008-06-15
glad its working bro

enjoy ubuntu :)
sam

---

### Post by kavmac on 2008-06-15
i'm a gal, but thanks :)

---

