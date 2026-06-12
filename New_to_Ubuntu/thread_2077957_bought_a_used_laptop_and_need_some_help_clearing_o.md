---
title: "bought a used laptop and need some help clearing out the grub loader"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by dylanZ on 2012-10-29
Hey guys, new here and need some Ubuntu related help.
I bought a laptop and I boot it up and there is around 5 versions of Ubuntu, a few memtests, and windows Vista and 7. I would like to dual-boot 7 and Ubuntu. I don't mind using Wubi. I guess I'm asking how to delete every OS on the grub except for 7. Please keep in mind that I am a complete Linux noob. 
Thank you for your time.

---

### Post by westie457 on 2012-10-29
Hi and welcome to the forum.

Before telling you how to delete an operating system and possibly hosing it away. We do not want to do that.

Are you able to boot into any of the Ubuntu OS's?

If so start any of them, open a Browser and go to here. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

When you have the bootinfo.txt file attach it to a new reply here by clicking on the paperclip at the top of the message pane.

The file will give us more than enough information to best advise you.

Thank you

---

### Post by dylanZ on 2012-10-29
Thank you for the warm welcome.
I cannot boot any of the Ubuntu OS's. It says that it cannot find a certain file. I'm not for sure which one, I'm on my phone now. I can get the missing file name if it would help.

---

### Post by westie457 on 2012-10-29
The name of that file would probably help. Once we sort that out we will more than likely hit the hurdle of the log in password.

We will take this one (small) step at a time.

Hope you are ready for a learning curve. From my point of view this will not be very easy for me however you might take to this like a duck to water.

I take it you are able to boot into one of the Windows installations which will be of use later.

---

### Post by dylanZ on 2012-10-29
I don't mind a challenge. I am not a complete computer noob so I'm not completely lost here. More of a code monkey though. The Vista OS is just some type of a backup/restore thing. I can boot into 7 just fine. I attached the pics of what Grub is showing. Oddly enough. I just tried to boot Ubuntu and it actually booted. The only problem is that I don't know the password for the Ubuntu account. I still want to whip the Ubuntus off and start fresh.

---

### Post by Vaphell on 2012-10-29
if you have a linux livecd/usb, boot it and run gparted to see the hdd configuration.
Linux stuff would occupy swap/extX partitions, windows would be NTFS/FAT. I think setting up fresh linux installation on top of existing ubuntu would do the trick (grub menu would be new).

During installation procedure you would have to select manual mode where you can get to the nitty gritty details. Explicitly assign swap to existing swap, root dir (/) to /.
Of course you can also wipe these existing linux partitions and split space according to your needs (separate /home? separate partition for user data?). Vista recovery probably can go away too, so you can expand useful partitions to occupy its space, but details will be known once you show 

After installation the system should scan partitions in search for OSes to create fresh grub menu for them.

---

### Post by dylanZ on 2012-10-29
The funny thing about this laptop(netbook) is that it doesn't have a CD drive and for some reason, I don't have an option to boot from USB.

---

### Post by twipley on 2012-10-29
If you bought an used laptop, the only way to ascertain that it is malware-free is to install stuff yourself.

If you are up to it, I would suggest installing 7 afresh, then doing the same with Ubuntu. Linux should always be installed after, though.

---

### Post by dylanZ on 2012-10-29
I would rather not have to buy/pirate Windows 7. It's looks like a pretty clean install though. Also for some reason I cannot boot from a USB.

---

### Post by Vaphell on 2012-10-29
> The funny thing about this laptop(netbook) is that it doesn't have a CD drive and for some reason, I don't have an option to boot from USB.

so how exactly did the previous owner install ubuntu? o.O
have you looked in bios? what Acer model is this?

> I would rather not have to buy/pirate Windows 7.
isn't that win7 pirated either way? ;-)
Vista recovery suggests that win7 doesn't belong to the native configuration (unless there was an upgrade allowed)

---

