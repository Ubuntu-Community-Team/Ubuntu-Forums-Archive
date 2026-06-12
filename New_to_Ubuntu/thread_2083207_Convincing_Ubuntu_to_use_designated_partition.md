---
title: "Convincing Ubuntu to use designated partition"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by areyouamogul on 2012-11-11
Hey everybody. I know you're gonna figure out my issues in no time, so allow me to be grateful already ;)

That said...

     Thing is I installed Ubuntu into what I thought was a perfectly fine and clean ext4 partition I had just created inside my 320gb disk. I designated 10Gb for the ''/'' plus 90 additional gb for ''/home''. All this, again, in ext4. My intention is to install it entirely independently to Windows, which happens to be installed as well. 
So imagine my surprise when, after installing Ubuntu and logging in, my Hard Disk icon in the whatever-you-call-that-bar-on-the-left tells me my drive is ''205gb'' big. 

     Typing ''Disk'' on the Dash leads me to a piece of pre-installed software called ''Disks''. Once there, I find out that while my 90+10 partitions do exist, Ubuntu is using the remaining 205gb as ''media.'' This event escapes my understanding. 
The thing is, this /media partition is a) where my Windows stuff lives, and b) therefore, written in NTFS.

     Just in case I didn't put this clear, I want Ubuntu to stick to those 90gb I assigned to it through the /home partition. I'd also love that someone could assure me I'm actually running Ubuntu through the ''/'' ext4 partition, 'cause I don't know why the UI is so laggy. 

Thanks a lot.

---

### Post by monkeybrain2012 on 2012-11-11
That is normal. It just mean that you can access the ntfs partition from Ubuntu as a mounted  partition. You can right click its icon from Nautilus (View > Show side bar) to mount and unmount it . All partitions of your hard drive will show up as media.

---

### Post by offgridguy on 2012-11-11
>   in the whatever-you-call-that-bar-on-the-left 

It's called the launcher,  the top icon- the dash.:)

---

### Post by newb85 on 2012-11-11
As monkeybrain2012 said, that's normal.  Ubuntu is not using anything outside the 100 GB you assigned it to.  It is only giving *you* the option of using the other space.  (This can be very helpful in passing documents etc. back and forth between OSes.)

---

### Post by deadflowr on 2012-11-12
The partitions you have set up for Ubuntu won't be listed as they are the ones in use.All other partitions will be listed as you see your 250GB NTFS is.

Unlike NTFS, which has limited abilty of reading other filesystems, EXT4 has no problem reading other filesystems like NTFS.

All "external"(meaning extra) partitions are accessed through the media directory by default.

---

### Post by areyouamogul on 2012-11-12
Hey, thanks a lot. 

Now the only thing I'd like to know is, what will Ubuntu use those /home 90Gb for? Will it store the things I download, plus my Ubuntu documents there? Because I don't seem to be able to access that partition independently from the whole drive. You see, my Windows partition is already quite full, 15Gb left when I log in to Windows. I wouldn't like Ubuntu to fill that space.

Thanks again.

---

### Post by newb85 on 2012-11-12
It's not really a matter of filsystems reading each other.  Windows can't read Ext4*, but Ubuntu can read NTFS.  Ubuntu hasn't always had this ability.  When I first installed Ubuntu, I had to create an extra "shared" partition that was FAT32, which both Windows and Ubuntu could read.  (For the record, a shared partition isn't a bad idea these days, but it's better to make it NTFS.)

*I remember reading that it's possible to install software on Windows to browse Ext* filesystems.  I don't know what it is or how well it works.

@areyouamogul, Ubuntu won't put anything in your Windows space unless you tell it to.  Your /home directory is where all your Documents, Downloads, media files, etc., are placed by default, as well as a lot of configuration files for Ubuntu and **[for]** the applications you have installed.  Configuration files are typically hidden, but if you'd like to see them in Nautilus (the default file browser), hit Ctrl+H.

Also, you mentioned in you initial post that your UI is "laggy".  This is typically due to RAM and graphics card limitations.  If this is hampering usability, you may nead to install a lighter-weight UI.

---

### Post by Impavidus on 2012-11-12
> **newb85 said:**
> 
@areyouamogul, Ubuntu won't put anything in your Windows space unless you tell it to.  Your /home directory is where all your Documents, Downloads, media files, etc., are placed by default, as well as a lot of configuration files for Ubuntu and the applications you have installed.  Configuration files are typically hidden, but if you'd like to see them in Nautilus (the default file browser), hit Ctrl+H.

Also, you mentioned in you initial post that your UI is "laggy".  This is typically due to RAM and graphics card limitations.  If this is hampering usability, you may nead to install a lighter-weight UI.
Actually, programs you install through the software centre are stored in /usr/bin (data in /usr/share), which is, if I'm correct, by default on your / partition, not /home.

