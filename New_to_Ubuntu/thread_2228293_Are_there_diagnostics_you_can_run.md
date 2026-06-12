---
title: "Are there diagnostics you can run?"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by simonf2 on 2014-06-06
I am a total newbie.  I have a Dell laptop - aged but was working ok and I had the desire to leave Windows and use Linux.

I tried to install another distro - bit of a nightmare during which I was advised to run it in compatibility mode.  Eventually I got the message "the x server is now disabled, restart MDM when it is configured properly".  Things went from bad to worse and in desperation I switched to Ubuntu and this installed but it is running very slowly - the windows kind of fade in and out in a slow and jerky manner (like an old movie). 

I have spent hours Googling, searching forums and looking through the settings for some sort of diagnostic.  I accept I am struggling - even opening the Terminal was an event ... I didn't even know what the terminal was - but I am hoping I can get this sorted.  I wonder if anyone can suggest something I can run to see if there are settings messed up.

If I may ask a supplementary - when you put a command in the terminal how do you know it is doing anything?  Mine just seems to sit there with nothing happening.

Sorry if I seem somewhat vacant.

---

### Post by grahammechanical on 2014-06-06
There are various diagnostic utilities in Linux. But unless we know what they are reporting it can confuse us even more. Well, they confuse me.

If we have a graphic adapter that does not support the default Ubuntu user Interface, Unity, the Ubuntu will load a fall back open source video driver that gives an approximation of Unity 3D. This fall back driver is called llvmpipe. If you open the power/cog menu and select About this Computer that will open the details page. What does that tell you about the graphics? Does it say Gallium llvmpipe? My details page simply says "Gallium." That is because I am using an open source video driver.

To find out if your graphic card can support Unity 3D run this command in the terminal.

```
/usr/lib/nux/unity_support_test -p
```

This is what I get

> OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVA5
OpenGL version string:  3.0 Mesa 10.1.3


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes


If you get No, then you need to install a flavour of Ubuntu such as Xubuntu or Lubuntu. If the answer is Yes, then go to System Settings>Software and Updates>Additional Drivers tab and experiment, and I do mean, experiment with available video drivers. Allow the utility time to find the drivers.

If you install a proprietary video driver and a reboot breaks the desktop then, at the Grub boot menu select Advance Options for Ubuntu, and then select Recovery mode and at the recovery menu select Resume. That should get you to a desktop but it will be with llvmpipe, again.

Regards.

---

### Post by 3rdalbum on 2014-06-06
Just how "aged" is this computer? Specs? Ubuntu requires decent 3D graphics support, and an older computer would probably struggle. It sounds like you have only basic 3D support, maybe even none at all.

There is a program preinstalled on Ubuntu that looks for 3D drivers that can be downloaded for you - I can't remember what it is called these days but it probably has the word Drivers in its name. If it says simply that no additional drivers can be found, then there is not much you can do to speed things up on Ubuntu.

However, there is a lighter and faster version of Ubuntu, called Lubuntu. It doesn't require 3D graphics, and it can run everything the normal Ubuntu can, but its user interface is a bit more old-school and more basic. I would give that a try if I were you.

---

### Post by Rob Sayer on 2014-06-07
First you should know what graphics adapter you have.  See here (copy and paste into terminal):

