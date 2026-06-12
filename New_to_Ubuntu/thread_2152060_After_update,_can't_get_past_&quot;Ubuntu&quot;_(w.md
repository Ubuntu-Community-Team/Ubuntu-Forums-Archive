---
title: "After update, can't get past &quot;Ubuntu&quot; (with the 5 dots)"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by john1despair on 2013-06-06
Hi

After a long illness (3 years) I returned to using my Dell Inspiron XT laptop which was successfully running Ubuntu.  Things seemed to work fine. Then, the update manager suggested I get the latest version and I did as instructed.  I returned several hours later and my screen was black.  I attempted a hard reboot, and now I don't get past the introductory screen  which has the word Ubuntu and five dots underneath the word which systematically change colors (red/white).  When I paused the reboot, I found cryptic messages such as:

***Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start S50cups***

There are many cryptic lines on the screen which end with ***[OK]***  except for one line which reads
[I][B]
*Stopping automatic crash report generation. [/B][/I]   ***[[COLOR=#ff0000]fail[/COLOR]]***

when I stopped pausing I return to the Ubuntu with five dots screen again.

Many years ago, I used to know something, but now I am the purest form of newbie possible.

Any suggestions as how to proceed?

---

### Post by monkeybrain2012 on 2013-06-06
What version did you upgrade from? Probably it was a blotched upgrade because your old version had reached end of life long ago (you last used it 3 years ago?)  I think you should just download a live iso for 12.04 and do a clean install,

---

### Post by john1despair on 2013-06-06
> **monkeybrain2012 said:**
> What version did you upgrade from? Probably it was a blotched upgrade because your old version had reached end of life long ago (you last used it 3 years ago?)  I think you should just download a live iso for 12.04 and do a clean install,

I am such a newbie that the phrase,

 ***you should just download a live iso for 12.04 and do a clean install ***

is not completely understood by me.  How would I do that?  I am used to having a functioning browser or such, downloading some self-extracting archive or such, executing it, and then "Yeah,  a new OS".
Where do I get a "live iso for 12.04" and how do I do a "clean install"
Also, what happens to the documents, files, etc. on the machine.  Will they reappear?


Thank you very much for your quick reply, and my regrets that I do not understand more than I do.

---

### Post by oldfred on 2013-06-06
If you do a new clean install, it will overwrite all you data. If partition is still readable, you can backup /home which has all you data & settings. If you have a separate /home partition a new clean install is a lot easier as you can just reuse your existing /home if you DO NOT reformat it as part of the install.

       Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

      
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by john1despair on 2013-06-06
Hi

Thanks for the information, but I will be very, very, very sad to lose the files already on the computer.  I do not know what I will do next.  I really want to retrieve the stuff that was on that computer. Thanks again.

---

### Post by oldfred on 2013-06-06
The live installer should let you mount the partition and then you can copy /home to a flash drive or another drive. Just be sure to include the hidden files & folders. Best not to copy to NTFS nor FAT32 as you lose ownership & permissions. With /home you can reset but easier not to have to.

---

