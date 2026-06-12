---
title: "Can't use DVD drive - 12.04 LTS"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by keeno.1 on 2013-11-01
Hi all,

I'm about to start a university course and have received a DVD on which there are exercises, and when the time comes some exam assignments, only to find I can't open the DVD drive on my desktop computer.  It can only be opened using the trick of putting a pin in the small hole under the DVD tray.  Then, once the DVD is inserted, neither does the DVD auto-run or auto-mount.

I am currently on Ubuntu 12.04 LTS and in looking at similar threads, it seems all the above problems are common on this version.  The various terminal commands I have seen suggested in these threads didn't work either.  Can anyone suggest what steps I should be taking to be able to run DVD's now?  I also haven't been able to work out how to access DVD files by exploring the file system on Ubuntu.  Are there solutions within 12.04 LTS, should I upgrade my Ubuntu version, or do I perhaps need to buy and use an external DVD drive?

Thanks in advance for any suggestions.

---

### Post by mörgæs on 2013-11-01
Hi, welcome to the fora.

What exactly have you tried? The **eject** command?

---

### Post by BrunoLotse on 2013-11-01
> I am currently on Ubuntu 12.04 LTS and in looking at similar threads, it seems all the above problems are common on this version.Eh?Running old sony vaio with 12.04 LTS and nothing of the kind.Cheers,Bruno

---

### Post by Dennis N on 2013-11-01
Have an Xubuntu 12.04 system; I use an external USB connected DVD r/w (the computer was built w/o such a drive) for all types of disk media. No problems with it at all. Activities such as play DVD, play audio CD, rip CD, burn CD, all work correctly. You might try one if you find the built-in unsatisfactory. Mine is a Samsung.

---

### Post by deadflowr on 2013-11-01
> [COLOR=#000000] It can only be opened using the trick of putting a pin in the small hole under the DVD tray[/COLOR]

That's a mechanical problem with the dvd player, and not something Ubuntu can fix.

As far as running a dvd, it depends on what the dvd content is.
Firstly, you can see if the dvd is even readable by opening up the home folder(if you haven't moved things around the home folder is the first thing(after the dash icon) in the left side launcher; it looks like a folder.
After opening the home folder, you can look at the left-side pane and see a listing for Devices.
Even if the dvd is not opening, it will be listed in this Devices section.
If the disk is not listed, then the disk is not readable.

Now, if the disk is readable and listed in home folder, the next step is to make sure you have the codecs to read the disk.
This is all assumption on my part, as I assume the disk is a movie, so either open up the software center or run this command
```
sudo apt-get install ubuntu-restricted-extras
```
The package is ubuntu restricted extras in the software center.
Here's what else you might need to do
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Have fun.

---

### Post by keeno.1 on 2013-11-01
I have tried a lot of things including that.  The eject command beings up the following:

[I]eject: tried to use `/dev/scd0' as device name but it is no block device
eject: unable to find or open device for: `cdrom'[/I]

 Other than that I have looked around on similar threads on Ubuntu-related forums, and tried commands given in these threads ('sudo mount...') intended to mount DVD drives but got nowhere with that.  I suspect the DVD folders and files might not be in the file system.   

I have tried 'sudo lshw' in the terminal and nothing like *cdrom and *dvdrom comes up on the list.

These are examples of things I have noticed from trying commands, but I am not very experienced with terminal commands so can't really say I know what I'm doing.

---

### Post by keeno.1 on 2013-11-01
> **deadflowr said:**
> 
As far as running a dvd, it depends on what the dvd content is.
Firstly, you can see if the dvd is even readable by opening up the home folder(if you haven't moved things around the home folder is the first thing(after the dash icon) in the left side launcher; it looks like a folder.
After opening the home folder, you can look at the left-side pane and see a listing for Devices.
Even if the dvd is not opening, it will be listed in this Devices section.
If the disk is not listed, then the disk is not readable.

Thanks.  This could be part of the problem.  I have opened up the Home folder and Devices is not listed in it.  I have Home, Desktop, Documents, Music, Pictures, Videos, File System and Trash, but not Devices.

---

### Post by deadflowr on 2013-11-01
I would then assume the drive is busted.
The fact that it isn't listed and that you need to use a pin to open it supports that.

It's very rare for a drive not to have some level of support in Ubuntu.
DVD drives are somewhat generic, as they all do the same thing.

Could also be something as simple as a loose connection.

---

### Post by Dennis N on 2013-11-01
On my Xubuntu 12.04 laptop with built in dvd drive, that device is **/dev/sr0**. The same is true on the previously-mentioned desktop with the external dvd drive. Try that.

---

### Post by Dennis N on 2013-11-01
**eject /dev/sr0** ejects a disk from the drive on my 12.04 laptop. Just checked it.

---

### Post by keeno.1 on 2013-11-01
> **Dennis N said:**
> **eject /dev/sr0** ejects a disk from the drive on my 12.04 laptop. Just checked it.

Thanks Dennis.  It didn't work for me though, and I don't have an sr0 file or folder under my dev folder.

---

### Post by Dennis N on 2013-11-01
> **keeno.1 said:**
> Thanks Dennis.  It didn't work for me though, and I don't have an sr0 file or folder under my dev folder.

Sounds broken to me too. 

Suggestions:
1) buy a new internal dvd drive and replace it.
2) buy an external dvd drive with usb interface. (what I use - see post 4)
3) use another computer with a working drive if you have one.

---

### Post by Petro Dawg on 2013-11-01
You might try checking the power supply connection to the DVD drive, perhaps its loose, or the power supply isn't providing power through that particular cable.  If your power supply has a spare power cable try plugging it into the DVD player instead.  Also, you could try using the power cable going to the Hard Drive (since we know it works) to the DVD player.  You computer might not boot, but if you have power to the DVD player you should be able to eject the drive whenever the computer is on.  If changing power cables doesn't work then you know you have a bad drive as the ejection button is not at all related to the operating system installed.

If the drive works using a different cable, then you know your power supply (or the original power cable) is going bad.

Also...

You probably already know this... make sure the computer is off and unplugged from the wall outlet when plugging and unplugging the power cables to the drives in the computer.

---

### Post by keeno.1 on 2013-11-01
Thank you for all the suggestions and help everyone.  Seems to me like getting a new external USB drive might be the way to go.  The one I have is internal in my computer so shouldn't be a matter of a loose connection.

---

### Post by Petro Dawg on 2013-11-01
Probably not, but not impossible.  And I'm also trying to help you rule out the possibility of a failing power supply or bad cable as well.  Typically a bad disk drive will still show some signs of response when the ejection button is pressed.  Even if it doesn't eject, you will typically hear the drive try to turn some gears and fail, or see a light blink, or something.  If it's completely unresponsive, there might be other issues.  Its good to rule out as much as possible before buying new parts in my opinion. 

When you hit the eject button does the drive make a sound or do anything at all?

---

### Post by whitesmith on 2013-11-01
> **Dennis N said:**
> **eject /dev/sr0** ejects a disk from the drive on my 12.04 laptop. Just checked it.Well, at least *something* works. Have you tried playing a CD or video to see if the failure replicates--as it almost certainly will. Optical drives are so cheap today you can get top-of-the-line for $50 or so. I like to do this from time to time, switch from hardware to software (my specialty) and back again--that seems to keep current flow optimized between synapses.

---

### Post by mörgæs on 2013-11-02
You could also salvage a DVD drive from a scrap computer. The drives are standard bricks and easy to swap.

---

