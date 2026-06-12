---
title: "[SOLVED] I don't understand what has happened,,"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by sayakb on 2008-05-25
I have 2 desktops, one running Gutsy (Q6600, 4GB DDR3,8800GTX)
Other one is a very old one having a Celeron 633MHz (that too after "upgrading" :lolflag:), 384MB RAM, intel i810 mobo.

Now taking into consideration the second one here. About 5-6 years back, this old PC had a celeron 550MHz, 256MB RAM and a 20GB HDD had a old RedHat Linux 4.7 (not sure about the version). It had a very good UI with both Gnome and KDE installed. But now, when I have a little more RAM and a faster processor :lolflag: the so called light environments like XFCE struggle to run, while XP runs very smoothly indeed. Other so called "lite" distros are so ugly that RedHat 4.7 looked much better than these. I really need to make my parents use XP to the minimum extent. I need a good looking, yet light distro (fluxbox is very ugly, and all I had is a panel with four arrows and a clock) Please suggest me something that would replace Xubuntu 7.10.
So:
1. I need a link to a light linux distro that is good looking :D
2. Secondly, I am presently dual booting Xubuntu with XP, Xubuntu being on a 7.4GB partition. I shall erase the partition and install the prescrived linux on it. So it should detect and access XP correctly.

EDIT: Topic of this thread was kept keeping in mind the beautiful RedHat 4.7 and the ugly fluxbox.

---

### Post by EXCiD3 on 2008-05-25
With a little customization you can get an openbox desktop looking beautifully and it is the same idea of fluxbox. you have NOTHING on screen by default making it a VERY very clean appearance. you can then add things such as a panel for your applications. I will upload a screenshot of my openbox desktop in a few. Running openbox on an install of Ubuntu 8.04 uses 117mb of ram. :)

---

### Post by sayakb on 2008-05-25
So can I just use the existing Xubuntu 7.10 install? PLus is there any tutorial on how to customize openbox? :)

---

### Post by EXCiD3 on 2008-05-25
You sure can just install openbox on your xubuntu install! :) Just search the repositories for "openbox" or run this in terminal to install it and its themes: ```
sudo apt-get install openbox openbox-themes
```

Customizing Openbox links:
[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/) (what i used)
[http://ubuntuforums.org/showthread.php?t=192106](http://ubuntuforums.org/showthread.php?t=192106)

Also i forgot to mention for my panel, im using the supplied gnome-panel from a standard Ubuntu intsall and i use nautilus still for file browsing, yet you can use ANYTHING you want! Its so very customizable! I think thats part of the reason why all the really neat and clean looking linux desktops ive seen are running openbox because its so customizable and simple.

You will probably want to make sure you install ObMenu (which you will have to compile from source, but its super easy) so that you can add program options to your openbox menu. Its much easier than editing the config file and adding your programs that way, but all this is covered in the tutorials. Have fun!

---

### Post by sayakb on 2008-05-25
Thank you very much. I would start working on it asap. 
Thanks again
Dave
=D>

---

### Post by EXCiD3 on 2008-05-25
No problem. Ever since i started using it, i havent been able to switch back to Gnome or KDE...because they are just so unclean and bloated (even though ive got 1.83ghz core 2 duo and 2gb of ram its nice to know i could run the same setup on just about any computer if i wanted)

Don't forget to mark your thread as solved, and feel free to hit me up on IM if you want to chat about anything! :)

---

### Post by sayakb on 2008-05-25
I will contact you if I need any further guidance. :)
Thanks

---

### Post by Inxsible on 2008-05-25
Yet another lite WM is Enlightenment and the DR17 is said to have a lot of eye candy too. There is also a distro that they are promoting, if you don't want to go thru the hassle of installing a minimal with E17. Its called OzOs, and the best part is that it is built on a variation of Ubuntu.....well Xubuntu to be precise.

---

### Post by sayakb on 2008-05-26
> **EXCiD3 said:**
> No problem. Ever since i started using it, i havent been able to switch back to Gnome or KDE...because they are just so unclean and bloated (even though ive got 1.83ghz core 2 duo and 2gb of ram its nice to know i could run the same setup on just about any computer if i wanted)

