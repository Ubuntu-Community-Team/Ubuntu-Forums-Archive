---
title: "problems booting -up dell"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by afhx on 2012-03-07
I have posted a previous thread but discontinued it when the problem resolved itself. I have a dell inspiron 530 desktop. The problem is as follows. I boot up , the computer comes on, the monitor comes on, then the monitor goes off, the computer goes off , then the cycle repeats itself. If and when I reach the stage when I can enter set-up or the boot-up menu, then generally things proceed okay. However, pass this stage lately , it has gone back into  the cycle. I only have ubuntu install; this is not a dual boot problem.Things I have done to resolve this problem.Read all the ubuntu literature I could find,per the suggestion when I previously posted this thread,,but found no clue as to the cause. Ran the dell utility to check the hardware, and particularly the hard drive, but found no problems. Tried Boot-Repair. Backed-up and reinstall 10-4. Then installed 11-10.I managed to read a message from dell which read:
Alert Previous attempts at booting this system have failed at checkpoint 50.The computer failed to complete the boot routine on three consecutive times for the same error.
I contacted dell but no one could tell me what it meant ; the advice given was to run the dell utility disc.
I searched on line for the above error and the suggestion it was a CMOS error due to a faulty battery. Even though the date was still accurate, I changed the battery on the mother board. On boot-up. the same problem occurred, then proceeded to a successful boot-up. I should mention that after the re-installation, but before the battery change, the computer booted up successfully with no problems on fifteen occasions.
Please help if you can

---

### Post by s.fox on 2012-03-07
Thread moved to [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326")

---

### Post by afhx on 2012-03-15
Changing the battery did not work

---

### Post by gordintoronto on 2012-03-15
It's hardware. Unplug and re-plug cables, RAM, etc. It appears that the computer works once it warms up, which often means a connector is not making good contact.

---

### Post by afhx on 2012-03-16
I  have checked the connections. However, for a double-check I  have restarted in the past after the computer have been on for at least 2 hours. Sometimes, the problem still occurs. Unfortunately, I did not keep a full record of the bios: I am trying booting -up from the defaults which , with two exceptions, is the same as previous config: the changes are that the dell service tag no longer is shown and errors have changed from ALL to ALL except keyboard.Thanks for the response. It is appalling that you give a very specific error message to dell technical support and you have to pay premium rates for someone who does not know the answer.

---

### Post by BHEJU on 2012-03-16
I think first you should try to flash BIOS (even if you have the latest version installed). And then chip-set drivers as well.
However,_ this process is already risky in itself but with battery in question, makes it even more risky._

But, I am suggesting this after exp. I had an HP pav which was behaving much like your machine. I flashed bios an chipset drivers and it worked for me.
 
Cheers,

---

### Post by gordintoronto on 2012-03-16
> **afhx said:**
> Thanks for the response. It is appalling that you give a very specific error message to dell technical support and you have to pay premium rates for someone who does not know the answer.

You didn't post in the Dell forum. I don't work for Dell, I'm just trying to help you.

---

### Post by afhx on 2012-03-19
With the default bios, the computer has booted up eleven times without error. Hope it continues( after I changed the bios, the computer took about ten minutes to boot, but since then it been fine.I let the forum know in a couple of weeks if things continue okay because it might prove helpful to someone else.(Surprised that when I searched for the error string that a google search revealed my query to the forum.

---

### Post by RJARRRPCGP on 2012-04-03
And the BIOS on some Dell PCs sometimes falsely reports a failure at a checkpoint. 

Usually, it's when the BIOS thinks something's wrong, because of shutting it off or rebooting it when the BIOS is in a pre-OS-boot stage.

(And on some Asus boards, that can cause a false "System failed due to CPU overclocking" (or similar) error message.)

---

### Post by afhx on 2012-05-02
As promised, here is the feedback in case it is of use to other members.
Recap: after the bios was changed to the defaults, the computer took about ten minutes to boot with the recurrence of the problem. Since then the computer has booted up successfully without any problems  86 times and 5 with problems.
Details:
20 consecutive successful boot-ups
blimp -monitor came on and then turned off before booting up with no further problems
11 consecutive successful boot-ups
blimp - monitor on, then off. Then grub menu  appears followed by successful boot-up
7 consecutive successful boot-ups
Recurrence of problem with dell message
ditto
Booted from grub menu, then saved defaults to CMOS again
14 consecutive successful boot-ups
dell error
34 successful boot-ups
In the original dell manual which I downloaded whern I purchased the computer (Inspiron 530) there was  just the instruction to contact dell when this error message appeared. In the latest copy  its states( no particular error number given):
      A CMOS CHECKSUM error or checkpoint error
      Causes: battery may not be functioning properly
                  BIOS was recently updated
Well I have covered these possibilities (The bios was definitely not altered when the problem first occurred)
This problem occurs in the dell forums. Yet to see the problem answered successfully.
Doing a search on Dell Support Site directs you to manual given above.
This raises several questions. Why the sudden relapse to the the dell message?
If this occurs again, I may extend  Gordintoronto suggestions and also check for  a bad connection. Since I am unwilling  to pay for a professional computer engineer to 
examine the computer I will probably save up for a lap-top and improve my competence in hardware trouble-shooting. I  really don't want to  install 12-4 and re-install all my backups knowing that  there is a good chance that I might be unable to boot-up in the future.

---

### Post by Shazaam on 2012-05-02
It sounds like you may have a failing motherboard. A few things...

1. I have had new-on-the-rack batteries turn out to be DOA.
2. Get a flashlight and look at the capacitors on the motherboard. Do any of them have tops that are bulging? Are there any deposits around the capacitor bases? This is rare on newer motherboards but it can still happen.
3. Did your pc suffer a power outage/fluctuation caused by lightning (or other things)?
4. As stated before, recheck all of the connections on the motherboard, especially the 20/24 pin plug(s).
5. If you have access to one, try swapping out the power supply with a known good one.

---

### Post by afhx on 2012-06-25
It seems that I have been making a VERY  SILLY  mistake. The battery did  need changing. I found no fault with the hardware(spent many days looking ). What I did wrong was this:
When changing the BIOS to the defaults and then saving a message comes up with a flashing y. I assumed that pressing ENTER was sufficient. What I should have done was press y then ENTER.  .Anyway, thanks to those whose tried to help and apologies .

---

