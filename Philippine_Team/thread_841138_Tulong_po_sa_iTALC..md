---
title: "Tulong po sa iTALC."
date: 2008-06-26
forum: Philippine Team
---

### Post by pogztimz on 2008-06-26
pwede po natin ma install ang iTALC sa Dapper drake? kac Dapper drake yung gami namin dito sa computer laboratory namin.. need po talaga namin ang iTalC.. sana po matulungun nyo ako sa problema anmin...

---

### Post by daxumaming on 2008-06-26
of course you can, you can download it from the Hardy repo. Pero mas maganda kung i-upgrade na ninyo sa Hardy ung computer nyo sa Laboratory for security as well as stability.

Besides, using an outdated version might give your users a bad impression of Ubuntu and ask for Vista instead.

---

### Post by pogztimz on 2008-06-26
> **daxumaming said:**
> of course you can, you can download it from the Hardy repo. Pero mas maganda kung i-upgrade na ninyo sa Hardy ung computer nyo sa Laboratory for security as well as stability.

Besides, using an outdated version might give your users a bad impression of Ubuntu and ask for Vista instead.

hello. ok naman po ang Dapper dito sa amin kasi LTS naman po d bah, atsaka nasasayangan kami sa installation namin. almost 2 years na kac ang Dapper Drake sa system namin kaya parang hindi pa feasible ung upgrade sa setup anmin dito sa comp lab. meron din po isang problema namin, mababagal ang mga machines namin dito kay na stuck kami sa Dapper Drake. anyway wala po kaming problema sa Dapper Drake, up-to-date po ang mga patch.

with regard naman po sa problema ko, pwede po ba ninyo ako matulungan kung papaano ko ma papatakbo ang iTALC sa Dapper? ano po ang advice or procedure ninyo?

sana po matulungan ninyo kami kac excited na talaga ung mga kasamahan kong faculty sa implementation nang iTALC dito sa amin. Malaki po ang maitutulong ng iTALC sa amin pagdating sa instruction dito sa laboratory..

edit: by the way u said earlier na pwede ko i download from the hardy repo? pwede mo ba akong matulungan kung papaano? salamat.. :)

---

### Post by loell on 2008-06-26
[https://launchpad.net/ubuntu/dapper/+source/italc]("https://launchpad.net/ubuntu/dapper/+source/italc")

so may italc sa dapper, have you already tried installing it?

---

### Post by loell on 2008-06-26
[https://launchpad.net/ubuntu/dapper/+source/italc]("https://launchpad.net/ubuntu/dapper/+source/italc")

so may italc sa dapper repo, have you already tried installing it from dapper's repo?

---

### Post by pogztimz on 2008-06-26
> **loell said:**
> [https://launchpad.net/ubuntu/dapper/+source/italc]("https://launchpad.net/ubuntu/dapper/+source/italc")

so may italc sa dapper repo, have you already tried installing it from dapper's repo?

sinusubukan ko na po. salamat. reply lang agad ako pag natapos na ang download sa depency files...

brb..


tol... ang hirap naman nito. hindi ko masyadon maintindihan... =)).. pwede na ma install to gamit sudo apt-get install? noob pa kac ako tol.. paki assist naman.. ty in advance?

---

### Post by jeffimperial on 2008-06-26
> **pogztimz said:**
> ...tol... ang hirap naman nito. hindi ko masyadon maintindihan... =)).. pwede na ma install to gamit sudo apt-get install? noob pa kac ako tol.. paki assist naman.. ty in advance?
I think the packages
[LIST]
[*]italc-client
[*]italc-master
[*]libitalc
[/LIST]
are available in Dapper's Universe Repos. Try using Add/Remove Programs or Synaptic Package Manager. Maybe you could try from there.

Additionally, below is italc's gutsy details. It should be in the same place within other releases.
> italc-client (source: italc): Intelligent Teaching and Learning with Computers. In component universe, is optional. Version 0.9.6.2-3 (gutsy), package size 151 kB, installed size 388 kB

---

### Post by loell on 2008-06-26
> **pogztimz said:**
> 
tol... ang hirap naman nito. hindi ko masyadon maintindihan... =)).. pwede na ma install to gamit sudo apt-get install? noob pa kac ako tol.. paki assist naman.. ty in advance?

