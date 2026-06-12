---
title: "switch installation from 32 to 64 bit"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by mmcl26554 on 2012-11-21
I am truly an absolute beginner, but learning!
When I installed Ubuntu 12.10, I didn't pay attention to whether it was installing the 32 or 64 bit versions.  My laptop is 64 bit. I ended up with the 32 bit version installed on my 64 bit laptop.  It is working fine.  should I / can I install the 64 bit version and not lose the settings and programs I have installed.
Michael

---

### Post by wildmanne39 on 2012-11-22
Hi, I recommend 64 bit but you would have to back up your important data and install 64 bit you can not just upgrade.
Thanks

---

### Post by LuisGMarine on 2012-11-22
As far as I know, you can't update your 32-bit Ubuntu to 64-bit Ubuntu without doing a fresh install.  The simple answer is that things can get messy between 32-bit and 64-bit libraries.  

If everything is working fine I would just leave it as is until you get better used to the system, and Ubuntu as a whole.  Personally for the stuff that I do on my computer, I don't notice any huge performace gains from 32-bit Ubuntu as opposed to 64-bit Ubuntu.  Again that will depend on what kind of tasks you are doing with your machine.

Then again I'm sure if you start a technical debate, people will each tell you different.

---

### Post by DuckHook on 2012-11-22
> **LuisGMarine said:**
> As far as I know, you can't update your 32-bit Ubuntu to 64-bit Ubuntu without doing a fresh install.  The simple answer is that things can get messy between 32-bit and 64-bit libraries.

I successfully "converted" a 32-bit to a 64-bit, but it is frankly more trouble than it's worth. As you note, the OS has to be a clean virgin install. What most users are interested in doing is keeping their programs, settings, configs, and personalizations. You do this basically by piping a dpkg inventory to a file before installing, then replacing the dpkg database with the file after the install and forcing dpkg to resync to its database. Theoretically, dpkg then downloads all of its "missing" apps. Sounds better in theory than works in actual practice and leaves so many broken packages and half-completed installations that it's really not worth the trouble. Far easier to just make a manual inventory of your programs, back up your mail, data, etc. and then install all of the proper 64-bit apps.

> Then again I'm sure if you start a technical debate, people will each tell you different.

I'm one who would tell you different.:)

Because of what I've already explained above, it just gets harder and harder to make the conversion as you accumulate more and more apps, configs and personalizations. The time to take on the unpleasant task is when you still have a relatively generic system. Unless one is willing to just live with a 32-bit system, it will only get more customized and complicated as time goes by. My recommendation is to bite the bullet now and convert. The future of all OSes is 64-bit, and it makes little sense to stay with 32-bit unless your processor is only 32-bit.

---

### Post by Paqman on 2012-11-22
> **DuckHook said:**
>  My recommendation is to bite the bullet now and convert.

If your current system is working fine I would wait until a new version comes out that you were considering upgrading to anyway, then just do a clean install using the 64-bit instead.

I'm a big fan of 64-bit, but I don't think it's necessarily worth reinstalling just to use it unless you do a lot of number crunching, video re-encoding, etc.

---

### Post by DuckHook on 2012-11-22
As I said, it depends on the OP's current situation. In my case, I did as you suggested: waited on my main machine from 10.04 to 12.04, on the theory that I could avoid the pain until I was going to go through some pain anyway. What I didn't factor in was how much critical stuff I would accumulate in the interim. The biggest headache was VirtualBox and the numerous Windows VMs I had by then installed, each DRMed to their unique UUID. Trying to keep the old VMs was the primary reason I tried to "convert" rather than just do a clean and virgin install. I got it to work but only after way too much time and effort.

If the OP is in the same boat I was, then you are right: it's already too late and s/he should just wait for a natural point of upgrade. However, if the "conversion" at this time involves just e-mail and a few themes and tweaks, then it's not too painful to make the conversion now, as it will only get more painful later.

---

### Post by mmcl26554 on 2012-11-22
Thanks for the information.   I'm just starting out and I don't have many programs into Ubuntu.  Just Opera & keepass2.  Mostly I asked the question to see if it might be easy to change.  Since it's not then for me a clean install is the thing to do.  I can use the experience of finding things and setting up Ubuntu again.  Again thanks for the reply's and everyone's willingness to help
Michael

---

### Post by CaptainMark on 2012-11-22
seen as you said its a laptop it probably doesnt have more than 4gb of ram so you wont notice a performance boost by going for 64 bit, i would sit tight until the next release and just reinstall then

---

### Post by mmcl26554 on 2012-11-22
You're right there is 4Gb of RAM.  However, the kind of computing I do just doesn't require much (Internet and word processing, no games or big time graphics only circuit board graphics.  I have another hard drive which has my main win7 on it and I use this drive for experimentation, so if I mess things up it won't be a problem.   I have begun installing Ubuntu on that one and did get the 64 bit version, I really see no difference in speed.   On thing I find interesting is this:  HP installed a new Motherboard under warranty because the USB ports had become so loose the plugs would fall out.  Since the ports on the left side are part of the MB they had to replace.  The port on the right is not part of the MB (good idea).   Anyway, after I got it back it would shutdown on its own, "Abruptly" (no power down just like you pulled the plug). When I'm running Ubuntu it doesn't shut down.  HP will replace the MB again but they won't do it in my home so I have to send it in albeit on their $$$. So I am very happy with the performance of Ubuntu!
Michael

---

