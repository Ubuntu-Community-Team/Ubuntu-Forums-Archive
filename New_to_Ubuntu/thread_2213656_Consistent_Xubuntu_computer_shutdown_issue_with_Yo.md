---
title: "Consistent Xubuntu computer shutdown issue with Youtube"
date: 2014-03-27
forum: New to Ubuntu
---

### Post by Chessgeek2900 on 2014-03-27
Greetings,

I am brand new to Linux, as in I just downloaded Xubuntu maybe three days ago and actually got it installed two days ago (after a bit of trial and error--the computer I used to download it is a slow 10+ year old Windows XP machine.)  After doing the basic software updates through the updater included with the system (including the preconfigured updates) I decided to test the computer's ability to handle videos.  Interestingly enough, under Linux this machine plays videos on Youtube at a higher quality--but it also shut itself down at (seemingly) random intervals.  I tried testing this in both Firefox and Seamonkey (Firefox's open-source cousin, which I am more familiar with) and had the same results in both.  Last night, I finally decided to try not running videos in full-screen mode--and went for about 3 hours with some of the highest quality video I have ever seen on Youtube (at least as good as my newer Windows 7 machine showed, which is significantly better than this computer has ever done before!) and no shutdowns.  
However, when I changed to full screen mode, the computer shut itself down during the second or third video.  Thinking back, the previous seemingly random shutdowns all occurred on the second, third, or fourth full-screen video I watched on Youtube, never on the smaller version.

Now for my questions: 

1) Might these shutdowns be caused by the computer using all of its memory to run the full-screen video?  If not, what else might it be?

2) Is there some way to defragment the memory in Linux, or perhaps limit the maximum amount to be used by a single application?


Any help here would be greatly appreciated.

Chessgeek2900

---

### Post by pqwoerituytrueiwoq on 2014-03-27
1. No it is not a ram issue
2. ext4 partitions don't need defraging like ntfs do

I suspect this is a cooling issue, flash is hell on the CPU in linux (try using [html5]("http://youtube.com/html5")), that old cpu is probably running as hard as it would be if you were running prime95 (CPU stress test) on windows
1. clean out dust bunnies
2. if you still have issues upgrade your [cooling solution]("http://www.newegg.com/Product/Productcompare.aspx?Submit=ENE&N=100008000%2050001333%2050002107%2050002177&IsNodeId=1&page=3&bop=And&CompareItemList=574|35-200-056^35-200-056-TS%2C35-103-075^35-103-075-TS%2C35-186-134^35-186-134-TS%2C35-103-064^35-103-064-TS&percm=35-103-064%3A%24%24%24%24%24%24%24"), be sure to check socket compatibility and clearance, you may be able to get by with modding a [side fan]("http://www.newegg.com/Product/Productcompare.aspx?Submit=ENE&N=-1&IsNodeId=1&Description=rosewill%20120mm%20red&bop=And&CompareItemList=-1|35-103-090^35-103-090-TS%2C35-103-060^35-103-060-TS%2C35-103-091^35-103-091-TS%2C35-103-061^35-103-061-TS%2C35-200-021^35-200-021-TS&percm=35-200-021%3A%24%24%24%24%24%24%24") onto your case

---

### Post by whatthefunk on 2014-03-27
Yes, I suspect cooling too.  Install the package lm-sensors.  This is a terminal program so youre going to have to open a terminal to continue.  In the terminal, type:
```
sudo sensors-detect
```

Answer yes to all the questions.  Once it is finished, to see the temperature of your system you can type:
```
sensors
```

Run a video or two, run "sensors" and post the output of that here.

---

### Post by Chessgeek2900 on 2014-03-27
Good evening.

Where the cooling fan is concerned, perhaps I should have specified this is a laptop with a history of overheating issues (and thus I have a USB-powered fan my mother gave me as a gift.)  Strangely enough, the computer did not feel warm when it shut down.  I have, however, now enabled html5, and will go try another extended run on Youtube to see if it makes a difference.

