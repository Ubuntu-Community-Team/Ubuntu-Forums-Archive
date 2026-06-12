---
title: "First impressions: Switched from RHE6 to Ubuntu 13.10 (non sophisticated user)"
date: 2013-10-21
forum: Recurring Discussions
---

### Post by Jim_Granite on 2013-10-21
My company had put RHE6 on my laptop, but, now that I left that company, I switched it to Ubuntu 13.10 today on a 64-bit Lenovo W510. Everything is different, of course, and I have to learn how to crawl all over again before I can walk, and then run.

So, I figured I'd document my temporal trials and tribulations (and exultations, when/if possible). 
The good news is that Googling for each of my issues to come should result in much better documentation of solutions.

My first happy surprise was that the Ubuntu 13.10 *almost* installed easily in a dual-boot (Win7 + Ubuntu) setup where I allowed Windows 7 to create the 100GB NTFS Windows partition plus a 250GB NTFS data partition.
For some reason, the Ubuntu 13.10 Boot DVD crashed every time I tried to have it make the Linux partitions (because I had wanted a 100GB EXT3 root partition, and a 25GB EXT3 home partition, and a 16GB linux-swap partition, i.e., 1xRAM).
So I was forced to allow Ubuntu to use its own defaults, which are clearly not what I want - but - which I will google to see how I can fix after the fact.
```
~$ cat /etc/fstab
...
# / was on /dev/sda5 during installation
UUID=efcb8f75-dadd-46bd-af35-1717a7afe19b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6a66657c-e2c5-40c9-a9ca-0e88ed03d7e9 none            swap    sw              0       0
```

The next surprise was that the graphics worked, considering that Nvidia is always problematic - but - as expected, the drivers were Nouveau (and not Nvidia):
```
~$ lspci|grep -i vga
01:00.0 VGA compatible controller: NVIDIA Corporation GT216GLM [Quadro FX 880M] (rev a2)
```

~$ sudo lshw -C display 
Hangs forever (with or without sudo)

~$ grep -i chipset /var/log/Xorg.0.log
[    23.038] (II) NOUVEAU driver for NVIDIA chipset families :
[    23.039] (II) VESA: driver for VESA chipsets: vesa
[    23.046] (--) NOUVEAU(0): Chipset: "NVIDIA NVA5"

~$ gnome-control-center ->Screen Display
Showed the correct display resolution of 16:9 (1920x1080).

While it was refreshing to see icons, by default, on the SIDE of the display (simply because the top and bottom real estate is precious in HD displays), more than half the icons were clearly useless, from the get go.

I had to immediately delete icons I'd never use (Amazon? Huh?, Ubuntu One? (what's that?), Ubuntu One Music? why would I want that?). I can't imagine that I need any of that stuff, and, if I actually wanted it, I'd put it there (which I doubt I ever will). So I removed them from sight without even looking up what they really did. All I want is what everyone wants, which is simply menus to all the installed programs and buttons for the most-often used programs. Nothing else is needed on the desktop.

The whole reason for the dual boot is to have MS Office, so, I also removed the LibreOffice icons, as I've learned my lesson over the years having tried very many times to pass documents back and forth between MS and everyone else. The minute they actually make a (truly) compatible office suite is the moment Linux will take over the world, and MS stock will plummet like Kodak in the age of digital cameras. But, we're nowhere near that point yet, so, out the door goes LibreOffice icons.

It's really disconcerting to see all those music "things" in the Ubuntu start menu first line. What is that stuff? Who on earth would want this crap. If I had wanted iTunes in my face, I would have bought a Mac and an iPhone instead of Linux and Android. The LAST thing I do on my computer is music (that's what my iPod is for, and even then I use SharePod and never ever even install iTunes). So, for now, I'll see that Frank Sinatra garbage - but when I have done the important stuff, I'll figure out how to wipe out music forever from my setup. (I don't mind storing, recording, and perhaps playing mp3 files, but there is zero chance I'll be using my laptop to obtain them.)

