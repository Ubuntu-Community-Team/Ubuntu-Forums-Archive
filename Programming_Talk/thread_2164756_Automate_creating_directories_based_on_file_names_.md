---
title: "Automate creating directories based on file names and moving files into them"
date: 2013-08-01
forum: Programming Talk
---

### Post by JohnnyC35 on 2013-08-01
I am trying to modify a command from [http://ubuntuforums.org/showthread.php?t=1744554](http://ubuntuforums.org/showthread.php?t=1744554)

```

find . -maxdepth 1 -type f -exec mkdir {}-DIR \; -exec mv {} {}-DIR \; ; find . -maxdepth 1 -type d -exec rename "s:\..{2,3}-DIR::" {} \;

```

This doesn't really work, for me anyways. I am tryng to modify it so it will find various files (tv shows), created a directory from part of the filename, either only using up to the first period or space, and then moving the file to that directory. It wouldn't be the best way to sort files but better than doing it manually. 

Any help would be great :)

---

### Post by TheFu on 2013-08-01
Not sure exactly what you are trying to do, but I have a script that does something like this.  Definitely not as cryptic.

```
#!/bin/bash

# Cur Dir?
curdir=`pwd`


    # List of AVI files
    FILES=`ls -1 *avi *mp4 *mkv *flv`

    # Loop over the list of files
    for file in $FILES ; do
    cd "$curdir"

#SKIP ALL THIS ------------------
    if [ 1 -eq 1 ] ; then

     # Create the name of the directory
     # Remove .mp4
     # Remove .avi
     # Remove -ws
     # Remove -tv
     # Remove -dvd
      new_dir=`echo $file |\
                sed -e 's/.mp4//g' |\
                sed -e 's/.avi//g' |\
                sed -e 's/.flv//g' |\
                sed -e 's/.mkv//g' |\
                sed -e 's/-ws//g' |\
                sed -e 's/-tv//g' |\
                sed -e 's/-dvd//g' `
      # mkdir on the remainder, but only if you aren't already in that dir
      found=`echo "$dir" | egrep -c $new_dir `
      if [ $found -eq 0 ] ; then
         `mkdir -p "$new_dir"`
      fi

      # Move the avi file into the newly created directory
      `mv "$file" "$new_dir"`
      cd "$new_dir"

#SKIP ALL THIS ------------------
    fi
    # Next file
    done

```

Sorry, but all my code, regardless of language looks like C. ;)  I use this a few times a week to put media files into separate directories. The key thing to know is that none of the files can have spaces inside and certain special characters will cause issues too.

---

### Post by JohnnyC35 on 2013-08-01
I woul like it if I could get my files sorted ino directories. If I had a list of files:
Firefly.S01E01
Firefly Episde 2
The.Simpsons.S01E01
Trigun.S01E01
The Sopranos S01E01

The above command would put each file in its own directory. What I am looking to do is to shorten the directory from the first character to the first space or period so..

Firefly/Firefly.S01E01
Firefly/Firefly Episde 2
The/The.Simpsons.S01E01
Trigun/Trigun.S01E01
The/The Sopranos S01E01

There would be an issue with The Simpson and The Sopranos but overall it would make sorting the files alot easier. I haven't found a program gui or otherwise that will do that so that's why I am looking at either cli or bash.

---

### Post by Crusty Old Fart on 2013-08-02
Howdy Johnny:

This might do it:
```

#!/bin/bash
set -e

find . -maxdepth 1 ! -name ${0#./} -type f -print0 | \
while IFN= read -rd '' i; do
  file=${i#./}
  tmp=${file// /.}
  dir=${tmp%%.*}
  if [[ ! -d $dir ]]; then
    mkdir $dir
  fi
  mv "$file" $dir
done

exit 0


```

Happy to answer any questions.

Best of luck to you,

Crusty

---

### Post by JohnnyC35 on 2013-08-09
Thanks for that :) the script acts funny at times but it's alot better than manul sorting :)

---

### Post by Crusty Old Fart on 2013-08-09
> **JohnnyC35 said:**
> Thanks for that :) the script acts funny at times but it's alot better than manul sorting :)

One thing I didn't mention was that in order for the script to work correctly, it must exist in the same directory that contains the files you want sorted.

I could help you debug it if you like. There's a possibility that it might not work as intended with some of your file names. When I run it on my system with the file names you provided above, it doesn't act funny on my system. If you could post the file names that cause it to choke, it would help me discover where the problems may be.

Secondly, the script uses parameter expansion, which embodies some relatively cryptic looking code. It's easy to make a typo if you manually retyped the script when you created it, rather than cutting and pasting it from the code box in my previous post. If you could cut and paste the exact code you are running into your next post, I may be able to spot a typo in it if you made one.

It would also help if you could provide a little more detail regarding the funny things it does.

We could get it to work perfectly, and even tweak it to handle the issue with "The Simpsons and The Sopranos" as well.

On the other hand, I noticed you marked this thread as [SOLVED]. So, perhaps you're happy enough with the results and don't have any desire to spend anymore time on it, especially if the script wasn't intended to be used more than a few times.

Have fun,

Crusty

---

### Post by JohnnyC35 on 2013-08-09
Sure that would be great. *briefly looks around for piracy police*

So here's a section of files, which is 55, including the script 2move .... ok scratch that. 54 files went through without a hitch

