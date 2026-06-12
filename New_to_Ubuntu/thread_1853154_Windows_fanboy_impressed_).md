---
title: "Windows fanboy impressed :)"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by d4m1r on 2011-10-01
Hey guys, I am a long time Windows fan as well as a hardcore user with everything Windows 95 and above. I have done advanced stuff with Windows Server 2003 as well, but my newest career in the IT world has me working with Solaris, something I had no experience with previously. All the Java guys at my work use Ubuntu and I was fascinated with it so I download 11.04 and installed it on my main PC at home that I use for gaming and work.

Wow is all I have to say....easy to use (and pretty!) interface, boots up and shuts down almost instantly, able to do the majority of the things my PC can do, and all with better security (virus wise) and better flexibility with command line! Few issues however:

1)I have to use a Cisco 64bit VPN client on my desktop to be able to connect to my PC at work, are there any applications you guys think will work on Ubuntu?

2)I have a Lexmark wireless printer, how do I go about setting it up on my Ubuntu partition if the manufacture doesn't make linux drivers for it?

3)Will Ubuntu improve my battery life if I installed it on my laptop? Its a 2 year old HP machine that I will be testing with a live cd on in a second, but am worried about memory leaks in Ubuntu draining the battery...

Note - both my desktop PC and my HP laptop run Windows 7 x64 with AMD 64 bit enabled CPUs.

---

### Post by Dangertux on 2011-10-01
Welcome to the forum and glad you like Ubuntu :-)

Hopefully this can be of some help to you

1 -- For your Cisco VPN you can probably use OpenVPN client , it supports many VPN's so long as your particular model doesn't require a proprietary client like some Fortinet ones do you should be good.

2 -- I have never dealt with installing a Lexmark printer under Linux so maybe someone else can help you with that. 

3 -- Depends on the equipment, I've noticed considerably longer battery life with my laptops than under Windows 7. Your mileage may vary.

Hope this is helpful

---

### Post by papibe on 2011-10-01
Welcome to the forums!

[Here]("https://wiki.ubuntu.com/VPN")'s some basic information about setting a VPN (including the Cisco's). And [this]("https://help.ubuntu.com/community/VPNClient") help page have more details.

Hope that helps,
Regards.

---

### Post by wildmanne39 on 2011-10-01
Hi, most of the time the battery life in ubuntu is about the same as in windows, however some people have issues where there battery drains quick do to a bug in 11.04, I am not sure that it has been fixed yet or not but I do not think it has, and it does not effect most hardware.
Thank you

---

### Post by angryfirelord on 2011-10-01
Heh, glad you like it! I first got started with it in 6.06 and I've been using it ever since. Just as a word of caution though, the state of the linux desktop is a little...messy at the moment. Ubuntu uses a desktop called Unity, which was made the default in 11.04, but some people reported issues with it. Judging from the review of the 11.10 beta, the user experience should be much improved in the next release, which is due in less than two weeks.

> 1)I have to use a Cisco 64bit VPN client on my desktop to be able to connect to my PC at work, are there any applications you guys think will work on Ubuntu?

There are a few options to do this. One way is to get the VPN package from Cisco and compile the kernel modules into Ubuntu. However, this way is kind of messy and usually always breaks. There is an easier way:

First, go into your Windows machine and go to the Cisco VPN's program folder. In there, look for a .pcf file. Make a copy of it and put it onto something like a USB drive or somewhere you can access it in Ubuntu.

Next, open up a terminal and type this in:
```
sudo apt-get install network-manager-vpnc
```
Once it's done, go to the network manager icon that's next to the clock. Click on it, go to VPN connections and select Configure VPN. From there, you should be able to import your file. If not, then you can look at the file and enter the information manually.
> 2)I have a Lexmark wireless printer, how do I go about setting it up on my Ubuntu partition if the manufacture doesn't make linux drivers for it?
Depends on the model. You can try adding it like any network printer and see if it picks it up. Otherwise, it'll probably require some Googling.
> 3)Will Ubuntu improve my battery life if I installed it on my laptop? Its a 2 year old HP machine that I will be testing with a live cd on in a second, but am worried about memory leaks in Ubuntu draining the battery...
This is a mixed answer because it all depends on what you're running and what drivers are loaded. Some people have reported better usage of power while others have been worse off. For me, my experience is that they're about the same within a half-hour range on a netbook.

---