dagdag lang sa sinabi ni jeff, anong output ang lumalabas pag 

```
apt-cache search italc
```

malamang ang lalabas ay yung nabanggit ni jeff na mga packages.

install mo lang yung **italc-master** package sa server at **italc-client** package sa mga client stations.

---

### Post by pogztimz on 2008-06-27
> **loell said:**
> dagdag lang sa sinabi ni jeff, anong output ang lumalabas pag 

```
apt-cache search italc
```

malamang ang lalabas ay yung nabanggit ni jeff na mga packages.

install mo lang yung **italc-master** package sa server at **italc-client** package sa mga client stations.

eto po ung output..
[http://www.pastebin.ca/1056987]("http://www.pastebin.ca/1056987")

sorry for the delay...

walang packages na italc-client at italc-master.. i think i will have to install this in the old fashion way.. download ko muna ung manga dependency files...


ang bagal nang internet connection dito.. huhuhuhuhu..
post lang po ako agad sa resulta.. brb

---

### Post by pogztimz on 2008-06-27
> **jeffimperial said:**
> I think the packages
[LIST]
[*]italc-client
[*]italc-master
[*]libitalc
[/LIST]
are available in Dapper's Universe Repos. Try using Add/Remove Programs or Synaptic Package Manager. Maybe you could try from there.

Additionally, below is italc's gutsy details. It should be in the same place within other releases.

wala po eh.. hindi talaga xa available sa dapper repo.. Pero i will try to install it manually na lang i think.. i still need ur help guys.. please be there when the time comes.. for now i will download all the necessary packages for iTALC.

---

### Post by jeffimperial on 2008-06-27
> **pogztimz said:**
> wala po eh.. hindi talaga xa available sa dapper repo.. Pero i will try to install it manually na lang i think.. i still need ur help guys.. please be there when the time comes.. for now i will download all the necessary packages for iTALC.
Hmmm... Posible kayang hindi naka-enable ang universe repos mo? Sa Add/Remove programs, naka-select naman ang "All available programs"?

---

### Post by pogztimz on 2008-06-27
> **jeffimperial said:**
> Hmmm... Posible kayang hindi naka-enable ang universe repos mo? Sa Add/Remove programs, naka-select naman ang "All available programs"?

Enabled napo lahat ang repo... download pa rin ako nang mga depency packages hanngang ngayon.. :( ang bagal talaga nang net namin.. 

post lang po ako pag natapos na ang downloads..

---

### Post by daxumaming on 2008-06-28
@loell: is it possible to apt-pin the hardy repo in dapper?

if so, @pogztimz maybe you can add the hardy repo, update it, and download italc.
however, _**do not under any circumstances**_, download and install other apps besides italc and its dependencies to prevent *b0rkage*.

---

### Post by loell on 2008-06-29
> @loell: is it possible to apt-pin the hardy repo in dapper?

di ko pa na-try mag pin nang package :) , pero diba mukhang malayo na yata ang agwat ni dapper at ni hardy? baka yung libc6 version nila magkaiba na.

---

### Post by jeffimperial on 2008-06-29
> **loell said:**
> di ko pa na-try mag pin nang package :) , pero diba mukhang malayo na yata ang agwat ni dapper at ni hardy? baka yung libc6 version nila magkaiba na.
Mukha nga na mas magandang from source na si pogztimz mag-install.. Darn this project needs to release .debs

