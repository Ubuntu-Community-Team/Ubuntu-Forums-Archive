---
title: "Ubuntu with Gnome Shell: How do I change the font size in top panel"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by shuttleworthwannabe on 2012-01-21
I am using Gnome Shell in 11.10 on my production machine; What I have noticed is that the top panel fonts are quite large and out of proportion with system fonts; and so are the dialogue boxes that pop up when icons are clicked/selected in the top panel; I suspect this behavior is from large font sizes?? or is this the usual panel behavior?

Any one show me how to adjust fonts on the top panel in Gnome Shell?

System I am using: Dell Vostro 3700, Nvidia 330m GForce. (up to date and all additional drivers installed using jockey).

Thanks in advance.

SwB

---

### Post by shuttleworthwannabe on 2012-01-21
A GUI based tool will be great.

---

### Post by MARP1961 on 2012-01-21
Install **gnome-tweak-tool** from Synaptic. When you launch it (it's listed as Advanced Settings) click on **fonts** and change the** text scaling factor**.

---

### Post by shuttleworthwannabe on 2012-01-21
I think changes the DPI scaling--not the font size; [this thread talks about it a bit]("http://ubuntuforums.org/showthread.php?t=1479239"); but i want to know if there anyone who has built a GUI for this??

---

### Post by cmcanulty on 2012-01-21
gnometweak is a GUI

---

### Post by shuttleworthwannabe on 2012-01-21
Okay--I think I did not make myself clear; I am using gnome-tweak-tool; it does font settings for system; I have set the font size to 9 pts; it does change the panel font size as well, but not to 9pts--the solution mentioned in the link I posted on the other hand does it well.
What I am asking if there is a GUI solution for this--so that beginners, like me (even though I have been using Ubuntu for close to 6 years), can customize the interface to their linking.

---

### Post by cmcanulty on 2012-01-21
I think you can get the same result in gnome tweak by moving the text scaling facor to the right. For some reason on my machine the font numbers do nothing but the text scaling works. Very unintuitive.

---

### Post by guidol on 2012-01-29
Faced the same problem, gnome-tweak-tool (besides it stopped working at all for some odd reason) is lacking this feature.

It wasn't too hard though, editing the gnome-shell css file directly did the trick for me:

sudo gedit /usr/share/gnome-shell/theme/gnome-shell.css

In the text file, look for the "#Panel" setting (without quotes). Underneath should be a "font-size" setting, in my case the value was set to 10.5 - setting it to 9.5 worked fine for me.

Save the text file and exit gedit.

Now restart gnome-shell by pressing the key combination ALT-F2. Enter the single letter "r" (without quotes) and press the Enter key. Gnome-shell now should reload with your new settings. Make sure not to mess around too much in that css file ;-) Succes!

More info here:

[http://ubuntuforums.org/showthread.php?t=1479239](http://ubuntuforums.org/showthread.php?t=1479239)

---

### Post by shuttleworthwannabe on 2012-01-29
Thanks I did that--now how to get the pop-ups and border paddings to honor the screen dpi settings--at the moment, they are huge, I want the fonts and bubbles that pop up when you click on username to be reasonably small--not like now, it occupies >75% of the vertical screen space.

---

### Post by anewguy on 2012-01-29
So you'd like a GUI to change the css file for gnome, correct?

I don't know squat about css, except what the initials stand for, so I wouldn't know what to put in for options, but I'd be willing to start working on such a tool - I just thought it already existed.

It might also be something that could be changed in one of the HTML tools - especially if it's a WSIWIG in terms of change the css and the preview changes to reflect it.

Also, is any of this still valid if you're running Unity?

Dave ;)

---

### Post by shuttleworthwannabe on 2012-01-29
That would be great! and I will be willing to give a spin and test it.(or are you just pulling my leg here ;-) 

I think this applies to Gnome Shell only--Ubuntu Unity uses a different windowing manager; GS windows (DE) are transparent by default, DE and pop-up dialogue in Unity are solid.

---

### Post by cbowman57 on 2012-01-29
> **shuttleworthwannabe said:**
> Thanks I did that--now how to get the pop-ups and border paddings to honor the screen dpi settings--at the moment, they are huge, I want the fonts and bubbles that pop up when you click on username to be reasonably small--not like now, it occupies >75% of the vertical screen space.

I don't know how adjusting dpi settings affects the theme but you can go through the gnome-shell.css with an editor & look for popup, combo & pointer, should put you in the general vicinity.

---

### Post by shuttleworthwannabe on 2012-01-29
Hi Charlie--I have done so (through trial and error), but this isa hit and miss, as I do not understand half what is written in code in the css.

What I am looking for (or help with) getting a GUI that would customize the UI in Gnome Shell.

---

### Post by cbowman57 on 2012-01-29
> **shuttleworthwannabe said:**
> Hi Charlie--I have done so (through trial and error), but this isa hit and miss, as I do not understand half what is written in code in the css.

What I am looking for (or help with) getting a GUI that would customize the UI in Gnome Shell.

That would be nice, then everyone could do it.  Wish one existed, would have saved me 100+ hours so far.

---

### Post by shuttleworthwannabe on 2012-01-29
This will be a killa-app; in my opinion, it will bring back the people who felt alienated by GS, be able to work with their desktop environment and also be productive.

Can someone build this app, now?! ;-)

---

### Post by cbowman57 on 2012-01-30
It would be a great app, but despite the fact that I've done a few themes I don't have the programming skills or good enough knowledge of css to even attempt it.

I was making an attempt to create a template that would allow users to enter 5-6 color values and have a decent theme but didn't have any luck implementing it.  You can also use php and fool the system into thinking it's css but that didn't help me.

---

### Post by anewguy on 2012-01-30
Well, I don't know squat about CSS as I mentioned before, but here's my offer:

- if someone can guide me through that file, so that screens can be presented in a logical way and knowing what the options mean, I can try and write the program in C with GTK.

Any takers for explaining how things should be grouped, what they mean, and what a resulting CSS file would look like?

Dave ;)

---

### Post by cbowman57 on 2012-01-30
Just to be clear, how much functionality are you thinking of building into it?

---

### Post by anewguy on 2012-01-30
Well, since I don't know a thing about that file, I therefore have no idea.  I should also mention that I'm running 11.10 and have Gnome enabled according to CharlesA's sticky, and I don't see this file.  Is it still there or is this only for older versions of Ubuntu?

Dave ;)

---

### Post by cbowman57 on 2012-01-30
It would be the gnome-shell.css file, one in every theme.

Here's a snippet I use from the portion that affects the panel.

```
#panel {
    padding-bottom: .15em;
    background-gradient-direction: vertical;
    background-gradient-start: #1b1b96;
    background-gradient-end: #000000;
    color: rgba(221,187,102,1.0); 
    border: .07em solid transparent rgba(221,187,102,0.7);
    border-top: 0px;
    border-left: 0px;
    border-right: 0px;
    height: 1.4em;
    box-shadow: 0px 3px 12px #1b1b96; /*rgba(210,105,30,0.5);*/
    font-size: 1em;
    font-weight: bold italic;
    font-family: Magik, MintSpirit, cantarell, ubuntu, serif;
    
}
```background-gradient- start & stop can be replaced with background-color if a gradient isn't wanted.

padding-bottom is optional

color: is text color

height: panel size, can also use px instead of em

box-shadow:  I use it with some success but remains a bit of a mystery to me.

font-size:  self explanatory, can also use pt in place of em

font-weight: self explanatory

the whole border family is pretty straight forward, can also include border-bottom:

Thanks for considering taking this on Dave.  If you decide to proceed I'll certainly assist all I can within my ability.  Also, if you have to give me by-the-numbers instruction to get exactly what you want don't hesitate to do so. :)

---

### Post by shuttleworthwannabe on 2012-01-31
This is what I like about community participation--thank you Dave and Chuck; i will watch the development and am happy to help test drive this (I am no coder, nor a developer of any kind, just keen learner!).

SwB

---

### Post by anewguy on 2012-02-01
I don't know what I don't have installed or something, but there are no gnome-shell.css file(s) in my entire file system in 11.10.

So, if we take one thing at a time, can the colors be colors that could be selected from a color wheel?  The gradient thing I have to express extreme ignorance on - what does this do, and how might these relate to a color wheel?

Trying to get a better understanding prior to starting the project.  Also, won't be immediate - I'm "debugging" my taxes this week!

Any information/explanations, and at the simplest terms, would be greatly appreciated.

Dave ;)

---

### Post by cbowman57 on 2012-02-01
A color wheel would be the bomb, there's a spideroak link in my signature, grab a copy of ChocoLatte or Absinthe and you can find the files you need to look at.  Are you using gnome shell?  You should also be able to find one in /usr/share/gnome-shell/theme but I don't think it has gradients.  If you pop ChocoLatte or Absinthe in your setup you'll understand the gradients better I think.  It can be used in a few places but it gives that old curved & shaded gnome panel look (think something similar o a stock lxde/lubuntu setup).

At this point any tool would be a godsend but if I could shoot for the moon I'd like to have hex, rgb & rgba capability.  If I were to prioritize and only one method is possible rgba would be the best choice.  You can have variations of transparency with rgba but only solid colors with rgb & hex.  gnome-shell.css can also use simple colors, red, white, black, etc..

I'm not a programmer so really don't know how to suggest you proceed but maybe if you incorporated code for an existing color picker it might give you a jumpstart.  Since you are considering a color wheel method maybe it would also include a color picker so you could click a color on the desktop and it would be added to the pallet.

Whenever or whatever you decide to do I'm available, retired & can meet you online on a schedule that's convenient for you.

I think gpick is abandoned but I thought it overly complicated. It does contain the code for the selector, hex, rgb, I think rgba & even CMY, possibly a couple more.

I have to admit, I'm pretty excited at the prospect of having something like this available. :)

If you just want to look here's a link to my gallery, all but RatRod uses gradients. [http://cbowman57.deviantart.com/](http://cbowman57.deviantart.com/)

---

### Post by anewguy on 2012-02-01
Well, the reason I mentioned a color-wheel is that *if* I'm remembering correctly, it's one of the things that there is a tool for when I do the programming.  And to be clear - gconf-editor doesn't provide the functions you need, correct?

Dave ;)

---

### Post by cbowman57 on 2012-02-01
> **anewguy said:**
> Well, the reason I mentioned a color-wheel is that *if* I'm remembering correctly, it's one of the things that there is a tool for when I do the programming.  And to be clear - gconf-editor doesn't provide the functions you need, correct?

Dave ;)

That's correct Dave, it doesn't go deep at all or make any changes to the shell theme itself. A very simple version could probably be developed around a template and give somewhat limited flexibility.  A deluxe version would be able to parse an existing theme, identify the proper entries and allow you change font, color & maybe a few other values (gradient or non-gradient for example). Naturally I'd like the deluxe version.

Just getting a project like this started is a huge thing & if you decide to limit development but make it GPL others could expand it if you were to lose interest.

I'm of course looking at this from the perspective of somebody that likes to make shell themes.  If you want to make it so anyone would find it easy to use I imagine you'd factor that in.

Actually you might just want to build it to use gradients because all you'd hve to do if you didn't want them is use the same color code for both start: & end:  (actually it might puke if it encountered a theme that doesn't use gradients so probably not such a good suggestion)

Don't want this tl;dr so I'll stop here for the moment. :)

---

### Post by anewguy on 2012-02-02
It probably sounds a little crazy, but what I'd like to do is figure out where themes are stored, then present a drop-box for the user to select the theme.  From there, I would just copy the incoming css file to a new one until I get to the #panel {.  At that point I would hope to present 1 or more screens to let one change things inside the panel, then when they are done append that to the new file and finish copying the input css file to the new.  When done I would just rename the existing css file so it's backed up, and rename the new one to gnome-shell.css.

However, I have Gnome enabled via CharlesA's stickie for getting Gnome in 11.10, and a nautilus search of my entire file system has not yielded a single gnome-shell.css.  So, I still don't know what the rest of the file looks like or where it would be found or how I could do some rudimentary testing here first.

any enlightenment on how I get one of these files to show up somehow in 11.10 would be greatly appreciated!

Hopefully I'll have my taxes finished up by sometime next week so I can get on this project.

Dave ;)

---

### Post by shuttleworthwannabe on 2012-02-02
Dave and Chuck--how about developing something with 12.04 in mind--it is an LTS after all; so if you working this hard for 11.10, might as well put this to 12.04 eternity. And thus, may I suggest, installing Gnome-Shell in 12.04 Alpha 2; then make it available as a PPA???
Is this just wishful thinking?
(an am so excited about this endeavor--as I said, I am no programmer, just a eager-beaver-learner, tester, and etc)

---

### Post by cbowman57 on 2012-02-02
I don't think he's working on this with purely Ubuntu in mind, maybe he is.  I figured he'd just make it generic.

