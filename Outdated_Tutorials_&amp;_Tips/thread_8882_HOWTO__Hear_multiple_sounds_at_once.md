---
title: "HOWTO:  Hear multiple sounds at once"
date: 2004-12-22
forum: Outdated Tutorials &amp; Tips
---

### Post by varunus on 2004-12-22
This one seems to stump most linux newbies..."Why can't I hear sounds from two applications at once?"  This is because your sound card requires something called "software mixing."  Thankfully, ALSA provides software mixing, so this shouldn't be very hard.

The first thing to do is install the package libesd-alsa0.  Use synaptic, a sudo apt-get install, or whatever.  Its available in the Ubuntu repositories.

Then, create the following file using "sudo gedit" or your favorite text editor, and save it as /etc/asound.conf.  (Make sure you use sudo, you need root priviledges to do this.)

pcm.card0 {
    type hw
    card 0
}

pcm.!default {
        type plug
        slave.pcm "dmixer"

}


pcm.dmixer  {
    type dmix
    ipc_key 1025
    slave {
           pcm "hw:0,0"
           period_time 0
           period_size 1024
           buffer_size 4096
           periods 128
           rate 44100
    }
    bindings {
           0 0
           1 1
    }
}

(the above file should work with most sound cards...I've tried it with 3 different ones with success.  I can't guarantee it'll work in all cases, though.)

Next, execute a "sudo gedit /etc/esound/esd.conf" and change the file to the following:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

Next, go to your Sound control panel in Gnome and enable sound server startup.  After this, go to your Multimedia Systems Selector control panel and set it to either ALSA or ESD.  Then, reboot your computer.

After doing this, you can set any application to use alsa or ESD, and you'll hear multiple sounds at once!  No more problems playing games that use ALSA and hearing sounds from a Gnome app that uses ESD...

---

### Post by ubuntu_demon on 2004-12-22
[QUOTE=varunus]This one seems to stump most linux newbies..."Why can't I hear sounds from two applications at once?"  This is because your sound card requires something called "software mixing."  Thankfully, ALSA provides software mixing, so this shouldn't be very hard.

The first thing to do is install the package libesd-alsa0.  Use synaptic, a sudo apt-get install, or whatever.  Its available in the Ubuntu repositories.

Then, create the following file using "sudo gedit" or your favorite text editor, and save it as /etc/asound.conf.  (Make sure you use sudo, you need root priviledges to do this.)

pcm.card0 {
    type hw
    card 0
}

pcm.!default {
        type plug
        slave.pcm "dmixer"

}


pcm.dmixer  {
    type dmix
    ipc_key 1025
    slave {
           pcm "hw:0,0"
           period_time 0
           period_size 1024
           buffer_size 4096
           periods 128
           rate 44100
    }
    bindings {
           0 0
           1 1
    }
}

(the above file should work with most sound cards...I've tried it with 3 different ones with success.  I can't guarantee it'll work in all cases, though.)

Next, execute a "sudo gedit /etc/esound/esd.conf" and change the file to the following:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

Next, go to your Sound control panel in Gnome and enable sound server startup.  After this, go to your Multimedia Systems Selector control panel and set it to either ALSA or ESD.  Then, reboot your computer.

After doing this, you can set any application to use alsa or ESD, and you'll hear multiple sounds at once!  No more problems playing games that use ALSA and hearing sounds from a Gnome app that uses ESD...[/QUOTE]
 Why isn't software mixing enabled by default ? And don't most current audio cards / audio chips support hardware mixing ?

---

### Post by Hikaru79 on 2004-12-22
> After this, go to your Multimedia Systems Selector control panel and set it to either ALSA or ESD.

Where would one find this? It's not in my Multimedia menu. Is there a command line for this?

---

### Post by lameaim on 2004-12-22
[QUOTE=Hikaru79]Where would one find this? It's not in my Multimedia menu. Is there a command line for this?[/QUOTE]
gstreamer-properties

---

### Post by CowPie on 2004-12-22
[QUOTE=Hikaru79]Where would one find this? It's not in my Multimedia menu. Is there a command line for this?[/QUOTE]
 Hi, use this to access control panel

gnome-control-center --use-shell

Can also place a shortcut in Nautilus application:///

---

### Post by iwasbiggs on 2004-12-23
[QUOTE=demon666_nl]Why isn't software mixing enabled by default ? And don't most current audio cards / audio chips support hardware mixing ?[/QUOTE]

Nope. A lot of cheap ones that come onboard do not.

---

### Post by ubuntu_demon on 2004-12-23
[QUOTE=iwasbiggs]Nope. A lot of cheap ones that come onboard do not.[/QUOTE]
 So why isn't hardware mixing enabled by default ? And if it is unknown whether the card/chip supports it then switch automatically to software mixing.

---

### Post by piedamaro on 2004-12-24
I don't know why, but it's enough to said that in the alsa's faqs they still mention they don't have software mixing and it will never be implemented!!
Yeah, I love this hacker non-sense :P

---

### Post by baylisscg on 2004-12-24
Thanks this works great on my nForce soundcard. However, it needed a couple of tweaks.

 1. I used hw: 0,2 to output through the SPDIF.
 2. Using > -d default caused crackling and pops in anything played back through the esd. Using > -d <device default points at> dmixer in your case fixed that.

I'm stuck with GStreamer using esd though as setting it to use ALSA caues it to lock up.

---

### Post by varunus on 2004-12-26
I can see why you would need to use 0,2 for your soundcard...some computers have the modem or some other device set as 0,1 so this would cause problems for you..  But having to use dmixer instead of default is kind of odd...I've never had to do that before to get clear sounds through ESD.  (I've used this exact setup on several different computers...this is mostly needed with cheap integrated soundcards.)  For gstreamer, do you have gstreamer0.8-alsa (I think that's the name of the package) installed?

DMIX is the plugin for ALSA that allows software mixing...it comes standard with ALSA, so I don't know why the ALSA website would say they don't support software mixing.  This HOWTO is written mostly from the DMIX howto over at the ALSA site!  Of course, that one goes into much more detail...

---

### Post by izmaelis on 2004-12-27
I followed these instructions and everything worked fine except that sound in some apps (gnome system notification sounds, rhythmbox...) was very cracky. What's wrong?

---

### Post by kurros on 2004-12-28
Thanks for this HOWTO!

I had to use "-d dmixer" instead of "-d default" in esd.conf as well on my nForce3 board to avoid crackly/buzzy audio.

My problem is that Crossover Office using winealsa.drv still will not output sound if "Enable sound server startup" is checked.

Edit: Okay it seems that the -d default is the critical component here, as setting it to that and turning on the soundserver, ALSA works. I guess the problem we need to figure out is why it screws up the audio.

---

### Post by baylisscg on 2004-12-29
[QUOTE=varunus]I can see why you would need to use 0,2 for your soundcard...some computers have the modem or some other device set as 0,1 so this would cause problems for you..  But having to use dmixer instead of default is kind of odd...I've never had to do that before to get clear sounds through ESD.  (I've used this exact setup on several different computers...this is mostly needed with cheap integrated soundcards.)  For gstreamer, do you have gstreamer0.8-alsa (I think that's the name of the package) installed?[/QUOTE]

  0,2 is the SPDIF output. When using default all sounds played back through ESD were crackly. I did install gstreamer0.8-alsa but any attempt to point gstreamer at ALSA causes the application trying to use ESD to crash. For example if I set the audio sink to ALSA in gstreamer properites and hit the test button I get a brief tone followed by gstreamer crashing. This sort of thing has locked up gnome on occasion :sad:

As far as I'm aware the !default bit just redirects the card to the mixer, stop me if this is nonsense, so why this would cause problems is odd. If I direct audio directly to ALSA's default device, through xmms or alsaplayer, it plays fine. 

[QUOTE=varunus]DMIX is the plugin for ALSA that allows software mixing...it comes standard with ALSA, so I don't know why the ALSA website would say they don't support software mixing.  This HOWTO is written mostly from the DMIX howto over at the ALSA site!  Of course, that one goes into much more detail...[/QUOTE] 

I read that and some of the other HOTOs but the whole thing is a bit of a mess. Right now OSS playes back though the analouge speakers and everything else through the SPDIF. Although, right now I have bigger problems so sound will have to wait for a bit.

---

### Post by adroit on 2004-12-30
I lost the sound completly..

I dont  know why... I follow the instructions and check it... Now I dont know what to do for have sound...

please help me...  :sad:

---

### Post by Vaportrail on 2005-01-08
I fixed the crackling by setting rate to 48000, my .asoundrc:

# ~/asoundrc

pcm.card0 {
	type hw
	card 0
}

pcm.!default {
	type plug
	slave.pcm "dmixer"
}


pcm.dmixer {
	type dmix
	ipc_key 1025
	slave {
		pcm "hw:0,0"
		period_time 0
		period_size 2048	#1024 old crackling setting
		buffer_size 32768	#8192 old crackling setting
		rate 48000
	}
	bindings {
		0 0
		1 1
	}
}

		0 0
		1 1
	}
}


