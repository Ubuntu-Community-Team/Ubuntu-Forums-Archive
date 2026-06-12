---
title: "PS2 mouse not working"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by tobias5 on 2013-10-05
Hello,

I've got an Compaq Presario 905EA Laptop with Lubuntu. Unfortunately I can't get any PS2 mouse working (I know that they must be plugged in before booting). 

The rare thing is: A USB mouse works without any problem (although USB mice are deactivated in BIOS), I don't even have to reboot.The PS2 mice worked well with Win XP on the same computer.

Any idea? Thank you in advance.
[h=2][/h]

---

### Post by asifnaz on 2013-10-05
Paste output of

```
lspci
```

---

### Post by tobias5 on 2013-10-05
Output:
> 00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS100 Host Bridge (rev 13)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS100 AGP Bridge (rev 01)
00:02.0 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03)
00:07.0 ISA bridge: ULi Electronics Inc. M5451 PCI AC-Link Controller Audio Device (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 20)
00:0c.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
00:0f.0 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03)
00:10.0 IDE interface: ULi Electronics Inc. M5229 IDE (rev c4)
00:11.0 Bridge: ULi Electronics Inc. M7101 Power Management Controller [PMU]
00:13.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [i0HCI-Lynx]
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS100 [Radeon IGP 320M]

---

