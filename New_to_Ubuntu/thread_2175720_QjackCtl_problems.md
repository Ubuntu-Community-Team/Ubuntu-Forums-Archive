---
title: "QjackCtl problems"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by Bobisha on 2013-09-20
I am trying to use QjackCtl as a patchbay between Rakarrack and Guitarix and I am having problems. I can't seem to get it running right. I keep getting the following message:

 [COLOR=#999999]13:46:09.146 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]13:46:09.150 Statistics reset.[/COLOR]
 [COLOR=#cccc99]13:46:09.186 ALSA connection change.[/COLOR]
 [COLOR=#999999]13:46:09.248 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#999999]13:46:09.454 D-BUS: JACK server is starting...[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Registered event listener change listener:  true 
 [COLOR=#66cc99]13:46:09.459 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]13:46:09.518 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).[/COLOR]
 Fri Sep 20 13:46:09 2013: Starting jack server...
 Fri Sep 20 13:46:09 2013: JACK server starting in realtime mode with priority 10
 Fri Sep 20 13:46:09 2013: ERROR: Cannot lock down 107335194 byte memory area (Cannot allocate memory)
 Fri Sep 20 13:46:09 2013: Acquired audio card Audio0
 Fri Sep 20 13:46:09 2013: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Fri Sep 20 13:46:09 2013: Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xfc220000 irq 51
 Fri Sep 20 13:46:09 2013: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
 Fri Sep 20 13:46:09 2013: ALSA: final selected sample format for capture: 32bit integer little-endian
 Fri Sep 20 13:46:09 2013: ALSA: use 2 periods for capture
 Fri Sep 20 13:46:09 2013: ALSA: final selected sample format for playback: 32bit integer little-endian
 Fri Sep 20 13:46:09 2013: ALSA: use 2 periods for playback
 Fri Sep 20 13:46:09 2013: ERROR: Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
 Fri Sep 20 13:46:09 2013: ERROR: AcquireSelfRealTime error
 Fri Sep 20 13:46:09 2013: graph reorder: new port 'system:capture_1'
 Fri Sep 20 13:46:09 2013: New client 'system' with PID 0
 Fri Sep 20 13:46:09 2013: graph reorder: new port 'system:capture_2'
 Fri Sep 20 13:46:09 2013: graph reorder: new port 'system:playback_1'
 Fri Sep 20 13:46:09 2013: graph reorder: new port 'system:playback_2'
 Fri Sep 20 13:46:09 2013: New client 'gx_head_amp' with PID 2467
 Fri Sep 20 13:46:09 2013: New client 'gx_head_fx' with PID 2467
 Fri Sep 20 13:46:10 2013: port 'gx_head_amp:in_0' created
 Fri Sep 20 13:46:10 2013: port 'gx_head_amp:midi_in_1' created
 Fri Sep 20 13:46:10 2013: port 'gx_head_amp:out_0' created
 Fri Sep 20 13:46:10 2013: port 'gx_head_fx:in_0' created
 Fri Sep 20 13:46:10 2013: port 'gx_head_fx:out_0' created
 Fri Sep 20 13:46:10 2013: port 'gx_head_fx:out_1' created
 Fri Sep 20 13:46:10 2013: Connecting 'gx_head_fx:out_0' to 'gx_head_amp:in_0'
 Fri Sep 20 13:46:10 2013: Connecting 'gx_head_fx:out_1' to 'gx_head_amp:in_0'
 Fri Sep 20 13:46:10 2013: ERROR: JackGraphManager::Connect already connected port_src = 9 port_dst = 5
 Fri Sep 20 13:46:10 2013: ERROR: JackGraphManager::Connect already connected port_src = 10 port_dst = 5
 Fri Sep 20 13:46:10 2013: Connecting 'system:capture_1' to 'gx_head_fx:in_0'
 Fri Sep 20 13:46:10 2013: Connecting 'system:capture_2' to 'gx_head_fx:in_0'
 Fri Sep 20 13:46:10 2013: Connecting 'gx_head_ampout_0' to 'systemplayback_1'
 Fri Sep 20 13:46:10 2013: Connecting 'gx_head_ampout_0' to 'systemplayback_2'
 Fri Sep 20 13:46:11 2013: Saving settings to "/home/michael/.config/jack/conf.xml" ...
 [COLOR=#9999cc]13:46:11.740 JACK connection change.[/COLOR]
 [COLOR=#999933]13:46:11.741 Server configuration saved to "/home/michael/.jackdrc".[/COLOR]
 [COLOR=#999999]13:46:11.741 Statistics reset.[/COLOR]
 [COLOR=#999999]13:46:11.757 Client activated.[/COLOR]
 [COLOR=#cc9966]13:46:11.786 JACK connection graph change.[/COLOR]
 Cannot lock down 107335194 byte memory area (Cannot allocate memory)
 Fri Sep 20 13:46:11 2013: New client 'qjackctl' with PID 2476
 [COLOR=#cc9966]13:46:13.592 JACK connection graph change.[/COLOR]
 [COLOR=#9999cc]13:46:13.789 JACK connection change.[/COLOR]
 Fri Sep 20 13:46:13 2013: Disconnecting 'gx_head_fxout_0' from 'gx_head_amp:in_0'
 Fri Sep 20 13:46:13 2013: Disconnecting 'gx_head_fxout_1' from 'gx_head_amp:in_0'
 Fri Sep 20 13:46:13 2013: Disconnecting 'gx_head_ampout_0' from 'systemlayback_1'
 Fri Sep 20 13:46:13 2013: Disconnecting 'gx_head_ampout_0' from 'systemlayback_2'
 Fri Sep 20 13:46:13 2013: Disconnecting 'system:capture_1' from 'gx_head_fx:in_0'
 Fri Sep 20 13:46:13 2013: Disconnecting 'system:capture_2' from 'gx_head_fx:in_0'
 Fri Sep 20 13:46:13 2013: Client 'gx_head_amp' with PID 2467 is out
 Fri Sep 20 13:46:13 2013: Client 'gx_head_fx' with PID 2467 is out
 [COLOR=#999999]QSpiAccessible::accessibleEvent not handled:  "6"  obj:  QMenu(0x1e56620) "

[/COLOR][COLOR=#000000]Any advice?[/COLOR][COLOR=#999999]
[/COLOR]

By the way... I am using a Lenovo Thinkpad T400 with an Intel Duo Core 2.53Ghz processor, 4GB ram, and a 250 GB Samsung SSD.

Thanks

---

