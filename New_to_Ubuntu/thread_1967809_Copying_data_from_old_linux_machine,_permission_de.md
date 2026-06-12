---
title: "Copying data from old linux machine, permission denied!"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by stc4thots on 2012-04-28
my mom was using ubuntu on her old toshiba laptop, and unfortunately it completely died recently. i pulled the harddrive from it and put it in a case, and am looking at the files i want to copy to her new pc. But alas, i do not have permission to even read them! 

can i force my way in so she can have her documents etc or does she just have to pay the price of being careless with her data?

Also, i am a relative novice, ive poked around with linux many a time but have never reached a level of proficiency that i see from most users here, so id prefer if theres a solution simple enough to do through the GUI, and off the live cd but beggars cant be choosers.

thank you for your time!

---

### Post by kimda on 2012-04-28
You can do alt-f2 and enter 
```
gksudo nautilus
```

Which starts nautilus with root permissions. This will alow you to copy/move files to the other drive. When you reboot to the other drive you want to set the permissions back to your moms account. You can do the same thing when you are logged in with her account (change folder permissions back to her account).

---

### Post by souravc83 on 2012-04-28
Did that work?
If not, you can do it the old command line way too.
If it is automatically mounted, I believe this drive should be in /media folder.

so can you open a terminal and type: 

```
cd /media

```
```
ls
```

one line at a time, and tell us the output of the last command.

Then you should be able to change permissions with the 'chmod' command.
We can write the syntax for you, if we know the output of the ls command.

---

### Post by stc4thots on 2012-04-28
i think there is some misunderstanding, mom's laptop is long dead, will not boot, the harddrive has been transferred to a case, and im using my laptop with a live cd to try and read the ext3 file structure (the utilities i found for xp pro (my main operating system) to do this kept prompting me to format the drive).

because im doing this off a live cd, nautilus doesnt seem to want to run. and like i said, im trying to use a live copy of ubuntu, to poke through an old installed ubuntu.

it may just be that it cannot be changed without me physically booting the old installation, in which case ill persue that. ive never tried to boot off of a usb harddrive before? is this a cleaner way of doing things than bugging you (kind and punctual!) folks?

the ls command worked, it spat this out

19eeb12a-687b-4c51-b2d8-b2cd8e80237e  cdrom  FreeAgent GoFlex Drive

thanks for the help i have received so far!!!

---

### Post by souravc83 on 2012-04-29
Okay.I've never worked off a LiveCD to mount a hard drive before.

The "ls" command gives the names of the folders which are mounted.(The drive is mounted as a folder)
I presume one of the folders that you mention is your mom's hard drive.
Its difficult for me to tell which one. 
Do you know which one it is? 
My suspicion is that it is:
19eeb12a-687b-4c51-b2d8-b2cd8e80237e 

but I might be wrong.
Assuming it is this one, you can use this command:
```
sudo chmod -R a+rw /media/19eeb12a-687b-4c51-b2d8-b2cd8e80237e 

```

This should solve your problem.

If your hard drive is any of the other folders, replace the name in the last command with the name of the folder which is your hard drive.


If you don't know which folder is your hard drive,try these:

1. The stupid but best way. unplug the hard drive. Type the commands I mentioned in the earlier post. See the result. One folder will me missing. This will be your hard drive. Now plug your hard drive back again.

2. Check out the sizes of the folders. If you know the size of the hard drive you can find out which folder represents the hard drive.

Go to terminal and type:
```
cd /media
ls -lh
```
one line at a time. This will give you the sizes of the folders in the fifth column. I presume the had drive will have a large size and the others a much smaller size.

Maybe if you paste the output of the last command, we can guess.

3. Mouse click to the media folder, and then you can see the four folders you mention. Right click on each of them and find the sizes.Or unplug hard drive and see which folder is no longer there.

---

### Post by kimda on 2012-04-29
So basically you have your mom's drive in a usb drive and you want to read with the live cd. And then transfer the files to your harddrive? 

If you boot with the life cd and you plugin the usb drive is it recognized by ubuntu? You should be able to see it in nautilus.

---

