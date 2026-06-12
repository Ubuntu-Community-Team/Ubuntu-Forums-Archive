---
title: "Samsung netbook n150 plus nonexistent touchpad settings"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by tastefuldeath on 2012-03-24
I need to at least get vertical scrolling and maybe more features for my touchpad. As of posting, it can only be used like a mouse, without scrolling or anything else. I was checking this:

[https://wiki.ubuntu.com/DebuggingTouchpadDetection]("https://wiki.ubuntu.com/DebuggingTouchpadDetection")

but when I go to Settings > Settings Manager > Mouse, there's no touchpad tab. I don't know what to do next, the other stuff on google sounds so technical.

Here's what I have on terminal when I did xinput list.
```
kirsten@Kirsten-N150P:~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
```

I am on Xubuntu 11.10 too. Help D:

---

### Post by Kevin McCready on 2012-03-24
In this forum, if you click on search, advanced and select Titles Only then put in your search term/s you get many responses. 

[http://ubuntuforums.org/search.php?searchid=85915163]("http://ubuntuforums.org/search.php?searchid=85915163")

Good luck.

---

### Post by tastefuldeath on 2012-03-24
Thanks, haven't fixed it yet but found out stuff on searching.

Well, when I did synclient -l, it showed parameter settings so I'm guessing that my Elantech Touchpad drivers are loaded? I just can't access the settings for this right now. 

Still gonna search tho!

---