Don't forget to mark your thread as solved, and feel free to hit me up on IM if you want to chat about anything! :)

I am facing problems setting up desktop icons. I use Xubuntu, so I don't have nautilus. Neither can I get ROX to work. How do I make icons show up on the desktop. 
Otherwise, I am using XFCE panel (since the fbpanel takes long time to load) I am using 80MB of RAM (ONLY!!!) and that too including Opera (I got rid of Firefox). Just the desktop icon issue now..

EDIT: Managed to use ROX. Problem solved :D

---

### Post by EXCiD3 on 2008-05-26
> **LinuxIsInnovation said:**
> I am facing problems setting up desktop icons. I use Xubuntu, so I don't have nautilus. Neither can I get ROX to work. How do I make icons show up on the desktop. 
Otherwise, I am using XFCE panel (since the fbpanel takes long time to load) I am using 80MB of RAM (ONLY!!!) and that too including Opera (I got rid of Firefox). Just the desktop icon issue now..

EDIT: Managed to use ROX. Problem solved :D

Glad you got it working, only 80mb!!! Thats pretty impressive! If i ever get the chance i will upload a screenshot for you to check out my openbox setup. :D

---

### Post by sayakb on 2008-05-27
> **EXCiD3 said:**
> Glad you got it working, only 80mb!!! Thats pretty impressive! If i ever get the chance i will upload a screenshot for you to check out my openbox setup. :D

Though I have got it working, but the ROX desktop seems useless. Seems like I can't get to have the files within /home/myusername/Desktop on the desktop. Also, I am using thunar with OpenBox. Now since I have a ROX desktop, in order to drag n drop something on the desktop, either:
1. I have to launch Thunar using any ROX launcher.
or
2. I have to launch a ROX file manager and drop it from there.

