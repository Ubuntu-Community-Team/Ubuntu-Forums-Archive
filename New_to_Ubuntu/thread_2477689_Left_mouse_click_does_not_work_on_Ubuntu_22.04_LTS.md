---
title: "Left mouse click does not work on Ubuntu 22.04 LTS"
date: 2022-08-03
forum: New to Ubuntu
---

### Post by r2020r on 2022-08-03
Left mouse click does no work inside VM running Ubuntu 22.04. VM is running inside VB. Host OS is Ubuntu 22.04. Tried changing mouse, ports, rebooting. Problem is intermittent. Sometime it happens repeatedly and sometimes not. Problem is so  bizarre people may think I do not know what I am doing ;-) 

[B]History:
[/B]I had similar problem with Lenavo P50 running Ubuntu 20.4. I changed over to MINT. Could not solve the problem 100%. I changed to Zbook 15". Now I am suddenly seeing this problem.

Can this problem be solved? Any help will be appreciated. 

Note: Touch pad's click is also not working, mouse move works, mouse R-click works.

Thanks

---

### Post by r2020r on 2022-08-03
One of the internet post suggested to use XORG instead of WAYLAND. I tried that and mouse click worked. I am not very confident about this solution because when using XORG on one occasion Left click failed.

---

### Post by Holger_Gehrke on 2022-08-03
It's not so much that errors like that don't happen with X11, it's more that X is (a lot ...) more mature and there's a lot of tools to influence the behaviour of pointing devices.

I sometimes encounter behaviour similar to what you describe on my laptop running XUbuntu 22.04 without any virtualization. I have both a mouse and a touchpad on this machine and the touchpad is set for tap-to-click. Sometimes while typing I manage to do a one-and-a-halve click (tap-release-tap-hold) and this starts a marking action which doesn't end with the release of the pad. While this is going on - and the system is quite content to stay in this state for minutes - no left clicks will be accepted from the mouse. Of course, tapping on the pad does put an end to this ... Since I like tap-to-click and the problem ends as soon as I give the pad another tap, I leave it as it is; but if I really was bothered by it I'd switch tap-to-click off with 
```
xinput setprop "name of device according to xinput --list" "libinput Tapping Enabled" 0
```
Holger

---

