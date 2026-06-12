---
title: "Install Probs"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by londonlad on 2008-06-20
hi all,

i have an ADVENT 5301 laptop which i really want to install Ubuntu on. but everytime i try, the cd just gets so far then locks up...........ive tried 6.06, 7.10 & 8.04! no joy, same thing everytime! :(

---

### Post by avtolle on 2008-06-20
First question: how much RAM does the laptop have?

---

### Post by kk0sse54 on 2008-06-20
Did you check the integrity of the iso after you downloaded it and the CD after you burned it?

---

### Post by londonlad on 2008-06-20
> **avtolle said:**
> First question: how much RAM does the laptop have?

2gb mate............[http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@1229104460.1213997397@@@@&BV_EngineID=ccffadeegilejffcflgceggdhhmdgmk.0&page=Product&fm=null&sm=null&tm=null&sku=958229&category_oid=-34074](http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@1229104460.1213997397@@@@&BV_EngineID=ccffadeegilejffcflgceggdhhmdgmk.0&page=Product&fm=null&sm=null&tm=null&sku=958229&category_oid=-34074)

---

### Post by londonlad on 2008-06-20
> **C!oud said:**
> Did you check the integrity of the iso after you downloaded it and the CD after you burned it?

im using the proper 8.04 disc, it installed on my desktop ok........

---

### Post by avtolle on 2008-06-20
OK, Cloud hit the next two things I would suggest. Please check those out, too. 

There are a number of reasons you might be having the problems you are having, and unfortunately, I've got to go here in a bit. Do what Cloud suggested, report back, and in the interim I'll give it a bit more thought.

---

### Post by Duck2006 on 2008-06-20
Did you try safe graphic mode?

---

### Post by Wobblybob on 2008-06-20
Have you tried running ubuntu from the CD or are you trying to instal from the start and at what point does it freeze and do you get any messages? Also are you trying to duel boot with XP?

---

### Post by avtolle on 2008-06-20
I've a thought; the hangup on installation might be due to a graphics card problem. If you can, download the alternative iso for 8.04, which uses a text-based, not graphic, installer which often avoids problems with the graphics card. It ends up with the same installation as with the Live CD (which I presume you are using). 

There are some other alternatives other than the graphics card which might affect installation. Try the safe graphics thing as suggested, and if that doesn't work, on boot, hit F6, and at the end of the boot string add, by typing in from your keyboard, all-generic-ide then try to boot from there. There are other boot parameters that might be needed, alone or in combination, but right now I don't have them handy; one is noapci, there are many others.

---

### Post by londonlad on 2008-06-20
ive tried with the 8.04 alternate cd, the screen just goes blank with a flashing cursor in the top left corner!

---

### Post by londonlad on 2008-06-20
> **Wobblybob said:**
> Have you tried running ubuntu from the CD or are you trying to instal from the start and at what point does it freeze and do you get any messages? Also are you trying to duel boot with XP? 


no im not trying to dualboot with XP, i dualboot XP/8.04 on my desktop already, im trying to install 8.04 on my ADVENT 5301 laptop, which atm, is running vista premium! :(

no messages, no nothing! :(

---

### Post by Duck2006 on 2008-06-20
> **londonlad said:**
> no im not trying to dualboot with XP, i dualboot XP/8.04 on my desktop already, im trying to install 8.04 on my ADVENT 5301 laptop, which atm, is running vista premium! :(

no messages, no nothing! :(

Did you use the partition tool within vista to give you some space to install ubuntu?

---

### Post by londonlad on 2008-06-20
partition tool? i just wanna do a clean 8.04 install, i aint too keen on vista! i can even boot into 8.04 using the live cd, that doesnt even touch the hdd! :(

---

### Post by Duck2006 on 2008-06-20
You could try formating your drive with parted magic. Then trying the install.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by londonlad on 2008-06-20
thanks.........im very tempted, but, if it doesnt work, i cant be doing with reinstalling vista if it goes belly-up! then there is the issue of 'will the hardware work'.............all too much hassle, my desktop installed 8.04 no probs, i fear my lappy will be a git & i may have to suffer vista instead!

i usually judge that, if the 8.04 live cd boots ok......then installation should be ok!

---

### Post by Duck2006 on 2008-06-20
Have you tried to boot an other disc'o ie knoppix?

---

### Post by londonlad on 2008-06-20
ewwww, i didnt like knoppix & anyway, im familiar with Ubuntu as i use it on my desktop!

---

### Post by Duck2006 on 2008-06-20
> **londonlad said:**
> ewwww, i didnt like knoppix & anyway, im familiar with Ubuntu as i use it on my desktop!

Just to see if your system boot to a linux cd.

---

### Post by londonlad on 2008-06-21
naaa, knoppix wont boot either! any ideas guys coz i favour Ubuntu to vista!

---

### Post by England_For_Ever on 2009-02-21
> **londonlad said:**
> 'will the hardware work'

no it doesn't mate. i tried on dual boot. Installed wubi, then ubuntu and loaded ubuntu up, had to use the menus because of video problems. Are you using SiS Mirage 3 graphics by default? They don't work, just leaves your screen size as 800X600, and the wireless internet doesn't work, i.e you cannot turn on the wireless device like in vista. my advice, wait until the next ubuntu is out then try that

---

### Post by cariboo on 2009-02-21
You  can  solve your video problem by using the vesa video driver, and as for your wireless device, just because the switch doesn't seem to work, did you try clicking on the network icon to see if any there were any wireless networks available? 

To setup the video driver press Alt-F2 and type:

```
gksu gedit /etc/X11/xorg.conf
```

this will open the configuration file in a text editor, modify the device section like this:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"vesa"
	EndSection
```

save the file and press Ctrl-Atl-Backspace or reboot to restart X. You should now be able to set your resolution to what looks good to you. Unfortunately you won't be able to use any of the visual effects. The chipset manufacturer has chosen not to write drivers, or to make the source open so that someone else can write drivers for the graphics adapter.

Jim

---

### Post by England_For_Ever on 2009-02-23
> **cariboo907 said:**
> 
To setup the video driver press Alt-F2 and type:

Jim

Sorry, where do you press this? On a menu or on the desktop?

---

### Post by Duck2006 on 2009-02-23
> **England_For_Ever said:**
> Sorry, where do you press this? On a menu or on the desktop?

In the terminal.

---

### Post by snapfire on 2009-05-18
i had the same problem with the same laptop,my suggestion is try ubuntu 9.04, before you use live cd or install press f6 for boot options,,select the first and third options {cant remember what they are called}then use live cd or install,it installed for me..screen resolution will be stuck at800x600, but downloading the winshoefer drivers that match your video card[or match them as closely as possible}and open the downloaded file using the gdebi package manager,should give you a screen resolution of 1280x800,,,wireless not working 100% for me at the moment but im working on it, wired internet works fine,i should have done my homework before buying this laptop,but we live and learn,some of the components in this machine are made by S.I.S,probably the most linux unfreindly hardware manufacturer in the world,hope this helps

---

### Post by mkwood64 on 2009-05-24
Hello, I am having a similar problem.  Do the splash screen graphics turn blue when the install freezes?

---

### Post by CaseSensative on 2009-07-06
Did you burn the ISO to fast? What speed did you use? and check the speed on the disc.

---

