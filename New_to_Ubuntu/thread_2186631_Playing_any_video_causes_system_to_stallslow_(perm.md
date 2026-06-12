---
title: "Playing any video causes system to stall/slow (permanently)"
date: 2013-11-08
forum: New to Ubuntu
---

### Post by mivadar on 2013-11-08
Can someone suggest a solution for this?

I have lubuntu 13.10 running on a fairly high spec laptop (Intel Core i7-4750HQ + Intel Iris Pro Graphics 5200).

If I try to play a video of any format (tried flv, mp4, divx avi, ogv), on any video player (I tried VLC, xine, GMplayer), the video starts and plays ridiculously slowly, skipping frames - unwatchable. The whole system also lags - other windows take for ever to open, if I try to open a terminal to kill the video player it takes about five minutes to open LXterm.
I turn off the player, and the system stays very, very slow (though faster then when it was running). Normal tasks (like opening windows, saving short documents, etc.) that usually take a fraction of a second take several seconds to a minute, until the next reboot when everything goes back to normal.
I checked the CPU and RAM usage - both during the attempted video playback, and after, both CPU and memory are utilized under 5% - the system should not be slow.

(And it definitely has the juice to play a short flv video in any case. Just out of curiosity, I tried playing a video inside a VirtualBox+WinXP I have installed, which is limited to 1 GB RAM and 1 CPU to use out of the 4 cores - works fine.)

Everything else seems to work.

I don't know what else to post here except this rather vague description.
There are no error messages, nothing crashes as such, everything starts as normal, no missing codec messages, etc.
Please ask me for details if You have any idea where to look / what to look for to pin the problem down.

Thank You!

---

### Post by TheFu on 2013-11-08
What do the system log files say?
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

---

### Post by mivadar on 2013-11-09
Thank You for the suggestion.
I have not found anything particularly enlightening in the logs:

VLC:
:~$ vlc -v
VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
[0x178a108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x7fdf6cc03348] avcodec decoder warning: disabling direct rendering
[0x7fdf88c09168] main audio output warning: PTS is out of range (-9978), dropping buffer
[0x7fdf88c09168] main audio output warning: PTS is out of range (-33918), dropping buffer
[0x7fdf88c09168] pulse audio output warning: starting late (-15623 us)
[0x7fdf88c09168] pulse audio output warning: too early by 55841 us
[0x7fdf88c09168] pulse audio output warning: too early by 55591 us
[0x7fdf88c09168] pulse audio output warning: too early by 55158 us
[0x7fdf88c09168] pulse audio output warning: too early by 52588 us
[0x7fdf88c09168] pulse audio output warning: too early by 52547 us
[0x7fdf88c09168] pulse audio output warning: too early by 52126 us
[0x7fdf88c09168] pulse audio output warning: too early by 51783 us
[0x7fdf88c09168] pulse audio output warning: too early by 51020 us
[0x7fdf88c09168] pulse audio output warning: too early by 49918 us
[0x7fdf88c09168] pulse audio output warning: too early by 45884 us
[0x7fdf64001238] main video output warning: picture is too late to be displayed (missing 1254 ms)
[0x7fdf64001238] main video output warning: picture is too late to be displayed (missing 1212 ms)

Then I thought maybe it's the disabled direct rendering that's the problem - so I went around it:

:~$ vlc -v --noffmpeg-dr
VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)
[0x8f9108] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x7f46a4000b78] pulse audio output warning: starting late (-34983 us)
[0x7f46a4000b78] pulse audio output warning: too early by 49796 us
[0x7f46a4000b78] pulse audio output  warning: too early by 49629 us
[0x7f46a4000b78] pulse audio output warning: too early by 40345 us
[0x7f469c2f3038] main video output warning: picture is too late to be displayed (missing 3991 ms)
[0x7f469c2f3038] main video output warning: picture is too late to be displayed (missing 3949 ms)
[0x7f469c2f3038] main video output warning: picture is too late to be displayed (missing 3908 ms)
[0x7f469c2f3038] main video output warning: picture is too late to be displayed (missing 3866 ms)
[0x7f469c2f3038] main video output warning: picture is too late to be displayed (missing 3824 ms)
[0x7f469c2f3038] main video output warning: picture is too late to be displayed (missing 3783 ms)
[0x7f469c2f3038] main video output warning: picture is too late to be displayed (missing 3741 ms)

etc. 

I searched the system logs as suggested, no 'error' or 'warning'.
Should I attach a particular log file? (Xorg, or anything else?)

Still no idea what's happening.

---

### Post by mivadar on 2013-11-09
Incidentally - I checked my VGA controller, in case there is a memory allocation problem - again no joy:

:~$ lspci -v -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation Crystal Well Integrated Graphics Controller (rev 08) (prog-if 00 [VGA controller])
	Subsystem: CLEVO/KAPOK Computer Device 7410
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915

---

