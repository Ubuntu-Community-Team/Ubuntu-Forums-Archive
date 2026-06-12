---
title: "[SOLVED] System Fan Not Coming On"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by lefo on 2008-05-19
New to Linux & Ubuntu.

I have a Compaq Presario SR1200NX Desktop PC w/1.25GB's RAM & a 40 GB HD. I have an ATI Radeon 9550 Graphics card, but other than that, pretty stock stuff.  I'm also using a Viewsonic VA1930wm LCD Monitor.

I've noticed that the System Fan is not coming on.  I installed the hardware sensors mentioned in another post.  I look at the BIOS on start up, and when in BIOS, the System Fan IS running.  Boot into Hardy, no fan.  I cannot see a way to set anything in the BIOS for the fan, and the CPU gets up to 140-150 degrees Fahrenheit.

Does anyone have a suggestion on how to get the fan to trigger?

TIA

lefo

---

### Post by Canis familiaris on 2008-05-19
This is really strange. I've never heard of fans going off while using Ubuntu. I suggest you to take support from HP.

---

### Post by Canis familiaris on 2008-05-19
Is this the problem
[http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg04204.html](http://www.mail-archive.com/linux-acpi@vger.kernel.org/msg04204.html)

Similar thread:
[http://ubuntuforums.org/showthread.php?t=364386](http://ubuntuforums.org/showthread.php?t=364386)

---

### Post by zabien1970 on 2008-05-19
I had a similar problem when I installed gkrellm system monitors, it allows you to control the fan speeds and when I set the temps I set them for Celcious instead of Farenhieght, if you have any monitors or something similar try looking at the settings

---

### Post by Canis familiaris on 2008-05-19
Which version of Ubuntu are you using?

---

### Post by lefo on 2008-05-19
> **Anurag_panda said:**
> Which version of Ubuntu are you using?

Ubuntu Hardy 8.04 Kernel Linux 2.6.24-16-generic GNOME 2.22.1

Haven't found anything that actually allows me to set fan on/off & temp ranges.  I've installed Sensors Applet Preferences.  Good info, but no control.

BTW, fan was working fine in WinXP Pro SP2 before I junked it and went to Ubuntu.

TIA

lefo

---

### Post by lefo on 2008-05-19
I did look at the links provided above, but honestly couldn't determine if any of them pertained to what I was trying to do.

Is there software that actually allows you to control/set the fans?

TIA

lefo

---

### Post by lefo on 2008-05-19
bump?

:confused:

---

### Post by MrKlean on 2008-05-19
For my Acer, I had to install software to get the fans going.  It wasn't in the kernel.  You might want to search like I did..mine were called acer** fan.bz2. Worth a shot !

---

### Post by lefo on 2008-05-20
I found the following in the Compaq.config file in the acpi-support folder.

case "$model" in
	"Armada    E500"*)
		ACPI_SLEEP=true
	;;
        "Evo N600c"*)
                ACPI_SLEEP=true
        ;;
esac 

Um...Is this what I should be looking into/at, and if it is, what if anything needs fixing?

TIA

lefo](*,)]

---

### Post by lefo on 2008-05-20
***bump***

---

### Post by lefo on 2008-05-20
Help?

---

### Post by lefo on 2008-05-20
Okay, have done some digging.  Looking in my ACPI folder, there are a number of things I don't know what to make of.  First, if I look at the Fan folder, there's another Fan folder in it, then a "State" file within that.  If I try to open the "State" file, using gedit, there's nothing in the file.  I've noticed the same exact thing when opening the Thermal_Zones folder and trying to see what if anything might be in the files in that folder.  Nothing.  Does this mean anything?

---

### Post by lefo on 2008-05-20
I'm getting this:

 cat /proc/acpi/thermal_zone/*/trip_points
critical (S5):           100 C
passive:                 -248 C: tc1=4 tc2=3 tsp=60 devices=CPU0 
active[0]:               -266 C: devices= FAN 

does this help in figuring out what's happening?  Also, Fan 1 isn't spinning up at all.  I'm using gkellm tools, and fan1 is at 0, and fan2 is at 2033 (goes a little up and down). Why isn't fan1 coming on?

tia

lefo

---

### Post by GregA on 2008-05-20
What happens if you set the critical (s5): from 100 to 60 C? or 50 C? to see if fan will come on when temp gets up to 140F (btw, 140 to 150 F is not especially hot for most CPU's)

here's another thread of interest.

[http://ubuntuforums.org/showthread.php?t=800348&highlight=PC+Fan](http://ubuntuforums.org/showthread.php?t=800348&highlight=PC+Fan)

---

### Post by lefo on 2008-05-20
> **GregA said:**
> What happens if you set the critical (s5): from 100 to 60 C? or 50 C? to see if fan will come on when temp gets up to 140F (btw, 140 to 150 F is not especially hot for most CPU's)

here's another thread of interest.

[http://ubuntuforums.org/showthread.php?t=800348&highlight=PC+Fan](http://ubuntuforums.org/showthread.php?t=800348&highlight=PC+Fan)

I really hate to show off my ignorance, but here goes...ahem...How do you set the critical (s5) from 100 to 60 C?  Too new to Ubuntu/Linux, but a quick study.

thank you very much for the reply!

lefo

---

### Post by lefo on 2008-05-20
> **lefo said:**
> I really hate to show off my ignorance, but here goes...ahem...How do you set the critical (s5) from 100 to 60 C?  Too new to Ubuntu/Linux, but a quick study.

thank you very much for the reply!

lefo

oh, boy...if I had simply gone to your link first.  Let me see if I can get that to work.

Thanks again!

lefo

---

### Post by lefo on 2008-05-21
I hear a fan!  Thank you so much for your help!  Me and my PC feel a lot better now!

And, if you're so inclined, I've got another issue at:

[http://ubuntuforums.org/showthread.php?t=800649](http://ubuntuforums.org/showthread.php?t=800649)

Regarding my monitor if you want to take a stab at that, too!

lefo

---

