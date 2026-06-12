---
title: "Leadtek DTV1800 H and H.264?"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by Skelas on 2008-08-12
According [http://ubuntuforums.org/showthread.php?t=648028]("http://ubuntuforums.org/showthread.php?t=648028"), it seems that DTV1800H can be compatible with Ubuntu.
However, I don't know if it will be possible to watch H.264 encoded video.
DTV1800 H should capture MPEG-4, but does it necessary mean that everything will be OK with H.264?
Is it matter of TV tuner or software used?
Any experience?

Or maybe any suggestion for another TV tuner compatible with Ubuntu 8.04 and H.264?

---

### Post by betchern0t on 2008-08-26
Hi,
    I have failed to get a DTV1800H with Hardy Heron using the instructions you quote. I believe that the instructions are specific to another kernel revision - Gutsy maybe. 

To get a list of supported cards goto the v4l repository and have a look in the header files. For example [http://linuxtv.org/hg/v4l-dvb/file/a4843e1304e6/linux/drivers/media/video/cx88/cx88.h](http://linuxtv.org/hg/v4l-dvb/file/a4843e1304e6/linux/drivers/media/video/cx88/cx88.h) gives:

#define CX88_BOARD_HAUPPAUGE                1
#define CX88_BOARD_GDI                      2
#define CX88_BOARD_PIXELVIEW                3
#define CX88_BOARD_ATI_WONDER_PRO           4
#define CX88_BOARD_WINFAST2000XP_EXPERT     5
#define CX88_BOARD_AVERTV_STUDIO_303        6
#define CX88_BOARD_MSI_TVANYWHERE_MASTER    7
#define CX88_BOARD_WINFAST_DV2000           8
#define CX88_BOARD_LEADTEK_PVR2000          9
#define CX88_BOARD_IODATA_GVVCP3PCI        10
#define CX88_BOARD_PROLINK_PLAYTVPVR       11
#define CX88_BOARD_ASUS_PVR_416            12
#define CX88_BOARD_MSI_TVANYWHERE          13
#define CX88_BOARD_KWORLD_DVB_T            14
#define CX88_BOARD_DVICO_FUSIONHDTV_DVB_T1 15
#define CX88_BOARD_KWORLD_LTV883           16
#define CX88_BOARD_DVICO_FUSIONHDTV_3_GOLD_Q  17
#define CX88_BOARD_HAUPPAUGE_DVB_T1        18
#define CX88_BOARD_CONEXANT_DVB_T1         19
#define CX88_BOARD_PROVIDEO_PV259          20
#define CX88_BOARD_DVICO_FUSIONHDTV_DVB_T_PLUS 21
#define CX88_BOARD_PCHDTV_HD3000           22
#define CX88_BOARD_DNTV_LIVE_DVB_T         23
#define CX88_BOARD_HAUPPAUGE_ROSLYN        24
#define CX88_BOARD_DIGITALLOGIC_MEC        25
#define CX88_BOARD_IODATA_GVBCTV7E         26
#define CX88_BOARD_PIXELVIEW_PLAYTV_ULTRA_PRO 27
#define CX88_BOARD_DVICO_FUSIONHDTV_3_GOLD_T  28
#define CX88_BOARD_ADSTECH_DVB_T_PCI          29
#define CX88_BOARD_TERRATEC_CINERGY_1400_DVB_T1  30
#define CX88_BOARD_DVICO_FUSIONHDTV_5_GOLD 31
#define CX88_BOARD_AVERMEDIA_ULTRATV_MC_550 32
#define CX88_BOARD_KWORLD_VSTREAM_EXPERT_DVD 33
#define CX88_BOARD_ATI_HDTVWONDER          34
#define CX88_BOARD_WINFAST_DTV1000         35
#define CX88_BOARD_AVERTV_303              36
#define CX88_BOARD_HAUPPAUGE_NOVASPLUS_S1  37
#define CX88_BOARD_HAUPPAUGE_NOVASE2_S1    38
#define CX88_BOARD_KWORLD_DVBS_100         39
#define CX88_BOARD_HAUPPAUGE_HVR1100       40
#define CX88_BOARD_HAUPPAUGE_HVR1100LP     41
#define CX88_BOARD_DNTV_LIVE_DVB_T_PRO     42
#define CX88_BOARD_KWORLD_DVB_T_CX22702    43
#define CX88_BOARD_DVICO_FUSIONHDTV_DVB_T_DUAL 44
#define CX88_BOARD_KWORLD_HARDWARE_MPEG_TV_XPERT 45
#define CX88_BOARD_DVICO_FUSIONHDTV_DVB_T_HYBRID 46
#define CX88_BOARD_PCHDTV_HD5500           47
#define CX88_BOARD_KWORLD_MCE200_DELUXE    48
#define CX88_BOARD_PIXELVIEW_PLAYTV_P7000  49
#define CX88_BOARD_NPGTECH_REALTV_TOP10FM  50
#define CX88_BOARD_WINFAST_DTV2000H        51
#define CX88_BOARD_GENIATECH_DVBS          52
#define CX88_BOARD_HAUPPAUGE_HVR3000       53
#define CX88_BOARD_NORWOOD_MICRO           54
#define CX88_BOARD_TE_DTV_250_OEM_SWANN    55
#define CX88_BOARD_HAUPPAUGE_HVR1300       56
#define CX88_BOARD_ADSTECH_PTV_390         57
#define CX88_BOARD_PINNACLE_PCTV_HD_800i   58
#define CX88_BOARD_DVICO_FUSIONHDTV_5_PCI_NANO 59
#define CX88_BOARD_PINNACLE_HYBRID_PCTV    60
#define CX88_BOARD_WINFAST_TV2000_XP_GLOBAL 61
#define CX88_BOARD_POWERCOLOR_REAL_ANGEL   62
#define CX88_BOARD_GENIATECH_X8000_MT      63
#define CX88_BOARD_DVICO_FUSIONHDTV_DVB_T_PRO 64
#define CX88_BOARD_DVICO_FUSIONHDTV_7_GOLD 65
#define CX88_BOARD_PROLINK_PV_8000GT       66
#define CX88_BOARD_KWORLD_ATSC_120         67

hth

Paul

---

### Post by STYX2009 on 2009-05-29
You can download the v4l-dvb driver which supports Leadtek DTV1800 H here:
[http://tw1965.myweb.hinet.net/](http://tw1965.myweb.hinet.net/)
[http://tw1965.myweb.hinet.net/Linux/v4l-dvb/20090609/v4l-dvb.tar.gz](http://tw1965.myweb.hinet.net/Linux/v4l-dvb/20090609/v4l-dvb.tar.gz)

 
And xc3028n firmware xc3028-v27.fw is here :
[http://steventoth.net/linux/hvr1500/xc3028-v27.fw](http://steventoth.net/linux/hvr1500/xc3028-v27.fw)

---

