---
title: "[SOLVED] Boot up Prompt"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Whispering on 2008-08-31
I am BRAND new to this so bear with me ;)

I recently install Ubunto, and when i selected it to boot up, it worked fine, the Ubunto loading screen came up, but then a command screen came up, and I had no idea what to do. It said type help for a list of commands, but that didn't help because i had no idea what the commands meant.
I have never successfully loaded Ubuntu if that helps?
Please help me get it working!

Thanks for any answer :)

---

### Post by jemate18 on 2008-08-31
> **Whispering said:**
> I am BRAND new to this so bear with me ;)

I recently install Ubunto, and when i selected it to boot up, it worked fine, the Ubunto loading screen came up, but then a command screen came up, and I had no idea what to do. It said type help for a list of commands, but that didn't help because i had no idea what the commands meant.
I have never successfully loaded Ubuntu if that helps?
Please help me get it working!

Thanks for any answer :)

Oh  what version did you download? was it DEsktop Ubuntu 8.04? 
DId you encountered any error in the installation?

Mark this thread SOLVED if you are able to do what you intend to do and DONT FORGET to THANK the people who HELPED YOU by clicking the "thanks" button

Hope this helps.

jemate18

---

### Post by prshah on 2008-08-31
> **Whispering said:**
> 
 but then a command screen came up, and I had no idea what to do. It said type help for a list of commands, 

The command screen, did it contain the words "BusyBox" and/or "(initramfs)"? In this case, ubuntu's never loaded up, you should probably check the CD, or burn another at a lower speed.

On the other hand, if the "command screen" shows a prompt such as "ubuntu@ubuntu ~$", then type ```
startx
``` to start the graphical interface. This will most likely return an error; posting the details of the error(s) returned will give us clues to further troubleshooting.

Post back if you need more information.

If this is not your problem, can you either post a screenshot of the "command screen" and/or mention what is on it? Eg, what prompt do you get?

---

### Post by Whispering on 2008-08-31
> The command screen, did it contain the words "BusyBox" and/or "(initramfs)"?
Yes it did, both of them.

> Oh what version did you download? was it DEsktop Ubuntu 8.04?
DId you encountered any error in the installation?
Desktop version 8.04 is the one ;)
And there was no error, I just didnt know what to do
The installation was perfect and I got the Ububntu loading screen when rebooting, but the prompt... confused me lol. :)

---

### Post by Daveski on 2008-08-31
This can happen if the CD you installed from has an error. Best to check the CD and/or burn a new one at a slow speed.
Failing that, this could be a symptom of a hardware problem (like a failing disk), or the fact that the installed OS is somehow not able to read the main boot partition - there is a potential workaround you can try:

Press **F6** at the boot up screen.
You should see a line ending with *"--quiet splash."*
Delete --quiet splash, add the option **noapic** after **ro** so you have **ro noapic**

Hit enter to boot.

If this does not work, try **all_generic_ide** instead of **noapic**

See these threads:
[http://ubuntuforums.org/showthread.php?t=854618](http://ubuntuforums.org/showthread.php?t=854618)
[http://ubuntuforums.org/showthread.php?t=844288](http://ubuntuforums.org/showthread.php?t=844288)

---

### Post by Whispering on 2008-08-31
At which part of the boot up screen? Sorry lol.
Im new. Really new. (:

---

### Post by jemate18 on 2008-08-31
> **Whispering said:**
> At which part of the boot up screen? Sorry lol.
Im new. Really new. (:

Most probably the error is caused by the installer.

Before installing Ubuntu, you should verify if the CD you have downloaded has error. You can check cd for defects when you boot your installer.

If your installer has defects, just download a new one and burn at a lower speed.

Another possible error is hard disk problem. I have encountered this error 3 months ago with and then I have detected the problem to be my hard disk.

________________________
Mark this thread SOLVED
"https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads" if you are
able to do what you intend to do and DONT FORGET to THANK the people
who HELPED YOU by clicking the "thanks" button on the lower right
"medal icon" for their help and useful post

jemate18

---

### Post by Whispering on 2008-09-01
I uninstalled it, and re installed it, and now it works fine :)
Thanks!

---

### Post by Daveski on 2008-09-01
> **Whispering said:**
> At which part of the boot up screen? Sorry lol.
Im new. Really new. (:

Glad you have it fixed - but for ref, the part where it pauses to ask what to boot (this is the Grub screen). Here you can make changes like those I mentioned in my last post.

---

