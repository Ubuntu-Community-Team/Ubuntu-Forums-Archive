---
title: "[Virtually] Complete repositories in DVD"
date: 2008-05-19
forum: Philippine Team
---

### Post by jeffimperial on 2008-05-19
Alam 'nyo, magsisimula ako at ilang mga kaibigan ko ng isang GNU/Linux enthusiasts' club dito sa Naga. Sa initial brainstorms namin, isa sa pinaka-malaking hadlang kung bakit napaka-bagal ng pick up ng appreciation sa Gnu/Linux [in general] at Ubuntu [in particular] ay ang kawalan ng Internet connection para sa mga ordinaryong Pinoy katulad ko at ng marami pang iba.


Ang mga nakikita kong viable options ay ito:
[LIST=1]
[*]ISO ng **BUONG** universe at multiverse main repos 
[*]Alamin natin kung ano 'yung mga pinaka-ginagamit na mga apps at i-collate natin ang mga 'yun sa isang ISO
[/LIST]

Syempre, kailangan nating ayusin at i-update regularly [every 3 months or so?]

Sa mga meron nang alam na links to ISOs as described above, please do post. Pero sana 'yun lang mga ISO na recently updated, confirmed working and still available. Kasi may mga nakita na akong ISOs na ganito pero either Error404 ang sagot, kaya naman ay antigo na ang lamang mga apps.

