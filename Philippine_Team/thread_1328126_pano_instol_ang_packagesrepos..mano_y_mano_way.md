---
title: "pano instol ang packages/repos..mano y mano way?"
date: 2009-11-16
forum: Philippine Team
---

### Post by eeeris on 2009-11-16
kamusta mga ubunturero, ako po ay isang hamak na baguhan sa ubuntu..sinubukan ko install ubuntu sa netbook ko (Eee pc 1000HA) gamit ang Ubuntu 9.04 (dual boot,side by side with WinXp) Ang tanong:

* Bkit po ayaw gumana ng webcam ko?

* Di ko maiplay mp3s ko, kelangan pala install pa ung ubuntu-restricted-extras..problema, wala internet ung netbook ko. Posible ba istall ung packages/repos offline or mano-mano? pano po?

maraming salamat sa mga tutugon sa aking mga katanungan ;)

---

### Post by loell on 2009-11-16
magandang gabi,

* ang webcam, natry mo na ba? paano mo sinubukan?

* gamit ka ng [keryx]("http://keryxproject.org/")

---

### Post by eeeris on 2009-11-17
Magandang gabi,
 
* Sa ngayon, di ko pa nasusubukan gamitin ang built-in web cam..wala kse akong makitang application na maaring gamitin upang masubukan ito. Pasenxa na po, sobrang baguhan talaga.
 
* susubukan ko po idownload ung keryx
 
Maraming salamat sir loell, Mabuhay ka!
 
Nga pala:
 
ako ung nag buzz sa'yo kagabi..sa tingin ko kse ikaw ang higit na makakatulong sa akin ayon sa pagbabasa ko ng ph forum dito. SAlamat.

---

### Post by loell on 2009-11-17
ah kaw pala yun, post ka lang dito, marami namang makakatulong sayo dito.

sa pamamagitan ng keryx, pwede kang mag-download ng "cheese" package, ito ay isang webcam booth application, malalaman mo doon kung may output ang webcam mo.

---

### Post by jaceleon on 2009-11-17
pwede ka rin na humanap ng iyo or iyong friend na merong parehong version ng ubuntu na gamit mo, then ask him to install aptoncd, then ask mo xa na create ng backup ng buong installed packages niya, though I don't recommend it, since kadalasan, hindi pareho PC ng 2 tao.

---

### Post by eeeris on 2009-11-18
Magandang gabi,
 
 Salamat sa inyong tugon. Nag-saliksik din ako sa ubuntu.com, ayon  sa nabasa ko maari din pala i-download ([www.archive.ubuntu.com](www.archive.ubuntu.com)) ung mga files na kelangan ko tapos i-save sa usb flash drive tapos i-instol ko. Hmmmm, ***[COLOR=Blue]jaceleon[/COLOR]*** mukhang mahihirapan talaga maghanap ng pc na may ubuntu dito sa lugar namin, ako p lang naglakas loob na sumubok eh. Hinihikayat ko nga ung mga katrabaho ko pero sabi nila ako muna daw, mga loko gusto pang gawing LAB-rat ung netbook ko.:D

---

### Post by loell on 2009-11-18
may problema lang kung doon ka archive mismo kukuha, kasi dapat alam mo ang lahat ng dependency na dapat mong kunin, mahirap kasi yun tantyahin.

---

### Post by eeeris on 2009-11-19
mukhang mahirap nga at komplikado. Salamat kaibigan, sa ngayon ginagawa ko muna ung unang payo mo. balitaan kita kung ano mangyayari. Mabuhay ka!

---

### Post by jaceleon on 2009-11-19
tga san po ba kau, kuya? pwede ko kc kaung bigyan ng iso na repository, since ako me aptoncd.

wag mo subukan basta basta ang mag install ng manually downloaded repo kasi hindi mo alam ang mga dependencies niyan. for example, kahit madownload mo ang adobe-flashplugin.deb (adobe flash player 10 for debian) e nid mo pa ng libtk-dev.deb at 2 pa (tma kaya ako sa name nito?)

see? hindi mo malalaman unless gugulin mo buong time mo sa pag-aaral ng linux dependencies kung ano ang mga manually na idownload mo.

---

### Post by eeeris on 2009-11-20
Salamat Jaceleon, taga san pedro laguna ako eh. san ka ba? napakabuti ng iyong alok na bigyan ako ng copy ng repos. Sa mga nabasa ko nga ay maraming dependencies ang isang program bago mo ito mapatakbo, hindi advisable sa isang katulad kong baguhan.


