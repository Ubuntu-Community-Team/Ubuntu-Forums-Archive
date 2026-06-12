---
title: "Beta just Beautiful - I can't believe it !!"
date: 2011-09-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-09-01
I can't believe my eyes - !! I downloaded the ISO file and then proceeded to install it on a USBB MoBo with 1GB of DDR, 2.8GHz dual core and an AGP card with only 8 MB of SDRAM !!!!! and I have Unity Working!!!

  It is a whole new experience!!

  Just baffling.

 Beautiful work !  and I have the smooth scroll on the main screen  .. etc..

---

### Post by VinDSL on 2011-09-01
Yep!

Can't wait for UbuPP pre-alpha.  LoL!  :D

---

### Post by ventrical on 2011-09-01
Well, the way this  Beta1 Ocelot is working, Perfect Penguin  will  certainly be the next hallmark. Sort of like taking the solid core of Lucid and  stream-melding into Maveric :lol

And BRAVO  for LUBUNTU!!!

---

### Post by Sashin on 2011-09-01
Question: Did you get Unity3d or 2d?

---

### Post by ventrical on 2011-09-01
I have both of them? I also installed FVWM-Crystal in case it crashes. I did not get anything GNOME at all.

Oddly enough the compiz is working - but very slow when I click the desktop wall.  This feature dows not work in Unity 2D.

 Umm.. how would I tell.? I have them both at the login screen and I am able to choose one from the other.

Mabey I don't have Unity 3D?

---

### Post by thonuz on 2011-09-01
Are you a tablet user? So far the only baffling thing is trying to find out what is running.

---

### Post by stoneguy on 2011-09-01
Don't try to do anything booting directly from the DVD, or from dd'ng the iso to a USB key. Without a heap of upgrades the system is seriously fubar'd.

Put the ISO on a >=4GB key using usb-creator adding a goodly chunk of persistency space. Then shut down and boot from that key. 

As soon as it comes up, go to a VT and do
    sudo apt-get update
    sudo apt-get install aptitude
    sudo aptitude safe-upgrade
    sudo aptitude upgrade
so that the upgrades are clean. If you get holdbacks, reject the upgrades and wait awhile to try later. They'll get the dependencies sorted out pretty quickly.

When you reach a point where all the upgrades go through, reboot into a decently functioning beta :biggrin:

Probably worth snaffling a daily sometime next week to have something to boot up and show friends and neighbours.

---

### Post by shuttleworthwannabe on 2011-09-02
That is really good advise; I tend to wait a couple of days after beta1 for these reasons. But agree, this is looking great!

---

### Post by kerry_s on 2011-09-02
Still to unstable for me, installed both ubuntu & lubuntu. 
Now I'm installing lubuntu 11.04 back on.

---

### Post by Sashin on 2011-09-02
Choose ubuntu3d at login, and tell me if its still a quick, smooth experience apart from the workspace thing.

---

### Post by cariboo on 2011-09-02
I installed the beta on two systems, one an AMD 3800+ with nvidia 9400GT, 2GiB ram and dual monitors, the second system an atom 270 with 1GiB ram and Intel 945 graphics. Both systems run Unity 3D without any problems

A couple of things I found, on the dual monitor system, the global menus work on the monitor an application is running on. not on both, and ram usage has dropped quite a bit. On the AMD system ram usage after a couple of hours was still in the low 600's and for the first ime since the tool chain upload, the atom powered system's ram usage was well below 300MiB.

Compiz cpu usage on both systems was between 0 and 2% even when running multiple applications.

At this rate, if the devs keep on working on memory leaks, we'll be seeing ram usage lower than any version since Hardy. :) :)

---

