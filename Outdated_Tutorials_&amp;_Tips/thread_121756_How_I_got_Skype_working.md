---
title: "How I got Skype working"
date: 2006-01-25
forum: Outdated Tutorials &amp; Tips
---

### Post by agapito on 2006-01-25
There are a already a few posts about this subject, but none of them did the trick for me, so I'm posting my solution here.

1. Follow  [this HOWTO]("http://ubuntuforums.org/showthread.php?t=32063") to configure ALSA. (Here you'll have to restart ALSA, or reboot the computer.)

2. Install Skype. I used Automatix, an "Automated Graphical Installer and Tweaker" (info  [here]("http://ubuntuforums.org/showthread.php?t=80295")), so I don't know if the deb in the repositories works.

3. [Download]("http://195.38.3.142:6502/skype/skype_dsp_hijacker-0.6.tar.gz") and install skype_dsp_hijacker. This prevents the  "*/dev/dsp1: Device or resource busy*" error. (More info [here]("http://juljas.net/linux/skype/") or [here]("http://195.38.3.142:6502/skype/").)
    You have to compile the included library, but it's really simple. I'll say how anyway:
```
tar xvzf skype_dsp_hijacker-0.6.tar.gz
cd skype_dsp_hijacker-0.6
make
sudo make install
```
After this the program and the library will go to /usr/local/bin/ and /usr/local/lib/, respectively.

4. Open gnome-volume-control and in Edit->Preferences, check every option to see the full configuration of the sound card.  Now make sure that it's configured correctly. In my case (I have a C-Media CMI8738 sound card) I have this set as default,

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=5576&stc=1&d=1138243549[/IMG][/CENTER]

so the mic doesn't work (There is some portuguese in the picture, but you got the idea, right? ;) ). It should be Mic-in. Now, set the Mic as your recording source, like this

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=5577&stc=1&d=1138243702[/IMG][/CENTER]

5. Use skype_dsp_hijacker to start skype. (Yes, it opens skype too. All you have to do is wait a bit.) I changed the path of the skype executable in the menu (with the Applications Menu Editor) to /usr/local/bin/skype_dsp_hijacker, so I won't have to type it in all the time.

6. Add echo123 to your contacts, so you can test your configuration. Now call echo123. If everything went well you'll be able to hear the message, record a message and hear it's replay. It takes about 25secs.

Note: I still can't record my own voice using gnome-sound-recorder but everything else is fine.

---

### Post by Moebius on 2006-01-27
This worked very well, was able to finally use skype in ubuntu.

One thing to add is that I can only call skype_dsp_hijacker by using sudo.
Therefore to use this little program I as a shortcut (icon) I had to add this to the sudoers file

```
sudo gedit /etc/sudoers
```

and then 

```
your_user_name	ALL= NOPASSWD: /usr/local/bin/skype_dsp_hijacker
```

Cheers,

Um grande obrigado Agapito, dica 5 estrelas!

---

### Post by agapito on 2006-01-27
[QUOTE=Moebius]
One thing to add is that I can only call skype_dsp_hijacker by using sudo.
[/QUOTE]

Probably the permissions on the binary are wrong. I guess all you have to do is this:
```
sudo chmod 755 /usr/local/bin/skype_dsp_hijacker
```

But your method is great too.

I'm glad I could help. 

Fica bem!

É sempre bom ver Tugas por aqui. ;)

---

### Post by maulattu on 2006-01-28
it's correct. Let's do a chmod 775 on the executable and it works fine

---

### Post by Zhukov on 2006-01-30
Well, i believe ive managed to use Skype without the hijacker, but still thanks :D

Se bem que acho que isto às vezes fana um pouco...Vou tentar a tua maneira ;)

---

### Post by henriquemaia on 2006-01-31
I would also recomend the skype_dsp_hijacker. Without it, I was having a really bad time with skype's dsp error.

Thanks for this howto.

