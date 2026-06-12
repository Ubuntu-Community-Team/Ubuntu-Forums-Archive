---
title: "Pcmanfm and usb flash drive"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by monkeybrain2012 on 2013-03-27
I have a strange problem with usb drives on lubuntu12.04. When I plug a usb drive into a pc with lubuntu installed and look at the content, then remove it and  modify its content in another machine then plug it back into the lubuntu machine, the change does not seem to be picked up by the gui. 

For example, if I plugin the drive, open it and then remove the drive, and plug it into a different machine and remove some files, then plug it in again into the first machine (with Lubuntu) and open it with pcmanfm the files' icons are still showing even though checking in the terminal confirms that they have indeed been deleted.

Or, I plug a usb into a lubuntu machine, open it and inspect its content, then remove it and plug it into a different machine to add some files. When plugging back into the lubuntu machine and open the drive with PCmanfm these files don't show up, yet checking with the terminal confirms that these files are present.

So it seems that when the usb drive is first plugged into lubuntu, it somehow remembers what is in it and that if the drive is modified later in a different machine, the changes don't get picked up by pcmanfm when the same drive is plugged into the original lubuntu machine a second time.


Sorry if it sounds a bit confusing, but it seems to be a very confusing problem. Does anyone experience the same problem?

Thanks for any suggestion or advice.

---

### Post by sudodus on 2013-03-27
Do you unmount the usb flash drive (click the eject symbol in pcmanfm) or use ```
sudo umount
```? Then, when remounting, linux should read the drive and update its content.

It is important to unmount drives in general, and slow USB drives in particular, to make sure all write operations have finished before disconnecting it. Otherwise you a likely to corrupt your file system. You can check that everything is written from the buffers using
```
sync
``` in a terminal window.

---

### Post by monkeybrain2012 on 2013-03-27
Yes I did unmount. As I said if I use the terminal to list the content it does show the changes and I can manipulate the content (say copying and moving them ) with the command line so I don't think the problem has to do with write operation not having completed. It seems that somehow pcmanfm remembers the previous state of the drive and fails to update it accordingly.

Edited: I should emphasize that the change was done on a different machine (say one with Ubuntu or another Lubuntu) and that this change is not picked up in the lubuntu machine if the drive has been in the lubuntu machine before.

---

### Post by sudodus on 2013-03-27
I see. What happens if you tell pcmanfm to ***reread*** the directory (either via the menu or with F5)?

*Edit*: Maybe pcmanfm uses some kind of caching data, but this should be updated by 'a reread'

---

### Post by monkeybrain2012 on 2013-03-27
> **sudodus said:**
> I see. What happens if you tell pcmanfm to ***reread*** the directory (either via the menu or with F5)?

I tried refreshing if that is what you mean.

---

### Post by sudodus on 2013-03-27
Yes, I translated from my language (anyway F5 should be doing it). Still no go?

---

### Post by monkeybrain2012 on 2013-03-27
No.

---

### Post by sudodus on 2013-03-27
Maybe it's a bug. What happens if you try another file browser, Nautilus from Ubuntu or Thunar from Xubuntu? They are easy to install from the repos
```
 sudo apt-get install nautilus
```
```
 sudo apt-get install thunar
```

Will the problem persist or is it only affecting pcmanfm?

---

### Post by monkeybrain2012 on 2013-03-27
> **sudodus said:**
> Maybe it's a bug. What happens if you try another file browser, Nautilus from Ubuntu or Thunar from Xubuntu? They are easy to install from the repos
```
 sudo apt-get install nautilus
```
```
 sudo apt-get install thunar
```

Will the problem persist or is it only affecting pcmanfm?

Thanks for the advice, I will try to do some more experiments when I go home. I think, however, mixing and matching file managers maybe a bad idea because some functions may stop working as the system is confused about which file browser should take over and when. For example, installing  nautilus along pcfman may result in folders on Desktop not openable with double click and some media failing to mount because apparently pcfman cedes control to Nautilus in some functions but Nautilus may not be aware of that, or some such reasons.

---

### Post by sudodus on 2013-03-27
> **monkeybrain2012 said:**
> Thanks for the advice, I will try to do some more experiments when I go home. I think, however, mixing and matching file managers maybe a bad idea because some functions may stop working as the system is confused about which file browser should take over and when. For example, installing  nautilus along pcfman may result in folders on Desktop not openable with double click and some media failing to mount because apparently pcfman cedes control to Nautilus in some functions but Nautilus may not be aware of that, or some such reasons.

I have all three running in the OS I am using right now, and there is no problem for me. They are just three independent programs. You might prefer to open Nautilus without control of the desktop with 
```
alias nautilus='nautilus --no-desktop'
```

*Edit*: Of course, after some testing you can select the one you like the best and remove the other two file browsers.

---

