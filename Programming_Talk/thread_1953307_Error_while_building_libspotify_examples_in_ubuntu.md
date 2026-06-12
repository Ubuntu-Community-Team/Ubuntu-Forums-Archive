---
title: "Error while building libspotify examples in ubuntu"
date: 2012-04-06
forum: Programming Talk
---

### Post by rahul_badboy on 2012-04-06
Hi!! I recently downloaded the libspotify c library and tried building the examples provided with distribution. However, it gave me an error while building the examples using make.

Here is the detailed error message. 

```

rahul@rahul-M14xR1:~/libspotify-11.1.60-Linux-i686-release/share/doc/libspotify/examples$ sudo make LIBSPOTIFY_PATH=../../../.. 
for a in jukebox spshell localfiles; do make -C $a LIBSPOTIFY_PATH="/home/rahul/libspotify-11.1.60-Linux-i686-release" all; done
make[1]: Entering directory `/home/rahul/libspotify-11.1.60-Linux-i686-release/share/doc/libspotify/examples/jukebox'
cc -I/usr/include/alsa   -I/home/rahul/libspotify-11.1.60-Linux-i686-release/include -Wall   -Wl,-rpath,/home/rahul/libspotify-11.1.60-Linux-i686-release/lib -L/home/rahul/libspotify-11.1.60-Linux-i686-release/lib -lasound   -lspotify jukebox.o appkey.o alsa-audio.o audio.o -o jukebox
jukebox.o: In function `try_jukebox_start':
jukebox.c:(.text+0x1c): undefined reference to `sp_playlist_num_tracks'
jukebox.c:(.text+0x5a): undefined reference to `sp_playlist_num_tracks'
jukebox.c:(.text+0xa8): undefined reference to `sp_playlist_track'
jukebox.c:(.text+0xd7): undefined reference to `sp_session_player_unload'
jukebox.c:(.text+0xf2): undefined reference to `sp_track_error'
jukebox.c:(.text+0x113): undefined reference to `sp_track_name'
jukebox.c:(.text+0x145): undefined reference to `sp_session_player_load'
jukebox.c:(.text+0x15a): undefined reference to `sp_session_player_play'
jukebox.o: In function `playlist_renamed':
jukebox.c:(.text+0x26b): undefined reference to `sp_playlist_name'
jukebox.c:(.text+0x2de): undefined reference to `sp_session_player_unload'
jukebox.o: In function `playlist_added':
jukebox.c:(.text+0x302): undefined reference to `sp_playlist_add_callbacks'
jukebox.c:(.text+0x313): undefined reference to `sp_playlist_name'
jukebox.o: In function `playlist_removed':
jukebox.c:(.text+0x357): undefined reference to `sp_playlist_remove_callbacks'
jukebox.o: In function `container_loaded':
jukebox.c:(.text+0x36a): undefined reference to `sp_playlistcontainer_num_playlists'
jukebox.o: In function `logged_in':
jukebox.c:(.text+0x399): undefined reference to `sp_session_playlistcontainer'
jukebox.c:(.text+0x3ad): undefined reference to `sp_error_message'
jukebox.c:(.text+0x3ef): undefined reference to `sp_playlistcontainer_add_callbacks'
jukebox.c:(.text+0x3fa): undefined reference to `sp_playlistcontainer_num_playlists'
jukebox.c:(.text+0x426): undefined reference to `sp_playlistcontainer_playlist'
jukebox.c:(.text+0x444): undefined reference to `sp_playlist_add_callbacks'
jukebox.c:(.text+0x455): undefined reference to `sp_playlist_name'
jukebox.c:(.text+0x481): undefined reference to `sp_playlistcontainer_num_playlists'
jukebox.o: In function `play_token_lost':
jukebox.c:(.text+0x668): undefined reference to `sp_session_player_unload'
jukebox.o: In function `track_ended':
jukebox.c:(.text+0x6a1): undefined reference to `sp_session_player_unload'
jukebox.c:(.text+0x6c6): undefined reference to `sp_playlist_remove_tracks'
jukebox.o: In function `main':
jukebox.c:(.text+0x82e): undefined reference to `sp_session_create'
jukebox.c:(.text+0x845): undefined reference to `sp_error_message'
jukebox.c:(.text+0x8c9): undefined reference to `sp_session_login'
jukebox.c:(.text+0x915): undefined reference to `clock_gettime'
jukebox.c:(.text+0x9cf): undefined reference to `sp_session_process_events'
alsa-audio.o: In function `alsa_open':
alsa-audio.c:(.text+0x25): undefined reference to `snd_pcm_open'
alsa-audio.c:(.text+0x40): undefined reference to `snd_pcm_hw_params_sizeof'
alsa-audio.c:(.text+0x76): undefined reference to `snd_pcm_hw_params_sizeof'
alsa-audio.c:(.text+0xa1): undefined reference to `snd_pcm_hw_params_any'
alsa-audio.c:(.text+0xbb): undefined reference to `snd_pcm_hw_params_set_access'
alsa-audio.c:(.text+0xd5): undefined reference to `snd_pcm_hw_params_set_format'
alsa-audio.c:(.text+0xf6): undefined reference to `snd_pcm_hw_params_set_rate'
alsa-audio.c:(.text+0x10f): undefined reference to `snd_pcm_hw_params_set_channels'
alsa-audio.c:(.text+0x12f): undefined reference to `snd_pcm_hw_params_get_period_size_min'
alsa-audio.c:(.text+0x14f): undefined reference to `snd_pcm_hw_params_get_period_size_max'
alsa-audio.c:(.text+0x17d): undefined reference to `snd_pcm_hw_params_set_period_size_near'
alsa-audio.c:(.text+0x191): undefined reference to `snd_strerror'
alsa-audio.c:(.text+0x1be): undefined reference to `snd_pcm_close'
alsa-audio.c:(.text+0x1e8): undefined reference to `snd_pcm_hw_params_get_period_size'
alsa-audio.c:(.text+0x1fc): undefined reference to `snd_strerror'
alsa-audio.c:(.text+0x222): undefined reference to `snd_pcm_close'
alsa-audio.c:(.text+0x23e): undefined reference to `snd_pcm_hw_params_get_buffer_size_min'
alsa-audio.c:(.text+0x250): undefined reference to `snd_pcm_hw_params_get_buffer_size_max'
alsa-audio.c:(.text+0x279): undefined reference to `snd_pcm_hw_params_set_buffer_size_near'
alsa-audio.c:(.text+0x28d): undefined reference to `snd_strerror'
alsa-audio.c:(.text+0x2ba): undefined reference to `snd_pcm_close'
alsa-audio.c:(.text+0x2d6): undefined reference to `snd_pcm_hw_params_get_buffer_size'
alsa-audio.c:(.text+0x2ea): undefined reference to `snd_strerror'
alsa-audio.c:(.text+0x310): undefined reference to `snd_pcm_close'
alsa-audio.c:(.text+0x32c): undefined reference to `snd_pcm_hw_params'
alsa-audio.c:(.text+0x340): undefined reference to `snd_strerror'
alsa-audio.c:(.text+0x366): undefined reference to `snd_pcm_close'
alsa-audio.c:(.text+0x375): undefined reference to `snd_pcm_sw_params_sizeof'
alsa-audio.c:(.text+0x3ab): undefined reference to `snd_pcm_sw_params_sizeof'
alsa-audio.c:(.text+0x3d6): undefined reference to `snd_pcm_sw_params_current'
alsa-audio.c:(.text+0x3ef): undefined reference to `snd_pcm_sw_params_set_avail_min'
alsa-audio.c:(.text+0x403): undefined reference to `snd_strerror'
alsa-audio.c:(.text+0x429): undefined reference to `snd_pcm_close'
alsa-audio.c:(.text+0x44d): undefined reference to `snd_pcm_sw_params_set_start_threshold'
alsa-audio.c:(.text+0x45e): undefined reference to `snd_strerror'
alsa-audio.c:(.text+0x484): undefined reference to `snd_pcm_close'
alsa-audio.c:(.text+0x4a0): undefined reference to `snd_pcm_sw_params'
alsa-audio.c:(.text+0x4b4): undefined reference to `snd_strerror'
alsa-audio.c:(.text+0x4da): undefined reference to `snd_pcm_close'
alsa-audio.c:(.text+0x4ec): undefined reference to `snd_pcm_prepare'
alsa-audio.c:(.text+0x500): undefined reference to `snd_strerror'
alsa-audio.c:(.text+0x526): undefined reference to `snd_pcm_close'
alsa-audio.o: In function `alsa_audio_start':
alsa-audio.c:(.text+0x591): undefined reference to `snd_pcm_close'
alsa-audio.c:(.text+0x609): undefined reference to `snd_pcm_wait'
alsa-audio.c:(.text+0x61d): undefined reference to `snd_pcm_avail_update'
alsa-audio.c:(.text+0x631): undefined reference to `snd_pcm_prepare'
alsa-audio.c:(.text+0x650): undefined reference to `snd_pcm_writei'
alsa-audio.o: In function `audio_init':
alsa-audio.c:(.text+0x6d0): undefined reference to `pthread_create'
collect2: ld returned 1 exit status
make[1]: *** [jukebox] Error 1
make[1]: Leaving directory `/home/rahul/libspotify-11.1.60-Linux-i686-release/share/doc/libspotify/examples/jukebox'
make[1]: Entering directory `/home/rahul/libspotify-11.1.60-Linux-i686-release/share/doc/libspotify/examples/spshell'
make[1]: Leaving directory `/home/rahul/libspotify-11.1.60-Linux-i686-release/share/doc/libspotify/examples/spshell'
make[1]: Entering directory `/home/rahul/libspotify-11.1.60-Linux-i686-release/share/doc/libspotify/examples/localfiles'
cc -I/home/rahul/libspotify-11.1.60-Linux-i686-release/include -Wall -Wl,-rpath,/home/rahul/libspotify-11.1.60-Linux-i686-release/lib -L/home/rahul/libspotify-11.1.60-Linux-i686-release/lib -lspotify main.o appkey.o -o posix_stu
main.o: In function `logged_in':
main.c:(.text+0x18): undefined reference to `sp_error_message'
main.c:(.text+0x63): undefined reference to `sp_localtrack_create'
main.c:(.text+0x71): undefined reference to `sp_session_playlistcontainer'
main.c:(.text+0x87): undefined reference to `sp_playlistcontainer_add_new_playlist'
main.c:(.text+0xb3): undefined reference to `sp_playlist_add_tracks'
main.o: In function `spotify_init':
main.c:(.text+0x163): undefined reference to `sp_session_create'
main.c:(.text+0x177): undefined reference to `sp_error_message'
main.c:(.text+0x1c2): undefined reference to `sp_session_login'
main.c:(.text+0x1d3): undefined reference to `sp_error_message'
main.o: In function `main':
main.c:(.text+0x310): undefined reference to `clock_gettime'
main.c:(.text+0x3c5): undefined reference to `sp_session_process_events'
collect2: ld returned 1 exit status
make[1]: *** [posix_stu] Error 1
make[1]: Leaving directory `/home/rahul/libspotify-11.1.60-Linux-i686-release/share/doc/libspotify/examples/localfiles'
make: *** [all] Error 2


```

---

### Post by MadCow108 on 2012-04-06
the build is buggy, it needs place the library after the objects:

```
cc -I/usr/include/alsa   -I/home/rahul/libspotify-11.1.60-Linux-i686-release/include -Wall   -Wl,-rpath,/home/rahul/libspotify-11.1.60-Linux-i686-release/lib -L/home/rahul/libspotify-11.1.60-Linux-i686-release/lib  jukebox.o appkey.o alsa-audio.o audio.o -lasound   -lspotify -o jukebox
```
please forward that to the distributor.

---

### Post by rahul_badboy on 2012-04-07
Thnks a lot.

---

