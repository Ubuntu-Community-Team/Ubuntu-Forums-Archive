---
title: "Trouble loading ChrUbuntu"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by temujin1 on 2013-06-20
Hello everyone,

I've installed ChrUbuntu successfully (I think) on my Samsung ARM Chromebook, following [the directions on Jay Lee's site]("http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html"). However, when I run it, it just shows an underscore at the top of the screen, blinking indefinitely. What did I do wrong...?

Also, how does one run ChrUbuntu from the Chromebook dev-mode screen? I had to set ChrUbuntu as the default OS in order to even see it, but I'd prefer to have Chrome OS be the default.

Thanks in advance ^^

---

### Post by temujin1 on 2013-06-21
I think I've figured out the problem. I pressed Ctrl+D again and it brought me to the ChrUbuntu terminal, and I was able to enter commands and such. But I'm still lacking a desktop environment. I had assumed that it would come automatically with Unity... How do I install it?

---

### Post by oldrocker99 on 2013-06-21
Try entering startx, and see what happens.

---

### Post by temujin1 on 2013-06-22
I typed "startx" (next to the $ sign) and the result was "Fatal server error: AddScreen/ScreenInit failed for driver 0".

---

### Post by temujin1 on 2013-06-23
Can someone please help?

---

### Post by temujin1 on 2013-06-23
I tried several steps to get a GUI in ChrUbuntu:
[LIST]
[*]Ran "curl -L -O [http://goo.gl/s9ryd;](http://goo.gl/s9ryd;) sudo bash s9ryd ubuntu-desktop"
[*]
[LIST]
[*]Said something about not being able to find "bash"
[/LIST]


[*]Ran "sudo apt-get install ubuntu-desktop"
[LIST]
[*]Result was "Failed to fetch some archives"
[*]Suggested that I run "--fix-missing" (didn't work) or "an apt-get update" (don't know how)
[/LIST]

[*]Tried to install packages cgpt, vboot-utils, xserver-xorg-video-armsoc
[LIST]
[*]Same failure as before
[/LIST]

[*]Ran "startx"
[LIST]
[*]"Server terminated with error (1). Closing log file"
[/LIST]
[/LIST]

I'm not sure what to do from this point... I don't know what it means that it "failed to fetch archives" and I don't know whether it can be fixed or whether I should try with a different environment.

I realise I forgot to specify this earlier -- I'm using Ubuntu 13.04 chrubuntu tty1 on the Samsung ARM Chromebook.

---

### Post by travis9 on 2013-09-30
I'm basically where you are, temujin. I also used Jay Lee's website instructions to get ChrUbuntu on my Samsung ARM Chromebook, but can only get a command line interface. The only difference from you is that I installed version 12.04.2 instead of 13.04 Unity, since Jay's website mentioned the ARM chromebook seems to have some issues with the former. And so I also got the xubuntu-desktop as he recommended that as default on ARM.

Really wish someone would help us... If I happen to figure it out, I'll mention it here though.

UPDATE:

Just found this in the comments section of Jay's webpage:

"Posting to confirm that if you are trying to get the script to run on the Samsung ARM platform you can run "curl -L -O [http://goo.gl/s9ryd](http://goo.gl/s9ryd):  bash s9ryd ubuntu-desktop lts" and it will work fine. Then if you want  to install lets say XFCE, once Ubuntu Loads, edit your sources.list.  (sudo nano /etc/apt/sources.list) Uncomment any line ending in  "main-restricted" and all four under the "universe" repo. (To be clear, I  dont know which one fixes it, I just uncommented all of those and it  worked.) Save the file and then run, "sudo apt-get update". After that  you can run "sudo apt-get install xubuntu-desktop" and after it install  you will be able to now switch launchers! I have only tested it with  XFCE, but it should work with all of the other launchers as well. Enjoy."

Not sure if it works yet...will get back to you.

---

### Post by richard24 on 2013-10-01
Hei, **termujin1**

Have you resolved this problem?

I am trying to install Linux(Ubuntu or other distro) on Samsung ARM Chromebook. I can't open the link you mentioned, maybe some network issue in China.
And I refer this one [http://www.amirkurtovic.com/blog/installing-chrubuntu-on-the-samsung-arm-chromebook-a-step-by-step-photo-guide/](http://www.amirkurtovic.com/blog/installing-chrubuntu-on-the-samsung-arm-chromebook-a-step-by-step-photo-guide/)

And after installation, I typed "Ctrl + U", it beeped and show the "OS verification is OFF" screen.
Just like no SD is pluged or no OS is installed.

Hmm, have you met this before?

---

