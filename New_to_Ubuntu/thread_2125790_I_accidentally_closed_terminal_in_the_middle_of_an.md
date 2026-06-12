---
title: "I accidentally closed terminal in the middle of an apt-get upgrade; am I screwed?"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by Steve the Pocket on 2013-03-15
I was told that in order to update a part of Steam that its auto-updater couldn't handle, I should run "sudo apt-get update" and "sudo apt-get upgrade". Well, I did, not realizing that the latter updates everything on my system to the latest build and that it would take over an hour. So I started doing other stuff while it ran, and then I accidentally closed the Konsole window along with everything else before it was finished. I don't know if it makes any difference that I was using Konsole instead of whatever terminal app Unity has, but either way, did I just ruin my computer?

---

### Post by arpanaut on 2013-03-15
try ```
sudo apt-get update && sudo apt-get upgrade
```

and see if it completes, if not post the error messages back here for help.

---

### Post by Steve the Pocket on 2013-03-15
It completed. I had interrupted it in the middle of downloading, not unpacking/installing.

But then the system tray prompted me to restart the computer, so I did. And then it froze in the middle of booting up.

Soooooo then I booted into repair mode or whatever it's called from the GRUB menu, and tried to run the package restore thing. It downloaded 30 megs of stuff and then asked if I wanted to remove three packages (y - yes, d - details). I made the mistake of typing d, because then it spat out the name of one package and "[END]" in white on black; I tried pressing Enter, End, and Esc, and I'm pretty sure Down as well, but nothing took me back to the prompt. So I started mashing keys and then the message changed to something I don't remember, and then it *really* didn't do anything no matter what I pressed. So I did a Ctrl+Alt+Del and now the GRUB menu is completely gone. Instead there's a text prompt that I have no idea how to use, but it probably doesn't matter because clearly I must have hosed it good for even the boot menu to have disappeared.

---

### Post by Paqman on 2013-03-15
What does it say at the prompt? If it's just a regular command prompt then try:
```
sudo apt-get install -f
```
If it's a Grub prompt then just reboot and start again. It's unlikely you've completely hosed your system, we should be able to recover it if you're still able to boot up into a command line with networking and run the package manager.

---

### Post by siddharth007 on 2013-03-15
Try these commands

```
apt-get autoclean
```

```
apt-get autoremove
```

Following these two commands,issue this command
```
apt-get -f install
```

Hope this helps.

---

### Post by Steve the Pocket on 2013-03-15
Oh hey, the menu did come right back.

Well, after trying the package restore again, I now have a system that boots with a text-mode version of the gray Kubuntu boot screen and goes to black when it hangs instead of just freezing. I tried going into the shell from the recovery menu and entering those three commands, but they all said nothing was changed.

Now what?

EDIT: I tried the package restore one more time as a Hail Mary, and it brought back the graphical boot screen but it still freezes.

---

### Post by Bashing-om on 2013-03-15
Steve the Pocket; Hi !
Let's see if the situation can be narrowed down somewhat - error codes are good -
Post the output of terminal code:
```
dpkg --audit
```which gives a list of unconfigured packages (if any).[INDENT=3]
hth

[/INDENT]

---

### Post by Steve the Pocket on 2013-03-15
Nothing.

Is it possible the graphics driver is messed up? I'm using a relatively new AMD legacy driver that I had to install manually with the "force" parameter on because the standard methods of removing fglrx weren't getting everything. I have no idea what trying to do an apt-get upgrade on top of that might do.

---

### Post by Bashing-om on 2013-03-15
Steve the Pocket;
A nothing return is a good thing; means all packages that the package manager is aware of are intact .

To explore your surmise in greater depth, let's load ubuntu up in "recovery mode" See how it likes the onboard "vesa" driver.
Not knowing what version you are running ->just general guidline:
Single operating system: 
cold boot, soon as bios screen clears depress and hold shift key -> grub menu
arrow down to "recovery mode" kernel, enter key to activate -> recovery console menu -> "resume normal boot"
GUI login -> username and password -> GUI desk top in degraded graphics ( we hope )
Yeas ? then from the "Additional Drivers" utility see if you can install the recommended driver.
Reboot 
.
Maybe all the background grunt work done for us and not required to (un)install the proprietary drivers.

Getting a driver to work with steam ....might be another matter, I just do not know.[INDENT=2]
we will see what is to be seen

[/INDENT]

---

### Post by Steve the Pocket on 2013-03-15
No dice. I select "resume normal boot" and after the text scroll I just get a blank screen.

---

### Post by Bashing-om on 2013-03-15
Steve the Pocket; That no go in "recovery mode" is unexpected.
OK ... Back up and regroup. Let's try a reversion prior to all the updates:
boot to grub, arrow down to an older kernel entry; enter to activate.
Will the older kernel boot up ?
[INDENT=4]
poke'n to see

