---
title: "Diko matikman ang Ubuntu gamit ang Wubi...paano solusyon?"
date: 2009-12-05
forum: Philippine Team
---

### Post by Hal21965 on 2009-12-05
Hello kabayan!  I am unable to install Ubuntu 9.10 via Wubi...three failed attempts already...ayaw talaga tumuloy nung install.  [Here's]("http://ubuntuforums.org/showthread.php?t=1341227") the thread I created to ask for help...diko pa alam nuon na meron palang Philippine Team section tayo.

Bale [Philips MT2700]("http://www.compisland.com/product,16,philips-mt2700.html") ang desktop ko.  I clicked "Download Now" on [this website]("http://wubi-installer.org/")...it put the Wubi icon on my desktop and when I clicked/run it the Ubuntu 9.10 amd64.iso was downloaded.  I was then asked to give a password and then asked to reboot.  After reboot where I selected Ubuntu ang dapat sanang mangyayari eh "the installation will continue for another 10-15minutes" according to [this]("http://i50.tinypic.com/14sjluw.jpg") KASO yung sa akin eh lumabas lang yung white circular Ubuntu icon dun sa black screen ko for about 30 seconds and then nag-disappear na sya...nag-sleep mode na yung monitor ko and silent na yung cpu ko.  I waited, pero wala talaga nangyayari.  Kelangan kopang mag-hard reboot para lang mabuksan uli pc ko.  Inulit ulit kopa yung pag-choose dun sa Ubuntu on reboot pero talagang ayaw tumuloy nung install ko.  Ano kaya problema?  May kinalaman kaya yung ATI Radeon graphics ko?  Driver issue kaya?  Sana matulungan nyo ako maituloy ang install ko ng Ubuntu via Wubi...titikman kolang naman...tapos siguro eh sa LiveCD rin ang tuloy ko later on hanggang sa full install kung mawili ako talaga...kaya lang ngayun palang parang minamalas nako sa Wubi install palang.  Salamat sa mga sasaklolo!

---

### Post by loell on 2009-12-05
magandang malamig na madaling araw kabayan... :)

maaring ang graphics nga ang dahilan sa paghahang, ganoon din kasi ang mga iilang kaso ng wubi at nvidia cards,  nasubukan mo bang mag press ng "escape" during the boot?

---

### Post by badrra on 2009-12-06
Matagal ko na ginagamit Wubi and I am sure hindi sa ATI yan kasi i dedetect lang nya ATI soon pag installed na ubuntu. So while installing, basic installation pa alng gagawin nyan. 

Possible na hindi maganda download nya. Ilipat mo yung Wubi sa isang folder then download mo yung ubuntu in that same folder. Then run wubi. It will automatically detect the ubuntu copy and it will install automatically. Also, check mo add/remove programs make sure na uninstalled yung previous wubi.

Edit: 

Checksum mo na din to check for integrity. Also you will need to download the 64bit ver.

---

### Post by Hal21965 on 2009-12-06
> **loell said:**
> magandang malamig na madaling araw kabayan... :)

maaring ang graphics nga ang dahilan sa paghahang, ganoon din kasi ang mga iilang kaso ng wubi at nvidia cards,  nasubukan mo bang mag press ng "escape" during the boot?
Thanks for the warm welcome!  It's autumn here and wintertime is just around the corner, malamig na nga at panay painit ko ng kape ahahahaha!!!  Yes I tried to press "esc" after I've chosen Ubuntu vs my XP in the boot menu...merong lumabas na 4 options yata yun(Normal, Verbose, and 2 others na dikona maalala)...kaso diko naman alam gamitin mga yun.  I tried the "Normal"...ganun parin...di tumuloy ang further installation.  So I'm stucked talaga.

I also initially entertained the idea na baka nga yung ATI Radeon graphics ko ang culprit pero I was assured by others, like in [this forum]("http://www.webuser.co.uk/forums/showflat.php/Cat/0/Number/441529/an/0/page/1#441529"), that they are using ATI Radeon graphics and their install or update to Ubuntu 9.10(karmic Koala) went smoothly...and so they advised me that maybe it is not my graphics card which is to blame.  Next kung pinagdiskitahan eh yung 64-bit ISO version of Ubuntu that was downloaded by Wubi to my pc...baka kako ang kelangan ko eh yung 32-bit version but I was also assured by others that my pc is very much OK dun sa 64-bit version so it's a no problem issue.

