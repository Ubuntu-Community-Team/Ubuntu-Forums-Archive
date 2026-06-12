---
title: "My dad bought me a laptop..."
date: 2009-06-04
forum: Philippine Team
---

### Post by zilu54 on 2009-06-04
My dad bought me a laptop since I am now entering college...
I would like to ask some help to customize my laptop.

Gustu ku sana ay na boboot siya sa Windows and Ubuntu [pwede naman dual booting at nakikita naman tuwing mag iinstall ng ubuntu diba] may mga iba pang mas maganda para hindi naman hazzle sa pag boot at merun pa aku nakikita sa iba na VMWare?

Ang windows ay gagamitin para sa Photoshop, Inkscape, MS Presentation at iba pang kailangan since dominating naman talaga ang Windows sa college [Graphic Arts = Photoshop] at ang Ubuntu naman ay para na rin sa safe surfing/downloads, gimp, document viewers at inkscape na rin. Halos parehas lang sila sa pangangailangan kaya pwede iisa lang ang OS para sa laptop, Kaso na enjoy aku sa Ubuntu at kailangan ku rin ng Windows dahil ginagamit rin kasi ng mom ku at medyu nalilito sa Ubuntu *dahil sa YM at nahihirapan gumamit*

[B]Ang specs nga pala ng aking laptop ay:
- Gateway ang tatak
- Windows Vista Home Premium
- 3GB of RAM
- 222GB HD Memory
- Intel Pentium Dual-Core Inside[/B]

Ang balak ku sana ay kahit naka-partition ang Ubuntu ng 50GB.
Sa inyu na rin po aku humihingi ng tulung kung papaano ipatakbo ng maganda ang Laptop ku dahil wala na rin akung ibang mahingian ng tulong since nag under-maintenance ang Convergence Forums.

Salamat po ng marami sa inyo.

---

### Post by mahn on 2009-06-04
parekoy, try this tuts from EasyBCD wiki site coz this one works for me. 
[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

I have my Dell Inspiron partitioned and multi-booted (Vista / Ubuntu 8.10) with EasyBCD as my bootloader. Pero ang mgging task mo lng kung pano ka mglalaan ng hard disk space pra sa Ubuntu. Mahihirapan ka kung nka-setup na agad ung Vista before ang Ubuntu pgdi pa nkpartitioned ang HDD mo. But sometimes, you will end up formatting your machine and installing Ubuntu before Vista, so you must have your Vista Recovery DVD with you.

---

### Post by dannybuntu on 2009-06-04
Sorry, hindi ko naintindihan gusto mo. Pero, anyway, kung ang gusto mo ay mag dual boot. Tama lang na unang nakainstall ang microsoft os. 

Kapag nauna kasi na nakainstall ang Ubuntu tapos pinatungan mo ng microsoft os - mabubura ang GRUB. Kumbaga sa Borg e "Resistance is Futile - You will be assimillated" (Tama ba spelling nun)

---

### Post by Ravskie on 2009-06-04
try to use partition magic for the vista first then thats it install ubuntu. dual Boot din ako dito sa opis using jaunty/M$ hehehehe !!!

---

### Post by Script Warlock on 2009-06-04
kug tulong lang nandito mga guru natin handa anytime 24/7....:KS

---

### Post by zilu54 on 2009-06-04
:) salamat po...sa marami~
halimbawa, kung papatungan ku ng ubuntu ang windows ku ay wala namang prublema at sa first post ni mahn, pwede ku bang gayahin tu? yung smooth dual booting

```
[FONT=monospace]
[/FONT]gksudo gedit /boot/grub/menu.lst[FONT=monospace]

thenchange from [/FONT]
timeout 5

to

timeout 0

```

...pwede po ba pa explain specifically yung EasyBCD?

salamat po ulit sa inyu.

---

### Post by leipogs23 on 2009-06-04
Oo. Just customize it 1 step at a time, andito lang sila para tumulong. Ako kasi bago bago pa lang din nagsstart sa ubuntu.hehehe. Kung gusto mo ipartition yang PC mo tapos Windows ang laman. Kelangan ata talaga ireformat, unlike sa Ubuntu na me partition editor blablabla.

Correct me if Im wrong, pero tingin ko. You could install wubi first to try ubuntu on your machine. Tingin ko pedeng magkasama Windows at Ubuntu in the same partition. Am I right guys???

---

### Post by zilu54 on 2009-06-04
^ peru pwede naman yata hindi na kailangan i-format pa ang windows dahil gagawa aku ng bagung partition para sa ubuntu sabihin natin na tatapyasan ku ng 50GB ang HD ku for ubuntu.

