---
title: "Tutorial - How to Install ALL those Required Plugins in Mozilla Firefox (Web Browser)"
date: 2006-02-23
forum: Outdated Tutorials &amp; Tips
---

### Post by dvarsam on 2006-02-23
Hello all!

I have more "Tutorial" contribution from me:


_Tutorial - How to Install ALL those Required Plugins in Mozilla Firefox (Web Browser)_:


_For Ubuntu 5.10_:


_Prerequisites_:
You should know how to use & work with the "Synaptic Package Manager" program.
If you do NOT have good knowledge of the above mentioned program, please go inside the Ubuntu's "Customization Tips & Tricks" Page & look for the Tutorial I have created, named:

"Tutorial - How to get those valuable ".deb" Program Files & Back Them Up" (Article #: 134914)


_Story_:
I once wanted to be able to view Apple's Quicktime Movie Clips (Streaming Video files), but NOT the kind that you download into your Ubuntu & you can view it later, whenever you want, but the kind of Streaming Video that you view it through (or within) the Mozilla Firefox's Internet Browser window.

So I went in the Forum & made a post on this.
I got many answers, but NO answer stated specifically what I really needed to install.

_Outcome_:
Eventually, if you go & install 10 or 12 programs in your Ubuntu, (some people suggested), at some point you are FOR SURE going to be able to view your  Apple's Quicktime Movie Clips...
... only ALSO you will NOT realize which program made it work or if it were actually a combination of programs that made it work or something else... (maybe a "miracle"!) ...

In the end you will feel like the "guinny pig"(how do you spell that?), where you are going to try anything (anybody) suggests to you, to finally get your job done...  

But do you really want to install SO many programs, while you can get what you want by just installing ONLY 2 programs?

At the same time I ALSO wanted to speak about OTHER required Plug-ins people would need in their Mozilla Firefox Internet Browsers.


In this Tutorial, I will explain in FULL all the needed steps to Install the following Mozilla Firefox's Plug-ins:

1. MPlayer Plug-in - for Mozilla Firefox (Internet Browser)

2. The "w32codecs"

3. Sun's Java 2 Runtime Environment Plug-in – for Mozilla Firefox (Internet Browser)

4. Macromedia's Flash Player – for Mozilla Firefox (Internet Browser)


_Note 1_:
As I mentioned before, you should know how to use & work with the "Synaptic Package Manager" program.
If NOT, go back up (in the beginning of this Tutorial) in the Prerequisites section, read the Prerequisites, and go search & READ through that Tutorial I made, cause you will need it.

Besides, I did NOT make it for me, but for YOU newcomers.

It may ALSO be required (I am NOT sure about this), in order to make all the above packages available in your "Synaptic Package Manager" program for Installation, that you MAY have to tamper your "sources.list" File, inside your Ubuntu's "/etc/apt/" Folder.

_In Brief, let me explain_:
If you launch "Synaptic Package Manager" program, you will notice on your "Status Bar", that the Packages available for installation from the Ubuntu Community are "4.092 packages listed – 1.033 installed" (if you have Ubuntu 5.10 installed).
 If you had tampered your "sources.list" File, you could get  on your "Status Bar", "17.824 packages listed – 1.033 installed", if not more...
That means that thousands of programs (authenticated or not) are available for you to install through the "Synaptic Package Manager" program.

	... isn't it nice to have lets say 5.000 programs (I am NOT including packages 
            designed ONLY to make other programs work properly) that are offered to 
            you for FREE (to download & install), in your Ubuntu Computer, while in 
            Windows, you are ONLY given 10 (or 20) programs overall & for the rest YOU 
            have to pay on an Per-Program basis...
	... aren't you getting ECSTATIC now about Ubuntu or what?