rather than a small segment I'll use one of the larger directories. About 331. Maybe I'm just being silly but I remember seeing something crop up so we'll see if it shows now.
oh. and here's the list of those files...
```

torage/files$ ls
12 - Fé.mp4
2 Legend of Korra s02e01 ~ Rebel Spirit [LOW].mkv
2move.sh
911-In.Plane.Site.DirectorS.Cut.WEBRip.H264.AAC-BladeBDP.mkv
ABC.Dancing.With.Dictators.HDTV.x264.720p.AC3.MVGroup.org.mkv
A.Century.of.Light.and.Shadow.8of8.Filmmakers.Without.Frontiers.x264.AC3.MVGroup.Forum.mkv
Adaptation 2002 720p BRrip X264 - MaNaM -.mp4
[A-Destiny] Toriko - 115 (1280x720 Hi10p AAC) [0B1D6158].mkv
Age of Dinosaurs 2013 BRRip x264 AAC-KiSSMYACE.mp4
amwitrc-debt.mkv
[Anime-Koi] Hakkenden Touhou Hakken Ibun - 18 [h264-720p][F03495C1].mkv
Ankur Arora Murder Case - Uyirvani.com.avi
aqos-sdatmm.2013.dvdrip.xvid.avi
[Asenshi-Doremi] Ro-Kyu-Bu! SS - 03 [720p 10bit][A1DF0A3F].mkv
[Asenshi-Doremi] Ro-Kyu-Bu! SS - 03 [720p 8bit][D5D1D9A5].mkv
[Asenshi-Doremi] Ro-Kyu-Bu! SS - 04 [720p 10bit][77B20E2D].mkv
[Asenshi-Doremi] Ro-Kyu-Bu! SS - 04 [720p 8bit][BCD412DD].mkv
[Asenshi-Doremi] Ro-Kyu-Bu! SS - 05v0 [720p 8bit][7DD06FA8].mkv
[Asenshi] Ro-Kyu-Bu! SS - 02 [2C025D27].mkv
axe.cop.s01e03.hdtv.x264-bajskorv.mp4
Bad Milo 2013 DvDScr 325MB blitz101.mkv
Bad Milo 2013 SCR x264 AAC-KiSSMYACE.mp4
BBC.Horizon.2013.Whats.Killing.Our.Bees.720p.HDTV.x264.AAC.MVGroup.org.mkv
BBC.The.Culture.Show.2013.The.Unstoppable.Thomas.Heatherwick.720p.HDTV.x264.AAC.MVGroup.org.mkv
[Beatrice-Raws] Nozoki Ana OVA (Sexy Extended Version) [BDRip 1280x720 x264 FLAC][rev].mkv
Berserk The Golden Age Arc 2 - The Battle for Doldrey 2012 ENG BRRip X264 AC3 FooKaS.mkv
Better.Man.Part.2.HDTV.XviD-AFG.avi
bio-fdtd.3.1.avi
bio-fdtd.3.2.avi
Bleach 309 (1920x1080) [Phr0stY] .mkv
B.o.B Ft. 2 Chainz - HeadBand [Explicit] 720p [Sbyky].mp4
breaking.pointe.s02e02.hdtv.x264-2hd.mp4
BT.Sport.Live.Launch.HDTV.XviD-AFG.avi
Burn.Notice.S07E08.HDTV.x264-EVOLVE.mp4
caligula.with.mary.beard.s01e01.720p.hdtv.x264-ftp.mkv
Ch5.Danger.50000.Volts.9of9.x264.AAC.MVGroup.Forum.mkv
[Coalgirls]_Hunter_X_Hunter_91_(1280x720_H.264_AAC)_[A5F852C0].mkv
comedy.bang.bang.0204.720p-yestv.mkv
[Commie] Dokidoki! Precure - 27 [3B951B50].mkv
[Commie] Free! - 05 [40CD70C4].mkv
[Commie] Futari wa Milky Holmes - 02 [98C5F233].mkv
[Commie] Gatchaman Crowds - 04 [5098A50C].mkv
[Commie] High School DxD New - 04 [3AADC054].mkv
[Commie] Hyperdimension Neptunia The Animation - 04 [2A1C99DA].mkv
[Commie] Senki Zesshou Symphogear G - 05 [D10AA1C4].mkv
[Commie] Servant x Service - 05 [9A2CFC19].mkv
[Commie] Shingeki no Kyojin - 17 [03F766BC].mkv
[Commie] Space Brothers - 68 [3F2CCE2F].mkv
[Commie] Tamako Market - 07 [BD 720p AAC] [E30CA5EF].mkv
[Commie] Tamako Market - 08 [BD 720p AAC] [D1C08054].mkv
Continuum.S02E13.HDTV.XviD-AFG.avi
Copper.S02E07.720p.HDTV.x264-EVOLVE.mkv
Copper.S02E07.HDTV.x264-EVOLVE.mp4
Crossing.Lines.S01E08.Desperation.and.Desperados.WEB-DL.XviD-FUM.avi
Das.Auto.The.Germans.Their.Cars.And.Us.S01E01.HDTV.XviD-AFG.avi
DC.Castle.Ghosts.2of4.Castle.Ghosts.of.Scotland.XviD.AC3.MVGroup.org.avi
[DeadFish] Blood Lad - 01 [720p][AAC].mp4
[DeadFish] Blood Lad - 02 [720p][AAC].mp4
[DeadFish] Blood Lad - 03 [720p][AAC].mp4
[DeadFish] Blood Lad - 04 [720p][AAC].mp4
[DeadFish] Blood Lad - 05 [720p][AAC].mp4
[DeadFish] Hunter X Hunter - 91 [720p][AAC].mp4
[DeadFish] Monogatari Series: Second Season - 01 [720p][AAC].mp4
[DeadFish] Monogatari Series: Second Season - 03 [720p][AAC].mp4
[DeadFish] Monogatari Series: Second Season - 04 [720p][AAC].mp4
[DeadFish] Monogatari Series: Second Season - 05 [720p][AAC].mp4
[DeadFish] Shingeki no Kyojin - 17 [720p][AAC].mp4
[DeadFish] Toaru Kagaku no Railgun S - 17 [720p][AAC].mp4
Dead.Man.Down.2013.480p.BRRip.XviD.AC3-RARBG.avi
Dead.Man.Down.2013.720p.BRRip.XviD.AC3-RARBG.avi
Der.Yalu.Fliesst.E01.081114.avi
Der.Yalu.Fliesst.E02.081114.avi
Der.Yalu.Fliesst.E03.081114.avi
Devious.Maids.S01E07.HDTV.x264-ASAP.mp4
Dexter.S08E06.HDTV.x264-EVOLVE.mp4
Dexter.S08E06.PROPER.HDTV.x264-ASAP.mp4
Discovery.Ch.True.Grit.The.True.Story.PDTV.x264.AAC.MVGroup.org.mp4
Discovery.Scanning.The.Skies.The.Discovery.Channel.Telescope.720p.x264.AAC.MVGroup.org.mp4
[DmonHiro] Kokoro Connect #11 - We Were Told About It Before It Started (BD, 720p) [1FB9643B].mkv
[DmonHiro] Kokoro Connect #12 - On A Snowy Street (BD, 720p) [A5E1458B].mkv
[DmonHiro] Kokoro Connect #13 - As Long As We're Together (BD, 720p) [5EC33A4A].mkv
[Doki] Kimi no Iru Machi - 04 (1280x720 Hi10P AAC) [221C4C20].mkv
[Doki] Kimi no Iru Machi - 04 (848x480 h264 AAC) [1DDA5BA1].mkv
Domestic.Blitz.AU.20130804.The.Block.to.the.Rescue.WS.PDTV.XviD.BF1.avi
Do.No.Harm.S01E07.HDTV.x264-LOL.mp4
DWDD_university_presenteert_De_wereld_van_klopping30.mp4
Eagle.Eye[2008]DvDrip-aXXo.avi
[EROBEAT]_Hontou_ni_Atta_Hitozuma_Furin_Kokuhaku_-_01_[LQ][x264][EF694154].mp4
[EveSenshi] Rozen Maiden Zuru&#776;ckspulen - 06 (10-bit 720p AAC)[5B2BE285].mkv
[EveTaku] Shingeki no Kyojin - 16 (1280x720 x264 AAC)[2097C0FF].mkv
[EveTaku] Shingeki no Kyojin - 16 (1280x720 x264-Hi10P AAC)[48CB5BDD].mkv
[EveTaku] Shingeki no Kyojin - 17 (1280x720 x264 AAC)[4D6E88DE].mkv
[EveTaku] Shingeki no Kyojin - 17 (1280x720 x264-Hi10P AAC)[FB5BC2E9].mkv
Eyewitness.War.S01E12.HDTV.XviD-AFG.avi
Eyewitness.War.S01E13.HDTV.XviD-AFG.avi
Eyewitness.War.S01E14.HDTV.XviD-AFG.avi
Falling.Skies.S03E10.HDTV.x264-EVOLVE.mp4
[FFF] Chuunibyou demo Koi ga Shitai! - 01 [BD][1080p-FLAC][6BF4B9D1].mkv
[FFF] Chuunibyou demo Koi ga Shitai! - 02 [BD][1080p-FLAC][7F54F36C].mkv
[FFF] Chuunibyou demo Koi ga Shitai! - ED01 [BD][1080p-FLAC][DA9EDFF1].mkv
[FFF] Chuunibyou demo Koi ga Shitai! - OP01 [BD][1080p-FLAC][94186416].mkv
[FFF] Love Lab - 05 [F701EE16].mkv
[FTW]_Tamayura_More_Aggressive_-_04_[720p][4FE231B1].mkv
[FTW]_Watashi_ga_Motenai_no_wa_Dou_Kangaetemo_Omaera_ga_Warui_-_04_[720p][F7C55EF8].mkv
full.metal.jacket.dvdrip.xvid.cd1-cultxvid.avi
full.metal.jacket.dvdrip.xvid.cd2-cultxvid.avi
Gatchaman.OVA.V03.The.Final.Countdown.DVDRip.XviD-PARAMOUNT.avi
[gg]_Shingeki_no_Kyojin_-_16_[A7317B05].mkv
Ghost.Hunters.S09E09.Ghost.Friends.Forever.HDTV.XviD-SPASM.avi
Ghost.Hunters.S09E10.HDTV.x264-CRiMSON.mp4
Ghost Rider Spirit Of Vengeance 2012 720p HDRip.avi
Gippi (2013) - 1CD - DVDRip - XviD - AC3 - 5.1 - E-Subs - DrC.avi
Gippi (2013) - DvdRip - X264 - AC3 (5.1CH) - ESubs - 1CD [Team Jaffa].mkv
God.Guns.and.Automobiles.S01E07.720p.HDTV.x264-EVOLVE.mkv
God.Guns.and.Automobiles.S01E07.HDTV.x264-EVOLVE.mp4
gold.rush.s04e01.720p.hdtv.x264-killers.mkv
Gold.Rush.The.Dirt.The Manventure.WS.DSR.x264.NY2.mp4
Graceland.S01E07.HDTV.x264-2HD.mp4
Grand.Designs.Collection.7.4of8.Penthouse.DVDRip.x264.AAC.MVGroup.org.mp4
Grand.Designs.Collection.7.8of8.Timber.Eco.House.DVDRip.x264.AAC.MVGroup.org.mp4
Gravity Falls s01e20 Gideon Rises.mp4
[Hatsuyuki]_Free_-_01_[720p][8D46237C].mp4
[Hatsuyuki]_Free!_-_03_[720p][EC911AE9].mp4
[Hatsuyuki]_Gin_no_Saji_-_01_[720p][733C91AD].mp4
[Hatsuyuki]_High_School_DxD_New_01_[848x480][76B2BB8C].avi
[Hatsuyuki]_High_School_DxD_New_-_02_[720p][62FED8C2].mp4
[Hatsuyuki]_High_School_DxD_New_-_02_[848x480][41B07D4D].avi
[Hatsuyuki]_Makai_Ouji_-_Devils_and_Realist_-_02_[720p][3996B70D].mp4
Haunted.History.2013.S01E04.Lost.Souls.of.Pennhurst.720p.HDTV.x264-DHD.mkv
Hit.The.Floor.S01E10.480p.HDTV.x264-mSD.mkv
Homem.de.Ferro.A.Batalha.Contra.Ezekiel.Stane.Dub.rmvb
[HorribleSubs] Blood Lad - 05 [400p].mkv
[HorribleSubs] Cardfight!! Vanguard Link Joker - 134 [1080p].mkv
[HorribleSubs] Cardfight!! Vanguard Link Joker - 134 [480p].mkv
[HorribleSubs] Cardfight!! Vanguard Link Joker - 134 [720p].mkv
[HorribleSubs] Fantasista Doll - 05 [1080p].mkv
[HorribleSubs] Fantasista Doll - 05 [480p].mkv
[HorribleSubs] Gen'ei o Kakeru Taiyou - Il Sole Penetra le Illusioni - 05 [1080p].mkv
[HorribleSubs] Gen'ei o Kakeru Taiyou - Il Sole Penetra le Illusioni - 05 [480p].mkv
[HorribleSubs] Gen'ei o Kakeru Taiyou - Il Sole Penetra le Illusioni - 05 [720p].mkv
[HorribleSubs] Genshiken Nidaime - 05 [1080p].mkv
[HorribleSubs] Genshiken Nidaime - 05 [480p].mkv
[HorribleSubs] Genshiken Nidaime - 05 [720p].mkv
[HorribleSubs] Hakkenden - Eight Dogs of the East S2 - 17 [720p].mkv
[HorribleSubs] Hunter X Hunter - 91 [1080p].mkv
[HorribleSubs] Hunter X Hunter - 91 [480p].mkv
[HorribleSubs] Hyperdimension Neptunia - The Animation - 04 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 01 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 02 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 03 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 04 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 05 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 06 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 07 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 08 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 09 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 10 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 11 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 12 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 13 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 14 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 15 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 16 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 17 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 18 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 19 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 20 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 21 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 22 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 23 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 24 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 25 [480p].mkv
[HorribleSubs] Kaiji S2 - Against All Rules - 26 [480p].mkv
[HorribleSubs] Kiniro Mosaic - 05 [1080p].mkv
[HorribleSubs] Kiniro Mosaic - 05 [480p].mkv
[HorribleSubs] Kiniro Mosaic - 05 [720p].mkv
[HorribleSubs] Naruto Shippuuden - 323 [1080p].mkv
[HorribleSubs] Naruto Shippuuden - 323 [480p].mkv
[HorribleSubs] Naruto Shippuuden - 323 [720p].mkv
[HorribleSubs] Naruto Shippuuden - 324 [480p].mkv
[HorribleSubs] Space Brothers - 68 [1080p].mkv
[HorribleSubs] Space Brothers - 68 [480p].mkv
[HorribleSubs] Space Brothers - 68 [720p].mkv
[HorribleSubs] Stella Jogakuin Koutouka C3-bu - 04 [720p].mkv
[HorribleSubs] The World God Only Knows - Goddesses Arc - 04 [480p].mkv
[HorribleSubs] Uchouten Kazoku - 05 [480p].mkv
[HorribleSubs] Watamote - 04 [1080p].mkv
[HorribleSubs] Watamote - 04 [720p].mkv
[HorribleSubs] Yami Shibai - Japanese Ghost Stories - 04 [1080p].mkv
[HorribleSubs] Yami Shibai - Japanese Ghost Stories - 04 [720p].mkv
How.Its.Made.Collection.1.11of26.Solar.Panels.Hockey.Sticks.PDTV.x264.AAC.MVGroup.org.mp4
How.Its.Made.Collection.1.12of26.Aluminum.Screw.Caps.Chocolate.PDTV.x264.AAC.MVGroup.org.mp4
How.Its.Made.Collection.1.13of26.Bicycle.Helmet.Lithium.Batteries.PDTV.x264.AAC.MVGroup.org.mp4
How.Its.Made.Collection.1.14of26.Eyeglass.Lenses..Microprocessors.PDTV.x264.AAC.MVGroup.org.mp4
How.Its.Made.Collection.1.16of26.Personal.Watercraft.Ice.Skates.PDTV.x264.AAC.MVGroup.org.mp4
How.Its.Made.Collection.1.17of26.Winter.Jackets.Animation.PDTV.x264.AAC.MVGroup.org.mp4
How.Its.Made.Collection.1.18of26.Hydroponic.Fishing.Flies.PDTV.x264.AAC.MVGroup.org.mp4
How.Its.Made.Collection.1.20of26.Laser.Eye.Surgery.Acoustic.Guitars.PDTV.x264.AAC.MVGroup.org.mp4
How.Its.Made.Collection.1.21of26.Fiberglass.Boats.Fireworks.PDTV.x264.AAC.MVGroup.org.mp4
How.Its.Made.Collection.1.22of26.Steel.Safes.False.Teeth.PDTV.x264.AAC.MVGroup.org.mp4
Hunter X Hunter-Phantom Rouge Movie.GRiN.mp4
ifpd-battledeathtales.us-xvid.avi
Killing.Season.2013.1080p.BluRay.x264.YIFY.mp4
Killing Season (2013) 720p MKV x264 AC3 BluRay-SSRG (1).mkv
Killing.Season.2013.LIMITED.720p.BRRiP.XViD.AC3-LEGi0N.avi
[Kousei]_One_Piece_605_[10bit][720p] [7E785CC8].mkv
[Kousei]_One_Piece_606_[10bit][720p] [6DAADDF7].mkv
Krrish 3 - Official Theatrical Trailer (Exclusive) - YouTube.MP4
La vraie vie des profs [x264] [HD 720p] [LUCN] 2013.mp4
Life.Below.Zero.S01E10.Hell.and.High.Water.mp4
Longmire.S02E09.720p.HDTV.x264-EVOLVE.mkv
Longmire.S02E09.HDTV.x264-EVOLVE.mp4
Love.and.Hip.Hop.Atlanta.S02E15.HDTV.x264-CRiMSON.mp4
Magic.City.S02E07.HDTV.x264-EVOLVE.mp4
Magic.Magic.2013.WEBRIP.XVID.AC3-MAJESTiC.avi
Major.Crimes.S02E08.480p.HDTV.x264-mSD.mkv
Major.Crimes.S02E08.HDTV.x264-EVOLVE.mp4
Man.Of.Tai.Chi.2013.720p.WEBRip.x264-SAUFi88.mkv
Marea Letal [2012][BD 1080p][Audio Castellano AC3 5.1][Thriller].mkv
Mirai Nikki Redial - OVA (DVD 720x480 AVC AAC).mp4
mistresses.us.109.hdtv-lol.mp4
Mountain.Men.S02E09.HDTV.x264-KILLERS.mp4
Mythbusters.S12.Breaking.Badl.720p.HDTV.x264-NOGRP.mkv
Mythbusters.S12E12.HDTV.x264-SHO.mp4
Naruto Shippuden - 323.mp4
Naruto Shippuuden - 324 [720p] [ENG-SUBBED] [GWC].mkv
Nazi.Mega.Weapons.S01E03.V2.Rocket.x264-SM.mp4
Necessary.Roughness.S03E08.720p.HDTV.x264-IMMERSE.mkv
Necessary.Roughness.S03E08.HDTV.x264-ASAP.mp4
NTSF.SD.SUV.S03E02.HDTV.x264-EVOLVE.mp4
Paranormal.Witness.S03E05.Deliver.Us.From.Evil.HDTV.XviD-SPASM.avi
Paranormal.Witness.S03E07.The.Bad.Man.HDTV.XviD-SPASM.avi
Paranormal.Witness.S03E08.The.Manson.Curse.HDTV.XviD-AFG.avi
Paranormal.Witness.S03E09.The.Wolf.Pack.HDTV.XviD-SPASM.avi
PBS.America.Extinction.PDTV.x264.AAC.MVGroup.org.mp4
PBS.Charlie.Rose.2013.Vince.Gilligan.Creator.of.Breaking.Bad.720p.x264.AAC.MVGroup.Forum.mp4
Pecker.1998.iNTERNAL.RERiP.DVDRip.XviD-MULTiPLY.avi
PhoneShop.S03E02.HDTV.XviD-AFG.avi
Pokemon Black & White Adventures in Unova and Beyond - 1627 - Danger, Sweet as Honey! {C_P}.avi
Pokemon.S15E21.Climbing.The.Tower.Of.Success.HDTV.XviD-AFG.avi
Princesses.Long.Island.S01E09.Chucky.avi
Project Runway S12E03-An Unconventional Coney Island.mp4
Ray.Donovan.S01E06.HDTV.x264-ASAP.mp4
Ray.Donovan.S01E06.HDTV.XviD-AFG.avi
Restaurant.Impossible.S04SP01.Wedding.Impossible.Meet.The.Irvines.HR.HDTV.x264-FOOD.mp4
Restaurant.Impossible.S04SP02.Behind.The.Impossible.50th.Episode.Special.HR.HDTV.x264-FOOD.mp4
Rihanna 777 (2013) 720p 525MB-blitz101.mkv
Royal.Pains.S05E07.HDTV.x264-ASAP.mp4
royal.pains.s05e08.hdtv.x264-2hd.mp4
RWBY 04 -  The First Step.mp4
Ryoujoku NewsCaster.mp4
saint.hoods.s01e01.720p.hdtv.x264-killers.mkv
[Saizen]_Taisho_Baseball_Girls_06v2_[720p][Blu-Ray][B3F52BDC].mkv
Scary.Movie.5.2013.BRRIP.Xvid.AC3-BHRG.avi
Scary Movie 5 (2013) BRRip XviD-LTRG.avi
Scooby-Doo Adventures The Mystery Map 2013 DVDRiP AC3 XViD-SSRG.avi
Season 1 EP4  Safe (HD).mp4
Serial.Killer.Earth.Series.1.08of10.Hurricane.Attacks.Weatherman.PDTV.x264.AAC.MVGroup.org.mp4
Shark.Week.2013.I.Escaped.JAWS.480p.HDTV.x264-mSD.mkv
shark.week.2013.top.ten.sharkdown.720p.hdtv.x264-killers.mkv
Siberia.S01E04.HDTV.x264-BAJSKORV.[VTV].mp4
Sky Fighters 2005.720p BluRay AC3.x264 (AtlaN64).mkv
[SubDESU] High School DxD NEW - 05 (1280x720 10bit Uncensored) [288D9440].mkv
Suits.S03E04.HDTV.x264-ASAP.mp4
Tabatha.Takes.Over.s05e11.Nadia's.Family.Salon.HDTV.x264-Weby.mp4
Tabatha.Takes.Over.s05e12.Where.Are.They.Now.HDTV.x264-Weby.mp4
[Taka]_Naruto_Shippuuden_321_[480p][27BC977A].mp4
[Taka]_Naruto_Shippuuden_321_[720p][BD3DC33D].mp4
The.Bridge.US.S01E05.HDTV.x264-ASAP.[VTV].mp4
the.call.centre.s01e01.720p.hdtv.x264-c4tv.mkv
The.Colbert.Report.2013.08.06.Daft.Punk.HDTV.x264-EVOLVE.[VTV].mp4
The Conjuring 2013 WEBRiP x264 AC3-KiSSMYACE.mp4
The Conjuring VODRip x264 AC3-animal.avi
TheCroods.2013.HDTV.720P.X264.AC3.2Audio.mkv
The Dealership S1 E1.avi
THE GEORGE BURNS and GRACIE ALLEN SHOW -- Blanche's dishonest brother Roger ( 5th Season ) with King Donovan.mp4
THE GEORGE BURNS and GRACIE ALLEN SHOW -- Buying George a Ranch ( 3rd Season ).flv
THE GEORGE BURNS and GRACIE ALLEN SHOW -- Emily Vanderlip's Elopement ( 4th Season ) with Sarah Selby and Robert Foulk.flv
THE GEORGE BURNS and GRACIE ALLEN SHOW -- Gracie Gets a Jury Summons ( 4th Season ) with Will Wright.flv
THE GEORGE BURNS and GRACIE ALLEN SHOW -- Gracie Gives a Party for an Atomic Scientist ( 3rd Season ).flv
The.Glades.S04E10.Gallerinas.720p.WEB-DL.DD5.1.H.264-Abjex.mkv
The Great American Snuff Film.avi
The.Hot.Flashes.2013.DVDRiP.AC3-5.1.XviD-AXED.avi
the.house.of.tomorrow.2011.dvdrip.x264-redblade.mkv
The.Killing.S03E10.HDTV.x264-2HD.mp4
The.Killing.S03E11E12.HDTV.x264-EVOLVE.mp4
The.Killing.S03E11E12.PROPER.720p.HDTV.x264-EVOLVE.mkv
The.Listener.S04E09.HDTV.x264-BAJSKORV.mp4
the.listener.s04e10.hdtv.x264-bajskorv.mp4
The.Listener.S04E10.HDTV.XviD-AFG.avi
The.Newsroom.2012.S02E04.HDTV.x264-2HD.mp4
The.Newsroom.2012.S02E04.HDTV.XviD-AFG.avi
The.Soul.Man.S02E07.720p.HDTV.x264-IMMERSE.mkv
The.White.Queen.1x08.Long.Live.The.King.HDTV.x264-FoV.mp4
Tifa 20 Years Old.avi
Top.Gear.20x01.HDTV.x264-FoV.mp4
Top.Gear.20x02.HDTV.x264-FoV.mp4
Top.Gear.20x04.HDTV.x264-FoV.mp4
Top.Gear.20x06.HDTV.x264-FoV.mp4
Top.Gear.S20E03.HDTV.x264-TLA.mp4
Top.Gear.S20E05.HDTV.x264-TLA.mp4
Tristan and Isolde 2006 BluRay 720p x264 (AtlaN64).mp4
True.Blood.S06E08.Dead.Meat.WEB-DL.XviD-FUM.avi
true.blood.s06e08.hdtv.x264-2hd.mp4
ultimate spider man 215 stand by me.FLV
under.the.dome.106.hdtv-lol.mp4
Under.the.Dome.S01E06.HDTV.x264-LOL.[VTV].mp4
Unforgettable.S02E02.HDTV.XviD-AFG.avi
Unsealed.Alien.Files.S01E22.HDTV.xvid-][ Alien Hot Spots ][ 04-Aug-2013 ].avi
Unsealed.Conspiracy.Files.S01E22.HDTV.xvid-][ Americas Flying Saucer ][ 04-Aug-2013 ].avi
Unutma Beni Istanbul (I axehasti Poli) 2011 DVDRipXvid.avi
[UTW]_Danganronpa_The_Animation_-_05_[h264-480p][CF17DD94].mp4
[UTW]_Fate_Kaleid_Liner_Prisma_Ilya_-_05v0_[396p][C9178A88].mkv
[UTW-Mazui]_Toaru_Kagaku_no_Railgun_S_-_17_[480p][1C09C873].mp4
[UTW-Mazui]_Toaru_Kagaku_no_Railgun_S_-_17_[720p][60B4FC61].mkv
[Vivid] Uchouten Kazoku - 05 [9658811A].mkv
We.Are.Legion.2012.720p.WEB-DL.AAC2.0.H.264-TC.mkv
Web.Therapy.S03E03.480p.HDTV.x264-mSD.mkv
Will 3D Printing Change the World by -=OzYrIs=-.mp4
www.TamilRockers.net - Hulk (2003) 720p BDRip [Tamil & Eng][x264 - 900MB - ESubs].mkv
www.TamilRockers.net - The Incredible Hulk (2008) 720p BDRip [Tamil & Eng][x264 - 700MB - ESubs].mkv
[ www.UsaBit.com ] - Crouching Tiger Hidden Dragon 2000 DUBBED 720p BRRip x264-PLAYNOW.mp4
[ www.UsaBit.com ] - Exploding Sun (2013) BluRay 720p x264 Ganool.mkv
[ www.UsaBit.com ] - Least Among Saints (2012) 720p WEB-DL 800MB Ganool.mkv
[ www.UsaBit.com ] - Passenger 57 1992 720p BRRip x264-PLAYNOW.mp4
[ www.UsaBit.com ] - Rihanna 777 (2013) 720p WEB-DL 550MB Ganool.mkv
[ www.UsaBit.com ] - Scary Movie 2 (2001) BluRay 720p 600MB Ganool.mkv
[ www.UsaBit.com ] - The Last Will And Testament Of Rosalind Leigh (2012) 720p WEB-DL 600MB Ganool.mkv
[ www.UsaBit.com ] - Touchy Feely (2013) 720p WEB-DL 600MB Ganool.mkv
YLE.Time.and.Matter.5of5.Optical.Sound.XviD.AC3.MVGroup.org.avi
[youshikibi] Naruto Shippuden - 324 (1280x720 h264 AAC) [e3b8fc93].mp4

```