It was definitely a little weird to see that the Firefox menu was way up on top of the screen, and actually nowhere near the Firefox window ... (???) but, given that my aspect ratio is vertically challenged, at least that fixed menu was blessedly thin, taking up little vertical real estate (and with the desktop panel on the side, I hope I don't have the RHEL6 gnome bouncing windows bug, which is apparently the longest-running gnome bug ever, at over 10 years and counting). 

At first I couldn't find the "start menu"; but then realized belatedly it's probaby in the "search your computer and online sources" button; but, it certainly does not look, act, or feel like the simple (KISS) menu that I prefer. I'll have to work on that. Later. 

It was also not initially obvious where the xterm icon lay, but I found it and will figure out how to make it permanent on the start bar.
The fact the Xterm kept fullsizing on me when I brought it to the top of the screen dug into my eyes like a spoon in a coffee mug, until I realized not to do that. 

So, there are these little gotchas.  For example, I can't imagine anyone dual booting with Windows who wants to have common simple widgets in vastly different places. As a result of the window-close widget being in the wrong corner, I somehow killed my browser - and - thought I lost everything- but - somehow - when I opened the browser back up, logged back into Ubuntu forums, and clicked to re-use what I had previously typed, all that I had thought was lost automagically came back up in this window where I then simply continued to type. That was a pleasant surprise! (I guess it's due to the open-id style login into the forum?).

The biggest pleasant surprise was that my Android 4.1.2 Samsung Galaxy SIII actually mounted on Ubuntu! It's still in PTP mode (because that's what worked best on Windows 7). That it mounted on Ubuntu without pulling my hair out was a shock, since on RHEL6 there was just no way you could (easily) accomplish that feat (whether in PTP mode or in MTP mode).  Of course, when I doubleclicked on my standard JPG photos, Ubuntu complained "Failed to open input stream for file", but when I pasted a photo on the desktop, it came up in the image viewer just fine - so it must be a protective thing of some sort.

Googling for how to put the window-management buttons on the correct corner, I find I need "gconf-editor", but, when I typed that into the Start-Run equivalent, the strangest thing happened. It didn't bring it up. It seems to have become a search in the browser. Had I wanted to search in a browser, I would have searched in a browser, so, whatever just happened, I'm going to have to turn off later, when I'm done with the important stuff. 

Opening up an xterminal, I find gconf-editor isn't installed by default, which is kind of surprising since that's got to be the first thing almost everyone (except Mac users) would want to do just so that they could *use* their desktop without screaming". 
```

~$ gconf-editor
The program 'gconf-editor' is currently not installed. You can install it by typing:
sudo apt-get install gconf-editor
```
I can't imagine that I need to install yet another program just to fix the window manager, so, I'll google a bit to see if there is a better way to fix the window system.

Another potential gotcha is that I don't remember giving the root any different password than the user (I don't even think I gave root a password at boot time), but now I can't log into root. This may be problematic, and, I hope, doens't force me to re-install the OS:
```
foo@foo:~$ su
Password: 
su: Authentication failure
```

Anyway, I'll close up this initial impression with only one major downside, which is that the OS is dog slow. I'm *sure* it's due to the wrong driver somewhere, so, I'll figure out what the problem is when I complete updates and other actions.

---

### Post by wildmanne39 on 2013-10-21
*Thread moved to **Recurring Discussions**.* To use elevated privaleges just use the sudo command.

---

### Post by stinkeye on 2013-10-21
Use dconf-editor or unity-tweak-tool not gconf-editor .
[**_[COLOR="#B22222"]By default, the Root account password is locked in Ubuntu[/COLOR]_**]("https://help.ubuntu.com/community/RootSudo")

I think you may be better served to search/post individual questions if you want answers, rather than a blog 
of the trials and tribulations of Jim_Granite.

---

### Post by Jim_Granite on 2013-10-22
> **stinkeye said:**
> Use dconf-editor or unity-tweak-tool not gconf-editor .
Ah, thanks. Googling found gconf-editor but that must be wrong.
```

foo@foo:~$ dconf-editor
The program 'dconf-editor' is currently not installed. You can install it by typing:
sudo apt-get install dconf-tools
foo@foo:~$ unity-tweak-tool
unity-tweak-tool: command not found

```

Looks like apt knows about the former, but not the latter. 
As for root being locked. Wow. I had no idea. That's a shocker to me. I guess, if sudo works as well, then there's no need for root. I guess. ... (although this is the first I'm hearing that there's no root in any OS).