### Post by dmoconnell on 2011-09-02
Downloaded using "Test Drive an Ubuntu ISO" and was able to create a bootable usb key on a 2 gb (some said you need 4 gb usb key but my 2gb works just fine) 
some of the program icons didn't show up. have yet to test the LightDM login (will wait till Final release) love that they ditched Evolution as the default mail/calendar program. Ubuntu loaded quick (can't wait to see it when i do a full install of ocelot) as did the 1 or 2 programs i tried (for reference I'm running this on a compaq CQ-50 (standard model except that i am dual booting Vista/Ubuntu 11.04)
looking forward to the final release in October

---

### Post by MG&amp;TL on 2011-09-02
Can't agree more. I think this is the release when people start to like Unity. :D I particularly love the golden aero snap feature...

And <cheers> for Lubuntu, its inclusion is probably overdue.

---

### Post by pasisti on 2011-09-02
My last Ubuntu version was maybe 9.10 and I have to say that I liked the beta very much! Even on the livecd it was sleek and nice. Of course it was slow from the cd but when the final 11.10 comes I will install it, too. 

I don't know that much about ubuntu or linux in general but I have to say that I loved Unity! The only thing I couldn't figure out in the 5 minutes of experimenting is that is there a way to see all installed applications in a sorted order like in the games/office/internet -menus that previous versions had?

---

### Post by MARP1961 on 2011-09-02
If you want to try Gnome Shell, just install it from Software Centre or Synaptic Package Manager. Once installed, you should get the login option 'Gnome'. 

Compare Gnome Shell with Unity. You might find you prefer Gnome Shell!

---

### Post by ratcheer on 2011-09-02
> **kerry_s said:**
> Still to unstable for me, installed both ubuntu & lubuntu. 
Now I'm installing lubuntu 11.04 back on.
 
Why don't you use a testing partition for pre-releases?
 
I have both 11.04 and 11.10 on my system, but I am now using 11.10 about 95% of the time.
 
Tim

---

### Post by sanderd17 on 2011-09-02
> **MARP1961 said:**
> If you want to try Gnome Shell, just install it from Software Centre or Synaptic Package Manager. Once installed, you should get the login option 'Gnome'. 

Compare Gnome Shell with Unity. You might find you prefer Gnome Shell!

For those that try GS, do note that GS and Unity are build from another philosophy. GS is made to be themed and extended. Look on sites like Web Upd8 or OMGUbuntu to find interesting themes and extensions. Unity is made to be as functional as possible without extra extensions.

---

### Post by EgoGratis on 2011-09-02
I do like what i see in Beta 1! I didn't have problems with Unity on my hardware in Ubuntu 11.04 but Ubuntu 11.10 does look and feel better and i will be happy to upgrade to Oneiric Ocelot when it is released!

---

### Post by walt.smith1960 on 2011-09-02
> **sanderd17 said:**
> For those that try GS, do note that GS and Unity are build from another philosophy. GS is made to be themed and extended. Look on sites like Web Upd8 or OMGUbuntu to find interesting themes and extensions. Unity is made to be as functional as possible without extra extra extensions.

Very good point.  Unity seems to be targeting the "I don't want 15 different looks.  Let me  learn one and leave me alone" user.  I find Gnome-Shell pretty usable though and it'll be better once there are more extensions.

---

### Post by ventrical on 2011-09-02
> **walt.smith1960 said:**
> Very good point.  Unity seems to be targeting the "I don't want 15 different looks.  Let me  learn one and leave me alone" user.  I find Gnome-Shell pretty usable though and it'll be better once there are more extensions.

Really good point !! Even beta testers are busy with other work as well as regular Ubuntu users. We go to get "stuff" done, ya know .. so thats not a real bad philosophy to take up.

It's is good to see Unity work on low-end graphics adapters. I think perhaps some may have felt left out when Unity came out with the Natty release.and the ensuing graphics adapter probs.

  Then again.. who knows where Ocelot will go. 

So far, so good... but I expects bugs of course.

---

### Post by Rasa1111 on 2011-09-02
but the real question....
Does gnome shell work properly in it yet? lol

---

### Post by BigSilly on 2011-09-02
Downloading the beta right now, but going purely on the shots over on OMG! Ubuntu! it looks absolutely tremendous. Lovely to see Unity taking proper shape and clear definition, and I only hope it's stable and solid when it's finished. I'd love to move back to Ubuntu.

But I agree, it really does look beautiful. Looking forward to trying it out.

---

### Post by cariboo on 2011-09-02
> **Rasa1111 said:**
> but the real question....
Does gnome shell work properly in it yet? lol

Why don't you try it, the more testers reporting bugs the better.

---

### Post by fjgaude on 2011-09-02
Beta 1 Unity 3D working great, no error msgs, yet!

Great jobs, fellows! Thank you.

---

### Post by Rasa1111 on 2011-09-02
> **cariboo907 said:**
> Why don't you try it, the more testers reporting bugs the better.

 I usually would.
But my experience with the alphas were pretty ...
hmm, ..... less than pleasant.. 
and the beta i downloaded and stuck on a USB drive won't boot. lol 

Maybe i try again......

---

### Post by Dangertux on 2011-09-02
I'm so sorry for what is about to be completely useless input, I just couldn't resist...

In regards to the thread title ...You beta believe it :-P

---

### Post by 23dornot23d on 2011-09-02
> 
but the real question....
Does gnome shell work properly in it yet? lol
Well its working for me now Rasa1111 ..... [_**LINK**_]("http://ubuntuforums.org/showpost.php?p=11213337&postcount=11")

It is holding back a few packages ... aptitude safe-upgrade I keep using ..... and it rarely lets me down.

But its as up to date as it will allow at this moment in time ......

**[COLOR=Red]Update ..... (  I killed it with a dist-upgrade ....... safe upgrade was ok up to this moment in time )[/COLOR]**

---

### Post by Rasa1111 on 2011-09-02
> **23dornot23d said:**
> Well its working for me now Rasa1111 ..... [_**LINK**_]("http://ubuntuforums.org/showpost.php?p=11213337&postcount=11")

It is holding back a few packages ... aptitude safe-upgrade I keep using ..... and it rarely lets me down.

But its as up to date as it will allow at this moment in time ......

Beautiful! :D
 Thanks mate! 
Going to re-dload now! :KS

---

### Post by flipper T on 2011-09-02
lots of bugs, but hey ! its barely beta.

& that shutter sound it makes when you take a screenshot...well, it makes me smile

:)

---

### Post by dmoconnell on 2011-09-02
oy yey. the program i used to download the ISO (beta) redownloaded the Alpha 3 iso instead. finally got the correct iso. Only 1 icon is not showing up (search for files icon) very fast. thunderbird is great.  and firefox is very fast. the new dash icon is ok.   (I'm in Ubuntu 11.10 beta 1 right now (via USB Key)
looking forward to the Oct 13 release.

---

### Post by kerry_s on 2011-09-02
> **ratcheer said:**
> Why don't you use a testing partition for pre-releases?
 
I have both 11.04 and 11.10 on my system, but I am now using 11.10 about 95% of the time.
 
Tim

not enough space & just don't want to. i usually switch over at beta time, but not this time. i got lockups/freezing, apps that don't launch when clicked, pop up hell, from stuff crashing in the background. :lolflag: i'll give it more time.

---

### Post by Hreinsi on 2011-09-03
> **ratcheer said:**
> Why don't you use a testing partition for pre-releases?
 
I have both 11.04 and 11.10 on my system, but I am now using 11.10 about 95% of the time.
 
Tim

 I am doing that just removed my win7 from hard disk :)

---

### Post by Rasa1111 on 2011-09-03
> **23dornot23d said:**
> Well its working for me now Rasa1111 ..... [_**LINK**_]("http://ubuntuforums.org/showpost.php?p=11213337&postcount=11")



**[COLOR=Red]Update ..... (  I killed it with a dist-upgrade ....... safe upgrade was ok up to this moment in time )[/COLOR]**

hahahaha!!  :lolflag:
That cracked me up,  ("update... Killed it!")  Lol! thanks. :P :lolflag:

---

### Post by raw_knee on 2011-09-03
Indeed, Oneiric Ocelot feels better than Natty Narwhal! I got it installed on a netbook this morning. No problems with the installation, but I am experiencing beta-related hiccups. Excited for the final release!

---

### Post by aquarius18 on 2011-09-03
Just "upgraded" a Natty install to the Oneiric Beta. 

One word: impressed!!

It certainly has a good feel about it, runs smooth and much faster than on the old 2.xx kernel. Few beta hiccups here as well (reported them as one should).

Keep up the good work, devs!

---

### Post by as2000 on 2011-09-03
Stunning!

This was the first time that the additional drivers actually worked! After running updates, beta 1 is very stable and enjoyable. 

Nice job team!

---

### Post by 23dornot23d on 2011-09-03
> **Rasa1111 said:**
> hahahaha!!  :lolflag:
That cracked me up,  ("update... Killed it!")  Lol! thanks. :P :lolflag:


