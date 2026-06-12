---
title: "Where's the  File Manager Windows equivalent"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by Berry Greene on 2014-04-08
I started using Ubuntu in a dual boot system with Windows when the issue was 8.10 - - some time ago. It was very good and I got along well until upgrading to include "Studio" It crashed soon after that. I had lost the grub which was re-located but after a while loading would not complete and I reverted to Windows only about 2yrs ago. 
XP cover by Microsoft finishes today and so I thought I'd reinstall UBUNTU for my on-line work. It seems to be pretty virus immune - anyone? I've been getting on very well with my new dual boot system, operating on the Windows database of word type files. Importing photos worked Ok but how do I transfer them to my existing photo Folders? I can't seem to find the equivalent of Windows File Manager.

So my primary question is: Where is, and how do you open the File Manager. Please.....! Full instructions for a bit thick guy. Thanks

---

### Post by Paulgirardin on 2014-04-08
It's the second icon from the top of the launcher,right click to open or left click to get a quicklist of the bookmarked folders, or hit the windows key and type files.

---

### Post by Mark Phelps on 2014-04-08
The File Manager in Ubuntu is known as Nautilus -- but it looks and behaves somewhat different than Windows Explorer.

If you want something closer to the Windows version, then download and install Gnome-Commander from the Software Center.

---

### Post by Berry Greene on 2014-04-09
Thanks Mark & Paul. That's very helpful. Nautilus & Rt Click yes! 
Unfortunately, this morning (UK) I have not got the icon for Thunderbird displayed at all! (V12.04.03). I really do hope this doesn't mean I have lost the Address Book which was such a devil to Import. Where on earth & why has it disappeared to? Other icons appear to work normally. Can it be recovered?
I was going to ask you if it was right to be guided by the installer and choose ext4 files format for my UBUNTU Partition and swap disk because I cannot see those Partitions from Windows now. In my original version (V8.04?) I could see UBUNTU from Windows. Should it be necessary to re-instal - (is it?) - should I choose NTFS format like the rest of my disks? 
Grateful for any help whatsoever; as my head aches!
Rgds, BG

---

### Post by coffeecat on 2014-04-09
From your description, you appear to be using Ubuntu with the Unity desktop, yet your profile says Ubuntu Studio. I'll assume that Studio in your profile refers to when you were using an earlier installation. It would be helpful if you would confirm which version and release of Ubuntu you are using so that people can give you appropriate advice. You might want to amend your profile too.

Assuming you are using Ubuntu with Unity and that you have either 12.04 or 13.10, the two currently supported releases, to get Thunderbird open the dash, either by clicking on the topmost icon in the launcher or by tapping the Windows key. Now start typing thunderbird. Thunderbird will appear as an option as soon as you have typed the first few letters. Click on the dash icon for Thunderbird and it will open. An icon for Thunderbird will also appear in the launcher, and you can make this persistent by right-clicking on it and then left-clicking on &#8220;lock to launcher&#8221;.

If you are using Ubuntu 13.10 (I can't remember whether this is so in 12.04), you will also see an envelope icon in the top bar near the right. Clicking on this reveals a number of options including opening Thunderbird. 

Your other questions:

Windows cannot read Linux filesystems such as ext3 and ext4 without a 3rd party driver. If your older Ubuntu 8.* installation could be read from Windows than you must have installed a driver for this. You cannot install Ubuntu to an NTFS partition (except with wubi which is a special case and now unspported anyway). Personally, I would not recommend an ext3/4 driver for Windows, but others may have a different view. One solution to being able to share personal data between Windows and Ubuntu is to create a data partition formatted NTFS. Ubuntu can read and write to NTFS but cannot run from it.

---

### Post by Berry Greene on 2014-04-09
Thank you Coffecat - much appreciated. You're right in every dimension! It seems now that Thunderbird had crashed as flagged "not responding - close & re-open." Working fine again now. Went into panic mode I confess - quite a lot of work setting up Address book imported from Win OExp, Lost without access to it. 
I will get this - I'm just rusty because as you rightly said I have a new "DISTRO" ??? and have amended my profile as you suggested I should.
Apart from that all is well and yes I already do have a suitable partition to used for UBUNTU data files that is NTFS so I'll use that. 
I want to thank you very sincerely for your very thorough clear response. I appreciate that very much indeed. ATB
Berry

---

