---
title: "Alert signal"
date: 2011-11-27
forum: Programming Talk
---

### Post by Stovey on 2011-11-27
Hi everyone!  My alert signal doesn't seem to be working.  It is enabled in "sound settings" even giving options for bark, ding, drip, etc... My computer doesn't beep when I type:

echo -e "\a" 

Is something broken?  Am I doing something wrong?  I am working through the Bash script tutorial in my signature.

---

### Post by crdlb on 2011-11-27
in Sound Settings, is Alert Volume set and not muted? If so, does pressing Backspace at an empty prompt make the alert sound? If not, check the "Terminal bell" setting in gnome-terminal (or your terminal of choice).

---

### Post by Stovey on 2011-11-28
Hi crdlb.  Thanks, I wasn't really aware of the terminal settings.  All the settings look good, I should really be hearing a bell!  Maybe this is a bug with my system?

Alert volume: slider at about midway
Mute: box not checked
Backspace at empty prompt: no sound
Terminal bell setting: box checked

---

### Post by Arndt on 2011-11-28
> **Stovey said:**
> Hi crdlb.  Thanks, I wasn't really aware of the terminal settings.  All the settings look good, I should really be hearing a bell!  Maybe this is a bug with my system?

Alert volume: slider at about midway
Mute: box not checked
Backspace at empty prompt: no sound
Terminal bell setting: box checked

Is it completely silent? My computer emits a click when it's supposed to beep, and this has been the case since I installed Ubuntu two years ago. During one release, it worked but then stopped again.

Once, when I experimented with generating sine waves programmatically and playing them, I found that I got that same click in some circumstances, something to do with left and right channels. But my computer is able to play sine waves, I know that much.

---

### Post by Stovey on 2011-11-28
> **Arndt said:**
> Is it completely silent?...

Yes, it's completely silent, not even a click.

---

### Post by emiller12345 on 2011-11-29
if your system is using ALSA, you can access some settings from the command line...
```
$ alsamixer
```
you can press 'esc' to exit
one of the items may be beep, which can be muted/unmuted with the 'm' key

---

### Post by Bodsda on 2011-11-29
Double check that it isnt blacklisted

Open the file '/etc/modprobe.d/blacklist' and look for a line like 'blacklist pcspkr'

---

### Post by Stovey on 2011-11-29
Thanks everyone.  Sure enough the beep and the speaker were muted in the Alsamixer.  I enabled them, but still no beep!
 
Here are the files in modprobe.d:

    alsa-base.conf
    blacklist-ath_pci.conf
    blacklist.conf
    blacklist-cups-usblp.conf
    blacklist-firewire.conf
    blacklist-framebuffer.conf
    blacklist-modem.conf
    blacklist-oss.conf
    blacklist-rare-network.conf
    blacklist-watchdog.conf

I looked at alsa-base but it didn't really make sense to me.

The blacklist-oss is a dynamic link:

    lrwxrwxrwx 1 root root 41 2011-10-13 17:07 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf

Would you mind explaining to me what modprobe is?  I'm new at this.  It looks maybe like a workaround for hardware incompatible with the OS?

---

### Post by Bodsda on 2011-11-29
> **Stovey said:**
> Thanks everyone.  Sure enough the beep and the speaker were muted in the Alsamixer.  I enabled them, but still no beep!
 
Here are the files in modprobe.d:

    alsa-base.conf
    blacklist-ath_pci.conf
    blacklist.conf
    blacklist-cups-usblp.conf
    blacklist-firewire.conf
    blacklist-framebuffer.conf
    blacklist-modem.conf
    blacklist-oss.conf
    blacklist-rare-network.conf
    blacklist-watchdog.conf

I looked at alsa-base but it didn't really make sense to me.

The blacklist-oss is a dynamic link:

    lrwxrwxrwx 1 root root 41 2011-10-13 17:07 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf

Would you mind explaining to me what modprobe is?  I'm new at this.  It looks maybe like a workaround for hardware incompatible with the OS?

Are you sure you mean the modeprobe.d file not the blacklist file?

The blacklist file is used to blacklist certain loadable kernel modules. The pcspkr is the most common entry people ask about. Usually because they want to turn it off! :)

---

### Post by emiller12345 on 2011-11-29
> **Stovey said:**
> Thanks everyone.  Sure enough the beep and the speaker were muted in the Alsamixer.  I enabled them, but still no beep!
 

FYI, although you may be expecting 'beep' to come from an internal speaker hidden inside the computer, it will probably be outputted from your computers external speakers. Make sure you have speakers attached and the volume is turned up.

---