Truth is I rarely even log into Ubuntu anymore but I still love the community so thought I'd lend support where I can. :)

---

### Post by anewguy on 2012-02-02
Well, I finally have the css file.  I had to install Gnome via synaptic package manager - that seems to have gotten it all.

I see there are many "groups" - buttons, panels, etc. - and since I have no clue what any of it is, I'll try to work up something starting next week.  Looks like there are a whole lot of things to accomplish eventually.

As far as 12.04 goes - I have no clue.  I've seen somethings referencing java files of some sort and I don't know it that applies to the default desktop manager.  After installing Gnome from the package manager the first thing I noticed is the desktop, etc., is quite different.  I get a Debian splash screen, an Ubuntu startup screen, and what I assume is an Ubuntu login screen.  There is something called "Activities" on the top bar which seems to show graphically what windows I have open.  I also notice that at least for Firefox, there is only a close button - no minimize, no window, just close button, and it's back on the right.

So, as a dumb guy who has taken his time trying to use Unity, it appears I now have something like light desktop manager, and with that a bunch of learning to do again.

Oh well, at least I have the css file now!

I will hopefully be able to start working with this mid to late next week.  One step at a time - it won't all be there at once - just a piece to try and keep adding pieces.

Dave ;)

---

### Post by cbowman57 on 2012-02-02
OMG!!  Never dawned on me that you weren't already using Gnome shell, but that would explain why you couldn't find the gnome-shell.css.

Yeah Dave, get familiar with the shell a bit before you decide to proceed. :)

---

### Post by shuttleworthwannabe on 2012-02-02
I am rooting for you! Go Dave!

---

### Post by shuttleworthwannabe on 2012-02-04
Okay--just discovered something interesting:

I am playing with Linux Mint 12--it has Gnome Shell and Mate installed by default--I am using Gnome at login. It seems Clem has customized the fonts, panel, and them using an extension from Gnome Shell extensions--and turned on User Themes > **User Themes**

Load shell themes from user directory


When I toggle this setting (on/Off), the panel changes fonts and color--Off--it returns to Gnome Shell theme default (black), on--this is Mint's theme (grey with smaller fonts and smaller dialogue boxes.


Does this add to the clue of what needs be done?

Hope this helps,
SwB

---

### Post by cbowman57 on 2012-02-04
Pretty sure that's just toggling ~/.themes & possibly /usr/share/themes off & on.  That would shift it to use the default that is located in /usr/share/gnome-shell/theme

---

### Post by anewguy on 2012-02-04
Everything I've seen so far seems to indicate you have to restart the theme manager whenever you change the css file, and that is all I'm planning on doing for now - modifying the css file.  In the future, if I find out how to make these things "live" as well I will.

I just need to start small and simple and work my way up on this.

Dave ;)

---

### Post by cbowman57 on 2012-02-04
Yeah, that's easily done by using the alt+f2, r, enter strokes or by logging out & back in.

Most of the gnome-shell.css changes actually occur in real time, normally not requiring a restart of the shell.

Start small & see where it goes. :)

---

### Post by anewguy on 2012-02-07
Making a slow bit of progress.  I had to post on a GTK forum as there are some things I don't understand.  So far they've been great at giving me answers.

What I have so far is an opening screen with a button.  You click on the button and a color wheel comes up.  You have to click on an eyedropper, click the eyedropper on the color wheeel, then click "Select" and it returns to the first screen.  The color wheel thing is a GTK built in so I don't really have much control over what goes on it.

But, this is a good first step - let me explain.  For entries in the css file that require color selection, all I need is a button with the existing color that "calls" the color wheel and returns the new color.  In other words, the "guts" are there for colors.  Reading the css file, replacing the entries as needed, is no big deal to me (I'll probably regret those words at 3 a.m. some night when I'm cussing at myself for "not getting it" ;) ).

So, I hope you can see it's a good step even though it may not sound like it.  I'll keep you updated, and I will try to get the source code posted on my Ubuntu One page for download and testing.  Just need to get further yet unless someone is interested in just seeing this. ;)

Dave ;)

---

### Post by cbowman57 on 2012-02-07
Morning Dave,

Even  slow progress is progress. :)

Have you expanded your project to include gtk-3.0 also or did you just go after some technical info.  Either way is fine by me.  Sounds like you were able to find a source that you can relate to but I'm still here if there is anything I can provide that might be useful.

At this stage I'll just be one of your cheerleaders and offer moral support.

Go Dave!  ;)

---

### Post by cortman on 2012-02-07
+1.4+e82 to this project!

This is what I have long considered the win-or-lose feature between Unity and Gnome shell: A decent GUI utility to let the user REALLY customize the shell. Gnome-tweak is ok in some ways, but others (themes?) is sadly opaque. A utility that would allow

[LIST]
[*] Change panel fonts/sizes/weights/colors (widgets, etc)
[*] Change panel width
[*] Change panel color
[*] Change notification area location
[*] A much more intuitive theme placer (rather than browsing for .zip files, or changing the border theme, the GTK theme, and the user theme?)
[*] Add or remove widgets to the panel (the program could come bundled with most available extensions, and ppa's for them)
[*] Add panels to the sides or bottom
[/LIST]

etc., etc. These are just a couple that come to mind.
I like Gnome shell a lot and use it on my production laptop. Gnome tweak has its good points too, but is sadly lacking on intuitiveness (in a lot of cases) and options.

I don't know much about .css or programming either, but I'd be happy to learn as I go to contribute to this project. Do you have this on launchpad, Dave?

---

### Post by anewguy on 2012-02-07
Nope, not on launchpad or anything.  Thought it might be best not to do anything like that - might get people's hopes real high and then what I might be able to do may seem like a joke.  So, I thought I'd just do it myself for now and have a couple of you test.  I think the 1st 4 options on your list I can handle readily - the others I don't have a clue on but can check on as things progress.

Dave ;)

---

### Post by anewguy on 2012-02-07
BTW - it may not be the prettiest or most elegant thing, as I'm not that good in programming in C and definitely not in GTK, but what I'm hoping is that *maybe* after I get some of these basic functions going there will be others who might want to put additions in it.  Not knowing css, and in particular not knowing what the Gnome Shell expects or does with things in the css file, this could be a little interesting for a while.  If someone knows of a site that explains the Gnome Shell css file, including things like allowed variables, their ranges, ones that can't be "x" if another is "y", etc., so I can try to get even a basic understanding of the thing would be appreciated.  I can code based on what's in my css file and make changes as people test, but it would be kind of nice to at least have the most basic of understandings of what the css file actually does.

Dave ;)

---

### Post by cbowman57 on 2012-02-07
Don't know if this is helpful to you or not.

[http://disruptive-innovations.com/zoo/cssvariables/](http://disruptive-innovations.com/zoo/cssvariables/)

---

### Post by anewguy on 2012-02-09
I should have the start of being to update the panel options sometime next week.  I hope you guys aren't too disapointed when you see it - I don't know graphics programming so it's a pretty basic GUI app.

Dave ;)

---

### Post by cbowman57 on 2012-02-09
I'll be looking forward to seeing it, whatever it looks like. :)

---

### Post by anewguy on 2012-02-14
Ok, I've got it to where it will allow you to select the panel color and the panel background color just so I could get things working simply for now before adding more.

Now is where I need help with that file -> when I use the color wheel and select each of those colors, then copy the resulting test css file over to the gnome-shell.css file and logout/login with Gnome shell, I don't get a panel at all.  Zip, nada.

These would seem to be straight forward, but there must be something the actual processor of that file has for rules or something that I'm not meeting.

Anyone find any detail on what/how the actual contents can be used?

---

### Post by cbowman57 on 2012-02-14
What's the content of the test.css & how are you merging it into the gnome-shell.css?

---

### Post by anewguy on 2012-02-14
Currently I don't merge it - just trying to get things working first.  I manually copy it over to the real gnome-shell.css file.  Since the file is huge, I'm just showing the pertinent part here.  Please note that no errors show up.  I had to do some debugging at first due to some typos generating gnome-shell startup errors when parsing the file.

```
/* Panel */

#panel {
    color: #0008f0;
    background-color: #00a5ff;
    border-image: url("panel-border.svg") 1;
    font-size: 10.5pt;
    font-weight: bold;
    height: 1.86em;
}
```

I know the original had the word "black" as the background color, but I don't know how to do a translation from the hex to a word.  I've read about some charts being available but there are literally thousands of combinations of words.

I've also tried removing the border image statement - it indeed removes the border image, but every button/clickable area and text on the resulting panel isn't there.

Thanks again!
Dave ;)

---

### Post by cbowman57 on 2012-02-14
Doesn't look like there is anything wrong with that.  Here's the similar entry from one of my themes. ```
/* Panel */ 

#panel {
    padding-bottom: .15em;
    background-gradient-direction: vertical;
    background-gradient-start: rgba(0,100,0,0.9); 
    background-gradient-end: rgba(0,0,0,0.9);
    color: rgba(221,187,102,1.0); 
    border: .05em solid transparent rgba(93,252,10,0.3);
    border-top: 0px;
    border-left: 0px;
    border-right: 0px;
    height: 1.4em;
    box-shadow: 0px 5px 10px rgba(93,252,10,0.2); 
    font-size: 1.1em;
    font-weight: bold italic;
    font-family: Magik, MintSpirit, cantarell, ubuntu, serif;
    text-align: center;
    
}
```

---

### Post by anewguy on 2012-02-14
Judging by what you have for panel options compared to mine - taken from the default css file - there must be a lot more options and possible values I don't know.  I really need to find some sort of tech documents explaining the css file, possible options and possible values.  Without that, I doubt anyone would really want what I'm doing so far.  I'd like to present a screen with all of the possible panel options (when panel options is selected from the main screen), a button for each saying whether or not to use that option, and a drop-down list of allowed values (except on colors and fonts, which will be selection screens).  I don't understand at all the information you have in your fonts portion.

So, while I have guts of the process in place, I need details to really be able to continue.  Just presenting the option to change the panel color and the background color, as an example, obviously won't cut it.

Dave ;)

---

### Post by anewguy on 2012-02-14
Just did some more testing - turns out background image and background color are mutually exclusive (it was one of those "doohhhh" moments ;) ).

I'm going to spend some time tonight looking for info for panel setting in the css file.

---

### Post by cbowman57 on 2012-02-14
I wish I could find a good tutorial myself.  But I've found I just picked up enough to get by as I went along.

---

### Post by anewguy on 2012-02-14
Went right to the gnome 3 site - nothing there that I could find.  Do you know if Gnome Shell comes from somewhere else?

I went to MicroCenter tonight and found a $40 book on sale for $7.99 - it's about css, so that can possibly help me more.

I need to rework the interface for panel options since the current one, even for testing, is very different from what I see now I need to do.  This will take me a few days (or I should say,nights).  I've put a lot of effort to get to where it is, but at least now I can build on it easier.  The using GTK for the first time in a few years has been tough.  Combine that with my nearly 2 decade absence from the field and hence any real C programming, and the working with C has been a challenge as well.  Slowly but surely.

I've attached 3 screen shots of what I've done so far.  The pscmain is the opening screen.  The pscpanelmain screen is the main screen (this is what is going to DRASTICALLY change) for panel options.  The pscpanelcol is the color selection screen - in this case for the panel.  I wanted to attach those so people could see where I've gotten in a week's worth of nights.  Knowing what more I know now, the pscpanelmain screen is going to change so much you won't recognize it the next time around.  This at least proved the concept.

Dave ;)

---

### Post by anewguy on 2012-02-15
Ok, I've started on the radically different panel options screen.  The attachment shows just the start. There will be a colored box by the Panel Color which will be clickable to call up the color wheel to select the new color. There will be additional options on the background image and background color lines.  Obviously a lot more options will be added to the screen.

After that, I need to add code to load everything from the existing file.  I still won't add code to actually replace/update the css file -> for now it will be up to the user to do the copy.  That will be changed later.

dave ;)

---

### Post by cbowman57 on 2012-02-15
Looks like a good start.

---

### Post by kendoori on 2012-02-16
I was looking to reduce the font size and make it less bold, which I was able to do. The side effect is that the size of the "active" app icons that appear in the panel are too large for the size of the actual panel. Look at the way the Firefox icon exceeds the height of the top panel per below. Which element controls the size of that icon? or what's the easiest way to pad the panel when an app is running. I tried playing around with with #panel (added padding, also adjusted height), also app-menu icon width and height... Neither did as desired.

[IMG]http://www.tpchealthcare.com/downloads/Selection_045.png[/IMG]

---

### Post by anewguy on 2012-02-17
BTW - I made another small change to the selection screen - I made the yes/no buttons toggle buttons instead with no labeling text.  I've attached a screen image for those who are interested.

