---
title: "Mint vs Ubuntu video tearing"
date: 2008-11-07
forum: Other OS Talk
---

### Post by L815 on 2008-11-07
I'm not sure this is the right place to post this.

In recent releases with Ubuntu, or any derivative, I have video tearing with or without compiz.

Strangely, Mint doesn't give me that issue. Although, there are problems with compiz and video (i don't care much for effects), there is no video tearing, only a slight blue background around the borders when moving the video.

Anyone know why? I'm currently looking for a distro to stick with, but Mint isn't exactly it. If i can find out the reason for this, than I should be able to find a distro that wouldn't havv the problem without having to install 1x times first.

Thanks

---

### Post by fwojciec on 2008-11-07
The difference is probably the video driver used in each of the distros -- there have been quite a few complaints about latest nvidia drivers and tearing issues, for example.

---

### Post by Zero Prime on 2008-11-07
They use the same drivers.  The difference is that all Gnome based Mint editions are based on Ubuntu Edgy and are modified to run the latest Ubuntu packages.  Being that Mint is Edgy based this may be why.

---

### Post by kjb34 on 2008-11-08
I thought Mint 5 was based on Hardy.

---

### Post by L815 on 2008-11-08
Would that mean mint is using an older xorg package? or is the intel driver managed separately from xorg?

---

### Post by Zero Prime on 2008-11-08
> **kjb34 said:**
> I thought Mint 5 was based on Hardy.
It is and isn't.

The original Mint was Edgy based.  For every new release they built upon the last release, modifying it to run the latest Ubuntu packages.  

Lets try and easier approach, LinuxMint is "based" on Hardy, but "built" on Edgy.  Does that help?

---

### Post by nitehawk777 on 2008-11-08
Well,...that may explain some things for me too!  I have an onboard Intel I815 video card thingy,....and it works fairly well in Ubuntu (except for most of the screensavers!!!!).   But Linux Mint just had a lot of that video tearing (couldn't get it to work).  I stuck in an old (yuck!) Matrox Mytique video card,.....and both Ubuntu and Mint love it!  Even the screensavers work perfectly.   And that Matrox Mytique is pretty old now.  Go figure.

---

### Post by xeriouxi on 2008-11-08
I've had tearing in Compiz since I first started using Ubuntu. Turning on the "Sync To VBlank" option in CCSM eliminates the tearing for me, but you can notice the heavy hit on the frame rate when spinning the cube, for example.

---

### Post by xArv3nx on 2008-11-08
> **Zero Prime said:**
> It is and isn't.

The original Mint was Edgy based.  For every new release they built upon the last release, modifying it to run the latest Ubuntu packages.  

Lets try and easier approach, LinuxMint is "based" on Hardy, but "built" on Edgy.  **Does that help?**
Not really, I know where you're getting that from, though. Why couldn't Clem just say it was based on Hardy? :|

He didn't have to get all complicated with it.

---

### Post by wolfen69 on 2008-11-08
> **L815 said:**
> I'm not sure this is the right place to post this.

In recent releases with Ubuntu, or any derivative, I have video tearing with or without compiz.

Strangely, Mint doesn't give me that issue. Although, there are problems with compiz and video (i don't care much for effects), there is no video tearing, only a slight blue background around the borders when moving the video.

Anyone know why? I'm currently looking for a distro to stick with, but Mint isn't exactly it. If i can find out the reason for this, than I should be able to find a distro that wouldn't havv the problem without having to install 1x times first.

Thanks

there is a chance that your video card is less than perfect. software isn't the only thing that can have problems. i fix computers and see hardware issues all the time.

---

### Post by Zero Prime on 2008-11-08
> **xArv3nx said:**
> Not really, I know where you're getting that from, though. Why couldn't Clem just say it was based on Hardy? :|

He didn't have to get all complicated with it.
He has, in very many posts.  It would just take a while to find them.  There have been numerous questions on this in the past on their forum.

---

### Post by lovinglinux on 2008-11-09
I'm also trying to solve the tearing issue. I tried Mandriva 2009 on my machine and it doesn't suffer from tearing. So, I guess is not my hardware, but Ubuntu itself.

EDIT: I finally solved the problem on my machine by enabling "Unredirect Fullscreen Windows" under CCSM General options:popcorn:

