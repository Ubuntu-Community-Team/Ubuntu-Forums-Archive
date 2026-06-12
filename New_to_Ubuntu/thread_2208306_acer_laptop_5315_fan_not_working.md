---
title: "acer laptop 5315 fan not working"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by isla on 2014-02-27
This is a recognised problem to do with this laptop andsomething about BIOS which has to be flashed or something but that can only be done if i install windows again which i don't have... the other solution is to install and run a file and i have followed many instructions but it doesn't work and i mayhave done it wrong because i am not used to ubuntu or the 'terminal'.

the fan will come on if i turn the computer on when the computer is still hot. it wont go off tho. so i guess the thermostat isn't working somehow - sort of.

i have already posted this problem but my post has disappeared...

please help! 

thanks 
isla totall newbie:o

---

### Post by mörgæs on 2014-02-27
Posts don't disappear. 
If you forget where you post something just go to 'advanced search' and search for your own user name.

---

### Post by isla on 2014-03-05
Hi sorry to reply to my own thread - i'm not sure what to do about not having any advice yet.
I have followed the instructions i found on previous similar posts but i can't understand what i'm doing wrong with the script.  At the mo i have to keep the laptop on because if i turn it off the fan wont come on again. it only comes on if the laptop is hot when i turn it on - then it stays on the whole time.  

thanks
isla

---

### Post by howefield on 2014-03-05
After 5 days waiting for assistance (feel free to bump your thread once in 24 hours when no response) I think I would bite the bullet and install windows and get the BIOS flashed,  rather than use some work around that means you can't switch back off :)

What you do after that might be a little less painful :)

---

### Post by mörgæs on 2014-03-05
If you want help with flashing the BIOS without Windows, which may or may not be possible, you need to post the exact steps you have tried and the exact result. 

Stating that you found some instructions and did something does not give people much of a foundation for helping. 

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by isla on 2014-03-09
ok yes thanks i'll explain more -
i followed these instructions
[http://ubuntuforums.org/showthread.php?t=1748521](http://ubuntuforums.org/showthread.php?t=1748521)

where i installed a script that is provided on this link. the bit that i was unsure what it meant was when it says change the directory on step 4 but regardless i followed the instructions several times over so i now have that script, and it doesn't seem to work.

i don't have a copy of windows which is why i used ubuntu - i mean...i have a feeling that there is a small part of this drive...that is sectioned off, because i did not know what the hell i was doing when i was partitioning or something in order to install ubuntu. But i think there may be a part of the C drive that has a reset ability like, it would possibly set it back to the silly windows vista thing it had when i got this laptop but i have no idea how to find out and do all this stuff.

Thanks for any help and yes i'm happy to explain more I just wasn't sure what info was needed and what wasn't...
isla x

---

### Post by Rob Sayer on 2014-03-09
> **isla said:**
> n...i have a feeling that there is a small part of this drive...that is sectioned off, because i did not know what the hell i was doing when i was partitioning or something in order to install ubuntu. But i think there may be a part of the C drive that has a reset ability like, it would possibly set it back to the silly windows vista thing it had when i got this laptop but i have no idea how to find out and do all this stuff....

I somehow doubt there's anything like that.  In a single boot linux system there is a part that's "sectioned off" but it has nothing to do with windows.  It's called a swap partition.

To see what disk partitions you have enter into terminal:

```
sudo fdisk -lu
```

Beyond that I think you'll probably have to take the advice offered above to reflash the bios.  They certainly know a hell of a lot more about power management than I do.

---

### Post by Mark Phelps on 2014-03-09
> but i think there may be a part of the C drive that has a reset ability like, it would possibly set it back to the silly windows vista thing it had when i got this laptop

Windows still calls them "drives" when, in reality, they are "partitions" -- and in this case, you would be talking about a Recovery Partition that was put there when the laptop was initially configured.  If it is still there, the fdisk command results will show that.

---

### Post by isla on 2014-03-13
Thankyou very much - ok i've done that - here are the results

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaa4b0686

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    24563384    12281661   27  Hidden NTFS WinRE
/dev/sda2        24563446    90638729    33037642    f  W95 Ext'd (LBA)
/dev/sda3   *    90652672   139480796    24414062+  83  Linux
/dev/sda5        24563448    90638729    33037641   82  Linux swap / Solaris
ila@computeris:~$ 

```

if there is a way to do this flash bios I would greatly appreciate directions or pointers towards how this is done..I don't know how this helps the fan situation either. When i installed ubuntu i'm fairly sure i did it in a way that cut off half of my partition space in case it didn't work out but it has worked out and I would love to come back to ubuntu.

thanks very much again
isla

---

### Post by Mark Phelps on 2014-03-13
Word of sound advice -- unless you KNOW that a BIOS flash will fix a specific problem, do NOT do it.  I continue to be appalled by how often folks suggest updating a BIOS when, in nearly all cases, not only does it do no good, it's also a very risk operation because, if it's not done right, or if it fails (and you don't have a way to restore the old BIOS), you are left with a completely nonfunctional machine.

As to the instructions in the linked post, those are commands you must enter at the terminal.  When you said you didn't know what to do in step 4, the command was provided for you. It really doesn't get much simpler than that.

---

### Post by isla on 2014-03-17
it doesn't get much simpler -
thankyou for that...it also doesn't get simpler than reading what i said which is that i followed the instructions but they did not work. At step four i did what it said regardless of not understanding what i was doing at that stage. i researched what 'uncommenting' meant and i did it to the best of my ability as well but I still wouldn't know if i had done it wrong which is the point i was making. Why it doesn't work..i don't know, that's what i need help with and it isn't nice to just keep telling me how simple things are. If you had never used the terminal before, and didn't know much about ubuntu or computer things then you would also be asking for help, politely as I have done.

Can anybody take me through some steps to either find out why the script isn't working (from the instructions on the link i provided) or how to look into anything else and find out how i can get my fan working?

thanks
isla

---

