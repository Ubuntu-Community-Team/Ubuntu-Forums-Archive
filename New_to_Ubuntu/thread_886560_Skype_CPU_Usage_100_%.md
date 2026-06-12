---
title: "Skype CPU Usage 100 %"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by cool_penguin on 2008-08-11
Hi Everyone,

I tried the tutorial stated on 

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I tried it to resolve problem with simultaneous use of Skype and you tube; basically a pulse-audio issue. While I could resolve the problem, I realized that each time I use Skype, the CPU usage shot up to 100 % and Skype became less responsive almost froze each time. I had to kill the skype process and that brought back the CPU usage to normal. 

I have been googling like crazy and also looking up forums, but no solution to my problem yet. I hope some of your Ubuntu experts might be able to help me out.

Thx in advance.

Cheers,
Harry

---

### Post by cool_penguin on 2008-08-11
Anybody with the same issue?

---

### Post by cool_penguin on 2008-08-12
It been well over 24 hours and no help yet. Somebody please help me. I don't wanna switch back to Xp.

---

### Post by cool_penguin on 2008-08-12
I am switching to Fedora. They seem to have done a better job with Pulse-audio.

---

### Post by funkameleon on 2008-08-13
I am having the same problem

---

### Post by svaens on 2008-09-17
hey, i have the same problem here. 
It doesn't seem to happen all the time. 
But often enough since I set everything to using pulseaudio. 
Having said that, I rather think that it is fault of skype rather than pulse audio. My problem comes just in using skype at all. I don't even have to have any other audio applications open. 

Frankly, i'm sick of using the closed source skype, but the only competitor in open source is open wengo. Just to install that seems a step backwards, as it is something like 3 times the install size. And skype is already bloated. What the hell is in open wengo!! And besides, I need to call land-lines. I think you can do that with wengo, but.... didnt want to fork out money for an application i didn't want to install... and haven't heard that many good reviews about. Anyone been there? I also don't know what the wengo sound issues are with pulseaudio, if there are any.

