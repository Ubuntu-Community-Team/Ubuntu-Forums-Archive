---
title: "Gnome-shell will soon enter Oneiric repos"
date: 2011-05-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-28
There is a new build of gnome-shell waiting for a dependency in Launchpad.
It will soon enter the Oneiric official repos.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.1-1](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.1-1)

---

### Post by MacUntu on 2011-05-28
I love this transition. Finally some real fun during the first weeks of development.

---

### Post by novatillasku on 2011-05-28
Yes, Bilal said it in twitter 1 hour ago:

@bilal_akhtar96 
YAY! GNOME SHELL LANDED IN ONEIRIC! THE FINAL PIECE OF GNOME3 TRANSITION HAS LANDED! Now to get Unity working well in the environment.
 
@bilal_akhtar96 
So right now Oneiric is full GNOME3 + Unity. Can't believe one of the major goals of this release have been completed so soon!

Is very interesting follow him ;-)

---

### Post by kansasnoob on 2011-05-28
Far out! Things just keep getting better :D

I've been wondering what type of breakage to expect changing from unity to gnome-shell, I guess we'll know soon \\:D/

---

### Post by Harry33 on 2011-05-28
> **novatillasku said:**
> Yes, Bilal said it in twitter 1 hour ago:

@bilal_akhtar96 
YAY! GNOME SHELL LANDED IN ONEIRIC! THE FINAL PIECE OF GNOME3 TRANSITION HAS LANDED! Now to get Unity working well in the environment.
 
@bilal_akhtar96 
So right now Oneiric is full GNOME3 + Unity. Can't believe one of the major goals of this release have been completed so soon!

Is very interesting follow him ;-)

Well not quite.
Gnome-panel (v.3) is still missing.
This would be then the correct fallback to gnome-shell.

And of course we do not have gdm (v.3) nor do we have gnome-menus there yet.

---

### Post by gnomeuser on 2011-05-28
> **Harry33 said:**
> Well not quite.
Gnome-panel (v.3) is still missing.
This would be then the correct fallback to gnome-shell.

And of course we do not have gdm (v.3) nor do we have gnome-menus there yet.

I think it is called gnome-panel-fallback or something like that

---

### Post by Harry33 on 2011-05-29
> **gnomeuser said:**
> I think it is called gnome-panel-fallback or something like that

OK!
Do you know why they haven't built that package into Gnome3 PPA?
That PPA works very well in my Natty setup, but it still relies on gnome-panel (v2) as a fallback.

---

### Post by TerminX on 2011-05-29
> **gnomeuser said:**
> I think it is called gnome-panel-fallback or something like that
Unfortunately, you're a bit confused.  It's actually a package called gnome-session-fallback that depends on gnome-panel and adds a session to the login manager to launch that instead of gnome-shell.

I'm sure there will be a GNOME 3 version of the gnome-panel package at some point soon, it just hasn't happened yet.  There's potentially a bunch of work that has to be done first... any packages containing GNOME 2 panel applets have to be removed from the repository (or just altered to drop the applet if the package contains more than that), dependencies need to be changed, etc.

---

### Post by kansasnoob on 2011-05-29
So, has anyone figured out how to get a true gnome3/gnome-shell DE in Oneiric?

I mean w/o adding any ppa's :)

I currently have Ubuntu (unity), Ubuntu 2D (unity-2d), classic, and classic w/o effects. Both classic DE's use the old gnome-panel(ish) DE.

I've not so far found a way to boot into an actual gnome-shell DE.

---

### Post by Harry33 on 2011-05-29
> **kansasnoob said:**
> So, has anyone figured out how to get a true gnome3/gnome-shell DE in Oneiric?

I mean w/o adding any ppa's :)

I currently have Ubuntu (unity), Ubuntu 2D (unity-2d), classic, and classic w/o effects. Both classic DE's use the old gnome-panel(ish) DE.

I've not so far found a way to boot into an actual gnome-shell DE.

You cannot do that yet without an additional PPA (like Gnome3).
You see the package gnome-shell is not yet in repos.
However, it is in Launchpad (the state is still "dependency wait").
It needs libnm-glib-dev in order to build.

When package gnome-shell is installed, you can choose the session "Gnome" from login window, and then the system boots into gnome-shell.

---

### Post by Starks on 2011-05-29
i'm not coming back from my adventure with fedora until gnome-shell works on oneiric.

nuff said.

---

### Post by Framli on 2011-05-29
Alt+F2; gnome-shell --replace; Alt+F2; unity --replace

:)

