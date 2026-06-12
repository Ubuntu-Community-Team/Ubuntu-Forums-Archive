---
title: "Computer won't fully shut down because of clamscan"
date: 2022-07-02
forum: New to Ubuntu
---

### Post by norahlo on 2022-07-02
Installed Ubuntu 20.04.4 LTS (focal fossa) a few days ago over Windows 8 on old XPS 2720 via bootable USB. Ubuntu first-timer; beginner; not very computer savvy. 

I shut down the computer onscreen in Ubuntu, waited the 60 seconds. No windows were open. The screen faded to black and stuff but it didn't shut down completely. There's a black screen with white plain text. Here's what it says:
```
[183394.193221] systemd-shutdown[1]: Waiting for process: clamscan, clamscan, cl
amscan, clamscan, clamscan, clamscan
[183394.196587] snd_hda_codec_hdmi hdaudioC0D0: HDMI: pin NID 0x6 not registered
[183394.201665] snd_hda_codec_hdmi hdaudioC0D0: HDMI: pin NID 0x6 not registered
[183484.200894] systemd-shutdown[1]: Waiting for process: clamscan, clamscan, clamscan, clamscan, clamscan, clamscan
[183564.461107] systemd-shutdown[1]: Could not detach DM /dev/dm-0: Device or resource busy
[183564.797100] systemd-shutdown[1]: Failed to finalize  DM devices, ignoring
```

This is the second time it's happened. Last time I just held the power button a couple seconds to force it to turn off. I sort of felt like a forced shutdown while clamscan is (apparently) still running might be something you're not supposed to do (Is it?), but installing Ubuntu hasn't been a straightforward piece of cake for me, it was late, and I didn't have the patience to spend another hour or more researching another issue. But I don't want to unwittingly mess things up so this time I came here first. The screen has been like that all night—haven't touched it. Help me figure out what the issue is? Please and thanks. Let me know of any other relevant details that I didn't mention.

---

### Post by ajgreeny on 2022-07-02
As you were told in your first forum post at [https://ubuntuforums.org/showthread.php?t=2476651](https://ubuntuforums.org/showthread.php?t=2476651), also about clamav, the best way to overcome your problem is to uninstall clamav which for the vast majority of Ubuntu desktop users is totally pointless.

Forget about all you learned regarding the importance of av systems; that was for Windows (I assume) but you are now using Linux for which there are no viruses in the wild, and clamav will never find the other malware that can affect Linux.

Read again the linked post shown in that first thread, [https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795](https://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795) and enjoy your new OS without the fears that you currently have.
I have been using Ubuntu (or another of the Ubuntu family of OSs) exclusively now for 17 years without running any av and have never had any viruses or malware in that time.

---

### Post by Autodave on 2022-07-02
Currently 11 machines running.....2 open to the public.  Not a virus after 12 years.  Get rid of Clam.....not needed.

---