Whats really weird ..... last night everything was in a mess ..... after a cold restart today its all
working ok ......

Not done any more upgrades yet ...... only thing last night was I never cold booted it ......

Well just to keep you updated - did not want you installing and finding it was dead in the water so to
speak .......

But I can give it a thumbs up for now ....... if it dies again for any reason ..... I will be quick to report it.

[[COLOR=Red]**SCREENSHOT**[/COLOR]]("http://img703.imageshack.us/img703/4340/27732837.jpg")

---

### Post by Rasa1111 on 2011-09-03
> **23dornot23d said:**
> Whats really weird ..... last night everything was in a mess ..... after a cold restart today its all
working ok ......

Not done any more upgrades yet ...... only thing last night was I never cold booted it ......

Well just to keep you updated - did not want you installing and finding it was dead in the water so to
speak .......

But I can give it a thumbs up for now ....... if it dies again for any reason ..... I will be quick to report it.

[[COLOR=Red]**SCREENSHOT**[/COLOR]]("http://img703.imageshack.us/img703/4340/27732837.jpg")

wow sweet! :guitar:
that's a plus! lol

thanks, i appreciate it. 

meant to ask..
what you got goin' up there, AWN?

---

### Post by jerrylamos on 2011-09-03
> **Sashin said:**
> Choose ubuntu3d at login, and tell me if its still a quick, smooth experience apart from the workspace thing.

The dash panel is very hard to read, big and blurry, like Mr. Magoo without his nearsighted coke bottle glasses.

After I have several sessions going, Alt-Tab which works fine on Unity-2D is this big blurry glop and I can hardly detect what fuzzy picture has a faint fuzzy halo and is to be selected.

Beauty is in the eye of the beholder.

Just installed a Lubuntu Beta 1 - I've got Lynx LTS, Meerkat, Narwhal, Oneiric Beta 1, Lubuntu Oneiric Beta 1 partitions.  At 10G each not a problem.

Now I tend to run what I perceive is ubuntu's direction looking for bugs so I do Unity-3D till I can't stand it and switch to Unity-2D.

I haven't done gnome-shell because I haven't stopped to figure out how.

Jerry....

---

### Post by VinDSL on 2011-09-03
> **jerrylamos said:**
> The dash panel is very hard to read, big and blurry, like Mr. Magoo without his nearsighted coke bottle glasses.[...]
Heh!  Never thought about it that way, but...  :D

What I don't understand is; there is a second (empty) dash panel below it.

Kinda hard to see, depending on the wall you're running, but...


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-3-sep-2011(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-sep-2011.png")[/INDENT]


Can you see the second (empty) one, down below, on your install?

**EDIT**

You know...

I was just staring at that screenie, drinking my coffee, and it occured to me - since the second instance isn't blurred, et cetera, it almost looks like a misplaced layer in the dash panel (above).

It's like the vertical alignment is horribly off, e.g. it's supposed to be a shading layer for the dash panel header.

Seems odd that they would shade the bottom of the panel, but not the top, eh what?

---

### Post by terry_gardener on 2011-09-03
it is not a second empty dash i have done it on mine to have a look and it looks part of the design since there is a clear strip that is small running from the bottom of the screen to the dash then thicker strip running along the bottom of the dash and running up the right side of the dash to the panel and then turns outwards to the right edge of the screen. 

the clear strip follows the edge of the launcher to the dash then round the dash and then out to the right of the screen along the panel.

---

### Post by 23dornot23d on 2011-09-03
> **Rasa1111 said:**
> wow sweet! :guitar:
that's a plus! lol

thanks, i appreciate it. 

meant to ask..
what you got goin' up there, AWN?

____________________________________________

I always run Cairo-Dock ..... go to themes ...... after configure ..... and pick Mee Go .... 

It sets the 3 docks up for you ..... I just move the middle one from the bottom to the top
then offset the small ones individually 25 pixels down ..... works well with GS

---

### Post by VinDSL on 2011-09-03
> **terry_gardener said:**
> it is not a second empty dash i have done it on mine to have a look and it looks part of the design[...]
Right, you are!  :)

I killed Conky and gave it the ol' Avril Lavigne Test (pure as the driven snow, she is)


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-3-2011(2)(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-2011(2).png")[/INDENT]

Shows the importance of a proper wall, yes?  

And/or the need for us to be able to tweak the dash panel appearance...  ;)

---

### Post by Rasa1111 on 2011-09-03
Man, that is nice.
You guys got me all excited to check it out now. lol
Almost done downloading! woot!  :guitar:

---

### Post by Rasa1111 on 2011-09-03
> **23dornot23d said:**
> ____________________________________________

I always run Cairo-Dock ..... go to themes ...... after configure ..... and pick Mee Go .... 

It sets the 3 docks up for you ..... I just move the middle one from the bottom to the top
then offset the small ones individually 25 pixels down ..... works well with GS

ahhh, 
I've never used (or even checked out) cairo dock. 
interesting, thanks man. :)

---

### Post by ventrical on 2011-09-03
> **VinDSL said:**
> Right, you are!  :)

I killed Conky and gave it the ol' Avril Lavigne Test (pure as the driven snow, she is)

[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-3-2011%282%29%28650x520%29.png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-2011%282%29.png")[/INDENT]Shows the importance of a proper wall, yes?  

And/or the need for us to be able to tweak the dash panel appearance...  ;)

  Nice wall! :)

---

### Post by VinDSL on 2011-09-03
> **ventrical said:**
> Nice wall! :)
Avril is cute, isn't she?

A Canadian National Treasure...  :)

---

### Post by karmila on 2011-09-03
Have just installed OO beta1 and i really excited that now compiz scale plugin also show minimized windows and we can set unity launcher opacity.

Although i quite bothered with window control being hidden for maximized window (need more click to minimize inactive maximized window)

---

### Post by Rasa1111 on 2011-09-04
Checking out the Beta now.
It is very, very nice indeed! :)
Niice work, Devs! 

At Karmila..
maximize window control is not hidden on mine.
Unless Im confused by your comment? 

Or do you mean that when its maximized, you cant see the controls?

If thats the case, all you have to do is put the cursor on the top panel/title bar, and the controls appear. 

Care to elaborate?

---

### Post by madjr on 2011-09-04
i guess no one will take pics without the dash close anymore ! :p

> I killed Conky and gave it the ol' Avril Lavigne Test (pure as the driven snow, she is)

