---
title: "Linux on low-end computer..."
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Stochastics on 2008-04-28
Hi everyone,

I want to have advice for which Linux/distros i can install on a low-end computer (P4 with 256 meg of RAM and 20G of HD). It's primary use is for web browsing and text editing (openoffice). I don't want to wait one hour to have a program to start up etc...any advice ?

Thanks

---

### Post by ugm6hr on 2008-04-28
That is not too low end.

I installed Xubuntu 7.10 (8.04 should be acceptable now) on an identical machine and use it for browsing at work, with occasional spreadsheet / document editing.

Do you really need OpenOffice for text editing?  Abiword is much faster.

If you want faster - try PuppyLinux.

---

### Post by Michael.Godawski on 2008-04-28
I would suggest Xubuntu. It runs smoothly on my older machines and I also use  it on my new laptop. It is more light weighted that Ubuntu but has the same great features and is based on the same packages.

---

### Post by phr0ze on 2008-04-28
I second the vote to use Abiword versus Open office if you are on a low end machine.

---

### Post by stchman on 2008-04-28
> **Stochastics said:**
> Hi everyone,

I want to have advice for which Linux/distros i can install on a low-end computer (P4 with 256 meg of RAM and 20G of HD). It's primary use is for web browsing and text editing (openoffice). I don't want to wait one hour to have a program to start up etc...any advice ?

Thanks

I installed Puppy on my old Athlon 700 and it works great.

What speed in the P4 processor?  If is is ~1.5GHz or better then all you need is some more RAM.  256MB is the bare minimum.  I recommend going at least 512MB, maybe 1GB.  RAM is pretty cheap these days so it should not cost you that much.

---

### Post by miwaypet on 2008-04-28
Try Linux Mint. Works well on an old desktop I have. Also, advise you upgrade to at least 512 RAM, as soon as you can. Check out someplace like Tiger Direct online for prices. Good luck.

---

### Post by rubbsdecvik on 2008-04-28
I've had good luck with Xubuntu and Puppy.  Damn Small Linux is pretty good too, but it wouldn't be as polished as the other two.  DSL is mostly for running off of really small platforms like flash cards.

---

### Post by Oldsoldier2003 on 2008-04-28
Puppy FTW DSL is great for super small installations and for embedded processors

---

### Post by c4v3m4n on 2008-04-28
I also back up the guys saying that Xubuntu and abiword is the way to go.  Xubuntu runs very smoothly and abiword is a good word editor.

---

### Post by taikonaut on 2008-04-28
Definitely Xubuntu!

Got it running on an old Asus Laptop with a PIII-850 with 256MB SD-Ram and it works very smoothly!

Regards,
Taiko

---

### Post by Whiffle on 2008-04-28
I'd go for a ram upgrade.  1 GB would make that sytem just dandy for gnome or kde.

---

### Post by bobpur on 2008-04-28
Definitely Xubuntu. If you use Mint Linux get the XFCE version which will be comparable to Xubuntu. I have both running on older machines and am happy with the performance they give.

Good Luck!

---

### Post by evozniak on 2008-04-28
if you have medium knowlegment in linux world try slackware, is fasterr
if you beginner in linux try Xubuntu or fluxbuntu.

---

### Post by doorknob60 on 2008-04-28
Ignore all those people saying that you need to upgrade your RAM. Obviously it would go faster if you did, but Xubuntu runs pretty well with 256 MB of RAM. If you want, you could also try Fluxbuntu (Google it), it has a steeper learning curve, but it runs at an acceptable speed (about the same as Win98 ) on my computer with a mere 64 MB of RAM, and it's *extremely* fast on my brother's computer with 256 MB of RAM and a Celeron 1.3 ghz :)

---

### Post by linuxlizard on 2008-04-28
a p4 with 256 megs should run ubuntu just fine.

I maintain my elderly parents computer- it's an amd 1800+ with 256 megs and it runs kubuntu with beryl and the cube and all the bells and whistles just fine.

---

### Post by zaussome on 2008-04-28
z

---

### Post by anewguy on 2008-04-28
You shouldn't have any problem.  I have installed 7.10 on my PIII_500 system when it only had 256mb.  Just due to the nature of the beast it's not the fastest fly on the block, but who expected it to be?  I did the upgrade to Hardy, and also now have 512mb and an ATI 9250 video card.  I run the desktop candy with the cube, tabbed windows, wobbly windows, etc., just fine.  I have noticed that with transparent windows turned on things seem to go a little slower - I presume that's because I usually have more than 1 window opened at a time so the transparency thing is kicking in.

Really, you shouldn't have any problem.  If you, or anyone else out there, has need of an AGP FXF FX5200 with 128mb and svideo out, just pm me.  I bought the ATI card and that card on 2 seperate auctions and said whichever one came first and worked with desktop effects I was keeping - the other I wouldn't need.  The ATI card arrived a week before and works great.  I've tried to sell the other one for even 99cents plus $10 shipping on EBay but nobody bid (2 times).  So, figure out the shipping from 61081 to you, pm me, let me know how you'll pay the shipping, and it's yours.  Gratis.