EDIT: OK weird! Having rate set to 48000 makes system sounds crackl and having set it to 44100 makes playing videos in xine crackl :|

EDIT 2: Finally got it without any crackls!
    Changed period_size to 2048
    Changed buffer_size to 32768

---

### Post by kurros on 2005-01-16
[QUOTE=Vaportrail]
EDIT 2: Finally got it without any crackls!
    Changed period_size to 2048
    Changed buffer_size to 32768[/QUOTE]


Awesome! Thanks.

---

### Post by stoffe on 2005-01-20
This seems to work just fine, thanks for the tip!

Would be real cool if this was set by default, or at least possible to enable easily... this is usually a mystical and terrifying area to explore. ;)

---

### Post by piedamaro on 2005-01-20
For those who have problems, should be noticed that everything works fine only if you use ALSA-based esd (for desktop sounds and mozilla) and sdl (for games). You should find them in the universe. ;)

---

### Post by RunningWild on 2005-01-21
it doesn't work with me... i'm using the audio device that comes with my Nf7-s 2.0, and if I try your tips sounds in vlc, etc doesn't work :(

---

### Post by piedamaro on 2005-01-26
[QUOTE=RunningWild]it doesn't work with me... i'm using the audio device that comes with my Nf7-s 2.0, and if I try your tips sounds in vlc, etc doesn't work :([/QUOTE]
 Vlc needs to use alsa outut to work, I haven't tried it, sorry.

