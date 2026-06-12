---
title: "ctcp plugin for pidgin 2.0.2"
date: 2007-07-04
forum: Programming Talk
---

### Post by slavik on 2007-07-04
took the whole day to figure out enough Perl prpl API, but now, I have a working plugin to send ctcp messages (the kind that triggers 99% of Fserves out there).

The version is 0.5 ...

Instructions:
- Download the attached file
- remove the .txt extension
- place it in ~/.purple/plugins/ (create the directory if it doesn't exist).

sorry, people, but this plugin will not be developed for gaim 2.0 beta, because pidgin is new and gaim beta will not be around much longer.

---

### Post by ffxr on 2008-05-25
hi, i have installed this script and thanks for it.. is it still the most current?

can you tell me if it is able to handle CTCP commands such as 

'Received CTCP 'SOUND snd/Cymbal.au' (to #proi) from cisco' ?

do i need to store the sound files locally?

thanks again.

---

### Post by slavik on 2008-05-25
no, it cannot. it simply sends ctcp commands (does nothing when receiving them). eventually though I am hoping to work in dcc chat capability (pidgin devs don't really like dcc and ctcp)

that and I am not sure what the sound command is supposed to do.

---

### Post by ffxr on 2008-05-25
ok , gotcha thanks.. ll look fwd to the update then : )

---

### Post by slavik on 2008-05-25
> **ffxr said:**
> ok , gotcha thanks.. ll look fwd to the update then : )
if it ever happens. :(

---

