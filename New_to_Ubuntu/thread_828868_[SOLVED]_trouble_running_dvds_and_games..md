---
title: "[SOLVED] trouble running dvds and games."
date: 2008-06-14
forum: New to Ubuntu
---

### Post by fr.theo on 2008-06-14
Hello my name is Fr. Theodore,

I have been using Ubuntu Linux Hardy now for over a month, and have resolved alot of the issues on the system with the help of others, however I have two problems I cannot overcome.

1. I cannot play any dvd's 

2. I cannot play any windows based games using wine (to complicated to use) or play on linux and cedega (will play oblivion but with graphics errors).

I was wondering if any help could be given or advice on what to do, otherwise I think Linux is awesome very fast and stable. I just wish things I wanted to work on it would work.

---

### Post by sharks on 2008-06-14
R u getting any error when playing DVD? and have u installed games thru wine and tried playing it? and is the games r in the wine DB?

---

### Post by mdpalow on 2008-06-14
Playing DVD's is tricky business for new users to Ubuntu. 

You can use QuickStart (see my signature below) to do it all for you with the click of a button if you like.

Sorry, can't help yo with gaming other than to tell you it might be necessary to keep a copy of Windows running (dual boot) if you want to play games.

Good luck.

---

### Post by fr.theo on 2008-06-15
ATT: Sharks, I have errors reading dvd's also the games are on the wine db eg. command and conquer 3 tiberium wars, no mouse some times no game at all. I have both installed these game through wine and play on linux, including Cedega.

---

### Post by fr.theo on 2008-06-15
ATT: mdpalow, thank you for you help, I have installed the packages according to your instructions and then restarted my computer but to no avail, the dvd's still will not work.

I have noticed that the update begins but, no  pop ups or window is shown to signify progression of the update, it simply start an administrative task and then ends. not sure of what to make of it.


thanks for you help.

FR. T

---

### Post by mdpalow on 2008-06-15
> **fr.theo said:**
> ATT: mdpalow, thank you for you help, I have installed the packages according to your instructions and then restarted my computer but to no avail, the dvd's still will not work.

I have noticed that the update begins but, no  pop ups or window is shown to signify progression of the update, it simply start an administrative task and then ends. not sure of what to make of it.


thanks for you help.

FR. T

What packages are you talking about? What update are you talking about? Something doesn't sound right.

I was suggesting you download/install QuickStart. You can find the link below. There you can get the program, install it, and then run the option that installs the proper drivers/codecs in order to play dvd's.

You should see a progression bar going back and forth telling you what is being installed. 

Did you do all of this?

---

### Post by fr.theo on 2008-06-16
ATT: mdpalow,

I apologise for not making my self clear, I installed the software quick start according to the instructions posted on the site you directed me to go to.

once I intalled it I ran quickstart and selected "install proper DVD/Codex files" 

then a pop up appeared requesting the following "Would you like QuickStart to identify your Ubuntu OS and install the proper DVD/CODECS files?" I pressed yes.

then on the task bar the "starting Administration.." appeared then went away, that was it.

I presumed that the codex were installed so I restarted my machine and tried to run a DVD but the same problem occurred on totem media player and kaffine they would not play the dvd and VLC just terminates.

sorry for all the trouble, I appreciate you help.

FR. T

---

### Post by rraj.be on 2008-06-16
You can even get games for ubuntu specifically here.
Just try out if you wish.
we have a wide varirty of games for you.

```
[[COLOR="Blue"]http://www.ubuntugames.org/en/UbuntuGames[/COLOR]]("http://www.ubuntugames.org/en/UbuntuGames")
```


```
[[COLOR="Blue"]//https://help.ubuntu.com/community/Games[/COLOR]]("https://help.ubuntu.com/community/Games")
```

```
[[COLOR="Blue"]http://www.playubuntu.com/[/COLOR]]("http://www.playubuntu.com/")
```

```
[[COLOR="Blue"]http://packages.ubuntu.com/gutsy/games/[/COLOR]]("http://packages.ubuntu.com/gutsy/games/")
```

Regarding your DVD issue go here


you should install all Gstreamer codecs and  restricted extras.If possible install w32 codecs also.

go here to get them.

