---
title: "KDE Firefox Form WIdgets"
date: 2007-08-07
forum: Outdated Tutorials &amp; Tips
---

### Post by hedgefighter on 2007-08-07
I wanted to fix the ugly form widgets in Firefox. So, I found this thread: [http://ubuntuforums.org/showthread.php?t=369596&highlight=firefox+widgets](http://ubuntuforums.org/showthread.php?t=369596&highlight=firefox+widgets). But those widgets are tailored to GNOME. There was a post about KDE which used some widgets made for OS X, but it didn't look right either. So, I started editing the default forms.css and came up with this style:

[IMG]http://hedgefighter.dreamhosters.com/kdewidgets1.png[/IMG]
[IMG]http://hedgefighter.dreamhosters.com/kdewidgets3.png[/IMG]

I did use the checkbox and radios from the OS X one though. I wanted the corners of everything to be rounded. However, there were two issues. First, the rounded corners don't antialias right so it looks a little funny. And second, you have to use mozilla css options which would prevent the borders from being styled. I wanted to make the widgets look good but be still be able to be changed by the page. If the author defines a new background color that will get shaded so it looks nicer:

[IMG]http://hedgefighter.dreamhosters.com/kdewidgets2.png[/IMG]

I still can't get the select box to do exactly what I want, but it looks ok. I hope to work on this more if there's interest and I have time.

To install, download and then:```
sudo cp -r /usr/lib/firefox/res/ /usr/lib/firefox/res_original
tar -xvvzf KDEwidgets.tar.gz
sudo mv ./KDEwidgets/* /usr/lib/firefox/res/
```

---

### Post by dilidon on 2007-08-08
Thanks.
I like it.:KS Using it under Gnome btw.
Lately I have been having problems installing  the widgets installed from the [http://ubuntuforums.org/showthread.php?t=369596](http://ubuntuforums.org/showthread.php?t=369596) thread - on two computers, for some reason, the submit buttons seem to be inwards not outwards (i.e. button like). Could be a visual effect caused by the video card, but anyhow, your version works like a charm and it looks good to.

---

### Post by hedgefighter on 2007-08-08
Thanks. It's certainly not desktop specific. I just had KDE in mind when I made it.

I'm not sure why the other one has been giving you issues. I doubt your video card is responsible. He's done some good work, especially with his new installer. I just tried to stay away from the -moz-border properties as they're not really modifiable by the page creator. But alas, that means no rounded corners.

Honestly, I just threw together some gradients and did a quick edit of the forms.css because I was tired of looking at the default ones. I decided to put it up here in case anyone else wanted it.

---

### Post by walkerk on 2007-08-08
Looks very nice. Good work.

---

### Post by dilidon on 2007-08-10
> **hedgefighter said:**
> 
I'm not sure why the other one has been giving you issues. I doubt your video card is responsible. He's done some good work, especially with his new installer.
To be clear, he definitely has done excellent work, and I have been using that installer several times. :) 
But for some reason on two of my freshly ubuntufied computers  the visual effect of the new buttons is just plain wrong - the radio buttons are ok, but it is as though the submit buttons' on and off positions had gotten reversed somehow, so they seem inwards before pressing on one of them. And so far, the only common trait I have been able to find between the desktop (CRT) and the laptop (LCD) has been that they have (crappy?) onboard graphics chips - and that does not make too much sense to me either. So still puzzled. Just thought that maybe the buttons have been drawn somehow so that a few pixels get displayed differently and hence provide and unexpected visual effect (as "inwards" and "outwards" are definitely a matter of a visual convention in 2d drawings). As no one else has reported this problem, I thought I should find a different solution. Your "few gradients" did the trick on both displays. ;)

---

