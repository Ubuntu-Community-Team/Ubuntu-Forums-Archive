---
title: "Bug with Wine in Ubuntu Hardy"
date: 2008-10-27
forum: Philippine Team
---

### Post by icodeme on 2008-10-27
I installed winehq in my ubuntu 8.04.1. Somehow after the installation, my cursor gets lost whenever wine is in focus. is there someone else in there who knows the fix for this?

Thank you and God Bless:confused:

---

### Post by gtechmyk on 2008-10-27
try to reinstall your wine dude.. follow this steps:

[PHP]sudo apt-get update[/PHP]
[PHP]sudo apt-get install wine[/PHP]
[PHP]sudo apt-get install winesetuptk[/PHP]

then if you want to use the latest wine in your distro dude just follow the instructions on this site:

[http://www.bross.eu/2008/05/15/how-to-install-latest-wine-in-ubuntu-804-debian-etch-40/](http://www.bross.eu/2008/05/15/how-to-install-latest-wine-in-ubuntu-804-debian-etch-40/)

100 percent this step is working good.. because to tell you dude i just follow this step and my wine is working good. i experience no problem at all..

i even enjoy playing my favorite online game FLYFF using wine.

hope this one helps you at lot.. thanks

---

### Post by icodeme on 2008-10-27
Unfortunately, I am a beginner and not really familiar about the terminal since i started just yesterday on Ubuntu.
I followed the instruction but ended up with this message

"W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
"

---

### Post by killer_d76 on 2008-10-27
have you tried using the method that i have posted on this thread?.. [http://ubuntuforums.org/showthread.php?t=922963]("http://ubuntuforums.org/showthread.php?t=922963")

...just follow the instruction to "sudo apt-get install wine"... that should do the trick. :guitar:

---

### Post by icodeme on 2008-10-28
I tried to do that but on the terminal, it automatically installs the latest 1.1.7 Wine. It still ended up the same.

Thank you for the replies guys. badly needing it :(

---

### Post by loell on 2008-10-28
so like i said, it may something to do with the video card. is it ATI?

---

### Post by icodeme on 2008-10-28
Sorry, How do I know if it is? Thanks. Im not really into hardware things.

---

### Post by loell on 2008-10-28
for hardware listing, in the terminal prompt, type

```
sudo lshw
``` 

copy/paste it here.

---

### Post by loell on 2008-10-28
oh, you haven't stated the application you're trying to run on wine.

---

### Post by icodeme on 2008-10-28
Adobe Photoshp and Dreamweaver. ( Please be informed that even in the dialogue box on configuring wine, the cursor gets lost also. It just appears in the Minimize, maximize, close part )

-------------------------------------

---

### Post by loell on 2008-10-28
you have an integrated video processor (built in video).

could you post the specific versions of the programs that you're trying to run?

also, delete the **.wine** directory to reset your wine settings.

```
rm -rf .wine
```

see if there's any change on the cursor.

---

### Post by icodeme on 2008-10-28
MacroMedia Dreamweaver 8 ( Installed and Running )
Adobe Photoshop CS2 ( Installed and Running )

.Wine directory has been deleted. What should I do nex?
Thanks for your time bro.

---

### Post by doas777 on 2008-10-28
could you post the output of ```

cat /etc/X11/xorg.conf

``` 
(in this case 'cat' prints the contents of a file.)

i've never seen a VIA vid card, let alone a "Chrome9 HC IGP", but this [thread]("http://ubuntuforums.org/showthread.php?t=504849") discusses installing a driver for one, if it;s not already installed.

Do you have Desktop effects turned on? if so try turning it off. to do that, RClick the desktop -> "Change Background" -> Visual Effects and select none. you may have to logout and back in for the changes to take effect. then give your wine app a try. 

good luck, 
Franklin

---

### Post by loell on 2008-10-28
just execute those apps, after deleting the settings. see if theres a cursor now.

---

### Post by icodeme on 2008-10-28
**Visual Effects -** [COLOR="Red"]"Cannot enable Desktop Effects"[/COLOR]

-

---

### Post by icodeme on 2008-10-28
> **loell said:**
> just execute those apps, after deleting the settings. see if theres a cursor now.

The program can't be executed now. Do I have to reinstall Wine?

Sorry bout this hassle bro

---

### Post by doas777 on 2008-10-28
well it looks like you don't have a specific driver for your vid card, so you may want to look at the thread I linked above. 

as for reinstalling wine, it's:
```

sudo apt-get install wine --reinstall

```

or 
```

sudo apt-get remove wine
sudo apt-get install wine

```

---

### Post by icodeme on 2008-10-28
OK. Maybe I should give it a try. If you guys got any development on this, please let me know Thanks a lot!

---

### Post by loell on 2008-10-28
> **icodeme said:**
> The program can't be executed now. Do I have to reinstall Wine?

Sorry bout this hassle bro

oh god [-o<, i think i just made a wrong advice, the **.wine** has those programs, so you can't execute it.  you won't have to re-install wine, but you'll gonna have to install dreamweaver etc..  so i guess i'll be the one apologizing for the hassle. :oops:

so this most likely video driver problem..

---

### Post by icodeme on 2008-10-28
No not at all. Nag-eexperiment kasi ako sa laptop ng bro. If I could get this workin' here, i'll use ubuntu on my other NEO laptop. Ginagamit ko kasi siya sa Web Developmet eh baka mahirapan ako pag wala yung main tools ko :)

Salamat ha. if may development bro, please inform me. Salamat1!

---

### Post by loell on 2008-10-28
> **icodeme said:**
> 

Salamat ha. if may development bro, please inform me. Salamat1!

not so related sa problem mo, but today you're in great luck, there's a free download for **codeweavers** its a commercial version of wine, you setup less and more or less have some comaptibility advantage than wine

[http://media.codeweavers.com/pub/crossover/lameduck/install-crossover-pro-7.1.0.sh]("http://media.codeweavers.com/pub/crossover/lameduck/install-crossover-pro-7.1.0.sh")


download it, its only for today!! :D

---

### Post by icodeme on 2008-10-28
:guitar: PARTY TIME!!!

But how do I go on with this after download, sypnatic package manager din ba ang mag-iinstall nito?

Salamat salamat. Hope it'll work!

---

### Post by loell on 2008-10-28
you'll be downloading a **sh** file, you'll gonna have to install it by typing it in the command line.

```
./install-corssover-pro.sh
```

but before that you'll gonna have to set the script  to be executed

```
chmod +x install-corssover-pro.sh
```

---

### Post by icodeme on 2008-10-28
OK i'll give it a try now.

Thank you:guitar:

---

### Post by icodeme on 2008-10-28
Dude I've already downloaded the file and I'm trying to execute the code you gave me in the terminal but it says it cannot locate the file " No such File / directory":

i renamed the file to the file you stated in the code but to no avail...

---

### Post by icodeme on 2008-10-28
> **loell said:**
> you'll be downloading a **sh** file, you'll gonna have to install it by typing it in the command line.

```
./install-corssover-pro.sh
```

but before that you'll gonna have to set the script  to be executed

```
chmod +x install-corssover-pro.sh
```


Typo Error:

./install-crossover-pro.sh
chmod +x install-crossover-pro.sh

---

### Post by icodeme on 2008-10-28
Now, I got it. I have successfully isntalled it and is currently installing photoshop and dreamweaver via crossover. I'll inform of you of the progress.

 Thank you and Goodluck to me:guitar:

---

