---
title: "Seeking advice regarding set-up"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by melak on 2008-05-13
I'm new to Ubuntu, tried it twice before and just couldn't find my groove but I've been using it for a week and I've found it so I'd like to move over more or less permanently, just wondering how I can do this with the least amount of problems.

Current Set-up
Master HD - 500 GB featuring windows formatted in NTFS
about 275 gigs worth of video files, my documents, non OS stuff
about 20-40 gigs windows os

Slave HD - 250 GB featuring Ubuntu (though only coming up 
230 Gig of Ubuntu first on drive (only using 5 gig) then a 3 gig swap at the end.

What I picture
Master HD - 250
Say 40gig devoted to Ubuntu, 60-80 to Windows, rest partitioned as just file storage

Slave HD - 500
featuring Documents and Settings of Windows, /home of Ubuntu, rest shared storage (this is where I picture the video files going)

Why I'm seeking adivce:
right now since the Ubuntu is a recently fresh install, I don't mind losing it and rebuilding but I'd like to port the windows as is, without reinstall. 

I'm not that worried about the video files as I assume I can just shrink the xp partition, slap another partition at the end, then transfer the files and once I get rid of the windows partition on the 500 G drive just expand the other one to take up the whole drive and have that be the settings/storage drive. I am worried about moving xp over and running into problems.

Any advice on how this can be done seemlessly? Am I out to lunch on the whole idea? What do you think?

---

### Post by tjwoosta on 2008-05-13
i think you sound like you pretty much have it covered


use the ubuntu live cd (System-Administration-Partition Manager) to shrink your xp partition 
(make sure to defragment windows a couple of times first, to move all the data to the beginning of the partition)

you can leave the space that you make unallocated,  then just go back to the desktop and click install 

when you get to the part where it asks how you want to install, just click "Guided Install: use largest contitnuous free space" (this will install to the unallocated space)

also make sure to install grub to the MBR (master boot record)

also after its installed you can simply mount the windows partition from ubuntu and copy all your files over


so i dont think you should run into any problems

---

