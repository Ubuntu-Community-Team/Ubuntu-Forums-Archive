---
title: "Mythtv cant watch tv or record after reboot"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by gdbutcher on 2012-03-23
Hi I used the excellent guide here to install Mythtv 0.24 on Xubuntu 64 bit 11.10 from repos: [http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php") 

Its a frontend/backend setup on the machine and I'm streaming the recordings to a PS3.

Everything worked perfectly imediatley following the installation, I could record and watch tv on both tuners: A volar x usb tuner and a Kworld DVB-t PC160 without problems.

After a reboot I can no longer watch live tv or record.

Live TV states that "you should have received a channel lock by now"
Recordings also fail.

I can still watch previously recorded programs through Myth-Frontend and the PS3. I just cant watch or record anything new. 

Anyone got any ideas please? I can't see anything in the logs:

Mythfrontend Log:

> Starting mythfrontend.real..
2012-03-23 14:25:47.549 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] [www.mythtv.org](www.mythtv.org)
2012-03-23 14:25:47.549 Using runtime prefix = /usr
2012-03-23 14:25:47.549 Using configuration directory = /home/gareth/.mythtv
2012-03-23 14:25:47.562 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2012-03-23 14:25:48.415 Empty LocalHostName.
2012-03-23 14:25:48.416 Using localhost value of gareth-xdesktop64
2012-03-23 14:25:48.426 New DB connection, total: 1
2012-03-23 14:25:48.433 Connected to database 'mythconverg' at host: localhost
2012-03-23 14:25:48.438 Closing DB connection named 'DBManager0'
2012-03-23 14:25:48.439 Connected to database 'mythconverg' at host: localhost
2012-03-23 14:25:48.441 Current locale EN_GB
2012-03-23 14:25:48.441 Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2012-03-23 14:25:48.676 ScreenSaverX11Private: XScreenSaver support enabled
2012-03-23 14:25:48.678 DPMS is active.
2012-03-23 14:25:48.724 Desktop video mode: 1440x900 59.887 Hz
2012-03-23 14:25:48.928 Enabled verbose msgs:  important general
2012-03-23 14:25:48.959 Loading en_us translation for module mythfrontend
2012-03-23 14:25:49.053 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
			eno: No such file or directory (2)
2012-03-23 14:25:49.053 JoystickMenuThread: Joystick disabled - Failed to read /home/gareth/.mythtv/joystickmenurc
2012-03-23 14:25:49.122 Using Frameless Window
2012-03-23 14:25:49.122 Using Full Screen Window
2012-03-23 14:25:49.412 Using the Qt painter
2012-03-23 14:25:50.147 New DB connection, total: 2
2012-03-23 14:25:50.148 New DB connection, total: 3
2012-03-23 14:25:50.148 Connected to database 'mythconverg' at host: localhost
2012-03-23 14:25:50.149 Current MythTV Schema Version (DBSchemaVer): 1264
2012-03-23 14:25:50.151 Connected to database 'mythconverg' at host: localhost
2012-03-23 14:25:51.111 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2012-03-23 14:25:51.111 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2012-03-23 14:25:51.211 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2012-03-23 14:25:51.211 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2012-03-23 14:25:51.663 Registering Internal as a media playback plugin.
2012-03-23 14:25:51.740 Loading en_us translation for module mytharchive
2012-03-23 14:25:51.760 Registering WebBrowser as a media playback plugin.
2012-03-23 14:25:51.775 Loading en_us translation for module mythbrowser
2012-03-23 14:25:51.838 MediaMonitorUnix::AddDevice() - empty device path.
2012-03-23 14:25:51.839 MediaMonitorUnix::AddDevice() - empty device path.
2012-03-23 14:25:51.839 MediaMonitorUnix::AddDevice() - empty device path.
2012-03-23 14:25:51.842 MediaMonitorUnix::AddDevice() - empty device path.
2012-03-23 14:25:51.842 MediaMonitorUnix::AddDevice() - empty device path.
2012-03-23 14:25:51.843 MediaMonitorUnix::AddDevice() - empty device path.
2012-03-23 14:25:51.843 MonitorRegisterExtensions(0x100, gif,jpg,png)
2012-03-23 14:25:51.859 Loading en_us translation for module mythgallery
2012-03-23 14:25:51.919 Loading en_us translation for module mythgame
2012-03-23 14:25:52.187 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2012-03-23 14:25:52.250 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2012-03-23 14:25:52.275 Loading en_us translation for module mythmusic
2012-03-23 14:25:52.309 Loading en_us translation for module mythnetvision
2012-03-23 14:25:52.344 Loading en_us translation for module mythnews
2012-03-23 14:25:52.390 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2012-03-23 14:25:52.427 Loading en_us translation for module mythvideo
2012-03-23 14:25:52.466 Loading en_us translation for module mythweather
2012-03-23 14:25:53.152 Found mainmenu.xml for theme 'MythCenter-wide'
2012-03-23 14:25:53.229 MythCoreContext: Connecting to backend server: 192.168.11.2:6543 (try 1 of 1)
2012-03-23 14:25:53.230 Using protocol version 63
2012-03-23 14:25:58.170 TV: Attempting to change from None to WatchingLiveTV
2012-03-23 14:25:58.170 MythCoreContext: Connecting to backend server: 192.168.11.2:6543 (try 1 of 1)
2012-03-23 14:25:58.171 Using protocol version 63
2012-03-23 14:25:58.264 Spawning LiveTV Recorder -- begin
2012-03-23 14:25:58.662 Spawning LiveTV Recorder -- end
2012-03-23 14:25:58.673 We have a playbackURL(/var/lib/mythtv/livetv/1001_20120323142558.mpg) & cardtype(DUMMY)
2012-03-23 14:25:58.673 We have a RingBuffer
2012-03-23 14:25:58.902 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2012-03-23 14:25:58.977 OSD: Base theme size: 1280x720
2012-03-23 14:25:58.977 OSD: Scaling factors: 0.5625x0.8
2012-03-23 14:25:59.067 OSD: Base theme size: 1280x720
2012-03-23 14:25:59.067 OSD: Scaling factors: 0.5625x0.8
2012-03-23 14:25:59.105 Player(0): Video timing method: DRM
2012-03-23 14:25:59.120 TV: Changing from None to WatchingLiveTV
2012-03-23 14:25:59.120 TV: State is LiveTV & mctx == ctx
2012-03-23 14:25:59.123 TV: UpdateOSDInput done
2012-03-23 14:25:59.123 TV: UpdateLCD done
2012-03-23 14:25:59.123 TV: ITVRestart done
2012-03-23 14:25:59.193 ScreenSaverX11Private: DPMS Deactivated 1
2012-03-23 14:25:59.258 VideoOutput: Created YV12 OSD.
2012-03-23 14:26:09.145 OSD: Base theme size: 1280x720
2012-03-23 14:26:09.145 OSD: Scaling factors: 0.5625x0.8
2012-03-23 14:26:12.998 TV: OSDDialogEvent: result -1 text  action DIALOG_INFO_CHANNELLOCK_0
2012-03-23 14:26:13.584 TV: Attempting to change from WatchingLiveTV to None
2012-03-23 14:26:13.741 TV: Changing from WatchingLiveTV to None
2012-03-23 14:26:13.742 ScreenSaverX11Private: DPMS Reactivated 1
2012-03-23 14:26:15.055 Deleting UPnP client...
Error in my_thread_global_end(): 2 threads didn't exit

