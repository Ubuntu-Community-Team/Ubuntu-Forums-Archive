---
title: "Takot ako sa..."
date: 2008-03-18
forum: Philippine Team
---

### Post by yssida on 2008-03-18
Amm, bago ko po ituloy iyon, ako po si yssida, na pinopronawns na 'isda'.  Bago pa po ako sa mundo ng linux at free and open source software. Pero di naman talaga bagong bago, I tried knoppix a while back and it was really nice. Ang main reason po na nagdecide ako na magswitch (or partially switch for now, i'll get there :) )  ay kasi ho sa philosophy ng free software. Maganda po ang idea na ito na dapat matamasa ng maraming tao. My ubuntu 7.10 na i386 ay dumating na via shipit at nagburn rin ako ng 64bit version, kasi mali pala iyong na-request ko. Anyway, may ilan lang po akong apprehension bago ko i-install itong Ubuntu sa aking laptop....at going back to topic....

**takot ako** na mabawasan ang buhay ng hard drive ko :( . Totoo po ba na may isang unsolved bug sa Ubuntu power management na nagcause daw na increase yung load/unload cycles(:confused:), thereby shortening its lifespan? May isa pa rin pong article na nagsabing firmware lang daw ito o BIOS problem at walang kinalaman sa ubuntu. Meron pa rin akong nabasa meron nga po (and it's in this forum, nakalimutan ko lang) at merong temporary workaround. Naconfuse ako! (nakalimutan ko tagalog ng confused, bisaya ako, and late at night na po sorry) alangan naman, nalibog ako! :)


said aticles
[http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)
[http://www.cyberciti.biz/tips/ubuntu-linux-hard-disks-may-shorten-lifetime.html](http://www.cyberciti.biz/tips/ubuntu-linux-hard-disks-may-shorten-lifetime.html)

---

### Post by februarius on 2008-03-18
ahihihihi naririnig ko na sya before, pero di ko pa naman na prove sa ubuntu na ganyan nga ahihi... im quite using debian eversince then upto now debian then little adoptation sa ubuntu, almost a 4 years stick to debian dist ako. never ko pa na encounter na siraan ako ng hardisk, good thing pa nga ang pagamit ko sa linux kasi ung may mga physical badsector na skip then usable ko uli ung hardisk :d

---

### Post by yssida on 2008-03-19
hindi ko po alam eh...pero if that's a feature found in linux distros, then mabuti nga po iyon na nagski-skip sya. iyon lang po talaga ang main concern ko na nagwewear out ang hard disk na mas mabilis sa normal, hindi ko po afford na bumili ng bago kung mangyari man.

---

### Post by loell on 2008-03-19
wag kang maniniwala dun, ;)  walang mangyayari sa hard disk mo.

at sa ka kung may mangyari talaga sa hard disk mo, no worries, bibilhan ka ni febrarius  nang bago :lolflag:

---

### Post by salbahis on 2008-03-19
kuyawa gud ug mao man gani maguba ang hard disk, mag palit nalang kog daghan, pareha jud ta!!!

---

### Post by Nhatz on 2008-03-19
Mas lalo ngang nasira yung hard disk ko nung windoez pa gamit ko... hehehe :)
Astig! :guitar:

---

### Post by yssida on 2008-03-19
pag meron po ako narining strange sounds report ko agad sa inyo po. salamat po sa mga reassuring comments :)

---

### Post by ragadanga63 on 2008-03-19
This affects only a few laptop models/brands.  I think it was a few Lenovo laptops and a couple of other brands.

Ubuntu has been running on my Compaq laptop for about a year now.  So far no clicking yet.

---

### Post by raxso on 2008-03-19
So far almost a year na itong dell laptop ko wala namang issue about sa hard drive... and sa pc ko n P3 eh ok naman, maganda p arin ang takbo using linux... sa windows na sira yung HDD ko kasi may virus... hehehehehe

---

### Post by yssida on 2008-03-20
Okay, so I've decided to take the plunge and install ubuntu. Another problem hit me, hindi ko pala alam ang proper na pagpartition ng hard disk..I followed manual...pero mas lalo akong nahirapan. Alam nyo na siguro na plano ko pong magdual boot with Vista. i did the hard drive formatting thing in Vista..I resized it etc...followed online tutorials...ngunit di ko naman maintindihan...it seems as if linux treats everything, including hardware as directory...hindi ko maidentify kung saan iyung may Vista na partition, yung dalawa pang partition (iba-ibang format) na di ko alam ang gamit,at saka yung free space...well yung free space naman, may 'free space' so alam ko pala yun.huhu confuzzled na naman ako///....:(

---

### Post by ragadanga63 on 2008-03-20
Hmmm...ganoon talaga pag mag-umpisa pa lang.  I'd love to help you out.  Medyo pareho ang set up natin.  Have you shrunk your Vista partition to make way for Linux?  Kindly post your hard drive partitions.

---

### Post by yssida on 2008-03-20
Opo, I have shrunk it, now I have 48 gigabytes na of free and unallocated na space.I don't know which way to go next.Ang laptop ko nga pala a Toshiba Portege M600. Noong pagboot ko with the live CD, hindi yata niya alam na 1280 x 800 ang preferred na screen resolution, walang sound at hindi maenable ang visual effects.

[[IMG]http://img296.imageshack.us/img296/7176/screenshotlz4.th.png[/IMG]](http://img296.imageshack.us/my.php?image=screenshotlz4.png)

---

### Post by glenn45 on 2008-03-21
Hello yssida,
Pwede mo mamodify yung screen resolution mo duon sa may [system -> preferences ] na menu. hanapin mo lang duon yung screen resoultion ata...hehe. sorry. di ko ma bigay yung exact path pero, hanapin mo na lang duon.

yung desktop effects kelangan naka install yung specific na graphics driver para sa laptop mo kaso di ko alam kung ano ang para sa laptop mo.

---

### Post by ragadanga63 on 2008-03-21
yssida, 

I've prepared a mini-howto for you.  Paki-PM na lang sa email mo so I can send it to you.

Di ko ma-attach  dito kasi nag exceed na sa file size limit.

---

### Post by killer_d76 on 2008-03-22
guys.. i've open my laptop today and i saw this message flashed across the screen "/dev/sd2/ has been mounted several times without checking" and then it did some checking for a few seconds and boot back to ubuntu?.. what does that mean?.. will this damage the harddisk of my laptop? need help here too!.. thanks!

---

### Post by loell on 2008-03-22
that's **fsck**, it just checking your file system for errors.

more detail [http://en.wikipedia.org/wiki/Fsck]("http://en.wikipedia.org/wiki/Fsck")

---

### Post by killer_d76 on 2008-03-22
hi loell, thanks for the quick reply and info!.. but how it was unmounted when i haven't done anything on it?.. is /dev/sd2/ my harddisk? or was it anything on my laptop that was unmounted for 35 times that i don't know of?.. thanks

---

### Post by loell on 2008-03-22
during shutdown the filesystem is being unmounted.

---

