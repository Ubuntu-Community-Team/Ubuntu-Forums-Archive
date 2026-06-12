---
title: "Black screen during boot"
date: 2014-01-29
forum: New to Ubuntu
---

### Post by maazmahmood on 2014-01-29
I've looked at this thread, I did the nomodeset, but instead of just a black screen, I get a blackscreen with blinking underscore
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I'm REALLY new to Linux/Ubuntu, so if there are some other instructions could someone dumb it down for me please?
Thanks in advance

---

### Post by Bucky Ball on 2014-01-29
Welcome. At that blinking underscore try:

sudo service lightdm start

... if you are using Ubuntu. For other flavours you may need a different command.

---

### Post by maazmahmood on 2014-01-30
I don't think I'm even able to type anything, it just sit's there blinking

---

### Post by Bucky Ball on 2014-01-30
You don't think or you can't?

---

### Post by maazmahmood on 2014-01-30
1st try was 12.04 and I'm 99% sure it didn't type, just downloaded 13.01 and I didn't try. Which version should I go with? But assuming I can't, what do I do

**Update** I was able to right it out, but nothing happens, it's as if though it's just text, nothing saved or anything.

---

### Post by Bucky Ball on 2014-01-30
You hit return after typing that in, naturally? What happens when you hit return? Does it simply go to a cursor or black screen? Please post all details. ;)

---

### Post by maazmahmood on 2014-01-30
Sorry, yeah, when I hit enter/return, it just moves the blinking underscore down and keeps blinking, as if it's just plain text and not a command.

---

### Post by squakie on 2014-01-30
I don't think you are in text mode yet - I think you are stuck in the gui start up when the video driver isn't correct.  

Please try the following:

- at the blinking cursor, hold down ctrl/alt and press F1
- do you get a login prompt?
- if you get a login prompt, type your normal userid and press enter
- when the password prompt comes up, type your password and press enter.  Note that nothing echoes on the screen when entering your passwrord.
- type:

lspci | grep VGA <press enter>

- copy those results so you can post them back here
- now is also the time to type the command that BuckyBall gave you:

sudo service lightdm start

- note any error messages (if any)
- if you then get the black screen with the blinking underscore cursor, do the ctrl/alt/F1 thing again to return to a terminal and check for any error messages

Please post all messages and the output I requested back here.

---

### Post by maazmahmood on 2014-01-30
Well when I did ctrl/alt F1 it flashed a bit and when I tried typing it typed a few letters then wouldnt let me type anymore. AND on the side note I don't have a login/password, because I haven't finished installation. 

Really sorry should have specified that this is during installation

---

### Post by squakie on 2014-01-30
I know there are other boot options to try as well.  If you have time, you could try downloading the alternate install CD image.  It installs everything but the installation process itself uses text mode and "terminal" style graphics.  Perhaps this would at least get it installed and everyone could work from there.

BTW - did you try the "Try Ubuntu" option instead of install to see if Ubuntu would even run off the media for you?

---

### Post by maazmahmood on 2014-01-30
I'm pretty sure I have the text mode, because I don't see any mouse, just have to move up and down with arrow keys and such. AND I'm installing from USB, as a DVD drive isn't available (long story). And yes I did try the Try Ubuntu Option as well

---

### Post by squakie on 2014-01-30
Did the "Try Ubuntu" option work - did you get a valid screen, etc.?

---

### Post by maazmahmood on 2014-01-30
I'm really sorry, I need to learn to provide more detail, and no it didn't same result as if I'm hitting "Install Ubuntu" exact same outcome. BTW how do I get graphical install?

Also I've been doing nomodeset, and without it, if I don't get blinking cursor I get this tiny red box on the top with just one letter in it. And every now and then the blinking cursor will have a higher resolution for some reaon

I've even tried the other options:frown:. I'm so frustrated I'm just about ready to give up

---