---

### Post by lovinglinux on 2008-11-12
> **lovinglinux said:**
> I finally solved the problem on my machine by enabling "Unredirect Fullscreen Windows" under CCSM General options

The fix above wasn't very stable. Sometimes it worked, sometimes not.

Now it seems to be solved by setting the Device in gstreamer-settings to "NV05 Video Blitter"

---

### Post by L815 on 2008-11-13
The problem exists with or without compiz. It is a driver issue.
I have found a solution that works temporarily.
You have to use VLC, and set it to use xVideo, and in the settings xVideo has an option of -1, set it to 1 and it works without tearing.

But the problem still remains everywhere else. I'm hoping a solution comes fast!

---

### Post by Cresho on 2008-11-13
There is no video tearing at all if you have your compiz config manager fixed properly...well in my case, it runs fine.

HERE IS THE DEAL

in compizconfig settings manager, you must use these settings.

Texture Filter "best"  if you have it fast, video tears.
detect refresh rate "OFF"
Lighting "on"
Refresh rate "200"
sync to vblank "on"
detect outputs "on"

remove all outputs.

overlapping output "smart mode"

anyway, keep your texture filter at best since this greatly affects the video refresh and tearing.

---

### Post by L815 on 2008-11-13
> **Cresho said:**
> There is no video tearing at all if you have your compiz config manager fixed properly...well in my case, it runs fine.

HERE IS THE DEAL

in compizconfig settings manager, you must use these settings.

Texture Filter "best"  if you have it fast, video tears.
detect refresh rate "OFF"
Lighting "on"
Refresh rate "200"
sync to vblank "on"
detect outputs "on"

remove all outputs.

overlapping output "smart mode"

anyway, keep your texture filter at best since this greatly affects the video refresh and tearing.

I'll give this a shot.
Thanks.

---

### Post by lovinglinux on 2008-11-13
> **Cresho said:**
> There is no video tearing at all if you have your compiz config manager fixed properly...well in my case, it runs fine.

I guess this varies from machine to machine, because here doesn't work. The only reliable "fix" I have found so far is to disable compiz.

---

### Post by Cresho on 2008-11-13
your other problem could be refresh rate is not correctly set for monitor.

---

### Post by lovinglinux on 2008-11-13
> **Cresho said:**
> your other problem could be refresh rate is not correctly set for monitor.

Nope. I did exactly as you suggested, unless your talking about refresh rate in other place rather than CCSM.

---

### Post by keypox on 2008-11-23
> **Cresho said:**
> There is no video tearing at all if you have your compiz config manager fixed properly...well in my case, it runs fine.

HERE IS THE DEAL

in compizconfig settings manager, you must use these settings.

Texture Filter "best"  if you have it fast, video tears.
detect refresh rate "OFF"
Lighting "on"
Refresh rate "200"
sync to vblank "on"
detect outputs "on"

remove all outputs.

overlapping output "smart mode"

anyway, keep your texture filter at best since this greatly affects the video refresh and tearing.

Tried your settings didnt work for me still have tearing in vlc... other people have posted similar settings with no luck for me.  Im running 8.10 with 8.11 ati drivers

---

### Post by simpsonatwork on 2008-11-27
The tearing appears for me when AA is set higher than 4x.

---

### Post by Cresho on 2008-11-27
> **simpsonatwork said:**
> The tearing appears for me when AA is set higher than 4x.

i forgot about those.  i have to have it at 0 or disabled in order for me to view videos without tearing.

---

### Post by fuzzmo on 2008-11-28
> **Cresho said:**
> There is no video tearing at all if you have your compiz config manager fixed properly...well in my case, it runs fine.

HERE IS THE DEAL

in compizconfig settings manager, you must use these settings.

Texture Filter "best"  if you have it fast, video tears.
detect refresh rate "OFF"
Lighting "on"
Refresh rate "200"
sync to vblank "on"
detect outputs "on"

remove all outputs.

overlapping output "smart mode"

anyway, keep your texture filter at best since this greatly affects the video refresh and tearing.

Nice - this seems to have solved my problems at least (well in the quick tests I did with VLC).  Will give it extensive testing later.  I reckon your mileage will vary depending on card etc....

---

