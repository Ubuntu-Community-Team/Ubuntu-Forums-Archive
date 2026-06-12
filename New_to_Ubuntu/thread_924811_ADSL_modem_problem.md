---
title: "ADSL modem problem"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by economy on 2008-09-19
After much ado, I managed to get my Connexant AccessRunner to locate the firmware and link through Ubuntu (USB connection). Now I need to know how to set Ubuntu to log in and connect to the internet using the modem. 

The things I tried:

pppoeconf - it says it scanned 2 items, but the access concentrator did not respond... this seems strange since i got the firmware and the second "link" light on the modem is solid. 

installing rp-pppoe - step 3 of the instructions says to run the configure file in [src], but through the terminal i get this output:

economy@economy-laptop:~$ '/home/economy/rp-pppoe-3.10/src/configure' 
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.

last, i have installed USB ADSL modem manager, but while installing I noticed it only supports SpeedTouch modems of the 330 variety. Is that going to be a problem?

I've been fiddling with this for about 3 days now... great intro for using the Terminal, but i could do a lot more if i could just get this connection working. any advice?

---

### Post by Shazaam on 2008-09-20
Is there a separate light labeled "Internet"? And is it on (or flashes)?

---

### Post by economy on 2008-09-20
There are 3 lights. The first is power (obviously on, and solid), the second is called "link" and it blinks momentarily when i turn my computer on but when i enter ubuntu it becomes solid, and the third is called activity or something like that, and when i'm in windows it blinks once i've signed into the proprietary software that came with the modem, and when there is some kind of traffic (clicking a link, loading a page, downloading, etc). That light isn't on, and I have no internet access to make it blink.

I struggled trying to get the firmware so that second light would even come on, and now that it's solid each time i sign in, i feel like all i need to do is communicate with the modem to sign in.

---

### Post by Shazaam on 2008-09-20
Found something...
[http://ubuntuforums.org/showthread.php?t=145138](http://ubuntuforums.org/showthread.php?t=145138)
I realize it is for Dapper (6.06) but the part you need is there. Scroll down to here...
```
Now, comes the hard part... write a script that polls the modem state and quits when it's ready. You'll understand later why we need it... for now, just create a file called checkADSL.sh with the following content in
```
Check it out and see if it helps.

---

### Post by economy on 2008-09-20
Shazaam, 

this looks like it will be helpful, i'll try it as soon as possible. it's greek to me though.

it says to create a file with the name listed. ok, that's in text editor right?

and i guess the code underneath is how you change the owner to root (chown) and give it permission to be executed (chmod), or am i missing it completely?

i guess you can see how new I am to all of this... thansk for your patience.

---

### Post by Shazaam on 2008-09-20
Correct.
The man (manual) pages are good for finding info on commands...
```
man chown
```
```
man chmod
```

---

### Post by economy on 2008-09-20
Ok, I'm still having trouble... I followed the above steps, but I still have no knowledge of how to dial in to the modem... 

is there an easy way to do it through the command line, or is there a GUI of some kind that can prompt me for a username/password and attempt to dial?

usbadslmodemmanager doesn't seem to recognize the firmware even... but that's probably because my modem isn't speedtouch 300. and again, i had issues installing rp-pppoe...

any ideas??

---

### Post by Shazaam on 2008-09-20
From what I gathered from the link I gave you that (login, connecting) is all done automatically when you boot the pc so you shouldn't need any other software to connect. Like a normal "always-on" dsl connection.

---

### Post by economy on 2008-09-20
Ah, right. So I should restart the system and see if it worked. This is hard because I'm back and forth between an internet cafe and my modem... 

Think I'm getting the hang of this command line thing. I also downloaded (I dunno if it's necessary if the previous post worked) some packages that deal with pppoe... I must be close now.

---

### Post by zvacet on 2008-09-20
You need **build-essential** for rp-pppoe.Put CD in drive and go to the synapticand in search box type build-essential.When you find pachage check white box on the left side of package and mark package for install.Instruction for rp-pppoe install are [here.]("http://www.linuxhelp.net/guides/pppoe/") maybe you can some additional help [here.]("http://ubuntuforums.org/showthread.php?t=852347&highlight=rp-pppoe+hardy")

---

