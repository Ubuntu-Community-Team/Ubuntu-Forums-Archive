---
title: "How many DTEs is too many to have installed?"
date: 2017-11-13
forum: New to Ubuntu
---

### Post by sterator on 2017-11-13
I'm still searching for the right DTE for me and at this moment I have I'd say 8 installed. I've read that if one installs too many DTE, there's the risk of damaging the Ubuntu installation itself.

Any thoughts or data on this?

---

### Post by vasa1 on 2017-11-13
What is a DTE? Do you mean desktop environment (DE)?

If so, different people have different opinions :)

I would not favor installing more than one DE.

---

### Post by sterator on 2017-11-13
Now that I have several installed, should I un-install all but one? I assume that Unity must stay as that's how Ubuntu ships..is this correct?

---

### Post by Quarkrad on 2017-11-14
This can be a bit confusing - if you install, for example, ubuntu 16.04 then it comes with Unity as the base desktop environment.  Many people have installed gnome flashback (also called classic gnome) as another desktop environment and then logged out and logged back into the classic gnome environment.  They (like I have for some years) stayed in the classic gnome desktop environment with Unity installed but sort of 'in the background and not running'.  Then again, you could have installed *Ubuntu **Mate** 16.04 *that has its own desktop environment and does not install Unity.  At the moment, I have uninstalled my Ubuntu 16.04 system and installed *Ubuntu gnome 3* - so I do not have a Unity desktop environment at all.  There can be conflicts with different desktop environments installed - take note of what vasa1 said, he is a moderator and very knowledgeable.  Many users install virtualbox and run different flavors/desktop to experience what they are like - I would suggest this is a better approach rather than installing different desktops on top of your main ubuntu system.

---

### Post by vasa1 on 2017-11-14
I was a bit rushed when I posted the first response.

During 12.10, I had Unity (default) with lubuntu-desktop and xubuntu-desktop installed later (towards the end of 12.10's life). Nothing exploded but I had to do some cleaning up of menus ...

Anyway, developers of individual flavors don't, I think, take into consideration the addition of other DE's and any complications arising as a consequence. So someone who asks for assistance on these "hybrids" may need to point out that they do have additional environments present even though one can only log in to one environment at a time.

A case in point is provided by the OP here: [How to turn off System sounds in LXDE?]("https://ubuntuforums.org/showthread.php?t=2377486"). Notice the use of "LXDE". What does that mean? What exactly did the poster install? I used pure Lubuntu from 13.04 onwards and never encountered > a beep, cluck, pop, boop, tick and honk every time I click something with the mouse.So where does that come from? Troubleshooting in such cases may be more difficult than otherwise.

---

### Post by sterator on 2017-11-14
Ha...sorry...

well..."LXDE" is, by what I have heard and read, a "desktop environment."  It's billed as "lightweight" regarding resources it requires. Beyond that I am not sure what it actually is, other than a cohesive aggregation of computer code which presents the user with a visual interface having characteristics different from other so-called "desktop environments." It (and other said desktop environments) can be installed with the sudo apt-get install command.

I'd been using "Cinnamon" which is another such desktop environment, and which didn't make a beep every time I clicked my mouse on a button or window. When I began using LXDE, I began to hear various beeps virtually any time I clicked on a button, window, dialogue box, etc, ad nauseum. One would hope such a "feature" wouldn't be turned on by default with no clear way to shut it off, but..here I am..

I'm fairly new enough to Linux and to Ubuntu and I can't tell what is and what isn't correct behavior, and whether I have or have not damaged my installation of Ubuntu by installing as many "desktop environments" as I have. Note that, when I began to install these DTEs, my reading told me that it was perfectly ok to do so...I didn't run into any caveats, but then, this is the internet..anybody can post anything about anything anytime they want to.

I was told that as long as I got software from the vetted Ubuntu repository, I'd be safe (as safe as one can be on Earth).

;-)

---

### Post by vasa1 on 2017-11-14
> **sterator said:**
> ...
I'm fairly new enough to Linux and to Ubuntu and I can't tell what is and what isn't correct behavior, and whether I have or have not damaged my installation of Ubuntu by installing as many "desktop environments" as I have. Note that, when I began to install these DTEs, my reading told me that it was perfectly ok to do so...I didn't run into any caveats, but then, this is the internet..anybody can post anything about anything anytime they want to.

I was told that as long as I got software from the vetted Ubuntu repository, I'd be safe (as safe as one can be on Earth).

;-)Like you, I've seen quite a few blogs and tech sites blithely showing how to add additional desktop environments. Feel free to experiment. All I'm saying is that one should acknowledge that what one sees may not be typical behaviour.

Removing a DE may not be trivial. See [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu) for example. _Do not_ follow those instructions now because they are outdated. I've provided that link just for historical interest.

---

### Post by sterator on 2017-11-14
Thank you for the advice...think I'll stay in LXDE and ignore the other ones...

---