[/INDENT]

---

### Post by Steve the Pocket on 2013-03-16
It does not. It too freezes during the boot-progress screen.

---

### Post by Bashing-om on 2013-03-16
Steve the Pocket;
By and large, your system is intact as the terminal is functional in all respects.
So looking at 2 scenes.
1, Reset the desktop;
2. (un)install the graphics drivers and (re)install.

So; What version are you running ?
and give the out put of terminal codes:
```
sudo lshw -C display
lspci -nnk | grep -iA3 vga
```
so we know what condition the condition is in and what we are hunting for.[INDENT=2]
moving right along

[/INDENT]

---

### Post by Steve the Pocket on 2013-03-16
lshw -C display yields:
> description: VGA compatible controller
product: M98L [Mobility Radeon HD 4850]
vendor: Hynix Semiconductor (Hyundai Electronics)
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 64 bits
clock: 33 MHz
capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
configuration: driver=fglrx_pci latency=0
resources: irq:16 memory:d0000000-dfffffff memory:feaf0000-feafffff ioport:d000(size=256) memory:feac0000-feadffff

lspci -nnk | grep -iA3 vga spat out
> 01:00.0 [COLOR="#FF0000"]VGA[/COLOR] compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI M98L [Mobility Radeon HD 4850] [1002:944a]
Subsystem: XFX Pine Group Inc. Device [16882:3000]
Kernel driver in use: fglrx_pci
Kernel modules: fglrx, radeon

(*Man* did that take a long time to type up on a tablet.)

---

### Post by Bashing-om on 2013-03-16
Steve the Pocket 	;

Welp. Card is recognized and a driver is loaded.Should workie, so why is it not - to beg the question.

Man you have not been typing all these responses ! ...Can you not copy and paste from your terminal directly into this thread (between code "#" tags) ???

Before delving deeper, how 'bout - on the off chance - a simple fix restores the desk top ? Need to know what version of ubuntu you are running .


[INDENT=3]still try'n

[/INDENT]

---

### Post by Steve the Pocket on 2013-03-16
Kubuntu 12.04 x64. Other than the video driver, everything was vanilla before the attempted update.

And I don't know my way around the terminal nearly well enough to copy the output of a command into a web forum post all from the shell. I don't even know how to use text-mode browsers.

---

### Post by Bashing-om on 2013-03-16
Steve the Pocket;

Hey we were all green at one time, not knowing how is not a sin !
     
copy and paste( will work if Xserver is running); 

Place the mouse cursor at the start of what you want to copy, hold the left mouse button down and drag the mouse to the end of what you want to copy. Release the mouse button; right click and choose "copy"// that copies the text to the clipboard.
In the open thread where you want the text "pasted" click on the "#" symbol at the top of the post and right click again and choose "paste". This will paste the contents of the clipboard between the "code tags" There also exist keyboard shortcuts to perform this operation.

Back on topic: Do this terminal command:
```
unity --reset
``` and see if that frees up your desk top. (copy/paste works the other way too ! from the thread to your terminal)
May need to reboot the computer to see the effect.[INDENT=2]
are we there yet ?

[/INDENT]

---

### Post by Steve the Pocket on 2013-03-16
Hang on. Were you under the impression that my GUI was functional? Because it's not; Kubuntu's recovery mode is ANSI-only (although oddly enough, it comes up with a custom font and a resolution that appears to be widescreen) with no mouse support; the menu is cursor-key driven and the shell comes up fullscreen. Hence why I've been accessing this forum from a tablet.

Oh, and Kubuntu uses KDE, not Unity.

---

### Post by Bashing-om on 2013-03-16
Steve the Pocket     ;


Just goes to show my ignorance//my ubuntu "recovery mode" is functional// Oh well ..live and learn.

Kde:
if you restart Kwin (in Konsole) are there error messages?
```
 kwin --restart
```[INDENT=2]
hang'n in there

[/INDENT]

---

### Post by steeldriver on 2013-03-16
I wonder if your kernel got upgraded to a version that is incompatible with an installed proprietary fglrx driver?

