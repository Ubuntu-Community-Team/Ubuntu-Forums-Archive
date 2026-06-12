---
title: "HOWTO: iPod Shuffle (Kubuntu)"
date: 2005-04-12
forum: Outdated Tutorials &amp; Tips
---

### Post by philipacamaniac on 2005-04-12
This is specific to Kubuntu, because Kynaptic's deficiencies and the use of gtkpod make things a little harder on KDE users. GNOME/Ubuntu users, you can follow the Wiki iPodHowto and it should work with the Shuffle.

1. You have to intialize/format your iPod Shuffle in Windows/Mac with iTunes. Enable the mass storage device option. Follow Apple's instructions for this procedure.

2. Plug your iPod Shuffle into your Kubuntu machine.

3. To add songs, you need to install gtkpod from Universe. Let's enable Universe.

[INDENT]In an open Konsole type:
```
sudo pico /etc/apt/sources.list
```
Uncomment (remove the "#") the following lines:
```
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe
```
Press CTRL-X and then "Y" to accept changes.
[/INDENT]

4. Install gtkpod and any dependencies.

[INDENT]Open Kynaptic from the System Menu. Browse to the "Multimedia (Universe)" Section, and scroll down to gtkpod. Right click and choose "Install." Accept any changes. Go to File-->Commit Marked Changes and let Kynaptic do its thing.[/INDENT]

5. If you haven't already, mount your iPod Shuffle by right clicking the USB Stick icon on the desktop and choose "Mount".

6. Configure gtkpod.

[INDENT]Open gtkpod from the Multimedia Menu. Go to Edit-->Edit Preferences. Change the following options.

*Input/Output*
iPod Mount Point: /media/volume_name*
Automatically import iTunesDB on startup: Yes

*Tools*
Command line for "Play Now": amarok %s
Command line for "Enqueue": amarok -e %s

Click Apply and then OK.
[/INDENT]
*To determine shuffle's volume name from terminal do
```
ls /media
```

7. Now you can add songs to your iPod Shuffle, or play songs directly from your iPod Shuffle.

---

### Post by poofyhairguy on 2005-04-12
One thing to add is that your mount point might not be the same as in this howto. When you plug in your shuffle, look at its properties to see where its mounted and tell GTKpod to mount from there.

Great howto otherwise...

---

### Post by mrbass on 2005-04-13
Suggestion change this:
iPod Mount Point: /media/sdb1

to this:
iPod Mount Point: /media/volume_name
To determine shuffle's volume name from terminal do
ls /media


For instance mine is /media/MRBASS 1G
once I did that it recognized it.  Music Player (Rymthbox) on ubuntu recognizes it automatically without having to set a mount point.

---

### Post by philipacamaniac on 2005-04-13
Thanks mrbass and poofyhairguy, I knew that Shuffles would probably mount to different locations, I just wasn't sure. I wonder if there is a some standard for media devices. If not, then there should be.

---

### Post by reuben on 2005-05-04
gtkpod doesn't work for me :(

It seems happy, but after I have synced and then safely disconnected (i.e. unmounted) the shuffle, I get the flashing orange/green error lights. 

Any ideas?

---

### Post by GNUmonkey on 2005-05-04
> It seems happy, but after I have synced and then safely disconnected (i.e. unmounted) the shuffle, I get the flashing orange/green error lights.

