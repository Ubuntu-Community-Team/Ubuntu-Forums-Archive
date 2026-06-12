---
title: "Quinarayan: Isang Proyekto sa Blender"
date: 2009-02-11
forum: Philippine Team
---

### Post by Samhain13 on 2009-02-11
Iko-cross post ko lang po ito: [http://www.pinoyblender.com/project-quinarayan-t483.html](http://www.pinoyblender.com/project-quinarayan-t483.html)

Baka lang kasi may iba pang Pinoy Blender enthusiast dito sa UF na walang magawa. Hehehe!

:guitar:

---

### Post by loell on 2009-02-11
> so, i'm making a game that i call "quinarayan"

jaw drops.. while saying, wow :)

---

### Post by Samhain13 on 2009-02-18
Bump. For great justice! (joke)
Loell, pa-test naman (at pa-review naman ng code kung maaari, diba nagpa-Python ka?).

By the way, new version is available for download.
[http://www.abcruz.com/objectFiles/Quinarayan-current.tar.gz](http://www.abcruz.com/objectFiles/Quinarayan-current.tar.gz) (0.02-alpha)

New alpha, forthcoming. May inaayos lang akong text/narration files at konting graphics. :D

---

### Post by loell on 2009-02-18
i'll try looking at it.. :)

can you give some python/blender references?

---

### Post by Samhain13 on 2009-02-18
Eto yung documentation na lagi kong kinukunsulta:
[http://www.tutorialsforblender3d.com/GameDoc/index_GameDoc.html](http://www.tutorialsforblender3d.com/GameDoc/index_GameDoc.html)

---

### Post by loell on 2009-02-20
mukhang kailangan ko muna yata ng blender 101. :oops:

paano pala e-render ang game?
for example yung introduction.blend?

---

### Post by Samhain13 on 2009-02-20
> **loell said:**
> paano pala e-render ang game?
for example yung introduction.blend?

Naku, madugong usapan yung rendering ng mga bagay-bagay na ginawa para lamang sa GameEngine.

Teka, napatakbo mo ba? Mabagal ba? Anong specs ng box mo?
Yun kasing mga na sa YouTube, nababagalan sila sa graphics, eh kaso sabay ko kasi silang pinapatako ng GTKRecordMyDesktop kaya ganun. Sa Vista, sabi ng girlfriend ko, gapang-- pero naman, ang dami daw niyang bukas na Office documents at Firefox nung pinatakbo niya yung game minsan.

Yun kasing 00-introduction.blend (na hindi ko na din ginagamit sa current version), ang laman lang niya ay puro "Text planes" at background planes. Dun ko lang binabato yung mga linya ng text galing sa files sa "resources/textfiles" para mabasa ng naglalaro. Tapos, toggle ko lang yung visibility ng ibang planes (na may lamang images) para may konting burloloy paminsan-minsan.

Hindi mo yun mare-"render" kasi wala siyang ilaw at yung UV's niya, hindi naka-map sa Textures. Kaya kung susubukan mo siyang i-render matapos kang maglagay ng ilaw, puro asul at puting kahon lang ang makikita mo.

---

### Post by loell on 2009-02-20
i see, heheh, pagni-render ko sa blender black space lang yung nakita ko, anyway nakita ko na yung .sh file, sensya na di ko nakita kanina (pasaway na LXDE) , nakita ko na rin yung code sa introduction.blend , sinulat mo to lahat? 300+ lines of code sa iisang file pa lamang yan, python expert ka na yata eh, para ano pa't  mag co-code review pa ako, di na siguro kailangan  :)

mag-eexplore muna ako sa proyekto mo, napakadami ko pang dapat malaman sa blender kasi.. =P~

---

### Post by Samhain13 on 2009-02-20
> **loell said:**
> i see, heheh, pagni-render ko sa blender black space lang yung nakita ko, anyway nakita ko na yung .sh file, sensya na di ko nakita kanina (pasaway na LXDE) , nakita ko na rin yung code sa introduction.blend , sinulat mo to lahat? 300+ lines of code sa iisang file pa lamang yan, python expert ka na yata eh, para ano pa't  mag co-code review pa ako, di na siguro kailangan  :)

mag-eexplore muna ako sa proyekto mo, napakadami ko pang dapat malaman sa blender kasi.. =P~

Sa totoo lang, yung 300+ lines na yun ang kinakatakot ko. Dahil nga sa natututo pa lang, baka naman may iba pang paraan ng pagsulat sa code na hindi naman aabutin nang ganyan kahaba. Kaya ko talaga gustong ipakita sa mga katulad mo na mas marunong pagdating sa programming ay para maturuan din ako sa pamamagitan ng "review". :D

Hahaha! Malay ko ba kung puwede palang isulat yang mga text evaluation/parsing code na yan sa loob lang pala nang 50 lines. Hahaha! ** toink **

---

### Post by loell on 2009-02-28
got a tiny feature request, on this beautiful Sunday morning.. heheh

1. 180 rotation for key control "S"?
2. default to run mode (increase the walking speed)?

it's up to you, on what's feasible and or fitting :)

---

### Post by Samhain13 on 2009-03-02
> **loell said:**
> got a tiny feature request, on this beautiful Sunday morning.. heheh

1. 180 rotation for key control "S"?
2. default to run mode (increase the walking speed)?

it's up to you, on what's feasible and or fitting :)