```
[[COLOR="Blue"]https://help.ubuntu.com/community/Medibuntu[/COLOR]]("https://help.ubuntu.com/community/Medibuntu")
```

Hope it helps you.

Further if you wish to play all windows based games it's better to go for a dual boot because you wont get complete support from wine for EVERY windows application's.many may not be compatible.

Just see here to install windows as dual boot.Its better option to get u satisfied completly even though it takes a 10GiB memory and one hour for instalation.

[[COLOR="Blue"]http:www.psychocats.net/ubuntu/installing[/COLOR]]("http://www.psychocats.net/ubuntu/installing")

---

### Post by crjackson on 2008-06-16
Try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Hardy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by fr.theo on 2008-06-16
thanks for all your help, it seems my ubuntu hardy is having trouble, I cannot access my administration tools, they start to run but after a short period nothing happens and no error messages.

even my update program wont work also add/remove program is also not responding.


when I try to download programs or update via these services the programs seem to be idle, I went to system monitor to see if it is active and it reports the program to be sleeping.

thanks again, if you know of any know issues regarding these problems it would be much appreciated.

FR.T.

---

### Post by rraj.be on 2008-06-16
We are here to help you but may take few minuets to solve your problem.

My Kind advice is "Dont post Duplicate thread's".

This may bring you Infraction's".

be cautious.

---

### Post by mdpalow on 2008-06-17
> **fr.theo said:**
> ATT: mdpalow,

I apologise for not making my self clear, I installed the software quick start according to the instructions posted on the site you directed me to go to.

once I intalled it I ran quickstart and selected "install proper DVD/Codex files" 

then a pop up appeared requesting the following "Would you like QuickStart to identify your Ubuntu OS and install the proper DVD/CODECS files?" I pressed yes.

then on the task bar the "starting Administration.." appeared then went away, that was it.

I presumed that the codex were installed so I restarted my machine and tried to run a DVD but the same problem occurred on totem media player and kaffine they would not play the dvd and VLC just terminates.

sorry for all the trouble, I appreciate you help.

FR. T

I think you should try it again based on what you've told me. In fact, try it twice in a row. Sounds like you needed an update after my install and it didn't get completed the first time around.

My suggestion is for you to try it twice in a row and install any updates. Please private message me in the future as I'm not watching this thread.

If it's DVDs for movies, QuickStart will work if there's no hardware issues. Try it again. :)

---

### Post by bufsabre666 on 2008-06-17
> **fr.theo said:**
> thanks for all your help, it seems my ubuntu hardy is having trouble, I cannot access my administration tools, they start to run but after a short period nothing happens and no error messages.

even my update program wont work also add/remove program is also not responding.

my system behaves this way before i install the proprietary graphics drivers, might i ask what is your graphic chipset? if you dont know post the result of

```
lspci -v
```

---

### Post by fr.theo on 2008-06-18
Hello, I am back with more problems, I am sure your all excited.

I am trying to get my IMate JasJam PDA to work with Ubuntu, any one have any Ideas.


Thanks again for all those who helped previously, this forum is ten times better than Microsoft help line.


FR. T.

---

### Post by hyper_ch on 2008-06-18
It is adviced to open for each seperate problema different thread. That way people konw what it's about and the thread can be marked as solved individually.

---

### Post by fr.theo on 2008-06-18
thanks just did, sorry about that, still new to the system

---

### Post by hyper_ch on 2008-06-18
> **fr.theo said:**
> thanks just did, sorry about that, still new to the system

you'll get better help that way ;)

---

### Post by sharks on 2008-06-18
Ya. Ubuntu is an OS which we can use easily.

---

### Post by letank on 2008-07-03
> **mdpalow said:**
> I think you should try it again based on what you've told me. In fact, try it twice in a row. Sounds like you needed an update after my install and it didn't get completed the first time around.

My suggestion is for you to try it twice in a row and install any updates. Please private message me in the future as I'm not watching this thread.

If it's DVDs for movies, QuickStart will work if there's no hardware issues. Try it again. :)

works, for DVDs, I spent all evening w the other refs..... Installed many apps twice.
HP omnibook XE4100 (8 year old laptop), feisty 7.04 and kernel 2.6.20-17

Cheers

Michel

---

