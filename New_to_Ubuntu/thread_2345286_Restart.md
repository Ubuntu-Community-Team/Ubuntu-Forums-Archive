---
title: "Restart?"
date: 2016-12-02
forum: New to Ubuntu
---

### Post by chunkydrew2 on 2016-12-02
I dual-boot Ubuntu 16.04 and Mint 18 on my Linux laptop. I sometimes want to switch quickly from one to the other without doing a full shutdown and restart. In Mint, the Restart option is offered. Is it possible to enable or do the same thing in Ubuntu?

---

### Post by RobGoss on 2016-12-02
I also use Mint I have never seen the option to switch between OS's unless you power down your machine completely and only using the grub menu.

Maybe someone else has better knowledge of this

---

### Post by #&amp;thj^% on 2016-12-02
> **RobGoss said:**
> I also use Mint I have never seen the option to switch between OS's unless you power down your machine completely and only using the grub menu.

Maybe someone else has better knowledge of this

+1:KS
This is not possible from a standard dual boot setup. You can put links on your desktop to reboot from one to another _but a reboot is required_. But I have never done the later...nor would I recommend it.
Just my 2 cents worth

---

### Post by chunkydrew2 on 2016-12-02
Maybe my question wasn't clear. I am not doing a full reboot, a la shutting down, then having to hit the power button to turn the laptop back on. When I choose restart in Mint, it does whatever housekeeping is needed, closes Mint,  then immediately brings up the GRUB menu. I don't have to touch the power button to bring up Ubuntu. That is what I'd like to do in Ubuntu, if possible.

Please pardon the question. What I wanted IS already available in Ubuntu. On the Shutdown screen, next to the Shutdown button, is Restart, which does the same as in Mint. It just isn't marked as such, so you don't know what it does until you click on it. Thanks for the responses.

---

### Post by deadflowr on 2016-12-02
try these two commands 
The first to add the restart button to Ubuntu settings menu (The menu in the top right corner of the top panel (looks like a cog wheel)
```
gsettings set com.canonical.indicator.session force-restart-menuitem true

```

then try this command to force ubuntu to not show it's shutdown popup window and log you out and restart automatically:
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```

Both of these options/setting can be found in the dconf graphical interface: dconf-editor, (needs to be installed)
but the locations are nutty.
(instead of being where you would expect them to be, they are located in apps >> indicator-session, and not the more obvious com >> canonical)

But basically in the graphical interface navigate to the apps > indicator-session window and set both the force-restart-menuitem and suppress-logout-restart-shutdown options to true.

I'm thinking that somewhat what you want.

---

### Post by #&amp;thj^% on 2016-12-02
> **chunkydrew2 said:**
> Please pardon the question. What I wanted IS already available in Ubuntu. On the Shutdown screen, next to the Shutdown button, is Restart, which does the same as in Mint. It just isn't marked as such, so you don't know what it does until you click on it. Thanks for the responses.

Thought that might be the case:) But it should highlight itself when you mouse over it.(More Noticeable)
And deadflowr has another good suggestion.
Cheers

---

### Post by deadflowr on 2016-12-02
Also, you can add the Reboot launcher to the launcher bar.
Open the dash and search Reboot, then drag it to the launcher bar.
That way you don't even need to go through the settings menu.

Of course, I assume this is unity, not sure how other desktop's can set that.

---

### Post by RobGoss on 2016-12-02
As **1fallen** pointed out when you hover over that menu are you able to see what it's labeled?

---

### Post by Geoffrey_Arndt on 2016-12-02
I wondered why the OP asked this question in the first place . . . as there are 3 or 4 ways (besides the standard shutdown icon in the panel) to restart (aka reboot) Ubuntu, and the "soft" shutdown (without use of power button) will always bring up the bootloader on a multi-OS system.   But - - it is still a restart, and not just a log-out and log-back in.     Essentially, the Mint and Ubuntu behaviours are the same.   OP was just a little lazy by not hovering over the pretty obvious button next to shutdown.

---