i dont think shes that pure, but i like her and she makes one damn nice wall :)

---

### Post by 3rdalbum on 2011-09-04
I don't like her antics, but she looks nice, and more importantly it's a very good wallpaper for demonstrating that the dash's opacity and colour now work when you have a white and grey wallpaper.

---

### Post by karmila on 2011-09-04
> **Rasa1111 said:**
> Or do you mean that when its maximized, you cant see the controls?

If thats the case, all you have to do is put the cursor on the top panel/title bar, and the controls appear. 

Care to elaborate?

Oh yes, that is what I meant. (sorry, english is not my first language :P)
This behavior makes harder to minimize inactive maximized window below another window (see the image below).

And why unity launcher can not be used to minimize window? :confused:
I think it should be able to minimize windows as well because it can unminimize and launch application windows...

And one more think i like, my usb cdma mobile broadband is recognized briefly, no need to wait before it detected and i can use it. Although, latest network-manager update broke things and i can not connect my usb modem from network-manager (Now I am connected through wvdial).

---

### Post by MG&amp;TL on 2011-09-06
Did it re-name anyone else's home folder? It truncated mine so my terminal prompt ended up:

```
otmyrealname@notmyrealname-laptop$_
```

So I changed my home folder name, which worked until I tried to login, when it failed, and went into a 'back to login' loop...I changed it back in recovery mode, and just got an error...oh well. :confused:

---

### Post by kbaumen on 2011-09-06
I was not looking forward very much to 11.10, thought I might stick with 10.04 for a while. However this discussion has gotten me interested in trying out the beta. Cheers guys.

---

### Post by JonM33 on 2011-09-06
I'm very pleased with Ubuntu 11.10 Beta as well. Love everything about it!

---

### Post by Rasa1111 on 2011-09-06
> **kbaumen said:**
> I was not looking forward very much to 11.10, thought I might stick with 10.04 for a while. However this discussion has gotten me interested in trying out the beta. Cheers guys.


lol, same here.
glad they "talked me into it" though.
as it is very nice! 

Karmila, no worries, your English is very good. :) 
I see what you're saying now, though.

---

### Post by fjgaude on 2011-09-06
The features of the Dash and Lenses make it so much better for me than 11.04. Can we imagine what 12.04 is to be? <smile>

---

### Post by MG&amp;TL on 2011-09-06
I think they would have lost less people to the Unity plague i they had kept this back a release....this one's brilliant, the older one was somewhat suspect...

---

### Post by nm_geo on 2011-09-06
> **VinDSL said:**
> Right, you are! :)
 
I killed Conky and gave it the ol' Avril Lavigne Test (pure as the driven snow, she is)
 
[INDENT](Click to expand)
 
[[IMG]http://vindsl.com/images/vindsl-desktop-3-2011(2)(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-3-2011(2).png")
[/INDENT]Shows the importance of a proper wall, yes? 
 
And/or the need for us to be able to tweak the dash panel appearance... ;)
 
When VinDSL kills Conky it has to be for a good reason.  I believe he has one.. ;)

---

### Post by 23dornot23d on 2011-09-06
Lols ..... first time I have seen VinDSL kill conky ...... he must be in love ;)

---

### Post by VinDSL on 2011-09-06
> **nm_geo said:**
> When VinDSL kills Conky it has to be for a good reason.  I believe he has one.. ;)> **23dornot23d said:**
> Lols ..... first time I have seen VinDSL kill conky ...... he must be in love ;)
Oh, my!  Don't take my post wrong...

For demonstration purposes, I temporarily killed Conky.

Here's my desktop today...


[INDENT][IMG]http://vindsl.com/images/vindsl-desktop-6-sep-2011(650x520).png[/IMG][/INDENT]


It's just a little hard to see the Dash Panel borders with a complex wall - that's all.  ;)

---

### Post by dmoconnell on 2011-09-07
VinDSL where do you get your wallpapers? Every time i see one of your snapshots you always have the coolest wallpapers.
Dm

---

### Post by sgage on 2011-09-07
> **dmoconnell said:**
> VinDSL where do you get your wallpapers? Every time i see one of your snapshots you always have the coolest wallpapers.
Dm

I don't know how he gets anything done with all that cra... stuff on his desktop :KS

---

### Post by BigCityCat on 2011-09-07
Been using it. It is pretty decent but it should get much better when people start doing themes for it.

Can anyone point me to the thread where everyone is testing gnome shell in Oneiric?

---

### Post by MG&amp;TL on 2011-09-07
I haven't seen one, but gnome-shell works pretty damn good, considering the mess it was in in 11.04

---

### Post by BigCityCat on 2011-09-07
> **MG&TL said:**
> I haven't seen one, but gnome-shell works pretty damn good, considering the mess it was in in 11.04

I didn't have much luck with it. I would expect it to get better. Installing it I recieved a message that installing gnome shell would stop all unity updates. I didn't want to do that in a beta. Kind of defeats the purpose of the beta testing.

---

### Post by MG&amp;TL on 2011-09-07
Nope, didn't get that. Try a newer build? :confused:

---

### Post by 23dornot23d on 2011-09-07
> 
I recieved a message that installing gnome shell would stop all unity updates.
Would be interesting to see how this works ........  does installing any other desktop manager do this also ....... or is it just Gnome-Shell ..... 

How does it block updates  ..... does it lock up all of the update managers ?

Do you have a link to the message you recieved ..  [BigCityCat]("http://ubuntuforums.org/member.php?u=726885") ... :confused:

I have Gnome-Shell installed - and somehow the updates are managing to get in .

---

### Post by Larkspur on 2011-09-07
> **23dornot23d said:**
> I have Gnome-Shell installed - and somehow the updates are managing to get in .

Same here.

---

### Post by clivejo on 2011-09-07
What are you using to show the system information down the right hand side?

> **VinDSL said:**
> Oh, my!  Don't take my post wrong...

For demonstration purposes, I temporarily killed Conky.

Here's my desktop today...

[INDENT][IMG]http://vindsl.com/images/vindsl-desktop-6-sep-2011%28650x520%29.png[/IMG][/INDENT]
It's just a little hard to see the Dash Panel borders with a complex wall - that's all.  ;)

---

### Post by rigel4 on 2011-09-07
Loving 11.10 well done all the devs.:KS:KS:KS:KS:KS