[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

---

### Post by Bashing-om on 2013-03-16
@ steeldriver, Glad to have your support. We tried booting an older kernel, with the same results. Would not booting the older kernel negate the driver/new kernel incompatibility ?
I am close to being lost for options and about to direct the OP to restore the desktop to defaults. But, keeping in mind that composting might be presenting a problem.[INDENT=3]what can I say ?

[/INDENT]

---

### Post by Steve the Pocket on 2013-03-17
Well now we might be getting somewhere: typing kwin at the shell prompt gets me
> kwin: FATAL ERROR while trying to open display

That might just be because X isn't running, though, or because the graphics driver needs to be started first or something.

---

### Post by steeldriver on 2013-03-17
... what happens if you type 'startx' instead of kwin?

(apologies if you already tried that - I didn't reread the whole thread)

---

### Post by Bashing-om on 2013-03-17
Steve the Pocket; steel driver;
"startx" is  valid -- see what errors that returns - on my list for troubleshooting -// Still looking at this as a display problem rather than a driver issue.
As such let's look at the/var/log/Xorg.0.log file as well as the hidden file in home directory ~/.xsession-errors and see if there are any reported errors, before we take drastic measures.[INDENT=3]my think'n

[/INDENT]

---

### Post by Steve the Pocket on 2013-03-17
Here's what startx does. First it spits out the parameter list, and then after a few seconds...
> Fatal server error:
Could not create lock file in /tmp/.tx0-lock

Please consult the The X.org Foundation support at [http://wiki.x.org](http://wiki.x.org) for help.

ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error
xauth: error in locking authority file /root/.Xauthority

---

### Post by steeldriver on 2013-03-17
OK if you are still in the 'Root Shell' of recovery mode, then it's normal to have no networking, and for the filesystem to be read-only (hence you won't be able to start X - the lock file /Xauthority files won't be writeable)

If that's the case, type

```
exit
```

at the # prompt to get back to the main recovery mode menu, then with your ethernet cable plugged in select 'Enable networking' from the menu and confirm (it will ask you if you want to remount the filesystem), then once it's done select 'Drop to root shell prompt' again and try

```
ifconfig eth0
```

Hopefully you will now see a valid IPv4 address - most likely something like 192.168.x.x if you have a regular LAN router

If that works then you can try

```

apt-get update
apt-get upgrade

```

Let us know how it goes

---

### Post by Steve the Pocket on 2013-03-17
Yeah, I tried running an update/upgrade yesterday, just in case there was something it had failed to grab the first time around. It told me there were no packages with updates available.

---

### Post by steeldriver on 2013-03-17
OK in that case, let's see if we can figure out why it won't boot past the text console

First, let's make sure the filesystem is mounted with read-write permissions:

```
mount -o remount,rw /
```

(note there's no space between the remount,rw options) THEN try to start the GUI display manager - I don't have Kubuntu but afaik 12.04 still uses kdm

```
service kdm start
```

Does it try to take you to a graphical login on tty7? If it fails, switch back to the root console (Ctrl-Alt-F1) and see if there are any error messages

---

### Post by Steve the Pocket on 2013-03-18
I think the mount command didn't go through correctly, because it dumped the param list. But I ran the enable networking option in the menu, which I know remounts the filesystem in read/write mode because it always warns me that it will. Then I ran the second command and it said something like "thread running, process 1337" and after a few seconds the screen went blank and stopped responding.

In the meantime, I decided to see if there's a solution documented elsewhere by googling "kubuntu updating broke my system" and found [this page](http://www.nixternal.com/why-does-kubuntu-suck/) with a rather worrisome post beneath:
> Here is one SERIOUS reason Kubuntu sucks. Any time an upgrade to core system packages like kde-workspace/desktop or plasma occurs, the entire system breaks. It removes essential packages and doesn't reinstall them. One has to do this through a recovery prompt. Perhaps this only happens with packages upgraded via the backports repo--I don't know. But it's it's still a major bug in the way certain package upgrades happen. I've been using Kubuntu since version 9 or 10 days and this bug still hasn't been fixed with version 12.10!
Eep. I may try to get in touch with that poster and see what they know.

---

### Post by teddybairs1 on 2013-03-18
Simple word of advice. More like a side note to all the command line gymnastics in order to save you some pain in the future. Regardless of which Ubuntu variant you're running, it's always safer to use Synaptic to run your upgrades. It's basically just a gui for APT, so whatever the command line can do, Synaptic can do. You can download it using Kubuntu's built in package manager or you can commandline jockey to get it, but it's still the most useful and most intelligent package manager program out there. It will warn you if you mistakenly try to close the program while an upgrade or install is in progress. I've used The Software Center, the commandline APT, Muon, and Synaptic and by far Synaptic is the most reliable and flexible of any of these methods that I've found.

---

### Post by Steve the Pocket on 2013-03-18
Doesn't surprise me. Muon doesn't even have a way to update apps. I only learned partway through the apt-get update process (because clicking some alert brought it up) that there's a *separate* app for that, which I never even noticed in the applications menu.

(This is so far my biggest complaint with KDE itself &#8212; things that ought to be part of the same app or the same menu or whatever are often not. I understand the need for Linux to be modular and all, but they take it way too far.)

---

### Post by cmcanulty on 2013-03-18
Can you explain how to upgrade from synaptic. I tried mark all upgrades and all my apps were selected even though I am quite up to date on 12.04

---

