---
title: "Ubuntu's Disk usurp &amp; yet visible nowhere!?"
date: 2016-08-26
forum: New to Ubuntu
---

### Post by saurabhdua2 on 2016-08-26
Hello Members!

I preferred installing Ubuntu(latest version) alongside Windows 8. Installation went through successfully but the System-Restart(as per the last prompt) has left me with the Windows Installation only, & Ubuntu is visible nowhere!

I remember seeing message during this Reboot which said--"Press any Key to skip Disk checking"....& then it went on to repair my Recovery Drive to 100% in split-seconds!

No trace of Ubuntu's installation or the Boot-menu (offering the choice b/w Windows & Ubuntu) are visible!?

However, Yes, Ubuntu's installation has indeed usurped my Free-Disk space to the tune of 250 GB, & as a consequence---Windows partition can be seen as reduced significantly!

Kindly help me set the things in order from here on....

Yours cooperation will be sincerely appreciated.

Thank you.

---

### Post by deadflowr on 2016-08-26
I'd say run boot repair's boot info summary and post the outcome in this thread.
Here's how to use boot-repair:
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

And here's how to set-up the boot-info part:
[https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")

For now, just run the boot-info summary part and post the outcome so that others who can help will be able before anything else bad might happen. 

well, that's what I think you should do, at least.

---

### Post by Impavidus on 2016-08-26
Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). Don't run the recommended repair yet, but create a BootInfo summary. Share the url it gives you with us. That should give us all the details we need.

---

### Post by saurabhdua2 on 2016-08-26
Hello deadflowr!

Initial Boot-Info repair summary can be accessed via [http://paste.ubuntu.com/23094541](http://paste.ubuntu.com/23094541)

& the one associated to Post-repair can be accessed at [http://paste.ubuntu.com/23094577](http://paste.ubuntu.com/23094577).

I wish to convey my Heartiest Thanks for your Guidance which helped me steer past the evident trouble! Have posted this response from within Ubuntu OS only!
Boot-Menu is now accessible with Multiple ( & Confusing) entries within it!

Nevertheless, I'll spot the one associated to Windows OS by hit & trial method. :-)

Thank you.

---

### Post by ajgreeny on 2016-08-26
Your description of how this has turned out suggests you probably installed Ubuntu in legacy BIOS mode instead of UEFI, and if Win8 was preinstalled when you purchased the computer it would  almost certainly have been in UEFI mode.

Boot Repair is the way to be sure of this but as the others have said **DO NOT ACCEPT THE DEFAULT REPAIR**, simply run the Boot-Info-Script and post back here the pastebin URL you are given.

EDIT:
It looks as if I might be too late to the party, but I am not sure from your post #4 whether or not you have solved the problem.
Can you now boot into either OS from a boot menu of some sort or do you have to run through a confusing procedure of some kind to do so?

What do you mean by **"Boot-Menu is now accessible with Multiple ( & Confusing) entries within it!"**

---

### Post by saurabhdua2 on 2016-08-26
Hello Impavidus!

Thanks for reiterating suggestion which helped resolve the trouble in a comprehensive manner! I wonder what a 'Magical' tool is this--Boot-Repair!
It ran plenty of Commands while disseminating Child-like instructions to the end user which were so simple to follow & implement!

I'll be surely sending Compliments to the creator via [email]boot.creator@gmail.com[/email]. What a magnificent creation on this part!!

& Yes, plenty of Thanks & Heaps of praises for the Guys@Ubuntu Support forum as well!

Heartiest Best wishes for your entire Team! Well-done! :-)

Hello ajgreeny,

For installation of Ubuntu, I chose the very-direct option getting listed against the Installer which said----"Install alongside Windows", & never came across any such Screen asking for my preference towards UEFI or Legacy BIOS.

That's how Ubuntu interpreted the scenario & sneaked in alongside Windows. :-)

I have already posted 2 URLs---associated to pre-repair & post-repair.

Is there anything else I need to do to offer you with more insidious details? Kindly suggest more on this further step.
 
& Lastly..."Default repair" were preceded by -- "Press any Key to skip Disk check"..& I couldn't foresee its Impact as there were no advisories listed anywhere on the frontal Ubuntu's resources (meant for the beginners & novices).

Thanks.

---

### Post by ajgreeny on 2016-08-26
Yes, definitely too late to the party, but as you are now apparently all sorted, can you please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

### Post by saurabhdua2 on 2016-08-26
Dear ajgreeny,

Boot-menu were found to contain 8-10 entries ! The ones associated to RECOVERY of Windows are also listed over there!
Would compile the entire list on a piece of paper & will post the same in a short time to come.

That's for I said--- A Number of unfamiliar entries under Boot menu.

Thanks.

Hello Members!
Please help me wade through these Confusing entries getting visible against the Boot-menu.  [http://bit.ly/2bHirbK](http://bit.ly/2bHirbK)

Upon choosing any of the relevant entries associated to Windows OS, this Boot-menu is disappearing altogether from subsequent System restarts & Windows OS is loading automatically without offering me a choice to choose b/w the two!?

Thereafter, Iam able to gain access to Ubuntu by fiddling with BOOT-ORDER again through the BIOS set-up of my HP AIO Desktop PC (18-1206in).

Thread continues to remain unresolved. Please assist further.

Thanks.

_PS - Here are the following Hyperlinks associated to Boot-Repair Logs::::_

1) [paste.ubuntu.com/23095013](paste.ubuntu.com/23095013)

2) [paste.ubuntu.com/23094905](paste.ubuntu.com/23094905)