Thank you,i would contribute in some small way if someone can point me to- how?

I am not a programmer

---

### Post by MG&amp;TL on 2011-09-07
Bug reports! Experiment with EVERYTHING, if it crashes (which a lot of stuff does at the moment), let apport collect all your details and things.

Programming's not something you can pick up in an evening, but it's worth doing.

---

### Post by BigCityCat on 2011-09-07
> **23dornot23d said:**
> Would be interesting to see how this works ........  does installing any other desktop manager do this also ....... or is it just Gnome-Shell ..... 

How does it block updates  ..... does it lock up all of the update managers ?

Do you have a link to the message you recieved ..  [BigCityCat]("http://ubuntuforums.org/member.php?u=726885") ... :confused:

I have Gnome-Shell installed - and somehow the updates are managing to get in .

I must have done something wrong. I wasnt really paying attention cause after you guys said that I took a look at it and no problems, but It's installed by default. I was trying to install it. I'm not sure what is going on with it. I didn't realize they have it installed by default.

---

### Post by MG&amp;TL on 2011-09-07
It's not installed by default.

---

### Post by DogMatix on 2011-09-07
Yep its looking pretty sweet. Did have issues with my updated system from Maverick, Natty heritage. Everything seemed fine until an issue with rfkill caused me to have to rmmod acer-wmi every boot to get the wireless working. Anyhoo, pratting around eventually caused problems with my graphics that caused Unity to fall back to 2d "Yuck!", so I experimented with gnome-shell, which didn't work. So tempted by a USB stick beta, lying next to my cigarettes, I reinstalled and said good bye to several months of detritus.

Glad I did? Yes. Loving the new log-in screen and one or two other treats that were broken before. There are breakages as there usually are with betas and a little extra effort submitting bug reports to Launchpad is required, but on the whole I like the way the Unity shell has evolved and it is my favorite desktop now.

PS. Still have an issue with 'rmmod acer-wmi' every boot to get wifi working. I need to find a way to make that stick. But I reckon its an Acer issue over Ubuntu's.

---

### Post by BigCityCat on 2011-09-07
> **MG&TL said:**
> It's not installed by default.

Well it's installed and I didn't install it. I must be losing my mind. It's pretty awesome though.

---

### Post by 23dornot23d on 2011-09-07
> **BigCityCat said:**
> Well it's installed and I didn't install it. I must be losing my mind. It's pretty awesome though.

Good to hear .... its running well for me too ...... :D

What version are you running ?

gnome-shell --version

---

### Post by flipper T on 2011-09-07
> **BigCityCat said:**
> Well it's installed and I didn't install it. I must be losing my mind. It's pretty awesome though.

same here

working fine

v. 3.1.4

---

### Post by MG&amp;TL on 2011-09-08
Hmmm...I guess the devs put different stuff in so they can test it.

---

### Post by VinDSL on 2011-09-08
> **sgage said:**
> I don't know how he gets anything done with all that cra... stuff on his desktop :KS
I'm sorry!

It's like Digital Rain, in the Matrix movie.

Kinda hard to see it in a static screenshot.

Maybe I'll make a video...  ;)

---

### Post by VinDSL on 2011-09-08
> **BigCityCat said:**
> Well it's installed and I didn't install it. I must be losing my mind. It's pretty awesome though.

> **23dornot23d said:**
> Good to hear .... its running well for me too ...... :D

What version are you running ?

gnome-shell --version

> **flipper T said:**
> same here

working fine

v. 3.1.4
Dittos!

```
vindsl@Zuul:~$ gnome-shell --version
GNOME Shell 3.1.4
```

In all fairness, I remember installing something-or-another that required GS to be installed, to satisfy this-or-that dependency.

If I think about it long enough, I can come up with an answer, but I don't know if it's necessary to tax my memory at 1:00 AM, you know?  :D

---

### Post by ratcheer on 2011-09-08
A few weeks ago, I had login options of Ubuntu, Ubuntu 2D, and Gnome. Without making any overt changes (ie, I did not manually remove any Gnome packages), I now only have options for Ubuntu and Ubuntu 2D.
 
Ubuntu really keeps me on my toes, trying to figure out WTH is going on. I mean, it is really crazy the way things just change right under your eyes. I am just about ready to seriously consider changing distributions. I love Ubuntu, but I wish it behaved more rationally.
 
Tim

---

### Post by lucazade on 2011-09-08
> **ratcheer said:**
> A few weeks ago, I had login options of Ubuntu, Ubuntu 2D, and Gnome. Without making any overt changes (ie, I did not manually remove any Gnome packages), I now only have options for Ubuntu and Ubuntu 2D.
 
Ubuntu really keeps me on my toes, trying to figure out WTH is going on. I mean, it is really crazy the way things just change right under your eyes. I am just about ready to seriously consider changing distributions. I love Ubuntu, but I wish it behaved more rationally.
 
Tim

ratcheer.. I understand your disappoint but if they don't change and experiment stuff during the development stage when they should do this kind of stuff?
Don't know if anyone have ever tried the development snapshots of vista or win7 before their release.. a bloody mess compared to ubuntu.. it is normal.

the only way I use Oneiric is to test stuff, report bugs and reinstall from scratch every week (because some bug fixing is not incremental during the dev stage).

---

### Post by Harry33 on 2011-09-08
> **ratcheer said:**
> A few weeks ago, I had login options of Ubuntu, Ubuntu 2D, and Gnome. Without making any overt changes (ie, I did not manually remove any Gnome packages), I now only have options for Ubuntu and Ubuntu 2D.
 
Ubuntu really keeps me on my toes, trying to figure out WTH is going on. I mean, it is really crazy the way things just change right under your eyes. I am just about ready to seriously consider changing distributions. I love Ubuntu, but I wish it behaved more rationally.
 
Tim

Well I haven't experienced anything like that.
What if you uninstall (purge) gnome-shell and then install it again.

---

### Post by fjgaude on 2011-09-08
> **ratcheer said:**
> A few weeks ago, I had login options of Ubuntu, Ubuntu 2D, and Gnome. Without making any overt changes (ie, I did not manually remove any Gnome packages), I now only have options for Ubuntu and Ubuntu 2D.
 
Ubuntu really keeps me on my toes, trying to figure out WTH is going on. I mean, it is really crazy the way things just change right under your eyes. I am just about ready to seriously consider changing distributions. I love Ubuntu, but I wish it behaved more rationally.
 
