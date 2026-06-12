---
title: "make using old header"
date: 2008-12-16
forum: Packaging and Compiling Programs
---

### Post by xzero1 on 2008-12-16
I need to load a LKM. After compiling and installing, modprobe yields 'module not found'. During the make I notice the make uses 2.6.27-7 header instead of my current 2.6.27-9 header which explains the modprobe error. Shouldn't the compiler use the current header? What am I missing?

```
 make
make -C /home/kdog/hdpvr/v4l 
make[1]: Entering directory `/home/kdog/hdpvr/v4l'
creating symbolic links...
Kernel build directory is /lib/modules/2.6.27-7-generic/build
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/kdog/hdpvr/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  Building modules, stage 2.
  MODPOST 279 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
./scripts/rmmod.pl check
found 279 modules
make[1]: Leaving directory `/home/kdog/hdpvr/v4l'
]
```Makefile:
```
BUILD_DIR := $(shell pwd)/v4l
TMP ?= /tmp
REPO_PULL := http://linuxtv.org/hg/v4l-dvb

ifeq ($(EDITOR),)
  ifeq ($(VISUAL),)
    EDITOR := vi
  else
    EDITOR := $(VISUAL) -w
  endif
endif

all:

install:
    $(MAKE) -C $(BUILD_DIR) install

%::
    $(MAKE) -C $(BUILD_DIR) $(MAKECMDGOALS)

commit cvscommit hgcommit change changes changelog:: whitespace
    @cd $(BUILD_DIR); scripts/cardlist; scripts/do_commit.sh $(EDITOR) $(TMP)/v4l_hg_whitespace; cd ..

qrefresh: Q=q
qrefresh:: whitespace
    cd $(BUILD_DIR); scripts/cardlist; cd ..
    v4l/scripts/prep_commit_msg.pl -q $(TMP)/v4l_hg_whitespace > \
        $(TMP)/v4l_hg_commit.msg
    $(EDITOR) $(TMP)/v4l_hg_commit.msg
    grep -v '^#' $(TMP)/v4l_hg_commit.msg | hg qrefresh -g -l -

pull update v4l-update::
    @echo "Pulling changes from master repository $(REPO_PULL)"
    -hg pull -u $(REPO_PULL)

push::
    @echo "Pushing changes to master repository"
    -hg push

whitespace whitespaces:
    @echo "Cleaning bad whitespaces"
    @v4l/scripts/strip-trailing-whitespaces.sh $(Q)fast | \
        tee $(TMP)/v4l_hg_whitespace | patch -p0
```

---

### Post by geraldm on 2008-12-19
I have not done this for many months (years?) but the headers should be the ones for the kernel module objects that you are installing into.   This is NOT 
related to the modprobe error message.

look into the file /lib/modules/{your_version}/modules.dep
This should have a line showing the  full path location where you put the module, and then the location of dependent modules which must be loaded before the module.

Careful backup and editing may be needed if you are doing this manually.
The modules.dep file is what modprobe needs to locate the module.

Gerald

---

### Post by xzero1 on 2008-12-19
I appreciate your help. Maybe I didn't explain clearly enough. Modprobe uses /lib/modules/'uname -r' for its files. I can find all the required modules and dependencies in /lib/modules/2.6.27-7-generic but uname -r is 2.6.27-9-generic. It just seems the modules are made using the wrong header.  

module hdpvr.ko is not in /lib/modules/2.6.27-9-generic/modules.dep but is in /lib/modules/2.6.27-7-generic/modules.dep

from /lib/modules/2.6.27-7-generic/modules.dep:

/lib/modules/2.6.27-7-generic/kernel/drivers/media/video/hdpvr/hdpvr.ko: /lib/modules/2.6.27-7-generic/kernel/drivers/usb/core/usbcore.ko /lib/modules/2.6.27-7-generic/kernel/drivers/media/video/v4l2-compat-ioctl32.ko /lib/modules/2.6.27-7-generic/kernel/drivers/media/video/videodev.ko /lib/modules/2.6.27-7-generic/kernel/drivers/media/video/v4l1-compat.ko /lib/modules/2.6.27-7-generic/kernel/drivers/media/video/v4l2-common.ko /lib/modules/2.6.27-7-generic/kernel/drivers/i2c/i2c-core.ko

