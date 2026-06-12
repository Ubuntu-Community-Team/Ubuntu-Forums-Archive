---
title: "Ubuntu for a 16 year old"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by logicus on 2008-09-01
Hey there

My girlfriends daughter is 16 and really into the usual teenage internet, chatting, online games and various social websites. Some of them infected with various virusses.

She is using windows and have already gotten 25 virus infections. So I want to get her onto the Ubuntu train. I showed her KDE 4.1 and that was enough eye candy to get her interested.

Anyway, to get her really hooked I was thinking about which other programs I should include, for instance amsn. Perhaps a program that everyday tells her how fantastic she is, she'd like that. Do you know of such a program and perhaps of something else that would be something she'd like ? 

Sincerely

Peter

---

### Post by perlluver on 2008-09-01
> **logicus said:**
> Hey there

My girlfriends daughter is 16 and really into the usual teenage internet, chatting, online games and various social websites. Some of them infected with various virusses.

She is using windows and have already gotten 25 virus infections. So I want to get her onto the Ubuntu train. I showed her KDE 4.1 and that was enough eye candy to get her interested.

Anyway, to get her really hooked I was thinking about which other programs I should include, for instance amsn. Perhaps a program that everyday tells her how fantastic she is, she'd like that. Do you know of such a program and perhaps of something else that would be something she'd like ? 

Sincerely

Peter

The games, that are available, maybe opera web browser.

---

### Post by swoll1980 on 2008-09-01
LimeWire [www.limewire.com](www.limewire.com)

exaile is a mp3 player/music library/ipod syncer
```
sudo apt-get install exaile
```

---

### Post by perlluver on 2008-09-01
If I may recommend Frostwire, since it is free, and has no nag screens.

---

### Post by swoll1980 on 2008-09-01
yeah I use frostwire as well, but familiarity is also important. By the way limewire is free as well where do you think frostwire comes from

---

### Post by dioltas on 2008-09-01
Pidgin Instant messenger maybe? Lets you chat on msn, aim etc...

ZNES nintendo emulator aswell, you'll have to get some game roms for it though. You can play super mario and other classics with it.
Maybe those eyes that you can put on the menu bar that follow your mouse around.

---

### Post by modmadmike on 2008-09-01
Im 16 and use ubuntu all the time (i have used linux for the past 8 years) Amarok is simply unbeatable in my opinion (besides VLC for anime)  and I use firefox as my main browser, if she is artistic then show her the gimp, Install Compiz fusion she probably won't be able to live with out it lol.

---

### Post by k3lt01 on 2008-09-01
Even though I don't really use it I would recommend Kopete instead of Pidgin as it has webcam capability and she can chat with her friends on cam.

For music player programs I like the old Banshee which is in the repositories for Hardy still. I wouldn't recommend the new version as it is buggy and doesn't download podcasts properly yet.

There are plenty of games in the standard install to get her going.

---

### Post by dioltas on 2008-09-01
Ya, I don't really use Pidgin either, so I can't say which IM client would be better.
As for music players I like Rythmbox. It installs with ubuntu.

---

### Post by dioltas on 2008-09-02
> **logicus said:**
> Hey there
Perhaps a program that everyday tells her how fantastic she is, she'd like that. Do you know of such a program and perhaps of something else that would be something she'd like ? 


to do the thing that tells her how fantastic she is you could use fortune and conky. Fortune gives random quotes from a text file. Install it and conky with 
apt-get install fortune
apt-get install conky

Just make a text file with the compliments seperated by %, like this:

You look great today!
%
You are really Fantastic!!
%
etc etc...

Save it as compliments
Then make a corresponding .dat file by typing 
sudo strfile compliments compliments.dat.

Type fortune -f, to see where your fortune files are stored and copy both compliments and compliments.dat into that directory.

If you now type "fortune compliments" you should get a random compliment from that file.

----------------------------------------------------------------

I havn't alot of experience with conky, but I think then all you would have to do is in the TEXT part of the conky config file (download a sample one of these or something and put in in your home directory) put 
${exec fortune compliments}
Set conky to start automatically, and it should display random compliments on the desktop. Only thing is I'm not sure how to set the interval so that it dosn't constantly change the compliment. Maybe someone else would know.
-----------------------------------------------------------------

Having said all that, there's probably a much easier way to do it, just a suggestion...

Edit: You could put "fortune compliments > /home/user/textfile" at the end of /etc/profile so that every time she logs in it saves a random compliment in textfile. Or set up a crontab so that every hour it executes "fortune compliments > /home/user/textfile". 

Then in conky put "${exec cat /home/user/textfile}" instead, so that the compliment displayed would change every time she logged in or every hour. Again probably easier ways to do it, but I dont see why it wouldnt work.

---

### Post by barbedsaber on 2008-09-02
Frostwire FTW
Rhythm Box FTW (especially if she is used to iTunes)
might I suggest empath (IM client) I haven't used it before, but it sounds very promising, and I don't like kopete much. (thats just me though.)

---

