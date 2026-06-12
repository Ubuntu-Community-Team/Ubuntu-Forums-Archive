---
title: "no sound please help"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by sladealive on 2012-06-26
Hi my friend put ubunter on my lap top and when i try to play my music it wont play he has got video audio by use of speakers but can not play through lap top and music through either lap top or speakers it worked fine on the last one he put on for me can anyone help thank you Alan

---

### Post by inashdeen on 2012-06-26
Hi, first off all,
could you specify:
1. your laptop model
2. ubuntu version
see menu > system monitor > system

3. Check if any driver need to be installed 
menu > additional drivers
 
4. use this and post the output for others to see.Read here > [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by idoitprone on 2012-06-26
> **inashdeen said:**
> Hi, first off all,
could you specify:
1. your laptop model
2. ubuntu version
see menu > system monitor > system

3. Check if any driver need to be installed 
menu > additional drivers
 
4. use this and post the output for others to see.Read here


only 1, 2, 4 will be useful because sound cards use open source drivers

Most cases sound card is recognized and have to be configured which is just so dawn hard to understand. I dont thing anyone here understand the alsa stack because it is just too complicted

post the output of

```
aplay -l

lspci -nnk | grep -iA 3 audio
```check if sound is muted
```
alsamixer
```then press f6 and select your sound card

---

