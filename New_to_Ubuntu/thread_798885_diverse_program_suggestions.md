---
title: "diverse program suggestions"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by tethys on 2008-05-18
ok guys, how you all doin? I am new to Linux as of like 3 days ago, and I absolutely luuuuurrrrve the freaking fast boot up time. I have a list of things I want to get on ubuntu before I consider getting rid of Vista completely, and need help finding them.

For some background info, I'm on ubuntu desktop lts 8.04... on a laptop, lol. I am also a complete noob on the inner workings of Linux, so don't be like real techy with me... that'll come later down the line.

First I have a question about Automatrix2: I can't get rid of it... I tried the sudo apt-get remove automatrix2, and it doesn't get rid of it at all... so that needs to be like... gone.

Next, I am having an issue with printing... I have the standard printer configurator installed, and the printer is a Lexmark C530dn color duplexing laser... everythime I try to print anything, it prints like 50 pages with a bunch of random characters about 2-3 rows long across the top... and by that time i cancel the job from the printer itself and reset it to rid it of the jobs.

I am also in the market for a cd label printing program... I have labels, but it seems the proggy for windows that is for the specific labels is windows only... haven't tried running in wine yet, but I'm not holding my breath...

I don't believe I have any other pressing issues at the moment, but I'll post more if I get the need for something.

Thanks a bunch for who will help...

---

### Post by soxs on 2008-05-18
Are you running x86 or x86_64? Important for printer drivers resolution approach...

---

### Post by shifty_powers on 2008-05-18
heh, for the most part, lexmark printers tend to be 'paperweights', though you may be lucky ;)

---

### Post by tethys on 2008-05-18
running x86

---

### Post by damis648 on 2008-05-18
OK, starting with Automatrix2. Try going into system>Administration>Synaptic Package Manager and click search. Type "automatrix" and search for that. When you find it, right click it and select uninstall, and that might solve it. If not report back here.

As for your printer, try System>Administration>Printing. In that dialog, select you printer in the left pane and in the right pane, Click "Change" where it says make and model. Select you make and model and then select the recommended driver. If it still does not work, try repeating the process but selecting different drivers.

For a good CD labeling program, I would recommend Glabel. Just go Applications>Add/Remove and search for "glabel" and check the box next to it and click apply.

Hope I helped :)

---

### Post by r76 on 2008-05-18
> **tethys said:**
> I tried the sudo apt-get remove automat**[COLOR="Red"]r[/COLOR]**ix2, and it doesn't get rid of it at all

Is that [COLOR="#ff0000"]**r**[/COLOR] a typo?  That would explain it.

---

### Post by damis648 on 2008-05-18
> **r76 said:**
> Is that [COLOR="#ff0000"]**r**[/COLOR] a typo?  That would explain it.

wow good point i did not notice that... i was just copying and pasting so i didnt notice :P

---

### Post by tethys on 2008-05-18
yeah apparently i dint know that, that would explain a lot... as for the rest, hang on a tic, ill give it a try

---

### Post by soxs on 2008-05-18
```
sudo apt-get remove --purge automatix
``` in case r was a typo. Will purge it from your system.

---

### Post by starcannon on 2008-05-18
Heres a link to a bunch of Open Office Label templates, these work out great for me.
[http://www.worldlabel.com/Pages/openoffice-template.htm](http://www.worldlabel.com/Pages/openoffice-template.htm)


GL hope those will work for you as well.

---

### Post by tethys on 2008-05-18
yeppers, automatIX is gone now, but my printer gives me one suggested driver, with the option of finding and installing another, tho i dunno where to get another for linux

---

### Post by shifty_powers on 2008-05-18
[http://openprinting.org/show_printer.cgi?recnum=Lexmark-C530dn](http://openprinting.org/show_printer.cgi?recnum=Lexmark-C530dn)

you're inluck, very fex lexmarks work at all with linux ;)

---

### Post by tethys on 2008-05-18
ok, now how about a proggy that runs commercial dvds? i cant seem to get any to work, tho they'll run the backups i made, they wont run my originals that i havent backed up yet, wtf

---

### Post by starcannon on 2008-05-18
You'll need to enable the medibuntu repositories:

[Medibuntu How To]("https://help.ubuntu.com/community/Medibuntu")

Be sure to read further down the page as well, there is some useful information there about windows codecs, and encrypted dvd playback.

---

### Post by tethys on 2008-05-18
omg, you people are gods... i got automatix uninstalled, got the printer working, and can now play commercial dvds... i wub you all

---

### Post by soxs on 2008-05-18
Note: There is one dvd encryption method out there, which will even not play with medibuntu. Its a (extremly) damaged filesystem and requires a vlc mediaplayer-hack to get it run (somewhat really nasty, I just got over one single DVD until today)

---

### Post by shifty_powers on 2008-05-18
heh yeah, the forums truly do rock. great way of learning about your shiny new ubuntu install as well.

oh and if you haven't grab vlc for video, it is in synaptic, and it rocks ;)

---

### Post by tethys on 2008-05-18
right now im using kaffeine since it lets me scan through the movie with no epic failures like the standard movie player thats built in does

ahh... i looked it up and i have tried it, didnt like it... thanks tho

---

