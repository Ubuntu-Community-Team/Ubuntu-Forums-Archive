---
title: "USB Install - booting to black/purple screen"
date: 2014-03-27
forum: New to Ubuntu
---

### Post by quadrplax on 2014-03-27
I used an Ubuntu live CD to install Ubuntu to two 16GB USB flash drives. They are both practically copies of each other. They were both insalled on my decent laptop. They both boot really fast on it, and the light that says things are happening (for lack of a better name) stays on, or flashes duing the boot time. I intend to use one with the laptop and one with another less-decent desktop. However, when I boot to the destop with either of the flash drives, I get a blank purple screen and the light turns off. After rebooting the system, I boot into grub, and if I chose normal boot, I get a black screen with a flashing _ in the top left (and the light goes off). Today, after "breaking" one (so it goes to grub), I booted the other one and tried waiting to see if anything would happen. I (I don't know why) plugging in another flash drive and pressing (not holding) the power button. Somehow, I wasn't paying too much attention to it but the light turned on, and after a delay(which is probably just because it's a bad computer), it progressed with the booting and sussessfully booted into Ubuntu. When I tried the "broken" one on the laptop, and selected normal boot in grub, it worked just fine like nothing had neer happened, and the light never turned off. I'm going to try tomorrow, see if another USB Drive and/or the power button affects things, or if that was coincidental timing, unless you tell me otherwise. Oh, and don't tell me to install to a Hard Drive or anything like that because I can't use the HDD on either computer.

---

### Post by PondPuppy on 2014-03-27
A little background info could possibly help. What version of Ubuntu (12.04, or 13.10, or something else)? 32- or 64-bit? When you say "bad computer" do you mean it's old, or just a little broken?

---

### Post by quadrplax on 2014-03-27
Ubuntu 12.04.4 LTS 32-bit
"bad" means old

---

### Post by pyrotheseus on 2014-03-28
You could always try re-installing Ubuntu on the flashdrives?

---

### Post by Bucky Ball on 2014-03-28
> **pyrotheseus said:**
> You could always try re-installing Ubuntu on the flashdrives?

Please read the last part of the original post. Ubuntu is booting fine from both USBs, so nothing wrong with the installs, but seems there are conditions to when they boot. A reinstall is generally the last option. ;)

@quadrplax: How did you create the USB installs? Also, please try and replicate a successful boot so you can tell us exactly what you do. (Hold the power button, plug in another USB? More detail thanks.)

---

### Post by quadrplax on 2014-03-28
I created the installs with a 2GB Fat32 Flash Drive. I just replicated a successful boot: Turn on computer, wait for purple screen, plug in another flash drive once light on first flash drive turns off (that magically turns it back on), and then I remove the secondary flash drive before it finishing booting. Also, if it helps the computer is a HP Compaq dc5800 Microtower

---

### Post by Bucky Ball on 2014-03-28
That ... is odd! Never seen that one. :-k

I meant how did you install Ubuntu to the flash drives? What app and OS did you use to do it?

---

### Post by quadrplax on 2014-03-28
Woah, speedy reply! I installed an Ubuntu "Live CD" to my 2GB flash drive via the pendrivelinux.com installer. Using this flash drive, I installed to both of the flash drives, one after the other, on the decent laptop, the same way you would install to a hard disk.

---

### Post by Bucky Ball on 2014-03-28
Ahh. I'm starting to see a glimmer of light. The USB you're plugging in to get it booting is not the one you cloned the other two from, by any chance?

I suggest you try a less exotic approach to install Ubuntu to the USB devices. 

[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/)

There's also the UNetbootin method:

[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

You leave a section of the USB as an empty storage partition. 

Are you using Windows or Ubuntu to create the Live USB installer USB? My feeling is that, even if it's not the installer you're sticking in, they're looking for their parent to tell them it's okay to play, perhaps.

---

### Post by quadrplax on 2014-03-28
The other USB is the other 16GB install (since that's the only other one I have with me), but aftter that one turns the light on on the first USB, I take it out and it boots fine.

---

### Post by Bucky Ball on 2014-03-28
I edited my last post.

---

### Post by quadrplax on 2014-03-28
Exotic? How is the pendrivelinux installer exotic? It's the official recommended way of making a bootable USB: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
I created the Live CD on a Windows 7 computer, and it has a 512MB persistant storage file. I'm not using the installer as the alternitive USB, I'm using the other nearly identical 16GB USB.
As I said, the 16GB installed copy of Ubuntu is where it acts weird, and only on that one computer. I think that the 2GB Live CD works perfectly fine, never had any installation issues.

---

### Post by quadrplax on 2014-03-31
Update: sorry for the delay, but today I tried booting to the desktop again. To my suprise, you were right about the second one having to be the other 16GB install, even the Live CD couldn't recover the drive! Also, out of curiosity, I tried unplugging and re-plugging the drive, and that didn't work. When it fails to boot, the next time it takes me to grub without having to do the USB thing, but I can't get a successful boot from there. I hope someone knows the solution, becase I don't want to have to take oth drives with me everywhere.

---

### Post by quadrplax on 2014-03-31
I just re-read you're post, the first meathod you suggested for installing Ubuntu is the way I did it. This gave me my 2GB Live CD. The other drive I am plugging in is not the one I cloned to the other 2 (16GB) drives, It's the other 16GB drive. In fact, plugging in the 2GB LiveCD, suprisingly, didn't work. Also, the 16GB sticks aren't really clones of the 2GB one, they are properly installed copies of Ubuntu.

---

### Post by quadrplax on 2014-04-01
I can't find anything about bumping in the Code of Conduct, so sorry if I shouldn't do this, but I don't think many people venture back to the 3rd page, so:
*BUMP*

---

### Post by Iowan on 2014-04-01
Like your other thread:
> **Iowan said:**
> That got moved to the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945")

---

### Post by quadrplax on 2014-04-01
Oh, sorry about that, didn't see posting guidelines. Well, I was only 4 hours early.

---

### Post by chileno35 on 2014-04-07
I have a HP Pavilion G6-1205sg notebook and sometimes after installing Ubuntu with the next restart my screen was purple and nothing happened.

My suggestion is to unplug the powercable and put the akku out of the notebook.... wait 20 seconds and then put the akku back and plug the power cable in. In my case it worked after this step.
It´s worth a try.

Hope it helps!!!

---

### Post by quadrplax on 2014-04-07
What is the akku? Ubuntu is installed on a flash drive, as my signature says. The computer I have trouble booting with is the desktop, the laptop works fine. It seems inconsistent, too. Today when I first tried to boot, the light turned off like usual, but before I plugged in the flash drive a few seconds later, The light turned back on on it's own. It never booted though, despite the light being on. I then chose regular boot from grub and put the other drive in immediately when the light turned off, and then it successfully booted.

---

### Post by Bucky Ball on 2014-04-08
> **quadrplax said:**
> Today when I first tried to boot, the light turned off like usual, but before I plugged in the flash drive a few seconds later, The light turned back on on it's own. It never booted though, despite the light being on. I then chose regular boot from grub and put the other drive in immediately when the light turned off, and then it successfully booted.

Does this mean your problem is solved?

---

### Post by quadrplax on 2014-04-08
No, because it never boots on it's own when the light comes on on its own, it hangs on the purple/black screen forever, as the original title says. I still require the second drive to boot it, which I would prefer not to have to do. I've put some useful information in my signature, and it's that desktop that this happens on.

---

### Post by chileno35 on 2014-04-11
> **quadrplax said:**
> What is the akku? Ubuntu is installed on a flash drive, as my signature says. The computer I have trouble booting with is the desktop, the laptop works fine. It seems inconsistent, too. Today when I first tried to boot, the light turned off like usual, but before I plugged in the flash drive a few seconds later, The light turned back on on it's own. It never booted though, despite the light being on. I then chose regular boot from grub and put the other drive in immediately when the light turned off, and then it successfully booted.

Ok. Sorry. Then i missunderstood you. :-) By the way, with "Akku" i mean the Notebook-battery... but never mind. :oops:

---

### Post by stalkingwolf on 2014-04-11
Did you install the live version to the flash drive or did you do a full system install?  Did you make the mistake i did several times and install grub to the wrong drive?  Have you tried the recovery mode and fix broken packages?
Usually when i do a full system install to a flash drive i unplug the main HDD.  That pervents me from commiting gross acts of stupid.

---

### Post by quadrplax on 2014-04-11
Recovery mode from GRUB returns an error and the light turns off as usual. As my signature states, the two flash drives are full installs of Ubuntu. How could you install grub to the wrong drive? As I said before, the boot sequence works perfectly fine on the EliteBook. Also, out of curiosity, today I tried booting to a HP ProBook 6560b, and it also worked perfectly fine. Also, not sure why this is happening, but every time I boot to Ubuntu now it shows grub, not just the times that I unplug the drive/turn off the computer while it's booting like it used to when I was trying to get it to work. I'm not sure why this is, data is saving and loading perfectly fine while I'm in Ubuntu.

EDIT: While I'm doing this on the ProBook, the light turns off for about 2 seconds, but then it comes back on and recovers. Also, I doubt this is any good information, but I'm trying to recover files off of a (really) old computer, a Packard Bell 945 with Windows 98, in order to convert it to a VM. It suprisingly can get all the way to grub. When I try to boot to any of the options in grub, it crashes to the bios.

---

### Post by 23dornot23d on 2014-04-14
Can you post a photograph of the two USBs plugged in when it works please.

I have an idea what it is - because I have a old computer that does something similar ..... but I need to
first see how you are connecting these USB drives to the computer. 

(  best if you can give one picture when it works / and / the other picture when you only have one plugged in ) 

> 
As I said before, the boot sequence works perfectly fine on the  EliteBook. Also, out of curiosity, today I tried booting to a HP ProBook  6560b, and it also worked perfectly fine. Also, not sure why this is  happening, but every time I boot to Ubuntu now it shows grub, not just  the times that I unplug the drive/turn off the computer while it's  booting like it used to when I was trying to get it to work. I'm not  sure why this is, data is saving and loading perfectly fine while I'm in  Ubuntu.


Then it may answer your questions .... especially since you have already said it works ok on 2 other computers.

---

### Post by quadrplax on 2014-04-14
I'm sorry, but I'm not capable of taking a picture of it, but here is a crummy diagram of the events in order:
[IMG]http://i.imgur.com/VRiG7hE.png[/IMG]

---

### Post by 23dornot23d on 2014-04-14
If the case of where it works is when two usb drives hold each other rigid and in place ......

Then it could be a faulty USB port .... or bad connection ... and what happens when the other USB is plugged into place
is that it either sits snug up against the other USB card and supports it such that the connection is better.

This results in no lost connection at any time during boot up ..... 

I have only got this on one of my own computers and it was found when using a connection to the internet
it was a USB cable and every now and then it would just stop ,,,,,, but once something else was plugged in below it
it was fine .......

Just with you saying its only happening on that one computer ...... and the others are fine ...... 

Just a thought and I think you said it was old ..... 

Something else to take a close look at ..... might be wrong but it does seem more likely to be something
happening on the hardware side - rather than the programs - if they work fine on other computers.

---

### Post by quadrplax on 2014-04-15
> two usb drives hold each other rigid and in place
There  is enough space between the USB ports that they don't touch each other.  Also, I don't think that would be the problem because it happens  consistently at one specific time during boot.
> it could be a faulty USB port .... or bad connection
It  happens on both of my 16GB USB's and it doesn't matter which port I  plug them into, it still happens. I've also tried it on other computers  of the exact same model and it still happens.
> I think you said it was old
See my signature.

---

### Post by quadrplax on 2014-04-24
Although my problem is not solved, I am going to close this thread. I will only be using this computer for 16 more days and therefore this is not worth the bother of trying to fix. Thank you all for trying to help.

---

