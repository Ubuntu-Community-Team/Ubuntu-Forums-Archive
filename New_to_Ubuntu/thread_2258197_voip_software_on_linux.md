---
title: "voip software on linux"
date: 2014-12-25
forum: New to Ubuntu
---

### Post by flex567 on 2014-12-25
Which voip software can you recommend for ubuntu linux ?

---

### Post by papibe on 2014-12-25
Hi flex567.

What are you looking for? Something that just works? concern about privacy? committed to open source?

Skype works pretty good. I heard good things about Viber. Both closed source though.

Browser tools: Google voice, Hangouts.

For an open source client take a look at Jitsi.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Lars Noodén on 2014-12-25
+1 for Jitsi

Linphone works well for me, too.  Ekiga works too but Jitsi is definitely better.

---

### Post by flex567 on 2014-12-25
The skype doesn't work, Viber is just for Ubuntu 64 bit and I think jitsi aslo doesn't work - It won't start. I can send text messages with Skype but I can't use video or voice.

I will try linphone

---

### Post by ajgreeny on 2014-12-25
What you have to use will depend on what the people you wish to speak to use; if they use skype you have no alternative but to also use skype, because as far as I'm aware, skype will only work with another skype, not to any other VOIP applications.

If you can't get skype to work there is something else wrong with your system, because skype works fine for me on both 32 and 64 bit systems and has done so now for many years, with both video and audio.

What exactly is your skype problem?

---

### Post by flex567 on 2014-12-26
When I connect with somebody that has skype they cannot hear me nor see me they can just see my text messages .

---

### Post by Bucky Ball on 2014-12-26
> **flex567 said:**
> When I connect with somebody that has skype they cannot hear me nor see me they can just see my text messages .

Then you have your Skype audio set up wrongly. Start a test call, open Pulse Audio Volume Control and make sure it is set to output and input to the correct device.

You can also test video via the Skype options.

---

### Post by flex567 on 2014-12-26
When I make a test call I don't hear things I said. That means that something is wrong with my settings? How should I set them?

---

### Post by Bucky Ball on 2014-12-26
As mentioned previously, open Pulseaudio Volume Control, make a test call, and check where the audio stream from Skype is going. If you don't have PAVControl installed, install it from Software Centre.

You need to look in the input tab and make sure that is set to receive input from whatever mic you are using. Check the playback option to make sure that is set to go to the appropriate device (speakers or headphones). 

Don't change anything in the Skype audio options. That is set correctly. You just have the stream going to the wrong device. Once you have sound, we can have a look at the video issue.

PS: Please attach large pics by using Go Advanced and the paperclip icon rather than pasting them into the body of your post. Thanks. I have edited your last post accordingly. ;)

---

### Post by ajgreeny on 2014-12-26
Does your microphone work with other applications; can you record sounds?
Can you hear output from the mic through your speakers?
Does your webcam work with other applications, eg cheese or guvcview?

---

### Post by ajgreeny on 2014-12-26
> Does your microphone work with other applications; can you record sounds?
Can you hear output from the mic through your speakers?
Does your webcam work with other applications, eg cheese or guvcview?
						Can you give answers to these queries from post #11 please;  other applications in Ubuntu is what I was asking, not in Windows.

---

### Post by flex567 on 2014-12-26
> Does your microphone work with other applications; can you record sounds? How can I test that?
> Can you hear output from the mic through your speakers? What is the best way to test that ? 
> Does your webcam work with other applications, eg cheese or guvcview? I installed the guvcview and I successfully recorded a video with sound.

---

### Post by Jonathan Precise on 2014-12-26
> **flex567 said:**
> How can I test that?

Use "gnome-sound-recorder".

If not installed, install by pressing CTRL-ALT-T, and typing there "pkexec apt-get install gnome-sound-recorder", no quotes, using CTRL-C to copy from Firefox/Opera/Chromium/Whatever, and SHIFT-CTRL-V to paste into the terminal.

> **flex567 said:**
> What is the best way to test that ?

Once you save the recording, try and play it with your music player/video player.

-Jonathan

---

### Post by Bucky Ball on 2014-12-27
> **flex567 said:**
> 
 I installed the guvcview and I successfully recorded a video with sound.

Then it sounds like all is fine. You just need to get the Skype audio stream directed to the correct device with PAVContol. Perhaps open PAVControl while you are using something that works (guvcview) and see where that is being directed, then make a test call with Skype and replicate it.

---

### Post by flex567 on 2014-12-27
> Then it sounds like all is fine. You just need to get the Skype audio  stream directed to the correct device with PAVContol. Perhaps open  PAVControl while you are using something that works (guvcview) and see  where that is being directed, then make a test call with Skype and  replicate it.

how do I do that?

---

