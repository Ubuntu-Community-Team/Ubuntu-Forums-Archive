---
title: "HOWTO: Transfer files to/from Sony Walkman MP3 player NW-E003F."
date: 2008-03-05
forum: Outdated Tutorials &amp; Tips
---

### Post by antonr on 2008-03-05
How to transfer files to/from Sony Walkman MP3 player NW-E003F.

(Probably works on other Sony NW-xxx models too.)
I did this successfully on Kubuntu 7.04

There is a java program JSymphonic which can transfer the files
in the correct way to the Sony media player.
(Being a java program it is cross-platform, so should work on Linux, Windows, Mac etc.)

[INDENT]	(There is another related project NW-E00x Mp3 File Manager
	which may be worth checking out too [This just appears to be an older version. Abandoned?]
	[http://sourceforge.net/projects/nwe00xmp3man](http://sourceforge.net/projects/nwe00xmp3man)
	)
[/INDENT]
How to run JSymphonic

Download JSymphonic 0.2b

[INDENT]	[http://sourceforge.net/projects/symphonic/](http://sourceforge.net/projects/symphonic/)
[/INDENT]	[http://sourceforge.net/project/showfiles.php?group_id=190494](http://sourceforge.net/project/showfiles.php?group_id=190494)
	[INDENT]The file I downloaded is  JSymphonic0.2beta.zip
	
	Unzip JSymphonic0.2beta.zip somewhere, so you will have a
	new directory JSymphonic0.2beta/
	
	Open a console (eg. Konsole) and change directory to the
	above directory.
	
	Inside there is a .jar file  JSymphonic_0.2b.jar[/INDENT]

Ok, so we have the java application, now we want to run it.
So make sure you have a version of Java which is compatible
with Sun's 1.6 version.

	[INDENT]Check your Java version in a console with:
	
		```
java -version
```
	
	It should report:
	
		[INDENT]java version "1.6.0"[/INDENT][/INDENT]

If not, then:
Install sun-java6-jre via Adept

	[INDENT]Roughly following the instructions in this page: [http://www.thelinuxsociety.org.uk/content/how-to-set-up-eclipse-in-ubuntu-using-sun-java-jdk-6](http://www.thelinuxsociety.org.uk/content/how-to-set-up-eclipse-in-ubuntu-using-sun-java-jdk-6)
	
	Open a console:
	
		```
sudo update-java-alternatives -s java-6-sun
```
	
	Edit /etc/jvm as root:

		```
sudo nano /etc/jvm
```

	and add to the top the command:
	
		```
/usr/lib/jvm/java-6-sun

```[/INDENT]
Now try to run the application:

	```
java -jar JSymphonic_0.2b.jar
```

It works!
The JSymphonic application window should open and after specifying
the location of the media player (for me it was /media/disk),
and the location of the mp3 files on your hard disk, you can
transfer and delete files from the Sony media player.
(Thankyou JSymphonic!)

It was recommended to actually copy the .jar file to the
Sony media player, then you carry the program with you
wherever you go. As long as the OS you plug into has
Java 1.6 installed, you can run JSymphonic.

I found that some mp3 tags were not displaying on the Sony player
correctly - boxes instead of readable characters. I fixed that by
first using Amarok to rewrite the mp3 tag header (just make any
small change, eg. add a space to the comment tag, then save).
After using JSymphonic to transfer the fixed mp3 to the Sony player,
it appears correctly. (Thankyou Amarok!)

Post back if if the above instructions work or don't work for you for any reason.

---

### Post by marn on 2008-03-17
Brilliant, thanks very much.

I used the alpha version (JSymphonic_0.2.1a.jar) and it worked perfectly. 

One more step towards independence!!

---

### Post by tropdoug on 2008-03-25
As a newbie, I don't want to run the risk of trashing my sony NW e005f  

so before beginning this can someone clarify the exact steps to take, ie do I have to format the player before beginning etc, or just delete the OMA files currently on there from sonic stage in windows? 

Thanks

---

### Post by marn on 2008-03-26
Hallo tropdoug

you don't have to format anything. You don't need to delete anything - that is what JSymphonic does. Follow the instructions from antonr and then run JSymphonic (you don't have to use the terminal if you dont want to, it can be started with right click --> open with "Sun Java 6 Runtime") JSymphonic dosen't reformat the player, so you should still be able to use it wit SonicStage, although I haven't bothered trying.

JSymphonic worked perfectly for me on my NW-E002 and on a friends NW-A1000 (albeit with a error message saying I should use compatible software :)) 

If you need anymore help, just ask

---

### Post by tropdoug on 2008-03-30
Thanks for that, ok all steps have been completed, but I have one problem, when I open symphonic, I cannot navigate to where my player is mounted which appears to be at the very top of the tree, alongside my ubuntu filesystem HD and the Windows HD. (see attachment)

When I plug the player into a USB port it automatically is mounted there. 

Some advice on either moving it, or specifying the correct path would help. 

Also when I downloaded the symphonic program, I put it in a new file I made in my 'Home' folder named 'Downloaded programs' (you can see my windows hangover hey!) so now I have a program installed there. I did not want that to happen, as all I wanted to keep in that folder would be the unpacked packages, so I still haven't worked out what folder on Linux is the equivalent of the 'Programs' folder in windows? But I guess to keep the integrity of the system, I should install all new programs into the same folder structure, should I not? 
(I will learn linux, I will learn Linux, I willll ......) :lolflag:

---

### Post by tropdoug on 2008-03-30
SOLVED! Doh, thanks for the help everyone, I suddenly realised what a dill I was being, and found the path just as Antonr described. 

Anyway thanks again guys.

---

### Post by |Porsche on 2008-03-30
Thanks for posting this. I found this post while googling Linux compatible mp3 players :). I guess I can keep my Sony NW-E003F for now, but I will get rid of anything sony in the future. That interface is better than Sonic Stage's hehe. 

Ahh viva FOSS. Rock On!:guitar:

---

### Post by tropdoug on 2008-03-31
anyone know if it's possible to compile a 'playlist' onto the sony player. In sonic you can make a playlist which is great, cos I have some deep meditation stuff, and with the playlist you can set it to just play those tracks. with  jsymphonic it's a B*tch to be deeply relaxed and suddenly Deep Purple comes on and blows me away!
Ok ok I know I am, showing my age, but hey good music is ageless :guitar:

---

### Post by antonr on 2008-04-01
Thanks for all the feedbacks !

About the playlist ;
In the version of JSymphonic that I originally used (0.2b), the readme lists playlist as a future feature.
I notice now that there is a newer alpha version available, which *may* have this feature. It's worth downloading to read the readme if you're really interested. Otherwise, you could look at the filesystem directly and try to figure out where and how a playlist is stored. I'm afraid I can't help you with that now because it's my friend's player, and he has it !
An alternative, constant-time, solution is to simply buy a second player (of different colour) , on which you load only meditative music. They are so cheap (I think my friend said it was ~AUD$30) that this should be a viable solution !

---

### Post by pt123 on 2008-04-01
Thanks I will try  this.

Before I was using  NW-E00x Mp3 File Manager, but it was buggy after the first addition of songs it was impossible to add any more at a later date. 
So I have been using windows and sonic stage to transfer songs.

---

### Post by dsm4r on 2008-04-30
[COLOR="Olive"]Thank-you I've been trying all sorts of things with my NW-E405 which I really love the design of (great for exercise). Jsymphonic worked a treat once I installed the DViD.dat file as per the readme.txt.
Now I can leave windows behind and be free, free, free.[/COLOR]



> **antonr said:**
> How to transfer files to/from Sony Walkman MP3 player NW-E003F.

(Probably works on other Sony NW-xxx models too.)
I did this successfully on Kubuntu 7.04

There is a java program JSymphonic which can transfer the files
in the correct way to the Sony media player.
(Being a java program it is cross-platform, so should work on Linux, Windows, Mac etc.)

---

### Post by manatsu on 2008-05-08
I have the Japanese NW-A919 and wanted to try the JSymphony to save some reboots to Windows. But it seems like there is a problem with the Hardy kernel and the sony player. The automount function of GNOME doesn't work and *dmesg* says:

 ```

[ 7904.836059] usb 4-4.3: new high speed USB device using ehci_hcd and address 11
[ 7904.928956] usb 4-4.3: configuration #1 chosen from 1 choice
[ 7904.942477] scsi7 : SCSI emulation for USB Mass Storage devices
[ 7904.945713] usb-storage: device found at 11
[ 7904.945719] usb-storage: waiting for device to settle before scanning
[ 7909.843484] usb-storage: device scan complete
[ 7909.844548] scsi 7:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 0 CCS
...
[ 7909.968649] sd 7:0:0:0: [sdc] 7977984 2048-byte hardware sectors (16339 MB)
[ 7910.077582] sd 7:0:0:0: [sdc] Write Protect is off
[ 7910.077590] sd 7:0:0:0: [sdc] Mode Sense: 00 34 00 00
[ 7910.077594] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 7910.077603]  sdc: sdc1
[ 7910.080544]  sdc: p1 exceeds device capacity
[ 7910.086095] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[ 7910.086167] sd 7:0:0:0: Attached scsi generic sg4 type 0
[ 7910.791717] attempt to access beyond end of device
[ 7910.791726] sdc: rw=0, want=4294967044, limit=31911936

``` 

Has anyone of you experienced similar problems?

---

### Post by Khaer on 2008-05-31
I have a problem with transfering files to my Walkman.
JS runs OK, but when I transfer files to the player, it just doesn't recognize them and displays "NO DATA" message. I know the files are there, because the free space on the disk decreases, and besides - JS sees them when I run it again.
And yes, I've set the device path in the options.

Any ideas?

---

### Post by antonr on 2008-06-01
> **Khaer said:**
> ... displays "NO DATA" message. I know the files are there, ...

Any ideas?

Hi Khaer,

I quickly searched the sourceforge Symphonic forum "Bug report"
[http://sourceforge.net/forum/?group_id=190494](http://sourceforge.net/forum/?group_id=190494)

and found this thread
[http://sourceforge.net/forum/forum.php?thread_id=1969339&forum_id=747001](http://sourceforge.net/forum/forum.php?thread_id=1969339&forum_id=747001)

which discusses a "NO DATABASE" message. Maybe it is the same?
It has a possible solution of deleting some of the files (particular files used for indexing etc) in the player and then using Symphonic to recreate the database.
(I would try to back up the files first.)
It's not guaranteed, but maybe that will work for you.

---

### Post by praads on 2008-06-01
Hi,
Is this work for SONY NW E013F (B) also? Please help me on this

Praads

---

### Post by mdma1 on 2008-06-10
i luv  you people. everything works perfectly. many thanks from russia

ps i use ubuntu 8.04 with nw-a608 and i'm so happy now so happy)))

---

### Post by heinlich on 2008-08-06
Hi, I just downloaded jsymphonic for my Hardy and my sony nw-s705f walkman player. The software is so small, convenient and powerful, 100 times better than SS. Now I can stay from Windows for another step away. But there is a question, after loading mp3s to the player, and I unplugged the player, it read the data and appeared "simple mode", and I couldn't see the album cover anymore, for any song. Other functions just worked like a charm.
Anybody has the same problem with me?thx

---

### Post by mike76 on 2008-08-15
> **manatsu said:**
> I have the Japanese NW-A919 and wanted to try the JSymphony to save some reboots to Windows. But it seems like there is a problem with the Hardy kernel and the sony player. The automount function of GNOME doesn't work and *dmesg* says:

 ```

[ 7904.836059] usb 4-4.3: new high speed USB device using ehci_hcd and address 11
[ 7904.928956] usb 4-4.3: configuration #1 chosen from 1 choice
[ 7904.942477] scsi7 : SCSI emulation for USB Mass Storage devices
[ 7904.945713] usb-storage: device found at 11
[ 7904.945719] usb-storage: waiting for device to settle before scanning
[ 7909.843484] usb-storage: device scan complete
[ 7909.844548] scsi 7:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 0 CCS
...
[ 7909.968649] sd 7:0:0:0: [sdc] 7977984 2048-byte hardware sectors (16339 MB)
[ 7910.077582] sd 7:0:0:0: [sdc] Write Protect is off
[ 7910.077590] sd 7:0:0:0: [sdc] Mode Sense: 00 34 00 00
[ 7910.077594] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 7910.077603]  sdc: sdc1
[ 7910.080544]  sdc: p1 exceeds device capacity
[ 7910.086095] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[ 7910.086167] sd 7:0:0:0: Attached scsi generic sg4 type 0
[ 7910.791717] attempt to access beyond end of device
[ 7910.791726] sdc: rw=0, want=4294967044, limit=31911936

``` 

Has anyone of you experienced similar problems?


Yes, I have. My sony does not mount and I can't find it it's like it is not detected at all.  Any hints I can try?

Thank you.

---

### Post by Proton Soup on 2008-08-18
> **antonr said:**
> Thanks for all the feedbacks !

About the playlist ;
In the version of JSymphonic that I originally used (0.2b), the readme lists playlist as a future feature.
I notice now that there is a newer alpha version available, which *may* have this feature. It's worth downloading to read the readme if you're really interested. Otherwise, you could look at the filesystem directly and try to figure out where and how a playlist is stored. I'm afraid I can't help you with that now because it's my friend's player, and he has it !
An alternative, constant-time, solution is to simply buy a second player (of different colour) , on which you load only meditative music. They are so cheap (I think my friend said it was ~AUD$30) that this should be a viable solution !

this thread?: [http://sourceforge.net/forum/forum.php?thread_id=2007399&forum_id=747000](http://sourceforge.net/forum/forum.php?thread_id=2007399&forum_id=747000)

i ran into the playlist problem just the other day.  i wanted to put together a set of workout music, copied everything into a folder, and when i tried to transfer the files, they all got split up. :(

so...  i thought i was going to be clever and make a workaround, changing the ID3 tags with Ex Falso.  i changed artist to "various artists", and album to "workout mix 1".  and from in JSymphonic, it appeared to work, but on the device itself i could never get to the new album i'd created.  so i thought maybe i'd messed up the database or something by not fiddling with the tracks.  tried to delete my additions, but although JSymphonic says it deletes, the files never seemed to leave the device.  set the tracks in Ex Falso, tried to import again, and still they appear to be there, but the device won't let me select my new album.  any ideas on what i may be leaving out here?  i haven't tried resetting the device yet.

---

### Post by sleepy_head on 2008-09-09
for me jsymphonic also works fine. nw-a3000

do anyone know if there's a project page?

---

### Post by futuroimperfetto on 2008-11-15
Hello,

 I just wanted to record more success for this solution. My girlfriend has a Sony NW-S705F Walkman bought in Japan and we were fed up with SonicStage.

She has Windows XP and not close to getting into the Ubuntu bandwagon (but I'm not done yet with her :P).

We downloaded the latest Java version for Win Xp and then JSymphonic and it worked like charm. 

Thank you for this solution antonr! :popcorn:

---

### Post by hpeat on 2008-11-23
thx guys but im having problem with some mp3 exported from my sony walkmann.it doesnt want to play in any of my players.any ideas?

---

### Post by scampiuk on 2008-12-03
Hi all,

I must say,as someone who's been looking for software to run my NW-A3000 on Linux for ages, the JSymphony application has saved me buying a new player!  Works' great, even tho it's still in development. 

Shame they don't enable Donations, I feel I owe them a few dollars :D

Scampi

---

### Post by smolty on 2008-12-17
I have no idea what is causing this but I can only transfer some of my music. If I click 'import' then 'apply' then it indicates that the music has been added to my Sony Walkman A806. On pressing 'ok', where I should then see a list of my music beneath the usb icon, there is nothing. And if I open up my walkman then it shows the songs but it wont let me play them. But some of the songs do play and show up as being on the player when transfering. So it obviously works with some files but not others.
Any ideas???

---

### Post by Skiro'n on 2008-12-27
Hi !

I'm JSymphonic main developer, I have just discover this topic. Since I found many topics talking about SonicStage, Sony's player under Linux or whatsoever refering to JSymphonic, I created [a topic to talk about it here]("http://ubuntuforums.org/showthread.php?p=6446800#post6446800").

Please consider that I've just released a new version (0.3.0a1) for Christmas. All bug reports should now refer to this version.

Concerning what you said here before:
- for the problem in exporting files, first try the lastest version, and if the bug is still present, do you know if initial title format was Atrac or Mp3 ? Can you send me a file which is not playable (nicolas_cardoso ~at~ users <dot> sourceforge.net).

- we didn't enable donation, if you want to thank us, support us, test, talk about us... :-)

- project page: [http://sourceforge.net/projects/symphonic/](http://sourceforge.net/projects/symphonic/)

- problem with "split artists", I will shortly improve the "read tag feature" so that it could be possible to read info from folder structure instead of tag, it should resolve the problem.

- intelligent fonctions (present on some device, like nw-s70x) are not yet implemented, this is planned after cover and playlist support.

---

### Post by claudia27 on 2009-11-27
Hi there! I'm pretty new at handling Linux and I've encountered some problems with this programme. I've followed all the instructions,did all i had to do in the console and still, it says that the .jar file can't be accessed...i did download another version of JSymphonic but i wrote the exact name of the jar file in the console...and i don't know what could have happened,like i said...I'm new at this,but i wanna learn...so...when you have time...some suggestions could help. Thanx!

---

### Post by TNuno on 2010-06-16
ok people. I tried, i download the program, but my issue is the right thing to put in device path, because the program says that can not find OMGAUDIO, so if i right click on walkman icon appear in the location computer:/// , if i click on OMGAUDIO folder appear /media/WALKMAN, i tryed both but appears always the same message!

Any way to solve it ?! 
Thanks in advance

---

### Post by cinger on 2010-07-28
This was pretty easy in lucid with a new sony nwz-e344.  
First I opened synaptic (sudo synaptic), did a quick search for java runtime, selected sun-java6-jre, the dependencies were automatically loaded, then sudo apt-get install jsymphonic to install jsymphonic.  

(Edit: At some point in the install I was directed by another page to sudo apt-get install ffmpeg, not sure if this was needed for success..)

Then I plugged the walkman into the usb, made sure the WALKMAN's files were uppercase, and that it was mounted properly to /media, then opened jsymphonic from Applications/Accessories, input the correct path to the mounted WALKMAN (/media/WALKMAN for me), and began managing music with drag and drop.  

I placed different folders into the WALKMAN/MUSIC folder, and the sony device seems to recognize and differentiate them pretty much as you would expect for playlists, and I just navigate to music/folders on the device.

All said, it was probably as easy to get this going out-of-the box using linux as it would have been under winblows.

---

### Post by Aeriel on 2010-11-22
i don't know if this is still open or whatever but my jsymphonic won't let me add/delete files to my mp3 and i don't really know why... the error message says that it can't delete my old database and it can't add a bunch of files .
also, i don't really know what generation to put so maybe that's the problem?
thnx

---

