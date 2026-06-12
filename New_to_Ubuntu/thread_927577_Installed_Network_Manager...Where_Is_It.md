---
title: "Installed Network Manager...Where Is It?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by bobby_fabulous on 2008-09-23
Ok I just installed 8.04 x64 on my notebook and followed a guide I found to install Network Manager, I went to synaptic package manager, searched for "network manager", chose to install it and it now shows as installed in the package list but how in the heck do I open it so that I can use it? I have searched high and low, preferences, administration, clicked the network tray icon and nothing. How do I access this Network Manager so I can view available networks?

Thanks

---

### Post by Orange_and_Green on 2008-09-23
Hello :)

NetworkManager should be installed by default, there's no need to install it via Synaptic...

anyway, NetworkManager by itself is a command-line program, it resides in /sbin/NetworkManager. Its gui frontend is nm-applet. In the default installation, there should be an icon on the right side of the top panel showing two black monitors one in front of another. Click on that.

If for some reason you don't have this icon, type
```
nm-applet &
```
in a terminal and it will start. If you don't have it, you might want to add nm-applet to your session.

Good luck:KS

---

### Post by jemate18 on 2008-09-23
> **bobby_fabulous said:**
> Ok I just installed 8.04 x64 on my notebook and followed a guide I found to install Network Manager, I went to synaptic package manager, searched for "network manager", chose to install it and it now shows as installed in the package list but how in the heck do I open it so that I can use it? I have searched high and low, preferences, administration, clicked the network tray icon and nothing. How do I access this Network Manager so I can view available networks?

Thanks

did it installed successfully?

try this to verify
```
dpkg --get-selections | grep -i "network-manager"

```

it should output this
> network-manager					install
network-manager-gnome				install


if not, then it wasnt installed

---

### Post by bobby_fabulous on 2008-09-23
> **Orange_and_Green said:**
> Hello :)

NetworkManager should be installed by default, there's no need to install it via Synaptic...

anyway, NetworkManager by itself is a command-line program, it resides in /sbin/NetworkManager. Its gui frontend is nm-applet. In the default installation, there should be an icon on the right side of the top panel showing two black monitors one in front of another. Click on that.

If for some reason you don't have this icon, type
```
nm-applet &
```
in a terminal and it will start. If you don't have it, you might want to add nm-applet to your session.

Good luck:KS

ok I have that icon but when I open it it does not show all my available wireless networks which is what I'm after so I can find a network to connect to.

thanks

---

### Post by bobby_fabulous on 2008-09-23
> **jemate18 said:**
> did it installed successfully?

try this to verify
```
dpkg --get-selections | grep -i "network-manager"

```

it should output this


if not, then it wasnt installed


yes they verify as installed

---

### Post by Idefix82 on 2008-09-23
Could you type in the terminal
```
lshw -C network
```
and post the output here?

---

### Post by Orange_and_Green on 2008-09-23
> **bobby_fabulous said:**
> ok I have that icon but when I open it it does not show all my available wireless networks which is what I'm after so I can find a network to connect to.

thanks

Just to clarify, when you click on that famous icon, does it say "wireless networks -> No networks available" (which would mean your system is aware it has a wireless network adapter, and can't find networks) or doesn't it talk about wireless at all?

Also, a silly little thing that is often overlooked... If you are using a notebook, more often than not they come with a small button/switch that allows you to cut the power from the network adapter if you don't need it. Have you made sure that button/switch is on?

Good luck:KS

---

### Post by bobby_fabulous on 2008-09-23
> **Orange_and_Green said:**
> Just to clarify, when you click on that famous icon, does it say "wireless networks -> No networks available" (which would mean your system is aware it has a wireless network adapter, and can't find networks) or doesn't it talk about wireless at all?

Also, a little silly thing that is often overlooked... If you are using a notebook, more often than not they come with a small button/switch that allows you to cut the power from the network adapter if you don't need it. Have you made sure that button/switch is on?

Good luck:KS

ok this may sound odd but i changed the default theme while waiting for response and I just clicked the network icon again and all of a sudden wireless networks are now shown...:S

maybe network manager only works when it wants to? 

lol in any event i changed theme to "glossy p" and all of a sudden poof there they are. 

strange but im happy nonetheless.

thank you for all of the response, im sure you will hear from this noob again :P

---

### Post by billgoldberg on 2008-09-23
> **bobby_fabulous said:**
> ok this may sound odd but i changed the default theme while waiting for response and I just clicked the network icon again and all of a sudden wireless networks are now shown...:S

maybe network manager only works when it wants to? 

lol in any event i changed theme to "glossy p" and all of a sudden poof there they are. 

strange but im happy nonetheless.

thank you for all of the response, im sure you will hear from this noob again :P

Glad to hear that.

Even though I highly doubt changing a theme has any impact at all on network manager.

Could you mark this thread as solved?

---

