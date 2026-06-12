---
title: "Ubuntu not using right driver for RX 480?"
date: 2016-08-19
forum: New to Ubuntu
---

### Post by nonbeing2 on 2016-08-19
Sorry for lengthy post, wanted to make sure I got everything.

I just built a new pc with an i5-6500 and an RX 480. It has 8 gb RAM and an SSD. The motherboard is MSI B150M Mortar. I installed Windows 10 and it's working very fast with no problems afaik, drivers installed, etc. However, when I tried to install Ubuntu Gnome, I had a serious problem. After overwriting Gnome with Kubuntu, I've continued to have more or less the same problem.

When I finished installing from a bootable usb, I immediately noticed that the os was very slow (happened with both gnome and kde). Taking 5 seconds to do stuff like dragging a window across the screen. Web searching suggested this was because of gpu drivers not being installed right. (the gpu itself is detected by lshw, and my monitor is plugged into it and receiving a signal, but is not listed on system information/about device). On gnome, I updated everything, restarted, and then tried going to amd's site and installing amdgpu-pro using the instructions on AMD's site; the script ran fine, but when I rebooted it froze at the gnome logo and had graphical glitches. The installation was unusable so I started over with kubuntu, but had the same slow performance.

Kubuntu's driver manager is apparently mucked up right now and endlessly detecting hardware (known bug), but even after (probably) fixing it by installing and updating apt-xapian-index, then restarting, the slowness continued and there was nothing displayed in the driver manager about the gpu. "ubuntu-drivers devices" only listed something about the cpu (which was also in the driver manager).

