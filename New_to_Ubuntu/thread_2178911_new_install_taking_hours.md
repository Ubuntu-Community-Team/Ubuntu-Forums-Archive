---
title: "new install taking hours"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by Eddie_Duncan on 2013-10-05
I have a new build and am trying unbuntu for the first time.  I am installing 12.04 lts and it is being installed on an a10 apu 6 gig ram, 3 tb hdd.  I have a cable modem for my internet connection.  I installed unbuntu and went through the normal screens for the install.  I have it to download updates as well asn third party software.  it now appears to be stuck on a doslike screen where it shows the steps to what it is doing.  it has been stuck on one like now for rover 2 hours. the hdd still is blinking every once in a while.  I feel like it is stuck but again being my first time, I have no clue how long it normally would take.  I have seen others say around 30 minutes to an hour but not sure if they are doing updates and third party downloads.

---

### Post by buzzingrobot on 2013-10-05
No, it should not take that long.  It's possible you lost the connection, or perhaps the server you were pulling from went offline. (It happens.)

If you are lucky, the install ran long enough to install the bootloader and the system just might boot up correctly. 

Odds are very good, though, that it did not.  Sadly, your only alternative is to do another install.

---

### Post by Bashing-om on 2013-10-05
Eddie_Duncan; Hi ! Welcome to the forum .

Yep, with a descent internet wired connection, should not take longer than 30 minutes.
Maybe the install medium is corrupt ?
1. Did you verify the .iso image integrity (md5sum);
2. Did you "check disk for defects" - boot options menu;
3. Did you "try ubuntu" prior to installing  ? -  makes sure all hardware is compatible;

Else; reformat the Hard drive, and try try again.

 'Nother thought, was that hard disk ever a part of a raid array such that "meta data" is still embedded onto that disk ? Or associated in a prior life with some form of "smart response" ?

[INDENT]ubuntu is supposed to just work[/INDENT]

---

### Post by grahammechanical on 2013-10-05
Depending upon your internet download speed it should take 30 to 45 minutes. And you should not get a DOS like screen at all. Did you run the Ubuntu Live session? How did things work? Here is a suggestion. Move the window to one side. You may see a dialog box waiting for you to approve the terms and conditions for using some piece of proprietary software.

I have done many test installations over the last year and I never tick to install third party software. So, I do not know if this is the problem. But it maybe. It could be that installing third party software includes Microsoft's core fonts. We need to accept the Microsoft terms and conditions or cancel installing the MS core fonts and the installation will stop waiting for our input. 

As I said, I had not had this experience during installation of Ubuntu but I did get caught in this situation a couple of weeks ago when I installed Ubuntu Restricted Extras (same as third party software) after installation. The dialog box sat behind the installation Window. So, see if that is the issue.

Regards.

---

### Post by Eddie_Duncan on 2013-10-05
doing a new install again.  this time I got to the restart the computer button.  I did.  go the splash screen after restarting.  now it is blank and the hard drive is reading again.  crossing fingers.

---

### Post by Eddie_Duncan on 2013-10-05
tried a new install with both updates and third party.  it stopped again the advice from grahmechanical and didn't click the 3rd party and now I am in.  thank you all that responded.  I am sure I will have several more posts/questions once I get in deeper.

---

### Post by Bashing-om on 2013-10-05
@ Eddie_Duncan; Outstanding ! Welcome to ubuntu !

You know where we are, do not be a stranger,

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by buzzingrobot on 2013-10-05
Glad it worked. 

For the  record, the MS font package is in restricted-extras.  It seems to have been a while since I've seen it hide the confirmation dialogue, but I haven't done an original 12.04 install in some time.

---

