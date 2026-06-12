---
title: "Stay with Windows or move to Ubuntu?"
date: 2014-02-03
forum: New to Ubuntu
---

### Post by mcnr on 2014-02-03
I’m familiar with computers and Windows operating systems but this is the first attempt at Ubuntu.  I’m building a third machine, an HTPC, for the living room.  This is a used computer a Dell Dimension C521 Windows Vista Home Premium.  

Processor Speed: 2.10 GHZ
Model: DIMENSION C521
Memory: 2 GB
Operating System: Windows Vista
Hard Drive Capacity: 320 GB
Processor Type: AMD Athlon 64 X2
Operating System Edition: Home Premium

I’ve formatted all my Windows machines with a primary partition for the operating system “C\:”, Programs :D\:”, My Documents “E\:” with the swap file (only of disc based hard drive not SSD drives) and the temp files on their own partition.  Should I do the same for Ubuntu?

I’m thinking about running the 64 bit version of Ubuntu will I have a problem running 32 bit Windows programs using Wine?

I use Foobar for my music and plan to use it on this machine.  I have a lot of music on my office computer on several partitioned drives.  I have the partitions mapped on another Windows machine with the mapped drives letter corresponding to the drive letters on the Office machine and it works great.  I want this new computer to access the music and play list.  Will I be able to do the same?

Thanks

---

### Post by andrew.46 on 2014-02-04
> **mcnr said:**
> I’m familiar with computers and Windows operating systems but this is the first attempt at Ubuntu. 

Just a quick thought: perhaps you should have a period of experimentation with either dual booting Windows/Ubuntu (might be the better option on the hardware that you have mentioned) or beefing up the RAM a little and trying a Virtual Machine?

---

### Post by tfrue on 2014-02-04
I suggest that you read this:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

It's about switching to Linux from Windows and it's a really good read.

The question is, what can Linux not do? :D

You can auto mount the Windows drives at boot, and access them the same way you would normally but there is generally more configurations you will have to edit. But never fear! It shouldn't be too difficult.

Many members will say to map your partitions, which has it's benefits so you can and like I said, a lot of people will tell you too. It's pretty easy to do but you need to make sure that everything is correct before you make permanent changes.

I've made the full switch and everything is fine for me, but I don't have a situation where I need Windows applications, so make sure it would be practical for you to do!

Good luck,
Chris

---

### Post by QIII on 2014-02-04
Hello!

