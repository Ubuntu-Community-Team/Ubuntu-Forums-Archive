---
title: "no sound in ubuntu 9.10"
date: 2009-10-03
forum: Philippine Team
---

### Post by sixrodriguez on 2009-10-03
waaaaaaaaaaaa!!!

help guys,

walang audio  after upgrading jaunty to karmic......

thank you po!! :(

---

### Post by loell on 2009-10-03
your audio's make and model is?

---

### Post by sixrodriguez on 2009-10-03
> **loell said:**
> your audio's make and model is?
  

sir loell paano malalaman audio and model?

---

### Post by loell on 2009-10-03
from the output of **sudo lshw**

---

### Post by sixrodriguez on 2009-10-03
six                       
    description: Desktop Computer
    product: P4M900T-M2
    vendor: ECS
    
  *-multimedia
          description: Audio device
          product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)
          vendor: VIA Technologies, Inc.
          physical id: 1
          bus info: pci@0000:80:01.0
          version: 10
          width: 64 bits
          clock: 33MHz
          capabilities: pm msi pciexpress bus_master cap_list
          configuration: driver=HDA Intel latency=0
          resources: irq:17 memory:febfc000-febfffff

---

### Post by loell on 2009-10-04
check  your volume control and see if it's just muted, apparently there are a couple of these cases with this sound device, when they upgrade their installation.

---

### Post by sixrodriguez on 2009-10-04
thank you sir loell.........

siguro balik muna ako ng jaunty.........

medyo madami ata akong haharapin sa karmic.....

excited lang siguro ako.........

ang ganda na kasi ng karmic........

dami ko lang din na experience na problema........

may audio pero static.....

sa wine naman ang hirap na mag install laging may error......

na-experience ko din po na medyo bumagal internet coonection ko, tinawag ko pa sa hotline ng provider namin, nung a-assist na ako ng operator then nalaman nya na ubuntu gamit ko, sabi nalang nya gawa na lang daw nya ako ng report (:P toinks!!! wehehe)

so far naman po sa ubuntu jaunty jackalope ok na po sa akin

YM nalang po talaga ang kailangan ko, sana lang before ma-release karmic my available narin YM messenger  ang Yahoo sa Ubuntu

more power Ubuntu Ph!!!!!!!!!!

---

### Post by loell on 2009-10-04
or try karmic on a livecd when it's finally out, kung may sound, then clean install ka na lang.

> sana lang before ma-release karmic my available narin YM messenger ang Yahoo sa Ubuntu 

wag ka ng umasa sa yahoo na mag release ng updated official port ng YM sa linux. :(  , ilang dekada na rin in computer years na hindi sila nag paparamdam sa area na yan.  third party  na lang talaga ang maa-asahan mo (pidgin, kopete, gyachi).

---

### Post by sixrodriguez on 2009-10-04
sir loell ano ba issue or agreement meron ang yahoo sa ubuntu/linux?.........

bakit sa ubuntu/linux lang walang YM?........

sa Mac and Windows may available sila.........

curious lang po....

---

### Post by loell on 2009-10-04
> **sixrodriguez said:**
> sir loell ano ba issue or agreement meron ang yahoo sa ubuntu/linux?.........



actually walang agreement.

> **sixrodriguez said:**
> 
bakit sa ubuntu/linux lang walang YM?........
sa Mac and Windows may available sila.........
curious lang po....


on it's early days meron, [YM Linux - old]("http://linux.softpedia.com/get/Communications/Chat/Yahoo-Messenger-2.shtml"), nag stop, kesyo maliit daw siguro ang market share, sayang  daw siguro ang development effort kung magkaganon.

kung mapapansin mo konti lang ang naghahanap ng YM for linux, kasi naman, napakarami na ng alternative, merong skype for linux, googletalk  with empathy, may ibat ibang soft-phone, at yun nga dadagdagan pa sa third party, kaya ayun, mas naging irrelevant na sya sa pag lipas ng panahon.

---

### Post by sixrodriguez on 2009-10-04
thank you po sa information......

more power Ubuntu Ph!!!!!!!!

---

### Post by Laibcoms on 2009-10-07
Yep, it seems that Karmic is the indeed the beginning of a new cycle of "breakages" :p  Which is great actually, because it only means that they're putting in plenty of new stuff.

Jaunty was too perfect to break ;)  I can't wait for 10.04LTS and 10.10, pretty exciting reports so far.  But back to Karmic, well, still downloading the LiveCD since the Alternate CD failed to detect my SATA.  Hopefully the LiveCD will.