> Possible na hindi maganda download nya. Ilipat mo yung Wubi sa isang folder then download mo yung ubuntu in that same folder. Then run wubi. It will automatically detect the ubuntu copy and it will install automatically. Also, check mo add/remove programs make sure na uninstalled yung previous wubi.Sinubukan ko narin 3x na i-re-download yung Wubi...everytime sinigurado ko talaga na tanggal muna Wubi at Ubuntu bago ako mag-redownload ng Wubi(I also edited the boot.ini that was modified by Wubi to include the Ubuntu option)...pero ganun parin talaga...walang progreso!

Natatakot na nga ako...baka ma-corrupt pc/XP install ko sa kaka-attempt ko...puro failed attempt naman...eh wala pa naman akong means para mag-reinstall ng XP ko.  I don't have XP cd, I don't have Recovery CD, and I don't have the Recovery console installed in my pc.  Tsk...tsk...tsk!  Papaano ba ako makakatikim ng Ubuntu?!  [Others]("http://www.daniweb.com/forums/thread242588.html") even advised me to be careful kasi nga wala daw akong tatakbuhan the moment na kailanganin ko mag-reinstall ng XP ko just in case.

Pasensya na...I hope talaga mag-progress na install ko ng Ubuntu via Wubi.  Tatlong forum na hiningan ko ng tulong(this is the 4th one!) pero di parin ako maka-progreso.  I will stick to this thread...kung wala na talaga pag-asa eh lie-low muna siguro ako.:)

---

### Post by badrra on 2009-12-06
A understand. Sugestion ko wag mo munang ipilit kasi mahirap mag install ng walang CD ng XP. Anyway marami pa namang pagkakataon na mainstall ang ubuntu. Yun lang hindi mo magagamit ang ubuntu 9.10 for a while. Just to give you a good feedback, right now I am using Kubuntu on my machine. Something that I could'nt do with the pevious versions. It is fast, efficient and stable. Dati hangang Xubuntu lang kayo ng PC ko pero ngayon I am running Kubuntu.

BTW: My PC is over 6 yrs old....

---

### Post by Hal21965 on 2009-12-06
Hay naku...malungkot talaga!  I tried to use the older version(Wubi-9.04-rev129.exe) of Wubi kani-kanina lang.  I got it from [here]("http://sourceforge.net/projects/wubi/files/").  No luck and no joy talaga...parehas din ang nangyari...parang nag-hang na sya after mappakita nung Ubuntu icon.  Right now I've removed again the Ubuntu that was downloaded by Wubi AND have deleted the Wubi.exe that was downloaded in my desktop AND have edited again my boot.ini to delete the Ubuntu option.  Lie-low na muna ako.  May bukas pa.  Salamat sa inputs nyo!):P:smile:

---

### Post by Script Warlock on 2009-12-06
kung dual boot na lang kaya sir suggestion lang......pero try muna with live cd kung gumana lahat hardwares....

---

### Post by jaceleon on 2009-12-08
Well, if you're really persistent on installing Ubuntu, I suggest that you make a USB installer of the XP CD. You read it right kuya. USB copy ng XP CD. Prepare that Just in case before you do anything that will create persistent changes on PC i.e. installing Ubuntu.

You can read a lot of material regarding making a USB copy of the XP installer. Google is your friend.

Upon successfully creating one, then create a separate USB installer of your selected Ubuntu distro. Then let the magic begin.

---

### Post by Hal21965 on 2009-12-10
> **jaceleon said:**
> Well, if you're really persistent on installing Ubuntu, I suggest that you make a USB installer of the XP CD. You read it right kuya. USB copy ng XP CD.
Pero papaano yun eh wala nga ako XP CD.  Nung binili ko 'tong desktop ko sa PCWorld eh wala namang kasamang XP cd...at lahat ng makausap ko ngayun sa store eh ganun na daw talaga ang trend ngayun...they don't give the OS cd dun sa buyer ng pc...they just pre-install the OS then sometimes give out a Recovery CD(wala din ako nyan) sa customer or the customer can make one himself(hindi rin ako gumawa/di ako marunong gumawa).  Meron naman ako sa Start>All Program ko na System Recovery...separate partition yata ito...kaso problem eh kung di talaga gumana HD or hindi magboot yung Windows ko eh papaano ko ma-aaccess yung System Recovery ko?  Bale diko alam ngayun kung papaano gagawin sakaling dumating time na kinatatakutan ko(corrupted XP/unbootable pc)...di tuloy ako maka-all d way sa quest ko for Ubuntu.  Mahirap na...at newbie pa!

---

### Post by loell on 2009-12-10
makaktakbo ka ba ng live cd mode ng Ubuntu? na try mo na?

---