### Post by rsgangr on 2013-04-01
I am also considering various file managers and decided to perform a simple test as follows:     Computer A   1. Insert USB drive   2. Copy a file to USB drive   3. Check that it is accessible from PCManFM - OK   4. Check that it is accessible from Thunar - OK   5. Unmount USB drive - this shuts down PCManFM. The USB drive is no longer visible in the other file manager.      Computer B   1. Insert USB drive   2. Check that it is accessible from PCManFM - OK   3. Check that it is accessible from Thunar - OK   4. Delete the file and empty Trash.   5. Unmount USB drive - this shuts down PCManFM. The USB drive is no longer visible in the other file manager.      Return to Computer A   1. Insert USB drive   2. In PCManFM the deleted file is still "visible" but not in Thunar.   3. In PCManFM pressing f5 updates the display and removes this spurious entry.      Notes:   (a) I have referred to computers "A" and "B" above. It makes no difference which of my two machines I call "A" or "B"; the same pattern is evident.    (b) I also said that the unmounting of a USB drive from PCManFM triggers the shutdown of PCManFM. This seems to be intermittent but happens more often than not.    (c) Both of my machines were running Xubuntu 12.04 and both have PCManFM 0.9.10 and Thunar 1.2.3 as file managers.      Addendum:   Both computers have multi-boot configurations and, as an afterthought, I rebooted one machine to Linux Mint 13. This only has one file manager (Thunar 1.4.0) and the result was the same as described above.      Conclusion:   (a) It seems, then, that PCManFM is saving some sort of status information as alluded to by "sudodus" above. This is not automatically updated when the same USB drive is subsequently mounted. However, pressing f5 to re-read the directory does update the file list.    (b) The intermittent shutting down of PCManFM when an external drive is unmounted is disconcerting to say the least. I am not very happy with PCManFM and shall certainly look at Nautilus as an alternative file manager.

---

### Post by gordintoronto on 2013-04-01
Do you plug into the same USB port? If you plug into a different port, does it make any difference?

---

### Post by monkeybrain2012 on 2013-04-01
> **rsgangr said:**
> I am also considering various file managers and decided to perform a simple test as follows:     Computer A   1. Insert USB drive   2. Copy a file to USB drive   3. Check that it is accessible from PCManFM - OK   4. Check that it is accessible from Thunar - OK   5. Unmount USB drive - this shuts down PCManFM. The USB drive is no longer visible in the other file manager.      Computer B   1. Insert USB drive   2. Check that it is accessible from PCManFM - OK   3. Check that it is accessible from Thunar - OK   4. Delete the file and empty Trash.   5. Unmount USB drive - this shuts down PCManFM. The USB drive is no longer visible in the other file manager.      Return to Computer A   1. Insert USB drive   2. In PCManFM the deleted file is still "visible" but not in Thunar.   3. In PCManFM pressing f5 updates the display and removes this spurious entry.      Notes:   (a) I have referred to computers "A" and "B" above. It makes no difference which of my two machines I call "A" or "B"; the same pattern is evident.    (b) I also said that the unmounting of a USB drive from PCManFM triggers the shutdown of PCManFM. This seems to be intermittent but happens more often than not.    (c) Both of my machines were running Xubuntu 12.04 and both have PCManFM 0.9.10 and Thunar 1.2.3 as file managers.      Addendum:   Both computers have multi-boot configurations and, as an afterthought, I rebooted one machine to Linux Mint 13. This only has one file manager (Thunar 1.4.0) and the result was the same as described above.      Conclusion:   (a) It seems, then, that PCManFM is saving some sort of status information as alluded to by "sudodus" above. This is not automatically updated when the same USB drive is subsequently mounted. However, pressing f5 to re-read the directory does update the file list.    (b) The intermittent shutting down of PCManFM when an external drive is unmounted is disconcerting to say the least. I am not very happy with PCManFM and shall certainly look at Nautilus as an alternative file manager.

I have done similar experiments and get similar results except that PCMANFM doesn't crash on removing usb drive as you reported. ATM I am not able to exactly replicate the tests because machine A was actually identical with machine B and both have Lubuntu 12.04 installed, I was actually setting up machine B for someone else he has already taken it. I repeated the same experiment with another 'machine B' whiich is my main laptop with Ubuntu 12.04. Again Nautilus is able to update changes while PCManfm cannot.

---

### Post by monkeybrain2012 on 2013-04-01
> **gordintoronto said:**
> Do you plug into the same USB port? If you plug into a different port, does it make any difference?

Tried all ports and made no difference.

---

### Post by rsgangr on 2013-04-02
_gordintoronto:_ Regardless of which USB port I use, I see the same pattern.  _monkeybrain2012:_ I have just repeated the test after booting one machine into Windows - the results are the same.  After installing and using Nautilus 3.4.2 for a few hours I think I shall uninstall PCManFM from both computers and use Nautilus and/or Thunar.

---

