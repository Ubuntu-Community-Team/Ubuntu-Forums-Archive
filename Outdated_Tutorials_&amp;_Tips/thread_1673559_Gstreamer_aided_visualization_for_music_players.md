---
title: "Gstreamer aided visualization for music players"
date: 2011-01-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Cabalbl4 on 2011-01-22
I was always wondering how to create a player-independable visualization. Impulse screenlet is good, but I wanted to add something more. Now it looks like this (2 visualization window open):

[IMG]http://img.ii4.ru/thumbs/2011/01/22/77774_visu.png[/IMG]
[Big image]("http://img.ii4.ru/images/2011/01/22/77774_visu.png")

_How to:_

Pre-requisites:
Pulseaudio server running.
gstreamer and plugins (incl. ugly) installed (usually comes with mplayer, if I am not mistaken).
gst-launch-0.10 installed.
zenity installed (for the script to run).

At first, we need to determine the audio sources we are going to take the audio data from:
```
cabalbl4@cabalbl4-desktop:/$ pactl list|grep monitor
Monitor Source: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
Name: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
        device.class = "monitor"

```So, our source is "alsa_output.pci-0000_00_1b.0.analog-stereo.monitor".

now, we can test a visualization, in terminal window run (do not forget to change source to yours before that!):

```
gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! libvisual_bumpscope ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
```You may try to run this command without the source device mentioned, but in some cases (incl. mine) it may cause problems. However, you may try to run it:

```
gst-launch-0.10 pulsesrc ! libvisual_bumpscope ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
```"libvisual_bumpscope" from the two commands above is the name of visualization library to run. The known list of those (to me) is the following:

[B]1. libvisual_bumpscope - Bumpscope visual plugin
2. libvisual_corona - Libvisual corona plugin
3. libvisual_infinite - Infinite visual plugin
4. libvisual_jakdaw - jakdaw visual plugin
5. libvisual_jess - Jess visual plugin
6. libvisual_lv_analyzer - Libvisual analyzer plugin
7. libvisual_lv_scope - Libvisual scope plugin
8. libvisual_oinksie - Libvisual Oinksie visual plugin
9. goom - goom visualization from Rhythmbox
10. goom2k1 - goom2k1 (new version) visualization from Rhythmbox
11. monoscope - monoscope visualization from Rhythmbox[/B]

So. That's it, you may open a visualization window for any player now.

Here is a script which saves me a lot of time by asking which visualization (by number) to run. Do not forget to replace the audio source to yours as mentioned above.

```
#!/bin/bash
asked=$(zenity --entry --text='
1) libvisual_bumpscope    Bumpscope visual plugin
2) libvisual_corona    Libvisual corona plugin
3) libvisual_infinite    Infinite visual plugin
4) libvisual_jakdaw    jakdaw visual plugin
5) libvisual_jess    Jess visual plugin
6) libvisual_lv_analyzer    Libvisual analyzer plugin
7) libvisual_lv_scope    Libvisual scope plugin
8) libvisual_oinksie    Libvisual Oinksie visual plugin
9) goom
10) goom2k1
11) monoscope')
case $asked in 
"1")
gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! libvisual_bumpscope ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"2")
gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! libvisual_corona ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"3")
gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! libvisual_infinite ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"4")
gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! libvisual_jakdaw ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"5")
gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! libvisual_jess ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"6")
gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! libvisual_lv_analyzer ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"7")
gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! libvisual_lv_scope ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"8")
gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! libvisual_oinksie ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"9")
gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! goom ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"10")
gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! goom2k1 ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"11")
gst-launch-0.10 pulsesrc device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor ! monoscope     ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
*)
zenity --error --text='WRONG SELECTION!'
esac
```There should also be other plugins which can be used for gstreamer, so this article should be expanded. The script can also be improved (I am not very good with bash :( ).


This post is based on information from [B][this thread]("http://ubuntuforums.org/showthread.php?t=1193916")

_Update_[/B]: a better version of script which is easy to edit:```
[COLOR=Black]#!/bin/bash
############################
#Written by Ivan Vokhmin (Cabalbl4) i_vohmin@mail.ru
############################
monselect=$(zenity --list --width="480" --height="100" --title="Select audio monitor" \
--column="Monitor" --column="Description" \
"Custom monitor" "Set this value inside script" \
"Default monitor" "Non-specific monitor" )
echo "USING MONITOR:" $monselect
case $monselect in
"Custom monitor")
################################################
#Custom monitor goes here, change 'device=...' according to the output of pactl list|grep monitor
mymon='device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor' 
################################################
;;
"Default monitor")

mymon='' 
;;
*)

zenity --error --text='No monitor selected. Using default.'
mymon='' 
esac

asked=$(zenity --list --width="480" --height="500" --title="Select Plugin" \
--column="Num" --column="Library name" --column="Description" \
"1" "libvisual_bumpscope" "Bumpscope visual plugin" \
"2" "libvisual_corona"    "Libvisual corona plugin" \
"3" "libvisual_infinite" "Infinite visual plugin" \
"4" "libvisual_jakdaw"    "Jakdaw visual plugin" \
"5" "libvisual_jess"    "Jess visual plugin" \
"6" "libvisual_lv_analyzer" "Libvisual analyzer plugin" \
"7" "libvisual_lv_scope" "Libvisual scope plugin" \
"8" "libvisual_oinksie"    "Libvisual Oinksie visual plugin" \
"9" "goom" "goom plugin" \
"10" "goom2k1" "goom2k1 plugin" \
"11" "monoscope" "monoscope plugin" )
case $asked in 
"1")
gst-launch-0.10 pulsesrc $mymon ! libvisual_bumpscope ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"2")
gst-launch-0.10 pulsesrc $mymon  ! libvisual_corona ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"3")
gst-launch-0.10 pulsesrc $mymon  ! libvisual_infinite ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"4")
gst-launch-0.10 pulsesrc $mymon  ! libvisual_jakdaw ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"5")
gst-launch-0.10 pulsesrc $mymon  ! libvisual_jess ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"6")
gst-launch-0.10 pulsesrc $mymon ! libvisual_lv_analyzer ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"7")
gst-launch-0.10 pulsesrc $mymon  ! libvisual_lv_scope ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"8")
gst-launch-0.10 pulsesrc $mymon ! libvisual_oinksie ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"9")
gst-launch-0.10 pulsesrc $mymon  ! goom ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"10")
gst-launch-0.10 pulsesrc $mymon  ! goom2k1 ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
"11")
gst-launch-0.10 pulsesrc $mymon ! monoscope     ! ffmpegcolorspace ! xvimagesink force-aspect-ratio=false
;;
*)
zenity --error --text='Cancelled'
esac[/COLOR]
```[B] 
New ver. screenshots:
[IMG]http://journals.ru/attach/177/17656/1020066_s.jpg[/IMG] [/B]Big ver:[http://journals.ru/attach/177/17656/1020066.jpg](http://journals.ru/attach/177/17656/1020066.jpg)

[IMG]http://journals.ru/attach/177/17656/1020067_s.jpg[/IMG] Big ver.: [http://journals.ru/attach/177/17656/1020067.jpg](http://journals.ru/attach/177/17656/1020067.jpg)

---

