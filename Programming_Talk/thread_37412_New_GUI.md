---
title: "New GUI"
date: 2005-05-27
forum: Programming Talk
---

### Post by credo on 2005-05-27
I'm looking to create an Audio mixing application, similar to that of Ableton Live ([screenshot](http://www.djcredo.co.uk/misc/ableton.gif)). Given the complexity of the functions required, it would seem wise to create a new GUI toolkit, such that the Ableton people have done. This also seems to work well in Blender.

How would I go about doing something like this?

My second question is: I would like this program to be portable to Windows if needed. Are there any good cross-platform audio toolkits around? If so, it needs to be accurate - the last time I used GStreamer, I was dissapointed by it's seek accuracy. lack of reverse function, sound quality when using the "speed" module, and it's overall difficulty on flushing its buffer when seeking. Latency was also an issue.

Finally, any tips on writing platform-independent code? I will probably use C++, but if someone can make a good case for mono, I might consider shifting to C#

Cheers

---

### Post by LordHunter317 on 2005-05-27
[QUOTE=credo]Given the complexity of the functions required,[/quote]I don't see anything complex in that GUI there.

>  it would seem wise to create a new GUI toolkit, such that the Ableton people have done.[/qoute]No, it really doesn't.

[quote] This also seems to work well in Blender.No, it really doesn't.  Blender is one of the least accessible programs on the planet.

> How would I go about doing something like this?You'd write a library to generate widgets that uses a bunch of nasty, low-level X11R6 API calls.

> My second question is: I would like this program to be portable to Windows if needed. Are there any good cross-platform audio toolkits around?SDL is your best bet.  It's also probably inadequate for your needs.  You're likely to end up writing an abstraction layer.

>  If so, it needs to be accurate - the last time I used GStreamer, I was dissapointed by it's seek accuracy. lack of reverse function, sound quality when using the "speed" module, and it's overall difficulty on flushing its buffer when seeking. Latency was also an issue.Some of this maybe related to your kernel configuration.  Stock 2.6 is inadequate for realtime-audio needs.

> Finally, any tips on writing platform-independent code?Write an abstraction/runtime layer.

---

### Post by tread on 2005-05-27
> 
Finally, any tips on writing platform-independent code?


Use mono :D. Sorry, but you really are trying to reinvent the wheel here. If you want real time, writing a GUI toolkit will not help since you cannot force the X calls to be real time (as far as I know). You can get better sound streaming real time, but that has more to do with your kernel than the toolkit.

Rather than writing the toolkit, time spent on the application itself would be more justified .. and using an existing toolkit also keeps the UI of your software consistent with the rest of the applications (which in turn means more people will use it).

Another option is QT .. I do not like KDE, but QT is a joy to program in.

---

### Post by LordHunter317 on 2005-05-27
[QUOTE=tread]If you want real time, writing a GUI toolkit will not help since you cannot force the X calls to be real time (as far as I know).[/quote]The GUI doesn't need to be realtime though.

---

### Post by credo on 2005-05-27
[QUOTE=LordHunter317]I don't see anything complex in that GUI there.[/QUOTE]

Well, I do. If you were to research the current state of professional music tools, you would see that the majority were not created with any regular toolkit, rather a customised one they have used for their purpose. 

[QUOTE=LordHunter317]
No, it really doesn't.  Blender is one of the least accessible programs on the planet.[/QUOTE]

Once you have learnt Blender, it's power is immense. Concerning my program, controls designed to look like their real-world counterparts (especially in audio equipment such as synthesizers and DJ mixing equipment) should have the effect of making the program more accessable to musicians. It might seem counter-intuitive to computer users, but that isn't the audience I'm going for. 

[QUOTE=LordHunter317]You'd write a library to generate widgets that uses a bunch of nasty, low-level X11R6 API calls.[/QUOTE]
Thankyou, that was an answer I was looking for. However, wouldn't that make it difficult to port? I have no experience in this area - its just a guess.

[QUOTE=LordHunter317]SDL is your best bet.  It's also probably inadequate for your needs.  You're likely to end up writing an abstraction layer.[/QUOTE]
Hmmm, now that does seem like re-inventing the wheel. Are there no other audio toolkits that provide a solution? JACK, portaudio etc?