---

### Post by hellomoto on 2008-04-28
I would say xubuntu too.

I have had it on my old laptop: P3 450Mhz, 192mb RAM, 10gb HD

Although now I have ubuntu 7.10 running on the above box! - Just wanted to see if it would work.... and its not to bad at all. However does take a while to boot up. But i like it because its what im used to.

---

### Post by daberger on 2008-04-28
i third

---

### Post by Vorl the Magnificent on 2008-05-22
I've had really good luck on an old pc built in the late 90's (733mhz processor, 10gb hd, but with quite a bit of RAM [900-somethingmb?]) by running a command-line version of Ubuntu Hardy with the IceWM window manager.  If you decide to try that, the Command-Line installation option is on the alternate edition of the Ubuntu install ISO/cd.  I'm not honestly sure if it's that much lighter than the full version of Ubuntu with respect to its memory/processor requirements, but I'm betting it is.

Be advised that you would have to download lots of the packages that you'll be wanting manually (e.g., icewm, firefox, abiword, the various components of the openoffice packet, etc) via the "sudo apt-get install" command, and you will be doing a lot of config file editing for both the BASH shell and the IceWM manager.  Last time I set this computer up, for example, the themes files for the IceWM package I installed from the Ubuntu repositories were broken, and I had to replace them with IceWM themes files from a Gutsy Gibbon (7.10) install (that's the workaround on the Launchpad bug reporting website, anyway, and it worked well).  Also, most of the themes you'll want from themes.freshmeat.net will require (especially if, like me, you're fussy about colors and icons and menus) some modification.  There's lots of info on this on these forums, on the IceWM site, and in other places (google specific issues; some poking about usually works).

I will also say, without condescension, that if all this is essentially gibberish or looks unpleasantly complicated and time-consuming (which, at points, it really is), I would recommend the Xubuntu installation.  Ultimately, though, the IceWM window manager is very light, and offers the means to use good programs from an extremely useable GUI environment.

On another note: for whatever system you're running, I would recommend the Dillo web browser for the reading of simple pages and for other undemanding tasks such as google searches.  I wouldn't trust it for webmail or for the display of complex sites, but it's very fast and small, and renders Wikipedia pages quite well.

If anyone's interested in the command line/IceWM option for a lower-end system, I can post some configuration instructions/suggestions.

--VoTMagn

---

### Post by ahmatti on 2008-05-22
You could also give FreeBSD a go with some lightweight window manager, I prefer openbox but fluxbox or icewm are OK too. You can get a really fast and responsive system, but you'll need a lot more manual tweaking than in Ubuntu...

---

### Post by ugm6hr on 2008-05-22
> **Vorl the Magnificent said:**
> If anyone's interested in the command line/IceWM option for a lower-end system, I can post some configuration instructions/suggestions.

There are always people asking for this advice.  An up-to-date Hardy How-To would be great.

