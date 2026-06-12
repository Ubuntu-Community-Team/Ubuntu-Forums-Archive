---
title: "resetting grub timout not working"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by piattj on 2014-05-13
[SIZE=2][FONT=arial]I'm trying to reset the timeout from 10 to 0 (or maybe to 1), to bypass the boot screen. I've tried making the following change in **/etc/default/grub**
```
GRUB_TIMEOUT=10 > GRUB_TIMEOUT=0
```

I then ran update-grub, and tried doing the same as root, to no effect.

I opened grub.cfg in **/boot/grub/** (which I know you're not supposed to edit), and saw these lines (in one of the first sections, as you can see)
```
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###
```

 These lines don't seem to get changed with update-grub, so I'm thinking these might be the ones determining the timeout, which indeed seems stuck on 10 seconds. I went through a couple tutorials on how to change the timeout and other boot options, but they all mention the file  /etc/default/grub as the place to do this, which will then get propagated up to grub.cfg, and that's not happening. Any ideas? I'm on Zorin OS 8 Lite. [/FONT][/SIZE]

---

### Post by slickymaster on 2014-05-13
Hi piattj, welcome to the forums.

I've edit your post so it matches what's expected and for making it easy to understand and read. Please refer to [this thread]("http://ubuntuforums.org/showthread.php?t=2158945") regarding the forum Posting Guidelines.

---

### Post by piattj on 2014-05-13
Thanks for the correction. I neglected to research how to post correctly, I was so busy researching the problem itself.

---

### Post by piattj on 2014-05-22
Kindly nudging for a bump...

---

### Post by Rex Bouwense on 2014-05-22
I missed this the first time around.  I always use Grub Customizer to change things.  I have mine set at 2 seconds to boot into the default OS so I have a little time to decide to boot to another.  My /etc/default/grub  looks like this

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="2"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Does that help?

---

### Post by piattj on 2014-05-25
Yes, it works now. I'm sure it's what I had been doing before, but now grub.cfg seems to gets changed when I update it after changing default/grub like you said. I don't like not knowing why, but at least it works! Thanks.

---

### Post by Rex Bouwense on 2014-05-25
Glad to be of help.

---