[QUOTE=LordHunter317]Some of this maybe related to your kernel configuration.  Stock 2.6 is inadequate for realtime-audio needs.[/QUOTE]
Thats a good point, i'll look into that.

---

### Post by 23meg on 2005-05-27
it seems 2.6.12 will come with task preemption built in, thus even the stock one might be suitable for realtime operations.

---

### Post by LordHunter317 on 2005-05-27
[QUOTE=credo]Well, I do. If you were to research the current state of professional music tools, you would see that the majority were not created with any regular toolkit, rather a customised one they have used for their purpose.[/quote]And my understanding is that most of them are crap, and that most professionals would rather something simpler.  Things like dials and VU meters don't translate well to a computer, and generally people I've spoken to would just like to see them left out then all the work done to add them in.

I certainly don't see anything whatsoever in that picture that couldn't be done with a regular UI.  It'll be more accessible and easy to use.

> Once you have learnt Blender, it's power is immense.Yes, but it doesn't change it's fact that shit is too kind of a word for its UI.

>  Concerning my program, controls designed to look like their real-world counterparts (especially in audio equipment such as synthesizers and DJ mixing equipment) should have the effect of making the program more accessable to musicians.But they really won't.  Try it out if you don't believe me. My computer doesn't have dials, so a program that looks like a mixing board is just hard to use.   Concepts that work well with physical hardware don't work well with virtual hardware. 

>  It might seem counter-intuitive to computer users, but that isn't the audience I'm going for. I think ultimately, it will be counter-intuitive to them, because it'd added work for little gain.  Comfort can go along way, but I think you're crippling them too much by doing this.