[http://indianalinux.blogspot.com/2007/02/howto-install-italc-from-source-on.html](http://indianalinux.blogspot.com/2007/02/howto-install-italc-from-source-on.html)

---

### Post by daxumaming on 2008-06-29
@pogztimz
go to 
[https://edge.launchpad.net/ubuntu/hardy/+source/italc](https://edge.launchpad.net/ubuntu/hardy/+source/italc) 
or 
[http://packages.ubuntu.com/hardy/italc-client](http://packages.ubuntu.com/hardy/italc-client)

then download the 3 files and save it to a folder
* italc_1.0.7-0ubuntu2.dsc
* italc_1.0.7.orig.tar.gz
* italc_1.0.7-0ubuntu2.diff.gz

Then download the ubuntu-dev-tools
```
sudo aptitude install ubuntu-dev-tools
```

cd to the directory and run this command:
```
sudo pbuilder build *.dsc
```

and there you go... you just built italc_1.0.7-0ubuntu2.deb. so all you have to do now is double-click on that file to install it.

if it didn't build, consult the Ubuntu Packaging Guide at
[https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html)
or more specifically 
[https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-scratch.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-scratch.html)
or
[https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-debhelper.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-debhelper.html)

NOTE: I've tried this before using another package (Mozilla Firefox and Thunderbird) , but using dsc files from the Feisty era. I haven't tried building debs from dsc for a couple of months now so I may be wrong.

---

### Post by daxumaming on 2008-06-29
arrgghh, uf.o hiccup.. double-post. please ignore this.

---

### Post by pogztimz on 2008-07-02
> **daxumaming said:**
> arrgghh, uf.o hiccup.. double-post. please ignore this.


wow. i am really impressed by ur attitude guys. i'm new here pa lang and then grabe na ang support na narecieve ko.. i am not currently on school atm.. nasira ang connection namin sa internet due to bagyong Frank, but rest assured na i will do it first thing pag ma normalize na yung connection namin. Maraming Salamat at Mabuhay kayong lahat. 

p.s. Psot lang ako ulit sa results.. :)

---

### Post by pogztimz on 2008-07-03
> **daxumaming said:**
> @pogztimz
go to 
[https://edge.launchpad.net/ubuntu/hardy/+source/italc](https://edge.launchpad.net/ubuntu/hardy/+source/italc) 
or 
[http://packages.ubuntu.com/hardy/italc-client](http://packages.ubuntu.com/hardy/italc-client)

then download the 3 files and save it to a folder
* italc_1.0.7-0ubuntu2.dsc
* italc_1.0.7.orig.tar.gz
* italc_1.0.7-0ubuntu2.diff.gz

Then download the ubuntu-dev-tools
```
sudo aptitude install ubuntu-dev-tools
```

cd to the directory and run this command:
```
sudo pbuilder build *.dsc
```

and there you go... you just built italc_1.0.7-0ubuntu2.deb. so all you have to do now is double-click on that file to install it.

if it didn't build, consult the Ubuntu Packaging Guide at
[https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html)
or more specifically 
[https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-scratch.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-scratch.html)
or
[https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-debhelper.html](https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/basic-debhelper.html)

NOTE: I've tried this before using another package (Mozilla Firefox and Thunderbird) , but using dsc files from the Feisty era. I haven't tried building debs from dsc for a couple of months now so I may be wrong.


i tried following your instructions above, but when i tried installing ubuntu-dev-tools. eto ung lumabas..

[http://www.pastebin.ca/1061100]("http://www.pastebin.ca/1061100")

ano po ibig sabihin nito?:confused:

---

### Post by loell on 2008-07-03
eek, :)

parang wala pa kasing **ubuntu-dev-tools** noon sa dapper
replace mo na lang as

```
sudo apt-get install build-essential
```

---

### Post by daxumaming on 2008-07-03
*headdesks*
oo nga pala, dapper....
install mo pbuilder, tapos try mo ulit.

---

### Post by pogztimz on 2008-07-03
> **loell said:**
> eek, :)

parang wala pa kasing **ubuntu-dev-tools** noon sa dapper
replace mo na lang as

```
sudo apt-get install build-essential
```

k. na install ko na po ung build-essential. ty

> **daxumaming said:**
> *headdesks*
oo nga pala, dapper....
install mo pbuilder, tapos try mo ulit.

na install ko na po ung pbuilder. ty din.. eto po ang lumabas sa terminal ko.. [http://www.pastebin.ca/1061892]("http://www.pastebin.ca/1061892")

:confused: help pls..

---

### Post by pogztimz on 2008-07-07
any update guys? i need to create a .deb for this release. i tried to follow all your instructions, but i simply cant do it..:( help me here.. we really need this program..

edit:

   anong kulang dito?

   [http://www.pastebin.ca/1064338]("http://www.pastebin.ca/1064338")

---

### Post by loell on 2008-07-07
can you,

```
sudo pbuilder create

```

---