hehehe tinatamad kasi aku mag install ng ubuntu sa laptop ku kahit ginugustu ku [kasi kinakabahan akung kalikutin tung laptop] first time lang kasi aku nagkaruon ng laptop after 15 years lols~

---

### Post by wersdaluv on 2009-06-04
Ganto lang. Set mo ang partitions gamit Ubuntu live cd. Meron ka na ba? I suggest download mo Jaunty 32 bit. 

Run the live cd tapos on System->Administration->Partition Editor, set mo partitions mo. Resize mo lang kung ano ang meron ka. Sensitive ang pag-gawa nito kaya kung hindi ka familiar, sabihin mo lang dito kung may tanong ka.

Pag-set na ang partitions mo, Install mo na ang Ubuntu. Right click mo lang yung "Install" sa desktop tapos alam mo na gagawin next. Piliin mo lang ang tamang partition kung saan mo iinstall ang Ubuntu. Maging ma-ingat ka para hindi mo mapatungan ang Windows mo. 

Pag-install mo ng Ubuntu ay automatic ayos na ang boot loader. Madedetect naman ang Vista automatically.

Malapit lang naman ang tirahan natin kaya kung sobrang kailangan mo na ng hands on na tulong, sabihin mo lang sakin. _Baka_ magawan ng paraan. hehe

---

### Post by leipogs23 on 2009-06-04
> **zilu54 said:**
> ^ peru pwede naman yata hindi na kailangan i-format pa ang windows dahil gagawa aku ng bagung partition para sa ubuntu sabihin natin na tatapyasan ku ng 50GB ang HD ku for ubuntu.

Me pang partition din ba ang windows???Ahehehe. Kita mo na, sabi na bago bago pa lang ako e.ahehehe. I better shotup.hehehehe.
> **zilu54 said:**
> 
hehehe tinatamad kasi aku mag install ng ubuntu sa laptop ku kahit ginugustu ku [kasi kinakabahan akung kalikutin tung laptop] first time lang kasi aku nagkaruon ng laptop after 15 years lols~
Try mo ang wubi, madali lang xa, para ka lang nagiinstall ng regular program sa windows.hehehe. Yun una ko ginamit sa laptop ko.hehehe

---

### Post by zilu54 on 2009-06-04
> **wersdaluv said:**
> Ganto lang. Set mo ang partitions gamit Ubuntu live cd. Meron ka na ba? I suggest download mo Jaunty 32 bit. 

Run the live cd tapos on System->Administration->Partition Editor, set mo partitions mo. Resize mo lang kung ano ang meron ka. Sensitive ang pag-gawa nito kaya kung hindi ka familiar, sabihin mo lang dito kung may tanong ka.

Pag-set na ang partitions mo, Install mo na ang Ubuntu. Right click mo lang yung "Install" sa desktop tapos alam mo na gagawin next. Piliin mo lang ang tamang partition kung saan mo iinstall ang Ubuntu. Maging ma-ingat ka para hindi mo mapatungan ang Windows mo. 

Pag-install mo ng Ubuntu ay automatic ayos na ang boot loader. Madedetect naman ang Vista automatically.

Malapit lang naman ang tirahan natin kaya kung sobrang kailangan mo na ng hands on na tulong, sabihin mo lang sakin. _Baka_ magawan ng paraan. hehe
Yup, merun na pu aku live cd ng ubuntu jaunty.

hmmm ipasuk ku ang live cd then -> demo & full download -> automatic mag rereboot siya -> system -> admin -> partition editor.

*hehe nanibagu aku kasi ginawa ku ay habang nag boot ay naka sak-sak ang live cd then "delete key" then naka set una ang cd* drive.

...peru tama yan then wala nang prublema straight na yan siya?

> Me pang partition din ba ang windows???Ahehehe. Kita mo na, sabi na bago bago pa lang ako e.ahehehe. I better shotup.hehehehe.
ahaha uu merun* yata *dun sa post ni mahn yung EasyBCD yun yata ang partitioner running in windows hehehe yun ang pag kakaintindi ku. wag kang mag alala parehas lang tayu *apir apir!

> Try mo ang wubi, madali lang xa, para ka lang nagiinstall ng regular program sa windows.hehehe. Yun una ko ginamit sa laptop ko.hehehe
hetu nag inopen ku yung live cd sa wubi hindi ku muna ginalaw...tiningnan ku lang bwehehe. ginawa ku kasi sa desktop ku ay "boot setup" yung may "delete key" pa siya :P

---

