---
title: "Synaptic no longer launching..."
date: 2011-08-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-08-17
Trying to launch Synaptic from the launcher does not work as of some point today. I can run "gksu synaptic" from a command line, and that works. What's up with that?

---

### Post by drs305 on 2011-08-17
Just to clarify a few things.
You are using a launcher item in the left panel?  Have you tried deleting it and/or launching directly from Dash? (It could be a synaptic.desktop problem)

Do you get the Authentication window, or does it fail prior to that?

I have an updated 64-bit installation and am not having any problems with Synaptic.

---

### Post by sgage on 2011-08-17
> **drs305 said:**
> Just to clarify a few things.
You are using a launcher item in the left panel?  Have you tried deleting it and/or launching directly from Dash? (It could be a synaptic.desktop problem)

Do you get the Authentication window, or does it fail prior to that?

I have an updated 64-bit installation and am not having any problems with Synaptic.

Yes, a launcher in the left panel that has been working fine. I did try deleting, and then launching from Dash. Dash found it alright, but same symptoms:

Yes, I do get the authentication window. I type in my password, and nothing happens.

'gksu synaptic' from a terminal works fine.

The behavior is the same in both Unity and Gnome Shell.

I'm running a fully updated 32-bit system. Any ideas?

---

### Post by Gunss on 2011-08-17
Here I have 32bit fully updated system and I do not have this problem. I call synapitc from dash.

---

### Post by sgage on 2011-08-17
> **Gunss said:**
> Here I have 32bit fully updated system and I do not have this problem. I call synapitc from dash.

I must not be living right :KS

---

### Post by lucazade on 2011-08-17
I have this issue, from command line it works but not from the launcher.

---