Right now I could use any input on how to get setting of a GTK widget (in this case, a GTK label) to change it's foreground and background colors.  I have followed what is in the online GTK 3 documentation but for some reason the colors on the screen are not changing.

I also could use some help figuring out how to convert the transparency value.  The GTK calls return it in what they call an "alpha" field - it's really a 16-bit integer and returns a value like 65000+.  The CSS file needs opacity (the alpha) as a fraction -> things like 0.3.  Does anyone know how or can point be to something that tells me how the heck to do this conversion?

I know the progress is slow - but I am working on it!  It's just taking more time initially than I thought, and I'm going to need to take a night or 2 off from programming until 3 or 4 a.m..

Thanks!
Dave ;)

---

### Post by shuttleworthwannabe on 2012-02-17
@dave (aka-anewguy)--I wish I could help--I am clueless when it come to programing or even digging deep into code/GUI creation. I can only offer you SOLID encouragement to carry on--I can see you may on to something here.

I am just checking if you had a look at how "themes" are created--because they also edit the CSS file to some extent; that must be a clue to something??

---

### Post by cbowman57 on 2012-02-17
I thought you were just trying to create a tool to modify a gnome-shell theme, I didn't know you were going to expand it into  gtk editor also, or are you just trying to extract color information?

---

### Post by shuttleworthwannabe on 2012-02-17
Guys--there is another thread that talks about changing color of Unity panel [here]("http://ubuntuforums.org/showthread.php?t=1927012&referrerid=67282"). If it may help shed some light??

---

### Post by anewguy on 2012-02-20
What I've been working on is a program to change the gnome shell css file.  right now it is just in it's beginnings, so I'm just showing setting the panel color and the background as an image or color.  I'm getting the feeling that what I'm doing may not be what is needed or wanted.

Unity isn't gnome shell.  I found that out when I kept trying to find the gnome-shell.css file and it wasn't there with Unity.  I had to install gnome-shell to get it, and it runs as a separate desktop manager instead of Unity.  So......for now I'm not interested in Unity UNLESS I find the page(s) have some insight into the css file, etc..

I also need to take a break for a week or so.  I've been working on this too many nights, and all weekend days and nights, and it's slow going due to my learning curve on simple things.  It's gotten a little agravatting and that reminds me too much of work - as Maynard G. Krebs said "*work????!!!!*  I'm just kind of going in a circle trying to get one thing to work right now and I just need to back away and come back with a fresher mind.

---

### Post by anewguy on 2012-02-21
In the break while I'm not messing with a program (which currently lets you select and set the panel color and opacity - a long journey just to get to that due to some things in GTK - the interfaces for building a GUI - not doing even what their sample code shows - big thanks to pbrane for his excellent help and long, long patience!).

I've been doing some reading, and if I understand things correctly, you "theme" Gnome 3, and the CSS file describes how things are to work in that theme.  I found something on the net (unfortunately I lost the link but will get it back) that explained a little about the CSS file - not the details per se of this particular CSS file, but at least a sample that shows how it is used in place of some of the old GTK themeing things.  Seeing the GTK statements and then what it translates to in CSS is a big help.

---

### Post by anewguy on 2012-02-22
This project is officially cancelled.  I'm too dang stupid to be able to figure out the simplest dang things with GTK/GDK, and I'm tired of fighting it.  It has turned from a labor of fun and learning into a labor of EXTREME frustration at not understanding pieces of the programming tools I have to use.

I'm sorry guys - anyone else could probably make this work.  I'm just too dang stupid anymore.  So much for all the work I did for so many years - it's like I don't know anything.

Dave ;(

---

### Post by shuttleworthwannabe on 2012-02-22
Hey Dave--no hassles; every attempt was a step forward. At least you gave it a go--and we appreciate the time and effort you out into this.

Let us see if someone else can pick this up.

BTW, how do we make this sub-project prominent so it is known "out-there"? Best would be to alert the Gnome Shell/Gnome 3.x developers? but how?

Great,
SwB

---

### Post by anewguy on 2012-02-23
It took all night again, but I finally got things back to where I wanted them.  So the project is back on!

I'm attaching some screen shots - it's just very basic right now as it is only covering panel color and panel background color.  I figured going with those 2 items first I might perhaps get most the headaches of learning out of the way - I just didn't know there'd be so many!

The opening screen is just dummied up for now so I could get to the panel screen, so it won't look like that further down the road.

Hopefully you can see it's getting somewhere now and hopefully it's a start of what you are looking for.

Note that the background can have an image or a color.  The selection buttons are there to toggle between image and color, and they do indeed toggle, but the image file handling isn't in place yet so it does nothing.

Next up: background image selection.

Thanks for being patient with me - this got me REALLY frustrated but I'm back on track now.  

Dave ;)

---

### Post by shuttleworthwannabe on 2012-02-23
Panel fonts?? next hopefully?

---

### Post by cbowman57 on 2012-02-23
I know the feeling though, I've forgotten much more than I know.

Whatever you decide to do, or however long it takes is fine.  Sometimes we need to step back & get a fresh perspective.  Glad you're making some progress. :)

> **anewguy said:**
> It took all night again, but I finally got things back to where I wanted them.  So the project is back on!

I'm attaching some screen shots - it's just very basic right now as it is only covering panel color and panel background color.  I figured going with those 2 items first I might perhaps get most the headaches of learning out of the way - I just didn't know there'd be so many!

The opening screen is just dummied up for now so I could get to the panel screen, so it won't look like that further down the road.

Hopefully you can see it's getting somewhere now and hopefully it's a start of what you are looking for.

Note that the background can have an image or a color.  The selection buttons are there to toggle between image and color, and they do indeed toggle, but the image file handling isn't in place yet so it does nothing.

Next up: background image selection.

Thanks for being patient with me - this got me REALLY frustrated but I'm back on track now.  

Dave ;)

---

### Post by cortman on 2012-02-23
> **anewguy said:**
> It took all night again, but I finally got things back to where I wanted them.  So the project is back on!

I'm attaching some screen shots - it's just very basic right now as it is only covering panel color and panel background color.  I figured going with those 2 items first I might perhaps get most the headaches of learning out of the way - I just didn't know there'd be so many!

The opening screen is just dummied up for now so I could get to the panel screen, so it won't look like that further down the road.

Hopefully you can see it's getting somewhere now and hopefully it's a start of what you are looking for.

Note that the background can have an image or a color.  The selection buttons are there to toggle between image and color, and they do indeed toggle, but the image file handling isn't in place yet so it does nothing.

Next up: background image selection.

Thanks for being patient with me - this got me REALLY frustrated but I'm back on track now.  

Dave ;)

Awesomeness! That is the beginnings of perfection right there. Keep it up, Dave! That's looking like some serious potential. If I can help in any way, let me know.

---

### Post by cbowman57 on 2012-02-23
A way to enhance the capability, when you get to that point, is to identify the original panel color, pick the new one & have the capability to search & replace all instances of the old color, which would make for a pretty complete custom theme.  About all that would remain would be playing with contrasting text colors (which in the gnome-shell.css is just identified as **color:**)

---

### Post by anewguy on 2012-02-23
Currently, at least for the panel option, the idea is to read in the current values, show them, and allow them to be modified.  So, in a real-world situation the "default" color that would show when you start the app would be the current panel color in the existing CSS file.

Fonts are on the list - probably right after the background image selection unless there are some more background options I should know about - then I'd like to keep them together.

Slow going, and to be honest, I don't know why the Gnome Shell folks don't already have a tool to do this.  I haven't taken the time to look.  Has anyone really scoured their site to see if such a tool exists?

Dave ;)

---

### Post by shuttleworthwannabe on 2012-02-24
@Dave--to be honest, Gnome Shell and Gnome 3.x by default even lack simple customization tools, take gnome-tweak-tool--this is absent from the default installation; it is the first thing I install when I install Gnome Shell on top of Ubuntu's Unity. So I doubt if such a tool you are developing exists--but, I have not done an extensive search so I may be wrong.

And again, great work there!

---

### Post by cortman on 2012-02-24
He's right- and I am REALLY disappointed and very surprised that the Gnome team would release not one, but a couple (Gnome 3-3.2) versions of the DE STILL without any simple customization tool like you're creating. Something like this, I believe, could easily decide the Unity vs. Gnome shell battle.

---

### Post by anewguy on 2012-02-28
slowly but surely......I hope to soon have just a test version available for just working with the panel color and the panel background - color, image or colors with a gradient.  For now, it will just create a new css file without paying any attention to what exists - it will be like the css file delivered with gnome-shell but with the panel color and/or panel background modifed.  I know that may not sound like much, but it's taking quite a bit of work for me to get just those parts.  I've also decided to back off of the working all night on it thing and go back to working on it for a reasonable time on the days I have time.  But don't worry - it's a work in progress and will get there.

do any of you change any of the options other than the panel options?

Dave ;)

---

### Post by cmcanulty on 2012-02-28
Thanks for all your work! I hope the text color will be optioned also. When I get a theme with light panels the white text disappears.

---

### Post by anewguy on 2012-02-28
Yeah - I'll be getting to text, corners, etc., a little later.  For right now, I'm just trying to get these 4 "little" pieces working - it's been a test of trying to get back some programming skills that left me years ago (I haven't worked since 1996) and the code shows it;)  Plus, I'm also using GTK functions in the programming - GTK allows the GUI programming - and let's just say that's been a "challenge" due to my ignorance and some rather iffy documentation - it defines things great but lacks the sample code I like to see.

So, yep - it will be coming.  Just getting my feet wet with these parts ;)

Hope things are going good with you!

dave ;)

---

### Post by anewguy on 2012-03-05
Okay, finally a simple test version for someone to try.  It only does panel-color, and panel-background options (color only, file or gradient).  There is a small readme, but remember this is just in its' infancy, so the readme is to just get you started with how things are now.  The program isn't real fancy.  I *think* I've avoided anything that might be distribution specific at this time, but I really have no way of knowing.

The zip file contains everything for now to get started.  You'll be compiling source code for now, so there are notes in the readme for those packages you will need to either install or be sure are installed.

I'm sure it will break in 2 seconds, but hey.

it will create a file called test.css -> you can scan through that file to see the changes it made in the panel section.  If you want, you can backup your existing file, then copy this one over (remember to rename it to gnome-shell.css) and actually test it if you want.

No promises on suitability, etc., etc., etc., - in other words - it's an alpha program and comes with all those warnings, including that I'm not responsible for anything! ;)

Please try it, see what you think so far (more options will be coming, I just want to be sure I'm on the right path for what you want first), and break it and tell me how you broke it and any error messages (like segmentfault, GTK errors, etc.).

Meanwhile, I'm going to get a little sleep.

EDIT:  AFTER SLEEPING A WHILE, I DID SOME MORE TESTING - FIXED A COUPLE OF THINGS AND CHANGED 1 SCREEN TO BE A LITTLE EASIER TO USE.  CAN'T CHANGE THE ATTACHMENT HERE, SO PLEASE USE THE ATTACHMENT ON MY NEXT POST INSTEAD.  THANKS!

Dave ;)

---

### Post by anewguy on 2012-03-05
OK, please use this attachment instead of the previous.  I corrected a couple of errors and modified a screen to be easier to use.

---

### Post by cbowman57 on 2012-03-09
> **anewguy said:**
> OK, please use this attachment instead of the previous.  I corrected a couple of errors and modified a screen to be easier to use.

Looks like some nice progress being made.  Really like the color wheel and the fact that it writes with transparency when selected.  Like what I see so far.

I didn't test everything but noticed that with the gradient feature it's adding a : before rgba on the end gradient,  ex. ```
rgba:(
```Easy enough to spot & edit.

---

### Post by anewguy on 2012-03-15
Hey, sorry I haven't been back here to check this thread for a week or so.  I built up a new PC and have Windows 7 64-bit and Ubuntu 11.10 64-bit running on it.  The freakin' wireless would work in Ubuntu, but not in Windows (how's that for irony??).  I had to wipe the PC, install Windows and install the wireless driver before I installed ANYTHING else, including the motherboard drivers!  What a PITA.  But, everything is cool now so I should be able to get back to the program.

cbowman57, thanks SO MUCH for the testing so far and the finding of the error I need to correct.

I'm working on the panel font right now, but it's getting into something else I don't know - pango - in order to pull the pieces out of the returned string for the font.  So, I've got to read more, try more, cuss more, and repeat that cycle until I finally can do it.  Hopefully won't be TOO long.

Thanks again!!

Dave ;)

---

### Post by cbowman57 on 2012-03-15
Take your time Dave, with 3.4 on the horizon we may have to adjust anyway, but I think the portion you're working on now shouldn't be affected.

---

### Post by anewguy on 2012-04-28
I've let this slide for now.  Any more knews on the new update and how it might effect what I have been doing?

Dave ;)

---

### Post by cbowman57 on 2012-04-28
> **anewguy said:**
> I've let this slide for now.  Any more knews on the new update and how it might effect what I have been doing?