### Post by squakie on 2014-01-30
If you downloaded the normal Ubuntu iso download, the installer will run in  graphical mode.  That is where the problem is coming in - the install is trying to start the graphical part of things and it would appear there is a video driver problem or some other sort of error.

Do you by any chance know what the video is in your PC?

---

### Post by maazmahmood on 2014-01-30
Well I have nvidia 9800GTX or 9600 GTX, can't remember. But I'm booting using vga port on motherboard..... wait could I unplug my GPU and then try because I think even though I'm using on board graphics, it's still   card drivers

Yes it's the 9800GTX/GTX+

---

### Post by squakie on 2014-01-30
If you are booting using the gpu on the motherboard, it would depend on the type of CPU, if the gpu is onboard on actually in the CPU (APU) - such as the newer AMD processors.  

Do you know, and could you provide, the following:

- make/model of PC
- type of CPU
- if a seperate video card (such as the nVidia) is currently installed and if you have set the BIOS to select the onboard graphics or it is selecting PCI graphics?

---

### Post by maazmahmood on 2014-01-30
Model of PC: is gateway (don't laugh :D )
CPU: [COLOR=#333333][FONT=Arial]Intel® Core&#8482;2 Quad Q6600 quad core processor with VT
[/FONT][/COLOR]GPU: Nvidia 9800 GTX/GTX+, HOWEVER, it is not activated in BIOS, in BIOS it is set to run off onboard graphics and NOT PCI graphics

---

### Post by squakie on 2014-01-30
Ok, that helps some - at least we know more about what we are dealing with.  Still don' know what the onboard GPU is, but since it's an intel processer, it's probably something in the Intel set (not positive, but hopefully more likely).  So, as a long shot, when you try the install media just to boot into a live session and not to install, where you put in "nomodeset" before on the boot options, replace that with "i915.modeset=1".  If that doesn't work, then reverse it to "i915.modeset=0" and see what happens.  You might also want try lubuntu or xubuntu just to see if perhaps they will install.  You could also try one of the vga= boot options.

Also, when it did install with the alternate cd, when it rebooted and then got the same screen, what happened when you pressed ctrl/alt/F1?

---

### Post by maazmahmood on 2014-01-30
Uhm, I think I might have said something confusing earlier, I've never installed it with CD before, I'm installing via USB. 
AS far as the i915.modeset=1 part, where do I type that in? Do I type it into the little Boot options line that pops up? Which brings me to something else, when I do nomodeset, and unselect it nothing seems to change in that, is that normal? Boot options ends at "initrd.lz quiet splash --" should i put the i915.modeset=1 after the "--"

COULD I install windows 7 on that machine then UNINSTALL all the nvidia drivers, then try Ubuntu?

---

### Post by Bucky Ball on 2014-01-30
Okay, confusion. 13.10 has no alternate. They don't exist anymore. 12.04 I believe did, not sure if still available.

You have the desktop (graphical) version, unless you specifically went out of your way to download the alternate. The only reason you're thinking you have the alternate is because you are not booting to a desktop I'm thinking. Mistake.

USB/Disk? Makes no difference whatsoever. They both use exactly the same ISO (it is your choice as to whether you burn it to disk or USB, there is no specific USB or disk installer).

As you were ... ;)

PS: The alternate does not have 'Try Ubuntu' on a funky purple screen. It is a text based install with NO colours, bells, whistles or disco lights.

---

### Post by maazmahmood on 2014-01-30
Ok, thanks for clearing that up :)

Again I'm sorry for all this newbie type responses/questions

---

### Post by Bucky Ball on 2014-01-31
That is absolutely fine. Just letting you know. ;)

---

### Post by squakie on 2014-01-31
Ooppsss - I didn't know there wasn't an alternative disk anymore - sorry about that, and thanks BuckyBall.  I know you were helping here originally, so how about if I back away now and let a real expert help while I watch and learn?  Thanks!  Dave

---

### Post by squakie on 2014-01-31
And OP - yes you would try the i915.modeset and the vga= options where you mentioned.

---

