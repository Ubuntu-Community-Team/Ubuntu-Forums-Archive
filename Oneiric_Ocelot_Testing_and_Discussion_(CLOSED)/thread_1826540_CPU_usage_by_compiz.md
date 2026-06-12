---
title: "CPU usage by compiz"
date: 2011-08-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by scradock on 2011-08-16
I have noticed that compiz is using an awful lot of CPU cycles just sitting there, with Unity desktop in Oneiric. Checking with "top", on the same machine (see sig):

Maverick (compiz, no Unity)      compiz uses 0.3% cpu

Natty (compiz, no Unity)         compiz uses 0.3% cpu

Natty (compiz, with Unity)       compiz uses 2 - 3% cpu. This rises when complex displays are involved, but goes back to 2% when other programs close.

Oneiric (compiz, with Unity)     compiz uses over 3.0% cpu, which can rise to 15 - 20% when firefox opens, and then does not go down again even after firefox is closed.  [ After another hour it's up to over 25%...]


Any ideas as to what is keeping it spinning? The desktop is just sitting there, for 2 hours without any activity, but compiz is still churning...

---

### Post by cariboo on 2011-08-16
My systems been up for just about 12 hours, and according top top compiz is using 1%. Running three different apps at the moment, cpu average usage is 1 - 3%.

My system runs and AMD X2 240, 2GiB ram and an nvidia GT218 graphics card.

---

### Post by fjgaude on 2011-08-16
My system has been up for well over 24 hours, an Intel i5 655K, 4 GB RAM, Intel GMA HD video integrated within CPU, with compiz using anywhere from 0 to 4%. The box is fast under Unity 3D, very fast.

---

### Post by jerrylamos on 2011-08-17
Compiz on my test pc's churns away even when I'm in full screen application mode.

Easy fix, Unity-2D doesn't do Compiz, crisper, faster, less useless overhead, ...

My 76 year old eyes do like nice sharp images and 3D "fuzzy shadows" and unreadable "transparent?" overlays do NOT help readability.

If fuzzy unreadable 3D was all there was I'd be on Lubuntu. 

Now Microsoft & Apples answer to all the overhead is "Buy a faster more expensive" pc.  This is from an Acer netbook, $248 (I saw $200 at Wallmart) which runs Ocelot just fine with Unity-2D.  It'll do 3D like my 1280x1040 and 1440x900 pc's will, but I don't like the fuzzy indistinct Unity-3D stuff on them either.  

Hopefully Ubuntu won't abandon their traditional "choices" theme.

Jerry

---

### Post by fjgaude on 2011-08-17
The drop shadows add depth to the windows. I'm sure the transparency will be adjustable before it is over, maybe in 12.04. I like sharpness too, I'm 79. <smile>

You can control the transparency for terminal through adjustment therein.

I like 2D on my netbook with its 1366x768 screen! Very sweet.

---

### Post by Xgen on 2011-08-17
The only thing that stops me from using 2d is non-centering windows. There is a patch for it, I believe, but not sure how to apply it.

---

### Post by fjgaude on 2011-08-17
> **Xgen said:**
> The only thing that stops me from using 2d is non-centering windows. There is a patch for it, I believe, but not sure how to apply it.

What is 'non-centering windows'?

---

### Post by Xgen on 2011-08-17
I would like windows that are not fully maximized centering to the middle of the screen...like the Place Windows plugin in compiz. Annoying (to me) that they place to the left side.

---

### Post by fjgaude on 2011-08-17
> **Xgen said:**
> I would like windows that are not fully maximized centering to the middle of the screen...like the Place Windows plugin in compiz. Annoying (to me) that they place to the left side.

Oh... thanks for the explanation!

---

### Post by yelo3 on 2011-08-20
I also get 30% of cpu usage in compiz.
Any workaround? Actually I choose the force fallback mode in the system info setting, but compiz is still running

---

### Post by cariboo on 2011-08-20
> **yelo3 said:**
> I also get 30% of cpu usage in compiz.
Any workaround? Actually I choose the force fallback mode in the system info setting, but compiz is still running

What are your hardware specifications? Even my atom powered netbook only uses 10 -15% when running Unity 3D

---

### Post by yelo3 on 2011-08-21
It's not hardware specification fault, I have a slightly better processor.
I think it's a bug because it does not happen every times

---

### Post by jerrylamos on 2011-08-21
> **cariboo907 said:**
> What are your hardware specifications? Even my atom powered netbook only uses 10 -15% when running Unity 3D

I'm not willing to give up 10%-15% for fuzzy borders and illegible transparent windows on my atom powered netbook.  

If I'm trying to get something done I run either Narwhal or else Unity-2D on Oneiric on the netbook.  I do give a whirl with Compiz just looking for bugs.

Speaking of bugs, Compiz Oneiric runs a few minutes then locks up tight on my 3.33 gHz tower with ati radeon xpress 200.  Last night I even had to use the terminal strip switch.

No action on my launchpad bugs.

Of course Unity-2D without Compiz bugs and Compiz hangups and Compiz overhead runs very nicely on that pc for as long as I want.  So does Narwhal, Meerkat, Lynx.

Jerry

---

### Post by pwnjangles on 2011-08-21
Always wondered is Compiz actually needed for anything other then special effects? I always uninstalled it but with Unity I'm guessing that's not a option...will 11.10 have the old (no effects) option?

---

### Post by ventrical on 2011-08-21
> **yelo3 said:**
> I also get 30% of cpu usage in compiz.
Any workaround? Actually I choose the force fallback mode in the system info setting, but compiz is still running


I got 10-15% CPU with compiz but it is not affecting my system . I have an older Acer Aspire 3620 and it does all  the stuff fairly nicely.

---

### Post by ventrical on 2011-08-21
I un 'ticked' 'wobbly windows' setting in the Compiz Settings Manager and the CPU usage is now 0 - 1%.

---

### Post by ventrical on 2011-08-21
I re-enabled 'wobbly windows' and turned off 'Fading Windows' and ' Opacity, Brightness and saturation' because they do not work anyways and the CPU went back to normal and I got a neat 'sticky effect/phenomenon also .. hehe .. really weird one.

** Actually the CPU usage went down only a bit after a while - 8 to 11% .. so I suspect 'wobbly windows' could be the culprit. From what I see from the error pop-ups I am getting (that I cannot send) it seems to be a hook with the "guest user"  or somthing to this effect - (which I should have captured a screenshot of.)

---

### Post by scradock on 2011-08-21
> **jerrylamos said:**
> I'm not willing to give up 10%-15% for fuzzy borders and illegible transparent windows on my atom powered netbook.  

If I'm trying to get something done I run either Narwhal or else Unity-2D on Oneiric on the netbook.  I do give a whirl with Compiz just looking for bugs.

Speaking of bugs, Compiz Oneiric runs a few minutes then locks up tight on my 3.33 gHz tower with ati radeon xpress 200.  Last night I even had to use the terminal strip switch.

No action on my launchpad bugs.

Of course Unity-2D without Compiz bugs and Compiz hangups and Compiz overhead runs very nicely on that pc for as long as I want.  So does Narwhal, Meerkat, Lynx.

Jerry

Yes, it's good to know that we don't get Compiz eating all the CPU cycles when it's not running; some of us are trying to test the standard offering to give feedback. That's why this is the Oneiric TESTING forum.

Looking at the responses it seems some folks get the high CPU usage running Compiz in Oneiric, others don't. No-one seems to know why.

---

### Post by scottstensland on 2011-08-25
if you strace the pid of compiz you will see its polling incessantly ...

sudo strace -p 2197   

replace this 2197 pid with your compiz pid - as per 

ps -eaf | grep compiz

I have a 2 year old intel Core 2 Due 2.4 gig and compiz typically sits at 12% CPU usage
which makes the laptop fan race continually - doing a reset of unity drops CPU to about 2% to 4%

unity --reset

which takes your unity back to initial default values
I am very interested in hearing about a fix to unity + compiz excessive CPU usage.  
These symptoms are also true on the latest dev release ubuntu 11.10 so no help come October.
... thinking about switching to a ~better~ window manager like xfce

---

