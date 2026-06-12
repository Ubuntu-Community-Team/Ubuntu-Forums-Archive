---
title: "[howto] gutsy uuber minimal install + compiz-fusion"
date: 2007-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by starscalling on 2007-10-22
grab the ubuntu server install iso and burn to disk 
install the kewl lil thing
edit /etc/apt/sources.list and delete the cd repo
```
sudo apt-get update
```
grab basic needed packages - i include conky, lm-sensors, sensors-applte, hddtemp, xchat, irssi, conky, firefox, etc feel free to take out anything you dont really want..
```
sudo apt-get install checkinstall compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main nautilus gnome-panel compiz-gnome linux-image-generic screen irssi firefox mousepad libgl1-mesa-dri emerald xserver-xorg-core xfonts-base gnome-terminal lm-sensors sensors-applet xchat pidgin pidgin-otr conky hddtemp linux-image-2.6.22.14-generic linux-ubuntu-modules-2.6.22-14-generic 
```
install any specific drivers you need for your video card - like i needed xserver-xorg-video-i810 [or intel of course as i use the 965 chipset]
perform any workarounds needed if on compiz blacklist listed here: 
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)
```
echo SKIP_CHECKS=yes > .config/compiz/compiz-manager
```
if this directory doesnt exist then make it:
```
 mkdir .config && mkdir .config/compiz
```
remove server kernel
```
sudo apt-get --purge remove linux-image-2.6.22-14-server linux-image-server linux-ubuntu-modules-2.6.22-14-server
```
reconfigure X
```
sudo dpkg-reconfigure xserver-xorg
```
create .xinitrc file; mine is as follows:
```
gnome-panel &
nautilus &
fusion-icon
```
grab and install fusion-icon
```
www-browser http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=HEAD
```
the reason i use www-browser is it works in commandline - just scroll over and push enter on 'tree' and then do same to snapshot and it lets you save the package - now lets extract it
```
tar -zxvvf fusion-icon-HEAD.tar.gz
```
time to install ;)
```
cd users/crdlb/fusion-icon/ && make && sudo checkinstall
```
now one tricky thing here in checkinstall: must reset name of package to fusion-icon [field 2] and then version [field 3]- i use 6.6.6 :P[/code]
reboot into generic kernel and startx! [sudo shutdown -r now]
so this leaves you with a cli system that startx starts nautilus/gnome-panel/fusion-icon which pumps compiz-fusion and emerald. you may need to get some emerald themes - but emerald-theme-manager is in there now etc so your good

---

### Post by adarkenigma on 2007-10-26
hello sir,
    newbie here. i am sorry to bombard your howto with questions but i am hoping that you are in mood to answer some of my questions.

1.) after removing sever kernel dont i have to install regular kernel? (sorry if it sounds dumb)

2.) is it necessary to install software thru command line or i can do thru synaptic? (i mean can i install comiz fusion regular way?)

cuz i am confused about this 

```
now one tricky thing here in checkinstall: must reset name of package to fusion-icon [field 2] and then version [field 3]- i use 6.6.6 :P
reboot into generic kernel and startx! [sudo shutdown -r now]
so this leaves you with a cli system that startx starts nautilus/gnome-panel/fusion-icon which pumps compiz-fusion and emerald. you may need to get some emerald themes - but emerald-theme-manager is in there now etc so your good
```

regular install of compiz doesn't require all that (isn't there is easy way?)

3.) "create .xinitrc file;" if i am correct it is start up script of sort. 
Do i have to create it if i am planning to install compiz later? 
( i have ATI x1400 and i am waiting for new driver release which will support AIXGL then i will install compiz fusion)

and last which is not about howto but more about sever edition

i have always wanted to install ubuntu with out evolution and openoffice and voip software.. i have asked before about how to uninstall those software.. and they told me to uninstall wat you can.. and i have always ended up uninstalling wrong stuff and faced black screen may times.... but i think sever edition doesn't install most stuff.. 

so my question is can server edition be really used as desktop edition? 
can i install other stuff later if i needed? .. doest sever edition install somethings specific to sever desktops? .. like extra services and stuff?

---

### Post by Jose Catre-Vandis on 2007-10-27
All goes well until this point:

```
echo SKIP_CHECKS=yes > .config/compiz/compiz-manager
```

console tells me these directories don't exist

I carried on and everything else worked, just rebooting now!

---

### Post by starscalling on 2007-12-10
> **adarkenigma said:**
> hello sir,
    newbie here. i am sorry to bombard your howto with questions but i am hoping that you are in mood to answer some of my questions.

1.) after removing sever kernel dont i have to install regular kernel? (sorry if it sounds dumb)

2.) is it necessary to install software thru command line or i can do thru synaptic? (i mean can i install comiz fusion regular way?)

cuz i am confused about this 

```
now one tricky thing here in checkinstall: must reset name of package to fusion-icon [field 2] and then version [field 3]- i use 6.6.6 :P
reboot into generic kernel and startx! [sudo shutdown -r now]
so this leaves you with a cli system that startx starts nautilus/gnome-panel/fusion-icon which pumps compiz-fusion and emerald. you may need to get some emerald themes - but emerald-theme-manager is in there now etc so your good
```

regular install of compiz doesn't require all that (isn't there is easy way?)

3.) "create .xinitrc file;" if i am correct it is start up script of sort. 
Do i have to create it if i am planning to install compiz later? 
( i have ATI x1400 and i am waiting for new driver release which will support AIXGL then i will install compiz fusion)

and last which is not about howto but more about sever edition

i have always wanted to install ubuntu with out evolution and openoffice and voip software.. i have asked before about how to uninstall those software.. and they told me to uninstall wat you can.. and i have always ended up uninstalling wrong stuff and faced black screen may times.... but i think sever edition doesn't install most stuff.. 

so my question is can server edition be really used as desktop edition? 
can i install other stuff later if i needed? .. doest sever edition install somethings specific to sever desktops? .. like extra services and stuff?

ok in answer to 1. yeah.. my bad.. fixed it
2. you wont have synaptic at first - try installing x-window-system gdm and gnome-core for instance - x-window-system is the X and add whatever WM you like.. or perhaps check out fluxbuntu? ;)
3. it is indeed a startup script - this is because i didnt put in gdm or kdm or xdm - which manages window manager sessions - thats that pretty lil thing you log in with ^_^
so instead we need a lil startup configuration file to tell system what to start when X starts..
@Jose Catre-Vandis - my apologies added that in - no need to add that bit unless your chipset is blacklisted like mine is - and i dont have a nvidia vid card for instance so i have no way to execute the c-f without hitting the blacklisted check.. all this does is fib to the checker :D

---

