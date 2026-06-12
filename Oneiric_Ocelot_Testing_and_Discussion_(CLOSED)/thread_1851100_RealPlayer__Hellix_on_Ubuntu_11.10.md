---
title: "RealPlayer / Hellix on Ubuntu 11.10"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by zaoka on 2011-09-27
Can somebody tell me how to install latest RealPlayer or Hellix on new Ubuntu 11.10?

Please do not tell me to use different software because we use RealPlayer to watch paid video streaming and other software does not work.

Thanks a lot! :popcorn:

---

### Post by tr4st on 2011-09-27
[QUOTE=Download RealPlayer]https://helixcommunity.org/projects/player/files/download/3388[/QUOTE]
[QUOTE=Download Helix Player]https://helixcommunity.org/projects/player/files/download/2955[/QUOTE]
[QUOTE=How to install RPM Packages on Ubuntu]http://embraceubuntu.com/2005/09/23/installing-using-an-rpm-file/[/QUOTE]

Now you can download both videoplayers from their Developer Websites and install them with the 'How To' for RPM Packages :)
If you have any further question, please ask and don't be shy :P

---

### Post by zaoka on 2011-09-28
Hi,

It does not work that way. I converted to .deb and installed package, however, no sign of RealPlayer. 

When I tried to reinstall I got message that its already installed..

Its not listed under installed programs, also from Terminal commands "realplay" or "realplayer" does nothing.

??

---

### Post by SevenMachines on 2011-09-28
> **zaoka said:**
> Hi,

It does not work that way. I converted to .deb and installed package, however, no sign of RealPlayer. 

When I tried to reinstall I got message that its already installed..

Its not listed under installed programs, also from Terminal commands "realplay" or "realplayer" does nothing.

??
Is it not in opt, usually not on the system binary search path... so you need to
```
$ /opt/real/Realplayer/realplay
```or something similar?

If not try 
```
 $ dpkg -L realplayer
```
if thats the packages name anyway, see whats actually installed

---

### Post by sgage on 2011-09-28
> **zaoka said:**
> Can somebody tell me how to install latest RealPlayer or Hellix on new Ubuntu 11.10?

Please do not tell me to use different software because we use RealPlayer to watch paid video streaming and other software does not work.

Thanks a lot! :popcorn:

I have a relatively recent deb package of RealPlayer 11 Gold - I can't remember where I got it, so I can't post a link. It's more recent than the one at the Helix website. It's 8.5 MB - I'd be happy to email it to you if you want to send me a private msg with your email address.

I believe I had to install it with dpkg --force-depends, and if you're running 64-bit, you need to --force-architecture. 

I have a professional need to view Real files once in a while, and it does work.

---