Bem-hajas ;)

---

### Post by Chrissss on 2006-01-31
Thanks for this Howto. Finally Skype works. For those of you, who use a bt headset and are disapointed of the sound quality under linux. Geht the btsco cvs version and compile it yourselt. It really boosts the quality :)

---

### Post by jmce on 2006-02-15
Dennis Kaarsemaker's repository includes a skype-dsp-hijacker package (and also a skype package) for Ubuntu:
[http://seveas.ubuntulinux.nl/dists/breezy-seveas/extras/]("http://seveas.ubuntulinux.nl/dists/breezy-seveas/extras/")

Installing it automatically diverts /usr/bin/skype, creating a symbolic link to /usr/bin/skype_dsp_hijacker.

---

### Post by tntc1978 on 2006-02-16
> You have to compile the included library, but it's really simple. I'll say how anyway

I just can't seem to compile the file. 
I get through these two:
> tar xvzf skype_dsp_hijacker-0.6.tar.gz
cd skype_dsp_hijacker-0.6

This is what I get:
> thomas@T22:~$ tar xvzf skype_dsp_hijacker-0.6.tar.gz
skype_dsp_hijacker-0.6/
skype_dsp_hijacker-0.6/skype_dsp_hijacker
skype_dsp_hijacker-0.6/README
skype_dsp_hijacker-0.6/skype_dsp_hijacker.c
skype_dsp_hijacker-0.6/Makefile
skype_dsp_hijacker-0.6/ChangeLog
thomas@T22:~$ cd skype_dsp_hijacker-0.6
thomas@T22:~/skype_dsp_hijacker-0.6$ make
bash: make: command not found
thomas@T22:~/skype_dsp_hijacker-0.6$ sudo make install
sudo: make: command not found


Any thoughts?

---

### Post by Gandalf on 2006-02-16
You need build-essential package..
```

sudo apt-get install build-essential

```

---

### Post by tntc1978 on 2006-02-16
It helped. But now I experience new problems:

1. I don't seem to get the same Line-in mode and Mic-in mode that Gandalf (vielder of the flame of Undun) shows above.

2. When I execute /usr/local/bin/skype_dsp_hijacker the Terminal is permanently open, and if I close it, skype closes.

3. When I "dial" echo123 The lady doesn't finish speaking, it seems she gets cut off. And I don't hear what I say through the speakers.

4. Maybe connected to this, there's no sound when using Totem, MPlayer, Rhytmbox and Beep Media Player, But XMMS and VLC works fine :-k 

5. when I try to configure the skypelaunch in Starter Application menu editor, it (the starter application menu editor) seems to start up, because I see it on the panel, but it actually never starts.

I think that was all the problems I have concerning this ;)

---

### Post by Copter on 2006-03-25
hi!

on my box, skype works now fine but i cant play music while talking (ie. amaroK) (i talk via skype _nand_ listen to the music ;). what i did : sys settings -> sound -> sound sys -> hardware -> audio device == ALSA. sound config files below

copter :]

---

### Post by wvelez on 2006-03-25
Thanks a bunch for this how-to!  I can finally use Skype and talk to my family and friends back in the States.

Thanks again.

-will

---

### Post by Scunizi on 2006-03-25
Without following any of the above instructions I've been able to get the echo test to work both directions.  I can hear "her" and record my voice.  I've done this just by messing aroung with the sound mixer.  I'm running Dapper so things might be a little different.  My sound control panel looks like it has a lot more options when everything is check.  The weird thing is, even though I can to the echo test, when I call one of my other contacts I don't hear any "ring".  It says ringing but nothing comes through as a ring.  However, it must be ringing on the other end 'cause it gets answered and I can hold a conversation.

Has anyone else (on Dapper) been able to use the Sound Recorder? That will NOT function for me.](*,)

---

### Post by Myndmelder on 2006-03-26
](*,)  My turn...

And yes, I am new and confused.

