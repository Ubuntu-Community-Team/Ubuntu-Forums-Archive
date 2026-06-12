---
title: "Screen Black/Off after upadating..."
date: 2013-04-16
forum: New to Ubuntu
---

### Post by iretrala on 2013-04-16
I installed Ubuntu 12.10 64-bit on my 2 year old laptop (Gateway ID49C01h - stock). All was going great until I decided to let it update. It downloaded all the updates and started to install them. Then it told me that it had to restart. So, I let it restart. Well, that was clearly a mistake.

Now, when I let it boot up I get the dark purple background, then, the display shuts off and does nto turn back on for anything. I can boot up GRUB and test things, go into command line, etc. Nothing else. :(

All was working 100% before the update. Can anyone advise on what I should do? Thanks.

---

### Post by Hadaka on 2013-04-16
Hi, you sure are having some great luck there !
ok..since you can get to a command prompt, Let's
see what you have for network cards. please do,,
```
rfkill list all
lspci -nn | egrep '0200|0280'
```
thanks.

---

### Post by afz12 on 2013-04-16
> **iretrala said:**
>  All was working 100% before the update. Can anyone advise on what I should do? Thanks.  Hi Hadaka. I had the same problem with Ubuntu 12.04 and posted this a week or so back. The "fix" was offered by one respondent that allowed the last update "version" to be removed. Some other people have posted similar observations - it seems that Ubuntu, these days, is loosing its original stability. I didn't get to test the fixes as I replaced Ubuntu 12.04 with your version Ubuntu 12.10. It did show boot up isses sometimes, and so rather than wait for the seemingly inevitable I replaced it now with Ubuntu 13.04 Beta. So far, this seems stable / secure. However I am not confident in Ubuntu at this stage and use dual boot with Mint Cinammon - if one OS plays games then I can boot into the other.   In any case, I don't beleive your computer is at fault, nor do I think you have installed the OS incorrectly. Instead, it seems more plausible (to me) that the Ubuntu team has made a silly blunder! I guess the more we do, the more likely mistakes become :)

---

### Post by iretrala on 2013-04-16
> **afz12 said:**
> Hi Hadaka. I had the same problem with Ubuntu 12.04 and posted this a week or so back. The "fix" was offered by one respondent that allowed the last update "version" to be removed. Some other people have posted similar observations - it seems that Ubuntu, these days, is loosing its original stability. I didn't get to test the fixes as I replaced Ubuntu 12.04 with your version Ubuntu 12.10. It did show boot up isses sometimes, and so rather than wait for the seemingly inevitable I replaced it now with Ubuntu 13.04 Beta. So far, this seems stable / secure. However I am not confident in Ubuntu at this stage and use dual boot with Mint Cinammon - if one OS plays games then I can boot into the other.   In any case, I don't beleive your computer is at fault, nor do I think you have installed the OS incorrectly. Instead, it seems more plausible (to me) that the Ubuntu team has made a silly blunder! I guess the more we do, the more likely mistakes become :)

I see. Would you be willing to post a link on this to the instructions you were given. I miss it working. lol

---

### Post by iretrala on 2013-04-16
> **Hadaka said:**
> Hi, you sure are having some great luck there !
ok..since you can get to a command prompt, Let's
see what you have for network cards. please do,,
```
rfkill list all
lspci -nn | egrep '0200|0280'
```
thanks.

I have full access on this laptop via WiFi or Ethernet. Are you sure you want to know? I did not think that they network cards had anything to do with the display. :/

---

### Post by afz12 on 2013-04-16
Hi iretrala. I found my original post 1 week ago (it took ages as I'm at a dial-up location just now!).


  [http://ubuntuforums.org/showthread.php?t=2132873&highlight=boot+Ubuntu+12.04](http://ubuntuforums.org/showthread.php?t=2132873&highlight=boot+Ubuntu+12.04)  


vincav91's reply-post supplied some useful links .


   [http://askubuntu.com/questions/10603...er-downgrading](http://askubuntu.com/questions/10603...er-downgrading)  [URL="http://ubuntuforums.org/showthread.php?t=1587462"]


http://ubuntuforums.org/showthread.php?t=1587462[/URL]


  [http://askubuntu.com/questions/13549...ack-in-old-one](http://askubuntu.com/questions/13549...ack-in-old-one)   


of which the first seemed most relevant. Good luck!

---

### Post by iretrala on 2013-04-22
Unfortunately, not a single thing worked. What I ended up doing is upgrading to 13.04 beta. Strangely enough, it is all working just fine, now. Faster, even.

Thank you for your help, though.

---

