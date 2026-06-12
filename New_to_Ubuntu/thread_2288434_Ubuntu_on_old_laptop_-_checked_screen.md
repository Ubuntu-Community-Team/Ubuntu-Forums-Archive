---
title: "Ubuntu on old laptop - checked screen"
date: 2015-07-27
forum: New to Ubuntu
---

### Post by Jarek_C on 2015-07-27
I'm trying to install Ubuntu on my mum's old Acer Aspire 1350 laptop but when the DVD loads for installation  I only see a checked screen that looks like Scottish kilt. Windows XP loads no problem though so it's not that there is something wrong with the laptop. Got the same when trying to install Fedora. Is there a workaround?

---

### Post by howefield on 2015-07-27
Define "old" and would help to know the machine specifications.

You may want a lighter version of Ubuntu, eg Lubuntu.

---

### Post by Vladlenin5000 on 2015-07-27
[Acer Aspire 1350]("http://www.miniputer.com/Acer/Aspire_1350.html") not looking good for anything recent...

---

### Post by stalkingwolf on 2015-07-27
if yours has the stated specs i would up the ram to at least 1 gb and try kubuntu or lubuntu.  or maybe an alt or lite install .  then just add the programs you need.

---

### Post by Jarek_C on 2015-07-27
Yeah, I tried Lubuntu. Same problem. It looks like missing graphics driver.

---

### Post by sudodus on 2015-07-27
You might have better luck with a community re-spin based on Ubuntu 12.04 LTS, for example ***LXLE, Bento, Bodhi***, which promise support until April 2017.

Or try ***Wary Puppy or TahrPup***.

---

### Post by Jarek_C on 2015-07-27
I'll try that. Thanks

---

### Post by kerry_s on 2015-07-27
so how much ram does your laptop have ? 2gb works great, 1gb you could get by, anything less is a lot of waiting if you can get it to work.

you'll need to boot with "nomodeset" to get working graphics. so when you boot & see the keyboard + stickfigure(?) press enter, then you'll see a menu of options, on try with out installing press "e" , type "nomodeset" & press enter to boot.

---

### Post by roger_1960 on 2015-07-27
Hi

I run one of those! (Aspire 1351)  It needs ubuntu 12.04 xfce as the latest that will work. (I does not have the power to run Unity)  Because this (xfce) is at end of life, your best distro (IMO) is LinuxMint 13 Maya xfce.  It works really well and has no hardware issues.  The bugbear issue is that the AMD XP-M processor does not support SSE2 processor instructions, so many newer versions (and their repository apps) do not run well. I used to use Bodhi (2.4) on it but recent updates introduced apps that need SSE2 instructions.

---

### Post by Jarek_C on 2015-07-27
Yeah the laptop has only 512MB of RAM. I had lots of this chips lying around but now they're somewhere at my grandma's basement. I'll try the Mint and get more RAM next time I have a chance. Thank you all for the very useful tips.

---

### Post by Jarek_C on 2015-07-28
All works :)

---

### Post by sudodus on 2015-07-28
Congratulations :KS

Please share the details of your solution with us in order to help other users :-)

And finally, please click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