If someone has problem with no sound in mozilla/firefox/epiphany with this setup on hoary, I've found that firefox seeks for libesd.so.1 at startup while there is only libesd.so.0.
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1 should solve the problem :)

---

### Post by Lifer on 2005-01-27
When I go into the multimedia selector menu, sound won't test with ALSA or ESS, only ESD :(

---

### Post by akurashy on 2005-01-29
i cant heard multiple sounds anyway O_o
i followed the instruction totally

---

### Post by rapala61 on 2005-01-29
it works really good here :D ... followed ur steps , with some modifications seen in this same thread so the final code i used was as this 8-) :
 
```

[CENTER]**/etc/asound.conf**[/CENTER]


pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"

}


pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 1024  // **changed to 2048**
buffer_size 4096   //     ** "          " 32768**
periods 128   //** I erased this line as i saw on this thread**
rate 44100   //   ** 48000**
}
bindings {
0 0
1 1
}
}

[CENTER]** /etc/esound/esd.conf**[/CENTER]


[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default  //   **-d dmixer**
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=


``` 
 :!: 
I also had to install (DONT REALLY REMEMBER) libesd-alsa0, libsdl1.2debian-alsa and vlc-pluging-alsa to use vlc ....   I had to reinstall Ubuntu for other reasons thats why i dont exactly remember what packages i installed , but that should be about right...  I was usin Hoary tho.. i haven't re- done this in Warty .. ill find out later...

After u change settings in Multimedia System Selector dont forget to reboot (Obviuously!! :mrgreen: ).

Mainly tested with alsa tho, didnt test ESD...

Specs :   Onboard Audio  on Abit NF7-S v2
               Overclocked 2500+ @ 3200+ 1.84 v.


