---
title: "How to type in Arabic in LibreOffice"
date: 2015-05-07
forum: New to Ubuntu
---

### Post by francescodll on 2015-05-07
Hi everybody

I used to write and read .odf and .doc files in Arabic on my laptop and then suddenly one day LibreOffice stopped reading and writing in Arabic. I can normally write in Arabic in the browser for example or in other programs but if I for example copy and paste an Arabic text in LibreOffice it would only paste numbers and symbols. Same thing if I enable the Arabic keyboard and try to type in Arabic: no letters will appear in the document.

- I have installed a language pack as suggested here: [http://ubuntuforums.org/showthread.php?t=1600059](http://ubuntuforums.org/showthread.php?t=1600059).

- I have installed an Arabic font.

- I have changed the Language settings as suggested here: [http://alefba.us/libreoffice-arabic-persian](http://alefba.us/libreoffice-arabic-persian).

What is wrong? 

(Sorry I am quite ignorant about these kind of issues (but willing to learn). Please try to speak a human language to let me understand which steps should I follow).

Thanks a lot
Francesco

---

### Post by tristan16 on 2015-05-09
Try enabling the Complex Text Layout (CTL). Open LibreOffice and go to settings. Under language settings, select languages. Check the box for Complex Text Layout (CTL) and select your Arabic language there.

Edit: I added a screenshot in case I was too confusing. ;)

---

### Post by grahammechanical on 2015-05-09
In Libreoffice we can also go to Tools>Language and that will give 3 options

For Selection
For Paragraph
For All Text

Each option will have other options. The More option will open a dialog box and that has a panel called Language. You may find a setting there that has been altered.

Regards.

---

### Post by francescodll on 2015-05-11
Already made all these attempts... still no results :(

---

### Post by dino99 on 2015-05-11
i suppose there is not so many users typing Arabic language reading that forum; so better to post on askubuntu to get devs advices

---

### Post by francescodll on 2015-05-12
It's not only about users typing Arabic actually. It can be any person using a non-western alphabet.

---

### Post by amanchesterman on 2015-05-12
Remember that there is a dedicated LibreOffice forum here: [http://en.libreofficeforum.org/](http://en.libreofficeforum.org/)
where there are quite a few postings about writing in Arabic.

However I think that your problem may be simply that your LibreOffice profile has become corrupted. You say in your first post that everything was OK and then 'suddenly' LO malfunctioned: that is the clue. There are instructions on how to reset your profile here:[ https://wiki.documentfoundation.org/UserProfile]("https://wiki.documentfoundation.org/UserProfile") 
and the page says
"If you notice any strange behavior on LibreOffice, or simply it fails  to start, the first thing to try is to reset the user profile"
which I have always found good advice.

---

