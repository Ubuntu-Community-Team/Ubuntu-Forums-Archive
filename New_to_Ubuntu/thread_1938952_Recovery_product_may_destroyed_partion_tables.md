---
title: "Recovery product may destroyed partion tables"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by stmpjmp on 2012-03-10
Hello (hopefully) new friends.:D

In a long, arduous repair of my old T60 laptop (requiring full disassembly, fan replacement, reseating processor, etc etc) I finally reached the finish line then promptly fell on my face inches short.#-o

During the ibm recovery console, my battery died killing the process. (yeah, ac power should have been plugged in. Live and learn.)Now the HDrive can't boot and my uneducated guess is the partition table is kablooie. My thought was a windows based solution but then I realized...

I'm exhausted with windows (its been nothing but an anchor w/my thinkpad)

So I'm going ubuntu/linux and starting with this very repair (all linux based tools too). I'm hope somebody has suggestions as to how I might repair the hd partition table enough so I can boot into recovery one last time, make the windows backup discs (in case I give it away to family later) and say so long. I've got partitions all over the drive. As far as I am concerned their deaths are evolution at work (adapt or die!) I feel I must save that recovery partition so I can make emergency discs then I can finally put windows in my rearview ):P

Thanks for any help. I'm happy to post any info, screenshots,etc needed just will need a little help in knowing how I do so.

Again. Thanks so much. :D

Mike

P.s. Oh and any thoughts suggestions in general are helpful too. I'm very new to it all so caveats are invaluable.

---

### Post by Mark Phelps on 2012-03-10
I've heard that Testdisk (Linux app) can restore damaged partitions -- but I've not personally had success using it.

If you have access to a Windows PC, you could try downloading and burning the FREE image of Partion Wizard -- and booting from that.  It might have an option for repairing or restoring the damaged Windows partition.

Once you get that working, instead of messing around creating recovery optical media, I would suggest the following:
1) Download and install (in MS Windows) the FREE version of Macrium Reflect (MR)
2) Image off the Windows install to an external drive
3) Use the MR option to create and burn a Linux Boot CD

NOW, you have a way of restoring MS Windows to the state it is in -- without losing data or applications.

---

### Post by stmpjmp on 2012-03-10
> **Mark Phelps said:**
> I've heard that Testdisk (Linux app) can restore damaged partitions -- but I've not personally had success using it.

If you have access to a Windows PC, you could try downloading and burning the FREE image of Partion Wizard -- and booting from that.  It might have an option for repairing or restoring the damaged Windows partition.

Once you get that working, instead of messing around creating recovery optical media, I would suggest the following:
1) Download and install (in MS Windows) the FREE version of Macrium Reflect (MR)
2) Image off the Windows install to an external drive
3) Use the MR option to create and burn a Linux Boot CD

NOW, you have a way of restoring MS Windows to the state it is in -- without losing data or applications.

AHA! Testdisk! Thats the name of the program I couldnt remember. Reaching it shortly.

Yes I can get access to a Win PC (xp pro) in a pinch if needed. Open to all tools really, just using this mess as a springboard to linux (I need a kick in the pants sometimes)

Macrium Reflect seems interesting and Ill need to add that to my toolkit. As far as the windows that is on there, the programs there are no great loss and I have a feeling the actual install in probably quite a mess. Probably would just as well start fresh if I go back to the Micro side.

It is however perfect for another non linux issue I was having w/sis computer so thanks so much for fixing a problem you didnt even know I had!

Keep the suggestions coming everyone. I'm eager to learn learn learn!

---

### Post by gordintoronto on 2012-03-10
Once you are finished with Windows, you should spend a little time figuring out which version of Linux has the most appeal for you. I suggest you look at the latest Ubuntu, Kubuntu and Linux Mint.

I recommend this site: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

From Windows, it can help you make a bootable flash drive containing whatever version of Linux you would like to try.

---

### Post by stmpjmp on 2012-03-11
> **gordintoronto said:**
> Once you are finished with Windows, you should spend a little time figuring out which version of Linux has the most appeal for you. I suggest you look at the latest Ubuntu, Kubuntu and Linux Mint.

I recommend this site: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

From Windows, it can help you make a bootable flash drive containing whatever version of Linux you would like to try.

Thanks. Running ubuntu off a pendrive'd SD card now thanks to you :D It's killing me to be ON and USING the laptop again (FINALLY!) but not have the whole issue "settled" yet. But pleased to know all my hardware fixes were a-ok.

Kubuntu is my next go as Ive heard middling things of Mint.

Back to my partition problem, I'm using the search function hard to d.i.y. it. Running out of steam and confidence now so will turn in and fight the good fight along side you gentleman tomorrow. Thanks again all!

---

### Post by stmpjmp on 2012-03-14
Ugh this thing is really kicking my butt... :frown:

Tried clonezilla and it seems my external harddrive had a devil of a time being seen. Shows up within seconds IN ubuntu but 'zilla shows little to no love. :confused:

Fudged up my boot order in bios when I had the reinstall into the laptop (for my zilla cloning) Oddest behavior... it showed all the various OS it wasnt showing before (the ubuntu, the XP Win and (what I assume) is the recovery partition. Just to see if it would go I went for the XP install, no AUTOCHECK error then BSofDeath (I have not missed thoses since going to usb Ubu)

A recovery console (the unknown Win NT/2000 parition) try seems to sit at "starting" on a black screen.

Used a grub2 boot disk cd to see what it might show.... just the Ubuntu and a recovery Ubuntu (so it called it)

Im terribly baffled now, not even a clue in which direction I should head. Windows sure is going out with a bang and not a whimper for me (kicking and screaming no less) ](*,)

Any thoughts gentlemen (and or ladies?) I'm :confused:

---

