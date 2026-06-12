---
title: "C++ Question"
date: 2013-02-28
forum: Programming Talk
---

### Post by Quantumstate on 2013-02-28
I run MythTV on my HTPC, and my recording device is an [R5000](http://www.nextcomwireless.com/R5000/home.htm).  For years I've had to patch MythTV and compile to work with the R5000, but as time's passed the patch developer is gone, the maker of the R5000 is gone, and I am left to try and keep this thing going with new versions of Myth.

I have adapted the patch to Myth0.27 and it compiles cleanly.  But when I start the Myth backend (server) I get this:
```
2013-02-27 16:06:31.572980 C [13987/13987] thread_unknown mythcommandlineparser.cpp:2572 (ConfigureLogging) - mythbackend version: master [v0.27-pre2-534-g47a2da4-dirty] www.mythtv.org
2013-02-27 16:06:31.573033 C [13987/13987] thread_unknown mythcommandlineparser.cpp:2574 (ConfigureLogging) - Qt version: compile: 4.8.2, runtime: 4.8.2
2013-02-27 16:06:31.573041 N [13987/13987] thread_unknown mythcommandlineparser.cpp:2576 (ConfigureLogging) - Enabled verbose msgs:  general
2013-02-27 16:06:31.573217 N [13987/13987] thread_unknown logging.cpp:852 (logStart) - Setting Log Level to LOG_INFO
2013-02-27 16:06:31.574229 I [13987/13987] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Interrupt handler
2013-02-27 16:06:31.574240 I [13987/13987] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Terminated handler
2013-02-27 16:06:31.574251 I [13987/13987] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Segmentation fault handler
2013-02-27 16:06:31.574260 I [13987/13987] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Aborted handler
2013-02-27 16:06:31.574268 I [13987/13987] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Bus error handler
2013-02-27 16:06:31.574278 I [13987/13987] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Floating point exception handler
2013-02-27 16:06:31.574286 I [13987/13987] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Illegal instruction handler
2013-02-27 16:06:31.574297 I [13987/13987] thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) - Setup Real-time signal 0 handler
2013-02-27 16:06:31.574368 N [13987/13987] thread_unknown mythdirs.cpp:55 (InitializeMythDirs) - Using runtime prefix = /usr/local
2013-02-27 16:06:31.574384 N [13987/13987] thread_unknown mythdirs.cpp:68 (InitializeMythDirs) - Using configuration directory = /home/mythtv/.mythtv
2013-02-27 16:06:31.574525 I [13987/13987] CoreContext mythcorecontext.cpp:238 (Init) - Assumed character encoding: en_US.UTF-8
2013-02-27 16:06:31.574729 I [13987/13988] Logger logging.cpp:307 (run) - Added logging to the console
2013-02-27 16:06:31.575224 N [13987/13987] CoreContext mythcontext.cpp:486 (LoadDatabaseSettings) - Empty LocalHostName.
2013-02-27 16:06:31.575239 I [13987/13987] CoreContext mythcontext.cpp:494 (LoadDatabaseSettings) - Using localhost value of cygnus
2013-02-27 16:06:31.588405 N [13987/13987] CoreContext mythcorecontext.cpp:1291 (InitLocale) - Setting QT default locale to EN_US
2013-02-27 16:06:31.588517 I [13987/13987] CoreContext mythcorecontext.cpp:1324 (SaveLocaleDefaults) - Current locale EN_US
2013-02-27 16:06:31.588570 N [13987/13987] CoreContext mythlocale.cpp:121 (LoadDefaultsFromXML) - Reading locale defaults from /usr/local/share/mythtv//locales/en_us.xml
2013-02-27 16:06:31.592622 I [13987/13987] CoreContext schemawizard.cpp:118 (Compare) - Current MythTV Schema Version (DBSchemaVer): 1310
2013-02-27 16:06:31.592930 I [13987/13987] CoreContext mythtranslation.cpp:65 (load) - Loading en_us translation for module mythfrontend
2013-02-27 16:06:31.593241 N [13987/13987] CoreContext main_helpers.cpp:572 (run_backend) - MythBackend: Starting up as the master server.
2013-02-27 16:06:31.799122 I [13987/13988] Logger logging.cpp:488 (launchLogServer) - Starting mythlogserver
2013-02-27 16:06:31.799292 I [13987/13995] SystemManager system-unix.cpp:263 (run) - Starting process manager
2013-02-27 16:06:31.799550 I [13987/13999] SystemSignalManager system-unix.cpp:490 (run) - Starting process signal handler
2013-02-27 16:06:31.799587 I [13987/14001] SystemIOHandlerW system-unix.cpp:90 (run) - Starting IO manager (write)
2013-02-27 16:06:31.801659 I [13987/14000] SystemIOHandlerR system-unix.cpp:90 (run) - Starting IO manager (read)
2013-02-27 16:06:31.909140 I [13987/13987] CoreContext r5000device.cpp:46 (r5000_msg) - R5kDev: R5kLib: R5000 initialization failed at stage 1:
	Expected 1 bytes, but got -16 bytes

2013-02-27 16:06:31.909379 I [13987/13987] CoreContext r5000device.cpp:46 (r5000_msg) - R5kDev: R5kLib: R5000 failed to locate any R5000 devices.  Are you sure you have permissions set properly?

2013-02-27 16:06:31.953152 I [13987/13987] CoreContext r5000device.cpp:46 (r5000_msg) - R5kDev: R5kLib: R5000 was not initialized before r5000_open().  Please call r5000_init() first

2013-02-27 16:06:31.953164 E [13987/13987] CoreContext recorders/channelbase.cpp:1235 (CreateChannel) - ChannelBase: CreateChannel() Error: Failed to open device 100563E
2013-02-27 16:06:31.954221 E [13987/13987] CoreContext main_helpers.cpp:198 (setupTVs) - Problem with capture cardsCard 5failed init
2013-02-27 16:06:31.999891 I [13987/13988] Logger logging.cpp:448 (initialTimeout) - Added logging to mythlogserver at TCP:35327
2013-02-27 16:06:32.025931 I [13987/13987] CoreContext programinfo.cpp:2114 (CheckProgramIDAuthorities) - Found 1 distinct programid authorities
2013-02-27 16:06:32.027977 I [13987/14025] Scheduler mythdbcon.cpp:436 (getStaticCon) - New static DB connectionSchedCon
2013-02-27 16:06:32.028785 I [13987/13987] CoreContext serverpool.cpp:395 (listen) - Listening on TCP 127.0.0.1:6544
2013-02-27 16:06:32.029821 N [13987/13987] CoreContext mediaserver.cpp:169 (Init) - MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2013-02-27 16:06:32.029826 I [13987/13987] CoreContext main_helpers.cpp:642 (run_backend) - Main::Registering HttpStatus Extension
2013-02-27 16:06:32.030670 W [13987/13987] CoreContext mainserver.cpp:262 (MainServer) - Unable to find IPv6 address to bind
2013-02-27 16:06:32.030716 I [13987/13987] CoreContext serverpool.cpp:395 (listen) - Listening on TCP 127.0.0.1:6543
2013-02-27 16:06:32.032032 N [13987/13987] CoreContext autoexpire.cpp:264 (CalcParams) - AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2013-02-27 16:06:35.033545 I [13987/14025] Scheduler scheduler.cpp:2088 (HandleReschedule) - Reschedule requested for MATCH 0 0 0 - SchedulerInit
```

I am not a coding genius, but it looks like the r5000 is not being init-ed before opened.  I just don't know what to do about it. It's definitely not a permissions problem.

 The error calles out the r5000device.cpp file, which is [here](https://paste.debian.net/238741/).

Can anyone see what might be wrong here?

---

### Post by Quantumstate on 2013-03-01
Can anyone advise?  I would be grateful for help, as I have no TV now.

Other r5000 files in that dir (libs/libmythtv) are:
```
-rw-r--r--  1 root staff 22120 Feb 18 17:28 r5000.c
-rw-r--r--  1 root staff  1856 Feb 18 17:28 r5000.h
-rw-r--r--  1 root staff  3840 Feb 18 17:28 r5000init.h
-rw-r--r--  1 root staff  3779 Feb 18 17:28 r5000_internal.h
-rw-r--r--  1 root staff  7031 Feb 18 17:28 r5k_directv_buttons.c
-rw-r--r--  1 root staff 12126 Feb 18 17:28 r5k_dish6000_buttons.c
-rw-r--r--  1 root staff  3825 Feb 18 17:28 r5k_dsr_buttons.c
-rw-r--r--  1 root staff  7560 Feb 18 17:28 r5k_misc.c
-rw-r--r--  1 root staff 10389 Feb 18 17:28 r5k_pes.c
-rw-r--r--  1 root staff 14340 Feb 18 17:28 r5k_sat.c
-rw-r--r--  1 root staff 14989 Feb 18 17:28 r5k_vip_buttons.c
-rw-r--r--  1 root staff  7509 Feb 18 17:28 r5k_vip.c
```

In libs/libmythtv/r5000:
```
-rw-r--r-- 1 root staff 10605 Feb 18 17:28 r5000/libusb_augment.c
-rw-r--r-- 1 root staff  1663 Feb 18 17:28 r5000/libusb_augment.h
-rw-r--r-- 1 root staff 22120 Feb 18 17:28 r5000/r5000.c
-rw-r--r-- 1 root staff  1856 Feb 18 17:28 r5000/r5000.h
-rw-r--r-- 1 root staff  3840 Feb 18 17:28 r5000/r5000init.h
-rw-r--r-- 1 root staff  3779 Feb 18 17:28 r5000/r5000_internal.h
-rw-r--r-- 1 root staff  7031 Feb 18 17:28 r5000/r5k_directv_buttons.c
-rw-r--r-- 1 root staff 12126 Feb 18 17:28 r5000/r5k_dish6000_buttons.c
-rw-r--r-- 1 root staff  3825 Feb 18 17:28 r5000/r5k_dsr_buttons.c
-rw-r--r-- 1 root staff  7560 Feb 18 17:28 r5000/r5k_misc.c
-rw-r--r-- 1 root staff 10389 Feb 18 17:28 r5000/r5k_pes.c
-rw-r--r-- 1 root staff 14340 Feb 18 17:28 r5000/r5k_sat.c
-rw-r--r-- 1 root staff 14989 Feb 18 17:28 r5000/r5k_vip_buttons.c
-rw-r--r-- 1 root staff  7509 Feb 18 17:28 r5000/r5k_vip.c
```


My patch for the configure file is:
```
diff -crBN ../../mythtv/mythtv/configure ./configure
*** ../../mythtv/mythtv/configure	2013-02-16 10:36:54.416158056 -0800
--- ./configure	2013-02-16 10:52:50.018567158 -0800
***************
*** 119,124 ****
--- 119,125 ----
    --disable-ivtv           disable ivtv support (PVR-x50) req. v4l2 support
    --disable-hdpvr          disable HD-PVR support
    --disable-dvb            disable DVB support
+   --disable-r5000          disable support for R5000 USB STBs
    --dvb-path=HDRLOC        location of directory containing
                             'linux/dvb/frontend.h', not the
                             directory with frontend.h [$dvb_path_default]
***************
*** 1676,1681 ****
--- 1677,1683 ----
      ceton
      hdpvr
      ivtv
+     r5000
      asi
      joystick_menu
      libcec
***************
*** 2284,2289 ****
--- 2286,2292 ----
  audio_oss_deps_any="soundcard_h sys_soundcard_h"
  dvb_deps="backend"
  firewire_deps="backend"
+ r5000_deps="backend"
  ivtv_deps="backend v4l2"
  hdpvr_deps="backend v4l2"
  hdhomerun_deps="backend"
***************
*** 2501,2506 ****
--- 2504,2510 ----
  enable ceton
  enable hdpvr
  enable ivtv
+ enable r5000
  enable asi
  enable lamemp3
  enable libass
***************
*** 5702,5707 ****
--- 5706,5712 ----
    echo "DVB-S2 support            ${fe_can_2g_modulation-no}"
    echo "HDHomeRun support         ${hdhomerun-no}"
    echo "Ceton support             ${ceton-no}"
+   echo "R5000 support             ${r5000-no}"
    echo "ASI support               ${asi-no}"
  fi
```

My patch for the files in libs/libmythtv/recorders:
```
diff -crBN ../../mythtv/mythtv/libs/libmythtv/recorders/channelbase.cpp ./libs/libmythtv/recorders/channelbase.cpp
*** ../../mythtv/mythtv/libs/libmythtv/recorders/channelbase.cpp	2013-02-16 10:36:55.184163115 -0800
--- ./libs/libmythtv/recorders/channelbase.cpp	2013-02-16 10:52:50.014567132 -0800
***************
*** 26,31 ****
--- 26,32 ----
  #include "firewirechannel.h"
  #include "mythcorecontext.h"
  #include "cetonchannel.h"
+ #include "r5000channel.h"
  #include "dummychannel.h"
  #include "tvremoteutil.h"
  #include "channelbase.h"
***************
*** 1195,1200 ****
--- 1196,1210 ----
          channel = new CetonChannel(tvrec, genOpt.videodev);
  #endif
      }
+     else if (genOpt.cardtype == "R5000")
+     {
+ #ifdef USING_R5000
+         channel = new R5000Channel(tvrec, genOpt.videodev, fwOpt.model, dvbOpt.dvb_on_demand);
+         dynamic_cast<R5000Channel*>(channel)->SetSlowTuning(
+             dvbOpt.dvb_tuning_delay);
+ #endif
+     }
+ 
      else if (CardUtil::IsV4L(genOpt.cardtype))
      {
  #ifdef USING_V4L2
diff -crBN ../../mythtv/mythtv/libs/libmythtv/recorders/recorderbase.cpp ./libs/libmythtv/recorders/recorderbase.cpp
*** ../../mythtv/mythtv/libs/libmythtv/recorders/recorderbase.cpp	2013-02-16 10:36:55.188163142 -0800
--- ./libs/libmythtv/recorders/recorderbase.cpp	2013-02-16 10:52:50.018567158 -0800
***************
*** 9,20 ****
--- 9,22 ----
  #include "firewirechannel.h"
  #include "importrecorder.h"
  #include "cetonrecorder.h"
+ #include "r5000recorder.h"
  #include "dummychannel.h"
  #include "hdhrrecorder.h"
  #include "iptvrecorder.h"
  #include "mpegrecorder.h"
  #include "recorderbase.h"
  #include "cetonchannel.h"
+ #include "r5000channel.h"
  #include "asirecorder.h"
  #include "dvbrecorder.h"
  #include "hdhrchannel.h"
***************
*** 649,654 ****
--- 651,663 ----
          recorder = new ImportRecorder(tvrec);
  #endif
      }
+     else if (genOpt.cardtype == "R5000")
+     {
+ #ifdef USING_R5000
+         recorder = new R5000Recorder(
+             tvrec, dynamic_cast<R5000Channel*>(channel));
+ #endif // USING_R5000
+     }
      else if (CardUtil::IsV4L(genOpt.cardtype))
      {
  #ifdef USING_V4L2
diff -crBN ../../mythtv/mythtv/libs/libmythtv/recorders/signalmonitor.cpp ./libs/libmythtv/recorders/signalmonitor.cpp
*** ../../mythtv/mythtv/libs/libmythtv/recorders/signalmonitor.cpp	2013-02-16 10:36:55.188163142 -0800
--- ./libs/libmythtv/recorders/signalmonitor.cpp	2013-02-16 10:52:50.018567158 -0800
***************
*** 54,59 ****
--- 54,64 ----
  #   include "cetonchannel.h"
  #endif
  
+ #ifdef USING_R5000
+ #   include "r5000signalmonitor.h"
+ #   include "r5000channel.h"
+ #endif
+ 
  #undef DBG_SM
  #define DBG_SM(FUNC, MSG) LOG(VB_CHANNEL, LOG_DEBUG, \
      QString("SM[%1](%2)::%3: %4").arg(capturecardnum) \

```


I find r5000_open() in libs/libmythtv/r5000/r5000.c, but it only has the error message:
"R5000 was not initialized before r5000_open().  Please call r5000_init() first\n"

I find r5000_open( in three places:
libs/libmythtv/r5000device.cpp starting line 289
```
bool R5000Device::OpenPort(void)
{
    LOG(VB_RECORD, LOG_DEBUG, LOC + "Starting Port Handler Thread");
    QMutexLocker mlocker(&m_lock);
    LOG(VB_RECORD, LOG_DEBUG, LOC + "Starting Port Handler Thread -- locked");
    if (usbdev)
    {
        m_open_port_cnt++;
        return true;
    }

    if (m_serial.length())
    {
      LOG(VB_RECORD, LOG_DEBUG, LOC + QString("Opening R5000 device type %1 with serial#: "+ m_serial).arg(m_type));
      usbdev = r5000_open((r5ktype_t)m_type, r5000_device_tspacket_handler, this, m_serial.toAscii().constData());
    }
    else
    {
      LOG(VB_RECORD, LOG_DEBUG, LOC + "Opening R5000 device with unknown serial#");
      usbdev = r5000_open((r5ktype_t)m_type, r5000_device_tspacket_handler, this, NULL);
    }
    if (! usbdev)
    {
        LOG(VB_GENERAL, LOG_DEBUG, LOC + "Failed to open R5000 device");
        return false;
    }

    LOG(VB_RECORD, LOG_DEBUG, LOC + "Starting port handler thread");
    m_priv->run_port_handler = true;
    pthread_create(&m_priv->port_handler_thread, NULL,
                   r5000_device_port_handler_thunk, this);

    LOG(VB_RECORD, LOG_DEBUG, LOC + "Waiting for port handler thread to start");
    while (!m_priv->is_port_handler_running)
    {
        m_lock.unlock();
        usleep(5000);
        m_lock.lock();
    }

    LOG(VB_RECORD, LOG_DEBUG, LOC + "Port handler thread started");

    m_open_port_cnt++;

    return true;
}
```

In libs/libmythtv/r5000/r5000.c starting line 341:
```
r5kdev_t *r5000_open(r5ktype_t type,
                     unsigned int (*cb)(unsigned char *buffer, int len, void *callback_data),
                     void *cb_data,
                     const char *serial)
{
  r5kdev_t *r5kdev, r5kd;
  int count = 0;

  r5000_log(0, "r5000_open(%d, NULL, %p, %s)", type, cb_data, serial);
  memset(&r5kd, 0, sizeof(r5kdev_t));
```

And in libs/libmythtv/r5000/r5000.h starting line 40:
```
extern int r5000_init(void (*_msgcb)(char *str));
extern r5kdev_t *r5000_open(r5ktype_t type, unsigned int (*cb)(unsigned char *buffer, int len, void *callback_data), void *cb_data, const char *serial);
extern int r5000_close(r5kdev_t *r5kdev);
```

I find r5000_init( in the same three files, starting with libs/libmyth/r5000device.cpp on line 81 then 408:
```
R5000Device::R5000Device(int type, QString serial) :
    m_type(type),
    m_serial(serial),
    m_last_channel(""),      m_last_crc(0),
    m_buffer_cleared(true), m_open_port_cnt(0),
    m_lock(),          m_priv(new R5kPriv())
{
    QMutexLocker locker(&s_static_lock);
    usbdev = NULL;
    if (! r5k_init)
      r5k_init = r5000_init(r5000_msg);
}

...

QStringList R5000Device::GetSTBList(void)
{
    QStringList STBList;
    int i;
    r5kenum_t r5k_stbs;
    if (! r5k_init)
    {
        r5k_init = r5000_init(r5000_msg);
        if (! r5k_init)
            return STBList;
    }
    if (! r5000_find_stbs(&r5k_stbs))
        LOG(VB_GENERAL, LOG_DEBUG, LOC + "Locating R5000 devices failed."
                                    "  This may be a permission problem");

    for (i = 0; i < r5k_stbs.count; i++)
        STBList.append((char *)r5k_stbs.serial[i]);
    return STBList;
}

```


Then libs/libmythth/r5000/r5000.c on line 301:
```
/* r5000_init must be called from a thread-safe context */
int r5000_init(void (*_msgcb)(char *str))
{
  int bus_count, dev_count;
  r5kdev_t r5kd;
  int count = 0;

  r5000_log(0, "r5000_init()");

  msgcb = _msgcb;

  if(r5000_usb_init)
    return 1;
  usb_init();
  bus_count = usb_find_busses();
  dev_count = usb_find_devices();
  if(bus_count == 0 || dev_count ==0) {
    r5000_print("R5000 failed to locate any USB devices.  Are you sure you have permissions set properly?\n");
    return 0;
  }
```


And then libs/mibmythtv/r5000/r5000.h line 40:
```
extern int r5000_init(void (*_msgcb)(char *str));
extern r5kdev_t *r5000_open(r5ktype_t type, unsigned int (*cb)(unsigned char *buffer, int len, void *callback_data), void *cb_data, const char *serial);
extern int r5000_close(r5kdev_t *r5kdev);
extern int r5000_start_stream(r5kdev_t *r5kdev);
```


The complete r5000.c is here: [https://paste.debian.net/239152/](https://paste.debian.net/239152/)
Alan Nisota quit the project a couple years ago.

---

### Post by steeldriver on 2013-03-01
I can't really offer any concrete help - but I noticed on one of the google results a mention of running [FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]r5ktest first, possibly as root to make sure t[SIZE=2]here is no permission issue?[/SIZE][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by Quantumstate on 2013-03-01
Yes thanks, but r5ktest runs fine.  I've carefully combed through permissions of the USB device. I can power the box on and off, and change channels just fine with r5ktest.  It definitely has to do with init in MythTV. 

There will be nothing out there on this, as I am the only one working on it.

---

