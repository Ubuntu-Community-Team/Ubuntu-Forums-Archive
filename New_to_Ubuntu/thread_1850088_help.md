---
title: "help?"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by Inlerah on 2011-09-25
Im new at this whole thing, so i'll try to explain my problem as best as i can.

I just recentally installed a dual boot of Ubuntu 11.04 and Vista. For about an hour everything was working fine and now none of the applications start up except for a few (terminal and control center are the only ones iv seen start up as of late). Can anyone tell me what I didwrong and any way I could fix it?

---

### Post by Captain Smiley Pants on 2011-09-25
Are you getting any error messages saying there are multiple instances of an application running? You can double check processes by going through System -> Administration -> System Monitor.

Have you tried rebooting the computer to see if the issue clears up? Perhaps after installing and installing the latest updates it needs to perform an reboot to complete it's installation process.

Any out of the ordinary error messages coming up lately?

Just wondering what else we can get out of this. There could be a multitude of issues but if we can narrow down a few questions that cuts down the possibilities. Thanks!

---

### Post by jockyburns on 2011-09-25
> **Captain Smiley Pants said:**
> Are you getting any error messages saying there are multiple instances of an application running? You can double check processes by going through System -> Administration -> System Monitor.



Where does one find this  "System/Administration/system monitor" on 11.04? I'm damned if I can find it. :confused::confused:

---

### Post by Captain Smiley Pants on 2011-09-25
My mistake, I'm Old Man Smithers and still running 10.04.

I'm not sure what the equivalent would be unless you logged into Ubuntu Classic (if that's an option from what I can tell), could someone else point this out please?

---

### Post by alegomaster on 2011-09-25
> **jockyburns said:**
> Where does one find this  "System/Administration/system monitor" on 11.04? I'm damned if I can find it. :confused::confused:

Try to reboot the computer first and then report back.

---

### Post by alegomaster on 2011-09-25
> **Captain Smiley Pants said:**
> My mistake, I'm Old Man Smithers and still running 10.04.

I'm not sure what the equivalent would be unless you logged into Ubuntu Classic (if that's an option from what I can tell), could someone else point this out please?

I could probably point it out if I could use my ubuntu computer. I think I know where it is, but I am not sure.

grrrr Unity

---

### Post by Frogs Hair on 2011-09-25
Select the icon on the top left and start typing system monitor and the icon will appear .

---

### Post by jockyburns on 2011-09-25
Tried rebooting, but I can't find anything that remotely looks like System/Administration /

If I click the start button (top right hand of screen. I get an option there for System Settings, but there's no Administration section in there at all. I wonder if 11.04 doesn't have the Admin bits on the user interface??

EDIT,, I can find the System Monitor, under my method above, in system. I assume I'm already logged in as system administrator .

---

### Post by Captain Smiley Pants on 2011-09-25
No worries, it should. It's just the fantastic new Unity interface isn't very... Eh I'll save that discussion for a different thread.

As stated above, try typing it in System Monitor to get to it.

And since you've rebooted, has the problem been persistent?

---

### Post by Inlerah on 2011-09-25
Ok, heres a little more
when i restarted it, a message came up in the top left corner that said "Install Problem! The configuration defaults for GNOME Power Manager have not been installed correctly". Also, as of restart, i can't log into my account.

I am, though, able to log into my normal Vista account; if that sheds light upon anything

---

### Post by alegomaster on 2011-09-25
It sounds like a large scale file corruption. I have no clue how, but that is my idea.

I suggest reinstalling ubuntu again. It is also a good idea to check the md5 sum with the one on the ubuntu website.

---

### Post by westie457 on 2011-09-25
If it is large scale file corruption then a clean reinstall will clear the issues however reinstalling is usually the last resort.

To the OP
Can you boot into the Live Desktop using whatever you used for the install, ie a LiveCD/USB. When that is running go to Disk Utility, select the partition and the option to check the File-system for errors. When that has finished reboot and check by opening a few apps to see if the problem has been resolved.

If not run these commands in a terminal ```
sudo apt-get install -f
``` If that has problems you should be prompted to run ```
sudo dpkg --configure -a
```

Those commands should sort your system to a usable state. If not post the exact error messages here for further suggestions

---

### Post by alegomaster on 2011-09-25
> **westie457 said:**
> If it is large scale file corruption then a clean reinstall will clear the issues however reinstalling is usually the last resort.


Reinstalling is so easy to do, I do it anytime i severely mess up ubuntu(which is every other week.

---

### Post by mörgæs on 2011-09-25
> **alegomaster said:**
> It sounds like a large scale file corruption. I have no clue how, but that is my idea.


Please only give advice, if you are sure what you are doing. A bad advice can be worse than nothing.

---

