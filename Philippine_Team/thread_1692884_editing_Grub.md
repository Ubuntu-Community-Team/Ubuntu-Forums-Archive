---
title: "editing Grub"
date: 2011-02-22
forum: Philippine Team
---

### Post by eeeris on 2011-02-22
Kamusta!

Ask ko lang kung pano ko edit grub? everytime na kapag nag-update ako..nadaragdagan yung menu ko sa grub...paano ba dapat gawin para maalis ko o delete ung old version ng kernel? since di ko naman xa pinipili..ang haba na kse ng menu ko. Salamat!
:guitar:

---

### Post by jepong on 2011-02-22
pa try...

```
sudo apt-get autoremove
```

ako kasi aptitude ginagamit ko instead of apt-get... inaalis kasi ni aptitude yung packages na di mo need like old kernel. you need to install aptitude na ata sa Ubuntu 10.10.

---

### Post by jao_madn on 2011-02-22
try to use some GUI..there are lots of gui about editing your requirements just search.. i forgot those name of the GUI but i know there a lots of it..The idea for the search is linux startup search GUI.. or grub GUI ng linux.

---

### Post by Script Warlock on 2011-02-22
na doble :)

---

### Post by Script Warlock on 2011-02-22
pwede mo matanggal using synaptics at ubuntu tweak...

---

### Post by jepong on 2011-02-22
try this one... Use Startup Manager daw.
 [http://ubuntuguide.org/wiki/Ubuntu:Maverick#Use_Startup_Manager_to_change_Grub_settings](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Use_Startup_Manager_to_change_Grub_settings)

---

### Post by tech-hero on 2011-02-22
ako mano mano lang. hehe. delete the old kernels, ititira ko yung latest then update grub. yun lang. pero hindi ko gagawin yun after ng update, siguro a month after para for sure na walang prob sa kernel. para incase may prob, pwede ko pa sila ibalik using the old kernel.

---

### Post by Ravskie on 2011-02-23
maybe you can use the default " Computer Janitor " .....

---

### Post by franchoy on 2011-02-23
marami bang lumalabas na options dun sa choice mo ng OS?kung ganun man eh try installing **grub manager** un ang solution na hinahanap mo.... :)

---

### Post by jepong on 2011-02-23
i think di naman masama maraming kernel sa grub list mo. fallback plan mo rin yan kung may bug pa yung new kernel. di naman din cya ganun kalaki... sa pagkakaalam ko ang recommended size ng /boot is 250mb.

---

### Post by tech-hero on 2011-02-23
> **jepong said:**
> i think di naman masama maraming kernel sa grub list mo. fallback plan mo rin yan kung may bug pa yung new kernel. di naman din cya ganun kalaki... sa pagkakaalam ko ang recommended size ng /boot is 250mb.
 
ganun na nga. saka, gasino lang ang 30mb bawat isang kernel compared sa Gigabytes of available memory :D pero minsan kasi, nakakainis sa startup ng grub yung mdaming pagpipilian eh. kaya ako naOOC, imbes idelete ko, binabackup ko nalang sa ibang folder at update grub. hehe.

---

### Post by franchoy on 2011-02-23
> **tech-hero said:**
> ganun na nga. saka, gasino lang ang 30mb bawat isang kernel compared sa Gigabytes of available memory :D pero minsan kasi, nakakainis sa startup ng grub yung mdaming pagpipilian eh. kaya ako naOOC, imbes idelete ko, binabackup ko nalang sa ibang folder at update grub. hehe.

try mo ung grub manager, GUI pa sya. dun na-solve ung problem ko na yan eh

---

### Post by pinoyskull on 2011-02-25
you can remove the old linux-images, just dont delete the 2 most recent ones :)

---