---

### Post by sixrodriguez on 2009-11-11
help guys........

dati lang sa 9.10 walang audio.........

now naman sa 9.10 ulit mahina audio......

full na po lahat ng volume.......

sa 9.04 naman po ok yung audio.....

and bakit po yung 9.04 alsa driver yung default......

bakit po sa 9,10 azalia na po with the same board im using..........

and clean install po now sa 9.10

please help po.....

salamat in advance......

Mabuhay Ubuntu Ph!!!

---

### Post by EIxIO on 2009-11-11
same thing no audio fresh copy of karmic hehe :p
dko pa ata na install audio drivers.. waaaa

---

### Post by sixrodriguez on 2009-11-11
> **EIxIO said:**
> same thing no audio fresh copy of karmic hehe :p
dko pa ata na install audio drivers.. waaaa

alam ko sir i-update lang ung update manager ok na....

katulad sa 9.04 update lang install na lahat ng motherboard support.........

kaso mahina parin yung audio ko sa 9.10........

---

### Post by loell on 2009-11-11
anong sound module ang ginamit ng ubuntu?
output ng,
**lsmod**

---

### Post by sixrodriguez on 2009-11-11
> **loell said:**
> anong sound module ang ginamit ng ubuntu?
output ng,
**lsmod**

sir loell eto po......

sixrodriguez@sixrodriguez:~$ lsmod
Module                  Size  Used by
isofs                  31620  1 
udf                    80900  0 
crc_itu_t               1852  1 udf
cbc                     3516  49 
aes_i586                8124  50 
aes_generic            27484  1 aes_i586
ecb                     2524  1 
via                    40192  0 
drm                   159584  1 via
binfmt_misc             8356  1 
vboxnetadp             79976  0 
vboxnetflt             86568  0 
vboxdrv               122792  2 vboxnetflt
snd_hda_codec_via      28988  1 
snd_hda_intel          26920  0 
snd_hda_codec          75708  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  11 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
ppdev                   6688  0 
lp                      8964  0 
parport_pc             31940  1 
parport                35340  3 ppdev,lp,parport_pc
dm_crypt               12928  0 
psmouse                56180  0 
iptable_filter          3100  0 
serio_raw               5280  0 
i2c_viapro              7312  0 
shpchp                 32272  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
via_rhine              22212  0 
usbhid                 38208  0 
mii                     5212  1 via_rhine
sata_via                9184  2 
via_agp                 7932  1 
agpgart                34988  2 drm,via_agp
sixrodriguez@sixrodriguez:~$

---

### Post by loell on 2009-11-11
try the suggestions in this thread, such as removing pulse config, headphone unmute?, and some others.

