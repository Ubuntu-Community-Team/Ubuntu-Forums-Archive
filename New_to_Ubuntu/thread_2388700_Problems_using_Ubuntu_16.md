---
title: "Problems using Ubuntu 16"
date: 2018-04-06
forum: New to Ubuntu
---

### Post by dave1956 on 2018-04-06
Hi all
I have moved from Ubuntu 12 to Ubuntu 16.  In Ubuntu 12 on the lower right hand of the screen there was like a little earth globe icon which I had made to quick link to one of my OpenOffice calc files (the one for my accounts) that is now missing in Ubuntu 16 along with the grey (task bar) which was handy to jump from calc to letter or letter or folder, as you could see what all was running or being used at one time.  Has this been removed or have I failed to turn it on.

As for that side bar thing (on the left) which I set to auto-hide, it likes playing hide and seek with me, it hides better than I can seek or find it, grr ...:mad:

With the help from yancek and others I have so far fixed the grub file, found and restored my book marks that I forgot to backup and restored all of my passwords to firefox

So, has the grey bar at the bottom of the screen been removed or hidden or am I too thick to use a computer ??? :lolflag:

Dave

---

### Post by Frogs Hair on 2018-04-06
If using Unity there should be no panel on the bottom of the screen. Use the following check.

```
echo $XDG_CURRENT_DESKTOP
```

---

### Post by dave1956 on 2018-04-07
I have just read Ubuntu Unity is Dead........which is a good thing, now I can get back the bar at the bottom of the screen to be able to move from one page of work to a different one with having to close them down to reopen them
So when is Ubuntu 18LTS being released April 2018 which we are now in

Dave

---

### Post by Frogs Hair on 2018-04-07
There is a community effort to maintain Unity in the repository and it will be available as maunually installed session for 18.04 though Canonical will no longer develop it. The Unity session will remain on systems upgraded from 16.04 to 18.04 AFIK.There are also other Unity forks looking for developers.   