### Post by djpurity on 2012-08-01
**I think I understand perfectly what is going on here, because I am having a very similar problem.**

Basically, due to a cat mistaking my powered on & shut laptop as a litterbox, thus "**[COLOR=Olive]wetting[/COLOR]**" my laptop, no, ***[COLOR=Olive]SOAKING[/COLOR]*** my laptop with **[COLOR=Olive]cat ****[/COLOR]** (which is _*quite*_ repugnant), before I could power it off and clean it, it seemed to have shorted something in the laptop. After *_**much**_* cleaning and drying it out, and equally much troubleshooting, I narrowed it down to the **hard drive** as the main device that shorted somehow, causing **Ubuntu to not properly work**. It would start up sometimes, but **crash erratically, spontaneously, and unpredictably**; it would **run incredibly slow** to the point I could not even open one web page, even after one night of trying to wait it out. **Five hours later** I still had not *_one_* full website or web page loaded. I gave up.

I then created on another computer two variations of a **live Ubuntu  64-bit 12.05 LTS** bootable image; one burned to a **USB flashdrive** and one to a **CD-ROM**. I am now trying to recover what is on my hard drive to yet *another* **USB flashdrive**. Or anywhere. 

**Like the lady above**, my **old hard drive** changed names to this really long-winded device name under the [COLOR=DarkGreen]**/media/ **[COLOR=Black]in the folder:[/COLOR]** /media/6efe5381-f6a3-4577-acc9-96b252c3e5ee**[/COLOR]. It was _***never***_ called that before ([COLOR=DarkGreen]**6efe5381-f6a3-4577-acc9-96b252c3e5ee**[/COLOR]). It is **owned** by [COLOR=Navy]**root**[/COLOR] and thus when I used to try to access any files on it, it refused to let me, saying **I did not have the permissions**. I have been reading the forums and fooling with [COLOR=Red]**chmod**[/COLOR] and **[COLOR=Red]chown[/COLOR]**  on this drive and its subfolders so I can copy my music, my work files,  my documents, my art portfolio, my web graphics, my web sites I was  building, my legal documents, my receipts, my letters, my records, my  saved emails, my tons and tons of irreplaceable photos and images from  my webcam as well as my digital camera, as well as off the Internet and  friends' emails; the list is endless.

What I really want to do is simply **format the hard drive and reinstall** **Ubuntu** freshly on it and start again; I hope that perhaps this will solve the problem. Perhaps the **[COLOR=DarkOrange]cat ****[/COLOR]**,  since it has salt in it, became an even better electrical conductive  medium, and perhaps thus the hard drive was written to in incorrect  areas, or the MBR or something like that got overwritten, or something  else got overwritten that wasn't supposed to be, or areas or blocks of  data just went AWOL. I don't know. Both the **live Ubuntu boot discs** are running fine, whether off the **USB flash drive** or the **CD-ROM**. 

I *was* having some trouble getting the **permissions** set correctly so I could **copy these files** to a new **USB flashdrive**  so that all data that is important and essential to my existence is  saved and preserved before just wiping it out. At one point **I accidentally set the ownerships** of part of the drive to an owner named **[COLOR=Navy]777[/COLOR]** of the group **[COLOR=Navy]1000[/COLOR]**. I think I meant to set ***something*** to [COLOR=Navy]**777**[/COLOR], just not set the ***owner*** ***name*** to **[COLOR=Navy]777[/COLOR]**. Anyway a mistake on my part because I forgot what [COLOR=Navy]**777**[/COLOR] was for, and the syntax of [COLOR=Red]**sudo chmod**[/COLOR] and [COLOR=Red]**sudo chown**[/COLOR] was wrong, hence the error.

So I am following this thread as well, despite it being a little  outdated, in hopes that in answering the question about the woman using  her husband's laptop to save his stuff for him due to his lack of  understanding, would also answer my question of saving my own stuff.

