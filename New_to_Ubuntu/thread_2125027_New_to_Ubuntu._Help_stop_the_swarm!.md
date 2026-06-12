---
title: "New to Ubuntu. Help stop the swarm!"
date: 2013-03-12
forum: New to Ubuntu
---

### Post by Digitallust on 2013-03-12
As the title says, I'm new to this Linux stuff but have had interest in it as of late. So I decided I'd rid myself of Windows for a fresh new scene. Enter Ubuntu! Anyways, It started out smoothly for a few days as I adjusted myself to the ins and outs of the new OS, but now...It won't stop. No more than 5-10 minutes into it, it just starts spitting screenshots at me. A lot of them. No matter how fast I click, they just keep coming. I thought that perhaps it was a stuck key, but it was not. I later thought that perhaps it was because I was using the newer 12.10 version, so I wiped everything and flew over to 12.04. Everything's cool for a bit, and then it happens again. I go to my calm place for a few and then go for another try. Nothing. So, I try switching to Kubuntu 12.04 (Which btw, Is just as awesome) but it to succumbs to the one million screenshots. I've also tried ridding myself of the screenshot tool altogether (Not sure if I did that right, sure I did though) but it didn't work either. I've tried Boot managers to try and turn it off, and nothing seems to work. There is also a few other issues to, but their not a big deal. Mainly text just trailing off in text boxes sometimes. It's a laptop, Toshiba Satellite U505-s2002. Please...HELP!

---

### Post by meteorrock on 2013-03-12
If that program reloops, and you are having this same problem in different distros that you have tried you should conclude it might be a hardware problem, and/or a driver, BIOS problem.  Did you update your drivers for your laptop? Flash based drivers and that program is notorious for doing that, opening up TONS of boxes in a loop when that app hangs, like what the game program "solitare" does on Windows when you win a game. So try to disable the flash apps on your laptop in Ubuntu. 

Then try to find the specs on your processor online through your vendor for your laptop and see if there is a BIOS upgrade and then a processor upgrade for those drivers, and update your other drivers also, your wifi drivers, sound drivers and such. A BIOS upgrade should help also with glitches like that. After you do these things, reboot your ubuntu distro you are using and see if that helps.

You can also try to purge your flash player to see if that is the problem with this command in the terminal. Then reinstall. But I would update all of my drivers and BIOS on that laptop first.

```
sudo apt-get update
```

```
 sudo apt-get remove flashplayer-nonfree
```

Then try to reinstall it.  Reinstall it after completing your BIOS upgrade and driver upgrades so you will not have that program reloop on you first.

 ```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

There are other different flash players to try if you still have problems after doing the steps above, like adobe flash. This link here shows you how to install that app. [http://www.dedoimedo.com/computers/flash_firefox_linux.html](http://www.dedoimedo.com/computers/flash_firefox_linux.html)

---

### Post by Frogs Hair on 2013-03-12
The fact that it has happened with three different operating systems might suggest a problem with the print screen key or binding. I am not familiar with the keyboard layout on that computer , but many forum members use them. Check keyboard > short cuts. If the binding is set to a common key you may be printing screen every time you use that key.

---

### Post by Digitallust on 2013-03-12
Thanks for the timely replies guys. I've already done another sweep up of the OS and am back to Ubuntu 12.10 now. Surprisingly, it hasn't given me any trouble, but I appreciate the helpful answers! I'll be updating my Bios and such right now while I'm thinking about it, since that's something I neglect to do often. IF it happens again, I'll try purging flash. I also thought it may have been a key it was binded to, but that doesn't seem to be the case. None of the keys "feel" broke, anyways. I appreciate the quick help! Solved for now.

---

### Post by Frogs Hair on 2013-03-12
I don't think it is broken key but possibly the binding . If print screen was set to use the B key or some other key for some reason during installation every time you hit that key you create a screen shot. Check for additional drivers also.

---

