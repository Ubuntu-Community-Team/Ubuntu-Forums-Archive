---
title: "compiz - The Composite extension is not available"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by jakupl on 2008-04-29
When I try to set the desktop effects to "extra", I get: The Composite extension is not available.

how do I change that?

I have;
ATI RC410 [Radeon Xpress 200M] and Gutsy Gibbon!

thank you very much :)

---

### Post by Alldan on 2008-04-29
install restricted drivers from system - administration - hardware drivers

---

### Post by jakupl on 2008-04-29
Have allready done it.
ATI accelerated graphics driver is in use :confused:

---

### Post by billgoldberg on 2008-04-29
I had the same issue with gutsy (don't happen with hardy).

You need to edit your xorg.conf file and change some line.

```
sudo gedit /etc/X11/xorg.conf
```

Then somewhere near the bottom you should see some mention of "composite". Change it from "0" to "1".

Save the file. 

It might be necessary to log out and back in.

note: I presume you already installed the graphics card.

---

### Post by jakupl on 2008-04-29
thanks. :)

Now my computer thinks a bit... then gives me this :"Desktop effects could not be enabled"

???

---

### Post by billgoldberg on 2008-04-29
mmm.

Strange.

Try rebooting.

---

### Post by jakupl on 2008-04-29
nope... no luck :(

---

### Post by jakupl on 2008-04-29
I don't understand why it won't work now... It has worked perfectly on previous Gutsy installs...

---

### Post by billgoldberg on 2008-04-29
EDIT:

this will most likely be what is causing the problem.

[http://www.linuxquestions.org/questions/linux-newbie-8/desktop-effects-could-not-be-enabled-ati-radeon-xpress-1100-compiz-635139/](http://www.linuxquestions.org/questions/linux-newbie-8/desktop-effects-could-not-be-enabled-ati-radeon-xpress-1100-compiz-635139/)

---

### Post by jakupl on 2008-04-29
this is what the terminal tells me when i enter 'compiz'

```
jakup@bobby:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```

---

### Post by billgoldberg on 2008-04-29
> **jakupl said:**
> this is what the terminal tells me when i enter 'compiz'

```
jakup@bobby:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```

Yes, you just need to install xgl.

I had to do it for 7.10, but not for 8.04 anymore.

Anyhow, I've written in my blog about doing it for 7.10, I'm pretty sure it will still be the same for 8.04.

[Link]("http://linuxowns.wordpress.com/2007/12/07/gutsy-gibbon-710-xgl-ati-fglrx-compiz-fusion/")

It should only take a minute or 2.

---

### Post by billgoldberg on 2008-04-29
If things shouldn't work after installing  

xserver-xgl

run compiz in the terminal again and give the error.

---

### Post by jakupl on 2008-04-29
It works perfectly now :) thankyou very much.

---

