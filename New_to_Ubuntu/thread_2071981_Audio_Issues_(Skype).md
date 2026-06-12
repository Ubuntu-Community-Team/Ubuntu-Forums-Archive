---
title: "Audio Issues (Skype)"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by Gnawnsense on 2012-10-16
Hello everyone, thanks for reading!

Brief background on me, so you know where I'm at as far as my Ubuntu know-how. I'm quite the Linux newbie. I've been trying to use Ubuntu off and on for the last 5 years or so and always ran into issues with my ATI drivers that drove me away. After cycling a few machines and waiting a few releases, installed 12.04 and have had absolutely no issues, and am loving my experience thus far. However, I'm basically a terminal virgin (I get it, but have no concept of what most commands mean, or have a full understanding of the system). I'm very fluent with Windows, so I have an understanding of computers and how most operating systems work, but I'm not extremely inclined when it comes to troubleshooting.



Now, onto the problem I'm having.. I work with Skype on a daily basis and installed it from the software center immediately. Install went fine, put in my login credentials, and immediately noticed the login sound was extremely distorted (speakers popping/static type sound). 

The first thing I did at this point was play a few videos from various sources online, from music to regular videos, increased the volume accordingly, and noticed outside of Skype I wasn't experiencing any sound issues.

I went to Google and typed something along the lines of "Ubuntu Skype sound quality/problems" and came up with quite a few results, all similar to mine. So I read through a few forum posts, tried one of the fixes, and lo and behold it was successful! The fix involved disabling pulse audio and rebooting. Upon rebooting, Skype was working wonderfully as far as audio quality.

So today, I've been booting back and forth between Windows. I just switched back over to Ubuntu and fired up Skype and immediately noticed the login sound was cracking and distorted all over again.

So before I attempt applying the previous fix, my question is, are there multiple ways to disable pulse audio? If so, what is a permanent solution? With disabling pulse audio hurt any of my other system features; is it required? Will disabling it cause issues that might hurt my system in the long run? Should I expect to have to periodically re-apply this fix?

Also, I did apply a system update last night, but it was minimal and I did not see anything relating to audio from the list of patches I was downloading. However, that's not to say there wasn't. Maybe the update could of caused an issue? Doubtful to me, tho, being as I had rebooted after update and not experienced the sound problem.

Below is the method I used to disable pulse audio:

> [i]- Opened up /etc/pulse/daemon.conf
- Located the line that included "default-fragment-size-msec = 10"
- Changed the 10 to 5
- Saved file
- Ran command: sudo /etc/init.d/pulseaudio --kill
- Reboot[/i]



Any information on the issue, fixes, or where to go from here would be appreciated. The issue isn't extremely pressing, but I would like to get it fixed. Switching to Windows just for Skype seems rather silly, and frustrating.

**Update #1:** *Recently logged in and out of Skype multiple times. I noticed I'm only getting the distortion and static from Skype off and on. Before I applied the original fix, it was constant. After the fix, it never did it. Now it appears I'm somewhat in the middle. One second the sound is distorted, the next it isn't.. but it always is predominantly distorted. And I further tested my sound system and have experienced no other issues outside of Skype, which leads me to believe it is related to the original issue with pulse audio as I expected.*

**Update #2:** *Editing the post to add my original method for disabling pulse audio. No idea how I forgot to add it, might make assistance a bit easier!*

**Update #3:** *I have yet to experience the sound distortion happening with Skype again. Assuming the other day after my initial fix was a fluke. So far it appears the original modification I did to pulse audio solved my issues. Thread set to resolved.*

---

### Post by newb85 on 2012-10-16
How exactly did you disable pulse audio?

---

### Post by Gnawnsense on 2012-10-16
> **newb85 said:**
> How exactly did you disable pulse audio?

Heylo, thanks for the reply! I noticed there were a few different methods when searching for solutions with pulse audio. This seemed like the easiest for me to reverse if something went wrong, so when I disabled pulse, this is exactly what I did:

> [i]- Opened up /etc/pulse/daemon.conf
- Located the line that included "default-fragment-size-msec = 10"
- Changed the 10 to 5
- Saved file
- Ran command: sudo /etc/init.d/pulseaudio --kill
- Reboot[/i]

---

### Post by newb85 on 2012-10-17
Yes, what you did is very reversible.  But no, it didn't really disable Pulse.