[any fedora uses that have skype and pulseaudio working without problem, i'd like to hear about your setup!]

---

### Post by bigjig on 2008-09-20
Well has anybody managed to fix this?

I have the same problem, CPU % went over the roof. I am using that pulse audio as well.

---

### Post by treris on 2008-09-29
Yeah, same here, when using Skype my cpu goes to 100% as soon as I start talking to somebody. When I'm not talking to anyone and it is just sitting in the tray it's hardly using anything at all. 

Pulseaudio might be the problem, but it is not causing me any problems with other applications so my bet is that it is something in the combination of Pulseaudio and Skype.

Any solutions???

---

### Post by Fuut on 2008-10-24
I found a solution:
Don't set the sound in device to pulse!
See this link:[http://www.howtoforge.com/how-to-fix-the-sound-issues-between-skype2.0-and-pulseaudio-on-fedora9](http://www.howtoforge.com/how-to-fix-the-sound-issues-between-skype2.0-and-pulseaudio-on-fedora9)

---

### Post by bigjig on 2008-10-25
> **Fuut said:**
> I found a solution:
Don't set the sound in device to pulse!
See this link:[http://www.howtoforge.com/how-to-fix-the-sound-issues-between-skype2.0-and-pulseaudio-on-fedora9](http://www.howtoforge.com/how-to-fix-the-sound-issues-between-skype2.0-and-pulseaudio-on-fedora9)

thanks but I did sort it a while ago, dont remember how.... but i got rid of all that pulse crap and all i did was install libflashsupport

it got sorted on its own.

---

### Post by merelin on 2009-08-08
Guys,

Try to change your /etc/pulse/daemon.conf:

high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
default-fragment-size-msec = 5

That seems to have solved the issue.
I have pulseaudio on karmic amd64 and skype from the medibuntu repo.
Skype is set to pulse. Used to experience 100% cpu load.

---

### Post by nmaster on 2009-08-08
You should try this:[INDENT] 
[LIST]
[*]killall pulseaudio
[*]sudo apt-get remove pulseaudio
[*]sudo apt-get install esound
[*]sudo rm /etc/X11/Xsession.d/70pulseaudio
[*]Reboot system and use the default sound setting in skype.
[/LIST]

this will downgrade you to esound, which works without any issues (at least for me)
 [/INDENT]

---

### Post by merelin on 2009-08-08
> **neal.m.master said:**
> You should try this:[INDENT] 
[LIST]
[*]killall pulseaudio
[*]sudo apt-get remove pulseaudio
[*]sudo apt-get install esound
[*]sudo rm /etc/X11/Xsession.d/70pulseaudio
[*]Reboot system and use the default sound setting in skype.
[/LIST]

this will downgrade you to esound, which works without any issues (at least for me)
 [/INDENT]

Getting rid of pulseaudio is not at all a solution.

---

### Post by nmaster on 2009-08-10
> **merelin said:**
> Getting rid of pulseaudio is not at all a solution.

like i said, it was a solution for me.  "not at all a solution" for you perhaps, but it fixed my problems.

---

### Post by whitethorn on 2009-08-10
> **svaens said:**
> hey, i have the same problem here. 
It doesn't seem to happen all the time. 
But often enough since I set everything to using pulseaudio. 
Having said that, I rather think that it is fault of skype rather than pulse audio. My problem comes just in using skype at all. I don't even have to have any other audio applications open. 

Frankly, i'm sick of using the closed source skype, but the only competitor in open source is open wengo. Just to install that seems a step backwards, as it is something like 3 times the install size. And skype is already bloated. What the hell is in open wengo!! And besides, I need to call land-lines. I think you can do that with wengo, but.... didnt want to fork out money for an application i didn't want to install... and haven't heard that many good reviews about. Anyone been there? I also don't know what the wengo sound issues are with pulseaudio, if there are any.

[any fedora uses that have skype and pulseaudio working without problem, i'd like to hear about your setup!]


You might want to take a look into Ekiga with voip.  I only tried it briefly, but it seems if you get an account and someone you know also get has one you can voice chat like with skype. Depending on where you get an account (SIP) you can then also call landphone lines really cheap.

---

### Post by dtakamori on 2009-10-26
actually, for me, switching to Skype 2.1beta (it has pulseaudio support!) seems to have helped.

---

### Post by ublintu on 2009-11-01
but not 4 me. In Karmic, with new skype, I still get high cpu usage and even disconecting. In skype options I can`t change anything, just pulseaudio in the list.

---

### Post by Nick Brohman on 2009-11-01
I have just upgraded to 9.10 & seem to have lost the Skype help link but I solved the problem of cpu usage in 9.04 by following a tip in their FAQs..

Can't quite remember the exact wording but it has something to do with no nv or xv.

As it has taken a while for me to get this upgrade finalised, I'm hitting the ZZZZbag & will research this tomorrow. 

Nicko

---

### Post by baytuni on 2009-11-13
bump

---

### Post by Sophont on 2009-11-13
Make sure you use this version (2.1 beta):
[http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

This one has PA support and didn't give me any problems.

Before that I used this version: 
[http://packages.medibuntu.org/karmic/skype-static-oss.html](http://packages.medibuntu.org/karmic/skype-static-oss.html)
Needs to be started with "padsp skype" to work with PA.
No more maxed CPU probs.

---

### Post by Nick Brohman on 2009-12-04
I found the answer to my problem with CPU usage in the Cheese Help pages.

Go to FAQs and do what the first solution suggests - Terminal> gstreamer-properties and reset the video. I've just done that myself and it has worked.

I don't run any other vid programs when using Skype.

Cheers..Nicko

---

### Post by martingugino on 2010-05-15
I have Skype 2.1.0.81 (the one you mentioned) and Ubuntu Lucid (10.4) on a Dell A90 netbook with dual atom 1.6G cpus, and Skype by itself pegs at 80%. If I open a browser, I can easily get 100% lock-ups. You may have more processor than I do; I expect so.  
I question whether your suggested solution will solve the problem for everyone.

I did not understand what you meant by the "Cheese Help" pages.

---

### Post by Der_Kommissar on 2010-06-29
I'm a new (only this month) Ubuntu user (10.04) and having problems with 64 bit version of Skype as well.  I'm only using it for text chat around the office here, but I've noticed I'll start getting the yellow triangle with "!".  If I check the system monitor or "top", Skype will have one of the CPUs pegged at 100%.  I can't seem to do anything specifically to cause Skype to fail like that - frustrating.  I have to kill -9 the process rather than ending it normally at that point.  Sometimes it runs for 5 minutes, other times it runs for an hour before locking up...but once it does, it seems to lock up fairly quickly afterwards.  

I tried launching Skype from a terminal window rather than from the GUI in hopes that I'd get some sort of error message - but no dice.  Can't seem to find an error log to help me sort it out either.

I contacted the Skype support folks and they had me remove and reinstall Skype through the terminal.  Still having problems. :|

If I could just shut the dang thing off it would be great- it runs fine on my Mac and Windows machines, but I've gotta run Ubuntu as I'm going to be supporting it for work.

Any suggestions?  

Skype 2.1.0.81

Ubuntu 10.04
Kernel Linux 2.6.32-22-generic
GNOME 2.30.0
Dual quad core Xeon CPUs (3 GHz)
4 MB of RAM

---

### Post by reve_etrange on 2010-07-28
I'm experiencing this issue as well...hopefully I'll figure out how to replicate it.

Ubuntu 10.04, Skype 2.1.0.81.

---

### Post by capput on 2010-07-28
I too am experiencing this problem.  This seems to be a regression, as I had never had this problem and a week or two ago it popped up.  Upon googleing it seems that this was a common problem solved for many by skype 2.1.x.  

Everything starts fine for me then at some point (there does not seem to be a correlation to up-time, time-on-skype, time-on-call, or other activity) the cpu usage of skype (and maybe pulseaudio)  starts going up.  Then the person on the other end tells me I am breaking up, then shortly after I notice that they are breaking up.  This happens when I am on a skype-skype call as well as a skype-regular phone call.  Oddly sometimes a system restart will fix the problem other times it won't; I can tell the times it won't work when I am logging in as the system log-in page takes a long time to load and then after typing my password it takes a long time till the desktop is loaded.

Started with skype 2.1.0.42 (whatever is in the repo) and continues with 2.1.0.81 (current build from the skype site).

9.10-64bit
2.6.31-22
nvidea 185
dell m1330

Has there been a resent update to pulseaudio?  Any other solutions?

---

### Post by Nick Brohman on 2010-07-28
> **martingugino said:**
> I have Skype 2.1.0.81 (the one you mentioned) and Ubuntu Lucid (10.4) on a Dell A90 netbook with dual atom 1.6G cpus, and Skype by itself pegs at 80%. If I open a browser, I can easily get 100% lock-ups. You may have more processor than I do; I expect so.  
I question whether your suggested solution will solve the problem for everyone.

I did not understand what you meant by the "Cheese Help" pages.

My apologies, the reply to this wasn't posted....

Cheese is a web cam program available thru' Software Centre......the Help pages give solutions to problems.....go to FAQs and the first question gives the answer to the problem......that is if your CPU usage is high, change your video settings....run gstreamer-properties in a terminal and change the X Window System setting to X11 etc.,....

I am using an Compaq Presario CQ61, and have a dual core AMD PC......this solution works on both units....

Once again, my apologies for this taking so long ...

---

### Post by capput on 2010-07-29
> **Nick Brohman said:**
> My apologies, the reply to this wasn't posted....

Cheese is a web cam program available thru' Software Centre......the Help pages give solutions to problems.....go to FAQs and the first question gives the answer to the problem......that is if your CPU usage is high, change your video settings....run gstreamer-properties in a terminal and change the X Window System setting to X11 etc.,....

I am using an Compaq Presario CQ61, and have a dual core AMD PC......this solution works on both units....

Once again, my apologies for this taking so long ...



Thanks Nick for the suggestion, however it has not solved my problem.  I continue having skype run the CPU up to 100% and then my calls not being heard by the other person and/or me not hearing them.  

I preformed a clean install of 10.04 last night hoping that would solve my problem, but alas it hasn't.  Another thing I am noticing now on 10.04 is that often after this occurs I will try to close skype and it will not quite even after the icon vanishes.  When this happens killall does not end the process, though it reports no error.  I am left with only rebooting with skype still not responding.

Any other ideas?


After skype has run-away like that it effects other things.  Most notably firefox which then starts taking up a lot of cpu time and bogging down the system even when killall says that skype is dead.

---

### Post by Elmer Fudd on 2010-07-29
It sounds like you are not using Video but just curious..
Under Skype/Options/Video Devices
Are either of the two video options selected?
-Enable Skype Video
-Start my Video Automatically 

Also
Are you able to Stop/restart pulseaudio when these sypmtoms occur and does that change cpu usage with skype or Firefox bootup?

---

### Post by Nick Brohman on 2010-07-29
G'day Capput,

The only other thing I can think of is to open Options and disable permission for Skype to set your levels......I'm afraid I can offer no other solution.....

One thing I found initially was that I had to get rid of Pulse.....that was on my 2.66 GHz Athlon X2 PC....when I was able to put Skype on the 'top and just had Pulse, I didn't have to do that.....

The PC is down at the moment so I can't check the situation with that.....having the two units going would have enabled me to do a comparison......Skype performs differently on both units......

I hope this can be resolved for you....

---

### Post by capput on 2010-07-30
Hi there Mr. Fudd,
 I am not using video, would like to...have in the past, but no video for now.

 I can kill pulse, which then restarts moments later.  This seems to have mixed results on the system; sometimes, like just now, it lowers the overall cpu usage and responsiveness returns, however other times it seems to have little to no effect.



Nick, good day to you.
 I had in fact disabled 'let skype set audio levels' and still no joy.

Could you elaborate on this:
> One thing I found initially was that I had to get rid of Pulse.....that was on my 2.66 GHz Athlon X2 PC....when I was able to put Skype on the 'top and just had Pulse, I didn't have to do that.....
I am not sure I understand what you are saying.


Other observations: 
My work computer, with 10.04 and all the same updates, runs skype like a champ.  This makes me think maybe there is some hardware issue..sound card?

When watching a video in vlc (which is using pulseaudio) many times the same result occurs.  Around 8-9 minutes in pulse begins to hog the cpu which is followed, in step, by the other app until they are using (combined) ~150% of the cpu.  I really think this is a pulse problem.  


Does anyone know if there has been an update to pulse in the last few weeks?  Is there a way to use ALSA in place of pulse?  I really appreciate all the help, usually I am able to find solutions myself but I am really stumped here.

---

### Post by Nick Brohman on 2010-07-31
G'day capput,

When I first installed Skype last November, I had problems with audio so I went looking for answers and Pulseaudio came up as culprit....seems to happen on different hardware and not the same for all...I removed Pulseaudio but one must be careful as some packages are required for Skype.....

I'll have to do a search for the thread where I found the answer, but it's to do with sound solutions in 9.04 (?) I think.....I'll post that later...

I made ALSA my sound system and had some more minor problems which were easily fixed......things like muting boost,....too long ago to remember completely...then the video was freezing or very slow, which annoyed me enough to find an answer for that.....hence the Cheese solution....

I had Camorama initially, along with Camera Monitor and had no webcam recognised.....got rid of them in favour of Cheese..

It seems to be a Koala thing.....I got this 'top about 6 mths ago and replaced the PITA 7 HD with a bigger HD within 24 hrs, loaded 9.10 and didn't have to do much with Pulse when I was finally able to get Skype to install.......

This is how crazy this is....I've just run gstreamer-properties on the Presario and found that I wasn't doing as I had advised....during a Skype call recently, I checked the CPU usage and 60 % was an average max on one and about 40 % on the other.....

I'm running Cheese at the moment and, after setting my video to the X11/...setting,.....none of my contacts are online so I'll have to wait to verify the usage figures but I've just done some voice recordings as a test and the graph shows 30 % max usage.....not conclusive, I know, but as close to making a call that I could muster....

I've also reduced the resolution of the cam from 800x600 to 320x240 and that seems to have reduced usage again... 

I had problems using a dual Athlon box but not with the dual Intel Celeron laptop.....it's a worry, as my old line boss would say in his Irish lilt.....
  
Two computers and two different scenarios.....aaaaggggghhhhhhh...yerwoodenbededferquids......

Cheers and good luck.....

PS....Re-reading your post makes me think PulseAudio is your culprit....I'll find that post for you ASAP...

---

### Post by capput on 2010-07-31
So I have found more edvidence this is a pulse problem, following these instructions:
>    1. Turn PulseAudio autospawn off, normally: $ echo "autospawn = no" > ~/.pulse/client.conf
   2. Kill PulseAudio: $ killall pulseaudio
   3. Shut down and restart Skype
   4. Go to the Skype sound device options, where your devices should now be exposed; Choose something.
   5. Shut down Skype
   6. Turn PulseAudio autospawn back on: $ echo "autospawn = yes" > ~/.pulse/client.conf
   7. Relaunch PulseAudio: $ pulseaudio -D
   8. Launch Skype
   9. Edit and test Skype sound device preferences

from [http://ubuntuforums.org/showthread.php?t=1416539]("http://http://ubuntuforums.org/showthread.php?t=1416539") I was able to use skype while pulse was disabled.  When pulse was enabled I never had any option other than pulse in the devices box in skype.  After I disabled pulse I changed the device and everything seemed to work fine (for a short call since all of my contacts are offline).  Then when I relaunched pulse and restarted skype I went to the audio devices and it was reset to pulse and again there were no other options.  When I tried the test call again this time the cpu usage started to rise.

I am considering removing pulse, but that often seems to cause its own problems.  What is troubling is how this was not a problem two weeks ago.  What has changed?  Maybe that is the best way to approach this as I seem to have run out of other ideas.

regards

---

### Post by Nick Brohman on 2010-07-31
G'day again,

Had to manually search a few pages for the thread that I wanted as I didn't ask the right ???s.....

It's not the sticky on the Multimedia Forum, I'm looking for it because it was an easier method for me to understand....I'll look again later today as it's time I had some ZZZZZzzzzzzsss...(we just got to Sunday....)

Removing Pulse outright will remove Skype so there are some packages that must be kept...my experience, anyway...

Two threads that might help.....

***100 % CPU usage***

[http://ubuntuforums.org/showthread.php?t=1359480](http://ubuntuforums.org/showthread.php?t=1359480)

[I][B]Rant about pulse
[/B][/I]
[http://ubuntuforums.org/showthread.php?t=1306679]("http://ubuntuforums.org/showthread.php?t=1306679&highlight=Sound+Solutions+9.04+Jaunty")

Pulse being the sound server, it is most probably the problem....and there's been no end of trouble with Pulse since late April, last year.....that's where I started looking...
 
[COLOR=Red]**Firefox**[/COLOR] is a possible culprit....

I notice that I sometimes get some funny glitches after a [COLOR=Red]**Firefox **[/COLOR]update.....there's an **lspci** command to run (see the **[COLOR=Navy]usage[/COLOR]** thread) that could possibly give you more to go on......

Cheers, I'm for the fartsack as the * Cross has turned over.....g'nite..


*Southern

---

### Post by Nick Brohman on 2010-07-31
G'day capput

[http://ubuntuforums.org/showthread.php?t=1175564](http://ubuntuforums.org/showthread.php?t=1175564)

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The latter of the links is by markbuntu and is out of date, but it is worth looking at.

This is by mark as well and is the thread I followed to remove Pulse.....read the post & take note of the paragraph in Necessary Packages that begins with 'The gnome-volume-control....

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

Thanks for getting me into this again, it's helped me in other ways....finally put a 2nd monitor to the 'top and worked out how to use the set-up properly......

I've left the first two links for you to look at as they could be of help.....thanks again for inadvertently helping me with some more knowledge...

[COLOR=SeaGreen]I did get to make a Skype call today and the highest spike of usage was 61%, the average usage was around 30 %.....my sound broke up but I suspect it was my brothers' mic, he does need a new one...
[/COLOR] 
Cheers, I hope you can resolve this problem....

---

### Post by capput on 2010-08-01
Thanks Nick, I will look at the links and modify my system accordingly I will post back what I find.

I'm glad to hear this has spurred you on, but truly I am the one who should be thanking you.  It has been wonderful to have someone else to offer other ideas rather than just running over the same things in my mind.  I have appreciated your help immensely.

Hopefully when I post back I will have good news.


cheers

---

### Post by Nick Brohman on 2010-08-01
> **capput said:**
> Thanks Nick, I will look at the links and modify my system accordingly I will post back what I find.

I'm glad to hear this has spurred you on, but truly I am the one who should be thanking you.  It has been wonderful to have someone else to offer other ideas rather than just running over the same things in my mind.  I have appreciated your help immensely.

Hopefully when I post back I will have good news.


cheers
Big bubbles, no troubles...I'm a real novice but if something happens to me where I can get a solution, I'll try to help others in the same boat.....the Forum is circular but but not a perfect circle....I've been put on the right track by markbuntu and others.....my little search for you was part of how I repay them.

I also learnt another trick in how to ask the right question....I asked my original question with 6 variations of it without satisfaction.....so I went to 30/4/09 and searched 'til my brain clicked in and told me to look for Pulse and ALSA, not Sound Solutions and there was the name I knew I would recognise...I knew it involved 'buntu....along the way, I found some threads where I gained more knowledge and some links that will be very helpful...this shows how fast I am tho', it only took about 400 pages to work out the right question. No worries because I have nothing to do all day...and all day to do it in, it's an advantage to being on a disability pension for the last 14 years (& a SPaNK).

I look forward to hearing of your success with this problem.

Hooroo

---

### Post by no2498 on 2010-08-02
this is the cheese help some 1 on page 3 was looking for


5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

### Post by krabunski on 2010-08-07
I've got the same problem. On my mother's machine it results in garbled sound. On my machine it results in a quiet high CPU usage of one core. Sound quality is good though.

---

### Post by Nick Brohman on 2010-08-09
Krabunski, I would suggest that you treat the machines as separate entities....deal with the garbled sound first....but determine if...

.......if the spike in CPU usage of one core, is it constant during a Skype call only? Does it happen when replaying music? Is there a program/app running that is a possible cause for the spike? Pulse starts to hog things if two or more sound apps are in use. If it happens as a natural progression of the 'wave', then I can't see a problem. If it's a constant spike  the answer is to investigate all avenues, determine the cause, if possible, post the solution so that others may benefit from your experience. 

The garbled sound, is it two-way? Does the receiver comment on sound quality? Does it happen when other audio sources are being used, games, music, etc.? You will have to adjust whatever sound mixer that you are using, 100% on the main sliders is not a good idea as that results in distortion.  Too much boost on the mic slider is a big no no.  Test with Sound Recorder but during a Skype call is best, that way one can get feedback from the other end. Ensure that the checkbox in the Audio Devices - "Allow Skype To Automatically Adjust Levels" - is unchecked.

Most of the solution is trial and error.....my solution came via 4 different threads....I got a bit here, some of from there...."will removing Pulse work for me?"...."is it my microphone?"....."what if I did this?"...."do I have something running that is part of the cause". It could be something as simple as positioning of mic and speakers and the garbled sound is caused by "feedback".

My latest experience in a related fashion happened in the last two days.....my PC was brought back online over the weekend, after a major dusting and clean out. It took two days before I could test Skype and when a contact finally came on line, no sound or video yet they had worked with Sound Recorder and Cheese.

The cam I fixed by resetting the Options in Skype, ran gstreamer-properties while having Cheese open, reset the Linux For Video.....audio was virtually the same....checked the mixer, and reset the options. It was a very different solution to how I first got audio on the PC last October....the example is there for you....mine might not be yours but.......I made sure the hardware/peripherals were working then went looking elsewhere......

---

### Post by krabunski on 2010-08-10
Nick, thanks for your suggestions. I don't have access to the machine making trouble right now. But I remember that I tried to record sound with the "Sound Recorder". It worked fine. Without distortion. Even Video-Recording together with sound worked without any problem. I will try your "Automaticall adjust mixer settings" tip when I get the chance again. I really think it's a pulse audio problem.

---

### Post by Nick Brohman on 2010-08-10
G'day krabunski, 

You're most probably right, it's a funny animal but the Skype move could just do it...it's a pity one solution doesn't work for everyone.....don't forget to ask/determine if it's your Mum's computer, or the person on the other end...it can be as simple as that...

I'm yet to test the laptop, it's only 10 minutes since I finished installing 10.04....it's too late at night to call any of my Skype mates.....manana for that..

What I've done is open Cheese, with a spike of 100 & on 1 CPU, which then fell back to the low end of the scale, recorded 20 seconds with Sound Recorder and no significant spike in usage....the only thing I've done to Skype was to ensure the lappy cam was seen, not my USB camera...

So far I'm a happy chappy...test call, sound and video work very well....

Good fortune to you....

---