### Post by d4m1r on 2011-10-01
Thanks for the reply guys! I know the hardcore users might not like it, but I am actually a fan of Unity...I also know that if I run into any issues, it is easy to switch back to gnome ;)

Few issues:

1)Lexmark apparently isn't too linux friendly and even thought there is a work-around available for my model (use a comparable models drivers) it requires me to hook it up with a USB cable and it is a wireless printer so I don't want to do that....The native printer application didn't find it either when I did a scan of network printers.

2)Am I not able to automatically mount NTFS drives in this release? I've tried both NTFS Config Tool and Storage Device Manager and neither work....NTFS Config tool prompts for a password but then nothing appears. Storage Device Manager was able to mount 2/3 at boot but only enables read-only access:(
Any command line way to do it so I can use sudo? (I think this is a permission issue)

3)Simple question, is there a way to change all the single click stuff to double click? (ie: clicking on applications on the left launch bar)

4)So I imported the .pcf file for the VPN and all the settings seem to have appeared, but now what? In windows, the Cisco VPN creates a second "fake" network adapter than allows me to be connect to 2 networks at the same time (my home real one to my modem, and the 2nd fake one to work). I then Remote Desktop in to my work PC. Is this not possible with Ubuntu? How do I connect to the saved VPN connection, and if I do so, will I lose internet access?

Thanks for the help guys!!

---

### Post by dFlyer on 2011-10-01
Welcome to the linux world. Just go slow and have fun.

---

### Post by josephmills on 2011-10-01
> **wildmanne39 said:**
> Hi, most of the time the battery life in ubuntu is about the same as in windows, however some people have issues where there battery drains quick do to a bug in 11.04, I am not sure that it has been fixed yet or not but I do not think it has, and it does not effect most hardware.
Thank you

I have a computer with a bad battery in it last 5 to 10 min in ubuntu with out being plugged in. in windows7 the instance the I unplug the cord the laptop shuts off. Just thought that I should trow that out there.

---

### Post by d4m1r on 2011-10-01
Ok, forgot about VPN and wireless printer stuff...it's a lot more complex on linux than I thought:(

Let me just worry about the basics, is there any known app that will allow me to automatically mount NTFS partitions at boot?

---

### Post by SeijiSensei on 2011-10-01
You don't need an app; you just create an entry in /etc/fstab.

When you install Ubuntu, if you pick manual partitioning you can set it up to mount the NTFS partition at that time.  Otherwise you need to add an entry to /etc/fstab that looks like 

```
/dev/sda1 /windows  ntfs defaults,nls=utf8,umask=007,gid=46 0  0
```

That assumes the NTFS partition is the first one on the disk, and that you've created an empty directory named /windows (use "sudo mkdir /windows").  

Another alternative is to use UUID's to identify the partition.  Use the command "sudo blkid" to see a list of the partitions and their UUIDs, then replace /dev/sda1 with "UUID=the-NTFS-partition-UUID".  The UUID will be some hexadecimal string like 4C1CE6C51CE6A8E2.

Once you've done that, your entire Windows filesystem will appear below /windows.

---

### Post by Dangertux on 2011-10-01
EDIT : Ninja'd ;-)

