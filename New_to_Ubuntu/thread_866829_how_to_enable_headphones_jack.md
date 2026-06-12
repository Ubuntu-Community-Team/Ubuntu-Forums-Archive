---
title: "how to enable headphones jack"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Kosimo on 2008-07-22
Hello guys.
I've just bough a new computer (Sony Vaio VGN-FZ335) And everything is working so fine, except for my headphones.  They don't work at all when being inserted, and main speakers keep working...

What can I do to solve this problem?

I'm using Hardy.

Thank you guys

---

### Post by Sealbhach on 2008-07-22
I had that problem with my Vaio too. The solution is in this thread here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

The important part is:

```
sudo gedit /ect/modprobe.d/alsa-base
```

Add this text to the bottom of that file:

```
options snd-hda-intel model=vaio 
```

When you restart you should have sound in the headphone/speaker jack.


.

---

### Post by Kosimo on 2008-07-22
> **Sealbhach said:**
> I had that problem with my Vaio too. The solution is in this thread here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

The important part is:

```
sudo gedit /ect/modprobe.d/alsa-base
```

Add this text to the bottom of that file:

```
options snd-hda-intel model=vaio 
```

When you restart you should have sound in the headphone/speaker jack.


.

Hi, thanks for the answer!
But alsa-base doesn't exist in my system. So I can't edit it.

I've been reading the (superpost) but I couldn't find out how to solve this specific problem.  
Thank you!

---

### Post by Sealbhach on 2008-07-22
> **Kosimo said:**
> Hi, thanks for the answer!
But alsa-base doesn't exist in my system. So I can't edit it.

Strange. 

It should be there - how do you know it's not?

If you need to install it, do this:

```
sudo apt-get install linux-sound-base alsa-base alsa-utils alsamixer
```

The try that module Vaio thing in the previous post.


.

---

### Post by sbusiso on 2008-07-22
ALSA is the Advanced Linux Sound Architecture project, and it supports a lot of different sound cards. You can check out the main page at [http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page") and install it to your machine.

One thing to check is to see what sound cards your computer is already supporting. Sometimes there are issues having on-board sound enabled with a sound card. Enter:

asoundconf list

in a terminal, and it should give a list of the available sound cards. There are other tutorials about setting up your default card, but start with trying the volumes on alsa. After you install alsa-base you can edit the volumes with the 'alsamixer' command in a terminal or install the alsamixergui.

Good luck!

---