[https://wiki.ubuntu.com/BionicBeaver/ReleaseSchedule](https://wiki.ubuntu.com/BionicBeaver/ReleaseSchedule)

---

### Post by Geoffrey_Arndt on 2018-04-07
Ubuntu Mate would provide a default panel at the bottom that shows "open apps".    The LibreOffice or OpenOffice - also shows the most recently accessed files - - so that's only two clicks away.

---

### Post by dave1956 on 2018-04-08
Hi Geoffrey for that, I have tried to install it, "Ubuntu Mate" but, just as a few other things it does NOT work, others being google earth and Stellarium and that stupid daft bar on the left hand side.
The one other thing I have noticed is how much slower 17 is compared to ver 12 of Ubuntu.
And at a guess, frogs hair would be a big fan of Unity ?  I don't know or understand what Unity does or does not do in Ubuntu, but I have to say that in my mind or IMHO Ubuntu has gone backwards, maybe a more stripped down version which 18 looks like may be a better option

Dave

---

### Post by Frogs Hair on 2018-04-08
> And at a guess, frogs hair would be a big fan of Unity ? No, just pointing out that it is not dead. I used the all the Unity releases along with other desktop environments with Budgie being of great interest at the moment. It has a bottom panel option and loads  of panel applets which can be placed where you want them . Budgie has a dock, but it can be disabled.

If you want more of a traditional look and feel check out Xubuntu, Ubuntu Mate or Kubuntu from a live usb or dvd.

---

### Post by monkeybrain20122 on 2018-04-08
> **dave1956 said:**
> Hi all
I have moved from Ubuntu 12 to Ubuntu 16.  In Ubuntu 12 on the lower right hand of the screen there was like a little earth globe icon which I had made to quick link to one of my OpenOffice calc files (the one for my accounts) that is now missing in Ubuntu 16 along with the grey (task bar) which was handy to jump from calc to letter or letter or folder, as you could see what all was running or being used at one time.  Has this been removed or have I failed to turn it on.

As for that side bar thing (on the left) which I set to auto-hide, it likes playing hide and seek with me, it hides better than I can seek or find it, grr ...:mad:

With the help from yancek and others I have so far fixed the grub file, found and restored my book marks that I forgot to backup and restored all of my passwords to firefox

So, has the grey bar at the bottom of the screen been removed or hidden or am I too thick to use a computer ??? :lolflag:

Dave

Because openoffice is no longer installed. Now Ubuntu comes with Libreoffice, you have a grey box when the software is no longer installed after "upgrade".  Upgrade is generally problematic and even if not outright broken some old config files might interfere with the new system, especially if the old and new are 4 years apart so much has changed. I generally advise against "upgrade", it takes hours and even if it appears to work, some hidden gotcha may lie about without you knowing and manifest as hard to diagnose problems down the road. I really recommend saving your data and do a clean install, that would automatically fix a lot of problems.

---

### Post by Frogs Hair on 2018-04-08
> [COLOR=#000000]I really recommend saving your data and do a clean install, that would automatically fix a lot of problems.[/COLOR]

^This^ 

Wait a few weeks try Ubuntu 18.04 and flavors and install what you like most.

---

### Post by dave1956 on 2018-04-10
Hi frogs hair,, back again...err I have been looking at a few of the points raised here on this thread about clean install ver upgrade and what is new in ver 18lts due release soon.
My old ver of Ubuntu 12 was very stable, I do have a screen shot of what it looked like with every thing up in the top left hand of the screen in the grey bar. I would show it to you only now after trying to install Ubuntu Mate, the mouse pointer is on speed jumping all over the place... Hence back to the wife's chrome book when she is in bed.


At this point in time I would have to join in with monkeybrain20122 do not upgrade but a clean install and not as stated on the "Its Floss, whats new in Ubuntu 18.04 LTS page" The upgrade procedure is mainly painless and all you have to do is to follow the on-screen suggestions. You must have a good internet connection though. and There has been no significant change in the default Ambiance theme of Ubuntu for years. It looks more or less the same in last several Ubuntu releases. Really ??? I don't think so?


The other thing I want to ask you is, if, Unity is going to be, no longer the default desktop environment for Ubuntu anymore.. I don't see a difference between it and ver 16LTS as the daft bar is still on the left 
The other point you made was to leave the new version for a few weeks and then install it and try what flavors I like, If I can get it to install, with gimp, Stalluium google earth and LidreOffice where I can see more than one open letter / spread sheet and the mouse not jump about, I will be happy
So a clean install it will be and with the help I got here I do NOW have all my files backed up ready for the new Clean Install


Dave

---

### Post by Frogs Hair on 2018-04-10
Gnome also has a bar on the left on 18.04 that's why I suggested trying the other Ubuntu [flavors]("https://www.ubuntu.com/download/flavours") before installing. If you are running 12.04 it is no longer supported and a security risk. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

To find out what release you are using post the output of the following command.```
lsb_release -a 
```

The applications you inquired about are all available with 18.04.

---

### Post by monkeybrain20122 on 2018-04-11
> **dave1956 said:**
> 
The other thing I want to ask you is, if, Unity is going to be, no longer the default desktop environment for Ubuntu anymore.. I don't see a difference between it and ver 16LTS as the daft bar is still on the left 



Actually since Ubuntu 16.04 you can move the bar to the bottom. :) Not that I think you sound like a big fan,  but just to note that unity even is not default in 18.04, it is still easily installable just one sudo apt install away. :)