1. Why not.
2. I'll have to get around some movement issues. The character doesn't "run" because I have to keep the movement speed to a tolerable minimum. Otherwise, if the character moves faster, he might be able to walk through the objects in the environment. I still haven't found a way to get around that. Sowee. :(

Will get back to this in a couple of weeks as there's other work to be done (the paying kind, hehehe).

But before I got to those other things, I was building a combat screen/simulator for the game. I haven't gotten the thing to work yet though.

---

### Post by loell on 2009-03-04
2. ah so you have to weigh the reasonable speed so as the animation won't flicker?

yeah, no rush though, just update me, err us, whoever is there lurking and also trying the game. :)

---

### Post by Samhain13 on 2009-03-05
Hehehe! Looks like no one else is interested? That's fine too as this is really just an exercise (built for very selfish reasons).

As for number two, no. It's not related to flickering&#8212; that's actually caused by the world having too many objects, and therefore, vertices. That's something that needs to be addressed later, when we (I) get to a later development stage.

The issue with number two is: if I make the character move faster, he will be able to pass through walls and other objects. And that's not very nice. Hehehe! :)

---

### Post by Samhain13 on 2009-06-04
Old thread is old. But I just had a bit of free time to get back to this thing. [Created a project page in my site](http://www.abcruz.com/?args=Development/Quinarayan_Blender_Game_and_Framework/). It includes screenies and some documentation.

Will be packing a new Beta. I do have a question though: will it be OK if I put the tarball in RapidShare instead of hosting it myself? Anyhoo... :D

---

### Post by Script Warlock on 2009-06-05
nasanay kc ako ng 3dmax gawa mga animated logos pero sounds interesting tong blender tuloy lang sir nakasubaybay kami. nice work sir:KS

---

### Post by dodimar on 2009-06-07
> **Samhain13 said:**
> Old thread is old. But I just had a bit of free time to get back to this thing. [Created a project page in my site](http://www.abcruz.com/?args=Development/Quinarayan_Blender_Game_and_Framework/). It includes screenies and some documentation.

Will be packing a new Beta. I do have a question though: will it be OK if I put the tarball in RapidShare instead of hosting it myself? Anyhoo... :D

No, not rapidshare... di ko ma-download yan...

---

### Post by loell on 2009-06-07
pwede naman siguro kung kahit ano, 
pero host mo kaya sa sourceforge or savannah?:D

syempre andyan lang sa dulo si launchpad ):P

---

### Post by Samhain13 on 2009-06-08
Maganda nga siguro sa Launchpad no? Kaso nahihiya ako eh.

---

### Post by loell on 2009-06-09
> **Samhain13 said:**
> Maganda nga siguro sa Launchpad no? Kaso nahihiya ako eh.

nah.. :) noble intentions are way more valuable than coding skills (well initially).

pag may nag criticize ng coding skills o kahit coding conventions ng project mo, sabihin mo lang "instead of just criticizing why not help and offer a solution?" naks!! :D

---

### Post by Samhain13 on 2009-06-10
^ sabagay. Pinapag-isipan ko siya talaga.

Anyway, kakatapos ko lang nung aking bagong XML processing script. Tapos na din yung bagong documentation para sa kaniya. Ngayon, puwede na akong gumawa nang gumawa ng iba pang samples at hindi na ako malilito. Hehehe!

Version 0.03 coming really soon. May isang XML na lang ako na kailangan lagyan ng laman. :D

---

### Post by Samhain13 on 2009-06-15
**UPDATE**

Quinarayan version 0.04 is now available (barubal yung 0.03, kaya wag na yun). Please download, test and help improve. Project page: [http://www.abcruz.com/?args=Development/Quinarayan_Blender_Game_and_Framework/](http://www.abcruz.com/?args=Development/Quinarayan_Blender_Game_and_Framework/) Download link is at the bottom. SALAMATS.

Changes from last time: nothing major on the outside, viewable aspects. But the NPC interaction is a lot more flexible. You now can buy stuff! If you're working for the NPC at the inn, he'll give you a grocery list and money to buy the stuff from the other NPC at the market. This can be the foundation for item buying and selling when I get to the point of extending the 3D world and adding some combat features. You also now have a compass.

Plan for the next version: an item and stats viewer. :D

---

### Post by Samhain13 on 2009-06-25
**New Demo Video**
[http://www.youtube.com/watch?v=pHt9beqgg5I](http://www.youtube.com/watch?v=pHt9beqgg5I)

Version 0.05 to be released soonish (kung walang trabahong biglang dadating). :D

---

### Post by Samhain13 on 2009-06-30
**BAMP!!!**

Quinarayan version 0.05 is available for testing:
[http://www.mediafire.com/?jmmzfgmrbre](http://www.mediafire.com/?jmmzfgmrbre)

Sorry I can't host the package in my site any more because it's getting big. Please test. *And please, if you can help me make it run in Windows...*, yeah. Di na lang kasi mag-Linux ang mga tao, pero talagang ganun.

---

### Post by daxumaming on 2009-07-01
> **Samhain13 said:**
> Sorry I can't host the package in my site any more because it's getting big.

Have it hosted on Google Code or, better yet, Launchpad. You wouldn't have to worry about disk space and bandwidth. Besides, your codes gets versioned.

---