[http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card](http://askubuntu.com/questions/72766/how-do-i-find-out-the-model-of-my-graphics-card)

and post the output here.  Embed them in [CODE] tags.  That's important.  The support here is great ... for that reason I don't think linux novices should use anything except ubuntu ... but it's free.  Making things readable helps a lot.

Some terminal commands may take a minute to finish.  No, they don't give you any indication they're running.

Also post other specs.  Some old XP machines may run ubuntu with Unity well if they're really specced out but most don't seem to.

I installed ubuntu/Unity first, but I don't use it anymore.  On my i3 based 4Gb laptop I found it too slow.  On that one I use Kubuntu 12.04 now.  It's also considered a heavyweight DE but, unlike UNity, you can shut off the eye candy and some other things and really speed it up.

Linux may run nicely on old hardware but the thing is, technically linux is *just the kernel*.  Many modern distros use DEs that aren't lightweight.  Unity (or others like Cinnamon) need about the same hardware spec as windows 7 or 8.

On my 1Gb netbook which also has linux hardware support issues (no video 3D acceration), I've never even considered using Unity.  Kubuntu was too slow as well (though faster than the Windows 7 starter it came with).  I tried installing the bare minimal KDE desktop and that was a lot better but not fast enough.

I'd consider KDE with at least 2Gb of RAM but Xubuntu would be a lot faster.  I'm running Xubuntu 14.04 now on this netbook.

But I had Lubuntu 13.10 before and I may install 14.04.1 when it comes out.  I find it a bit clunky but not much less so than Xubuntu, and it's *way* faster in 1Gb.

With less than 1Gb I'd definitely try Lubuntu, unless it's less than 512Mb.  Then I'd frankly try another distro.  No Ubuntu version is really intended for that small a memory space.
On this 1Gb netbook

---

### Post by stalkingwolf on 2014-06-07
i have run mint 13 on as little as 1.6 gz processor and 1 gb ram. it was at times slow.
When using the terminal or really anything else there is one critical step to remember.  This might sound trite but it is not meant to be
i do it now and then still and sit and watch for things to happen until i realize, ..................   hit enter dummy.

Always remember to hit enter to start things.

---

### Post by oldos2er on 2014-06-07
> **simonf2 said:**
> If I may ask a supplementary - when you put a command in the terminal how do you know it is doing anything?  Mine just seems to sit there with nothing happening.

Some commands will show verbose output when they're working, some will show none at all; some can be made verbose with -v, -V, or --verbose. When you're returned to the prompt, the command is done.

---

### Post by simonf2 on 2014-06-07
Firstly a big thanks to everyone who has posted; I have endeavoured to follow everything through sequentially.  My apologies for being a bit slow but I am having real trouble getting anything to happen and I am getting a lot of &#8220;this window is not responding&#8221; messages.  Anyway:
[B]
Grahammechanical:
[/B]
Opened details of the computer and about graphics it says Intel 852GM/855GM x86/MMX/SSE2

When I run: /usr/lib/nux/unity_support_test -p the significant answers (I imagine) are:

Not software rendered: no
Unity 3D supported: no

Although I do not at this stage understand the reasons, presumably the reality is that this laptop will not run 14.04

[B]3rdalbum:

[/B]The laptop may be 8 years old.  In my ignorance I thought that as long as it met the technical spec that I found on the Ubuntu website then all would be ok.

I have searched for drivers and against additional drivers it states that none are available.

Would Lubuntu really give me a flavour of Ubuntu I wonder?
[B]
Rob Sayer:[/B]

The laptop has 1.2 Gb of memory 2.4 GHz processor video card as above.  

I have tried to run these commands off the link and seem to get &#8220;command not found&#8221; each time.  I am aware that I am not used to the syntax but I have been careful and previously other commands have worked.  At one stage it suggested I meant another command so I typed this in but then it said there was an &#8220;unexpected token&#8221;.  Truth told and after years of messing with Windows in an amateurish way, this is like starting all over.  I must admit I don't even know what &#8220;code tags&#8221; are.  Anyway, the technical info regarding compatibilities is really helpful.

Thanks too to **Stalkingwolf** and **oldos2er** &#8211; helpful stuff both.

Sad as it may seem &#8230; I am really excited at getting to grips with Ubuntu and very appreciative of the posts. 

Thanks in advance for any other comments anyone would care to add.  One way forward I have considered is to make my W7 laptop dual boot - this is a relatively recent Dell Latitude E5410 with an i5 2.40 GHz processor but it still only has what I believe is called an onboard graphics card.  How would I know if this would be ok?

---

### Post by sudodus on 2014-06-07
Seeing your specs I think you can choose between Lubuntu or Xubuntu 14.04 LTS or Xubuntu 12.04.4 LTS or another light-weight respin of Ubuntu 12.04 LTS, Bento, Bodhi or LXLE.

If you manage to get the hardware drivers to work in 14.04 LTS, I would recommend it, but sometimes it is better to use an older (but still supported) version for an older computer.

See this link for more details and tips
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by simonf2 on 2014-06-08
Thanks for the post and link, I'll give Xubuntu a go first I think

Cheers

Simonf2

---