Tim

Tim, it would be a good idea for you not to use a development version of an OS. Simply wait for the release and then the changes, crashes, etc., will be less, at least we can hope. <smile>

---

### Post by Jack Brown on 2011-09-08
IT IS great!

At first everything was sluggish, 

even CTRL+ALT+T for terminal still not working.

then after apt-get upgrade, unity was soo responsive.  

Was reading this thread on firefox on the oneiric machine.

Then closed LibreOffice Writer after trying it out.

Clicked Discard Changes.

Writer window still in the background.

It hanged / crashed.  Then won't boot anymore.

A roller coaster ride.  Can't wait to get on again.

But maybe will wait for Beta2 :popcorn:

---

### Post by ratcheer on 2011-09-08
> **fjgaude said:**
> Tim, it would be a good idea for you not to use a development version of an OS. Simply wait for the release and then the changes, crashes, etc., will be less, at least we can hope. <smile>

Huh? I have been doing this for several years, now. I was also actively involved as an Ubuntu project tester on Lucid and Maverick.

I guess that sometimes things just get away with me a little. I'll be ok. ;)

Tim

---

### Post by fjgaude on 2011-09-08
> **ratcheer said:**
> Huh? I have been doing this for several years, now. I was also actively involved as an Ubuntu project tester on Lucid and Maverick.

I guess that sometimes things just get away with me a little. I'll be ok. ;)

Tim

Happy you have found a sweet spot to find peace! Continue to test and report bugs, as we all do.

---

### Post by ratcheer on 2011-09-08
> **Harry33 said:**
> Well I haven't experienced anything like that.
What if you uninstall (purge) gnome-shell and then install it again.

I reinstalled gnome-shell and it is working. The font in the title bar is unreadable, but otherwise, it seems to be fine.

Thanks,
Tim

---

### Post by rigel4 on 2011-09-08
> **MG&TL said:**
> Bug reports! Experiment with EVERYTHING, if it crashes (which a lot of stuff does at the moment), let apport collect all your details and things.

Programming's not something you can pick up in an evening, but it's worth doing.

I am doing that as of last night , and i am going to learn C++
(I hope).
I can't say how much i respect the Ubuntu community, for giving us this wonderful software.

---

### Post by MG&amp;TL on 2011-09-08
Very good....you sound like me two months ago! :D

Errr...learning C++, try here:

[http://cplusplus.com/doc/tutorial/]("http://cplusplus.com/doc/tutorial/")

Learn BASH script, too. [LinuxCommand.org]("LinuxCommand.org") you can call bash through C++ with system() command (hint for later use);

Awesome. One new coder. ):P

---

### Post by ventrical on 2011-09-08
> **ratcheer said:**
> Huh? I have been doing this for several years, now. I was also actively involved as an Ubuntu project tester on Lucid and Maverick.

I guess that sometimes things just get away with me a little. I'll be ok. ;)

Tim

I had some great installs with Alpha versions and Beta1 but then I was workijng on this one machine (with an Intel MoBo, 2.66GHz DualCore) and a strange ATi Radeon Express OnBoard video!! I also purchased a SATA drive for this beast and all I have had is difficulty getting it up and running. Thanks to  the community here I now have a lot of info to get started on that machine in a little while (when I cool down) but, yeah .. I know it can be frustrating with getting some machines up and running. It is a real bonus to have seamless out of the box installs - but this is not always the case. 
btw .. you guys did a great job on Lucid !!

---

### Post by Longinus00 on 2011-09-08
> **MG&TL said:**
> ...you can call bash through C++ with system() command (hint for later use);


You *could* do that but that's honestly a really silly idea.

---

### Post by MG&amp;TL on 2011-09-08
Why? Most of my code at the moment is based around that...

---

### Post by MG&amp;TL on 2011-09-08
You COULD do a straight bash script, but then 

a) it's not an executable, so no .debs

b) function calls I don't think exist in bash, so that's out of the window.

c) what happens if you have a GUI?

---

### Post by Longinus00 on 2011-09-08
> **MG&TL said:**
> You COULD do a straight bash script, but then 

a) it's not an executable, so no .debs

b) function calls I don't think exist in bash, so that's out of the window.

c) what happens if you have a GUI?

We should stop this derail and you should create a thread in Programming Talk but I'll go over your points before you do.

a) chmod +x (for fun count how many files in /bin or /usr/bin are bash scripts)
b) bash has functions
c) you can use zenity

---

### Post by MG&amp;TL on 2011-09-08
Yes, we should. Agree to disagree, and present both arguments?

Got my beta working again, software centre's faster even though it has increased functionality.

---

### Post by Longinus00 on 2011-09-08
Just post your sourcecode (both your c and bash files) and ask if your use of system() is appropriate.

---

### Post by MG&amp;TL on 2011-09-08
If I did that, I'd need about five posts and a lot of upload time. And the tarball doesn't fit.

My current project is a plugin for grub-customizer that switches between bash to run the grub commands, and C++ for compatibility with the rest of grub-customizer. I see no other way I could do this. And it's convenient.

Personal preference? ):P

Sorry about the derail guys. We're sorry.

---

### Post by Longinus00 on 2011-09-08
I highly advise you to at least ask when using system() would be appropriate in Programming Talk because your 3 bullet point post earlier was more or less completely wrong. Alternatively post your bash script and ask if it's possible to implement what it does in pure C++.

---

### Post by MG&amp;TL on 2011-09-08
OK,I agree, hats off to you:

-I'm still having slight problems as a new convert to linux-why is batch file suddenly executable-ish? It confuses the brain...although I can see this now. 

-Function calls are not exactly well-pointed out in bash, whereas with C++ they are everywhere. My bad.

-OK, you have a GUI, but it's still not compatible with most of what other people write (typically not in bash)

I forsee no problem with a system() call, so unless you're really paranoid about RAM usage (and almost nobody is these days), switching between bash (via system()) and C++, to me really doesn't make a lot of difference. 


I apologize deeply for above inaccuracies, but as a programmer, I genuinely find that a system() call in C++ is really not a major issue, and it cuts around many beginner's programming issues, like how to copy a file conveniently, from your programming language of choice. Apologies to all affected, could we take this somewhere else(I'm making a programming thread.), and agree to carry out discussion there?

---