### Post by squakie on 2014-01-31
Hey BuckyBall - what do you think the chances are that the onboard video won't work with the current X?

---

### Post by maazmahmood on 2014-01-31
Hey what about my idea of doing windows 7 then uninstalling the drivers?

And i tried adding the i915 thing, same result

---

### Post by squakie on 2014-01-31
I don't really understand - do you want Windows 7 or do you want Linux?  Windows 7 and installing/uninstalling drivers would have no affect on Linux.  So, if you want Windows 7, go for it - you shouldn't need to uninstall any drivers there either.  If you want linux, then I at least believe that step would be a waste of time.  Remember - Linux/Ubuntu is a completley "different animal" - nothing from Windows does anything with Linux.

It's up to you what you want to do - and if you feel Windows is a better option for you that's fine.  I'm not an OS "bigot" - I beleive a person should use what they are comfortable with and works for them.  If there was such thing as a Planet Peanutbutter OS and it worked for someone, who am I to argue? ;)

Anyway, if you could perhaps clarify that thought it would help.  And I really would like BuckyBall to take this forward - I'm not the expert they are - I've just been trying to help is all. ;)

---

### Post by maazmahmood on 2014-01-31
I get that they're different, but what I was thinking was that I get into the machine as Windows, get rid of drivers THEN get Linux
And I do appreciate you helping though.

---

### Post by squakie on 2014-01-31
Um, I'm not following that.  Maybe I should also ask another question, just in case:

I don't think it's an option anymore (if it is it isn't supported anymore), but are you trying to install along side Windows - a so-called Wubi install, or are you trying a normal install?  If you do the "Try Ubuntu", exactly where does it fail?  If you are  in the install, where does it fail?  Has it asked for ANY information yet?  Has it asked you to set up your disk(s)?  Has it asked for a userid and password to use?  Those details could be important.


EDIT:  I left out some words which made for a very confusing post - sorry!!

---

### Post by maazmahmood on 2014-01-31
Oh no no, this is on an old machine, doesn't have ANYTHING, it used to have Windows, but it is removed, atleast it should be because, my flash drive is last boot order, and it hasn't booted to Windows. But it opens to a purple screen with a keyboard symbol on the bottom. I press a random key (spacebar), asks for my language. Then It has options like "Try Ubuntu w/o Installing", "Install Ubuntu" etc. That's where I hit F6 to select nomodeoptions, then it adds a line below the options with the title "Boot options" where I get this long string that ends in "--" which is where I added "i915.modeset=0"

---

### Post by squakie on 2014-01-31
Yep - that's where you enter all those different boot options.  What happens when you press the key to oontinue (I'm not looking at it but I *think* it's the esc key - it should say on the screen)?

---

### Post by squakie on 2014-01-31
And again - it this is old hardware, you really might want to try something like xubuntu.  It uses a completely different desktop manager that works better with older graphics adapters - I just don't know if it's any different in the install or not.  I have it on an ancient Dell Inspiron 8500 laptop I'm using to just junk around on, and installed it on several friends PC's lately since Windows XP support is ending.  They all like it.  Perhaps - I don't know - it would do better in the install.  I'm just afraid that your onboard graphics won't support the Unity desktop that is part of "normal" Ubuntu.  But none the less.......as long as we have come this far, we can keep going if you'd like to see if we can at least isolate the problem more.

---

### Post by maazmahmood on 2014-01-31
Yeah it's fairly old hardware. I guess I could try out xubuntu, but is it essentially the same? Like same commands and all that, because I'm taking linux class and wanted to have an actual desktop more then just virtual machine to play with.

---

### Post by squakie on 2014-01-31
Hey, I missed a rather important question - how much memory does the PC have?  Sorry I didn't ask earlier!

---

### Post by maazmahmood on 2014-01-31
Memory as in RAM? 8 GB, last I checked

So is xubuntu more or less the same?

---

### Post by Bucky Ball on 2014-01-31
> **squakie said:**
> Yep - that's where you enter all those different boot options.  What happens when you press the key to oontinue ... ?

You have not answered this. Vital. What you describe is what is supposed to happen up until when you add the option to the end of the kernel line ... then you don't tell us what happens next? When you hit return, give us the EXACT error, unless it doesn't give one, of course.

---

### Post by squakie on 2014-01-31
Thank you for coming back, Bucky Ball!!  I didn't feel like I was quaified to keep hammering at this. ;)

---

### Post by Bucky Ball on 2014-01-31
I have little clue either or I would have been posting. ;)

