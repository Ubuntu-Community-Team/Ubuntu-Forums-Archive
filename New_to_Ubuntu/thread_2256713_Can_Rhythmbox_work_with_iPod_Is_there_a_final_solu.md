---
title: "Can Rhythmbox work with iPod? Is there a final solution?"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by avishek2 on 2014-12-14
Just started using Ubuntu 14.04 LTS, have also installed the latest Rhythmbox (rhythmbox 3.1.0-1~ppafossfreedom).

But can't get my ipod to play the music! The music is there on the ipod but doesn't show up in the Rhythmbox GUI and on clicking "Sync" Rhythmbox crashes.

Have gone through several resources (Bug 131430, Bug 1132215, etc.) nothing works!

Maybe it is my iPod, here is the SysInfoExtended

```
<plist version="1.0"><dict><key>AppleDRMVersion</key><dict><key>Minimum</key><integer>0</integer><key>Maximum</key><integer>4</integer></dict><key>AudioCodecs</key><dict><key>MP3</key><dict><key>Mono</key><true/><key>Stereo</key><true/><key>MaximumSampleRate</key><integer>48000</integer><key>MaximumDataRate</key><integer>320</integer></dict><key>WAV</key><dict><key>Mono</key><true/><key>Stereo</key><true/><key>Multichannel</key><false/><key>MaximumSampleRate</key><integer>48000</integer><key>MaximumBitDepth</key><integer>16</integer></dict><key>AIFF</key><dict><key>Mono</key><true/><key>Stereo</key><true/><key>Multichannel</key><false/><key>MaximumSampleRate</key><integer>48000</integer><key>MaximumBitDepth</key><integer>16</integer></dict><key>AAC</key><dict><key>AppleDRM</key><true/><key>MaximumSampleRate</key><integer>48000</integer><key>LC</key><dict><key>VariableBitRate</key><true/><key>PerceptualNoiseSubsitution</key><true/></dict></dict><key>Audible</key><dict><key>Type1</key><false/><key>Type2</key><true/><key>Type3</key><true/><key>Type4</key><true/></dict></dict><key>BuildID</key><string>1.0.4</string><key>ConnectedBus</key><string>USB</string><key>MaxTransferSpeed</key><integer>61440</integer><key>FamilyID</key><integer>130</integer><key>FireWireGUID</key><string>000A27001C6672E8</string><key>FireWireVersion</key><string>2.70</string><key>MinITunesVersion</key><string>7.2</string><key>SerialNumber</key><string>4H848K80YX6     </string><key>UpdaterFamilyID</key><integer>133</integer><key>UpdateMethod</key><integer>2</integer><key>VisibleBuildID</key><string>1.0.4</string><key>OEMID</key><integer>0</integer><key>OEMV</key><integer>12</integer><key>NumMBytes</key><integer>1024</integer><key>NumSongs</key><integer>0240</integer><key>PowerInformation</key><dict><key>WillFlash</key><true/><key>USB</key><true/><key>FireWire</key><false/></dict><key>VoiceMemosSupported</key><false/><key>iCalendarsSupported</key><false/><key>vCardsSupported</key><false/><key>AutoRebootAfterFirmwareUpdate</key><true/><key>VolumeFormat</key><string>FAT32</string><key>ShadowDB</key><true/><key>ShowFlashUI</key><true/><key>SupportsSoundCheck</key><true/><key>SupportsVolumeLimit</key><true/><key>BangFolder</key><false/></dict></plist>

```

Any help will be much appreciated!

Thanks!

---

### Post by DuckHook on 2014-12-14
Rhythmbox and iPods/iPhones = oil and water.

In my experience, the behaviour changes sometimes almost monthly depending on updates. My theory is that Apple purposefully breaks third-party access in order to protect their jail. Gnome is therefore constantly playing catch-up in addition to the already difficult process of building drivers for which the manufacturer refuses to cooperate much less release HW info. I've tried numerous solutions and finally gave up and installed iTunes on Windows running in a VM. Three months ago, I enacted a more elegant solution by putting all of my music on a new Android phone and retiring the iPhone. Nirvana.

If you simply must use Apple's jailware, then my suggestion is the iTunes in Windows in a VM workaround, as the most painless. Yes, it is not an elegant solution, and on older machines, it runs like a pig, but you are at least using the Apple siloware that is designed for their jail.

---

### Post by andrew.46 on 2014-12-19
I guess it depends on your ipod. I have an ipod classic and it works just fine with gtkpod but later ipods can be hit or miss :(.

---

