---
title: "gcc is unable to create an executable file."
date: 2007-01-21
forum: Programming Talk
---

### Post by montgoss on 2007-01-21
I have a fresh install of Ubuntu v6.10.  I'm trying to compile something and I get a weird error:```
montgoss@montgoss-desktop:~/downloads/mythtv-0.20$ ./configure 
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --cross-compile option.
C compiler test failed.
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
mythtv-dev@mythtv.org mailing list or IRC #mythtv on irc.freenode.net
Include the log file "config.err" produced by configure as this will help
solving the problem.
```

Per the error, here is config.err: ```
# ./configure 
BUILDSUF=''
CCONFIG=' linux release'
COLORTERM='gnome-terminal'
CONFIG_DEFINES=''
CONFIG_INCLUDEPATH=''
DBUS_SESSION_BUS_ADDRESS='unix:abstract=/tmp/dbus-QUMHd9qMHS,guid=5d15b44568e3201cf757b19a96754200'
DECODER_LIST='oggvorbis_decoder
h263_decoder
h261_decoder
mpeg4_decoder
msmpeg4v1_decoder
msmpeg4v2_decoder
msmpeg4v3_decoder
wmv1_decoder
wmv2_decoder
vc1_decoder
wmv3_decoder
h263i_decoder
flv_decoder
rv10_decoder
rv20_decoder
svq1_decoder
svq3_decoder
wmav1_decoder
wmav2_decoder
indeo2_decoder
indeo3_decoder
tscc_decoder
cscd_decoder
nuv_decoder
ulti_decoder
qdraw_decoder
xl_decoder
qpeg_decoder
loco_decoder
kmvc_decoder
wnv1_decoder
aasc_decoder
fraps_decoder
aac_decoder
mpeg4aac_decoder
mpeg1video_decoder
mpeg2video_decoder
mpegvideo_decoder
mpeg_xvmc_decoder
mpeg_xvmc_vld_decoder
dvvideo_decoder
mjpeg_decoder
mjpegb_decoder
sp5x_decoder
png_decoder
mp2_decoder
mp3_decoder
mp3adu_decoder
mp3on4_decoder
mace3_decoder
mace6_decoder
huffyuv_decoder
ffvhuff_decoder
ffv1_decoder
snow_decoder
cyuv_decoder
h264_decoder
vp3_decoder
theora_decoder
asv1_decoder
asv2_decoder
vcr1_decoder
cljr_decoder
fourxm_decoder
mdec_decoder
roq_decoder
interplay_video_decoder
xan_wc3_decoder
rpza_decoder
cinepak_decoder
msrle_decoder
msvideo1_decoder
vqa_decoder
idcin_decoder
eightbps_decoder
smc_decoder
flic_decoder
truemotion1_decoder
truemotion2_decoder
vmdvideo_decoder
vmdaudio_decoder
mszh_decoder
zlib_decoder
zmbv_decoder
smacker_decoder
smackaud_decoder
sonic_decoder
ac3_decoder
dts_decoder
ra_144_decoder
ra_288_decoder
roq_dpcm_decoder
interplay_dpcm_decoder
xan_dpcm_decoder
sol_dpcm_decoder
qtrle_decoder
flac_decoder
shorten_decoder
alac_decoder
ws_snd1_decoder
vorbis_decoder
libgsm_decoder
qdm2_decoder
cook_decoder
truespeech_decoder
tta_decoder
avs_decoder
cavs_decoder
rawvideo_decoder
flashsv_decoder
amr_nb_decoder
amr_wb_decoder
bmp_decoder
mmvideo_decoder
pcm_s32le_decoder
pcm_s32be_decoder
pcm_u32le_decoder
pcm_u32be_decoder
pcm_s24le_decoder
pcm_s24be_decoder
pcm_u24le_decoder
pcm_u24be_decoder
pcm_s24daud_decoder
pcm_s16le_decoder
pcm_s16be_decoder
pcm_u16le_decoder
pcm_u16be_decoder
pcm_s8_decoder
pcm_u8_decoder
pcm_alaw_decoder
pcm_mulaw_decoder
adpcm_ima_qt_decoder
adpcm_ima_wav_decoder
adpcm_ima_dk3_decoder
adpcm_ima_dk4_decoder
adpcm_ima_ws_decoder
adpcm_ima_smjpeg_decoder
adpcm_ms_decoder
adpcm_4xm_decoder
adpcm_xa_decoder
adpcm_adx_decoder
adpcm_ea_decoder
adpcm_g726_decoder
adpcm_ct_decoder
adpcm_swf_decoder
adpcm_yamaha_decoder
adpcm_sbpro_4_decoder
adpcm_sbpro_3_decoder
adpcm_sbpro_2_decoder
dvdsub_decoder
dvbsub_decoder'
DEMUXER_LIST='fourxm_demuxer
aiff_demuxer
amr_demuxer
asf_demuxer
au_demuxer
audio_demuxer
avi_demuxer
avs_demuxer
daud_demuxer
dc1394_demuxer
dv1394_demuxer
dv_demuxer
ea_demuxer
ffm_demuxer
flic_demuxer
flv_demuxer
gif_demuxer
gxf_demuxer
idcin_demuxer
roq_demuxer
image2_demuxer
image2pipe_demuxer
image_demuxer
imagepipe_demuxer
ipmovie_demuxer
matroska_demuxer
mm_demuxer
mmf_demuxer
mov_demuxer
mp3_demuxer
mpegps_demuxer
mpegts_demuxer
mxf_demuxer
nsv_demuxer
nut_demuxer
nuv_demuxer
ogg_demuxer
str_demuxer
shorten_demuxer
flac_demuxer
ac3_demuxer
dts_demuxer
aac_demuxer
h261_demuxer
h263_demuxer
m4v_demuxer
h264_demuxer
mpegvideo_demuxer
mjpeg_demuxer
ingenient_demuxer
pcm_s16le_demuxer
pcm_s16be_demuxer
pcm_u16le_demuxer
pcm_u16be_demuxer
pcm_s8_demuxer
pcm_u8_demuxer
pcm_mulaw_demuxer
pcm_alaw_demuxer
rawvideo_demuxer
rm_demuxer
rtsp_demuxer
sdp_demuxer
redir_demuxer
segafilm_demuxer
vmd_demuxer
smacker_demuxer
sol_demuxer
swf_demuxer
tta_demuxer
v4l2_demuxer
video_grab_device_demuxer
voc_demuxer
wav_demuxer
wc3_demuxer
wsaud_demuxer
wsvqa_demuxer
yuv4mpegpipe_demuxer'
DESKTOP_SESSION='default'
DISPLAY=':0.0'
ENCODER_LIST='ac3_encoder
mp2_encoder
mp3lame_encoder
oggvorbis_encoder
faac_encoder
flac_encoder
xvid_encoder
mpeg1video_encoder
h264_encoder
mpeg2video_encoder
h261_encoder
h263_encoder
h263p_encoder
flv_encoder
rv10_encoder
rv20_encoder
mpeg4_encoder
msmpeg4v1_encoder
msmpeg4v2_encoder
msmpeg4v3_encoder
wmv1_encoder
wmv2_encoder
svq1_encoder
mjpeg_encoder
ljpeg_encoder
jpegls_encoder
png_encoder
ppm_encoder
pgm_encoder
pgmyuv_encoder
pbm_encoder
pam_encoder
huffyuv_encoder
ffvhuff_encoder
asv1_encoder
asv2_encoder
ffv1_encoder
snow_encoder
zlib_encoder
dvvideo_encoder
sonic_encoder
sonic_ls_encoder
x264_encoder
libgsm_encoder
rawvideo_encoder
amr_nb_encoder
amr_wb_encoder
pcm_s32le_encoder
pcm_s32be_encoder
pcm_u32le_encoder
pcm_u32be_encoder
pcm_s24le_encoder
pcm_s24be_encoder
pcm_u24le_encoder
pcm_u24be_encoder
pcm_s24daud_encoder
pcm_s16le_encoder
pcm_s16be_encoder
pcm_u16le_encoder
pcm_u16be_encoder
pcm_s8_encoder
pcm_u8_encoder
pcm_alaw_encoder
pcm_mulaw_encoder
adpcm_ima_qt_encoder
adpcm_ima_wav_encoder
adpcm_ima_dk3_encoder
adpcm_ima_dk4_encoder
adpcm_ima_ws_encoder
adpcm_ima_smjpeg_encoder
adpcm_ms_encoder
adpcm_4xm_encoder
adpcm_xa_encoder
adpcm_adx_encoder
adpcm_ea_encoder
adpcm_g726_encoder
adpcm_ct_encoder
adpcm_swf_encoder
adpcm_yamaha_encoder
adpcm_sbpro_4_encoder
adpcm_sbpro_3_encoder
adpcm_sbpro_2_encoder
dvdsub_encoder
dvbsub_encoder'
EXESUF=''
FFLDFLAGS='-Wl,--warn-common'
FFMPEG_CONFIGURATION=' '
FFSERVERLDFLAGS='-Wl,-E'
GDMSESSION='default'
GDM_XSERVER_LOCATION='local'
GNOME_DESKTOP_SESSION_ID='Default'
GNOME_KEYRING_SOCKET='/tmp/keyring-MvJg94/socket'
GTK_RC_FILES='/etc/gtk/gtkrc:/home/montgoss/.gtkrc-1.2-gnome2'
HISTCONTROL='ignoredups'
HOME='/home/montgoss'
IFS=' 	
'
LANG='en_US.UTF-8'
LDCONFIG='ldconfig'
LESSCLOSE='/usr/bin/lesspipe %s %s'
LESSOPEN='| /usr/bin/lesspipe %s'
LIB='$(LIBPREF)$(NAME)$(LIBSUF)'
LIBOBJFLAGS=''
LIBPREF='lib'
LIBSUF='.a'
LOGNAME='montgoss'
LS_COLORS='no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:'
MUXER_LIST='adts_muxer
aiff_muxer
amr_muxer
asf_muxer
asf_stream_muxer
au_muxer
audio_muxer
avi_muxer
crc_muxer
framecrc_muxer
dv_muxer
ffm_muxer
flv_muxer
gif_muxer
gxf_muxer
image2_muxer
image2pipe_muxer
image_muxer
imagepipe_muxer
mmf_muxer
mov_muxer
tgp_muxer
mp4_muxer
psp_muxer
tg2_muxer
mp2_muxer
mp3_muxer
mpeg1system_muxer
mpeg1vcd_muxer
mpeg2vob_muxer
mpeg2svcd_muxer
mpeg2dvd_muxer
mpegts_muxer
mpjpeg_muxer
nut_muxer
ogg_muxer
flac_muxer
ac3_muxer
h261_muxer
h263_muxer
m4v_muxer
h264_muxer
mpeg1video_muxer
mpeg2video_muxer
mjpeg_muxer
pcm_s16le_muxer
pcm_s16be_muxer
pcm_u16le_muxer
pcm_u16be_muxer
pcm_s8_muxer
pcm_u8_muxer
pcm_mulaw_muxer
pcm_alaw_muxer
rawvideo_muxer
null_muxer
rm_muxer
rtp_muxer
swf_muxer
voc_muxer
wav_muxer
yuv4mpegpipe_muxer'
OLDPWD='/home/montgoss'
OPTIND='1'
PARSER_LIST='mpegvideo_parser
mpeg4video_parser
cavsvideo_parser
h261_parser
h263_parser
h264_parser
mjpeg_parser
pnm_parser
mpegaudio_parser
ac3_parser
dvdsub_parser
dvbsub_parser
aac_parser'
PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games'
PPID='6611'
PREFIX='/usr/local'
PROFILEFLAGS=''
PS1='$ '
PS2='> '
PS4='+ '
PWD='/home/montgoss/downloads/mythtv-0.20'
SESSION_MANAGER='local/montgoss-desktop:/tmp/.ICE-unix/4575'
SHELL='/bin/bash'
SHFLAGS='-shared -Wl,-soname,$@'
SHLVL='1'
SLIBNAME='$(SLIBPREF)$(NAME)$(SLIBSUF)'
SLIBNAME_WITH_MAJOR='$(SLIBNAME).$(LIBMAJOR)'
SLIBNAME_WITH_VERSION='$(SLIBNAME).$(LIBVERSION)'
SLIBPREF='lib'
SLIBSUF='.so'
SSH_AGENT_PID='4610'
SSH_AUTH_SOCK='/tmp/ssh-CjHQtb4575/agent.4575'
TERM='xterm'
TMPC='/tmp/ffmpeg-conf--7132-.c'
TMPDIR1='/tmp'
TMPE='/tmp/ffmpeg-conf--7132-'
TMPH='/tmp/ffmpeg-conf--7132-.h'
TMPO='/tmp/ffmpeg-conf--7132-.o'
TMPS='/tmp/ffmpeg-conf--7132-.S'
USER='montgoss'
USERNAME='montgoss'
VHOOKFLAGS='-shared -Wl,-soname,$@'
WINDOWID='41943135'
XAUTHORITY='/home/montgoss/.Xauthority'
_='./configure'
a52='yes'
a52bin='no'
altivec='default'
amr_if2='no'
amr_nb='no'
amr_nb_fixed='no'
amr_wb='no'
appleremote='no'
ar='ar'
asmalign_pot='unknown'
audio_alsa='default'
audio_arts='default'
audio_beos='no'
audio_jack='default'
audio_oss='default'
backend='yes'
bigendian='no'
bindings_perl='no'
bindir=''
bktr='no'
cc='gcc'
ccache='yes'
compile_type='release'
cpu='x86'
cpu_overide='no'
cpu_raw='i686'
cross_compile='no'
cross_prefix=''
cxx='g++'
dbox2_dvb_box='yes'
dc1394='no'
debug='no'
direct_fb='no'
direct_x='no'
distcc='yes'
dlfcn='no'
dlopen='no'
dostrip='yes'
dts='yes'
dv1394='no'
dvb='no'
dvb_path='/usr/include'
emu_fast_int='no'
extralibs='-lm'
faac='no'
faad='no'
faadbin='no'
ffplay='no'
ffserver='no'
firewire_cable_box='yes'
freebox_box='yes'
frontend='yes'
gpl='yes'
gprof='no'
hdhomerun_box='yes'
incdir=''
installstrip='-s'
inttypes='yes'
ip_network_recorder='yes'
ipv6='yes'
ivtv='yes'
ivtv_header='no'
iwmmxt='default'
joystick_menu='yes'
libdir=''
libdir_name='lib'
libgsm='no'
libogg='no'
lirc='yes'
logfile='config.err'
logging='yes'
lshared='no'
lstatic='yes'
mac_accel='no'
make='make'
mandir=''
memalignhack='no'
mingw32='no'
mingwce='no'
mmi='default'
mmx='default'
mp3lame='no'
mpegaudio_hp='yes'
need_inet_aton='no'
netserver='no'
network='yes'
opengl='no'
opengl_vsync='no'
optimize='yes'
os2='no'
powerpc_perf='no'
pp='yes'
proc_opt='no'
processor='model name	: AMD Athlon(tm) 64 Processor 3400+'
processor_flags='flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext lm 3dnowext 3dnow up ts fid vid ttp'
protocols='yes'
pthreads='no'
ranlib='ranlib'
shared_pp='no'
shlibdir=''
simpleidct='yes'
source_path='/home/montgoss/downloads/mythtv-0.20'
source_path_used='no'
strip='strip'
sunmlib='no'
swscaler='no'
targetos='Linux'
tune='generic'
v4l='yes'
v4l2='no'
valgrind='no'
vhook='no'
vorbis='no'
x11='yes'
x11_include_path='/usr/X11R6/include'
x264='no'
x86_64_cpus='x86-64,athlon64,k8,opteron,athlon-fx,nocona'
x86_cmov_cpus='i686,pentiumpro,pentium2,pentium3,pentium3m,pentium-m,,pentium4,pentium4m,prescott,athlon,,athlon-xp,athlon-tbird,athlon-4,athlon-mp,,c3-2'
x86_cpus='i386,i486,i586,i686,pentium,pentiumpro,pentium-mmx,pentium2,pentium3,pentium3m,pentium-m,pentium4,pentium4m,prescott,athlon,athlon-xp,athlon-tbird,athlon-4,athlon-mp,,c3,c3-2,k6,k6-2,k6-3'
x86_mmx_cpus='pentium-mmx,pentium2,pentium3,pentium3m,pentium-m,pentium4,pentium4m,prescott,athlon,athlon-xp,athlon-tbird,athlon-4,athlon-mp,,c3,c3-2,k6,k6-2,k6-3'
xrandr='yes'
xv='yes'
xvid='no'
xvmc='no'
xvmc_lib=''
xvmc_opengl='no'
xvmc_pro='no'
xvmc_vld='yes'
xvmcw='yes'
zlib='yes'
check_ld
check_cc
BEGIN /tmp/ffmpeg-conf--7132-.c
     1	int main(){
     2	    return 0;
     3	}