For example: [http://ubuntuforums.org/showthread.php?t=799814&page=3](http://ubuntuforums.org/showthread.php?t=799814&page=3)

---

### Post by Inxsible on 2008-05-22
I second ugm6hr.

I am planning to install a minimal with IceWM or Fluxbox as a dual boot with my Xubuntu on a P3-1.1GHz, 256MB RAM 30GB HDD.

I would love to have a nice howto - as opposed to scanning a million different pages.

I still haven't decided on IceWM/ Fluxbox/Enlightenment.

I guess I will use each one and see which fits me best. But as far as the "look" (from screenshots) goes, all three are pretty good.

---

### Post by ugm6hr on 2008-05-22
> **Inxsible said:**
> I am planning to install a minimal with IceWM or Fluxbox as a dual boot with my Xubuntu on a P3-1.1GHz, 256MB RAM 30GB HDD.

I would love to have a nice howto - as opposed to scanning a million different pages.

The problems are things like choosing a desktop manager, file manager, networking applet, USB-mounting app, decent looking theme, editing menus, startup apps....

I tried aysiu's advice ([http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)) on an old desktop that I have since given away with Xubuntu, because I decided that trying to configure everything was too confusing!

As for enlightenment, there is a How-to to mimic gOS out there, and another by Rui Pais (I believe a developer of OzOS) here: [http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

---

### Post by Inxsible on 2008-05-22
> **ugm6hr said:**
> The problems are things like choosing a desktop manager, file manager, networking applet, USB-mounting app, decent looking theme, editing menus, startup apps....

I tried aysiu's advice ([http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)) on an old desktop that I have since given away with Xubuntu, because I decided that trying to configure everything was too confusing!

As for enlightenment, there is a How-to to mimic gOS out there, and another by Rui Pais (I believe a developer of OzOS) here: [http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)
That's why I thought I would go in for a dual boot with Xubuntu and minimal with Ice/Flux/E

But i just booted with a minimal CD and there is no way to tell it to install in a specific partition. I guess I will have to download the alternate or server cd and then install a command line and go from there.

My Xubuntu runs a little on the slower side. I do have xfwm4 running as my compositor - only because I have AWN as my dock. I should probably try and minimize all the effects of xfwm and see if it gives me any speed increase. 

I would really like to use AWN - so I do need a compositor. We'll see !!

---

### Post by Vorl the Magnificent on 2008-05-26
I don't feel qualified a how-to just yet: my situation is very specific, I'm pretty new to Linux, and I have fairly limited applications for my old computer.  Secondly, you wouldn't really trust a how-to from a guy who couldn't get his sound card to work, right?  (that's the only major problem I'm still having).

First: if this post is too long, I apologize.  Please tell me where posts like this best belong, and I will refrain from putting them into existing threads in the future.  Still new in these forums (and forums in general).

**Premise/Basic Ideas**
I was interested in configuring an old computer to do some basic computing, and I didn't want to load it down with Gnome or KDE.  I also wanted to drop to the honest-to-god command line to play Infocom games via frotz, and to learn how to move files and carry out other basic functions without a gui.

My computer has two usb inputs, a standard old cdrom and a floppy, an ethernet card, a 733mhz pentium III processor, @900mb ram cannibalized from other sources, and a 20gb hard drive (as it turns out, it's larger than I recalled).  It is used by a single person with a single login on a wired home network wherein all pcs connect to the interwebs via a single router.

Here is the sequence of steps I use to set up a box using Ubuntu 8.04 Command Line install and the IceWM window manager.  My directions may skip steps or prove unnecessary, but they've worked for me.  Comments and clarifications are welcomed.

**First, install Ubuntu 8.04 as a command line system.**  Do this by (1) downloading the alternate install CD from Ubuntu/Canonical and burning it to disc via some other functional computer, (2) inserting it into your cdrom and booting from it, and (3) selecting the other options/alternate installation option (press f4 or some other function key at the install menu), selecting "install command-line system," and then (4) telling the disc to install ubuntu.  The exact menus may differ slightly, but this provides the general idea.  Installation itself is fairly straightforward, and proceeds via a text-based interface.

Once the installer brings you to the partitioning/formatting stage, you have the option to create an encrypted volume for installing your system, which is one of the advantages of the Alternate Install disc.  If you do this, you will have to create a volume password, which you will be required to enter during the early stages of booting--each and every time you boot.

When asked by the installer, choose username and password.  Choose the password carefully: you will use it frequently for performing tasks as the superuser (via sudo).  For the purposes of this discussion, the login name and home directory name will be "billy".

Once the system is up and running, log in.  You will find yourself at the command line, and ready to begin configuring your system.

[B]1.  Edit the GRUB menu to your tastes.
[/B]Personally, I like to bypass the GRUB menu entirely and get on with a verbose, normal boot.  If you ever have to do a system recovery, you can simply boot from a live cd and change the GRUB menu file to allow you back in to do a recovery boot.  Here's what I do with my GRUB menu.lst file:

Use the nano text editor to edit grub to remove loading pause & make boot verbose.
```
sudo nano /boot/grub/menu.lst

```You'll be prompted to enter your password, as with all sudo commands. In first boot entry near the bottom of the file, find the first boot choice.  It will look something like this:
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=/dev/mapper/CLIbuntu-root ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
quiet
```
copy the kernel line, paste it, and edit it to choice. (copy: meta+6.  paste: ctrl+u).  Remove all items around the boot entry such as "quiet" & "splash" so that the block ends up looking like this:
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-16-generic root=/dev/mapper/CLIbuntu-root ro
#kernel	/vmlinuz-2.6.24-16-generic root=/dev/mapper/CLIbuntu-root ro quiet splash
initrd		/initrd.img-2.6.24-16-generic
#quiet
```
Press ctrl+o to save, and exit nano.

**2. Set computer to set numlock key, clear screen upon login, and prevent screen from blanking after a period of time.**
```
sudo nano /home/billy/.bashrc

```Just above the final "fi", enter the following two lines:
```
setleds +num
setterm -powersave off -blank 0
clear
```
Save and exit.

**3. Prevent your computer from ever making a beeping noise.**
```
sudo nano /etc/modprobe.d/blacklist
```
add the line
```
blacklist pcspkr
```
to the end of the file.  Save and exit.
[B]
4. Edit /etc/fstab to mount a second, ext3 hard disk at startup.[/B]  (If you're using an ntfs, fat16, fat32, or other format of hd, you'll need to research what kind of fstab entry you'll need.)
```
sudo nano /etc/fstab
```
Add this line at the end:
```
/dev/sdb1 /media/ext3hd ext3 users,rw,auto 0 0 

```Save and exit.

**5. create mount directories for second hard drive and your flash drives (the latter of which we'll talk about soon):**
```
cd /media
sudo mkdir ext3hd
sudo mkdir usbflash

```
**6. install desired programs and packages** (for me, these include graphic interface [xorg and icewm], productivity software [openoffice progs, abiword, mousepad, evince-gtk{pdf reader}], internet browsers [firefox, dillo], ftp software [filezilla], newsgroup reader [pan], a lightish file manager [thunar], a program to set numlock once I enter Icewm [numlockx], and some games [kq, cuyo, bastet]).
```
sudo apt-get install xorg numlockx frotz thunar abiword mousepad icewm dillo pan filezilla deluge-torrent kq cuyo bastet evince-gtk firefox xfce4-icon-theme tango-icon-theme openoffice.org openoffice.org-writer openoffice.org-calc openoffice.org-impress

```
**7. (OPTIONAL) Install & Configure podencoder** (a program for converting movies into .mp4 files for the video ipod) and its required programs.
```
sudo apt-get install lsdvd mplayer mencoder gpac zenity

```put podencoder script (from [HTML]http://diveintomark.org/public/2007/06/podencoder.txt[/HTML]) file in home directory.  See [HTML]http://diveintomark.org/archives/2007/06/07/howto-batch-encode-video-for-ipod-under-linux-2007-edition[/HTML] for an explanation.
Create .podencoderrc in home directory, containing these lines:
```
outputdir=/[absolute path for your chosen directory for the mp4 files]
scratchdir=/[absolute path for your chosen directory for the work product of podencoder]

```
```
sudo nano .bashrc

```
Add this line as an alias, so that you can podencoder it up from any directory:
```
alias podencoder='/home/[username]/podencoder'

```	
**8. (OPTIONAL) Add aliases for graphic user interface and for manually updating the "locate" command's database**.  This will allow you to type either "gui" or "startx" to go into your x-session, or graphical user interface, which should now default to the IceWM window manager.  (Aliases are essentially different, often shorter, names for specific commands that you specify.  If you had a long, complicated command that you used frequently, such as "sudo farkle -t aiden.000015.337 anaheim -SHOE => dev null," you could create an alias for it called "farkle.aiden", or anything else that's reasonably specific.  This would allow you to type "farkle.aiden" and run the whole, lengthy command.)  Anyway, 
```
nano .bashrc

```Add these lines near the end where you find other commented aliases:
```
alias gui='startx'
alias refreshdb='sudo /etc/cron.daily/mlocate'

```
9. Update "locate" command so you can effectively use "locate" to find files later on.
```
sudo /etc/cron.daily/mlocate

```
[or, if you've restarted already and created the "updatedb" alias, just use the updatedb command from your previously created alias.]
[B]
10. (OPTIONAL) Set your icon themes for the Thunar file manager.[/B]
```
nano .gtkrc_2.0

```
add these lines:
```
gtk-icon-theme-name = "Tango"
#gtk-icon-theme-name = "Rodent"
#gtk-icon-theme-name="Gnome"

```
[as always, the lines starting with "#" are not read: they are commented out ]

**11. Configure icewm.**
***11.1 Correct Ubuntu 8.04's problems with the icewm themes*** (e.g., the window button graphics issues you may notice if you login) by dropping a themes folder saved from a running Ubuntu 7.10 (Gutsy Gibbon) icewm install into /usr/share/icewm (after deleting the existing "themes" folder).  You can also just use the themes I've saved and modified.  Download the tarball (tar archive)  at  my skydrive public folder [HTML]http://cid-3fba8b9436b5548e.skydrive.live.com/browse.aspx/Public?lc=1033[/HTML].  Decompress the tarball by using the "tar" program from the command line, or using "7zip" or another archiving program in windows.  Assuming you're using your new system to get my themes, (1) get into IceWM by typing "startx" or "gui" from the command line.  Then, (2) go to Firefox, enter the url I've provided, and download the TAR file.  It should save to /home/billy/Desktop (and remember: "billy" will be replaced by your username).  Then, (3) open a terminal in IceWM by either clicking on it from the start menu, or pressing meta+t (meta=WindowsKey for many keyboards).  Once in the terminal, get to your Desktop folder by typing
```
cd /home/billy/Desktop

```
Now, (4) decompress the tar file by typing
```
tar xf icewm.themes.tar

```
Now, in the same terminal window, (5) get yourself into a superuser file manager by typing
```
sudo thunar /home/billy/Desktop

```
You will likely find yourself in your Desktop folder, looking at a "themes" folder and the file "icewm.themes.tar."  You can (6) delete that tar file now.  Next, (7) right-click on the "themes" folder and cut it (or select it and press ctrl+x) to cut it.  Next, (8) navigate in the same file manager to /usr/share/icewm/, where you'll see a "themes" folder there.  (9) Right-click it, delete the whole folder, and now (10) right-click in the empty space and (11) paste your new themes folder.

Voila.  Repaired themes.  Log out of IceWM, log back in, and select your theme from the start menu.

***11.2 Correct/edit menus pertaining to existing programs and icewm behaviors.***
I won't go into a great deal of detail here, because everyone has different preferences with respect to how they want their menus to be configured; but I will tell you that you'll need to poke around in and work with the following files until you learn how the menu structure, syntax, and configuration of IceWM work:				
```
/etc/X11/icewm/menu
/etc/X11/icewm/toolbar
/usr/share/icewm/menu
/usr/share/icewm/toolbar
/usr/share/icewm/preferences
/usr/share/icewm/winoptions

```

One thing I would recommend specifically is attending to the following lines in the file /usr/share/icewm/preferences:
```
#  Show programs submenu
ShowProgramsMenu=1 # 0/1

```

Because I list most of my menu items in /etc/X11/icewm/menu instead of under the "Programs" folder, I change this as follows:
```
#  Show programs submenu
ShowProgramsMenu=0 # 0/1

```
That way, the programs menu doesn't even show.

For convenience, I have almost every program I use listed in /etc/X11/icewm/menu.  You'll need to find out where your actual program files reside, and then use that info to make your menus.

IceWM menus are a little formidable initially in terms of structure, but familiarity comes along rather quickly after a while.  You can create any number of menus and submenus with different programs underneath, and you can specify icons to use with each.  For simplicity, I create a few menus, pertinent program entries, and NO ICONS.  The basic syntax of a menu containing a program is as follows:
```
menu "Shoe-related Applications" folder {
	prog shoe shoe.xpm /usr/bin/shoe
}

```
Here, the first line tells IceWM to create a menu called "Shoe-related Applications" which contains all of the programs listed between its brackets {}.  Each program goes on a separate line.

The program entry on line 2 is broken down as follows: header (prog), title ("shoe"), icon image (shoe.xpm), and program location (/usr/bin/shoe).

If your program title consists of two or more words, put quotation marks around it.  E.g., if my program was called shoe pie instead of shoe, line 2 above would read:
```
prog "shoe pie" shoe.xpm /usr/bin/shoe

```
With respect to icons: evidently, there is a line in /usr/share/icewm/preferences telling IceWm where to look for image files.  Because I don't use icons in my menus, I don't list image files: I just put a dash (-), and no image appears.  If you do choose to use images, I believe they need to be in the xpm format.

In any case, as an example, here is the exact output of my /etc/X11/icewm/menu file:
```
# This is an example for IceWM's menu definition file.
#
# Place your variants in /etc/X11/icewm or in $HOME/.icewm
# since modifications to this file will be discarded when you
# (re)install icewm.
#
prog Terminal - x-terminal-emulator -ls
prog Thunar - /usr/bin/thunar
menu Productivity folder {
    prog "Openoffice Writer" - /usr/bin/oowriter
    prog Abiword - /usr/bin/abiword
    prog Mousepad - /usr/bin/mousepad
    prog "Openoffice Spreadsheet" - /usr/bin/oocalc
    prog "Openoffice Impress" - /usr/bin/ooimpress
    prog "Evince PDF" - /usr/bin/evince
}
menu "Interwebs" folder {
    prog Firefox - /usr/bin/firefox
    prog Dillo - /usr/bin/dillo
    prog Filezilla - /usr/bin/filezilla
}
menu "Games" folder {
    prog Cuyo - /usr/games/cuyo
    prog KQ - /usr/games/kq
}
menu "Utilities" folder {
    prog Clock - /usr/bin/xclock
    prog Calculator - /usr/bin/xcalc
}
menu "Removable Media" folder {
    prog "Mount CD" - /home/billy/a/scripts/mount.cd.x
    prog "Unmount CD" - /home/billy/a/scripts/umount.cd.x
    prog "Mount Flash Drive" - /home/billy/a/scripts/mount.usb.x
    prog "Unmount Flash Drive" - /home/billy/a/scripts/umount.usb.x
}

```
[I][B]11.3 Configure files & settings to read data CDs and Flash Drives
[/B][/I]You may note in the printout above that the "Removable Media" section contains items that seem to point to script files.  That's exactly right.  In order to mount and unmount CDs and usb flash drives, I decided to create simple scripts with menu links to do the work rather than installing other programs.  (Actually, I didn't know of any other programs).

I actually work with cds and flash drives in IceWM and from the command line, so I'll talk about how that goes.

***11.3.a Create Aliases for working with CDs and Flash Drives from the Command Line.***

From a command line, edit your .bashrc file:
```
nano .bashrc

```
Add the following aliases where the other aliases are:
```
alias mount.cd='sudo mount /dev/cdrom'
alias umount.cd='sudo umount /dev/cdrom'
alias mount.usb='sudo mount -t vfat /dev/sdc1 /media/usbflash'
alias umount.usb='sudo umount /dev/sdc1'

```
Your cdrom should be configured to mount its contents into /media/cdrom , so you shouldn't have to fuss with this.  For CDs, all you'll have to do now in the command line is type "mount.cd" and then navigate to /media/cdrom to get cd contents.  When you're done, type "umount.cd", and the cd will be unmounted.  I'm not entirely sure that sudo is necessary for mounting and unmounting cds, but I believe so.  I tend to sudo everything as a habit, which is probably not good.

For your flash drive, you'll recall that we created the directory /media/usbflash earlier for this very purpose.  Flash drives seem to require mounting by root, and thus the sudo.  All the command "sudo mount -t vfat /dev/sdc1 /media/usbflash" means is "mount the vfat partition on /dev/sdc1 in the /media/usbflash folder, and do it as though I was the superuser" (or something like that).  Be aware, here and below, that I only mount one flash drive at a time on this machine, and it always appears as /dev/sdc1.  In order to see what volumes you've got running in your machine in order to identify your connected flash drive(s), you can type
```
sudo fdisk -l

```
and read the screen output.  This will list your connected filesystems, mounted and unmounted (so far as I know).

Anyway, you now have aliases for easily mounting and unmounting cds and flash disks from the command line.

***11.3.b Create scripts for mounting cds and usb flash from the start menu.***
In my user folder (/home/billy), I always create an "a" directory to keep my files separate from the config files in the /home/billy folder, as I turn on the "show hidden files" feature in Thunar.  I then create the folder "scripts" for holding script files.  Using an editor (mousepad, nano, etc), I create four script files: one to mount cd, one to unmount cd, one to mount usb flash, and one to unmount usb flash.  I then connect those to the start menu using the menu entries listed above, and have one-click mounting and unmounting capabilities.

[U]Be advised that this method (1) requires you to allow these scripts to run as programs, and (2) that it requires some alterations to your /etc/sudoers file.

MESSING WITH YOUR /etc/sudoers FILE CAN BE DANGEROUS, SO PROCEED WITH EXTREME CAUTION.[/U]

First, create your script to mount cds.  Mine is at /home/billy/a/scripts/mount.cd.x , and it reads as follows:
```
#!/bin/sh
mount /dev/cdrom
wait
thunar /media/cdrom
exit

```
This mounts the cd, waits for the mount, and then opens the thunar file manager to display the cd contents.

Next, create your script to unmount cds.  Mine is at /home/billy/a/scripts/umount.cd.x ,and it reads as follows:
```
#!/bin/sh
umount /dev/cdrom
exit

```
Next, create your script to mount usb flash drives appearing at /dev/sdc1 (as all of mine do).  Mine is at /home/billy/a/scripts/mount.usb.x, and it reads as follows:
```
#!/bin/sh
sudo mount -t vfat /dev/sdc1 /media/usbflash
wait
thunar /media/usbflash
exit

```
Finally, create your script to mount usb flash drives appearing at /dev/sdc1 (as all of mine do).  Mine is at /home/billy/a/scripts/umount.usb.x, and it reads as follows:
```
#!/bin/sh
sudo umount /dev/sdc1
exit

```
Now, you will need to change the permissions on these scripts to allow them to run as programs.  In thunar, navigate to /home/billy/a/scripts (or wherever you're keeping them), click on their properties, go to permissions, and check "allow this file to run as a program" for each file.

So far so good.  Now, we have to circumvent a problem pertaining to the USB-related scripts.

You will note in each that a "sudo" is required.  Unfortunately, when these scripts run as programs, there's no place to enter your password: the program simply hangs or exits without doing its job.  Accordingly, we have to tell BASH that it's ok for the command involved to run as sudo without a password.

_**At this point, please be advised**_: I have no idea how dangerous or insecure the following instructions might prove.  Since my PC is used by a single person and is on a secure network, it's a non-issue for me: but you may need to ask someone who knows more about file permissions before trying this.  In fact, if anyone reading this in this thread has any insights on this point, please post them, as I'm curious as to how this modification could potentially be exploited.

The way I allow the script to run is to edit the /etc/sudoers file.
```
sudo mousepad /etc/sudoers

```
At the very end of the file, I type:
```
billy ALL = NOPASSWD: /bin/mount, /bin/umount
```

Here, of course, you would substitute your username for "billy".  The "ALL" evidently tells the OS that it's OK for Billy to do this on any PC in its jurisdiction, and the "NOPASSWD: /bin/mount, bin/umount" line lets it know that if billy ever tries to run mount or umount as the superuser, it shouldn't require a password.

There it is.  I hope the foregoing proves useful to some, and I look forward to hearing of alternate methods and other issues pertaining to IceWM on Ubuntu command line 8.04.

This post was written on the same machine I configured as described above.

--VoTMagn

---

### Post by Vorl the Magnificent on 2008-05-28
Actually, the scripts for mounting the flash drive aren't working out so well.  The aliases do ok, and the scripts seem to work all right superficially; but things get really flaky when you try to do anything with a mounted flash drive other than read files.  (I still haven't figured this out).

---

### Post by joshedmonds on 2008-05-29
I have been playing with a low-end system for a few days now - PIII 450mhz with 128mb ram. I created 3 partitions on the 10 gig hard drive and installed Puppy Linux, Arch Linux and Zenwalk with grub as the bootloader.

Puppy is basic but great for recovery tasks - you are auto root and have gParted etc to help you out. It really is a basic system though - I would never give it to a newbie, too easy to mess up and too hard to understand

Zenwalk rocks - XFCE desktop is really easy to configure, really fast, includes enough core apps that you don't need to download anything to have a fairly functional system. It does want to use lilo so you have to edit your grub menu.lst manually which can be a slight challenge (or use lilo...)

Arch is for people who want to work for their Linux, rather than the other way around (with the benefits of getting exactly what you want optimised for your machine) - I don't have an ethernet internet connection so I didn't even get as far as a Window manager, but the instructions are good as you go along.

I really recommend Zenwalk

---

### Post by lostlinuxkiwi on 2008-05-29
Theres fluxbuntu if you want. ive never tried it but im about to download it for this old toshiba laptop ive got. It runs xubuntu at the moment and it does an ok job but it still lags a bit which annoys me. 

[http://fluxbuntu.org/intro.html](http://fluxbuntu.org/intro.html)

---

### Post by kerry_s on 2008-05-29
i would suggest pmount for the mounting scripts, you use it as normal user so no need to fight permission issues or edit sudoers. always edit the sudoers file with "sudo visudo", anything else and you will break sudo.

sudo apt-get install pmount

> #!/bin/sh
mount /dev/cdrom
wait
thunar /media/cdrom
exit

becomes

```
#!/bin/sh
pmount /dev/cdrom
wait
thunar /media/cdrom
exit
```

> #!/bin/sh
sudo umount /dev/sdc1
exit

becomes

```
#!/bin/sh
sudo pumount /dev/sdc1
exit
```

i use pmount on my setup, no permission problems, no editing, no making directories.
i just:
sudo fdisk -l

(see what the drive is)

pmount /dev/sda1

(it will create the mount point in media for you, which is usually the name, so mine gets mounted to /media/sda1)

---

### Post by Inxsible on 2008-05-29
> **joshedmonds said:**
> I have been playing with a low-end system for a few days now - PIII 450mhz with 128mb ram. I created 3 partitions on the 10 gig hard drive and installed Puppy Linux, Arch Linux and Zenwalk with grub as the bootloader.

Puppy is basic but great for recovery tasks - you are auto root and have gParted etc to help you out. It really is a basic system though - I would never give it to a newbie, too easy to mess up and too hard to understand

Zenwalk rocks - XFCE desktop is really easy to configure, really fast, includes enough core apps that you don't need to download anything to have a fairly functional system. It does want to use lilo so you have to edit your grub menu.lst manually which can be a slight challenge (or use lilo...)

Arch is for people who want to work for their Linux, rather than the other way around (with the benefits of getting exactly what you want optimised for your machine) - I don't have an ethernet internet connection so I didn't even get as far as a Window manager, but the instructions are good as you go along.

I really recommend Zenwalk

 I agree with your observations in Puppy, Zenwalk and Arch. However, 1 problem I found with Zenwalk was that I didn't quite like it's package management. When you go in to install a package, the folders are named with only one letter like 'e' or 'l'. 

 Didn't quite comprehend initially. Or, it could only be because I was so used to the way Ubuntu and its derivatives manage packages.

---

### Post by Vorl the Magnificent on 2008-06-02
> **kerry_s said:**
> i would suggest pmount for the mounting scripts, you use it as normal user so no need to fight permission issues or edit sudoers. always edit the sudoers file with "sudo visudo", anything else and you will break sudo.

Thanks for the pmount suggestion: it works like a charm.  Also, I absolutely agree about using visudo to edit /etc/sudoers because of visudo's syntax checking function; but unfortunately, I haven't gotten around to learning how vi works yet, so I just had to risk it.

And yes, I broke /etc/sudoers once by using nano, and had to rescue it with a live cd. It was no fun.

Thanks again!  If I knew how to provide the formal "thank you" in these forums, I'd sure give one.

---

### Post by Weidbrewer on 2008-06-02
Lots of good stuff in here.  I hadn't really thought of Xbuntu, but that's a good bet.  XP totally bogs down my wife's laptop, and I wanted to try one of the linux distros...of course, the live CDs I have won't run, because it doesn't have 256M of RAM.  (And, best price I've found on bumping it any decent amount is running $80 - and this laptop ain't worth $80)


I'll probably DL it and give it a try when I get home.

---

### Post by sayakb on 2008-06-02
Try this.. Im running this combination on a old 633MHz Celeron, 384MB RAM junk:
Xubuntu + Openbox as Window Manager + ROX Files for desktop icons + Thunar as file manager + FBPanel for panel
Runs like cheese on the old computer.. The best part with OpenBox/Fluxbox is that you can run whatever you want to.. cutting off the useless packages.
Read here: [http://ubuntuforums.org/showthread.php?t=807318]("http://members.cox.net/mushroomlake/Compiz.html")

---

### Post by schmidtbag on 2008-06-02
I don't know about xubuntu, i tried that and was a little disappointed.  i heard it was supposed to be good for worse computers but it was unnoticeable faster.  the whole distro seemed really old-fashioned to me too; its hard to explain how.  using regular ubuntu on the same computer and disabling a few things (such as compiz) seemed to have worked better than xubuntu, imo.  anyways, even though ubuntu can work on the crappiest machines, the fact that its constantly updated is kind of a given that it was only intended for relatively modern computers.  same goes for windows xp.  sure it can work on a p2 with 64mb of ram, but the os is pretty useless unless you have something thats a p4 or better so you go with the next best thing - windows 2000, which is basically a really simple form of xp (they can both do mostly the same things).  my point is, on a computer that crappy, you would need a different distro like puppy or dsl

---

### Post by Inxsible on 2008-06-02
> **Weidbrewer said:**
> Lots of good stuff in here.  I hadn't really thought of Xbuntu, but that's a good bet.  XP totally bogs down my wife's laptop, and I wanted to try one of the linux distros...of course, the live CDs I have won't run, because it doesn't have 256M of RAM.  (And, best price I've found on bumping it any decent amount is running $80 - and this laptop ain't worth $80)


I'll probably DL it and give it a try when I get home.

Yeah... i know those kinds of laptops...where it aint worth sh**, but you still don't wanna throw it away because of sentimental values and/or the fact that a light Linux distro runs great on it. Believe me, I have 3 of those ;-) 

 BTW...since you don't even have 256 MB RAM, I think Xubuntu would also be very slow. I have 256 MB and if I start a music player like Audacious .. everything comes down to a crawl. Same with firefox.  

I would highly advise you to go with a minimal install and then adding your favorite light WM like IceWM, PekWM, Blackbox, OpenBox or Fluxbox or Enlightenment DR17. I just did the very same thing last night. Installed minimal and DR17.  
 I personally liked Fluxbox and Blackbox. I hated PekWM - too bland for my taste. IceWM was good only in 3 themes. the default theme sucks and so do the installed themes. Haven't tried Openbox much. 
They say Enlightenment is very lightweight, even though it has lot of eye candy. I will find out over some days :-D  

 If minimal installs and all those choices are not your cup of tea, you should go with Fluxbuntu (uses Fluxbox on Ubuntu based distro) or OzOs which is Enlightenment DR17 on xubuntu base. Although OzOs is still in development.  

Try them all out and see which ones you like. Good Luck !!

---

### Post by BruisedQuasar07 on 2008-06-24
I actually use Ubuntu, Xubuntu, Damn Small Linux, and Puppy Linux & several others. I have four PCs and I enjoy trying out different versions of Linux. I've had Windows 2000 pro & Xubuntu installed on my classic IBM Thinkpad laptop T-23 for two years. Originally I had a 20gb hard drive. It did the job just fine. Despite installing several programs, docs, etc the Xubuntu side of the partition had plenty of HDD space left. I upgraded to a used 40gb drive concerned I might run out of space on the Windows side. 

On my Dell Optiplex GX60 I have only 30gb HDD. I have Ubuntu installed on it. I occassionally use live CD Puppy, Damn Small,Systemrescuecd, Devil,  FeatherLinux and others, mainly I use Puppy to surf the net. The new Puppy 4.0 is such a leap that it is now my main operating system. 

I strongly recommend Puppy. It will automatically load itself into RAM memory. It boots, loads and is ready to use faster than any full use O/S I have ever seen. Puppy even has Seamonkey (the firefox module based browser) add-on page just like Firefox'es.

The entire Puppy U/S image is under 85 MB and that includes a lot of small, fast, good programs. I believe 256mb is what Puppy needs
to load & operate well into a RAM disk. If it sees you do not have enough RAM, it auto loads  much of itself into RAM disk and can use a pen drive, CDRW, or hard drive for the rest. 

Visit distrowatch.com and read their info on Puppy. There are several smaller versions of Puppy as well.

---

### Post by liquidfunk on 2008-06-24
I put Ubuntu 7.10 on a Laptop with a Celeron M 1.6Ghz and 192Mb RAM. That runs fine. 

 My Mums Desktop has a P4 1.6Ghz with 256Mb RAM and I put Debian Etch on it. Pretty good.

---

### Post by known on 2008-07-04
> **Stochastics said:**
> Hi everyone,

I want to have advice for which Linux/distros i can install on a low-end computer (P4 with 256 meg of RAM and 20G of HD). It's primary use is for web browsing and text editing (openoffice). I don't want to wait one hour to have a program to start up etc...any advice ?

Thanks

[http://wiki.dennyhalim.com/ubuntu-minimal-desktop](http://wiki.dennyhalim.com/ubuntu-minimal-desktop)

---

### Post by soleille on 2008-07-05
If you want to hear from somebody who is using regular Hardy (dual boot with Win2K- Ubuntu wins hands down!) because I knew I liked Gnome and thus didn't want to try one of the smaller Linuxes without it - for basic purposes (internet, email, word processing -yes, with OpenOffice-, basic games like mines or tetris and watching the occasional .avi), it's totally fine on a machine that's even lamer than yours (Thinkpad T20 with 128 RAM, and not too sure about the rest)

It won't win any speed races, but so far I haven't found anything that I would need faster... but then what I'm looking for is mainly a typewriter that gets me online :O)

---