### Post by drs305 on 2011-09-28
I found the RealPlayer11GOLD.deb at:
[http://www.mediafire.com/?tgynvjwmtvm]("http://www.mediafire.com/?tgynvjwmtvm")

It installed on a 64-bit system with:
```
sudo dpkg -i --force-architecture --force-depends RealPlayer11GOLD.deb
```

It ran with:
```
realplay
```

Added: I'd just updated the Community doc on RealPlayer in the past week, removing outdated information. The link to mediafire isn't included on that page since the Community docs generally don't provide commercial (even free) links. In my editing remarks I'd recommended removing the page, as hardly anyone uses RealPlayer any longer and it's not supported by Ubuntu or sponsors.  ;-)

---

### Post by sgage on 2011-09-28
> **drs305 said:**
> I found the RealPlayer11GOLD.deb at:
[http://www.mediafire.com/?tgynvjwmtvm]("http://www.mediafire.com/?tgynvjwmtvm")

It installed on a 64-bit system with:
```
sudo dpkg -i --force-architecture --force-depends RealPlayer11GOLD.deb
```

It ran with:
```
realplay
```

This deb is slightly larger than the one I have, so perhaps it is more recent. But yes, use dpkg with the appropriate --force options and you should be good to go.

---

### Post by zaoka on 2011-09-28
here is what I got:

> milica@milica-Aspire-5050:~$ cd ~/Desktop
milica@milica-Aspire-5050:~/Desktop$ sudo dpkg -i --force-architecture --force-depends RealPlayer11GOLD.deb
[sudo] password for milica: 
Selecting previously deselected package realplay.
(Reading database ... 154123 files and directories currently installed.)
Unpacking realplay (from RealPlayer11GOLD.deb) ...
dpkg: error processing RealPlayer11GOLD.deb (--install):
 trying to overwrite '/opt/real/RealPlayer/realplay.bin', which is also in package realplayer 11.0.2.2315-20101117
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 RealPlayer11GOLD.deb
milica@milica-Aspire-5050:~/Desktop$

---

### Post by zaoka on 2011-09-28
dpkg -L realplayer

> milica@milica-Aspire-5050:~/Desktop$ dpkg -L realplayer
/.
/opt
/opt/real
/opt/real/RealPlayer
/opt/real/RealPlayer/LICENSE
/opt/real/RealPlayer/share
/opt/real/RealPlayer/share/default
/opt/real/RealPlayer/share/default/pause.png
/opt/real/RealPlayer/share/default/clipinfo.png
/opt/real/RealPlayer/share/default/volume_popup_mid.png
/opt/real/RealPlayer/share/default/play.png
/opt/real/RealPlayer/share/default/volume_popup_mute.png
/opt/real/RealPlayer/share/default/prefs_internet.png
/opt/real/RealPlayer/share/default/congestion.png
/opt/real/RealPlayer/share/default/volume_mute.png
/opt/real/RealPlayer/share/default/volume_popup_off.png
/opt/real/RealPlayer/share/default/prefs_advanced.png
/opt/real/RealPlayer/share/default/prefs_content.png
/opt/real/RealPlayer/share/default/volume_off.png
/opt/real/RealPlayer/share/default/stop.png
/opt/real/RealPlayer/share/default/volume_popup_high.png
/opt/real/RealPlayer/share/default/prefs_mediatypes.png
/opt/real/RealPlayer/share/default/prefs_playback.png
/opt/real/RealPlayer/share/default/volume_low.png
/opt/real/RealPlayer/share/default/prefs_connection.png
/opt/real/RealPlayer/share/default/volume_popup_low.png
/opt/real/RealPlayer/share/default/volume_high.png
/opt/real/RealPlayer/share/default/prefs_raw.png
/opt/real/RealPlayer/share/default/prefs_hardware.png
/opt/real/RealPlayer/share/default/next.png
/opt/real/RealPlayer/share/default/prefs_proxy.png
/opt/real/RealPlayer/share/default/rewind.png
/opt/real/RealPlayer/share/default/fastforward.png
/opt/real/RealPlayer/share/default/prefs_transport.png
/opt/real/RealPlayer/share/default/tactoggle.png
/opt/real/RealPlayer/share/default/previous.png
/opt/real/RealPlayer/share/default/volume_mid.png
/opt/real/RealPlayer/share/realplay.xml
/opt/real/RealPlayer/share/icons
/opt/real/RealPlayer/share/icons/mime-audio-au_192x192.png
/opt/real/RealPlayer/share/icons/mime-audio-ogg_192x192.png
/opt/real/RealPlayer/share/icons/mime-text-realtext_192x192.png
/opt/real/RealPlayer/share/icons/mime-audio-ogg_48x48.png
/opt/real/RealPlayer/share/icons/mime-audio-wav_192x192.png
/opt/real/RealPlayer/share/icons/mime-video-mov_48x48.png
/opt/real/RealPlayer/share/icons/mime-audio-wav_48x48.png
/opt/real/RealPlayer/share/icons/mime-video-avi_192x192.png
/opt/real/RealPlayer/share/icons/mime-application-rpm_192x192.png
/opt/real/RealPlayer/share/icons/mime-video-swf_192x192.png
/opt/real/RealPlayer/share/icons/mime-video-generic_48x48.png
/opt/real/RealPlayer/share/icons/mime-application-rm_48x48.png
/opt/real/RealPlayer/share/icons/mime-audio-mp4_48x48.png
/opt/real/RealPlayer/share/icons/mime-video-ogg_48x48.png
/opt/real/RealPlayer/share/icons/mime-audio-mp3_192x192.png
/opt/real/RealPlayer/share/icons/mime-audio-generic_192x192.png
/opt/real/RealPlayer/share/icons/mime-video-mov_192x192.png
/opt/real/RealPlayer/share/icons/mime-application-ram_48x48.png
/opt/real/RealPlayer/share/icons/mime-audio-mp4_192x192.png
/opt/real/RealPlayer/share/icons/mime-video-avi_48x48.png
/opt/real/RealPlayer/share/icons/mime-video-rv_48x48.png
/opt/real/RealPlayer/share/icons/realplay_32x32.png
/opt/real/RealPlayer/share/icons/mime-video-swf_48x48.png
/opt/real/RealPlayer/share/icons/mime-audio-generic_48x48.png
/opt/real/RealPlayer/share/icons/realplay_16x16.png
/opt/real/RealPlayer/share/icons/mime-video-generic_192x192.png
/opt/real/RealPlayer/share/icons/mime-audio-aiff_192x192.png
/opt/real/RealPlayer/share/icons/mime-application-ogg_48x48.png
/opt/real/RealPlayer/share/icons/mime-video-ogg_192x192.png
/opt/real/RealPlayer/share/icons/mime-text-realtext_48x48.png
/opt/real/RealPlayer/share/icons/mime-audio-ra_192x192.png
/opt/real/RealPlayer/share/icons/mime-application-generic_48x48.png
/opt/real/RealPlayer/share/icons/mime-application-generic_192x192.png
/opt/real/RealPlayer/share/icons/realplay_192x192.png
/opt/real/RealPlayer/share/icons/mime-application-smil_192x192.png
/opt/real/RealPlayer/share/icons/mime-audio-ra_48x48.png
/opt/real/RealPlayer/share/icons/mime-application-ram_192x192.png
/opt/real/RealPlayer/share/icons/mime-application-ogg_192x192.png
/opt/real/RealPlayer/share/icons/mime-audio-mp3_48x48.png
/opt/real/RealPlayer/share/icons/realplay_48x48.png
/opt/real/RealPlayer/share/icons/mime-application-smil_48x48.png
/opt/real/RealPlayer/share/icons/mime-video-rv_192x192.png
/opt/real/RealPlayer/share/icons/mime-audio-au_48x48.png
/opt/real/RealPlayer/share/icons/mime-application-rpm_48x48.png
/opt/real/RealPlayer/share/icons/mime-audio-aiff_48x48.png
/opt/real/RealPlayer/share/icons/mime-application-rm_192x192.png
/opt/real/RealPlayer/share/hxplay_help.html
/opt/real/RealPlayer/share/realplay.applications
/opt/real/RealPlayer/share/realplay
/opt/real/RealPlayer/share/realplay/prefs_general.png
/opt/real/RealPlayer/share/realplay/embedded_logo.png
/opt/real/RealPlayer/share/realplay/setup_welcome.png
/opt/real/RealPlayer/share/realplay/icon.png
/opt/real/RealPlayer/share/realplay/setup_title.png
/opt/real/RealPlayer/share/realplay/playlist_error.png
/opt/real/RealPlayer/share/realplay/logo.png
/opt/real/RealPlayer/share/tigris.css
/opt/real/RealPlayer/share/locale
/opt/real/RealPlayer/share/locale/fr
/opt/real/RealPlayer/share/locale/fr/player.mo
/opt/real/RealPlayer/share/locale/fr/LICENSE
/opt/real/RealPlayer/share/locale/fr/widget.mo
/opt/real/RealPlayer/share/locale/fr/README
/opt/real/RealPlayer/share/locale/es
/opt/real/RealPlayer/share/locale/es/player.mo
/opt/real/RealPlayer/share/locale/es/LICENSE
/opt/real/RealPlayer/share/locale/es/widget.mo
/opt/real/RealPlayer/share/locale/es/README
/opt/real/RealPlayer/share/locale/zh_CN
/opt/real/RealPlayer/share/locale/zh_CN/player.mo
/opt/real/RealPlayer/share/locale/zh_CN/LICENSE
/opt/real/RealPlayer/share/locale/zh_CN/widget.mo
/opt/real/RealPlayer/share/locale/zh_CN/README
/opt/real/RealPlayer/share/locale/ko
/opt/real/RealPlayer/share/locale/ko/player.mo
/opt/real/RealPlayer/share/locale/ko/LICENSE
/opt/real/RealPlayer/share/locale/ko/widget.mo
/opt/real/RealPlayer/share/locale/ko/README
/opt/real/RealPlayer/share/locale/de
/opt/real/RealPlayer/share/locale/de/player.mo
/opt/real/RealPlayer/share/locale/de/LICENSE
/opt/real/RealPlayer/share/locale/de/widget.mo
/opt/real/RealPlayer/share/locale/de/README
/opt/real/RealPlayer/share/locale/zh_TW
/opt/real/RealPlayer/share/locale/zh_TW/player.mo
/opt/real/RealPlayer/share/locale/zh_TW/LICENSE
/opt/real/RealPlayer/share/locale/zh_TW/widget.mo
/opt/real/RealPlayer/share/locale/zh_TW/README
/opt/real/RealPlayer/share/locale/it
/opt/real/RealPlayer/share/locale/it/player.mo
/opt/real/RealPlayer/share/locale/it/LICENSE
/opt/real/RealPlayer/share/locale/it/widget.mo
/opt/real/RealPlayer/share/locale/it/README
/opt/real/RealPlayer/share/locale/pt_BR
/opt/real/RealPlayer/share/locale/pt_BR/player.mo
/opt/real/RealPlayer/share/locale/pt_BR/LICENSE
/opt/real/RealPlayer/share/locale/pt_BR/widget.mo
/opt/real/RealPlayer/share/locale/pt_BR/README
/opt/real/RealPlayer/share/locale/ja
/opt/real/RealPlayer/share/locale/ja/player.mo
/opt/real/RealPlayer/share/locale/ja/LICENSE
/opt/real/RealPlayer/share/locale/ja/widget.mo
/opt/real/RealPlayer/share/locale/ja/README
/opt/real/RealPlayer/share/realplay.desktop
/opt/real/RealPlayer/share/realplay.mime
/opt/real/RealPlayer/share/mimelnk
/opt/real/RealPlayer/share/mimelnk/text
/opt/real/RealPlayer/share/mimelnk/text/vnd.rn-realtext.desktop
/opt/real/RealPlayer/share/mimelnk/application
/opt/real/RealPlayer/share/mimelnk/application/sdp.desktop
/opt/real/RealPlayer/share/mimelnk/application/x-smil.desktop
/opt/real/RealPlayer/share/mimelnk/application/ogg.desktop
/opt/real/RealPlayer/share/mimelnk/application/vnd.rn-realmedia-secure.desktop
/opt/real/RealPlayer/share/mimelnk/application/vnd.rn-realmedia-vbr.desktop
/opt/real/RealPlayer/share/mimelnk/application/x-streamingmedia.desktop
/opt/real/RealPlayer/share/mimelnk/application/vnd.rn-realmedia.desktop
/opt/real/RealPlayer/share/mimelnk/video
/opt/real/RealPlayer/share/mimelnk/video/vnd.rn-realvideo.desktop
/opt/real/RealPlayer/share/mimelnk/video/x-3gpp2.desktop
/opt/real/RealPlayer/share/mimelnk/audio
/opt/real/RealPlayer/share/mimelnk/audio/x-pn-realaudio.desktop
/opt/real/RealPlayer/share/mimelnk/audio/x-wav.desktop
/opt/real/RealPlayer/share/mimelnk/audio/x-aac.desktop
/opt/real/RealPlayer/share/mimelnk/audio/x-m4a.desktop
/opt/real/RealPlayer/share/mimelnk/audio/x-mpegurl.desktop
/opt/real/RealPlayer/share/mimelnk/audio/x-aiff.desktop
/opt/real/RealPlayer/share/mimelnk/audio/mpeg.desktop
/opt/real/RealPlayer/share/mimelnk/audio/x-scpls.desktop
/opt/real/RealPlayer/share/mimelnk/audio/vnd.rn-realaudio.desktop
/opt/real/RealPlayer/share/realplay.keys
/opt/real/RealPlayer/share/superbuffer
/opt/real/RealPlayer/share/superbuffer/superbuffer.png
/opt/real/RealPlayer/share/superbuffer/track.png
/opt/real/RealPlayer/share/superbuffer/nonsuperb.png
/opt/real/RealPlayer/share/superbuffer/sliders.png
/opt/real/RealPlayer/share/superbuffer/superbufferlive.png
/opt/real/RealPlayer/share/distcode
/opt/real/RealPlayer/share/realplay.png
/opt/real/RealPlayer/doc
/opt/real/RealPlayer/mozilla
/opt/real/RealPlayer/mozilla/nphelix.xpt
/opt/real/RealPlayer/mozilla/nphelix.so
/opt/real/RealPlayer/realplay.bin
/opt/real/RealPlayer/codecs
/opt/real/RealPlayer/codecs/drv2.so
/opt/real/RealPlayer/codecs/colorcvt.so
/opt/real/RealPlayer/codecs/amrn.so
/opt/real/RealPlayer/codecs/wma9.so
/opt/real/RealPlayer/codecs/atrc.so
/opt/real/RealPlayer/codecs/drvc.so
/opt/real/RealPlayer/codecs/wmv8.so
/opt/real/RealPlayer/codecs/raac.so
/opt/real/RealPlayer/codecs/rv40.so
/opt/real/RealPlayer/codecs/rv20.so
/opt/real/RealPlayer/codecs/cook.so
/opt/real/RealPlayer/codecs/drv1.so
/opt/real/RealPlayer/codecs/rv30.so
/opt/real/RealPlayer/codecs/amrw.so
/opt/real/RealPlayer/codecs/sipr.so
/opt/real/RealPlayer/codecs/rv10.so
/opt/real/RealPlayer/codecs/ralf.so
/opt/real/RealPlayer/realplay
/opt/real/RealPlayer/plugins
/opt/real/RealPlayer/plugins/memfsys.so
/opt/real/RealPlayer/plugins/wmvrender.so
/opt/real/RealPlayer/plugins/pngrender.so
/opt/real/RealPlayer/plugins/wbmpfformat.so
/opt/real/RealPlayer/plugins/wbmprend.so
/opt/real/RealPlayer/plugins/amrff.so
/opt/real/RealPlayer/plugins/rpjpgplin.so
/opt/real/RealPlayer/plugins/mp3fformat.so
/opt/real/RealPlayer/plugins/mp3render.so
/opt/real/RealPlayer/plugins/smmrender.so
/opt/real/RealPlayer/plugins/rtrender.so
/opt/real/RealPlayer/plugins/clbascauth.so
/opt/real/RealPlayer/plugins/vsrlocal.so
/opt/real/RealPlayer/plugins/jpgrender.so
/opt/real/RealPlayer/plugins/gifrender.so
/opt/real/RealPlayer/plugins/hxsdp.so
/opt/real/RealPlayer/plugins/h263render.so
/opt/real/RealPlayer/plugins/imaprender.so
/opt/real/RealPlayer/plugins/rn5auth.so
/opt/real/RealPlayer/plugins/mp3metaff.so
/opt/real/RealPlayer/plugins/pcmrend.so
/opt/real/RealPlayer/plugins/rpgifplin.so
/opt/real/RealPlayer/plugins/ramrender.so
/opt/real/RealPlayer/plugins/aufformat.so
/opt/real/RealPlayer/plugins/sdpplin.so
/opt/real/RealPlayer/plugins/giffformat.so
/opt/real/RealPlayer/plugins/wmarender.so
/opt/real/RealPlayer/plugins/oggfformat.so
/opt/real/RealPlayer/plugins/rvrender.so
/opt/real/RealPlayer/plugins/vidsite.so
/opt/real/RealPlayer/plugins/theorarend.so
/opt/real/RealPlayer/plugins/hxxml.so
/opt/real/RealPlayer/plugins/vorbisrend.so
/opt/real/RealPlayer/plugins/jpgfformat.so
/opt/real/RealPlayer/plugins/smlrender.so
/opt/real/RealPlayer/plugins/mp4fformat.so
/opt/real/RealPlayer/plugins/swfrender.so
/opt/real/RealPlayer/plugins/rppngplin.so
/opt/real/RealPlayer/plugins/mp4arender.so
/opt/real/RealPlayer/plugins/rpfformat.so
/opt/real/RealPlayer/plugins/rtfformat.so
/opt/real/RealPlayer/plugins/pngfformat.so
/opt/real/RealPlayer/plugins/vsrcplin.so
/opt/real/RealPlayer/plugins/smplfsys.so
/opt/real/RealPlayer/plugins/smlfformat.so
/opt/real/RealPlayer/plugins/rmfformat.so
/opt/real/RealPlayer/plugins/swfformat.so
/opt/real/RealPlayer/plugins/ramfformat.so
/opt/real/RealPlayer/plugins/rarender.so
/opt/real/RealPlayer/plugins/hxrecordengine.so
/opt/real/RealPlayer/plugins/httpfsys.so
/opt/real/RealPlayer/plugins/asfff.so
/opt/real/RealPlayer/plugins/dtdrplin.so
/opt/real/RealPlayer/plugins/rprender.so
/opt/real/RealPlayer/plugins/audplin.so
/opt/real/RealPlayer/plugins/authmgr.so
/opt/real/RealPlayer/README
/opt/real/RealPlayer/postinst
/opt/real/RealPlayer/postinst/remove_path.sh
/opt/real/RealPlayer/postinst/uninstall_locale_files.sh
/opt/real/RealPlayer/postinst/install_menu.sh
/opt/real/RealPlayer/postinst/postuninst.sh
/opt/real/RealPlayer/postinst/install_misc.sh
/opt/real/RealPlayer/postinst/unregister_mime_types.sh
/opt/real/RealPlayer/postinst/uninstall_misc.sh
/opt/real/RealPlayer/postinst/profile.d
/opt/real/RealPlayer/postinst/profile.d/realplay.sh
/opt/real/RealPlayer/postinst/profile.d/realplay.csh
/opt/real/RealPlayer/postinst/install_icon_on_desktop.sh
/opt/real/RealPlayer/postinst/uninstall_menu.sh
/opt/real/RealPlayer/postinst/xdg-utils
/opt/real/RealPlayer/postinst/xdg-utils/xdg-desktop-menu
/opt/real/RealPlayer/postinst/xdg-utils/xdg-mime
/opt/real/RealPlayer/postinst/xdg-utils/xdg-desktop-icon
/opt/real/RealPlayer/postinst/xdg-utils/xdg-icon-resource
/opt/real/RealPlayer/postinst/install_gconf_settings.sh
/opt/real/RealPlayer/postinst/packaging_time_postinst.sh
/opt/real/RealPlayer/postinst/install_moz_prefs.sh
/opt/real/RealPlayer/postinst/setup_path.sh
/opt/real/RealPlayer/postinst/uninstall_gconf_settings.sh
/opt/real/RealPlayer/postinst/install_icon_resource.sh
/opt/real/RealPlayer/postinst/postinst.sh
/opt/real/RealPlayer/postinst/register_mime_types.sh
/opt/real/RealPlayer/postinst/uninstall_icon_resource.sh
/opt/real/RealPlayer/postinst/install_fedora_selinux_workaround.sh
/opt/real/RealPlayer/postinst/uninstall_moz_plugins.sh
/opt/real/RealPlayer/postinst/install_moz_plugins.sh
/opt/real/RealPlayer/postinst/functions
/opt/real/RealPlayer/postinst/install_locale_files.sh
/opt/real/RealPlayer/postinst/uninstall_icon_on_desktop.sh
/opt/real/RealPlayer/postinst/install_system_wide_sym_links_non_LSB.sh
/opt/real/RealPlayer/postinst/uninstall_system_wide_sym_links_non_LSB.sh
/opt/real/RealPlayer/common
/opt/real/RealPlayer/common/clntxres.so
/opt/real/RealPlayer/common/clntcore.so
/usr
/usr/share
/usr/share/doc
/usr/share/doc/realplayer
/usr/share/doc/realplayer/changelog.Debian.gz
/usr/share/doc/realplayer/copyright


---

### Post by cor2y on 2011-09-29
I have to ask , is there a reason that real player needs to be installed these days on linux?
I admit i havent played a ram/rm file in years but doesnt vlc and gstreamer codecs now have real media support?

---

### Post by sgage on 2011-09-29
> **cor2y said:**
> I have to ask , is there a reason that real player needs to be installed these days on linux?
I admit i havent played a ram/rm file in years but doesnt vlc and gstreamer codecs now have real media support?

I've never seen it, but if it exists, I wish someone would let me know about it.

---

### Post by cor2y on 2011-09-29
According to videolan.org ([http://www.videolan.org/vlc/features.html/](http://www.videolan.org/vlc/features.html/)) and gstreamer ([http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/)) they now have support for all versions of the real media codec both audio and video, of course i remember a few years ago real was trying to launch their own drm'd audio/video codec i have no idea if it ever took off but if its drm then neither vlc or gstreamer (which the default movie player for ubuntu uses) will be able to play it.

---

### Post by sgage on 2011-09-29
> **cor2y said:**
> According to videolan.org ([http://www.videolan.org/vlc/features.html/](http://www.videolan.org/vlc/features.html/)) and gstreamer ([http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-ugly-plugins/html/)) they now have support for all versions of the real media codec both audio and video, of course i remember a few years ago real was trying to launch their own drm'd audio/video codec i have no idea if it ever took off but if its drm then neither vlc or gstreamer (which the default movie player for ubuntu uses) will be able to play it.

When Totem plays an .rm file, I get audio but no video. I have the latest gstreamer "ugly" installed, which supposedly can do Real video according to the website, but no go.

---

### Post by cor2y on 2011-09-29
peculiar but like i said havent tried to play a rm file in years.

Well if its not too much trouble maybe file a bug with the gstreamer folks via gnome or launchpad let them know some real media files are still not working.

---

