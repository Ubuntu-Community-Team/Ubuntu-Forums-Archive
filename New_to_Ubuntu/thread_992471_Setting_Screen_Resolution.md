---
title: "Setting Screen Resolution"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by suomalainen on 2008-11-24
Ubunteros,

Just as the UBUNTU login/password splash screen appears a message on my screen pops up stating to the effect that for optimal viewing my resolution should be set to 1440 X 900. 

However, when I go to  System>Preferences>Screen Resolution The best I can set my screen resolution to is:

Resolution = 1280 X 800

Refresh Rate: 60Hz

I have a HP x1907 (this is model)

How can I have the 1440 x 900 Resolution?

Thank YOU!

---

### Post by Kellemora on 2008-11-24
HI Suo

If I set my resolution that high, I would need a 50,000 power magnifying glass to read it!

Default is 800x600, but Ubuntu can't resize itself so it spills off the screen at that resolution.

I thought Ubuntu was configured now for 1024x768 as the optimal resolution?

If I jump up even one more size it becomes unreadable!

Already the clickboxes at that resolution are less than 1/8 inch square and very hard to hit with a mouse arrow.

However, you can go into Screens and Graphics and set the resolution from there to whatever your monitor will support.  
It's under Applications/Other from your Panel.
If not there, right click on Applications, then on Edit Menus and you can install it.

TTUL
Gary

---

### Post by coolethan on 2008-11-24
so what happens to those people who's computers won't open up screens and graphics for whatever reason under any circumstances? this is getting rediculous whith the massive screen res.

---

### Post by suomalainen on 2008-11-24
I don't know but the setting I have now doesn't look at all bad.

See attached pic.....

---

### Post by pi.boy.travis on 2008-11-24
What is your graphics card?  Do you have drivers available for it?  Check System>Administration>Hardware Drivers to see if there are any available for your card.

---

### Post by Olivier2371 on 2008-11-24
Sorry to drop in,

you seem to have a 19" widescreen monitor with maximum resolution of

1440x900. There for your monitor should be set to 1440x900.

---

### Post by pi.boy.travis on 2008-11-24
> **Olivier2371 said:**
> Sorry to drop in,

you seem to have a 19" widescreen monitor with maximum resolution of

1440x900. There for your monitor should be set to 1440x900.

Wish I had one of those. . . ;)

---

### Post by oldsoundguy on 2008-11-24
resolution has nothing to do with the OS but with the video drivers and the video display.  make sure you have the appropriate drives installed for your card ... and 800 x 600?  

Not many are using that any more:

