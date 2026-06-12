---
title: "System clock resets ahead four hours after shut down"
date: 2015-03-23
forum: New to Ubuntu
---

### Post by t9rfbb on 2015-03-23
I am dual booting Lubuntu 14.04.1/Win XP Pro. Each is installed on a seperate drive and I select the drive from the boot menu when first starting PC.

When booting into Lubuntu after a Win XP session I notice that the time on the clock in the bottom right corner is momentarily off (four hours ahead) and then corrects itself.

However, each time I shut down Lubuntu and boot back into Windows XP Pro I have to reset the clock four hours back. :-(

This is not a Windows issue. Rebooting Windows multiple times does not affect system clock. It only occurs ofter booting into Lubuntu and then shutting down Lubuntu.

If I check the time in the BIOS after shutting down Lubuntu but before booting Windows I see that the system clock has been reset four hours ahead. Clearly Lubuntu is resetting the sytem clcok in error at time of shutdown.

Because the error is exactly four hours I am guessing that somehow Lubuntu has the wrong time zone info and uses that to reset the sytem clock on shut down. I have "Time and Date" (default w/Lubuntu) installed and it shows the correct time zone as America/Toronto. I have also installed "Date & Time" in order to be able to edit the the list of NTP servers. "Date & Time" also reports the correct time zone. I prefer using a time server located in Canada. I use that same time server for all the Windows computers I support with no issues. Also I have tested and Lubuntu does correctly connect with my prefered NTP time server.

Not sure at this point where to look or what to do. Suggestions?

This is a new intall of Lubuntu. Though I have bags of compter support experience since before DOS (yeah, been around for awhile) I am a newby as far as Linux goes, so please be gentle with your answers. I'm no stranger to using a command line but am still learning all the acronyms, commands, and how to get at things "under the hood". Thanks in advance.

---

### Post by kerry_s on 2015-03-24
change the clock, there's another one in addons called orage time, there's also 1 not installed by default called xfce4-dateime-plugin

---

### Post by DuckHook on 2015-03-24
I suspect that your problem is the very common one that afflicts dual booters of XP and any Linux distro...

Linux uses Universal Time (UTC) or, as we old timers used to call it, Greenwich Mean Time (GMT). XP uses local time. Since the 'buntus by default synchronize to Universal Time using NTP at every boot, it will reset your MOBO clock to Universal Time. This happens automatically. Then, when you go into XP, that OS reads the MOBO clock and thinks that it is local time.

So, despite your conclusion, this is very much a Windows issue. It is, in fact, another instance in a long line of Windows design insanity. Since the convention among those serious about time is to offset everything from UTC, it makes no sense to base any OS on local time. I would suggest that you change a registery entry in XP so that it bases it's timekeeping in UTC. Instructions [here]("http://askubuntu.com/questions/232405/how-do-i-set-my-clock-in-windows-to-utc-localtime").

On a related matter, if you are still dual booting XP, you are basically pointing a gun to your head and playing Russian roulette. XP was buried with very few tears about a year ago and is no longer supported. Given that it has more security holes than Swiss cheese and is the favourite target of every cracker in creation, you are just begging to get owned.

If you still want to run XP (as I do), then I would suggest doing so in a virtual machine that you have backed up and snapshotted eight ways to Sunday. You should also sandbox it by running it without a virtual NIC so that it has absolutely no way of interacting with the outside world. Properly safeguarded, you can still use any of your old XP programs, so long as they don't access anything outside. It's a far better way to head off what would otherwise be an open invitation to disaster.

---

### Post by Impavidus on 2015-03-24
It's best to have the mobo clock run on UTC. Imagine what would happen if multiboot 8 systems, have the clock on EST and all 8 systems want to change it to DST. You would end up using Moscow time. Obviously, Windows wasn't designed with multiboot in mind.

But you can instruct Ubuntu/Lubuntu to use local time for the mobo clock. When installing a dual boot system with Windows, this is the default. As you say that you select which OS to boot using the BIOS, I assume you had the Windows drive disconnected during installation, so the Lubuntu installer didn't detect Windows and used UTC by default. To change the setting, open the file **/etc/default/rcS** and change the line **UTC=yes** to **UTC=no**.```
sudo nano /etc/default/rcS

#Change
UTC=yes
#To
UTC=no
```Works fine most of the time, but there may be anomalies when changing to/from DST.

---

### Post by t9rfbb on 2015-03-25
**kerry_s**
Thanks for the suggestion. I'll defiitely look into changing the clock but after I try a few other things. Trying to keep this Lubuntu install as vanilla as possible till I feel more at home with Linux.

**DuckHook**
Thanks for the pointers. Very educational. Haven't had a chance to check your link about setting Windows to use UTC but will probably use that solution for now. As far as Microsoft abandoning XP I'm comfortable with that. Appreciate your tips re security. We actually have a few machines running XP here which we refer to as teflon PCs becaause nothing sticks to them. Screw it up or get a virus and just reboot. Using Enhanced Write Filter on custom nLite XP Pro. And your suggestion of virtual machine is exactly where I intend to go. I'm planning to build a machine (for myself) with many cores and lots of ram that can flip between running virtual machines as well as real-time video editing. Probably use some version of linux for host. Still a long ways to go before I feel I know enough to start that project. Incidentally we also run Win 7 and 8, and argh! one Vista.

**Impavidus**
Yes, the Windows drive was not present when I installed Lubuntu. I have read that Intalling a linux varient on top of a windows drive will create a dual boot option but that was not my interest. I wanted to keep the two apart. So, thank for the tip about getting Lubuntu to use the system clock but I would prefer it get the updates from the NTP server.

Thank you all for the fast replies and good info. I am looking forward to becoming more competant with linux in general. May not get a chance to try out your suggestions before the weekend, but will get back with my end result once I do.

---

### Post by nerdtron on 2015-03-25
It's better to use Impadivus suggestion since that setting should have been adjusted automatically if only Lubuntu detected the windows drive during the installation. And also using the NTP server may help sync but NTP won't make you jump +/-4hrs instantly so you won't imeediately see the result.
Goodluck!

---

### Post by t9rfbb on 2015-03-25
**nerdtron**
Your post motivated me to look into this further. I found the following info on a forum at Sysinternals from 2010 regarding UTC in Windows XP.
[INDENT]"The problem is that if the computer goes into Standby, then when it wakes from Standby, the time is displayed UTC time rather than as local time; i.e., the system doesn't seem to apply the UTC offset.  If you simply run w32tm /resync, then the error is corrected. Apparently the bug is in how XP re-initializes the system when you come out of Standby."
[/INDENT]

Further reading suggests that the problem was resolved in Win 7 (and I assume therefor 8) and was an issue in Vista until Microsot provided a patch.

Others noted that changing XP to UTC also means that when looking at the system clock in BIOS one would have to remember to mentally apply the local offset for the correct local time.

So I've decided not to edit the XP registry to enable UTC as I may move this Lubuntu drive to more than one PC. instead I will edit the Lubuntu file as Impavidus suggested and you recommend. Life will be simpler. My reticence to do that has mostly to do with being so new to linux and even understanding what to many of you is simple and taken for granted like "sudo nano".

Thanks for the push.

---

### Post by DuckHook on 2015-03-25
I agree that if the majority of your computing life is in Windows machines, that you should conform to Windows conventions (no matter how loony). Good to hear you've found the fix.

Happy Lubuntuing!

---

### Post by t9rfbb on 2015-03-25
Just a quick follow-up. After changing RUN=no in /etc/default/rcS all is well and the system clock does not do the four hour jump regardless whether booting Lubuntu or XP.

I did have to learn how to get write privelege to save the edited file.

I used LXterminal, entered sudo -i, then my password, then pcmanfm, then using the file manager browsed to the file, doubled clicked to open it, did the edit, and was able to do a save. Wow! Way different from being admin in Windows environment with 'God' rights.  :-)

---

### Post by DuckHook on 2015-03-25
> **t9rfbb said:**
> Wow! Way different from being admin in Windows environment with 'God' rights.  :-)Yes, at first it seems obscure, convoluted and a real bother. Seemed that way to me too, way back when. But I soon realized that it was procedures like these that did away with the need for anti-virus, anti-spam, anti-malware and antibiotics of all kinds. It's been close to 20 years now, and I'm still happy I made that trade.

At some point, you will be comfortable just doing:```
sudo nano /etc/default.rcS
```...but until then, I must say that you pick up very quickly. You have a good and exciting future ahead of you exploring Linux.

---