```
kdog@kdog-desktop:~/hdpvr$ uname -r
2.6.27-9-generic

kdog@kdog-desktop:~/hdpvr$ sudo make install
make -C /home/kdog/hdpvr/v4l install
make[1]: Entering directory `/home/kdog/hdpvr/v4l'
Stripping debug info from files
-e 
Removing obsolete files from /lib/modules/2.6.27-7-generic/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/2.6.27-7-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.27-7-generic/kernel/drivers/media/:
    video/gspca/m5602/: gspca_m5602.ko 
    dvb/dvb-usb/: dvb-usb-dtv5100.ko dvb-usb-opera.ko dvb-usb-cxusb.ko 
        dvb-usb-vp7045.ko dvb-usb-af9005-remote.ko dvb-usb-ttusb2.ko 
        dvb-usb-af9015.ko dvb-usb-dib0700.ko dvb-usb-a800.ko 
        dvb-usb-gp8psk.ko dvb-usb-dibusb-common.ko dvb-usb-au6610.ko 
        dvb-usb-digitv.ko dvb-usb.ko dvb-usb-dibusb-mc.ko 
        dvb-usb-af9005.ko dvb-usb-nova-t-usb2.ko dvb-usb-dtt200u.ko 
        dvb-usb-cinergyT2.ko dvb-usb-vp702x.ko dvb-usb-umt-010.ko 
        dvb-usb-anysee.ko dvb-usb-dibusb-mb.ko dvb-usb-dw2102.ko 
        dvb-usb-gl861.ko dvb-usb-m920x.ko 
    video/zoran/: videocodec.ko zr36050.ko zr36016.ko 
        zr36060.ko zr36067.ko 
    video/cx18/: cx18.ko 
    video/cpia2/: cpia2.ko 
    dvb/b2c2/: b2c2-flexcop-pci.ko b2c2-flexcop.ko b2c2-flexcop-usb.ko 
    video/ivtv/: ivtvfb.ko ivtv.ko 
    video/hdpvr/: hdpvr.ko 
    common/tuners/: tuner-xc2028.ko mt2060.ko tda9887.ko 
        mt2131.ko qt1010.ko mt20xx.ko 
        tda827x.ko tda18271.ko xc5000.ko 
        mxl5007t.ko tea5761.ko tuner-types.ko 
        tda8290.ko tuner-simple.ko mt2266.ko 
        tea5767.ko mxl5005s.ko 
    video/sn9c102/: sn9c102.ko 
    dvb/dvb-core/: dvb-core.ko 
    video/: videobuf-dma-contig.ko vpx3220.ko videobuf-dma-sg.ko 
        bt856.ko upd64083.ko v4l2-compat-ioctl32.ko 
        stradis.ko videobuf-core.ko tda9840.ko 
        saa7191.ko cx2341x.ko wm8775.ko 
        meye.ko w9968cf.ko saa7185.ko 
        tuner.ko zr364xx.ko ks0127.ko 
        stv680.ko videobuf-dvb.ko tvaudio.ko 
        bt866.ko tea6420.ko cafe_ccic.ko 
        saa5246a.ko msp3400.ko tcm825x.ko 
        soc_camera.ko wm8739.ko stkwebcam.ko 
        saa5249.ko cpia_pp.ko tda7432.ko 
        w9966.ko mt9m001.ko upd64031a.ko 
        ir-kbd-i2c.ko ov511.ko tea6415c.ko 
        dabusb.ko bt819.ko cpia_usb.ko 
        videodev.ko tda9875.ko adv7175.ko 
        mxb.ko vivi.ko soc_camera_platform.ko 
        cs53l32a.ko s2255drv.ko btcx-risc.ko 
        se401.ko saa7110.ko saa7115.ko 
        saa6588.ko saa7111.ko tvmixer.ko 
        v4l2-common.ko saa7114.ko hexium_orion.ko 
        hexium_gemini.ko tvp5150.ko mt9m111.ko 
        vp27smpx.ko adv7170.ko ov772x.ko 
        ov7670.ko saa7127.ko m52790.ko 
        mt9v022.ko v4l1-compat.ko videobuf-vmalloc.ko 
        v4l2-int-device.ko sh_mobile_ceu_camera.ko c-qcam.ko 
        tveeprom.ko cs5345.ko saa717x.ko 
        cpia.ko tlv320aic23b.ko bw-qcam.ko 
    video/cx23885/: cx23885.ko 
    dvb/bt8xx/: dst_ca.ko dvb-bt8xx.ko bt878.ko 
        dst.ko 
    dvb/siano/: sms1xxx.ko 
    video/cx25840/: cx25840.ko 
    dvb/ttusb-dec/: ttusbdecfe.ko ttusb_dec.ko 
    dvb/dm1105/: dm1105.ko 
    video/saa7134/: saa6752hs.ko saa7134-empress.ko saa7134-alsa.ko 
        saa7134-dvb.ko saa7134.ko 
    dvb/ttpci/: dvb-ttpci.ko budget-patch.ko ttpci-eeprom.ko 
        budget-av.ko budget.ko budget-core.ko 
        budget-ci.ko 
    video/et61x251/: et61x251.ko 
    dvb/frontends/: nxt6000.ko dib7000m.ko drx397xD.ko 
        s5h1411.ko si21xx.ko au8522.ko 
        s5h1420.ko stv0288.ko nxt200x.ko 
        mt352.ko s921.ko isl6405.ko 
        s5h1409.ko sp887x.ko dibx000_common.ko 
        isl6421.ko mt312.ko or51132.ko 
        tda1004x.ko dib3000mb.ko lgs8gl5.ko 
        dib3000mc.ko itd1000.ko sp8870.ko 
        l64781.ko dib7000p.ko ves1x93.ko 
        tda8083.ko stb6100.ko dib0070.ko 
        ves1820.ko stv0297.ko tda10086.ko 
        cx22700.ko zl10353.ko cx24110.ko 
        stv0299.ko dvb_dummy_fe.ko cx24123.ko 
        lgdt330x.ko dvb-pll.ko lnbp21.ko 
        cx22702.ko stb6000.ko lgdt3304.ko 
        cx24116.ko tda8261.ko tda10023.ko 
        tua6100.ko bcm3510.ko tda10021.ko 
        tda10048.ko stb0899.ko or51211.ko 
        tda826x.ko af9013.ko 
    video/cx88/: cx8802.ko cx8800.ko cx88-blackbird.ko 
        cx88-alsa.ko cx88xx.ko cx88-vp3054-i2c.ko 
        cx88-dvb.ko 
    video/bt8xx/: bttv.ko 
    video/gspca/: gspca_pac207.ko gspca_stk014.ko gspca_spca501.ko 
        gspca_spca500.ko gspca_mars.ko gspca_spca508.ko 
        gspca_t613.ko gspca_sunplus.ko gspca_vc032x.ko 
        gspca_spca561.ko gspca_tv8532.ko gspca_spca505.ko 
        gspca_spca506.ko gspca_sonixj.ko gspca_zc3xx.ko 
        gspca_main.ko gspca_conex.ko gspca_pac7311.ko 
        gspca_sonixb.ko gspca_ov519.ko gspca_finepix.ko 
        gspca_etoms.ko 
    dvb/pluto2/: pluto2.ko 
    video/usbvideo/: ibmcam.ko usbvideo.ko vicam.ko 
        ultracam.ko konicawc.ko quickcam_messenger.ko 
    video/usbvision/: usbvision.ko 
    common/: saa7146_vv.ko ir-common.ko saa7146.ko 
    video/em28xx/: em28xx-dvb.ko em28xx-alsa.ko em28xx.ko 
    video/pvrusb2/: pvrusb2.ko 
    radio/: dsbr100.ko radio-maestro.ko radio-maxiradio.ko 
        radio-si470x.ko radio-gemtek-pci.ko radio-mr800.ko 
    video/uvc/: uvcvideo.ko 
    dvb/ttusb-budget/: dvb-ttusb-budget.ko 
    video/pwc/: pwc.ko 
    video/zc0301/: zc0301.ko 
    video/ovcamchip/: ovcamchip.ko 
    video/au0828/: au0828.ko 