> - Opened up /etc/pulse/daemon.conf
- Located the line that included "default-fragment-size-msec = 10"
- Changed the 10 to 5
- Saved file
This changed a parameter for Pulse--a method that can sometimes be used to fix "glitching" issues.

> sudo /etc/init.d/pulseaudio --kill
This stops the instance of Pulse that is currently running.  In Ubuntu, when this is done, a new instance of Pulse starts.  So, you effectively restarted Pulse in order to have the parameter changes you made take effect.

> - Reboot
This was unnecessary, since you had already restarted Pulse.

By the way, have you tried turning that setting down to something lower than 5msec?

---

### Post by Gnawnsense on 2012-10-17
> **newb85 said:**
> By the way, have you tried turning that setting down to something lower than 5msec?

Thanks for the reply!

No, I didn't try lowering it or raising it to anything above or below 5msec. Reason being is I still don't have a grasp on exactly what pulse audio is (tho that's just a Google search away), but I have no idea what I actually modified within pulse audio, nor what changing 10 to 5 actually did other than eliminating the sound quality regarding Skype.

At this point, I'm assuming the issue returning last night temporarily was a fluke. After a few reboots I haven't experienced the distortion again.

---

### Post by Kevin McCready on 2012-10-17
I also had probs like yours when trying to record sound. I settled on
mplayer in gnome-media (I had to install PulseAudio Volume Control and then select Sound Recorder). I also use alxamixer
good luck

---

### Post by Gnawnsense on 2012-10-18
> **Kevin McCready said:**
> I also had probs like yours when trying to record sound. I settled on
mplayer in gnome-media (I had to install PulseAudio Volume Control and then select Sound Recorder). I also use alxamixer
good luck

Definitely good to know, will make a mental note of that.

However, my sound issues are actually happening when no sound is being recorded. For example, when you initially sign into Skype, you get that famous whooping sound. Starting with that sound, everything is completely distorted coming out of my speakers that is coming from Skype. Skype is also the only program that seems to be affected thus far.

I haven't tried recording audio yet. I imagine using the microphone built into the camera I'll have issues there to work through, even on Windows it wasn't a friendly microphone. But this current problem has nothing to do with sound or input being recorded.

I haven't experienced the issues anymore, tho. Will go ahead and chalk it up to a fluke the other day and assuming the initial modification to the Pulse Audio was a good fix.

---

### Post by PhL38F on 2012-11-02
Hi!
Though I have not exactly the same background (I daily work at the office with  Linux systems, using the command line), I faced sound issues also  recently at home, but with a version 10.04 of Ubuntu (Lucid Lynx). Please find  the details below that I copy from a post to somewhere else. I should *sound *familiar...
Any expert here to tell why this happens?


After  recent issues (the configuration seemed to work perfectly until a  recent upgrade), I got Skype (version 2.2) not giving any sound out any  more. The issue was indeed linked to Skype since other applications  (Rythmbox, Audacity, Soundrecorder) did continue to show the global  sound system did worked (with Pulseaudio, version  1:0.9.22~0.9.21-63-gd3efa-dirty, running by default).
I have been  since a few years using Lucid Lynx (Ubuntu 10.04) with a kernel upgraded  upto 2.6.32.42, on an AMD 64 machine with an NVidia do-it-all  video/sound coprocessor -ALC888). Considering this, I thought that maybe  some recent upgrade was making old Skype not compatible.
I tried to switch to a newer Skype version (4.0) to no better result.
After  fighting hours and browsing some tens of pages, I stumbled on the same  article quoted in the thread  ([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)).
The "killall pulseaudio" did my day! 
I  started being able to see something else in the sound configuration  panel of Skype than the only "PulseAudio server (local)" stuff and choosing  the very first in the list made it work. I got intrepid enough to launch  again pulseaudio from a terminal, reconfigure the sound source/sink/events under Skype  to <pulse> and had the pleasure to see it worked also.
Unfortunately,  the thing seems to be both stable and unstable: quitting Skype showed  again the same tiny "PulseAudio server (local)"-only list when  restarting it with pulseaudio already running :(. On the contrary,  killing again pulseaudio before launching Skype and relaunching  pulseaudio afterwards (skype already running) would bring you again the  better of both worlds :confused:.
I think thus that the case is not yet  closed and there is something yet to be understood. That way, I  eventually won't be needing a launcher that first kills all pulseaudio items,  then launches skype and only then relaunches pulseaudio...:guitar:

All and any help welcome.

---