I tried to plug in an **RCA USB MP3 player**, and despite at one point being able to access my /media/[COLOR=DarkGreen]**6efe5381-f6a3-4577-acc9-96b252c3e5ee/home/djpurity/Music/**[/COLOR] direcrtory, none of the folders showed any of my mp3 collections within them. **All the subfolders** were strange looking and **unknown file types**  and not being recognized as folders themselves, thus not showing the  contents within them (all the mp3s that I had sorted by album, the album  being the folder name, but now just an unknown file type... **_I hope I didn't lose all those mp3 files that were once within those folders!!_**). Then I realized that I had accidentally recursively [COLOR=Red]**chown**[/COLOR]'d them to the **owner** named **[COLOR=Navy]777[/COLOR]**, like I said, and I was at a loss at how to **become that owner**, or otherwise put it back. I think I got it, as I just tried the code:

sudo chmod -R a+rw /media/6efe5381-f6a3-4577-acc9-96b252c3e5ee 
And I hope that it will **change the permissions** at least, but I think firstly, I MUST change the **ownership** to [COLOR=Navy]**Ubuntu Live User**[/COLOR] of **group** **[COLOR=Navy]Ubuntu[/COLOR]**. I **cannot** start **Nautilis** like this:

gksudo nautilus 
Because using the **CD-ROM Live Ubuntu version,** I _cannot_ write any new files. I think if I run it off the **USB Live Ubuntu version**, I _can_. But since I am now on the **CD-ROM**, I would like to [COLOR=Red]**chown**[/COLOR] back to [COLOR=Navy]**Ubuntu**[/COLOR] rather than fool with **Nautilis** setting myself to **root ownership**.

Can anyone tell me **how to change the ownership** back to either [COLOR=Navy]**root**[/COLOR] or [COLOR=Navy]**Ubuntu Live User**[/COLOR] with full read, write, execute, create directories, delete directories, all that and more? I think **[COLOR=Red]chown[/COLOR]** comes first, then [COLOR=Red]**chmod**[/COLOR]. I wouldn't have to do the [COLOR=Red]**chown**[/COLOR] except I screwed up and changed it to **[COLOR=Navy]777[/COLOR]** as I said.... I forget how I did that because now whenever I try to do a [COLOR=Red]**chown**[/COLOR], it says that I am doing it wrongly.

I think answering my question will also solve this issue. We both seem to have the same problems!** I also could not see my old hard drive due to permissions**  while running a live Ubuntu copy! I am getting there, but little by  little. I think she is as well. I don't think her old hard drive is on  USB.

[COLOR=Purple]**Does this make sense??? Thanks!**[/COLOR]

---

### Post by mastablasta on 2012-08-01
right click on the drive in the file manager and then propperties and select permisisons you want to have for it.

---

### Post by JKyleOKC on 2012-08-01
Djpurity: As a cat person from way back, I can well appreciate your situation! However, I don't think it was the hard drive itself that suffered the damage. If it were, you would not be able to read it at all now.

The most likely component for damage would be the laptop motherboard itself, which holds almost all of the electronic stuff that makes the computer work, and I'm sure that dried cat urine is an excellent conductor, and when it's liquid it's still better. It would take only one short on the motherboard to literally burn out critical components. I'm afraid that your laptop is now toast.

All is not lost, however. Since you can read enough of the drive's data to get it mounted, your chances of recovering your files are very good. Do NOT fiddle with changing ownership or permission, though, since that can easily make them unreadable. Just force permission for yourself on the Live CD session by typing "gksudo nautilus" at a terminal prompt, then use copy and paste to copy each file or folder from the laptop's drive to another location such as a second external drive.

When in the file manager that results from that command, take extreme care NOT to delete or move anything. Only copy from the laptop drive, nothing else.

---

### Post by djpurity on 2012-08-02
Okay, I went to [COLOR=Red]**ALT+CTRL+F2**[/COLOR] and entered [COLOR=Red]**gksudo nautilus**[/COLOR]. It seemed to work so I went back to the **GUI** because I couldn't find the **8GB** new **SanDisk USB flashdrive** under the [COLOR=Purple]**/dev/**[/COLOR] folder, where my **CDROM** and my other 4GB flashdrive named **KUBUNTU** are the only ones listed. It could be because I had formatted these to be **Ubuntu bootable mediums**.... (??) while the **8GB SanDisk flashdrive** is one I just got and haven't formatted it yet. But it ***is*** readable in [COLOR=Red]**Unity**[/COLOR], and I can **create** and **delete** **folders** and **access all the folders** that came preformatted on it.

Now back in [COLOR=Red]**Unity**[/COLOR], I am looking through my home folders on my hard drive, and **all the subfolders** within the ones I have under [COLOR=Purple]**/home/djpurity/***[/COLOR] are all **unknown file types**.. thus I cannot access the numerous and impossible to count files that are sorted within these folders. How did the folders get turned into these strange icons, and when I double click on them, they say I still "**[COLOR=Navy]DO NOT HAVE PERMISSION TO VIEW THE CONTENTS OF[/COLOR] "[COLOR=Purple]PHOTOS OF FRIENDS[/COLOR]**" *etc*... where "[COLOR=Purple]**Photos of Friends**[/COLOR]" is a **subfolder** of my [COLOR=Purple]**Pictures**[/COLOR] folder.

When I click on **PROPERTIES**, it shows that under **Permissions**, "[COLOR=Blue]**THE PERMISSIONS OF 'PHOTOS OF FRIENDS' CANNOT BE DETERMINED.**[/COLOR]" Under the **Basic**, it shows **TYPE** as: "[COLOR=Blue]**unknown (application/octet-stream)**[/COLOR]" and **CONTENT** as "[COLOR=Blue]**unreadable**[/COLOR]" and the **Location is accurate**, but **VOLUME** is also "[COLOR=Blue]**unknown**[/COLOR]" as well as **FREE SPACE**, also "[COLOR=Blue]**unknown**[/COLOR]." These are all for the subfolder that I just tried to open and failed.

Anything else within the **base** **directory [COLOR=Purple]/Pictures/[/COLOR]** is viewable or able to be opened. It is just **subfolders** that somehow have become corrupted. As I look at the other subfolders within the folders under [COLOR=Purple]**/home/djpurity/**[/COLOR] I see that _**NOT ALL**_ the **SUBFOLDERS** in every folder are corrupted. It just appears to be **the most important files**!!! Go figure!!! For example, in the **[COLOR=Purple]/home/djpurity[/COLOR][COLOR=Purple]/Music/[/COLOR]** folder, it lists all the artists as folders I can access. But the subfolders within each artist are *all* corrupted, but any mp3s that are within the folders are *not*. 

What is going on here? Can I still copy the contents of these directories? Like, if I did it in a [COLOR=Red]**terminal**[/COLOR] or something? Is it possibly just within [COLOR=Red]**Unity**[/COLOR] that the corruption is appearing?

In [COLOR=Red]**Terminal**[/COLOR], the hard drive is under [COLOR=Purple]**/media/6efe5381-f6a3-4577-acc9-96b252c3e5ee**[/COLOR] and now in the **GUI Properties** of [COLOR=Purple]**6efe5381-f6a3-4577-acc9-96b252c3e5ee**[/COLOR], it states that [COLOR=Navy]**(Some of the Contents are Unreadable)**[/COLOR] when it is listing the total number of files, a number that keeps counting upwards, not staying consistent. 

