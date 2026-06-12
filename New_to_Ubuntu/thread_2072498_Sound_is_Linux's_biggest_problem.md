---
title: "Sound is Linux's biggest problem"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-10-17
I recorded sound off the internet with Sound Recorder.

When I play back the sound the volume is too low. 

Adjusting the volume control doesn't change things.

Using alsamixer to put the "capture" bars higher puts an awful buzz into the sound.

I'm aware that sound is Linux's biggest problem and hope there is an app that will just do it all for me and save me endless mucking around in the terminal.

Or failing that ...

---

### Post by shreepads on 2012-10-18
How exactly did you record "sound off the internet with Sound Recorder"?

What was the sound source?

---

### Post by Kevin McCready on 2012-10-18
source was youtube

From the menu in Lubuntu, accessed at the bottom left of the screen, I clicked on the Sound and Video menu, then on Sound Recorder. I then clicked on the red button in Sound Recorder.

---

### Post by shreepads on 2012-10-18
If I got that right, Sound Recorder was recording from your mic the audio played out from your speaker...

If so, this route would never give you good quality audio (no matter what OS) and boosting the volume of poor quality audio will always give you a.. erm... buzz.

Ideally you should save the digital audio source from youtube direct to file for good quality. Either try one of those tools that allow you to download youtube video and then extract the sound, else try Jack...

---

### Post by Peripheral Visionary on 2012-10-18
Yes, you recorded the sound emitted from your own speakers and picked up by your microphone (which added the buzzing noise).  Been there, done that too.

If there's a sound source you want to save, the only real way to do that - in Linux or Windows or BSD or Mac or any other OS - is to save the file to your computer or to some external media.

---

### Post by ianhawke on 2012-10-18
With so many services over the net converting videos of u2b in audio, why would you not use one of those and instead use a method that has never been any good?

If you need a hint, google for youtube to mp3... :guitar:

---

### Post by Grenage on 2012-10-18
I imagine the OP is probably recording via a master output, rather than a microphone....

---

### Post by buckyaustin on 2012-10-18
Doing what you did would cause your computer to lagg thus reducing sound quality. Something you don't want to do. Your going to have to find a different way to the same thing. Thus getting quality. 

But I think your are correct. I have been using Linux for years and looking back over the years there is only one constant problem and that was sound. Even now im plaqued with sound errors. 

I never keep sound above 90% in Linux just so I can keep the quality to a acceptable level.

---

### Post by Kevin McCready on 2012-10-18
thanks everybody.

When I used to run the old bloated legacy operating system OBLAS (Windows) I used Total Recorder which, as I understand it, picked up the signal directly from the sound card before it went to the speakers. I find it a bit hard to believe that linux can't do the same thing. So the idea that I'm recording off the speakers ... well I'm not too sure.

In Sound Recorder, there is a box which says:
Record from input:
This is selected to "Master". In fact there is no other choice in the drop down box.

Thanks for the youtube to mp3 hint, but I'm left with the same problem when I want to record off other websites.

---

### Post by nothingspecial on 2012-10-18
Saving media from youtube to your hard drive is against their ToS and not supported here. So long as the thread continues as a general sound capture question that's fine. If not it will be closed.

You have to get the capture level in alsamixer right. For example, when recording my LPs I find that a Capture level of 44 is perfect with the mic boost turned all the way down (but not muted). Much higher than that and I get the "buzz".

Experiment.

---