However if you need a more in depth explanation check here :  [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by d4m1r on 2011-10-01
> **Dangertux said:**
> EDIT : Ninja'd ;-)

However if you need a more in depth explanation check here :  [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)


My vi skills are extremely basic so I didn't want to manually edit my fstab incase I would #&*$ something up....Thanks for that link Danger but I tried all those apps and they don't work.

Eventually I searched for "mount" in that software center and "Mount Manager" came up so I tried it and it seemed to work....until I restarted. Now Ubuntu will not boot, not even into safe mode. I am guessing the app screwed up my fstab, so it looks like I'll have to nuke my linux partition and start from scratch. If I can specify NTFS partitions I want automatically booted @ startup during install, even better....

---

### Post by Dangertux on 2011-10-01
Oh -- well it tells you how to manually edit fstab down at the bottom, sorry you nuked your install :-/ You can just fix it from the livecd if you know what you did.

Also -- if you don't like vi/vim , just use nano instead, it's easier to use than vi/vim but not as fully featured. I still highly recommend learning vi

```

nano filename

```

---

### Post by d4m1r on 2011-10-01
> **Dangertux said:**
> Oh -- well it tells you how to manually edit fstab down at the bottom, sorry you nuked your install :-/ You can just fix it from the livecd if you know what you did.

Also -- if you don't like vi/vim , just use nano instead, it's easier to use than vi/vim but not as fully featured. I still highly recommend learning vi

```

nano filename

```


Hmm, ok I'll give nano a go.

@repairing my install from the livecd, is there a way I can rebuild or use a default fstab file? I am pretty sure its corrupt and thats why my loading screen just stays purple and windowed and my safe mode throws an error (can't set <something> to exp<something>)

---

### Post by Dangertux on 2011-10-01
> **d4m1r said:**
> Hmm, ok I'll give nano a go.

@repairing my install from the livecd, is there a way I can rebuild or use a default fstab file? I am pretty sure its corrupt and thats why my loading screen just stays purple and windowed and my safe mode throws an error (can't set <something> to exp<something>)

I'm not positive if you can recreate a default, however if you are concerned you corrupted it , if you post it here I'm sure me or someone else will be able to help you.

---

### Post by parth.s on 2011-10-02
> **d4m1r said:**
> 
3)Will Ubuntu improve my battery life if I installed it on my laptop? Its a 2 year old HP machine that I will be testing with a live cd on in a second, but am worried about memory leaks in Ubuntu draining the battery...

Note - both my desktop PC and my HP laptop run Windows 7 x64 with AMD 64 bit enabled CPUs.

This is my experience so far, Win7 because of the processor frequency variation(leading to power consumption variation) achieves good battery life. I would suggest you to check out indicator-cpufreq...
The ondemand mode actually allowed me to push my (just a month old) laptop nearly to 5hr (was mainly using it for some surfing and music), better than win7....also the heat dissipation is reduced...
hope it helps

---

### Post by Paddy Landau on 2011-10-02
> **Dangertux said:**
> if you don't like vi/vim, just use nano instead
Heck, why not use the GUI gedit? Whether from the terminal or from Alt-F2, the command is:```
gksudo gedit *filename*
```e.g.```
gksudo gedit /etc/fstab
```

---

### Post by d4m1r on 2011-10-02
Thanks parth and paddy! Will be looking into both of those....Good news, I am typing this from my linux partition:D Its very strange though...I totally deleted the partition and installed over it yet all my files and settings are still here....

@setting NTFS drives to mount during OS install, its not really possible...I have 3 NTFS partitions I'd like to mount and the installer only specifies 2 mount locations (/dos and /windows) and neither are /media....looks like I'll be manually editing my fstab today...

@single click, does anyone know how to turn it into double click? (ex: clicking on an application on the launch bar)

---

### Post by d4m1r on 2011-10-02
gedit rules!!

Just an update guys, I was able to edit my fstab and auto mount all my NTFS partitions on boot :D I got my firefox up and running (95% of my computing these days is web based) and all my hardware seems to be detected (except my G15 keyboard but thats minor). I have given up on getting my works Cisco VPN and my lexmark wirless printer setup as neither are a straightforward process.

Things I will still have to use my Windows 7 x64 partition for:
-photoshop
-bad company 2
-cod 2/4/5
-premier
-fraps
-office 2007
-printing
-cisco vpn
-itunes
-nero
-winavi
-daemon tools

For the most part, my gaming days are over and I love the Unity interface so....I won't be switching my laptop over however. I don't want to worry about battery life and I will lose those HP specific applications (wifi switcher and mobility settings) so....Now if I can only figure out this single click thing:lol:

---

### Post by wildmanne39 on 2011-10-02
Hi, you can use brasero in place of nero, you did need to install the restricted packages.

I use libreoffice instead of office 2007.
Thank you

---

### Post by d4m1r on 2011-10-02
> **wildmanne39 said:**
> Hi, you can use brasero in place of nero, you did need to install the restricted packages.

I use libreoffice instead of office 2007.
Thank you

Looked through both those applications and they don't give me the same functionality or UI as Office 2007 and Nero...Maybe its just because I am used to them, idk :lol:

---

### Post by Rubykuby on 2011-10-02
LibreOffice is based off of the Office 2003 look. 2007 was a shock to many people, including me, so I'm really happy to use LibreOffice. Even then, I use Google Docs more often than not.

As alternative to fraps, you can use an application called "desktop recorder" as found in the Software Centre. It does exactly what the name says.

iTunes seems to be working under wine, too, but I don't use any Apple devices so I really can't tell.

Also, you'll get used to single-clicking :p It took me a few days and I still make the occasional mistake.

---

### Post by MG&amp;TL on 2011-10-02
Depends what you use photoshop for.

The GIMP is fairly impressive:

```
sudo apt-get install gimp
```

---

### Post by d4m1r on 2011-10-02
I use Fraps/Premier/Photoshop for graphic design jobs from time to time, but mainly gaming related...Something I have less and less time for but I am a fairly advanced user so have specific requirements.

@Office 2007, I love the simplicity of the interface and just the overall look...I've used all the previous versions and do heavy work in all 3 apps (word, powerpoint, and even *sigh* excel) and nothing compares, especially not google docs LOL (no offense)

---

### Post by alphacrucis2 on 2011-10-02
> **d4m1r said:**
> Looked through both those applications and they don't give me the same functionality or UI as Office 2007 and Nero...Maybe its just because I am used to them, idk :lol:

For another alternative to Nero you could try k3b. It's a KDE application so it will pull in quite a lot of KDE libs that it needs. Once installed though, they will already be there if you want to run any other KDE apps.

---

### Post by wolfen69 on 2011-10-02
> **d4m1r said:**
> 
Let me just worry about the basics, is there any known app that will allow me to automatically mount NTFS partitions at boot?
It only takes a second to open a file manager and click on the drive you want mounted. No need for NTFS config tools or anything. Btw, almost all HP printers are plug and play in linux. I tossed my lexmark printer out the window after I went linux full time. Can't help you with the VPN thing.

---

### Post by wolfen69 on 2011-10-02
> **d4m1r said:**
> I use Fraps/Premier/Photoshop for graphic design jobs from time to time, but mainly gaming related...Something I have less and less time for but I am a fairly advanced user so have specific requirements.

@Office 2007, I love the simplicity of the interface and just the overall look...I've used all the previous versions and do heavy work in all 3 apps (word, powerpoint, and even *sigh* excel) and nothing compares, especially not google docs LOL (no offense)

2 words: dual boot. It's not against the law.

---

### Post by d4m1r on 2011-10-02
I do dual boot. I am not about to toss out a printer that works perfectly (just not on Linux) for a garbage HP one...I would know, I sold them for years lol...

---

### Post by ubudog on 2011-10-02
Welcome to Ubuntu!  

I've moved this to Testimonials and Experiences.  :)

---

### Post by MG&amp;TL on 2011-10-03
This is interesting. Most people come to Ubuntu because they hate windows, not because they love windows, just love Ubuntu more.

'tis good. :)

---

### Post by Paddy Landau on 2011-10-03
> **d4m1r said:**
> @Office 2007, I love the simplicity of the interface...
That's funny -- I found it unnecessarily complicated. Office 2007 was the last straw that had me change over to OpenOffice (now Libre Office), which in turn allowed me to change to Ubuntu. This, coming from someone who knew Word and Excel backwards. My wife found 2007 completely unusable.

> **wolfen69 said:**
> ... almost all HP printers are plug and play in linux.
However, I advise you install [hplip]("apt:hplip") before using your HP printer. It gives you access to the extra HP functions.

> **wolfen69 said:**
> dual boot.
Or, if your computer is powerful enough, load Windows in [Virtual Box]("https://www.virtualbox.org/"). If you install the Guest Additions and turn on the "seamless" interface, you even have the option to open Windows applications within your Ubuntu desktop.

You need 64-bit virtualisation if your Windows is 64-bit -- check your BIOS to ensure that it is turned on (keywords: *svm* if you use AMD, or *vmx* if you use Intel).

Or, if you have the patience to work out how to do it, use a hypervisor (virtual machine manager or VMM) to switch between Windows and Ubuntu without rebooting. Look up Xen and KVM. But you need 64-bit virtualisation to do this.

To check if your computer is 32-bit or 64-bit hardware, enter the following command. If it returns zero, your computer has 32-bit hardware. If it returns 1 or more, you have 64-bit hardware.```
grep -cF lm /proc/cpuinfo
```If you have 64-bit hardware, check if it has virtualisation. Enter the following command. If it returns 0, your computer does not have virtualisation (or it is turned off in the BIOS). If it returns 1 or more, your computer has virtualisation and it is turned on in the BIOS.```
grep -cE 'svm|vmx' /proc/cpuinfo
```

---

### Post by scorp123 on 2011-10-03
> **d4m1r said:**
>  but my newest career in the IT world has me working with Solaris ... I have to use a Cisco 64bit VPN client on my desktop to be able to connect to my PC at work ... 

Don't you guys use Oracle Secure Global Desktop? I mean ... you just said you use Solaris. So why not use SGD too?

[http://www.oracle.com/us/technologies/virtualization/061996.html](http://www.oracle.com/us/technologies/virtualization/061996.html)

Once you have that up and running accessing your stuff remotely is only a matter of typing [https://your-url-here](https://your-url-here) into your browser and taddaaaaaa ... you're connected. The browser and the OS don't even matter (Mac OS X, Linux 32-bit and 64-bit, Windows ... they all work tip top as SGD clients).

If you can afford Solaris licenses ... you can afford SGD licenses too.

---

### Post by spook1980 on 2011-10-03
> **d4m1r said:**
> Looked through both those applications and they don't give me the same functionality or UI as Office 2007 and Nero...Maybe its just because I am used to them, idk :lol:

try k3b you can find it in synaptic or by sudo apt-get install k3b in a terminal i perfer it to all cd/dvd burning programs in fact its 1 program that i truly miss when i use windows nero is a close 2nd but k3b puts it 2 shame

---

### Post by stalkingwolf on 2011-10-03
yep i use k3b.  if i am forced to use windows i use Nero.

Check out crossover linux for those windows applications you need.

---

### Post by d4m1r on 2011-10-03
> **MG&TL said:**
> This is interesting. Most people come to Ubuntu because they hate windows, not because they love windows, just love Ubuntu more.

'tis good. :)

Sorry, I still love my Windows 7 and Windows Server 2003 but this might change when I get Ubuntu on my server box at home!

Good news btw, was able to setup my Cisco VPN client to my Windows machine @ work using the built in Network Manager app and Terminal Server Client! There is a bug however...once you add a VPN profile, you can't actually connect to it until you restart the app.

Will have to try transmission tonight but I have a feeling I won't like it as much as utorrent...Either way, I am up to 80-85% of the capabilities of my Windows partition!

---

### Post by Paddy Landau on 2011-10-04
> **d4m1r said:**
> Will have to try transmission tonight but I have a feeling I won't like it as much as utorrent...
Try [Deluge]("http://deluge-torrent.org/"). It's in the repository, but it tends to be out of date, so visit the website and follow the instructions to add its PPA.

---

### Post by d4m1r on 2011-10-04
> **scorp123 said:**
> Don't you guys use Oracle Secure Global Desktop? I mean ... you just said you use Solaris. So why not use SGD too?

[http://www.oracle.com/us/technologies/virtualization/061996.html](http://www.oracle.com/us/technologies/virtualization/061996.html)

Once you have that up and running accessing your stuff remotely is only a matter of typing [https://your-url-here](https://your-url-here) into your browser and taddaaaaaa ... you're connected. The browser and the OS don't even matter (Mac OS X, Linux 32-bit and 64-bit, Windows ... they all work tip top as SGD clients).

If you can afford Solaris licenses ... you can afford SGD licenses too.


Yes, Solaris/Oracle costs are very high but all this stuff was in place years before I got here ;) I have never heard of that product, but 11.04 has built in VPN capabilities (just had to download vpnc) and now I am connect to my Windows XP machine at work using terminal server client (RDP>all):grin:

---

### Post by MG&amp;TL on 2011-10-05
> **d4m1r said:**
> Sorry, I still love my Windows 7 and Windows Server 2003 but this might change when I get Ubuntu on my server box at home!

It wasn't a criticism. :)

Have fun, anyways.

---

### Post by spook1980 on 2011-10-05
> **d4m1r said:**
> Sorry, I still love my Windows 7 and Windows Server 2003 but this might change when I get Ubuntu on my server box at home!

Good news btw, was able to setup my Cisco VPN client to my Windows machine @ work using the built in Network Manager app and Terminal Server Client! There is a bug however...once you add a VPN profile, you can't actually connect to it until you restart the app.

Will have to try transmission tonight but I have a feeling I won't like it as much as utorrent...Either way, I am up to 80-85% of the capabilities of my Windows partition!

utorrent does run very well in wine

---

### Post by d4m1r on 2011-10-05
> **spook1980 said:**
> utorrent does run very well in wine

I still have my Windows partition so I don't want to setup Wine just  for utorrent. I was going to for Office 2007 but then I remembered I can't print anything from this partition anyway so it would be pointless for the most part:lol:

LibreOffice seems OK though, for basic editing at least...

---

### Post by Sef on 2011-10-06
Moved to Absolute Beginner Talk since solutions were being asked for.

---

