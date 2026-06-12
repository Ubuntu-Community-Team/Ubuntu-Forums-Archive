---
title: "Unable to Install driver for Canon Pixma iP 2600 printer in Ubuntu 14.4"
date: 2015-04-01
forum: New to Ubuntu
---

### Post by Victor_Gilbert on 2015-04-01
I opened printer in software centre - and for all 3 ports I searched printer driver to download. In each case it started downloading from Gutenburgh and then froze.
I tried downloading driver from Ubuntu database but although lots of Canon drivers not unfortunately mine!

Is there an alternative to try?

Victor

---

### Post by arochester on 2015-04-01
[http://ubuntuforums.org/showthread.php?t=811811](http://ubuntuforums.org/showthread.php?t=811811) ?

---

### Post by pdc on 2015-04-01
so Victor; welcome to the ubuntu forums; that is a senior and trusty printer you have there: it must be 7yrs old and still going strong; back then, ubuntu was 32bit and so the drivers were 32bit; nowadays many install 64bit ubuntu and that may clash with the older printer;

arochester has pointed you to a thread that I think is fairly long and involved; 

perhaps the simple answer is: yes, Canon did release a debian (ubuntu-supporting) driver back then; so it is still available; 

so I can point you to the driver; and how to install it; but there will likely be a couple of steps beforehand; ............ a bit like putting lime and fertiliser on the soil before putting the plant in .........

__________

do you want some details? (I ask because you may well have digested the 2008 post .................)

---

### Post by Victor_Gilbert on 2015-04-02
Thanks
> That is a senior and trusty printer you have there: it must be 7yrs old and still going strong;
Yes your right - I'm 77 but not going so strong!
> so I can point you to the driver; and how to install it; but there will likely be a couple of steps beforehand; 

Yes would like to try - been through the 2008 post - but have a keen gardener for a wife.

Victor
Having big trouble booting up my 10 year old Acer Extensa  series - so may not beback for a time

---

### Post by pdc on 2015-04-02
............sorry forgot to ask you .......... are you using a 32bit ubuntu please? 

If you are, there are 3 steps: 

1) install libtiff4 from here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and go 17 down for the 386 driver (the 32bit one..) ........clicking on it should activate Software Center ..............that should offer to "open" it .........which means *install* so accept that kind offer .........
2) install the Canon drivers: back then, in 2008, they issued a COMMON driver and then a SPECIFIC one for each printer ....... 7yrs on, current printer have a standard install script that covers all new releases ..................
3) register the printer on your system (ie you are telling it .......when I ask you to use .. XXprinter........please use YY.ppd to do the work ..........)

______________

.........so the details .............-

1) install libtiff4 from here [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and go 17 down for the 386 driver (the 32bit one..) ........clicking on it should activate Software Center ..............that should offer to "open" it .........which means *install* so accept that kind offer .........
2a) get the COMMON Canon driver from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html) and click to download and select OPEN and it should be installed ............
2b) get the SPECIFIC driver from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html) and again select OPEN and it should be installed .....
__________

3) ............. sort of hoping the specific install creates a registration; so click on this link [http://localhost:631/printers/](http://localhost:631/printers/) which opens your printer admin; it is just on your computer; and 4th column: Make & Model; .. do you see an entry for "Canon ip2600 series Ver.2.90"

.............if you do, it is registered............if not ..............go to Menu..................Printers....................... ADD and when you click to add the system should find the ip2600 and it will find the right ppd file etc and it should all be good ...........

_________

if you have 64bit.........seems unlikely given the seeming seniority of your computer........ we will add some symbolic links before we start a 64 bit install ............

---

### Post by Victor_Gilbert on 2015-04-02
Whow!

But have a 64 bit Ubuntu! Giving it a clean- so can check age.
Victor

---

### Post by pdc on 2015-04-03
OK Victor; 

for 64bit: 

1) make symbolic links ........open terminal......... control and alt and t keys all held down together.....then copy these commands and paste line by line into terminal; paste into a terminal is 3 keys: shift and control and v keys all held down together ....... hit enter key and the terminal is immediately ready for the next command .................(it doesn't flash a signal like..........ok victor, I have done that .........it just sits ready for the next command .........)

```
sudo ln -s /usr/lib /usr/lib64
```

```
sudo ln -s /usr/local/lib /usr/local/lib64
```

2) install libtiff4 for 64bit so go here as before [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and go 14 down the list for your 64bit version ............

3) install drivers as described before .........

4) register if needed..............as described before

________---

any joy?

---

### Post by Victor_Gilbert on 2015-04-03
Thanks [SIZE=3]**pdc**[/SIZE]

Carefully followed instructions BUT
[PHP]2a) get the COMMON Canon driver from here http://support-asia.canon-asia.com/contents/ASIA/EN/0100118902.html and click to download and select OPEN and it should be installed ............
2b) get the SPECIFIC driver from here http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html and again select OPEN and it should be installed .....[/PHP]
Got an error message for 2a: *Dependency is not satisfied: libcupsys (>=1.2.1)*
& same message for 2b cnijfilter-ip2600series.

At least I've seen there really is an ip2600 series!

A solution would be to re-install WinXp alongside Ubuntu (IF POSSIBLE) & saving from Libre Office in Ubuntu to a memory stick and printing from Libre Office in WinXp . What do you think?

Thanks again for all your efforts

Victor

---

### Post by sandyd on 2015-04-04
Apparently, libcupsys2 is a dummy package. See [https://bugs.launchpad.net/ubuntu/+bug/458445](https://bugs.launchpad.net/ubuntu/+bug/458445)

Seeing as its a dummy package, we can just fetch the last version and install it from an older version of ubuntu.
```

wget http://launchpadlibrarian.net/25606454/libcupsys2_1.3.9-17ubuntu1_all.deb
sudo dpkg -i libcupsys2_1.3.9-17ubuntu1_all.deb
```

Follow instructions again after that, should be fine

---

### Post by Victor_Gilbert on 2015-04-06
> Follow instructions again after that, should be fine 				

Gave it my best shot - No Go

Hoping the WinXp way works

Victor

---

### Post by sandyd on 2015-04-07
What error are you getting?

---

