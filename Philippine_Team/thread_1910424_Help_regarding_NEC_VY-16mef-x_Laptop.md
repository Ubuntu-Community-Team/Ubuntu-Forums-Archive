---
title: "Help regarding NEC VY-16m/ef-x Laptop"
date: 2012-01-17
forum: Philippine Team
---

### Post by justoxyoskyscraper on 2012-01-17
Hi!

I have this laptop from a secondhand store po. It works OK on ubuntu 10.04 and 11.10. ANg problem ko lang po is that there is no sound na nilalabas yung speaker. (It had sound when it was in windows XP).

I will post the logs I see in the computer in the next message. For now, ask ko lang po kung may experience kayo sa laptop na ito.

I've tried using ALSA and OSS, pero pareho silang di gumagana. May nakikita ring multimedia audio controller si lspci.

---

### Post by nakama1925 on 2012-01-19
parekoy naexperience ko yan dun sa old skul kung dell dati.
nasubukan mo na bang buksan yung alsa mixer sa terminal?
command 'alsamixer' in terminal without qoute.
novice lang din ako pero baka sakaling gumana.hehe

---

### Post by kiminaiseah on 2012-01-25
make sure you have the following

alsa-base alsa-utils linux-sound-base

or apt-get install alsa-base alsa-utils linux-sound-base

then dpkg-reconfigure linux-sound-base

select ALSA then okay

then alsamixer

check mo yung control pag meron ka makikita na MM sa may baba nung bar it means naka mute 

try mo press M para ma unmute then arrow keys yung pag lipat and up./down yung adjust

---

