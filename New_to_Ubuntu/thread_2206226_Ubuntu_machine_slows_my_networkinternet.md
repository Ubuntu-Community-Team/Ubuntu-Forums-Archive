---
title: "Ubuntu machine slows my network/internet"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by keith3 on 2014-02-18
My home network is pretty laden with devices, but a speed test shows my Mac (one of the devices) chuggs along at about 10 mbps, a windows laptop at around 11.

When I connect the ubuntu machine to the network, the Mac slows to about 3 mbps. The internet is almost unusable when the ubuntu machine is connected - pages won't load, for example, on the Mac.

So, any thoughts on how I fix this? When other devices connect to the same network, there are no slowing issues.

Thanks in advance!

---

### Post by Vladlenin5000 on 2014-02-18
Was it recently installed? It could be downloading a huge load of updates...
Are you torrenting with the Ubuntu machine?

---

### Post by Vladlenin5000 on 2014-02-18
... Or the "old crappy netbook" you mentioned here [http://ubuntuforums.org/showthread.php?t=2203514&p=12919379#post12919379](http://ubuntuforums.org/showthread.php?t=2203514&p=12919379#post12919379) has a b/g only wireless thus automatically slowing down any "b/g/n mixed mode" wireless network?... 

Note: This is anew thread and you should have provided some more info. Other users shouldn't have to go through your other posts in order to get the above information which may or may not be crucial to understand your reported problem.

---

### Post by keith3 on 2014-02-18
Sorry, Vlad. I didn't expect you to go through my previous posts to find answers, but I wasn't sure of the questions and what details to provide.

I don't think that any updates are being uploaded, and when I disconnect the wireless it doesn't tell me that there was anything interrupted.

The machine itself is an Acer Aspire one notebook - not new, but it should at least have n wireless. I'm not sure how to check the stats on the wireless card, though - any suggestions?

Thanks.

---

### Post by keith3 on 2014-02-18
Oh, and further to that, I am only using the ubuntu machine to expose folders for files, it isn't doing anything other than using Samba.

---

### Post by mastablasta on 2014-02-18
lspci command should get you the chip out. see more here on hwo to get answers faster: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

samba shouldnt' be an issue unless you are using it to do some file indexing on shared drives. :-)

use top command to see what processes are running and also check sytsem monitor to see if there is any excessive network usssage on ubuntu maschine.

---

### Post by fdrake on 2014-02-18
i had the same problem with my acer aspire one too. Nobody would be able to go online if I was connected with my notebook. I tried with fedora and the problem dissapeared. Must have been a driver issue. Check you driver , but first check the previous suggestions.
possible help: [http://askubuntu.com/questions/253470/wi-fi-interferes-with-other-devices-when-connected?rq=1](http://askubuntu.com/questions/253470/wi-fi-interferes-with-other-devices-when-connected?rq=1)

---

### Post by varunendra on 2014-02-18
@keith3 ,

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It will give us a detailed information about your wireless and related configurations.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

