---
title: "Dual monitor setup on Ubuntu 12.04"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by jnedenrod on 2012-08-09
I want my computer monitor to be on the left, tv on the right.  I want new new windows and apps  to load to the left screen.  Right now, those are working fine.

Here's what's not happening right now:
When I'm in Firefox and click fullscreen for a video, I want it to go fullscreen on the monitor that it's on.  So, if I have a video on the computer monitor and click fullscreen, it should go fullscreen on the computer monitor.  If on the tv screen, it should go fullscreen on the tv. Instead, no matter what monitor the web browser is on, it always goes to the computer screen.  When I'm in MoviePlayer and click fullscreen, it stays on its monitor as it should.

The following link is why I went to Terminal and entered this: gedit ~/.config/monitors.xml

[http://askubuntu.com/questions/80763/how-can-i-force-fullscreen-on-my-right-screen/81016#81016](http://askubuntu.com/questions/80763/how-can-i-force-fullscreen-on-my-right-screen/81016#81016)

I'm confused about the outputs and what they mean-- LVDS, DFT1, and CRT1. LVDS=laptop video display? CRT1= cathode ray tube (my tv)? DFT???
Note that I just rebooted with the TV still attached via HDMI.


Here are my current settings in gedit ~/.config/monitors.xml :


<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="LVDS">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1280</width>
          <height>720</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
      <output name="DFP1">
          <vendor>SNY</vendor>
          <product>0x01f8</product>
          <serial>0x01010101</serial>
          <width>1280</width>
          <height>720</height>
          <rate>60</rate>
          <x>1280</x>
          <y>20</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="CRT1">
      </output>
  </configuration>
</monitors>

---

### Post by jnedenrod on 2012-08-09
Okay, now I'm REALLY confused. Some videos in Firefox will fullscreen in their own monitor, others always go to the laptop monitor.

Your mouse pointer should tell you which X to click to close the ads in front of the video.  If you click the wrong one, you'll get a pop-up or new tab with ads.  Don't install any software from these links:

Correctly opens on own monitor:
[http://www.usagoals.com/live/167024-nfl-green-bay-packers-vs-san-diego-chargers/watch/stream/online/free/feed/p2p/en/vivo/tv/gratis/](http://www.usagoals.com/live/167024-nfl-green-bay-packers-vs-san-diego-chargers/watch/stream/online/free/feed/p2p/en/vivo/tv/gratis/)

Always goes to Primary (laptop) monitor:
[http://www.usagoals.com/live/166758-nfl-network/watch/stream/online/free/feed/p2p/en/vivo/tv/gratis/](http://www.usagoals.com/live/166758-nfl-network/watch/stream/online/free/feed/p2p/en/vivo/tv/gratis/)

---

### Post by jnedenrod on 2012-08-09
I've tried to fix this myself for the last month or so.  It'd be nice if someone would frickin' help.  Is this the cause?  Does the following info and coding help anyone to figure out a solution?

[https://developer.mozilla.org/en-US/docs/DOM/Using_full-screen_mode](https://developer.mozilla.org/en-US/docs/DOM/Using_full-screen_mode)

---