Really.  Dials/Knobs don't work on a computer.  Meters only work to a certain extent, and seem kind of silly when you can give me an exact numerical reading.  Scopes work, but the ideal layout for it's controls is not like it is in the real-world (where it's usually constrained by other concerns).    Sliders work, but they don't have the fine grained control they do in the analog world, so you have to provide a numerical input **anyway**.

Seriously.  Sit down at a mixer board or whatever piece of equipment you're interested in, and pretend all you have is a keyboard and a mouse to control it.  You'll quickly realise that doing this is a PITA.  Remember that some stuff doesn't translate perfectly as well:  Sliders are analog in the real-world, but digital in the computer world.  

Then think about the fact this application has to exist on a computer with a bunch of other applications as well.  You have limited real-estate as well.  If you have 32 channels and want to look at one and 18 together, that's somewhat easy for a human to do in the real-world.  It's harder to do on the screen if I can't drag and drop them to be right next to each other.

Then realize for Windows and Linux, you're going to have to learn not one, but two very low-level GUI APIs to provide what you want.

I'm not a sound engineer, but I am a ham radio operator.  And I know for a fact that doing computer-control of a radio with a GUI that looked like a radio would be absoutely useless.  It'd just get in the way.  A lot of the physical controls are based on the same precepts, which is why I bring this up.

> Thank you, that was an answer I was looking for. However, wouldn't that make it difficult to port?If you write your GUI library to be portable to begin with, sure.

> Hmmm, now that does seem like re-inventing the wheel. Are there no other audio toolkits that provide a solution? JACK, portaudio etc?No portable ones.

---

### Post by credo on 2005-05-27
I can see you are definately coming from a HCI standpoint, and I agree - knobs don't translate well to a computer.

However, Ableton Live is a prime example of how, in this specialized circumstance, emulating musical hardware is a plus. 

I know for a fact that this sort of software is used by professionals in the DJ industry, I mean, arguable the world's biggest DJ (Sasha) uses it in his mixes. And remember, most people will link it to a MIDI controller which *does* have knobs. I also disagree that most music software designed with an independent gui is crap.

Perhaps Blender was a poor example. Lets take the Wired project ([Screenshot](http://bloodshed.net/wired/img/screenshots/wired_shot-01.png)). Now, your views on this may differ from my own, but being a musician myself, I would find this much easier to work with due to its obvious similarities with real-world equipment.

---

### Post by 23meg on 2005-05-27
ableton live is emulating music hardware in terms of looks? which hardware? it's the least hardware-like looking major audio app out there. i think trying to make things look like hardware by drawing smooth scrolling 3d knobs etc .is kind of lame, and for god's sake, look at all major sequencers and vst plugins: all they want to do is look like hardware. live has completely 2d, plain, vectoral graphics that don't at all try to look like "the real thing", which is a very good design decision.

[QUOTE=LordHunter317]My computer doesn't have dials, so a program that looks like a mixing board is just hard to use. Concepts that work well with physical hardware don't work well with virtual hardware.[/QUOTE]

you should remember that even most semi-pro users use a dedicated midi controller that has knobs and faders to control this kind of interface, not a mouse or a keyboard, so it kind of make sense to have, say, dials. but it definitely doesn't to try to make them look like the real thing.

---

### Post by credo on 2005-05-27
I think with Ableton, it's still the visual representation thats important. The programmers went that step further in creating widgets that resembled the functionality of the hardware they were emulating, rather than sticking with your standard stock widgets.

The sequence of dials and knobs may not look picture-perfect, but I would argue that the layout and representation is enough for producers and DJ's to feel at home with the software. I know I do.

Hence the overall look is more "polished", whilst still giving it the look and feel of a "musical instrument".

---

### Post by toojays on 2005-05-27
By the way, for the GUI thing, to keep it cross platform, your best bet is to just take an already existing toolkit like Qt or wxWidgets, and create your own custom widgets for the things you need. For example, [this page](http://www.koansoftware.com/en/prd_svil_wxindctrl.htm) shows some widgets for industrial control, based on wxWidgets.

---

### Post by LordHunter317 on 2005-05-27
[QUOTE=credo]However, Ableton Live is a prime example of how, in this specialized circumstance, emulating musical hardware is a plus. [/quote]And you can do that, and that's fine.  But you **can** do it with **standard** controls.  

When I look at that GUI, I see mostly standard controls that have been dressed up.  
The whole sidepane could be a regular treeview with no issues for example.  The buttons could be regular push buttons.  This is where my beef is.  That and the fact the color scheme is horrid, but that's an aside :p

>  I also disagree that most music software designed with an independent gui is crap.Most GUI software is crap IME, especially if it's specialied to any industry.  Even in a "consistent" world like Windows, you have things that act in wierd and non-standard ways.  And it just serves to fustrate and confuse the user.

[quote=23meg]so it kind of make sense to have, say, dials. but it definitely doesn't to try to make them look like the real thing.[/quote]A dial is probably the worse control you could ever have in a GUI, even if corresponds to a real-world one.

[quote=credo]The programmers went that step further in creating widgets that resembled the functionality of the hardware they were emulating, rather than sticking with your standard stock widgets.[/quote]And obviously, for any audio application, the standard widgets aren't going to completely provide what you need.  And providing custom widgets where necessary for functionality is fine and OK.

But that's a far cry from reinventing the whole GUI and writing a whole toolkit.

> Hence the overall look is more "polished", whilst still giving it the look and feel of a "musical instrument".That's just the thing, it's not a musical instrument, it's a bloody computer.  While this line of thinking is somewhat noble in trying to provide a more familiar environment to the user, I think it's ultimately nieve.  It just doesn't translate well enough to be worthwhile.

---

### Post by 23meg on 2005-05-28
[QUOTE=LordHunter317]A dial is probably the worse control you could ever have in a GUI, even if corresponds to a real-world one.[/QUOTE]

can you elaborate; why exactly?

---

### Post by LordHunter317 on 2005-05-28
[QUOTE=23meg]can you elaborate; why exactly?[/QUOTE]
Well, one advantage of dials is that they have tactile feedback.  No such thing exists on a computer (well, a standard one anyway).  They're also cumbersome to work with.  We don't generally move our mice in circular motions, so the idea is somewhat foreign.  Having the dial move when you move the mouse up/down compenstates for that, but is also non-intuitive.

Dials are also hard to read, even in the real world.  They also take up a ton of screen real-estate, for the dial and it's markings.  This is the biggest problem.  They're not easy to read, in fact, most of the equipment I use daily that has dials doesn't have markings on them at all: you never read a value from a dial.
Logic follows then if I'm going to have a textbox then with the value of the dial anyway, why not let me select from a drop-down list (for discrete ranges) or enter a value (for analog ones)?  It's certainly a more natural way of doings things on a computer and I feel it's more optimal.

To be clear: I'm talking about circular dials, like a gain control on a mixer, or a flywheel on a radio.

---

### Post by flightcrank on 2005-05-30
[QUOTE=credo]I'm looking to create an Audio mixing application, similar to that of Ableton Live ([screenshot](http://www.djcredo.co.uk/misc/ableton.gif)). Given the complexity of the functions required, it would seem wise to create a new GUI toolkit, such that the Ableton people have done. This also seems to work well in Blender.

How would I go about doing something like this?

My second question is: I would like this program to be portable to Windows if needed. Are there any good cross-platform audio toolkits around? If so, it needs to be accurate - the last time I used GStreamer, I was dissapointed by it's seek accuracy. lack of reverse function, sound quality when using the "speed" module, and it's overall difficulty on flushing its buffer when seeking. Latency was also an issue.

Finally, any tips on writing platform-independent code? I will probably use C++, but if someone can make a good case for mono, I might consider shifting to C#

Cheers[/QUOTE]
 Java is cross platform it will work on Liunx,windows and mac without have to change your source code at all

---

### Post by sudokubuntu on 2005-12-02
Hello! 
This is my first post in here, so hello to you all.

This is an interesting thread.
I just installed Ubuntu a couple of days ago, and I'm liking it.
Just installed Ableton live with wine but I'm such a noob so I don't know how to run things installed through wine yet   :confused: .
BUT
Seems to me LINUX is a much better OS than WINDOWS XP, and i'd like to continue using it, just need some music making software   :smile:    

If I can get all this to work, it might be goodbye to WINDOWS.

So please, if you develop anything, please post info here, I would really like to know.



CHEERS

---

### Post by Lagiv on 2005-12-02
I want to say also that I would love a music app with standard widgets. I hate it that every VST plugin etc has to have it's own *sleek* GUI. :???:

---

### Post by David Marrs on 2005-12-04
I think it would be much easier to add functionality to gtk (or whatever) to get what you need rather than completely create a new widget set from scratch. You might even find that people at Ardour, for example, have already done what you need. Or there's always Cairo now. :)

Gstreamer isn't designed for real time processing, so that's out of the question. I've just started getting into Jack but I know it's not supported in Windows (it is on Mac though). To be honest, I think you're going to have a problem in this area.

I think I'd want to go with C or C++. It's very portable and it's got to be faster than managed code, which is a must in audio. I don't know about C#. How easy is it to work with unmanaged code from within mono? It might be more trouble than it's worth trying to bind to Jack, Ladspa or what have you.

As for Ableton Live...

It's designed to be used in a dark, smokey room, on a vibrating table. The graphics are simple, bold and large for good reason. Dials are good because you can fit more of them into a space and that's a good thing when you've got lots of parameters to simultaneously control and read. They're also good because **that's what you're using in real life.** Nobody's controlling this thing with a fecking mouse. They're using dedicated hardware controllers and that's what Live is trying to emulate in its design. I don't want to see a slider moving up and down as I turn a knob.

Personally I think Live is a good example of what an audio interface should be doing: exploiting the environment of a PC while retaining the familiarity of a hardware controller.

---

### Post by David Marrs on 2005-12-05
[QUOTE=David Marrs]
Gstreamer isn't designed for real time processing, so that's out of the question. I've just started getting into Jack but I know it's not supported in Windows (it is on Mac though). To be honest, I think you're going to have a problem in this area.[/QUOTE]
Btw, I came across [PortAudio](http://www.portaudio.com) yesterday. It's a cross-platform API for music production. Unfortunately, ALSA seems to be unsupported, so you're stuck with OSS. It might be what you're after.

---

