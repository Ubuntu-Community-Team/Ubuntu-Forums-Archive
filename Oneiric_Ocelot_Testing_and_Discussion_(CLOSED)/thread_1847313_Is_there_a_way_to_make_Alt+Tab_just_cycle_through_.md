---
title: "Is there a way to make Alt+Tab just cycle through the windows on the current Desktop?"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ajayrockrock on 2011-09-20
I'm having a problem with Alt+Tab and IMO I think it's broken for me.  

Here's how I operate:

Virtual Desktop 1:  a bunch of terminals and firefox
Virtual Desktop 2:  a bunch of terminals, chrome, and another chrome window in "privacy mode".  

When I'm in Desktop 1, I like to alt+tab between firefox and the terminals.  And in Desktop 2, I like to flip through my terminals and my TWO chrome windows with alt+tab.

Right now with the beta (with all updates applied as of September 19th) alt+tab flips between all open applications.  So if firefox has the focus and I crtl+alt+right to move to desktop 2 then chrome will have the focus.  Perfect.  Now when I alt+tab though, it should only cycle between the windows on Desktop 2.  Instead it will slide me back to Desktop 1 and firefox.

Keeping alt+tab between Desktops worked great on every version of Ubuntu in the past and I'm hoping that it's a configuration change I can make or if it's just an active problem that will be fixed before release.  Or maybe I'm the only one that is bothered by this..  :)

---

### Post by mc4man on 2011-09-20
The settings for the new switcher are in ccsm > unity > switcher, there is nothing about Ws's
Currently there is a default scale binding, (Shift+Alt+up. > arrow keys or cursor )   that does 'similar', though I guess not really what you're looking for?

(Atm I'm getting orange boxes instead of orange outline in the switcher so find it currently not as useful as it could be

---

### Post by Seq on 2011-09-20
> **ajayrockrock said:**
> Keeping alt+tab between Desktops worked great on every version of Ubuntu in the past and I'm hoping that it's a configuration change I can make or if it's just an active problem that will be fixed before release.  Or maybe I'm the only one that is bothered by this..  :)

I hope per-workspace behaviour is added to Unity's alt-tab switcher as well.

You can switch to the old switcher, though. You have to disable the keyboard shortcuts that activate Unity's switcher, then activate one of the other alt-tab switchers (the old one was 'Application Switcher'). 

Unfortunately, only the Unity switcher supports the fancy application grouping, so you'd lose that by switching to the classic behaviour.

---

### Post by HuaiDan on 2011-09-21
Ring-switcher in CCSM has bindings that allow for this, I'm sure Static switcher does as well. Currently I have alt-tab set to switch apps on current desk, and alt-super-tab set to switch between all apps.

---

### Post by cariboo on 2011-09-21
Alt-tab now switches between open application, no matter what workspace they are on, using the Alt-tick (the key above tab) switches between multiple instances of an application

---

### Post by ajayrockrock on 2011-09-22
> **Seq said:**
> I hope per-workspace behaviour is added to Unity's alt-tab switcher as well.

You can switch to the old switcher, though. You have to disable the keyboard shortcuts that activate Unity's switcher, then activate one of the other alt-tab switchers (the old one was 'Application Switcher'). 

Unfortunately, only the Unity switcher supports the fancy application grouping, so you'd lose that by switching to the classic behaviour.

I disabled the unity switcher and enabled the "Application Switcher".  While it's not as "pretty" as the unity one, it's way more functional for my needs.  

Thanks for the help!

---

### Post by Gnurfos on 2011-09-23
Hi,

> **cariboo907 said:**
> Alt-tab now switches between open application, no matter what workspace they are on, using the Alt-tick (the key above tab) switches between multiple instances of an application


Do you mean this is a temporary workaround, or the requested feature will not come back ?

Thanks.

---

### Post by cariboo on 2011-09-23
> **Gnurfos said:**
> Hi,




Do you mean this is a temporary workaround, or the requested feature will not come back ?

Thanks.

What requested feature, where was the request made?

---

### Post by Gnurfos on 2011-09-23
Sorry I just meant, the feature this thread was about. I did not want to imply there was some official "request".

But this is still an important feature in my opinion.

---

### Post by cariboo on 2011-09-23
As far as I know, what I posted [here]("http://ubuntuforums.org/showpost.php?p=11271032&postcount=5"), is the expected behavior, and won't be changed.

---

### Post by Gnurfos on 2011-09-23
While that is nice, I don't think it's a replacement for the feature in question here.
Users don't assign windows randomly to workspaces, they rather dedicate workspaces to their "meta-tasks". And then they have 2 use cases:
- switch between meta-tasks. in which case they switch workspace
- stay on the same task but switch windows (inside this task)

Of course I did not do any real study, but I have a strong intuition that I am far from the only one working like this.

---

### Post by stoupa on 2011-10-02
> **Gnurfos said:**
> While that is nice, I don't think it's a replacement for the feature in question here.
Users don't assign windows randomly to workspaces, they rather dedicate workspaces to their "meta-tasks". And then they have 2 use cases:
- switch between meta-tasks. in which case they switch workspace
- stay on the same task but switch windows (inside this task)

Of course I did not do any real study, but I have a strong intuition that I am far from the only one working like this.

That's a very good point.

---

### Post by vanatteveldt on 2011-10-04
> **cariboo907 said:**
> As far as I know, what I posted [here]("http://ubuntuforums.org/showpost.php?p=11271032&postcount=5"), is the expected behavior, and won't be changed.

I don't want to sound like a troll (I am a big ubuntu enthousiast!), but: 

- I've been using ubuntu for a number of years, and have a certain workflow
- This workflow consists of having multiple task-specific desktops, and I use alt tabs to switch between windows within a task, and control-alt-arrows to switch between tasks (desktops)
- From the posts above, I conclude that I am not the only one working like this
- The current Oneric beta2 does not support this workflow, and it seems from your post that the release version won't either (?)
- In other words, Ubuntu 11.10 breaks my workflow, without allowing for a simple config opt-out, for the (imho) sole purpose of adding eye candy

I know I can remove the task switcher and reinstall the old one, after having installed ccsm manually and fiddling with key bindings, but how difficult is it to add a single check box to make sure that the new version has all the features of the old version.

In other words: please stop breaking work flows without real (ie security etc) reason. And if you create an 'improved' version of a much-used application (alt-tab is probably one of the most pressed shortcuts by most users?), please make sure that it is an *improvement* feature-wise, not a regression for some features.

Thanks, and keep up the good work!

-- Wouter

---