---

### Post by stinkeye on 2013-10-22
> **Jim_Granite said:**
> Ah, thanks. Googling found gconf-editor but that must be wrong.
```

foo@foo:~$ dconf-editor
The program 'dconf-editor' is currently not installed. You can install it by typing:
sudo apt-get install dconf-tools
foo@foo:~$ unity-tweak-tool
unity-tweak-tool: command not found

```

Looks like apt knows about the former, but not the latter. 
As for root being locked. Wow. I had no idea. That's a shocker to me. I guess, if sudo works as well, then there's no need for root. I guess. ... (although this is the first I'm hearing that there's no root in any OS).
I use synaptic instead of the software center.
Just searched in the software center but doesn't show.
Search for "tweak" and it will show.

Install synaptic, unity-tweak-tool and dconf-editor.....
```
sudo apt-get install synaptic unity-tweak-tool dconf-editor
```

[COLOR="#FF0000"]Edit:[/COLOR] [S]I think **dconf-tools** is installed by default and just need to search in the dash for **dconf-editor**.[/S]
Was in 13.04 but looks like you just need to install **dconf-editor** which is now a separate package,

---

### Post by Jim_Granite on 2013-10-22
Thanks for the advice.
I ran the following:
$ sudo apt-get install synaptic dconf-editor unity-tweak-tool
---
The dconf-editor on Ubuntu 13.10 has problems, and isn't what I'd suggest for beginners to fix their window controls anyway, because it's horridly complex and not intuitive for setting window-control locations:
$ which dconf-editor
=> /usr/bin/dconf-editor
$ dconf-editor
=> ** (dconf-editor:11866): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends
This pops up a windows that is too complicated (but which may be useful to resolve the Ubuntu 13.10 TBB ibus error):

[ATTACH=CONFIG]247147[/ATTACH]

So, I used the unity-tweak-tool which was much more intuitive for a noob:
$ unity-tweak-tool
[unity-tweak-tool]Window Controls->Alignment->Right
[ATTACH=CONFIG]247148[/ATTACH]

In the future, I'd recommend a noob use the unity-tweak-tool, and I would deprecate dconf-editor for a noob.

---

### Post by Jim_Granite on 2013-10-22
While the Tor Browser Bundle was easy to install, it was very frustrating, as a noob, getting it to work on Ubuntu 3.10.
 [https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)

The extremely non-intuitive trick to get TBB to work on Ubuntu is to kill  the Google "ibus":
$ ibus exit
Who knows what unintended consequences that will have; but, it's the ONLY way I could get the Tor Browser Bundle to accept any inputs from the keyboard! Otherwise, the TBB was just a pretty window that you couldn't type a single thing into!

EDIT: Another workaround is to remove the ibus entirely, & reboot; but, then you won't have any foreign-language-input support:
$ sudo apt-get remove ibus 
$ sudo reboot

EDIT: Another Ubuntu 13.10 bug that's very hard to get used to is the lousy way Ubuntu 13.10 deals with showing that Tor/Vidalia/Privoxy/Firefox is running. In all other operating systems (RHEL6 and Windows anyway), by default, you'll  see a separate Tor-onion icon in the task bar which shows the wholly separate  process status (which takes a while to initialize to go from purple to green). On Ubuntu, by  default anyway, you're wholly blind. It's like taking off in a plane  into a wall of fog. You can't see what's going on. The Tor/Vidalia/Privoxy/Firefox process does NOT show up as a separate icon on the default Gnome desktop panel like it does on all other operating systems using Gnome. You just can't find it on Ubuntu 13.10. You're wholly blind in Ubuntu 13.10. It's as if the people who decided this have never ever used a Tor Browser Bundle before. It's not at all a usable use model.

That's got to be a bug. 

For example, one very common use model, is to kill the TBB when you're done with one web page, and then start anew (sans latent cookies!)with a new Tor process for a second web page.
On all other operating systems, this is easy to do.
However, on Ubuntu 13.10, it's miserable because you can't find the all-important Vidalia process on the task bar to right click and kill it (there is no separate "onion" icon!).
If you right click and kill the Firefox on the task bar, you'll lose your normal Firefox window.
Clearly nobody tested this concept of not separating Tor/Vidalia/Privoxy/Firefox from Firefox in the real world on the Ubuntu side. 