### Post by L815 on 2008-11-28
> **simpsonatwork said:**
> The tearing appears for me when AA is set higher than 4x.


What is AA?

---

### Post by lovinglinux on 2008-11-28
> **L815 said:**
> What is AA?

[[COLOR="Red"]**Anti-Aliasing **[/COLOR]]("http://en.wikipedia.org/wiki/Anti-Aliasing")

---

### Post by L815 on 2008-11-30
> **lovinglinux said:**
> [[COLOR="Red"]**Anti-Aliasing **[/COLOR]]("http://en.wikipedia.org/wiki/Anti-Aliasing")

Where can I set this option to 0?

---

### Post by Cresho on 2008-11-30
sudo apt-get install nvidia-settings, and in antialiasing settings, set to "use application settings" "compiz uses" and anisotropic setting 0, texture quality leave alone to no check.

But you are not using nvidia.

---

### Post by L815 on 2008-11-30
Yeah, unfortuneatly :/ Is it possible with Intel graphics? 
I'd like to try everything possible before giving up.

---

### Post by Cresho on 2008-12-01
try under video, sync to refresh or anything related to sync.

---

### Post by screaminj3sus on 2008-12-01
> **xeriouxi said:**
> I've had tearing in Compiz since I first started using Ubuntu. Turning on the "Sync To VBlank" option in CCSM eliminates the tearing for me, but you can notice the heavy hit on the frame rate when spinning the cube, for example.

sync to vblank has never worked for me on any video card/ driver/ cf version it's ridiculous.

I'v had plent of ati and nvidia cards and it has never worked. Which is defeating one of the major advantages of having a 3d desktop in the first place- to eliminate tearing.

---

### Post by L815 on 2008-12-02
I agree. Why spend so much effort on compiz and 3d effects if you can't get rid of video tearing first >.<

I wouldn't mind having to deal with no-3d if the drivers worked like they did a few releases back. But not, if I add the work around to xorg.conf, the screen flashes a lot when playing video, and there are too many artifacts between applications.

I am patient though, I'm sure someone is working on fixing it ):P

---

### Post by UnrealMiniMe on 2008-12-15
> **keypox said:**
> Tried your settings didnt work for me still have tearing in vlc... other people have posted similar settings with no luck for me.  Im running 8.10 with 8.11 ati drivers

Have you tried restarting X after changing the Compiz settings?

