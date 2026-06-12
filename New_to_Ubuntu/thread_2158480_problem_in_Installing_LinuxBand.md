---
title: "problem in Installing LinuxBand"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by su:bhatta on 2013-06-29
Ok.. I have already seen these 2 threads:
1)[http://ubuntuforums.org/showthread.php?t=2010840](http://ubuntuforums.org/showthread.php?t=2010840)
2)[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Now the problem I am facing is I have tried ti install the glib-2.0 the codes are given below!

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
tres-bhatta@nbe42:/usr/local/src/linuxband-12.02$ apt-get install glib-2.0
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
tres-bhatta@nbe42:/usr/local/src/linuxband-12.02$ sudo -i
[sudo] password for tres-bhatta: 
root@nbe42:~# sudo apt-get install glib-2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'gir1.0-glib-2.0' for regex 'glib-2.0'
Note, selecting 'libspice-client-glib-2.0-1' for regex 'glib-2.0'
Note, selecting 'libspice-client-glib-2.0-4' for regex 'glib-2.0'
Note, selecting 'libspice-client-glib-2.0-8' for regex 'glib-2.0'
Note, selecting 'gobject-introspection-glib-2.0' for regex 'glib-2.0'
Note, selecting 'gir1.2-glib-2.0' for regex 'glib-2.0'
Note, selecting 'gir1.2-spice-client-glib-2.0' for regex 'glib-2.0'
Note, selecting 'libqtglib-2.0-0' for regex 'glib-2.0'
Note, selecting 'libspice-client-glib-2.0-dev' for regex 'glib-2.0'
gir1.2-glib-2.0 is already the newest version.
The following extra packages will be installed:
  libpixman-1-dev libpthread-stubs0 libpthread-stubs0-dev
  libspice-protocol-dev libspice-server-dev libspice-server1 libssl-dev
  libssl-doc libusbredirhost1 libusbredirparser1 libx11-dev libx11-doc
  libxau-dev libxcb1-dev libxdmcp-dev libxext-dev libxinerama-dev
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev x11proto-xext-dev
  x11proto-xinerama-dev xorg-sgml-doctools xtrans-dev zlib1g-dev
Suggested packages:
  libxcb-doc libxext-doc
The following NEW packages will be installed:
  gir1.2-spice-client-glib-2.0 libpixman-1-dev libpthread-stubs0
  libpthread-stubs0-dev libqtglib-2.0-0 libspice-client-glib-2.0-8
  libspice-client-glib-2.0-dev libspice-protocol-dev libspice-server-dev
  libspice-server1 libssl-dev libssl-doc libusbredirhost1 libusbredirparser1
  libx11-dev libx11-doc libxau-dev libxcb1-dev libxdmcp-dev libxext-dev
  libxinerama-dev x11proto-core-dev x11proto-input-dev x11proto-kb-dev
  x11proto-xext-dev x11proto-xinerama-dev xorg-sgml-doctools xtrans-dev
  zlib1g-dev
0 upgraded, 29 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,602 kB of archives.
After this operation, 33.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y



Now when i'm doing./configure i am back at the same message: Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.

Any help appreciated.. this is my first time at compiling something...

Thanks
bhatta

---

### Post by steeldriver on 2013-06-29
You probably need the glib-2.0 **development** package

```
sudo apt-get install libglib2.0-dev
```

---

### Post by su:bhatta on 2013-06-29
> **steeldriver said:**
> You probably need the glib-2.0 **development** package

```
sudo apt-get install libglib2.0-dev
```

Thanks steeldriver.. libglib2.0-dev did the trick...
Now am at my next hurdle....

> checking for JACK... no
configure: error: Package requirements (jack >= 0.102.0) were not met:

No package 'jack' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables JACK_CFLAGS
and JACK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
root@nbe42:/usr/local/src/linuxband-12.02# sudo apt-get install jack
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jack is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I am using Ubuntu studio 13.04 and jack is preinstalled.. i tried to ./configure with jack running, that dind't help..
next i did > sudo apt-get install jack

downloaded 1.5 megs...

still getting the same error...
any help appreciated..

my first compilation n am at a loss...

thanks..
bhatta

---

### Post by steeldriver on 2013-06-29
Again, if you are building a package from source, then you likely need the -dev packages of its dependencies - in fact it says right there on the Linuxband webpage

> 
**Requirements**

  Following are the requirements for build and runtime:
  
[LIST]
[*]MMA (Musical MIDI Accompaniment)
 [http://www.mellowood.ca/mma](http://www.mellowood.ca/mma) 
[*]JACK Audio Connection Kit
 [http://http://jackaudio.org](http://http://jackaudio.org) 
[*]Standard MIDI File format library
 [http://sourceforge.net/projects/libsmf](http://sourceforge.net/projects/libsmf) 
[*]Python >= 2.5 
 [http://python.org](http://python.org) 
[*]PyGTK: GTK+ for Python
 [http://www.pygtk.org](http://www.pygtk.org) 
[*]GtkSourceView 2.x and Python bindings
 [http://projects.gnome.org/gtksourceview](http://projects.gnome.org/gtksourceview)
 [http://projects.gnome.org/gtksourceview/pygtksourceview.html](http://projects.gnome.org/gtksourceview/pygtksourceview.html) 
[/LIST]
  On Debian you can install the dependencies by typing (as root):
[COLOR=#0000ff]** apt-get install libjack-dev**[/COLOR]
 apt-get install libsmf-dev
 apt-get install python-gtk2
 apt-get install python-gtksourceview2


[http://linuxband.org/documentation.html](http://linuxband.org/documentation.html)

---

### Post by su:bhatta on 2013-06-29
Many thanks steeldriver for your time... I didn't know these information would be available on the documentation page... next time I compile i will surely make sure to read all the pages for instructions...

Thanks...
bhatta

---

### Post by steeldriver on 2013-06-29
No problem, you will know for next time! sometimes the instructions are not so clear, so it's good to get some practice in figuring these things out - e.g. you can use the apt-cache search to find likely candidates for the missing packages

```
$ apt-cache search -- -dev | grep jack
libjack-dev - JACK Audio Connection Kit (development files)
libjack-jackd2-dev - JACK Audio Connection Kit (development files)
libbio2jack0-dev - oss/alsa to jack porting lib - development files
libbjack-ocaml-dev - OCaml blocking interface to jack audio connection kit

```

or you can install and use the apt-file utility

```

$ apt-file search jack.pc
libjack-dev: /usr/lib/i386-linux-gnu/pkgconfig/jack.pc
libjack-jackd2-dev: /usr/lib/i386-linux-gnu/pkgconfig/jack.pc

```

---

### Post by su:bhatta on 2013-06-29
Ok.. after removing all dependencies here is the deal on make command

   [FONT=Times New Roman, serif]But after installing the files mentioned I am having this error: error 1 it says...:

Code:
```
root@nbe42:/usr/local/src/linuxband-12.02# make
cc -o target/linuxband-player  -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include    -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -I.   -lglib-2.0   -pthread -lgthread-2.0 -lglib-2.0   -ljack -lpthread -lrt   -lsmf -lm -lglib-2.0   src/main/c/linuxband-player.c src/main/c/midi.c src/main/c/remote_control.c
src/main/c/linuxband-player.c: In function ‘main’:
src/main/c/linuxband-player.c:768:2: warning: ‘g_thread_init’ is deprecated (declared at /usr/include/glib-2.0/glib/deprecated/gthread.h:260) [-Wdeprecated-declarations]
/tmp/ccjtL1Tu.o: In function `warning_async':
linuxband-player.c:(.text+0x144): undefined reference to `g_log'
/tmp/ccjtL1Tu.o: In function `warn_from_jack_thread_context':
linuxband-player.c:(.text+0x168): undefined reference to `g_idle_add'
/tmp/ccjtL1Tu.o: In function `nframes_to_ms':
linuxband-player.c:(.text+0x184): undefined reference to `jack_get_sample_rate'
/tmp/ccjtL1Tu.o: In function `ms_to_nframes':
linuxband-player.c:(.text+0x26b): undefined reference to `jack_get_sample_rate'
/tmp/ccjtL1Tu.o: In function `send_all_sound_off':
linuxband-player.c:(.text+0x33b): undefined reference to `jack_midi_event_reserve'
/tmp/ccjtL1Tu.o: In function `process_midi_output':
linuxband-player.c:(.text+0x3e3): undefined reference to `jack_port_get_buffer'
linuxband-player.c:(.text+0x430): undefined reference to `jack_midi_clear_buffer'
linuxband-player.c:(.text+0x50d): undefined reference to `jack_transport_query'
linuxband-player.c:(.text+0x588): undefined reference to `jack_transport_query'
linuxband-player.c:(.text+0x5a3): undefined reference to `jack_last_frame_time'
linuxband-player.c:(.text+0x616): undefined reference to `jack_last_frame_time'
linuxband-player.c:(.text+0x673): undefined reference to `smf_peek_next_event'
linuxband-player.c:(.text+0x6b6): undefined reference to `smf_event_is_metadata'
linuxband-player.c:(.text+0x6d3): undefined reference to `smf_event_decode'
linuxband-player.c:(.text+0x711): undefined reference to `g_log'
linuxband-player.c:(.text+0x761): undefined reference to `g_log'
linuxband-player.c:(.text+0x7a0): undefined reference to `smf_get_next_event'
linuxband-player.c:(.text+0x8b3): undefined reference to `smf_get_next_event'
linuxband-player.c:(.text+0x914): undefined reference to `jack_midi_event_reserve'
linuxband-player.c:(.text+0x9ac): undefined reference to `jack_midi_event_reserve'
/tmp/ccjtL1Tu.o: In function `sync_callback':
linuxband-player.c:(.text+0xb56): undefined reference to `g_log'
linuxband-player.c:(.text+0xbe0): undefined reference to `g_log'
/tmp/ccjtL1Tu.o: In function `timebase_callback':
linuxband-player.c:(.text+0xc5b): undefined reference to `smf_peek_next_event'
linuxband-player.c:(.text+0xc82): undefined reference to `smf_get_tempo_by_pulses'
/tmp/ccjtL1Tu.o: In function `connect_to_input_port':
linuxband-player.c:(.text+0x104f): undefined reference to `jack_port_disconnect'
linuxband-player.c:(.text+0x1071): undefined reference to `g_log'
linuxband-player.c:(.text+0x1087): undefined reference to `jack_port_name'
linuxband-player.c:(.text+0x10a0): undefined reference to `jack_connect'
linuxband-player.c:(.text+0x10c9): undefined reference to `g_log'
linuxband-player.c:(.text+0x10f0): undefined reference to `g_log'
/tmp/ccjtL1Tu.o: In function `init_jack':
linuxband-player.c:(.text+0x1127): undefined reference to `jack_client_open'
linuxband-player.c:(.text+0x1153): undefined reference to `g_log'
linuxband-player.c:(.text+0x1176): undefined reference to `jack_set_process_callback'
linuxband-player.c:(.text+0x1198): undefined reference to `g_log'
linuxband-player.c:(.text+0x11c5): undefined reference to `jack_set_sync_callback'
linuxband-player.c:(.text+0x11e7): undefined reference to `g_log'
linuxband-player.c:(.text+0x120a): undefined reference to `jack_on_shutdown'
linuxband-player.c:(.text+0x12bd): undefined reference to `jack_port_register'
linuxband-player.c:(.text+0x12fd): undefined reference to `g_log'
linuxband-player.c:(.text+0x1330): undefined reference to `jack_activate'
linuxband-player.c:(.text+0x134d): undefined reference to `g_log'
/tmp/ccjtL1Tu.o: In function `show_version':
linuxband-player.c:(.text+0x140e): undefined reference to `smf_get_version'
/tmp/ccjtL1Tu.o: In function `main':
linuxband-player.c:(.text+0x148e): undefined reference to `g_thread_init'
linuxband-player.c:(.text+0x149d): undefined reference to `g_log_set_default_handler'
linuxband-player.c:(.text+0x1551): undefined reference to `g_log'
linuxband-player.c:(.text+0x15ef): undefined reference to `g_log'
linuxband-player.c:(.text+0x1619): undefined reference to `smf_load'
linuxband-player.c:(.text+0x1653): undefined reference to `g_log'
linuxband-player.c:(.text+0x1676): undefined reference to `smf_decode'
linuxband-player.c:(.text+0x1692): undefined reference to `g_log'
linuxband-player.c:(.text+0x16c8): undefined reference to `g_log'
linuxband-player.c:(.text+0x16e6): undefined reference to `g_timeout_add'
linuxband-player.c:(.text+0x1731): undefined reference to `g_log'
linuxband-player.c:(.text+0x1763): undefined reference to `jack_transport_locate'
linuxband-player.c:(.text+0x1772): undefined reference to `jack_transport_start'
linuxband-player.c:(.text+0x178b): undefined reference to `jack_frame_time'
linuxband-player.c:(.text+0x17b9): undefined reference to `g_main_loop_new'
linuxband-player.c:(.text+0x17c1): undefined reference to `g_main_loop_run'
/tmp/ccqyxcxZ.o: In function `show_track':
midi.c:(.text+0x1b2): undefined reference to `g_log'
midi.c:(.text+0x1c7): undefined reference to `smf_event_decode'
midi.c:(.text+0x1ef): undefined reference to `g_log'
midi.c:(.text+0x204): undefined reference to `smf_track_get_event_by_number'
/tmp/ccqyxcxZ.o: In function `show_smf':
midi.c:(.text+0x229): undefined reference to `smf_decode'
midi.c:(.text+0x245): undefined reference to `g_log'
midi.c:(.text+0x26f): undefined reference to `smf_get_track_by_number'
/tmp/ccqyxcxZ.o: In function `find_song_end':
midi.c:(.text+0x2a6): undefined reference to `smf_event_is_metadata'
midi.c:(.text+0x2b6): undefined reference to `smf_event_decode'
midi.c:(.text+0x2f2): undefined reference to `smf_get_next_event'
/tmp/ccqyxcxZ.o: In function `find_bar_end':
midi.c:(.text+0x350): undefined reference to `smf_event_is_metadata'
midi.c:(.text+0x360): undefined reference to `smf_event_decode'
midi.c:(.text+0x3ad): undefined reference to `smf_get_next_event'
/tmp/ccqyxcxZ.o: In function `find_bar_num':
midi.c:(.text+0x40e): undefined reference to `smf_event_is_metadata'
midi.c:(.text+0x41e): undefined reference to `smf_event_decode'
midi.c:(.text+0x471): undefined reference to `smf_get_next_event'
/tmp/ccqyxcxZ.o: In function `find_bar_num_seconds':
midi.c:(.text+0x4c0): undefined reference to `smf_rewind'
/tmp/ccqyxcxZ.o: In function `get_bar_offsets':
midi.c:(.text+0x507): undefined reference to `smf_rewind'
/tmp/ccqyxcxZ.o: In function `copy_event':
midi.c:(.text+0x57f): undefined reference to `smf_event_new_from_pointer'
/tmp/ccqyxcxZ.o: In function `copy_events':
midi.c:(.text+0x5ad): undefined reference to `smf_seek_to_pulses'
midi.c:(.text+0x5f4): undefined reference to `smf_get_track_by_number'
midi.c:(.text+0x625): undefined reference to `smf_track_add_event_pulses'
midi.c:(.text+0x631): undefined reference to `smf_get_next_event'
/tmp/ccqyxcxZ.o: In function `create_marker':
midi.c:(.text+0x677): undefined reference to `smf_event_new'
/tmp/ccqyxcxZ.o: In function `create_empty_smf':
midi.c:(.text+0x70d): undefined reference to `smf_new'
midi.c:(.text+0x726): undefined reference to `smf_set_ppqn'
midi.c:(.text+0x75c): undefined reference to `smf_set_format'
midi.c:(.text+0x78c): undefined reference to `smf_track_new'
midi.c:(.text+0x7a3): undefined reference to `smf_add_track'
/tmp/ccqyxcxZ.o: In function `copy_smf_bars':
midi.c:(.text+0x829): undefined reference to `smf_rewind'
midi.c:(.text+0x83a): undefined reference to `smf_get_track_by_number'
midi.c:(.text+0x84f): undefined reference to `smf_get_track_by_number'
midi.c:(.text+0x89f): undefined reference to `smf_event_decode'
midi.c:(.text+0x8d4): undefined reference to `smf_track_add_event_pulses'
midi.c:(.text+0x8e0): undefined reference to `smf_track_get_next_event'
midi.c:(.text+0x981): undefined reference to `smf_track_add_event_pulses'
/tmp/ccqyxcxZ.o: In function `loop_smf':
midi.c:(.text+0x9ab): undefined reference to `smf_rewind'
midi.c:(.text+0x9f8): undefined reference to `smf_rewind'
midi.c:(.text+0xabc): undefined reference to `smf_get_track_by_number'
midi.c:(.text+0xb09): undefined reference to `smf_track_add_event_pulses'
/tmp/ccqyxcxZ.o: In function `load_smf_data':
midi.c:(.text+0xb30): undefined reference to `smf_load_from_memory'
midi.c:(.text+0xb54): undefined reference to `g_log'
midi.c:(.text+0xb62): undefined reference to `smf_decode'
midi.c:(.text+0xb7e): undefined reference to `g_log'
/tmp/ccUHLIxu.o: In function `open_pipes':
remote_control.c:(.text+0xe9): undefined reference to `g_log'
remote_control.c:(.text+0x104): undefined reference to `g_log'
remote_control.c:(.text+0x157): undefined reference to `g_log'
remote_control.c:(.text+0x1a5): undefined reference to `g_log'
/tmp/ccUHLIxu.o:remote_control.c:(.text+0x1c7): more undefined references to `g_log' follow
/tmp/ccUHLIxu.o: In function `loop_song':
remote_control.c:(.text+0x311): undefined reference to `smf_peek_next_event'
remote_control.c:(.text+0x360): undefined reference to `g_log'
remote_control.c:(.text+0x376): undefined reference to `smf_seek_to_pulses'
remote_control.c:(.text+0x3a4): undefined reference to `smf_peek_next_event'
/tmp/ccUHLIxu.o: In function `check_event':
remote_control.c:(.text+0x42e): undefined reference to `g_log'
/tmp/ccUHLIxu.o: In function `partial_seek':
remote_control.c:(.text+0x468): undefined reference to `smf_peek_next_event'
remote_control.c:(.text+0x48f): undefined reference to `smf_rewind'
remote_control.c:(.text+0x49b): undefined reference to `smf_peek_next_event'
remote_control.c:(.text+0x4f3): undefined reference to `g_log'
remote_control.c:(.text+0x515): undefined reference to `smf_get_next_event'
remote_control.c:(.text+0x545): undefined reference to `smf_peek_next_event'
remote_control.c:(.text+0x59d): undefined reference to `g_log'
remote_control.c:(.text+0x5e9): undefined reference to `g_log'
/tmp/ccUHLIxu.o: In function `loop_seek':
remote_control.c:(.text+0x648): undefined reference to `g_log'
/tmp/ccUHLIxu.o: In function `free_smf':
remote_control.c:(.text+0x71a): undefined reference to `smf_delete'
/tmp/ccUHLIxu.o: In function `start_playback':
remote_control.c:(.text+0x757): undefined reference to `g_log'
remote_control.c:(.text+0x770): undefined reference to `jack_transport_start'
remote_control.c:(.text+0x781): undefined reference to `jack_frame_time'
/tmp/ccUHLIxu.o: In function `command_load':
remote_control.c:(.text+0x7ee): undefined reference to `g_log'
remote_control.c:(.text+0x849): undefined reference to `g_log'
remote_control.c:(.text+0x869): undefined reference to `g_log'
remote_control.c:(.text+0x884): undefined reference to `smf_delete'
/tmp/ccUHLIxu.o: In function `command_stop':
remote_control.c:(.text+0x8db): undefined reference to `jack_transport_stop'
/tmp/ccUHLIxu.o: In function `command_play':
remote_control.c:(.text+0x95e): undefined reference to `smf_rewind'
remote_control.c:(.text+0x9a5): undefined reference to `jack_transport_locate'
/tmp/ccUHLIxu.o: In function `command_play_from_bar':
remote_control.c:(.text+0xa18): undefined reference to `g_log'
remote_control.c:(.text+0xa71): undefined reference to `smf_rewind'
remote_control.c:(.text+0xab5): undefined reference to `g_log'
remote_control.c:(.text+0xb03): undefined reference to `jack_transport_locate'
remote_control.c:(.text+0xb1e): undefined reference to `smf_seek_to_seconds'
/tmp/ccUHLIxu.o: In function `command_play_bars':
remote_control.c:(.text+0xc41): undefined reference to `smf_rewind'
remote_control.c:(.text+0xc88): undefined reference to `jack_transport_locate'
/tmp/ccUHLIxu.o: In function `command_pause':
remote_control.c:(.text+0xce8): undefined reference to `jack_transport_stop'
remote_control.c:(.text+0xd17): undefined reference to `jack_transport_start'
/tmp/ccUHLIxu.o: In function `command_intro_length':
remote_control.c:(.text+0xda8): undefined reference to `g_log'
/tmp/ccUHLIxu.o: In function `command_finish':
remote_control.c:(.text+0xdd1): undefined reference to `jack_client_close'
/tmp/ccUHLIxu.o: In function `jack_shutdown':
remote_control.c:(.text+0xe00): undefined reference to `g_log'
/tmp/ccUHLIxu.o: In function `remote_control_loop':
remote_control.c:(.text+0xe65): undefined reference to `g_log'
remote_control.c:(.text+0xe8f): undefined reference to `g_log'
remote_control.c:(.text+0xeb7): undefined reference to `g_log'
remote_control.c:(.text+0xee1): undefined reference to `g_log'
/tmp/ccUHLIxu.o:remote_control.c:(.text+0xf0b): more undefined references to `g_log' follow
collect2: error: ld returned 1 exit status
make: *** [target/linuxband-player] Error 1
root@nbe42:/usr/local/src/linuxband-12.02# make install
cc -o target/linuxband-player  -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include    -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -I.   -lglib-2.0   -pthread -lgthread-2.0 -lglib-2.0   -ljack -lpthread -lrt   -lsmf -lm -lglib-2.0   src/main/c/linuxband-player.c src/main/c/midi.c src/main/c/remote_control.c
src/main/c/linuxband-player.c: In function ‘main’:
src/main/c/linuxband-player.c:768:2: warning: ‘g_thread_init’ is deprecated (declared at /usr/include/glib-2.0/glib/deprecated/gthread.h:260) [-Wdeprecated-declarations]
/tmp/ccMI8YLK.o: In function `warning_async':
linuxband-player.c:(.text+0x144): undefined reference to `g_log'
/tmp/ccMI8YLK.o: In function `warn_from_jack_thread_context':
linuxband-player.c:(.text+0x168): undefined reference to `g_idle_add'
/tmp/ccMI8YLK.o: In function `nframes_to_ms':
linuxband-player.c:(.text+0x184): undefined reference to `jack_get_sample_rate'
/tmp/ccMI8YLK.o: In function `ms_to_nframes':
linuxband-player.c:(.text+0x26b): undefined reference to `jack_get_sample_rate'
/tmp/ccMI8YLK.o: In function `send_all_sound_off':
linuxband-player.c:(.text+0x33b): undefined reference to `jack_midi_event_reserve'
/tmp/ccMI8YLK.o: In function `process_midi_output':
linuxband-player.c:(.text+0x3e3): undefined reference to `jack_port_get_buffer'
linuxband-player.c:(.text+0x430): undefined reference to `jack_midi_clear_buffer'
linuxband-player.c:(.text+0x50d): undefined reference to `jack_transport_query'
linuxband-player.c:(.text+0x588): undefined reference to `jack_transport_query'
linuxband-player.c:(.text+0x5a3): undefined reference to `jack_last_frame_time'
linuxband-player.c:(.text+0x616): undefined reference to `jack_last_frame_time'
linuxband-player.c:(.text+0x673): undefined reference to `smf_peek_next_event'
linuxband-player.c:(.text+0x6b6): undefined reference to `smf_event_is_metadata'
linuxband-player.c:(.text+0x6d3): undefined reference to `smf_event_decode'
linuxband-player.c:(.text+0x711): undefined reference to `g_log'
linuxband-player.c:(.text+0x761): undefined reference to `g_log'
linuxband-player.c:(.text+0x7a0): undefined reference to `smf_get_next_event'
linuxband-player.c:(.text+0x8b3): undefined reference to `smf_get_next_event'
linuxband-player.c:(.text+0x914): undefined reference to `jack_midi_event_reserve'
linuxband-player.c:(.text+0x9ac): undefined reference to `jack_midi_event_reserve'
/tmp/ccMI8YLK.o: In function `sync_callback':
linuxband-player.c:(.text+0xb56): undefined reference to `g_log'
linuxband-player.c:(.text+0xbe0): undefined reference to `g_log'
/tmp/ccMI8YLK.o: In function `timebase_callback':
linuxband-player.c:(.text+0xc5b): undefined reference to `smf_peek_next_event'
linuxband-player.c:(.text+0xc82): undefined reference to `smf_get_tempo_by_pulses'
/tmp/ccMI8YLK.o: In function `connect_to_input_port':
linuxband-player.c:(.text+0x104f): undefined reference to `jack_port_disconnect'
linuxband-player.c:(.text+0x1071): undefined reference to `g_log'
linuxband-player.c:(.text+0x1087): undefined reference to `jack_port_name'
linuxband-player.c:(.text+0x10a0): undefined reference to `jack_connect'
linuxband-player.c:(.text+0x10c9): undefined reference to `g_log'
linuxband-player.c:(.text+0x10f0): undefined reference to `g_log'
/tmp/ccMI8YLK.o: In function `init_jack':
linuxband-player.c:(.text+0x1127): undefined reference to `jack_client_open'
linuxband-player.c:(.text+0x1153): undefined reference to `g_log'
linuxband-player.c:(.text+0x1176): undefined reference to `jack_set_process_callback'
linuxband-player.c:(.text+0x1198): undefined reference to `g_log'
linuxband-player.c:(.text+0x11c5): undefined reference to `jack_set_sync_callback'
linuxband-player.c:(.text+0x11e7): undefined reference to `g_log'
linuxband-player.c:(.text+0x120a): undefined reference to `jack_on_shutdown'
linuxband-player.c:(.text+0x12bd): undefined reference to `jack_port_register'
linuxband-player.c:(.text+0x12fd): undefined reference to `g_log'
linuxband-player.c:(.text+0x1330): undefined reference to `jack_activate'
linuxband-player.c:(.text+0x134d): undefined reference to `g_log'
/tmp/ccMI8YLK.o: In function `show_version':
linuxband-player.c:(.text+0x140e): undefined reference to `smf_get_version'
/tmp/ccMI8YLK.o: In function `main':
linuxband-player.c:(.text+0x148e): undefined reference to `g_thread_init'
linuxband-player.c:(.text+0x149d): undefined reference to `g_log_set_default_handler'
linuxband-player.c:(.text+0x1551): undefined reference to `g_log'
linuxband-player.c:(.text+0x15ef): undefined reference to `g_log'
linuxband-player.c:(.text+0x1619): undefined reference to `smf_load'
linuxband-player.c:(.text+0x1653): undefined reference to `g_log'
linuxband-player.c:(.text+0x1676): undefined reference to `smf_decode'
linuxband-player.c:(.text+0x1692): undefined reference to `g_log'
linuxband-player.c:(.text+0x16c8): undefined reference to `g_log'
linuxband-player.c:(.text+0x16e6): undefined reference to `g_timeout_add'
linuxband-player.c:(.text+0x1731): undefined reference to `g_log'
linuxband-player.c:(.text+0x1763): undefined reference to `jack_transport_locate'
linuxband-player.c:(.text+0x1772): undefined reference to `jack_transport_start'
linuxband-player.c:(.text+0x178b): undefined reference to `jack_frame_time'
linuxband-player.c:(.text+0x17b9): undefined reference to `g_main_loop_new'
linuxband-player.c:(.text+0x17c1): undefined reference to `g_main_loop_run'
/tmp/ccwcipSZ.o: In function `show_track':
midi.c:(.text+0x1b2): undefined reference to `g_log'
midi.c:(.text+0x1c7): undefined reference to `smf_event_decode'
midi.c:(.text+0x1ef): undefined reference to `g_log'
midi.c:(.text+0x204): undefined reference to `smf_track_get_event_by_number'
/tmp/ccwcipSZ.o: In function `show_smf':
midi.c:(.text+0x229): undefined reference to `smf_decode'
midi.c:(.text+0x245): undefined reference to `g_log'
midi.c:(.text+0x26f): undefined reference to `smf_get_track_by_number'
/tmp/ccwcipSZ.o: In function `find_song_end':
midi.c:(.text+0x2a6): undefined reference to `smf_event_is_metadata'
midi.c:(.text+0x2b6): undefined reference to `smf_event_decode'
midi.c:(.text+0x2f2): undefined reference to `smf_get_next_event'
/tmp/ccwcipSZ.o: In function `find_bar_end':
midi.c:(.text+0x350): undefined reference to `smf_event_is_metadata'
midi.c:(.text+0x360): undefined reference to `smf_event_decode'
midi.c:(.text+0x3ad): undefined reference to `smf_get_next_event'
/tmp/ccwcipSZ.o: In function `find_bar_num':
midi.c:(.text+0x40e): undefined reference to `smf_event_is_metadata'
midi.c:(.text+0x41e): undefined reference to `smf_event_decode'
midi.c:(.text+0x471): undefined reference to `smf_get_next_event'
/tmp/ccwcipSZ.o: In function `find_bar_num_seconds':
midi.c:(.text+0x4c0): undefined reference to `smf_rewind'
/tmp/ccwcipSZ.o: In function `get_bar_offsets':
midi.c:(.text+0x507): undefined reference to `smf_rewind'
/tmp/ccwcipSZ.o: In function `copy_event':
midi.c:(.text+0x57f): undefined reference to `smf_event_new_from_pointer'
/tmp/ccwcipSZ.o: In function `copy_events':
midi.c:(.text+0x5ad): undefined reference to `smf_seek_to_pulses'
midi.c:(.text+0x5f4): undefined reference to `smf_get_track_by_number'
midi.c:(.text+0x625): undefined reference to `smf_track_add_event_pulses'
midi.c:(.text+0x631): undefined reference to `smf_get_next_event'
/tmp/ccwcipSZ.o: In function `create_marker':
midi.c:(.text+0x677): undefined reference to `smf_event_new'
/tmp/ccwcipSZ.o: In function `create_empty_smf':
midi.c:(.text+0x70d): undefined reference to `smf_new'
midi.c:(.text+0x726): undefined reference to `smf_set_ppqn'
midi.c:(.text+0x75c): undefined reference to `smf_set_format'
midi.c:(.text+0x78c): undefined reference to `smf_track_new'
midi.c:(.text+0x7a3): undefined reference to `smf_add_track'
/tmp/ccwcipSZ.o: In function `copy_smf_bars':
midi.c:(.text+0x829): undefined reference to `smf_rewind'
midi.c:(.text+0x83a): undefined reference to `smf_get_track_by_number'
midi.c:(.text+0x84f): undefined reference to `smf_get_track_by_number'
midi.c:(.text+0x89f): undefined reference to `smf_event_decode'
midi.c:(.text+0x8d4): undefined reference to `smf_track_add_event_pulses'
midi.c:(.text+0x8e0): undefined reference to `smf_track_get_next_event'
midi.c:(.text+0x981): undefined reference to `smf_track_add_event_pulses'
/tmp/ccwcipSZ.o: In function `loop_smf':
midi.c:(.text+0x9ab): undefined reference to `smf_rewind'
midi.c:(.text+0x9f8): undefined reference to `smf_rewind'
midi.c:(.text+0xabc): undefined reference to `smf_get_track_by_number'
midi.c:(.text+0xb09): undefined reference to `smf_track_add_event_pulses'
/tmp/ccwcipSZ.o: In function `load_smf_data':
midi.c:(.text+0xb30): undefined reference to `smf_load_from_memory'
midi.c:(.text+0xb54): undefined reference to `g_log'
midi.c:(.text+0xb62): undefined reference to `smf_decode'
midi.c:(.text+0xb7e): undefined reference to `g_log'
/tmp/ccMUiLFf.o: In function `open_pipes':
remote_control.c:(.text+0xe9): undefined reference to `g_log'
remote_control.c:(.text+0x104): undefined reference to `g_log'
remote_control.c:(.text+0x157): undefined reference to `g_log'
remote_control.c:(.text+0x1a5): undefined reference to `g_log'
/tmp/ccMUiLFf.o:remote_control.c:(.text+0x1c7): more undefined references to `g_log' follow
/tmp/ccMUiLFf.o: In function `loop_song':
remote_control.c:(.text+0x311): undefined reference to `smf_peek_next_event'
remote_control.c:(.text+0x360): undefined reference to `g_log'
remote_control.c:(.text+0x376): undefined reference to `smf_seek_to_pulses'
remote_control.c:(.text+0x3a4): undefined reference to `smf_peek_next_event'
/tmp/ccMUiLFf.o: In function `check_event':
remote_control.c:(.text+0x42e): undefined reference to `g_log'
/tmp/ccMUiLFf.o: In function `partial_seek':
remote_control.c:(.text+0x468): undefined reference to `smf_peek_next_event'
remote_control.c:(.text+0x48f): undefined reference to `smf_rewind'
remote_control.c:(.text+0x49b): undefined reference to `smf_peek_next_event'
remote_control.c:(.text+0x4f3): undefined reference to `g_log'
remote_control.c:(.text+0x515): undefined reference to `smf_get_next_event'
remote_control.c:(.text+0x545): undefined reference to `smf_peek_next_event'
remote_control.c:(.text+0x59d): undefined reference to `g_log'
remote_control.c:(.text+0x5e9): undefined reference to `g_log'
/tmp/ccMUiLFf.o: In function `loop_seek':
remote_control.c:(.text+0x648): undefined reference to `g_log'
/tmp/ccMUiLFf.o: In function `free_smf':
remote_control.c:(.text+0x71a): undefined reference to `smf_delete'
/tmp/ccMUiLFf.o: In function `start_playback':
remote_control.c:(.text+0x757): undefined reference to `g_log'
remote_control.c:(.text+0x770): undefined reference to `jack_transport_start'
remote_control.c:(.text+0x781): undefined reference to `jack_frame_time'
/tmp/ccMUiLFf.o: In function `command_load':
remote_control.c:(.text+0x7ee): undefined reference to `g_log'
remote_control.c:(.text+0x849): undefined reference to `g_log'
remote_control.c:(.text+0x869): undefined reference to `g_log'
remote_control.c:(.text+0x884): undefined reference to `smf_delete'
/tmp/ccMUiLFf.o: In function `command_stop':
remote_control.c:(.text+0x8db): undefined reference to `jack_transport_stop'
/tmp/ccMUiLFf.o: In function `command_play':
remote_control.c:(.text+0x95e): undefined reference to `smf_rewind'
remote_control.c:(.text+0x9a5): undefined reference to `jack_transport_locate'
/tmp/ccMUiLFf.o: In function `command_play_from_bar':
remote_control.c:(.text+0xa18): undefined reference to `g_log'
remote_control.c:(.text+0xa71): undefined reference to `smf_rewind'
remote_control.c:(.text+0xab5): undefined reference to `g_log'
remote_control.c:(.text+0xb03): undefined reference to `jack_transport_locate'
remote_control.c:(.text+0xb1e): undefined reference to `smf_seek_to_seconds'
/tmp/ccMUiLFf.o: In function `command_play_bars':
remote_control.c:(.text+0xc41): undefined reference to `smf_rewind'
remote_control.c:(.text+0xc88): undefined reference to `jack_transport_locate'
/tmp/ccMUiLFf.o: In function `command_pause':
remote_control.c:(.text+0xce8): undefined reference to `jack_transport_stop'
remote_control.c:(.text+0xd17): undefined reference to `jack_transport_start'
/tmp/ccMUiLFf.o: In function `command_intro_length':
remote_control.c:(.text+0xda8): undefined reference to `g_log'
/tmp/ccMUiLFf.o: In function `command_finish':
remote_control.c:(.text+0xdd1): undefined reference to `jack_client_close'
/tmp/ccMUiLFf.o: In function `jack_shutdown':
remote_control.c:(.text+0xe00): undefined reference to `g_log'
/tmp/ccMUiLFf.o: In function `remote_control_loop':
remote_control.c:(.text+0xe65): undefined reference to `g_log'
remote_control.c:(.text+0xe8f): undefined reference to `g_log'
remote_control.c:(.text+0xeb7): undefined reference to `g_log'
remote_control.c:(.text+0xee1): undefined reference to `g_log'
/tmp/ccMUiLFf.o:remote_control.c:(.text+0xf0b): more undefined references to `g_log' follow
collect2: error: ld returned 1 exit status
make: *** [target/linuxband-player] Error 1
```


Any advise is appreciated....

bhatta
[/FONT]

---

### Post by steeldriver on 2013-06-29
Hmm well that appears to be quite a common issue due to the Makefile not being designed to work with newer versions of the gcc compiler - it's placing the dependent libraries ( -lgthread-2.0 -lglib-2.0   -ljack -lpthread -lrt   -lsmf -lm ) ahead of the source files that depend on them (src/main/c/linuxband-player.c src/main/c/midi.c src/main/c/remote_control.c) - that doesn't work

Unfortunately I don't know a way to fix that apart from getting your hands dirty and editing the Makefile to get everything in the right order - if it's not too long, you can post it (or at least the section for the linuxband-player target) and I will be happy to take a look

EDIT: WAIT... I just downloaded the 12.02[SIZE=3]**.1**[/SIZE] tarball and that appears to work right:

```

~/src/linuxband-12.02.1$ make
cc -o target/linuxband-player src/main/c/linuxband-player.c src/main/c/midi.c src/main/c/remote_control.c  -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include    -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include   -I.   -lglib-2.0   -pthread -lgthread-2.0 -lrt -lglib-2.0   -ljack -lpthread -lrt   -lsmf -lm -lglib-2.0

```

---

### Post by su:bhatta on 2013-06-30
Steeldriver ur a lifesaver... just downloaded the 12.02.1.. but no time this weekend .. gotta try tomorow...
r u a musician btw...

---

### Post by steeldriver on 2013-06-30
well I have a wall full of guitars - but I rarely make anything that could be called music come out of them :) I used to be into electronic music way back in the day when midi was just getting started (had a couple of synths including an original Yamaha DX7)

Post back if the 12.02.1 version doesn't fix it for you

---

### Post by su:bhatta on 2013-06-30
Just did ./configure, make & make install...

the last codes are below...
> 
root@nbe42:/usr/local/src/linuxband-12.02.1# make install
/usr/bin/install -c -d /usr/local/bin
/usr/bin/install -c -d /usr/local/lib/linuxband
/usr/bin/install -c -d /usr/local/share/linuxband
/usr/bin/install -c -t /usr/local/bin target/linuxband
/usr/bin/install -c -t /usr/local/lib/linuxband target/linuxband-player
/usr/bin/install -c -t /usr/local/share/linuxband target/linuxband.rc 
PY_SOURCE=$(cd src/main/python && find . -name '*.py'); \
        for F in ${PY_SOURCE}; do \
          /usr/bin/install -c -D src/main/python/$F /usr/local/share/linuxband/$F; done
/usr/bin/install -c -t /usr/local/share/linuxband src/main/config/default.mma
/usr/bin/install -c -t /usr/local/share/linuxband src/main/glade/gui.glade
/usr/bin/install -c COPYING /usr/local/share/linuxband/license.txt
/usr/bin/install -c -t /usr/local/share/linuxband src/main/resources/* 

Cant find any shortcuts to it in allpications menu... but starts from Alt+F2... that will do...


Good to know getting help from another musician... I got a few guitars of my own... and a broken down band added to it...
Married the drummer, so life ain't without good music of my own...

My fav is J.J.Cale btw... cool n laid back...

wanted the linuxband to keep us company.....

---

### Post by su:bhatta on 2013-07-01
One last help !! linuxband is working but there is no sound output... according to the 'download' page of their website i should have qsynth running , but i guess there is some configuration I am missing... the files can be exported as mma files.. but how do i play them?

Also I had  a look at this page : [http://uklinuxinfo.blogspot.in/2013/02/using-mma-to-generate-musical.html](http://uklinuxinfo.blogspot.in/2013/02/using-mma-to-generate-musical.html)

So do i need this a2jmidid to get the thing working? then I gotta compile that from the tarball!! Oh Boy!!

thanks,
bhatta

---

### Post by su:bhatta on 2013-07-01
Hey! Linuxband ain't opening any more... herez the codes: any help is appreciated:

> root@nbe42:~# linuxband

(linuxband:4376): libglade-WARNING **: could not find a parent that handles internal children for `vbox'
18:52:24 ERROR __load_grooves_from_cache Unable to load grooves from cache '/root/.linuxband/grooves.cache'
Traceback (most recent call last):
  File "/usr/local/share/linuxband/linuxband/mma/grooves.py", line 142, in __load_grooves_from_cache
    infile = file(fname, 'r')
IOError: [Errno 2] No such file or directory: '/root/.linuxband/grooves.cache'
Traceback (most recent call last):
  File "/usr/local/bin/linuxband", line 77, in <module>
    main()
  File "/usr/local/bin/linuxband", line 67, in main
    Gui()
  File "/usr/local/share/linuxband/linuxband/gui/gui.py", line 512, in __init__
    grooves.load_grooves(True)
  File "/usr/local/share/linuxband/linuxband/mma/grooves.py", line 41, in load_grooves
    self.__grooves_model, grooves_list = self.__load_grooves()
  File "/usr/local/share/linuxband/linuxband/mma/grooves.py", line 90, in __load_grooves
    self.__do_load_grooves(grooves_list, self.__config.get_mma_grooves_path())
  File "/usr/local/share/linuxband/linuxband/mma/grooves.py", line 115, in __do_load_grooves
    grooves_list.append([gname, doc, gdesc, author, time, full_name])
UnboundLocalError: local variable 'time' referenced before assignment

---

### Post by steeldriver on 2013-07-01
why are you trying to run it as root? what happens if you run it as your regular user?

---

### Post by su:bhatta on 2013-07-01
OK, I am marking this thread as closed. 

the main problem i had of installing Linuxband has been resolved , many thanks to Steeldriver....

Now there seems to be only the issue of reconfiguring jack, which seems to be because of installing libjack-dev during the process of installing Linuxband...

As for the sound problem, the utilisation of of Qsynth n Soundfonts as mentioned in [www.linuxband.org]("http://www.linuxband.org") will resolve the issue...

Thanks a ton to steeldriver for helping me in my first succesful compiling...

---

### Post by marianoa on 2013-07-02
did you manage to make it work in the end? I managed  to install linuxband but now I have problems connecting it to qsynth and jack and getting any sound out of it

---

### Post by su:bhatta on 2013-07-02
Nah man... couldn't get it to work in the end... I also tried the same combination of qsynth & jack.. never got a beep outta it...
but as i had wrote I marked the thread as 'solved' coz the original problem of compiling the LinuxBand was well taken care of thanx to steeldriver...
Just lemme know if it works at your end, would appreciate that .... i will keep a look out at this thread for the next week or so... n try from my end...

BTw, found another GUI for mma, Thatz calle Lemma.. herez their deal...

[http://welltemperedstudio.wordpress.com/code/lemma/](http://welltemperedstudio.wordpress.com/code/lemma/)

will try that out too.. good thing they hav .deb files, but very old.. 2 years n no updates, the guy said he has stopped developing it, coz he doesn't hav to...
U can check that out too....

---

### Post by marianoa on 2013-07-02
I managed to make it work! In qsynth I went in "Setup..." and in the "MIDI" tab I changed the value of "MIDI_driver" from alsa_seq to jack. When I saved the changes it asked me if I wanted to restart the qsynth engine which I did and at that point in the QJack connections window, in the "MIDI" tab I could see linuxband-player in the left panel (this was the case even before) and qsynth in the right panel (this didn't happen before). I connected the two, while in the "Audio" tab there was an automatic connection between qsynth and system. At this point pressing the play button in linuxband I could hear the music playback. Hope it helps, I can give you more details about my settings but what I wrote was the only thing that I modified manually after a standard installation of jack, qsynth and linuxband.

---

### Post by su:bhatta on 2013-07-02
Many thanks for sharing marianoa... Itz nearly 1 am here so will hafta try tomorow... Just a few quick questions to get the idea clear:
1) Did u install any soundfonts, like it is mentioned in linuxband.org?
2) Did u use patchage to route anything?

I got another thread running([http://ubuntuforums.org/showthread.php?t=2159192](http://ubuntuforums.org/showthread.php?t=2159192)) if u can throw some light there it would be invaluable...

If I can make it work then I will have fulfilled Sheldon Cooper's dream of replacing Raj with a short computer program....

---

### Post by marianoa on 2013-07-02
1) I think that the soundfont (at least a basic one) has been installed automatically together with qsynth (the actual package should be fluid-soundfont-gm)
2) I didn't use patchage, I just use the connection manager found in qjackctl (the JACK gui)

---

### Post by su:bhatta on 2013-07-03
Thanks ! Thanks a ton... I got linuxband working... 

here's a few things i found out which i wanted to share...
1) Under view tab in linux band u can choose 'path to mma grooves directory' u can select 3 libraries i) kara ii)stdlib & iii)yamaha
2)From options in qsynth u can choose soundfonts and i found fluid font already present there, i used fluid fonts...
3) I started Patchage while running linuxband & Qsynth and it showed the pathway from linuxband to qynth to output, that was for understandin patchage for future reference... may be a effects process like rakarrack can be used later to modify signals before it gets in qsynth...

I am puttin the findings here for future reference n any new user help...

Now the hurdle is to delete the drum, i already have a drummer & she wont be happy if she finds  she has been replaced with a simple program :)

---

### Post by marianoa on 2013-07-03
In a MMA file I've read a command like
```
Bass Off
```
to turn off the bass, maybe you can use something similar for the drums

---

### Post by su:bhatta on 2013-07-03
Thank u... definitely gonna try..
But am currently facing somee problems with jack...
maybe due to all that tweaking i did to get linuxband, midi, qsynth to work togather...

Jack isn't on the sound settings and is not the fallback which i had set it earlier...
If i run jack then system sound n other applications sounds r not being played/heard.... i stop jack n all is ok..

gotta get that right...

btw, do u use 13.04 studio or vanilla?

---

### Post by marianoa on 2013-07-03
I use a plain 13.04 version. I think that the fact that all non-jack compatible applications can't play any sound while jack is running cannot be helped

---

### Post by su:bhatta on 2013-07-03
It could be done previously... R u having the same problem urself, of no sound from non-jack compatible programs while jack is running?

I use Ubuntu Studio 13.04 n i used this page([https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro)) to set up the Jack configuration(so that Jack n Pulse run simultaneously) n got results for a couple of weeks, but i guess I tweaked something and the Fallback option brokedown..
Also, according to that page maybe I have to look at the Mixers n choose the correct controls.. 
lemme play around with them...

Boy u surely had to download a lotta stuff to get all that, Jack, linuxband Qsynth n all working...
r u a musician btw?

---

### Post by marianoa on 2013-07-03
I'm an amateur musician and a linux enthusiast so I like to try what the FLOSS world has to offer. Regarding the pulseaudio/jack compatibility, I managed to use a non jack compatible application while jack is running installing the package pulseaudio-module-jack and running the following commands after starting the jack server
```
pactl load-module module-jack-sink channels=2; pactl load-module module-jack-source channels=2;pacmd set-default-sink jack_out
```
as found here [http://trac.jackaudio.org/wiki/WalkThrough/User/PulseOnJack](http://trac.jackaudio.org/wiki/WalkThrough/User/PulseOnJack) (bottom of the page)

---

### Post by su:bhatta on 2013-07-03
Thanks for sharing....
I just resolved that issue of mine a couple of hours back... using the same codes... trac.jack was down for updates for last two days n today I got it to work... 

I am an amateur guitarist with a urge to learn linux... been usin 'buntu for last 3 years of and on,  just a month back finally took the plunge and shifted to Ubuntu Studio, so that I can record my jams n hav something to play along with...

PS: This post describes how to make the changes permanent so as not to run the command on terminal every time u start Jack...
[http://http://ubuntuforums.org/showthread.php?t=843012](http://http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by marianoa on 2013-07-04
There's probably another way to have pulseaudio and jack work together automatically. After installing pulseaudio-module-jack, in the qjackctl settings in the "Settings" tab you can change the jack server from "/usr/bin/jackd" to "/usr/bin/jackdbus", this jackdbus should be a pulseaudio-aware version of the jack server. At this point starting jack you should get the pulseaudio source and sink in the qjackctl connection window and they should be connected to the system input and output automatically.

Then if you still don't get any sound from a pulseaudio application (I tried using vlc) you should check with pavucontrol that the application is actually sending the sound to jack: when both jack and the application are running, pavucontrol shows you a menu in which you can choose to send the output from the specific application to jack, that's what happened to me trying to use vlc and jack together. 

jackdbus should be already installed but if it's not you can install it with apt-get/aptitude, the same holds for pavucontrol. I think that you've already installed pulseaudio-module-jack, it's necessary.

This is the cleanest method I've found so far, hope it's useful. Furthermore, turning jack on and off while a pulseaudio application is playing is practically seamless, the application keeps playing smoothly. As a last remark, I had to deal with pavucontrol only the first time, now vlc and jack interact just fine. Looks like the first time you use a pulseaudio application with jack you have to use pavucontrol to make it "talk" to jack but after that it just works.

---

### Post by su:bhatta on 2013-07-04
WOW, thats a nice share... 
But I have got that .sh file workin for me pretty good n don wanna change a winnin combination... next time i mess things up, n i am sure to do just that soon, i will employ this...

So whatz up with linuxband? I am using Patchage to connect things up, u tried that? its really easy n works gr8, but crashes too...

any other new things u try out yet, that might help create a band like sound over which to improvise?

---

