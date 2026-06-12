---
title: "Can't boot Ubuntu or Windows XP"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Rustbeard on 2008-06-19
So I think I just royally F-ed up my computer. I installed Ubuntu the other day, first time I used Linux I did a dual partition with windows xp which I was already running. But then I was installing updates later that day and it froze up and after awhile nothing was happening I just held down the power button and shut it down. Now since then I haven't been able to boot up. It would get to the OS loading bar then the bar would just stop in almost the same place every time and nothing would happen. Now I went back to using windows xp but just today it froze and after awhile I did the same thing, hold down the power button and turned it off. Now I tried rebooting it and it said that a systems file was missing, I tried again and now its saying NTLDR is missing. I tried booting Ubuntu again and now it is saying Error 22: no such partition. Now I'm using the Live disk. And when I try to go to either my windows partition hard dive or my 2nd internal hard dive (that just has media files), I get a "Cannot mount volume" error message which says 

"Unable to mount the volume...

Details: $LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by	clicking on the 'Safety Remove Hardware' icon in the Windows	   taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can 'force' option for    your own responsibility. For example type on the command line:     mount -t ntfs-3g/dev/sdal/media/New Volume -o force     Or add the option to the relevant row in the /etc/fstab file: dev/sdal/media/New Volume ntfs-3g force 0 0"

I am afraid to do anything else cause I'll probably just mess things up even worse.

Any help would be greatly appreciated, to get at least one OS working and access to my hard drives. I am not particularly computer/tech savvy.

---

### Post by mikeyphi on 2008-06-19
Unfortunately, often when Windows is powered off rather than shut down, this problem occurs. You need to get back into Windows and do a normal shut down. That should allow full access with the LiveCd and allow you to rescue your Ubuntu system.

---