Dave ;)

No problem, we've got all the time you need.

From what I've seen so far, 3.4 shouldn't have any affect on what you've done.

---

### Post by anewguy on 2012-04-28
Well, guess I'm going to have to get back to work!

Dave ;)

---

### Post by anewguy on 2012-05-22
OK, what with the warm spring and summer coming on, I haven't done much yet.  I'm trying to get this font thing figured out.  I want to present fonts in a box, font size in a box, font color in a box and font height in a box, but not having much luck finding anything tool-wise to help me.  The font selection in GTK is, well, shall we say "different" from just about every font selection I've ever seen.  I've got to figure out how to pull things apart so I can build what I want to present.

Also, at least for Ubuntu 12.04 (and I assume this is probably a GTK/GDK thing actually), the color selection tool changed.  It appears "they" decided to give a small selection of colors in boxes, with an "advanced" selection to move on to a wider selection.  I'm going to have to go find some docs and find out what changed and if there is any way to go back to the old color wheel.

So, progress may be slow for a little while - the weather's too nice and outdoors calls.  I haven't forgotten, I haven't stopped - just slow ;)

Dave ;)

---

### Post by cbowman57 on 2012-05-23
That color selector in 3.4 took a great leap backward IMO.  Now I have to use the selector & gcolor2 to find the code I want.

Take all the time you need.  :)

---

### Post by anewguy on 2012-05-23
Yeah, I HATE the new color selector.  I will try to look into what you mentioned and see if that helps me out.

the font thing is also not good in my opinion.  The old (I think prior to version 3) selector showed font name, size, bold/italic, etc., and height in separate spaces in the selector box.  This new way of having things like "arial bold italics" as a font name is rather clumsy - it should still be a font family like "arial" with bold/italics as separate options.  Right now I'm trying to figure out how to get a list of font names - I've seen an old GTK function for doing so into a listbox, but I don't know if it is current or not.  There is another still-supported font selector I'd like to try, but I keep getting errors about setting window on a high level object, and I have no idea why.  I have a main window and it gets hidden when the panel selection is made.  Panel selection has it's own window, and this is where I try to use the other font selector - the user clicks a button, I pop up the selector.  But this is where it fails with the parent window errors.  I'm at a loss on that, and the devhelp just doesn't have the information I need.  Can't seem to find a decent example on line either.

I'll get this yet - if I can just get the list of fonts easily - like into a list box, then I'll give that a try.  I just need to get some serious time in working on it without getting too frustrated with myself for not understanding a lot of the documentation and the errors.

Dave ;)

---

### Post by cmcanulty on 2012-05-24
in 11.10 and 12.04 classic my panels keep changing back to grey even when set to blue. Does this on several different computers and is very irritating.

---

### Post by traditionalist on 2012-05-24
This will do what you want I think. Works great on my system in combination with the Gnome tweak tool;

[[IMG]http://img213.imageshack.us/img213/3341/gnomecolorchooser006.th.png[/IMG]]("http://img213.imageshack.us/i/gnomecolorchooser006.png/")

you can get it here;

[[IMG]http://img232.imageshack.us/img232/1625/ubuntusoftwarecenter007.th.png[/IMG]]("http://img232.imageshack.us/i/ubuntusoftwarecenter007.png/")

---

### Post by cbowman57 on 2012-05-24
This is an interesting tool.  Writes it's own .gtkrc basically, nice for adjusting some problem areas in gtk-2.0 displays (Firefox).

Might want to review the code in this if you can find it Dave.  Might be adaptable to gtk-3.0 as well, and the shell as well.  Dunno, maybe.  :)

> **traditionalist said:**
> This will do what you want I think. Works great on my system in combination with the Gnome tweak tool;


you can get it here;

[[IMG]http://img232.imageshack.us/img232/1625/ubuntusoftwarecenter007.th.png[/IMG]]("http://img232.imageshack.us/i/ubuntusoftwarecenter007.png/")

---

### Post by traditionalist on 2012-05-24
Yes, I adjusted firefox and thunderbird to suit my preferences, along with a lot of other stuff. Played around for a couple of hours to get it all set up but it was quite easy to do.

I wanted fairly dark ( but functional!) themes. Most of those available are either very poor or barely functional. ( Black on black text etc).

This worked very nicely.  This is what Firefox looks like now;

[[IMG]http://img526.imageshack.us/img526/8376/workspace1008.th.png[/IMG]]("http://img526.imageshack.us/i/workspace1008.png/")

and I have all my other software set up with the themes I like.  By far the easiest tool I have ever used for such a job.

Some examples;

[[IMG]http://img39.imageshack.us/img39/7731/workspace1010h.th.png[/IMG]](http://img39.imageshack.us/i/workspace1010h.png/)


I thought some of the brighter colours might be a nuisance, but they are proving extremely useful;

[[IMG]http://img207.imageshack.us/img207/3184/imageshackuploader23001.th.png[/IMG]](http://img207.imageshack.us/i/imageshackuploader23001.png/)

---

### Post by cbowman57 on 2012-05-24
I agree, most of the themes I do are dark & I spend an awful lot of time trying to correct that.  With gnome-color-chooser maybe I can be a little less picky. :)

---

### Post by anewguy on 2012-05-26
Well, I finally got a combobox showing only the font names, sorted alphabetically.  I need to add checkboxes for bold and italic, a size combobox and a height combobox.  When I get those things in so I am at a break point (i.e., all things related to fonts work), I'll take a look at that tool. 

Also, I'm just doing this to work on the css file for gnome shell itself - not making a handle all themes kind of thing.  If everyone really wants an all-inclusive tool we may want to beg the gnome tweak tool writers to add this functionality.

Dave ;)

---

### Post by cbowman57 on 2012-05-26
That sounds like a good plan Dave.

I don't plan on going anywhere, in the interim I'll just continue using gcolor2 & gedit. :D

---

### Post by anewguy on 2012-05-26
While I'm at it, does anyone here know if you can use gtk_widget_modify_font on an entry in a gtk_combo_box_text??  I've been trying to set it (it does compile ok) but it doesn't change the font.

Dave ;)

---

### Post by cbowman57 on 2012-05-27
Wish I knew more about gtk, & programming, I do a lot of trial & error myself. :)

> **anewguy said:**
> While I'm at it, does anyone here know if you can use gtk_widget_modify_font on an entry in a gtk_combo_box_text??  I've been trying to set it (it does compile ok) but it doesn't change the font.

Dave ;)

---

### Post by cmcanulty on 2012-05-27
I am using the color chooser but my panels still switch back to grey

---

### Post by anewguy on 2012-05-27
If you are running the test version of my program, it writes the css file out in it's own folder.  You need to copy it (and change the name to match) over the existing one (needless to say, back up the existing one 1st - I forgot to the first time ;) ).  I would imagine there might be certain color combinations that may not work - I don't know anything about the actual gnome-shell to know how it handles the colors - my program is just based on the css file.

Getting font selection to work.

I've changed to using the notebook format, which makes things easier to manage.  Going by the link towards the beginning of the thread, where it shows what sections/lines to edit to change different things, I plan on trying to build those notebook pages in the same type of way - keeps things separated easier.  Right now in the version I'm working on the panel options are the only page, so it just shows, with the tab at the top that says "Panel Options".

Dave ;)

---

### Post by cmcanulty on 2012-05-28
Sorry to be dense but can you explain where the folder it creates is and where the original is and how to make it work.

---

### Post by anewguy on 2012-05-28
> **cmcanulty said:**
> Sorry to be dense but can you explain where the folder it creates is and where the original is and how to make it work.

No problem!

The program creates a file called "test.css" in the folder that the program is run from.  Once you're satisfied it looks like it should, you need to:

sudo cp test.css /usr/share/gnome-shell/template/gnome-shell.css


Also - for now, since it's a lot more work and I just wanted to build parts and have them work first, the beginning css file is hard-coded in the program.  I haven't checked it against the new one yet - hopefully it's still the same.  After I get the pieces working, then I'll go back through and read the css file, locate the pieces and replace pieces as needed.

BTW - I'm working on fonts as we speak.  Finally got one big stepping stone solved with that so the rest of the font selection should go quickly.  I can post up another test version of the program after that if you'd like.

Dave ;)

---

### Post by cbowman57 on 2012-05-28
Didn't hurt me to review your process too, been awhile since I tested it.

---

### Post by anewguy on 2012-05-29
I'm just about finished with getting all the font information - need to add height and the option for pixels or ems.  Once I've got that I need to actually build the output css statements for the font.


The attached zip file is the latest executable if anyone wants to try it out.  The font selection tools are almost complete but they don't generate any output.  GTK changed their default color selection so until I can find someway to get the old back, the current color selection is much different - you'll need to click on the "+" to get to more options.  It's not the color wheel - that's what I'm trying to see if there is a way to get back to.  The same limitations apply as originally.

Slowly but surely.  I hope you can see from the notebook page idea that each of the sections in the css file will eventually be a separate (or maybe even more than 1) notebook page.  I also haven't found a way to change the background color for a notebook page.

If you do try it - let me know of any errors, and also what you think.

It's a slow process - I'm trying to pick back up on C and trying to do more with GTK than I have done in the past, so it's a big learning curve.  Top that off with not actually knowing anything about css, and it makes it interesting generating something that I don't have a clue how it works!

Dave ;)

---

### Post by cbowman57 on 2012-05-29
I just want to hit some switches, push a couple slides & generate something like this.

[ATTACH]218872[/ATTACH]

Is that too much to ask?  :D

I'll try & look at your tool within the next couple days, this project is keeping me busy with gcolor2 & gedit. :)

---

### Post by Shadius on 2012-05-29
Maybe this link will be of use to you about understanding CSS. I'm not a programmer or anything of the sort, but I find your venture very interesting as I am interested about coding myself. :) 

[CSS]("http://www.w3schools.com/css/")

Good luck!

---

### Post by anewguy on 2012-05-29
Well, I'm a LONG way from being able to generate the CSS for that yet.  It involves most of the sections in the css file, and so far I'm just doing some things for the panel section.  When the panel section is acceptable, I'll move on to the next section.

You know what's driving me crazy?  If you use gtk_color_selection_dialog_new you get the color wheel, yet when you use the recommended gtk_color_button you get that new stupid looking color selection.  If I could figure out how to get a button press to pop up the color selection dialog I'd use it - I just can't figure it out.  When I define it, the selection dialog is right on the screen, instead of a button press calling it up.

Let me know if you think it's worth continuing with what I'm doing.  It's a lot of work if it's not along the lines of what people are looking for.

Dave ;)

---

### Post by anewguy on 2012-05-29
> **Shadius said:**
> Maybe this link will be of use to you about understanding CSS. I'm not a programmer of anything of the sort, but I find your venture very interesting as I am interested about coding myself. :) 

[CSS]("http://www.w3schools.com/css/")

Good luck!

If you'd like a copy of the source code - so you can see just how bad I can bugger up C and GTK, let me know and I'll post it.

---

### Post by Shadius on 2012-05-29
> **anewguy said:**
> If you'd like a copy of the source code - so you can see just how bad I can bugger up C and GTK, let me know and I'll post it.

Definitely. :)

---

### Post by czgirb on 2012-05-29
> **guidol said:**
> 
... 
sudo gedit /usr/share/gnome-shell/theme/gnome-shell.css
In the text file, look for the "#Panel" setting (without quotes). Underneath should be a "font-size" setting, in my case the value was set to 10.5 - setting it to 9.5 worked fine for me ...[U]
[/U][]("http://ubuntuforums.org/showthread.php?t=1479239")

Open Terminal
Copy > Paste > gedit was opened, but nothing in it.
Have a clue?

---

### Post by anewguy on 2012-05-29
Here's a zip of the current state of the source code.  I've been adding things for the font selection, and it seems to randomly (at least to me) abort.  Sometimes you try to start the thing and it aborts.  Sometimes you can get it going and get into font selection and then it eventually aborts.  I'm not sure, but I think it has something to do with a dynamic string array I have in the code -> didn't even know how to do an array of strings, so I found some samples on the net I modified.

But......it will at least give you a glimpse of the source code.

Dave ;)

OOOOPPPSSS - forgot to attach the file - follow up post will do so!

---

### Post by anewguy on 2012-05-29
Jeez, maybe THIS time I'll remember to at least attach the file! ;)

---

### Post by anewguy on 2012-05-30
Uh, it may be a while.  I had some strange things happening, so I posted in the ubuntu programming forum.  After several pieces of conversation, I was politely asked today why I tackled such a project when I don't know the basics of what I'm doing.

I used to be a systems programmer.  I used to know C.  But apparently not doing anything with it since 1983 or so means I'm not just rusty, but have forgotten the basics.

So, basically, I need to do some serious reading for a while on the very basics again so I can try to make this work right.