3) [paste.ubuntu.com/23094577](paste.ubuntu.com/23094577)

4) [paste.ubuntu.com/23094541](paste.ubuntu.com/23094541)

Image here.
[http://bit.ly/2bHirbK](http://bit.ly/2bHirbK)

---

### Post by Dennis N on 2016-08-27
They are EFI (or UEFI) applications for various purposes. Read more:
[https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Applications](https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Applications)

---

### Post by saurabhdua2 on 2016-08-27
Hello Dennis N!

I wish to inquire whether that's how the Boot-menu should look like upon a Flawless installation of Ubuntu?
Secondly, upon choosing any of the relevant entries associated to Windows OS, Iam unable to see such a Boot-menu thereafter!
Everytime Iam made to tinker with the Boot-order within BIOS setup to gain an access to the Ubuntu again!

Please reveal a more insight on the basis Boot-repair info summary.

Thanks.

---

### Post by Dennis N on 2016-08-27
These entries starting with /EFI/HP are probably pre-installed with Windows by HP. Judging from the titles, they are for diagnostics, recovery, and updates to the firmware.

My own UEFI machines (I assemble from components) do not have Windows installed, and don't have extra entries like these in the grub menu or the UEFI boot menu. How common they would be I can't say.

I understand that on some machines, Windows will rearrange the boot order if it finds it is not first in order for booting. Your HP machine may be one of those. That would explain why after selecting Windows, it boots Windows by default on the next boot. There are ways to fix this, but I don't know the details. Please wait for a response from a member who knows this fix.

That said, I don't think you need to use boot repair for this.

If you don't get an answer in a day or so, post a question in "Installation and Upgrades" on the Windows problem.

---

### Post by saurabhdua2 on 2016-08-27
Dear Dennis N,

Thanks for the above reply.

However, I were in fact suggested to run Boot-Repair Utility as per the posts made by fellow members towards - [http://bit.ly/2bOu9yW](http://bit.ly/2bOu9yW)

I decided to install Ubuntu 16.04 LTS 'alongside' Windows 8 & have now run into this trouble.

Nevertheless, I will make sure to follow your advice to further follow-up this case on "Installation & Upgrades" in a day or two!

Pray for the Help to arrive soon by then. :-)

---

### Post by ajgreeny on 2016-08-27
You show us 4 separate boot-info-script output files

Why?

Which one is the one that you did last.  I think it is No 1 but just want to be sure.

---

### Post by mook765 on 2016-08-27
From your Boot-Repair-Summary:
> 
If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
Try the mentioned example...

In this link you can find another way to solve the problem:
[http://askubuntu.com/questions/349526/how-to-set-grub-default-not-windows-boot-manager](http://askubuntu.com/questions/349526/how-to-set-grub-default-not-windows-boot-manager)

Your Boot-Repair-summary looks like a clean install, the problem is HP-specific...

---

### Post by saurabhdua2 on 2016-08-28
I hereby request the Dear members to please post an 'Update' towards the issue resolution.
Iam keenly waiting to receive Inputs from your end.

Hello ajgreeny!

Yes the Number 1 entry pertains to the last attempt to set things right. Its the most recent indeed.

Thanks.

Hello mook765,

I did try out the command listed in the referred article for Windows OS, it said--"Access is Denied"! I made sure to use the command under C:\ only (which I suppose represents Admin).

Please suggest if there exist an another method to run "cmd.exe" as Administrator.

Help will be sincerely appreciated.

Thank you.

---

### Post by mook765 on 2016-08-28
Here is help:
[https://technet.microsoft.com/en-us/library/cc947813(v=ws.10).aspx](https://technet.microsoft.com/en-us/library/cc947813(v=ws.10).aspx)

---

### Post by oldfred on 2016-08-28
HP puts its .efi system files in the ESP - efi system partition. Somewhere you may have instructions on booting HP apps or repairs. Other vendors use another FAT32 partition that is not the ESP, but works like one or is a hidden one to boot system files.

Boot-Repair saw all those system files and created a new 25_custom grub script and added all of them into that file.
Many with HP edit or delete some or all of the entries in 25_custom. I do not know but assume HP from UEFI has a direct way to use those files.

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub 


 [http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705](http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705)

Boot-Repair cannot easily tell difference between an efi boot file that you would want and an efi system file that is not required for booting. And you may or may not want that in grub menu.

---

### Post by saurabhdua2 on 2016-08-31
Hello Members,

Apropos of the Great ORDEAL encountered via issue posted against -- [https://ubuntuforums.org/showthread.php?t=2335211](https://ubuntuforums.org/showthread.php?t=2335211) , I now wish to reclaim the Disk space to the tune to 250 GB lost to Ubuntu!

Please help me recover the same asap.

Thank you.

---

### Post by howefield on 2016-08-31
Threads merged and obfuscated URL replaced.

---

### Post by saurabhdua2 on 2016-08-31
Hello Howefield!

Therefore, please let me know the Credible way to reclaim the Disk space of worth 250 GB "Lost" to the Ordeal of installing Ubuntu alongside Windows 8?

Do I need to use "Recovery Manager" available within Windows OS to install & thus reclaim everything as afresh?

Does there exist a hassle-free way to 'part ways' with Ubuntu without going for a Clean Install?

Inputs will be sincerely appreciated...& are keenly awaited.

Thank you.

---

### Post by howefield on 2016-08-31
I'd use Windows built in disk management tool to delete and return the Ubuntu partition to where it came from. Have only skimmed the thread but it looks like there is no grub to worry about ?

---

### Post by Geoffrey_Arndt on 2016-08-31
Maybe this is just "preaching to the choir" . . . but several PC makers do not make it easy to install "Ubuntu" (or any Linux) alongside Windows especially on certain specific PC models.    It can be done,  . . . by the persistent and technically capable.    But,  for others . . . you can get Linux PC's pre-installed (including Dual-Boot).   Potential buyers need to examine every seller, as prices and service vary quite a lot.    Personally, I'm very happy with my System76 computers running Ubuntu and their 5 or 10 minute set-up time.

So, for those frustrated by the often complex "retrofitting" of Linux on PC's "designed" for Windows, perhaps it's time to support our vendors supply pre-installed Linux systems.

---

### Post by saurabhdua2 on 2016-08-31
Hello Members!

Would like to "Update" that the entire Disk-Space has been reclaimed by using the "Recovery Manager" available for Windows 8.
'Breath of Fresh Air' is what Iam able to experience after Reinstalling my Win 8 OS & getting Rid of Bulky Bloatware Ubuntu!

Branded PCs are there in business since a long time, & the Developers at Ubuntu must have encompassed a few advisories to make the 'alongside' Installation favorable & sustainable!

'Alongside' Installation is perhaps still lingering in the WinXP era & have rather failed to take stock of the Market trend!

Windows OS & Recovery-Partition have become sine qua non since Year 2009 or so, & therefore such a Permutation should have been taken into account for the Post-2009 versions of Ubuntu! Isn't it so?

Why am I suppose to tinker with Boot-Menu at every single instance to regain an access to Ubuntu? You Guys did really FAIL to anticipate the current & the forthcoming PC setup equation!

If there ever be a Portal enumerating BIG BLOATWARE, Ubuntu would certainly catch-up with Top tens!

Done with you..! & feeling relieved! Huh!

---

### Post by Geoffrey_Arndt on 2016-08-31
Such a classy last post Saurabhdua2 . . . . biting the hand that tries to help - - because of a lack of knowledge on your part . . .  and an unwillingness to read and learn.

---

