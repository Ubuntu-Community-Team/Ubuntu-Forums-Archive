---
title: "Problem after installing proprietary drivers"
date: 2013-12-25
forum: New to Ubuntu
---

### Post by Greasyboi on 2013-12-25
After installing these ([http://i.imgur.com/pvXL2vc.png](http://i.imgur.com/pvXL2vc.png))  drivers, and rebooting my computer got stuck in a loop at boot up  saying - "asking for cache data failed ---  assuming data cahe: write through" over and over. I couldn't type  anything or open anything just a blank screen repeating the text. I then  had to reinstall ubuntu.
  The two choices on the top are the same and the two on the bottom are  the same. (At least the descriptions are the same). I don't know what  caused the problem and since this is my first time with ubuntu idk what  I'm doing. How do I prevent this from happening again? I would like to  play some games on steam but it prompts me to update the propietary  drivers and I'm not sure with one to use to update.
  Thanks guys!

---

### Post by deadflowr on 2013-12-25
I would install the 400 updates you have first.
Then look into the additional drivers again.

After you update, it might list better results.

---

### Post by zeljkojagust on 2013-12-26
"asking for cache data failed ---  assuming data cahe: write through" -> This usually means a USB stick/drive is connected to you computer. Please check if there are any, unplug it if there is and try again.

Related to nvidia drivers, after you have your Ubuntu up and running, open a terminal window and install them by entering the following command:
sudo apt-get install nvidia-current

---

### Post by Greasyboi on 2013-12-26
That's what I read but I have none connected! And I'll try that! I just installed the 400 updates. Didnt' realize what those were.

---

### Post by Greasyboi on 2013-12-26
After installing the 400 updates and using sudo apt-get nvidia-current, I've now got these showing up ([http://imgur.com/a/A9emS](http://imgur.com/a/A9emS)) Just differen't options. Steam still shows I have old drivers. Any advice?

---

### Post by deadflowr on 2013-12-26
It seems you have nvidia-173 installed, from what it looks like on the one screenie you posted that I can tell.
Do you know what card you have?
I think running
```
nvidia-smi
```
in the terminal should give you all the info you would need to figure that out.

The nvidia-173 drivers are older drivers.
Post what card it is, so we can advise whether you can install the newer drivers.

---

### Post by Greasyboi on 2013-12-27
Gpus found in probe:
Found Gpuid 0x2000
Attaching all probed Gpus...OK
Getting unit information...OK
Getting all static information..



Thats all that shows up -  it doesn't seem to be able to get the info though..

EDIT:

After some googling I figured out this is the GPU ---**NVIDIA GeForce 8200M**---

---

### Post by deadflowr on 2013-12-27
Take the recommended driver in the additional drivers.
I think it's marked as 319.
I believe those are the long term support drivers nvidia just put out last year.
Should be well supported for Steam.

---

### Post by Greasyboi on 2013-12-27
[http://imgur.com/bynvzm0](http://imgur.com/bynvzm0) shows up now.  Then continues to do asking for cache data failed assuming write through.  I can't do anything so it seems I'll have to reinstall again? I hope that isn't the case though

---

### Post by Greasyboi on 2013-12-27
It's been 6 hours of this screen and it repeats :[ It's so difficult to use Ubuntu.

---

### Post by Greasyboi on 2013-12-27
Update - My computer boots up to a black unlit screen now. No BIOS, nothing. I'm at a loss.

---

### Post by Greasyboi on 2013-12-27
again-update- After placing another HDD into the computer the screen still stay black. It seems a bigger problem has come up thanks to installing those drivers for the Nvidia graphics.

---

### Post by deadflowr on 2013-12-27
I don't see what the relation between the cache and the graphics card is, must be something.
It does seem, though that your card isn't workable with other drivers, though it is stated as supported on nvidia's site for the latest drivers.[http://www.nvidia.com/Download/driverResults.aspx/69371/en-us](http://www.nvidia.com/Download/driverResults.aspx/69371/en-us) (toggle the supported products tab to see the list of supported card)
Of course we could see to verify that that is the card
```
lspci | grep VGA
```
WILL give what card it is exactly.
At this point you'd have to run a livecd to look.
Or if you can boot into a console session(ctrl+alt+F1-6)
removing the drivers should put you back at point zero, using the open-source nouveau drivers.
Something in here might help on that
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Greasyboi on 2013-12-28
I can't even boot from a live CD. nothing shows up either

---

### Post by deadflowr on 2013-12-28
I don't know if you posted this earlier, but do you know the general specs of the machine.
Stuff like the brand name or something like that (something like hp pavilion something?)Desktop tower or laptop?

It seems to be a hardware issue.
I've never seen a driver cause the system to not load a bios screen, though I guess it's possible,maybe.
The bios loads way way before the driver does.

---

### Post by Greasyboi on 2013-12-28
Hey I appreciate your help so much. So I just got off work and I burned a new img to a new CD. I eventually got to the point where I could reinstall ubuntu completely so I'm back at square one :D Once again I appreciate your help! But I still don't know what drivers to install without bricking this computer!

---

### Post by deadflowr on 2013-12-28
At this point I'm as lost as you are.
We know the newer drivers make things go boom.
And the really old drivers are okay, but unsupported for the stuff you want to do.
I don't think it's a lost cause, though.
I'm hesitant to suggest maybe looking at installing the drivers directly from nvidia, maybe?
I mean,there has to be drivers somewhere that doesn't make things go belly up.

---

### Post by Greasyboi on 2013-12-29
Yeah true! I'll give the ones off the website a try. Is it possible Ubuntu could just be recommending the wrong ones?

---

### Post by crazypj10 on 2013-12-29
Are you getting any 'beep' codes from motherboard?
I removed memory to remove hard drives and fitted it back in the wrong positions (4 slots, 2 x 2Gb 'sticks')
Didn't get any beeps but had same problem, black screen, wouldn't boot

---

### Post by Greasyboi on 2013-12-30
No beep codes or nothing! But I've seemed to get it working!

---

