---
title: "Issues on Booting up with Ubuntu 16.04 from Virtualbox."
date: 2019-01-28
forum: New to Ubuntu
---

### Post by Lou Reed on 2019-01-28
I have chosen to re-install Ubuntu 16.04. In a previous thread I had three versions of python3 and one version of python and keeping track of everything was a nightmare. So I decided to reinstall Ubuntu.

It went very smoothly. No surpise there.

However, when I started it from vurtual box, it gave me a warning or error that is shown in the first attached graphic. Something about not enough space for virtual hard drive. 

I had the choice to either ignore it or check it out. I chose to check it out. The dialogue box that resulted when I chose to check it out is shown in the second graphic. 

I installed Ubuntu 16.04 using a iso file that was on my thumb drive. It just seemed an easy conveneient way to place the original iso file. 

Now when I boot up, I get the warning shown in the first graphic and when I check it out, I get the second graphic. What is going on?

This warning does not occur if I leave the original thumb drive in my laptop. It only occurs when I take the thumb drive out. 

I guesss it must be using part of the space on my thumb drive. But it never asked me during the install if I wanted to do that. I do not.

How can I fix this issue. I want to boot up Ubuntu 16.04 from virtualbox with no error or waring when I leave the thumb drive out.

Any help appreciated. Thanks in advance.

Respectfully,

ErnestTBass

---

### Post by jdeca57 on 2019-01-28
Ok your disk is 10 GB and that is enough for a test. Normally, after an install from an iso there is a moment the program asks you to remove the disk and then everything turns around the virtual hard drive. So the first thing I'd think is to go to the second tab (the one with the ! mark) and remove the missing element, probably the thumb drive. The problem is one of Virtualbox, not one of Ubuntu.

---

### Post by Lou Reed on 2019-01-28
Okay, thanks. I will give it a try.

Respectfully,

ErnestTBass

---

### Post by Lou Reed on 2019-01-29
I see your point, but my install of Ubuntu 16.04 is over. I want to use it now. The install sequence,I performed several days ago. So what can I do in booting up Ubuntu 16.04, that will avoid this error and does not require the thumb drive to be in the laptop. I just as soon re-purpose my thumb drive to something else.

I would also prefer not to install Ubuntu 16.04 again.

Respectfully,

ErnestTBass

---

### Post by monkeybrain20122 on 2019-01-29
The easy way is to reinstall with a bigger virtual drive. If you don't want to do it, you can expand your virtual disk and partition like [https://askubuntu.com/questions/101715/resizing-virtual-drive](https://askubuntu.com/questions/101715/resizing-virtual-drive), takes more work though.

---