### Post by Lisiano on 2012-10-18
Gnome Sound Recorder will only display inputs from your default input. If you wish to force it to record from another source, you may try using [pavucontrol](apt://pavucontrol). In the Recording tab you may tell Sound Recorder (While it's recording) to "listen" to a different input (It will remember what it was listening to so you won't need to configure it again).

For example to listen to a monitor (A monitor is a virtual input which "inputs" whatever is being outputed to the device), just start Sound Recorder, hit record, tell Sound Recorder from inside pavucontrol to listen to a monitor (Example: Monitor of Built-in Audio Analog Stereo), then Sound Recorder will record what the monitor "hears", or to be more precise, what is being played back on whatever device whose monitor you are listening to.

Also a great application for audio recording and mixing is [Audacity](apt://audacity). It will let you pick a monitor from inside it.

EDIT: Per say, audio is not a very big problem in Linux. It can do WAY more stuff than you can in Windows, for example using that same pavucontrol, you can loopback music being played on your PC to Skype, all the while mixing in your own voice so the other party can hear you. Or doing crazy voice manipulation in real-time using [sox](apt://sox). Like adding an chorus effect and modifying your pitch (While again, adding music and piping it all to Skype).

Hope I helped.

---

### Post by Kevin McCready on 2012-10-18
thanks again
but I need a PhD in recording before I can use Audacity. A search in title on this website finds nothing for "configure audacity".

When I finally found out where in the menu (Edit, preferences) I could begin to configure it, I was faced with a bewildering array of options under devices, recording, defaults etc etc.

All I want to do is set up to record of the internet (not youtube, no of course not, I wouldn't even think about it, I wouldn't even think about it for fair use, I wouldn't dare think about it in case even thinking about it upset the recording industry).

So I still say sound is Linux's biggest problem. It's all very well being the master of the universe but if you're not in the driver's seat .... In fact I'm reminded of when I first tested linux 15 years ago and gave up because it was too technical. I haven't got much hair left now.

---

### Post by Lisiano on 2012-10-18
> **Kevin McCready said:**
> thanks again
but I need a PhD in recording before I can use Audacity.
My friend is taking courses to become a proper DJ, one of the basics was the ability to use Audacity. So yeah, there are courses on how to use it if you are interested.

On a more serious note: Linux will only get as technical as you wish it to get, if you need it to only do a simple task, it will do that task without asking many questions, but as soon as you start going out of the norm and try to make Linux (Or Windows) do something that is not for beginners, then there will be questions you will need to answer before your OS will know what you want. 

Monitor/Output recording is a simple enough task and I understand if someone can't grasp new concepts very fast, but blaming the tools that provide you with the power to learn and grasp those concepts just because you don't get them on the first go, is low. 

*Sigh*... Sorry if I offended you in any way, needed to vent.

We can and will help those who are open to learn new concepts, but we can't help unless you wish to be helped.

If you want, I can make a simple tutorial with step-by-step screenshots on how to record from a monitor, but please: stop blaming the tools.

---

### Post by Kevin McCready on 2012-10-18
I see your point, but raise you one. Total Recorder was simple to use. Yes I would love some advice as to how to record from the internet with audacity.

---

### Post by Lisiano on 2012-10-18
And I raise you the fact that Total Recorder is a paid application, while Linux can perform these actions for free and out of the box (pavucontrol is not needed, but it does simplify things).

I'll make a pictorial explaining how to record monitors with Audacity in a moment.

---

### Post by mike acker on 2012-10-18
> **Lisiano said:**
> And I raise you the fact that Total Recorder is a paid application, while Linux can perform these actions for free and out of the box (pavucontrol is not needed, but it does simplify things).

I'll make a pictorial explaining how to record monitors with Audacity in a moment.

me subscribing to this thread. i've been using Audacity Windows version with a Bheringer CODEC for a while now. I expect the Linux version to be pretty much the same.  I have REALTEC audio on my motherboard; that should work just fine, particularly as my new monitor isn't going to have built in speakers. the 'puter will need to be hooked up to the amp anytime i want sound

---

### Post by Lisiano on 2012-10-18
[LIST=1]
[*]Let's get some music going, shall we?
[IMG]http://ubuntuone.com/239mgXCmTsNBHebxz4pDPX[/IMG]
[*]Now that we have some music to listen to, let's go and start up Audacity and hit Record.
[IMG]http://ubuntuone.com/63pnw8TDpLMklwyIGQGCe5[/IMG]
Wait, nothing's happening, it's not recording at all... Well, it is, just not from my music.
[*]Let's fix that and open up pavucontrol (Alt+F2 -> pavucontrol)
[IMG]http://ubuntuone.com/6LNxR0LceQl0a3CJNqnrX9[/IMG]
Now, I don't want to listen to my Webcam or my Microphone, I want to "hear" what my computer is playing instead. So I pick a monitor.
[*]Now we should check back on Audacity
[IMG]http://ubuntuone.com/6XfWK24ZgZPdREoQ6ea2Ek[/IMG]
Oh hey! I see waveforms! It's recording my music now!
[*]But wait. Maybe I'm just playing tricks and just saying stuff in the microphone?
[IMG]http://ubuntuone.com/5G25jTRjIoV3R4ULFKPImv[/IMG]
Nope, music still playing.
[/LIST]

Oh, to export from Audacity, go File -> Export

---

### Post by Lisiano on 2012-10-18
> **mike acker said:**
> me subscribing to this thread. i've been using Audacity Windows version with a Bheringer CODEC for a while now. I expect the Linux version to be pretty much the same.  I have REALTEC audio on my motherboard; that should work just fine, particularly as my new monitor isn't going to have built in speakers. the 'puter will need to be hooked up to the amp anytime i want sound Not sure what you are expecting from the pictorial. And yes, Audacity in Windows is the same as Audacity in Linux. Bar the fact Windows doesn't have Pulseaudio or Jack but still.

Oh, this recording is lossless in the sense that there is nothing lost between what is being outputted and what is being recorded. There might be loss from Pulse mixing audio but I don't notice anything since I'm not an Audiophile, they might not notice it either.

---

### Post by shreepads on 2012-10-18
> **Lisiano said:**
> 
Let's get some music going, shall we?

Oh, to export from Audacity, go File -> Export

Excellent, bookmarked!

---

### Post by Kevin McCready on 2012-10-19
Huge thanks to Lisiano! Now sorted. 

The problem was that it was indeed recording from both the external microphone and the sound card at the same time. I changed the recording input to "Monitor of Internal Audio Analog Stereo" and it worked fine. I had to open pavucontrol from the terminal though.

You're right too about Total Recorder. I bought it so long ago, I'd forgotten I'd paid for it. It remains to this day the only unbundled software I've ever shelled out for - and long may it reign so. But I think this also shows how keen people are for sound and I still think Linux apps need more work to make them friendly to non-geeks. Who would have guessed that the difference between "Monitor of Internal Audio Analog Stereo" "Internal Audio Analog Stereo" was an external microphone.

Anyway, thank you again. You've been very patient with me.

---

### Post by Kevin McCready on 2012-10-19
PS Ta for the uplifting intro to Project Twin

---

### Post by Lisiano on 2012-10-19
You're welcome.

Remember, a monitor is a virtual input and it is created for EVERY output you have, even virtual outputs. You can record any output this way.

Also for the best recording quality, set both, the recording volume and the playback volume, to 100%. This way the audio will maintain it's volume and there won't be any clipping.

---

### Post by SHULTZIE on 2013-02-17
Thank you Lisiano,
GREAT SOLUTION!  Your detailed and graphic explanation was the key to help me solve this.

Today is my second day as a Linyx Ubuntu user (Migrating from Windows) and it only took me 6 hours to resolve this (My most challenging fix).  If it wasn't for you, I might have given up on Ubuntu.:wink:

May I also pass an editorial regarding FREEWARE?  I paid $40 for Total Recorder in 2003 and have been using it (with free updates) since.  It only took me 10 min's to lock, load and shoot my first recording.  It's been a staple for many projects since.  Amortizing that cost over this many years is like it was free (compared with the incredible power it has over current solutions, I might still see a need to keep windows around).   Free isn't free if it costs you in time to figure out and maintain.  I would be happy to pay for software that is as easy, powerful, useful and long lasting as Total Recorder was.  Who wouldn't.

Thank you to all the developers working hard to provide clean sleek and useful projects.  I'm excited to be involved with this community.
:p

---