/sbin/depmod -a 2.6.27-7-generic 
make[1]: Leaving directory `/home/kdog/hdpvr/v4l'
kdog@kdog-desktop:~/hdpvr$
```Why aren't the modules installed into uname -r so that modprobe can find them?

---

### Post by DHunt on 2009-02-07
Did you ever figure this out?  I'm having the same issue but with a different library.  I find my hdpvr.ko in the moudles.dep of 2.6.27-9-generic lib.  I also have a 2.6.27-7-generic lib and 2.6.27-11-generic lib with both modules.dep not having the hdpvr.ko listed.

My "uname -r" shows 2.6.27-11-generic.

When I "modprobe hdpvr", I receive the "FATAL:  Module hdpvr not found." error, which appears to be the same thing your running into.

I'm quite new to Linux so I'm just digging through google searches until I figure it out and learn a few things in the process.  Your post here has been the closest thing I've found to figuring out my/your issue.

Thanks if your able to help!

---

### Post by xzero1 on 2009-07-27
This is a reply to an old post, but it had not been resolved. Hopefully, it will help.

Problem:
When the kernel headers are updated, some modules will no longer compile properly. The compiler uses the wrong header.

A kludge that seems to work:
The first line in Makefile ```
BUILD_DIR := $(shell pwd)/v4l
``` uses a .version file in the v4l directory. The Kernel version is in that file. Note: After the modprobe, even if there are errors, reboot.

This problem reoccurs every time the headers are updated. If someone knows a more proper way to address the problem, I invite your post.

As far as the HDPVR, the karmic kernel contains the module. No compilation will be necessary.:D

---