---

### Post by Starks on 2011-05-29
seamless switching between unity and a CURRENT gnome-shell works?

---

### Post by Framli on 2011-05-29
Works on my box: up to date Oneiric, Gnome-Shell 3.0.2+git20110525.33a3b804-0~11.10~ricotz0 (Ricotz testing PPA, Git snapshot from 05/25)

---

### Post by Atermoon on 2011-05-29
> **Framli said:**
> Works on my box: up to date Oneiric, Gnome-Shell 3.0.2+git20110525.33a3b804-0~11.10~ricotz0 (Ricotz testing PPA, Git snapshot from 05/25)

Last time I checked there was no ppa for Oneiric (unless I missed it somehow) and I didn't want to mess up something with the Natty version. Going to check it out right now, thanks!

Edit: Yep, works fine :)

---

### Post by Harry33 on 2011-05-30
> **Atermoon said:**
> Last time I checked there was no ppa for Oneiric (unless I missed it somehow) and I didn't want to mess up something with the Natty version. Going to check it out right now, thanks!

Edit: Yep, works fine :)

There is the PPA for Oneiric, and it is exactly the one Framli pointed out.
Here:
[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

---

### Post by Atermoon on 2011-05-30
> **Harry33 said:**
> There is the PPA for Oneric, and it is exactly the one Framli pointed out.
Here:
[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

That's the one I added. Sorry if I wasn't clear enough.

---

### Post by Harry33 on 2011-05-30
The Gnome-shell from the Ricotz testing PPA works very well in Oneiric.
You just need to install the newer network-manager (from Ricotz Testing PPA) with its dependencies
(libnl1, libnm-glib2, libnm-util1) too.
This is because Gnome-shell depends on gir1.2-networkmanager-1.0 and that is not yet in Oneiric repos either.

Actually package gnome-shell is waiting for its dependency in the Launchpad.
This is the above mentioned newer network-manager.
Then Gnome-shell is in Oneiric repos too.

---

### Post by kansasnoob on 2011-05-30
> **Harry33 said:**
> You cannot do that yet without an additional PPA (like Gnome3).
You see the package gnome-shell is not yet in repos.
However, it is in Launchpad (the state is still "dependency wait").
It needs libnm-glib-dev in order to build.

When package gnome-shell is installed, you can choose the session "Gnome" from login window, and then the system boots into gnome-shell.

Thanks Harry33. I'll probably just wait then, but I thought I might be overlooking something.

---

### Post by Harry33 on 2011-05-30
> **kansasnoob said:**
> Thanks Harry33. I'll probably just wait then, but I thought I might be overlooking something.

You can get a very good working version from Ricotz testing PPA:
[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

Really, with that the new gnome-panel from Oneiric repos is a good pair.

---

### Post by kansasnoob on 2011-05-30
> **Harry33 said:**
> You can get a very good working version from Ricotz testing PPA:
[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

Really, with that the new gnome-panel from Oneiric repos is a good pair.

I'm just waiting right now because my Oneiric is working acceptably well and I want something to compare Alpha1 iso-testing images to in case I encounter any specific problems.

Once iso-testing is over I'll play much more, in fact I'll then have more Ocelot's to play with because I already have a Natty set up for the upgrade test and my manual partitioning test will also go on my main hard drive unless ubiquity is super borked.

When it comes to gnome3 I prefer beginning with gnome-shell and then forcing the fallback via "/usr/share/gnome-session/sessions/gnome.session" (or the actual gnome3 gui if it works).

I've been playing that way in Natty using ppa's, and also in Fedora, and the only thing I haven't figured out is how to "inhibit" the screensaver like I would have using "inhibit-applet" in gnome2.

I guess the Gnome3 gurus kind of forgot about screensaver settings altogether from the looks of things :(

---

### Post by mick8985 on 2011-05-30
I am getting so bored of waiting for libnm-glib-dev to be packaged!
Hurry up MOTU's!

---

### Post by Harry33 on 2011-05-30
> **mick8985 said:**
> I am getting so bored of waiting for libnm-glib-dev to be packaged!
Hurry up MOTU's!

It has been built already, wait for a couple of hours for the new network-manager to be in official repos or go and download it straight from here:
[https://launchpad.net/ubuntu/oneiric/+source/network-manager/0.8.9997-1ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/network-manager/0.8.9997-1ubuntu1)

The next thing is to wait until the rebuilding of gnome-shell package starts here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.1-1](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.1-1)

The rebuilding starts when NM is in repos.

---

### Post by Harry33 on 2011-05-31
OK now there is a real ubuntu version of gnome-shell.
Gnome-shell_3.0.1-1 is in official Oneiric repos (32-bit and 64-bit).
Here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.1-1](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.0.1-1)

That one is of course a bit older than Ricotz git-version
(3.0.2+git20110525.33a3b804-0~11.04~ricotz0)

I am using the Ricotz version. It works very well.
Only one thing: I do not have button for reboot nor shut down.
I have to use terminal for those:
- sudo reboot
- sudo halt

---

### Post by Quackers on 2011-05-31
Harry33 are you getting this screen? (Excuse the quality - and the dirty screen)

---

### Post by Harry33 on 2011-05-31
> **Quackers said:**
> Harry33 are you getting this screen? (Excuse the quality - and the dirty screen)

:P :guitar:

Oh yes, I have seen that now twice (once in my both machines).
It goes away for good, just by accepting the relogging.
It appeared after I upgraded gnome-panel (GTK+3) and rebooted.

---

### Post by Quackers on 2011-05-31
Ah, thanks. I'm not on my own then :-)
I only get that on my gnome3 system, not unity.

---

### Post by Harry33 on 2011-05-31
> **Quackers said:**
> Ah, thanks. I'm not on my own then :-)
I only get that on my gnome3 system, not unity.

Yeah, I think it is connected only with gnome-session.

---

### Post by Quackers on 2011-05-31
Yes, it seems so here.  Thanks again :-)

---

### Post by Atermoon on 2011-05-31
> **Harry33 said:**
> Only one thing: I do not have button for reboot nor shut down.
I have to use terminal for those:
- sudo reboot
- sudo halt

Click on the user menu / me menu / whatever they call it in gnome shell (top right corner). Then hold the ALT key and a "shutdown" option will appear in the menu. You can also reboot from the dialog that pops up after clicking it ;)

---

### Post by Quadunit404 on 2011-05-31
Well now that GNOME Shell is in the repos, the transition to G3 is going along smoothly. All what's left is to port the themes to GTK3, add support for GNOME 3 apps to the global menu in Unity and the G3/GTK3 transition will be complete, correct? :D

Then Canonical should be able to focus on fixing the MANY remaining bugs, improving Unity's usability and themeability right?

---

### Post by ronacc on 2011-05-31
yes another step tword making things easier , it now takes both hands to shutdown . We need a way to customize that menu . I only want 2 options there , reboot and shut down . I never suspend or hibernate and I never use IM  so those choices are a waste of space for me .

---

### Post by kansasnoob on 2011-05-31
> **ronacc said:**
> yes another step tword making things easier , it now takes both hands to shutdown . We need a way to customize that menu . I only want 2 options there , reboot and shut down . I never suspend or hibernate and I never use IM  so those choices are a waste of space for me .

Step #1: Make it so no one can change the position and duration of notifications.

Step #2: Break the live CD so you have 3 seconds to identify and react to two obscure icons to edit boot parameters.

Step #3: Continue down this path insisting that end users need to adjust to the change, rinse, and repeat :lolflag:

---

### Post by Atermoon on 2011-05-31
> **ronacc said:**
> yes another step tword making things easier , it now takes both hands to shutdown . We need a way to customize that menu . I only want 2 options there , reboot and shut down . I never suspend or hibernate and I never use IM  so those choices are a waste of space for me .

There's an extension that makes it always visible. Should be pretty simple to write one to hide the stuff you don't need there ;)

---

### Post by Squonk07 on 2011-05-31
I went ahead and installed gnome-shell from the OO repo. Booting into it I was greeted with a profoundly broken experience in which any opened windows draw totally garbled and resist movement. Near as I can tell the "shell" parts (everything but application windows) draw just fine. Overall utterly useless at this point (maybe more so than usual? :tongue: I can't say I've warmed to it yet based on Fedora 15; I'm hoping I'll like the incarnation in OO better).

FTR, I've installed Lucazade's GTK+3 port of Ambiance, and though I went ahead and switched the GTK+ theme back to "Adwaita" in dconf-editor, the problem (and the theme) persist in GS. Could this be my problem?

---

### Post by Quackers on 2011-05-31
> **ronacc said:**
> yes another step tword making things easier , it now takes both hands to shutdown . We need a way to customize that menu . I only want 2 options there , reboot and shut down . I never suspend or hibernate and I never use IM  so those choices are a waste of space for me .

There is a way to change that menu in Fedora, so it's likely that when all the packages are done it will be available in Ubuntu - maybe :-)

---

### Post by ronacc on 2011-05-31
At least the shell is working well for me ( plain vanilla install no ppa's ) we will just have to see how things shape up as we move along .

---

### Post by Harry33 on 2011-06-01
> **Atermoon said:**
> Click on the user menu / me menu / whatever they call it in gnome shell (top right corner). Then hold the ALT key and a "shutdown" option will appear in the menu. You can also reboot from the dialog that pops up after clicking it ;)

Oh yes, I had completely forgotten that.
It's been a long time since I last time used Gnome-shell.

Hey, thank you very much Atermoon! :guitar:

---

### Post by arpanaut on 2011-06-01
OH Joy, another DE to be completely confused by...

j/k

Actually quite interesting to compare and contrast with Unity.
Jury is still out on both!  But ain't this fun?

---

### Post by xebian on 2011-06-01
I'm loving gnome-shell right now.  I hate unity because windows has to be maximized.  When they are not, the screen is not re-drawn making a mess.

---

### Post by cariboo on 2011-06-01
I just install gnome-shell from the repositories. It works quite well, no screen redraw problems with programs not running full screen.

---

### Post by jppr on 2011-06-01
> **cariboo907 said:**
> I just install gnome-shell from the repositories. It works quite well, no screen redraw problems with programs not running full screen.

+1 :popcorn:

---

### Post by xebian on 2011-06-01
> **cariboo907 said:**
> I just install gnome-shell from the repositories. It works quite well, no screen redraw problems with programs not running full screen.

If you are responding to my post above about screen not re-drawn when not maximized then you need a new set of glasses or something else.

```

I'm loving gnome-shell right now. [COLOR="Red"]**I hate unity**[/COLOR] because windows has to be maximized. When they are not, the screen is not re-drawn making a mess.
```

---

### Post by afv on 2011-06-01
> **xebian said:**
> If you are responding to my post above about screen not re-drawn when not maximized then you need a new set of glasses or something else.

```

I'm loving gnome-shell right now. [COLOR="Red"]**I hate unity**[/COLOR] because windows has to be maximized. When they are not, the screen is not re-drawn making a mess.
```

Try this:

```

$ gsettings set org.gnome.desktop.background show-desktop-icons true

```

---

### Post by cariboo on 2011-06-01
> **xebian said:**
> If you are responding to my post above about screen not re-drawn when not maximized then you need a new set of glasses or something else.

```

I'm loving gnome-shell right now. [COLOR="Red"]**I hate unity**[/COLOR] because windows has to be maximized. When they are not, the screen is not re-drawn making a mess.
```

You're right,  I can't read properly :), my excuse is lack of sleep. :)