Maybe you'd be better off finding someone who is current with everything and could probably whip this out in a heart beat.  

I feel extremely old today.

---

### Post by cbowman57 on 2012-05-30
Don't let it get to you.  I remember spending an entire weekend doing data entry on  a Timex Sinclair just to see a clock on my TV. :D

---

### Post by Shadius on 2012-05-30
> **anewguy said:**
> Uh, it may be a while.  I had some strange things happening, so I posted in the ubuntu programming forum.  After several pieces of conversation, I was politely asked today why I tackled such a project when I don't know the basics of what I'm doing.

I used to be a systems programmer.  I used to know C.  But apparently not doing anything with it since 1983 or so means I'm not just rusty, but have forgotten the basics.

So, basically, I need to do some serious reading for a while on the very basics again so I can try to make this work right.

Maybe you'd be better off finding someone who is current with everything and could probably whip this out in a heart beat.  

I feel extremely old today.

I wish I knew C! I would help! Alas, I am just starting out with programming languages. :( Don't let it get to you. I'm sure all you need is a refresher and you'll be good as new!

---

### Post by anewguy on 2012-05-30
> **cbowman57 said:**
> Don't let it get to you.  I remember spending an entire weekend doing data entry on  a Timex Sinclair just to see a clock on my TV. :D

Man does that bring back memories!  I remember building my own extra memory, a keyboard with buffering and a printer interface for mine way back then.  Hand assembled a word processor, created a bunch of "REM" statements so I had enough memory allocated to get started, then poke'd in about 5k worth of machine code.  Included calls for the save and read commands, so the first thing I did was save it!  It took several days to get that thing in.  Worked great - "normal" cursor, scrolling, word-wrap on/off, justification, filling each print line as needed with spaces to make it go from margin to margin (fixed font on the old dot-matrix [$500 then, only uni-directional, no descenders - jeez how things have changed!].  Fun days back then - went right along with what I was doing at work but that was all fun then.

Right now I wish I new how to generate a map for my executable so I could read a dang dump and figure out where everything is wrong.

Dave ;)

---

### Post by anewguy on 2012-05-30
> **czgirb said:**
> Open Terminal
Copy > Paste > gedit was opened, but nothing in it.
Have a clue?

Did you install the gnome-shell package in the package manager first?

Dave ;)

---

### Post by cbowman57 on 2012-05-31
Greets Dave!

I'm just trying my best to keep pace in this brave new world. :D

---

### Post by anewguy on 2012-05-31
Well, from the results of my pleas  for help on the programming forum:

[http://ubuntuforums.org/showthread.php?t=1992476]("http://ubuntuforums.org/showthread.php?t=1992476")

and 

[http://ubuntuforums.org/showthread.php?t=1989933&page=5]("http://ubuntuforums.org/showthread.php?t=1989933&page=5")

I'm s.o.l.  What I've got so far runs without aborting now, but honestly even though I've forgotten what I used to know I really did expect some guidance on debugging in Linux.  Without that, I give up.

I guess you're going to have to find someone else to do this for you.  Maybe the Gnome-shell guys since it is their product.

Sorry for being so stupid now.

---

### Post by cbowman57 on 2012-05-31
[IMG]http://fav.me/d51hs67[/IMG]Don't sweat the small stuff Dave, hope you enjoyed getting the oars back in the water even though you didn't get the results you were hoping for.

I'll just keep plugging away with the primitive tools at hand. :)


[ATTACH]219036[/ATTACH]

---

### Post by anewguy on 2012-06-01
Hey, here's something for everyone to ponder - it's a start - see the picture.  Using my program (I knew it wasn't causing the problems!) I generated a new css file, copied over to /usr/share/gnome-shell/theme/gnome-shell.css, logged off, selected "Gnome" for the manager, and logged back in.

Notice 2 things (I know, a lot of work just to get to here!):

- the panel font has changed to what I selected (though the weights of bold and italic didn't seem to do anything).  Note that I originally programmed in a font-color for the panel, but it turns out that either there just isn't one for the css file, or else I don't know how to specify it correctly.  For now just stuck as white.

- The panel background is the gradient I selected - it even has the transparency thing going on the ending color (there appears to be black under there if I set the transparency even higher)

So, this is going in the right direction.  Yep, a LOT of work ahead yet, but what I've been working on is working.  I hope that's a big step compared to having to use a manual editor.

Dave ;)

---

### Post by anewguy on 2012-06-01
Crap - I forgot to attach the picture again!  It should be on this post.

---

### Post by cbowman57 on 2012-06-01
Ok, the italics, bold, normal, etc.. should be ```
font-style:  bold;
```The font-family: can be placed up top making it universal  ```
stage {
    font-family: MintSpirit, "Droid Sans", cantarell, sans-serif;
}

```or in specific sections, #panel for instance, that's the section I do most of my customizing.  Then in this recent Cherry Bomb theme I split the #panelLeft, #panelCenter, #panelRight into their own sections so I could manage them individually.

Good progress Dave, don't let people tell you it can't be done. :)

Oh, & a lot of the coolest stuff I come up with is by accident. :D

---

### Post by anewguy on 2012-06-01
It's funny - this is what happens if you make the font too big!

---

### Post by cbowman57 on 2012-06-01
One nice thing about using em compared to px is that em will stretch proportionately, px is a fixed size.

Some may have other preferences but I prefer to use em.

---

### Post by Shadius on 2012-06-01
> **anewguy said:**
> It's funny - this is what happens if you make the font too big!

Whoa that's huge! :lolflag:

---

### Post by anewguy on 2012-06-01
I need to make a change such that the user can select em's or px's and then show the appropriate sizes to choose from.  I also found out that what I thought was black under the panel is actually the desktop background carried over - in my case that orange-brown.  I played with the colors a little and some combinations really make the gradient visible.  I've tried solid colors too - some good, some not so good, but that's the nature of the colors - nothing with my program.  I haven't tried the background image selection yet as I don't have an image for it and don't have a clue about creating one without a bunch of learning.

I should have the panel font selection modified for the em vs px thing by early next week.  Then for now the panel modification options should be done and I can move on to the next step - I'm just going to follow what's in the link in the original answer for the OP of this thread.  That way I know what these things do and can do them in an orderly fashion.  I see hope at getting at least part way to your image now.

Dave ;)

---

### Post by cbowman57 on 2012-06-01
There's a lot of experimentation with setting transparency & achieving the perfect gradient for a theme. I like to start with hex codes then move to rgba as I start refining an exact look.

---

### Post by anewguy on 2012-06-01
> **cbowman57 said:**
> There's a lot of experimentation with setting transparency & achieving the perfect gradient for a theme. I like to start with hex codes then move to rgba as I start refining an exact look.

While you can actually see the transparency and gradient when you select in the program (hummm, I don't know if I can do that with a GTK label or not - it would need to be a Pango font string....might have to look), although the color selection does at least show the transparency by how much you can see the checkered background.  BTW - for anyone who might want to know, the GTK color selector was changed in the new release, so you first get a block with several colors on it - if you click "advanced" you'll get a slider and a box to adjust the color and you can set the transparency.

It is a challenge knowing what it's going to look like.  I suppose since your css file also has other mods in it that I haven't implemented yet, you could still use the program to select the colors and transparency and then just use the editor to pull those css statements out of the test.css the program generates and paste them into yours - it would at least save doing the hex codes.

Going to take a day or two away and then get back working on this.  The last week has been aggravating so I just want to get away for a day or two.

Dave ;)

---

### Post by cbowman57 on 2012-06-01
Yeah, I just eyeball it until it's what I want.  The hex codes are a starting point (for my process) but others probably do it differently.  I get the hex for the approximate colors than edit the .css using the rgb data in gcolors2 to create the right balance, sometimes that means changing the shade. 

But yeah, what you have now might help the process, especially for some people that have never done it any other way.  I support your project for the masses, I might not be able to adapt & what I do works for me. ;)

Take a break, enjoy life.

---

### Post by anewguy on 2012-06-02
Sounds good to me.  Your theme you developed that you posted the picture and link to is what gave me a little more gas to try.  I don't know if it will ever get there, but I hope to someday have the program be able to set up as much of that as possible, and by updating the existing file and restarting the manager so the changes show.  That's along way down the road but your theme is a great example to strive towards!  You did a great job on it!

Dave ;)

---

### Post by cbowman57 on 2012-06-02
Thank you Dave, red's not for everybody but it does seem to have attracted some interest.

I think you're on the right track though, something that the average user can use to personalize his/her desktop.  A little more like some apps we had for gnome2.  That gnome-color-chooser is actually a pretty potent piece of software.

The way I go about it is a rather tedious process, I don't even know if I do it right, I just do it. :)

---

### Post by anewguy on 2012-06-02
Sounds like me when I look at the CSS.  I may be basically starting over with C, but I just don't follow the CSS at all yet.  I'm starting to see what a piece at a time does, but man, there's a lot in there!


EDIT:  I was looking on the net for some attributes in CSS, and I found [this]("http://www.w3.org/MarkUp/Guide/Style") website that has the "safe" colors in a chart with their hex values - maybe it can help you?


Dave ;)

---

### Post by cbowman57 on 2012-06-02
Yeah, I use some of those online charts too, they are helpful.  I usually start by finding a wallpaper I like, or modifying one, then the theme sort of fills in around it. Goofy, I know. :D

I know ZIP about programming so I can't even comment, other than to say, isn't there some crossover between .css & html? So maybe being forced to get comfortable with .css will carry over to other things you like to work on.  Who knows, just killing time. :)

---

### Post by anewguy on 2012-06-02
Very definitely!  CSS (cascading style sheets) are (or at least were when I first heard of them many years ago!) the big thing - they "describe" things much better and usually easier than it is to do them in traditional HTML - at least that's what I heard way back when!  I haven't messed with HTML in a lot of years either, and I've heard something about HTML5 or some such thing - I've got no clue now!  ;)  I just never took the time back then to learn CSS as I wasn't building that many websites to make it worth while for me.  I probably should have!

Have a great weekend!

Dave ;)

---

### Post by cbowman57 on 2012-06-02
You too Dave.

---

### Post by coldjeanz on 2012-06-02
I have this same problem but I don't want to read through 14 pages. Is there a fix to this?

---

### Post by cbowman57 on 2012-06-02
> **coldjeanz said:**
> I have this same problem but I don't want to read through 14 pages. Is there a fix to this?

Yes.

One word answers aren't all that helpful.  I meant to say, yes, there is. :)

---

### Post by anewguy on 2012-06-02
> **cbowman57 said:**
> Yes.

One word answers aren't all that helpful.  I meant to say, yes, there is. :)

I like it!

To the poster - you are probably going to have to read the thread to understand what people have been doing - including the link posted in the second post of the thread (I think that's where it's at - it's at the beginning).  I'm trying to come up with a programmatic way of doing this but it's not really ready for anyone to use except in just testing.  See the screen shots attached in my post a few back.

Once you've gone through that (and really, there's just no way around it), and you still have questions, then post back.

Dave ;)

---

### Post by cbowman57 on 2012-06-02
Wow!  I found it on the first page.

[http://ubuntuforums.org/showpost.php?p=11649498&postcount=8](http://ubuntuforums.org/showpost.php?p=11649498&postcount=8)

Imagine my surprise.
(I've been using Arch too long :D )

---

### Post by anewguy on 2012-06-02
Been a lot of stuff out there but so far now editor - seems weird.

I think the link that post points to is in about the 2nd post of this thread.  I've been following it to think about setting up the notebook pages my program will present for options.  But you know what?  I missed something until now:  I need to put color: <some color def> in the panel to get the font color!  Also, I've been thinking - I guess it makes sense that I haven't been able to get the font "bold" to work (still don't understand why italics won't) - it dawned on me that when you move the mouse of the text, etc., in the panel it makes it bold.  So if I was allowed to make it bold to being with I don't know what I would do.  For now I'm going to change the way I output the font color in the css file and see what happens.

---

### Post by cbowman57 on 2012-06-02
I had this thought recently Dave.  Is there a way to @define_colors in .css?  It's done it gtk-3.0, but I've been unable to crack the code.

To me the ultimate tool would allow a person to define maybe 6-12 colors ad the theme would just draw from that.

I meant to raise this question/idea a couple weeks ago but it slipped my mind.  Your comment reminded me of it.

I also seem to remember reading somewhere that python(?) can be tricked into running as .css, or vice versa.  The information was over my head.

The more I think about it though all we've really been doing is tweaking Adwaita. Maybe that is the only way but perhaps it's possible to think outside the box.  I have no clue if what I'm talking about is even possible but since I have your ear I thought run it past you.

---

### Post by anewguy on 2012-06-02
I don't know - I don't know anything about CSS and wasn't aware of the @define_colors either - do you know where you use this in GTK3?  All the screen stuff in my program is all GTK3.

It really might be worth while to present a single notebook page with several different color options on it, but right now I don't even know enough to figure what the sections mean in the gnome-shell.css file, so I don't have any ideas what to actually put on that screen.  If you have some suggestions, and could point me to where they are at in the gnome-shell.css file, I can sure try to do that next.  It might be the best option to put out there first.

It's a good idea, so if you can give me a few pointers from the stuff you've done I can try to figure it out.

Also, I've never heard of or used Adwaita.  Does it do a gui'd interface to the gnome-shell.css file?

Dave ;)

---

### Post by cbowman57 on 2012-06-03
> **anewguy said:**
> I don't know - I don't know anything about CSS and wasn't aware of the @define_colors either - do you know where you use this in GTK3?  All the screen stuff in my program is all GTK3.

In the gtk.css & gtk-widgets.css it uses that method to define colors in the gtk theme.  If we could find a method your app could look at specific locations instead of trying to parse an entire file. Just a thought, don't know the full capabilities.  I'm trying to absorb some css references now but am not certain how much capability is built into the shell.  I have more questions than answers i'm afraid. :)

> It really might be worth while to present a single notebook page with several different color options on it, but right now I don't even know enough to figure what the sections mean in the gnome-shell.css file, so I don't have any ideas what to actually put on that screen.  If you have some suggestions, and could point me to where they are at in the gnome-shell.css file, I can sure try to do that next.  It might be the best option to put out there first.

It's a good idea, so if you can give me a few pointers from the stuff you've done I can try to figure it out.

Also, I've never heard of or used Adwaita.  Does it do a gui'd interface to the gnome-shell.css file?

Dave ;)