Mythbackend Log:

> 2012-03-23 13:57:12.082 MythBackend: Starting up as the master server.
2012-03-23 13:57:12.156 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2012-03-23 13:57:12.268 New DB connection, total: 2
2012-03-23 13:57:12.327 Connected to database 'mythconverg' at host: localhost
2012-03-23 13:57:14.832 New DB connection, total: 3
2012-03-23 13:57:14.885 Connected to database 'mythconverg' at host: localhost
2012-03-23 13:57:19.232 New DB scheduler connection
2012-03-23 13:57:19.277 Connected to database 'mythconverg' at host: localhost
2012-03-23 13:57:19.337 Main::Registering HttpStatus Extension
2012-03-23 13:57:19.411 Enabled verbose msgs:  important general
2012-03-23 13:57:19.468 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2012-03-23 13:57:20.865 UPnpMedia: BuildMediaMap VIDEO scan starting in :/media/sdb1/Videos:
2012-03-23 13:57:21.589 UPnpMedia: BuildMediaMap Done. Found 173 objects
2012-03-23 13:57:22.397 Reschedule requested for id -1.
2012-03-23 13:57:22.634 Scheduled 1 items in 0.2 = 0.12 match + 0.12 place
2012-03-23 13:57:22.675 AUTO-Startup assumed
2012-03-23 13:57:22.804 TVRec(1): Changing from None to RecordingOnly
2012-03-23 13:57:22.866 TVRec(1): HW Tuner: 1->1
2012-03-23 13:57:23.331 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2012-03-23 13:57:23.375 Started recording: "ITV News & Weather":"The latest headlines from around the world": channel 1003 on cardid 1, sourceid 1
2012-03-23 13:57:23.573 TVRec(2): ASK_RECORDING 2 0 0 0
2012-03-23 13:57:23.578 TVRec(3): ASK_RECORDING 3 0 0 0
2012-03-23 13:57:23.582 TVRec(4): ASK_RECORDING 4 0 0 0
2012-03-23 13:57:23.587 TVRec(5): ASK_RECORDING 5 0 0 0
2012-03-23 13:58:39.342 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2012-03-23 14:00:00.350 TVRec(1): Changing from RecordingOnly to None
2012-03-23 14:00:00.569 Updating status for "ITV News & Weather":"The latest headlines from around the world" on cardid 1 (Tuning => Recorder Failed)
2012-03-23 14:00:00.646 Reschedule requested for id 0.
2012-03-23 14:00:00.832 Scheduled 0 items in 0.2 = 0.07 match + 0.12 place
2012-03-23 14:00:01.127 Preview Error: Encountered problems running '/usr/bin/mythpreviewgen --size 0x0 --chanid 1003 --starttime 20120323135700  > /dev/null'
2012-03-23 14:01:01.277 New DB connection, total: 4
2012-03-23 14:01:01.322 Connected to database 'mythconverg' at host: localhost
2012-03-23 14:01:01.366 New DB connection, total: 5
2012-03-23 14:01:01.406 Connected to database 'mythconverg' at host: localhost
2012-03-23 14:04:55.605 Reschedule requested for id -1.
2012-03-23 14:04:55.752 Scheduled 0 items in 0.1 = 0.04 match + 0.11 place
2012-03-23 14:08:50.861 Reschedule requested for id -1.
2012-03-23 14:08:51.013 Scheduled 0 items in 0.1 = 0.05 match + 0.10 place
2012-03-23 14:11:29.718 Reschedule requested for id -1.
2012-03-23 14:11:29.868 Scheduled 0 items in 0.1 = 0.05 match + 0.10 place
2012-03-23 14:12:39.440 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2012-03-23 14:16:41.029 Reschedule requested for id -1.
2012-03-23 14:16:41.161 Scheduled 0 items in 0.1 = 0.04 match + 0.09 place
2012-03-23 14:17:03.177 MainServer::ANN Monitor
2012-03-23 14:17:03.264 adding: gareth-xdesktop64 as a client (events: 2)
2012-03-23 14:23:42.908 Reschedule requested for id -1.
2012-03-23 14:23:43.047 Scheduled 0 items in 0.1 = 0.04 match + 0.09 place
2012-03-23 14:25:53.230 MainServer::ANN Monitor
2012-03-23 14:25:53.328 adding: gareth-xdesktop64 as a client (events: 0)
2012-03-23 14:25:53.371 MainServer::ANN Monitor
2012-03-23 14:25:53.412 adding: gareth-xdesktop64 as a client (events: 1)
2012-03-23 14:25:58.171 MainServer::ANN Playback
2012-03-23 14:25:58.212 adding: gareth-xdesktop64 as a client (events: 0)
2012-03-23 14:25:58.377 TVRec(1): Changing from None to WatchingLiveTV
2012-03-23 14:25:58.426 TVRec(1): HW Tuner: 1->1
2012-03-23 14:25:58.593 LoadFromScheduler(): Error, called from backend.
2012-03-23 14:25:58.596 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2012-03-23 14:26:13.603 TVRec(1): Changing from WatchingLiveTV to None
2012-03-23 14:27:25.646 UPnpMedia: BuildMediaMap VIDEO scan starting in :/media/sdb1/Videos:
2012-03-23 14:27:25.844 UPnpMedia: BuildMediaMap Done. Found 173 objects
2012-03-23 14:27:31.638 Reschedule requested for id -1.
2012-03-23 14:27:31.794 Scheduled 0 items in 0.2 = 0.05 match + 0.10 place
2012-03-23 14:27:39.531 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2012-03-23 14:28:39.598 Expiring 0 MB for 1001 at 2012-03-23T14:25:58 => "Escape to the Country":Hereford
2012-03-23 14:32:52.050 Reschedule requested for id -1.
2012-03-23 14:32:52.184 Scheduled 0 items in 0.1 = 0.04 match + 0.09 place