Yeah, I used to get this problem using gtkpod under gnome. Only way I could find to fix it was download the GNUPod suite from [here](http://www.gnu.org/software/gnupod/) and run the mktunes.pl program after synching in gtkpod, but before unmounting the shuffle.

Hope this helps

EDIT: after a little more research, it turns out that the gnupod tools are in the universe repo, so you dont have to download them from the site above.

---

### Post by nyuhuhuu on 2005-05-04
[QUOTE=reuben]gtkpod doesn't work for me :(

It seems happy, but after I have synced and then safely disconnected (i.e. unmounted) the shuffle, I get the flashing orange/green error lights. 

Any ideas?[/QUOTE]

This is beacuse only GtkPod version 0.88.2 supports Shuffle. Ubuntu arrives with package 0.88.1. Tested.

---

### Post by reuben on 2005-05-05
I guessed as much. Any idea as to ETA of 0.88.2 in the universe repositories?

---

### Post by jesse on 2005-07-07
**NO NEED FOR WINDOWS** 

This is a very useful how to. However, I was actually able to get my Ipod shuffle to work using Linux only to get it going, without the need to initialize it or format it on a Windows pc. I simply used gtkpod, opened the file menu and selected "create ipod directories" and everything worked. I don't have Windows or access to any Windows pc and didn't need it. 

I do have hfs file system packages installed on my Ubuntu Hoary, but I'm not sure if I even needed them to get the Ipod working. When first tried to get it going, I couldn't play anything but just got an orange blinking light error, until I read here that I need a newer version of gtkpod. I installed it from the debian unstable repository and the problem was solved. [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=129232#](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=129232#)

---

### Post by reuben on 2005-07-08
Cool; I can confirm this works well. 

For newbies who may be having the same problem:



sudo gedit /etc/apt/sources.list

add this line to the end:

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) unstable main non-free contrib


Save, fire up synaptic; reload; find gtkpod, and upgrade it to 0.93 :)

Some other stuff (notably libc) will be upgraded too; this is par for the course. It doesn't appear to break anything - YMMV.

Comment out the line in sources.list (put a # in front of it) once you're done upgrading gtkpod; you don't want to be using that repository as a matter of course.

---

### Post by reuben on 2005-07-08
I do have a question tho; how do I nuke the ipod's file system and rebuild it from scratch? Gtkpod has no nuke option.

---

### Post by jesse on 2005-07-09
Rueben, 

I wish I knew how to "nuke" the filesystem. I would do so by opening the device in a window browser like konqueror or nautilus (if the ipod is plugged in and mounted there will be an icon for it on the desktop) and deleting the files and directories manually like you would from a hard drive partition. 

I'm not sure what you meant by "nuke" though.

---

### Post by reuben on 2005-07-09
Yeah, that doesn't work for me; konqueror (and the cli) believe the ipod to be mounted as a "read-only filesystem" (despite the file permissions indicating otherwise).

By nuke, I mean refresh back to its original state, like the apple updater can do on windoze.

---

### Post by jesse on 2005-07-09
That's interesting. I'm using Hoary, and as soon as I plug in my ipod shuffle an icon shows up on the screen and I'm able to open it by clicking on it and can then add or delete files. Of course, this is not the way to put mp3 songs on it. For that you have to use gtkpod. 

As far as using the shuffle as a "flash disk" is concerned, have you tried running konqueror or nautilus as root? I don't even need to do so, as mine is writable even as a normal user. I'm using Gnome and nautilus by the way, not KDE and konqueror.

---

### Post by reuben on 2005-07-10
Yeah, I have tried as root. I haven't tried under gnome; I can't imagine it is very different, but I will give it a shot if I run out of other ideas
thanks

---

### Post by reuben on 2005-07-19
My Ipod was fried (I tried something stupid with the hfd utils) so Apple sent me a new one. Gtkpod had problems creating the directories until I manually added a line for the ipod in /etc/fstab:

/dev/sda1    /mnt/ipod    vfat    sync,user,noauto,umask=000    0 0

---

### Post by jesse on 2005-07-19
How on Earth did you fry it?

---

### Post by reuben on 2005-07-20
I don't know how I fried it originally, but it ended up so that gtkpod couldn't create dirs etc, windows couldn't reinitialize it, etc. So  I followed a howto somewhere which suggested zeroing it with dd, and then reformatting with the hfs utils. It stopped responding after the dd step. Luckily apple's return policy is most sweet - you just type your serial # in, enter your address, and they send you a new ipod, with a prepaid return package. I wonder if they'll play nice when the batteries start dying in a couple of years...?

---