My best workaround, so far, is to manually kill Vidalia manually from the command line:
$ ps -elfww  | grep vidalia
$ kill -9 [vidalia process id]
Only then can you restart the Tor browser bundle, with new cookies, and a new identity, with new entrance and exit nodes:
$ tor

EDIT: Another Ubuntu 13.10 bug is that the desktop can't seem to tell the difference between your native Firefox and the Firefox of the Tor Browser Bundle (which is effectively a wholly different browser).  I'm not sure how to workaround this bug yet - but if you have input, I'd appreciate it.

BTW, where is the suggested location to put hierarchies such as the TBB in? 
$ echo $PATH 
=> /usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
What I ended up doing was:
$ sudo mv /tmp/tor/tor-browser_en-US/ /usr/local/sbin/.
$ cd !$
$ sudo ln -s ./tor-browser_en-US/start-tor-browser tor
$ cd
$ which tor
=> /usr/local/sbin/tor

---

### Post by Jim_Granite on 2013-10-25
I've only been on Ubuntu for a few days, but, having been on RHEL6 for so many years, it was a shock to see how difficult it is to use Ubuntu 13.10 out of the box, in comparison.

I guess that makes sense, since RHEL6 is actually tested with users for a long time before being released, so, I guess the bugs I'm seeing out of the box in Ubuntu are a result of no testing (some of which happen to everyone at the onset - so - the only explanation is that Ubuntu 13.10 was never tested properly).

Maybe I just forgot my learning pains on RHEL6/Gnome. 
Dunno, it has been so long since I re-installed my OS; but, so far I'd say the Ubuntu 13.10 default environment is lacking horribly in some respects by way of comparison.

It didn't bode well that the installation DVD crashed every single time I tried to have it partition my dual-boot system (which only had a small Windows partition at the time); so I STILL have to go back and spend the time and effort to manually partition to what I want, which is simply a 100GB NTFS Windows partition; a 250GB NTFS shared-data partition; a 100GB EXT3 Linux partition; and a 16GB linux-swap partition. That this was impossible to accomplish using the Canonical DVD is a bit of a shocker, since it's standard practice to install the two NTFS partitions with the Windows 7 DVD, and then to do the rest on the unformatted space. Sigh.

However, other than the fact that the most basic of operations crashed the DVD, the installation otherwise worked just fine.

The worst desktop problem, so far, is that you can never know ahead of time WHERE the window control buttons will lie.
- Sometimes they're on the right (where they belong, especially in a dual-boot Windows/Linux system!)
- Yet, sometimes they're on the left (where you have to hunt for them since they auto-hide when they go left)
- And, worse yet, sometimes they're nowhere to be seen (e.g., when the application windows go to full screen)
You waste a lot of time hunting for where the window controls are, and, as a result, you can never go full screen with an application, as the only viable workaround. 

It's a ridiculous use model. Clearly, it is a very bad decision, and, since it's a basic decision, that's portends ill for the future for Canonical's very basic decision-making ability.

Another bad decision was to make the same mistake Apple made in the late 80's and early 90's to disassociate the application menus from the applications. Sure, in the 80's, people only ran one application at a time, so having the menus stay in the top-left corner made sense, especially since one could overshoot and still hit a menu selection that way; but Apple was unable to change it to a more modern approach when computers and monitors got bigger and faster in the 90's. But just because Apple is stuck in time, doesn't make Ubuntu want to have to emulate them by copying bad practices as new. It makes absolutely no sense to have the application menus disassociated from the applications. In some cases, the menus are a good ten inches away from the application, by default! That's just crazy. 

And that's just the default desktop! Some of the applications everyone uses every day are broken horribly right out of the box.

For example, somehow they royally screwed up the Tor Browser Bundle Launcher settings. As a result, you can't distinguish TOR from Firefox. They are mixed together. Which also means you can't start TOR from a launcher, since you can't even MAKE a launcher for tor that is separate from Firefox. Yikes! Clearly they never even tested this one once!