This is what I get:

```
myndmelder@alpha-primus:~$ tar xvzf skype_dsp_hijacker-0.6.tar.gz
tar: skype_dsp_hijacker-0.6.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

The bloody file is sitting on my destop...

Anyways, I tried finding a way to get the file reconised, but no dice...

---

### Post by Gandalf on 2006-03-26
[QUOTE=Myndmelder]](*,)  My turn...

And yes, I am new and confused.

This is what I get:

```
myndmelder@alpha-primus:~$ tar xvzf skype_dsp_hijacker-0.6.tar.gz
tar: skype_dsp_hijacker-0.6.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

The bloody file is sitting on my destop...

Anyways, I tried finding a way to get the file reconised, but no dice...[/QUOTE]
It's sitting on ur dekstop and u're untarring in ~ :o
go to desktop first (cd Desktop) and then untar it...

---

### Post by Myndmelder on 2006-03-26
Thank you...

Windows crashed yesterday around ten am.
I decided I was tired of it, and installed Ubuntu.
Been working on getting Ubuntu the way I like it 20+ hours now.
Sitting at my desk with shades on, going thru all the info. This is the first time I was stumped.

Thanks again.

---

### Post by gymsmoke on 2006-03-26
Nice job.  Except that now I have ABSOLUTELY NO SOUND AT ALL!

---

### Post by Scunizi on 2006-03-26
I installed skype using the method in the wiki and have been able to get it working with mic & speakers as I mentioned in my previous post.  In looking into the ring issue I found the following read me in one of Skype's directory/folders.
I had an idea that the ring sound didn't have a file attached to it.  When I went to look the Skype folder in /usr/share/.skype is not only hidden but protected and says I don't have access, that I'm not the owner.  How do I gain access? I've tried sudo cd .skype, sudo cd ./skype and other variations to no avail.  I've also tried chown -hR <myname> .skype, /.skype, ./skype.  I know it's something simple but I'm to new at this.  Anyone have any suggestions?  :rolleyes: 

Here's the readme quote:
Skype keeps its resources in a resources directory. The resources
directory must contain the following subdirectories:
* "sound". This contains the following files:
 - call_in.wav - "incoming call" ringtone
 - call_out.wav - "ringing" tone for caller
 - im.wav - incoming Instant Message alert sound
 You can modify or change these files to your liking.
* "lang" - contains *.qm files for Skype UI translation

Skype searches the following locations for a resource directory
and stops at first match:

1) command line option "resources-path":
   ./skype --resources-path /some/directory/with/resources
2) environment variable SKYPE_RESOURCES_PATH
3) hardcoded paths of current directory, /usr/share/skype and
   /usr/local/share/skype

---

### Post by Tylo on 2006-04-01
Great tutorial. Fixed my problems. Now I can listen to multiple voice mails without having the close the program inbetween. You made my life in Ubuntu so much easier. Thanks to all who worked on these programs!

-Tylo

---

### Post by gymsmoke on 2006-04-01
I actually have 2 sound cards on my workstation, which may be why the sound went AWOL after doing this.  Since my main audio input was through my webcam back when i had winbloze on this box, i (naively) assumed that linux would "just see it"...
Well, Ubunut does recognize it, but that's about it...

I'm going to try re-installing skype with a stick mic plugged directly into the audio in port and see what that brings...

But, I'd sure like to have the webcam handle this.  It's rather convenient to have a very small, onubtrusive appliance on my desk that handles audio/video, rather than have to hold a mic to talk to someone...

---

### Post by Juharanto on 2006-04-17
I can call one time to echo123, but when i tried to call again I get a message Problem with sound device.. I cant understand why but it didnt work with me.. I must restart skype after every calls. Its irritating and Skype's take so many time to start.

