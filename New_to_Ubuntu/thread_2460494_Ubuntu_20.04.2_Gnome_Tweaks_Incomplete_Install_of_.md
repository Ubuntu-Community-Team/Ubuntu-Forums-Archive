---
title: "Ubuntu 20.04.2: Gnome Tweaks Incomplete Install of Extensions"
date: 2021-04-11
forum: New to Ubuntu
---

### Post by snorlaxtrap on 2021-04-11
Hello all,

I am a new user of Ubuntu 20.04.2 LTS

 I have been trying to install gnome tweaks (3.34.0-2ubuntu1) completely with all of its extensions for the past two days.  I am following the directions to install gnome tweaks on this website [https://linuxhint.com/gnome_tweak_installation_ubuntu/](https://linuxhint.com/gnome_tweak_installation_ubuntu/). When entering the commands, the terminal correctly processes them, showing that it was installed however when I open Tweaks it only displays " Applications " and  "Suspend when laptop lid is closed" just as shown in step 7 from the link above. I have continued the rest of the steps to install all the extensions but nothing changes when I open Tweaks again or after restarting gnome tweaks (ALT +F2 >> 'r'>> ENTER)

- I've tried other steps that I have found online 
- Used sudo apt autoremove to remove gnome-tweaks, gnome-shell-extensions, gnome-tweak-tool then start the process all over. 
- Re-installed Ubuntu to make sure that I installed everything correctly --and I have. 

I don't know what to do now, any help would be appreciated.

Many thanks.

---

### Post by Dennis N on 2021-04-12
> when I open Tweaks it only displays " Applications " and "Suspend when laptop lid is closed" just as shown in step 7 from the link above.
To see and activate (or deactivate) the extensions that are installed, you need to click on "Extensions" in the list on the left side of Tweaks window. The installed extensions will then show on the right side.

There are more extensions on the Gnome Shell Extensions web pages:
[https://extensions.gnome.org/](https://extensions.gnome.org/)

Extensions can also be installed using your web browser.

---

### Post by snorlaxtrap on 2021-04-12
Hi Dennis,

When I open Tweak there is no "Extension" Icon available to click on as you had described. I tried installing the browser extensions but nothing changed.

---

### Post by Dennis N on 2021-04-12
> **snorlaxtrap said:**
> Hi Dennis,

When I open Tweak there is no "Extension" Icon available to click on as you had described. I tried installing the browser extensions but nothing changed.

This is no icon to click on. Click on the word "Extensions". See the screenshot attached.

---

### Post by snorlaxtrap on 2021-04-12
As I said the list on the side doesn't appear. There is nothing to click on. Only the toggles for [COLOR=#000000]" Applications " and "Suspend when laptop lid is closed".[/COLOR]

---

### Post by deadflowr on 2021-04-12
Post back the results from
```
env | grep CURRENT_DESKTOP
```

The description you provide is what I usually see in non-gnome-shell desktops, like unity.
The above should output the desktop session currently in use.

---

### Post by tea for one on 2021-04-12
> **snorlaxtrap said:**
> As I said the list on the side doesn't appear. There is nothing to click on. Only the toggles for [COLOR=#000000]" Applications " and "Suspend when laptop lid is closed".[/COLOR]

Either make the window larger to see all the options

Or click on the little arrow in top left

---

### Post by snorlaxtrap on 2021-04-12
Hello, 

Thanks for taking the time to assist with this basic problem. I did just as you said, I entered that line in the terminal and here is the output:

XDG_CURRENT_DESKTOP =ubuntu:Gnome

---

### Post by snorlaxtrap on 2021-04-12
LMAO!! Wow! I have expanded the window before and it didn't show. Since I am on a VM I did not play with the VIEW to get it in full screen mode, I was working on the default a small window size, and I was assuming you can see everything with the default window size. But now I figured out how to get full screen mode and now I can finally see the side list. 

Gosh, that....was....ridiculous. &#55358;&#56614;*&#9794;&#65039;

Thanks.

---