### Post by leipogs23 on 2009-06-04
> **zilu54 said:**
> 
hetu nag inopen ku yung live cd sa wubi hindi ku muna ginalaw...tiningnan ku lang bwehehe. ginawa ku kasi sa desktop ku ay "boot setup" yung may "delete key" pa siya :P

Hehe. Mukang natatakot ka nga.hehehe. Ganyan lang talaga pag first time. Ganan din ako nung una. Malas pa nga first time ko sa Ubuntu. Nasira ang XP ko. Kala ko ung pagiinstall ko ng Ubuntu ang dahilan. Yun pala,gawa ng defective driver na nainstall ko. Blessing in desguize na din. Kasi nagkaron ako ng rason para ifull blown Ubuntu ang laptop ko. O diba diba!!!hehehe

Dun pala sa sabi mo na kelangan mo ng windows para sa nanay mo, problem ko din yan dati. Kasi ginagamit din to ng sis ko. Ang ginawa ko, naginstall ako ng XPGnome.wahehehehe

---

### Post by Nhatz on 2009-06-04
ok lang yan meron naman step dun sa installation ng Ubuntu na pwede mong i-resize yung windows partition mo then install nya sa free space yung Ubuntu.

sana may magbigay din sakin ng lappy... hehehehe :D

ASTIG!!! :guitar:

---

### Post by leipogs23 on 2009-06-04
> **Nhatz said:**
> ok lang yan meron naman step dun sa installation ng Ubuntu na pwede mong i-resize yung windows partition mo then install nya sa free space yung Ubuntu.

sana may magbigay din sakin ng lappy... hehehehe :D

ASTIG!!! :guitar:

hehe. Mura na lang laptop ngayon sir. Yakang yaka nyo na yan.hehe

---

### Post by pogztimz on 2009-06-05
Madali lang naman po ang mag dual boot MS Windows at Linux Ubuntu. kapag mayroon ka nang Windows Installation at gusto mong magdagdag nang OS na Ubuntu ay mas mainam at mas madali kung gagamitin mo po ang pinaka unang option sa pag install nang ubuntu 

WUBI - mula sa Live CD nang Jaunty. Sa pamamagitan po nang pag gamit nang WUBI ay pwede mo pong i-install ang ubuntu sa Loob ng WINDOWS. ang ibig ko pong sabihin ay ang paraan na ito ay para ka lang nag i-install ng Windows Applications tulad nang Photoshop, MS Office, atbp. Maari rin po na i-uninstall ang ubuntu sa loob nang windows. ito po ang recommended na solusyon kung ikaw po ay nag-nanais nag mag dual boot.:)

---

### Post by Script Warlock on 2009-06-05
ang dali na magpartition ng windows with U9.04 kc drag lang yun na! pwede ka na install ubuntu sa space na allocated. ewan ko pero wubi is parang for evaluation lang at i wont recommend too.

---

### Post by pogztimz on 2009-06-05
> **Script Warlock said:**
> ang dali na magpartition ng windows with U9.04 kc drag lang yun na! pwede ka na install ubuntu sa space na allocated. ewan ko pero wubi is parang for evaluation lang at i wont recommend too.

i agree. madali na lng po ang ubuntu installation ngayon. napaka user-friendly. on the other hand, nasubukan ko rin ang wubi installer since 8.04 hanggang ngayon. so far, wla naman pong untoward issues na na-encounter ko.

---

### Post by jepong on 2009-06-05
Wubi ka na lang dre... ala pa hassle... maaccess mo pa rin naman ntfs drive mo from ubuntu e. :popcorn:

---

### Post by leipogs23 on 2009-06-05
I am recommending wubi based on my experience. From an ordinary persons point of view din kasi, It is a lot easier installing a program than formatting a harddrive.hehehe

---

### Post by zilu54 on 2009-06-05
....I'll choose the simpliest and safe installation na lang para hindi na mag kanda buhul buhol lols.
sa pag install ng ubuntu, hindi naman mag foformat ang HD memory diba? basta it will separate into two then ok na siya?

---

### Post by Script Warlock on 2009-06-05
yup thats right make it safe since bago yan lappy mo...kung nagkasabit-sabit ka just beep us d2 lang kami sa tabitabi nagyoyosi...:p

---

### Post by wersdaluv on 2009-06-05
Basta meron kang partition na allocated for ubuntu at yon lang ang galawin mo, walang issue sa windows installation mo. Madedetect ng grub yon at maari mo nang piliin lahat ng OS na meron ka sa bootloader pagkatapos mo install ang Ubuntu.

---

