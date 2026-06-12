---
title: "Major problem with ubuntu"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by DMzda on 2008-08-29
I have a problem now. Whilst trying to fix Grub, I reinstalleed ubuntu on the same partition without formatting it. It worked fine, although the windows had no close, minimize or maximize buttons. Using Apt-on-cd, I backed up some of the packages I had installed. I tried to install them all at once by using:

```
sudo dpkg -i *
```

after I had used "cd" to open the directory. This caused major mayhem as lots of dependencies were missing. I couldn't use:

```
sudo apt-get install -f
```

to fix the dependencies as I needed ntlmaps to authorize the ISA proxy server that I must use.

I performed a command in dpkg which deselected all non-essential packages. It turned out to be a bad mistake as nothing would work. Eventually, using Ctrl+Alt+F2 (something like tty2 :confused: ), I got ntlmaps to work. However, when it works, I cannot do anything else, only end it with Ctrl+C. With tty1, I tried to install a package from the internet while ntlmaps was running in tty2. This failed. Now I have a command line and windows .

It was a stupid thing to do :(

Any help???

---

### Post by nicedude on 2008-08-29
If any of the dependencies you are missing are standard on the install CD then you could try adding the install CD to your sources and then try 


sudo apt-get install -f
And see if some of the dependencies get taken care of. 

I also don't understand what all you have done as your description is leaving me guessing. For example is there no way for you to use a regular internet connection as in say just plug Ethernet up to a friends router etc. As that would let you fix whatever more than likely.

You might also want to look at trying build-dep and autoremove with apt-get and see if they might help you fix this.

Hope this helps a bit, maybe someone else will know more.

EDIT

I see dpkg has some options that might help but I don't know for sure. You might want to look at the following switches and see if the could help you roll back some of the bad changes.

--auto-deconfigure & --force-remove-reinstreq look like they could apply

---

### Post by DMzda on 2008-08-29
Thanks for the quick reply.

> **nicedude said:**
> If any of the dependencies you are missing are standard on the install CD then you could try adding the install CD to your sources and then try 


sudo apt-get install -f
And see if some of the dependencies get taken care of. 

I have tried this with no success.

> **nicedude said:**
> 
I also don't understand what all you have done as your description is leaving me guessing. For example is there no way for you to use a regular internet connection as in say just plug Ethernet up to a friends router etc. As that would let you fix whatever more than likely.


I cannot do that at the moment. To use apt-get and synaptic, I had to use ntlmaps to autorize through an ISA proxy server. I do not know how to use this via the command line.

---

### Post by DMzda on 2008-08-29
Any help?

---

### Post by Crafty Kisses on 2008-08-29
Try the following:
```
sudo dpkg --configure
```
Then after that, do this:
```
sudo apt-get update
```

---

### Post by DMzda on 2008-08-30
Thanks for the reply, but

```
sudo apt-get update
```

doesn't work, as it comes up with a lot of proxy server *authentication* errors.

Any other suggestions?

---

### Post by DMzda on 2008-08-30
Any help?

---

### Post by DMzda on 2008-08-30
Ok...

So I reinstalled over the old partition using the live CD. I forgot to install grub, so I will do that now.

---

### Post by DMzda on 2008-08-30
After I reinstalled grub, I booted into ubuntu. After logging in, the screen only showed the cream coloured background, and nothing else!!! 

I went into the termicnal (Ctrl+Alt+F1) and tried to run firefox and other programs such as gedit. They came up with errors like "unable to open window manager" (not exact words). I then tried : ```
sudo apt-get install ubuntu-desktop
``` but it said it was already installed.

The live CD works fine though.

---

### Post by nicedude on 2008-08-30
Instead of this
sudo apt-get install ubuntu-desktop
try this

sudo apt-get reinstall ubuntu-desktop

That may work

---