---

### Post by maazmahmood on 2014-01-31
There really is no error, just goes back to the black screen blinking underscore.

---

### Post by squakie on 2014-01-31
That's the only thing you see after giving the okay to the boot?  Both booting a live session and trying to install?

---

### Post by maazmahmood on 2014-01-31
Just to clarify:  what is booting a live session mean

---

### Post by squakie on 2014-01-31
If you select "Try Ubuntu" instead of "Install Ubuntu" that boots what is called a live session.  It runs off the install media (USB in your case) and doesn't do anything to your drive.  It is running linux.  Since you seem to get the hang right at the boot - nothing more appears on the screen after giving the ok to boot - then something more is wrong.

A couple of things come to mind:

- did you download the 32-bit or 64-bit version of Ubuntu (if you don't know and just let it download it will be the 32-bit version)?
- I'm wondering, since the hardware is older, if perhaps the PAE kernel versus the non-PAE kernel may be the problem.  I'd have to look to see if there are separate downloads for that yet or if it is a single download.
- just plain video hardware incompatibility, especially since it works if you use the geforce 5200 card.  I seem to remember something from a couple of years ago about doing something in the boot options for this, but I'll be danged if I can remember or locate it.  I *think* it had something to do with forcing the video to just vesa at low graphics, but again I don't remember.

- did you try one of the vga= options in the boot options?  

The below is a portion of a how-to for troubleshooting some boot problems:

>   If you have a very old machine, and the kernel hangs after saying Checking 'hlt' instruction..., then you should try the **no-hlt** boot argument, which disables this test.  
                   Some systems (especially laptops) that have a native resolution that is not a 4:3 ratio (i.e. not for example 800x600 or 1024x768) may have a blank display after the installer has been booted. In that case adding the boot parameter **vga=788**[SUP][[11]("https://help.ubuntu.com/lts/installation-guide/i386/boot-troubleshooting.html#ftn.idp3708024")][/SUP] may help. If that does not work, try adding the boot parameter **fb=false**.  


You may want to try those one at a time also.

Sorry, but there is no easy answer here.  It's going to take trial and error to try to get it to work. ;)

---

### Post by squakie on 2014-01-31
I see I didn't answer one of your earlier questions - yes, xubuntu and lubuntu are the same ubuntu kernel.  They run different desktop managers (xfce *I think* and ldxe *I think* respectively), instead of the "heavier" Unity desktop that standard Ubuntu has.  If you are working from the command line, everything would be the same.  If you are working on things from a GUI standpoint, there are some differences in which packages are actually installed to better "fit" the particular version - the editor might be different, the package manager might be different, etc..  As far as I know, though, you can install anything "normal" ubuntu has to either xubuntu or lubuntu so things are the same except for the desktop.  Of course, this may take away some of the "lightness" of these versions of Ubuntu.

---

### Post by Bucky Ball on 2014-01-31
There is no alternate install anymore, but there is the minimal install. That is text-based and might get you somewhere different. (Server version also text based, but pulls in a lot of things you don't want.)

[https://duckduckgo.com/?q=minimal+install+ubuntu](https://duckduckgo.com/?q=minimal+install+ubuntu)

We can guide you through that. Download ISO, use disk or USB to burn to and boot, then see how it goes.

---

### Post by squakie on 2014-01-31
Sorry, didn't know about that either!  Glad you're catching my screw-ups!  ;)

---

### Post by maazmahmood on 2014-01-31
Ok, wait, I'll look into these suggestions BUT before I do that. when I hit F6, then go to nomodset, nothing in bootoptions change. Should I manually insert "nomodeset=1"

I just realized something, opened up the computer to check the RAM, and it's 2 different sets of sticks. They're all 2 GB each, but one set of 2 is different manufacturer then another set of two, AND they operate at a lower clock then the other. Should I downgrade to 32-bit Ubuntu, as I've been doing 64?

And as far as addding vga=788, and fb=false etc., what do I do to make space between them, just like a semicolon or underscore?

---

### Post by Bucky Ball on 2014-01-31
Better idea. Take out one stick and test. If it fails, take it out and put the other one in. Test. It is about the processor, not the RAM. You might have mentioned what the CPU is, but refresh our memories. Is it a dual-core?

Also, try one stick in different slots. One slot can sometimes die (which is exactly the case on my desktop) which has a 1Gb stick in each of the other slots, if that makes sense. If that happens, the results might be unpredicatble.

---

### Post by maazmahmood on 2014-01-31
[COLOR=#333333][FONT=Arial]This is the exact copy from gateways website
Intel® Core&#8482;2 Quad Q6600 quad core processor with VT[/FONT][/COLOR]
[LIST]
[*]Each core operates at 2.40 GHz
[*]2 × 4MB L2 cache
[*]1066 MHz front side bus
[/LIST]

---

### Post by squakie on 2014-01-31
Lets do 1 thing at a time so while we are troubleshooting, so please do the individual memory tests as Bucky Ball recommended.  Once we know the outcome of those we can move on.  One thing I don't know that perhaps Bucky Ball can help on - I don't know if the Core 2 line and associated motherboard still required memory sticks to be in pairs.  That may change the testing procedures.

Once we know the results of that it will determine what we try next.  All the boot options, etc., can wait until we know the state of the hardware.  Given that it did boot up okay with the geforce 5200 I would think the hardware is ok, but lets be sure before we continue on to other things.

---

### Post by maazmahmood on 2014-02-01
What if I uploaded a video of what's exactly going on? Like when I select nomodeset, and all that?

---

### Post by squakie on 2014-02-01
You would probably have to post that to one of the free film/picture hosting places and then post a link.  We do understand if you just have a screen with a blinking cursor - we just want to be sure you put in the boot option, tell it to boot and then tell us each step afterward.  If it immediately goes to the screen with the blinking underscore, and never comes up with another screen, we need to know that.  

I still suspect your onboard video is having problems either physically or a driver nad/or X problem.

So, please, let us know the following before we go any further:

- every step you take from the moment the "Try UBUNTU" screen shows
- the results of the memory testing

---

### Post by maazmahmood on 2014-02-02
I hit F6 as soon as "try Ubuntu" screen shows  up, select nomodeset, then select Install Ubuntu, it like pauses for a bit (possibly because hardware slow) then it goes to the black screen with blinking underscore, EXACT same thing if I select Try without installing

Memory tested: no different result.

---

### Post by squakie on 2014-02-02
Then I would seriously suggest using unetbootin or one of the other tools to download and install the ISO for xubuntu or lubuntu to your flash stick and try that.  For now just try going through the "Try Ubuntu", don't try to install.

If it does come up, go to terminal (it will be in the menus of which ever you choose), then type the following:

lspci | grep VGA <press enter>

If you can get your networking going in the "Try Ubuntu" option (a live session), then just copy and paste the output back to a reply here.  If not, write down the output, then post it back here in whatever way you can.  *Hopefully* this will allow us to see what the onboard graphics are and go from there.  Also, if you still have the geforce 5200 be sure to just remove it from the motherboard entriely - this will be sure we are dealing with just the onboard GPU.

---

### Post by westie457 on 2014-02-02
> **maazmahmood said:**
> I hit F6 as soon as "try Ubuntu" screen shows  up, select nomodeset, then select Install Ubuntu, it like pauses for a bit (possibly because hardware slow) then it goes to the black screen with blinking underscore, EXACT same thing if I select Try without installing

Memory tested: no different result.

When you say 'select nomodeset' are you hitting the Spacebar to put a check mark in the box?

Have not read all the thread so apologies to all if this has already been covered.

Is your graphics chip Intel base with AMD/Nvidia overlay?

---

### Post by squakie on 2014-02-02
Westie457, thanks for helping out!  I forgot to ask if they had made sure the option was checked and went through the boot.  The video is what we are trying to identify but can't even get far enough to be able to tell what it is.  Have suggested some othe options as well, such as VGA=788 to see if it can get the video working.  Right now they can't even get a live session running.  Any help here is greatly appreciated!

dave

EDIT:  I think I forgot to mention to the OP:  it can sit at that screen for quite a while depending on the hardware.  I would think that if you have let it sit for 10 minutes or more that is way more than enough.

---

### Post by maazmahmood on 2014-02-02
Ok, i'm downloading xubuntu (32-bit version), right now. However I'd like to state I tried booting to Windows 7 (just to see what happens), and same problem when it gets to "starting windows" screen, it freezes, no spinning balls making Microsoft logo. Not trying to get WIN 7 but still. 

@Westie457 That's a great question, I'm pretty sure I hit space bar to select **Update** I hit both enter and spacebar, both select it the same way. But I'd also like to add again that when I do select "nomodeset" then the boot options line pops up but there is nothing about nomodeset on there, do I have to add nomodeset manually?

@squakie I type VGA=788 in the boot options right? that little string that shows up. Well I tried that as well. Seems to have no effect as it just goes to black screen blinking underscore

I'd also like to add one thing for the record, occasionally if I don't hit a key when the keyboard symbol shows up (purple screen) if I don't hit it fast enough then it freezes and computer makes beeping noises when i do hit a key. Not sure if that's related but just throwing it out there

Tried booting xubuntu, exact same thing. I tried the "Try xubuntu" with nomodeset, then black screen blinking underscore.

---

### Post by squakie on 2014-02-02
If you're having si,ilar problems with Windows also, I would suspect a hardware problem.  Since you didn't have this problem with the nVidia GeForce 5200 installed, it leads me to believe it's the video adapter on the motherboard.  I have forgotten now, but did you have any OS running on this system prior to now with only the onboard graphics, and was it working?

I suspect the onboard video isn't "good" enough for the demands of Win 7 or for "normal" ubuntu.  Let us know what happens with xubuntu.

---

### Post by westie457 on 2014-02-02
Question 2 in the silly questions department.
The Nvidia card, is it fitted to a slot on the motherboard and have you plugged the monitor into this card?

Now the background; Many years ago I bought a computer off e-bay with a S3 graphics chip built in, the performance was adequate on Windows 98 however on XP it was poor/terrible. Bought a cheap card to help improve things,got it fitted very easily. Turned the computer on and nothing  on the screen after the BIOS. Scratched head and said some unkind things reseated the card several times still nothing. Finally the penny dropped with a resounding clang. I had plugged the screen into the onboard VGA port, moved to the new card and everything worked.

---

### Post by squakie on 2014-02-03
To follow a slightly different angle on that:


I never asked before - you have physically removed the nvidia card from the system, correct?  I mean the card is  not physically in the system.

---

### Post by squakie on 2014-02-04
I've been thinking about this problem more, and I have to say that if:
- the nvidia card is physically removed from the system
- the different boot options didn't help
- you've tried xubuntu and/or lubuntu with no difference

Then I'm pretty much out of ideas.  It seems weird to me that it does show text - it's just when it tries to go graphical the it hangs, so that's what makes me think it's an incompatibility - either in X or with the lack of a driver (although I would have thought it would default to the VESA driver and just give you low colors and lousy resolution).  That is where I'm out of ideas.  I know no other way to find out what that on-board GPU is.  If you have the nvidia card in the system and set the BIOS to allow booting with it, I don't think it will ever see the o-board GPU so I don't think we'd be able to tell there either.

The only other things I can think of:
- get the full model number for the PC and we can look on the manufacturers site to see if it says what the default GPU is
- perhaps, check the POST screens as the hardware initializes - you can press the pause key at any point so you can check what you see and any key will resume.  I would *think* it would tell the GPU it detected in the POST report.

---

### Post by maazmahmood on 2014-02-04
Sorry been at school/work. Yes the card is plugged in, and no the monitor is plugged into the VGA port in onboard graphics. Now the nvidia graphics card is tied down with a zip tie (long story) so I can remove it if necessary but prefer not to, would it be enough if I unplugged power from the card?

---

### Post by westie457 on 2014-02-04
Gently pulling the power lead out of the card might be enough. If not, that zip tie will have to come off.
The other option is to plug the monitor into the Nvidia card.
Your choice. Let us know how it goes.

---

### Post by maazmahmood on 2014-02-05
Yeah, that stuff didn't work. although there is one more thing. When I don't select nomodeset from other options. And I hit "Try ubuntu/Install Ubuntu" and when it goes to black screen blinking underscore, THEN I try Ctrl+alt+F1, the screen becomes like a higher resolution, don't know if that means anything

Well all of a sudden when I try to turn on the computer, it gives 3 beeps, and fan become VERY loud, happened out of no where. Going to look into that.

Real quick what are PC minimum requirements for Ubuntu?

Well I just tried installing on an even older computer (xubuntu), works fine. This computer is so old it's louder then a train :D. I guess I'll play around with ubuntu on here for now, till I can see what's wrong with the semi old computer. Thank you all for your help, I know it was pretty frustrating from your guys' end. 

And btw westie457, that's an awesome monkey :)

---

### Post by maazmahmood on 2014-02-05
Ok last post was getting too long, so I decided to add more here, I tried again on old computer, and the way I got it to work, was literally do NOTHING, when keyboard icon comes up, or anything, just sit there. 

However, no I get this window when I have to select my time zone, it says: Installer Crashed. We're sorry; the installer crashed. After you close this window we'll allow you to file a bug report using the integrated bug reporting tool. This will gather information about your system and your installation process. The details will be sent to our bug tracker and a developer will attend to the problem as soon as possible.

and when i hit Ctrl+alt+F1, then type in sudo service lightdm start, it's just a black screen, then when i hit ctrl+alt+f1 again, it takes me back to command line and says "start: job failed to start"

---

### Post by squakie on 2014-02-10
This thread has gotten so long that I have forgotten if some things were already answered, so........

- can you give the exact name and model of the PC in question so we can look up it's specs?

- how old are we talking about here - 5 years, 10 years, more??

- if I remember correctly, you CAN boot with the add-in nVidia card, right?  Right now that is going to be your best bet until we know the exact details on the PC.  Just "emachines" or whatever isn't enough - we need a model number.

- when you use only only the intergrated GPU, and the nVidia card is physically removed from the system, does your BIOS happen to have a video memory setting?  *if* so, perhaps it is set to some really tiny size.

Other than that, I'm out of ideas.  This is one of those "if I had the box in front of me...." sort of things for me.

---

### Post by maazmahmood on 2014-02-10
Actually got it fixed, thanks though :)

---

### Post by Bucky Ball on 2014-02-11
> **maazmahmood said:**
> Actually got it fixed, thanks though :)

It is forum etiquette to let us know how you got it fixed and mark the thread as solved to help others.

Please share your solution and mark the thread as solved. Thanks.

---

### Post by squakie on 2014-02-11
> **Bucky Ball said:**
> It is forum etiquette to let us know how you got it fixed and mark the thread as solved to help others.

Please share your solution and mark the thread as solved. Thanks.

I tried hard to help here but I must have been being stupid again.  Oh well.  Maybe I'll try again sometime on something really simple.

---