One other thing that may or may not be relevant: I had weird inconsistencies when trying the live systems. Sometimes it would go straight to the install or try screen and have 1080p (my monitor's native resolution), and would shut down as intended. Other times it would go to some version of grub with options, then would boot in 768 resolution, which could not be changed; if I shut it down after that it would prompt to press enter as always, but instead of actually shutting down it would just move a command line cursor in the corner of the screen down a line, and I'd have to power down the pc by holding the power button. This happened with both gnome and kubuntu, but in both cases the actual operating systems ran cleanly and quickly apart from the issues listed above. There didn't seem to be any rhyme or reason to when it worked correctly or incorrectly, but the messed up boot only happened on the new pc, not on my laptop iirc. Both times that I installed an os, it was when the live system was messed up.

Another thing: at the suggestion of an irc user I ran the command ```
lspci -nnk | grep -i vga -A3 | grep 'in use'
``` but the terminal gave no response and just gave me another prompt as if I'd just opened it.

---

### Post by QIII on 2016-08-19
Hello!

Which release of *buntu are you using?

---

### Post by nonbeing2 on 2016-08-19
I am currently using kubuntu, though as I said I had a similar problem in Ubuntu Gnome.

---

### Post by QIII on 2016-08-19
The numerical release number will be important.

---

### Post by nonbeing2 on 2016-08-19
It's 16.04, the latest version from the official torrent.

---

### Post by QIII on 2016-08-19
OK.

The open source AMDGPU driver should install by default with these chipsets:  Tonga, Carrizo, Fiji -- and now your Polaris.

With my R9 380X, the AMDGPU driver on 16.04 outperforms the fglrx driver on 14.04.  You should clearly not be having performance issues.

So, let's first see if the AMDGPU driver is loaded.  Issue the following command in the terminal and post back the results:

```
lsmod | grep amdgpu
```

to see if the AMDGPU driver module is loaded.

---

### Post by nonbeing2 on 2016-08-19
I entered the command and received no response from the terminal, much like when I entered the command in the op.

---

### Post by QIII on 2016-08-19
Do you get anything from just ```
lsmod
```

---

### Post by nonbeing2 on 2016-08-19
Yeah, I tried that as well and received a long list of things that looked like drivers.

---

### Post by QIII on 2016-08-19
Ok.

Try ```
lsmod | grep radeon
```

---

### Post by nonbeing2 on 2016-08-19
No response again.

---

### Post by QIII on 2016-08-19
Is this a dual boot, or have you installed it in a virtual machine?

---

### Post by nonbeing2 on 2016-08-19
Dual boot

---

### Post by QIII on 2016-08-19
Ok.  That's troubling.  

It should have installed either RadeonSI or AMDGPU -- unless the newly released Polaris chipsets are not accounted for in the installation.

I'm going to look through the reported bugs on Launchpad and see if this has come up.

While I do that, you might try to load the module manually:

```
sudo modprobe amdgpu
``` should do it, I think.

---

### Post by QIII on 2016-08-19
Ok.  Found something already:  Polaris will not be supported until kernel 4.7.

Ouch.  Let me try to find you some better news.

---

### Post by Geoffrey_Arndt on 2016-08-19
Maybe a couple options . . since this is a dual boot, perhaps installing 16.10 (Yakkety Yak) or upgrading the kernel via process described here:   [http://ubuntuhandbook.org/index.php/2016/07/install-linux-kernel-4-7-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/07/install-linux-kernel-4-7-ubuntu-16-04/)


Note:   re Link . . comments have some clarify info . .

---

### Post by nonbeing2 on 2016-08-19
That is certainly unfortunate news...

Will 4.7 be installed on Yakkety Yak? I see the stable release is scheduled for October. I guess two weeks isn't *that* long to wait if all else fails, since I do have one functioning OS already. The guide to updating the kernel says it should only be done by experienced users, but it's not like there's really anything on my ubuntu installation to lose anyway, and the instructions *seem* pretty straightforward; I think I could try that.

Should I expect any problems from using a newer version of the kernel than the distro was built for?

---

### Post by nonbeing2 on 2016-08-19
Posting an update here:

I updated the kernel with deb packages as described in the link above and rebooted, forgetting to update grub. When it rebooted, I selected Ubuntu in Grub and got a black screen. Rebooted into recovery mode, updated grub on the menu there, then selected the option to start normally. It displayed a notice saying I may need to reboot for some drivers to work correctly, then started. When plasma booted it was working at fast speeds, and everything was usable. 

I opened a terminal and entered some of the commands from earlier in this thread, such as ```
lsmod | grep amdgpu
``` and basically anything else that would check for a driver, but received no response from the terminal just like before. Remembering the notice when I left recovery mode, I rebooted. However, it gave me a black screen again. Powered down the pc and tried again, and this time it showed some text going down the screen like one often sees when booting linux, but it reached ```
---[ end Kernel panic - not syncing: Fatal exception in interrupt
``` and then stopped, forcing me to power down yet again. I took a picture of the screen when the kernel got stuck, which I can try to post if necessary.

Thinking I might have made a mistake when updating the kernel, I did a clean install of kubuntu 16.04, installed regular updates, rebooted, installed the kernel packages by copypasting the exact commands given in the comments on the link, updated grub, and then rebooted again. Again I am getting a black screen after selecting ubuntu from grub.

Anyone have any idea what's causing this? Should I just wait for the October release and see if I have better luck then?

---

### Post by Geoffrey_Arndt on 2016-08-19
Usually, the next 9 month point release (16.10 YY) is quite usable by this point in the dev. cycle . . . minor glitches are more the norm than major issues.   But it's your choice - - you can certainly wait, but on the other hand, you do have very current hardware and this is one of the trade-offs (meaning latest LTS support not always available).   

You can download the daily build from here to "test" it out (what to lose?),

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by nonbeing2 on 2016-08-19
Looking at the release schedule, I see that the beta version is coming out next week. Should I perhaps wait till then? Though if it's on a nightly schedule, will there even be much difference between today and the beta? I may give the nightly a try tomorrow, depending on how much spare time I have. If I do then I'll come post the result itt.

---

### Post by Geoffrey_Arndt on 2016-08-20
Whatever version you install is not a fixed version.   The updater process will take your alpha to beta to final release.   Given your situation and inexperience with kernels, this is probably the safest way to go as long as you understand not to use your 16.10 install as a "Prod" device.

---

### Post by deadflowr on 2016-08-20
Currently, if you install 16.10 you would have the same issue anyway.
That is because they are still on the 4.4 kernel.
They haven't re-based the kernel yet.

I think (last I remember) they had 4.6 in yakkety-proposed.
But that was sometime around last week.
things change.

But enabling proposed on the development branch is not for the feint of heart.


Better thing to do is to post the exact kernel version from mainline you tried.

Exact kernel version.
Perhaps someone can shed light on why it wasn't loading correctly.

In the mean time, you should still be able to boot the original kernel using the grub boot menu.
(during boot if the boot menu does not show normally you can invoke it by pressing the shift key or the esc key (depends on Bios setup; shift for legacy bios and ESC for UEFI setup.)
In the grub menu go down to the Advanced Options, click it and it will open the sub menu where you can load an older kernel.
Since you have xenial I would take the first entry for a 4.4.something kernel that is listed.
Then it should just boot like it did before, but of course with the busted video driver.
But at least it might be more functional. Something better than nothing kind of thinking.

---

### Post by QIII on 2016-08-20
I found [this]("https://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-16.30-Released") a little bit ago.

You can maybe start there.  It seems Phoronix has possibly tested AMDGPU-PRO on the Polaris chipsets, but that appears to be on Yakkety (
I can't vouch for any of this.

I can say that I am using AMDGPU-Pro on a Yakkety install with the R9 380X and I am very happy so far in my testing.

---

### Post by Geoffrey_Arndt on 2016-08-20
Well, I thought Yakkety would have 4.7 by Oct release, but maybe not.   We have a couple folks in our local LUG using Arch and am thinking they are on 4.7 already.   But, Arch would be a challenge for a new user (unless one enjoys a challenge and reading a lot in Arch Wiki/Forums).    In the original instruction link for upgrading kernel to 4.7, there was a comment (alternate instructions) worth a look at too - - be sure you have build-essential installed.   But more folks with recent kernel experience - as suggested by deadflowr may offer additional info.

---

### Post by deadflowr on 2016-08-20
> Well, I thought Yakkety would have 4.7 by Oct release, but maybe not. 
Oh it will be (Or they hope to make it 4.8 by release time; fingers crossed), just not currently.
Seems like they want to make a big leap this time.

---

### Post by nonbeing2 on 2016-08-21
Well, I just typed up a long response to all these posts, but accidentally backspaced out of the page and deleted it all.

TL;DR was that:
 -I did not check if build-essential was installed, but wouldn't that be preinstalled? It is on my Mint Rosa distro according to synaptic.
-I'm not exactly sure what deadflowr means by "exact version from the mainline," but I installed the all header, the generic amd64 header, and generic amd64 image deb packages in that order, updated grub, and reinstalled. I followed the instructions in the comment mentioned by Geoffrey_Arndt.
-Using the old kernel would be pointless because it is too slow to be practical for anything involving a gui. EDIT: just want to point out that I still have windows 10 installed on this pc, as well as a laptop, so it's not as though I'm stranded without a computer or anything.
-I don't see how using the proprietary driver would help if the kernel doesn't support polaris. Trying that earlier broke 16.04. Please correct me if I misunderstand.

In light of this, should I try again with a clean install of the LTS and install build-essential, try the proprietary driver on the daily, or wait for a daily that includes 4.7? Or something else entirely? Also, should I post the picture of where the kernel stopped working when I tried to boot?

Thanks again to everyone for their help.

---

### Post by deadflowr on 2016-08-21
> I did not check if build-essential was installed, but wouldn't that be preinstalled? 
No, it's not typical for a regular user to install and/or build from source packages, so no need for that as a default.
What mint does is what mint does, and is unrelated to what Ubuntu does.

That said, is there any real reason to install a newer kernel if the AMDGPU-PRO driver states it works on 16.04 as is?
I mean I see nothing on [AMD's how to install the drivers' page]("https://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx") about any prerequisites to upgrade the kernel.
So in that case shouldn't it run with the 4.4 kernel 16.04 uses?

---

### Post by nonbeing2 on 2016-08-21
Okay, posting another update here. There are some really weird things going on here.
Did a clean install, got updates, installed build-essential, and rebooted. Then I updated the kernel  and grub again, rebooted, and got another black screen. That's not the weird part though.

At this point I booted into kernel 4.4 (the version used by default) in order to uninstall 4.7 and maybe take another shot at installing the proprietary driver in case I made some human error the first time.
Well, remember how I said that when I was running the live system, it would work in two different ways? When it worked with the wrong resolution, it would go through grub and then show me the fancy kubuntu logo. When it worked "right," it would go straight to a much simpler boot screen, with nothing but the orange word kubuntu and four dots below that (It looks like the TAILS bootup screen). But whenever I've actually installed it to the ssd, it would always show me the full logo. Well, when I went into Grub's advanced options and selected 4.4, it brought me to that simple screen with the four dots, even though I was booting from my ssd. And when it actually got to plasma... everything was working at full speed with no evident problems. The terminal still did not indicate that amdgpu or radeon were installed, however.

After successfully uninstalling 4.7, I rebooted to see it it would continue to work well, but it went back to the regular boot screen and slow performance. I rebooted again and manually selected 4.4 from advanced options to see if that made the difference, but again it booted to the slow version.

What in the world is going on here? Does this shed any light on the overall problem? Should I just ignore it and go ahead with the AMDGPU-PRO installation (though I am not confident that that will be more sucessful than the last attempt)?

Oh, another thing I just remembered is that a couple days ago, when I booted from the recovery menu, it also worked at full speed for that session. Forgot to mention that at the time, I just assumed it was because it was apparently running 4.7

---

### Post by nonbeing2 on 2016-08-21
OK guys, I just tried installing the proprietary driver again, and I am happy to say that it worked this time, after some initial troubles (it didn't work the first time because of some firmware issue, had to try running the script again and it worked; my guess is that the first time I tried it, I didn't realize that it didn't work and rebooted with it only partially installed). lsmod is now displaying amdgpu as being installed, and everything is running great so far.

I feel pretty stupid for making this thread if that was the only problem, but thanks so much to everyone for your help. I'll try to learn to be a better linux user so I can avoid these kinds of problems in the future. Looking forward to using this OS, though.

---