As for the package lm-sensors, where would I find it?  The closest thing I could find in the Ubuntu software center was Psensors, which seems to be little more than a graphical interface for something more which I do not have.

Thanks for the help, and I'll check back probably in the morning.


Chessgeek2900


EDIT:  I just followed the directions for checking the sensors.  The results are below.

```

 avalon@avalon-Satellite-A75:~$ sudo sensors-detect
[sudo] password for avalon: 
# sensors-detect revision 6085 (2012-10-30 18:18:45 +0100)
# System: TOSHIBA Satellite A75 [PSA70U-003002] (laptop)
# Board: TOSHIBA EDW10

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     Yes
Found `SMSC LPC47N217 Super IO'                             
    (no hardware monitoring capabilities)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc ATI SMBus
Module i2c-dev loaded successfully.

Next adapter: Radeon i2c bit bus DVI_DDC (i2c-0)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: Radeon i2c bit bus VGA_DDC (i2c-1)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: Radeon i2c bit bus MONID (i2c-2)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: Radeon i2c bit bus LCD (i2c-3)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: SMBus PIIX4 adapter at 8060 (i2c-4)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS.
avalon@avalon-Satellite-A75:~$ 



```

---

### Post by monkeybrain20122 on 2014-03-28
> **pqwoerituytrueiwoq said:**
> 1. No it is not a ram issue
2. ext4 partitions don't need defraging like ntfs do

I suspect this is a cooling issue, flash is hell on the CPU in linux (try using [html5]("http://youtube.com/html5")), that old cpu is probably running as hard as it would be if you were running prime95 (CPU stress test) on windows
1. clean out dust bunnies
2. if you still have issues upgrade your [cooling solution]("http://www.newegg.com/Product/Productcompare.aspx?Submit=ENE&N=100008000%2050001333%2050002107%2050002177&IsNodeId=1&page=3&bop=And&CompareItemList=574|35-200-056^35-200-056-TS%2C35-103-075^35-103-075-TS%2C35-186-134^35-186-134-TS%2C35-103-064^35-103-064-TS&percm=35-103-064%3A%24%24%24%24%24%24%24"), be sure to check socket compatibility and clearance, you may be able to get by with modding a [side fan]("http://www.newegg.com/Product/Productcompare.aspx?Submit=ENE&N=-1&IsNodeId=1&Description=rosewill%20120mm%20red&bop=And&CompareItemList=-1|35-103-090^35-103-090-TS%2C35-103-060^35-103-060-TS%2C35-103-091^35-103-091-TS%2C35-103-061^35-103-061-TS%2C35-200-021^35-200-021-TS&percm=35-200-021%3A%24%24%24%24%24%24%24") onto your case

I doubt that html5 would be easier on cpu usage, at least it doesn't seem that way on my machines. flash actually performs a lot better on Youtube because gpu acceleration works on those machines,--but tends to crash on other sites if gpu acceleration is enabled. 

Previously I set up lubuntu on a 10 year old XP machine, the optimal solution was Viewtube, a greasemonkey script that plays flash videos with mplayer (need to install gecko-mediaplayer from repo) or totem on popular flash streaming sites such as Youtube, Vimeo, dailymotion etc
[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

P.S. flash is problematic even on Windows. :)

---

### Post by pqwoerituytrueiwoq on 2014-03-28
> **monkeybrain20122 said:**
> P.S. flash is problematic even on Windows. :)been a while since i used windows, but i don't recall it eating my cpu link it does on linux, figure it has better hardware acceleration support, long story short flash sucks and needs to perish, if you can get the video to play in mplayer DO IT
i attached a script i use to do that, it works on most sites, i have a launcher in my top xfce4-panel for it, i start a flash video and hit pause then click my launcher once it has buffered enough

---

### Post by whatthefunk on 2014-03-28
So, it looks like the program didnt find any sensors, but lets check again.  In a terminal, type:
```
sensors
```

Paste the output here.

What kind of laptop is it?  Can you hear the fans running or feel any air coming out of the vents when its on?

---

### Post by Chessgeek2900 on 2014-03-28
Good morning.

Here is the result of typing 'sensors' directly into the terminal:

```


