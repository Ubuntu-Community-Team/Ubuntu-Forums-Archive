---
title: "Random crashes - will provide logs"
date: 2014-03-12
forum: New to Ubuntu
---

### Post by KyleCo on 2014-03-12
Hello and thanks in advance for the help!

I installed Ubuntu 13.10 on my machine(custom built hardware) and I get very random crashes that happen all the time. It is difficult for me to go more than a day without my system hard freezing. By this I mean that the system does not recognize keyboard or mouse commands and requires me to hard reset my machine. I have very few applications installed, mainly just Plex Media Server. I do not believe that Plex is the culprit, as I can stream multiple shows/movies to multiple devices and have it refresh the library without any issues. I've also got TeamViewer installed for remote access. I've looked over the logs in the system log app but cannot see anything at the time of crash. I have been struggling with this for over a month now, trying to squash a bug here and a bug there with to positive results. I've ran a mem test and everything passes. I've tried a fresh install multiple times and continue to have this problem. I am more than willing to provide logs and anything else that will help troubleshoot this. I'm just looking for a little guidance. I have done a lot of research on this and will research anything I need to from your responses, I'm not looking for handouts, just guidance. I am quite knowledgeable with computers and know basic programming, but I am stumped with this!

If anyone could even point me a better log to look at, it would be greatly appreciated. I'm not sure which logs you might need, but will reply with the logs attached ASAP as soon as someone recommends one.

Logs I've looked at:
sys.log(spent the most time with, googled many issues here only to find they are common/insignificant)
Xorg.log
udev
kern.log(had trouble reading, don't rule this out)

I've tried implementing linux-crashdump from here [https://wiki.ubuntu.com/Kernel/CrashdumpRecipe?action=show&redirect=KernelTeam%2FCrashdumpRecipe](https://wiki.ubuntu.com/Kernel/CrashdumpRecipe?action=show&redirect=KernelTeam%2FCrashdumpRecipe) but could not get it to work.

Thanks again, I work cellular retail and know how annoying noobs are with things :) I'm willing to put in the work, just need to know where the road is.

Kyle

Edit: Might be helpful to know it's Gnome Ubuntu and I have an Nvidia Graphics Card 660Ti. Tried every single graphics driver including nouveau (from my researching it seems likely its a graphics issue? So I wanted to include this right away) Thanks

---

### Post by tgalati4 on 2014-03-13
First, validate your RAM.  Run memtest for 30 complete cycles--it will take several hours.  Then test your power supply for correct voltage--either check the levels in BIOS or use a voltmeter.  Don't bother with the log files until you have the hardware sorted out.  The log files will just leave you baffled because hardware faults leave inconsistent error messages.

---

### Post by KyleCo on 2014-03-13
Thanks for the reply. I will run a memtest again. Mine had said 1 pass when I ran it, is this the same as a cycle(so do 30 "passes")?

I do want to mention that I was running Windows 7 for about a year without issue. And did boot Windows 7 since installing Ubuntu and had no problems. I'm not sure if that sorts out my hardware, but I will begin with the memtest right now.

---

### Post by matt_symes on 2014-03-13
Hi

As stated, check the hardware first !

After that, check to see if X or Gnome is crashing, or if it is the kernel that is crashing on you.

After a crash, instead of resetting, try getting to a console (ALT + F1). Can you get to a console ?

If so, restart Gnome fron the console.

```
sudo service lightdm restart
```

If you can't get to a console, then try the magic key combination to safely reboot.

Press and hold:

```
ALT + SySRq
```, then hit these keys one after another

```
R E I S U B
```

Leave a couple of seconds between key each press. Practice the key presses before it crashes so you know you are doing it correctly when it does crash.

Does it reboot successfully ?

These actions may help point us in the right direction.

But as already stated, check the hardware first..... and then check the hardware again.

Kind regards

---

### Post by tgalati4 on 2014-03-13
Well, dual-booting into Win7 was a key piece of evidence that was not mentioned in the original post.

So, now let's look for a kernel issue versus a graphics card issue:

Right after a fresh linux boot, open a terminal:

```
dmesg | more
```

Spacebar to page forward, "q" to quit.

Look for any irregularities during the boot process.  Post only the entries that you don't understand AND you can't find a reasonable explanation on the interwebz.

---

### Post by KyleCo on 2014-03-14
Ok, I've got all the test done and I've looked at some files, so let me try and respond to everyone here.

tgalati4:
I ran all 30 passes in memtest and every one passes with no errors. I checked the voltages in bios and looked up the voltages I wasn't sure and everything checks out. My RAM is comprised of 4 sticks each 4GB. Two of them can handle 1600 and 2 can handle 1333. I set to 1333 as both have that as an option. They were already set to 1333 in bios and that's how they were when I was running Windows

matt_sysmes:
I had found those commands before on previous sites and tried them numerous times and neither ALT + F1 nor ALT + SySRq (R E I S U B) would do anything. Hard reboot via power button was the only way to get it back up.

tgalati4: 
I'm not dual booting Windows with Ubuntu. I just installed a hard drive I have with Windows already established and unplugged my Ubuntu hard drives. I'm sorry if that created any confusion. I did dmesg | more and looked through the results as best I could. A lot of gibberish to me honestly but I took my time and looked for what I would consider "errors"(ie. things not being found, 'falling back' messages, things missing) and Googled what I saw. All results were of people's systems not starting properly and the replys that referenced the logs did not reference to anything around those lines, so I assumed they were just normal kernel messages (as a few posts stated the kernel just displays those messages or 'rolls back' to something for different hardware setups). 

I've had the machine up all day and haven't had any problems yet. though the issue usually takes two or more days to appear. Any other thoughts or recommendations would be appreciated.

