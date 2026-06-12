---
title: "Problem using an old Inno3d AGP-VA Graphics Card"
date: 2008-06-15
forum: Philippine Team
---

### Post by jeffimperial on 2008-06-15
I'm not much of a hardware tech, but I know the LoCo Team has several of them, so I come in humble need of help :)

I have a friend who brought her PC here at my place. The [old, real old] PC had WinXP on it and was working fine. For some unknown reason, the graphics card (see complete hardware description below) stopped working properly; as in there are "dead" lines all over the screen. You'd still see the images but it's like a dot matrix printer's output when the ribbon runs out of ink -->can't think of a better desciption.

Anyways, I'd like to install Xubuntu or Edubuntu on it. I'm still downloading the ISO for that, so I'm using a Hardy LiveCD to test it. When I do, stuff load like normal. But when the orange-on-black status bar fills up, I get to a blank screen with some squiggly lines on the upper portion.

This also goes for the Fedora 9 LiveCD.

When I try "safe-video-mode" in the Boot Options of the Ubuntu 8.04 LiveCD, I get "Kernel panic - not syncing - VFS - unable to mount root fs..."

Graphics Card in question:
Inno3D
MX 400 64BIT 64MB AGP VA
-->This is what I see on the sticker on the Graphics Card

Tornado
Geforce2 MX
-->This is what I see printed on the card's underside

I dunno if this would help, but the Mother Board is an Asus P4PE
Processor = Intel Pentium 4

---

### Post by loell on 2008-06-15
probably the card is already toasted? how about the monitor? did you try different monitors?

---

### Post by jeffimperial on 2008-06-15
> **loell said:**
> probably the card is already toasted? how about the monitor? did you try different monitors?
I have tried one other monitor and got the same thing. I don't think the card is toasted yet (though I think it's probably due for retirement) since I can see the Ubuntu Logo and the status bar just fine. Any other ideas?

---

### Post by jsgotangco on 2008-06-15
what does dmesg and dmidecode tell you?

---

### Post by jmazaredo on 2008-06-15
Try cleaning the video adapter first and the slot (AGP) if this doesnt help, the card is the problem. lines all over the place with different colors.. garbage picture adapter problem.

Palagay ko dumi nalang nag papagana dyan. eh ginalaw hayun nawala yung dumi kaya ganun :O

---

### Post by jeffimperial on 2008-06-15
> **jsgotangco said:**
> what does dmesg and dmidecode tell you?
Well, I really can't find out since it's all LiveCD. It's been a virgin as far as Linux is concerned :)

---

### Post by jeffimperial on 2008-06-15
> **jmazaredo said:**
> Try cleaning the video adapter first and the slot (AGP) if this doesnt help, the card is the problem. lines all over the place with different colors.. garbage picture adapter problem.

Palagay ko dumi nalang nag papagana dyan. eh ginalaw hayun nawala yung dumi kaya ganun :O
Haha.. I just got it to work. Here's what I did:
In the BIOS options > PCI Configuration > Changed AGP-PCI to AGP-VGA
Before selecting to boot, press F4 for GUI selection of Safe Graphics Mode. It got into the Live User Session just fine,

But the darn thing fell into another problem. Ang lumalabas na HD sa "Computer" eh hindi 30 GB Device or anything that I'd expect, kundi "SCSI Device". Kapag sinubukan kong install-an, partition manager fails.. Naku naku..

---

### Post by loell on 2008-06-15
> **jeffimperial said:**
> Well, I really can't find out since it's all LiveCD. It's been a virgin as far as Linux is concerned :)

you can also execute those commands in a livecd session :)

---

### Post by jsgotangco on 2008-06-15
> **jeffimperial said:**
> Well, I really can't find out since it's all LiveCD. It's been a virgin as far as Linux is concerned :)

it should work as long as the kernel is loaded even on a live cd session

---

### Post by jeffimperial on 2008-06-16
Oh. Is that so? Good to know, para next time...

Anyways, mukhang hindi pa natatapos ang aking problema. It's a really old PC so it's expected.