### Post by fjgaude on 2011-09-08
> **MG&TL said:**
> If I did that, I'd need about five posts and a lot of upload time. And the tarball doesn't fit.

My current project is a plugin for grub-customizer that switches between bash to run the grub commands, and C++ for compatibility with the rest of grub-customizer. I see no other way I could do this. And it's convenient.

Personal preference? ):P

Sorry about the derail guys. We're sorry.

Pray tell, what does any of this have to do with testing oneiric?

---

### Post by MG&amp;TL on 2011-09-09
Errr...IDK. Hence 'derail'. We got here somehow. Anyway, continue. Beta's going good, I love the way that you can change the dash transparency in ccsm.

---

### Post by Sashin on 2011-09-09
So Beta testers, how stable is Oneiric as of now? Is it getting much better? Does it seem like it'll be ready by release or still a bit crashy/buggy?

---

### Post by VinDSL on 2011-09-09
> **Sashin said:**
> So Beta testers, how stable is Oneiric as of now? Is it getting much better? Does it seem like it'll be ready by release or still a bit crashy/buggy?
[LIST]
[*]It's not.
[*]Yes.
[*]Yes.
[*]LoL!
[/LIST]

---

### Post by lucazade on 2011-09-09
> **fjgaude said:**
> Pray tell, what does any of this have to do with testing oneiric?

just nothing.. only some spam posts ;)

---

### Post by cariboo on 2011-09-09
> **Sashin said:**
> So Beta testers, how stable is Oneiric as of now? Is it getting much better? Does it seem like it'll be ready by release or still a bit crashy/buggy?

It's stable enough to run as a second install right now, and it should be fairly useful on release day. I'd suggest you create a small (10GiB) partition and install it, and help out with reporting bugs.

---

### Post by ventrical on 2011-09-09
> **cariboo907 said:**
> It's stable enough to run as a second install right now, and it should be fairly useful on release day. I'd suggest you create a small (10GiB) partition and install it, and help out with reporting bugs.


 I agree .. for the most part on my other 4 installs it works like a stable version.

---

### Post by Sashin on 2011-09-09
I see, I've caved in and installed alpha's for quite a few Ubuntu releases now. This time I've lasted until the Beta, and I'm not sure how to take what you've said.

Since its kinda stable I can take that as being no excuse to install it and help test or, I can take that as since its already progressing well I don't really need to test it and can save installing it for final release...

Until then I've decided to at least wait until Beta 2... its exciting how its getting closer and closer to stable release...

---

### Post by ricsi-pontaz on 2011-09-09
Today's update (dist-upgrade) want to remove these packages:

  libunity-2d-private0 libunity-core-4.0-4 unity unity-2d unity-2d-launcher
  unity-2d-panel unity-2d-places unity-2d-spread

Is it normal?

---

### Post by lucazade on 2011-09-09
> **ricsi-pontaz said:**
> Today's update (dist-upgrade) want to remove these packages:

  libunity-2d-private0 libunity-core-4.0-4 unity unity-2d unity-2d-launcher
  unity-2d-panel unity-2d-places unity-2d-spread

Is it normal?

not normal.. there is some issue with libnux and unity-2d.
wait for some new updates or in the meanwhile use "sudo aptitude safe-upgrade" to avoid problematic updates

---

### Post by ricsi-pontaz on 2011-09-09
> **lucazade said:**
> not normal.. there is some issue with libnux and unity-2d.
wait for some new updates or in the meanwhile use "sudo aptitude safe-upgrade" to avoid problematic updates

Okay, thanks.

---

### Post by karmila on 2011-09-09
Maybe it's easy but... where can i find font settings?
It is okay on may notebook but looks too big on my desktop monitor.

---

### Post by PuddingKnife on 2011-09-09
Loving it so far. 

Has anyone figured out how to change the icon set tho?

---

### Post by fjgaude on 2011-09-09
> **ricsi-pontaz said:**
> Okay, thanks.

Seems to be fixed now... try it and see.

---

### Post by effenberg0x0 on 2011-09-09
> **karmila said:**
> Maybe it's easy but... where can i find font settings?
It is okay on may notebook but looks too big on my desktop monitor.

sudo apt-get install gnome-tweak-tool

Regards,
Effenberg

---

### Post by fjgaude on 2011-09-09
> **effenberg0x0 said:**
> sudo apt-get install gnome-tweak-tool

Regards,
Effenberg

Such tool is very unstable now...likely will be fixed in the next five weeks, before release.

---

### Post by Rasa1111 on 2011-09-13
Alright, So I finally made a new partition to install 11.10 beta on.. 
and you guys are right... it is freakin' beautiful! lol :D 

I like this Unity much better than the previous. 
In fact.. I even installed Gnome Shell, but have been using Unity all night and today instead of GS. 
GS is still my favorite i think.. But I have no issues with Unity. 

11.10 is also the first distro. Ive used that requires no tinkering or changing settings to get my trackpoint/scroll to work!  haha! awesome. 

Gonna be a saweeeet distro when it's done. !

Thanks devs.! <3

---

### Post by icyitscold on 2011-09-13
I've had 11.10 working in virtualbox and it really is nice looking to be honest...

One think I really want to do though is get a look at Gnome Shell for the first time so I've downloaded it but it keeps loading a black screen when I log into it on vbox.... Anyone have any thoughts on this? I'm hoping it's a virtualbox issue and not an Ubuntu issue..

---

### Post by Rasa1111 on 2011-09-13
must be a vbox issue..
I have gnome shell installed under 11.10, and under 11.04. 
No problems. :)

---

### Post by aquarius18 on 2011-09-16
After doing another upgrade on this test installation and then re-booting, my Beta install is a goner. It won't fire up anymore, gets stuck at "Checking Battery State".

Did the Recovery bit and the Repair Packages bit - to no avail.

But that's a Beta :) , so I am not overly disappointed, just wait for Beta2 and do it all over again.

Maybe I have overdone the upgrades, don't know.

Bottom line is that I like what I am seeing and I guess the stable final release will be just a treat.

Cheers / Frank

---

### Post by NCLI on 2011-09-16
> **DogMatix said:**
> Yep its looking pretty sweet. Did have issues with my updated system from Maverick, Natty heritage. Everything seemed fine until an issue with rfkill caused me to have to rmmod acer-wmi every boot to get the wireless working. Anyhoo, pratting around eventually caused problems with my graphics that caused Unity to fall back to 2d "Yuck!", so I experimented with gnome-shell, which didn't work. So tempted by a USB stick beta, lying next to my cigarettes, I reinstalled and said good bye to several months of detritus.

