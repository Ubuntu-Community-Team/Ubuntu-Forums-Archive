---
title: "Dual Boot with MS Vista"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by rohitsb on 2008-04-28
Hello,

To give me something to do in my free time, I've decided to pursue Linux. I must confess that I'm a newbie when it comes to Linux, but I do have sufficient programming experience. After trawling the net, I found that Ubuntu is probably the best distro for beginners.

While I have found a wealth of information in these forums, some questions still make me uneasy:

1. I currently have Vista installed on my Acer AS5920 laptop - 1 HDD with 1 recovery partition, 2 Windows partitions (C: & D:) & one Acer-specific partition. Questions:
         i. Which of these partitions should I resize ?
        ii. Can we have more than 4 partitions on a HDD (Linux + Windows) ?

2. Since I'm new to Linux, I'd prefer to keep Vista for some more time, which would mean that I'll need a dual boot. Questions:
         i. Should I install GRUB to MBR or to /boot ?
        ii. If I install GRUB to MBR, does it remove the ability to boot into recovery partition ?

3. Is anyone aware of any driver issues with AS5920 (bit of a long shot !!) ?

Finally, some freezing has been reported on 8.04, is it worth the risk to install 8.04 (which might have better driver support) or stick with 7.10 for the time being ?

Thanks for your inputs, people.

RSB

PS: I couldn't find a thread which addressed these questions, if there's one, you can just point me in the direction.

---

### Post by daraman2000 on 2008-04-28
I would recommend using the Wubi install option to try things out. Wubi installs ubuntu by "tricking" the PC into thinking there's another partition. it can easily be uninstalled , and has only a minor speed hitch.

Now, on to your questions: 
you can have as many partitions as you like, just don't go crazy. Too many may cause corruption. Vista's own drive resize tool (right click on computer, select manage) is surprisingly good at resizing. Also, remember to have another PC handy to ask questions with. 

Also, I'd recommend trying out [Linux Mint]("http://www.linuxmint.com/") too. Its very user-friendly, a little more stable, and generally better for beginners. 

The only viible advantages with 8.04 are the new kernel (its bittersweet tho), and Wubi.

Other tips:
don't give up to easily
the terminal, or console, is your FRIEND
also, you may want to read [this article]("http://linux.oneandoneis2.org/LNW.htm").
Don't be discouraged if your flamed; longtime linux users can sometimes do that. Just read it as constructive criticism.

PS: the cake is a lie

---

### Post by smoker on 2008-04-28
i would try the live-cd before you commit yourself to an install, this will give you some time to experiment and learn some basics, as well as let you know if all your hardware is detected ok,

as for partitions, you can have as many as you need, though only a max of 4 primary partitions. if you resize a windows ntfs partition to make space for a new linux partition, if you defrag windows a few times first, it will be easier and quicker  when it comes to resizing that partition. it is up to you how you want to divide your hard drive, but i would want a bare minimum of 10 gb for ubuntu, plus you will need a 'swap' partition, usually sized to double your ram.

i would put grub on the mbr, you will be able to use the windows recovery app to remove it if ever required.

hope this has helped some, welcome to ubuntu

---

### Post by daraman2000 on 2008-04-28
also, your ram + your SWAP should be under 4 gigs if you're using a 32 bi system.

---

### Post by rohitsb on 2008-04-28
@daraman2000
  Thanks for the Wubi tip - I'll definitely give it a shot before I commit to a devoted partition for Linux. I'll also read-up on the Linux Mint (which from what I gathered uses the Gutsy kernel) before making a final decision. What makes me lean towards a distro like Ubuntu is the presence of a large community (such as this one) to help resolve issues.

@smoker & @daraman2000
  I'm still a little confused about the MBR thingie, though. Is it worth it to install on MBR or should I use EasyBCD (or equivalent) to accomplish the dual boot ? My primary concern is whether updating the MBR will render my other partitions (recovery, Vista and Acer-specific) unusable and _not_ whether my recovery application would be able to fix the corrupted MBR.

PS: A brave new world, this Linux (well, maybe not new, but at least brave)

---

### Post by sam_delta on 2008-04-28
you shoulnt worry for the double boot at all, you insert the live cd, click install and when installing it will let you resize your windows partition in order to let some free space for ubuntu, and unless you completely remove windows partition, it will install GRUB and set up the double boot for you.

sam

---

### Post by rohitsb on 2008-04-29
Hello,

I finally dipped my toes in Ubuntu. As suggested here, I got a copy of Wubi and 8.04 and proceeded to install on my T61 XP machine first. Installation was a breeze. The /host folder provides access to my NTFS part, which I find really nice.

However, I think I have some driver issues. I'm able to connect to the net via a wired connection but not via my Intel 4965 card Wireless Card. Any ideas ?

---

### Post by daraman2000 on 2008-04-29
What's ur wireless card's name?

---

### Post by rohitsb on 2008-04-29
It's a Intel 4965 card. When I try to connect to the wireless network, nothing happens (even though it "sees" all networks and correctly prompts me for the passphrase). I tried to catch hold the resident linux expert who suggested:

sudo iwconfig wlan0 essid "<network>" enc s:<passphrase>

I don't know why but that worked !! Next thing is to try to get my nVidia drivers working.

Thanks for your help, everyone.

---