Thanks in advance! :)

---

### Post by Daveth on 2012-03-23
was the failure after a software upgrade, or just as random as it sounds?

---

### Post by gdbutcher on 2012-03-23
No I don't think there was an update I installed it yesterday and everything worked. I booted it up today and the record function stopped working!? Strange

---

### Post by anewguy on 2012-03-23
Do you remember if, along with everything you had to do to make this work, you had to load a module - something in the syntax of 

sudo modprobe xxxxxxx

If so, it's possible that "xxxxxxx" was never added to the /etc/modules file, so when you rebooted the module was no longer loaded.

If you think this may be the case, try the modprobe again - if it works, use gksudo gedit /etc/modules and add whatever "xxxxxxx" might be on a new line at the end of the file.  Save it, exit the editor, and reboot and see if it works then.

This is about all I can think of that would change on a reboot.

This could be particularly certain if you had to load some sort of driver for your video capture device.

Dave ;)

---

### Post by Derek Karpinski on 2012-03-23
My guess is you have a webcam as well as your TV tuner card.  When you restarted, your tuner was no longer on /dev/video0 (or 1), and it swapped with your webcam.
 
I think you'll have to write a udev rule to get your tuner to consistantly stick to video0 (or 1).
 
Just my guess.

---

### Post by gdbutcher on 2012-03-23
Thank you for your responses, unfortunatley I dont have a webcam attached to this PC so sadly it cant be that i'm afraid. 

Nor did I use modprobe, I used the instructions on this page: [http://www.mythtv.org/wiki/AVerTV_DVB-T_Volar]("http://www.mythtv.org/wiki/AVerTV_DVB-T_Volar") to install the AverTV Volar T USB stick and as for the Kworld P160 I simply activated the drivers available in Settings > Additional Drivers.

Thanks anyway, I appreciate it. :)

---

### Post by anewguy on 2012-03-23
So, when I looked at that link, they have you download some device firmware if you are on 7.10 or earlier, otherwise it claims that the dvb-usb driver is used.  I'm on Windows right now (netbook, in bed due to back problems ;( ) so I can't do the checking on my system.  If it was me, I'd try the following (no guarantee the syntax is even correct right now):

- unplug the device
-in a terminal window type:

sudo modprobe dvb-usb (this may be where things say something like module not found or any other number of error).  If an error occurs, use cut-and-paste if possible to copy the terminal window here (or a screenshot attached), and the same thing for:
lsmod

- plug the device back in and see if it works.  You may want to try kaffiene (I think that's what it said in the link for testing).

Also, post the output of dmesg back here as well (click the "#" on the menu bar and paste between).

Sorry I can't be of more direct help, but I don't have that card, and I've never tried making my card work yet at all.

Dave ;)

---

### Post by gdbutcher on 2012-03-26
Thanks for your suggestions anewguy, here is the info you requested:
1. sudo modprobe dvb-usb doestn't output any messages
2. Output from lsmod is:
```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  4 
bluetooth             166112  10 bnep,rfcomm
tda18271               58632  2 
snd_hda_codec_hdmi     32040  1 
rc_avermedia_m135a     12526  0 
mxl5005s               46356  1 
af9013                 27791  3 
ppdev                  17113  0 
snd_hda_intel          33390  1 
snd_hda_codec         104931  2 snd_hda_codec_hdmi,snd_hda_intel
snd_cmipci             45105  3 
gameport               19693  1 snd_cmipci
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_cmipci
snd_opl3_lib           19391  1 snd_cmipci
snd_hwdep              13668  2 snd_hda_codec,snd_opl3_lib
snd_mpu401_uart        14169  1 snd_cmipci
ir_lirc_codec          12898  0 
lirc_dev               19204  1 ir_lirc_codec
ir_sony_decoder        12549  0 
ir_jvc_decoder         12546  0 
ir_rc6_decoder         12546  0 
ir_rc5_decoder         12546  0 
ir_nec_decoder         12546  0 
snd_seq_midi           13324  0 
dvb_usb_af9015         31068  14 
dvb_usb                24444  1 dvb_usb_af9015
dvb_core              110616  1 dvb_usb
rc_core                26963  10 rc_avermedia_m135a,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,dvb_usb_af9015,dvb_usb
snd_rawmidi            30547  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
k8temp                 13057  0 
edac_core              53746  0 
edac_mce_amd           23709  0 
radeon               1016475  2 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
parport_pc             36962  1 
sp5100_tco             13791  0 
i2c_piix4              13301  0 
snd_timer              29991  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device         14540  4 snd_opl3_lib,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
drm                   236290  4 radeon,ttm,drm_kms_helper
snd                    68266  20 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_cmipci,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 radeon
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usb_storage            57901  0 
firewire_ohci          40722  0 
usbhid                 47198  0 
firewire_core          63626  1 firewire_ohci
uas                    18027  0 
hid                    95463  1 usbhid
crc_itu_t              12707  1 firewire_core
r8169                  52788  0 
floppy                 70365  0 
pata_atiixp            13164  0 
ahci                   26002  3 
libahci                26861  1 ahci 
```

