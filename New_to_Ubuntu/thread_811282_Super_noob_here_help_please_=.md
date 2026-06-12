---
title: "Super noob here help please =/"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Linux_noob616 on 2008-05-29
Hi, i hope this can be done. But i need some (i think anyway) some drivers for audio, and maybe motherboard (or any other proprietary device)

here is my PC, i got the nVidia driver already.

model number is: GATEWAY GT5644E

Serial number is: GCX7AC1006061

i know i need the realtek HD audio driver cause i can't use a mic at all and everything is far quieter on Kubuntu then on Windows.

And one more thing, i use aMSN most recent version. and on ubuntu the webcam worked fine, but if anyone sends me a cam or anything it hangs and then runs slllloooooowwwww. Can anyone help me? if kopete supports file transfer, voice chat (yes i know i'm lazy :P) and webcam with MSN then i'll just use that

---

### Post by sam_delta on 2008-05-29
hey , i dont know about the mic, but kopete in fact has webcam and filetransfer support you might give it a try

sam

---

### Post by Linux_noob616 on 2008-05-29
Sam you saved me once again haha.

Any help with the drivers? (in windows it says i use realtek HD audio drivers)

---

### Post by sam_delta on 2008-05-29
yeah no problem bro, anything you need.

sry i duno anything about the audio thing, but im sure someone else will be able to help

sam

---

### Post by Linux_noob616 on 2008-05-29
bump

---

### Post by LaRoza on 2008-05-29
> **Linux_noob616 said:**
> bump

Please don't bump so soon. Try to wait 24 hours at the least before bumping.

That link doesn't give us your computer, but a page to search for drivers. You should give the model of your computer or its hardware that is not working.

---

### Post by Linux_noob616 on 2008-05-29
> **LaRoza said:**
> Please don't bump so soon. Try to wait 24 hours at the least before bumping.

That link doesn't give us your computer, but a page to search for drivers. You should give the model of your computer or its hardware that is not working.

oh i'm sorry about the bump didn't know.

and the model number is: GATEWAY GT5644E

Serial is: GCX7AC1006061

---

### Post by LaRoza on 2008-05-29
> **Linux_noob616 said:**
> oh i'm sorry about the bump didn't know.

and the model number is: GATEWAY GT5644E

Serial is: GCX7AC1006061

[http://support.gateway.com/s/SOFTWARE/MICROSOF/7509594/750959421.shtml](http://support.gateway.com/s/SOFTWARE/MICROSOF/7509594/750959421.shtml)

Do you still have Windows on it? Could you find out the audio device you have?

I am not skilled at dealing with sound issues. Everything I have done involves just using asoundconf-gtk. You can install that:

```

sudo apt-get update && sudo aptitude install asoundconf-gtk

```

And see if it can help (run from a terminal, although it is GUI)

It might work. If it doesn't, someone else will have to help. Sorry.

---

### Post by Linux_noob616 on 2008-05-29
> **LaRoza said:**
> [http://support.gateway.com/s/SOFTWARE/MICROSOF/7509594/750959421.shtml](http://support.gateway.com/s/SOFTWARE/MICROSOF/7509594/750959421.shtml)

Do you still have Windows on it? Could you find out the audio device you have?

I am not skilled at dealing with sound issues. Everything I have done involves just using asoundconf-gtk. You can install that:

```

sudo apt-get update && sudo aptitude install asoundconf-gtk

```

And see if it can help (run from a terminal, although it is GUI)

It might work. If it doesn't, someone else will have to help. Sorry.

not to correct you since you've been here awhile. But isn't GTK for Gnome?

and i use realtek hd audio driver version 6.something (so says gateway)

---

### Post by kansasnoob on 2008-05-29
I'd almost bet if Realtek drivers worked in Windows and your sound is only weak you'll solve it by going to Synaptic and installing "gnome-alsamixer".

You'll then find gnome alsa mixer in Sound and Video. Just adjust the toggles ........... probably the first three and the last four.

---

### Post by LaRoza on 2008-05-29
> **Linux_noob616 said:**
> not to correct you since you've been here awhile. But isn't GTK for Gnome?

and i use realtek hd audio driver version 6.something (so says gateway)

It will still work, but yes, GTK is used by GNOME. You can run KDE applications and GNOME applications on the others. 

I never had to configure sound beyond using that little application to select the device I wanted.

---

### Post by Linux_noob616 on 2008-05-29
> **kansasnoob said:**
> I'd almost bet if Realtek drivers worked in Windows and your sound is only weak you'll solve it by going to Synaptic and installing "gnome-alsamixer".

You'll then find gnome alsa mixer in Sound and Video. Just adjust the toggles ........... probably the first three and the last four.

oh Kubuntu but it will still work right? (kubuntu equivalent would be better if not I'm fine)

---

### Post by LaRoza on 2008-05-29
> **Linux_noob616 said:**
> oh Kubuntu but it will still work right? (kubuntu equivalent would be better if not I'm fine)

I am really out of touch with Ubuntu and Kubuntu at the moment. I use a heavily customized setup and have no real clue what is available at the moment. (This is one of the reasons I have not been in this forum for a while)

---

### Post by Linux_noob616 on 2008-05-29
nevermind it opened up but it's having issues and i'd still like to remove it, it's saying that my sound card is nvidia. Does this mean i have an nforce chipset?

---

### Post by LaRoza on 2008-05-29
> **Linux_noob616 said:**
> i used ```
sudo apt-get update && sudo aptitude install asoundconf-gtk
```

and it refuses to load in Kubuntu, how can i remove it?

```

sudo aptitude remove --purge asoundconf-gtk

```

---

### Post by Linux_noob616 on 2008-05-29
made a post just after i corrected myself =/ It's saying i use an nVidia sound card (even though Windows says i use realtek)

---