END /tmp/ffmpeg-conf--7132-.c
gcc -c -o /tmp/ffmpeg-conf--7132-.o /tmp/ffmpeg-conf--7132-.c
gcc -Wl,--warn-common -o /tmp/ffmpeg-conf--7132- /tmp/ffmpeg-conf--7132-.o -lm
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
C compiler test failed.
```

Any ideas what is happening?

Someone else had a problem with gcc and the first thing asked for was a test compile.  So, I made test.c which contains ```
#include "stdio.h"

int main()
{
  printf("hello world\n");
}
```My attempt to compile that produces: ```
montgoss@montgoss-desktop:~/downloads/mythtv-0.20$ gcc -o test test.c 
test.c:1:19: error: stdio.h: No such file or directory
test.c: In function ‘main’:
test.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
```
Does that give you any idea what's going on?

---

### Post by runningwithscissors on 2007-01-21
crt1.o should be part of glibc.
Are you using a cross-compiler? If so, see this error message from your output
```
If gcc is a cross-compiler, use the --cross-compile option.
```

Also, what does this return?

$ find /usr -name "crt1.o"

If you find it: you could try exporting the path of the crt1.o parent directory as shell variable GCC_EXEC_PREFIX
$ export GCC_EXEC_PREFIX="<path for crt1.o directory>"

And then compiling.

---

### Post by po0f on 2007-01-21
montgoss,

You probably installed just gcc, install [build-essential](http://packages.ubuntu.com/edgy/devel/build-essential) as well.

---

### Post by phossal on 2007-01-21
> **po0f said:**
> You probably installed just gcc, install [build-essential](http://packages.ubuntu.com/edgy/devel/build-essential) as well.

Likely. In fact, I've *installed build-essential*, and, after updates, had to reinstall it again.

---

### Post by Lux Perpetua on 2007-01-22
> ```
[FONT="Courier New"]#include "stdio.h"

