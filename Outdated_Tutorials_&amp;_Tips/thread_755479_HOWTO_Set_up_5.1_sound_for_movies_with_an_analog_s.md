---
title: "HOWTO: Set up 5.1 sound for movies with an analog surround sound card (ALSA)"
date: 2008-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Afkpuz on 2008-04-14
I know there are alot of people trying to get 5.1 surround sound to work in Ubuntu.  It's actually pretty easy, but took me a long time to figure it out.  Here are the specs for this guide.

1.) Your sound card has analog output 

2.) It actually has a plug for front, rear, center/woof speakers (5.1 not 7.1 or anything else)

3.) You're using ALSA 
**EDIT** I have confirmed that this method works in Hardy heron as well, so PulseAudio doesn't seem to cause any trouble with this method.

4.) You can get sound out of the card, just not surround sound


*********************The Hopeful Result**************************************
You'll have surround sound for your movies and any audio program that uses ALSA will out put stereo sound through all of your speakers with the woofer handling bass appropriately




I did read somewhere that ALSA can be made to output through pulse audio, but this is a straight up ALSA guide.


So, from a fresh install of 7.10, you'll have ALSA already installed.  You just need to configure it.


Open a terminal and check if your sound card is detected

```
asoundconf list
```

Note the name of your sound card.  In my case, it was called "Audio"  

Then, set your sound card to be the default card for ALSA
```
asoundconf set-default-card cardname
```
Where "cardname is replaced with your cards name.  So for me, I typed in "asoundconf set-default-card Audio"

Now, enter this to edit your ALSA config file
```
sudo gedit ~/.asoundrc
```

Whatever is in there, empty or not, paste this in at the bottom
> pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}

That should do it for ya.  It did for me on a fresh install.  Now test your glorious sound!  try out rhythmbox.  you should get sound from all your speakers.  Now, try watching a movie.  I only use VLC, so I'll tell you how to get 5.1 in that.  Make sure vlc is set to use ALSA and your soundcard in Edit>Preferneces.  Then, play your movie, and once the movie is actually playing, select Audio>Audio Device>5.1


Enjoy!

---

### Post by SR_ELPIRATA on 2008-04-19
Well, it most definitely not work with me :(

No sound at all on the other channels, but is ok, I kind of expected it, it was my last resort. Now is off to get a 5.1 card as it seems that Ubuntu wont be able to use my onboard 5.1 audio.

ELP

---

### Post by Afkpuz on 2008-04-20
I'm sorry to hear that.  If you're in the market for analog 5.1, I can recommend the card I use.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16829126101](http://www.newegg.com/Product/Product.aspx?Item=N82E16829126101)

It's small, usb, has 2 line ins, and is only $20!!  

I know for sure that this card will work with the above steps.  If you're not looking for digital sound, you might give this one a try.

---

### Post by SR_ELPIRATA on 2008-04-20
Yeah, I read about that USB option some days ago, I think it was you who posted about it. Im looking for something more professional though not too expensive, I've heard wonders about the M-Audio Revolution and just want to confirm them.

At $20 though, the GWC is a nice option which I will consider.

ELP

---

### Post by dublued on 2008-05-02
I have Asus M2NPV-VM mobo with integrated 5.1 surround.  i'm using dell 5.1 surround speakers

i tried your method and when i listed my devices, it lised NVidia and UART

i did your method for NVidia but it did not work for me.  When I do the speaker-test, it works perfectly fine.  all the speakers are called out properly from their respective speaker.  But i can't for the life of me get the surround to work with mp3's or movies.

any other ideas?  i've tried it many different software including vlc and audacious but no luck

---

### Post by victorgreen on 2008-05-04
I have that EXACT GWC usb sound card. It worked fine with tweaking in fiesty and gutsy, but I CANNOT make it work in Hardy, even with your instructions. Setting everything to in sound preferences in VLC and Ubuntu and with the computer only detecting the 1 USB sound card:

```
aplay -l 
```

> 
**** List of PLAYBACK Hardware Devices ****
card 1: Audio [USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I get this infernal list of errors. 

> 
VLC media player 0.8.6e Janus
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM surround51
[00000349] pulse audio output error: Failed to connect to server: Connection refused
[00000349] pulse audio output error: Pulse initialization failed
[00000349] jack audio output error: failed to connect to JACK server
[00000349] oss audio output error: cannot open audio device (/dev/dsp)


HOWEVER, Amarok will play stuff fine, but only from my front speakers!!! Im totally at a loss, please help!!

---

### Post by victorgreen on 2008-05-04
Oh and Im running Hardy 64bit and I had it import my setting and files, etc when I installed it. I have since recompiled alsa and alsa utils to no avail.

---

### Post by victorgreen on 2008-05-04
I finally have sound coming out of my 4 speaker sets!!

1. Clean install of Hardy64 with nothing imported
2. In sys==>prefs==>sessions uncheck pulse audio manager
3. in sys==>admin==>services check alsa-utils
4. in gnome volume applet change device to USB audio
5. In sys==>prefs==> sound 
           In devices tab: set all to auto-detect, set device to USB audio, select PCM in the box below the device selector 

           In sounds tab UNCHECK ESD 
6. ```
sudo gedit  /etc/modprobe.d/alsa-base
```
     ALSA had blacklisted the module snd-usb-audio for some reason by inserting: > options snd-usb-audio index=-2- DELETE THAT LINE

Instead I blacklisted my onboard audio with
 > options snd-hda-intel index=-2

7. Recompile alsa from source easily with
```
sudo module-assistant a-i alsa-source
```

8. Use Afkpuz's instructions for modifying ~/.asoundrc

9. Reboot and enjoy sound!

---

### Post by dublued on 2008-05-05
thank you Afkpuz and victorgreen...

i now have sound out of all of my speakers!  which is great... but not what i was looking for :D.  first i'll outline how i did it and then the problems i'm having.

I first followed Afkpuz's post to the letter and i still wasn't getting any sound.

victorgreen's post was for the usb sound card but it worked for my onboard sound.

i didn't have to do step 1.  in step 4, i changed the device to HDA Nvidia (Alsa mixer).  I didn't have to do step 6 and 7.  after a reboot, sound is now coming out of all 4 speakers.

now the problem is that it does not decode surround.  i have videos that have surround sound decoded into them but the "surround" doesn't work... but sound comes out of all 4 speakers.

VLC:  now when i try to play the file in vlc it's all choppy and eventually vlc crashes.  also, 5.1 surround does not show up under audio>audio devices... it's only mono or stereo.  same file works fine in Mplayer but still no proper surround

i wonder if there is a fix for that.

thanks!

---

### Post by Afkpuz on 2008-05-07
I should mention that I'm running hardy 32 bit.  It looks like my method doesn't work for the 64 bit version.

---

### Post by victorgreen on 2008-05-07
The best Ive ever gotten has been sound out of my 4 speaker sets. I have them set up 'surrounding' me so for me its good enough. 

As a note- I am running 64bit Hardy. VLC for me plays normal avi's mkv's, etc perfectly fine with sound coming out of all my wonderful little speakers. In my VLC audio preferences, its set to ALSA, default device. Im sorry Im not of more help dublued.

---

### Post by dublued on 2008-05-07
yea i'm running 32 bit hardy also... but on a 64 bit processor.... i heard 64 was a pain so i never went with it.

well i'm sure there is a solution out there... if not, it shouldn't be too far along until one shoes up.  my surround works with speaker-test just fine... so atleast i have that going for me.  just can't seem to get the files to play properly.  i'm going to try a dvd since i haven't tried that yet and i'll post

---