As a side note and learning opportunity for me, if my hardware works with Windows, could it really not work with Ubuntu under the same settings? I ask only because this hardware setup was working flawlessly under Windows 7 for over a year.

---

### Post by matt_symes on 2014-03-15
Hi

If the magic key combination does not work then that would suggest a kernel panic for some reason.

Can you pin point any task you are doing when it freezes ?

Looking at the logs would be the way forward. 

You could also try removing the hardware, an item at a time, to see if that is the cause of the problem.

Kind regards

---

### Post by tgalati4 on 2014-03-15
When booted into Ubuntu, what is the SMART status of the disk drive?  I'm thinking that the disk drive has intermittent faults.

```
sudo smartctl -a /dev/sda
```

---

### Post by KyleCo on 2014-03-15
matt_symes:
The only programs I really have on here are Plex Media Server and TeamViewer, both of which run all the time. I  can use TeamViewer just fine, it's when I'm not using the computer freezes. Plex on the other hand, I can use all day/night w/o issue, and the system will freeze when no one is using Plex. Or I can be using Plex and it can freeze part through my show. So I cannot find a way to duplicate the issue. I could probably have fixed it if I could :(

What logs would be good to look at? I'm not really familiar with the naming scheme and what log gives the input of what.

tgalati:
When I tried running sudo smartctl -a /dev/sda I got "sudo: smartctl: command not found". I did a google search and saw that it was part of smartmontools, so I installed that. During the install, it displayed:

"Suggested packages:
  exim4 mail-transport-agent gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils"

mailx was not found and mail-transport-agent gave this:

"Package mail-transport-agent is a virtual package provided by:
  dma:i386 0.9-1
  xmail 1.27-1.1build1
  ssmtp 2.64-7
  sendmail-bin 8.14.4-2.1ubuntu4
  qmail-run 2.0.2
  nullmailer 1:1.11-2
  msmtp-mta 1.4.31-1
  masqmail 0.3.4-1
  esmtp-run 1.2-10
  dma 0.9-1
  courier-mta 0.68.2-1ubuntu1
  citadel-mta 8.16-1ubuntu1
  postfix 2.10.2-1
  lsb-invalid-mta 4.1+Debian11ubuntu4
  exim4-daemon-light 4.80-7ubuntu3
  exim4-daemon-heavy 4.80-7ubuntu3"

I'm not familiar with any of those, so I skipped that. not sure if I need mail-transport-agent, and if so what package? After all that, I was able to run the smartctl command and saw no errors. I do have a lot more drives than just sda, and ran on all of them, all checked out with SMART capabilities on and no errors found.


I haven't had any crash's since doing the memtest, but are there some logs that i should make sure to save when it crashes again? Are all the logs saved across a hard reboot?

Thank you everyone! I greatly appreciate the help!

---

### Post by tgalati4 on 2014-03-15
You don't need the mail agent.  It sends you messages if you have a failing disk--useful for servers.  Log files are generally saved, but depending on the crash they may or may not be useful.  What is useful is to have an ssh session going from another computer into the sick computer.  When it freezes, check the ssh session and see if it is still alive from the other computer.  If so, then you have an X-session freeze, or desktop environment freeze, or a graphics card freeze, but the kernel can still be running and you can do some troubleshooting from the commandline.

Time to inspect the motherboard for bulging or leaking capacitors.  Reseat the graphics card.  Check the temperature of the graphics card:

```
sensors
```

---

### Post by KyleCo on 2014-03-15
I had another lockup. This time I was streaming a movie to my chromecast using plex with transmission and chrome beta open. My mouse worked, but I was unable to actually click anything. The keyboard's lights were on and the caps lock/num key lights responded. The magic key combination did nothing for me. neither did Alt + F1. 

This is what sensors gives me after I reset the graphics card:

kyle@kyle-OEM:~$ sensorsacpitz-virtual-0
Adapter: Virtual device
temp1:        +23.0°C  (crit = +6280.3°C)


coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +34.0°C  (high = +81.0°C, crit = +101.0°C)
Core 1:       +40.0°C  (high = +81.0°C, crit = +101.0°C)
Core 2:       +38.0°C  (high = +81.0°C, crit = +101.0°C)
Core 8:       +38.0°C  (high = +81.0°C, crit = +101.0°C)
Core 9:       +38.0°C  (high = +81.0°C, crit = +101.0°C)
Core 10:      +39.0°C  (high = +81.0°C, crit = +101.0°C)


Not sure which one of those is the graphics card

EDIT: I am streaming using my tablet through Plex, so chrome is not doing anything with anything chromecast.

---

### Post by matt_symes on 2014-03-16
Hi

If the keyboard caps key responds, it may not be a kernel crash.

I'm surprised that the magic key combination is not working. Maybe it's disabled on your machine ?

what's the ouput of 

```
cat /proc/sys/kernel/sysrq
```

If it's non zero and not empty it should be enabled.

Your temps look fine so it's beginning to look like your hardware may be alright. 

Did you try to ssh into the machine and have you had a visual inspection of the board ?

What do your logs say ?

Kind regards

---

### Post by Jonathan_Lundstr on 2014-12-25
Hello!

I'm having this exact same issue as your were describing. Although, when my machine crashes, the LCD on my case also goes dark, and it does not respond to any keyboard interaction, nor network access like SSH. These issues started occurring when I updated from 11.10 to 13.10, and I'm now running 14.04LTS with the same issues. My server seems to completely freeze at random times. I'm only running Plex, Samba, Netatalk and Apache/PHP etc. I would be stoked if you could shed some light on the issue, and if/how you managed to resolve it. If not, I'll have to do a complete reinstall of my server.

Thanks in advance!

Regards,
Jonathan

---

