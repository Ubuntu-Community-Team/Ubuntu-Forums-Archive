---
title: "[SOLVED] Sound Card Tradegy!"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by PhaeZee5 on 2008-07-28
ever since an automatic update (or the install of virtualbox), my sound card has no longer been recognized! It has always functioned beautifully, and i am fairly sure it is a software problem. Are there any terminal commands to see if ubuntu even knows it's there? Any help would be greatly appreciated!

---

### Post by pauper on 2008-07-29
Try this, change "grep snd_hda_intel" for your match:

```
:~$ **sudo lshw -C multimedia**
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 [highlight]module=snd_hda_intel[/highlight]
:~$ **lsmod | grep snd_hda_intel**
snd_hda_intel         293152  1 
snd_pcm                80644  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
snd_hwdep              10628  1 snd_hda_intel
snd                    56708  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
```

Now, try the same commands with Live CD, assuming that your audio works in
that environment. See what kind of module it loads. Go back to your hard drive
installation and load that module (print messages in the event of error):

```
sudo modprobe -v some_module
```

If it works, make it consistent. First, make sure this module is not
blacklisted somewhere:

```
find -L /etc/modprobe.d -type f | xargs grep some_module 2> /dev/null
```

If it appears so--comment it out with # symbol at the beginning of that line.
You will see the path and name of the file if "find" matches anything. Make
that module load at every startup:

```
echo "some_module" | sudo tee -a /etc/modules
```

---

### Post by PhaeZee5 on 2008-07-29
It worked!:)
Thank you so much!
I'll try to make it permanent now.

And in non-beginner terms, what  exactly did that do?

---

### Post by PhaeZee5 on 2008-07-29
I got it working permanently now...time to watch *An Inconvenient Truth*!

---

### Post by pauper on 2008-07-29
> And in non-beginner terms, what exactly did that do?

Well, you didn't provide any output of "lsmod | grep some_module" before and
after the issue, so I can only speculate that for some reason the module
in question wasn't inserted and by running "sudo modprobe -v some_module" you
changed that. Was it blacklisted?

By the way, if you are happy with the results mark this thread as solved.

---

