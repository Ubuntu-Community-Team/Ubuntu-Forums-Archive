---
title: "Possible security breach"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by bean@ on 2012-06-02
Am using 11.10,let someone connect their I phone to PC and copy some files(music and pic.s,also they transfered some files onto my machine.It turns out they are very much not to be trusted,have changed main login password and 'locked' the files they left,
   How can I check to see if anything malicious loaded either in said files or elsewhere,may well just being paranoid but then again maybe not!
       Any suggestions,apart from not letting this situation arise again,thanks,Bean

---

### Post by mikewhatever on 2012-06-02
Look at the logs, terminal history, installation history. There is no universal way for finding malicious files.
Have you been able to change the changed password?
How are the files locked? Encryption? Permissions?

---

### Post by bean@ on 2012-06-02
> **mikewhatever said:**
> Look at the logs, terminal history, installation history. There is no universal way for finding malicious files.
Have you been able to change the changed password?
How are the files locked? Encryption? Permissions?
Thanks for answering,am probably being over cautious but turned out to be a right SOB I gave access to. 
 I meant I'd changed password and again since I posted. Files locked by permissions via properties>permissions-I don't know another way.
  Something called telinit 1 in terminal past commands(sudo) and don't remember that,I don't know how to check/understand logs or installation history,must be why am still a beginner but seems to be stuff again I don't /can't make sense of in log viewer files ie "dmsg 1.gz" thru"dmsg4 .gz" over last few days but I don't know if thats a bad thing. Need to update profile as am using 11.10 gnome style.don't like Unity so am holding off upgrading till can use it(Unity)

---

### Post by matt_symes on 2012-06-02
Hi

@Beans@. I live in the same neck of the woods as you.

Have you considered looking for a local LUG (Linux user group) to get extra support. 

Most of them meet once a month in the local pub/ resturant for a chat etc. 

It can be a good network and help you to learn quickly.

Indecently, why did you give them access to your PC ?

You still need elevated privileges to use the telinit command from a normal user account unless they used a root exploit.

Kind regards

---

### Post by bean@ on 2012-06-03
I need to learn more,just never seem to have the time!
  Only got back in front of a PC again Jan 2011 after a break of 16 yrs,started re-learning windows then got interested in Linux after an acquaintance mentioned it and was quickly converted!
  I gave said SOB access 'cos I made a serious misjudgement , ce la vie. They wanted some of my pictures and music and visa versa,since turned out to be a thief and general a-hole,am normally a fair judge of people but got it v.wrong this time and am thus worried.I do no banking on this machine,use a windows laptop for that but all my business stuff is on this pc.
  Sorry to ramble,blame it on the espresso.Am checking out irc now

---

### Post by mapes12 on 2012-06-03
If I had your problem I would back up all the stuff I wanted to keep, wipe the drive with something like Killdisk, then do a fresh install of Ubu. It may be overkill but at least you know you haven't got something nasty lurking around on your system.
> 
I do no banking on this machine,use a windows laptop for thatOuch! You're more likely to get hacked using this. I recommend to all my friends and family never to do anything financial online with a windoze machine but to use a Ubu machine instead.

---

### Post by mikewhatever on 2012-06-03
> **mapes12 said:**
> If I had your problem I would back up all the stuff I wanted to keep, wipe the drive with something like Killdisk, then do a fresh install of Ubu. It may be overkill but at least you know you haven't got something nasty lurking around on your system.
...

Letting the installer format the drive once would be enough, no need to be completely paranoid and waist time.

---

### Post by bean@ on 2012-06-04
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by TBABill on 2012-06-04
I would recommend going over those files in your /home carefully before backing them up if the person who had access is as malicious as you stated. Then save the files you really want to keep and reinstall as suggested earlier.

---

### Post by gordintoronto on 2012-06-04
Does your visitor have expertise in Linux? That is so rare, I think you are probably being paranoid. Instead, you should be paranoid about banking with Windows.

A flash drive might have been a good way to keep your visitor away from direct access to your computer.

---

### Post by Ms. Daisy on 2012-06-04
> **bean@ said:**
> Thanks for answering,am probably being over cautious but turned out to be a right SOB I gave access to. 
 I meant I'd changed password and again since I posted. Files locked by permissions via properties>permissions-I don't know another way.
  Something called telinit 1 in terminal past commands(sudo) and don't remember that,I don't know how to check/understand logs or installation history,must be why am still a beginner but seems to be stuff again I don't /can't make sense of in log viewer files ie "dmsg 1.gz" thru"dmsg4 .gz" over last few days but I don't know if thats a bad thing. Need to update profile as am using 11.10 gnome style.don't like Unity so am holding off upgrading till can use it(Unity)
For help in looking for suspicious stuff in the logs, look at the "[Did I Just Get Owned]("https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned")" wiki.

---

