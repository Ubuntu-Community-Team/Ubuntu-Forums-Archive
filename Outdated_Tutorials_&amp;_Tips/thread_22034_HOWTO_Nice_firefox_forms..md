---
title: "HOWTO: Nice firefox forms."
date: 2005-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu-geek on 2005-03-25
I stumbled upon this gem a few months ago when I was looking for a way to make my form widgets in firefox look half way decent.

This will work with Hoary or Warty. I took all the updates from this [site]("http://linuxart.com/log/archives/2004/09/22/firefox-forms-work-in-progress/") and this [site]("http://linuxart.com/log/archives/2004/10/15/firefox-default-widgets-part-ii/") then made a tar ball.

**Screenshot from linuxart.com**
[img]http://linuxart.com/dir/stuff/screenshots/partial/firefox-widgets-default-after-2.png[/img]
[]("http://ubuntuforums.org/download/ff-forms.tar.gz")
**Installation:** 
cd /usr/lib/mozilla-firefox/
sudo wget [http://ubuntuforums.org/download/ff-forms.tar.gz]("http://ubuntuforums.org/download/ff-forms.tar.gz")
sudo tar xvzf ff-forms.tar.gz
sudo rm ff-forms.tar.gz

You will need to re-apply this after firefox updates.

---

### Post by Julius on 2005-03-25
Cool, I was looking for this. In my previous installation I had something like this, I knew I had to change some .css file to change the widgets :P

---

### Post by TravisNewman on 2005-03-26
anyone have a before shot? I'm having trouble noticing what's changed.

---

### Post by vrunt on 2005-03-26
[QUOTE=panickedthumb]anyone have a before shot? I'm having trouble noticing what's changed.[/QUOTE]

Here's an explanation:
[https://bugzilla.mozilla.org/show_bug.cgi?id=264523](https://bugzilla.mozilla.org/show_bug.cgi?id=264523)

---

### Post by jdong on 2005-03-26
Are these stable? I'd love for it to be a part of Backports Firefox.

---

### Post by Julius on 2005-03-26
This things are just CSS tweaks, no it doesnt matter what version you have :P I remember I had done somethng similar in warty. I'm sure it can be done in windows too

---

### Post by ubuntu-geek on 2005-03-26
[QUOTE=jdong]Are these stable? I'd love for it to be a part of Backports Firefox.[/QUOTE]
 Stable enough for me.. I have never had a problem (4 months now), some widgets dont pickup the changes but most do.

---

### Post by notzac on 2005-04-29
Thanks a heap for this - the ugliness of the form element widgets in Firefox was a little off-putting, seeing as everything else looks so damn good :)

One little thing though - the image used for the selected radio button is .. odd. You get the dot to denote that it's been selected, but no 'ring' surrounding it (it's hard to describe). I've created a replacement image file, which appears to have fixed it all up for me - I've managed to work out how to attach the image file to this post, so if you want to add it to the package - you're more than welcome to :)

..and yeah, it'd be great if this could be included as a part of the Firefox package in hoary-backports :D

---

### Post by pjack76 on 2005-04-29
Oh thank you, thank you, THANK YOU! I absolutely abhor the default Firefox form widgets on Linux. My screen doesn't have a lot of contrast so it looks like the text entry boxes only have 2 sides. This is great!

Possible to include this in Breezy by default? There is actually an accessibility issue here, the default widgets make it impossible to see where one control ends and another begins if you're partially blind (or slowly going blind like me).

-Paul

---

### Post by Chayyiel on 2005-04-30
Beautiful! Thanks!

---

### Post by popdog on 2005-05-01
Excellent, i really hated those ugly form foxes before!  Only problem i can see is that on some  sites it makes text in drop down boxes almost unreadable.  Apart from that big improvment thanks :)

---

### Post by kiddo on 2005-05-08
Ah, this makes life more bearable ;) but am I the only one seeing that SOME (well.. 50% ?) sites don't render the forms with this trick? Half of the forms render the ugly way. Just look at gmail. Speaking of gmail, when hovering the "send" button, it shrinks, so you can "save draft" by mistake ! :D

---

### Post by Sam on 2005-05-09
[QUOTE=kiddo]Ah, this makes life more bearable ;) but am I the only one seeing that SOME (well.. 50% ?) sites don't render the forms with this trick? Half of the forms render the ugly way. Just look at gmail. Speaking of gmail, when hovering the "send" button, it shrinks, so you can "save draft" by mistake ! :D[/QUOTE]
You're right. This trick doesn't work well when forms objects use css.