### Post by Stovey on 2011-11-29
Yeah, I was expecting it to beep through the internal speakers (and I wondered if it wasn't beeping because external speakers are attached).  So I have been checking for the beep with speakers plugged and unplugged.  Both speakers work for sure.

---

### Post by emiller12345 on 2011-11-29
> **Stovey said:**
> Yeah, I was expecting it to beep through the internal speakers (and I wondered if it wasn't beeping because external speakers are attached).  So I have been checking for the beep with speakers plugged and unplugged.  Both speakers work for sure.
you may consider checking out a package in the repos called beep (sudo apt-get install beep). it's the easiest way (that I know of) to test a beep.

---

### Post by F.G. on 2011-11-29
so, i've never got the 'bell' ('\a') to make a sound using Ubuntu, or other distros. does seem to work fin in Windows though.

---

### Post by creator101 on 2011-11-30
I don't remember this off the top of my head, but this command might work:

org.gnome.desktop.sound event-sounds true

---

### Post by jwbrase on 2011-12-01
I'm having a similar problem: echo -e "\a" doesn't work at first, but beep does. If I switch from Compiz to Metacity, then echo -e "\a" works, and if I switch back, it also works. But it doesn't seem to work when Compiz first starts up.

An incidental annoyance here is that there doesn't seem to be any way to get Compiz to use a sound file rather than the system beep like Metacity does (aside from compiling and installing a plugin off the web that seems to need Compiz 0.9, which is unavailable on Lucid). Metacity also plays its bell sound file through my laptops external speakers even if headphones are plugged in.

---

### Post by linfidel on 2012-01-19
I've been looking into the problem of alerts not working from a question on Stack Exchange.

His question has to do with alert beeps - there is no sound when an alert comes up, like for a question about saving a modified file.

I discovered that this is not a sound problem.  The event is not being fired from Compiz.  I discovered this by going into universal access settings, and trying to set the visual alerts for the titlebar or screen to flash on alerts.  It did nothing.

I then ran "metacity --replace", and sounds began working as expected, including the terminal.

Edit:  If you do this in Unity, I found that much of the UI will go away, and Alt-F2 doesn't seem to work.  However, other keys work, such as Alt-Ctrl-T for the terminal, and I was able to run compiz again.

---

### Post by Paddy Landau on 2012-01-20
Well, I have the same problem as Stovey. My normal alerts work absolutely fine, but not [FONT=Lucida Console]echo -e '\a'[/FONT].

I installed [FONT=Lucida Console]beep[/FONT], but it too makes no sound!

---

### Post by CoffeeRain on 2012-01-20
Did you try all of the suggestions?

---

### Post by Paddy Landau on 2012-01-20
> **CoffeeRain said:**
> Did you try all of the suggestions?
:redface: I thought I had, but I had missed the blacklist.

I did the blacklist, and now [FONT=Lucida Console]beep[/FONT] works. (However, [FONT=Lucida Console]echo -e '\a'[/FONT] does not.)

Thank you.

---

### Post by linfidel on 2012-01-20
I entered a bug report into the Compiz bugzilla ([Bug #70]("http://bugs.compiz.org/show_bug.cgi?id=70")).  So far, no response at all, but hopefully someone will see it and either comment on it or fix it.

But as I said, this is not a sound problem; the event that produces the sound, or visual cue, is somehow getting lost or not sent in Compiz.  Metacity works as expected.

---

### Post by linfidel on 2012-01-20
> **Paddy Landau said:**
> Well, I have the same problem as Stovey. My normal alerts work absolutely fine, but not [FONT=Lucida Console]echo -e '\a'[/FONT].

I installed [FONT=Lucida Console]beep[/FONT], but it too makes no sound!By normal alerts, do you mean the ones configured in the sounds settings?  If you try to exit an editor without saving the file, when you get an alert asking if you want to save, do you get the sound there?

Other programs that play a sound will work - just not the system alerts.

---

### Post by Paddy Landau on 2012-01-21
> **linfidel said:**
> By normal alerts, do you mean the ones configured in the sounds settings?  If you try to exit an editor without saving the file, when you get an alert asking if you want to save, do you get the sound there?
Ah, I think there is something I have not realised.

If I press (say) the Close button on the dialogue, it makes a sound. But if I try to close an unsaved file, there is no sound when the warning dialogue pops up.

So, it seems I also suffer from this problem.

I have had a look at the bug that you raised, but I don't see how to vote for it.

---

### Post by linfidel on 2012-01-21
> **Paddy Landau said:**
> Ah, I think there is something I have not realised.
. . .

It's pretty hard to realize the absence of a feature.  I didn't really realize it either, until I happened to get into a discussion on askubuntu.com (stackexchange forum) that made me curious. I didn't remember for sure if there were alerts or not.  I only notice something like sounds for a program such as Skype, which I really wanted to have working.

I have no idea how to really handle bug reports for Compiz.  Seems like it's hit or miss.

---