Installing a lighter-weight user interface means installing xfce4 (lighter) or lxde (lightest), both available in the software centre. Off course, you could also opt for a clean install, which gets rid of gnome3/unity at the same time, but you may want to try it first.  On the other hand, if your computer is fairly new (a 320 GB drive doesn't sound ancient) it may be a driver problem that causes hardware acceleration of your graphics to malfunction.

---

### Post by newb85 on 2012-11-12
Should have made that more clear.  I meant the config files for the apps you install.  The apps themselves are definitely not stored under /home.

---

### Post by areyouamogul on 2012-11-12
Thanks again.

Now I see there's a 'Home Folder' icon right under the dash. Must be the 90Gb partition I made. Great, that sure makes a milestone. 

The thing with the drivers though, it's a tricky one. My system features 4gb RAM + 9200M GS from Nvidia. Not the latest, sure, but I mean, should be more than enough to display the dash screen toggle animation when I click on the icon. What currently doesn't happen smoothly at all. Same with the auto-hide launcher. The reason I say it's a tricky thing is that as far as I know, the drivers are working. I couldn't tell you where I saw it, but I recall seeing ''Nvidia drivers - 9200M GS blahblahblah'' in an Ubuntu control panel somewhere. 

Anyways, if you could tell me how to ultimately ascertain whether they're installed and working, that'd make my day. Same thing if you could tell me how to fix the ''firefox is running but not responding, go reboot lol'' issue... it forced me to install chromium :S

Thanks people, you're all bosses.

---

### Post by newb85 on 2012-11-12
Please give the results of
```
sudo lshw -C video
```

---

### Post by mlentink on 2012-11-12
Ubuntu Software Center > Edit > Software Sources > Additional Drivers
is probably where you saw those nVidia drivers.

---

### Post by Bartender on 2012-11-12
> **areyouamogul said:**
> Anyways, if you could tell me how to ultimately ascertain whether they're installed and working, that'd make my day. Same thing if you could tell me how to fix the ''firefox is running but not responding, go reboot lol'' issue... it forced me to install chromium :S

On my 10.04 PC, I go to System in the upper panel, then Administration>Hardware Drivers.  Click on that, it does a search, and shows me exactly what nVidia driver is in use.  Notice along the bottom of the window it says the "driver is activated and in use".

In 12.04, I click on the reddish "System Settings" icon in the launcher, then click on "Additional Drivers", and the same thing happens.  It does a search and tells me what it found.  In this case it didn't find anything, because the 12.04 PC is running Intel onboard graphics, but I'm quite sure the 12.04 window is identical to 10.04's.

EDIT: On the 12.04 PC I installed lubuntu-desktop because it's an old PC and runs noticeably slower in Unity.  If running Lubuntu 12.04, you click on the little blue "bird" (or whatever it is) in the lower left, then "Preferences", then Additional Drivers".  Odd to find it under Administration in 10.04, then Preferences in Lubuntu 12.04, but there it is.

ANOTHER EDIT:  Take a look at these [mozilla instructions]("http://support.mozilla.org/en-US/kb/firefox-already-running-not-responding").  Make sure to follow the link that explains where to find your profile.  To repeat their instructions, open your Home Folder, then go to View>Hidden Folders.  You won't see the mozilla folders until you do that.

---

### Post by areyouamogul on 2012-11-13
> **newb85 said:**
> Please give the results of
```
sudo lshw -C video
```

sudo lshw -C video
[sudo] password for ricardo: 
  *-display               
       description: VGA compatible controller
       product: G98 [GeForce 9200M GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:8000(size=128)

---

### Post by areyouamogul on 2012-11-13
> **Bartender said:**
> On my 10.04 PC, I go to System in the upper panel, then Administration>Hardware Drivers.  Click on that, it does a search, and shows me exactly what nVidia driver is in use.  Notice along the bottom of the window it says the "driver is activated and in use".

In 12.04, I click on the reddish "System Settings" icon in the launcher, then click on "Additional Drivers", and the same thing happens.  It does a search and tells me what it found.  In this case it didn't find anything, because the 12.04 PC is running Intel onboard graphics, but I'm quite sure the 12.04 window is identical to 10.04's.

EDIT: On the 12.04 PC I installed lubuntu-desktop because it's an old PC and runs noticeably slower in Unity.  If running Lubuntu 12.04, you click on the little blue "bird" (or whatever it is) in the lower left, then "Preferences", then Additional Drivers".  Odd to find it under Administration in 10.04, then Preferences in Lubuntu 12.04, but there it is.

ANOTHER EDIT:  Take a look at these [mozilla instructions]("http://support.mozilla.org/en-US/kb/firefox-already-running-not-responding").  Make sure to follow the link that explains where to find your profile.  To repeat their instructions, open your Home Folder, then go to View>Hidden Folders.  You won't see the mozilla folders until you do that.

Found it, says:

NVIDIA CORPORATION G92 (9200MGS)
this device is using the correct driver.

- Using Nvidia binary Xorg, kernel module and VDPAU from Nvidia current (propietary, tested).

There're like three more options, but for some reason that's the one that's checked.

---

### Post by areyouamogul on 2012-11-13
Oh by the way, excuse me for the triple posting, but:

I've read there's been quite some controversy? on Canonical (who're they, like, the creators?) including Amazon ads in the OS, as well as other couple things? What's all that about? 

I've moved to Ubuntu in an effort to escape from other OSs 'productification' of users. So far it's been so good with this OS, but anyway, I wouldn't be the happiest if that means supporting the same practices over here. I know we're now like miles away from the original topic, but you seem to be all savvy users. Could anybody give me some advice?

---

### Post by newb85 on 2012-11-13
I agree with your sentiments.  Fortunately, while the Amazon search results are included in the Dash by default in 12.10 (a poor decision), they can easily be removed.  Many howtos are available, and can easily be found with a Google search.

---

### Post by Wim Sturkenboom on 2012-11-13
> **deadflowr said:**
> Unlike NTFS, which has limited abilty of reading other filesystems, EXT4 has no problem reading other filesystems like NTFS.

The ability to use a certain filesystem is a functionality of the OS (kernel?), not of the filesystem itself.

Your statement should read something like "*Unlike Windows, which has limited abilty of reading other filesystems, Linux has no problem reading other filesystems like NTFS.*". And I'm quite sure that we can find some obscure filesystems that are not supported in Linux either.

---

