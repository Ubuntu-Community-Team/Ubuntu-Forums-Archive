---
title: "Restart button missing in 11.10"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by Charlie Chick on 2011-10-23
Hello Everybody,

I seem to have lost (actually, I'm not sure I ever had it) the restart button in my upgrade to 11.10. Apparently, after clicking on SHUT DOWN you are supposed to get a dialogue box before it shuts down offering you the option to restart instead. I don't get this box, the computer just shuts down. 

Can anybody help me get it back, please?

Thanks.

---

### Post by in·ter·punct on 2011-10-23
It's there, hiding in the corner.

You can also access shutdown and restart from the dash.

---

### Post by Charlie Chick on 2011-10-23
> **in·ter·punct said:**
> It's there, hiding in the corner.

You can also access shutdown and restart from the dash.

Sorry, but it isn't on my machine. Straight after pressing SHUT DOWN, the computer just shuts down!

---

### Post by gandaran on 2011-10-23
> **Charlie Chick said:**
> Sorry, but it isn't on my machine. Straight after pressing SHUT DOWN, the computer just shuts down!
what desktop display are you using? unity, gnome classic or gnome shell?

---

### Post by dcsoldschool53 on 2011-10-23
> **Charlie Chick said:**
> Hello Everybody,

I seem to have lost (actually, I'm not sure I ever had it) the restart button in my upgrade to 11.10. Apparently, after clicking on SHUT DOWN you are supposed to get a dialogue box before it shuts down offering you the option to restart instead. I don't get this box, the computer just shuts down. 

Can anybody help me get it back, please?

Thanks.
Hi, you need to change the setting in your configuration editor. I think it is under "indicator-session". It will say something about suppress the restart menu. Remove the check mark from it.
FYI, gconf-editor didn't work for me, so I had to down load a new configuration editor dconf-editor for 11.10.```
sudo apt-get install dconf-tools
```

---

### Post by Larkspur on 2011-10-23
If you're using Unity, open the dash and type "r"; Restart should be the first option.

---

### Post by dcsoldschool53 on 2011-10-23
> **Larkspur said:**
> If you're using Unity, open the dash and type "r"; Restart should be the first option.
Thank you. It works for me.:KS

---

### Post by Charlie Chick on 2011-10-23
> **dcsoldschool53 said:**
> Hi, you need to change the setting in your configuration editor. I think it is under "indicator-session". It will say something about suppress the restart menu. Remove the check mark from it.

Tried that. Unticked the box but, sadly, no difference.

I'm using Unity 3D (as far as I know). The System Settings menu isn't nearly as comprehensive as in Gnome.

---

### Post by dcsoldschool53 on 2011-10-23
@Charles download the new version.```
sudo apt-get install dconf-tools
```It works!

---

### Post by drs305 on 2011-10-23
> **dcsoldschool53 said:**
> Hi, you need to change the setting in your configuration editor. I think it is under "indicator-session". It will say something about suppress the restart menu. Remove the check mark from it.

There are several ways to approach this. There are 'indicator-session' settings accessible via both gonf-editor and dconf-editor (dconf-tools must be installed for this one).

1. dconf-editor appears to have priority, so you can open 'dconf-tools' and go to /apps/indicator-session. The setting is 'suppress-logout-restart-shutdown'.

If it is not suppressed, the restart button is accessed by pressing "Shutdown", at which point you will have the "Restart" option on the left (see a previous post for the graphic).

If the selection is enabled/true, which is probably the OPs setting, when pressing the "Shutdown" option the system shuts off without ever seeing an option to 'Restart'.

To change the setting to see the 'Restart' option when you press 'Shutdown', you can run the following command:
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown "false"
```

2. As I think was mentioned, you can also type 'restart' from Dash.

3. If you want to put a 'Restart' button on your Launcher, in Dash type "Restart", then drag the icon to your Launcher. One reason to do this is because with the 'suppress' setting set to false, you always have to confirm you want to shut down the computer. If you don't want confirmation, you also lose the 'Restart' option. If you have the 'Restart' in the Launcher and also 'suppress' as true, you avoid the confirmation and also have access to 'Restart'. (Yeah, I know it's geeky!)

---

### Post by Charlie Chick on 2011-10-23
> **dcsoldschool53 said:**
> @Charles download the new version.```
sudo apt-get install dconf-tools
```It works!

Done, but it hasn't made any difference.

---

### Post by Charlie Chick on 2011-10-26
Aha, so there's a difference between gconf and dconf! I installed dconf and tried again. Success! 

Thanks to everybody who replied.

Charlie

---

### Post by AgenT on 2011-10-27
I there a way to enable the "restart" entry in the actual indicator so that "restart" is listed along side of shutdown, logout, suspend, etc.? I only use restart and suspend and would like them to be instantaneous like in every Ubuntu prior to 11.10. The shutdown confirmation popup is annoying.

---

### Post by drs305 on 2011-10-27
> **AgenT said:**
> The shutdown confirmation popup is annoying.

Not to mention that if the settings aren't correct and you press 'Shutdown' you won't get the 'Restart' button display, but the system will shut down without further warning...

---

### Post by theWrkncacnter on 2012-02-04
> **AgenT said:**
> I there a way to enable the "restart" entry in the actual indicator so that "restart" is listed along side of shutdown, logout, suspend, etc.? I only use restart and suspend and would like them to be instantaneous like in every Ubuntu prior to 11.10. The shutdown confirmation popup is annoying.

Bump. I also vote for this. Anyone know dconf well enough to know how to do it?

---

### Post by ledzepjes on 2012-04-13
bump

I would also like to see the Restart button back in the menu by Lockout, Logoff, Suspend, Hibernate, and Shutdown, it makes no functional sense to me why it's missing and why the developers would exclude it. And when I go into gconf editor or dconf editor neither one show the Restart item suppressed, so why is it still hidden? When I suppress the shutdown option, shutdown is hidden, but Restart has no effect either way? It's not visible for me.

why would anyone remove Restart, it's as silly as gnome 3 not having Shutdown

shaking my head

---

### Post by souravc83 on 2012-04-13
It is silly indeed. Gnome 3 not having shutdown puzzled me too.
I think its just the developers being "oh, this is so cool, we can interact with the hardware and decide whether the machine supports suspend or not". However, not having shutdown and restart buttons are annoying.

But I find it convenient to shutdown from the command line. This way, I don't have to deal with the quirks of Unity and Gnome 3.

If you don't mind using the command line, then just shutdown or restart from the command line, instead of using the title bar. Its much faster and you have full control.
To, shutdown, use:
[HTML]sudo shutdown -h now
[/HTML]

To restart, type
[HTML]sudo shutdown -r now[/HTML]

---

### Post by anewguy on 2012-04-13
Sounds a little like Windows 7, eh?  In XP I remember clicking shutdown and being presented with the restart/shutdown/etc menu.  Windows 7 and all of a sudden it's click shutdown and it shutsdown - you have to go to the arrow on the right to get the other options.

I also thought this was a rather silly change/omission/bug with ubuntu lately - all the other options are there, why not restart?

I may have to do some digging to see how all of this works - the gconf and dconf things, etc., and see if I can figure it out.  That's going to be a fun and long journey.

You have my vote for including it with the other options again!

Dave ;)

---

### Post by u2nTu on 2012-10-24
Just to give a last update (as this appears to be the best thread on subject in UF), this problem is apparently solved in Quantal 12.10.

Reportedly, when the confirmation dialog is killed:```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown "true"
```then the Restart button reappears in the menu (like the old days).

This should give hope that the bad ideas that do get implemented are eventually rooted out and discarded. May this one RIP.

---

### Post by AgenT on 2012-10-24
I can confirm that I now have a "Restart" menu item. Too bad it took a whole year (2 full releases) to get fixed.

---

