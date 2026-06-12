---
title: "lxkeymap setting disappears upon reboot. How to make a change and keep it?"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by currang2 on 2013-03-31
This is first time I have used Lubuntu (or Linux). I have just installed on a MSI Wind U100.

Perhaps I selected incorrect keyboard option during install. The computer types " when I press the @ button.

I have tried Preferences / Keyboard and mouse / gone into lxkeymap and selected the "English US with euro on 5".

That corrects the problem during the remainder of the session and @ types as @.

I haven't been able to save that setting or to find a different way of changing the default system setting. The problem returns after restarting the computer.

Any pointers would be welcome.

I suspect it might require a command line command, but I am expecting that the UI should let me change the keyboard setting permanently and I am just too green to have found the key.

---

### Post by Rex Bouwense on 2013-03-31
At the bottom of the lxkeymap is a little box with apply written on it.  Did you click on that?  What was the the default before you tried to change it?

---

### Post by currang2 on 2013-03-31
I keep pressing the apply button.

I am not sure what the default mapping is.

On the "Input Device Preferences" dialog / Keyboard tab, the (bold) words "Keyboard layout" are followed by a blank and then the lxkeymap button. I half expected to see the name of the keyboard layout there.

When I enter the lxkeymap dialog, "United Kingdom" is highlighted in the left column, but nothing in the right column.

If I press the redo button, the bottom of the dialog reads "Current Keymap: ["gb"]".

I haven't gone into tools to create a new profile. I don't know whether that would help, but didn't think it would.

There is no save button. All I do is close the dialog and start working.

---

### Post by Rex Bouwense on 2013-03-31
The left column indicates that You chose United Kingdom as your default keyboard layout.  If that is the one you wanted you are good to go.  If you wanted United States you need to change it.  The column on the right appear to be variations of the keyboard for that country.  After you apply, the computer should automatically change to that keyboard.

---

### Post by currang2 on 2013-04-01
Thanks Rex.

That's what I hoped would happen, but after I restart the computer it reverts back to the UK keyboard mapping.

There is probably something really fundamental that I am missing, but I can't see it!

---

### Post by currang2 on 2013-04-01
Is there some sort of command line command I should be typing to save the modified boot/config file?

---

### Post by currang2 on 2013-04-01
Aha! Rummaging around a bit more on Google I found reference to command line change of the keyboard. sudo dpkg-reconfigure keyboard-configuration did the trick, although it was perplexing trying to guess which keyboard I should call up.

Anyway, it seems to be working now, upon rebooting, so I can rest easy.

Once again, thanks for your help, I do appreciate the effort.

---

### Post by vatbier on 2013-05-12
In Lubuntu 13.04 "sudo dpkg-reconfigure keyboard-configuration" does not keep the chosen keyboard layout remembered for me.
I had to put "@lxkeymap --autostart" in /home/vatbier/.config/lxsession/Lubuntu/autostart (putting it in /etc/xdg/lxsession/Lubuntu/autostart doesn't work if you already got an autostart file in your home directory .config/lxsession/Lubuntu)

---

### Post by PjhNs on 2014-04-26
I've had a similar problem I'd love some assistance with; after a fresh install of Lubuntu 14.04, I had to use ```
setxkbmap -layout gb
``` in the terminal after every boot, as the keyboard layout would always default back to US. 

After some Googling and trial-and-error I adapted [this advice]("http://askubuntu.com/questions/446835/why-does-this-command-doesnt-run-at-startup") and tried```
gsettings set org.gnome.desktop.input-sources xkb-options "['-layout gb']"
``` and I thought this solved the problem... it certainly did what I wanted after one restart and I genuinely thought I'd fixed it. HOWEVER, after a second restart my keyboard's defaulted back to US layout. Disappointing and confusing! Any tips? I really thought I'd fixed it! :(

p.s. Sorry if anyone considers this thread-necroing!

---

### Post by Darren_Jones on 2014-09-19
Just in case anyone else finds the previous post and has the same issue with 14.04, you need to remove the ibus packages for the GB keyboard setting to stick (and others). 
[https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1284635](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1284635)

---

