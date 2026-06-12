---
title: "Purple screen of death"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by Ben macgillivray on 2013-02-24
Please help! I'm very new to this Linux stuff and am having real problems. I have installed Ubuntu 12.04 LTS on my Zotac Zbox, but when I restart the computer I just get the purple splash screen and it goes no further. The install was completed and if I reinstall, it tell me there is an OS there already. I have tried the nomodeset fix on the F6 menu, which allowed me to complete the install, but still can't load from hard drive. I have also tried holding shift and editing the text to replace 'quiet splash' with no mode set and hitting ctrl x, but then it just says I will be operating in reduced graphics mode, which then sometimes results in a black screen login menu, sometimes an screen of death. The black screen login menu accepts my details, but then goes no further. It just won't load the actual desktop software. I'm really sick of this now, please help!!

---

### Post by matt_symes on 2013-02-24
Hi

Try booting into recovery mode from the grub menu. Can you get to a desktop from there ?

Kind regards

---

### Post by howefield on 2013-02-24
What make/model of graphics card do you have in your machine ?

---

### Post by Ben macgillivray on 2013-02-24
Hi, thanks for quick replies. Booting in recovery mode gives me the recovery menu, tried selecting resume normal boot, didn't work. Where should I go from the recovery menu?

It's an intel atom d4/5 series processor with integrated graphics core(intel GMA) does that help?

---

### Post by matt_symes on 2013-02-24
Hi

You want to choose the "drop to a root shell" option. If you can get there then it just means you have graphics cards, X or lightdm problems.

At the root console you may be able to do some things to fix it check as see log files.

Kind regards

---

### Post by Ben macgillivray on 2013-02-24
This brings up a bar at the bottom with root@(my name)-zboxsd-id12-id13:~#

---

### Post by matt_symes on 2013-02-24
Hi

That's good. Let's edit your grub file with nomodeset as you had to use that to install it.

```
sudo nano /etc/default/grub
```Look for the line that says

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```and change to 

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```Ctrl + 0 to save and ctrl + x to exit

Then type 

```
sudo update-grub
```That will update grub

then

```
sudo apt-get install pastebinit
``````
cat /var/log/Xorg.0.log | pastebinit
```Post the link back here to the paste bin. It is one of your log file for you x server.

Kind regards

---

### Post by Ben macgillivray on 2013-02-24
Sorry, I was with you until the Ctrl 0 then Ctrl x bit, it's now asking for:

File name to write: /etc/default/grub

With a flashing cursor

---

### Post by matt_symes on 2013-02-24
Hi

It's control o and not zero. The legend is displayed at the bottom of nano You did use the sudo command to open the file ? If not you will not be able to save it.

After sending the log file (the pastebin part), reboot and see how you get on using the no modeset switch.

Kind regards

---

### Post by Ben macgillivray on 2013-02-24
I still get the file name to write thing, is it as simple as hitting enter then running update grub?

---

### Post by howefield on 2013-02-24
> **Ben macgillivray said:**
> ...is it as simple as hitting enter...

Yes. Then Ctl + x

---

### Post by matt_symes on 2013-02-24
Hi

If your having trouble with nano, let's do it a different way. Close nano (ctrl x) and type

```
sudo sed -i 's/quiet splash/nomodeset/g' /etc/default/grub
``````
sudo update-grub
```

Then continue with the pastebin part

Kind regards

---

### Post by Ben macgillivray on 2013-02-24
Ok, managed to get the default grub changed as you said, it now opens a page with the " you are running in low graphics mode window. Help!

---

### Post by matt_symes on 2013-02-24
Hi

Well that's a step forward :)

Now your log files please.

```
cat /var/log/xorg.0.log | pastebinit
```

Kind regards

---

### Post by Ben macgillivray on 2013-02-24
Unable to locate package pastebinit

---

### Post by matt_symes on 2013-02-24
Hi

```
sudo apt-get install pastebinit
```and then run the command i posted above.

You'll get a link like this

```
matthew-S206:/var/lib/dpkg % cat /var/log/Xorg.0.log | pastebinit      
[COLOR=Red]http://paste.ubuntu.com/5561689/[/COLOR]
matthew-S206:/var/lib/dpkg %
```

Post the link into your next post.

Kind regards

---

### Post by Ben macgillivray on 2013-02-24
I may be being really dense here but when I type: sudo apt-get install pastebinit

It says:

Reading package lists... Done
Building dependency tree
Reading state information...done
E: unable to locate package postbinit

If I then type: cat /var/log/Xorg.0.log 
 It says: fatal error 8.804] no screens found
8.804] (EE)

---

### Post by matt_symes on 2013-02-24
Hi

```
E: unable to locate package postbinit

```

It's pastebinit not postbinit.

Kind regards

---

### Post by Ben macgillivray on 2013-02-24
Apologies, it is pastebinit I've been typing in.

---

### Post by matt_symes on 2013-02-24
Hi

Maybe a ppa or other source is required for pastebinit then. I can't remember.

Alright open it in gedit and copy and paste it into your next post

```
gedit /etc/apt/sources.list
```

I'll take a look (along with others) here.

Kind regards

---

### Post by Ben macgillivray on 2013-02-24
I can't copy and paste as the computer I'm trying to boot won't do anything, so I'm on another device here, is it ok to just write what it says?

---

### Post by Ben macgillivray on 2013-02-24
I can't copy and paste, I can't boot anything on that computer, I'm using another device to chat here, is it ok to just tell you what it says?

---

### Post by matt_symes on 2013-02-24
Hi

Oh right. I though it booted you to low graphics mode. 

Whats the exact state of the computer at the moment please. I am making assumptions that may not be valid you see.

This will be much harder if we cannot look at your log file.

Take a look at this about pastebinit. It may help and we may be able to go back down that route.

[https://help.ubuntu.com/community/Pastebinit](https://help.ubuntu.com/community/Pastebinit)

Kind regards

---

### Post by Ben macgillivray on 2013-02-24
Initial install goes fine, but the computer won't boot. If I try in safe mode or with the no mode set grub, it says it is operating in low graphics mode, but any time I try to use any of the low graphics mode options, it pushes me back to a DOS style black screen root.

---

### Post by matt_symes on 2013-02-24
Hi

I see. That sounds like X crashing. 

What was the make and model of your graphics card again ?

```
lspci -nnk | grep -iA3 vga
```

^^ case sensitive so captial A

Kind regards

---

### Post by Ben macgillivray on 2013-02-24
It's an intel atom d4/5 series processor with integrated graphics core(intel GMA) does that help

---

### Post by matt_symes on 2013-02-24
Hi

Can you run this command and post the results back here.

```
lspci -nnk | grep -iA3 vga
``` ^^ case sensitive so captial A

EDIT: Just been reading up on your card family and they have been problematic. Not sure of there current state though

Kind regards

---

### Post by Ben macgillivray on 2013-02-24
This is probably a stupid question, but what is that line in the middle, it's not a character I recognise

---

### Post by Ben macgillivray on 2013-02-24
If I input the first half it says

Kernel driver in use: ath9k

Any help?

---

### Post by Ben macgillivray on 2013-02-24
When I do the gedit, the response is

Auto launch error: X11 initialisation failed.\n
Cannot open display:

---

### Post by matt_symes on 2013-02-24
Hi

That character is the pipe character. It should be on your keyboard somewhere. 

I really do need the output of that command if i am going to be able to help you as the driver you posted was for a wireless card.

If you want an easier command there's this one

```
sudo lshw -c display
```

but if you can do the other one 5then that will tell me the vendor and device id and that's kind of what i am trying to find out.

I'm trying to find the exact make and model of you card and what driver the system is using.

Kind regards

---

### Post by Ben macgillivray on 2013-02-24
Intel corporation N10 family integrated graphics controller

---

### Post by Ben macgillivray on 2013-02-24
Kernel modules: i915

---

### Post by matt_symes on 2013-02-24
Hi

> **Ben macgillivray said:**
> Kernel modules: i915

Well you have the correct driver i believe. It may be the driver crashing or it may be X. 

But i have just read that...

> All versions since 2.15 of the Intel-driver only support KMS. If you've  deactivated KMS e.g. by adding the option "i915.modeset=0" to the file  "/etc/default/grub", please reactivate KMS by deleting this option.


source => [https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

You could try a newer driver from the above ppa or the xedgers/drivers ppa. I can talk you though that if you want.

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

For a start though, disable nomodeset grub option and try hitting the back light button when Ubuntu has booted. A number of people found that was a solution and it's worth a try.

Ideally i need the log files because until then i am just guessing and suggesting different options.

If you have an external monitor, try plugging into that. Do you get a picture ?

Kind regards

---

