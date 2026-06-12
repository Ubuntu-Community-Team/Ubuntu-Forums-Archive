---
title: "HP PSC Photosmart All-in-one 2510 and 10.04.03 LTS Desktop"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by SheaMan on 2011-11-16
Links I have found regarding this problem.

[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html) - useful
[http://ubuntuforums.org/showthread.php?t=1727811&highlight=photosmart+2510](http://ubuntuforums.org/showthread.php?t=1727811&highlight=photosmart+2510) - similar..
[https://bugs.launchpad.net/hplip/+bug/877793](https://bugs.launchpad.net/hplip/+bug/877793) - ;) incomprehensible..to me :D

So, I installed teh LTS buntu, and everything seems fine, pop in the usb wifi stick - good, plug in the printer ..... and ..... :phthbbt: either |I| R total newb fail, or ..idk. I am used to WinXP freaking out whenever you plug something into a USB slot, but that is not happening here on this new buntu. Am I missing obvious step one or am I facing a real problem here?

In the process I have turned on the HP PSC Photosmart 2510's wireless radio on the hp itself ( but I don't know how to detect it ) and I have run 'dpkg -l hplip' in the terminal.. and.. 'hp-check -t' - a screenshot of the terminal results is attached to this message. I will not be surprised if this is a pebkac error ( ..but.. I am not sitting in a *chair* - smirk ) umm.. also - I am doing this configuration for a family member. They actually had Ubuntu installed before, but the inability to use this specific printer with the system was the reason they went back to windows. They obviously didn't ask ya'll for help ;)

---

### Post by Miljet on 2011-11-16
I'm not familiar with that particular printer, but normal procedure is to plug in USB cable, make sure printer is turned on, go to System -> Administration -> Printers, click on "Add new printer", and let Ubuntu find the printer and install the drivers. The only thing left is to print a test page to make sure everything worked.

---

### Post by SheaMan on 2011-11-16
Either I am doing something wrong or this model is not being autodetected. 

screenshots attached to post. I choose 'system > administration > printing = printing.png
clicking the +add button = new.png ..... next click? :oops: I feel so newb.. :oops:

---

### Post by Mark Phelps on 2011-11-16
HOW are you trying to connect to the HP?  You mention turning on the wireless, but doesn't this one also come with a network jack?

I have an HO 8510 and it was auto-detected by CUPS -- which made it very easy to install.  But, I have it connected via wired network cable to a router.

If you want to try that, plug a network cable into your home router and into the HP, boot into Ubuntu, open a browser and enter "localhost:631".  That will launch CUPS.

Then, select the option Manage Printers and see if there is a listing for your HP.  If not, select the option to Add a Printer.  Your HP should be listed on the page as being detected.

---

### Post by SheaMan on 2011-11-16
:morn: I would have to leave the house to do that, :smirk: but it is plugged in with the USB. That would normally work automatically right? Just like [COLOR=Red]Miljet [COLOR=Black]said.. add~autodetect~confirm? :sing: I am going to look ..well.. thats an obvious answer :yeesh: 

*Terminal* ( I gotta turn the voice command deal on ) 

oh yeah - test Ubuntu and Zynga - Lessee G+/Cityville seems the stabelist, Farmville is always being worked over. The layering on frickin .. blasted.. Frontierville is bunked and I mean how! I am nervous that it will not even display at all - which would mean that there would be no sleak~buntu podcast ( webshow, podcasts are radio - screencast? but its only the game..and some intro outro face time ..whatever) 
:popcorn: fyi[/COLOR]
[/COLOR]

---

### Post by SheaMan on 2011-11-16
So I am trying to use terminal to access this HPLIP thing and it has no man thing. Poked around online and found this page

[http://hplipopensource.com/node/309](http://hplipopensource.com/node/309)

So it says something ( and seeing as I only quite follow half of each sentance.. ) about some sort of plugin that may or may not be installed - gives the command

```

hp-setup

```This did not work. Image attached (GUI). 

```

hp-setup -i 

```Interactive mode? Choose USB, :zorch: Image (USB)

This one launches a GUI?

```

hp-setup --qt3

```No.. that must be gt3? (qt3)

```

hp-setup --gt3

```nope..why would it tell me to use that flag in the first error if that flag does nothing?

This is supposed to run the GUI mode that is supposed to run by default. 

```

hp-setup -u

```same problem - googled "hp-setup requires GUI support" and got
[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne) :read:
:aha: ' you need to execute sudo apt-get install python-qt4 in a terminal before running hp-setup'

```

sudo apt-get install python-qt4

```were doing ..something.. and were back to @. 

I ..am going to try rebooting..or..hmm.... I'll turn off the printer and turn it back on.. no autodetect. Well.. 

```

hp-setup

```Yay! Window! Choose USB..nothing appears in the list..

Okeee.. I try unplugging and and replugging the USB into all the different USB ports and refreshing the list. Nothing.

I find a spare ethernet cord and try using that - still nothing. 

:grumble:

Lets play around somewhere I know better. Plug the Photosmart in to windows via USB - no autodetect..what is wrong with this mutant?

Add new printer - search - nothing..whu?

Lord, 344 megs worth of driver..what does this thing do? The dishes?

This is going to take a minute..

---

### Post by SheaMan on 2011-11-17
:guitar: aA~aand when I run the install package for it on WinXP, nuthin :lolflag:
what is wrong with this thing - I am going to try these other printers.. :popcorn:


[list]
[*]HP Officejet 5510 aio
[*]Epson Stylus Photo RX595
[*]aaand (of course) HP Photosmart 2510 aio
[/list]


:rolleyes: wait..updates! :reboot:

---

### Post by SheaMan on 2011-11-18
:yeeha: Aha! The EPSON ..just.. worked. SO POOP on HP ( ahehe, **P**resume **O**utside **O**rigination of **P**roblem ). 
:smirk:
The other HP doesnt get recognized either.. wonder why, think its time to click the contact button. Lessee what HP's Linux suppt. dept. has to say about the matter :hrmph:

---

### Post by SheaMan on 2011-11-20
No response from HP yet. Guess I will monkey with other stuff..

hmm...interesting :popcorn:

 [http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1540-top-things-to-do-after-installing-ubuntu-1104-natty-narwhal)

---

