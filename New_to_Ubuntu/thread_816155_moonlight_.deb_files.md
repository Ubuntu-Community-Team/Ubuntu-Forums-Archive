---
title: "moonlight .deb files"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-06-02
Are there any .deb files available that will install moonlight?

I have found a site that offers debian etch debs that should work with hardy but the site must be down, because I'm not getting in.

---

### Post by billgoldberg on 2008-06-02
bump

---

### Post by dracayr on 2008-06-02
this is an instruction for how to install it:

[http://www.deepakg.com/blog/archives/39.htm](http://www.deepakg.com/blog/archives/39.htm)

Quote from that link:"The Moonlight plug-in for Firefox is not available as a binary package and needs to be compiled from source"

dracayr

---

### Post by shifty_powers on 2008-06-02
i found a link that will install moonlight into firefox.....

it is the mono version of silverlight you are after, yes?

---

### Post by shifty_powers on 2008-06-02
> **dracayr said:**
> this is an instruction for how to install it:

[http://www.deepakg.com/blog/archives/39.htm](http://www.deepakg.com/blog/archives/39.htm)

Quote from that link:"The Moonlight plug-in for Firefox is not available as a binary package and needs to be compiled from source"

dracayr

[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

disagrees with you ;)

---

### Post by philinux on 2008-06-02
Same here I've been after this for a while. I tried compiling it but no dice.

---

### Post by shifty_powers on 2008-06-02
the link i just gave gives you an xpi for moonluight for firefox ;)

---

### Post by shifty_powers on 2008-06-02
indeed, i've just installed it ;)

---

### Post by philinux on 2008-06-02
Cheers shifty .

Profile 1 or profile 2?

[edit] 
Aaaargghhh just seen this.

These are currently built without multimedia support. No video or mp3 playback is enabled on these binaries.

---

### Post by shifty_powers on 2008-06-02
heh never mind. and i would stick with profile 1, silverlight 2 is itself beta, so best to avoid it ;)

---

### Post by philinux on 2008-06-02
Just checked the site I want it for and flash is borked as well.
[http://www.itv.com/CatchUp/default.html](http://www.itv.com/CatchUp/default.html)

---

### Post by billgoldberg on 2008-06-02
thanks shifty_powers but without multimedia support I have no use for moonlight.

---

### Post by shifty_powers on 2008-06-02
[http://www.robblackwell.org.uk/?p=97](http://www.robblackwell.org.uk/?p=97)

any good?

---

### Post by billgoldberg on 2008-06-02
Thank, I stumbled across that website myself in my google search.

I don't really need moonlight, I just like to know if there are .deb available for it.

I don't feel to spend more than 20 seconds on installing it.

---

### Post by shifty_powers on 2008-06-02
np's though phil linux might like it ;)

and heh, i really couldn't be bothered to go through all that :D

---

### Post by pmaconi on 2008-06-02
If you install checkinstall you can do a ./configure, make, and then checkinstall to install with a deb instead of ./configure, make, make install.

---

### Post by QcFox on 2008-09-29
I've the moonlight modules on but i can't see video
take from website [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/) :
"Note: These are currently built without multimedia support. No video or mp3 playback is enabled on these binaries."

---

### Post by directhex on 2008-10-10
I'm working with upstream on trying to get ITV Catchup working.

---

### Post by directhex on 2008-10-10
Oh, and for those in a hurry, real work HAS taken place.

```
jms@osc-franzibald:~$ dpkg -l \*moon\* | grep ^ii
ii  libmoon0                                   0.8.1+dfsg-1                                         open source clone of Microsoft Silverlight
ii  moonlight-plugin-core                      0.8.1+dfsg-1                                         open source clone of Microsoft Silverlight -
ii  moonlight-plugin-mozilla                   0.8.1+dfsg-1                                         open source clone of Microsoft Silverlight -
```

---

### Post by Prosis on 2008-10-17
> **shifty_powers said:**
> [http://www.robblackwell.org.uk/?p=97](http://www.robblackwell.org.uk/?p=97)

any good?

Doesn't work for me...make Firefox crash...took me a half hour to install it...:(

---

### Post by directhex on 2008-10-17
> **Prosis said:**
> Doesn't work for me...make Firefox crash...took me a half hour to install it...:(

And the instructions are obsolete and actively harmful for your system.

Ho hum.

---

### Post by Prosis on 2008-10-19
How are they harmful?

---

### Post by directhex on 2008-10-19
./autogen.sh  --with-moonlight=yes --prefix=/usr

Do i have to draw you a diagram? It involves the app in question taking a big dump all over your package manager

---

### Post by Prosis on 2008-10-19
I don't know what you mean (I'm not all that saavy yet)

---

### Post by directhex on 2008-10-19
> **Prosis said:**
> I don't know what you mean (I'm not all that saavy yet)

Using --prefix=/usr is the equivalent to unzipping a huge directory of random stuff into c:\windows, with "overwrite without asking" turned on

Which might, at a push, work - until Windows Update gets its hands on it, screams, and falls over dead

---

### Post by Prosis on 2008-10-19
Ohh I see :???:

Thanks :)

---

### Post by slimx3m on 2009-04-09
> **shifty_powers said:**
> [http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

disagrees with you ;)
thnx for this link

---

### Post by directhex on 2009-04-10
There are packages in the main Jaunty repos, and in my PPA for Intrepid.

```
deb http://ppa.launchpad.net/directhex/ppa/ubuntu intrepid main
```
is the repo you need to add for Intrepid, then click [here](apt:moonlight-plugin-mozilla)

---

### Post by DarinB on 2010-02-19
any PPA for karmic or LM8

---

