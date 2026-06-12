---
title: "Certain Fonts Display too HUGE to view"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by jondavisct on 2008-04-27
I am a Linux newbie and just installed Ubuntu 8.04 on a dell computer from my office. I do not know the video type nor how to find out. I did a full install and had it reformat the hard drive. Everything seemed to run well but there are certain places where the font size is sooooo BIG that a single letter cannot fit on the screen.

For instance, the fonts when you go to the Help function or if you do a google search. With a google search, most of the fonts are fine but the 1,2,3, etc. at the bottom for the next page of results is way too big.

I have tried changing screen resolution, I have update by display font size in Firefox from -1 to 96, I have changed font types in appearance all to know avail. 

I installed Sysinfo to try and see what type of video card I have but it does not tell me. I am using the built-in video from dell that comes on the motherboard.

I am using a dell GX260 and am NOT using the add-on video card that came with the system but i have removed it to use in another computer so it is not affecting the system.

I have looked at my xorg.conf file and basically everything is the default settings except for my keyboard section.

Any help would be appreciated.

---

### Post by caro on 2008-04-27
This may be way too basic (sorry if it is) but have you gone to System > Preferences > Appearance > Fonts and set them up the way you want?

---

### Post by jondavisct on 2008-04-27
Thanks for the quick response. No thing is too basic for a Linux newbie. However, I have gone through every setting I could find and made minor changes to font sizes and appearance settings to see if this would make a difference. I did leave it on 120 dpi at one point since I am getting older and at the high resolution the fonts are too small.

However, my problem is that only certain fonts are too big. and when I say big, I mean BIG. For those that know font sizes, these are probably 288 pts

---

### Post by caro on 2008-04-27
Is it only happening in your web browser or other apps too?

---

### Post by jondavisct on 2008-04-27
I would say it is only happening in the browser. I am running the default Firefox 3 beta 5 that comes with 8.04 but I did download and test Epiphany as well which exhibits the same behavior. 

Also, when I click the ? help icon in the top left corner, the resulting page has the big fonts on it. This looks like it is using Firefox to handle the help function though.

Like I said, many pages are fine. For instance I can go in and look at the help forums, but when I click to see the details about a particular topic, the text that is displayed is in this HUGE font.

---

### Post by caro on 2008-04-27
In the Firefox address bar, enter about:config and then filter on "font".  See if you have any non-default settings or large font size.  

If you have set the fonts in System > Preferences and checked your settings in Firefox (I'm using FF3 Beta 5 also with Hardy), then I'm out of ideas. Maybe someone else has run into this.  Good luck.

---

### Post by jondavisct on 2008-04-27
No Joy. All that is fine. Should I post this to a new forum? If so, which one do you suggest?

---

### Post by caro on 2008-04-27
You can try the General Help forum here on Ubuntu.  There are so many people asking questions right now, especially in the Absolute Beginners forum, that people just can't keep up.  There may be less traffic in General Help.  Sorry I couldn't help.

---

### Post by chaparrazo on 2008-06-04
Don't know if this is much of a fix. I just found this discussion while searching for an answer to the same problem. The individual letters almost fill the whole screen! 

Here's my lame workaround: in Firefox, select View, then Page Style and select "No Style" It's not cute, but it works. ;)

---

