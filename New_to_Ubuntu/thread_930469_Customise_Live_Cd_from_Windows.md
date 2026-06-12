---
title: "Customise Live Cd from Windows"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by Rhyn Weatherhead on 2008-09-26
Hi I'm tryng to customise a live cd, using windows.
Reason can't inastall ubunut on machine too little space on hdd.
What I do have is a pimped up version of 6.06 live cd.
It has everything every big game I rekon easy over 5gb of stuff, trouble is this live cd wont run on my lenovo T61P probably nvidia drivers or support, but she aint taking it.
However the new 8.04 live cd does work on my t61p so i wanted to know if i could copy the right file from the 8.04 live cd onto the 6.06 live cd recreate iso using Gizmo and be on my way or visa versa.

Sadly no one can tell if this can be done or if it can what file must be copied and replaced.

I tried this two ways because all the games are located in the filestsystem.squashfs ( I think) I copied the 6.06 squashfs file and pasted it over the one in the 8.04 live cd in the casper folder, I created the Image using gizmo but the darn thing wont boot.

Then I tried to copy the other way 

I only took the initrd file from the 8.04 live cd and copied over the one on the 6.06 live cd,

Please if anyone knows what I should do please advise. 
I can't open the squashfs file from windows there doesn't appear to be any such software available otherwise I'm guessing I could move the files from my old live cd into somewhere on my new live cd and proberly have a better change of getting a customised live cd with all my games and nividia support again.

I live in South africa Bandwidth is problem so I cant just download these games It could cost in the region of about $90 US just to download these gamining files and that is no joke.

So you can see why I'm trying to do What I'm trying to do.
I would be really gratefull for advise or assistance.
I'm reluctant to install ubuntu as I have very little space left on my machine and the live cd is working nicely for gaming around the office on other machines.

I am planning on getting ubuntu onto a flash drive soon so that I can save my game data but I'll get there soon too.

Any or all information possible will be apprecaited.

Regards
Big Ubuntu Fan

---

### Post by nowshining on 2008-09-26
what's the size of the HD that ubuntu won't install on?

---

### Post by Rhyn Weatherhead on 2008-09-26
I've go 30gbs left of my HDD, its 160Gb,but I dont feel like messing around with HDD at all. Data is too valuble on it and its just not an option right now anyway. I have seen the many threads of how to do it in ubuntu,I migh be able to pull it off I did try and got stuck install the squashfs tools, I had an ubuntu partition but then I need all the space back again so my window of opportuinity has closed there is there nothing really to guide me through this using windows?

---

### Post by Sycron on 2008-09-26
Well 5GB it's enough for a ubuntu install. But you have to clean some files periodically.

---

### Post by Rhyn Weatherhead on 2008-09-26
Hi 
Yes I know that its not a big install and now with Wubi its amazing, but I can't right now. Putting ubuntu back onto Hdd not an option,I had to use Rescue and recovery Cd's to completaly get everything back to normal after my last ubuntu install, I'm just not there yet with ubuntu.

However i was just thinking that when I had booted with the live cd it gave me access to the etc file that I couldn't get from eploring the cd from window explorer. What if I copy the file system to to my docs and then boot back into windows edit the etc file which contains the xorg.conf file and then try remaking the iso.

I will try and advise. okay not going to work I can't copy the files from the 6.06 cd in this way because I can't get it to boot. LOL

Formally stuck here.

Looks like the only way to do it is to install Ubuntu I have to face facts here...

---

### Post by Rhyn Weatherhead on 2008-09-26
Just incase any of you are interested I have, used Gizmo a free windows program 

[http://www.download.com/Gizmo-Drive/3000-2248_4-10407554.html](http://www.download.com/Gizmo-Drive/3000-2248_4-10407554.html)

Then I burn't both the images of my Ubuntu live Cd's and I have opened them using winrar, 
It has an option to convert to rar from iso, i hope it can reverse that?

I am then going to change the filesystem.squashfs file inside the casper folder on the live cd. Swopping the 690 mb one for the 3 gb one and then I'm going to try and turn it back into an Iso file using winrar or what ever I can get my hands on and then I'm going to try and boot this sucker.

Still desperate for expert advise. as I am extreemly doubtfull this will work???

Still an Ubuntu Fan!

---

### Post by Sycron on 2008-09-26
I think you can't. The iso contains a boot sector.

---