Mabuhay ka kaibigan!

---

### Post by _duncan_ on 2009-11-20
Another alternative is to use the "Generate package download script" option of the Synaptic Package Manager.

In theory, this will create a script to download all the necessary packages, including dependencies. Save the script to a portable medium (e.g. flash drive), Take the flash drive to an on-line computer running linux, run the script to save the downloaded packages to the portable drive.

Go back to the offline computer, then use the "Add downloaded packages" feature of synaptic to access the flash drive.

The caveat of this method is if you have access to another on-line computer running some form of linux. If not, then this method is not feasible for you.

---

### Post by jaceleon on 2009-11-20
>   	 		**Re: pano instol ang packages/repos..mano y mano way?**
 Salamat Jaceleon, taga san pedro laguna ako eh. san ka ba? napakabuti ng iyong alok na bigyan ako ng copy ng repos. Sa mga nabasa ko nga ay maraming dependencies ang isang program bago mo ito mapatakbo, hindi advisable sa isang katulad kong baguhan.


Mabuhay ka kaibigan! 	

Taga San Andres Bukid Manila ako. At isa akong **Ubuntu Karmic Koala** user. If you wish, I could provide you po some help regarding your option to upgrade your installation here or a fresh installation ng 9.10, which is a much-advised method compared to the first mentioned.

If you can somehow make a way to get here, I will assist you po. After all, you're an Ubuntu user, and I help our fellow users to whatever extent I can manage.

If you cannot do so, I would ask you to do _duncan_'s method of downloading repositories.

---

### Post by eeeris on 2009-11-23
Magandang gabi, 

Salamat sa inyo..as of now, try ko muna ung 1st option na binigay ni G. Loell..sa tingin ko mas madali. Medyo may problema ako sa pghananap ng oras para mapunthan ka jaceleon, pero by this december ay lumuwas ako ng manila..maari cguro kita punthan jace. Gusto ko rin kse makameet ng isang experienced ubuntu user..para na rin makita mo ung setup ko.

* Samantala, may isa akong katanungan regarding sa mirror site, ano ba pinaka advisable na regional site na mas mabilis? ang default kse na site sa keryx ay ph.archive.ubuntu.com, may alam ba kayong alternative dito. Sobrang bagal kse.

Salamat

---

### Post by Script Warlock on 2009-11-23
hehe nice signature......:P

---

### Post by jaceleon on 2009-11-25
Anyway, excited din ako to meet you up. kelan ka visit nang mapaghandaan? after all, I will (actually I hope to) make your visit here worthwhile.

Keryx seems like a good tool, kaso medyo mabagal ang downloading speed nun sa regional. I advice na baguhin mo ang settings ng repositories nun sa option at ituro mo sa main server. mas mabilis ang downloading there. took me 2 hrs to download all updates at lahat ng iiinstall ko (vlc, ubuntu restricted, java, adobe flash, kde, xfce, lxde) on a pc with 2mbps from the main server, compared ko sa 5 hrs + na downloading mula sa PH regional server.

---

### Post by eeeris on 2009-11-25
@script warlock hehehehe borrowed ko lang yang nasa signature ko...from John Lennon

---

### Post by eeeris on 2009-11-25
Magandang gabi,


Ok jace..sabihin ko na lang kung kelan pwede. 

Sige try ko ung binigay mong advice..super kupad kse ung sa regional site. almost 2 hrs na inabot ko..

Salamat;)

---

### Post by eeeris on 2009-11-25
nga pala jace, ato ba address ng main server,  [http://www.archive.ubuntu.com](http://www.archive.ubuntu.com)

salamat

---

### Post by confulity on 2010-05-01
Kuya,

Dagdag ko lang kahit alam kong pwedeng na solve mo na tong issue na to kasi last year pa sya, pwede mo pong magamit yung script na na produce sa synaptics.. just open the script in notepad then gamitin mo yung links na nasa script tapos ayun ma ddownload mo na yung mga dependencies, ganyan kasi ginawa ko nung nawala yung gnome netmanager ko after kong installan ng Wicd.

---

### Post by aljoriz on 2010-05-01
kung wala kang internet wag mo sanang ikakagalit yung pag payuhan kitang ipunan mong bumili ng smartbro / sun o kaya globe tattoo, makakatulong sa iyo yan sa pag aarala at iba tulang ng pag video chat gamit ang skype

---

