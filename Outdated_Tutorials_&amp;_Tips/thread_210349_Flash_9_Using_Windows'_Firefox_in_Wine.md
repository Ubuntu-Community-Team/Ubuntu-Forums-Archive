---
title: "Flash 9 Using Windows' Firefox in Wine"
date: 2006-07-06
forum: Outdated Tutorials &amp; Tips
---

### Post by taketheveil on 2006-07-06
Ok this one's easy, and I'm sure plenty of you have already figured this one out, but just in case not:

1. download/install wine from synaptic (make sure all the repositories are enabled just in case)
2. download firefox for windows 98 from getfirefox.com, save it to your desktop
3. open up a terminal and type
```
cd /home/YOUR_NAME/Desktop
wine firefoxsetup.exe
```

and follow directions to install it.  Note that the actual installer isn't really named "firefoxsetup.exe", just type the first capital F and press tab to tab-complete the rest of the file's name.

After firefox is done installing, you can run it anytime by opening up terminal and typing
```

wine ~/.wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe

```

Next, navigate to adobe.com, and click on the "get flash" link.  Download flash 9, and open it when its done downloading.  You have to close firefox and open it again for it to finish installing itself.

Open up the windows version of firefox again (see above) and navigate to [http://theflashblog.com/?p=181#](http://theflashblog.com/?p=181#) to test and see if you've got flash 9!  Congrats if you did!

**Optional**:  Here's how to add the windows firefox to your menu so you can access it easier:

1. Open alacarte menu editor
2. Highlight the submenu that says "Intarweb" (yours may say "Internet" ;) )
3. File --> new entry
4. Name it "Winfox" or whatever you feel like
5. Add "wine ~/.wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe" to command
6. pick an icon you like
7. Press ok

Now you'll be surfing the internets in all its Flash 9 gory!

edit: actually, I just tried that last part, and it didn't work... must be a typo in there or something, I'll let you guys sort it out because I am supposed to be somewhere else right now! :(

---

### Post by starscalling on 2006-07-10
well
flash installer failed... said i was missing a dll
i installed shockwave via wine [same method]
then i went to the page u listed there....
clicked on that and it asked me if i wanted to install flash player...
i said i did and i got a successful install ~_^
might as well do shockwave while yer at it eh :P

btw check out lolifox ;p

---

### Post by acorey on 2009-10-20
The shockwave trick worked for me.

9.04 64 bit in HP dv2000

Then installed ABC viewer plugin and it made my graphics freak out. Very trippy. I logged out and back in and ABC video worked.

wine seems to be a lot better these days. There are only a couple of things I am not able to get working between Virtualbox and wine.

Thanks for the help!

---