Adwaita is the default gnome shell theme.  My curiosity is based on the possibility that Adwaita didn't use the entire css toolbox & there is a lot more to be done with them.

I think a good theme for you to examine is Nord [http://fav.me/d3jl36q](http://fav.me/d3jl36q) he used a modular method that I have yet to adopt but it looks to me like it breaks it down into easy to understand components. panel.css file, overview.css, etc.  It's one of the early themes but his approach intrigues me.

---

### Post by cbowman57 on 2012-06-03
Hey Dave, I know I've drifted outside the scope of your project but these are just some crazy ideas I've been thinking about lately.

Look at this css reference, don't know if they all would work in a theme but it would be cool if they did.  [https://developer.mozilla.org/en/CSS/CSS_Reference](https://developer.mozilla.org/en/CSS/CSS_Reference)

---

### Post by anewguy on 2012-06-03
I looked at and bookmarked that page - it should come in very handy, especially when I want to know what the heck something is.

And, to show how little I know, if the gnome-shell.css file is actually a theme, then what I'm trying to do is a theme editor, and surely there must be a bunch of those around!

Still plugging away!

---

### Post by cbowman57 on 2012-06-03
Take a look at this Dave [http://fav.me/d525x6c](http://fav.me/d525x6c).

I was unable to get it to behave the way I think it's described but he themes on Ubuntu.  Quite possible it provides a dependency that Arch doesn't.  What he's done is basically, from what I can figure out, is set real high transparency values then has a daemon-like something running in the background to inherit colors from the elegance-colors.conf file.

Thought you might find it interesting.

---

### Post by anewguy on 2012-06-03
Yeah, they created and use a daemon - hence the background process.  Without the separate process, nothing would know the theme changed and to adjust the colors.

I think I'll just keep plugging away.  It might not be useful when it's done, but I thought just allowing mods to the gnome-shell.css file via the gui would help some who may not be fluent in things like creating themes - like me ;) - but who just want to change the default look to some of gnome shell.

My programming skills and lack of knowing any of this would make it difficult to do more - heck, it's difficult just doing what I'm doing! ;)

Maybe someone else reading this thread with more experience in all of this can make a contribution to ubuntu? ;)

Dave ;)

---

### Post by cbowman57 on 2012-06-03
If he can pass that via daemon to the shell theme after reading it from a .conf file or the gtk theme, it should be possible to do something similar to @define_color, like the gtk3 .css. which to me is actually more practical.  I'd think different if his had a settings panel where you could actually change colors, including luminousity, on the fly that would really be impressive.

Whatever you feel like doing, or not is fine.  I enjoy the learning process.   This thread has actually been real interesting to me. :)

---

### Post by anewguy on 2012-06-03
I do want to make setting changes dynamic if I can.  Right now I do't know how to.  So, I thought I'd keep plugging away on other parts and leave that for last as that won't be too east for me at all.

I also put a post in the ABT forum for someone who knows their programming and maybe CSS to come in and do this project.  That way they could ask the right questions, find out how best to make options what people want, etc., and implement them.  I don't know a thing about any of this so I was just working off of trial and error changing parts of gnome-shell.css to see how the appearance of things changes and if I could build a GUI for those options.  Years ago this would have been my thing - I think I'm "too old for this ...insert word of choice here,,,," as they say.

I'll keep plugging away on my project and see what happens if someone else can jump in here.  When it comes to themes, customizing the desktop, etc., I just plain don't know anything - so I can visually see in the posts what people are thinking of, but I don't know how to actually do it.

I'm enjoying this thread as well - it's throwing out a lot of ideas for people to think about and maybe integrate into a future version of gnome-shell itself!

EDIT:  I just searched for gtk3.css - I don't have it.  I am running gnome-shell and obviously have GTK 3 (the packages, not a theme) installed.  Was it supposed to be part of the gnome-shell package?

Have a good one!

Dave ;)

---

### Post by cbowman57 on 2012-06-03
Depending on how you've installed your custom themes they could either be in ~/.themes/<theme name>/gtk-3.0 if you installed for local user.  /usr/share/themes/<etc> for global.

Yeah, if you can recruit some more talent that would be great. I'm surprised that we haven't had any young, enthusiastic programmers new to Ubuntu jump on this.  Maybe a new thread looking for recruits reflecting this shift in direction?

> **anewguy said:**
> I do want to make setting changes dynamic if I can.  Right now I do't know how to.  So, I thought I'd keep plugging away on other parts and leave that for last as that won't be too east for me at all.

I also put a post in the ABT forum for someone who knows their programming and maybe CSS to come in and do this project.  That way they could ask the right questions, find out how best to make options what people want, etc., and implement them.  I don't know a thing about any of this so I was just working off of trial and error changing parts of gnome-shell.css to see how the appearance of things changes and if I could build a GUI for those options.  Years ago this would have been my thing - I think I'm "too old for this ...insert word of choice here,,,," as they say.

I'll keep plugging away on my project and see what happens if someone else can jump in here.  When it comes to themes, customizing the desktop, etc., I just plain don't know anything - so I can visually see in the posts what people are thinking of, but I don't know how to actually do it.

I'm enjoying this thread as well - it's throwing out a lot of ideas for people to think about and maybe integrate into a future version of gnome-shell itself!

EDIT:  I just searched for gtk3.css - I don't have it.  I am running gnome-shell and obviously have GTK 3 (the packages, not a theme) installed.  Was it supposed to be part of the gnome-shell package?

Have a good one!

Dave ;)

---

### Post by anewguy on 2012-06-03
Actually, and this is going to sound pretty dumb on my part, but I've never installed a theme!  That explains why when I let nautilus search my whole file system it never found the file! ;)

Yeah, I sure hope some "youngester" (at least compared to me!) comes on board to see what kind of fancy stuff they can do.

I suppose that after I get the other things working I could try to add a notebook page for the gtk3.css file.  As stupid as I am, how do I (1) download a them for gnome-shell and (2) install the thing?  I really need to do that to see how much the gnome-shell.css file and the defined theme override or replace each other.  Like everything else, right now I don't know a thing about it!  I must seem pretty dang dumb to people!

If you could tell me how to do that, then perhaps I can see about adding something in over time.  You know - the first parts on modifying colors, fonts, etc., on the panel, drop-downs, pull-downs, menus, calendar, etc., and then more for modifying gtk3.css.  The only thing I'm afraid of is that people are going to want a generic gui'd css editor, and that's way beyond what I can actually do.  Again, I just don't know any of that stuff.

Keep her going here - we'll see what I can do, and hopefully somebody else will jump in.  I'm not asking anyone to take over my code - that would be a waste of time for them.  I really (at least currently) don't really need this for myself (I'm extremely simple), so hopefully some young gun can come in a do it.  Heck, if their young enough they could even be looking at some possible extra-credit at their school when they get done by showing them the project they did! (I suppose that was rather a shameless ploy ;) ).

At any rate, let's just see how things progress both with what I'm currently doing and with what other things you and others would like to have in it as well.  We'll hope somebody comes around!

Have a good one!

Dave ;)

---

### Post by traditionalist on 2012-06-03
Can't remember if I  already posted this here or not, but this tool does everything for you, you  just have to choose what you want;

