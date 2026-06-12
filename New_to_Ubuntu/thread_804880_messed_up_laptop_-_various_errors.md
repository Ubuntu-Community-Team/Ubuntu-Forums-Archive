---
title: "messed up laptop - various errors"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by boblettoj99 on 2008-05-23
hi i have windows and ubuntu dual booting on my laptop.
when i try to boot kubuntu, it gets to the end of the loading bar then goes black to text. i get several errors, some flash up too quickly for me to write down but im pretty sure its messed up big time.

Firstly i get "segmentation faultowd" thats all i could read...
next came something about interrupt crtitical something..
next came "clocksource tsc unstable"
finally it stopped on acpi exception (battery 0216) (repeated several times with different numbers at the beginning).

I read a different post about the acpi exception and that said to edit the menu.lst, i tried to access it from windows but it says the disk was not formatted (yes i pressed cancel :p) 


Now when i boot into windows it works alright until i get to typing stuff. The keyboard lags like hell! could this be related to the critical interrupt thing?? otherwise windows works Ok.

sorry its all a bit vague but i really need some help here!
thanks!

EDIT:
just remembered, this is the first time i tried booting linux after i updated the bios from the dell website, this was meant to fix a battery problem i had, what it seems to have done is just make the problem "go away". ill try and roll back bios, humph :(

---

### Post by KingTermite on 2008-05-23
Did Kubuntu ever work correctly or is this from the first time you installed?

What type of laptop?

Are you plugged in (not on battery)?

Have you tried kubuntu safe mode?

---

### Post by HotShotDJ on 2008-05-23
> **boblettoj99 said:**
> I read a different post about the acpi exception and that said to edit the menu.lst, i tried to access it from windows but it says the disk was not formatted (yes i pressed cancelHave you tried booting into recovery mode?  This can be found in the grub menu (press "Esc" when the grub prompt appears at boot).  You'll be able to edit menu.lst using the command nano -w /boot/grub/menu.lst

Make sure you edit ONLY the portion below the line that reads ```
## ## End Default Options ##
```unless specifically told otherwise.  Use "Ctrl + x" to save and exit.

---

### Post by boblettoj99 on 2008-05-23
> **KingTermite said:**
> Did Kubuntu ever work correctly or is this from the first time you installed?

What type of laptop?

Are you plugged in (not on battery)?

Have you tried kubuntu safe mode?


kubuntu has been working for ages, been playing games on windows non stop for ages, havent been on it in a while, this is the first time ive been on it since a bios update.

laptop is Dell inspiron 1501

im plugged in yes

and iv tried it in recovery mode if thats what you mean

---

### Post by boblettoj99 on 2008-05-23
ok ubuntu boots fine now but the keyboard lag still happens in windows. Could it have been related in any way?
wrong forum i suppose!

---

### Post by HotShotDJ on 2008-05-23
> **boblettoj99 said:**
> Could it have been related in any way?
wrong forum i suppose!I suppose it is possible.  It is also possible that I'll have dinner with Shania Twain tonight.  Both are equally unlikely. :)

---

