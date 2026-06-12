---
title: "A Few Little Issues"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by CyanideSun666 on 2008-08-23
Hello everyone :)

I have used Windows for about 10 years, and up until two days ago, I used Vista Ultimate.I never had a single problem as far as Vista goes with this PC.It rarely if ever crashed, and did everything I needed.But something about Ubuntu was pretty attractive.

Having tried it, I am, for the most part, extremely satisfied.If I can work out a few nagging problems, I really don't think I will be going back to Windows.Forgive me if any of these have been covered before, but I haven't found through the search, anything exactly like what I am having issues with.I have worked out my flash audio and ati agp card issues...

My biggest issue now is, sound stutters.I have searched and found a lot of stuff about different problems similar...But nothing has worked yet.My sound is fine as long as I am just listening to music, or watching a movie.But the moment I open something, stutter, the moment I load a page in firefox, stutter(which seems REALLY weird...).Move a window, stutter.My computer, ran Vista flawless, everything maxed out, very, very fast and smooth unless I got to doing a LOT at once, then it would bog down.But it seems to stutter a lot, and is a little rocky with Ubuntu.Run's noticeably slower than Vista as well, all around.I'm sure it's probably drivers or something...

Specs if it helps...
2.4 GHz AMD Processor
2GB RAM
320 GB hard drive
ATI HD2400 AGP card (Finally got the driver issues worked out with it..I think)
Realtek AC'97 Soundcard (Cannot seem to figure out how to use it...Maybe thats why the sound stutters massively.But I do not understand why loading a webpage, consistantly, any page, makes the sound stutter or totally stop for a few seconds)

Anyway, I'm a total noob with Ubuntu, and as I said, I am sorry if something like this has been covered.I have tried many solutions for issues "similar" to mine, but none so far, have worked to fix the problem

Thanks in advance for any help at all you can offer!

---

### Post by elmoosecapitan on 2008-08-23
Does this only happen when you are listening to music, or watching a video online? What is original source of your audio?

---

### Post by elmoosecapitan on 2008-08-23
Sorry, I misread a line. Does this also happen when you are watching something on firefox? What audio/video programs are you using?

---

### Post by CyanideSun666 on 2008-08-23
It happens when I am listening to music.It always smooths back out, but it's pretty annoying, not being able to do anything with music going for fear of stutters.My install of Ubuntu is clean, I haven't installed anything save for making flash player work in Firefox, and my video card drivers.

I haven't tried streaming much from the internet until now, but streaming audio, it seems to do the same.In sound preferences (which is the only place I know to look, forgive me if it is not right) Everything is set to ALSA, and the device is VIA 8237 (ALSA mixer)

I don't see my card there at all, in any options, but being fresh from Windows, I am not sure how to do everything in Linux yet, still reading up on it all =)

EDIT: I am using Rythymbox for audio, I just tried Amarok and it seems to do the same.For video, just the default Video player.And watching something on firefox seems to work fine.It stutters a bit but I'm not so sure thats not my internet speed.But for music, it stutters even when playing from my computer, not streaming

---

### Post by CyanideSun666 on 2008-08-24
One other thing I have noticed today, when the sound stutters, the mouse cursor does as well...and I hadn't played the games that come with it yet while listening to music, but I was a bit ago, and moving the solitaire window, caused the sound to stutter.The window stuttered as far as movement goes, the cursor stuttered, and when the sound came back smooth, everything moved again.And of course loading any website, causes EVERYTHING, sound and video included, to stutter.(Didn't have a chance to try so many things at once last night, I was really busy)Thanks again for any help :)

Edit: Looking further, when this happens, when the sound or video stutters and the computer more or less freezes, I noticed the track itself, does not stop playing.Say the sound stops for 10 seconds,or off and on, the track time and bar progress, then the sound goes wild, trying to catch up to the point in the track it is at.with video it's the same.

---

### Post by unutbu on 2008-08-24
I can't promise any of these suggestions will work, but they might be worth trying:

