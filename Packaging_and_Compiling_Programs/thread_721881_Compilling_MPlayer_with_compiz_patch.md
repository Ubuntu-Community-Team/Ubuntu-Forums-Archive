---
title: "Compilling MPlayer with compiz patch"
date: 2008-03-11
forum: Packaging and Compiling Programs
---

### Post by Revenant86 on 2008-03-11
I have been following this guide [http://ubuntuforums.org/showthread.php?t=571556](http://ubuntuforums.org/showthread.php?t=571556) to compile MPlayer with the patch that will allow XV output while running in compiz. It works until I do sudo debian/rules binary and then I get this output:
cc -o mplayer mplayer.o m_property.o mp_fifo.o mp_msg.o mixer.o parser-mpcmd.o command.o asxparser.o codec-cfg.o cpudetect.o edl.o find_sub.o get_path.o m_config.o m_option.o m_struct.o mpcommon.o parser-cfg.o playtree.o playtreeparser.o spudec.o sub_cc.o subopt-helper.o subreader.o vobsub.o unrar_exec.o libvo/libvo.a libao2/libao2.a input/libinput.a vidix/libvidix.a libmpcodecs/libmpcodecs.a libaf/libaf.a libmpdemux/libmpdemux.a stream/stream.a libswscale/libswscale.a libvo/libosd.a libavformat/libavformat.a libavcodec/libavcodec.a libavutil/libavutil.a libpostproc/libpostproc.a loader/libloader.a mp3lib/libmp3.a liba52/liba52.a libmpeg2/libmpeg2.a libfaad2/libfaad2.a tremor/libvorbisidec.a dvdread/libdvdread.a libdvdcss/libdvdcss.a libass/libass.a osdep/libosdep.a -ldirectfb -lXext -lX11 -lpthread -lXss -lXv -lXinerama -lXxf86vm -lXxf86dga -lGL -ldl -lggi -lggiwmh -laa -lcaca -lcucul -lvga -lSDL -laudio -lXt -ldl -lartsc -lpthread -lgmodule-2.0 -ldl -lgthread-2.0 -lrt -lglib-2.0 -lesd -laudiofile -lm -laudiofile -lm -lfaac -lx264 -lpthread -lmp3lame -L/usr/lib -L/usr/lib -L/usr/lib -L/usr/lib -Wl,-z,noexecstack    -lncurses -lsmbclient -lpng -lz -ljpeg -lungif -lasound -ldl -lpthread -lcdda_interface -lcdda_paranoia -lfreetype -lz -lfontconfig  -L/usr/lib -lfribidi -lenca -lz -llzo2 -lmad -lspeex  -ltheora -logg   -ldts -lmpcdec -lliveMedia -lgroupsock -lUsageEnvironment -lBasicUsageEnvironment -lstdc++ -ldv -lxvidcore -lm -lpthread -ldl -rdynamic  -lm   
mp_msg.o: In function `mp_msg':
mp_msg.c:(.text+0x31a): undefined reference to `guiMessageBox'
command.o: In function `mp_property_fullscreen':
command.c:(.text+0x894): undefined reference to `guiGetEvent'
command.o: In function `run_command':
command.c:(.text+0x5003): undefined reference to `mplNext'
command.c:(.text+0x51f9): undefined reference to `guiGetEvent'
command.c:(.text+0x6882): undefined reference to `mplPrev'
libvo/libvo.a(x11_common.o): In function `vo_x11_check_events':
x11_common.c:(.text+0x3093): undefined reference to `guiGetEvent'
libvo/libvo.a(vo_x11.o): In function `config':
vo_x11.c:(.text+0xecf): undefined reference to `guiGetEvent'
libvo/libvo.a(vo_xover.o): In function `config':
vo_xover.c:(.text+0xcf2): undefined reference to `guiGetEvent'
libvo/libvo.a(vo_xv.o): In function `config':
vo_xv.c:(.text+0x1f74): undefined reference to `guiGetEvent'
libvo/libvo.a(vo_gl.o): In function `config':
vo_gl.c:(.text+0x146a): undefined reference to `guiGetEvent'
libvo/libvo.a(vo_gl2.o):vo_gl2.c:(.text+0x1dcb): more undefined references to `guiGetEvent' follow
collect2: ld returned 1 exit status
make[1]: *** [mplayer] Error 1
make[1]: Leaving directory `/usr/src/mplayer'
make: *** [build-stamp] Error 2
I have no clue what to do. I am running Gutsy.
UPDATE: Fixed. I just had to run make clean all.

---

### Post by heng on 2008-03-18
Try . I abused the epoch number to make sure it has a higher version number than the normal package maintainers version. You'll need to remove it to revert back (or perhaps Ubuntu will bump the epoch number too).

Its based on the ubuntu patchset so pulse should work.

edit: made a balls up of the link the first time.

---

### Post by heng on 2008-03-18
Try [this deb here]("http://www.srcf.ucam.org/~whg21/mplayer_1.0rc2~0compiz-1_i386.deb"). I abused the epoch number to make sure it has a higher version number than the normal package maintainers version. You'll need to remove it to revert back (or perhaps Ubuntu will bump the epoch number too).

Its based on the ubuntu patchset so pulse should work.

---

