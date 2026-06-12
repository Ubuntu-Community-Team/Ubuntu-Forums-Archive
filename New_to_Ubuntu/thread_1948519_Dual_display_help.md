---
title: "Dual display help"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by t3ddyg on 2012-03-28
I use Geforce 210 with dual displays - regular pc monitor + 42" tv (for occasional htpc/xbmc duties). I read a bunch of tutorials, installed nvidia 295.20, and configured dual display with nvidia control panel. It works fine with both displays turned on and desktop extended across both displays. But I don't always want both displays turned on, and I don't ever use extended desktop (my displays aren't side-by-side).

Desired config: 
I want to use my PC monitor as single/primary monitor when the TV is off/unplugged. When the TV is on, I want the TV to be the primary display (so XBMC will display fullscreen on it).

Previous example of how it worked on Windows 7:
Desktop was extended across both displays, with TV as primary. When I wanted to use my PC monitor, I would simply unplug the HDMI from the TV. Then the pc monitor would switch to primary display on the fly. When I wanted to watch XBMC, I would replug the hdmi into the TV - and the tv would become the primary display automatically.

Is this possible? Is there a 'better' way to achieve this? Thanks for your advice.:confused:

Addtl info: 
Ubuntu 11.10 x64
Geforce 210

---

### Post by t3ddyg on 2012-03-30
Hate to bump... but does anyone have any advice? Thanks

---

### Post by skatinjj on 2012-03-30
I have to ask since you do not mention it, did you unplug the HDMI cable from the TV when using linux like you did for Windows 7?

---

### Post by cortman on 2012-03-30
Your TV is plugged into HDMI... what is your standard monitor plugged into?

---

### Post by t3ddyg on 2012-04-01
> **skatinjj said:**
> I have to ask since you do not mention it, did you unplug the HDMI cable from the TV when using linux like you did for Windows 7?
Yes

> **cortman said:**
> Your TV is plugged into HDMI... what is your standard monitor plugged into?
TV = HDMI
Monitor = VGA

I did some more testing, and took some notes:
**Seperate X Screen mode**
HDMI (TV) is primary, and works fine with all the desktop icons etc displayed. Programs opened properly on screen. My Monitor (VGA) shows the desktop background, but has no functionality. I can't drag apps to it. The mouse cursor displays as a black "X" when moved over to this screen. When I right click, the menu doesn't even pop up. XBMC opens in full screen mode, displays properly on HDMI(TV).

**Twinview Mode**
HDMI (TV) is primary, and works fine with all the desktop icons etc displayed. Programs opened properly on screen. Monitor (vga) also works properly. Programs can be dragged between both spaces. XBMC opens in full screen mode, and is stretched across both displays.

If I unplug the hdmi from the tv, the monitor (VGA) remains a secondary display, and does not automatically switch to my primary display with desktop icons etc like happened on windows. If I restart with my HDMI unplugged (TV), and only Monitor (VGA) connected, the monitor is primary. It displays all my desktop icons and shortcuts. However, there is no mouse cursor on screen. If i right click, it does display the right click options, however there is still no cursor anywhere on screen.

---------------
Is there any advice on how to get this working? Ideally I could do twinview - XBMC would open in fullscreen on HDMI (TV) only, not stretched across both displays. Then when I pulled the HDMI out of the tv, or turned off the tv - the monitor (VGA) would become the primary display, and mouse cursor would display/work properly without having to restart.

Thanks:confused:

---

### Post by t3ddyg on 2012-04-01
So.. i think i'm dealing with a 2 part problem here. I discovered this thread: [http://ubuntuforums.org/showthread.php?t=1041308](http://ubuntuforums.org/showthread.php?t=1041308)

This is precisely the way I'm configured right now. HDTV (1920x1080) on the left, and LCD monitor (1680x1050) on the right. When I try to set my LCD monitor as primary display, it doesn't show the desktop icons/shortcuts at all.

Secondly, it looks like Ubuntu can't autodetect and switch profiles when plugging/unplugging the hdmi cable. Some people do mention that you can setup a keyboard shortcut though, that will switch profiles. That way I can switch profiles when I want to watch XBMC on my HDTV. There is a workaround mentioned here:
[http://askubuntu.com/questions/7292/is-there-a-way-to-autodetect-when-a-display-is-disconnected](http://askubuntu.com/questions/7292/is-there-a-way-to-autodetect-when-a-display-is-disconnected)

---------------

Bottom line - this multidisplay is a mess it seems. Sucks, but I don't know if there is a way to fix this. I'll try the profile shortcut work around with disper program. As far as the other problem with bigger resolution, secondary monitor on the left, ....it seems to be the same problem for years now. I don't know what the heck to do about that one.

---

### Post by cortman on 2012-04-02
What I did was write a little script that ran on startup. If it detected the HDMI plugged in, it automatically switched it to primary. If not, the laptop remained primary.
If you're plugging/unplugging your monitor in all the time while Ubuntu is running, you should just assign a hotkey to said script to be able to toggle back and forth. I can find and post the script if you're interested.

---

### Post by t3ddyg on 2012-04-07
> **cortman said:**
> I can find and post the script if you're interested.

I'm willing to give anything a shot at this point. Please let me know. Thanks!

---

### Post by cortman on 2012-04-07
The script is available [here.]("http://cortman.wordpress.com/wp-admin/post.php?post=46&action=edit&message=6&postpost=v2") Any questions, feel free to re-post.

---

