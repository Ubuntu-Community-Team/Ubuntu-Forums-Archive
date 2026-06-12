---
title: "installing updates question / problem"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by graphiteg4 on 2008-06-13
i just finally made the decision to install Ubuntu fully on a machine a ditch the live cds. so i am a new proud owner of linux machine. my problem is when i went to install updates i went to update manger and there is 162 updates. are these updates all security updates and fixes or are these things that are nice to have but not important to running the os. any help would be helpful thanks

---

### Post by gr4nf on 2008-06-13
It's usually a mix of both. Probably a good idea to keep your system up to date.

---

### Post by cdtech on 2008-06-13
Those are all updates to the default programs installed on your system. They should be updated to keep your system current.

Hope this helps.....

---

### Post by drs305 on 2008-06-13
It would probably be more trouble than it's worth to try to sort them out. I would just let the update run and get it over with. ;-) 

On a serious note, one of the updates will probably be the kernel. This will expand your grub boot menu to include this new kernel. You control the grub menu most easily through Startup-Manager. System, Admin, StartUp-Manager. You can decide how many kernels you want to see, how long the menu is displayed, and perhaps most importantly, whether you want it to use the new kernel by default, and more. To install it:
```
sudo aptitiude install startupmanager
```


[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by avtolle on 2008-06-13
And, as there are three kernel updates (at least), I'll give you another thought to ponder: if you have a smallish boot partition set up on the HDD, you may run out of space there, preventing the new(er) kernels from downloading and installing. Fix (quick and dirty): delete older ones (obviously not the one currently used); better fix; enlarge boot partition. Again, this is only a problem with a separate /boot partition, and if you don't have one, will not be a problem for you. Download them all, by the way.

---

### Post by Hospadar on 2008-06-13
there's only so many because it's a fresh install.  Generally updates show up in groups of around 5-20 and take no more than a couple minutes on a broadband connection for me (and I have all sorts of silly extra repositories enabled, so if you just stick to security updates it will be even shorter)

---

### Post by JackieMc on 2009-09-04
I'm new to all this so forgive me if I've posted this wrong.  I'm having problems installing the updates.  I get the following:

  	 	 	 	 	 	  This was from the Error Message;
E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline
 

 This is what showed in the detail box.

(Reading database...dpkg: error processing / var/ cache / apt / archives/ linux-image-2.6.24-22-lpia_2.6.24-2245netbook9_lpia.deb (--unpack):
  files list file for package 'libxcb-shape0' is missing final new line
 Errors were encountered while processing:
  /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24.22,45netbook9_lpiadeb
 Processing was halted because there were too many errors.
 E: Sub-process /usr/bin/dpkg returned an error code (1)
 A package failed to install.  Trying to recover:
 
I've read this thread but I don't understand what I'm reading.

Thank you for any help you can give me.

---

### Post by drs305 on 2009-09-04
> **JackieMc said:**
> I'm new to all this so forgive me if I've posted this wrong.  


Jackie,

Welcome to Ubuntu and the Ubuntu forums.

Actually, yes, you did post to the wrong place. Generally you are expected to begin a new thread for a different problem than the original post. You do this with the "New Thread" link at the top right of the forum page.  But, being you are new, you are forgiven. ;-)

> 
I'm having problems installing the updates.  I get the following:
This was from the Error Message;
E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline
 

Try opening a terminal and running this command (Applications, Accessories, Terminal). When you run the command, you will be asked for your password. Type it even though you won't see it being entered, then press ENTER. There is a good chance there are other problems as well, but this should clear the original error message.

```

echo -en '\n' | sudo tee -a /var/lib/dpkg/info/libxcb-shape0

```
This will add a "newline" to the file referred to in the error message. It may solve the issue. If not, please start a new thread, repeating your post and what you have already tried.

---

### Post by LewRockwell on 2009-09-04
don't worry, the moderators will be by shortly to break this off and create a wonderful shiny new thread for us to post in!

.

---

### Post by JackieMc on 2009-09-05
Thank you for your help. I'll try it!

---

### Post by PorkyPie on 2009-09-05
Soz, wrong thread!

---

