---
title: "Why why why does Ubuntu hate blazing-fast refresh rate monitors?"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by eriktilton on 2013-07-19
):P First of all I would like to thank everyone who uses and contributes to Ubuntu for making it so popular and stable. I predict that in a few years there will be no reason to use any other OS.

This topic is going to sound negative, strange, and fault-finding but it's from the heart and I really would like to see the following improvements. I think it would help Ubuntu / other Linux distributions in a big way and help bring PC gamers and other PC enthusiasts over on our side.

I predict this is going to turn into a novel-length post so please bear with me, save it into your bookmarks to peruse at your leisure. It's going to be the most stimulating manifesto you've ever read in a long-long time. Once again it's from the heart.

OK so I've come from Windows XP which I had discontinued around 2010 because spyware is a pain and so is being addicted to online games. I was also going back to school and felt that I needed to redirect my focus and concentration towards what's really important in life: bettering myself. So I bought a laptop (HP Mini which is very nice and light, excellent battery) and put Ubuntu on it. Life was good and I was able to do my studies.

Now I've graduated and we're in 2013. I give my HP Mini to my GF **and get my massive PC out of storage** --

It has the following "specs":
- 17" Diamondtron CRT Monitor
- Model M Keyboard
- Intellimouse and Steelseries Mat
- Sennheiser Headphones

I dust it off, uninstall XP and put Ubuntu in instead. "Life is going to be sooo cool." I remembered how great it was in XP when I figured out how to remove pointer acceleration, overclocked the mouse to 1000Hz input, and ran the monitor at **800x600@160Hz,** blazing through Call of Duty 4 and other games so well that I was kicked from almost every server because I could hit people before they could see me coming around the corner.

**800x600@160Hz**
My mouth salivates when I think about a monitor possessing the ability to flicker me pictures at 160 frames per second, so smoothly that my eyes would blend everything into a smooth blur and giving me such ample opportunity to blast opponents with a shotgun in Shipment, or hip-fire an MP5 at the very first sign of trouble.

You must think I'm nuts by now.

So I load up Ubuntu and start tweaking. I cleverly create a **50-mouse-acceleration.conf** file in **/usr/share/X11/xorg.conf.d**. I'm on a roll! Can I keep up at this momentum? I go online and learn about 

**Xrandr**

OK so I try it and Xrandr **doesn't work** to get me 800x600@160Hz, for some reason. *60-85Hz* is the max. Let me try

**Xorg**

I put in some monitor-related stuff and screw up my computer.
Time to reinstall Ubuntu! Ohh well.

**Let me try Nvidia X Server Settings**

Huh! The highest refresh rate it'll let me do is 100Hz @ 1152x864. Everything else is between 60-85Hz. Hmm OK I guess, I can live with **1152x864@100Hz**.

But I really really really *like* **800x600@160Hz**! And *1152x864@100Hz doesn't stick*, when I restart the computer it goes to 75Hz :(.
So let me see if I can get Ubuntu to fetch my monitor EDID with **edid-decode**.

Is "fetch" even the right word? I don't know.

Edid-decode doesn't work. Let me try **get-edid**.

[I]"The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID"[/I]

adghopdsjfg
sd

What I would eventually like to do is be able to use **800x600@160Hz** in Ubuntu. This will allow me to play games from Ubuntu and get kicked from servers like I used to in XP. Because being at the top of the scoreboard all the time is [fun]("http://www.youtube.com/watch?v=OioBbQOpptI&feature=PlayList&index=0&list=PL68A45E0C2E95C5CD").

I would also like to somehow check to see if I truly have **1000Hz mouse inputs** (AKA mouse polling), because the only indication I have of having that is in **CompizConfig Settings Manager** that I have **1ms** response time (which is 1000 Hz). Is there a program where I can "see" this? Like in MS Paint on XP you could swing the spray paint brush and see all the "sprays" alongside each other and see a big difference between the 125 Hz default and the 1000 Hz.

So what do you think? Don't tell me everything I wrote here is BS, and that there's no point to having high refresh rates, blah blah blah. I'll school you in a 1-vs-1, (once I get cable internet again :P).

This post ended up being shorter than I expected. I covered all the bases

Thanks for your time. Please post helpful things [-o< not opposing opinions or thread-killing statements. That would make me sad IRL, and make me feel excluded like I'm some kind of weirdo 8-[

---

### Post by grahammechanical on 2013-07-19
I have not read all the way through your post. You might think it is short but it is not and your title is incorrect. Ubuntu is based upon other open source projects. It relies on other people's work on video drivers and display managers. Perhaps you should try another Linux distribution, one that requires the user to configure every aspect of the hardware. You might get what you want that way. But you might also ask why that distribution hates its users. :)

From the beginning it has been the intention that Ubuntu be a Linux distribution for ordinary users. And that approach of necessity limits what any user can do. For example, we are hindered from running the monitor at screen resolutions that are not the maker's optimum settings. We do not want people saying, Ubuntu broke my monitor when they made unwise modifications.

Regards.

---

### Post by dannyboy79 on 2013-07-19
what's the exact model number of your crt monitor and what's the exact graphics chipset you're using. Just because windows xp told you you were running 800x600@160 doesn't mean you were

---

### Post by snowpine on 2013-07-19
Why did you uninstall Windows if it was working flawlessly, *especially *if you had not yet tested whether Ubuntu was an adequate replacement for your needs?

---

### Post by eriktilton on 2013-07-19
It was most-definitely the smoothest, silkiest 160 Hz anyone could possibly imagine; and I say that with 110% certainty. My monitor would even say that on its OSD, back when I had XP.

Here's my 10-monitor.conf file with the details:

[I]Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "GatewayVX920"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX+"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "1152x864_100 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection[/I]

Gateway-branded VX 920 Diamondtron NF

I've swapped back and forth between the Ubuntu and Nvidia drivers and I've settled with the Nvidia one due to it being able to produce 1152x864@100Hz. The other ones max out at 75Hz. I'm using a DVI-to-VGA adapter but I don't think that would make any difference because XP could see it as a fast VGA.

From the bottom of my heart **thank you** for looking into this :D:D

---

### Post by eriktilton on 2013-07-19
> **snowpine said:**
> Why did you uninstall Windows if it was working flawlessly, *especially *if you had not yet tested whether Ubuntu was an adequate replacement for your needs?

Thanks for the question
My using Ubuntu now is a result of trying it as a test. The reason I'm still sticking with it is because at the moment I don't have a fast internet and at present aren't running around game servers like a bunny-hopper. But I will later on in the future. In the meantime, I'm going to be loyal to Ubuntu until I go back to storage in a few months (it's in another state) and dig up my copy of XP.

I'm hoping Ubuntu can match XP in this regard -- fast refresh rates -- and thus exceed it as an OS of choice.

Thanks again

---