3. Output from dmesg is ```
n't support DPO or FUA
[    1.940118] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.940120] ata3.00: configured for UDMA/133
[    2.020626]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[    2.020947] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.548018] ata2: softreset failed (device not ready)
[    2.548021] ata2: applying SB600 PMP SRST workaround and retrying
[    2.720025] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.720125] ata2.00: ATAPI: SONY    BD-ROM  BDU-X10S, 1.0d, max UDMA/66
[    2.720127] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.720603] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.720605] ata2.00: configured for UDMA/66
[    2.724497] scsi 1:0:0:0: CD-ROM            SONY     BD-ROM BDU-X10S  1.0d PQ: 0 ANSI: 5
[    2.729450] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[    2.729452] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.729522] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.729580] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.729702] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    2.729790] sd 2:0:0:0: [sdb] 976771055 512-byte logical blocks: (500 GB/465 GiB)
[    2.729812] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    2.729829] sd 2:0:0:0: [sdb] Write Protect is off
[    2.729831] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.729849] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.737800]  sdb: sdb1
[    2.737996] sd 2:0:0:0: [sdb] Attached SCSI disk
[    2.742812] Initializing USB Mass Storage driver...
[    2.743481] firewire_ohci 0000:02:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.743709] input: AVerMedia A815 as /devices/pci0000:00/0000:00:13.5/usb1/1-1/1-1:1.1/input/input3
[    2.743763] scsi6 : usb-storage 1-3:1.3
[    2.743856] generic-usb 0003:07CA:A815.0001: input,hidraw0: USB HID v1.01 Keyboard [AVerMedia A815] on usb-0000:00:13.5-1/input1
[    2.743876] usbcore: registered new interface driver usb-storage
[    2.743878] USB Mass Storage support registered.
[    2.743878] usbcore: registered new interface driver usbhid
[    2.743881] usbhid: USB HID core driver
[    2.796107] firewire_ohci: Added fw-ohci device 0000:02:0e.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    3.296106] firewire_core: created device fw0: GUID 001d7d0000f201ac, S400
[    3.430142] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[    3.744737] scsi 6:0:0:0: Direct-Access     HP       Photosmart C4280 1.00 PQ: 0 ANSI: 5
[    3.748691] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    3.749971] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   15.473318] udevd[379]: starting version 173
[   15.525254] lp: driver loaded but no devices found
[   15.544951] Adding 4190204k swap on /dev/sda9.  Priority:-1 extents:1 across:4190204k 
[   15.563502] [drm] Initialized drm 1.1.0 20060810
[   15.595612] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   15.599118] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   15.599194] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   15.646089] parport_pc 00:0a: reported by Plug and Play ACPI
[   15.646148] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   15.675044] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   15.696740] [drm] radeon defaulting to kernel modesetting.
[   15.696743] [drm] radeon kernel modesetting enabled.
[   15.701838] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.701844] radeon 0000:01:00.0: setting latency timer to 64
[   15.702056] [drm] initializing kernel modesetting (RV770 0x1002:0x9442 0x174B:0xE104).
[   15.702087] [drm] register mmio base: 0xFDFE0000
[   15.702088] [drm] register mmio size: 65536
[   15.702411] ATOM BIOS: HD4850
[   15.702441] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[   15.702443] radeon 0000:01:00.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   15.702732] [drm] Detected VRAM RAM=512M, BAR=256M
[   15.702735] [drm] RAM width 256bits DDR
[   15.708297] [TTM] Zone  kernel: Available graphics memory: 2028048 kiB.
[   15.708300] [TTM] Initializing pool allocator.
[   15.708325] [drm] radeon: 512M of VRAM memory ready
[   15.708327] [drm] radeon: 512M of GTT memory ready.
[   15.708343] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.708344] [drm] Driver supports precise vblank timestamp query.
[   15.708384] radeon 0000:01:00.0: irq 41 for MSI/MSI-X
[   15.708389] radeon 0000:01:00.0: radeon: using MSI.
[   15.708419] [drm] radeon: irq initialized.
[   15.708425] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   15.709995] [drm] Loading RV770 Microcode
[   15.730134] MCE: In-kernel MCE decoding enabled.
[   15.730797] EDAC MC: Ver: 2.1.0
[   15.737760] lp0: using parport0 (interrupt-driven).
[   15.738046] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   15.751590] AMD64 EDAC driver v3.4.0
[   15.754319] EDAC amd64: DRAM ECC disabled.
[   15.754329] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   15.754330]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   15.754331]  (Note that use of the override may cause unknown side effects.)
[   15.772575] udevd[418]: renamed network interface eth0 to eth1
[   15.785967] IR NEC protocol handler initialized
[   15.793826] IR RC5(x) protocol handler initialized
[   15.796852] IR RC6 protocol handler initialized
[   15.800610] IR JVC protocol handler initialized
[   15.809411] IR Sony protocol handler initialized
[   15.819007] lirc_dev: IR Remote Control driver registered, major 249 
[   15.819189] IR LIRC bridge handler initialized
[   15.864222] type=1400 audit(1332752812.181:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=771 comm="apparmor_parser"
[   15.864263] type=1400 audit(1332752812.181:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=700 comm="apparmor_parser"
[   15.864583] type=1400 audit(1332752812.181:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=771 comm="apparmor_parser"
[   15.864704] type=1400 audit(1332752812.181:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=700 comm="apparmor_parser"
[   15.864809] type=1400 audit(1332752812.181:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=771 comm="apparmor_parser"
[   15.864985] type=1400 audit(1332752812.181:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=700 comm="apparmor_parser"
[   15.867049] type=1400 audit(1332752812.181:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=777 comm="apparmor_parser"
[   15.869894] type=1400 audit(1332752812.185:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=778 comm="apparmor_parser"
[   15.932736] C-Media PCI 0000:02:07.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.965403] ppdev: user-space parallel port driver
[   16.014839] radeon 0000:01:00.0: WB enabled
[   16.036223] dvb-usb: found a 'AVerMedia AVerTV DVB-T Volar X' in warm state.
[   16.036290] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.036710] DVB: registering new adapter (AVerMedia AVerTV DVB-T Volar X)
[   16.053099] af9013: firmware version:4.95.0.0
[   16.060102] DVB: registering adapter 0 frontend 0 (Afatech AF9013 DVB-T)...
[   16.062380] [drm] ring test succeeded in 1 usecs
[   16.062484] [drm] radeon: ib pool ready.
[   16.062554] [drm] ib test succeeded in 0 usecs
[   16.062561] failed to evaluate ATIF got AE_BAD_PARAMETER
[   16.062768] [drm] Radeon Display Connectors
[   16.062770] [drm] Connector 0:
[   16.062771] [drm]   DVI-I
[   16.062772] [drm]   HPD2
[   16.062774] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
[   16.062775] [drm]   Encoders:
[   16.062776] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   16.062778] [drm]     DFP2: INTERNAL_KLDSCP_LVTMA
[   16.062779] [drm] Connector 1:
[   16.062780] [drm]   HDMI-A
[   16.062781] [drm]   HPD3
[   16.062782] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   16.062784] [drm]   Encoders:
[   16.062785] [drm]     DFP1: INTERNAL_UNIPHY
[   16.062786] [drm] Connector 2:
[   16.062787] [drm]   VGA
[   16.062788] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
[   16.062790] [drm]   Encoders:
[   16.062791] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   16.071196] MXL5005S: Attached at address 0xc6
[   16.072757] [drm] Radeon display connector DVI-I-1: No monitor connected or invalid EDID
[   16.085610] [drm] Radeon display connector HDMI-A-1: No monitor connected or invalid EDID
[   16.116036] Registered IR keymap rc-avermedia-m135a
[   16.116181] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.5/usb1/1-1/rc/rc0/input4
[   16.116256] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:13.5/usb1/1-1/rc/rc0
[   16.116259] dvb-usb: schedule remote query interval to 500 msecs.
[   16.116262] dvb-usb: AVerMedia AVerTV DVB-T Volar X successfully initialized and connected.
[   16.142889] [drm] Radeon display connector VGA-1: Found valid EDID
[   16.142928] [drm] Internal thermal controller with fan control
[   16.143006] [drm] radeon: power management initialized
[   16.220712] [drm] fb mappable at 0xD0142000
[   16.220715] [drm] vram apper at 0xD0000000
[   16.220717] [drm] size 5324800
[   16.220718] [drm] fb depth is 24
[   16.220719] [drm]    pitch is 5888
[   16.220802] fbcon: radeondrmfb (fb0) is primary device
[   16.220927] Console: switching to colour frame buffer device 180x56
[   16.220951] fb0: radeondrmfb frame buffer device
[   16.220952] drm: registered panic notifier
[   16.220959] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:00.0 on minor 0
[   16.223126] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   16.223201] HDA Intel 0000:01:00.1: irq 42 for MSI/MSI-X
[   16.223226] HDA Intel 0000:01:00.1: setting latency timer to 64
[   16.241038] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   16.241162] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input5
[   16.504561] dvb-usb: found a 'KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T)' in cold state, will try to load a firmware
[   16.520504] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   16.526185] dvb-usb: downloading firmware from file 'dvb-usb-af9015.fw'
[   16.624449] dvb-usb: found a 'KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T)' in warm state.
[   16.624656] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.625103] DVB: registering new adapter (KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T))
[   16.628312] af9013: firmware version:4.95.0.0
[   16.636391] DVB: registering adapter 1 frontend 0 (Afatech AF9013 DVB-T)...
[   16.653538] tda18271 8-00c0: creating new instance
[   16.659684] TDA18271HD/C2 detected @ 8-00c0
[   16.793976] r8169 0000:02:0f.0: eth1: link down
[   16.794487] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   16.920836] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.921249] DVB: registering new adapter (KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T))
[   17.002503] type=1400 audit(1332752813.317:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1005 comm="apparmor_parser"
[   17.002869] type=1400 audit(1332752813.317:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=1004 comm="apparmor_parser"
[   17.133029] init: failsafe main process (946) killed by TERM signal
[   17.138779] init: apport pre-start process (1043) terminated with status 1
[   17.147013] init: apport post-stop process (1069) terminated with status 1
[   17.326967] Bluetooth: Core ver 2.16
[   17.327014] NET: Registered protocol family 31
[   17.327016] Bluetooth: HCI device and connection manager initialized
[   17.327018] Bluetooth: HCI socket layer initialized
[   17.327020] Bluetooth: L2CAP socket layer initialized
[   17.328381] Bluetooth: SCO socket layer initialized
[   17.330232] Bluetooth: RFCOMM TTY layer initialized
[   17.330237] Bluetooth: RFCOMM socket layer initialized
[   17.330239] Bluetooth: RFCOMM ver 1.11
[   17.430944] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.430948] Bluetooth: BNEP filters: protocol multicast
[   17.636893] af9013: found a 'Afatech AF9013 DVB-T' in warm state.
[   17.640723] af9013: firmware version:4.95.0.0
[   17.659774] DVB: registering adapter 2 frontend 0 (Afatech AF9013 DVB-T)...
[   17.661070] tda18271 9-00c0: creating new instance
[   17.665894] TDA18271HD/C2 detected @ 9-00c0
[   17.947815] Registered IR keymap rc-empty
[   17.947899] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:02:06.2/usb2/2-1/rc/rc1/input7
[   17.947961] rc1: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:02:06.2/usb2/2-1/rc/rc1
[   17.947964] dvb-usb: schedule remote query interval to 500 msecs.
[   17.947966] dvb-usb: KWorld PlusTV Dual DVB-T PCI (DVB-T PC160-2T) successfully initialized and connected.
[   17.959502] usbcore: registered new interface driver dvb_usb_af9015
[   17.959661] Did not find alt setting 1 for intf 0, config 1
[   18.419270] r8169 0000:02:0f.0: eth1: link up
[   18.419789] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   19.365198] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   19.972288] init: plymouth-stop pre-start process (1554) terminated with status 1
[   21.926532] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   26.813279] tda18271: performing RF tracking filter calibration
[   28.008306] af9015: recv bulk message failed:-71
[   28.008553] af9015: recv bulk message failed:-75
[   28.008555] af9013: I2C read failed reg:d417
[   28.008558] tda18271_read_extended: [8-00c0|M] ERROR: i2c_transfer returned: -1
[   28.008561] tda18271_powerscan: [8-00c0|M] error -1 on line 506
[   28.008563] tda18271_rf_tracking_filters_init: [8-00c0|M] error -1 on line 601
[   28.008565] tda18271_calc_rf_filter_curve: [8-00c0|M] error -1 on line 662
[   28.008567] tda18271c2_rf_cal_init: [8-00c0|M] error -1 on line 687
[   28.008569] tda18271: RF tracking filter calibration failed!
[   28.018179] tda18271: performing RF tracking filter calibration
[   29.080013] eth1: no IPv6 routers present
[   31.469732] tda18271: RF tracking filter calibration complete
[   91.547016] usb 1-1: USB disconnect, device number 2
[   91.572652] af9015: bulk message failed:-19 (8/0)
[   91.572661] af9013: I2C read failed reg:d730
[  240.708035] INFO: task khubd:20 blocked for more than 120 seconds.
[  240.708044] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  240.708050] khubd           D ffffffff81805120     0    20      2 0x00000000
[  240.708061]  ffff880127a01ae0 0000000000000046 ffff880125e19f00 ffff88011152b0a8
[  240.708070]  ffff880127a01fd8 ffff880127a01fd8 ffff880127a01fd8 0000000000012a40
[  240.708078]  ffff880128f18000 ffff880128b5c560 ffff880127a01af0 ffff88012529b000
[  240.708086] Call Trace:
[  240.708102]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[  240.708131]  [<ffffffffa02f67d5>] dvb_unregister_frontend+0xc5/0x110 [dvb_core]
[  240.708143]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[  240.708154]  [<ffffffffa02a66c2>] dvb_usb_adapter_frontend_exit+0x22/0x40 [dvb_usb]
[  240.708164]  [<ffffffffa02a55dc>] dvb_usb_exit+0x4c/0xd0 [dvb_usb]
[  240.708174]  [<ffffffffa02a56b1>] dvb_usb_device_exit+0x51/0x70 [dvb_usb]
[  240.708184]  [<ffffffffa02cb06d>] af9015_usb_device_exit+0x5d/0x70 [dvb_usb_af9015]
[  240.708195]  [<ffffffff814585f2>] usb_unbind_interface+0x52/0x180
[  240.708206]  [<ffffffff813d05ec>] __device_release_driver+0x7c/0xe0
[  240.708213]  [<ffffffff813d067c>] device_release_driver+0x2c/0x40
[  240.708220]  [<ffffffff813d0128>] bus_remove_device+0x78/0xb0
[  240.708227]  [<ffffffff813cd6fd>] device_del+0x12d/0x1b0
[  240.708234]  [<ffffffff8145631f>] usb_disable_device+0xaf/0x1d0
[  240.708243]  [<ffffffff8144f110>] usb_disconnect+0xa0/0x140
[  240.708250]  [<ffffffff8144ff10>] hub_port_connect_change+0xa0/0x6e0
[  240.708258]  [<ffffffff81455837>] ? usb_control_msg+0xf7/0x120
[  240.708266]  [<ffffffff81450a04>] hub_events+0x4b4/0x610
[  240.708273]  [<ffffffff815f0874>] ? __schedule+0x3d4/0x700
[  240.708281]  [<ffffffff81450b95>] hub_thread+0x35/0x180
[  240.708288]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[  240.708295]  [<ffffffff81450b60>] ? hub_events+0x610/0x610
[  240.708303]  [<ffffffff8108135c>] kthread+0x8c/0xa0
[  240.708312]  [<ffffffff815fc324>] kernel_thread_helper+0x4/0x10
[  240.708320]  [<ffffffff810812d0>] ? flush_kthread_worker+0xa0/0xa0
[  240.708327]  [<ffffffff815fc320>] ? gs_change+0x13/0x13
[  360.708040] INFO: task khubd:20 blocked for more than 120 seconds.
[  360.708048] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  360.708055] khubd           D ffffffff81805120     0    20      2 0x00000000
[  360.708066]  ffff880127a01ae0 0000000000000046 ffff880125e19f00 ffff88011152b0a8
[  360.708074]  ffff880127a01fd8 ffff880127a01fd8 ffff880127a01fd8 0000000000012a40
[  360.708083]  ffff880128f18000 ffff880128b5c560 ffff880127a01af0 ffff88012529b000
[  360.708091] Call Trace:
[  360.708107]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[  360.708136]  [<ffffffffa02f67d5>] dvb_unregister_frontend+0xc5/0x110 [dvb_core]
[  360.708147]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[  360.708158]  [<ffffffffa02a66c2>] dvb_usb_adapter_frontend_exit+0x22/0x40 [dvb_usb]
[  360.708168]  [<ffffffffa02a55dc>] dvb_usb_exit+0x4c/0xd0 [dvb_usb]
[  360.708178]  [<ffffffffa02a56b1>] dvb_usb_device_exit+0x51/0x70 [dvb_usb]
[  360.708188]  [<ffffffffa02cb06d>] af9015_usb_device_exit+0x5d/0x70 [dvb_usb_af9015]
[  360.708198]  [<ffffffff814585f2>] usb_unbind_interface+0x52/0x180
[  360.708209]  [<ffffffff813d05ec>] __device_release_driver+0x7c/0xe0
[  360.708216]  [<ffffffff813d067c>] device_release_driver+0x2c/0x40
[  360.708223]  [<ffffffff813d0128>] bus_remove_device+0x78/0xb0
[  360.708230]  [<ffffffff813cd6fd>] device_del+0x12d/0x1b0
[  360.708236]  [<ffffffff8145631f>] usb_disable_device+0xaf/0x1d0
[  360.708245]  [<ffffffff8144f110>] usb_disconnect+0xa0/0x140
[  360.708253]  [<ffffffff8144ff10>] hub_port_connect_change+0xa0/0x6e0
[  360.708260]  [<ffffffff81455837>] ? usb_control_msg+0xf7/0x120
[  360.708267]  [<ffffffff81450a04>] hub_events+0x4b4/0x610
[  360.708275]  [<ffffffff815f0874>] ? __schedule+0x3d4/0x700
[  360.708282]  [<ffffffff81450b95>] hub_thread+0x35/0x180
[  360.708289]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[  360.708296]  [<ffffffff81450b60>] ? hub_events+0x610/0x610
[  360.708303]  [<ffffffff8108135c>] kthread+0x8c/0xa0
[  360.708312]  [<ffffffff815fc324>] kernel_thread_helper+0x4/0x10
[  360.708319]  [<ffffffff810812d0>] ? flush_kthread_worker+0xa0/0xa0
[  360.708327]  [<ffffffff815fc320>] ? gs_change+0x13/0x13
[  480.708037] INFO: task khubd:20 blocked for more than 120 seconds.
[  480.708046] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  480.708052] khubd           D ffffffff81805120     0    20      2 0x00000000
[  480.708063]  ffff880127a01ae0 0000000000000046 ffff880125e19f00 ffff88011152b0a8
[  480.708071]  ffff880127a01fd8 ffff880127a01fd8 ffff880127a01fd8 0000000000012a40
[  480.708080]  ffff880128f18000 ffff880128b5c560 ffff880127a01af0 ffff88012529b000
[  480.708088] Call Trace:
[  480.708103]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[  480.708132]  [<ffffffffa02f67d5>] dvb_unregister_frontend+0xc5/0x110 [dvb_core]
[  480.708143]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[  480.708154]  [<ffffffffa02a66c2>] dvb_usb_adapter_frontend_exit+0x22/0x40 [dvb_usb]
[  480.708164]  [<ffffffffa02a55dc>] dvb_usb_exit+0x4c/0xd0 [dvb_usb]
[  480.708174]  [<ffffffffa02a56b1>] dvb_usb_device_exit+0x51/0x70 [dvb_usb]
[  480.708184]  [<ffffffffa02cb06d>] af9015_usb_device_exit+0x5d/0x70 [dvb_usb_af9015]
[  480.708194]  [<ffffffff814585f2>] usb_unbind_interface+0x52/0x180
[  480.708205]  [<ffffffff813d05ec>] __device_release_driver+0x7c/0xe0
[  480.708212]  [<ffffffff813d067c>] device_release_driver+0x2c/0x40
[  480.708220]  [<ffffffff813d0128>] bus_remove_device+0x78/0xb0
[  480.708226]  [<ffffffff813cd6fd>] device_del+0x12d/0x1b0
[  480.708233]  [<ffffffff8145631f>] usb_disable_device+0xaf/0x1d0
[  480.708242]  [<ffffffff8144f110>] usb_disconnect+0xa0/0x140
[  480.708249]  [<ffffffff8144ff10>] hub_port_connect_change+0xa0/0x6e0
[  480.708256]  [<ffffffff81455837>] ? usb_control_msg+0xf7/0x120
[  480.708264]  [<ffffffff81450a04>] hub_events+0x4b4/0x610
[  480.708271]  [<ffffffff815f0874>] ? __schedule+0x3d4/0x700
[  480.708279]  [<ffffffff81450b95>] hub_thread+0x35/0x180
[  480.708286]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[  480.708293]  [<ffffffff81450b60>] ? hub_events+0x610/0x610
[  480.708300]  [<ffffffff8108135c>] kthread+0x8c/0xa0
[  480.708309]  [<ffffffff815fc324>] kernel_thread_helper+0x4/0x10
[  480.708316]  [<ffffffff810812d0>] ? flush_kthread_worker+0xa0/0xa0
[  480.708323]  [<ffffffff815fc320>] ? gs_change+0x13/0x13
[  600.708052] INFO: task khubd:20 blocked for more than 120 seconds.
[  600.708061] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  600.708067] khubd           D ffffffff81805120     0    20      2 0x00000000
[  600.708078]  ffff880127a01ae0 0000000000000046 ffff880125e19f00 ffff88011152b0a8
[  600.708087]  ffff880127a01fd8 ffff880127a01fd8 ffff880127a01fd8 0000000000012a40
[  600.708095]  ffff880128f18000 ffff880128b5c560 ffff880127a01af0 ffff88012529b000
[  600.708103] Call Trace:
[  600.708119]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[  600.708148]  [<ffffffffa02f67d5>] dvb_unregister_frontend+0xc5/0x110 [dvb_core]
[  600.708158]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[  600.708171]  [<ffffffffa02a66c2>] dvb_usb_adapter_frontend_exit+0x22/0x40 [dvb_usb]
[  600.708181]  [<ffffffffa02a55dc>] dvb_usb_exit+0x4c/0xd0 [dvb_usb]
[  600.708190]  [<ffffffffa02a56b1>] dvb_usb_device_exit+0x51/0x70 [dvb_usb]
[  600.708200]  [<ffffffffa02cb06d>] af9015_usb_device_exit+0x5d/0x70 [dvb_usb_af9015]
[  600.708211]  [<ffffffff814585f2>] usb_unbind_interface+0x52/0x180
[  600.708222]  [<ffffffff813d05ec>] __device_release_driver+0x7c/0xe0
[  600.708229]  [<ffffffff813d067c>] device_release_driver+0x2c/0x40
[  600.708236]  [<ffffffff813d0128>] bus_remove_device+0x78/0xb0
[  600.708243]  [<ffffffff813cd6fd>] device_del+0x12d/0x1b0
[  600.708249]  [<ffffffff8145631f>] usb_disable_device+0xaf/0x1d0
[  600.708258]  [<ffffffff8144f110>] usb_disconnect+0xa0/0x140
[  600.708266]  [<ffffffff8144ff10>] hub_port_connect_change+0xa0/0x6e0
[  600.708273]  [<ffffffff81455837>] ? usb_control_msg+0xf7/0x120
[  600.708280]  [<ffffffff81450a04>] hub_events+0x4b4/0x610
[  600.708287]  [<ffffffff815f0874>] ? __schedule+0x3d4/0x700
[  600.708295]  [<ffffffff81450b95>] hub_thread+0x35/0x180
[  600.708302]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[  600.708309]  [<ffffffff81450b60>] ? hub_events+0x610/0x610
[  600.708316]  [<ffffffff8108135c>] kthread+0x8c/0xa0
[  600.708325]  [<ffffffff815fc324>] kernel_thread_helper+0x4/0x10
[  600.708333]  [<ffffffff810812d0>] ? flush_kthread_worker+0xa0/0xa0
[  600.708340]  [<ffffffff815fc320>] ? gs_change+0x13/0x13
[  720.708050] INFO: task khubd:20 blocked for more than 120 seconds.
[  720.708059] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  720.708065] khubd           D ffffffff81805120     0    20      2 0x00000000
[  720.708106]  ffff880127a01ae0 0000000000000046 ffff880125e19f00 ffff88011152b0a8
[  720.708114]  ffff880127a01fd8 ffff880127a01fd8 ffff880127a01fd8 0000000000012a40
[  720.708122]  ffff880128f18000 ffff880128b5c560 ffff880127a01af0 ffff88012529b000
[  720.708131] Call Trace:
[  720.708146]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[  720.708176]  [<ffffffffa02f67d5>] dvb_unregister_frontend+0xc5/0x110 [dvb_core]
[  720.708187]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[  720.708199]  [<ffffffffa02a66c2>] dvb_usb_adapter_frontend_exit+0x22/0x40 [dvb_usb]
[  720.708208]  [<ffffffffa02a55dc>] dvb_usb_exit+0x4c/0xd0 [dvb_usb]
[  720.708218]  [<ffffffffa02a56b1>] dvb_usb_device_exit+0x51/0x70 [dvb_usb]
[  720.708228]  [<ffffffffa02cb06d>] af9015_usb_device_exit+0x5d/0x70 [dvb_usb_af9015]
[  720.708239]  [<ffffffff814585f2>] usb_unbind_interface+0x52/0x180
[  720.708250]  [<ffffffff813d05ec>] __device_release_driver+0x7c/0xe0
[  720.708257]  [<ffffffff813d067c>] device_release_driver+0x2c/0x40
[  720.708264]  [<ffffffff813d0128>] bus_remove_device+0x78/0xb0
[  720.708271]  [<ffffffff813cd6fd>] device_del+0x12d/0x1b0
[  720.708277]  [<ffffffff8145631f>] usb_disable_device+0xaf/0x1d0
[  720.708286]  [<ffffffff8144f110>] usb_disconnect+0xa0/0x140
[  720.708294]  [<ffffffff8144ff10>] hub_port_connect_change+0xa0/0x6e0
[  720.708301]  [<ffffffff81455837>] ? usb_control_msg+0xf7/0x120
[  720.708309]  [<ffffffff81450a04>] hub_events+0x4b4/0x610
[  720.708316]  [<ffffffff815f0874>] ? __schedule+0x3d4/0x700
[  720.708323]  [<ffffffff81450b95>] hub_thread+0x35/0x180
[  720.708330]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[  720.708337]  [<ffffffff81450b60>] ? hub_events+0x610/0x610
[  720.708345]  [<ffffffff8108135c>] kthread+0x8c/0xa0
[  720.708354]  [<ffffffff815fc324>] kernel_thread_helper+0x4/0x10
[  720.708361]  [<ffffffff810812d0>] ? flush_kthread_worker+0xa0/0xa0
[  720.708369]  [<ffffffff815fc320>] ? gs_change+0x13/0x13
[  840.708066] INFO: task khubd:20 blocked for more than 120 seconds.
[  840.708076] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  840.708082] khubd           D ffffffff81805120     0    20      2 0x00000000
[  840.708092]  ffff880127a01ae0 0000000000000046 ffff880125e19f00 ffff88011152b0a8
[  840.708101]  ffff880127a01fd8 ffff880127a01fd8 ffff880127a01fd8 0000000000012a40
[  840.708109]  ffff880128f18000 ffff880128b5c560 ffff880127a01af0 ffff88012529b000
[  840.708118] Call Trace:
[  840.708133]  [<ffffffff815f0ecf>] schedule+0x3f/0x60
[  840.708162]  [<ffffffffa02f67d5>] dvb_unregister_frontend+0xc5/0x110 [dvb_core]
[  840.708173]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[  840.708186]  [<ffffffffa02a66c2>] dvb_usb_adapter_frontend_exit+0x22/0x40 [dvb_usb]
[  840.708196]  [<ffffffffa02a55dc>] dvb_usb_exit+0x4c/0xd0 [dvb_usb]
[  840.708205]  [<ffffffffa02a56b1>] dvb_usb_device_exit+0x51/0x70 [dvb_usb]
[  840.708215]  [<ffffffffa02cb06d>] af9015_usb_device_exit+0x5d/0x70 [dvb_usb_af9015]
[  840.708226]  [<ffffffff814585f2>] usb_unbind_interface+0x52/0x180
[  840.708237]  [<ffffffff813d05ec>] __device_release_driver+0x7c/0xe0
[  840.708244]  [<ffffffff813d067c>] device_release_driver+0x2c/0x40
[  840.708251]  [<ffffffff813d0128>] bus_remove_device+0x78/0xb0
[  840.708258]  [<ffffffff813cd6fd>] device_del+0x12d/0x1b0
[  840.708265]  [<ffffffff8145631f>] usb_disable_device+0xaf/0x1d0
[  840.708274]  [<ffffffff8144f110>] usb_disconnect+0xa0/0x140
[  840.708282]  [<ffffffff8144ff10>] hub_port_connect_change+0xa0/0x6e0
[  840.708289]  [<ffffffff81455837>] ? usb_control_msg+0xf7/0x120
[  840.708296]  [<ffffffff81450a04>] hub_events+0x4b4/0x610
[  840.708304]  [<ffffffff815f0874>] ? __schedule+0x3d4/0x700
[  840.708311]  [<ffffffff81450b95>] hub_thread+0x35/0x180
[  840.708318]  [<ffffffff81081e00>] ? add_wait_queue+0x60/0x60
[  840.708325]  [<ffffffff81450b60>] ? hub_events+0x610/0x610
[  840.708332]  [<ffffffff8108135c>] kthread+0x8c/0xa0
[  840.708341]  [<ffffffff815fc324>] kernel_thread_helper+0x4/0x10
[  840.708349]  [<ffffffff810812d0>] ? flush_kthread_worker+0xa0/0xa0
[  840.708356]  [<ffffffff815fc320>] ? gs_change+0x13/0x13

``` 

Hope this helps, thanks

---

### Post by bilboubu on 2012-04-18
[FONT=Book Antiqua]did you find a solution?[/FONT]

---

### Post by danellisuk on 2012-04-24
I have a KWorld PC160-2T and have an issue where the tuner card does not work after a system reboot.  So make sure you fully power cycle your machine off and on again.  I think the issue is something to do with loading the card's firmware which is not happening after a system reboot.

---

