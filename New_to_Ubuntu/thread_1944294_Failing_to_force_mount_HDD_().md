---
title: "Failing to force mount HDD (?)"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by wild8900 on 2012-03-21
Hello, my windows laptop had a terrible crash and no longer boots into safe mode or regular mode. The recovery partition also does not work. I do not have any CDs to burn a recovery disk. My only option is my Ubuntu Live USB flash disk. It loads up fine, I am in the environment, I can access the disk utility and the terminal just fine.
*However*, I cannot access the harddrive. I would like to recover the files and abandon ship.
Fails to mount through the standard interface.

I did some research and was able to identify my hard drive as /dev/sd3
I learned these commands:
> 
sudo mkdir /media/windows
sudo mount ntfs /dev/sda3 /media/windows -o forceIn the terminal,** I received no errors** but I also saw no results. What am I doing wrong? I just want to mount sd3 to media/windows to recover important files.

EDIT:
When I attempted
> sudo ntfs-3g /dev/sda3 /media/windows -o forceI got this error:
> NTFS IS EITHER INCONSISTENT OR THERE IS A HARDWARE FAULT
OR IT IS A SOFTRAID/FAKERAID HARDWARE
IN THE FIRST CASE
RUN CHKDK /F ON WINDOWS
THEN REBOOT INTO WINDOWS TWICE
THE USAGE OF THE /F IS VERY IMPRTANT
IF THE DEVICE IS A SOFTRAID/FAKERAID THEN FIRST
ACTIVATE IE AND MOUNT IT UNDER THE /DEV/MAPPER
DIRECORY

---

### Post by chipbuster on 2012-03-21
> NTFS IS EITHER INCONSISTENT OR THERE IS A HARDWARE FAULT

Methinks that's your problem, although I'm not super-great at this stuff.

---

### Post by wild8900 on 2012-03-21
Yeah I read into fixing corrupt volumes and discovered this:
[http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/](http://www.makeuseof.com/tag/fix-corrupted-windows-ntfs-filesystem-ubuntu/)
I'll have to try it later, but even if the volume is corrupt and requires repair, wouldn't trying to mount it output an error message?
Thanks for the reply, buddy.

---

### Post by wild8900 on 2012-03-21
Anyone have any ideas?

---

### Post by chipbuster on 2012-03-21
Any luck with the fix on that link? Also, can you hear the HDD spinning up?

I'm starting to wonder if you had a hardware failure if you can't get it to respond at all.

---

### Post by wild8900 on 2012-03-21
I did what the link suggested to the very end.
It did not say there were any errors to fix and when I tried to mount it again I got no error. I just went to a new line ":~$"

---

