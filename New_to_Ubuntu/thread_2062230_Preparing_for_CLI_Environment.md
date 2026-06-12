---
title: "Preparing for CLI Environment"
date: 2012-09-24
forum: New to Ubuntu
---

### Post by sooqing on 2012-09-24
Hi everyone

After a few years, I realise that I have been using less GUI and more of CLI to do daily stuffs like copying, editing text files, etc... My daily job does not require the use of a computer. As such, with an Ultrabook given recently as a present and with much consideration, I have decided to move to 100% CLI environment, ie. without installing X.

I hope to be able to finish setting up and configuring the machine within the next 2 months, and members are able to help me in the process. 

Thanks everyone in advance!

My questions (This list would be updated as often as possible):

(1) Do I use the alternate ISO to install a CLI version of Ubuntu 12.04.1? I do not have a optical drive so it should be able to be written or dd to USB drive, like the desktop version.

(2) Should I choose x86 or AMD64? I have 8 GiB of RAM, though I don't see how I would even utilise 1 GiB.

(3) How do I underclock my CPU to conserse battery life, as its likely I do not need the full power of my CPU?

---

### Post by Lars Noodén on 2012-09-24
You can install a 'command line' system using the Alternate install disc image.  You might be better off thinking of it as the shell because what you are really doing is writing short program in a scripting language.  Also if you are really going text only, you might want to look into starting with a terminal multiplexer like tmux or screen.  

As far as x86 or AMD64, that depends on you system.  Which processor do you have?

---

### Post by irv on 2012-09-24
If you have your system setup the way you like (what I mean is you have all the programs you want already installed) why start all over? If you want to run without GUI, just do a [Ctrl][Alt][F2]. This will drop you to a shell with a prompt. Just login and run from there. The nice thing about doing it this way, is if you want to go back to the GUI just press [Ctrl][Alt][F7] and you will be back in the GUI.

---

### Post by sooqing on 2012-09-24
Indeed, my present set up on my home _desktop_ is okay. I am planning to replicate the same to a new laptop, difference is that I would not be installing X.

After 6 or 12 months of pure CLI usage, if I am satisfied I can survive without a GUI, I would repeat the same for my desktop.

Sorry that I am a bit of purist.

---

### Post by jerrrys on 2012-09-24
Ever check out [TUI's]("http://en.wikipedia.org/wiki/Text_user_interface") like [xmonad]("http://xmonad.org/").

---

### Post by JKyleOKC on 2012-09-24
It used to be possible to avoid loading the X Windows server, at boot time, by passing the kernel parameter "text" in grub. I don't know if that is still true or not, but it would be worth trying. You can edit the /etc/defaults/grub file, as the super user, and replace the "quiet splash" phrase you find there with "text" then run update-grub and reboot to test it. Make a backup copy of the file first, just in case it fails to work and you have to bail out...

---

### Post by Cheesemill on 2012-09-24
> **sooqing said:**
> (1) Do I use the alternate ISO to install a CLI version of Ubuntu 12.04.1? I do not have a optical drive so it should be able to be written or dd to USB drive, like the desktop version.
You could use the Alternative ISO but instead I would recommend using the Mini ISO. If you use the Alternative you will still need to upgrade a lot of the packages that you have just installed whereas the Mini ISO downloads all of its installation packages directly from the internet so you start off with all of the latest versions.
[http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/mini.iso)

(Also from 12.10 onwards the Alternative CD has been dropped and will no longer be an option)

> (2) Should I choose x86 or AMD64? I have 8 GiB of RAM, though I don't see how I would even utilise 1 GiB.
If your hardware supports 64-bit (which it does) then there is no reason to even consider installing the 32-bit version of Ubuntu, you would effectively be throttling your machine with old-school technology.

---

### Post by cortman on 2012-09-24
Check out screen/fbterm/emacs for x-less window management.

---

### Post by doktorOblivion on 2012-09-24
Yes, you should be able to create a usb bootable drive using something like LinuxLive USB Creator.  I found this tool very useful, but be prepared to erase anything that might be on the usb drive.

[http://www.linuxliveusb.com/]("http://www.linuxliveusb.com/")

---

### Post by jerrrys on 2012-09-24
> **Cheesemill said:**
> (Also from 12.10 onwards the Alternative CD has been dropped and will no longer be an option)

Yes, but the mini.iso lives on, right :confused:

---

### Post by doktorOblivion on 2012-09-24
Yes, of course.  However, not all distros are supported by that tool.  You have to check.

---

### Post by sooqing on 2012-09-24
Thanks everyone for your input so far.

To add on: My daily programs would be vi, wget, mc, mp123... and other hundred of scripts which I had collected over the years for tasks.

I have decided to stick to Ubuntu, coming from Slackware.

1. The lappy is 64 bit but I am not sure what benefits running a 64 bit OS have for a CLI environment. 

2. Do I need to run GMP to use my mouse if I disable X?

3. Is there a text based spreadsheet like Lotus 123 which is still being maintained?

4. As I need Internet access using both wire and wireless, is there a network manager that can manage both together?

---

### Post by Cheesemill on 2012-09-24
> **jerrrys said:**
> Yes, but the mini.iso lives on, right :confused:
Yep, it's just the Alternate that's been dropped.

---

### Post by Cheesemill on 2012-09-24
> **sooqing said:**
> 4. As I need Internet access using both wire and wireless, is there a network manager that can manage both together?
Both network-manager and wicd have CLI interfaces.

---

