---
title: "Where does ubuntu saves all its software?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by disappearedng on 2008-09-09
Hi everyone
I have recently installed Apache2 with apt-get (sudo apt-get install apache2)

The site [http://127.0.0.1](http://127.0.0.1) works. (It works!)

I am currently reading a book which teaches me how to use apache but I can't seem to find the htdocs folder which is needed for the index. 

Where does ubuntu install apache2 under?

---

### Post by wolfen69 on 2008-09-09
for example, if i do ```
locate vlc
```the following comes up:```
ed@ubuntu-gods:~$ locate vlc
/home/ed/.vlc
/home/ed/.vlc/cache
/home/ed/.vlc/vlcrc
/home/ed/.vlc/cache/CACHEDIR.TAG
/home/ed/.vlc/cache/plugins-04041e.dat
/usr/bin/svlc
/usr/bin/vlc
/usr/bin/wxvlc
/usr/lib/libvlc.so.0
/usr/lib/libvlc.so.0.0.0
/usr/lib/vlc
/usr/lib/mime/packages/vlc
/usr/lib/vlc/access
/usr/lib/vlc/access_filter
/usr/lib/vlc/access_output
/usr/lib/vlc/audio_filter
/usr/lib/vlc/audio_mixer
/usr/lib/vlc/audio_output
/usr/lib/vlc/codec
/usr/lib/vlc/control
/usr/lib/vlc/demux
/usr/lib/vlc/gui
/usr/lib/vlc/misc
/usr/lib/vlc/mux
/usr/lib/vlc/packetizer
/usr/lib/vlc/services_discovery
/usr/lib/vlc/stream_out
/usr/lib/vlc/video_chroma
/usr/lib/vlc/video_filter
/usr/lib/vlc/video_output
/usr/lib/vlc/visualization
/usr/lib/vlc/access/libaccess_directory_plugin.so
/usr/lib/vlc/access/libaccess_dv_plugin.so
/usr/lib/vlc/access/libaccess_fake_plugin.so
/usr/lib/vlc/access/libaccess_file_plugin.so
/usr/lib/vlc/access/libaccess_ftp_plugin.so
/usr/lib/vlc/access/libaccess_http_plugin.so
/usr/lib/vlc/access/libaccess_mms_plugin.so
/usr/lib/vlc/access/libaccess_smb_plugin.so
/usr/lib/vlc/access/libaccess_tcp_plugin.so
/usr/lib/vlc/access/libaccess_udp_plugin.so
/usr/lib/vlc/access/libcdda_plugin.so
/usr/lib/vlc/access/libdvb_plugin.so
/usr/lib/vlc/access/libdvdnav_plugin.so
/usr/lib/vlc/access/libdvdread_plugin.so
/usr/lib/vlc/access/libpvr_plugin.so
/usr/lib/vlc/access/libscreen_plugin.so
/usr/lib/vlc/access/libv4l_plugin.so
/usr/lib/vlc/access/libvcd_plugin.so
/usr/lib/vlc/access/libvcdx_plugin.so
/usr/lib/vlc/access_filter/libaccess_filter_dump_plugin.so
/usr/lib/vlc/access_filter/libaccess_filter_record_plugin.so
/usr/lib/vlc/access_filter/libaccess_filter_timeshift_plugin.so
/usr/lib/vlc/access_output/libaccess_output_dummy_plugin.so
/usr/lib/vlc/access_output/libaccess_output_file_plugin.so
/usr/lib/vlc/access_output/libaccess_output_http_plugin.so
/usr/lib/vlc/access_output/libaccess_output_udp_plugin.so
/usr/lib/vlc/audio_filter/liba52tofloat32_plugin.so
/usr/lib/vlc/audio_filter/liba52tospdif_plugin.so
/usr/lib/vlc/audio_filter/libaudio_format_plugin.so
/usr/lib/vlc/audio_filter/libbandlimited_resampler_plugin.so
/usr/lib/vlc/audio_filter/libdolby_surround_decoder_plugin.so
/usr/lib/vlc/audio_filter/libdtstofloat32_plugin.so
/usr/lib/vlc/audio_filter/libdtstospdif_plugin.so
/usr/lib/vlc/audio_filter/libequalizer_plugin.so
/usr/lib/vlc/audio_filter/libfixed32tofloat32_plugin.so
/usr/lib/vlc/audio_filter/libfixed32tos16_plugin.so
/usr/lib/vlc/audio_filter/libfloat32tos16_plugin.so
/usr/lib/vlc/audio_filter/libfloat32tos8_plugin.so
/usr/lib/vlc/audio_filter/libfloat32tou16_plugin.so
/usr/lib/vlc/audio_filter/libfloat32tou8_plugin.so
/usr/lib/vlc/audio_filter/libheadphone_channel_mixer_plugin.so
/usr/lib/vlc/audio_filter/liblinear_resampler_plugin.so
/usr/lib/vlc/audio_filter/libmpgatofixed32_plugin.so
/usr/lib/vlc/audio_filter/libnormvol_plugin.so
/usr/lib/vlc/audio_filter/libparam_eq_plugin.so
/usr/lib/vlc/audio_filter/libs16tofixed32_plugin.so
/usr/lib/vlc/audio_filter/libs16tofloat32_plugin.so
/usr/lib/vlc/audio_filter/libs16tofloat32swab_plugin.so
/usr/lib/vlc/audio_filter/libs8tofloat32_plugin.so
/usr/lib/vlc/audio_filter/libsimple_channel_mixer_plugin.so
/usr/lib/vlc/audio_filter/libtrivial_channel_mixer_plugin.so
/usr/lib/vlc/audio_filter/libtrivial_resampler_plugin.so
/usr/lib/vlc/audio_filter/libu8tofixed32_plugin.so
/usr/lib/vlc/audio_filter/libu8tofloat32_plugin.so
/usr/lib/vlc/audio_filter/libugly_resampler_plugin.so
/usr/lib/vlc/audio_mixer/libfloat32_mixer_plugin.so
/usr/lib/vlc/audio_mixer/libspdif_mixer_plugin.so
/usr/lib/vlc/audio_mixer/libtrivial_mixer_plugin.so
/usr/lib/vlc/audio_output/libalsa_plugin.so
/usr/lib/vlc/audio_output/libaout_file_plugin.so
/usr/lib/vlc/audio_output/libjack_plugin.so
/usr/lib/vlc/audio_output/liboss_plugin.so
/usr/lib/vlc/audio_output/libpulse_plugin.so
/usr/lib/vlc/codec/liba52_plugin.so
/usr/lib/vlc/codec/libadpcm_plugin.so
/usr/lib/vlc/codec/libaraw_plugin.so
/usr/lib/vlc/codec/libcinepak_plugin.so
/usr/lib/vlc/codec/libcmml_plugin.so
/usr/lib/vlc/codec/libcvdsub_plugin.so
/usr/lib/vlc/codec/libdts_plugin.so
/usr/lib/vlc/codec/libdvbsub_plugin.so
/usr/lib/vlc/codec/libfake_plugin.so
/usr/lib/vlc/codec/libffmpeg_plugin.so
/usr/lib/vlc/codec/libflacdec_plugin.so
/usr/lib/vlc/codec/liblibmpeg2_plugin.so
/usr/lib/vlc/codec/liblpcm_plugin.so
/usr/lib/vlc/codec/libmpeg_audio_plugin.so
/usr/lib/vlc/codec/libpng_plugin.so
/usr/lib/vlc/codec/librawvideo_plugin.so
/usr/lib/vlc/codec/libsdl_image_plugin.so
/usr/lib/vlc/codec/libspeex_plugin.so
/usr/lib/vlc/codec/libspudec_plugin.so
/usr/lib/vlc/codec/libsubsdec_plugin.so
/usr/lib/vlc/codec/libsvcdsub_plugin.so
/usr/lib/vlc/codec/libtelx_plugin.so
/usr/lib/vlc/codec/libvorbis_plugin.so
/usr/lib/vlc/control/libgestures_plugin.so
/usr/lib/vlc/control/libhotkeys_plugin.so
/usr/lib/vlc/control/libhttp_plugin.so
/usr/lib/vlc/control/liblirc_plugin.so
/usr/lib/vlc/control/libnetsync_plugin.so
/usr/lib/vlc/control/librc_plugin.so
/usr/lib/vlc/control/libshowintf_plugin.so
/usr/lib/vlc/control/libtelnet_plugin.so
/usr/lib/vlc/demux/liba52sys_plugin.so
/usr/lib/vlc/demux/libaiff_plugin.so
/usr/lib/vlc/demux/libasf_plugin.so
/usr/lib/vlc/demux/libau_plugin.so
/usr/lib/vlc/demux/libavi_plugin.so
/usr/lib/vlc/demux/libdemuxdump_plugin.so
/usr/lib/vlc/demux/libdtssys_plugin.so
/usr/lib/vlc/demux/libflac_plugin.so
/usr/lib/vlc/demux/libh264_plugin.so
/usr/lib/vlc/demux/libid3tag_plugin.so
/usr/lib/vlc/demux/liblive555_plugin.so
/usr/lib/vlc/demux/libm3u_plugin.so
/usr/lib/vlc/demux/libm4a_plugin.so
/usr/lib/vlc/demux/libm4v_plugin.so
/usr/lib/vlc/demux/libmjpeg_plugin.so
/usr/lib/vlc/demux/libmkv_plugin.so
/usr/lib/vlc/demux/libmod_plugin.so
/usr/lib/vlc/demux/libmp4_plugin.so
/usr/lib/vlc/demux/libmpc_plugin.so
/usr/lib/vlc/demux/libmpga_plugin.so
/usr/lib/vlc/demux/libmpgv_plugin.so
/usr/lib/vlc/demux/libnsc_plugin.so
/usr/lib/vlc/demux/libnsv_plugin.so
/usr/lib/vlc/demux/libnuv_plugin.so
/usr/lib/vlc/demux/libogg_plugin.so
/usr/lib/vlc/demux/libplaylist_plugin.so
/usr/lib/vlc/demux/libps_plugin.so
/usr/lib/vlc/demux/libpva_plugin.so
/usr/lib/vlc/demux/librawdv_plugin.so
/usr/lib/vlc/demux/libreal_plugin.so
/usr/lib/vlc/demux/libsgimb_plugin.so
/usr/lib/vlc/demux/libsubtitle_plugin.so
/usr/lib/vlc/demux/libts_plugin.so
/usr/lib/vlc/demux/libtta_plugin.so
/usr/lib/vlc/demux/libty_plugin.so
/usr/lib/vlc/demux/libvobsub_plugin.so
/usr/lib/vlc/demux/libvoc_plugin.so
/usr/lib/vlc/demux/libwav_plugin.so
/usr/lib/vlc/demux/libxa_plugin.so
/usr/lib/vlc/gui/libncurses_plugin.so
/usr/lib/vlc/gui/libskins2_plugin.so
/usr/lib/vlc/gui/libwxwidgets_plugin.so
/usr/lib/vlc/misc/libdummy_plugin.so
/usr/lib/vlc/misc/libexport_plugin.so
/usr/lib/vlc/misc/libfreetype_plugin.so
/usr/lib/vlc/misc/libgnutls_plugin.so
/usr/lib/vlc/misc/libgrowl_plugin.so
/usr/lib/vlc/misc/libipv4_plugin.so
/usr/lib/vlc/misc/libipv6_plugin.so
/usr/lib/vlc/misc/liblogger_plugin.so
/usr/lib/vlc/misc/libmemcpy_plugin.so
/usr/lib/vlc/misc/libnotify_plugin.so
/usr/lib/vlc/misc/libscreensaver_plugin.so
/usr/lib/vlc/misc/libvod_rtsp_plugin.so
/usr/lib/vlc/misc/libxml_plugin.so
/usr/lib/vlc/misc/libxtag_plugin.so
/usr/lib/vlc/mux/libmux_asf_plugin.so
/usr/lib/vlc/mux/libmux_avi_plugin.so
/usr/lib/vlc/mux/libmux_dummy_plugin.so
/usr/lib/vlc/mux/libmux_mp4_plugin.so
/usr/lib/vlc/mux/libmux_mpjpeg_plugin.so
/usr/lib/vlc/mux/libmux_ogg_plugin.so
/usr/lib/vlc/mux/libmux_ps_plugin.so
/usr/lib/vlc/mux/libmux_wav_plugin.so
/usr/lib/vlc/packetizer/libpacketizer_copy_plugin.so
/usr/lib/vlc/packetizer/libpacketizer_h264_plugin.so
/usr/lib/vlc/packetizer/libpacketizer_mpeg4audio_plugin.so
/usr/lib/vlc/packetizer/libpacketizer_mpeg4video_plugin.so
/usr/lib/vlc/packetizer/libpacketizer_mpegvideo_plugin.so
/usr/lib/vlc/services_discovery/libbonjour_plugin.so
/usr/lib/vlc/services_discovery/libhal_plugin.so
/usr/lib/vlc/services_discovery/libpodcast_plugin.so
/usr/lib/vlc/services_discovery/libsap_plugin.so
/usr/lib/vlc/services_discovery/libshout_plugin.so
/usr/lib/vlc/stream_out/libstream_out_bridge_plugin.so
/usr/lib/vlc/stream_out/libstream_out_description_plugin.so
/usr/lib/vlc/stream_out/libstream_out_display_plugin.so
/usr/lib/vlc/stream_out/libstream_out_dummy_plugin.so
/usr/lib/vlc/stream_out/libstream_out_duplicate_plugin.so
/usr/lib/vlc/stream_out/libstream_out_es_plugin.so
/usr/lib/vlc/stream_out/libstream_out_gather_plugin.so
/usr/lib/vlc/stream_out/libstream_out_mosaic_bridge_plugin.so
/usr/lib/vlc/stream_out/libstream_out_rtp_plugin.so
/usr/lib/vlc/stream_out/libstream_out_standard_plugin.so
/usr/lib/vlc/stream_out/libstream_out_switcher_plugin.so
/usr/lib/vlc/stream_out/libstream_out_transcode_plugin.so
/usr/lib/vlc/video_chroma/libi420_rgb_plugin.so
/usr/lib/vlc/video_chroma/libi420_ymga_plugin.so
/usr/lib/vlc/video_chroma/libi420_yuy2_plugin.so
/usr/lib/vlc/video_chroma/libi422_yuy2_plugin.so
/usr/lib/vlc/video_filter/libadjust_plugin.so
/usr/lib/vlc/video_filter/libblend_plugin.so
/usr/lib/vlc/video_filter/libclone_plugin.so
/usr/lib/vlc/video_filter/libcrop_plugin.so
/usr/lib/vlc/video_filter/libdeinterlace_plugin.so
/usr/lib/vlc/video_filter/libdistort_plugin.so
/usr/lib/vlc/video_filter/libinvert_plugin.so
/usr/lib/vlc/video_filter/liblogo_plugin.so
/usr/lib/vlc/video_filter/libmagnify_plugin.so
/usr/lib/vlc/video_filter/libmarq_plugin.so
/usr/lib/vlc/video_filter/libmosaic_plugin.so
/usr/lib/vlc/video_filter/libmotionblur_plugin.so
/usr/lib/vlc/video_filter/libmotiondetect_plugin.so
/usr/lib/vlc/video_filter/libosdmenu_plugin.so
/usr/lib/vlc/video_filter/librss_plugin.so
/usr/lib/vlc/video_filter/librv32_plugin.so
/usr/lib/vlc/video_filter/libscale_plugin.so
/usr/lib/vlc/video_filter/libtime_plugin.so
/usr/lib/vlc/video_filter/libtransform_plugin.so
/usr/lib/vlc/video_filter/libwall_plugin.so
/usr/lib/vlc/video_output/libaa_plugin.so
/usr/lib/vlc/video_output/libcaca_plugin.so
/usr/lib/vlc/video_output/libglx_plugin.so
/usr/lib/vlc/video_output/libimage_plugin.so
/usr/lib/vlc/video_output/libopengl_plugin.so
/usr/lib/vlc/video_output/libx11_plugin.so
/usr/lib/vlc/video_output/libxvideo_plugin.so
/usr/lib/vlc/visualization/libvisual_plugin.so
/usr/lib/vlc/visualization/libxosd_plugin.so
/usr/share/vlc
/usr/share/app-install/desktop/vlc.desktop
/usr/share/app-install/icons/vlc.png
/usr/share/applications/vlc.desktop
/usr/share/doc/libvlc0
/usr/share/doc/vlc
/usr/share/doc/vlc-nox
/usr/share/doc/vlc-plugin-pulse
/usr/share/doc/libvlc0/changelog.Debian.gz
/usr/share/doc/libvlc0/changelog.gz
/usr/share/doc/libvlc0/copyright
/usr/share/doc/vlc/bugreport-howto.txt
/usr/share/doc/vlc/changelog.Debian.gz
/usr/share/doc/vlc/changelog.gz
/usr/share/doc/vlc/copyright
/usr/share/doc/vlc/fortunes.txt.gz
/usr/share/doc/vlc/intf-cdda.txt.gz
/usr/share/doc/vlc/intf-vcd.txt.gz
/usr/share/locale/af/LC_MESSAGES/vlc.mo
/usr/share/locale/ar/LC_MESSAGES/vlc.mo
/usr/share/locale/ca/LC_MESSAGES/vlc.mo
/usr/share/locale/co/LC_MESSAGES/vlc.mo
/usr/share/locale/cs/LC_MESSAGES/vlc.mo
/usr/share/locale/da/LC_MESSAGES/vlc.mo
/usr/share/locale/de/LC_MESSAGES/vlc.mo
/usr/share/locale/en_GB/LC_MESSAGES/vlc.mo
/usr/share/locale/es/LC_MESSAGES/vlc.mo
/usr/share/locale/eu/LC_MESSAGES/vlc.mo
/usr/share/locale/fa/LC_MESSAGES/vlc.mo
/usr/share/locale/fr/LC_MESSAGES/vlc.mo
/usr/share/locale/fur/LC_MESSAGES/vlc.mo
/usr/share/locale/gl/LC_MESSAGES/vlc.mo
/usr/share/locale/he/LC_MESSAGES/vlc.mo
/usr/share/locale/hi/LC_MESSAGES/vlc.mo
/usr/share/locale/hu/LC_MESSAGES/vlc.mo
/usr/share/locale/it/LC_MESSAGES/vlc.mo
/usr/share/locale/ja/LC_MESSAGES/vlc.mo
/usr/share/locale/ka/LC_MESSAGES/vlc.mo
/usr/share/locale/ko/LC_MESSAGES/vlc.mo
/usr/share/locale/lt/LC_MESSAGES/vlc.mo
/usr/share/locale/lv/LC_MESSAGES/vlc.mo
/usr/share/locale/ms/LC_MESSAGES/vlc.mo
/usr/share/locale/nb/LC_MESSAGES/vlc.mo
/usr/share/locale/ne/LC_MESSAGES/vlc.mo
/usr/share/locale/nl/LC_MESSAGES/vlc.mo
/usr/share/locale/nn/LC_MESSAGES/vlc.mo
/usr/share/locale/oc/LC_MESSAGES/vlc.mo
/usr/share/locale/pa/LC_MESSAGES/vlc.mo
/usr/share/locale/pl/LC_MESSAGES/vlc.mo
/usr/share/locale/pt_BR/LC_MESSAGES/vlc.mo
/usr/share/locale/ro/LC_MESSAGES/vlc.mo
/usr/share/locale/ru/LC_MESSAGES/vlc.mo
/usr/share/locale/sk/LC_MESSAGES/vlc.mo
/usr/share/locale/sl/LC_MESSAGES/vlc.mo
/usr/share/locale/sq/LC_MESSAGES/vlc.mo
/usr/share/locale/sv/LC_MESSAGES/vlc.mo
/usr/share/locale/th/LC_MESSAGES/vlc.mo
/usr/share/locale/tr/LC_MESSAGES/vlc.mo
/usr/share/locale/zh_CN/LC_MESSAGES/vlc.mo
/usr/share/locale/zh_TW/LC_MESSAGES/vlc.mo
/usr/share/man/man1/svlc.1.gz
/usr/share/man/man1/vlc.1.gz
/usr/share/man/man1/wxvlc.1.gz
/usr/share/menu/vlc
/usr/share/pixmaps/vlc.png
/usr/share/vlc/http
/usr/share/vlc/osdmenu
/usr/share/vlc/pda-forwardb16x16.xpm
/usr/share/vlc/pda-openb16x16.xpm
/usr/share/vlc/pda-pauseb16x16.xpm
/usr/share/vlc/pda-playb16x16.xpm
/usr/share/vlc/pda-playlistb16x16.xpm
/usr/share/vlc/pda-preferencesb16x16.xpm
/usr/share/vlc/pda-rewindb16x16.xpm
/usr/share/vlc/pda-stopb16x16.xpm
/usr/share/vlc/skins2
/usr/share/vlc/vlc.xpm
/usr/share/vlc/vlc16x16.xpm
/usr/share/vlc/vlc48x48.ico
/usr/share/vlc/wxvlc.xpm
/usr/share/vlc/http/.hosts
/usr/share/vlc/http/dialogs
/usr/share/vlc/http/favicon.ico
/usr/share/vlc/http/iehacks.css
/usr/share/vlc/http/images
/usr/share/vlc/http/index.html
/usr/share/vlc/http/js
/usr/share/vlc/http/mosaic.html
/usr/share/vlc/http/old
/usr/share/vlc/http/requests
/usr/share/vlc/http/style.css
/usr/share/vlc/http/vlm.html
/usr/share/vlc/http/vlm_export.html
/usr/share/vlc/http/dialogs/.hosts
/usr/share/vlc/http/dialogs/browse
/usr/share/vlc/http/dialogs/footer
/usr/share/vlc/http/dialogs/input
/usr/share/vlc/http/dialogs/main
/usr/share/vlc/http/dialogs/mosaic
/usr/share/vlc/http/dialogs/playlist
/usr/share/vlc/http/dialogs/sout
/usr/share/vlc/http/dialogs/vlm
/usr/share/vlc/http/images/delete.png
/usr/share/vlc/http/images/delete_small.png
/usr/share/vlc/http/images/eject.png
/usr/share/vlc/http/images/empty.png
/usr/share/vlc/http/images/fullscreen.png
/usr/share/vlc/http/images/help.png
/usr/share/vlc/http/images/info.png
/usr/share/vlc/http/images/loop.png
/usr/share/vlc/http/images/minus.png
/usr/share/vlc/http/images/next.png
/usr/share/vlc/http/images/pause.png
/usr/share/vlc/http/images/play.png
/usr/share/vlc/http/images/playlist.png
/usr/share/vlc/http/images/playlist_small.png
/usr/share/vlc/http/images/plus.png
/usr/share/vlc/http/images/prev.png
/usr/share/vlc/http/images/refresh.png
/usr/share/vlc/http/images/repeat.png
/usr/share/vlc/http/images/sd.png
/usr/share/vlc/http/images/shuffle.png
/usr/share/vlc/http/images/slider_bar.png
/usr/share/vlc/http/images/slider_left.png
/usr/share/vlc/http/images/slider_point.png
/usr/share/vlc/http/images/slider_right.png
/usr/share/vlc/http/images/slow.png
/usr/share/vlc/http/images/snapshot.png
/usr/share/vlc/http/images/sort.png
/usr/share/vlc/http/images/sout.png
/usr/share/vlc/http/images/speaker.png
/usr/share/vlc/http/images/speaker_mute.png
/usr/share/vlc/http/images/stop.png
/usr/share/vlc/http/images/vlc16x16.png
/usr/share/vlc/http/images/volume_down.png
/usr/share/vlc/http/images/volume_up.png
/usr/share/vlc/http/images/white.png
/usr/share/vlc/http/images/white_cross_small.png
/usr/share/vlc/http/js/functions.js
/usr/share/vlc/http/js/mosaic.js
/usr/share/vlc/http/js/vlm.js
/usr/share/vlc/http/old/.hosts
/usr/share/vlc/http/old/admin
/usr/share/vlc/http/old/cone_minus.png
/usr/share/vlc/http/old/cone_plus.png
/usr/share/vlc/http/old/index.html
/usr/share/vlc/http/old/info.html
/usr/share/vlc/http/old/style.css
/usr/share/vlc/http/old/vlm
/usr/share/vlc/http/old/webcam.html
/usr/share/vlc/http/old/admin/.access
/usr/share/vlc/http/old/admin/browse.html
/usr/share/vlc/http/old/admin/dboxfiles.html
/usr/share/vlc/http/old/admin/index.html
/usr/share/vlc/http/old/vlm/edit.html
/usr/share/vlc/http/old/vlm/index.html
/usr/share/vlc/http/old/vlm/new.html
/usr/share/vlc/http/old/vlm/show.html
/usr/share/vlc/http/requests/browse.xml
/usr/share/vlc/http/requests/playlist.xml
/usr/share/vlc/http/requests/readme
/usr/share/vlc/http/requests/status.xml
/usr/share/vlc/http/requests/vlm.xml
/usr/share/vlc/http/requests/vlm_cmd.xml
/usr/share/vlc/osdmenu/default
/usr/share/vlc/osdmenu/default.cfg
/usr/share/vlc/osdmenu/dvd
/usr/share/vlc/osdmenu/dvd.cfg
/usr/share/vlc/osdmenu/default/selected
/usr/share/vlc/osdmenu/default/selection
/usr/share/vlc/osdmenu/default/unselected.png
/usr/share/vlc/osdmenu/default/volume
/usr/share/vlc/osdmenu/default/selected/bw.png
/usr/share/vlc/osdmenu/default/selected/esc.png
/usr/share/vlc/osdmenu/default/selected/fw.png
/usr/share/vlc/osdmenu/default/selected/next.png
/usr/share/vlc/osdmenu/default/selected/play_pause.png
/usr/share/vlc/osdmenu/default/selected/previous.png
/usr/share/vlc/osdmenu/default/selected/stop.png
/usr/share/vlc/osdmenu/default/selected/volume.png
/usr/share/vlc/osdmenu/default/selection/bw.png
/usr/share/vlc/osdmenu/default/selection/esc.png
/usr/share/vlc/osdmenu/default/selection/fw.png
/usr/share/vlc/osdmenu/default/selection/next.png
/usr/share/vlc/osdmenu/default/selection/play_pause.png
/usr/share/vlc/osdmenu/default/selection/previous.png
/usr/share/vlc/osdmenu/default/selection/stop.png
/usr/share/vlc/osdmenu/default/selection/volume.png
/usr/share/vlc/osdmenu/default/volume/volume_00.png
/usr/share/vlc/osdmenu/default/volume/volume_01.png
/usr/share/vlc/osdmenu/default/volume/volume_02.png
/usr/share/vlc/osdmenu/default/volume/volume_03.png
/usr/share/vlc/osdmenu/default/volume/volume_04.png
/usr/share/vlc/osdmenu/default/volume/volume_05.png
/usr/share/vlc/osdmenu/default/volume/volume_06.png
/usr/share/vlc/osdmenu/default/volume/volume_07.png
/usr/share/vlc/osdmenu/default/volume/volume_08.png
/usr/share/vlc/osdmenu/default/volume/volume_09.png
/usr/share/vlc/osdmenu/default/volume/volume_10.png
/usr/share/vlc/osdmenu/dvd/selected
/usr/share/vlc/osdmenu/dvd/selection
/usr/share/vlc/osdmenu/dvd/unselect
/usr/share/vlc/osdmenu/dvd/volume
/usr/share/vlc/osdmenu/dvd/selected/bw.png
/usr/share/vlc/osdmenu/dvd/selected/esc.png
/usr/share/vlc/osdmenu/dvd/selected/fw.png
/usr/share/vlc/osdmenu/dvd/selected/mute.png
/usr/share/vlc/osdmenu/dvd/selected/next.png
/usr/share/vlc/osdmenu/dvd/selected/pause.png
/usr/share/vlc/osdmenu/dvd/selected/play.png
/usr/share/vlc/osdmenu/dvd/selected/previous.png
/usr/share/vlc/osdmenu/dvd/selected/slow.png
/usr/share/vlc/osdmenu/dvd/selected/stop.png
/usr/share/vlc/osdmenu/dvd/selected/volume.png
/usr/share/vlc/osdmenu/dvd/selection/bw.png
/usr/share/vlc/osdmenu/dvd/selection/esc.png
/usr/share/vlc/osdmenu/dvd/selection/fw.png
/usr/share/vlc/osdmenu/dvd/selection/mute.png
/usr/share/vlc/osdmenu/dvd/selection/next.png
/usr/share/vlc/osdmenu/dvd/selection/pause.png
/usr/share/vlc/osdmenu/dvd/selection/play.png
/usr/share/vlc/osdmenu/dvd/selection/previous.png
/usr/share/vlc/osdmenu/dvd/selection/slow.png
/usr/share/vlc/osdmenu/dvd/selection/stop.png
/usr/share/vlc/osdmenu/dvd/unselect/barroff.png
/usr/share/vlc/osdmenu/dvd/volume/volume00.png
/usr/share/vlc/osdmenu/dvd/volume/volume01.png
/usr/share/vlc/osdmenu/dvd/volume/volume02.png
/usr/share/vlc/osdmenu/dvd/volume/volume03.png
/usr/share/vlc/osdmenu/dvd/volume/volume04.png
/usr/share/vlc/osdmenu/dvd/volume/volume05.png
/usr/share/vlc/skins2/default.vlt
/usr/share/vlc/skins2/fonts
/usr/share/vlc/skins2/skin.catalog
/usr/share/vlc/skins2/skin.dtd
/usr/share/vlc/skins2/winamp2.xml
/usr/share/vlc/skins2/fonts/FreeSans.ttf
/usr/share/vlc/skins2/fonts/FreeSansBold.ttf
/var/lib/dpkg/info/libvlc0.list
/var/lib/dpkg/info/libvlc0.md5sums
/var/lib/dpkg/info/libvlc0.postinst
/var/lib/dpkg/info/libvlc0.postrm
/var/lib/dpkg/info/libvlc0.shlibs
/var/lib/dpkg/info/vlc-nox.list
/var/lib/dpkg/info/vlc-nox.md5sums
/var/lib/dpkg/info/vlc-plugin-pulse.list
/var/lib/dpkg/info/vlc-plugin-pulse.md5sums
/var/lib/dpkg/info/vlc.list
/var/lib/dpkg/info/vlc.md5sums
/var/lib/dpkg/info/vlc.postinst
/var/lib/dpkg/info/vlc.postrm
ed@ubuntu-gods:~$ 


```
this would give you a good indication of what type of files are found in certain directories. doing: locate apache will probably give you a good idea of where that file is. this is a good way to learn what goes where.

---

### Post by mevets on 2008-09-09
you can find the folder in /var/www/

---

### Post by disappearedng on 2008-09-14
Thx guys.
 
But I am just curios as to where Ubuntu (and linux) generally saves applications. Under windows, we have a central location (program files) but then there is a bin and then an sbin. There's a bin under / but also under /share. Why are there so many different bins directory and sbins directory?

---

### Post by Mornedhel on 2008-09-14
The Wikipedia article : [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

The gory details : [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by its_jon on 2008-09-14
Thanks - I was wondering exactly the same as I liked to reskin some apps in windows....

I can't say I immediately grasp the structure on first glance....

Is it dangerous to attempt to alter some files/png's etc when found ?

---

### Post by mevets on 2008-09-14
i'd say its fine as long as you back the originals up.

---

### Post by scorp123 on 2008-09-14
> **wolfen69 said:**
> for example, if i do ```
locate vlc
``` Very inefficient!

Why not simply ask the package where it installed itself???  ```
dpkg -L NameOfPackage
``` I don't have Apache here, but let's do this with e.g. Firefox 3: 
```
dpkg -L firefox-3.0
/.
/usr
/usr/lib
/usr/lib/firefox-addons
/usr/lib/firefox-addons/extensions
/usr/lib/firefox-addons/plugins
/usr/lib/firefox-addons/searchplugins
/usr/lib/firefox-addons/searchplugins/amazondotcom.xml
/usr/lib/firefox-addons/searchplugins/answers.xml
/usr/lib/firefox-addons/searchplugins/creativecommons.xml
/usr/lib/firefox-addons/searchplugins/eBay.xml
/usr/lib/firefox-addons/searchplugins/google.xml
/usr/lib/firefox-addons/searchplugins/wikipedia.xml
/usr/lib/firefox-addons/searchplugins/yahoo.xml
/usr/lib/firefox-addons/searchplugins/debsearch.gif
/usr/lib/firefox-addons/searchplugins/debsearch.src
/usr/lib/firefox-3.0.1
/usr/lib/firefox-3.0.1/components
/usr/lib/firefox-3.0.1/components/aboutRobots.js
/usr/lib/firefox-3.0.1/components/FeedConverter.js
/usr/lib/firefox-3.0.1/components/FeedWriter.js
/usr/lib/firefox-3.0.1/components/fuelApplication.js
/usr/lib/firefox-3.0.1/components/nsBrowserContentHandler.js
/usr/lib/firefox-3.0.1/components/nsBrowserGlue.js
/usr/lib/firefox-3.0.1/components/nsMicrosummaryService.js
/usr/lib/firefox-3.0.1/components/nsPlacesTransactionsService.js
/usr/lib/firefox-3.0.1/components/nsSafebrowsingApplication.js
/usr/lib/firefox-3.0.1/components/nsSearchService.js
/usr/lib/firefox-3.0.1/components/nsSearchSuggestions.js
/usr/lib/firefox-3.0.1/components/nsSessionStartup.js
/usr/lib/firefox-3.0.1/components/nsSessionStore.js
/usr/lib/firefox-3.0.1/components/nsSetDefaultBrowser.js
/usr/lib/firefox-3.0.1/components/nsSidebar.js
/usr/lib/firefox-3.0.1/components/WebContentConverter.js
/usr/lib/firefox-3.0.1/components/browser.xpt
/usr/lib/firefox-3.0.1/components/libbrowsercomps.so
/usr/lib/firefox-3.0.1/components/libbrowserdirprovider.so
/usr/lib/firefox-3.0.1/modules
/usr/lib/firefox-3.0.1/modules/distribution.js
/usr/lib/firefox-3.0.1/firefox
/usr/lib/firefox-3.0.1/run-mozilla.sh
/usr/lib/firefox-3.0.1/defaults
/usr/lib/firefox-3.0.1/defaults/preferences
/usr/lib/firefox-3.0.1/defaults/preferences/firefox-l10n.js
/usr/lib/firefox-3.0.1/defaults/preferences/firefox.js
/usr/lib/firefox-3.0.1/defaults/preferences/firefox-branding.js
/usr/lib/firefox-3.0.1/defaults/preferences/channel-prefs.js
/usr/lib/firefox-3.0.1/defaults/preferences/ubuntu-useragent.js
/usr/lib/firefox-3.0.1/icons
/usr/lib/firefox-3.0.1/icons/mozicon16.xpm
/usr/lib/firefox-3.0.1/icons/mozicon50.xpm
/usr/lib/firefox-3.0.1/icons/document.png
/usr/lib/firefox-3.0.1/icons/mozicon128.png
/usr/lib/firefox-3.0.1/chrome
/usr/lib/firefox-3.0.1/chrome/en-US.jar
/usr/lib/firefox-3.0.1/chrome/en-US.manifest
/usr/lib/firefox-3.0.1/chrome/browser.jar
/usr/lib/firefox-3.0.1/chrome/browser.manifest
/usr/lib/firefox-3.0.1/chrome/classic.jar
/usr/lib/firefox-3.0.1/chrome/classic.manifest
/usr/lib/firefox-3.0.1/chrome/icons
/usr/lib/firefox-3.0.1/chrome/icons/default
/usr/lib/firefox-3.0.1/chrome/icons/default/default16.png
/usr/lib/firefox-3.0.1/chrome/icons/default/default32.png
/usr/lib/firefox-3.0.1/chrome/icons/default/default48.png
/usr/lib/firefox-3.0.1/browserconfig.properties
/usr/lib/firefox-3.0.1/blocklist.xml
/usr/lib/firefox-3.0.1/application.ini
/usr/lib/firefox-3.0.1/.autoreg
/usr/lib/firefox-3.0.1/firefox.sh
/usr/lib/firefox-3.0.1/firefox-3.0-restart-required.update-notifier
/usr/lib/firefox-3.0.1/ffox-3-beta-profile-migration-dialog
/usr/lib/xulrunner-addons
/usr/lib/xulrunner-addons/extensions
/usr/lib/xulrunner-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/usr/lib/xulrunner-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/usr/share
/usr/share/doc
/usr/share/doc/firefox-3.0
/usr/share/doc/firefox-3.0/copyright
/usr/share/doc/firefox-3.0/firefox.cfg
/usr/share/doc/firefox-3.0/MPL.gz
/usr/share/doc/firefox-3.0/changelog.Debian.gz
/usr/share/menu
/usr/share/menu/firefox-3.0
/usr/share/applications
/usr/share/applications/firefox.desktop
/usr/share/bug
/usr/share/bug/firefox-3.0
/usr/share/bug/firefox-3.0/presubj
/usr/share/apport
/usr/share/apport/package-hooks
/usr/share/apport/package-hooks/firefox-3.0.py
/usr/share/pixmaps
/usr/bin
/etc
/etc/firefox-3.0
/etc/firefox-3.0/profile
/etc/firefox-3.0/profile/bookmarks.html
/etc/firefox-3.0/profile/localstore.rdf
/etc/firefox-3.0/profile/prefs.js
/etc/firefox-3.0/profile/mimeTypes.rdf
/etc/firefox-3.0/profile/chrome
/etc/firefox-3.0/profile/chrome/userChrome-example.css
/etc/firefox-3.0/profile/chrome/userContent-example.css
/etc/firefox-3.0/pref
/etc/firefox-3.0/pref/firefox.js
/usr/lib/firefox-3.0.1/defaults/syspref
/usr/lib/firefox-3.0.1/defaults/profile
/usr/lib/firefox-3.0.1/extensions
/usr/lib/firefox-3.0.1/plugins
/usr/lib/firefox-3.0.1/searchplugins
/usr/lib/firefox-3.0.1/dictionaries
/usr/share/pixmaps/firefox-3.0.png
/usr/bin/firefox
/usr/bin/firefox-3.0
```

If you're not sure about a package name you can use 'dpkg -l' to list all packages that have a similar name. Example again with Firefox - I want to see a list of all packages that have "fox" in their name: ```
dpkg -l '*fox*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  firefox                   3.0.1+build1+nobinonly-0u meta package for the popular mozilla web browser
un  firefox-2                 <none>                    (no description available)
ii  firefox-3.0               3.0.1+build1+nobinonly-0u safe and easy web browser from Mozilla
ii  firefox-3.0-gnome-support 3.0.1+build1+nobinonly-0u Support for Gnome in Mozilla Firefox
ii  firefox-gnome-support     3.0.1+build1+nobinonly-0u meta package pointing to the latest gnome-support package for fire
un  firefox-granparadiso      <none>                    (no description available)
un  firefox-granparadiso-gnom <none>                    (no description available)
un  firefox-libthai           <none>                    (no description available)
un  firefox-trunk             <none>                    (no description available)
un  firefox-trunk-gnome-suppo <none>                    (no description available)
un  totem-gstreamer-firefox-p <none>                    (no description available)
un  totem-xine-firefox-plugin <none>                    (no description available)
ii  ubufox                    0.5-0ubuntu1              Ubuntu Firefox specific configuration defaults and apt support
```

So with "dpkg -l" and "dpkg -L" you should instantly get all the info you need and don't have to waste time with needless file searches that might not even produce the result you want. :D

---

