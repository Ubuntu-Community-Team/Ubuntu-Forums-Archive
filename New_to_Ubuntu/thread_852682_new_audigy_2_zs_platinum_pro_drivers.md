---
title: "new audigy 2 zs platinum pro drivers?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by LeDechaine on 2008-07-07
I was wondering if there was new "drivers", or whatever you call that in linux, for the SoundBlaster Audigy 2 ZS Platinum Pro card.

My card is actually only "half-working", i.e.: most of the outputs and inputs doesn't even work. I can listen to my music via the headphones output, but the "optical out" doesn't work, and the "aux in" of the card doesn't, too. Which means that I can't output sound to my speakers (optical out), and I can only "watch" the TV, without *listening* to it, because my TV Card must be plugged in the "aux in" to output sound. (And for the other inputs/outputs, I don't care.)

As you can see, the "support" for this card is pretty bad. And sadly, again, everything works #1... in Windows.

So, has something changed, or is this card "pseudo-support" still as bad as it was?

Thanks in advance.

---

### Post by ZabiGG on 2008-07-09
Hi there ;) I'll translate everything I'll say to you in English after to help out our anglophone friends...


peux-tu coller le résultat de la commande

lspci 

dans le terminal, afin que nous sachions exactement quel pilote est utilisé par le système? (Can you post the result of terminal command lspci so we can determine exactly which driver is used by the system?)

Merci/thanks,

Z.

---

### Post by k3lt01 on 2008-07-09
Go to the creative website and click through to the section for your hardware, then click to see all drivers. Creative is working hard to get Linux stuff working and last I remember they had beta drivers out for nearly all of their new stuff.

---

### Post by ZabiGG on 2008-07-09
> **k3lt01 said:**
> Go to the creative website and click through to the section for your hardware, then click to see all drivers. Creative is working hard to get Linux stuff working and last I remember they had beta drivers out for nearly all of their new stuff.

Translation: Rends-toi au site Create et clique jusqu'à la section relative à ton matériel, puis clique pour voir tous les pilotes. Creative trime dur pour faire fonctionnner tous tes trucs Linux,  et, aux dernières nouvelles, ils avaient sorti tous les pilotes Linux pour au moins la moitié de leurs trucs. (Visit the section on your hardware and click to see all drivers. Creative is working hard to make all your stuff work, and, based on the latest news, they had published all of the Linux drivers for at least half of their stuf.)

---

### Post by k3lt01 on 2008-07-09
> **ZabiGG said:**
> Translation: Rends-toi au site Create et clique jusqu'à la section relative à ton matériel, puis clique pour voir tous les pilotes. Creative trime dur pour faire fonctionnner tous tes trucs Linux,  et, aux dernières nouvelles, ils avaient sorti tous les pilotes Linux pour au moins la moitié de leurs trucs. (Visit the section on your hardware and click to see all drivers. Creative is working hard to make all your stuff work, and, based on the latest news, they had published all of the Linux drivers for at least half of their stuf.)Mate, he posted the OP in English, there is no need to go translating my reply which is also in English, nor is there any need to re-word it and make spelling mistakes while doing so. Unless of course you are just trying to boost your post count :lolflag:

---

### Post by LeDechaine on 2008-07-09
Haha yeah no need to translate! ;)

> ~$ sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
[B]00:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)[/B]
00:0a.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0a.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0a.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0a.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:0b.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:0d.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
ledechaine@A99-LeDechaine:~$ 

Voilà! :)

---

### Post by ZabiGG on 2008-07-09
@[k3lt01]("http://ubuntuforums.org/member.php?u=397303")

Was just trying to be nice to a newbie and make them feel welcome... as for the "re-write," it had nothing to do with correcting you: it was a backtranslation of what I had said in French so no one would jump on the paranoid wagon thinking I'd said anything nasty or incorrect. As for the missing final f, I stand corrected.

---

### Post by ZabiGG on 2008-07-09
@ledéchaîné

Looks like you are using a generic driver. You should definitely check out the site recommended to see if they don't have any drivers more specific to your card.

Cheers,

Z.

---

### Post by Tatty on 2008-07-09
Just a thought, have you made sure that the channels you are trying to use are turned up?

Go to a terminal and type ```
alsamixer
```  This will open up a mixer in the terminal where you can alter the levels of the channels in your card.

---

### Post by k3lt01 on 2008-07-09
Zabi, chill mate, it was a joke. I suppose only an Aussie will get another Aussie's humour properly.

Tatty, or he could just double click on the speaker icon and open it without going through the App>Accesories>Terminal procedure and then typing!

LeDechaine, let us know how you go with it all. I have an old Live Drive setup with similar issues but Creative, as far as I am aware, aren't going to bring their older stuff like mine up to speed.

---

### Post by LeDechaine on 2008-07-09
@ZabiGG: Merci ;)

@Tatty: Already done this :)

@k3lt01: Okay!

---

### Post by LeDechaine on 2008-07-13
> **k3lt01 said:**
> Go to the creative website and click through to the section for your hardware, then click to see all drivers. Creative is working hard to get Linux stuff working and last I remember they had beta drivers out for nearly all of their new stuff.

Well, finally, Linux has been **deleted** from their operating systems list recently, so it looks like **Creative completely stopped supporting Linux**.

And [according to alsa]("http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1"), ADAT (optical) and SPDIF still aren't supported.

For OSS, though, i've found this:
[http://manuals.opensound.com/sources/sblive.c.html](http://manuals.opensound.com/sources/sblive.c.html)

So maybe [this]("http://www.opensound.com/download.cgi") will work!

EDIT: Hah, nice one, the .deb is corrupted!
Going back to Windows, where everything is slow as hell, but at least where everything ***WORKS.***

---

### Post by k3lt01 on 2008-07-13
I'm not disagreeing with you, cause I can't find the page right now, but It was only last week I saw something about Creative's new Beta drivers for Linux so I know they haven't stopped support. Methinks you need to make google your best friend and use the "Search within results" function.

---

### Post by LeDechaine on 2008-07-15
Maybe it was the X-Fi drivers.

---

