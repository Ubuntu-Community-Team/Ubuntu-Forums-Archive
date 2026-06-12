---
title: "Ubuntu 12.10 keeps on booting to black and screen and other issues"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by neewbee on 2012-10-28
Hey everyone I just installed Ubuntu 12.10 on my desktop.

Here are my specs

Corsair ssd 60gb 
Radeon Hd 7770 1 ghz edition 
Asus P8 V-77 Motherboard 
Corsair 650 Watt PSU 

I just did a clean install of 12.10 recently . When I restart the desktop it goes to a black screen and than I have to remove my vga to mini adapter out of the back of graphics card to see the purple background.  

Also my desktop freezes and I get the error that compiz crashed. This is getting very annoying. What solutions are out there so I can fix this problem? I am new to ubuntu but not new to programming. I am learning something new all the time. 

I am willing to get a new graphics card. I heard Nividia is good with linux systems. I have always used Nividia .It wasn’t until recently that I got an ATI card. Cant say I like it much. 

I plan on using that new graphics card for gaming on windows 8 as well as running mac osx lion.  What Nividia card do you suggest thats mid level  and good for gaming and linux as well as a hackintosh and gaming?

Thanks for your help!

---

### Post by Bashing-om on 2012-10-28
neewbee; Hi ! Welcome to the forum.

Graphics issues can definitely be problematic with a myriad of possible solutions.

here, I  present one --temporary see if it works -- to boot:
radeon.modeset=0 -. This link for full implementation/explanations:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Then, this most excellent trouble shooting guide ..very long read, very informative; added bonus: if you can follow and understand the concepts, it renders a good foundation for working in ubuntu !
[http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915](http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915)

Have a read, direct your graphical queries related to this problem on this thread; Other questions submit on new thread for broader viewing.

All questions are welcome.
[INDENT]warm regards <== BDQ

[/INDENT]

---

### Post by gordintoronto on 2012-10-28
Can you describe "VGA to mini adapter" more fully, please? What CPU? What brand and model of monitor?

Further reading about the black screen:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by alphacrucis2 on 2012-10-28
I'd try installing the latest AMD Catalyst driver (version 12.10 released on 22 October)) from the AMD website.

---

### Post by pau1w on 2012-10-30
I have had the hd 7770 for quite a few months and i have tested it on ubuntu after every few updates, but I still get a error when installing the ati driver.
 
I have gotten full support for the card by installing Linux Mint and then the 12.10 ati driver. I would like to use ubuntu instead, except there is and extra package or something the lm that ubuntu doesn't have.

---

### Post by neewbee on 2012-10-30
I am thinking of getting GT 640 [http://www.newegg.com/Product/Product.aspx?Item=N82E16814127680&nm_mc=KNC-GoogleAdwords&cm_mmc=KNC-GoogleAdwords-_-pla-_-NA-_-NA](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127680&nm_mc=KNC-GoogleAdwords&cm_mmc=KNC-GoogleAdwords-_-pla-_-NA-_-NA)

will this work well in Ubuntu?

---

### Post by neewbee on 2012-10-30
Bump I am ordering a new card tonight what do you guys suggest that is stable in ubuntu? My 7770 has been malfunctioning in windows as well.

---

### Post by squakie on 2012-10-30
Just get a new nVidia card that has the specs you need.  There may still be a couple of options to tweak before it will boot correctly, but it is workable.  AMD/ATI really hasn't been that great with Ubuntu from what I've seen on the forum.  I'm running an GeForce GS 450 (I think - it's been a while since I put the box together) and it has worked fine with Ubuntu.

---

### Post by neewbee on 2012-10-30
Thanks for the input!


Could you suggest anything more powerful that could work in Ubuntu besides the 450.

---

### Post by pqwoerituytrueiwoq on 2012-10-30
what are you going to use the gpu for?
eg videos, unity, gaming (what resolution, desired fps, which game), bitcoin mining, bragging rights, etc

---

### Post by neewbee on 2012-10-30
I plan on using this for gaming on both Ubuntu and windows. I plan on also running osx Lion.

my resolution for 32 inch t.v is 720p 


Thanks again!

---

### Post by pau1w on 2012-10-30
Like I said in my last post, I have been testing ubuntu off and on for support of my gpu (hd 7770) after updates. Today I did a fresh 12.10 install, installed the kernel headers, and then ati 12.11 driver, and the drivers successfully installed.
If you haven't installed the latest ati 12.11 driver, then you should do that before buying a new card.

ps. dual monitors also works great!

---

### Post by pqwoerituytrueiwoq on 2012-10-31
720p does not take that much
[all of these should]("http://www.newegg.com/Product/Productcompare.aspx?Submit=ENE&N=100006662&IsNodeId=1&Description=560%20se&bop=And&CompareItemList=-1|14-130-827^14-130-827-TS%2C14-162-124^14-162-124-TS%2C14-134-119^14-134-119-TS%2C14-130-625^14-130-625-TS%2C14-500-241^14-500-241-TS") do playable on high settings for any game at 720p
be sure to check the psu requirements before ordering

+1 for the above post, the HD 7770 should be better than most/all the cards in that link
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
some gpu driver relevant PPAs
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates) (stable)
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) (testing)

---

### Post by pau1w on 2012-10-31
Today I installed ubuntu 12.10 on my main hdd(my previous post was on my hdd for testing) and I installed the required header files. 

The time previous that it worked, I manually installed the file from this link [http://www.ubuntuupdates.org/package/core/quantal/main/base/linux-headers-3.5.0-17-generic](http://www.ubuntuupdates.org/package/core/quantal/main/base/linux-headers-3.5.0-17-generic) because i needed it to get ethernet drivers(networking worked, it was just slow).

This time when I was installing the headers, I selected the header files through synaptic package manager and then installed the ati driver. This time it resulted in a black screen like the op said. The fix to this was to manually install the file linked above instead of having synaptic automatically install it.  

:)

---