[list=1]
[*]
Try installing the linux-rt package. This package will install the latest rt Linux kernel available. "rt" stands for real time and is supposedly better at dealing with processes whose commands need to be executed at a given time. See [http://rt.wiki.kernel.org/index.php/Frequently_Asked_Questions#What_is_real-time.3F](http://rt.wiki.kernel.org/index.php/Frequently_Asked_Questions#What_is_real-time.3F) .

The option to boot the rt kernel will be added to your GRUB boot menu. Reboot into the rt kernel and see if that helps.

[*]Try running rhythmbox with a higher priority:
```

nice -n -20 rhythmbox
```

You can try this with or without installing the rt kernel, but it may not be as effective a solution as using an rt kernel. See [http://ubuntuforums.org/showthread.php?t=896721&highlight=nice](http://ubuntuforums.org/showthread.php?t=896721&highlight=nice)

[*]If the stuttering of the audio is affected by moving the mouse, there may be an IRQ conflict. It may (or may not) help to boot with a kernel option like "irqpoll".
See [http://ubuntuforums.org/showpost.php?p=5586563&postcount=4](http://ubuntuforums.org/showpost.php?p=5586563&postcount=4) for instructions on how to boot with a kernel option.
[*]If none of the above work, please post
```
lspci -nnvv           # Tells us about your hardware. 
cat /proc/interrupts  # Tells us what hardware is handled by what IRQ 
```
The output may help with google searches for a solution.
[/list]

---

### Post by CyanideSun666 on 2008-08-24
I haven't had a chance to try that yet since I have been at work, but will here in a bit thank you =) But, one thing I have noticed...Just out of curiousity I tried to remove my ati card and install Ubuntu with onboard.Though the video is terrible, the sound doesn't seem to be skipping...Reinstalled with the ati card, the eye candy and all that works, but the sound stutters like mad when loading a page, opening a new program, even if i turn the eye candy off.

If it is indeed related to this ati card, would an nvidia agp card be better?I don't have PCI-E as an option, and I understand that old PCI, is not good at all?I don't mind replacing the video card, but I have been reading...LOTS of problems with ati cards, and though nvida are not open sourced, it seems they work easier, much better...Anyway, whether or not the problem here is my card, what agp cards are the best all around for Ubuntu?I don't game...But I would like the desktop to have the options all turned on XD

I'll try your suggestions though and get back when I can, thanks again!!

---

### Post by CyanideSun666 on 2008-08-25
Thanks for the suggestions and help =) I tried what was suggested, couldn't really get it to work for me.After a couple of days total now with this problem, narrowing down what it might be, bit by bit, it seemed the biggest cause, was loading anything in Firefox.It didn't matter what the webpage was, it always caused a stutter.Just to take a chance, I tried to install Opera instead.Problem seems to be gone as long as I use Opera and not Firefox.

I'm a bit confused as to why under Vista, my PC ran very fast and smooth, and I used Firefox, but in Ubuntu, Firefox seems to have rendered my sound useless, and it completely locked up Ubuntu each time I loaded a page, until the page loaded all the way, and even then it stuttered a lot as I scrolled.I don't remember doing anything to Firefox, and I tried several clean installs, but I am sure it is probably something I did.I'll keep trying to figure out what it might have been.

Linux is definately good, in my opinion now.I started to get really frustrated, but working with it, I learned a lot, and I feel much more satisfied accomplishing that than I ever did in Windows.I guess you just have to forget everything you know when you get into Linux for the first time :D

---

### Post by aloshbennett on 2008-08-25
Do you have any plugins installed on firefox?
When you face this problem, could you try a 'top' from the terminal?
Sort by processor time (Shift + P) and do you see npviewer.bin somewhere high up hogging a lot of processor?

---

### Post by pi.boy.travis on 2008-08-25
Opera is my browser of choice. . . But your Fx sound problem is intriguing. . .Do you have all updates installed from the default repositories?  You could also try proposed or backported updates.  Check out the updates tap in System-Administration-Sofwtare Sources.

---

### Post by unutbu on 2008-08-25
Does this sound like your problem:
[https://bugs.launchpad.net/gst-plugins-good/+bug/190754](https://bugs.launchpad.net/gst-plugins-good/+bug/190754)
?

If so, the thread contains are a few reports of fixes, maybe one of them would work for you.

---

### Post by CyanideSun666 on 2008-08-26
First, thanks everyone, for all the input and suggestions, sorry for not posting back as I tested the things you all suggested.I read all through [https://bugs.launchpad.net/gst-plugins-good/+bug/190754](https://bugs.launchpad.net/gst-plugins-good/+bug/190754) and though not a single thing listed there, helped, I decided to give it one last go using what I learned there.So just in case someone else has a problem, I'll post what worked for me.

I had tried so many things I couldn't even remember anymore, so I started fresh again, I hadn't even installed updates, I wanted to go one step at a time and keep track.So...Reading that thread posted here, I saw pretty much it seems to be a pulse audio thing, which I gathered from other things I had read before earlier today.Someone mentioned changing Amarok to use only alsa, instead of autodetect.Since I use Amarok now, I tried that, it told me it couldn't detect any sound hardware.So I put it back to autodetect, and the sound was back.

I downloaded linux drivers for my realtek ac97 card,and installed them.Then I restarted, and opened System > Preferences > Sound.I put everything on alsa, and went back to Amarok.I switched it to alsa, not autodetect.This time, sound still worked...And so far, an hour later, I think it has stuttered maybe once when I purposefully tried to load the pc hard.When before it was stuttering several times a minute, even when the system idled.(Well, Firefox would be open, but even so much as typing this would cause a stutter in sound, and the system would freeze)Doesn't seem to do it now, hopefully it stays this way :lolflag:

Firefox still stutters/freezes sometimes, even when I just type, with no music playing.Even the mouse cursor movement is slow and hard to control when it does this.But Opera doesn't do that, and I like Opera anyway, so I can live without Firefox.Though I am absolutely puzzled how even typing into a forum in Firefox, can cause the system to become all but useless until I wait a few seconds for it to calm down.And it repeats.But oh well, the sound has stopped stuttering it seems, and thats all I really was annoyed with.Thanks again!

---

### Post by CyanideSun666 on 2008-09-08
Okay, I reinstalled Ubuntu after installing a new hard drive so I would have more space...I have tried to get past this again, like before, but I can't seem to.So rather than make a new thread, I am just reviving this old one since it's pretty much the same problem.

If I am doing nothing, just listening to music, the computer is fine.It responds fast if I bring up a program, chat in MSN, etc.But when I go to browse the web, in ANY browser, the cpu use skyrockets, everything stutters and the computer comes to a complete and total crawl.Once a page has loaded, which takes quite some time, it is ok, unless I try to type.basically if I do ANYTHING in any browser, the cpu is pegged, everything stutters.The most noticeable is if I am listening to music, but even without, the cursor stutters, window movement, typing, I can type almost a whole paragraph before even the first letter will show on screen.If I try to scroll down, the page scrolls very slowly, also in any browser, anything flash, I might as well give up on...I can almost deal with the sound stuttering, even though that sucks, but a web browser rendering the computer useless, is kind of a problem :P

I have tried solutions from before, and all posted here so far, (even searched the forums for similar issues)but nothing works so far.I appreciate any help, again in advance :)

---

### Post by BenAshton24 on 2008-09-08
Heres an idea Try this. in terminal type:
> sudo asoundconf list
you should see a list of sound cards, one of them will probably say Realtek or Intel or something like that, whichever sound card you think is the one you use. once you know the name type:
> sudo asoundconf set-default-card NameOfCard
obviousley replacing nameofcard with whatever your sound card is called.

Just a thought, it might work :P

hope this helps, Ben :D

---

### Post by whitethorn on 2008-09-08
I also had sound stutters, I don't remember if all the symptoms I had were the same it was a while ago.  This is what worked for me

```
sudo /etc/init.d/alsa-utils reset
```

---

### Post by unutbu on 2008-09-08
Since all aspects of your machine start to slow down once you start firefox (or any browser!) and you don't have to point to a webpage with sound in order to elicit the problem, I'm going to assume the fundamental problem does not have to do with sound.

Perhaps try
```

strace firefox > output.txt 2>&1
```

This will dump all system calls and signals generated by firefox into a file called output.txt

Allow firefox to run only long enough to make the machine start to stutter. 
The shorter the better, since a long output.txt will only make it harder to find the problem. 

Quit firefox. The strace will then end.
```

bzip2 output.txt      # bzip2 compresses the file

```
Please post output.txt.bz2 as an attachment. I'm not sure I can find what the problem is, but this might be a start.

---

### Post by CyanideSun666 on 2008-09-09
unutbu : Where will it put this txt file so I can post it?

I think you are right, though I appreciate the other responses as well!(I tried the suggestions in them, but no luck.)Because I can be multitasking with anything else, I can play music, sort photos, watch movies, type in Openoffice, emails, play games etc., and it doesn't miss a beat.Nothing stutters, all is well even with the desktop effects on full.The computer is fast and highly responsive.But man when I have a browser open and am trying to do anything in it...

When I open Firefox, and load a page, xorg and firefox share the cpu.Neither uses 100% alone, but they both skyrocket and use 100% between them when loading ANY page.I searched more and using different terms over the last days, and am still working on trying all the solutions I have found, but so far none have worked completely.Though the one that made the most difference, was using a different version of Flash.I found a thread where the guy had a similar problem, but his was almost fully related to the flash plugin.

Opera seems to be the most stable as it was the last time I had this problem, it uses MUCH less cpu than Firefox.But last time I got around this problem just using Opera.This time Opera still does it.Nowhere near as noticeable, but it's still there.Since tweaking with the Flash player made quite a noticeable impact, and fully disabling flash/java almost completely rid me of the problem, I am guessing it's probably related to that in some way?

On another note even if flash is not my problem, with flash as it was, and fully enabled, every webpage would cause this problem.Some far less than others, but all would do it.I am kinda ignorant about such things but want to learn, do all or most pages use some form of flash?

---

### Post by unutbu on 2008-09-09
If you open a terminal and type the commands, the output will be in the top level of your home directory. Look for output.txt.bz2.

---

### Post by CyanideSun666 on 2008-09-09
Here it is =) As I said it's not as noticeable after what I have done, but it froze some there.Not sure if it will help or not.Thanks again!

---

### Post by unutbu on 2008-09-09
Although the strace clearly shows something is wrong, it is not clear to me what needs to be done to fix it. I think it important to warn you that there is a very low chance that I know enough to help you fix this problem.

Your best bet may be to file a bug report at [https://bugs.launchpad.net/bugs/](https://bugs.launchpad.net/bugs/)

What follows are my half-baked ideas. 

In output.txt.bz2, this error was repeated 28462 times:
```
gettimeofday({1220993709, 518412}, NULL) = 0
```

Why is firefox calling gettimeofday so many times? 
[list]
[*]When I ran strace on my firefox, it did not seem to call gettimeofday at all. (I'm using firefox ver. 2.0.0.6 on Gutsy.)
[*]Lots of people are running firefox-3 and not experiencing stuttering, and you are running off a fresh installation, with no extensions, no java, no flash and I assume no compiz. You've given no indications there were any errors during installation, so it seems to me your problem must be hardware-configuration related. So the natural question seems to be, what piece of hardware is involved with gettimeofday? The CPU? the BIOS? 
[*]Maybe you need to boot your kernel with a special boot option. *Maybe* one having to do with clocksource. Perhaps post the output of 
```

sudo cat /sys/devices/system/clocksource/clocksource0/available_clocksource
```
Given the output I can tell you how to boot with a few different temporary boot options. (It's a safe thing to try.) Then you can test if any of them alleviate the problem. I got to warn you though, if it works I'll fall out of my chair.
[*]I wonder if your problem is the same as the one described in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/227185](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/227185)
[/list]

This was also repeated 7442 times:
```
read(3, 0x807532c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
```
I googled around and found people reporting doing strace on firefox and also finding this error. I wasn't able to locate a solution, however.

There were 1766 "(No such file or directory)" errors. It's too much output to list here, but you can type
```

bzgrep '(No such file or directory)' output-cyanide.txt.bz2 | less
```

to see the missing files it was looking for. (Full disclosure: I believe my firefox works fine, though I got 27 of these errors too.)

You might want to try other browsers to see if you can simply avoid the problem. Perhaps try firefox-2, galeon, epiphany-browser.

---

### Post by CyanideSun666 on 2008-09-10
Here is the output of that command :) 

```
tsc acpi_pm pit jiffies 
```

I'll look through that bug report now, and see about making my own I suppose :) I have also noticed, that the longer the pc is on (today was the longest I have ran it constant with Ubuntu) The problem gets worse and worse.After it was up for about 4 hours, it would freeze rock solid, and only a hard restart would get out of it...

The install is still clean, aside from Opera and the updates, and my personal documents and pictures, I have not installed anything.No extensions, no programs, nothing.I went ahead and updated before fixing it, as it does it with, or without updates.

Oh and I will try Firefox 2 and the others, and post back.Thanks again!

EDIT: I tried Firefox-2, and the others you listed, and they did the same thing, although not as much.The latest version of Firefox is by far the worst of all the browsers, followed closely by Firefox 2 but they all do it to one degree or another, Opera doing it the least (that I can tell) I can live with it, using Opera, but it sure does drive me a bit crazy...XD

---

### Post by unutbu on 2008-09-10
Here are general instructions on how to boot with a kernel option: [http://ubuntuforums.org/showpost.php?p=5586563&postcount=4](http://ubuntuforums.org/showpost.php?p=5586563&postcount=4). Try doing it the temporary way. That way, if it works, then great, but if it doesn't, your system will be in no way affected after you reboot.

Try, one at a time, booting with one of these kernel options:
```

clocksource=acpi_pm
clocksource=pit
clocksource=jiffies
notsc
```

After booting with one of these alternate clocksources, test if there is no more stutter while browsing. If there is, reboot and try another.

---

### Post by CyanideSun666 on 2008-09-10
Edit: Nevermind I am stupid, testing more and I'll post back with results XD

---

### Post by CyanideSun666 on 2008-09-10
Well, as you thought, that didn't seem to do anything for the problem, but thanks again for the help :)

---

### Post by CyanideSun666 on 2008-09-15
Just bumping to see if maybe anyone else has an idea as this is still a really nagging problem XD

---

### Post by unutbu on 2008-09-16
Have you tried this?
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

I know we have been thinking that the problem is not just audio-related, but since this post seems to have helped an enormous number of people, I thought I'd pass it along.

---

### Post by kpmoore on 2008-10-15
I know this thread is a month old, but I had the exact same problem. Did some research and realized that killing pulseaudio fixed it.

```
pulseaudio -k
```

Hope that helps.

---