avalon@avalon-Satellite-A75:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
avalon@avalon-Satellite-A75:~$ 



```



This is an Intel Pentium 4 laptop.  I have copied the summary generated by System Profiler and Benchmark in below this line.

(begin summary)


-Computer-
Processor        : 2x Mobile Intel(R) Pentium(R) 4 CPU 2.80GHz
Memory        : 895MB (380MB used)
Operating System        : Ubuntu 13.10
User Name        : avalon (Avalon)
Date/Time        : Fri 28 Mar 2014 10:24:10 AM CDT
-Display-
Resolution        : 1024x768 pixels
OpenGL Renderer        : Mesa DRI R200 (RS300 5835) x86/MMX/SSE2 TCL DRI2
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : ATIIXP - ATI IXP
Audio Adapter        : ATIIXP-MODEM - ATI IXP Modem
-Input Devices-
 Lid Switch
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 Video Bus
 PixArt USB Optical Mouse
 PS/2 Mouse
 AlpsPS/2 ALPS GlidePoint
-Printers-
No printers found
-SCSI Disks-
ATA IC25N060ATMR04-0
TOSHIBA DVD-ROM SD-R2512


(end summary)

Yes, I can hear the fan running (it sounds VERY loud to me, but then I have pretty sensitive hearing.)  However, I cannot feel any real airflow from the vents (there is just a hint, but that's it.)  The USB fan, which sits underneath my computer, runs silently, and on its own extended the time before overheating from less than an hour to at least 10 hours.


Oh, wow... I just realized something really weird...  This computer has a 2.8 GHz processor, while my much newer Windows 7 machine has a mere 2.3 GHz processor!


Surprisedly,

Chessgeek2900

EDIT:  I just tried inputting 'sensors' from the root directory.  The only difference between the output from that and the previous output is a shorter path on the input side (in other words, no difference to the output.  *laughs at self for being as clear as rusty iron*)

---

### Post by pqwoerituytrueiwoq on 2014-03-28
sounds like it is packed with dust, remove some scews and get some caned air to blast them out
clock speeds are not everything, your old laptop probably only has 1 core, your new laptop has at least 2 cores
also if i showed you my desktops AMD Phenom II 965 CPU clock speed was 4.2GHz and showed you a i5-4670 that was 3.4 GHz (they are both quad cores)
you would think my cpu is better, however the intel cpu is about 25% faster and it sips power while mine gourdes on it, google MHz myth

---

### Post by Chessgeek2900 on 2014-03-28
And hello again!

Actually, this is the old laptop.  Both computers are dual-core processors.  The Windows 7 machine is at most 3 years old, while this one is at least 4 years old (a friend gave it to me when he got a new computer, and I decided I was not going to let this machine die if I could help it!)

I'll see if I can take this thing apart without damaging it and clean it out a bit.  I've been a bit reluctant to do that, though, since my other laptop died after I took it apart looking for a different issue (I think I damaged the power supply on that one, but I have no idea how I did it.)  That's one nice thing about desktops, they are easier to take apart and put back together properly.

Hmm...  I know that the size of your hard disk does not matter if you do not have enough RAM to run your operating system.  Is there a similar interaction between the processor speed/number of cores and how much RAM you have?  If so, that might explain some of the performance differences between my two laptops.  Though where graphics are concerned, I might have to break down and get a new graphics card for this machine (I think it might have been damaged by the computer overheating one time too many.  That would certainly explain the display issues in games for which this machine has always met the optimal requirements!)

Gratefully,

Chessgeek2900

---

### Post by pqwoerituytrueiwoq on 2014-03-28
1. dust kills computers, you should actually clean them once a month by rule of thumb
2. ram requirements are relative to your OS and your running applications, same with cpu/gpu requirements
3. idk how you damaged a laptops PSU by taking the system apart, ever laptop i ever saw had it PSU in the middle of a long cable

some laptops are designed to fail after so much time, this is usually done by giving the system a poor cooling solution

---

### Post by Chessgeek2900 on 2014-03-28
Good... noon, approximately.  xD

Well, I took this laptop apart and put it back together, and it still works, even though it took me at least 30 minutes to figure out which screws were for the case and which ones were for the hardware.  (Thankfully, unlike my newer laptop, the only screws accessible without taking the thing apart are for various covers, so it did NOT fall apart in my hands.  I did, however, spend quite some time trying to figure out why, even with all the screws out, I could not open the thing.  I finally found the culprits--two well-hidden screws in the battery compartment.)

From what I could see of the inside, there was virtually no dust in there.  In fact, it looked cleaner than my desktop ever has!  So, after I put the case back together, plugged things back in, and started the computer, I picked it up so I could watch the cooling fans (both are on the bottom of the case, towards the right side.  No fans or vents whatsoever are present in the left-hand side of the computer.  Both vents [the ones without fans] are in the right rear.)  The cooling fans ran for maybe 10 seconds, making their usual racket, then shut off.  While they were running, however, I was able to feel a cool breeze from them.  Also, even when the fans are not running, I can feel hot air coming from the two vents in the right rear of the computer.  The USB fan, unlike the computer's own cooling fans, runs constantly, though it is very quiet.

I take that back.  I just checked underneath my laptop with a flashlight (while holding it up) after it sounded like the cooling fans stopped running, and saw that they actually are still running.  However, I could not feel any air flow from them at this point, unlike when they were making a racket.  I am beginning to suspect that the over-heating issue with this machine is indeed a planned failure, which the USB fan in large part negates.

I feel I should give a better idea of how this machine is set up (especially since it is so different from any other laptop I have seen.)

The power adapter plugs in in the right rear corner.  On the right side in the rear is a plastic wireless switch [at least, I assume it is for wireless because of the little picture of an antenna which looks something like this ((( | ))) ]  Headphone and microphone jacks are on the right side, as is one USB port and the volume control (a wheel-type volume control--sooooo much better than the unreliable software-only setup on my Windows 7 machine!)  Half of the left side is taken up by the DVD/CD drive/burner.  Left rear has two USB ports, followed by phone and ethernet jacks (why the phone jack?), middle contains plug-ins for printer, monitor, and mouse, then we hit the first vent.  The second vent is a bit smaller and is next to the adapter plug-in.  One of the two fans is almost directly below the first vent, though a little farther towards the front of the computer, and the second is placed about in the middle of the right side, also on the bottom.  The hard drive, based on what I could see when I had this thing taken apart, is in the front, near the right corner.

Hmm...  Power supply has ventilation, volume control (which probably does not need it) has ventilation, hard drive *may* have ventilation, DVD/CD drive/burner has virtually no ventilation, along with half the circuit-boards in this thing...  Did I miss anything?

I think I'll try running a couple more videos and keep an eye on the fans.  I am wondering if they shut off before the computer powers down, or if they are still doing their best to keep up at that point.  If they shut off pre-maturely, that may be the cause of the overheating issue (and thus the total shut downs.)

Curiously,

Chessgeek2900


EDIT:  The power supply on my Windows 7 laptop is in the left rear corner.  Unless that is simply a plug-in and the actual power supply is on the adapter/power cord--might that be where we are misunderstanding each other?  The damage I mentioned before was a partially torn ribbon that seemed to hook into the same thing as the plug-in for the adapter.

EDIT (2):  It would appear that fan speed is *not *directly related to the sudden shut downs.  The cooling fans, which speed up initially when starting the computer, slow down to a lower speed when I hit the login screen.  From that point on, they typically stay at about the same speed (the USB fan has one speed only, and it runs at that speed as long as it is plugged into the computer.)  I did not notice any changes in fan speed before the shut down.  Fan, monitor, and sound all died at the same time, as did the power LED on the front of the computer.  There is one new thing, though, which I first noticed late last night: the shut downs are not limited to the full screen player on Youtube.  The large screen player sometimes has the issue also, but not always.  Sometimes it will go for 2+ hours then suddenly shut down, others it will not last 10 minutes.  Full screen remains the same as before, shutting down on the second, third, or fourth video.  The smallest size does not seem to be affected.

I have only tested this with videos thus far, not with any games, full-screen or otherwise.  I am having a separate issue with Steam (at least, I think it is separate) where much of the text in the client is whited-out and the Steam client's background sometimes changes color, and I am currently talking to their support team (via email) about it.

I have also encountered another problem for the first time since I changed this computer to Linux (it happened a few times in Windows.)  Sometimes, after a sudden shut down, the volume will be muted, whatever the system says, and cannot be un-muted without shutting the computer down and waiting at least 30 seconds before starting it up again.  I am guessing this has something to do with the computer being over-heated (as it almost never happens after a normal shut down--based on my previous experience in Windows.  It has only happened once in Linux thus far.)

---

### Post by whatthefunk on 2014-03-28
What brand and model is your laptop?  Many laptops have issues with cooling and people have developed model specific fixes.

---

### Post by Yellow Pasque on 2014-03-28
Ugh, it's one of those laptops with a Prescott-based Pentium4. There's really not much you can do in this case except avoid using the Flash plugin to play videos, and avoid anything else that pegs the CPU for extended periods of time.

My computer learning center has a small testing room with 5 or 6 cubicles that is abnormally warm (which makes the exams more fun). I did not bat an eye when I saw the Pentium4 logo on each of the machines...

---

### Post by Chessgeek2900 on 2014-03-29
Good morning.

Yes, it is a Pentium 4, distributed by Toshiba.  I am not sure where to find things like the model number, though.  I believe I included an attachment towards the bottom of the first page of this thread with the system information I was able to get through System Profiler and Benchmark.  If it's not there, please let me know, and I'll re-upload it.

Thanks,

Chessgeek2900

---

### Post by Vladlenin5000 on 2014-03-29
Your machine is from the time when there was a widespread issue with a small electronic component present mostly but not limited to motherboards: Swollen capacitors. Your symptom is consistent with this problem. This has affected almost all brands including Apple. Dell - if I remember correctly - even extended its warranty for 3 years more on top of the mandatory European 2 years for free in order to "save the face" in the end.

Haven't you noticed some swollen capacitors, perhaps even liquid pouring out of the top "cross"? Keep in mind capacitors should be cylindrical at all times. Any deviation from that shape means a serious malfunction.

---

### Post by Yellow Pasque on 2014-03-29
> **Chessgeek2900 said:**
> I am not sure where to find things like the model number, though.

It's a Satellite A75 of some kind. The sad fact is that you have a laptop that doubles as a space heater and there's not much you can do...

Hardware:
1. Verify fans are functioning properly (sounds like you already did that with the ear test)
2. Clean/dust the internals (you just did that)
3. Use things like external cooling pads/fans (I guess you have an external fan?)
4. Reapply heatsink thermal paste (I have a feeling it won't help much in your case)

Software:
1. Find ways to avoid watching video with the Flash plugin (minitube?)
2. Find ways to throttle the CPU before it becomes critically overheated (need output from temp sensor)

---

### Post by Yellow Pasque on 2014-03-29
> **Vladlenin5000 said:**
> Swollen capacitors. Your symptom is consistent with this problem.

I disagree completely. Leaking capacitors usually result in strange behavior or stability issues. This is a Pentium4 we're talking about here, so it probably ran hot from day one.

---

### Post by Chessgeek2900 on 2014-03-29
Salutations!

Yes, this computer has run hot as long as I have had it.  The friend who gave it to me warned me that it had an overheating issue.  The USB fan I am using is indeed an external fan, one that is setup like a platform at an angle for the computer to rest on (single fan easily covering almost all of the bottom of the computer.)

I did not notice any leaking capacitors when I had the cover open, but then I was not looking for anything of the sort at the time.  Really, the only other strange behavior this computer has exhibited (other than the shut downs and a consistent graphics glitch in some games for which my graphics card surpasses the optimum requirements) started with a Windows update about 6-12 months ago--and wiping the computer and switching to Linux did not fix it.  About 2-3 inches of screen on the right side are simply black, almost as though the computer thought the screen to be much smaller than is the case.  There is a small section on the edge of the viewable screen that looks like a partial reflection from nearer the middle.  I've been getting used to it (it is not *quite* so bad in Linux as in Windows) but I still do not know the cause.

I have downloaded a media player and a plugin through the Ubuntu Software Center (Gnome mplayer and something else--I don't remember the name of the plugin) but I do not really know what I am doing with those thus far.  The plugin, I believe, only works with Firefox, not with Seamonkey (first time I've seen that, but then there have been a lot of firsts recently!) so I probably should do a bit more testing in Firefox to see if it helps.

For temperature sensors/controls, I posted the results of trying to find them earlier in this thread (either near the end of the first page or on this page.)  I am not sure how to proceed from this point.  I did download lm-sensors, but got lost on how to install it (and deleted it before trying to get it via the terminal--let's just say I only know the bare basics of using the command line.)

Thank you all for your continuing advice.


Chessgeek2900

---

### Post by Yellow Pasque on 2014-03-29
sensors-detect said:
> Sorry, no sensors were detected. This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS.

So you need to figure out whether you can access temp through ACPI (don't ask me exactly how as most of my Linux experience is on desktops). Hopefully, someone else can help you there...

---

### Post by whatthefunk on 2014-03-30
> **Chessgeek2900 said:**
> Good morning.

Yes, it is a Pentium 4, distributed by Toshiba.  I am not sure where to find things like the model number, though.  I believe I included an attachment towards the bottom of the first page of this thread with the system information I was able to get through System Profiler and Benchmark.  If it's not there, please let me know, and I'll re-upload it.

Thanks,

Chessgeek2900

What brand is the laptop?  Sony?  Toshiba?  There must be some sort of brand name on it somewhere.....and there should also be a model number on it.

---

### Post by Yellow Pasque on 2014-03-30
^
```
# System: TOSHIBA Satellite A75 [PSA70U-003002] (laptop)
# Board: TOSHIBA EDW10
```

---

### Post by Chessgeek2900 on 2014-03-30
Good afternoon.


According to a sticker on the bottom of the computer, this is a Toshiba Satellite A75-S206.  It looks like the information in Temüjin's post (directly before this one) is correct.  I'm guessing that was copied from the system summary earlier in this thread?

I have found something through Ubuntu Software Center called collectd, which apparently is used to monitor various things through ACPI, but the information on the website left me rather confused.  I've been feeling recently as though I were jumping straight into advanced computer programming before even having mastered the basics! D:  I should have realized that such seemingly simple things as checking my computer's temperature and getting it to recognize that the screen is approximately 13"x8" (NOT the 10.67"x7.99" reported by Steam, which almost matches the display issue I am having) could easily become more complicated than placing a unit in Battle for Wesnoth--and that can easily be over a page of coding under some circumstances, too!

Anyway, there is one piece of good news; the overheating issue on Youtube appears to be fixed.  Viewtube is playing videos now that crashed the entire system when using Adobe Flash.  I can also watch some of those HD videos that used to be annoyingly laggy without the lag, though I have to lower their quality in Viewtube.  Thank you so much to the person who suggested this before!  (Unfortunately, however, this does not extend to other full-screen graphics intensive applications, namely, games.)

Gratefully,

Chessgeek2900

---

### Post by Yellow Pasque on 2014-03-30
Maybe these packages will help?
```
sudo apt-get install toshset acpitool
```

---

### Post by Chessgeek2900 on 2014-03-31
Greetings.

As this issue appears to be solved (as of last night) I will go ahead and mark this thread as solved.  

Thanks for all the help!

Chessgeek2900

P.S.  The issue listed in another thread I just posted is almost certainly separate from this one. ;)

---

