---
title: "Update Manager listings"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by BobJam on 2012-11-05
Ubuntu 12.04 LTS
Mate DE
Inspiron 1545 laptop
4GB RAM

I want to get rid of these bothersome listings in Update Manager FOREVER:

[IMG]http://i46.tinypic.com/1h566g.jpg[/IMG]

Getting rid of Bluetooth would be one option.  I have three reasons for wanting to do that:

1.  This perpetual update notification for THESE PARTICULAR UPDATES annoys me.  This is what reminded me that I didn't want Bluetooth anyway.  My update notification symbol in my panel is showing up:

[IMG]http://i46.tinypic.com/r10myr.jpg[/IMG]

When I click on "show updates", this is what displays:

[IMG]http://i46.tinypic.com/1h566g.jpg[/IMG]

Now I'm NOT suggesting that either the panel symbol or the Update Manager is displaying incorrectly.  On the contrary, they're doing what they're supposed to do.  And I WANT the panel notification, and I WANT to set Update Manager to "Automatically check for updates".

(BTW, I set this to "Never", and that didn't eliminate either the panel notification OR the listing of the updates in Update Manager.  I didn't expect it to, but I was just 'sperimenting to see if by some weird circumstance this would make both the notification FOR THESE PARTICULAR UPDATES and the listings go away.  One other thing I did was disable bluetooth in my start up program  listings . . . I did that a long time ago actually . . .  and that doesn't impact this  situation either.)

I don't want the updates, but furthermore I don't want to be notified about THESE PARTICULAR updates.

Now I can uncheck the updates, and of course they won't download, so I can solve that part of the problem.  But when I restart/boot again, the same notification shows up again, and the same two updates display in Update Manager.

What I need is a "don't inform me of these updates again" setting.  But I don't know if Ubuntu has that, so I don't even know if this is possible.

I want other Mate updates . . . so disabling the Mate PPA is not an option, I just don't want to be notified about THESE PARTICULAR updates.

So, removing Bluetooth seems to be the only solution.

But, there are problems with that too.  Removing Bluetooth seems to be a case of throwing the baby out with the bathwater.

In Synaptic, I see that removing Bluetooth involves removing several other essential items unavoidably . . . like "gnome-shell", "mate-desktop-environment", and other stuff.  Bluetooth seems to be tightly integrated with the gnome-shell.  So I don't want to go that route.


2.  I don't use or have any bluetooth devices.  Additionally, my laptop is not equipped with Bluetooth to begin with, nor do I have/use an external adapter:

[IMG]http://i46.tinypic.com/316xlbt.jpg[/IMG]

So Bluetooth is totally useless, just clutter.  Besides, if ever need it, I can always install it from Synaptic.

3.  I have a space problem, and anything I can eliminate helps.  Now eliminating Bluetooth may not result in a lot of recovered space, but even if it saves me only a little bit of space, that's just one more reason to get rid of this useless clutter.

But never mind Bluetooth.  I can live with it if it's not possible to remove it without removing my DE.

What I really want is NOT to be alerted to THESE PARTICULAR updates, and not get a notification OF THEM.  As I said, I want a "don't inform me of these updates again" setting.

And as I said, I want the notification symbol in my panel, but only for updates OTHER THAN Bluetooth crap.  And I want Update Manger to "check for updates automatically", just not for THESE TWO PARTICULAR UPDATES.  Plus, I DON'T want to disable the Mate PPA.

(Even if I used Unity or another DE, I suspect this bothersome situation with Bluetooth would prevail, so I don't know that getting rid of Mate would solve the problem.  It would still want to update Bluetooth.  Besides, getting rid of mate is NOT something I want to do.  So if the only solution is getting rid of the Mate DE, then I guess I'll just have to live with it.)

Is there a way to do what I want to do?

---

### Post by arpanaut on 2012-11-05
In Synaptic select the packages in question then in the menu select Package>Lock Version.
That should take it out of the upgrade listing.
Not positive if that works but worth a shot.
Might need to refresh/check repositories to update the listings.

---

### Post by newb85 on 2012-11-05
Perhaps I missed something, but is there a specific reason you didn't simply install the updates?  The download size is relatively tiny.  If you don't even use Bluetooth, you don't need to worry about breaking functionality there.

I'm not saying locking the version or removing the package would be bad options.  It just seems to me that installing the updates is the one that would take the least time/thought/energy.

---

### Post by BobJam on 2012-11-06
@arpanaut,

Thanks very much.  Your "lock" method worked very nicely and immediately.  Should have 'sperimented some by NOT refreshing the repositories and seeing if it worked then, but right away I refreshed too . . . so I don't know if it would have worked without refreshing the repositories.   (I doubt it though, but who knows? )

One thing occurs to me.  I assume that if I ever want to use Bluetooth (unlikely, but possible I guess), I can "unlock" the packages and apply the updates before I use it.

Might 'speriment by "unlocking" and seeing if they show up again.

Anyway, thanks for the tip . . . I've always wondered if there was a "don't inform me of these updates again" setting, and I guess your lock method is Ubuntu's version of that setting.

There are a few other times that I've wanted to remove the update listings (NOT CRITICAL SECURITY ONES THOUGH), so I guess this is the way to do it for anything.

@newb85,

Yes, I was holding doing the updates anyway as my fall back position.  Had I not gotten any usable responses to this, I probably just would have flat out done the updates (and grumbled under my breath.)

As it turned out, arpanaut's lock method DID "take the least time/energy" as applying the updates would have (and, Yes, it did take a little bit of "thought" . . . and I guess "time" and "energy" also . . . to make the OP, but I'm glad I did.)  Had that method been either complex or time consuming, I likely would have opted for just flat out installing the updates.

And had I had to wait more than a day for arpanaut's suggestion, again I probably would have just installed and been done with it, but I'm glad now I posted and waited because now I have a ""don't inform me of these updates again" method I didn't know about.

Fortunately, the issue wasn't "urgent", and I had the luxury of giving a potential solution some time.

But, you are correct . . . installing the updates (and grumbling) WAS my fall back option.

---