If I call thunar from the terminal, it would not drop the icons on the desktop (the icons seem to prevent being dropped on the desktop). Also, the ROX filemanager somewhat lacks a File menu, and the capability to change folder icons (or you might say, I haven't yet learned how to do so ;) )
Can you help me out with ROX with these issues:
1. Desktop management
2. Icon and menu customization

---

### Post by sayakb on 2008-05-27
Regarding the panel, I had been using fbpanel (since I strictly stick to the debians, and I was getting only source downloads for other "lite" panels). Fbpanel has the following problems in my case:
1. Takes 5-6 seconds to load (as it flickers about 4-5 times before it loads). Even the XFCE panel loads immediately, but it uses much more resources that fbpanel (but I don't seem to have a choice either :( )
2. I can't seem to change its color from black which looks ugly.

---

### Post by EXCiD3 on 2008-05-27
Check out this for configuring fbpanel: [http://fbpanel.sourceforge.net/docs.html#configuring](http://fbpanel.sourceforge.net/docs.html#configuring)

I've never used it, i use pypanel, its super easy to install, but since ive gone back to using gnome-panel...

I havent used ROX either, but on their website it says that ROX Desktop cannot actually store files, but links to file locations instead [http://roscidus.com/desktop/node/169](http://roscidus.com/desktop/node/169)

---

### Post by sayakb on 2008-05-27
If not ROX, then what should I use, since Thunar doesn't give me desktop icons..

---

### Post by inportb on 2008-05-27
I would try Enlightenment. Check: [http://timony.com/mickzblog/2008/04/15/e17-on-ubuntu-revisited/](http://timony.com/mickzblog/2008/04/15/e17-on-ubuntu-revisited/)

---

### Post by sayakb on 2008-05-27
Also, looks like fbpanel will remai black in my case. The Tint for fbpanel works with compositing and hence, I can't have it.. (cant dream of compositing on the old PC of mine!)

---

### Post by sayakb on 2008-05-27
> **inportb said:**
> I would try Enlightenment. Check: [http://timony.com/mickzblog/2008/04/15/e17-on-ubuntu-revisited/](http://timony.com/mickzblog/2008/04/15/e17-on-ubuntu-revisited/)
Wow.. that is the default theme? That looks good. I would keep that side-by-side of Openbox..

EDIT: Btw, I hope enlightment doesn't require compositing? I have an i810 mobo with a pathetic onboard VGA.. so no chances of compositing..

---

### Post by EXCiD3 on 2008-05-27
Here is stuff on the openbox wiki about desktop icons: [https://help.ubuntu.com/community/Openbox#head-f96c5c2cdf7fc1748cf358fc2dfa04278f2c83fc](https://help.ubuntu.com/community/Openbox#head-f96c5c2cdf7fc1748cf358fc2dfa04278f2c83fc)

and i think enlightenment supports compositing but it doesnt require it.

---

### Post by jviscosi on 2008-05-27
> **LinuxIsInnovation said:**
> If not ROX, then what should I use, since Thunar doesn't give me desktop icons..

In addition to the stuff in the OpenBox wiki, you can also use fbdesk to get desktop icons.  I recall it as pretty light, but somewhat clunky to set up.  I don't remember if you can drop icons onto it.  (I run OpenBox with no desktop icons.)

> **LinuxIsInnovation said:**
> Also, looks like fbpanel will remai black in my case. The Tint for fbpanel works with compositing and hence, I can't have it.. (cant dream of compositing on the old PC of mine!)

I use fbpanel and can change the colors (right now I have it transparent so all you see are the icons) without using compositing.  Are you unable to edit the fbpanel profile to change the color?  Maybe I don't understand what problem you're experiencing.

---

### Post by EXCiD3 on 2008-05-27
> **jviscosi said:**
> I use fbpanel and can change the colors (right now I have it transparent so all you see are the icons) without using compositing.  Are you unable to edit the fbpanel profile to change the color?  Maybe I don't understand what problem you're experiencing.

Yeah im not sure if its something other than just modifying the config file. If it is, can you post a screenshot?

---

### Post by inportb on 2008-05-27
> **LinuxIsInnovation said:**
> Wow.. that is the default theme? That looks good. I would keep that side-by-side of Openbox..

EDIT: Btw, I hope enlightment doesn't require compositing? I have an i810 mobo with a pathetic onboard VGA.. so no chances of compositing..

Yep, that is the default theme. You can make it nicer with add-ons, but the philosophy of the Enlightenment dev team is to make *lightweight* eyecandy.

Compositing is not required. There are packages that provide compositing support, like bling (xcompmgr on EFL) and ecomorph (compiz-like stuff), and they only enhance the experience. Even without compositing, Enlightenment is lightweight, fast, and beautiful.

---

### Post by jviscosi on 2008-05-27
> **EXCiD3 said:**
> Yeah im not sure if its something other than just modifying the config file. If it is, can you post a screenshot?

Sure, here you go. This is relatively old but I happened to have it handy.  That's fbpanel down the right side.

---

### Post by sayakb on 2008-05-28
Seems like the fbpanel problem is solved. Though I would be trying out enlightment now. I would post if I face any problems. 
Thanks :)

---

### Post by tylerspaska on 2008-05-28
I like new new version of Dreamlinux. It looks good and it's dumb simple (if you're into that).

---

### Post by deysub on 2008-05-28
I am getting following message:

maillog ignored: nsmail-vps popper[23153]: nc150 at 192.168.201.226 (192.168.201.226): -ERR POP EOF or I/O Error [popper.c:820]

is this a error. why this occurs and what is the solution?

Please help.

Thanks

---

### Post by inportb on 2008-06-01
> **deysub said:**
> I am getting following message:

maillog ignored: nsmail-vps popper[23153]: nc150 at 192.168.201.226 (192.168.201.226): -ERR POP EOF or I/O Error [popper.c:820]

is this a error. why this occurs and what is the solution?

Please help.

Thanks

Looks like a networking thing to me. You should start a new thread instead of hijacking somebody else's. And be sure to provide more information.

---

### Post by sayakb on 2008-06-01
> **deysub said:**
> I am getting following message:

maillog ignored: nsmail-vps popper[23153]: nc150 at 192.168.201.226 (192.168.201.226): -ERR POP EOF or I/O Error [popper.c:820]

is this a error. why this occurs and what is the solution?

Please help.

Thanks

Post a new thread. And do mention ***when** *are you getting this error.

---

### Post by EXCiD3 on 2008-06-01
Hey, hows enlightenment going? I've yet to try it and havent had time to download it all on dialup here!

---

### Post by sayakb on 2008-06-01
> **EXCiD3 said:**
> Hey, hows enlightenment going? I've yet to try it and havent had time to download it all on dialup here!

I'm sticking to OpenBox, though I seriously miss a direct shutdown/restart launcher/menu option.
Enlightment gave me 2 boxes and an empty panel. Need a screenshot? :)

---

### Post by EXCiD3 on 2008-06-01
Screenshot would be nice! What do you mean "direct" option for shutdown, etc?

---

### Post by Rui Pais on 2008-06-02
> **EXCiD3 said:**
> Screenshot would be nice!

Here a thread on that topic:
[http://ubuntuforums.org/showthread.php?p=4383444](http://ubuntuforums.org/showthread.php?p=4383444)

And several screenshots from get-e site:
[http://www1.get-e.org/Screenshots/User_Submitted/index.html](http://www1.get-e.org/Screenshots/User_Submitted/index.html)

Just to pick some more or less randomly. 
A lot of diversity ;)

---

### Post by sayakb on 2008-06-02
Very nice screenshots :) Thank you :D\
[This ]("http://www1.get-e.org/Screenshots/User_Submitted/_previews/winter-e17.png.html")is beautiful ;)

---

### Post by sayakb on 2008-06-02
> **EXCiD3 said:**
> Screenshot would be nice! What do you mean "direct" option for shutdown, etc?

Check the screenshots on my Wiki page. Theres one running OpenBox there:
[https://wiki.ubuntu.com/Dave701](https://wiki.ubuntu.com/Dave701)

Also, yes, I would like a direct shutdown/reboot option. I have made a Logout by creating a launcher that kills openbox, hence logging me out. But I cant seem to create a launcher for shutdown/reboot which doesn't need to be issued as superuser (CLI command sudo shutdown -h now). Is there some applet/plugin I could use?

---

### Post by jviscosi on 2008-06-02
> **LinuxIsInnovation said:**
> I have made a Logout by creating a launcher that kills openbox, hence logging me out.

You can also add a menu item with an action of exit, rather than killing OpenBox.  (I'm not sure if killing OpenBox is really anything different from what the exit action does internally.)

> 
      <item label="Exit">
        <action name="Exit" />
      </item>


---

### Post by durand on 2008-06-02
I'd also recommend enlightenment DR17. Its the only desktop/wm of the lightweight desktops that I can use properly without having to configure anything.

---

### Post by Inxsible on 2008-06-02
> **LinuxIsInnovation said:**
> Check the screenshots on my Wiki page. Theres one running OpenBox there:
[https://wiki.ubuntu.com/Dave701](https://wiki.ubuntu.com/Dave701)

Also, yes, I would like a direct shutdown/reboot option. I have made a Logout by creating a launcher that kills openbox, hence logging me out. But I cant seem to create a launcher for shutdown/reboot which doesn't need to be issued as superuser (CLI command sudo shutdown -h now). Is there some applet/plugin I could use?

Hey.. are you sure the Openbox screenshot is not running Thunar? It looks like Thunar to me.  I thought Rox-Filer was much more sparse.

---

### Post by sayakb on 2008-06-02
The desktop icons are through ROX-filer. I have created a launcher which calls thunar with the argument as my home directory's path.
I use this combination because of two problems:
1. ROX filer is too minimalistic
2. I cant seem to get desktop icons with thunar (which purpose was served by ROX)

Plus, looks like thunar is going easy on the system too :)

Heres a [screenshot]("http://i27.tinypic.com/2rekyld.png").

---

### Post by Inxsible on 2008-06-02
> **LinuxIsInnovation said:**
> The desktop icons are through ROX-filer. I have created a launcher which calls thunar with the argument as my home directory's path.
I use this combination because of two problems:
1. ROX filer is too minimalistic
2. I cant seem to get desktop icons with thunar (which purpose was served by ROX)

Plus, looks like thunar is going easy on the system too :)

Heres a [screenshot]("http://i27.tinypic.com/2rekyld.png").

yup... thunar is pretty easy on the system.  I just installed a minimal and then added the e17 from cvs...just did that last night...so haven't played much with it..

---

### Post by sayakb on 2008-06-02
> **jviscosi said:**
> You can also add a menu item with an action of exit, rather than killing OpenBox.  (I'm not sure if killing OpenBox is really anything different from what the exit action does internally.)

Yepp.. works fine :D

---

### Post by sayakb on 2008-06-02
> **durand said:**
> I'd also recommend enlightenment DR17. Its the only desktop/wm of the lightweight desktops that I can use properly without having to configure anything.

I installed Enlightment from the repos. Is there a debian resource that I can use?

---

### Post by Inxsible on 2008-06-02
> **LinuxIsInnovation said:**
> I installed Enlightment from the repos. Is there a debian resource that I can use?

 [COLOR=Red]Shamelessly ripped from Rui Pais installation guide[/COLOR] :)
1) Add the following repos to your /etc/apt/sources.list:```
deb http://cafelinux.org/Downloads/oz-os tinwoodman main 
```  OR you can do it via terminal by executing the following command ```
sudo sh -c "'deb http://cafelinux.org/Downloads/oz-os tinwoodman main' >> /etc/apt/sources.list"
``` 2) Get the authentication key for the repo```
wget -q http://cafelinux.org/Downloads/oz-os/key.asc -O- | sudo apt-key add -
```3) Finally, install it using```
sudo apt-get update && sudo apt-get install e17-cvs
```

---

### Post by Rui Pais on 2008-06-02
> **LinuxIsInnovation said:**
> Very nice screenshots :) Thank you :D\
[This ]("http://www1.get-e.org/Screenshots/User_Submitted/_previews/winter-e17.png.html")is beautiful ;)

