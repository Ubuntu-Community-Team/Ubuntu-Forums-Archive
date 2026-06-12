---
title: "Asus ZX53VW Keyboard Backlight Issue"
date: 2017-01-10
forum: New to Ubuntu
---

### Post by tyrian411 on 2017-01-10
I recently purchased an Asus ZX53VW laptop and installed Ubuntu on it.  (Link to Newegg page for specs:  [http://www.newegg.com/Product/Product.aspx?Item=N82E16834234484](http://www.newegg.com/Product/Product.aspx?Item=N82E16834234484))  Everything works fine, except I can't turn the keyboard backlight on at all.  The Fn+F3 combo should dim it, and the Fn+F4 combo should brighten it.  When I first got the laptop, I powered on Windows 10 and was able to successfully brighten/dim the keyboard backlight, so I know that the hardware is good.  However, nothing happens when I use the same key combo in Ubuntu.  

I've found several references to this problem on both AskUbuntu ([http://askubuntu.com/questions/644410/cannot-turn-on-keyboard-backlight](http://askubuntu.com/questions/644410/cannot-turn-on-keyboard-backlight)) and the Ubuntu Forums ([https://ubuntuforums.org/showthread.php?t=2185305](https://ubuntuforums.org/showthread.php?t=2185305)); however, the stated solutions don't work for me.  All of the solutions involve manipulating the variable stored in:

```

/sys/class/leds/asus::kbd_backlight/brightness

```

My system doesn't have that variable present.  Here's the listing of what's in that directory:

```

/sys/class/leds
/sys/class/leds/input4::capslock
/sys/class/leds/input7::kana
/sys/class/leds/phy0-led
/sys/class/leds/input7::capslock
/sys/class/leds/input7::scrolllock
/sys/class/leds/input7::numlock
/sys/class/leds/input4::scrolllock
/sys/class/leds/input4::numlock
/sys/class/leds/input7::compose

```

I've read that the asus::kbd_backlight entry is provided by the asus-nb-wmi module, which is loaded, according to 'lsmod | grep asus'.  The output of that is:

```

asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  2 i915_bpo,asus_wmi

```

So, the module is loaded, but it doesn't seem to supply the right entry in /sys/class/leds.  The only other thing I thought to try was this snippet from the Ubuntu Forums thread to see if the keycodes are being picked up:

```
xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'
```

I then hit Fn+F1 through Fn+F12.  Here's the output:

```

keycode 133 = (keysym 0xffeb, Super_L), state = 0x0
keycode 33 = (keysym 0x70, p), state = 0x40
keycode 121 = (keysym 0x1008ff12, XF86AudioMute), state = 0x40
keycode 121 = (keysym 0x1008ff12, XF86AudioMute), state = 0x40
keycode 122 = (keysym 0x1008ff11, XF86AudioLowerVolume), state = 0x40
keycode 122 = (keysym 0x1008ff11, XF86AudioLowerVolume), state = 0x40
keycode 123 = (keysym 0x1008ff13, XF86AudioRaiseVolume), state = 0x40
keycode 123 = (keysym 0x1008ff13, XF86AudioRaiseVolume), state = 0x40
keycode 133 = (keysym 0xffeb, Super_L), state = 0x40

```ro

Super_L is my Fn key.  Fn+F1 through Fn+F7 produces no output, Fn+F8 apparently maps to the 'p' key (which is super weird), and Fn+F9 produces no output.  The audio hotkeys are correctly bound with Fn+F10 mapping to mute, Fn+F11 mapping to volume down, and Fn+F12 mapping to volume up.  

Has anyone seen a problem like this before?

Thanks!

---