Interestingly, their Firefox-based "Launchpad" works just fine with it's own separate launcher; so, it's not that TOR is designed to be impossible to start outside of the command line. And, I should note, the TBB works perfectly fine, with it's own green/purple onion icon in Windows and in RHEL6, so, it's not a bug with Tor. It's only a bug on Ubuntu. I don't know if anyone has reported this yet though - so - maybe they're fixing it - but it shows it was never tested even once. That doesn't indicate good things about Canonical QA processes.

In addition to TOR not having been tested with the Launcher, it also wasn't tested once to see if a user could actually go to a single URL in the browser. Yup. You can't type a thing into TOR unless you have the secret decoder ring that tells you to kill the Google ibus, which is running by default in Ubuntu 13.10. That this happens to everyone is yet another indication that Tor (a very common browser setup!) was not tested even once! Sad. But true.

In addition, the sound is broken, out of the box. Luckily that's so easy to fix, that one has to wonder WHY they haven't patched that bug with Ubuntu working with Alsa.

There's a Gnome problem that the backspace key no longer works properly (to go back one level in the hierarchy for each press); but luckily that's a single-line fix.

I guess this is a short list, so, that's the good news. For example, the hardware all seems to work - which was a nice surprise. And most applications are working just fine - which is also a nice surprise. 

But, after a week of using Ubuntu 13.10, I'd say the sheer frustration of having to hunt for the window controls, and the fact that the browser I use all the time can't even start up from the Launcher, indicates that Canonical never tested these things properly. That's sad. Then again, what do I want for free! :)

---

### Post by zKhtdyX on 2013-10-28
It sounds like you got the user interface change shook a few years after most people :)

Why did you switched from RHEL to Ubuntu?

---

### Post by Jim_Granite on 2013-10-29
> **zKhtdyX said:**
> It sounds like you got the user interface change shook a few years after most people 
I'm just starting to get used to the user interface of Unity. 
There are more things I don't like than I like, but, I'm working around the bugs one by one.
For example, I understand why having iconified windows take up real estate might be bad, but, having to always click on a launcher to see a half dozen windows pop up that I can barely read on my small monitor isn't really an improvement. What it teaches me is to change my use model. I'm forced to kill applications way sooner than I would if the use model were more friendly to multiple applications running at the same time.

Basically Unity is a single-tasking user interface. For that, it's clean. Very clean. That's nice. But, if you have multiple windows, you can't even tell what applications are running (e.g., Tor and Firefox have nothing to do with each other but they're all mixed up in the same launcher item). So, you're pretty much forced to run a single application at a time.

Once you change your use model, Unity seems to work reasonably well in single application mode.

> **zKhtdyX said:**
> Why did you switched from RHEL to Ubuntu?
This is a very good question because the answer highlights what's GOOD about Ubuntu.

The ONLY reason I was on RHEL6 for my desktop was that it was a work machine, and the work software was only tested on RHEL6, so, if I filed a bug report, it would have to be on RHEL6 or the developers at my company wouldn't look at it. Then I switched jobs. The company let me keep the computer. So, now I had no need for RHEL6 - but I kept it there until ... 

Until my machine crashed. It wouldn't boot to the graphical environment. So, I needed to reload the OS. But, one of the nastiest things about RHEL6 for a Desktop is that newer stuff doesn't work. Newer stuff like Android 4.1.2 doesn't work. You can't mount your cellphone because it doesn't support MTP. And Google deprecated USB mode in Android 4.1.2, so, I couldn't mount my cellphone.

A nice surprise was that I was able to mount my cellphone just fine on Ubuntu.

Another PITA with RHEL6 was that a lot of desktop applications were old (e.g., the Pan nntp client), and a lot more non existant. Mostly in the multimedia space is where I saw this problem. I'm presuming I won't have that problem with Ubuntu.

That's pretty much my rationale.

---

### Post by zKhtdyX on 2013-10-31
I don't really think Unity is ment to be a "single tasking user interface". DOS is a single task system. In contrast to DOS, with the upcoming later windows versions it was possible to run multiple application at the same time. A huge advantage.

If you dont get happy with the task switching model in Unity (like me) you could use a classic task bar like tint2 (its in the repos) and autohide the Unity Dock. Another option could be using the gnome2-like flashback session.

---

