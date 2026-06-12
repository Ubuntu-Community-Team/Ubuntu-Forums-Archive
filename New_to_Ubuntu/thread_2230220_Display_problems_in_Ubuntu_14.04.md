---
title: "Display problems in Ubuntu 14.04"
date: 2014-06-18
forum: New to Ubuntu
---

### Post by flyfishingphil on 2014-06-18
Just about to go crazy with this one,

Everything was fine until I reset the display to 800 x 600 and attached a projector. When finished with the slide show I tried to reset to the 1280 x 800 but cannot do so because the "APPLY" is not available at the bottom of the screen.

In the 800 x 600 screen setting the display is not taking up the whole screen and this is an HP EliteBook with a 12" (diagonal) screen.

I have gone into Applications > System Settings > Display and tried to set it to the 1280 x 800 it was on before and have tried hitting "Enter" but that doesn't work either. Sometimes, if I left click at the top of the page I can drag it up enough to see the "Apply" button but cannot get to it. As soon as I "let go" of the page it drops back down and the "Apply" button drops below the bottom of the screen. Also tried resizing the view but cannot make it any smaller.

I have done this before, to project pictures at meetings, and haven't had this happen. 

Any suggestions?

This is on an HP EliteBook with the following:

Memory: 1.8 GiB
Processor: intel core 2 duo CPU l9400 @ 1.86 GHZ x 2
Graphics: Mobile Intel GM45 express chipset
OS Type: 64 bit
Disk: 116.0 GB

Does it appear that I need to do a full format and re-install 14.04 or would it be etter to do that and go back to 12.04?

Anything I can do to make it clearer or easier to solve/correct.

Thanks for any assists.

flyfishingphil

---

### Post by rahul4557 on 2014-06-18
type this in terminal

> xrandr --output LVDS --mode 1280x800

---

### Post by flyfishingphil on 2014-06-18
Tried that but here's what I got:

ffp@ffp-HP:~$ xrandr --output LVDS --mode 1280x800
warning: output LVDS not found; ignoring

---

### Post by rahul4557 on 2014-06-18
type 

> xrandr -1

and see which interface says connected

then type

> xrandr --output <the interface name> --mode 1280x800

---

### Post by flyfishingphil on 2014-06-18
ffp@ffp-HP:~$ xrandr -1
xrandr: unrecognized option '-1'
Try 'xrandr --help' for more information.

Tried help and got this, not that I can understand it!

ffp@ffp-HP:~$ xrandr --help
usage: xrandr [options]
  where options are:
  --display <display> or -d <display>
  --help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3> 
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --current
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --scale-from <w>x<h>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [flags...]
            Valid flags: +HSync -HSync +VSync -VSync
                         +CSync -CSync CSync Interlace DoubleScan
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>
  --listproviders
  --setprovideroutputsource <prov-xid> <source-xid>
  --setprovideroffloadsink <prov-xid> <sink-xid>

Trying to figure it out and ran this:

ffp@ffp-HP:~$ xrandr -q
Screen 0: minimum 320 x 200, current 800 x 600, maximum 32767 x 32767
LVDS1 connected primary 800x600+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.2 +
   1024x768       60.0  
   800x600        60.3*    56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
TV1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

Could it be that I forgot to "eject" the VGA connection? If so, is there a way to correct that? I have the projector and could plug it back in, if needed, to do that.

YAHOOOOO!!!!! Read down thru the xrandr -q results and noted the listing of LVDS1. Tried your original recommendation, xrandr --output LVDS --mode 1280x800 but added the 1 behind the LVDS. Now have what I wanted. 

Thanks for the assist, and kicking the slipping gears into action, on this one. Didn't sleep at all trying to figure out what I had done.

This one is solved.

Thanks again for the assist.

---