For some odd reason, naging Unallocated Space 'yun buong hard drive na iinstallan ko sana. Kaya ikinabit ko as slave sa isa kong PC. Tapos ni-reformat ko doon. Kaya hayun, nainstallan ko na sya ng Ubuntu (on the old PC).

Problem is, hindi nag-prompt ng para sa restricted drivers matapos ang install. Inupdate ko muna tuloy, tapos restart. I was still stuck at low resolutions, so I decided to go to Hardware Drivers. Nakita ko, In Use naman ang restricted driver, pero unchecked ang Enabled checkbox. Check ko sya at restart ulit. Ganun pa rin, low resolution. 

I went to nVidia.com at ininstall ko 'yung tamang GPU driver. Ayos naman, nag-install sya. Kaso, nung mag-reboot ako, may error. Pinapili nya pa kung aling card meron ako, at kung aling monitor ang gamit ko. Eh di ko nakita iyong akin, kaya cancel ko. It logged me in fine, but still at low resolution.

Kaya ginawa apt-get install envyng-gtk. Nag-install sya, at pina-reboot ulit ako. Nung makapasok na ako ulit, low resolution pa rin.

*SIGH*

Kaya mamaya pag-dating ko sa bahay di ko naayos within 30 minutes, susubukan kong i-clean install si Gutsy. Baka gumana na. 

:)

---

### Post by Samhain13 on 2008-06-17
Teka, teka. Batuhin niyo na lang po ako kung nagkakamali ako, pero diba dito:
> In the BIOS options > PCI Configuration > Changed AGP-PCI to AGP-VGA
ibig-sabihin, ang gumaganang video card ay on-board at hindi yung nVidia?

Kung gayon, gagana kaya ang nVidia drivers sa on-board card ng "Asus P4PE"? Kasi kung hindi, bakit pa kailangan ng nVidia drivers? Baka naman kaya "hindi nag-prompt ng para sa restricted drivers matapos ang install" kasi nga hindi kailangan ng restricted (nVidia) drivers at yung on-board ang umaandar?

Anyway, baka naman ang ibig-sabihin lang nito (galing sa unang post): "I get to a blank screen with some squiggly lines on the upper portion" ay hindi lang tugma yung settings sa xorg.conf ng LiveCD sa nVidia card? Kung ganun, nakakapasok ka ba sa terminal kung mag-CTRL-ALT-F1 ka? Kasi kung nakakapasok, ibig-sabihin nun, nagagamit yung nVidia pero hindi ka lang makapasok sa graphical interface.

---

### Post by jeffimperial on 2008-06-17
Sorry, AGP-PCI pala talaga ang tama. Card nga siya, Inno3D ang may gawa, at wala nga syang onboard video. Anyways, medyo ayos na rin naman kahit hindi ko gamit 'yung restricted driver. In fact, nasisira nga kapag 'yun an gamit ko - as in hindi ma-load ang gdm.

Installed and working na sya ngayon. Kaso nung pinalitan ko ng monitor (one that was newer), hayun, ayaw nanaman mag-load ng gdm. Kaya reformat at reinstall nanaman ako.

By the way, may paraan ba na i-reset lang ang lahat na related sa X (na parang bagong install na Ubuntu) without *actually* going through the complete installation process again?

---

### Post by Samhain13 on 2008-06-17
Try mo i-reconfigure yung xorg.

```
sudo dpkg-reconfigure xserver-xorg
```

kung magkakabit ka ng bagong monitor. Then, restart x(?).

Tapos pagnakapasok ka na sa GDM, para makuha yung mga gusto mong resolutions (kung medyo "unknown" yung monitor mo na tulad sakin at nabili ko lang sa surplus shop), punta ka sa Applications > Other > Screen and Graphics Preferences. Kung wala siya sa menu, right click mo yung Applications tapos "Edit Menus", check mo yung item na yun para lumabas.

Pagnakuha mo na yung dialogue box nung Screen and Graphics Preferences, click mo yung Model at mamili ka na lang ng babagay sa monitor mo. In my case, kinuha ko: Manufacturer (Generic), Model (Monitor 1600x1200).

---

