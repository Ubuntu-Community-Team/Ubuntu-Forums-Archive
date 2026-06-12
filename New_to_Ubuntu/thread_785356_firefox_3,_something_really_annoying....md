---
title: "firefox 3, something really annoying..."
date: 2008-05-07
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-07
when i rightclick on fullscreen for a moment always blinks on blackscreen and then goes back to normal...
it really annoying...
some help?

maybe it because of the desktop effects

---

### Post by forumache on 2008-05-07
> **lunaluna said:**
> maybe it because of the desktop effects

Try without desktop effects. Same problem?

---

### Post by lunaluna on 2008-05-07
> **forumache said:**
> Try without desktop effects. Same problem?

yeap it's the desktop effect... but isn't there something we can do about it?

---

### Post by forumache on 2008-05-07
I would be interested in a solution too. I have a similar problem with NX Client in fullscreen mode.

---

### Post by Sef on 2008-05-07
What are your system specs, including your video card?

---

### Post by corevette on 2008-05-07
you could always try running 'firefox' from the terminal and see if anything unusual comes up when you make it flicker

---

### Post by lunaluna on 2008-05-07
> What are your system specs, including your video card?

2.13 ghz intel pentium M
ati x700 mobility radeon
___
> 
you could always try running 'firefox' from the terminal and see if anything unusual comes up when you make it flicker

nope everything seemed ok..

---

### Post by forumache on 2008-05-07
@Sef: Ubuntu Hardy, nvidia GeForce 6200 128Mb (with restricted drivers)

I don't think the other specs matter, but nevertheless, here they are:
AMD64 3500+, 1Gb RAM, 400GB HDD

---

### Post by gerben1 on 2008-05-07
same problem here, not that surprising as I have the same video card as lunaluna:

```

gerben@CC1184274-A:~$ sudo lshw -C video
[sudo] password for gerben:
  *-display
       description: VGA compatible controller
       product: Radeon Mobility X700 (PCIE)
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx

```

---

### Post by glennric on 2008-05-07
I have an nvidia card and after coming back from fullscreen there is a brief flicker of the screen when using compiz.  So it is probably some bug in the fullscreen windows redirection.

---

### Post by lunaluna on 2008-05-07
i dont know but since a min ago i dont have that problem anymore...!!!
its like my pc is listening to me...boooo!!!

---

### Post by jimv on 2008-05-07
> **lunaluna said:**
> i dont know but since a min ago i dont have that problem anymore...!!!
its like my pc is listening to me...boooo!!!

It's the new Ubuntu Listens(TM) feature!

---

### Post by lunaluna on 2008-05-07
> **jimv said:**
> It's the new Ubuntu Listens(TM) feature!

i guess even laptops have ears now...lol

---

### Post by gerben1 on 2008-05-07
Are you sure you do not just have Compiz turned off?

---

### Post by lunaluna on 2008-05-07
actually i just was turning on off desktop effects-no problem there
i dont know how to compiz -anyway
but if you have any ideas to follow-more i'm glad to listen...

---

### Post by mister_pink on 2008-05-07
This is pretty strange, it must be something about the way the window is drawn in full screen, and then the menu is drawn over the top. Mine does it too (using fglrx), and I also noticed in full screen mode theres no problem with jerky scrolling.

---

### Post by forumache on 2008-05-07
Yeah, I have the problem with NX Client, but firefox works just fine in full screen with desktop effects enabled. Except that black flicker when I return from full screen.

Cheers,
Dan.

---

### Post by GoCool on 2008-05-07
Hope you are not talking about the ripple feature which you have enabled on the desktop. Say when you scroll down a document using your arrow keys, and even after you hit the bottom and click on the down arrow again, it notify's you by normally giving a 'beep' sound or a ripple.

---

### Post by forumache on 2008-05-07
No GoCool, black flicker is no ripple effect here :)

I have just the Normal Desktop Effects, no extra or custom.

---

### Post by gerben1 on 2008-05-07
I noticed something else, but first just to explain clearly again what is happening:

In firefox, when in fullscreen (meaning the full screen mode that you get when you press F11 in Firefox), the screen will go black for about a second or so when you press the right mouse button

What I just noticed is that when I press the right mouse button and without letting it go I immediately move the mouse then not the whole screen will be black for a second but only the rectangular area where the "right-mouse-button-menu" would have appeared if I had  not moved the mouse.

---

### Post by forumache on 2008-05-07
right click in fullscreen => black for a second, same here.
although I was right clicking many times and some times I don't get the black. But I cannot predict when. Even if I try to move the mouse immediately after right-clicking and not releasing, the black thing still occurs. Maybe I am not quick enough :)

---

### Post by lunaluna on 2008-05-08
well the annoying black screen it's back...!
any ideas you might came up so far?

---

### Post by zergamat on 2008-05-10
try this
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153204](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/153204)

Desctop effects config (compiz) - general options - uncheck **undirect fullscreen windows**

---

### Post by gerben1 on 2008-05-11
That worked, thanks Zergamat

---

### Post by lunaluna on 2008-05-15
i realized that when it blinks it shows the page i previously visited...

---