Do any of the pieces of this puzzle add up to any bigger picture? Even after going into the **[COLOR=Red]ALT+CTRL+F2[/COLOR] terminal screen**, and typing [COLOR=Red]**gksudo nautilus**[/COLOR] it still states under **Permissions** of the hard drive as being [COLOR=DarkGreen]**Root**[/COLOR] and that I am [COLOR=Navy]**NOT the owner and can NOT change the permissions**[/COLOR]. 

Didn't I get those permissions with **[COLOR=Red]gksudo nautilis[/COLOR]**? Or did I do it in the wrong screen? Well, like I said before, I ***_CANNOT_*** TYPE THAT COMMAND IN [COLOR=Red]**TERMINAL**[/COLOR] that is opened in **[COLOR=Red]UNITY[/COLOR]** because it will tell me: [COLOR=Navy]**Nautilus could not create the required folder "/root/.config/nautilus". Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.**[/COLOR] This is because I am running Ubuntu off a Live CD. Now if I had it on a USB drive, I probably could do this.

BUT what about the folder corruptions and their contents? Are they repairable?? 

I do have **[COLOR=Green]KUBUNTU[/COLOR]** on a **bootable USB drive**, but I am not familiar with **[COLOR=Green]KUBUNTU[/COLOR]**. I am sure it is easy to figure out; it is just another variety of **[COLOR=Green]Ubuntu[/COLOR]**. I am sure I could figure out how to get into [COLOR=Red]**Terminal**[/COLOR] there and type the **[COLOR=Red]Nautilus[/COLOR]** command. Perhaps with that, I could view and access the contents of the hard drive that I cannot while running a [COLOR=Green]**Live Ubuntu CD**[/COLOR] that is not a CD-RW.
[B]
Help![/B] (Should this be moved to its own Thread?)

