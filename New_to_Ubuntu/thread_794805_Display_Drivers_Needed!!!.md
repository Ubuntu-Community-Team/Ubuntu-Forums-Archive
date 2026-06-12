---
title: "Display Drivers Needed!!!"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Etheredge on 2008-05-15
Alright long story short im having a battle with playin wow in wine

testing out the updating of my graphics drivers 

GM965/GL960 integrated graphics controller is all the info i have on it

Also i used EnvyNG to try and update the drivers but it was unable to detect any drivers what so ever ati or nvidia

need some help!

---

### Post by HotShotDJ on 2008-05-15
> **Etheredge said:**
> GM965/GL960 integrated graphics controller is all the info i have on itIntel's integrated graphics chipsets do not require proprietary drivers.  The open source drivers are already included as part of Ubuntu.

I am not familiar with WoW or any other type of gaming, for that matter.  But keep in mind that the Intel integrated graphics controllers are NOT high-end gaming video cards.  They are inexpensive, general purpose "cards."

EDIT:  Well, they aren't cards at all... but that's beside the point.  You get my meaning. :)

---

### Post by Etheredge on 2008-05-15
ya see thats the thing.....

i played wow just fine on this laptop with vista but its a no go for wine

its a toshiba satallite a2054777 

which also has an ati card inside but i cant seem to find a way to locate it. 
the drivers off the toshiba site show the ati display driver so it is there

does this help?

---

### Post by MaindotC on 2008-05-15
If you have an ATI card you can use proprietary drivers to operate it.  I'm not sure how to select one video card over another in Ubuntu, but you should have an option in System -> Administration -> Restricted Drivers Manager.  Can you select that and see if it detects your ATI card?

---

### Post by Etheredge on 2008-05-15
there is no restricted drivers manager from what i can tell. only hardware drivers and when i select that there is nothing on the list at all.

---

### Post by Victormd on 2008-05-15
> **Etheredge said:**
> ya see thats the thing.....

i played wow just fine on this laptop with vista but its a no go for wine

its a toshiba satallite a2054777 

which also has an ati card inside but i cant seem to find a way to locate it. 
the drivers off the toshiba site show the ati display driver so it is there

does this help?

The laptop has both cards? Have you checked your BIOS to see which one is enabled?
> there is no restricted drivers manager from what i can tell. only hardware drivers and when i select that there is nothing on the list at all.
Restricted driver is a term from Gutsy, that is under Hardware Driver in Hardy...

---

### Post by HotShotDJ on 2008-05-15
> **Etheredge said:**
> which also has an ati card inside but i cant seem to find a way to locate it. 
the drivers off the toshiba site show the ati display driver so it is there

does this help?Those number -- GM965/GL960 -- are Intel model numbers.  So, if I understand you correctly, you are saying you have both an integrated intel video controller AND a discrete video card, probably some type of ATI?  Please verify this information and post back.  Also, from a terminal (Applications --> Accessories --> Terminal) please type the following and post the output:```
lspci | grep VGA
```

---

### Post by Etheredge on 2008-05-15
etheredge@etheredge-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
etheredge@etheredge-laptop:~$

---

### Post by MaindotC on 2008-05-15
The only pages I can find related to this product are in Spanish.

---

### Post by HotShotDJ on 2008-05-15
> **Etheredge said:**
> etheredge@etheredge-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
etheredge@etheredge-laptop:~$Ok.  If you are absolutely sure that there is an other video card, you'll need to go into your BIOS (check your Toshiba user manual... different laptops use different keystrokes to accomplish this) and make sure that the Intel card is DISABLED and that the ATI card is ENABLED (although the ATI card may not show up in the BIOS ... I'm not sure about your particular configuration)

After that, Ubuntu should detect the ATI card, and then you'll be able to use the Hardware Drivers application to install the proprietary drivers, if needed.

---

### Post by Etheredge on 2008-05-15
should hardware drivers actually show me the drivers on my computer?

---

### Post by MaindotC on 2008-05-15
If you can get an updated BIOS can you try installing that?  It will probably be a windows binary so you'll have to do it in a windows partition or I've had a lot of success advising people to do it in Virtualbox.

---

### Post by Xiong Chiamiov on 2008-05-15
> **Etheredge said:**
> 
i played wow just fine on this laptop with vista but its a no go for wine


Wine is not a replacement for Windows.  Some things work really well (I could never get Starcraft working right in XP, but it runs flawlessly in wine), some pretty good (Guild Wars with a few pixel-shader tweaks and proprietary NVIDIA drivers) and others (most) not at all, or terribly.  Don't expect it to deliver the same kind of performance as Windows does.

---

### Post by Etheredge on 2008-05-15
bah this is a headache.... all for wow.....

i dont understand why im not able to see any drivers tho

i have to update my bios?

and i checked for the option to switch from intel to ati and there was none as far as i could see in the bios

---

### Post by Xiong Chiamiov on 2008-05-15
Are you absolutely sure that you have a video card in this system?  Just because there are drivers for it doesn't mean you do, as some are available with different configurations.

---

### Post by HotShotDJ on 2008-05-15
> **Etheredge said:**
> should hardware drivers actually show me the drivers on my computer?No.  The name of that application is a misnomer.  It only shows hardware that requires proprietary drivers, such as ATI and NVidia cards.

---

### Post by HotShotDJ on 2008-05-15
> **Etheredge said:**
> and i checked for the option to switch from intel to ati and there was none as far as i could see in the biosOk.  I REALLY doubt that you have an other video card in that laptop.  I think Xiong Chiamiov's comments are most applicable to your problem.

---

### Post by Etheredge on 2008-05-15
so its just a matter of how its set up for the most part?

ive heard numerous reports of wow runing fine

---

### Post by PmDematagoda on 2008-05-15
Are you sure that you have an ATi card? Because the specifications of the laptop say that there is an Intel VGA card but none of them mention the presence of an ATi card. So unless you manually put in an ATi card(which would be difficult since the VGA cards of laptops usually cannot be easily changed), it is impossible to be having an ATi card.

---

### Post by MaindotC on 2008-05-15
If you do:
```

man lspci

```
It tells you that there's a PCI device connected to your motherboard, which there should be if it's an ATI card, the lspci command should show it.  You may not have drivers for it, which is the software that helps the kernel interact with the device in an electrical sense, but it should at least be detected with the lspci command.  From your output, I'm not seeing an ATI card so I'm questioning if it's really in there.

---

### Post by HotShotDJ on 2008-05-15
> **Etheredge said:**
> so its just a matter of how its set up for the most part?

ive heard numerous reports of wow runing fineGive this web page a try: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Perhaps something there will get things fixed up for you.  There are some instructions under the heading of "Configuration" that look like they may apply to what you are experiencing.

---

### Post by Xiong Chiamiov on 2008-05-15
> **Etheredge said:**
> so its just a matter of how its set up for the most part?

ive heard numerous reports of wow runing fine
First, you should always take a look at the [Wine AppDB]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9429").  There are lots of user comments and stuff on how to get it working.

Second,... ah gosh darnit, I forgot what was 2nd.

---

### Post by Victormd on 2008-05-17
I have to agree with PmDematagoda, I find it very unlikely that you would have 2 video cards in a laptop so I would review that very closely.

On the WOW note, I've used it with no problems under WINE. However, I also used wine-tools to install some "core windows drivers" that facilitate this.

---