If you can find a cheap, small hard drive, I would second the suggestion to dual boot (or even remove the current drive if the case won't hold two?) -- on separate hard drives so that you don't need to worry about messing with the partitions on your Windows drive.  You can unplug the Windows drive, add the new drive, set it to be the first HDD in the boot order (of course you want an optical drive or USB as the first boot drive so you can boot to the install media), install Ubuntu and get it working, plug the Windows drive back in and update GRUB.

Judging from the specs given, this is not a UEFI setup and doing this with BIOS should be fairly painless -- and you eliminate the danger of ruining your Windows drive if you should decide you don't like Ubuntu.

I wouldn't even really consider "switching".  Consider just using both for the duration.  I think the "one or the other" mentality is not pragmatic.

Best wishes!

---

### Post by squakie on 2014-02-04
Big +1.   One of the things that caught my eye in your post was the question about running Windows programs in Wine.  It might help to know what you want to run, then check the Wine site's compatibility page.  Not all programs by far will run in Wine.  Some "kind of" run - but you end up with an abort somewhere or some strange result.

If you really want to make a switch to using Linux, and in this case Ubuntu in particular, I would get a list of your Windows-base "must-have" software.  Then start checking the net for Linux equivalents.  While dual-booting, try these Linux equivalents out to see if they do what you need in an acceptable way.

As far as HTPC, depedning on what you want to do, there are other possible routes for you.  One that comes to mind only because I've built a few for others and myself ;) is running OpenELEC on a Raspberry Pi model B.  You can easiily set up a media center for well under $100 less of course the disk.  But this is beyond the scope of your thread.  If interested, just PM me.

EDIT:  forgot to mention - I've just been using XBMC in Ubuntu on my computers when I want to try something and not mess with the Pi meida centers.  This same XBMC is what is included in OpenELEC and runs like a champ on the Raspberry Pi's.  When you decide how you are going to go - and I do hope you follow previous advice for dual-boot - install XMBC and test it out.  You can link to network shares, etc., with it for the sources.  If you decide you can use it, then it would be an easy thing for you if you wanted to go the Raspberry Pi route.

---

### Post by Impavidus on 2014-02-04
+1 to dual boot suggestions in general, but if this is an extra machine, with the Windows machines still in use for critical stuff, there is no need to dual boot. Just make sure you have Windows available on some machine until you feel really comfortable with Linux.

Linux doesn't use drive letters. Instead it puts everything in one directory tree, with one partition acting as the root (or stem, to follow the analogy of the tree), with the other partitions connected to that on mountpoints (like the branches of a tree). The root partition, known as /, is similar to the Windows C partition. In Linux it is possible to make a separate partition for programs (mounted at /usr), but this is only recommended in very special circumstances. The equivalent of a partition for My Documents is the /home partition, which is common on Linux systems. Linux usually doesn't have a swap file, but a swap partition instead.

You can attach any other partition to this single tree, including partitions mounted via a network, using any name you want. You could, for example, mount your F: drive at /media/F and your G drive at /media/G.

I don't think wine should have much problems with 32 bit Win .exes only because it's 64 bit itself, but with wine it's always a hit-or-miss game: sometimes it works, sometimes it doesn't. On 64 bit processors it's generally recommended to use the 64 bit OS as it may be a little faster, but it will also use a bit more memory. To comfortably access all your RAM you only need the 64 bit system when you have more than about 3GB of it. With memory in the 2-3GB range you're in a grey area, where it doesn't matter much whether you run a 32 or 64 bit system. If you consider upgrading your memory later, use 64 bit.

---

### Post by Bucky Ball on 2014-02-04
RaspBMC is also a perfect fit for a Pi as a media server. It's what I use. It is basically XBMC for the Pi. Works great and I can stream music/vid from any partition/directory on any of the four computers in the house.

From your post, you are not moving anywhere. You are locked down with a bunch of Win machine and dependent on Win apps. So I presume you are asking should you swap this one machine to Ubuntu. If you are using a lot of Win apps, I'd stay with Win. If not, then you should find everything, with the exception of the Win apps and Wine, will work fine using Ubuntu, but you will need to do a bit of a brain shift and go on a learning curve. If you're up for that, you can always ask for directions here.

For you Wine apps, as suggested, check if they will work here:

[http://www.winehq.org/](http://www.winehq.org/)

Hit and miss. You might get lucky. Then, again, maybe not. Again, if you need to use a LOT of Win apps, then Windows it is. ... ;)

---

### Post by mcnr on 2014-02-04
I apologize I typed this last night in an almost comatose state and I should have included this information.

Regardless of going to Ubuntu; Vista is coming off and I'll install XP.  

I'll use this for:

-HTPC, of course, (XBMC looks very cool)
-tagging music files so I'll need to have some way to do some basic editing of jpgs for cover art
-some very basic word processing but this could be nothing more that a text editor
-web browsing occasionally and some email

Eventually I will build a new machine that will do the above and also have a copy of all the music on the office machine for back up.  As of right now I have over 3TB of mp3s, FLAC and some DTS audio files.  These are on 4 hard drives.

I want to keep Foobar because I use it on my other machines and I already have playlists created.  As I listen to music in the office I'll add songs to playlist for different occasions.  I haven't found any cross media player playlist formats of "universal translators" but I also haven't looked.

I've already thought of upgrading the RAM in the near future so that's not a problem.

Thanks

---

### Post by Bucky Ball on 2014-02-04
Very bad idea to plan on connecting XP to the internet. Support finishes in April so this would be a short term solution. You would want to get it offline after that. I intend to get mine offline sometime this week (partly because I rarely boot it nowadays and when I do don't often go online, though).

---

### Post by Mark Phelps on 2014-02-04
I'll say it up front -- NOT a big fan of Wine.  When it works well, which is rarely, you CAN use Windows apps; but more realistically, it works poorly or not at all --especially on recent Windows apps like Office 2013 and IE v10+.

Use a test machine to try out alternatives to Windows apps, but running natively in Linux.

Then, if you reach a point that you're comfortable using the Linux apps instead of the Windows apps -- that would be the time to decide whether or not to completely switch over to Linux.

---

### Post by LukasLeon on 2014-02-04
Why you just don try out the wubi.exe installation if you want to just try Ubuntu? I know, everyone is hating it here, but for me it worked just fine, and did what it should do a.k.a allowed me to get to know with Ubuntu and try some of the features and programs it has, without a fear of screwing up partitions or deleting Windows.

---

### Post by mastablasta on 2014-02-04
> **mcnr said:**
> 
-HTPC, of course, (XBMC looks very cool) **YES **
-tagging music files so I'll need to have some way to do some basic editing of jpgs for cover art **YES - simple to more complex**
-some very basic word processing but this could be nothing more that a text editor **YES - simple to more complex to office suite, cli or gui whatever you want**
-web browsing occasionally and some email **YES - again plenty in this area - Firefox, Chrome, Chormium, Opera, Thunderbird, Empathy or whatever Outlook wannabe is called now.**




> 

I want to keep Foobar because I use it on my other machines and I already have playlists created. As I listen to music in the office I'll add songs to playlist for different occasions. I haven't found any cross media player playlist formats of "universal translators" but I also haven't looked.



have a look apparently it works well under wine/playonlinux: [http://ubuntuforums.org/showthread.php?t=2128514](http://ubuntuforums.org/showthread.php?t=2128514)
or use a replacement there is so many players. for example: [http://ubuntuforums.org/showthread.php?t=1914739](http://ubuntuforums.org/showthread.php?t=1914739)

not to mention XBMC has it's own players and let's not forget that XBMC will pull down fan art for you.

What is a playlist but a list of files?

and since you are reformating why not try to install the OS see how well it works. if it performs bad you can always reformat.

another foobar alternative foobnix: [http://www.foobnix.com/en/index.html](http://www.foobnix.com/en/index.html)

---

### Post by Bucky Ball on 2014-02-04
Foobnix looks very much like Clementine and has a lot of the same features. Have you looked at that? It's in the repositories. Install it and have an experiment. Easy enough to remove again. ;) 

[http://www.clementine-player.org/](http://www.clementine-player.org/)

---

### Post by squakie on 2014-02-04
> **LukasLeon said:**
> Why you just don try out the wubi.exe installation if you want to just try Ubuntu? I know, everyone is hating it here, but for me it worked just fine, and did what it should do a.k.a allowed me to get to know with Ubuntu and try some of the features and programs it has, without a fear of screwing up partitions or deleting Windows.
wubi may be oh the installation media, but it is no longer supported nor recommended to even try.

---

### Post by rburkartjo on 2014-02-05
yes i wont use xp after support runs out not a good idea and not all programs run in linux even with wine. imho i would bite the bullet any up grade to win7 or win8 and dual boot. thats what i do. i need windows for dishanywhere and chromecast.

---

### Post by tripp98 on 2014-02-05
You may want to just install Ubuntu on your XP/Vista box.  There is nice applications that will do what you  are wanting within Ubuntu not using wine.  Firefox and/or chrome.   great browsers.  Libreoffice - great office application.  Media can be  managed via Plex and stream throughout your network. Rhythmbox works great as a music player.  spend some time in the OS.  it works great on the vista age machine.  I have setup many labs and everyone that touches it finds out that computers can be fun again.  you dont have to spend time fighting viruses and malware.  you can actually use the computer for what you want.

---

### Post by icypunkpixie on 2014-02-05
I'd suggest a dual-boot for now, although I certainly hope you'll do a full migration. The awesome thing about Ubuntu (besides the whole orange-and-purple color scheme, hehe) is that you can customise it however you like -- as an example, I don't like the Unity interface, so I use Cairo-Dock. The other great thing is all of the open source software... You'll be able to find good alternatives to IE and MS Office in the Software Centre.

---

