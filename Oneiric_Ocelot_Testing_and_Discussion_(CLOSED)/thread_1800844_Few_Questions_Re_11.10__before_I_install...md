---
title: "Few Questions Re: 11.10  before I install.."
date: 2011-07-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Rasa1111 on 2011-07-09
Hey all, 

 I've downloaded the 11.10 Alpha 2 image last night,
and tried to 'test' it out , via Live USB a little while ago..
But I ran into a couple things that I'd like some clarity on before I make a partition for it. 

1. Does "Gnome3" not load properly via Live CD/USB? 
I mean, Does 11.10 need to actually be installed for it to load up? 
 I cannot seem to get the GNOME session to load, and Im thinking (hoping) it is simply because the OS isnt installed. 

When I try to switch to it, 
I get a screen that looks like GNOME3 for the most part,
But everything else is blank, and in the top right corner there is a little "Padlock" icon that says "Live session user"

Im assuming that means., "this is locked and unavailable because you are using a live session"
Is this the case? 

Would installing it fix this so that I could test out the new GNOME3 desk? 

2. For those who have been using 11.10..
have you found Unity to be better/ more stable than it is in 11.04? 

It is rather 'stable' for me, usually no issues..
but the occasional annoying bug/glitch still happens from time to time.
Usually not with the Unity "dock" itself.. Just with everything else. lol

3. The "Appearance" menu/window is no longer present?
How does one change/install themes/icons/etc? 

4. My mind has gone blank..
Don't remember what else I wanted to ask. :o
Knew I shoulda kept the live session open instead of booting back into 11.04. :rolleyes: 

If these questions come back to me, Ill come back and ask them..
But I guess my main concern/question is about the GNOME3 thing. 

I don't need to test "Unity" anymore..
Im as familiar with that as I can get , I think..

But I really just want to give gnome3 a test drive, and work on getting used to it, if possible. 

 Thanks.

---

### Post by sgage on 2011-07-09
I think you are confusing Gnome 3 with Gnome Shell. Oneiric Ocelot is based on Gnome 3. By default you get Ubuntu's own Unity shell, but you can install and use Gnome Shell (though it's not working so great for me at the moment).

There is even a Gnome Panel for Gnome 3.

I think it's important to make the distinction between Gnome 3 and whatever shell is running on top of the Gnome 3 stack - things are confusing enough as it is. I'm not picking on you - an awful lot of folks who should know better are muddying the waters.

People, Gnome Shell is NOT Gnome 3.

As far as the rest of your questions, Oneiric is at Alpha 2, and should probably be expected to have quite a few issues and omissions. Things will work great for a few days, and then start getting flaky for a few days. It gets worked out.

That said, lately things have been working quite reliably for me, though the sound indicator applet has gone screwy.

I too feel the lack of the "Appearances" function, but you can accomplish much the same with a utility called "Tweak Advanced Settings", which is available in the repos. You can adjust other things with dconf-editor, which is in the package dconf-tools, also in the repos.

Remember though, this is still fairly early in the development cycle, so expect the unexpected at any time!

---

### Post by Rasa1111 on 2011-07-09
Hey thanks for the reply.

 No, I understand there is a difference..
But you're right.. it does confuse me a bit. 
Sorry about that. 

 What Im talking about is simply the "GNOME" session, in 11.10. (not "classic") 

That's all I want to test out.

So, Does it need to be installed on disk in order to use it? 
or can it be run from a live session, and something just isnt right on my side? 

Sorry for the confusion. 

Thanks for the quick reply.

---

### Post by sgage on 2011-07-09
> **Rasa1111 said:**
> Hey thanks for the reply.

 No, I understand there is a difference..
But you're right.. it does confuse me a bit. 
Sorry about that. 

 What Im talking about is simply the "GNOME" session, in 11.10. (not "classic") 

That's all I want to test out.

So, Does it need to be installed on disk in order to use it? 
or can it be run from a live session, and something just isnt right on my side? 

Sorry for the confusion. 

Thanks for the quick reply.

No apologies necessary - like I said, I didn't mean to single you out.

