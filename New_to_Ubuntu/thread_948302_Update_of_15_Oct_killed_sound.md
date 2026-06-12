---
title: "Update of 15 Oct killed sound"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by NE Key on 2008-10-15
Just done the update of today and now sound is dead.

As the new kernel bits were being automatically built there was a comment about alsa failure which went over my head.

Any clues as to where I start ?

(Went into Grub and selected 2.6.24-19-generic to boot and sound worked. The update is 2.6.24-21-generic and sound [alsa, I believe] is not working.)

---

### Post by NE Key on 2008-10-15
Partial solution

removed the new kernel;

 "sudo apt-get remove linux-restricted-modules-2.6.24-21-generic"

then "gksu nautilus" to edit boot/grub/menu.lst and remove the -21 option.


Edited to add - and everything now works perfectly. (Just as did before the "up"-grade).


Edited to add link to other thread about this [http://ubuntuforums.org/showthread.php?t=947999](http://ubuntuforums.org/showthread.php?t=947999)

---

### Post by kansasnoob on 2008-10-15
I just had the same problem so I came here looking.

For the moment I just changed Startup-Manager to boot the old kernel rather than removing the new kernel.

I'll fool with it more a bit later, just no time at present.

One thing I might mention is this is a fairly "virgin" installation on a test hard drive - that is I've not done the pulse audio fixes and such, but all has been working well with Flash 10 with no tweaks to sound other than installing Gnome Alsamixer to improve sound.

---

### Post by PCZahra on 2008-10-15
ditto.

---

### Post by Turboflame on 2008-10-15
Looks like there's another thread here about it too.

[http://ubuntuforums.org/showthread.php?t=947999]("http://ubuntuforums.org/showthread.php?t=947999")

I haven't had any problems with the new kernel personally.

---

### Post by kpkeerthi on 2008-10-15
> **NE Key said:**
> Partial solution

removed the new kernel;

 "sudo apt-get remove linux-restricted-modules-2.6.24-21-generic"

then "gksu nautilus" to edit boot/grub/menu.lst and remove the -21 option.


Edited to add - and everything now works perfectly. (Just as did before the "up"-grade).


Edited to add link to other thread about this [http://ubuntuforums.org/showthread.php?t=947999](http://ubuntuforums.org/showthread.php?t=947999)

If you follow [this]("http://ubuntuforums.org/showpost.php?p=5112848&postcount=3"), you do not have to manually update your GRUB config file. This is the suggested way as it will also remove other packages (like modules) that came with the kernel version.

---

### Post by kansasnoob on 2008-10-15
Well, mine was fixed after doing this:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

I'm guessing that somehow my sound card was not properly detected with the kernel upgrade and since that tutorial purges '/etc/asound.conf' and then completely replaces it I'm rockin' again:)

---

### Post by kansasnoob on 2008-10-15
Check out bobnutfield's posts here:

[http://ubuntuforums.org/showthread.php?t=948553](http://ubuntuforums.org/showthread.php?t=948553)

Looks like he has a handle on it!

---

### Post by christina_svats on 2008-10-15
I always did the following when I had trouble with sound (and it was more than a few times):
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils
sudo apt-get install gdm ubuntu-desktop

```

---

### Post by PCZahra on 2008-10-15
I got mine. TY Dell for choosing Intel, but at least they provided the instructions.

---

### Post by NE Key on 2008-10-17
> **kpkeerthi said:**
> If you follow [this]("http://ubuntuforums.org/showpost.php?p=5112848&postcount=3"), you do not have to manually update your GRUB config file. This is the suggested way as it will also remove other packages (like modules) that came with the kernel version.

And thus you demonstrate the joy of this forum. 

Whatever solution one might find, some one else has a better one !

---

### Post by Dermot Doyle on 2008-10-18
Just downloaded updates and have the same problem with sound on Ubunto 8.04. I followed the advice from NE Key, but when I typed in 'sudo gksu nautilus' I got this:

Initializing nautilus-share extension

seahorse nautilus module initialized



** (nautilus:10141): WARNING **: Unable to add monitor: Operation not supported

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory

Please ask your system administrator to enable user sharing.


I'm now way past my level of understanding computers. Can anyone help?
Thanks

---

### Post by Dermot Doyle on 2008-10-18
A quick update in case anyone reads this thread. When I type 'aplay -l' I get 'aplay: device list:205: no souncards found...'

---

### Post by stinger30au on 2008-10-18
i have had this happen, but my fix has been as simple as double clikcing the speaker icon on the desktop and move the volume levels back up as after an update all the volume controlls were set to mute for some unknown reason

---

### Post by Andy Moon on 2008-10-18
Hello,

Im using an Inspiron 1525 laptop.
Audio device shown by shell command:
lspci -v | grep audio -i
00:1b.0 _Audio device: Intel Corporation 82801H (ICH8 Family)_ HD Audio Controller (rev 02)


Reinstalling the audio driver fixed the problem in my case. [The procedure is explained on dell unbuntu wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade"), as I wrote in this post :

> **Andy Moon said:**
> 
Here's a summary of how it worked in my case, if that can help others :

_Computer : _
Inspirion 1525
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

_OS :_
Ubuntu Hardy 8.04
Kernel Linux 2.6.24-19-generic UPGRADED TO 2.6.24-21-generic => that's when I encountered the sound problem
[U]
The problem[/U]

After I upgraded to kernel 2.4.24-21, I had no sound anymore. Some symptoms :
there was a red warning flag on my sound icon tray
no driver found by ubuntu, as revealed by the shell command 
"aplay -l" (result was something like :  device_list:221: no soundcard found...)


_What solved my problem_

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)

Quotes from that page :
```
Description: No sound after upgrade from Ubuntu 7.10 or upgrade to kernel 2.4.24-17
Systems Affected: Inspiron E1505n, 1420n and 1525n.
```
=>this procedure also fixes the problem after upgrade to kernel 2.4.24.-21


Follow the instructions given in the second part, titled _"If already running Ubuntu 8.04 and upgrading to kernel 2.6.24-17-generic"_. 

Shall fix it for you too ;)

Cheers,

Andy

---

### Post by Dermot Doyle on 2008-10-18
Thanks for that, I'll give it a go. I have followed another thread and temporarily set the previous kernel as a default until it's sorted.

---

### Post by Dermot Doyle on 2008-10-18
Unfortunately that didn't work for me. I may well have buggered something up trying the other fixes suggested on other threads. Oh well, I'll keep looking and see what comes up.

---

