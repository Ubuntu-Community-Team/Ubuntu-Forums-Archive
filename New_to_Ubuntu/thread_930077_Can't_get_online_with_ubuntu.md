---
title: "Can't get online with ubuntu"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by Goku08 on 2008-09-25
Okay, I have vista, and I saw a video of someone using Ubuntu, I saw how fast it loaded, and I wanted to give it a go.

For some reason, when I'm in ubuntu, my internet card/internet switch whatever it's called, doesn't turn on. I flick the switch but it still can't turn on. It does fine in windows.

All the solutions to this involve downloading some drivers...but I can't get online?

I have a broadcom wireless card...

Yeah, I'm using Ubuntu 8.10 if anyone wants to know. So please try to help me. I can't even enable special effects or go online! =(

---

### Post by crazypenguin2008 on 2008-09-25
8.10 is still in devolopmental stages. its not stable just so you know. 

seems alot of folks have had trouble with broadcom cards. might be worth a look thru the fourms and get a idea.

---

### Post by GavinZac on 2008-09-25
8.10 is testing-quality software so if you're not comfortable with the extra work contributing to getting it to release-quality, I'd say try 8.04

You're online now, I would suggest downloading the drivers to this pc, transporting them via USB key or whatever, and installing them on the wireless pc from there. Alternatively, plug your wireless pc (assuming that it is wireless by choice, and not by necessity) into the router directly and work from there.

---

### Post by Goku08 on 2008-09-25
Wow dude I didn't even think of that, so I can download the drivers and put em on a cd and ubuntu will read it? Nice.

Hmm, since I'm a complete noob, how would I open up 'my computer' in ubuntu?

---

### Post by GavinZac on 2008-09-25
> **Goku08 said:**
> Wow dude I didn't even think of that, so I can download the drivers and put em on a cd and ubuntu will read it? Nice.

Hmm, since I'm a complete noob, how would I open up 'my computer' in ubuntu?

"Computer" is in your Places menu, along with cd drives, usb keys, etc.

Do you have a link to what you're using as a guide for your wireless driver install? Wireless remains one of the more awkward things to fix in Ubuntu, for most people you just turn it on and it works but for maybe 1 in 4 people it takes a little bit of time to get it just right.

---

### Post by Goku08 on 2008-09-25
....Okay I'm confused now. I don't even know what files to put on a disc. When I run ubuntu, I go to my drivers, and then I see they're disabled, I try to hit 'enable', but, of course, I need to be on the internet for that. There must be an easier way.

If I download these [http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/) and open them up in ubuntu, would I be able to enable wireless?

---

### Post by GavinZac on 2008-09-25
> **Goku08 said:**
> ....Okay I'm confused now. I don't even know what files to put on a disc. When I run ubuntu, I go to my drivers, and then I see they're disabled, I try to hit 'enable', but, of course, I need to be on the internet for that. There must be an easier way.

If I download these [http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/](http://ubuntu.cafuego.net/dists/hardy-cafuego/broadcom/) and open them up in ubuntu, would I be able to enable wireless?

[http://packages.ubuntu.com/intrepid/linux-restricted-modules-common](http://packages.ubuntu.com/intrepid/linux-restricted-modules-common)

Download that (thats what the hardware driver program wants to download, but can't), burn it on a CD, and insert the CD to your wireless pc. ubuntu should recognise that its's got a package on it and ask if you want to install it; if it doesn't, just open the CD from your Places menu and double click the package.

---

### Post by ludu900 on 2008-09-25
ok 
im a complete noob too
will this work on a 64 bit amd processor???
i saw the ndiswrapper driver and i thought of plugging my computer into my router but it says it is not supported by the 64 bit amd
what should i do???

---

### Post by Goku08 on 2008-09-27
Hey again everyone!!

You guys are awesome! I connected my cable modem directly to my pc, and enabled my drivers, and now I have the Desktop effects and Wireless internet working very good!

But a few questions to you guys
1.) Does anyone else have less-quality audio?
2.) Is your wireless internet card MUCH weaker in ubuntu than windows?

But again, I LOVE these effects! =D

---

### Post by RequinB4 on 2008-09-27
> **Goku08 said:**
> Hey again everyone!!
1.) Does anyone else have less-quality audio?
But again, I LOVE these effects! =D

Try going to your volume icon in your panel, (right) clicking and edit volume, and make sure PCM is at about 79%

I can't remember the exact method because I've customized my box to the point I don't have panels - but if you can't find it you can also go to applications - accessories - terminal and type in

```

alsamixer

```

and use the keyboard.

---