No prob :)
Yes winter it's a beautiful theme and have very nice and delicate animations you can't see on screenshots (buttons on window bars and pager on change of desktop).

> **LinuxIsInnovation said:**
> I installed Enlightment from the repos. Is there a debian resource that I can use?


> **Inxsible said:**
> [COLOR=Red]Shamelessly ripped from Rui Pais installation guide[/COLOR] :)
...

No need to shame (or absence of shame) ;)
Hope you find it useful.

The only important part you shouldn't had rip is the one the important warning about repos mixing.
It's important not mix different ways and/or different repos to install e17, or problems may appear. 

Good luck on installation :)

---

### Post by EXCiD3 on 2008-06-02
> **LinuxIsInnovation said:**
> Check the screenshots on my Wiki page. Theres one running OpenBox there:
[https://wiki.ubuntu.com/Dave701](https://wiki.ubuntu.com/Dave701)

Also, yes, I would like a direct shutdown/reboot option. I have made a Logout by creating a launcher that kills openbox, hence logging me out. But I cant seem to create a launcher for shutdown/reboot which doesn't need to be issued as superuser (CLI command sudo shutdown -h now). Is there some applet/plugin I could use?

You have to edit the sudoers file to allow the "sudo shutdown -h now" to work ok in your openbox menu. I got suspend, shutdown, reboot, and hibernate added to mine. Heres a quick tut: [http://kmandla.wordpress.com/2007/10/27/howto-shut-down-linux-from-the-openbox-right-click-menu/](http://kmandla.wordpress.com/2007/10/27/howto-shut-down-linux-from-the-openbox-right-click-menu/)

---

### Post by sayakb on 2008-06-03
Thanks too Inxsible, Rui Pais and EXCiD3.. I think I'll try E17 on my laptop and OpenBox on the desktop :)
Thnks again 

Dave

---

### Post by Inxsible on 2008-06-03
> **LinuxIsInnovation said:**
> Thanks too Inxsible, Rui Pais and EXCiD3.. I think I'll try E17 on my laptop and OpenBox on the desktop :)
Thnks again 

Dave
You won't regret it !!

I know I have installed it only a couple of days back...but I am loving the fact that its fast AND it has quite a bit of eye candy.

Firefox doesn't take up 108MB with 2 tabs -- like it does in my Xubuntu install in the same machine.

Once I set up E17 - the way I like it, I am gonna get rid of Xubuntu completely.

---

### Post by EXCiD3 on 2008-06-03
> **Inxsible said:**
> You won't regret it !!

I know I have installed it only a couple of days back...but I am loving the fact that its fast AND it has quite a bit of eye candy.

Firefox doesn't take up 108MB with 2 tabs -- like it does in my Xubuntu install in the same machine.

Once I set up E17 - the way I like it, I am gonna get rid of Xubuntu completely.

Man you are making me anxious to install e17 now...gotta get to highspeed internet fast!

Note to self: When buying a house, first thing to check is if highspeed internet is available. My parents failed that portion...

---

### Post by Inxsible on 2008-06-03
> **EXCiD3 said:**
> Note to self: When buying a house, first thing to check is if highspeed internet is available. My parents failed that portion...LOL !!

You still can't get yourself a new set of parents....can you?:lolflag:

Naah...not until the last time I checked ;)

---

### Post by EXCiD3 on 2008-06-03
> **Inxsible said:**
> LOL !!

You still can't get yourself a new set of parents....can you?:lolflag:

Naah...not until the last time I checked ;)