### Post by westie457 on 2012-10-29
Hooray for getting a Grub menu up, now we can progress.

Lets get a ubuntu up and running first. Take a look here [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Write down or print out the steps to change the password.

Once that is done you can go ahead and do the bootinfo script.

The main reason I am taking this in easy steps is this is strange territory for me. On the job training so to speak. All steps are tried before being suggested.

---

### Post by dylanZ on 2012-10-29
In the BIOS, there is only two options to boot from: Hard Drive and a network boot.
I can't speak for the previous owner but you're probably right. Now that I think about it, do you have to have a Live CD USB plugged in for the option to boot from it shows up?
Also it's an Acer Aspire One. I havem't really been able to find much on this model.

---

### Post by dylanZ on 2012-10-29
Success! I now have access to the Ubuntu. That wasn't bad at all. Now what do I need tl do exactly?

---

### Post by westie457 on 2012-10-29
Next is for you to follow the instructions in the first link posted for the bootinfoscript.

Once the information of what is where, we can come up with a plan to leave you with hopefully a hard drive containing the Vista recovery partition (for if you feel like going back to Vista), a working Win 7 and a fully upto date functioning Ubuntu installation.
In short a dual booting computer without going near a Wubi installation. FWIW a Wubi installation is usually for relatively short term testing.

---

### Post by dylanZ on 2012-10-29
Ok, sounds like a plan. I now need help finding my wifi to connect to it. I've looked for a tool to scan existing wireless networks but I've just found the tool to make a new wireless network. Got any ideas?
This is sad lol.
EDIT: nevermind. It's a dark icon and it was disabled.

---

### Post by westie457 on 2012-10-29
Go ahead and create a connection, it will either work right away or it won't.
If it does not work a cable would be preferable to installing drivers the hard way.

By the way, thanks for the challenge.

---

### Post by dylanZ on 2012-10-29
> **westie457 said:**
> Go ahead and create a connection, it will either work right away or it won't.
If it does not work a cable would be preferable to installing drivers the hard way.

By the way, thanks for the challenge.

Got it fixed. 
No thank you, it's a learning experience for both of us.
Downloading the script now.

---

### Post by westie457 on 2012-10-29
There was a better than even chance the wireless would work straight away because the previous owner had set everything up.

After all this we will probably find that you only have one Ubuntu installed and what you first thought was a bunch of OS's is only one and the list is all the installed kernels. Keeping fingers crossed.

---

### Post by dylanZ on 2012-10-29
> **westie457 said:**
> There was a better than even chance the wireless would work straight away because the previous owner had set everything up.

After all this we will probably find that you only have one Ubuntu installed and what you first thought was a bunch of OS's is only one and the list is all the installed kernels. Keeping fingers crossed.
That's actually what I am thinking now. who knows. I attached the results.txt after I figured out that when I was trying to run it, /Downloads is case sensitive. Bear with me.

---

### Post by westie457 on 2012-10-29
Just looked at the info, not really any thing to be done at the moment unless you want to remove some of the older kernels. Normally I would suggest upgrading to a newer version however because of the changes between what you have and the newer versions the thing will break.... badly.

Play with what you have for a couple of months, get used to Ubuntu. The version you have though old is supported until April of next year.

When you have any questions post a new thread, lots of people here are more than willing to help.

Enjoy the learning curve at your leisure.

One final thing, using 'Thread Tools' near the top of the page could you mark this as 'Solved' please.

Thank you

---

### Post by dylanZ on 2012-10-29
Thank you for all the help.

---

### Post by bogan on 2012-10-30
Hi!,** dylan**Z,

Re you not having a Bios option to boot from a USB:

It is quite common for USBs to be listed under HDDs, as external HDDs may be USB plugins

You will probably find, if you select HDD, that it includes any USB in a drop-dowm menu.

Select it and if there is an USB drive plugged in it will be listed by name.

It would have to be pretty old not to have the option.

Chao!, bogan.

---

