---
title: "How do I launch google chrome or firefox from the terminal?"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by mferarri on 2012-03-09
How do I launch google chrome or firefox from the terminal?

---

### Post by haqking on 2012-03-09
> **mferarri said:**
> How do I launch google chrome or firefox from the terminal?


type

```
google-chrome
```

```
firefox
```

;-)

If your path is not set then you may need to change to directory like /opt/chrome for example.

If you dont know where they are then

```
whereis chrome
```

cheers

---

### Post by arochester on 2012-03-09
Strange, my Chrome starts with the command: > google-chrome

---

### Post by haqking on 2012-03-09
> **arochester said:**
> Strange, my Chrome starts with the command:

actually yeah you are right, i edited.

I was doing it from (poor) memory as oppose to trying it first ;-)

---

### Post by mferarri on 2012-03-09
> ```
google-chrome
```

```
firefox
```

Thanks Haqking, these commands work for me.

> If you dont know where they are then

```
whereis chrome
```

whereis chrome dosent work for me. But whereis google-chrome does.

how can i find the right name for the right applications? is there a way to grep a list of apps installed on my comp?

---

### Post by nothingspecial on 2012-03-09
Hi

```
nothingspecial:~$ dpkg --get-selections | grep chrom
chromium-browser				install
chromium-browser-l10n				install
chromium-codecs-ffmpeg				install
xserver-xorg-video-openchrome			install

```

---

### Post by mferarri on 2012-03-09
> **nothingspecial said:**
> Hi

```
nothingspecial:~$ dpkg --get-selections | grep chrom
chromium-browser				install
chromium-browser-l10n				install
chromium-codecs-ffmpeg				install
xserver-xorg-video-openchrome			install

```

thanks nothingspecial!:popcorn:

---

### Post by daslinkard on 2012-03-09
The one thing that i would add to this post is that if you want a specific site to launch with Firefox from the terminal you would type the following:

> firefox google

Or you could open up several tabs at one time by doing

> firefox google news.yahoo.com foxnews

Hope this helps someone!

---

### Post by mferarri on 2012-03-10
> **daslinkard said:**
> The one thing that i would add to this post is that if you want a specific site to launch with Firefox from the terminal you would type the following:



Or you could open up several tabs at one time by doing



Hope this helps someone!

thanks for the tip daslinkard!

---

### Post by srikanthganta on 2012-10-24
good information..but want to update the info about my Ubuntu 12.04:

>firefox
>chromium-browser
above commands are working for me
("chrome" or "google-chrome" not working)

>chromium-browser google.com news.yahoo.com foxnews.com
(.com is mandatory)

---