I have a dual-monitor setup with different refresh rates (actually a monitor and a TV) running nvidia Twinview, AND I'm running Compiz, so I have a particularly difficult setup.  For the longest time, I couldn't eliminate tearing no matter what settings I chose for vsync in nvidia-settings (you might have some different driver difficulties from mine though, since you're using ATI).  I read about the CCSM tweaks in another thread yesterday, so I decided to try them:
I installed and opened CCSM, went to General Options, the Display Settings tab, put a checkmark next to "Sync to VBlank," and changed "Refresh Rate" to 200*.  I also kept "Detect Refresh Rate" checked, since the post I read didn't mention anything about that.

At first, nothing changed.  I was still getting tearing like crazy whenever I moved the windows and especially whenever I watched any videos.  However, after I restarted X, the new Compiz settings seemed to take effect, because vsync started working...**regardless** of how I had it set in nvidia-settings!  Apparently, the Compiz vsync setting is taking precedence over the driver settings for some odd reason.  Anyway, my TV has a refresh rate of 60hz, and I'm getting absolutely no tearing with it now whatsoever.  My computer monitor has an odd refresh rate of 59.95hz, so I'm getting a single tearing line that takes twenty seconds to move from the bottom to the top of the screen, but nothing else (because an additional 5% of the screen is drawn with the "next" frame every second, relative to the frame that started to be drawn at the top).  I don't think that can be avoided unless either Compiz or my driver vsyncs to both displays separately, and it's not a big deal...**but anyway, in case the situation is the same with ATI cards, I would try to turn on vsync in the Compiz settings and then restart X (ctrl+alt+backspace).  Good luck!**

*Actually, I also changed the Compiz "Refresh Rate" setting from 200 to 120 and it's still working fine.  I imagine vsync would still work now regardless of the Compiz "Refresh Rate" setting, though the framerate would suffer if Compiz wasn't reliably refreshed as quickly as my displays.

---

### Post by Roasted on 2009-01-28
Any update in this department, folks? I'm running a 9600GT by Nvidia with 177 drivers. I'm running 8.10 64 bit. I have tried everything I could think of... disable compiz, changed my VLC settings to -1 +1 or whatever that one tricky fix is, tried X11 as my video output for VLC, etc etc... nothing works.

I'd at least like to hear more information about this problem.

Is it Ubuntu's fault?
Is it Nvidia's fault? Well I guess it can't be since ATI users are experiencing issues...
Is it a driver issue?
Is it something that is being worked on?

I'd just like to hear more about this issues, and maybe anymore fixes I haven't tried yet... anybody have anything?

---

### Post by Cresho on 2009-01-29
launch nvidia-settings in terminal.  if it isnt in your system, install it by sudo apt-get install nvidia-settings


go to x server xvideo settings.  "sync to vblank."  and in opengl, do the same.  this will work with compiz off.  if you need to fix it with compiz fusion, you will need to install advanced desktop effects and change mhz to 200 refresh rate, disable detect refresh and texture filter"this one fixes video tear" to best. sync to vblank on and leavecheck detect outputs alone or you'll be viewing 640x480 res.

---

### Post by Roasted on 2009-01-29
I already tried the sync to vblank setting, but I will give the rest a shot when I get home.

Sounds a little ridiculous to have to do all that to get video working half decently again. :(

---

### Post by NESFreak on 2009-02-04
for me on my 8400M with the 180.22 drivers it sums up to the following:
forced AA (in the nvidia drivers) + ANY compositing window manager = video tearing.

Since most Linux opengl applications don't allow you to even enable AA, turning this off isn't an option. So i turned off compiz.

So until compositing windowmanagers start to support AA, this remains unfixed. (well actually just guessing, I'm not in anyway involved in the development of either compiz nor the video drivers)

On windows machines your able to force anti aliasing on a per application basis. Has this got a Linux equivalent?

---

### Post by Cresho on 2009-02-04
aa is allowed if you know how to work with it


i forgot to mention that you need to have "allow flipping" disabled in opengl of nvidia graphics.

also in sessions, add this


nvidia-settings --load-config-only


one last thing.  the trick to getting aa to work is to disable it in the themes manager and having it mannually start about 12-20 seconds after boot.  the nvidia-settings load config will load in sessions and you now have aa.

also, if you do any configuration while compiz is running, compiz needs a restart.

aa does work and I have no video tearing.  just remove "allow flip"  if you followed the directions i posted before here for compiz config manager, this is where the refresh rate is really controlled besides nvidia's drivers.  You have about 3 variables controlling what you see 0n the screen

---

### Post by Roasted on 2009-02-04
Is there a way to install 180.22 drivers without completely borking your system?

I installed them via Nvidia's instructions and completely screwed up my graphics settings. Two days of solid googling and many stumped Ubuntu enthusiasts later I did a fresh install. Thankfully I left my home directory on another partition so I didn't even lose a thing!

---

### Post by Cresho on 2009-02-04
> **Roasted said:**
> Is there a way to install 180.22 drivers without completely borking your system?

I installed them via Nvidia's instructions and completely screwed up my graphics settings. Two days of solid googling and many stumped Ubuntu enthusiasts later I did a fresh install. Thankfully I left my home directory on another partition so I didn't even lose a thing!

You guys are so crazy.  just tarball the root directory and keep the home.  in a fresh install, rename your username to username-backup, after install do not exit and then rename your old username to the new one after deleting the new one, then you sudo untar your root files over the root directory leaving ubuntu intact as if nothing ever happened.  It is just the best.  when i decide to screw up my system by installing stuff, i do it after a backup and then i pop in my boot cd and work with the live cd.  search for that command line thingy.  nothing beats it!\

install the regular nvidia drivers via the restricted drivers in admin..it works fine.

---

### Post by NESFreak on 2009-02-05
> **Cresho said:**
> aa is allowed if you know how to work with it


i forgot to mention that you need to have "allow flipping" disabled in opengl of nvidia graphics.


you know, that actually improved it a lot. Thanks. What does 'flipping' do anyway?

---

### Post by L815 on 2009-02-05
Any intel solutions yet?

---

### Post by elkanguro on 2009-02-15
I have the same issue with ATI card:(

---