I'll check in the community market :popcorn:

---

### Post by Rui Pais on 2008-06-03
> **Inxsible said:**
> LOL !!

You still can't get yourself a new set of parents....can you?:lolflag:

Naah...not until the last time I checked ;)

Naah parents are usually big and have heavy dependencies... you would need highspeed connection just to download them :lol:

---

### Post by Inxsible on 2008-06-03
Hey Rui..I installed E17 via cvs. Liking it so far. I was wondering what file manager does E17 use? I can't say I am a fan of it....since it opens multiple windows while navigating.

I even turned on the option "Open folders in place" which got rid of it, but then I could not go back or forward in the directory structure.

I think I will probably install thunar in place of it...

Tell me if there are ways to configure it.

---

### Post by Rui Pais on 2008-06-03
> **Inxsible said:**
> Hey Rui..I installed E17 via cvs. Liking it so far. I was wondering what file manager does E17 use? I can't say I am a fan of it....since it opens multiple windows while navigating.

I even turned on the option "Open folders in place" which got rid of it, but then I could not go back or forward in the directory structure.

I think I will probably install thunar in place of it...

Tell me if there are ways to configure it.

No Inxsible, right now the efm (thats the name) it's quite basic and i think it's not much flexible or even allow to config much. :(

Regrettably File managers on e17 has been one of the weak things. I think this one it's the 4th or 5th... They are(were) all either weird or abandoned after a while.
So i don't have much hope on this one either.

Not a great problem it self.
What people usually do it's just unload the 'File Manager' module and use a decent, well tested, File Manager.
For me the good ones: thunar, rox and pcmanfm (ordered by size).
I used each one for a while then i just stick with the one i feel more comfortable with.

hth

---

### Post by Inxsible on 2008-06-03
> **Rui Pais said:**
> No Inxsible, right now the efm (thats the name) it's quite basic and i think it's not much flexible or even allow to config much. :(

Regrettably File managers on e17 has been one of the weak things. I think this one it's the 4th or 5th... They are(were) all either weird or abandoned after a while.
So i don't have much hope on this one either.

Not a great problem it self.
What people usually do it's just unload the 'File Manager' module and use a decent, well tested, File Manager.
For me the good ones: thunar, rox and pcmanfm (ordered by size).
I used each one for a while then i just stick with the one i feel more comfortable with.

hthThanks Rui....but when I unload the File Manager module, I lose all the files that are on my Desktop. Meaning I cant see them on the desktop. I have to use emelFM2 (a file manager) to actually go to /home/my username/Desktop to see those files.

How can I still have my Desktop files shown after unloading the File Manager(efm) module?

---

### Post by starcannon on 2008-06-03
@LinuxIsInnovation

Nice job, and yeah ROX takes a minute to wrap your head around, once you "get it" its great though. I use it when I set up old jurassic ware laptops for underpriv kids in our area, the first one was a bugger, it goes nice and simple now though.

Oh and 80mb of ram?!?!?!? Wow WTG, lol I thought I was working with old iron (i just build the give aways out of junk people give me or throw away)

catch ya later

---

### Post by sayakb on 2008-06-04
> **starcannon said:**
> Oh and 80mb of ram?!?!?!? Wow WTG, lol I thought I was working with old iron (i just build the give aways out of junk people give me or throw away)

LOL.. no I guess you got that wrong :D
The desktop has 384MB RAM, but my setup uses <80MB of it! :guitar:

@EXCiD3:
Got the shutdown/restart/logout working. :popcorn:
Thanks :)

---

### Post by EXCiD3 on 2008-06-04
Awesome glad to hear it! Its amazing that you can give life to such an old computer and it runs almost as good as these $3000 computers you can get now a days! :D

---

### Post by sayakb on 2008-06-04
> **EXCiD3 said:**
> Awesome glad to hear it! Its amazing that you can give life to such an old computer and it runs almost as good as these $3000 computers you can get now a days! :D
Lolz... ROTF.
I've fallen in love with OpenBox I guess..

Thank you everybody for replying. I think all my queries have been solved!! :D
:KS:KS:KS

---

### Post by EXCiD3 on 2008-06-04
> **LinuxIsInnovation said:**
> Lolz... ROTF.
I've fallen in love with OpenBox I guess..

Thank you everybody for replying. I think all my queries have been solved!! :D
:KS:KS:KS

You sound like me...after about 20 sec with openbox i fell in love myself!! Now im rocking openbox with conky and theres no stopping me now!! :guitar:

---

### Post by sayakb on 2008-06-05
Can you upload your conkyrc file? I haven't put up conky with OpenBox yet :)

---

### Post by Rui Pais on 2008-06-05
> **Inxsible said:**
> Thanks Rui....but when I unload the File Manager module, I lose all the files that are on my Desktop. Meaning I cant see them on the desktop. I have to use emelFM2 (a file manager) to actually go to /home/my username/Desktop to see those files.

How can I still have my Desktop files shown after unloading the File Manager(efm) module?

Hi Inxsible.
Yes thats right, efm it's the e "thing" that draws the desktop...

If you want to have desktop icons you may need to use a file manager that implements that, like Nautilus or Rox, or some extra tool that just do that like fbdesk (i think there others...)

Although i advise to try to get used to a clean desktop... 
Easily one became as productive as with it, and file organization would be better (not to mention open apps covering desktop would not be an issue and so no need for a ShowDesktop module or equivalent :))

