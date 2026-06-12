---
title: "Time displayed on desktop is 6 hours ahead of the time I set."
date: 2008-09-13
forum: New to Ubuntu
---

### Post by drcdebaca on 2008-09-13
As stated above the time that is displayed on my desktop in the upper right hand corner is 6 hours ahead of the time I have set in Time and Date Settings.  This only occurs when I am the user and if I adjust the Time and Date Setting to compensate for the shift every others user's time will be off.  What did I do?  What will I do?

---

### Post by SuperSonic4 on 2008-09-13
Have you checked the time zone of the one ahead of you? What does your BIOS time say?

Check Regional and Language settings to see if you're in the right timezone

---

### Post by kansasnoob on 2008-09-13
You can just go to System > Administration > Time & Date to change the time or date.

---

### Post by lisati on 2008-09-13
A couple of things come to mind for you to check: the time zone that Ubuntu thinks you're in, and your BIOS settings for your clock.

---

### Post by SunnyRabbiera on 2008-09-13
Some people do have basic clock issues, you could try to change your time settings by right clicking your clock applet and select "adjust date&time"
unlock it by clicking unlock and then type in your password.
here is where you can change time zone, and change your configuration from manual to upload stuff from servers,
For that bit it will install extra files if needed.
But if its a hardware clock issue you may have to edit your bios, but one step at a time.

---

### Post by matrix14 on 2008-09-13
I am using Xubuntu 8.04.1 and I got same problem.
I am currently life at Indonesia at Central Java (about 150 km from Jakarta). If I switch the timezone to Asia/Jakarta, I've got 6 hours ahead of the time on the BIOS setting.
Then I've got simple idea by switch the timezone to :confused: Malli/Bammako :confused:... Peeps... I am living at Indonesia but use African timezone on my desktop :confused::confused:

---

### Post by starcannon on 2008-09-13
> **matrix14 said:**
> I am using Xubuntu 8.04.1 and I got same problem.
I am currently life at Indonesia at Central Java (about 150 km from Jakarta). If I switch the timezone to Asia/Jakarta, I've got 6 hours ahead of the time on the BIOS setting.
Then I've got simple idea by switch the timezone to :confused: Malli/Bammako :confused:... Peeps... I am living at Indonesia but use African timezone on my desktop :confused::confused:

The clock is adjusted +/- Grenwich Mean Time, so as long as the "timezone" you chose is the same amount of hours +/- from GMT as your particular location on planet earth, then it really doesn't matter. For instance, I live in Spokane WA, but set my timezone using Los Angeles CA. Were both GMT -8 so no big deal what the label is.

GL have fun.

---

### Post by drcdebaca on 2008-09-21
Alright, so I checked the BIOS time and adjusted it to my local time; however, this had no effect.  I then used hwclock to set the hardware time and then hctosys to set the system time with the hardware time.  I still have the same problem.  Any other advice would be appreciated.

---

### Post by mike1234 on 2008-09-21
> **drcdebaca said:**
> Alright, so I checked the BIOS time and adjusted it to my local time; however, this had no effect.  I then used hwclock to set the hardware time and then hctosys to set the system time with the hardware time.  I still have the same problem.  Any other advice would be appreciated.

 My bios clock is off (too lazy to go and buy a battery) if you mouse over your clock. right click and select adjust date and time. Unlock and setup internet time services. You'll have to close and restart it to notice the change. My clock works just fine using Internet time. But I'm also on cable modem and it's always on too. But even if you're not, it should still keep accurate time.

M.

---

