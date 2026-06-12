---
title: "HP Compaq cq61-414eo, update BIOS"
date: 2014-02-14
forum: New to Ubuntu
---

### Post by fanin2 on 2014-02-14
hi
I have a problem installing a BIOS update. i have a [HP Compaq cq61-414eo]("http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&product=4126344") and have version BIOS version F.21, and want to update it to F.23 but don't know how to do it in Ubuntu. i tried installing Windows XP in Virtualbox, but there is an error saying that i need to be admin to install, even if i am admin (typical windows :P). I also tried installing it with Wine and it says the same thing "InsydeFlash can not load the driver. Please close all applications. If you are running this utility in Windows XP, please run as administrator."
the reason i am doing this is because i read that this laptop gets very hot and starts crashing after 1-2 hours of use, and that Virtualbox gets confused when trying to install Kali and thinks this is a 32bit, even if it is 64bit (not sure if this is related to the BIOS but worth a try)
is there some other way of installing this update, or am i missing something?
not sure if this is an Ubuntu problem or windows problem, hopefully i'm posting this in the right forum :P

---

### Post by Yellow Pasque on 2014-02-14
Do not try to update your BIOS through WINE or a VM. It's not going to work.

I'm pretty sure the HP BIOS updates in .exe format like that actually require Windows Vista/7. Not even FreeDOS will help you...

---

### Post by Frogs Hair on 2014-02-14
Check the release notes with the Bios update and see if there are any benefits to your hardware. Quite often Bios updates don't even apply to the hardware your'e using . Don't use wine because you might end up with an electronic brick on your hands. Bios update methods can vary depending on mother board . Some use a flash method from USB , DVD or even floppy depending on the age of the computer   and other windows computers have update software .

---

### Post by Mark Phelps on 2014-02-14
Installing BIOS updates is one of the key reasons that many folks (like me) retain multi-boot systems.

Additionally, you should NOT even attempt to do a BIOS update unless BOTH of the following are true:
1) You have a way to save off the current working BIOS to some media that you can use to do a restore later
2) You have a way to restore the saved BIOS even if you can't boot into Windows.

---

### Post by jp734 on 2014-02-15
I have hp as well and  used flashrom to update the bios.

**flashrom -p internal -r backup.rom -o backuplog.txt** (to backup your existing bios)
**flashrom -p internal -w [COLOR="#0000FF"]newbios_filename[/COLOR] -o writelog.txt** (to update your bios using the downloaded program)
**flashrom -p internal -w backup.rom -o restore.log** (to restore bios using the original)

---

### Post by LostFarmer on 2014-02-15
The comp you have is a laptop/notebook/netbook, so **do not try** useing flashrom.  It can/will make your comp a door stop.  Info taken from [http://www.flashrom.org/Laptops](http://www.flashrom.org/Laptops).

---

### Post by linux4me on 2014-02-15
According to the HP site, they only support BIOS updates for Windows 7 for your model. I hate to say this, but if you really want to update the BIOS, and there are the usual reasons for not doing so listed on the HP site, you would probably be safest installting Windows 7 on there, doing the BIOS update, then reinstalling Ubuntu. It looks like the only files they offer for BIOS updates are Windows executables, not even self-extracting archives like some manufacuturers offer.

From reading the stuff on the site, it looks like you only need to update the BIOS if you're running Win 7. If the machine came with Win XP, you probably have nothing to gain from a BIOS update if you're running Ubuntu and not having issues.

---

### Post by fanin2 on 2014-02-16
I've read somewhere (can't remember where) that a common problem with HP Compaq laptops is the temperature of the motherboards gets unnecessarily hot, which i guessed was the problem with its crashes. i also saw that the hard disk was getting too hot in SMART data in disk utility on a hard disk i used earlier. i just rechecked and it says warning in "reallocated sector count" and "current sector pending count" :/ . i tried installing windows 7 on the earlier hard disk on this laptop but it didn't work because hard disk was corrupt. i find it highly unlikely that both hard disks are corrupt by coincidence. it says on the BIOS update page "[COLOR=#000000][FONT=HPSimplified]- Fixes an intermittent issue that may result in an unexpected behavior, where the system stops responding (hangs) or a memory page fault is generated[/FONT][/COLOR]". could this be it?
so it would be best to install Windows 7 and then update? or would you think that the update is pointless?

!The cooling fan is running just fine, and hard disk temperature now is 48C (checked with disk utility) and processor cores are 46/45C (checked with lm-sensors), and [FONT=Ubuntu Mono]uname -a.[/FONT] now says it's a 64-bit. now im just confused :confused:.
i'll try and keep the laptop running to see if it still crashes or slows down again.

---

### Post by Frogs Hair on 2014-02-16
My HP Netbook which I dual boot with 12.04 has Bios updating software on the Win 7 side . If the Bios is a .exe you will most likely need Windows if there is no option to flash the Bios ether from DVD, USB, or external floppy. .

---