---

### Post by EXCiD3 on 2008-06-05
I have to agree, get used to no desktop icons...it might be handy to have a desktop icon once in a while, but just add a bookmark or a link to the folder in your menu somewhere...plus when you show off your comp it looks so spankin clean! :D

Heres my conkyrc for you! I've been playing with the config a bit recently...moving it to the sides...different colors...also trying to get it so that my wifi will show only when its being used and then i also want to add the 3 day weather forecast from the new weather script...thats just gorgeous looking!

Well now that ive got 1337 posts :guitar:
im not sure what to do...do i keep editing my posts ive already made to try to help but keep the same number, create a new account and leave this one in all its glory or do i just blow it off like i didnt notice it?? :confused: :lolflag:

---

### Post by sayakb on 2008-06-05
> **EXCiD3 said:**
> Well now that ive got 1337 posts :guitar:
im not sure what to do...do i keep editing my posts ive already made to try to help but keep the same number, create a new account and leave this one in all its glory or do i just blow it off like i didnt notice it?? :confused: :lolflag:


Oh.. now you seem to have 1338 :(
Thanks for the conkyrc :)

---

### Post by EXCiD3 on 2008-06-05
Ah, decided to go ahead and "pretend i didnt see it" ;)

---

### Post by Inxsible on 2008-06-05
> **Rui Pais said:**
> 
Although i advise to try to get used to a clean desktop... 
Easily one became as productive as with it, and file organization would be better (not to mention open apps covering desktop would not be an issue and so no need for a ShowDesktop module or equivalent :))