Not exactly what I saw before but... so the script did it's thing and up came
**mkdir: cannot create directory ‘B’: File exists**

and there are 119 files unsorted. The list of what's what below
```

john@Home:/storage/files$ ls --group-directories-first
12
amwitrc-debt
[Anime-Koi]
[Asenshi]
[Asenshi-Doremi]
axe
B
Bad
Bleach
breaking
BT
Burn
Ch5
[Coalgirls]_Hunter_X_Hunter_91_(1280x720_H
[Commie]
Continuum
Copper
Crossing
[DeadFish]
Devious
Dexter
[DmonHiro]
Do
[Doki]
DWDD_university_presenteert_De_wereld_van_klopping30
[EROBEAT]_Hontou_ni_Atta_Hitozuma_Furin_Kokuhaku_-_01_[LQ][x264][EF694154]
[EveSenshi]
[EveTaku]
Eyewitness
Falling
[FFF]
[FTW]_Tamayura_More_Aggressive_-_04_[720p][4FE231B1]
[FTW]_Watashi_ga_Motenai_no_wa_Dou_Kangaetemo_Omaera_ga_Warui_-_04_[720p][F7C55EF8]
[gg]_Shingeki_no_Kyojin_-_16_[A7317B05]
Ghost
God
Gold
Graceland
Gravity
[Hatsuyuki]_Free_-_01_[720p][8D46237C]
[Hatsuyuki]_Free!_-_03_[720p][EC911AE9]
[Hatsuyuki]_High_School_DxD_New_01_[848x480][76B2BB8C]
[Hatsuyuki]_High_School_DxD_New_-_02_[720p][62FED8C2]
[Hatsuyuki]_High_School_DxD_New_-_02_[848x480][41B07D4D]
[Hatsuyuki]_Makai_Ouji_-_Devils_and_Realist_-_02_[720p][3996B70D]
Hit
Homem
[HorribleSubs]
How
Hunter
[Kousei]_One_Piece_605_[10bit][720p]
[Kousei]_One_Piece_606_[10bit][720p]
Krrish
Life
Longmire
Love
Magic
Major
Mirai
mistresses
Mythbusters
Naruto
Nazi
Necessary
NTSF
Paranormal
PhoneShop
Pokemon
Project
Ray
Restaurant
Royal
royal
RWBY
Ryoujoku
[Saizen]_Taisho_Baseball_Girls_06v2_[720p][Blu-Ray][B3F52BDC]
Season
Shark
[SubDESU]
Suits
[Taka]_Naruto_Shippuuden_321_[480p][27BC977A]
[Taka]_Naruto_Shippuuden_321_[720p][BD3DC33D]
THE
The
the
Tifa
ultimate
Under
under
Unforgettable
Unsealed
[UTW]_Danganronpa_The_Animation_-_05_[h264-480p][CF17DD94]
[UTW]_Fate_Kaleid_Liner_Prisma_Ilya_-_05v0_[396p][C9178A88]
[UTW-Mazui]_Toaru_Kagaku_no_Railgun_S_-_17_[480p][1C09C873]
[Vivid]
Web
Will
YLE
[youshikibi]

<<fake spacing; above are directories, below are files left>>

2 Legend of Korra s02e01 ~ Rebel Spirit [LOW].mkv
2move.sh
911-In.Plane.Site.DirectorS.Cut.WEBRip.H264.AAC-BladeBDP.mkv
ABC.Dancing.With.Dictators.HDTV.x264.720p.AC3.MVGroup.org.mkv
A.Century.of.Light.and.Shadow.8of8.Filmmakers.Without.Frontiers.x264.AC3.MVGroup.Forum.mkv
Adaptation 2002 720p BRrip X264 - MaNaM -.mp4
[A-Destiny] Toriko - 115 (1280x720 Hi10p AAC) [0B1D6158].mkv
Age of Dinosaurs 2013 BRRip x264 AAC-KiSSMYACE.mp4
Ankur Arora Murder Case - Uyirvani.com.avi
aqos-sdatmm.2013.dvdrip.xvid.avi
BBC.Horizon.2013.Whats.Killing.Our.Bees.720p.HDTV.x264.AAC.MVGroup.org.mkv
BBC.The.Culture.Show.2013.The.Unstoppable.Thomas.Heatherwick.720p.HDTV.x264.AAC.MVGroup.org.mkv
[Beatrice-Raws] Nozoki Ana OVA (Sexy Extended Version) [BDRip 1280x720 x264 FLAC][rev].mkv
Berserk The Golden Age Arc 2 - The Battle for Doldrey 2012 ENG BRRip X264 AC3 FooKaS.mkv
Better.Man.Part.2.HDTV.XviD-AFG.avi
bio-fdtd.3.1.avi
bio-fdtd.3.2.avi
caligula.with.mary.beard.s01e01.720p.hdtv.x264-ftp.mkv
comedy.bang.bang.0204.720p-yestv.mkv
[Commie] Dokidoki! Precure - 27 [3B951B50].mkv
[Commie] Shingeki no Kyojin - 17 [03F766BC].mkv
Copper.S02E07.720p.HDTV.x264-EVOLVE.mkv
Das.Auto.The.Germans.Their.Cars.And.Us.S01E01.HDTV.XviD-AFG.avi
DC.Castle.Ghosts.2of4.Castle.Ghosts.of.Scotland.XviD.AC3.MVGroup.org.avi
Dead.Man.Down.2013.480p.BRRip.XviD.AC3-RARBG.avi
Dead.Man.Down.2013.720p.BRRip.XviD.AC3-RARBG.avi
Der.Yalu.Fliesst.E01.081114.avi
Der.Yalu.Fliesst.E02.081114.avi
Der.Yalu.Fliesst.E03.081114.avi
Discovery.Ch.True.Grit.The.True.Story.PDTV.x264.AAC.MVGroup.org.mp4
Discovery.Scanning.The.Skies.The.Discovery.Channel.Telescope.720p.x264.AAC.MVGroup.org.mp4
Domestic.Blitz.AU.20130804.The.Block.to.the.Rescue.WS.PDTV.XviD.BF1.avi
Eagle.Eye[2008]DvDrip-aXXo.avi
[EveTaku] Shingeki no Kyojin - 17 (1280x720 x264 AAC)[4D6E88DE].mkv
[EveTaku] Shingeki no Kyojin - 17 (1280x720 x264-Hi10P AAC)[FB5BC2E9].mkv
[FFF] Chuunibyou demo Koi ga Shitai! - 01 [BD][1080p-FLAC][6BF4B9D1].mkv
[FFF] Chuunibyou demo Koi ga Shitai! - 02 [BD][1080p-FLAC][7F54F36C].mkv
full.metal.jacket.dvdrip.xvid.cd1-cultxvid.avi
full.metal.jacket.dvdrip.xvid.cd2-cultxvid.avi
Gatchaman.OVA.V03.The.Final.Countdown.DVDRip.XviD-PARAMOUNT.avi
Ghost Rider Spirit Of Vengeance 2012 720p HDRip.avi
Gippi (2013) - 1CD - DVDRip - XviD - AC3 - 5.1 - E-Subs - DrC.avi
Gippi (2013) - DvdRip - X264 - AC3 (5.1CH) - ESubs - 1CD [Team Jaffa].mkv
God.Guns.and.Automobiles.S01E07.720p.HDTV.x264-EVOLVE.mkv
gold.rush.s04e01.720p.hdtv.x264-killers.mkv
Grand.Designs.Collection.7.4of8.Penthouse.DVDRip.x264.AAC.MVGroup.org.mp4
Grand.Designs.Collection.7.8of8.Timber.Eco.House.DVDRip.x264.AAC.MVGroup.org.mp4
[Hatsuyuki]_Gin_no_Saji_-_01_[720p][733C91AD].mp4
Haunted.History.2013.S01E04.Lost.Souls.of.Pennhurst.720p.HDTV.x264-DHD.mkv
[HorribleSubs] Cardfight!! Vanguard Link Joker - 134 [1080p].mkv
[HorribleSubs] Fantasista Doll - 05 [1080p].mkv
[HorribleSubs] Gen'ei o Kakeru Taiyou - Il Sole Penetra le Illusioni - 05 [1080p].mkv
[HorribleSubs] Genshiken Nidaime - 05 [1080p].mkv
[HorribleSubs] Hunter X Hunter - 91 [1080p].mkv
[HorribleSubs] Kiniro Mosaic - 05 [1080p].mkv
[HorribleSubs] Naruto Shippuuden - 323 [1080p].mkv
[HorribleSubs] Space Brothers - 68 [1080p].mkv
[HorribleSubs] Watamote - 04 [1080p].mkv
ifpd-battledeathtales.us-xvid.avi
Killing.Season.2013.1080p.BluRay.x264.YIFY.mp4
Killing Season (2013) 720p MKV x264 AC3 BluRay-SSRG (1).mkv
Killing.Season.2013.LIMITED.720p.BRRiP.XViD.AC3-LEGi0N.avi
La vraie vie des profs [x264] [HD 720p] [LUCN] 2013.mp4
Longmire.S02E09.720p.HDTV.x264-EVOLVE.mkv
Magic.Magic.2013.WEBRIP.XVID.AC3-MAJESTiC.avi
Man.Of.Tai.Chi.2013.720p.WEBRip.x264-SAUFi88.mkv
Marea Letal [2012][BD 1080p][Audio Castellano AC3 5.1][Thriller].mkv
Mountain.Men.S02E09.HDTV.x264-KILLERS.mp4
Mythbusters.S12.Breaking.Badl.720p.HDTV.x264-NOGRP.mkv
Necessary.Roughness.S03E08.720p.HDTV.x264-IMMERSE.mkv
PBS.America.Extinction.PDTV.x264.AAC.MVGroup.org.mp4
PBS.Charlie.Rose.2013.Vince.Gilligan.Creator.of.Breaking.Bad.720p.x264.AAC.MVGroup.Forum.mp4
Pecker.1998.iNTERNAL.RERiP.DVDRip.XviD-MULTiPLY.avi
Princesses.Long.Island.S01E09.Chucky.avi
Restaurant.Impossible.S04SP01.Wedding.Impossible.Meet.The.Irvines.HR.HDTV.x264-FOOD.mp4
Rihanna 777 (2013) 720p 525MB-blitz101.mkv
saint.hoods.s01e01.720p.hdtv.x264-killers.mkv
Scary.Movie.5.2013.BRRIP.Xvid.AC3-BHRG.avi
Scary Movie 5 (2013) BRRip XviD-LTRG.avi
Scooby-Doo Adventures The Mystery Map 2013 DVDRiP AC3 XViD-SSRG.avi
Serial.Killer.Earth.Series.1.08of10.Hurricane.Attacks.Weatherman.PDTV.x264.AAC.MVGroup.org.mp4
shark.week.2013.top.ten.sharkdown.720p.hdtv.x264-killers.mkv
Siberia.S01E04.HDTV.x264-BAJSKORV.[VTV].mp4
Sky Fighters 2005.720p BluRay AC3.x264 (AtlaN64).mkv
Tabatha.Takes.Over.s05e11.Nadia's.Family.Salon.HDTV.x264-Weby.mp4
Tabatha.Takes.Over.s05e12.Where.Are.They.Now.HDTV.x264-Weby.mp4
the.call.centre.s01e01.720p.hdtv.x264-c4tv.mkv
The Conjuring 2013 WEBRiP x264 AC3-KiSSMYACE.mp4
The Conjuring VODRip x264 AC3-animal.avi
TheCroods.2013.HDTV.720P.X264.AC3.2Audio.mkv
The.Glades.S04E10.Gallerinas.720p.WEB-DL.DD5.1.H.264-Abjex.mkv
The Great American Snuff Film.avi
The.Hot.Flashes.2013.DVDRiP.AC3-5.1.XviD-AXED.avi
the.house.of.tomorrow.2011.dvdrip.x264-redblade.mkv
The.Killing.S03E11E12.PROPER.720p.HDTV.x264-EVOLVE.mkv
The.Newsroom.2012.S02E04.HDTV.XviD-AFG.avi
The.Soul.Man.S02E07.720p.HDTV.x264-IMMERSE.mkv
Top.Gear.20x01.HDTV.x264-FoV.mp4
Top.Gear.20x02.HDTV.x264-FoV.mp4
Top.Gear.20x04.HDTV.x264-FoV.mp4
Top.Gear.20x06.HDTV.x264-FoV.mp4
Top.Gear.S20E03.HDTV.x264-TLA.mp4
Top.Gear.S20E05.HDTV.x264-TLA.mp4
Tristan and Isolde 2006 BluRay 720p x264 (AtlaN64).mp4
True.Blood.S06E08.Dead.Meat.WEB-DL.XviD-FUM.avi
true.blood.s06e08.hdtv.x264-2hd.mp4
Unutma Beni Istanbul (I axehasti Poli) 2011 DVDRipXvid.avi
[UTW-Mazui]_Toaru_Kagaku_no_Railgun_S_-_17_[720p][60B4FC61].mkv
We.Are.Legion.2012.720p.WEB-DL.AAC2.0.H.264-TC.mkv
www.TamilRockers.net - Hulk (2003) 720p BDRip [Tamil & Eng][x264 - 900MB - ESubs].mkv
www.TamilRockers.net - The Incredible Hulk (2008) 720p BDRip [Tamil & Eng][x264 - 700MB - ESubs].mkv
[ www.UsaBit.com ] - Crouching Tiger Hidden Dragon 2000 DUBBED 720p BRRip x264-PLAYNOW.mp4
[ www.UsaBit.com ] - Exploding Sun (2013) BluRay 720p x264 Ganool.mkv
[ www.UsaBit.com ] - Least Among Saints (2012) 720p WEB-DL 800MB Ganool.mkv
[ www.UsaBit.com ] - Passenger 57 1992 720p BRRip x264-PLAYNOW.mp4
[ www.UsaBit.com ] - Rihanna 777 (2013) 720p WEB-DL 550MB Ganool.mkv
[ www.UsaBit.com ] - Scary Movie 2 (2001) BluRay 720p 600MB Ganool.mkv
[ www.UsaBit.com ] - The Last Will And Testament Of Rosalind Leigh (2012) 720p WEB-DL 600MB Ganool.mkv
[ www.UsaBit.com ] - Touchy Feely (2013) 720p WEB-DL 600MB Ganool.mkv

```