Also Google-earth is now a webpage [https://earth.google.com/web](https://earth.google.com/web) but only works in Chrome. But with Chrome you can easily make a webapp which needs no installation (though there is a google-earth-pro package you can install if you want to, but not sure if it works in 18.04, never tested it)

---

### Post by dave1956 on 2018-04-11
> **Frogs Hair said:**
> 

To find out what release you are using post the output of the following command.```
lsb_release -a 
```

The applications you inquired about are all available with 18.04.

Oh dear,  bit hard to do that Frogs Hair, like I said, the mouse is on speed, 9 times out of 10 the computer is totally UN-usable due to the mouse pointer jumping all over the place, creating folders opening files and drives, it can do more in 10seconds that the video showing Ubuntu 18.04 LTS with out me touching the mouse.

What flavor would you recommend ? L-Ubuntu or X-Ubuntu "don't like them,  Ubuntu 18.04 looks just about right when less is MORE: 

Dave

---

### Post by dave1956 on 2018-04-11
> **monkeybrain20122 said:**
> 

Also Google-earth is now a webpage [https://earth.google.com/web](https://earth.google.com/web) but only works in Chrome. But with Chrome you can easily make a webapp which needs no installation (though there is a google-earth-pro package you can install if you want to, but not sure if it works in 18.04, never tested it)

If google earth is now a web-page ? can or could I still replace or keep my markers POI's of different markers that I have put together over the years ? now that I found them and have them backed up..I also have an older version of google earth stable downloaded, wonder could that version be installed rather than a web-page ??

Did you know that the daft bar first appeared in windows office 97, it was hid way back in the background and could also be moved all round the screen, but don't say I told you that....](*,)

And I see they have put the box the X and the - things back to the right hand side, rumour had it, tha t whats his name who ran and setup Mac computers was left handed hence the X, the box and the other were on the left hand side of the screen...

Dave

---

### Post by Frogs Hair on 2018-04-12
Please tell us what exactly what we can help with. As already addressed here there are alternatives to the Gnome Shell and Unity desktops.

If you don't care for Xubuntu or Lubuntu there is Kubuntu,Ubuntu Mate, and Budgie. There is a google-earth package for 17.10 and I suspect it will be updated for 18.04 .

---

### Post by monkeybrain20122 on 2018-04-12
> **dave1956 said:**
> If google earth is now a web-page ? can or could I still replace or keep my markers POI's of different markers that I have put together over the years ? now that I found them and have them backed up..I also have an older version of google earth stable downloaded, wonder could that version be installed rather than a web-page ??




As I said there is also google-eath-pro now works for Linux. [https://www.google.com/earth/download/gep/agree.html](https://www.google.com/earth/download/gep/agree.html)
But never tested it on 18.04, works on 16.04 though, not sure about your settings, it probably would respect that I guess. Every now and then there are people posting threads about problems with installing GE, just wanted to point out now there is a way which doesn't require any installation (the webpage/webapp)

---

### Post by dave1956 on 2018-04-14
> **Frogs Hair said:**
> Please tell us what exactly what we can help with. As already addressed here there are alternatives to the Gnome Shell and Unity desktops.

If you don't care for Xubuntu or Lubuntu there is Kubuntu,Ubuntu Mate, and Budgie. There is a google-earth package for 17.10 and I suspect it will be updated for 18.04 .

Ah, I have just looked at Ubuntu Mate, THAT looks what I have run for the past X number of years.. So I am going to give it a clean install and hopefully I will not wipe out XP as I had to use it yesterday as this ver of Ubuntu would not print for me
Yes the mouse has come off speed I UN-installed something

Returning to, Ubuntu Mate and quoting vwhillbilly  "When is the next LTS Mate due out ?"

Dave

---

### Post by Frogs Hair on 2018-04-14
> [COLOR=#000000]Returning to, Ubuntu Mate and quoting vwhillbilly "When is the next LTS Mate due out ?"[/COLOR]

April 26 , good journey with Mate it's most like the pre-unity Ubuntu releases. :)

---

### Post by dave1956 on 2018-04-14
> **Frogs Hair said:**
> April 26 , good journey with Mate it's most like the pre-unity Ubuntu releases. :)

Hi frogs hair, ya I am running the live DVD now using Ubuntu Mate, I must say I do like it more than Ubuntu with the daft bar, "sorry but, just have to get that in".  Yip come mid May I will do a clean install and hopefully I will not run into too many problems, or at least one's this time round I may be able to fix error with grub etc

Dave

---