> **EXCiD3 said:**
> I have to agree, get used to no desktop icons...it might be handy to have a desktop icon once in a while, but just add a bookmark or a link to the folder in your menu somewhere...plus when you show off your comp it looks so spankin clean! :D
Guys, believe me, I like my desktop clean just as you guys. But I do have an occasional txt file where I will jot down some of the important things that I have to do after coming back from work...or the next day. So its nice to have it right on the desktop..so I can remember. 

That's no big deal though... I guess I can use one of those note taking apps.

EXCiD..I am gonna have a look at your conky too...see if there is something i like. You can use ```
if ...fi
``` to show your wireless only if its being used.

I will post mine after I install Debian xfce that I just burned.. my Xubuntu started to get bogged down and its unusable. :(

Also in the process of creating a debian netinst + Fluxbox installation in the same machine....

Will keep me busy for the evening :)

Until l8r..

---

### Post by EXCiD3 on 2008-06-05
Cool, yeah my conky still has a lot of work to do. I'm not sure if the code is there or not, but you can use the "cat" command to have it display a todo list text file. i find that kinda handy sometimes :) 

The other day i changed up my config match Farrel's computer in Die Hard 4 ;)

Heres a couple of screenshots of my desktop, the die hard 4 one and then the white/black theme, both are gnome but ive moved the white/black one over to openbox recently.

