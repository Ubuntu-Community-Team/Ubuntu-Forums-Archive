---
title: "Acer aspire 5315 laptop on 12.04"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by Jocklad on 2012-06-26
This machine was previously loaded with Vista which was in an awful mess.

Have sucessfully installed 12.04 with all updates but have found to my horror

that the fan control is controlled by Vista software.

Of course the fan is not running and will overheat and shut down system.

Any way round this running 12.04...?.

Thanks for any help.

Jocklad

---

### Post by ikt on 2012-06-26
[http://ubuntuforums.org/showthread.php?t=1748521](http://ubuntuforums.org/showthread.php?t=1748521)

Appears to have the issue fixed :)

---

### Post by jmfal on 2012-06-26
Take a look at this,  go to post #5 and open the link :

[http://ubuntuforums.org/showthread.php?t=1998011&highlight=acer+aspire+fan](http://ubuntuforums.org/showthread.php?t=1998011&highlight=acer+aspire+fan)

---

### Post by Jocklad on 2012-06-26
Thank you all for the info.

But am lost as how to actually load it to HDD

Jocklad:?:

---

### Post by Fernhill Linux Project on 2012-06-26
I purchased an Acer 5315 some years ago, and had the same overheating problems you have. After trying many solutions I upgraded/flashed the Bios from version 1.19 which it came with to version 1.43 (the latest at the time). This resolved all problems and the fan worked properly after that.

I downloaded to Bios update from the official acer site, google will find it for you.

There may be other solutions but the above worked for me.

---

### Post by Jocklad on 2012-06-26
Thanks for that but it seems from the Acer site that Bios update can 

only be done with Windows installed.

Does not even mention Linux.

Stumped......

Jocklad:confused:

---

### Post by Fernhill Linux Project on 2012-06-26
Sorry I forgot to mention that I did a fresh install of windows (because there was no linux support for the bios flash as you reminded me) before updating the Bios, and deleting windows forever...

Bit of a fiddle and some messing around, but I know this solution works for this laptop.

Hope it helps ;)

---

### Post by idoitprone on 2012-06-26
[http://www.linlap.com/wiki/acer+aspire+5315](http://www.linlap.com/wiki/acer+aspire+5315)

this is the link

I cannot guarantee that it will work, but this is a suggestion from lin laptop

[http://ubuntuforums.org/showthread.php?p=9646303#post9646303](http://ubuntuforums.org/showthread.php?p=9646303#post9646303)

---

### Post by Jocklad on 2012-07-04
Thank you all for your replies.

Had a thought and did a fresh install of XP.

Fan was running perfectly.

Flashed the Bios and Reinstalled 12.04

Bliss..............All is well.:guitar:

Jocklad):P

---

### Post by makuto on 2013-01-19
yep! I had the same CPU fan issue, and after trying "smoother" solutions as the script mentioned in [http://ubuntuforums.org/showthread.php?t=1748521](http://ubuntuforums.org/showthread.php?t=1748521), updating kernel to 3.7.2..., and all worthless for my aspire 5315 fan problem, that didn't run with the consequentional overheating and further shut off after a while...I took the risk and finally flashed the BIOS, updating my actual version 1.19 to 1.45 successfully (downloaded from the official Acer page)

the only cons?   I had to install a win OS temporally (I did not wanted to risk with wine) only for flashing BIOS, anyway...it worked and now back on Ubuntu 12.04 LTS with a laptop working with no problems: no more overheatings, sudden shut downs, or not working CPU fan.

thanks for all of you that make possible the solutions to problems that many of us thougt impossible, hehehe!!;-)

---

### Post by agfox on 2013-01-24
Hi, I am a bit of an Ubuntu newbie, and am enjoying learning a lot more about how computer, operating systems etc work, and totally love Ubuntu. However. I too have experienced the same fan issue with my Acer Aspire 5315, whereby it hasn't worked since I wiped Vista off it, and inadvertently wiped the Acer e management software which controls the fan, (google research).

 I have no way of getting windows back as I deleted all partitions. I have found a kind of fix whereby if I suspend the laptop and then go back in, Ubuntu seems to realize there is a fan and controls it. 

However more than once I have forgotten to do this and have nearly fried my 5315!

 I have seen the link

[http://ubuntuforums.org/showthread.php?t=1748521](http://ubuntuforums.org/showthread.php?t=1748521) 

and have had a go doing it, but am seriously lacking knowledge to achieve this as I think it assumes moderate Ubuntu knowledge. Is there any chance somebody could write a set of simplified instructions with more steps, explaining unpacking so on and so forth and when I need to be in terminal or somewhere else? 

Also I cannot even download that file on the above mentioned thread until I have made 25 posts, so its 24 to go, although I believe I may have found the same file by some simple googling.

I'm currently running Ubuntu 12.04 lts, have an Acer Aspire 5315 which I upgraded from 1gb to 2 gb

Thanking you in advance

agfox

---