> juha@ubuntu:~$ /usr/local/bin/skype_dsp_hijacker
hijacker: skype_dsp_hijacker v0.6
hijacker: when Skype opens DSP /dev/dsp
hijacker: - microphone used: /dev/dsp
hijacker: - speakers used:   /dev/dsp
hijacker: when Skype opens mixer /dev/mixer
hijacker: - mixer used: /dev/mixer
/dev/dsp1: Laite tai resurssi varattu
/dev/dsp1: Laite tai resurssi varattu

Anything ideas?

---

### Post by Zhukov on 2006-04-17
I would suggest you to tweak you sound configuration.
Try this: [http://jpoa.ecwhost.com/?p=34](http://jpoa.ecwhost.com/?p=34)

Good luck!

---

### Post by Scunizi on 2006-04-17
[Check out the Wiki ]("https://wiki.ubuntu.com/SkypeHowto?highlight=%28skype%29").  This is how I got it working...

---

### Post by AtZeuS on 2006-04-24
I've got Alsa and OSS emulation running correctly ( can run a OSS and ALSA app at the same time ) but somehow skype_dsp_hijacker CAN get to the microphone but not to the speakers when I am also playing and mp3 on xmms(ALSA).

I've been trying to get this work for ages, any ideas?

Cheers.

here's my .asoundrc

```
pcm.card0 {
  type hw
  card 0
# mmap_emulation true
}

#pcm.dmix0 {
#  type dmix 
#  ipc_key 34521 
#  slave {
#    pcm "card0" 
#  }
#}


pcm.dmix0 {
	type dmix
	ipc_key 1024 ## needs to be a power of 2
	slave {
		pcm "hw:0"
		period_time 0
		period_size 1024
		buffer_size 8192
               # format S16_LE
		rate 44100 ## not necessary
	}
#slowptr true
}





pcm.dsnoop0 {
  type dsnoop 
  ipc_key 2048
  slave {
    pcm "hw:0" 
  #  rate 48000
  }
}

pcm.asym0 {
  type asym 
  playback.pcm "dmix0" 
  capture.pcm "dsnoop0"
}

pcm.pasym0 {
  type plug 
  slave.pcm "asym0"
}

# 'dsp0' is espected by OSS emulation etc.
pcm.dsp0 {
  type                  plug
  slave.pcm             "asym0"
}

ctl.dsp0 {
    type                hw
    card                0
}

pcm.!default {
  type                  plug
  slave.pcm             "asym0"
}

ctl.!default {
    type                hw
    card                0
}
```

---

### Post by ramos on 2006-04-25
I have used the instructions but didn't get an executable. Look below:

alexandre@dickens:/usr/local/bin$ sudo chmod 755  /usr/local/bin/skype_dsp_hijacker

alexandre@dickens:/usr/local/bin$ sudo chmod 775 /usr/local/bin/skype_dsp_hijacker

alexandre@dickens:/usr/local/bin$ sudo ./skype_dsp_hijacker
./skype_dsp_hijacker: line 105: exec: skype: not found

What is the next step?
Thanks,
Ramos

---

### Post by Andrew1234 on 2006-06-16
Hi I have followed all the above installed skype_dsp_hijacker opens the prog. fine but still no sound any ideas, 

andrew@shopmail:~$ skype_dsp_hijacker
hijacker: skype_dsp_hijacker v0.6
hijacker: when Skype opens DSP /dev/dsp
hijacker: - microphone used: /dev/dsp
hijacker: - speakers used:   /dev/dsp
hijacker: when Skype opens mixer /dev/mixer
hijacker: - mixer used: /dev/mixer


I get the error below in the terminal window?

write error, written = -1 repeated many times

---

### Post by Scunizi on 2006-06-16
Try typing "killall esd" at the consol prompt, then call echo again.

---

### Post by Andrew1234 on 2006-06-17
Tried that but still no sound :sad: certainly got sound in normal use and mplayer?

---

### Post by F0CUS on 2006-06-19
Grreat! thanks, worked perfect!

---