---

### Post by JKyleOKC on 2012-08-03
Unfortunately I know nothing about Unity's operation, having avoided it completely. It's possible that the system is recognizing the drive as being formatted by Windows, and if that is the case then ownership and permissions will be set during the mount process and cannot be changed later from the command line. However it will take someone with more knowledge of the 12.04 packages to help you from this point on... Sorry!

---

### Post by Paqman on 2012-08-03
It sounds to me like the drive has suffered some degree of corruption. I would make a backup of it using something like dd or dd-rescue, which will copy absolutely everything on it. From that copy you could try **chown**ing all the files (if it'll let you), and if the filesystem seems really broken you can try using a recovery tool like photorec (part of the [testdisk]("apt:testdisk") package) which will recover files on a one-by-one basis. I wouldn't bother trying to repair the filesystem, just get your data off there safely.

By the way, you don't want to be rummaging around in /dev. Things in /dev are the system's way of representing actual devices (hence /dev), what you want to get at is the filesystem on that device, which will be mounted at /media for a removable device.

Unity isn't an issue, things like this work exactly the same as previous versions.

---

### Post by Kirboosy on 2012-08-03
Since the data is going to be moved off the drive anyways wouldn't it be simpler to do the following

```
chmod -R 777 /media/<drivepath>/
```

That way you can retrieve all data off the drive easily and not have any permission issues...

---

### Post by thunder686 on 2012-10-21
If you are trying to access the home folder from kubuntu live CD then you should use this command from the terminal to access the home folder that has restricted permission.
> kdesudo dolphin

---

### Post by Myglaren on 2012-11-17
I'm having a similar problem.   My desktop motherboard died so I pulled the hard drive and put it in a USB caddy, dragged the home folder onto my laptop - it did shout about not having permission but did it anyway.
I repartitioned and reformatted the drive but now it refuses to allow me to drag the files back onto the desktop drive.

It doesn't seem to like the idea of changing the ownership despite me using the same username and password on both machines.

I had presumed that the repartition/reformat would nullify the ownership but not so, it would seem.

---

### Post by audiomick on 2012-11-17
Just to make sure I understood: you moved the files off the drive out of the desktop, the old drive, onto your laptop, and then reformatted the drive after that. Now you want to move the files back to the newly reformatted old drive. You had a warning about permissions when moving the files. 

A very important question: can you see the files in question on your laptop? It is possible, if you didn't have permission to move them, that they didn't get moved.

If the files are on your laptop, it is possible that they still are owned by the user off the desktop that the old drive came out of. I gather that having the same user name etc. isn't quite enough. There is some behind the scenes identification that means that this can go wrong. I am not well informed about this, though.

Anyway, assuming the files are really where you think they are, and that you are using a standard Ubuntu, you should be able to start an instance of the file manager, Nautilus, with root privileges and change the ownership to that of the user on the laptop. To do this, do
```
gksu nautilus
```
in a terminal. Enter your password upon the request, and don't worry that you don't see what you are typing. Hit enter.

In the resulting instance of the file manager, navigate to the files in question, right click on them and choose properties. On the appropriate tab in there you can see and change the ownership. When the user on the laptop owns the files, you should be able to move them to wherever you want.

If you then take the old drive and use it in a new installation, you are likely to have to change the ownership again to match the new user on the new installation.

As you have no doubt gathered your self, the ownership properties are associated with the files themselves, and not with the drive or partition that they are stored on.

---