Heto, isa: [http://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/)

---

### Post by pmcastillo on 2008-05-19
WOW! Maganda eto ha! O_O

Bro, paturo naman ano ilalagay ko sa sources.list para makuha ko yung apps sa DVD? O_O

---

### Post by jeffimperial on 2008-05-19
Two ways, PM

**THIS:**

Terminal:
Open a Terminal (Applications &#8594; Accessories &#8594; Terminal) and enter the following command:

```
sudo apt-cdrom add
```

Insert the first disc and follow the instructions (it will ask you to name each disc). When apt-cdrom is finished with the disc, eject it with

```
eject
```

(yeah, just type it in and hit Enter) and insert the next and use the same command. Repeat the process per disc.

Once the last disc is done do this:

```
sudo apt-get update
```

followed by

```
sudo apt-get upgrade
```


**OR THIS:**

Basically the same steps as above, but instead of having to burn the ISOs into DVDs, you point synaptic to the mounpoint.
```
sudo synaptic --add-cdrom /media/iso/
```
You will have to comment (disable) the repos that the CD/DVD contain in sources.lst by adding a hash mark (#) before the deb line.


Excellent howto here -->[http://ubuntuforums.org/showthread.php?t=352460&highlight=synaptic+ISO](http://ubuntuforums.org/showthread.php?t=352460&highlight=synaptic+ISO)
-->[http://openjeff.wordpress.com/2008/05/20/making-your-own-ubuntu-repository/](http://openjeff.wordpress.com/2008/05/20/making-your-own-ubuntu-repository/)

---

### Post by glenn45 on 2008-05-23
kumpleto ako ng ubuntu 7.04 at 7.10, kaso for amd64 lang. di ko pa tapos yung pang 32 bit. :popcorn:

---

### Post by jeffimperial on 2008-05-24
> **glenn45 said:**
> kumpleto ako ng ubuntu 7.04 at 7.10, kaso for amd64 lang. di ko pa tapos yung pang 32 bit. 

Beautiful news, man! Sige, try ko ring gumawa ng sarili kong version, tapos compare tayo ng work natin; merge then deploy. tapos pwede rin natin 'to i-announce as a project maintained by us and the Pinoy community. Hehe

What'cha think?

---

### Post by glenn45 on 2008-05-24
eh Jeff,
ano ibig mo sabihin ng deploy? anyway, yung buong repository for gutsy at feisty 64 bit ang na download ko na. gamit ko rin yung tutorial ni bobsongs.

:guitar:

---

### Post by jeffimperial on 2008-05-24
> **glenn45 said:**
> eh Jeff,
ano ibig mo sabihin ng deploy? ...
Baka mali ang gamit kong word. Hehe

I just meant na 'yung mga finished product na ISO i-upload natin sa ilang mga local server (para mas mabilis ang download speeds). Purpose: kung sinong may gusto ng repos, DL lang sila. Every six months or so siguro, update tayo ng ISOs. Kapag may bagong ISOs "deploy" :lolflag: natin sa mga servers na 'yun. Ibig sabihin, may bago tayong release evey update.

---

### Post by pmcastillo on 2008-05-24
> **jeffimperial said:**
> Beautiful news, man! Sige, try ko ring gumawa ng sarili kong version, tapos compare tayo ng work natin; merge then deploy. tapos pwede rin natin 'to i-announce as a project maintained by us and the Pinoy community. Hehe

What'cha think?



Announce din natin kahit sa mga banyaga... Spread the spirit of Ubuntu ^_^

Tapos kunwari... Every 3 months tayo magre-release... Tapos release natin under both downloads at torrents...

---

### Post by glenn45 on 2008-05-24
Yung size ng isang dvd ng repository para gutsy 4.1 GB x 6 . Yung sa feisty 4.1 x5 . Hehe. Meron kang ganong kalaking space sa server mo at enough bandwitdth? :popcorn:

---

### Post by jeffimperial on 2008-05-25
> **glenn45 said:**
> Yung size ng isang dvd ng repository para gutsy 4.1 GB x 6 . Yung sa feisty 4.1 x5 . Hehe. Meron kang ganong kalaking space sa server mo at enough bandwitdth? 
Kaya nga sa tingin ko kelangan lang nating piliin kung alin ang isasama sa repo.  We'll have to handpick the most commonly used and the best loved apps from all the different repos. Syempre pa, dagdag na trabaho. Pero estimate ko that would cut the size by more than half.

---

### Post by bme on 2008-05-26
mga tol,

meron dito-"ftp://tuma.ui.edu/pub/ubuntu-repository/8.04"-download na lang tayo

---

### Post by dodimar on 2008-05-26
Siguro mas mainam ito sa mga walang sariling internet connection or mabagal ang internet (kagaya ko)... maganda siguro kung pwede sira request tapos send via mail, tapos shipping cost na lang ang babayaran.

---

### Post by bme on 2008-05-26
Kung titignan mo yong site na sinabi ko([ftp://tuma.ui.edu/pub/ubuntu-repository/8.04](ftp://tuma.ui.edu/pub/ubuntu-repository/8.04)) iba-ibang ISO ang ginawa nila. Iisa isahin mo pa kung alin ang kailangan mo.Kung bibili ka,I think you will be better off to purchase yong LinuxMint o kaya yong Ultimate Edition kesa gumamit ka ng repo DVD.(Huwag na yong Ubuntu DVD di rin kumpleto yon)

---

### Post by jeffimperial on 2008-05-26
Kaya nga siguro pag-isipan na lang muna natin kung anu-anong mga apps ang usually ginagamit ng community, at kung alin 'yung mga pinakasikat. Pwede rin natin gamitin 'yung popularity category ng mga apps sa Add/Remove. Sabihin na natin lahat lang ng 3 stars pataas ang isasama sa ISO. Pwede din tayong magtanong-tanong dito UF-Ph kung alin ang trip na apps ng mga tao. Dun pa lang bawas na ang bigat nya. Tapos deployment na lang ang prob, kung papano natin ikakalat. One-time download ba o free-cds gaya ng ginagawa ng Proj. Gutenberg ?

---

### Post by Nhatz on 2008-05-27
Magandang Idea yan mga ubuntureros... kasi hindi lahat ng gumagamit ng ubuntu ay merong internet connection sa bahay at tulad ng pinapatupad ng gov (at DOST ata) sa mga public schools na edubuntu ang gamit, hindi lahat ng public schools ay may internet connection. kaya mas maganda kung updated din sila kahit wlang internet connection. magana kung magsagawa tayo ng survey kung ano ang mga apps na kalimitang ginagamit.

ASTIG! :guitar:

---

### Post by gothdaddee on 2008-06-25
ay... medyo late na ang post ko siguro. pero game. hehe!

sabi sa ubuntu ultimate edition "lahat" daw ng apps na kailangan nandun na daw. pero i doubt it. maganda pa din ung idea ng complete repos in dvd.  may dvd ako nung ultimate ed pero hindi ko pa nasubukan.

sa tingin ko isa sa mga mahalagang ilagay sa repos in dvd ay ang kumpletong codecs ng video and audio (at least siguro para sa akin kasi mahilig ako sa entertainment and video editing. hehehe!). anyway, sana buhay pa din ang project na ito.

---

### Post by pmcastillo on 2008-06-25
I'll make an experiment on my own:

Well maga-allot talaga ako ng space ko sa PC ko para ma-download lahat sila. Then ibu-burn ko sila lahat sa DVD, bibili ng magandang CD cases, then lagyan ng magandang packaging.

Then siguro, maghahanap ako ng buyer (kahit isa lang muna), then ang payment sa akin its either (load ng cellphone or "Pera Padala"), then ima-mail ko sa kanila, (hindi ko pa alam yung mga ibang types ng mails, kaya normal mail nalang muna gagawin ko).

Then pagna-recieve na nila, ia-assess ko lahat kung feasible nga eto. Pag naging successful ako itutuloy ko pa eto...

---

### Post by king leoric on 2008-06-25
Gaganda ng mga ideas ninyo. Sana mailagay to sa sticky thread para hindi matabunan balang araw:)

---

### Post by jeffimperial on 2008-06-25
May ginagawa rin nga ako ngayong version ko naman. But from where I'm sitting, two challenges presented themselves:
[LIST=1]
[*]**Size of the final disc**. It would round up to ~40-45GB. I imagine this as obtrusively large for common use. So, I'm trying up to come up with a list of which apps to include. I think I'm going with the 5 top choices for every kinda task. This will include both multiverse and universe repos, so it still might be a little large. As to how large, I still can't say.
[*]**Distribution**. Since it's going to be darn large, and considering that the primary beneficiaries of this little venture are those with limited or no bandwidth, I think it's safe to assume that uploading it to my server won't be that much of a hit. Maybe start a little something like [Project Guttenberg]("http://www.gutenberg.org") where volunteers send discs to people who want it?
[*]**Which apps to include** (as a direct result of the first challenge) I know that we Pinoys have our own ways of doing things. And needless to say, we also have individual needs and preferences. That's why I think pleasing everyone with this would be a real source of grief.
[/LIST]

If anyone has **suggestions** to the above, please [COLOR="Red"]**please do tell**[/COLOR]. I'd like to get this up and running :)

---

### Post by pmcastillo on 2008-06-25
@jeffimperial

Bakit 40-45GB sya? Kase nung tinignan ko sa:

[http://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/)

About 5 DVDs lang yung kailangan:

> 
[ ]	unofficial-ubuntu-DVD-gutsy-i386-main-restricted-universe-multiverse-18-10-2007-1.iso	18-Oct-2007 09:24 	4.1G
[ ]	unofficial-ubuntu-DVD-gutsy-i386-main-restricted-universe-multiverse-18-10-2007-2.iso	18-Oct-2007 09:46 	4.1G
[ ]	unofficial-ubuntu-DVD-gutsy-i386-main-restricted-universe-multiverse-18-10-2007-3.iso	18-Oct-2007 10:07 	4.1G
[ ]	unofficial-ubuntu-DVD-gutsy-i386-main-restricted-universe-multiverse-18-10-2007-4.iso	18-Oct-2007 10:30 	4.1G
[ ]	unofficial-ubuntu-DVD-gutsy-i386-main-restricted-universe-multiverse-18-10-2007-5.iso	18-Oct-2007 10:44 	2.5G


---

### Post by jeffimperial on 2008-06-25
> **pmcastillo said:**
> @jeffimperial

Bakit 40-45GB sya? Kase nung tinignan ko sa:

[http://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/](http://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/)

About 5 DVDs lang yung kailangan:
Tama, 5 DVDs at ~8.5-9GB each

---

### Post by pmcastillo on 2008-06-25
The capacity of a DVD is about 4GB... (pwera nalang kung DVD-DL sya, which means dual-layer). Plus naka indicate sa website na iyan ay:

> 
[ ] unofficial-ubuntu-DVD-gutsy-i386-main-restricted-universe-multiverse-18-10-2007-1.iso 18-Oct-2007 09:24 **4.1G**
[ ] unofficial-ubuntu-DVD-gutsy-i386-main-restricted-universe-multiverse-18-10-2007-2.iso 18-Oct-2007 09:46 **4.1G**
[ ] unofficial-ubuntu-DVD-gutsy-i386-main-restricted-universe-multiverse-18-10-2007-3.iso 18-Oct-2007 10:07 **4.1G**
[ ] unofficial-ubuntu-DVD-gutsy-i386-main-restricted-universe-multiverse-18-10-2007-4.iso 18-Oct-2007 10:30 **4.1G**
[ ] unofficial-ubuntu-DVD-gutsy-i386-main-restricted-universe-multiverse-18-10-2007-5.iso 18-Oct-2007 10:44 **2.5G**


So...

4.1 + 4.1 + 4.1 + 4.1 + 2.5 = 18.9GB lang yung kailangang i-download...

Right?

---

### Post by bme on 2008-06-25
the idea of a pinoy repo dvd is good but then.....who will maintain the contents of the repo? as we all know there are updates to almost all linux packages almost everyday....so by the time one finishes the dvd a new version is already available.....
Sad to say,and I've learned this the hard way-one of the very basic things REQUIRED for one to use ubuntu is a FAST INTERNET CONNECTION. this was emphasized to me when I complained about it in the forum.
So if you have a fast connection then there is no need for a dvd repo as updating will ony take a few minutes(if not seconds)....
besides, napakamura na ngayon ng high speed internet sa atin...whether smartbro or globe...

---

### Post by jeffimperial on 2008-06-26
> **bme said:**
> the idea of a pinoy repo dvd is good but then.....who will maintain the contents of the repo? as we all know there are updates to almost all linux packages almost everyday....so by the time one finishes the dvd a new version is already available.....
Sad to say,and I've learned this the hard way-one of the very basic things REQUIRED for one to use ubuntu is a FAST INTERNET CONNECTION. this was emphasized to me when I complained about it in the forum.
So if you have a fast connection then there is no need for a dvd repo as updating will ony take a few minutes(if not seconds)....
besides, napakamura na ngayon ng high speed internet sa atin...whether smartbro or globe...

Iyan nga mismo ang tinitingnan ng thread posters dito, kung papaano magagawang feasible ang ganitong venture.

Maybe I could set up a local repo server dun sa office, tapos dun kukuha ng debs para sa DVD Repo para updated ang makukuha. Then every 6-month release ng Ubuntu, sasabayan ng bagong release naman ng DVD Repo. Of course, pwede din tayo magsimula ng bagong project para may official group maintaining such, o kaya ampunin na lang ng LoCo team as pet project.

I'm so into this because we've all been talking about how to better market Linux (in general), Ubuntu (in particular), to the Philippine computing scene. Or how we could help out educational institutions who are using / who wish to use Ubuntu. This might be it.

---

### Post by jeffimperial on 2008-06-26
Uhmm.. Ang alam ko po kasi Double-layer disks ang intended medium nung mga ISOs na 'yun.. Kaya each ISO would ultimately measure up to ~8.5 ~9 GB

---

### Post by bme on 2008-06-26
why not focus instead efforts to a localized version of ubuntu-perhaps "pinoybuntu" or the like?
Patay na yong bayanihan linux wala na ring lorma linux-kaya pagkakataun na para sa pinoybuntu...
hindi ako programmer pero kung makaktulong tutulong ako.......

---

### Post by daxumaming on 2008-06-26
I'm all for this initiative, however, I'd go against DVD and use plain old CD-Rs or CD-RWs for the following reasons:

1) most of the school's and companies I've been with order workstations with CD-ROM drives, not DVD
2) it'll take days to download, even with a fast internet connection
3) you'll dispose of it after 6mos.

So I'd rather go for CD-RWs and use AptOnCD to create ISOs from cached downloads. Here's the catch though, I need to know exactly what applications one need. I won't, obviously, download all the apps on the repo - that's just crazy.

I actually have a set of ISOs in my possession that contains LAMP/Server, Development, Graphics, Animation, Office, and Multimedia apps. Each set is placed on one CD, this way, I know exactly what CD to apt-cdrom instead of listing them all on sources.list when I only need to install one app.

Also, I don't bother downloading apps I've never heard of, it's a waste of bandwidth and space.

[http://cdimage.ubuntu.com](http://cdimage.ubuntu.com) <-- nandito mga DVD isos

---

### Post by Nhatz on 2008-06-26
Yeah... may point si dax. bakit hindi nalang parang hatiin...ex. para sa mga common users, then meron din para sa mga programmers or para sa mga graphic artist... yun nga lang ang problema hindi rin natin alam kung anong mga apps ang ginagamit ng ibang users... wag rin katimutan yung mga 3rd party apps diba? para rin nagpagod ka lang i-download lahat then after 6 months wala na rin. hehehe :)
ASTIG! :guitar:

---

### Post by pmcastillo on 2008-06-26
@jeffimperial

Try mong i-download kahit isa doon 4.1 GB lang ^_^ (kasya sa DVD)

One thing I've noticed sa difference namin ni jeffimperial ay: Siya, he intended to include the mostly used programs by Pinoy. Ako naman, I intended to download the whole repo ^_^ But we both have the same common goal "Repository in DVD" ^_^

Am I crazy? No I'm not. Think about the possibility pag na-download ko sila lahat ng nasa repo. This about it, you could install almost anything the open-source world could offer. Kahit hindi pinoy matutulongan ko sa gagawin ko.

Can I do it? As I said, "18-20GB lang sya"... Mas malaki pa yung torrent na: Naruto Anime Series, Heroes Series, The Simpsons TV Series, McGayver TV Series, at ku ano ano pa... (Usually mga 50GB eto... eh paano pa kaya etong 20GB na eto?)


@About sa CD or DVD

Hindi pa kaya ng powers ko i-download yung buong repo at hatiin sila into CD sizes eh... kaya ang gagawin ko maghahanap ako ng mga ibang FTP sites na hinati according to CD sizes... Kung wala, balik ulet ako sa DVD versions



Rather than speculating stuffs... I'd rather **DO** stuffs...

---

### Post by pmcastillo on 2008-06-26
I've inserted a screenshot to prove that it is 4.1GB per ISO only...

[img]http://img120.imageshack.us/img120/5562/screenshotkget1lr3.png[/img]

---

### Post by daxumaming on 2008-06-26
hmm, afaik, the main, universe, multiverse, restricted, and backports' around 80-90GB. i tried downloading those (Feisty) repos using apt-mirror to my Maxtor 250GB External HDD so I have a portable repo with me during my stint at camarines norte.

---

### Post by pmcastillo on 2008-06-26
Hmmmmmmmm... So ano kaya yung dinadownload ko....

Anyway, I'll know it when I get there...

---

### Post by jeffimperial on 2008-06-26
> **daxumaming said:**
> I'm all for this initiative, however, I'd go against DVD and use plain old CD-Rs or CD-RWs for the following reasons:

1) most of the school's and companies I've been with order workstations with CD-ROM drives, not DVD
2) it'll take days to download, even with a fast internet connection
3) you'll dispose of it after 6mos.

So I'd rather go for CD-RWs and use AptOnCD to create ISOs from cached downloads. Here's the catch though, I need to know exactly what applications one need. I won't, obviously, download all the apps on the repo - that's just crazy.

I actually have a set of ISOs in my possession that contains LAMP/Server, Development, Graphics, Animation, Office, and Multimedia apps. Each set is placed on one CD, this way, I know exactly what CD to apt-cdrom instead of listing them all on sources.list when I only need to install one app.

Also, I don't bother downloading apps I've never heard of, it's a waste of bandwidth and space.

[http://cdimage.ubuntu.com](http://cdimage.ubuntu.com) <-- nandito mga DVD isos

**RE DVD vs CD**
I originally started this thread with schools and other organizations in mind as priority. So, perhaps Dax there is right. Again, I imagine Ubuntu is top choice for many because it's ideal for older units/systems (and perhaps it's safe to assume that those have CD-Roms instead of DVD right?)

**RE Apps to include**
I think a different thread needs to be started, or a totally separate poll page. I'll try to come up with a voting system kung saan makaka-pamili na lang ang boboto sa top three choices nya per category. Let's say we assign a category for each sort of task, then the applications as sub-items for those categories. I have a general concept here, but I still have to work out the details.

**RE Disk repos' lifespan (short..real short)**
It's just going to be the price for something like this I guess. Well, at least schools, other institutions and everyone else gets the repos without having to cough up the cash for bandwidth right? Plus, CDs have become cheap since some time ago. So as far as the 6-month limitation of these disks is concerned, I think the hurdle would be initial in nature. Once we have the disk packages set-up, all we need to do is update them. And if we do release in tandem with Ubuntu major releases, we get some working time to work out a system of some sort.

---

### Post by gothdaddee on 2008-06-26
maganda nga din yung mga sinasabi ni dax and nhatz. yung specialized compilation ng repos. may para sa education, may para sa video/audio enthusiasts, may para sa graphics. siguro mas madali nga yung ganito kasi naka sort na din by category yung mga apps.  kung hindi naman pala kakayanin sa iisang dvd ang buong repo e di hatiin na nga lang pero naka categorize according to a specific interest. mas madali din mamili ng apps para saming common users na hindi masyadong techie.

---

### Post by pmcastillo on 2008-06-26
@daxumaming

Kasama ba yung source codes nung nagdowload ka noon?

Kase yung iniisip ko kaya naging ganoon kala sya kase, kasama yung source codes...

Then kaya ganito kaliit yung mga ida-download ko, kase wala etong source codes...

---

### Post by daxumaming on 2008-06-26
oh yeah, kasama pati source, pero i still don't think a repo would fit on one dvd though. that's around 65K+ apps

---