### Post by asifnaz on 2013-10-06
[COLOR=#333333][FONT=UbuntuRegular]Go to the main lens, select applications, type in "hardware" or "device". There should still be a "device manager" syle application. See if your mouse shows up there and is enabled. You could also search for "mouse". The application that allows you to adjust the mouse settings might also allow you to select which mouse you use and/or enable/disable them.[/FONT][/COLOR]

---

### Post by tobias5 on 2013-10-10
I'm sorry, but as far as I can tell, there is no such thing as a "lens" in my version of Lubuntu. I can't find any type of search mechanism. The desktop is Windows-like with a "Start menu". Apart from the installed programs I can select "System tools" or "Preferences". Moreover there is the possibility "Run", which probably executes programs I know the name of. 

There are a lot of applications as "Lubuntu Software Center" or "Synaptic Package Manager", where I can search for and install software - but not change any settings. 

"Preferences/Keyboard and Mouse" allows me to change settings for acceleration and sensitivity of the mouse. But not to enable anything.

The only thing which gets close to your suggestions is "System Tools/System Profiler and Benchmark", as far as I can tell. There I can select "Devices/Input Devices" to get a list with items as "Sleep Button", "AT Translated Set 2 keyboard" and others. All of them are of the type "keyboard", but two. One is the "Lid Switch" (Type "Unknown") and the other the "SynPS/2 Synaptics TouchPad" of Type "Mouse". No sign there of any external mouse. There is some "Device Information" provided, but I can't change any settings, either. Well, I don't know if that matters but opening "System Profiler and Benchmark" there are always appearing a lot of empty message windows, I have to close.

Do you (or someone else) have another idea? Or do you know what I maybe made wrong?

---

### Post by varunendra on 2013-10-10
> **tobias5 said:**
> The rare thing is: A USB mouse works without any problem (although USB mice are deactivated in BIOS), I don't even have to reboot.
USB devices are plug an play, and 'disabling mouse in BIOS' only disables it until an OS is loaded, after that, if the OS can detect USB devices, it'll detect and use a USB mouse too, so nothing really strange there.

However, 'Disabled in BIOS' part rings a bell to me. Have you tried with that option being 'enabled' and "Legacy USB" support enabled too (it should be somewhere in the BIOS).

> The PS2 mice **worked** well with Win XP on the same computer.
Can you confirm if the mouse still works well elsewhere?

If yes, please post the outputs of -
```
xinput
lsmod
```
..after booting with the PS/2 mouse plugged in. And in the meanwhile, try -
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse
```
It will remove the driver "psmouse" (which may disable your touchpad too, until being reloaded) and reload it. Sometimes it may help making a pointing device work if it is somehow stuck at boot time. But it must be detected in the first (must show up in "xinput").

---

### Post by elliotn on 2013-10-11
I had the same problem with ubuntu linux krrnel the I installed liquorix kernel and it worked

---

### Post by tobias5 on 2013-10-12
> However, 'Disabled in BIOS' part rings a bell to me. Have you tried with  that option being 'enabled' and "Legacy USB" support enabled too (it  should be somewhere in the BIOS).

I was talking of the "Legacy USB" support, too. I didn't describe it sufficiently, because I didn't know anything about that function and moreover my BIOS was running in another language.
Well, that doesn't matter. Enabling "Legacy USB" didn't change anything.

[SIZE=4]_**xinput**_[/SIZE]
> Virtual core pointer            id=2 [master pointer (3)]
[INDENT]- Virtual core XTEST pointer            id=4 [slave pointer (2)]
- SynPS/2 Synaptics TouchPad            id=12 [slave pointer (2)]
[/INDENT]
 Virtual core keyboard            id=3 [master keyboard (2)][INDENT]- Virtual core XTEST keyboard            id=5 [slave keyboard (3)]
- Power Button            id=6 [slave keyboard (3)]
- Sleep Button            id=7 [slave keyboard (3)]
- Video Bus            id=8 [slave keyboard (3)]
- Power Button            id=9 [slave keyboard (3)]
- Sleep Button            id=10 [slave keyboard (3)]
- AT Translated Set 2 keyboard            id=11 [slave keyboard (3)]
[/INDENT]


[SIZE=4]_**lsmod**_[/SIZE]
> 
[TABLE="width: 500"]
[TR]
[TD]Module [/TD]
[TD]Size[/TD]
[TD]Used by[/TD]
[/TR]
[TR]
[TD]dm_crypt[/TD]
[TD]22321[/TD]
[TD]1[/TD]
[/TR]
[TR]
[TD]joydev  [/TD]
[TD]17097[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]ppdev[/TD]
[TD]12817[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]bnep[/TD]
[TD]17669[/TD]
[TD]2[/TD]
[/TR]
[TR]
[TD]rfcomm[/TD]
[TD]37420[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]bluetooth [/TD]
[TD]202226[/TD]
[TD]10 bnep,rfcomm[/TD]
[/TR]
[TR]
[TD]snd_ali5451[/TD]
[TD]23183[/TD]
[TD]2[/TD]
[/TR]
[TR]
[TD]snd_ac97_codec[/TD]
[TD]105692[/TD]
[TD]1 snd_ali5451[/TD]
[/TR]
[TR]
[TD]ac97_bus[/TD]
[TD]12670[/TD]
[TD]1 snd_ac97_codec[/TD]
[/TR]
[TR]
[TD]snd_pcm[/TD]
[TD]80890[/TD]
[TD]2 snd_ac97_codec,snd_ali5451[/TD]
[/TR]
[TR]
[TD]snd_page_alloc[/TD]
[TD]14230[/TD]
[TD]1 snd_pcm[/TD]
[/TR]
[TR]
[TD]snd_seq_midi[/TD]
[TD]13132[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]snd_seq_midi_event[/TD]
[TD]14475[/TD]
[TD]1 snd_seq_midi[/TD]
[/TR]
[TR]
[TD]snd_rawmidi[/TD]
[TD]25114[/TD]
[TD]1 snd_seq_midi[/TD]
[/TR]
[TR]
[TD]powernow_k7[/TD]
[TD]13369[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]snd_seq[/TD]
[TD]51280[/TD]
[TD]2 snd_seq_midi_event,snd_seq_midi[/TD]
[/TR]
[TR]
[TD]psmouse[/TD]
[TD]81065[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]snd_seq_device[/TD]
[TD]14137[/TD]
[TD]3 snd_seq,snd_rawmidi,snd_seq_midi[/TD]
[/TR]
[TR]
[TD]snd_timer[/TD]
[TD]24411[/TD]
[TD]2 snd_pcm,snd_seq[/TD]
[/TR]
[TR]
[TD]serio_raw[/TD]
[TD]13031[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]pcmcia[/TD]
[TD]39544[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]snd[/TD]
[TD]56485[/TD]
[TD]11 snd_ac97_codec,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_ali5451[/TD]
[/TR]
[TR]
[TD]parport_pc[/TD]
[TD]27504[/TD]
[TD]1[/TD]
[/TR]
[TR]
[TD]soundcore[/TD]
[TD]12600[/TD]
[TD]1 snd[/TD]
[/TR]
[TR]
[TD]shpchp[/TD]
[TD]32129[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]yenta_socket[/TD]
[TD]27095[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]i2c_ali15x3[/TD]
[TD]12815[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]pcmcia_rsrc[/TD]
[TD]18191[/TD]
[TD]1 yenta_socket[/TD]
[/TR]
[TR]
[TD]i2c_ali1535[/TD]
[TD]12745[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]mac_hid[/TD]
[TD]13037[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]lp[/TD]
[TD]13299[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]pcmcia_core[/TD]
[TD]21505[/TD]
[TD]3 pcmcia,pcmcia_rsrc,yenta_socket[/TD]
[/TR]
[TR]
[TD]parport[/TD]
[TD]40753[/TD]
[TD]3 lp,ppdev,parport_pc[/TD]
[/TR]
[TR]
[TD]pata_acpi[/TD]
[TD]12886[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]radeon[/TD]
[TD]875105[/TD]
[TD]2[/TD]
[/TR]
[TR]
[TD]i2c_algo_bit[/TD]
[TD]13197[/TD]
[TD]1 radeon[/TD]
[/TR]
[TR]
[TD]ttm[/TD]
[TD]71289[/TD]
[TD]1 radeon[/TD]
[/TR]
[TR]
[TD]firewire_ohci[/TD]
[TD]35292[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]drm_kms_helper[/TD]
[TD]47545[/TD]
[TD]1 radeon[/TD]
[/TR]
[TR]
[TD]8139too[/TD]
[TD]23071[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]firewire_core[/TD]
[TD]61718[/TD]
[TD]1 firewire_ohci[/TD]
[/TR]
[TR]
[TD]drm[/TD]
[TD]228489[/TD]
[TD]4 ttm,drm_kms_helper,radeon[/TD]
[/TR]
[TR]
[TD]pata_ali[/TD]
[TD]13562[/TD]
[TD]2[/TD]
[/TR]
[TR]
[TD]crc_itu_t[/TD]
[TD]12627[/TD]
[TD]1 firewire_core[/TD]
[/TR]
[TR]
[TD]ati_agp[/TD]
[TD]13177[/TD]
[TD]1[/TD]
[/TR]
[TR]
[TD]video[/TD]
[TD]18894[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]8139cp[/TD]
[TD]26557[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]floppy[/TD]
[TD]55441[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]



[SIZE=4][U][B]sudo modprobe -rv psmouse
sudo modprobe -v psmouse[/B][/U][/SIZE]

Didn't change anything.

> I had the same problem with ubuntu linux krrnel the I installed liquorix kernel and it worked
I'm sorry, but I don't know anything about installing kernels. Therefore I don't understand your hint.

---

### Post by varunendra on 2013-10-12
> **tobias5 said:**
> Enabling "Legacy USB" didn't change anything.
..and it isn't detected in "xinput" either. So -
> **varunendra said:**
> Can you confirm if the mouse still works well elsewhere?

---

### Post by tobias5 on 2013-10-13
> Can you confirm if the mouse still works well elsewhere?

Yes. The mouse works perfectly with a Win Vista computer (I tried some minutes ago). Until recently I used the mouse with a Win 2000 computer. The problem can't lie with the mouse. I've already tried three different PS2 mice without sucess. Do you consider it wise to repeat these tests you posted with all of them?


_**Edit:**_ To verify if the PS2 connection is working, I plugged a PS2-keyboard in. The keyboard is working - no problem with Lubuntu. However, the "xinput"-result isn't any different. Does that information help?

---

### Post by varunendra on 2013-10-13
> **tobias5 said:**
> _**Edit:**_ To verify if the PS2 connection is working, I plugged a PS2-keyboard in. The keyboard is working - no problem with Lubuntu. **However, the "xinput"-result isn't any different**.

That would be surprising for me. It would mean that the system is able to use the keyboard without being able to 'see' it. Can you post the output of xinput when the PS2 keyboard is connected? Along with that, also the output of -
```
[s]cat /proc/[COLOR="#FF0000"]but[/COLOR]/input/devices[/s]
cat /proc/bus/input/devices
```

---

### Post by tobias5 on 2013-10-13
I tried it two more times with the keyboard plugged in. The output is the same:
> Virtual core pointer            id=2 [master pointer (3)]
[INDENT]- Virtual core XTEST pointer            id=4 [slave pointer (2)]
- SynPS/2 Synaptics TouchPad            id=12 [slave pointer (2)][/INDENT]
 Virtual core keyboard            id=3 [master keyboard (2)][INDENT]- Virtual core XTEST keyboard            id=5 [slave keyboard (3)]
- Power Button            id=6 [slave keyboard (3)]
- Sleep Button            id=7 [slave keyboard (3)]
- Video Bus            id=8 [slave keyboard (3)]
- Power Button            id=9 [slave keyboard (3)]
- Sleep Button            id=10 [slave keyboard (3)]
- AT Translated Set 2 keyboard            id=11 [slave keyboard (3)]
[/INDENT]


Well, I don't understand much of this, but: What if one of the items (e.g. AT Translated Set 2 keyboard) is the PS2 keyboard? When the PS2 mouse was plugged in, maybe the computer regarded it as a keyboard. Therefore it always was listed?

**cat /proc/but/input/devices** resulted in
> cat: /proc/but/input/devices: No such file or directory

---

### Post by varunendra on 2013-10-13
> **tobias5 said:**
> Well, I don't understand much of this, but: What if one of the items (e.g. AT Translated Set 2 keyboard) is the PS2 keyboard? When the PS2 mouse was plugged in, maybe the computer regarded it as a keyboard. Therefore it always was listed?
That must be your laptop's keyboard.
Does it work when the external one is plugged in and is working?

> **cat /proc/but/input/devices** resulted in
[QUOTE]cat: /proc/**[COLOR="#FF0000"]but[/COLOR]**/input/devices: No such file or directory[/QUOTE]
Sorry, it was a typo. The command should have been "cat /proc/**bus**/input/devices". Corrected in the original post too. Please answer the above question (do both k/b work when the external one is plugged?) and post back the above corrected command with the keyboard plugged in.

**PS:**
The 'Quote' box can not preserve the formatting of the output as you can see. You should use 'Code' box instead to post the outputs. Please follow the "Using Code Tags" link in my signature to see how.

---

### Post by tobias5 on 2013-10-13
> **varunendra said:**
> Does it work when the external one is plugged in and is working?

Yes, both keyboards are working at the same time.


**cat /proc/bus/input/devices**
```
I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=LNXSLPBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSLPBN:00/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: PROP=0
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=sysrq kbd event5 
B: PROP=0
B: EV=120013
B: KEY=4 2000000 3803078 f800d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:08/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=3e000b 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=9db1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse0 event7 
B: PROP=1
B: EV=b
B: KEY=6420 0 3000f 0 0 0 0 0 0 0 0
B: ABS=11000003

```

---

### Post by varunendra on 2013-10-13
> **tobias5 said:**
> Yes, both keyboards are working at the same time.

And was the output from when both were plugged in? If yes, then I'm afraid it's gone beyond my understanding of these things.

The /proc....devices file is saying there is only one keyboard connected to the system, while you say both are connected and both are working. The only explanation to this that I can think of is some sort of bridging between the two interfaces done internally at BIOS level. But then the behaviour should have been same for any OS, while you mentioned the mouse worked on xp.

Please do a test and let me know the result -

**1)** Boot with the external keyboard connected.

**2)** When the system is ready, type something somewhere from both keyboards to make sure both are working.

**3)** Then run the following two commands in two different terminals and keep them running -
```
tail -f /var/log/syslog
tail -f /var/log/dmesg
```

**4)** Now disconnect the external keyboard and see if any new lines appeared in either terminal. If there are any, post back the whole output of that terminal, of both if some change occurs in both of them.

You can stop the process in the terminal by pressing Ctrl+Z or by simply closing it.

---

### Post by tobias5 on 2013-10-19
I did as you said. But neither in the terminal with syslog nor in the terminal with dmesg appeared any additional line, when I unplugged the keyboard.

---

### Post by varunendra on 2013-10-19
As much as I understand about Linux (and my understanding may not be good enough), 'Any' thing that even tries to communicate with the system does register some messages in at least syslog. So no messages in syslog suggest to *me* that it is something wrong at the BIOS or hardware level.

Until the system can at least 'sense' the availability of a 'different' device, not much can be done about it from the OS. The only thing that I can suggest now is to check and fiddle with your BIOS settings, and/or try a PS2-to-USB adapter.

If anyone reading this thread has any experience or ideas about this, please share with us.

---

