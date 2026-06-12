---
title: "Is default coffee cup backup meant to be encrypted ?"
date: 2014-04-12
forum: New to Ubuntu
---

### Post by hebdave on 2014-04-12
High I took a back up with dejavu coffee cup i think its called and it seems to encrypt without giving a choice. I don't mind this as long as it restores okay. I think the other options it gives were like 128 and other numbers. I can't seem to access what those numbers were now since backing up to my external drive or what they were referring too. Were they other encryption number types or something. Sorry for any poor English here I hope you no what I mean. 

Thanks !

---

### Post by TheFu on 2014-04-13
duplicity **really** wants backups to be encrypted and requires a CLI option **not** to encrypt for every command. 
Dejavu is a GUI over duplicity. 

If you don't want encrypted backups (and there are times when that isn't necessary or a good idea), then looking at different tools would be smart. I cannot recommend any GUI backup too - don't use them. Sorry.  Mixing a GUI with something that needs to run as root is generally a bad idea, especially when a strong grasp of file/directory permissions/ownership is lacking. Bad things can happen with many GUI tools when run as root.

For non-encrypted, CLI backup tools, [rsnapshot]("http://www.rsnapshot.org/"), [rdiff-backup]("http://www.nongnu.org/rdiff-backup/"), or a [complex rsync script]("http://www.howtoforge.com/backing-up-with-rsync-and-managing-previous-versions-history") can work well. There are many, many, many examples on the internet. Just be certain that whatever you select does versioned backups, not just a mirror.

---

### Post by hebdave on 2014-04-13
High thanks would it be possible to use a GUI from root or would that make little difference. Would you recommend a simple copy and paste of my home folder to my external drive instead. This of course is not encrypted but I can use bleach bit to erase all traces straight after each back up.

Also does anyone else use dejavu cup. Also as far as I could tell there was no option to in the GUI dejavu cup to have anything else other than encrypted. Since setting it there is no option to change anything a second time. It seems to be a one time set it approach perhaps for security ? 

I am pretty clueless so I did not understand it original options which said something like 128 , 256 etc which were as far as I remember different types of numbered encryption you could choose. Again I could be entirely wrong since I can see no way of going back to reset it and have a look at what I first saw. This is why the question is here to see if anyone knows and so i can get a feel for anyone elses 'experience' of its reliability. Is there any one here who has used it via the GUI and has it working fine ? Or should I copy and paste as a beginner with Ubuntu. Please note I now use clonezilla for images so am just talking about ongoing file backups a separate topic.

Thanks for the suggestions above by the way.

---

### Post by TheFu on 2014-04-14
>  Mixing a GUI with something that needs to run as root is generally a bad idea, especially when a strong grasp of file/directory permissions/ownership is lacking. Bad things can happen with many GUI tools when run as root.

Asked and answered.

When I'm lost on something, I look for a youtube video to explain the parts I don't understand. Are there any dejadup/dejavu videos?

---

### Post by hebdave on 2014-04-17
If I don't encrypt backups will a GUI still use 'root' in the same way. Since i wanted to use a GUI I wondered this. Sorry I have been struggling with some other things so have not got back to this post till now. I was looking at simple backup from the Utube videos you suggested. It looks like more what I am used to from my microsoft windows days.

---