[http://www.tamingthebeast.net/blog/web-development/monitor-resolution-statistics-0208.htm](http://www.tamingthebeast.net/blog/web-development/monitor-resolution-statistics-0208.htm)

mine is 1680 x 1050 and I can see things just fine ... but the monitor is 24" wide screen cinema display.

Currently the drivers for NVida are just basic .. no bells and whistles and they are taking forever to get them fixed for Intrepid.  NVida does not do drivers for anything that has not been off the shelf (out of production) for more than 6 months .. all the work is being done by Alberto and his crew at Envy now.

---

### Post by Olivier2371 on 2008-11-24
pi.boy.travis,

I have one of my desktops computer hook up to a 26" widescreen lcd hd tv,

running Ubuntu 8.10.

And my laptop as a 17" widescreen, dual booting vista and ubuntu 8.04.

---

### Post by pi.boy.travis on 2008-11-24
> **Olivier2371 said:**
> pi.boy.travis,

I have one of my desktops computer hook up to a 26" widescreen lcd hd tv,

running Ubuntu 8.10.

And my laptop as a 17" widescreen, dual booting vista and ubuntu 8.04.


I'm on a humble Dell Inspiron 1520 15in.  Intel C2D, 2 GB RAM. . . 

Glad we got that other guy with the lost data set straight, eh?

What's this, a coffee cup?!?!  HUZZAH!

---

### Post by Olivier2371 on 2008-11-24
pi.boy.travis  	

you know what they say, RTFM.

---

### Post by coolethan on 2008-11-24
i have a NVIDIA graphics card with the appropriate drivers installed and enabled. i used to be able to set my resolution in 7.1 no problem through screens and graphics. but screens and graphics doesn't open anymore and as far as i know this bug is not fixed yet. right now whenever i open somehting with a tall window i have to hit the tab button to move the selection down through the options and guess where the ok button is and then double check and try again

---

### Post by pi.boy.travis on 2008-11-24
> **coolethan said:**
> i have a NVIDIA graphics card with the appropriate drivers installed and enabled. i used to be able to set my resolution in 7.1 no problem through screens and graphics. but screens and graphics doesn't open anymore and as far as i know this bug is not fixed yet. right now whenever i open somehting with a tall window i have to hit the tab button to move the selection down through the options and guess where the ok button is and then double check and try again

I'm not quite sure I understand your problem. . . can you post a screenshot?

If you are using a widescreen monitor, make sure the "widescreen" tick box is checked.

---

### Post by Olivier2371 on 2008-11-24
Are you using 8.4 or 8.10?

---

### Post by coolethan on 2008-11-24
the windows spill out of the screen beyond where i can see and the mouse can reach, i am using 8.1 and not a widescreen.

---

### Post by Olivier2371 on 2008-11-24
What this screenshot for?

---

### Post by coolethan on 2008-11-24
pi.boy wanted me to post a screen shot because he didn't quite understand what i was saying. it shows the predicament i am in with my screen resolution. it won't go higher than 800x600 in the screen resolution thing and screens and graphics won't open so i can't select the monitor i have and set the resolution properly.

---

### Post by Olivier2371 on 2008-11-24
Are you sure you have the correct driver for your graphic adapter.

---

### Post by coolethan on 2008-11-25
i'm almost certain it is the right driver because when i put in the card it told me about drivers and blah blah blah and this is the one that automatically installed itself sorta thing. i did have a rage 128 graphics card before but the actual drivers shouldn't be the reason that screens and graphics won't open. i used the same monitor and graphics card in 7.1 and there was absolutely no problems using screens and graphics and now all of a sudden it won't respond at all. sometimes it makes like it's loading and starting up and even asks me for my password and then nothing nothing nothing.

---

### Post by Olivier2371 on 2008-11-25
sorry I've got problem understanding what you say.

What do you mean by "screens and graphics won't open".

---

### Post by coolethan on 2008-11-25
wow, ok i will explain this a little clearer. i click on applications then on "other", screens and graphics pops out to the side like normal and i select it from the menu. ok now listen carefully. after clicking on "screens and graphics" a thing pops up on the bottom bar on my screen and it says "initializing screens and graphics" or something to that effect. then that thing goes away and nothing happens ok, sometimes it askes me for my password but in the end absolutely nothing happens. I will repeat myself a little bit here just to make sure that everyone understands what is going on. NOTHING HAPPENS! there is no GUI that pops up not window it simply stops processing my command or something and NOTHING happens. i hope i made it clearer for you. sorry if i'm coming accross as a bit of an a@$ hole but after a million hours of google and ubuntu forum research there are absolutely no answers and when i start a thread about this, it drops off the face of the earth because nobody replies. i'm getting a little bit peeved if you know what i mean.

---

### Post by pi.boy.travis on 2008-11-25
If you are using 8.10, it is because 8.10 has eliminated the X.conf file.  It is all automatic now.  If you have a legacy Nvidia card, they are no longer supported in 8.10, so I would recommend a regression to 8.04.  You will have to back up your files and do a clean install.

---

### Post by coolethan on 2008-11-25
nope i'm still on 8.04 hardy heron. i've searched for an answer before and this is the best one i've found or the only one. [HTML]http://ubuntuforums.org/showthread.php?t=969941&highlight=screens+graphics[/HTML]

notice all the wonderful help i got, it astounds me how much support you guys give around here. i'm pretty sure it doesn't have anything to do with my graphics card, in 7.1 i used to be able to open screens and graphics with the same graphics card and now theres a glitch or a bug or something and i'm the only person in the world who has it.

---

### Post by suomalainen on 2008-11-26
Well, I did outline in the beginning of my post what it is that I want to do.... But the selection required is not available for one reason or another...

This is real strange because I have another PC with a LG screen requiring the 1440X900 and Ubuntu found it during a new install of 8.04LTS right away BUt with this other machine I have it doesn't even want to let me select 1440 X900 as it isn't available and yet the 2 o/s's are the same....

So please stay and have as much coffee as you like.....

---

### Post by coolethan on 2008-11-26
The day has finally arrived! i have solved my resolution problem, ubuntu didn't offer me a resolution above 800x600 and my screens and graphics GUI would not run so i tried something different. i loged in as root and added screens and graphics to the menu. still loged in as root i tried to open up S&G and it worked! i selected my monitor and graphics card from the list and choose the appropriate screen resolution. the only thing was that it wouldn't take into effect when i logged off which it is supposed to do. so i got a pretty good surprise today when i turned on my computer.the resolution was sooo huge it spilled out of my screen but i could scroll to the side and to the top and bottom by moving the mouse, as opposed to having my screen spill out of the monitors field of vision and not being able to access anything beyond it. so i just made a small adjustment and refit the screen size to fit my monitor and now i am a happy man.

---

### Post by joesky on 2008-11-28
I have am using v 8.10 with a Samsung 191T monitor.  The only screen size I can use with Ubuntu is 800x600.  I would like 1024x1280.  How do I do that? I read in this thread that I should do as follows:
[I]
i loged in as root and added screens and graphics to the menu. still loged in as root i tried to open up S&G and it worked![/I]

I have no idea how to do that.  But would like to learn. I guess that the "screens and graphics" option was dropped from 8.10, but I really wish it was there.

Thanks

---

### Post by Justin Pentecost on 2008-11-28
I also Have this problem with intrepid and an HP w1907v monitor .. what it want's is 1440x900 at 60hz .. and all other resolutions give the wrong aspect ratio and very soft images.

This is not an Ubuntu or Linux problem exclusively (AFAIK).   I bought the monitor not realising how non standard it was ..  I ended up having to buy a new graphics card to make it work with Win2000 on my old computer (then I bought a new computer "Designed for Windows Vista" with vista pre loaded .. I could rant for days.)   Then I tried to reinstall win 2000 which worked but had no drivers (so I lived without sound) .. 

Now I have an Nvidia 512mb graphics card and 8.10 installed and this monitor .. 

HELP !!

Justin

---

### Post by suomalainen on 2008-11-28
Justin Pentecost, Looks like we got the same monitor and issue?

My LG offers the choice we need but HP does not.....

---

