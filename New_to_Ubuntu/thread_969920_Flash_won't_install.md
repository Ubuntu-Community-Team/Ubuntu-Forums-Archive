---
title: "Flash won't install"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by mindlessly self indulgent on 2008-11-03
I'm having difficulty getting flash to install.  Supposedly when I download it straight from the adobe site, I already have it installed, but it is not working in Firefox at all.  When I go to "install missing plugins" and click on flash, this screen comes up. 

[IMG]http://img.photobucket.com/albums/v214/sakurarocket/pluginerror.png[/IMG]

Anyway, I'm a total Noob to Ubuntu, so I have no idea what that means.  Since I'd like to start using Ubuntu for most of my web browsing, flash would be nice.  Can anybody help me here?

Hope this question isn't too stupid :P

---

### Post by BGFG on 2008-11-03
Hey,
Go system>>administration>>Synaptic package manager then install the package:

flashplugin-nonfree

If you are using Intrepid, this will be the latest version which works for me .

---

### Post by mindlessly self indulgent on 2008-11-03
It just gave me the same exact error message when I tried to do that.  I'm using 8.04 btw, I believe that is hardy herron.  I guess updating to Ibex couldn't hurt though.

---

### Post by kansasnoob on 2008-11-03
First of all do just what it says. At terminal:

```
sudo dpkg --configure -a
```

Next run:

```
 sudo apt-get install --reinstall ubuntu-restricted-extras
```

Then restart Firefox by going to File > Quit. Then restart Firefox and see what you have.

---

### Post by mindlessly self indulgent on 2008-11-03
Wow, I have a feeling that this is way less confusing than I'm making it.  I'm really not sure what to do with terminal (of maybe I'm just scared of crashing something).  

It's amazing how I can use regedit and all that fun stuff in Windows, but I see an unfamiliar screen in Ubuntu and I run screaming :P

Is there any way somebody could give me a step by step, or am I really missing the simplicity of it all ^^;

EDIT: Okay, I'm pretty sure I get the gist of what you're saying, but I'm just a little nervous, new os and all ^^;

---

### Post by kansasnoob on 2008-11-03
> **mindlessly self indulgent said:**
> Wow, I have a feeling that this is way less confusing than I'm making it.  I'm really not sure what to do with terminal (of maybe I'm just scared of crashing something).  

It's amazing how I can use regedit and all that fun stuff in Windows, but I see an unfamiliar screen in Ubuntu and I run screaming :P

Is there any way somebody could give me a step by step, or am I really missing the simplicity of it all ^^;

EDIT: Okay, I'm pretty sure I get the gist of what you're saying, but I'm just a little nervous, new os and all ^^;

Hey, my first month with Linux was only 10 months ago and I thought I'd lose my mind. But I started with gOS and Freespire!

It's going to be confusing at times! when you're at all unsure just keep coming here.

We (myself included) don't always get it right but you'll love it after a while!

---

### Post by kansasnoob on 2008-11-03
Heck the first time someone said terminal I asked "what terminal"?

Accessories > Terminal!

There is no dumb question!

---

### Post by mindlessly self indulgent on 2008-11-03
Okay, as far as Terminal goes, do I go to file/new profile, or is that totally wrong?  

Yeah, this should be interesting, but I really like what I see so far.  It's a little confusing to me, but being a semi-expert with Windows, I don't think it should take me *too* long to get it (well, that's what I'm hoping anyway) :)

---

### Post by oldos2er on 2008-11-03
Copy and paste the first command kansasnoob gave you into the terminal. You'll be asked to enter your password, type it in. It's normal to see nothing echoed to the screen when you do so. Then run the second command.

---

### Post by kansasnoob on 2008-11-03
> **mindlessly self indulgent said:**
> Okay, as far as Terminal goes, do I go to file/new profile, or is that totally wrong?  

Yeah, this should be interesting, but I really like what I see so far.  It's a little confusing to me, but being a semi-expert with Windows, I don't think it should take me *too* long to get it (well, that's what I'm hoping anyway) :)

It'll look like this:

[ATTACH]91065[/ATTACH]

Then hit enter.

Then you enter your password. The password won't show.

You'll get this!

---

### Post by mindlessly self indulgent on 2008-11-05
It worked!  Thank you so much everybody :)

I am now officially over my first Ubuntu hurdle :)

---