Glad I did? Yes. Loving the new log-in screen and one or two other treats that were broken before. There are breakages as there usually are with betas and a little extra effort submitting bug reports to Launchpad is required, but on the whole I like the way the Unity shell has evolved and it is my favorite desktop now.

PS. Still have an issue with 'rmmod acer-wmi' every boot to get wifi working. I need to find a way to make that stick. But I reckon its an Acer issue over Ubuntu's.
How about just adding that command to "Startup Applications"?

---

### Post by ventrical on 2011-09-16
I have had some really great experiences so far with  tower PCs and laptops alike.  I am currently working with a terminal on an Intel Desktop PC MoBo with GEForce (Nvidia512) and a 2.66 Dual Core  Intell 32 bit processor. The Unity Desktop Inetrface is really progressing forward and it is  very snappy and smooth with it's graphical transitions.

  It works just as well on my laptops and it is a great improvement from natty Narwhal which had problems with the wireless connections

 It just keeps getting better ..adn thanks again Ubuntu.

---

### Post by Sashin on 2011-09-16
Does it look good regardless of the colours of the wallpaper? 
When I tried beta one, the feel of the dash seemed very dependent on what was in the background. In Natty the Dash looks good regardless of the wallpaper.

---

### Post by Rasa1111 on 2011-09-16
> Does it look good regardless of the colours of the wallpaper? 

I think so.

---

### Post by BigSilly on 2011-09-17
Quick questions about the current beta: Is it playing nicely with the nVidia proprietary driver? Are there still the random theme changes that caused users problems with Natty/Maverick? 

Thanks.

---

### Post by INTENSETUX on 2011-09-17
After reading this thread i have just caved in and started an upgrade :p

Would also be interested to hear about any nvidia issues , and does anyone think that the dash icons are still way to big ?

---

### Post by buntu63 on 2011-09-17
I feel scare among people to upgrade to 11.10...dunno why?

---

### Post by BigSilly on 2011-09-17
> **buntu63 said:**
> I feel scare among people to upgrade to 11.10...dunno why?

You mean people are afraid to upgrade? Well, I can only speak for myself, but yes I am, mostly because of a poor experience with 11.04. Not because of Unity (well, not directly), but because of various usability bugs. I had to switch distros, which I never expected to have to do with Ubuntu.

I'm hoping that 11.10 rectifies this and turns out brilliantly. So far the betas look really good, but I haven't installed one to see how it runs on the metal. I've only played with the live CD. But I'm crossing my fingers all will be well. It will certainly have to be good to move me off my current distros.

---

### Post by buntu63 on 2011-09-17
I've got to admit is full of bugs! at least this &#946; 1 !!

---

### Post by ratcheer on 2011-09-17
> **buntu63 said:**
> I feel scare among people to upgrade to 11.10...dunno why?

You should not be upgrading to 11.10 now, anyway. It is a development release - there are still plenty of bugs.

If you want to take Oneiric for a spin, you should install it in a separate partition (or on a separate computer). But, by all means, do your main computing on a fully released version, such as Maverick or Natty.

Tim

---

### Post by ventrical on 2011-09-23
I just installed Oneiric into an 8GB pendrive (fully updated). hp v255w

I'm stunned!

---

### Post by Rasa1111 on 2011-09-23
> **ventrical said:**
> I just installed Oneiric into an 8GB pendrive (fully updated). hp v255w

I'm stunned!

 it *is* awesome! :KS

---

### Post by ventrical on 2011-09-24
> **Rasa1111 said:**
> it *is* awesome! :KS

It looks like they incorporated some good solid build routines from Lucid and Maveric!! Thats a real bonus because that means a lot less people left out in the cold so-to-speak.

---

### Post by Supergoo on 2011-09-24
I just installed the 11.10 second beta and I like it alot. Unity is looing really good and you can install Gnome Shell ( Gnome3 ) and it runs very well. 11.10 is going to be a winner, in my book. They have Unity and Gnome 3 and every other desktop you could want to install. Nice going guys.

---

### Post by EgoGratis on 2011-09-24
I agree, Ubuntu 11.10 is great! It is not done yet but it is starting to feel like it is!

---

### Post by Rasa1111 on 2011-09-24
> **ventrical said:**
> It looks like they incorporated some good solid build routines from Lucid and Maveric!! Thats a real bonus because that means a lot less people left out in the cold so-to-speak.

 Definitely.
I've already decided that 11.10 is going to be the only install on my thinkpad. lol
I can run Unity, I can run gnome shell... I'm set! 

Seems like the distro Ive been "needing"/and wanting, is finally here! :)

---

### Post by sammiev on 2011-09-24
Been running it for at least 6 weeks now ( Alpha to Beta2 ). Must say that it's a winner on my computers. :)

---

### Post by ventrical on 2011-10-12
I just want to thank everyone for participating in this thread. It has been a very enlightening , as well as educating, experience for me. I also look forward to participating in alpha/beta testing Precise Pangolin.

  I want to also thank the developers and Ubuntu in general for producing a dynamic distribution with Oneiric Ocelot. The themes, graphics and responses as well as nimbleness and intuitiveness is exceptional. If I was a newbie falling into OSS for the first time I would be stunned (as I was with Maveric and Lucid)

 So I offer my congradulations to all the Ubuntu team and especially  all of us de-buggers and beta testers and hackers!!

Man o man .. it's been a slice !! :)

regards, Ventrical

---

### Post by madjr on 2011-10-12
> **ventrical said:**
> I just want to thank everyone for participating in this thread. It has been a very enlightening , as well as educating, experience for me. I also look forward to participating in alpha/beta testing Precise Pangolin.

  I want to also thank the developers and Ubuntu in general for producing a dynamic distribution with Oneiric Ocelot. The themes, graphics and responses as well as nimbleness and intuitiveness is exceptional. If I was a newbie falling into OSS for the first time I would be stunned (as I was with Maveric and Lucid)

 So I offer my congradulations to all the Ubuntu team and especially  all of us de-buggers and beta testers and hackers!!

Man o man .. it's been a slice !! :)

regards, Ventrical

cant wait to see what happens at the UDS and what new plans come from it.

see u all soon next dev cycle!

---