[http://ubuntuforums.org/showthread.php?t=1988119](http://ubuntuforums.org/showthread.php?t=1988119)

---

### Post by cbowman57 on 2012-06-03
Just make sure you have gnome-tweak-tool installed.  Create ~/.themes if it doesn't exist. Download a theme, put it in the ~/.themes directory & extract it.  Open gnome-tweak-tool, open the Themes panel and use the comboboxes to select your GTK, Window &/or shell themes.  You can mix & match easily.

I agree though, you need to just explore it & get a feel for the layout.  There are times I'll stare at it & be totally baffled.  Take a break, come back & wonder why I was so stupid. LOL

---

### Post by cbowman57 on 2012-06-03
> **traditionalist said:**
> Can't remember if I  already posted this here or not, but this tool does everything for you, you  just have to choose what you want;

[http://ubuntuforums.org/showthread.php?t=1988119](http://ubuntuforums.org/showthread.php?t=1988119)

Interesting, it looks like gnome-color-chooser quite a bit. But it does gtk3 too?    Does it do shell themes?  I couldn't make it out looking at the images.

---

### Post by anewguy on 2012-06-03
Yeah, I'd be interested in seeing it in a size I can actually see stuff in, and more details on what's going on.

Does this allow changes not only to colors, but to fonts, fonts sizes, background window colors, etc., as specified in the gnome-shell.css file?

If so, there's no need for me to do anything - we'll just ask you to post detail about the tool, where to get it and how to use it.

Thanks!
Dave ;)

---

### Post by traditionalist on 2012-06-03
As far as I can tell it does more or less everything one wants. You have to play with it for a while and it takes some time to set up a proper theme, ( as opposed to just changing random fonts or colours).

I have set up my whole system, including Firefox, Thunderbird, and all the system programs that will use a default theme.

Here are some better pictures for you; ( in this case, as an exception,  full sized images,)

[[IMG]http://img51.imageshack.us/img51/4008/gnomecolorchooser001.png[/IMG]]("http://img51.imageshack.us/i/gnomecolorchooser001.png/")


[[IMG]http://img36.imageshack.us/img36/4008/gnomecolorchooser001.png[/IMG]]("http://img36.imageshack.us/i/gnomecolorchooser001.png/")

I just chose a couple of the possible choices.  "Global Colors" and "Panel". When you are finished setting up ( changes are more or less immediate on system windows, you have to restart stuff like Firefox for the theme to take effect).  You can save the result as a theme.  I have attached the theme I set up with this, and am presently using.
It is very comprehensive. The themes are saved as *.gnomecc  in xml format.

Looks like this, and is very handy for finding codes etc;

```
style "gnome-color-chooser-compact"
{
  GtkContainer::border_width=0
  GtkButton::default_border    = { 0, 0, 0, 0 }
  GtkButton::interior-focus = 0
  GtkButton::focus-padding = 0
  GtkButton::focus-line-width = 0
  GtkButton::focus-line-height = 0
  GtkButton::inner-border      = {2, 1, 1, 2}
  
#  GtkRange       ::trough_border     = 0
#  GtkPaned       ::handle_size       = 3
#  GtkRange       ::slider_width      = 12
#  GtkRange       ::stepper_size      = 12
#  GtkOptionMenu::indicator_spacing = { 0, 0, 0, 0 }
#  GtkOptionMenu::indicator_size = { 16, 18 }
  
#  GtkEntry     ::inner-border         = { 0, 0, 0, 0 }

#  GtkNotebook::tab-border = 0
#  GtkNotebook::tab-hborder = 0
#  GtkNotebook::tab-vborder = 0
#  GtkNotebook::show-border = 0
#  GtkNotebook::gtk-button-images = 0
#  GtkNotebook::gtk-menu-images = 0
#  GtkNotebook::arrow-spacing = 0
#  GtkNotebook::tab-curvature = 0
#  GtkNotebook::tab-overlap = 0
#  GtkNotebook::focus-line-width = 0
  
  
#  GtkScrollbar   ::min_slider_length = 30
#  GtkScale       ::slider-length     = 27
#  GtkCheckButton ::indicator_size    = 12   # for tinyphil people
# GtkMenuBar     ::internal-padding  = 0
#  GtkExpander    ::expander_size     = 12
#  GtkComboBox    ::appears-as-list = 1      # as gnomecc option!
  GtkComboBox    ::arrow-size = 4
    
  GtkButton      ::child-displacement-x = 0
  GtkButton      ::child-displacement-y = 0
  GtkButtonBox   ::child-min-height=18
  GtkButtonBox   ::child-min-width=18
  GtkButtonBox   ::child-internal-pad-x=1
  GtkButtonBox   ::child-internal-pad-y=1

#  WnckTasklist   ::fade-overlay-rect = 0

  GtkTreeView::expander-size = 9
#  GtkTreeView::expander-indent = 0
  GtkTreeView::focus-line-width = 0
#  GtkTreeView::spacing = 0
  GtkTreeView::horizontal-separator = 0
  GtkTreeView::vertical-separator = 0
#  GtkTreeView::row-ending-details = 0
#  GtkTreeView::treeview-left=1
#  GtkTreeView::treeview-right=0
#  GtkTreeView::treeview-middle=0
#  GtkTreeView::passive_focus = 0
#  GtkTreeView::separator-height = 0
#  GtkTreeView::tree-line-pattern = "\000\000"
#  GtkTreeView::grid-line-pattern = "\000\000"
#  GtkTreeView::grid-line-width = 0
#  GtkTreeView::tree-line-width = 0


  
#  GtkCheckButton::indicator-spacing=0
#  GtkCheckButton::indicator-size=13
#  GtkCheckMenuItem::indicator-size=13
    
  xthickness = 1
  ythickness = 1
}
class "GtkWidget" style "gnome-color-chooser-compact"

style "gnome-color-chooser-compact-tooltips"
{
  xthickness = 4
  ythickness = 4
}
widget "gtk-tooltip*" style "gnome-color-chooser-compact-tooltips"
  
```

---

### Post by traditionalist on 2012-06-04
The tool is here;

[[IMG]http://img252.imageshack.us/img252/5117/ubuntusoftwarecenter001.th.png[/IMG]](http://img252.imageshack.us/i/ubuntusoftwarecenter001.png/)

There are also various engines for gtk+ 2.x ( gtk2-engines) available as add-ons. But I have not used them yet, just the basic tool.

I am running GNOME Classic;

[[IMG]http://img137.imageshack.us/img137/5255/selection001sn.th.png[/IMG]](http://img137.imageshack.us/i/selection001sn.png/)

No idea why the system says "Unknown".  For other details see my signature.  If you need any more info then just ask.

---

### Post by traditionalist on 2012-06-04
This tool, ( Ubuntu Tweak)  gives the setup correctly;

[[IMG]http://img138.imageshack.us/img138/2510/selection001u.th.png[/IMG]](http://img138.imageshack.us/i/selection001u.png/)

---

### Post by traditionalist on 2012-06-04
The installed gtk stuff is;

[[IMG]http://img62.imageshack.us/img62/7234/selection001fx.th.png[/IMG]](http://img62.imageshack.us/i/selection001fx.png/)

---

### Post by traditionalist on 2012-06-04
Clicking on any of the boxes in the tool gives you a colour chooser flyout;

[[IMG]http://img151.imageshack.us/img151/1087/pickacolor001.th.png[/IMG]]("http://img151.imageshack.us/i/pickacolor001.png/")

If you play about with this and similar stuff you need to use GConf-cleaner now and again and then restart. This removes any errors and prevents odd effects occurring;

[[IMG]http://img525.imageshack.us/img525/4465/gconfcleaner1of5001.th.png[/IMG]]("http://img525.imageshack.us/i/gconfcleaner1of5001.png/")
[[IMG]http://img525.imageshack.us/img525/73/gconfcleaner3of5001.th.png[/IMG]]("http://img525.imageshack.us/i/gconfcleaner3of5001.png/")
[[IMG]http://img151.imageshack.us/img151/8306/gconfcleaner5of5001.th.png[/IMG]]("http://img151.imageshack.us/i/gconfcleaner5of5001.png/")

Get the tool here;

[https://code.google.com/p/gconf-cleaner/](https://code.google.com/p/gconf-cleaner/)

or here;

[[IMG]http://img266.imageshack.us/img266/6553/ubuntusoftwarecenter001s.th.png[/IMG]](http://img266.imageshack.us/i/ubuntusoftwarecenter001s.png/)

I think that was about it?

---

### Post by anewguy on 2012-06-04
Looks like it does everything everyone has wanted!  So, I can dump my project.  Thanks for bringing this up for everyone!!

Dave ;)

---

### Post by traditionalist on 2012-06-04
> **anewguy said:**
> Looks like it does everything everyone has wanted!  So, I can dump my project.  Thanks for bringing this up for everyone!!

Dave ;)

Entirely my pleasure, always good to help if possible.  This only came about because my flaky graphics were causing me a great deal of trouble, and I had a lot of trouble even installing Ubuntu on my main machine.  So I went looking for stuff. 

Having decided on GNOME Classic ( it was the only one that ran stably! I tried quite a few.), and being unable to find a theme that suited me, ( I work a lot at night, and themes with bright white and similar stuff in them just make my eyes water and the dark ones I tried didn't suit either), I went looking for ways to set that up too. I found all this lovely stuff!

This is now my fourth week of using Ubuntu Linux  ( I have never used Linux before and of course lots of things are new to me), and I am extremely pleased with it. I have never had a system that was so customisable. It is also very very powerful. Some really fantastic software.  I still have a very great deal to learn of course, but there is no way you could prise this system away from me now. I now have it running on all my machines, and I have a few Windows setups running in VM's, but they will gradually be phased out I think. If you had told me four weeks ago that I would not be running Windows 7 as a main system in a month's time, I would simply have laughed.

Anyway, I do hope people enjoy it and find it useful.

---

### Post by traditionalist on 2012-06-04
As a couple of people asked, here are a few windows on my desktop using that theme;

[[IMG]http://img822.imageshack.us/img822/6480/workspace1001je.th.png[/IMG]]("http://img822.imageshack.us/i/workspace1001je.png/")

The dock is the avant-window-navigator  and the panel on the second monitor is the usual GNOME panel mainly being used as an open window indicator, to mount various media as required and it also has a search utility and a terminal so that I can get to them immediately without going anywhere else.

---

### Post by vasa1 on 2012-06-04
> **traditionalist said:**
> ... ( I work a lot at night, and themes with bright white and similar stuff in them just make my eyes water and the dark ones I tried didn't suit either), ...
If you could come up with a way to un-white the Ubuntu Software Center that would be fantastic. Someone had posted a tweak but it looks like it has to be redone with each revision.

---

### Post by traditionalist on 2012-06-04
> **vasa1 said:**
> If you could come up with a way to un-white the Ubuntu Software Center that would be fantastic. Someone had posted a tweak but it looks like it has to be redone with each revision.

Would this suit you? 

[[IMG]http://img23.imageshack.us/img23/5117/ubuntusoftwarecenter001.th.png[/IMG]]("http://img23.imageshack.us/i/ubuntusoftwarecenter001.png/")

[[IMG]http://img829.imageshack.us/img829/5117/ubuntusoftwarecenter001.th.png[/IMG]]("http://img829.imageshack.us/i/ubuntusoftwarecenter001.png/")

that's in the theme I posted.  It wont change even if you reinstall the software center. I have not yet managed to change all the white pages, but I will get that fixed as well. Brilliant white stuff just kills my eyes at night.

Nautilus is a problem as well, every update ruins my patches and colours! That is the only program where the background panel will not accept the default theme. But it 's not really too bad, at least not as bad as some windows were. 

[[IMG]http://img99.imageshack.us/img99/7451/sda1data001.th.png[/IMG]]("http://img99.imageshack.us/i/sda1data001.png/")

 I also use the theme colours for webpages so they don't blind me, you need to set Firefox to use the system colours for that;

[[IMG]http://img803.imageshack.us/img803/1936/selection001r.th.png[/IMG]]("http://img803.imageshack.us/i/selection001r.png/")


This is the forum using that setting and the theme colours;

[[IMG]http://img855.imageshack.us/img855/3092/ubuntuforumsmozillafire.th.png[/IMG]]("http://img855.imageshack.us/i/ubuntuforumsmozillafire.png/")

this also highlights visited links etc.


As somebody else asked, yes, scroll bars etc are also completely customisable;

[http://img195.imageshack.us/i/gnomecolorchooser001.png/](http://img195.imageshack.us/i/gnomecolorchooser001.png/)

---

### Post by traditionalist on 2012-06-04
Sorry, I don't know if it works on any other systems. I only use GNOME Classic, ( see my signature).  With regard to various "Eye candy", I am not a fan of it.  This is what my desktop looks like when I log in;

[[IMG]http://img543.imageshack.us/img543/8437/workspace1001s.th.png[/IMG]](http://img543.imageshack.us/i/workspace1001s.png/)

I don't like things that flash or blink or blind me with bright colours. Doubtless it is possible to make a "neon" theme, but I would not use it.  My personal messages and all that sort of stuff are disabled. If you know who I am then you can e-mail me, but I am on the forum to discuss this stuff and don't want to do it privately.

---

### Post by cbowman57 on 2012-06-04
> **anewguy said:**
> Looks like it does everything everyone has wanted!  So, I can dump my project.  Thanks for bringing this up for everyone!!

Dave ;)

No it doesn't.  That's gnome-color-chooser, & he's not using gnome-shell.  All that's doing is writing custom gtkrc file, which is gtk-2.0.  This does nothing to the panel on Gnome shell, it doesn't affect gtk-3.0.   As a tool it still has some usefulness left but it won't customize your gnome shell setup.

---

### Post by nicolasforum89 on 2012-06-04
Thank you for the screenshots! Pretty usefull

---

### Post by Shadius on 2012-06-04
> **traditionalist said:**
> Sorry, I don't know if it works on any other systems. I only use GNOME Classic, ( see my signature).  With regard to various "Eye candy", I am not a fan of it.  This is what my desktop looks like when I log in;

[[IMG]http://img543.imageshack.us/img543/8437/workspace1001s.th.png[/IMG]](http://img543.imageshack.us/i/workspace1001s.png/)

I don't like things that flash or blink or blind me with bright colours. Doubtless it is possible to make a "neon" theme, but I would not use it.  My personal messages and all that sort of stuff are disabled. If you know who I am then you can e-mail me, but I am on the forum to discuss this stuff and don't want to do it privately.

This works for GNOME Classic? I'm running GNOME Classic as well and I've tried to use this, but nothing is changing. I've tried changing the color of the scrollbar and it didn't work. Maybe I'm doing something wrong?

---

### Post by cbowman57 on 2012-06-04
Ubuntu with Gnome **Shell**: How do I change the font size in top panel

I appreciate the enthusiasm guys but if you're not going to read the thread before "helping", at least read the title. :)

---

### Post by cbowman57 on 2012-06-04
> **Shadius said:**
> This works for GNOME Classic? I'm running GNOME Classic as well and I've tried to use this, but nothing is changing. I've tried changing the color of the scrollbar and it didn't work. Maybe I'm doing something wrong?

There are only a few legacy apps that use gtk-2.0 on 12.04. 

If you guys are trying to customize gnome-fallback that would be a different thread.

---

### Post by traditionalist on 2012-06-04
> **cbowman57 said:**
> No it doesn't.  That's gnome-color-chooser, & he's not using gnome-shell.  All that's doing is writing custom gtkrc file, which is gtk-2.0.  This does nothing to the panel on Gnome shell, it doesn't affect gtk-3.0.   As a tool it still has some usefulness left but it won't customize your gnome shell setup.

Well. that seems to be fair comment. I really don't know anything about all these various gtk matters.  I just went ahead and used what I found to customise my own system and a couple of others.  It works fine and I am happy with it but it may not even work at all on many systems. I don't know.  I am reading as much as I can about all this. I will keep at it. It suits me for the nonce. Maybe I will set about actually customising the Gnome shell.  have to wait and see how things go. I have not bothered much with the actual panel, as I have an excellent dock. I just use the panel for a couple of things on my second monitor.

---

### Post by traditionalist on 2012-06-04
> **cbowman57 said:**
> There are only a few legacy apps that use gtk-2.0 on 12.04. 

If you guys are trying to customize gnome-fallback that would be a different thread.


I have not found an application it doesn't work on, and I have a fair number of applications on here now. I am obviously not entirely sure how you define "customisation" and of what.  I read the thread a few times but am not a lot wiser. Once I have read a lot more about the various gtk matters I will be better placed to judge what to do.

---

### Post by vasa1 on 2012-06-04
> **cbowman57 said:**
> Ubuntu with Gnome **Shell**: How do I change the font size in top panel

I appreciate the enthusiasm guys but if you're not going to read the thread before "helping", at least read the title. :)

You're absolutely correct. I'm sorry for asking about tweaking the USC in this thread. **No deliberate offence intended**! Just another goof-up by me.

---

### Post by cbowman57 on 2012-06-04
> **vasa1 said:**
> You're absolutely correct. I'm sorry for asking about tweaking the USC in this thread. **No deliberate offence intended**! Just another goof-up by me.

:D  It happens, I do it.  I used to do it a lot. :)

Dave & I did veer from the stated topic, but it was directly related.  My comments in reference to the Gtk were just some random thoughts about how it is similar to what we're trying to do to the gnome-shell.css & if it would be possible to apply similar syntax, just a little brainstorming.

Somebody new to Linux coming to this thread would be totally confused, which I think is what happened here recently. :)

---

### Post by Shadius on 2012-06-04
> **cbowman57 said:**
> Ubuntu with Gnome **Shell**: How do I change the font size in top panel

I appreciate the enthusiasm guys but if you're not going to read the thread before "helping", at least read the title. :)

> **cbowman57 said:**
> There are only a few legacy apps that use gtk-2.0 on 12.04. 

If you guys are trying to customize gnome-fallback that would be a different thread.

Got a bit confused for a second. My apologies.

---

### Post by cbowman57 on 2012-06-04
Between Gnome & Canonical it's easy enough to get that way these days.

Old & new thrown together and I don't think they differentiated things very well.

---

### Post by Shadius on 2012-06-04
> **cbowman57 said:**
> Between Gnome & Canonical it's easy enough to get that way these days.

Old & new thrown together and I don't think they differentiated things very well.

I'm constantly getting confused between GNOME & Canonical especially since I'm fairly new to the Ubuntu Linux. :( I've just started learning how to install themes and icons also. This thread has helped me learned a few things. :) As I'm a picky user, I like pretty much everything to be customizable! :popcorn:

---

### Post by cbowman57 on 2012-06-04
> **Shadius said:**
> I'm constantly getting confused between GNOME & Canonical especially since I'm fairly new to the Ubuntu Linux. :( I've just started learning how to install themes and icons also. This thread has helped me learned a few things. :) As I'm a picky user, I like pretty much everything to be customizable! :popcorn:

Well it's easy to get confused, 18 months ago the "ubuntu-desktop" was gnome2.  Then Unity got thrown in the mix & it became ubuntu-desktop.  To add to the confusion the first Ubuntu had Unity, which was now ubuntu-desktop.  A hybrid version of gnome2 came along with it, I think they called that Gnome Classic.  Then the next version Gnome Classic was gone.

So when you get us old Ubuntu users thinking sometimes in older terminolgy vs. somebody brand new to Ubuntu, or linux talking in the current tongue it sometimes makes it hard. 

I used to try & support the Ubuntu community quite a bit but they've made it difficult.  I've aged into Archlinux now, nice & sedate. :)

But I did my own Gnome shell respins last year, built on Ubuntu, so my focus became the desktop itself, not what distro it runs on top of.  I can still talk Gnome shell & pure linux stuff but Ubuntu & I went different directions.

I will say this though, I've been using computers since 1982 & within 48 hours of using Gnome shell I knew I'd finally found a home.  It's the most comfortable& customizable desktop I've ever used.  Anything else feels like torture. :D

---

### Post by traditionalist on 2012-06-04
Well, I still haven't figured out what is meant by a lot of stuff here, but I tried what I have described in "GNOME", GNOME Classic" and "GNOME Classic ( No Effects).

It worked in all of them. I do have the "Gnome Shell"installed; 

[[IMG]http://img689.imageshack.us/img689/8964/selection001t.th.png[/IMG]](http://img689.imageshack.us/i/selection001t.png/)

---

### Post by anewguy on 2012-06-04
> **cbowman57 said:**
> No it doesn't.  That's gnome-color-chooser, & he's not using gnome-shell.  All that's doing is writing custom gtkrc file, which is gtk-2.0.  This does nothing to the panel on Gnome shell, it doesn't affect gtk-3.0.   As a tool it still has some usefulness left but it won't customize your gnome shell setup.

There I go again - not knowing ;)  I'll get back to work on that then!

I had even closed the thread looking for help since I thought this was working.  I'll go re-open it and remove my text.

I think I can get this, I'm just slow!  I remember back in the 70's and 80's when I was a younger man doing support on what are big boat anchors now - coming home and building a CP/M machine by buying a bare board and soldering everything in your self, making your own cables, even building a hard disk interface from scratch and writing the driver for it - all of those things were fun back then.  This would be extremely fun for me if I still remembered what the heck I was doing!  ;)

Thanks for clarifying that, and I'll get back on the project.  After adding the font size "type" - which I'm going to allow ems and px (unless there are others I need to be aware of), I think the panel portion would be done.  Then I can move on to the next section.  I'm sure I'll be asking more questions since I don't have a clue what the sections do at this time.

Have a good one my friend!

Dave ;)

---

### Post by Shadius on 2012-06-04
> **traditionalist said:**
> Well, I still haven't figured out what is meant by a lot of stuff here, but I tried what I have described in "GNOME", GNOME Classic" and "GNOME Classic ( No Effects).

It worked in all of them. I do have the "Gnome Shell"installed; 

[[IMG]http://img689.imageshack.us/img689/8964/selection001t.th.png[/IMG]](http://img689.imageshack.us/i/selection001t.png/)

Wait, the GNOME Color Chooser **does** work for GNOME Classic (No effects)?

---

### Post by traditionalist on 2012-06-04
Indeed it does, it works on all the GNOME flavours, I have tried all those I have.

It works on Cinnamon as well. The theme I made using it is applied immediately and with no problems at all.  It looks very similar to GNOME classic but I think it is a tad faster.  It also shows the graphics setup it is using, ( most don't ) ;

[[IMG]http://img834.imageshack.us/img834/1758/details001.th.png[/IMG]]("http://img834.imageshack.us/i/details001.png/")

[[IMG]http://img26.imageshack.us/img26/7060/selection001l.th.png[/IMG]]("http://img26.imageshack.us/i/selection001l.png/")

---

### Post by cbowman57 on 2012-06-04
gnome-color-chooser only works on gtk-2.0.  Firefox is gtk-2.0, Nautilus is gtk-3.0,  which is why in a previous post traditionalist was unable to change things in Nautilus, etc..

That being said,  y'all do whatever you want.  I'm outta this thread.

Dave, you know where to find me. :)

---

### Post by traditionalist on 2012-06-05
> **cbowman57 said:**
> gnome-color-chooser only works on gtk-2.0.  Firefox is gtk-2.0, Nautilus is gtk-3.0,  which is why in a previous post traditionalist was unable to change things in Nautilus, etc..

That being said,  y'all do whatever you want.  I'm outta this thread.

Dave, you know where to find me. :)

I finally grasped the differences here, after a lot of reading and trials. I see the problems involved. However, they  are not problems for me as I only want a functional desktop and theme.

There is not much point in making things more complex apparently just for the sake of it. Neither the new GNOME shell  nor Unity are much use to an average user in my opinion. They are certainly no use to me. The tweaks for the gtk2  stuff are sufficient for my purposes right now. and for some things like Nautilus I can edit the theme setup just for that program,  it requires some research of course. 

Sorry if all this upset you.

---

### Post by anewguy on 2012-06-08
I've been without internet service a few days, so I just got back here.  The tool I'm working on is for modifying the gnome-shell.css file that comes when you install the gnome-shell package.  What I'm doing is all gtk 3.

I'll keep plugging away, and I'll definitely being talking with you, cbowman57!  Thank you **SO*** much for your help here!!

Dave ;)

---

### Post by airtonix on 2012-06-08
If you're using pyGTK could you think about hosting the source code on github or bitbucket and allowing others to help contribute?

Also, if you are using pyGTK i would implore you to consider future projects to be written in py-side. 

py-side makes it much easier to distribute on all platforms (for applications where it makes sense to be multi-platform).

---

### Post by anewguy on 2012-06-08
> **airtonix said:**
> If you're using pyGTK could you think about hosting the source code on github or bitbucket and allowing others to help contribute?

Also, if you are using pyGTK i would implore you to consider future projects to be written in py-side. 

py-side makes it much easier to distribute on all platforms (for applications where it makes sense to be multi-platform).

I don't know any of those.  All I've been doing is trying to re-educate myself in C and using GTK.  Thought I would still remember enough C, but that's been more than a battle, but getting there.

Please also note:  I would prefer someone to step in who is more adept in a current language and CSS and write a completely new program using that language but of course providing a simple GUI for the user.  The average user isn't going to know what panel-button:focus is, but if you describe in plain English what it is in the GUI they will be able to use it.

I've posted here before and in another thread asking for help - not for me, not to take over my code.  Rather, start this project from scratch for someone looking for a way to contribute to Ubuntu.  I don't need it myself, and believe me when I say NOBODY would want to get stuck with my code.

---

### Post by traditionalist on 2012-06-11
This will change the nautilus background colour, I have used a medium grey here;

[[IMG]http://img254.imageshack.us/img254/1390/pictures002.th.png[/IMG]]("http://img254.imageshack.us/i/pictures002.png/")

you need the dconf-editor;

```
sudo apt-get install dconf-tools

```And then run the dconf editor:

```
sudo dconf-editor
```Browse to org.gnome.desktop.interface and locate: gtk-color-scheme

In this case; 

[[IMG]http://img72.imageshack.us/img72/7940/configurationeditor003.th.png[/IMG]]("http://img72.imageshack.us/i/configurationeditor003.png/")

This will change numerous backgrounds system wide. In combination with the "GNOME Colour Chooser", you can set up a general theme. I have used the Ambiance theme from here as a basis; 

[http://www.webupd8.org/search/label/eyecandy?max-results=10](http://www.webupd8.org/search/label/eyecandy?max-results=10)  I am running GNOME Classic, but this will also work on GNOME Shell with the right theme.

To change the font in the top panel on Gnome, go to "Advanced Settings " ( Gnome Tweak tool);

Fonts
[[IMG]http://img823.imageshack.us/img823/8426/advancedsettings004.th.png[/IMG]]("http://img823.imageshack.us/i/advancedsettings004.png/")

Change the value in the FIRST font setting box ( here set to 25);

[[IMG]http://img137.imageshack.us/img137/9217/advancedsettings005.th.png[/IMG]]("http://img137.imageshack.us/i/advancedsettings005.png/")

this sets the font size in the top panel.

---

### Post by anewguy on 2012-06-11
While nice to know, that is off topic for this thread.  This thread is specifically for changing options in the top panel (and perhaps it's pull downs) when you are using the gnome-shell package, not just gnome.

Let's try to keep everything here specific to using the gnome-shell package.  It's not gnome as you get by default - you have to install the package.  There is a difference.

So, following the title of the thread and the beginnings of this thread until lately, you will notice everything is about the gnome-shell package.  All the other options discussed should actually have been in a seperate thread.  Right now everyone is taking the thread off topic.  That's also the point that cbowman57 was trying to make.  While nautilus is gtk-3, there is also no tie to gnome-shell.  Gnome-shell is a seperate package.

Dave ;)

---

### Post by traditionalist on 2012-06-11
> **anewguy said:**
> While nice to know, that is off topic for this thread.  This thread is specifically for changing options in the top panel (and perhaps it's pull downs) when you are using the gnome-shell package, not just gnome.

Let's try to keep everything here specific to using the gnome-shell package.  It's not gnome as you get by default - you have to install the package.  There is a difference.

So, following the title of the thread and the beginnings of this thread until lately, you will notice everything is about the gnome-shell package.  All the other options discussed should actually have been in a seperate thread.  Right now everyone is taking the thread off topic.  That's also the point that cbowman57 was trying to make.  While nautilus is gtk-3, there is also no tie to gnome-shell.  Gnome-shell is a seperate package.

Dave ;)

The thread title is;

				**Re: Ubuntu with Gnome Shell: How do I change the font size in top panel**

That is what I described.  What I described works in GNOME Shell, and I know that because I tried it.

It was a direct answer to the question in the thread title.

If you consider it off topic then that is rather odd.

However this may be, you just lost a contributor.

Bye bye.....................

---

### Post by anewguy on 2012-06-11
Font size?  Top Panel?  That's the title.  Not nautilus.  This in the past has all been about things that deal with the top panel in gnome-shell, hence the title.  Doesn't say "everything that runs while you are using gnome-shell".  Open another thread.

---

### Post by anewguy on 2012-06-14
Well, anyone can do whatever they want with this thread now.  I'll be notifying cbowman57 as well.  I'm dropping out of ubuntu completely and just going back to Windows 7.  I just can't take the bickering and finger-pointing anymore.

Good luck.

---

### Post by drs305 on 2012-06-14
FTR:

Since the OP has indicated he is through with the thread, the thread is closed. If the OP wishes to reopen it please contact any forum staff member.

---