### Post by fanin2 on 2014-02-16
This is just weird, but it runs fine now and has for about 5 hours. should i be worried about those hard disk errors?
[COLOR=#000000]"reallocated sector count" and "current sector pending count"
[/COLOR]

---

### Post by Yellow Pasque on 2014-02-16
Yeah, they're a bit disconcerting. Can you give the smart log?
```
smartctl -a /dev/sda
```

---

### Post by fanin2 on 2014-02-17
> **Temüjin said:**
> Yeah, they're a bit disconcerting. Can you give the smart log?
```
smartctl -a /dev/sda
```

```
=== START OF INFORMATION SECTION ===
Model Family:     Fujitsu MHV
Device Model:     FUJITSU MHV2120BH PL
Serial Number:    NW9XT682A3U4
Firmware Version: 892C
User Capacity:    120,034,123,776 bytes [120 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  ATA/ATAPI-7 T13 1532D revision 4a
Local Time is:    Mon Feb 17 08:34:55 2014 WET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 120)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (  702) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  82) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   084   046    Pre-fail  Always       -       238962
  2 Throughput_Performance  0x0005   100   100   030    Pre-fail  Offline      -       31981568
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       2041
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       72 (1954, 46)
  7 Seek_Error_Rate         0x000f   100   100   047    Pre-fail  Always       -       3845
  8 Seek_Time_Performance   0x0005   100   100   019    Pre-fail  Offline      -       0
  9 Power_On_Seconds        0x0032   088   088   000    Old_age   Always       -       1h+45m+28s
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       2009
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       124
193 Load_Cycle_Count        0x0032   094   094   000    Old_age   Always       -       136681
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       25 (Min/Max 7/55)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       15970
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       46 (0, 6902)
197 Current_Pending_Sector  0x0012   093   091   000    Old_age   Always       -       8
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000f   100   100   060    Pre-fail  Always       -       23809
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       2632749286066
240 Head_Flying_Hours       0x003e   200   200   000    Old_age   Always       -       0


SMART Error Log Version: 1
ATA Error Count: 962 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.


Error 962 occurred at disk power-on lifetime: 6316 hours (263 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 9d 97 16 ec 40  Error: UNC 157 sectors at LBA = 0x00ec1697 = 15472279


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 34 12 ec 40 00      00:36:35.270  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:36:17.571  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:59.771  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:42.094  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:24.395  READ DMA EXT


Error 961 occurred at disk power-on lifetime: 6316 hours (263 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 9d 97 16 ec 40  Error: UNC 157 sectors at LBA = 0x00ec1697 = 15472279


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 34 12 ec 40 00      00:36:17.571  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:59.771  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:42.094  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:24.395  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:06.768  READ DMA EXT


Error 960 occurred at disk power-on lifetime: 6316 hours (263 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 9d 97 16 ec 40  Error: UNC 157 sectors at LBA = 0x00ec1697 = 15472279


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 34 12 ec 40 00      00:35:59.771  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:42.094  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:24.395  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:06.768  READ DMA EXT
  25 00 00 5b 6f eb 40 00      00:35:06.729  READ DMA EXT


Error 959 occurred at disk power-on lifetime: 6316 hours (263 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 9d 97 16 ec 40  Error: UNC 157 sectors at LBA = 0x00ec1697 = 15472279


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 34 12 ec 40 00      00:35:42.094  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:24.395  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:06.768  READ DMA EXT
  25 00 00 5b 6f eb 40 00      00:35:06.729  READ DMA EXT
  25 00 00 80 08 eb 40 00      00:35:06.694  READ DMA EXT


Error 958 occurred at disk power-on lifetime: 6316 hours (263 days + 4 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 9d 97 16 ec 40  Error: UNC 157 sectors at LBA = 0x00ec1697 = 15472279


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 34 12 ec 40 00      00:35:24.395  READ DMA EXT
  25 00 00 34 12 ec 40 00      00:35:06.768  READ DMA EXT
  25 00 00 5b 6f eb 40 00      00:35:06.729  READ DMA EXT
  25 00 00 80 08 eb 40 00      00:35:06.694  READ DMA EXT
  25 00 00 c6 9f ea 40 00      00:35:06.659  READ DMA EXT


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       80%      6316         446136


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

---

### Post by fanin2 on 2014-02-17
ok, so i found a dusty old hard disk somewhere, switched it with the Ubuntu hard disk, installed Windows 7, updated BIOS, and switched back to the Ubuntu hard disk and i now have a new BIOS update. i thought this would solve the hard disk errors but having Googled a bit more about those errors i found that it simply means that my hard disk will die soon and I should backup valuable data on it. i guess i'll do just that.
I saw in the:
```
[COLOR=#000000][FONT=Ubuntu Mono]smartctl -a /dev/sda[/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=Ubuntu Mono]Error 962 occurred at disk power-on lifetime: 6316 hours (263 days + 4 hours)[/FONT][/COLOR]
```
i suppose that it's dying of old age :D

---

### Post by linux4me on 2014-02-17
Even if you didn't get the hard drive problem solved, it sounds like you have figured out what you need to do, and you can still take pride in having updated the BIOS without turning your machine into an expensive brick.

---