The session called "Gnome" is supposed to be a Gnome Shell session (and Ubuntu should have labeled it "Gnome Shell"). I never tried it from the Live CD/USB. I've tried from my installed version, and it comes up in a very simple Gnome Shell, but is a little too flaky at this point even for me :)

It's early days for Oneiric, but one cool thing about early days is that things change rapidly. Go ahead and install it and have some fun testing and experimenting. Just don't trust any important work to it :KS

---

### Post by Rasa1111 on 2011-07-09
haha, Alright, cool. :)

One more question... lol.

 When using Unity in 11.10, I found the "Appearance" menu is gone,
So Im unsure of how to install a new theme or icons. 

Do i have to download/install the "gnome tweak tool" (I think that's what its called) in order to do this?
or how is it done in 11.10?  
It's like they removed even MORE options to be able to customize things how you want them! O_o

Thanks again man. 
I appreciate it.

---

### Post by mc4man on 2011-07-09
> have you found Unity to be better/ more stable than it is in 11.04? 
There have been some 'under the hood' changes and a few minor bug fixes, otherwise nothing different than what's in 11.04 in any regard.
(though gnome/nautilus 3 and O in general is slightly more restrictive, along the 'we know what's best for you' line

> 3. The "Appearance" menu/window is no longer present?
How does one change/install themes/icons/etc?

You can make some minor changes thru the gnome-tweak-tool and I guess dconf/gconf-editor
(I use ambiance so not much of an issue, to change the Selected item color had to manually edit an .rc and a .ini to get rid of the orange

The default gnome-shell works ok here, a bit lacking without extensions so interest for me has faded for the moment.

---

### Post by sgage on 2011-07-09
> **Rasa1111 said:**
> haha, Alright, cool. :)

One more question... lol.

 When using Unity in 11.10, I found the "Appearance" menu is gone,
So Im unsure of how to install a new theme or icons. 

Do i have to download/install the "gnome tweak tool" (I think that's what its called) in order to do this?
or how is it done in 11.10?  
It's like they removed even MORE options to be able to customize things how you want them! O_o

Thanks again man. 
I appreciate it.

No problemo. You are asking the same questions I asked myself, and I'm glad to share what I've learned.

The tool is called "tweak advanced settings" and appears as gnome-tweak-tool in the repos. You can change themes (there are only limited selections at the moment), icon sets, set system fonts and sizes and scaling and such. 

I was able to further tweak things to my tastes using dconf-editor. Got the mounted-volumes icons off my desktop, made the Nautilus side-panel "tree" instead of "places", that sort of thing.

I forgot to ask - how are things on the ISS? How's the broadband up there? :KS

---

### Post by Rasa1111 on 2011-07-09
> **mc4man said:**
> There have been some 'under the hood' changes and a few minor bug fixes, otherwise nothing different than what's in 11.04 in any regard.
(though gnome/nautilus 3 and O in general is slightly more restrictive, along the 'we know what's best for you' line


You can make some minor changes thru the gnome-tweak-tool and I guess dconf/gconf-editor
(I use ambiance so not much of an issue, to change the Selected item color had to manually edit an .rc and a .ini to get rid of the orange

The default gnome-shell works ok here, a bit lacking without extensions so interest for me has faded for the moment.

 Hey, thanks. 

So you mean that you have the same old "Appearance" menu in your 11.10?
It appears to me, it is gone.
Unity can't even find it when I type it in> Like this, in my 11.04 install> [ATTACH]197072[/ATTACH]

and this is the "Appearance menu" Im talking about..
[ATTACH]197073[/ATTACH]
Which is completely missing from 11.10, here. 

You're saying you still have this, in your 11.10 install? :confused:

---

### Post by Rasa1111 on 2011-07-09
> **sgage said:**
> No problemo. You are asking the same questions I asked myself, and I'm glad to share what I've learned.

The tool is called "tweak advanced settings" and appears as gnome-tweak-tool in the repos. You can change themes (there are only limited selections at the moment), icon sets, set system fonts and sizes and scaling and such. 

I was able to further tweak things to my tastes using dconf-editor. Got the mounted-volumes icons off my desktop, made the Nautilus side-panel "tree" instead of "places", that sort of thing.

I forgot to ask - how are things on the ISS? How's the broadband up there? :KS

 ahh cool. 
That sounds like it will be helpful. 
Thanks again man. :)

Re: broadband on ISS..
It's not as fast as some might expect! (can't even call it "broadband")
Safe to say it is not quite as "fast" as dial-up. :lolflag:  :P

---

### Post by mc4man on 2011-07-09
No I mean more like what's in screenshot - the 'tweak' tool
( just noticed screenshots are now labeled by date/time vs. window name, will have to see if that's configurable, wonder whose brilliant idea that was..
there's no guarantee that anything beyond  the basics is obviously configurable, if at all

---

### Post by Rasa1111 on 2011-07-09
oh alright. 
Thank you, man :)

---

### Post by el_koraco on 2011-07-09
You have to get a little manual. Install gnome-tweak-tool, and then you need to manually copy themes that you downloaded off the web insto /usr/share/themes,  and icon themes into usr/share/icons, in order to use them with GTT. 

Plus, you gotta make sure you have the right engines installed, and that the themes are GTK 3, or else you get them falling back on a Clearlooks kinda setting, but like it's 1995.

---

### Post by mc4man on 2011-07-09
As far as screenshot naming - it's not configurable, and no big deal anyway.
Some will like timestamps better, some may not and one is free to rename.
(though the idea that a timestamp is more identifiable than a window name is beyond me.
For the curious - [https://bugzilla.gnome.org/show_bug.cgi?id=565907](https://bugzilla.gnome.org/show_bug.cgi?id=565907)

---

### Post by Rasa1111 on 2011-07-09
> **el_koraco said:**
> You have to get a little manual. Install gnome-tweak-tool, and then you need to manually copy themes that you downloaded off the web insto /usr/share/themes,  and icon themes into usr/share/icons, in order to use them with GTT. 

Plus, you gotta make sure you have the right engines installed, and that the themes are GTK 3, or else you get them falling back on a Clearlooks kinda setting, but like it's 1995.

lol, Things just keep getting more and more "logical" huh? :mad:

Do you know if the "Unico" ~for GTK3 engine is installed by default? 
or do you need to install it? 

lol yeah, I can't stand that "clearlooks"/"1995" look. 
Hideous. 

Thanks for the info. 
Will come in handy Im sure. 
Even though Im now debating on whether to even install it or not. lol :P

---

### Post by el_koraco on 2011-07-09
Ambiance and Radiance are built on Unico, so it should be there. I'm using GS on Fedora for GTK3 fun though, so I'm not a 100 percent sure. The thing is you're not gonna have the array of theme options like you do with GTK2 for a while.

---

### Post by alexandrum77 on 2011-09-21
To change the "Selected Items color" in Oneiric you have to edit the following files:

/usr/share/themes/THEME_NAME/gtk-3.0/gtk.css
/usr/share/themes/THEME_NAME/gtk-3.0/settings.ini

The Ubuntu Orange is #F07746. Replace it with the color you like and restart. This only works for users. When you run any root application (synaptic, gksu something), it will still use the Orange. I haven't figured it out how to change the color for root.

Does anybody know how to change the colors for root applications?

---

### Post by Rasa1111 on 2011-09-21
> **alexandrum77 said:**
> To change the "Selected Items color" in Oneiric you have to edit the following files:

/usr/share/themes/THEME_NAME/gtk-3.0/gtk.css
/usr/share/themes/THEME_NAME/gtk-3.0/settings.ini

The Ubuntu Orange is #F07746. Replace it with the color you like and restart. This only works for users. When you run any root application (synaptic, gksu something), it will still use the Orange. I haven't figured it out how to change the color for root.

Does anybody know how to change the colors for root applications?

Hey, that's good to know! Thanks!
While I do like the default orange color..
I was wondering just last night how one would change it if they didnt like it. 
:)  thanks man.

---