_Note 2_:
This Tutorial's main objective is NOT to teach you how to MAKE available to your "Synaptic Package Manager's" MORE program packages, but to teach you How to Install Mozilla Firefox's (Internet Browser) Plug-ins.
Look at a different Tutorial for this (I currently have NOT made one yet, but probably some other person has – take a look at the Ubuntu's "Customization Tips & Tricks" Page & hopefully you will find one).


_Part 1 – Installing the MPlayer Plug-in - for Mozilla Firefox (Internet Browser)_:

The first thing you will want to ask me, is:

Why do I want this Plugin?

Well, if your Ubuntu is NEWLY installed, it does NOT install (by default), this Plugin to be available to your Mozilla Firefox (Internet Browser).

So, launch a window of your Mozilla Firefox browser & go visit the following Internet page:

	[http://www.pixar.com/featurefilms/ts/theater/index.html](http://www.pixar.com/featurefilms/ts/theater/index.html)

	_Note_:
	The "Warner Brothers" film making company, also Requires (in some cases) 
        the MPlayer Plug-in to let you watch their upcoming Movies releases in 
        Streaming Video from inside your Mozilla Firefox (Internet Browser)...

So, you want to watch the trailer of that old but famous Pixar's "Toy Story"?

Why don't you click under the "Teaser Trailer", the "240x180" one, to watch the Streaming Video from within your Mozilla Firefox (Internet Browser)...

If you have a CLEAN Ubuntu install (meaning that you have just installed Ubuntu but NO other programs), you will probably get a window saying the following: "Totem could not play 'fd://0'" ("Totem" is Ubuntu's default pre-installed Movie Player). Close that window & press on the (Site's) green "Exit" button, to return to the previous Page, the one you first visited.

What happened to your Mozilla's Firefox window?

Did you get the result I got?

My Mozilla's Firefox (version 1.0.7) window unexpectedly closed...

I had to re-launch the Mozilla Firefox Browser window, type that Internet Address again, to go visit that page...

So, what is the problem?

Basically to see this Apple's Quicktime Movie Trailer, you NEED the MPlayer Plug-in - for  Mozilla Firefox (Internet Browser).

How can you get it to install?

Launch your "Synaptic Package Manager" program & perform a "Search" for the program "mozilla-mplayer".

Go on & install this program.

_Note_:
Again, I assume that YOU know how to work with the "Synaptic Package Manager" program.
If NOT, I suggested before, to go & read My other Tutorial –  Article #: 134914.

Some people (people with better knowledge), will probably say:

	Why don't I use my other Method to install ".deb" Packages?
	... I will just use "Synaptic" to get the ".deb" Packages, &...
	... instead of installing them using "Synaptic", I will use the classic old  "dpkg -i 
            filename.deb" method.
	... and I will search for dependencies with the other classic "dpkg -I 
             filename.deb" method, &
	... after I find the order in which I will have to install dependency files, 
            everything will end up ... great...

And they will probably install their programs with NO problem...

However, if they EVER decide to "Uninstall" their programs:

If they are lucky, the program they installed, should have some "Uninstall" ReadMe file or an "Uninstall" button somewhere in the Program's Menu...

If NOT, then they would have to try-out (or experiment) their way to "Uninstall" that program.
... and of course, NO one can assure them that they "Uninstalled" the right way or that they have left some packages behind or that they have even deleted possibly wrong stuff (in the case of a Newbie...)

However, if they had used the "Synaptic Package Manager" program, from the START, they could have easily "Uninstalled" their program in a nice, clean & straightforward way.
The "Synaptic Package Manager" program, does NOT care if the program (you are installing) has an embedded "Uninstall" option.
"Synaptic" keeps track of every install step (the program you are installing makes), so when the time comes you want to "Uninstall", it knows exactly what it needs to get rid off.
But that does NOT mean that you SHOULD start installing a whole bunch of Programs, (without caring whether you really need them or not), & then rely totally in "Synaptic" to clean you up from ALL the "junk" (& trouble) you installed...
"Synaptic" is just a program & it is designed to work perfectly 99.99% of the times.
So, do NOT push it to its limits & get the 0.01% chance to "mess" your system... 
And try NOT to install junk!
Compared to the Windows world, you will eventually find that your Ubunty is much more STABLE, FAST & RELIABLE.
Your problems (crashes, etc.), are going to be VERY little, but it does NOT mean that they do not exist...
Every OS maker would hope to achieve this level, but STILL it is very hard to be achieved by anyone...


_Back to the Part 1_:
You have installed the program named "mozilla-mplayer".

Why don't you go back now & try to see that famous Pixar's "Toy Story" Movie Trailer (created in the Apple's Quicktime format)?

_Result_:
Assuming that you have a CLEAN Ubuntu install, you should NOW be able to view the Streaming Video from within your Mozilla Firefox (Internet Browser), but with NO sound.

So what do YOU do?

Well, you need to install those "w32codecs".


_Part 2 - Installing the "w32codecs"_:

_(Before you Install) Note_:
If you enter a Forum & post a "Please help me install the "w32codecs", you will get a reply:

	Please go read the "Wiki" page, on Restricted Formats:

	[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

_In a few words_:
I am NOT sure about Quicktime specifically, but I assume it's similar to MP3 as far as the legalities go. 
So (as I understand it), the deal with "mp3" is that it's patented technology & if you write any software that plays mp3s you have to (in the US at least) pay a small License fee to the patent holders for each copy of the software you distribute.
When you buy a copy of Windows, for example, the fee for using "mp3" & several other proprietary formats is included in the cost.
Since Ubuntu is distributed for Free, obviously they can NOT afford to pay for a license for each person that installs Ubuntu.
That's why a lot of multimedia does NOT work "out of the box" with Ubuntu. 

In some countries, the law does NOT require such a fee, so you should check the laws for your country and see.
Also, as I understand it, if you own a copy of Windows (that you are NOT using on a different computer), you are allowed to install the "win32codecs" & use them legally.

If any of the above is not accurate, I hope someone corrects me...

_Outcome_:
Is it legal in YOUR country, for you to play these formats?
ONLY if your country's laws allow you to do so, should you play media using the "w32codecs".

OR: 

If you own a copy of Windows (that you are NOT using on a different computer), you are allowed to install the "win32codecs" & use them legally.


So, If you are OK with the above, go on & install in your Ubuntu the "w32codecs".

  
_Note_:
Keep in mind that the "w32codecs" you are installing are NOT Authenticated.
That means, that the program has NOT passed through extensive testing, to get a CERTIFICATION that there are NO problems or Conflicts or "whatever else" (with other programs), when using it...
Install & use the "w32codecs" at your own Risk.

Of course, if CERTIFICATION could GUARANTEE that EVERYTHING would work 100% Fine & with NO problems, then ALL Microsoft's Made products (which I assume have ALL passed CERTIFICATION), would create NO trouble to the Microsoft family Software...
Unfortunately, experience proves the opposite...
... however CERTIFICATION makes us ALL feel a little better!


If you are NOT OK with the above 2 REQUIREMENTS to be able to install the "w32codecs", I do NOT have ANY alternative to suggest to you.
I am sure that there are Always alternative ways to make your "sound" work, but I do NOT know any... (sorry, I am still a Newbie like you...).
Hopefully an Ubuntu PRO could help you out on this or hopefully Add a Post on this Tutorial with suggestions or better Add a step-by-step guide to show other possible directions...


After you installed in your Ubuntu the "w32codecs", go & visit again that famous Pixar's "Toy Story" Movie Trailer (created in the Apple's Quicktime format).

ALL should be working fine & you SHOULD be able to view the Streaming Video from within your Mozilla Firefox (Internet Browser), ONLY this time WITH sound.


_Part 3 - Installing Sun's Java 2 Runtime Environment Plug-in – for Mozilla Firefox (Internet Browser)_:

You will probably want to ask again:

Why do I want this Plugin?

Well, if your Ubuntu is NEWLY installed, it does NOT install (by default), this Plugin to be available to your Mozilla Firefox (Internet Browser).

So, launch a window of your Mozilla Firefox browser & go visit the following Internet page:

	[http://www.intel.com/products/motherboard/d865perl/index.htm](http://www.intel.com/products/motherboard/d865perl/index.htm)

The above Internet link takes you to Intel's Internet Site, on a specific Motherboard Page.

Inside that page, you will probably, see that there is a picture that you can NOT view, because you are missing a Plug-in – the "Sun's Java 2 Runtime Environment" one.

... and you will find a "click here to install plugin" button – only to find that it can NOT install in this 
    way...

_BUT REMEMBER_:
If you install Software with a different method rather than use "Synaptic", there is no go-back (or "Uninstall") option. It's only one way – & no way back!
Better do it with "Synaptic"...

Launch your "Synaptic Package Manager" program & perform a "Search" for the program "j2re1.4-mozilla-plugin".

Go on & install this program.

_Note_:
Again, I assume that YOU know how to work with the "Synaptic Package Manager" program.
If NOT (I suggested also before to), go & read My other Tutorial –  Article #: 134914.
Do NOT make me repeat myself...

Then inside your Mozilla Firefox's (Internet Browser) Standard Toolbar, click on the button named "Reload current page" (the equivalent to Internet Explorer's "Refresh" button – currently NOT "__fresh" but rather "Stinky" & "Rust(y)").

With the Internet Page "Reloaded", now you should be able to VIEW that nice Picture created for "Sun's Java 2 Runtime Environment" Plug-in.


_Part 4 - Installing Macromedia's Flash Player Plug-in – for Mozilla Firefox (Internet Browser)_:

You will probably want to ask again:

More Plugins?	... Oh NO !!! ...

Well, if your Ubuntu is NEWLY installed, it does NOT install (by default), this Plugin to be available to your Mozilla Firefox (Internet Browser), either.

So, launch a window of your Mozilla Firefox's browser & go visit the following Internet page:

	[http://www.nokia.com/](http://www.nokia.com/)

Look around inside that Internet Site & you will find that a Plug-in is missing.

	_Note_:
	The "Warner Brothers" film making company, also Requires (in some cases) 
        the MPlayer Plug-in to let you watch their upcoming Movies releases in 
        Streaming Video from inside your Mozilla Firefox (Internet Browser)...
	Other Companies, include:
	1. Canon
	2. Dreamworks
	3. Paramount Pictures
	... etc. etc. ...

This time, if you click on the "click here to install plugin" – you will find that it CAN be installed in this way!

_BUT REMEMBER_:
As I said before, if you install Software with a different method rather than use "Synaptic", there is no go-back (or "Uninstall") option. It's only one way – & no way back!
Better do it with "Synaptic"...

Launch your "Synaptic Package Manager" program & perform a "Search" for the program "flashplayer-mozilla".

Go on & install this program.


_Conclusion_:
You managed to install the required Plugins to make Your Mozilla Firefox Internet Browser capable to show you pretty much (& hopefully) everything out there... in the Net...

Hopefully there is NO other Plug-in missing to install.

If there is, write to me about it.
We would ALL like to know...

Give us an example too, so that we can see ourselves!


Have Fun !!!


P.S.1> Sorry for my bad grammar syntax (& repetitions), but I have spent more than 
           4 hours (this time) to create this... 
           ... excluding the Formats to my Ubuntu Hard Drive to find which (minimum) 
               combination of programs (installed) makes my Mozilla Firefox work "top 
               notch" ...
           ... hope it is helpful to you too!

P.S.2> I would appreciate if somebody has something to Add that corrects me if I 
           have performed a mistake.

	   PLEASE do NOT add comments like "thanks dude", or "that's how you do it" 
           because people that want to read a Tutorial, end up reading comments of 
           NO Learning value.
	   Thanks !!!

---

### Post by zi99y on 2006-02-24
Thanks for this, but I guess it's only relevant to Firefox 1.0.7 as I'm using 1.5.0.1 and the JRE or Quicktime plugins don't work.

Do you know if there are packages specific to this version?

---

### Post by lleberg on 2006-02-25
Really nice, missed java.. and finaly installed mplayer plugin.

Just one thing.
Mplayer is somehow set not to zoom in if you change the size of your window..
This inclues if you go fullscreen from the plugin...
```
echo "zoom=yes" >> .mplayer/config
```

And this'll make it zoom to fit the video to the window :)

---

### Post by dcstar on 2006-02-26
[QUOTE=zi99y]Thanks for this, but I guess it's only relevant to Firefox 1.0.7 as I'm using 1.5.0.1 and the JRE or Quicktime plugins don't work.

Do you know if there are packages specific to this version?[/QUOTE]
All FF plugins must reside in the "plugins" directory in whereever you have your FF installed. These can either be links or the actual .so and .xpt files, with the following exception:

The Java plugin **must be a link** to the actual file, the file itself will not work if copied to the plugin directory.

All my FF 1.07 plugins work in 1.5.

---

### Post by chaoschannel on 2006-02-28
I just upgraded to firefox-1.5.0.1 myself and ran into the same problem with plugins not working properly when installed from synaptic. So after a bit of tinkering I came up with this fix.

First delete the plugins folder from /home/[COLOR="Red"]YOUR-PROFILE[/COLOR]/.mozilla/ 
WARNING: if you have installed any plugins through firefox your will need to reinstall them from synaptic.
then make a link to the plugins folder at /usr/lib/mozilla/
finally move the link to /home/[COLOR="Red"]YOUR-PROFILE[/COLOR]/.mozilla/
and name it plugins.
In a firefox window go to "about[color="#000000"]:[/COLOR]plugins" and everything should be listed properly

Hope it works as well for you as it did for me.
<I apoligize if this isn't very clear. I'm new to Linux and not familiar enough to give you shell commands. If somebody would like to clear it up a bit that would be apreciated.>

---

### Post by daredevil on 2006-03-01
Have seen this b4. als olook at,,,

[https://wiki.ubuntu.com/MplayerInstallHowto](https://wiki.ubuntu.com/MplayerInstallHowto)

---