@notzac & pjack76: It's NOT a good idea to make this as default. For web designers it'll provide a lot more work to ensure that every form layout will be the same on any browser/theme.


By the way, to backup your old settings just make a copy of the file /usr/lib/mozilla-firefox/res/platform-forms.css. When you want your old firefox forms, just replace it back.

---

### Post by royg1234 on 2005-06-08
Nice howto!  But is there any way to undo this?  Don't get me wrong, it's pretty and I like it; but some form text gets cut off, like this **[screenshot](http://www.geocities.com/pilstilin9/forms.png)** .  It's really annoying with my bank website, becuase the dates are cut off, so 2 Jan looks the same as 2X Jan.

ThankS!

---

### Post by ow50 on 2005-06-08
[QUOTE=royg1234]But is there any way to undo this?[/QUOTE]
At least reinstalling firefox will undo it.

---

### Post by royg1234 on 2005-06-08
[QUOTE=ow50]At least reinstalling firefox will undo it.[/QUOTE]
Will this default all ther rest of my settings, bookmarks, and extensions?

---

### Post by ow50 on 2005-06-08
[QUOTE=royg1234]Will this default all ther rest of my settings, bookmarks, and extensions?[/QUOTE]
No.

Your settings are stored in your home folder. Apt installations will never touch your home folder. Reinstall will only overwrite files is system directories, for example the /usr/lib/mozilla-firefox, where the forms were installed.

---

### Post by Gothic on 2005-06-09
[QUOTE=notzac]Thanks a heap for this - the ugliness of the form element widgets in Firefox was a little off-putting, seeing as everything else looks so damn good :)

One little thing though - the image used for the selected radio button is .. odd. You get the dot to denote that it's been selected, but no 'ring' surrounding it (it's hard to describe). I've created a replacement image file, which appears to have fixed it all up for me - I've managed to work out how to attach the image file to this post, so if you want to add it to the package - you're more than welcome to :)

..and yeah, it'd be great if this could be included as a part of the Firefox package in hoary-backports :D[/QUOTE]
thx. i've got the same problem, thx again for your work :)

---

### Post by Sionide on 2005-06-09
[QUOTE=notzac]One little thing though - the image used for the selected radio button is .. odd. You get the dot to denote that it's been selected, but no 'ring' surrounding it (it's hard to describe). I've created a replacement image file, which appears to have fixed it all up for me - I've managed to work out how to attach the image file to this post, so if you want to add it to the package - you're more than welcome to :)[/QUOTE]

Yeah I had this trouble too.

I love check boxes, they look sooo nice :) Hooray for eye candy!

Edit: It's a lot better with that new file notzac - thanks. Note to others; stick it under /usr/lib/mozilla-firefoz/res

---

### Post by topcop on 2005-06-14
hopefully firefox will have native GTK2 forms one day - this bug has been there for a while but no patches  [https://bugzilla.mozilla.org/show_bug.cgi?id=232553](https://bugzilla.mozilla.org/show_bug.cgi?id=232553)

---

### Post by flamarro on 2005-06-19
Just to say thanks also.
I was just frustrated in google for instance i couldn't see the all search box, and in some sites i couldn't even see some words that i could see in XP, now i can.

Ps: I have Ubuntu installed for about 15 days already, and i also have XP installed, but for 15 days i don't even once saw XP, and with the help of all here i manage to do all the thing i've used to do. THANKS again

---

### Post by niels on 2005-11-27
Just, installed it and it look really goooood!

The only problem was, that ff-forms.tar.gz didn't exist! I spent five seconds searcing for it. I have add the radio_checked.png from this thead and uploaded it to my homepage for you to download.

[Just click here to download ff-forms.tar.gz]("http://nielshansen.info/files/ff-forms.tar.gz")
or type this in a terminal (you should be in the mozilla-firefox directory)
sudo wget [http://nielshansen.info/files/ff-forms.tar.gz]("http://nielshansen.info/files/ff-forms.tar.gz")

---

### Post by trampolando on 2005-12-03
hello... I've installed Firefox 1.5 and this procedure to change the "look" of firefox buttons doesn't work... any idea?
thanks
rIKY

---

### Post by BitTorrentBuddha on 2006-05-25
anyway to get this working under dapper?

---

