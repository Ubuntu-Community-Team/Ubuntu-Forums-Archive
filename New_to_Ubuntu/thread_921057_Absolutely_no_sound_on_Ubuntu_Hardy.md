---
title: "Absolutely no sound on Ubuntu Hardy"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Kimmerset on 2008-09-15
All right, I guess I kinda fail right now, but I've been working for the past couple hours and have not had any progress on getting my sound working.  I've browsed numerous threads, sites, postings and the like and I guess I suck at finding solutions or something.

I have a Tecra A9 laptop dual-booted with XP Professional.  The sound card is a Realtek ACL262 and sound works just fine in Windows.  

I've downloaded and updated Alsa, downloaded the mixer and made sure nothing has been muted and tried most of the suggestions that I've found with no positive results.  

Any suggestions would be a pleasure.

---

### Post by bangmalley on 2008-09-16
select ALSA from sound option.

or try following methods:
[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)
[http://ubuntuforums.org/showpost.php?p=5131958](http://ubuntuforums.org/showpost.php?p=5131958)
[http://ubuntuforums.org/showthread.php?t=539595](http://ubuntuforums.org/showthread.php?t=539595)

---

### Post by HousieMousie2 on 2008-09-16
If those fail... you might take a look at the 'alsamixer' in terminal.  My Mom's machine periodically resets the values for the last few entries to zero.

Using the arrow keys, go to the end and look at the 'VIA DXS' settings, all four of mine are set at '81<>81', (both mine and Mom's are Realtek, though of a different flavor than yours.)

Best of luck!

---

### Post by tuxxy on 2008-09-16
Do the test files play, when you select ALSA as your sound output at system > prefs > sound

---

### Post by Kimmerset on 2008-09-16
Hmm, yeah, figured out the problem.  Friend of mine has the same laptop (school issued) and it was an issue with something windows does. 

Kept the soundcard muted in Windows and it transfered over to using Ubuntu.  Problem solved, thanks for the suggestions.

---

### Post by tsunadehime on 2008-11-07
awwww man this is great:lolflag:

---

