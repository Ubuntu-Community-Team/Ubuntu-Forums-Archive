---
title: "Hydrogen Error Message!?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by moose4204l on 2008-05-28
when i type hydrogen in the command line, it loads and i can use it but i get this in the terminal:
> hydrogen
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH
Warning: no locale found: /usr/share/hydrogen/data/i18n/hydrogen.en_US.UTF-8
Warning: error loading locale: /usr/share/hydrogen/data/i18n/hydrogen.en_US.UTF-8.qm

Hydrogen 0.9.3 [Jan  6 2008]  [[http://www.hydrogen-music.org]](http://www.hydrogen-music.org])
Copyright 2002-2005 Alessandro Cominu


Compiled modules:  (FLAC) (LASH) (Jack) (Alsa) (OSS) (LRDF)

Hydrogen comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details

Using data path: /usr/share/hydrogen/data
[LadspaFX::getLadspaFXGroup]
[WARNING]   JackDriver   	Jack server not running?
[ERROR]     Hydrogen      	[createDriver] Error starting audio driver [audioDriver::init()]
[ERROR]     AlsaAudioDriver   	Can't set realtime scheduling for ALSA Driver
[ERROR]     AlsaAudioDriver   	[alsaAudioDriver_processCaller] XRUN
[ERROR]     AlsaAudioDriver   	[alsaAudioDriver_processCaller] XRUN


what is all this stuff and can i resolve any of it?

---

### Post by moose4204l on 2008-05-28
bump

---

### Post by starcannon on 2008-05-28
This thread had a happy resolution of your bug:

[http://www.hydrogen-music.org/forum/index.php?action=show_thread&thread=545&fid=5&page=1](http://www.hydrogen-music.org/forum/index.php?action=show_thread&thread=545&fid=5&page=1)

Give that a go and see how it works out.

---

### Post by moose4204l on 2008-05-28
nope, that made it worse and i cant even play sound from hydrogen anymore. and when i try to go back and change the file listed, its already back to normal. i dont know why. anyways, here is the new error messages.

> hydrogen -d jack --verbose
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH
Warning: no locale found: /usr/share/hydrogen/data/i18n/hydrogen.en_US.UTF-8
Warning: error loading locale: /usr/share/hydrogen/data/i18n/hydrogen.en_US.UTF-8.qm

Hydrogen 0.9.3 [Jan  6 2008]  [[http://www.hydrogen-music.org]](http://www.hydrogen-music.org])
Copyright 2002-2005 Alessandro Cominu


Compiled modules:  (FLAC) (LASH) (Jack) (Alsa) (OSS) (LRDF)
Verbose log mode = active

Hydrogen comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details

Using data path: /usr/share/hydrogen/data
[INFO]      Preferences   	INIT
[INFO]      Preferences   	[loadPreferences] Loading preferences file (GLOBAL) [/usr/share/hydrogen/data/hydrogen.default.conf]
[INFO]      Preferences   	[loadPreferences] Loading preferences file (USER) [/home/moose/.hydrogen/hydrogen.conf]
[INFO]      SongReader   	[readSong] /home/moose/hydrogen/3rd.h2song
[INFO]      Song        	INIT "Untitled Song"
[LadspaFX::getLadspaFXGroup]
[INFO]      Hydrogen      	*** Hydrogen audio engine init ***
[INFO]      Hydrogen      	[audioEngine_startAudioDrivers]
[INFO]      Hydrogen      	[createDriver] Jack
[INFO]      JackDriver   	INIT
[WARNING]   JackDriver   	Jack server not running?
[ERROR]     Hydrogen      	[createDriver] Error starting audio driver [audioDriver::init()]
[INFO]      JackDriver   	DESTROY
[INFO]      JackDriver   	[disconnect]
[INFO]      JackDriver   	[deactivate]
[ERROR]     Hydrogen      	[audioEngine_startAudioDrivers] Error starting audio driver
[ERROR]     Hydrogen      	[audioEngine_startAudioDrivers] Using the NULL output audio driver
[INFO]      NullDriver   	INIT
[INFO]      AlsaMidiDriver   	INIT
[INFO]      AlsaMidiDriver   	alsaMidiDriver_thread() starting
[INFO]      AlsaMidiDriver   	MIDI port name: None
[INFO]      AlsaMidiDriver   	MIDI addr client: -1
[INFO]      AlsaMidiDriver   	MIDI addr port: -1
[INFO]      AlsaMidiDriver   	Midi input port at 128:0
[INFO]      AlsaMidiDriver   	MIDI Thread INIT
[INFO]      NullDriver   	connect
[INFO]      NullDriver   	[getOut_L()] not implemented yet
[ERROR]     Hydrogen      	[audioEngine_startAudioDrivers] m_pMainBuffer_L == NULL
[INFO]      NullDriver   	[getOut_R()] not implemented yet
[ERROR]     Hydrogen      	[audioEngine_startAudioDrivers] m_pMainBuffer_R == NULL
[INFO]      Hydrogen      	[audioEngine_setupLadspaFX] buffersize=0
[INFO]      Hydrogen      	[audioEngine_setupLadspaFX] m_pSong=NULL
[INFO]      Hydrogen      	[audioEngine_setSong] Untitled Song
[INFO]      Hydrogen      	[audioEngine_clearNoteQueue()]
[INFO]      Hydrogen      	[audioEngine_setupLadspaFX] buffersize=0
[ERROR]     Hydrogen      	[audioEngine_setupLadspaFX] nBufferSize=0
[ERROR]     NullDriver   	[setBpm] not implemented yet
[INFO]      NullDriver   	[locate] not implemented
[INFO]      PatEditPanel   	[selectedPatternChangedEvent]
[INFO]      DrumkitManager   	INIT
[INFO]      DrumkitManager   	[updateDrumkitList]
[INFO]      LayerPreview   	INIT
[INFO]      WaveDisplay   	INIT
[INFO]      HydrogenApp   	[showInfoSplash] Selected news: news-051113.html



---

### Post by starcannon on 2008-05-28
Did you try this post:

> 
 Same problem since jack 0.109.0 & qjackctl 0.3.2
Hi

That's right. I have checked out the global hydrogen.default.conf (which writes ~/.hydrogen/hydrogen.conf) and the solution is right there. One has to change the jack port name from alsa_pcm to system as per the following:

<jack_driver>
<jack_port_name_1>system:playback_1</jack_port_name_1>
<jack_port_name_2>system:playback_2</jack_port_name_2>
<jack_transport_mode>USE_JACK_TRANSPORT</jack_transport_mode>
<jack_connect_defaults>true</jack_connect_defaults>
<jack_track_outs>true</jack_track_outs>
</jack_driver>

The default condition for jack_track_outs was set to false, so change that to true if you'd like to have all the tracks. Version 0.109.0 of jack does not appear to work around this. Furthermore, even 0.107.2 (my previous version) didn't have this problem.

Happy hydrumming! 

other than that I can't think of anything, perhaps its something to do with pulse-audio?

---

### Post by moose4204l on 2008-05-28
yeah thats the file i was talking about, thanks anyways, maybe someone else will lend a hand

---