### Post by mc4man on 2011-08-17
Also works fine here from various means, (normally a quicklist

What is a bit odd, (on a 08/15 install) is that while synaptic was to be switched to pkexec and does ship with a policykit file it still seems to use (gk)sudo
 - I see this because I use an older sudo and have a -1 timeout, synaptic never needs an auth password, if it was using pkexec it would require one each time opened
(have a .pkla ready for the switch but I guess not needed atm

What happens if you use - 
```
/usr/sbin/synaptic-pkexec
```

Edit:  just realized why from quicklist didn't require auth - using the old Exec=

---

### Post by lucazade on 2011-08-17
> **mc4man said:**
> Also works fine here from various means, (normally a quicklist

What is a bit odd, (on a 08/15 install) is that while synaptic was to be switched to pkexec and does ship with a policykit file it still seems to use (gk)sudo
 - I see this because I use an older sudo and have a -1 timeout, synaptic never needs an auth password, if it was using pkexec it would require one each time opened
(have a .pkla ready for the switch but I guess not needed atm

What happens if you use - 
```
/usr/sbin/synaptic-pkexec
```

Edit:  just realized why from quicklist didn't require auth - using the old Exec=

doesn't work here:
$ synaptic-pkexec 

(synaptic:3888): Gtk-WARNING **: cannot open display:

---

### Post by sgage on 2011-08-17
> **lucazade said:**
> doesn't work here:
$ synaptic-pkexec 

(synaptic:3888): Gtk-WARNING **: cannot open display:

Same thing here...

---

### Post by mc4man on 2011-08-17
Wierd - I'm up to date and works here - maybe some bug of sorts?

If desired you could for the moment adjust your synaptic.desktop back to previous or create a quicklist entry with Exec= of
```
gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
```

I did notice the other night when using gdm for a moment to add something lightdm wouldn't that /usr/sbin was not in the $PATH in gdm, but probably not relevant here. (and didn't seem to affect anything anyway

---

### Post by Harry33 on 2011-08-17
Hmm, the switch to pkexec did also change the authentication window when starting synaptic. It is black and it has a face-browser too.
That is with my 64-bit setup.

In my 32-bit setup, the authentication window has not changed.

However, synaptic works well with both my setups.

---

### Post by mc4man on 2011-08-17
Definitely a bug - just received the new synaptic
It was moved to /usr/bin (shell script) because /usr/sbin may not be in the $PATH for some as mentioned and now can't be opened w/ auth.
So if you revert or have it opened w/ gksu should work as long as /usr/sbin is in path

I believe the issue may be  that they didn't include /usr/share/polkit-1/actions/com/ubuntu.pkexec.synaptic.policy in the latest synaptic - adding it and synaptic now works fine

---

### Post by Harry33 on 2011-08-17
> **mc4man said:**
> Definitely a bug - just received the new synaptic
It was moved to /usr/bin (shell script) because /usr/sbin may not be in the $PATH for some as mentioned and now can't be opened w/ auth.
So if you revert or have it opened w/ gksu should work as long as /usr/sbin is in path

Are you talking about this version:
Synaptic 0.75.2ubuntu4
>  * debian/synaptic-pkexec: use /bin/sh, not /bin/bash.
  * debian/rules: install synaptic-pkexec wrapper to /usr/bin, not
    /usr/sbin as it may not be in the path. (LP: #824985, LP: #827878)
  * debian/patches/11_use-pkexec.dpatch: rename extra .patch from filename,
    remove superfluous line break in policy files.

It works fine here, as I also wrote above.

---

### Post by Gunss on 2011-08-17
Correction. I'd just updated my system and synaptic doesn't open anymore.

---

### Post by lucazade on 2011-08-17
> **mc4man said:**
> 

I believe the issue may be  that they didn't include /usr/share/polkit-1/actions/com/ubuntu.pkexec.synaptic.policy in the latest synaptic - adding it and synaptic now works fine

how to? thanks!

---

### Post by mc4man on 2011-08-17
(my isp is currently got some issue, may not be able to post for a while - takes 5+ min right now to reply
Anyway you should have the previous synaptic in /var/cache/apt/archives - just extract it to your desktop and then browse to /usr/share/polkit-1/actions/
Copy the .policy to same place in your install

(if it works and you want a .pkla to remove the need to auth just ask...

---

### Post by Harry33 on 2011-08-17
> **Gunss said:**
> Correction. I'd just updated my system and synaptic doesn't open anymore.

What is your synaptic version?
Synaptic 0.75.2ubuntu4 ?

---

### Post by ventrical on 2011-08-17
> **Gunss said:**
> Correction. I'd just updated my system and synaptic doesn't open anymore.


Right you are . Same Here. No synaptic from Unity 2D, 3D nor GNOME Shell.  I had to use FVWM-Crystal Windows Manager which I installed when I first started alpha testing. So far it has been a reliable method to log on  to Oneiric just in case the Unity or GNOME 3 goes buggy.

  I just got an update so I will try that now and see if the bug has been fixed with those other DEs.

---

### Post by ventrical on 2011-08-17
Definitely  a bug!!

However, synaptic works fine in the FVWM - Crystal  Windows Manager so it is definitely not synaptic that's the culprit IMO.

---

### Post by ventrical on 2011-08-17
> **mc4man said:**
> Definitely a bug - just received the new synaptic
It was moved to /usr/bin (shell script) because /usr/sbin may not be in the $PATH for some as mentioned and now can't be opened w/ auth.
So if you revert or have it opened w/ gksu should work as long as /usr/sbin is in path

I believe the issue may be  that they didn't include /usr/share/polkit-1/actions/com/ubuntu.pkexec.synaptic.policy in the latest synaptic - adding it and synaptic now works fine

 I think it is a bug with Nautalis  because I go an error report concerning Nautalis and sent the report and it brought me to the synaptic bug page .. but I don't understand why it works just great using the FVWM-Crystal DM.

---

### Post by cbowman57 on 2011-08-17
Locate your synaptic.desktop files , probably in /usr/share/applications & /usr/share/app-install/desktop (though the second one is probably optional)

Open with your editor, find the entry that says something like su-to-root -X and replace it with gksu, so it simply reads gksu synaptic.

---

### Post by jbicha on 2011-08-17
> **cbowman57 said:**
> Locate your synaptic.desktop files , probably in /usr/share/applications & /usr/share/app-install/desktop (though the second one is probably optional)

Open with your editor, find the entry that says something like su-to-root -X and replace it with gksu, so it simply reads gksu synaptic.

No, that's not the right fix. For one thing, any future synaptic upgrades will overwrite that file and the new pkexec-enabled Synaptic works just fine.

You need to remove the old Synaptic launcher from the menu. I'd also look in ~/.local/share/applications if there's a synaptic.desktop there that needs to be deleted also.

Trying to run pkexec synaptic won't work because pkexec isn't exactly a drop-in replacement for gksu. There's a longer command that you need that I would have to look up. I'd like to see Ubuntu Oneiric include a wrapper to make a pkexec type command work to replace gksu but that hasn't happened yet.

I believe upstream has a different idea in their heads about what pkexec is for; that's why it's a bit more complicated to use as a substitute for gksu's power.

---

### Post by mc4man on 2011-08-17
Here on a stock install this is what I see as the issue - synaptic needs to be authenticated thru policykit, if there is no usable policy in place then that can't happen
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/828315](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/828315)

---

### Post by ventrical on 2011-08-17
> **mc4man said:**
> Here on a stock install this is what I see as the issue - synaptic needs to be authenticated thru policykit, if there is no usable policy in place then that can't happen
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/828315](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/828315)

Is it safe to assume to just wait  for an update rather than to fiddle and bork up a perfectly good working system?

---

### Post by mc4man on 2011-08-17
> **ventrical said:**
> Is it safe to assume to just wait  for an update rather than to fiddle and bork up a perfectly good working system?
Sure - I suspect a new synaptic should come along shortly - 
As it turns out the .policy file was in the 64 bit package but not in the x86 one

---

### Post by ventrical on 2011-08-17
> **mc4man said:**
> Sure - I suspect a new synaptic should come along shortly - 
As it turns out the .policy file was in the 64 bit package but not in the x86 one


Ahhhh...Ah Ha!

---

### Post by sgage on 2011-08-17
> **ventrical said:**
> Ahhhh...Ah Ha!

Indeed!

---

### Post by ventrical on 2011-08-17
> **sgage said:**
> Indeed!

Well I still do not get it because Synaptic works just fine when I switch to FVWM-Crystal  (which is a desktop manager DE  that can be found in the Ubuntu Software Center. I have been getting small updates all through this dilema using that DE. When I first had *the bug* an occasion of 'Nautalis" open with an error. It prompted me to send the report and then sent me to the synaptic error page. So there is somthing really screwy with the desktop, once again, because it isn't synaptic that has the problem!!!!

  I wrote about this before , with the Natty problems and Compiz - and I am going to  propound that there is STILL a problem with Unity, GNOME and Compiz intergration. I think this is where the core bug lies. The devs are trying to slipstream compiz into the Unity/GNOME Shell DEs and it is playing real havoc with other depends.

So , my question is, why does synaptic package manager  work just fine with FVWM-Crystal and not with Unity2D, 3D and GNOME Shell???

And I am on a 32bit system and got the last upgrade.

Thanks for listening.

---

### Post by ventrical on 2011-08-17
Oh..policy kit bug. Sorry.

---

### Post by Harry33 on 2011-08-18
The newest version of Synaptic (0.75.2ubuntu5) does not start in Oneiric-64bit, the previous one (0.75.2ubuntu4) does.

However, it is easy to workaround this without any modifications.
1) If Synaptic starts OK, then pkexec policy works
2) If Synaptic does not start (pkexec is not working), then it will start from terminal "gksu synaptic".

Here is the bug report (#828315) of this issue:
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/828315](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/828315)

---

### Post by ventrical on 2011-08-18
Thanks for the new fix for synpatic bug for 32bit !!!!!!!!!!!!!!!!!!!!!!

:)

---

### Post by rapiertg on 2011-08-18
As for me synaptic doesn't work since a long time. After start it crashes immediately. Any of you faced this problem  too? In terminal i get:

$ synaptic-pkexec
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
Aborted (core dumped)

---

### Post by Harry33 on 2011-08-18
> **rapiertg said:**
> As for me synaptic doesn't work since a long time. After start it crashes immediately. Any of you faced this problem  too? In terminal i get:

$ synaptic-pkexec
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
Aborted (core dumped)

What happens when you try this in terminal?

```
gksu synaptic
```

---

### Post by sgage on 2011-08-18
synaptic-pkexec is working for me now as of an upgrade this morning.

---

### Post by rapiertg on 2011-08-18
> **Harry33 said:**
> What happens when you try this in terminal?

```
gksu synaptic
```

I got same behavior, but no output in terminal.

---

### Post by Harry33 on 2011-08-18
> **sgage said:**
> synaptic-pkexec is working for me now as of an upgrade this morning.

And you do have a 32-bit setup.
Same here.
But not in 64-bit setup.

---

### Post by Harry33 on 2011-08-18
> **rapiertg said:**
> I got same behavior, but no output in terminal.

Perhaps you should go back to non pkexec version: 0.75.2ubuntu2
Download that and install with dpkg

Here:
[https://launchpad.net/ubuntu/+source/synaptic/0.75.2ubuntu2](https://launchpad.net/ubuntu/+source/synaptic/0.75.2ubuntu2)

---

### Post by rapiertg on 2011-08-18
I think this is not related to gksu or pkexec, as synaptec is starting and crashing immediatelly. I can see it for about a second. In addition it started to crash before the transition to pk-exec. Will have to file a bug probably or try some historical versions...

---

### Post by 3vi1 on 2011-08-18
I can start synaptic fine from the command line (sudo or gksu), but it doesn't start from the menus anymore.  It asks for the password, then goes away forever after I input it.

---

### Post by mc4man on 2011-08-18
synaptic - 0.75.2ubuntu6 should fix for all and be available shortly

Slightly OT - if one decided for some reason to use gdm instead of lightdm then be aware that your $PATH is lacking and may occasionally cause some issue 
(may also come up in an upgrade from 11/04 to 11.10

---

### Post by Harry33 on 2011-08-18
I have tested the latest synaptic_0.75-2ubuntu6 on both 64-bit and 32-bit setups.
It works just fine (and with pkexec).

---

### Post by ventrical on 2011-08-18
As I said , works great here. I am glad I installed FVWM-Crystal before I started testing because that policy kit was not busted  in that DE. Definitely a Nautalis prob.

---

### Post by ventrical on 2011-08-18
Temporary work-a-round for Synaptic:

1. Go to Ubuntu Software Center
2. download FVWM-Crystal
3. Log-out
4. Log in using FVWM-Crystal
5. Click the icon next to the GNOME icon and it will give yout the synaptic option.
6. Run synaptic from there and it will download the new synpatic fix so that it can be
run from the launchers in Unity and GNOME Shell.

:)

*note* errr that is depending your Ubuntu Software Center installer is working :(

---

### Post by JoZ3 on 2011-10-12
> **ventrical said:**
> Temporary work-a-round for Synaptic:

1. Go to Ubuntu Software Center
2. download FVWM-Crystal
3. Log-out
4. Log in using FVWM-Crystal
5. Click the icon next to the GNOME icon and it will give yout the synaptic option.
6. Run synaptic from there and it will download the new synpatic fix so that it can be
run from the launchers in Unity and GNOME Shell.

:)

*note* errr that is depending your Ubuntu Software Center installer is working :(

I have the synaptic_0.75-2ubuntu8 for oneiric and not work in unity and gnome shell :(

---

