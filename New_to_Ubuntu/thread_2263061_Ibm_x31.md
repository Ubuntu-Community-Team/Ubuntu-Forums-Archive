---
title: "Ibm x31"
date: 2015-01-29
forum: New to Ubuntu
---

### Post by TheBigBean on 2015-01-29
I'm completely new to Linux and I'm hoping someone would be kind enough to help.

I think my question (at the end) might be easy to answer, but I am starting with what went wrong. This is what I did:
1. Created a 10 GB partition on my IBM X31 running Windows XP. I did this with windows.
2. Installed Lubuntu 10.04 on the paritition. I chose this because it works with a Pentium M processor and I had the ISO already on a USB (from playing with the live version a couple of years ago).
 3. Everything worked.
4. Tried to update Lubuntu from the command line. 
5. It downloaded and installed lots of things. I thought it was a sucess, so rebooted.
6. I received varying messages on start-up: IBM telling me to reinstall the operating system due to partition problems, blue screen of death when selecting windows from the bootloader and a message about disk problems along with a failed boot when selecting Lubuntu. So, a bit of a disaster with no operating system functioning, and only occasional ability to access the bootloader.
7. I put the USB back in, and after a few attempts managed to launch a live version of Lubuntu. I then re-installed it. It didn't seem obvious how to remove the previous installation, so I simply installed another version.
8. Tried to boot the new Lubuntu. Failed as before.
9. Was giving up and thought I would try Windows again. After some checks and tests, it worked. No idea why. 
10. I wasn't brave enough to try Lubuntu again.

So, I have now have a laptop with a functioning Windows when selected from a bootloader with two other Lubuntu installations present. I'd like to go back to step 1 with a clean paritition and a clean bootloader, so I can try installing Lubuntu again. This time I will probably try 14.04 and try to work around the pentium M issue. So what do I need to do?

I could probably sort out the now multiple partitions and format them in Windows, but will this kill the bootloader meaning that Windows will no longer work?

I do not have an XP recovery disk.

I'd be grateful for any advice as I'm a bit stuck.

---

### Post by ajgreeny on 2015-01-29
First thing is probably to restore the WinXP bootloader which you can do with a live Lubuntu system.

Boot to your live system, open a terminal and run
```
sudo apt-get install lilo
```
Ignore the warning which you will probably see then run
```
sudo lilo -M  /dev/sda mbr
```
That will install a basic windows bootloader to the first disk (sda) and allow you to delete the Lubuntu partitions, which you can best do with gparted from the live system, which will show you much more info than windows.

Having got some unallocated space, leave it that way, and install Lubuntu again, but choose "Something Else" at partitioning stage and use the unallocated space to add the Lubuntu partitions.

---

### Post by TheBigBean on 2015-01-29
Thank you very much for your help. 

I think fixing the Win XP bootloader would be a good start. Do you think the method you outline would be more reliable than downloading a bootsect.exe from somewhere on the internet and trying to fix it throught windows? I'm a little apprehensive at the moment about using Linux to fix Windows. I've also found mention of OS-Uninstaller ( [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller) ) which is another way to do it from a live Ubuntu system - do you have any experience of this?

---

### Post by sudodus on 2015-01-29
Please specify your computer

- (We know the brand name and model: IBM X31)
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier to give relevant advice. Maybe the most important data here is the RAM size.

Please try the *current* version of ***Lubuntu, 14.04.1 LTS***, or another distro or re-spin based on Ubuntu ***12.04 LTS***, for example ***Bento, Bodhi ***or*** LXLE***. If these do not work well, try an ultra-light distro, for example ***Wary Puppy, TahrPup ***or*** Tiny Core***.

See these links
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL] 				
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.[/URL]

---

### Post by TheBigBean on 2015-01-29
> **sudodus said:**
> 

Please try the *current* version of ***Lubuntu, 14.04.1 LTS***, [.]("http://ubuntuforums.org/showthread.php?t=2229730")

As stated in my original post I fully intend to do this when I have sorted out my current mess. The purpose of my post was to establish the best way to remove current installations, so that I could do that. I even gave the post a suitable title which for some reason was changed to something irrelevant.

I have since found this really useful thread which outlines a number of options. I'm still not clear which is the best approach for XP, but I'm confident that it is not going to be influenced by my graphics or wifi card.

[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

I don't expect anyone to read my post in full, but if someone is going to muster the energy to reply it is surely more beneficial for all to have done so.

---

### Post by ajgreeny on 2015-01-29
Sorry but I can't help with any other way to get your XP bootloader back, as the lilo way I showed is the only way I know of if you have no WinXP install disk.

Alternatively you could just install Lubuntu 14.04, assuming that your machine has spec enough to run it (see sudodus's post above) but use the "Something Else" option at partitioning, as I said before, and install into that empty space you should have having deleted the old Lubuntu partition(s).

---

### Post by mörgæs on 2015-01-30
I changed the title because the computer itself is the matter here. 

As you have noticed your Pentium M does not digest a new Buntu without modifications which mislead you to install 10.04. A better solution would be installing Lubuntu 14.04.1 or 14.10 using the *forcepae *option. 

As others have mentioned: First delete all Buntu partitions from a live boot and then you can install in the free space.

---

### Post by TheBigBean on 2015-01-30
> **ajgreeny said:**
> Sorry but I can't help with any other way to get your XP bootloader back, as the lilo way I showed is the only way I know of if you have no WinXP install disk.

Alternatively you could just install Lubuntu 14.04, assuming that your machine has spec enough to run it (see sudodus's post above) but use the "Something Else" option at partitioning, as I said before, and install into that empty space you should have having deleted the old Lubuntu partition(s).

Many thanks for your help on this. It is now all sorted.

I managed to restore the bootloader using the Bootsect.exe from the very useful link I posted earlier. I can't imagine anyone will come across this thread, but just in case they do I needed the option "/nt52" for XP. I have no doubt your method would also have done the trick, but I'm still not completely comfortable changing Windows things in Lubuntu.

After that it was all very easy to repartition and install Lubuntu 14.04. The "Something Else" option is a bit too involved for an absolute beginner, but it seemed to work ok just using the side by side installation. If I like using Lubuntu I think I will do some more reading about setting up the partitions - it seems it is a good idea to have the home directory on a separate partition, but that is for another day.

Anyway, I now have a dual boot Lubuntu and XP working, so I think my X31 may live on for a few years more yet.

Thanks again for your help.

---

### Post by ajgreeny on 2015-01-30
Great!

Can you go to the **Thread Tools** menu at the top and mark this as SOLVED, please.

---

### Post by TheBigBean on 2015-01-30
Certainly, sir. Done.

---

