---
title: "gdm.virus"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by nidoo on 2008-05-02
OK, to start I need somebody to confirm something for me. I recently used clamav because I wanted to search some mail folders for windows viruses. I got for hits but not where i was expecting them for example got a hit off gdm.virus and cache.virus..:confused: I expect these are false positive given how secure Linux is against viruses.

Can anyone confirm this for me?:)

---

### Post by aeiah on 2008-05-02
from a quick google it seems that gdm.virus is indeed a virus, but it isnt related to gnome desktop manager. see here: [http://secunia.com/virus_information/41758/agent-gdm/](http://secunia.com/virus_information/41758/agent-gdm/)

it just shares the same three letters.

---

### Post by nidoo on 2008-05-02
Thanks for a speedy reply.

I did the same search with all the results earlier. Unfortunately with the lack of information from the site I couldn't say for sure it's the same thing. I worried if I get rid of them I might screw up GDM. I know if I accidentally get rid of gdm i can just reinstall using the terminal but I'd rather know for sure.

---

### Post by nidoo on 2008-05-02
Ok, found out my own answer these are definitely false positives. After using the agent switcher GDM crashed. I had to go reboot into terminal and

> sudo apt-get remove gdm  
and then 
> sudo aptitude install ubuntu-desktop

Luckily my home directory is on a separate partition. And this solved my problems without having to completely reset all my setting and preferences.8)

---

### Post by leo3307 on 2008-09-29
i have a good idea when it happen to my 
i look for my live cd and star from it look for the file that was deleted or quarentine and copy it using gksudo nautilus and it work with no problems and i don`t lose my data:D

---

### Post by jenelle on 2008-10-18
i had a _cache_3 i think jp  or js was in it somewhere i found it via my virus scanner i deleted it then when i went back on the computer i thought i would scan again half an hour later there it was again i quarantined it then deleted it i hope that is all i needed to do as i am not 100% sure on these things

---

### Post by SunnyRabbiera on 2008-10-18
yeh GDM and the gdm virus are not the same.
also just because clam does detect a virus it doesnt mean the virus will even effect linux.
Yes linux can attract viruses but it cannot get infected by them and any issues you had with GDM well GDM is buggy sometimes :D
And yes Clam can give out false positives.

---

### Post by jenelle on 2008-10-19
> **SunnyRabbiera said:**
> yeh GDM and the gdm virus are not the same.
also just because clam does detect a virus it doesnt mean the virus will even effect linux.
Yes linux can attract viruses but it cannot get infected by them and any issues you had with GDM well GDM is buggy sometimes :D
And yes Clam can give out false positives.

so do i just delete or press false positive ?
seems to go slow loading pages when it is there never had it before ?

_cache_003,virus is what came up , happened again so made sure i wrote it down

---

### Post by gandaran on 2008-10-19
> **jenelle said:**
> so do i just delete or press false positive ?
seems to go slow loading pages when it is there never had it before ?

_cache_003,virus is what came up , happened again so made sure i wrote it down

where did you find this virus? firefox cache or email folders? if it is in firefox cache just clean the firefox cache which you should do from time to time.

---

### Post by jenelle on 2008-10-19
> **gandaran said:**
> where did you find this virus? firefox cache or email folders? if it is in firefox cache just clean the firefox cache which you should do from time to time.

i think when i put my pointer on it it did say firefox i do clear chache and cookies often so sounds like i am doing right thing there , thanks :cool:

---

### Post by ethoxyethaan on 2008-10-19
sorry to get a lil bit off topic but isent ClamAV intended to scan for WINDOWS viruses on your computer/server. (as in the mails etc)

---

### Post by jenelle on 2008-10-19
???????? don't know to be honest
i know it scans all on the computer my pics everything so got to be more then just mail i thought

---

### Post by ethoxyethaan on 2008-10-19
> **jenelle said:**
> ???????? don't know to be honest
i know it scans all on the computer my pics everything so got to be more then just mail i thought
well its scans exactly what you want it to scan or what you gave it to scan.

i don't think its updated for linux viruses, perhaps it is, but i have no idea.

anyhow its smart to read this i guess:
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

along these lines:
> There has not yet been a single widespread Linux malware threat of the type that Microsoft Windows software currently faces, this is commonly attributed to the malware's lack of root access and fast updates to most Linux vulnerabilities

and double read this line

> and fast updates to most Linux vulnerabilities.

---

### Post by jenelle on 2008-10-19
> **ethoxyethaan said:**
> well its scans exactly what you want it to scan or what you gave it to scan.

i don't think its updated for linux viruses, perhaps it is, but i have no idea.

anyhow its smart to read this i guess:
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

along these lines:


and double read this line
cool thanks will check it out

---

### Post by Hozza on 2009-01-10
i just did a clamAV scan because i interact with windows on a daily basis.

I had it set to auto quarintine viruses so by the time i read that it was a false positive and will cause damage if it is removed it was too late.

i rebooted and it came up with a missing GDM error

On start up i had to:

[LIST=1]
[*]Ctrl + Alt + F2 to accsess terminal
[*]Type username
[*]Type password
[*]type "sudo apt-get remove gdm" (without speach marks) and click enter
[*]type "sudo aptitude install ubuntu-desktop" (without speach marks) and click enter
[*]then "sudo reboot"
[/LIST]

logged in and i did not loose any settings or data, if that is not a lesson in researching things you don't know about i don't know what is :D

---