---

### Post by Luffield on 2011-06-02
What's Ubuntu 11.10's Gnome shell experience going to be like? Is it going to be very close to the upstream Gnome shell, or something customized like Gnome 2.X was in all recent versions of Ubuntu?

---

### Post by wgarcia on 2011-06-02
As far as I understand there will be no Gnome Shell option in the default Desktop menu at the login screen. But since everything will be updated to GTK3 it will be easy to download and install from the standard repositories.

---

### Post by sparker256 on 2011-06-02
> **wgarcia said:**
> As far as I understand there will be no Gnome Shell option in the default Desktop menu at the login screen. But since everything will be updated to GTK3 it will be easy to download and install from the standard repositories.
Here are the options that I have at the login screen with everything up to date.

GNOME
GNOME classic
GNOME Classic (no effects)
Recovery Console
Ubuntu
Ubuntu 2D
User Defined

Bill

---

### Post by el_koraco on 2011-06-02
> **Luffield said:**
> What's Ubuntu 11.10's Gnome shell experience going to be like? Is it going to be very close to the upstream Gnome shell, or something customized like Gnome 2.X was in all recent versions of Ubuntu?

pure VANILLA!

---

### Post by dino99 on 2011-06-02
unity* & compiz* removed here, so no trouble :)

---

### Post by Harry33 on 2011-06-02
> **dino99 said:**
> unity* & compiz* removed here, so no trouble :)

+ 1   :guitar:

---

### Post by gagansinghjarry on 2011-06-02
Just out of curiosity does the panel in fallback mode let you add applets?

---

### Post by Harry33 on 2011-06-02
There is a new Gnome-shell version (3.0.2-1) in repos now.
Here:
[https://launchpad.net/ubuntu/+source/gnome-shell/3.0.2-1](https://launchpad.net/ubuntu/+source/gnome-shell/3.0.2-1)

---