int main()
{
  printf("hello world\n");
}[/FONT]
```This should really be```
[FONT="Courier New"]#include [highlight]<stdio.h>[/highlight]

int main()
{
  printf("hello world\n");
  [highlight]return 0;[/highlight]
}[/FONT]
```That should fix your last error. (The return statement is there because main is declared to return an int, so technically it should return something. It would probably still compile without the return statement, though.)

---

### Post by montgoss on 2007-01-22
It was that build-essentials.  Thanks!  =D>

---

### Post by lenooh on 2007-04-23
I get the same error when trying to install pspvc ([pspvc.sourceforge.net]("http://pspvc.sourceforge.net")):
```
...
ffmpeg/libswscale/yuv2rgb_altivec.c
ffmpeg/libswscale/rgb2rgb_template.c
ffmpeg/libswscale/swscale_template.c
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --cross-compile option.
Only do this if you know what cross compiling means.
C compiler test failed.
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
ffmpeg-devel@mplayerhq.hu mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.
-e \E[01;31mERROR during configure FFMPEG
```

i have build-essential installed, but it doesn't help...

any ideas?

I'm using kubuntu 6.10.

---

### Post by lenooh on 2007-05-20
ok, i solved it. had to install libx11-dev:

```
sudo apt-get install libx11-dev
```

---

### Post by sushant.d84 on 2011-03-23
> **lenooh said:**
> ok, i solved it. had to install libx11-dev:

```
sudo apt-get install libx11-dev
```


Hey ! 
I too tried this thing I installed that ..But I dont know what to do after that .. 

I am new for linux and ubuntu too :)

here is the text from ternminal 


============================================
root@user-desktop:/opt/lampp/htdocs/ffmpeg-0.6.0-old# ./configure  --enable-libfaad --enable-gpl --enable-libfaac --enable-nonfree --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-libmp3lame  --enable-cross-compile
Must specify target arch and OS when cross-compiling

If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-user@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

==================================




Please help me
:(

---

### Post by JupiterV2 on 2011-03-23
Well...that would be because you used the flag --enable-cross-compile without specifying a --target architecture you're trying to build for. 

Are you sure you're trying to cross-compile?

---

### Post by sushant.d84 on 2011-03-23
):P

Thanks for reply ! 


I am using cross-compile because of this ... 

============================================================
root@user-desktop:/opt/lampp/htdocs/ffmpeg-0.6.0-old# ./configure  --enable-libfaad --enable-gpl --enable-libfaac --enable-nonfree --enable-libopencore-amrnb --enable-version3 --enable-libopencore-amrwb --enable-libmp3lame  
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --enable-cross-compile option.
Only do this if you know what cross compiling means.
C compiler test failed.

If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-user@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.
===============================================================


And If I am using the --cross-compile I don't know how to use  --target for Ubuntu 10.04 LTS                - the Lucid Lynx - 




Yesterday I tried to solve the problem of
"""""""
/usr/local/bin/ffmpeg: /opt/lampp/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

"""""

I solved that problem by moving renaming some related files in lib..


Can you please guide me

---

### Post by s.fox on 2011-03-23
Thread necromancy.  Please start a new thread.

Thread closed.

---