[http://farm4.static.flickr.com/3045/2474068143_e1f0295df7_b.jpg](http://farm4.static.flickr.com/3045/2474068143_e1f0295df7_b.jpg)
[http://farm4.static.flickr.com/3082/2547017050_b14c675c92_b.jpg](http://farm4.static.flickr.com/3082/2547017050_b14c675c92_b.jpg)

---

### Post by Inxsible on 2008-06-05
Hey Excid,

I really like the 1st screenshot. Nice and minimalistic. I especially like the clock in Conky (it is in conky right?) That will save a lot of memory than running another app for time.

Tell me one thing though..the Firefox and Terminal in the middle of the desktop -- were they dockapps or screenlets?

or something else entirely ?

---

### Post by EXCiD3 on 2008-06-05
Glad u liked it, the config is all conky with Zekton font, I dont think i have that conkyrc file anymore unfortuantely :(

Firefox and Terminal are actually just shortcuts ;)

---

### Post by cardinals_fan on 2008-06-05
Zenwalk and SLAX are good light distros.  Use Openbox, Pekwm, or a tiling wm.

---

### Post by EXCiD3 on 2008-06-05
I played with awesomewm a little bit...that is crazyness. all you get is terminals, everything is keyboard based...if you could get used to it thats a possibility too but not the most efficient i guess u could say since it would take a while to learn.

---

### Post by Inxsible on 2008-06-06
My minimal + Enlightenment 17 uses about 74MB RAM - if I don't count the buffered RAM  :)

Sweet !!!

Also, I switched from Xubuntu to Debian Xfce...and notice quite a performance difference. I am going to re-install the Enlightenment on a Debian netinst and hopefully make my E17 install even faster and better. I even have a Debian and Fluxbox install.

Good stuff !!!!!

---

### Post by EXCiD3 on 2008-06-07
Nice!

Whenever i get some time on highspeed im going to reinstall my favorite os...Arch linux :D and setup that badboy with Openbox and conky! :D

---

