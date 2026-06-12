---
title: "understanding /sys/firmware/acpi/interrupts/gpe"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by rawrmonster on 2014-01-31
Hello :D. I have been on this new kick of trying to understand how and why parts of the linux os work the way they do and what parts of the file system are related to what part of the OS. This brings me to my question, I have looked up on google what a gpe is and i seem to find the answer "general purpose event", and it has on my computer gpe00-gpe3F. Is there a way to find out what each of these events are linked to? I have tried to cat the file and all i get is "0 invalid", "0 enabled", "0 disabled". When i tried looking up acpi gpe on google all i seem to find are people talking about gpe storms. Thanks for reading and have a great day!

---

### Post by Bashing-om on 2014-01-31
rawrmonster;

NewDocs is a great resource - thank several of the forum members.
This should satisfy your thirst, I trust only temporarily:
[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=%2Fsys%2Ffirmware%2Facpi%2Finterrupts%2Fgpe&sa=Search&siteurl=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FNewDocs](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=003883529982892832976%3Ae2vwumte3fq&ie=UTF-8&q=%2Fsys%2Ffirmware%2Facpi%2Finterrupts%2Fgpe&sa=Search&siteurl=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FNewDocs)
This search has lots of links.

[INDENT]because
[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by rawrmonster on 2014-01-31
I have already looked through the documentation on ubuntu and a few other distros as well. None of them say anything about what i am talking about only what i stated before about the gpe storms.

---

### Post by Bashing-om on 2014-01-31
rawrmonster; Hi !

I beg to differ, please look at the search link and see that there is indeed a wide variety that are all directly applicable to this our operating system of choice. Nothing else.

NewDocs ->
[INDENT][INDENT]only ubuntu
[/INDENT][/INDENT]

---

### Post by rawrmonster on 2014-01-31
I dont know how many times i have to say that i have looked at your link and have not found a single thread that has anything to do with how to find out what a /sys/firmware/acpi/interrupt/gpe links to and how to find what inturrupts are being used by with gpe. The only thing I can find is about gpe storms, I would love for you to find one link about what i am talking about. If you could prove me wrong i would be very happy but i have spent about 3+ hours looking for anything about this, and have found nothing.

---

### Post by Bashing-om on 2014-01-31
rawrmonster; Well,

From the link, does this give ya any indicators of where to go looking ?

> 
The solution for me and for many others was, first of all, find out the "gpe" that is causing the bad stuff with something like:

grep . -r /sys/firmware/acpi/interrupts/
and check for an high value (mine was gpe13 - with a value like 200K - so, you have to change it accordingly, if differs). After that:

~ cp /sys/firmware/acpi/interrupts/gpe13 /pathtobackup
~ crontab -e
Add this line, so it will be executed every startup/reboot:

@reboot echo "disable" > /sys/firmware/acpi/interrupts/gpe13
Save/exit. Then, to make it work also after wakeup from suspend:
<snip>
<snip>

[INDENT][INDENT]I am only trying to help
[/INDENT][/INDENT]

---

### Post by rawrmonster on 2014-01-31
This still does not help me as it only gives me the answer that i stated i found up top. I am not looking for how many inturrupts that a gpe has handled i am looking for what is sending thos gpe's the inturrupts.

---