EDIT: YEAH.. CONFIRMED THAT JUST WORKED FOR ME WHEN I UPDATED TO HOARY... DIDNT WORKED ON WARTY

---

### Post by piedamaro on 2005-01-30
[QUOTE=rapala61]
After u change settings in Multimedia System Selector dont forget to reboot (Obviuously!! :mrgreen: ).[/QUOTE]
Do you reboot everytime you change something? That was windows...:D
You should need to reboot linux only if you want to load a new kernel, i.e. a new linux.
In the worst case you have to log out and back from gnome.

---

### Post by rapala61 on 2005-01-30
[QUOTE=piedamaro]Do you reboot everytime you change something? That was windows...:D
You should need to reboot linux only if you want to load a new kernel, i.e. a new linux.
In the worst case you have to log out and back from gnome.[/QUOTE]


 8-[  I just cant help to think i need to restart to make changes effective...   :mrgreen: 
  Thanks to Winblows...

---

### Post by viuks on 2005-01-30
Great HOWTO  =D> 
It was reary big problem for me. I used about half year mepis before, and there was no  such problems with sond. This is my 2 day on ubuntu, and after I solwed this sound problem I can say, it is great distribution.

---

### Post by ctt1wbw on 2005-01-30
I've followed every how-to here and they all work.  Thanks!

---

### Post by clparker on 2005-01-30
After living with the sound problem for like a month, I finally buckled down and followed this walkthrough to the t and it worked like a champ.

---

### Post by rapala61 on 2005-01-30
I started to have problems with the  sound.. dont know y... but i found this other thread and it might be usefull to some of us here... it really was for me as i added that code to my /etc/asound/conf.  [A software mixing code for a NF7-S 2](http://forums.gentoo.org/viewtopic.php?t=168223&highlight=dmix) . ;)

---

### Post by Saibei on 2005-02-01
I've tried near every configuration listed, and *still* cannot get multiple sounds :(

My ultimate goal is to use mplayer (either streaming audio, local audio, or local video) and hear other sounds (gaim, etc) at the same time.

Using the onboard sound of the NF7-S rev2

---

### Post by rapala61 on 2005-02-02
Are u using Warty, cuz i couldnt get the code to work on warty...  u shouldnt have problems with the board u have, i got the same chipset and its working here... i think u might be missing some packages, try installing alsa-base, libesd-alsa0 libsdl1.2debian-alsa... then u follow the step to change ur multimedia option to alsa...
just make sure avery application that uses sound its using alsa as default  or  the software mixing wont work while the app is running..

NOTE.. i used the asound.conf from the link i posted her just 3 threads before.. and changed the rates to the one posted here...

---

### Post by Saibei on 2005-02-02
[QUOTE=rapala61]Are u using Warty, cuz i couldnt get the code to work on warty...  u shouldnt have problems with the board u have, i got the same chipset and its working here... i think u might be missing some packages, try installing alsa-base, libesd-alsa0 libsdl1.2debian-alsa... then u follow the step to change ur multimedia option to alsa...
just make sure avery application that uses sound its using alsa as default  or  the software mixing wont work while the app is running..

NOTE.. i used the asound.conf from the link i posted her just 3 threads before.. and changed the rates to the one posted here...[/QUOTE]

Hrmm. I reinstalled the packages you mentioned along with alsa-oss, and now I can play local audio files with parallel sounds, and local video without parallel sounds, mplayer however throws the error "Could not open/initialize audio device -> no sound." but plays video just fine with sound. Rhythmbox throws the error "There is no element present to handle the stream's mime type audio/mpeg" when trying to listen to streaming audio.

asound.conf:
```
pcm.card0 {
	type hw
	card 0
}

pcm.!default {
	type plug
	slave.pcm "dmixer"
}


pcm.dmixer {
	type dmix
	ipc_key 1025
	slave {
		pcm "hw:0,0"
		period_time 0
		period_size 2048
		buffer_size 32768
	rate 44100
	}
	bindings {
		0 0
		1 1
	}
}
#Note: a rate 48000 setting sounds buzzy
```

esd.conf:
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d dmixer
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

Summary:
-I can play local audio files (flac/mp3) via xmms, but only flac via rhythmbox, and streaming audio ([www.somafm.com/groovesalad.pls](www.somafm.com/groovesalad.pls) for example) I cannot play at all. With no asound.conf and the default esd.conf I can play streaming audio via mplayer, but not at the same time as other sounds.
-I cannot play any audio on websites ([www.badgerbadgerbadger.com](www.badgerbadgerbadger.com) for example) 
-I cannot play sound with mplayer, but video works fine.

To revise my goal: to have a centralized program to suit all of my media needs and be able to hear other sounds at the same time.

---

### Post by rapala61 on 2005-02-02
Im working on this.. see if its work.. im on warty tho.. it "works" in hoary , warty is kinda  harder for me to make it work with dmixin.. newb :D ... anyway  heres a very interesting link.. read it and see if it helps

[dmixing](http://gentoo-wiki.com/HOWTO_ALSA_sound_mixer_aka_dmix#Setting_up_ALSA)

---

### Post by rapala61 on 2005-02-03
from what i've been reading, there seems to be a problem with alsa and gstreamer,  i have it working with ESD  here..  it mixes sound although it doesnt sound that good as alsa did when it was working...

---

### Post by NeoChaosX on 2005-02-04
I've got it working Warty with local files (music in XMMS, video in Totem) , but not with online stuff (for instance, can't play Flash files in Firefox while playing a local file with XMMS). MPlayer also whines about not being about to access the sound device even when playing a local file, dunno how to change it's output. Using ALSA with no problem.

Dangit, noticed that if I pause a song in XMMS, it won't resume with these settings. It plays for a second, then stops playing.

---

### Post by Arktis on 2005-02-08
This fix gets mplayer and totem to behave and enables me to finally play games like tuxracer and bzflag with sound, but **ONLY** *from the command prompt*.   Still, I'm thankful it actually did anything at all.  It also does **not** allow me to hear multiple sounds at once.  On the upside, flashplayer finally has audio, so I can watch strong bad emails. =p
 
 I'm running Hoary with an nForce chipset.

---

### Post by NeoChaosX on 2005-02-17
Still having pausing problems with XMMS. Most of the time I pause a song in XMMS with these settings, it won't resume when I hit the puse button. When I try to resume, it just stops and I'll have to replay it from the start. Anybody have that problem since applying these fixes?

And still not getting other programs' sound to play nice with MPlayer (EDIT: Or Flash in Firefox that matter).  :-|

---

### Post by jdong on 2005-02-17
I just got this package from ubuntu-desktop in Hoary -- seems like Hoary will ship with this ability!

---

### Post by rapala61 on 2005-02-17
great.... i can listen to music and some mixing in my hoary install but i have no clue how is working..  i dont care for now as im thinking on doing a new install with the Hoary RC or the Release edition.... then ill get down to tweak  the hell out of my install..

---

### Post by NeoChaosX on 2005-02-17
[QUOTE=jdong]I just got this package from ubuntu-desktop in Hoary -- seems like Hoary will ship with this ability![/QUOTE]
Which package are you talking about?

---

### Post by NeoChaosX on 2005-02-19
Ugh. Still having MPlayer problems. Now everytime I start the program, it's ALWAYS muted by default, and I can't get sound in mplayerplug-in with Firefox.  :|  Has anybody else ran into any of the problems I have had, or has it been smooth sailing for the rest of you?

---

### Post by songochain on 2005-02-20
I've problem, synaptic doesnt find libesd-alsa0 so i cant do nothing yet. Here's my source.list
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha amd64 Binary-1 (20050217)]/ unstable main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://es.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://es.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
#deb http://es.archive.ubuntu.com/ubuntu hoary-updates main restricted
#deb-src http://es.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe


```
Thanks

---

### Post by NeoChaosX on 2005-02-21
:-x 

I'm starting to get annoyed by nobody replying. Is there anybody else who has had the XMMS pause/resume problems I have had since I started using this?

And now I'm noticing that if I have libsdl1.2debian-alsa installed, that there's a one-second delay in playing sounds in SDL games. If I switch to libsdl1.2debian-esd, it'll work for about half-an-hour before sound gets scratchy and out of sync as well. Anyone else having these kind of problem?  ](*,)

---

### Post by rapala61 on 2005-02-21
[QUOTE=NeoChaosX]:-x 

I'm starting to get annoyed by nobody replying. Is there anybody else who has had the XMMS pause/resume problems I have had since I started using this?

And now I'm noticing that if I have libsdl1.2debian-alsa installed, that there's a one-second delay in playing sounds in SDL games. If I switch to libsdl1.2debian-esd, it'll work for about half-an-hour before sound gets scratchy and out of sync as well. Anyone else having these kind of problem?  ](*,)[/QUOTE]

I 've had plenty of problems trying to get this to work....  then one of this days it just worked and i dont even want to mess with it anymore.... this is just one of those things that u have to mess with in order to make it work as u want in linux.

stay with esd and save yourself headaches for now, it seems Hoary will be somewhat simplier to have software mixing to work.

I havent tried (polypaudio??) , u might want to go that way.. see if it works for you.

---

### Post by NeoChaosX on 2005-02-21
Acutally, I've managed to get proper pausing working in XMMS/Beep by disabling MMap mode in the ALSA plugins for those programs.  \\:D/  SDL games are the only problem left.

---

### Post by guggi on 2005-02-22
nice howto, this gave me back my microphone

pcm.dmixer { 
    type dmix 
    ipc_key 1024 
    slave { 
        pcm "hw:0,0" 
        period_time 0 
        period_size 1024 
        buffer_size 8192 
   rate 44100 
    } 
  
    bindings { 
        0 0 
        1 1 
    } 
} 

pcm.asymed { 
        type asym 
        playback.pcm "dmixer" 
        capture.pcm "hw:0,0" 
} 


  
pcm.dsp0 { 
    type plug 
    slave.pcm "asymed" 
} 
  
pcm.!default { 
        type plug 
        slave.pcm "asymed" 
} 
  
pcm.default { 
   type plug 
   slave.pcm "asymed" 
} 
  
ctl.mixer0 { 
    type hw 
    card 0 
}

---

### Post by NeoChaosX on 2005-02-25
Just went back to libsdl1.2debian-oss. It's not like I'll need to listen to other apps when play a game. :/

---

### Post by mriya3 on 2005-02-28
For Realplayer

1. Install realplayer as described in [http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)

2. Install **alsa-oss**

3. Open the launcher script **realplay** located in Realplayer's install directory (/opt/RealPlayer if you followed previous instructions)

4. Find lines
```
if [ -n "$LD_PRELOAD" ]; then
    echo "Warning: LD_PRELOAD=\"$LD_PRELOAD\""
fi

```
5. ...and after add this code:
```
LD_PRELOAD="$LDPRELOAD:/usr/lib/libaoss.so"
export LD_PRELOAD
```

---

### Post by herweg on 2005-03-02
Quick question for the OP - did you do this under Warty or Hoary? The instructions worked for me (after some tweaking, I have an odd hardware setup) in Warty, but I'm considering moving to Hoary. However, last time I used Hoary, I had to do a ```
 killall esd 
``` every time I wanted sound from something other than just Gnome system sounds.

---

### Post by rapala61 on 2005-03-02
i thinks hoary is using polypaudio which is working great for me... no need to hack the alsaconf file....

---

### Post by Technoviking on 2005-03-15
[QUOTE=rapala61]i thinks hoary is using polypaudio which is working great for me... no need to hack the alsaconf file....[/QUOTE]
Hoary had to switch back to esound, since the developer could not get polyaudio stable enough. 

This solution will not currently work in hoary with esd, since libesd-alsa0 will not install, it conflicts with libesd.

I have submitted the following bug report.
[https://bugzilla.ubuntu.com/show_bug.cgi?id=7704](https://bugzilla.ubuntu.com/show_bug.cgi?id=7704)

---

### Post by ctt1wbw on 2005-03-16
[QUOTE=mriya3]For Realplayer

1. Install realplayer as described in [http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)

2. Install **alsa-oss**

3. Open the launcher script **realplay** located in Realplayer's install directory (/opt/RealPlayer if you followed previous instructions)

4. Find lines
```
if [ -n "$LD_PRELOAD" ]; then
    echo "Warning: LD_PRELOAD=\"$LD_PRELOAD\""
fi

```
5. ...and after add this code:
```
LD_PRELOAD="$LDPRELOAD:/usr/lib/libaoss.so"
export LD_PRELOAD
```[/QUOTE]

PLEASE make sure you follow step number 2.  I went days and days trying to get MPlayer to work and I didn't have that file installed.  It will save you many headaches.

---

### Post by &lt;Mstaaravin /&gt; on 2005-03-24
Hi, how ferified what is my potin at...?

[QUOTE=baylisscg]Thanks this works great on my nForce soundcard. However, it needed a couple of tweaks.

 1. I used hw: 0,2 to output through the SPDIF.
 2. Using  caused crackling and pops in anything played back through the esd. Using  dmixer in your case fixed that.

I'm stuck with GStreamer using esd though as setting it to use ALSA caues it to lock up.[/QUOTE]

---

### Post by SAMsan on 2005-03-25
THANKS :D

I finally heard the great logon sound of my Ubuntu !!

+++
Samsan.

---

### Post by thinusp on 2005-04-09
[QUOTE=Mike Basinger]Hoary had to switch back to esound, since the developer could not get polyaudio stable enough. 

This solution will not currently work in hoary with esd, since libesd-alsa0 will not install, it conflicts with libesd.

I have submitted the following bug report.
[https://bugzilla.ubuntu.com/show_bug.cgi?id=7704](https://bugzilla.ubuntu.com/show_bug.cgi?id=7704)[/QUOTE]

I instsalled libesd-alsa0 and uninstalled libesd, works fine. According to the description libesd is for OSS (which is emulated by alsa in any case) and libesd-alsa0 is for alsa. Everything seems to work.

Cheers
T

---

### Post by rimmer on 2005-04-10
> After doing this, you can set any application to use alsa or ESD ?
Being new to all this, I'd like to know how would I achieve this ? 

Also following this how to will I be able to execute two instances of say Xmms or even run one instance of Music Player with Xmms simultaneously ?

rimmer
"Better dead than smeg"

---

### Post by kuleali on 2005-04-12
thanks

---

### Post by emmbec on 2005-04-15
Is there a way to know what chipset I'm using??? I ave an Inspiron 8200 laptop computer. I tryed the alsa configuration from the beginin  of this thread but I still hear one sound at a time. Has anyone manage to get it working for this laptop?? thanx

---

### Post by rimmer on 2005-04-16
[QUOTE=emmbec]Is there a way to know what chipset I'm using??? I ave an Inspiron 8200 laptop computer. I tryed the alsa configuration from the beginin  of this thread but I still hear one sound at a time. Has anyone manage to get it working for this laptop?? thanx[/QUOTE]
 Hi If you type > alsamixer in the konsole you should see your card and chipset listed top left.
Providing you installed Alsa.

---

### Post by motionsiren on 2005-05-12
OK, so, as a newbie may I ask...

does dmix replace ESD entirely? Does it have better (or less i suppose) latency? 

Im using VMware > Windows 2k to use some sound apps and sound works, but get choppy and skippy under any decent CPU load.

any tips? I'll try getting dmix going tonight, but im still confused.

---

### Post by Ceebo on 2005-08-31
wtf is the problem?
i did everything what had to and still sound is crackling :|

---

### Post by baylisscg on 2005-08-31
[QUOTE=Ceebo]wtf is the problem?
i did everything what had to and still sound is crackling :|[/QUOTE]
 Hi,

    Well if all else fails. You could try:

   1. If you are using hoary (5.04) and not warty (4.10) try asking in the hoary forum. For example [this thread](http://ubuntuforums.org/showthread.php?t=27684&highlight=sound+crackle) suggests muting channels in ALSA.
   2. Upgrade to hoary, or breezy if you are feeling brave. Breezy is still a development release just now so be careful. I would try the Live CD before commiting to an upgrade. 
   3. Experiment.  period_size, buffer_size and rate in the asound configuration file appear to be critical. Be careful. Read the documentation to see what rules, if any, govern their values. 
   4. If OSS worked OK go back to it and wait for a fix.
   5. If it just won't work consider filing a bug in bugzilla [here](http:///bugzilla.ubuntu.com/). Please follow the guidelines [here](http://bugzilla.ubuntu.com/page.cgi?id=bug-writing.html)

---

### Post by BlueEagle on 2005-09-06
[QUOTE=ctt1wbw]I've followed every how-to here and they all work.  Thanks![/QUOTE]

Would you please be so kind and be more spesific. This would be so very very much better if the reply was:

I've followed every how-to here and they all work on my Creative SoundBlaster 16 ISA card.

Also people saying "This just does not work!" would also stand a much better chance if they tell everyone which hardware it doesn't work on.

Sorry ctt1wbw, nothing particular against you it's just that I had seen enough of these posts for the cup to run over at yours. :)

---

### Post by S.nazari on 2005-09-07
[QUOTE=varunus]This one seems to stump most linux newbies..."Why can't I hear sounds from two applications at once?"  This is because your sound card requires something called "software mixing."  Thankfully, ALSA provides software mixing, so this shouldn't be very hard.

The first thing to do is install the package libesd-alsa0.  Use synaptic, a sudo apt-get install, or whatever.  Its available in the Ubuntu repositories.

Then, create the following file using "sudo gedit" or your favorite text editor, and save it as /etc/asound.conf.  (Make sure you use sudo, you need root priviledges to do this.)

pcm.card0 {
    type hw
    card 0
}

pcm.!default {
        type plug
        slave.pcm "dmixer"

}


pcm.dmixer  {
    type dmix
    ipc_key 1025
    slave {
           pcm "hw:0,0"
           period_time 0
           period_size 1024
           buffer_size 4096
           periods 128
           rate 44100
    }
    bindings {
           0 0
           1 1
    }
}

(the above file should work with most sound cards...I've tried it with 3 different ones with success.  I can't guarantee it'll work in all cases, though.)

Next, execute a "sudo gedit /etc/esound/esd.conf" and change the file to the following:

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

Next, go to your Sound control panel in Gnome and enable sound server startup.  After this, go to your Multimedia Systems Selector control panel and set it to either ALSA or ESD.  Then, reboot your computer.

After doing this, you can set any application to use alsa or ESD, and you'll hear multiple sounds at once!  No more problems playing games that use ALSA and hearing sounds from a Gnome app that uses ESD...[/QUOTE]

Could you also mention somethings about the KDE sound configuration

---

### Post by RSL on 2006-10-10
Is this thread [whose latest post was over a year ago] still valid? With all the changes for Dapper [and soon Edgy] I'm questioning its stickiness. Anyone else?

UPDATE: Nevermind all that mistaken talk about stickiness. I am still wondering if it's valid though.

---

### Post by Pixilarion on 2007-01-20
Thanks for this how-to! It still works in Xubuntu Edgy and saved me after a day of frustration! :)

---

### Post by ph3ar on 2007-11-26
As far as I can see in ubuntu & vmware forum the fix is working only for the workstation version. What about VMware Server 1.0.4 build-56528,
any workaround?

I just open the workstation with vmwareart or vmwaredsp, but again I don't have simultaneous sound in my machine and in the VM. :confused:

---

### Post by carrierpilot1357 on 2009-04-17
reply to varunus: 
I did that, now my built in volume button on my keyboard doesnt work
I have a SiS SI7012 built in to motherboard card.

---

### Post by Clancy_s on 2009-04-18
A carrierpilot1357: this is a really old howto, from 4 1/2 years so 9 releases ago, there have been quite a few changes in how Ubuntu handles sound since then, this howto isn't for hardy which comes with alsa.  I'm no expert - I've just been chasing down sound threads the last week because I've been having trouble with mine.  Some active tips threads (for Hardy & Intrepid) you might find more helpful are:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If you've upgraded there's a shorter ibex specific one here 

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

