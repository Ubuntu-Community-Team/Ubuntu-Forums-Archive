---
title: "help: i can't install ubuntu 7.10 to my laptop"
date: 2007-12-06
forum: Philippine Team
---

### Post by traxid on 2007-12-06
any help here to install ubuntu 7.10 to my acer travelmate 280 series, i have only here the CD's that came with it( the windows xp home oem and its drivers) i tries running the live cd but there is blank screen after running the live cd,thanks

---

### Post by gbutalid on 2007-12-06
The Live CD needs about 256 MB of RAM. How much RAM do you have on your laptop?

---

### Post by ragadanga63 on 2007-12-06
Make sure that the Ubuntu live CD u are using is not a bad burn.  Check MD5sum.

---

### Post by traxid on 2007-12-06
may laptop has 512 MB of RAM, the live CD im using is the 1 sent by canonical,i have run it into my two desktop and runs perfectly and eventually installed the ubuntu 7.10( CD sent by canonical) into my 2 desktop, sa laptop ko lang ayaw gumana ng live CD

---

### Post by loell on 2007-12-06
whats the last thing you see before the black screen?

---

### Post by ragadanga63 on 2007-12-07
Please tell us up to what point in the booting process you encounter problems.  Have you tried pressing F6 on GRUB, and then entering the following options:  * noapic irqpoll noirqdebug*, then press Enter to continue booting?

---

### Post by traxid on 2007-12-07
yung parang welcome screen nya na may progress bar,then dapat yata ang kasunod noon is yung log in name na,pero naging blank na yung screen( color black na)

---

### Post by Hanamichi Sakuragi on 2007-12-08
[COLOR="Red"][SIZE="2"][FONT="Comic Sans MS"]sa tingin ko bro sa md5sum nga yan..di match..Nangyari na rin sa akin yan...Kaya nagdownload me ulit pero ibang torrent na....Pero try mo muna check...search mo lang md5sum. I assume naka XP ka pa rin...right click mo lang yung ubuntu 7.1 gutsy gibbon ISO file then open with mo...Select mo yung md5sums.exe na dinownload mo then magapear na yung md5sums niya...then check mo sa download site kung parehas lang...kung di parehas eh dowload ka ulit...Kung  okay naman ay burn mo na lang ulit..Baka may nangyaring di kanais nais during
burning :lolflag:[/FONT][/SIZE][/COLOR]


Linux Mint User
Registered # 459692

---

### Post by ragadanga63 on 2007-12-08
Have you tried the *noapic irqpoll noirqdebug* options during booting?  Certainly looks like that's your problem.

---

### Post by traxid on 2007-12-08
thanks po sa mga replies

i think wala pong problen yung ubuntu CD ko kasi gumana naman ito sa dalawang desktop ko,napagana ko yung live cd at the same time na install ko na na yung ubuntu sa 2 desktops,so faw wala naman problem,
dito lang talagas a laptop ko ayaw gmana ng live cd,check ko sana kung compatible sila para eventually install ko na rin ng ubuntu itong lappy ko

---

### Post by traxid on 2007-12-08
> **ragadanga63 said:**
> Have you tried the *noapic irqpoll noirqdebug* options during booting?  Certainly looks like that's your problem.

ano po itong " noapic irqpoll noirqdebug"
san ko ito makikita?

---

### Post by traxid on 2007-12-08
other members posted this

"Its definately something to do with your graphics in that laptop. The newer the onboard intel graphics the more annoying to deal with. It could also be some weird thing wtih the 64 bit disk, but if your using the 32bit install my guess is its jacked up graphics drivers. Do some searching for solutions for your specific graphics chip"

32 bit lang po yung laptop ko so def. 32 bit din yung ubuntu cd na ginamit ko

---

### Post by eilu on 2007-12-08
> **traxid said:**
> thanks po sa mga replies

i think wala pong problen yung ubuntu CD ko kasi gumana naman ito sa dalawang desktop ko,napagana ko yung live cd at the same time na install ko na na yung ubuntu sa 2 desktops,so faw wala naman problem,
dito lang talagas a laptop ko ayaw gmana ng live cd,check ko sana kung compatible sila para eventually install ko na rin ng ubuntu itong lappy ko

try another CD. Un ang pinaka mabilis na suggested solution. Nangyari na sa akin na ayaw magload ng Dapper CD sa laptop pero gumagana sa desktops. Never found out why; burned a new CD and install worked fine.

---

### Post by loell on 2007-12-08
> **traxid said:**
> other members posted this

"Its definately something to do with your graphics in that laptop. The newer the onboard intel graphics the more annoying to deal with. It could also be some weird thing wtih the 64 bit disk, but if your using the 32bit install my guess is its jacked up graphics drivers. Do some searching for solutions for your specific graphics chip"

32 bit lang po yung laptop ko so def. 32 bit din yung ubuntu cd na ginamit ko

try to start the livecd in safe graphics mode. you can select the safe graphics mode during the livecd boot process.

---

### Post by traxid on 2007-12-09
i've tried it to run in safe graphics mode but to no avail

---

### Post by raxso on 2007-12-09
Can you try this.

At the menu press F6 and add these parameters:

Code:

noapic irqpoll noirqdebug

NOTE: Only adding 'noapic' to the boot parameters has been reported to disable the USB ports. Only adding 'nolapic' has been reported to prevent the NVIDIA driver from loading correctly. However use of both 'noapic and 'nolapic' is not know to cause these problems. Also if you use "IRQPOLL" or "IRQFIXUP" along with "noapic" will enable usb support.

Code:

Select  safe mode, hit F6 and add the option: "all_generic_ide" right before "quiet splash"

---

### Post by KalChung on 2007-12-09
You may want to check you laptop&#347; memory, the ubuntu cd should have an option to run a memory check.

I had a similar problem before when installing on a desktop, it works on others desktop/laptops but didn´t want to install on one particular pc, turns out one of its memory modules was damaged.

Graphic problems normally shouldn´t surface during install, unless your vid card is one of the older generations.. from my own experience any vid card since 2003 should install fine..

---

### Post by traxid on 2007-12-11
tnx for the replies guys, ill try it tomorrow, my lappy was bought 2003

---

### Post by perbiu on 2007-12-11
Puede rin na mahina na yung lens ng Laptop CD Drive kaya nag loloko.

---

### Post by traxid on 2007-12-12
about the lens?
i think there's no problem about it coz i can play audio CD,DVD movies, read files from a cd-r,cd-rw, and i recently installed a software from a cd

---

### Post by loell on 2007-12-12
do try the ```
noapic irqpoll noirqdebug
```   during the boot process by pressing the **f6** during the boot menu on the livecd session. and see what happens :)

---

### Post by traxid on 2007-12-12
up

---

### Post by loell on 2007-12-12
wuzz up? is it "up thread"? or do you mean the system is up already? ;)

---

### Post by traxid on 2007-12-16
im trying to do it now

---

### Post by bboyskidz on 2007-12-21
i have ubuntu on my travelmate 280 right now.

it does take about 3 minutes to boot into the live cd and it goes blank while it does this.  It also does the same thing for about 20-30 seconds while it boots into the successfully installed OS.

i figure it is just the way that the splash/loading screen for ubuntu loads itself.  It never worked in previous versions either...

My suggestion - boot up the live cd and then go make a sandwich. by the time you come back, it should be waiting at the live cd desktop.

---