I thought it might be because of "B.o.B Ft. 2 Chainz - HeadBand [Explicit] 720p [Sbyky].mp4" so I renamed the first part from B.o.B to BoB, next error was **mkdir: cannot create directory ‘A’: File exists**

There is an A directory and A.Century.of.Light.and.Shadow.8of8.Filmmakers.Without.Frontiers.x264.AC3.MVGroup.Forum.mkv is in it.

hmmm

From what I see in the script, it should try to make the directory, but even if it can't it should still keep going and move the file into the directory that is already created.

I just moved all the files out and kept the directory structure:** find -type f -exec mv {} /storage/files/ \;** and then ran the script again. all the files that were moved before were moved and I still got the cannot create directory 'A', file exists.

Not too sure what's next. Other than using it on small directory listings only :)

---

### Post by Crusty Old Fart on 2013-08-10
Johnny:

Thank you for taking the time to provide a large list of files to use for debugging.

I experienced similar problems when I ran my original script with it. The script seemed to be choking on file names that begin with left brackets: [

It appears to me that I made two errors in my original script:
[LIST=1]
[*]I should have adhered to the good habit of being more generous with enclosing my variable expansions in double quotes. 
[*]In the line that begins the while loop, I used: [COLOR=#ff0000]**IFN=**[/COLOR]  ( it should have been [COLOR=#008000]**IFS=**[/COLOR] ) 
[/LIST]

The corrected script, which worked as intended for all the files in the large list, is in the code box below:
```

#!/bin/bash
set -e

find . -maxdepth 1 ! -name ${0#./} -type f -print0 | \
while IFS= read -rd '' i; do
  file=${i#./}
  tmp=${file// /.}
  dir=${tmp%%.*}
  if [[ ! -d "$dir" ]]; then
    mkdir "$dir"
  fi
  mv "$file" "$dir"
done

exit 0

```

So sorry for my errors. I hope the corrected script works as well for you as it did for me.

Thanks again,

Crusty

---

### Post by JohnnyC35 on 2013-08-10
Not at all Crusty, thanks for the help. I had kind of figured out what to do... if I was using Q/Visual Basic but it's not the same in bash/python :)

I saw no errors and the only 'problem' that came up was with files with underscores instead of spaces which was fixed with **find . -depth|rename 's/\_/ /g'** before the whole sorting thing, and a couple other tweaks heh.

This will make it much easier to go through the directory that time forgot :)

> 
#!/bin/bash
set -e

echo && echo

read -p "This will move all files from folders in this, the parent, folder. Afterwards the files will be sorted into new folders with any underscores stripped. Do you want to continue??? Press Enter to continue."

echo && echo Removing all files from parent directory to the parent directory
find -type f -exec mv {} $(pwd) \; > /dev/null 2>&1

echo && echo Replacing '_' with spaces
find . -depth|rename 's/\_/ /g'

echo && echo Moving files into directories based on the first word
find . -maxdepth 1 ! -name ${0#./} -type f -print0 | \
while IFS= read -rd '' i; do
  file=${i#./}
  tmp=${file// /.}
  dir=${tmp%%.*}
  if [[ ! -d "$dir" ]]; then
    mkdir "$dir"
  fi
  mv "$file" "$dir"
done

echo && echo "For your own safety the script will now make itself unexecutable."
sudo chmod -x 2move.sh

exit 0


---

### Post by Crusty Old Fart on 2013-08-10
Johnny:

Ahhh...now we're getting somewhere. Nice job.

I have a few things to present that you may decide to use to make the script a little better, and perhaps turn you on to some command options and bash resources that you may not have discovered. Please understand that *nothing* I'm presenting below is meant to criticize anything you've done with the script. Some of it is simply a matter of "coding style". After all, we all have our own personal preferences when writing code and there are often several ways to accomplish the same objective. Also, please don't be offended if I mention something that you already know about. I don't mean to suggest ignorance on your part with anything I've written below. Thanks in advance for your understanding.
[HR][/HR]
_The "-e" option for the "echo" command:_
This option allows the flexibility of embedding escape characters anywhere within an echo statement that is bounded by double quotes ("). It could be applied to your read prompt to embed newline characters (\n) as follows:
```

echo -e "\nThis will move all files from folders in this, the parent, folder.\nAfterwards the files will be sorted into new folders with any underscores stripped.\nDo you want to continue???\n"
read -p "Press [Enter] to continue or [Ctrl+C] to abort: "

[COLOR=#008000]**~~~ Output: ~~~**[/COLOR]

This will move all files from folders in this, the parent, folder.
Afterwards the files will be sorted into new folders with any underscores stripped.
Do you want to continue???

Press [Enter] to continue or [Ctrl+C] to abort: 

```
[HR][/HR]
_Parameter Expansion:_
A few years ago, I was involved in a thread where I was writing string replacement commands with sed. At the time, I hadn't discovered the "parameter expansion" features of bash. One of the other posters, who had much more experience than I do, suggested to me that I should use "parameter expansion" instead of sed commands wherever possible because they run so much faster. He helped educate me by directing me to the following resources:
[http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073) 
and
[http://mywiki.wooledge.org/BashFAQ/100](http://mywiki.wooledge.org/BashFAQ/100)

Parameter expansion could be used in our while loop to replace the underbar characters (_) with whitespaces when building our directory names as follows ([COLOR=#0000FF]**Note Step 2**[/COLOR]):
```
while IFS= read -rd '' i; do
# Create directory name:
  # Step 1: Strip the leading dot and slash from the file name and store the result in a variable named: file
      file=${i#./}
[COLOR=#0000CD][B]  # Step 2: Replace all the underbar characters (_) with whitespaces in the file variable and store the result in a variable named: tmp1
      tmp1=${file//_/ }[/B][/COLOR]
  # Step 3: Replace all the whitespaces with dot characters (.) in the tmp1 variable and store the result in a variable named: tmp2
      tmp2=${tmp1// /.}
  # Step 4: Remove all characters from (and including) the first dot to the end of the character string in the tmp2 variable and store the result in a variable named: dir
      dir=${tmp2%%.*}
  # Step 5: If a directory having the name of the string contained within the dir variable does not exist, then create it:
      if [[ ! -d "$dir" ]]; then
        mkdir "$dir"
      fi
# Move file into directory:
    mv "$file" "$dir"
done

```

By using parameter expansion to replace the underbar characters with whitespaces, we eliminate the need for this code...
```
find . -depth|rename 's/\_/ /g'
```
...which has a comparatively much higher processor overhead.
[HR][/HR]
_Process Substitution:_
I should have used **[COLOR=#0000FF]"Process Substitution"[/COLOR]** (Ref.: [http://mywiki.wooledge.org/ProcessSubstitution](http://mywiki.wooledge.org/ProcessSubstitution)) to bypass the subshell caused by piping the output of my "find" command into the while loop. For our script, it wouldn't have made any difference (at least, not yet), but it is a good habit to develop and it would look like this:
```

while IFS= read -rd '' i; do
# Create directory name:
  # Step 1: Strip the leading dot and slash from the file name and store the result in a variable named: file
    file=${i#./}
  # Step 2: Replace all the underbar characters (_) with whitespaces in the file variable and store the result in a variable named: tmp1
    tmp1=${file//_/ }
  # Step 3: Replace all the whitespaces with dot characters (.) in the tmp1 variable and store the result in a variable named: tmp2
    tmp2=${tmp1// /.}
  # Step 4: Remove all characters from (and including) the first dot to the end of the character string in the tmp2 variable and store the result in a variable named: dir
    dir=${tmp2%%.*}
  # Step 5: If a directory having the name of the string contained within the dir variable does not exist, then create it:
    if [[ ! -d "$dir" ]]; then
      mkdir "$dir"
    fi
# Move file into directory:
  mv "$file" "$dir"
done **[COLOR=#0000FF]< <(find . -maxdepth 1 ! -name ${0#./} -type f -print0)[/COLOR]**

```
[HR][/HR]
Now, if I combine some of what you've done with the changes I've presented above, and I remove the comments that are cluttering up the while loop, the script could look like this:
```

#!/bin/bash
set -e

echo -e "\nThis will move all files from folders in this, the parent, folder.\nAfterwards the files will be sorted into new folders with any underscores stripped.\nDo you want to continue???\n"
read -p "Press [Enter] to continue or [Ctrl+C] to abort: "

while IFS= read -rd '' i; do
  file=${i#./}
  tmp1=${file//_/ }
  tmp2=${tmp1// /.}
  dir=${tmp2%%.*}
  if [[ ! -d "$dir" ]]; then
    mkdir "$dir"
  fi
  mv "$file" "$dir"
done < <(find . -maxdepth 1 ! -name ${0#./} -type f -print0)

echo -e "\nFor your own safety the script will now make itself unexecutable."
sudo chmod -x 2move.sh

exit 0

```
[HR][/HR]
Sorry if I've beaten a dead horse so hard that I've pounded him several more feet below ground level. But, in the interest of education and adding to the toys in our bash toolbox, I thought this post might be of some help to you.

Crusty

---

### Post by Crusty Old Fart on 2013-08-10
We both have overlooked the problem that would result if any of the file  names begin with either a single or repeating whitespace or underbar or any string consisting of a mixed combination of the two of them.
Ugh!
I'm going to need to spend a little time studying up on parameter expansion for a solution to this problem that doesn't end up making an ugly mess of some otherwise relatively clean code.

---

### Post by Crusty Old Fart on 2013-08-10
Well, I couldn't figure out a way to solve the leading space and/or underbar problem using only parameter expansion. So, I had to fall back on one of those ugly little sed commands. To compensate for the sed induced ugliness, I made the conditional inside the while loop a little less clunky.

Here's what I ended up with:
```

#!/bin/bash
set -e

echo -e "\nThis will move all files from folders in this, the parent, folder.\nAfterwards the files will be sorted into new folders with any underscores stripped.\nDo you want to continue???\n"
read -p "Press [Enter] to continue or [Ctrl+C] to abort: "

while IFS= read -rd '' i; do
  file=${i#./}
  tmp1=${file//_/ }
  tmp2=${tmp1// /.} 
  tmp3=$(echo "$tmp2" | sed 's/^\.\+//')
  dir=${tmp3%%.*}
  [[ ! -d "$dir" ]] && mkdir "$dir"
  mv "$file" "$dir"
done < <(find . -maxdepth 1 ! -name ${0#./} -type f -print0)

echo -e "\nFor your own safety the script will now make itself unexecutable."
sudo chmod -x 2move.sh

exit 0

```
...and here's some test input you can copy and paste if you want to play around with it:
```

 zzz.space
_zzz.bar
 _zzz.spacebar
_ zzz.barspace
zzz nuttin
yyy.whatnow
yyy what then
xxx.whatnext
xxx whatever
__  _ _ __  what. the hell_   _   
___   __ what .is this

```

Is this fun yet?

Crusty

---

### Post by JohnnyC35 on 2013-08-14
oh my goodness. I can follow it but I'll be darned if I could have come up with anything half that elegant :)
heh

I'll give it a whirl next time I have a chance.

---

### Post by TheFu on 2013-08-14
Are you trying to make these dirs for a specific media center program?  I'm familiar with XBMC and the required (er ... highly suggested) directory structures it likes for TV and Movies.  This doesn't look like it.  Also, there are tools that make that stuff already, though from what I've seen all the extra crap that torrent filenames have breaks it.

Still, a nice script is always appreciated.

---

### Post by JohnnyC35 on 2013-08-14
I've been downloading alot of stuff for awhile but through lack of time and laziness I haven't sorted through the stupid amount of files. We're talking like a couple terabytes of files here. But with the script Crusty has hammered out it at least makes it a bit easier to get everything looked after. I might still have to deal with the stupid "The" directory but everything else is tucked away for the most part that now I can go through and check the duplicates, sort the seasons, etc :)

---

### Post by Crusty Old Fart on 2013-08-15
> **JohnnyC35 said:**
> ...I might still have to deal with the stupid "The" directory...

Maybe not :cool:

The testing that I've done on the following code appears to fix the stupid "The" directory problem.
Note the **[COLOR=#008000]bold green[/COLOR]** lines:
```

#!/bin/bash
set -e

echo -e "\nThis will move all files from folders in this, the parent, folder.\nAfterwards the files will be sorted into new folders with any underscores stripped.\nDo you want to continue???\n"
read -p "Press [Enter] to continue or [Ctrl+C] to abort: "

while IFS= read -rd '' i; do
  file=${i#./}
  tmp1=${file//_/ }
  tmp2=${tmp1// /.} 
  tmp3=$(echo "$tmp2" | sed 's/^\.\+//')
[B][COLOR=#008000]  shopt -s nocasematch
    [[ "$tmp3" =~ ^the\. ]] && tmp3=${tmp3#*.}
  shopt -u nocasematch[/COLOR][/B]
  dir=${tmp3%%.*}
  [[ ! -d "$dir" ]] && mkdir "$dir"
  mv "$file" "$dir"
done < <(find . -maxdepth 1 ! -name ${0#./} -type f -print0)

echo -e "\nFor your own safety the script will now make itself unexecutable."
sudo chmod -x 2move.sh

exit 0

```

Crusty

---

### Post by Bucky Ball on 2013-08-15
*Thread moved to **Programming Talk**.*

I know it's solved already, but will be more help to future travellers here. ;)

---

### Post by Crusty Old Fart on 2013-08-15
Thanks Buck.

---

### Post by Vaphell on 2013-08-15
> **Crusty Old Fart said:**
> Well, I couldn't figure out a way to solve the leading space and/or underbar problem using only parameter expansion. So, I had to fall back on one of those ugly little sed commands. 

extglob to the rescue :)
```
$ shopt -s extglob
$ x='...abc'; y='_ _ _ _ 111'
$ echo "$x => ${x/#+([._ ])/:D }"
...abc => :D abc
$ echo "$y => ${y/#+([._ ])/:D }"
_ _ _ _ 111 => :D 111
```

---

### Post by Crusty Old Fart on 2013-08-15
> **Vaphell said:**
> extglob to the rescue :)

Hot damn! I've been hoping a wizard would jump in here.
Welcome to the thread venerable Sir.
You just rocked my world!
I've been wishing for years that there was a way to inject regex into parameter expansion, but never knew it was possible.
Thank you SO MUCH.

Here you go, Johnny. This bud's for you:
```

#!/bin/bash
shopt -s extglob
set -e

echo -e "\nThis will move all files from folders in this, the parent, folder.\nAfterwards the files will be sorted into new folders with any underscores stripped.\nDo you want to continue???\n"
read -p "Press [Enter] to continue or [Ctrl+C] to abort: "

while IFS= read -rd '' i; do
  file=${i#./}
  tmp=${file//+([_ ])/.}
  tmp=${tmp/#+(\.)/}
  tmp=${tmp/#@(@(THE|The|the)\.)/}
  dir=${tmp%%.*}
  [[ ! -d "$dir" ]] && mkdir "$dir"
  mv "$file" "$dir"
done < <(find . -maxdepth 1 ! -name ${0#./} -type f -print0)

echo -e "\nFor your own safety the script will now make itself unexecutable."
sudo chmod -x $0

exit 0

```

By the way Vaphell, if you run into sisco311 in your forum travels, please wish him well for me.

Thanks again for everything.

All the best to you,

Crusty

---

