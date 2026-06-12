---
title: "Audio pc"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by ZootHornRollo on 2008-04-30
Hi,

I am trying to resurect an old pc to use as a music library for my hifi.  

I have a dell GX520 MT which is currently missing the CPU, DVDRom and HD.  I plan to source the CPU and DVDRom from freecycle or ebay and buy a new 500GB HD. 

Are there any issues with running ubunto linux on an Optiplex GX520, i have seen issues regarding the onboard intel graphics chip, anyone know if this has been resolved?

I will also need a soundcard to provide connectivity to the hifi amp and to improve sound processing.  I was intending to get a soundblaster x/fi card but have since heard that drivers are as yet unavailable.  Any known problems with Audigy SE cards? 

I will also need CD ripping software (FLAC format preffered) and a suitable player.   I have been told EAC is the best ripper but its not available for linux but will run using a windows emulator, as a complete novice linux user, how easy is that to do?  any suggestions for a good quality CD ripper that is compatable with linux?

have i missed anything?  i simply need it to rip and store music and play music to a good standard.  nothing else.

---

### Post by ZootHornRollo on 2008-05-03
bump

---

### Post by billgoldberg on 2008-05-03
I don't know about the hardware compatablitly, but ubuntu has lots of audio rippers that are easy to use.

There is even one installed by default.

The intel set should only have issues running compiz fusion, what you shouldn't be needing.

---

### Post by halitech on 2008-05-03
intel video cards are actually well supported in ubuntu so shouldn't be a problem there. far as the sound card, not sure as I'm just using cheap cards in my systems.

far as ripping audio, Sound juicer is installed by default and does a very nice job and realitivily quick at it. For playback, there are numerous players. If you like winamp, there is xmms which is very similiar, vlc, amarock, rythymbox and numerous others.

where all you want is a music box, you may want to do a minimal install or go with something like Xubuntu which is a little lighter on resources and just add what you need after. If you want something that you can control from other computers and play the music locally, look into Edna ( [http://edna.sourceforge.net/](http://edna.sourceforge.net/) ) as it runs a webserver interface that allows you to stream to any web browser as well.

---

### Post by ZootHornRollo on 2008-05-03
hi,

i just ran ubunto 8.04 from the live disk on my main pc.

have to say i am very impressed, it looks and feels a lot more slick than i was expecting.  

i am wanting to connect the pc to my hifi (using a Behringer UCA202 external soundcard - linux compatable i beleve) and use it as the source and put all my CDs on it in FLAC format.  I just realised this morning that i am going to have to get a  graphics card (probably nvidia fx5500 or similar, needs to be PCI) in order to use the TV as a monitor as, correct me if i'm wrong, the intel onboard graphics doesn't do tv out (think its intel 950 graphics chip).  don't suppose there is any way to control the music player from my XP pc via wi-fi???  bit hopeful, i know!  i suppose i could always install linux on it aswell as a secondary OS if that would make remote control possible?

i am also wanting to network the server with my main xp pc wirelessly. is that possible or do the two OS's not speak to each other? (i have a Sky router - netgear DG834T in disguise)  it would only be to transfer audio files to/from the server and is not essential.

i take your point on xubunto.  seems sensible.

---

### Post by halitech on 2008-05-03
not sure on output to a tv but if all you need to do is move files around, use Terminal server Client and do it remotely then you don't need a monitor or a video card except during initial setup.

You could use the same thing to control it from your XP computer or as I suggested earlier, run Edna and do it from any web browser.

Far as networking, they will but you will need to set up samba to allow it

---

### Post by ZootHornRollo on 2008-05-03
is terminal server client on the windows pc or the linux one?  (or both?)
- sorry i don't know  agreat deal about networking, only had to connnect two XP pcs together over a wifi network before adn that did almost everything automatically.

would VNC be what i'm after?

i had a look at the edna page.  it only talks about .mp3s, not any other file formats so didn't think it would be an option. :confused:  would edna let me remote control the audio pc or play the files on the audio pc on my main (or any!) pc - the audio pc needs to be playing the file via the soundcard.

i'd be glad to be able to set up without a monitor, a few less cables to have trailing about! :)

thanks for taking the time to help :KS

---

### Post by halitech on 2008-05-03
Terminal services clietn would be on a linux computer so yes, VNC would be what you would use on a windows computer to control the linux box. 

Edna will play flac and ogg as far as I can remember, not sure on other formats but it would also be playing them on the remote systems so I guess that wouldn't really be what you are looking for so I think we are back to using VNC and controlling the host system that way.

yeah, a few less cables laying around is always good :)

---

### Post by ZootHornRollo on 2008-05-26
i ended up getting an m-audio audiophile 2496 soundcard. and i cannot get it working...  have tried all sorts of things from these forums to get it working but no success.  have tried another distro of linux (PClinuxOS), again no luck.

so i am going to try the card on my windows machine.  if it works i will probably transfer my windows instalation to the Audio PC and use linux on my main pc.

thinking about how i use my pc - web-browsing, photo editing (i use GIMP in windows) and office apps (i use open office in windows) - linux will suit me.  i haven't played a pc game for over 3 months so i will not miss that side of things.

just need to check my camera wokrs flawlessly with linux and i am good to go.

---

### Post by cariboo on 2008-05-26
Check this out  to get your sound card working:

[http://ubuntuforums.org/showthread.php?t=621768](http://ubuntuforums.org/showthread.php?t=621768)

---

### Post by ZootHornRollo on 2008-05-26
hi,

i ahve tried everything i can find in this forum - i ahve been posting on that thread!

i have now tried the card under xp and still can't get it to output any sound.

verey frustrating.

i think i will be returning the card and will get a behringer UCA202 instead.

---

### Post by ZootHornRollo on 2008-05-27
got it working in XP...  WOO HOO!!1

---

### Post by ZootHornRollo on 2008-06-02
i install ubuntu 7.10, it works fine now.

delighted. :)

just need to go through the laborious task of transfering all my cd's onto the hard drive now. :(

---