[http://ubuntuforums.org/showthread.php?t=1243064]("http://ubuntuforums.org/showthread.php?t=1243064")

---

### Post by sixrodriguez on 2009-11-11
> **loell said:**
> try the suggestions in this thread, such as removing pulse config, headphone unmute?, and some others.

[http://ubuntuforums.org/showthread.php?t=1243064](http://ubuntuforums.org/showthread.php?t=1243064)

sir loell ok na po yung audio ko malakas na po siya........

ang problema naman po nagstatic yung sound pag play ako ng music sa player...

please help po.......

salamat in advance....

Mabuhay Ubuntu Ph!!!!

---

### Post by loell on 2009-11-11
ano yung "nagstatic" na sound?

---

### Post by sixrodriguez on 2009-11-11
> **loell said:**
> ano yung "nagstatic" na sound?

pag volume ko yung music nag static scratch po yung music......

hindi naman po siya ganon dati sa 9.04.......

pag flash naman ang sound wala naman problema......

---

### Post by loell on 2009-11-11
di naman kaya corrupted yung audio file? sa ibang player kaya anong resulta?

---

### Post by sixrodriguez on 2009-11-11
> **loell said:**
> di naman kaya corrupted yung audio file? sa ibang player kaya anong resulta?

sir loell maraming salamat po sa mga links.....

need ko lang siguro ng graphic equalizer or other music enhancement......

maraming salamat po ulit sir loell....

Mabuhay Ubuntu Ph!!!

---

### Post by loell on 2009-11-11
no probs.. :)

---

### Post by Lila_IT_CMU on 2009-11-13
ako po wla rin sound...nung pag install ko meron pa syang sound pero after pag restart ko wala na....ano po ba nangyari? kahit anong gagawin ko walang sound eh... help po plsss

---

### Post by chitx2000 on 2009-11-13
I also installed karmic lately on HP Mini 1137NR and had some issues with the sound but right after upgrading the alsa version to Alsa 1.0.21 everything works from skype calls using external mic, videos (VLC) and music (Rhythmn Box). Here's the link on how to [upgrade Alsa]("http://monespaceperso.org/blog-en/2009/10/29/upgrade-alsa-1-0-21-on-ubuntu-karmic-koala-9-10/").

---

### Post by eeeris on 2009-11-13
Mga sir....newbie po ako ng ubuntu, thru browsing sa ubuntu.com ko lang natutunan install ubuntu sa Eee pc 1000HA ko..the only problem lang po eh..ayaw magplay ng mga mp3s ko sa rhytmn box..nalaman ko na kelangan ko pala install ung ubuntu-restricted-extras, unfortunately, wala internet connection ung netbook ko. Tanong po, POSSIBLE po ba na idownload (thru my desktop pc w/Winxp) ko un , then install manually sa netbook ko? 

thank you very much...;)

---

### Post by Lila_IT_CMU on 2009-11-14
> **eeeris said:**
> Mga sir....newbie po ako ng ubuntu, thru browsing sa ubuntu.com ko lang natutunan install ubuntu sa Eee pc 1000HA ko..the only problem lang po eh..ayaw magplay ng mga mp3s ko sa rhytmn box..nalaman ko na kelangan ko pala install ung ubuntu-restricted-extras, unfortunately, wala internet connection ung netbook ko. Tanong po, POSSIBLE po ba na idownload (thru my desktop pc w/Winxp) ko un , then install manually sa netbook ko? 

thank you very much...;)

nku, mahihirapan ka lng tol. naranasan ko na yan manual download tapos wala nangyari.. wala kaba kahit wifi lng? pinagtyagaan ko na lng ung wifi para maka download ako ng mga kailangan na packages

---

### Post by jaceleon on 2009-11-14
In ALSA GNOME equalizer, PCM ang controller ng treble, so adjust it to your taste, also adjust LCM, affecting yun sa mga scratchy sounds at atatic sounds sa background ng mga audio.

---

### Post by jaceleon on 2009-11-15
> **loell said:**
> actually walang agreement.



on it's early days meron, [YM Linux - old]("http://linux.softpedia.com/get/Communications/Chat/Yahoo-Messenger-2.shtml"), nag stop, kesyo maliit daw siguro ang market share, sayang  daw siguro ang development effort kung magkaganon.

kung mapapansin mo konti lang ang naghahanap ng YM for linux, kasi naman, napakarami na ng alternative, merong skype for linux, googletalk  with empathy, may ibat ibang soft-phone, at yun nga dadagdagan pa sa third party, kaya ayun, mas naging irrelevant na sya sa pag lipas ng panahon.

Alam ko medyo baka ma out of topic ako no, pero about yahoo, you could always try this [website]("http://webmessenger.yahoo.com") (click mo lang po). That is the website of yahoo! messenger website version. I normally use this kasi at least direct connect siya sa yahoo, at mas mabilis mag-login kesa sa mga 3rd party software na connecting din sa YM like Pidgin.

---

### Post by sixrodriguez on 2009-11-16
> **jaceleon said:**
> In ALSA GNOME equalizer, PCM ang controller ng treble, so adjust it to your taste, also adjust LCM, affecting yun sa mga scratchy sounds at atatic sounds sa background ng mga audio.

wow galing...

salamat ok na po yung sound ko.....

Mabuhay Ubuntu Ph!!!

---

