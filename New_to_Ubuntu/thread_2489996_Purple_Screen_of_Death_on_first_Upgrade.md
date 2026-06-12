---
title: "Purple Screen of Death on first Upgrade?"
date: 2023-08-18
forum: New to Ubuntu
---

### Post by subliminaldiving on 2023-08-18
I ran into a problem tonight when trying o install Ubuntu Server (64-bit) on my Raspberry Pi 4 Model B. First, I tried to install Jammy Jellyfish. And that went okay. Then I tried to follow the tutorial [here]("https://ubuntu.com/pro/tutorial") to connect my Ubuntu Pro subscription, and the first step was to just run "sudo apt update" and "sudo apt upgrade."

The update went find. But when I ran the upgrade I got what I'm going to call the Purple Screen of Death. It said something about the kernel not being the version it was expecting. I didn't want to screw up the kernel in my RaspBerry Pi, so I shut down the machine, and decided to re-flash my microSDHC card with Lunar Lobster and try again.

Once more, I got the Purple Screen(s) of death. This time, I hit "okay" and then "cancel" and then tried to re-run "sudo apt update" and "sudo apt upgrade" and now its showing "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded." So maybe everything is fine? I'm not sure. But I don't think I can connect a Pro subscription to a non-LTS release, can I?

---

### Post by Paddy Landau on 2023-08-18
> **subliminaldiving said:**
> I didn't want to screw up the kernel in my RaspBerry Pi…
When you replaced 22.04 with 23.04, that would have changed your kernel anyway. That won't mess up your hardware.

I can't tell you what happened with 22.04, sorry. If that's what you want, try installing it again.
> **subliminaldiving said:**
> Once more, I got the Purple Screen(s) of death.
I am unfamiliar with this, as I've never seen it. In Windows, "screen of death" refers to a condition where the machine is now unresponsive, and you have to reboot, but you said that you could hit "okay" and "cancel", and continue. A screenshot or photograph would be helpful.
> **subliminaldiving said:**
> 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
That means that everything has been updated.

Side note: You can sometimes get some packages available to upgrade, but they don't upgrade right away. That's because Canonical uses a phased approach similar to that used by Android, Windows, etc.
> **subliminaldiving said:**
> I don't think I can connect a Pro subscription to a non-LTS release, can I?
Correct. Ubuntu Pro extends the time of support of an LTS version from 5 years to 10 years. Short-term releases last 9 months, and that's it. As you're a beginner, you really should use the LTS version, as the other versions should be treated as experimental.

I would retry installing 22.04, and if the problem recurs (which seems likely to happen), take a screenshot or photograph of the problem, and post it here. You also need to tell us how you installed (is this a standard desktop or a server, and did you use a minimal installation or the full installation)? Before installing, did you [validate the downloaded ISO]("https://ubuntu.com/tutorials/how-to-verify-ubuntu")? For those of us who don't know the Raspberry, please also include the RAM specifications.

---

### Post by subliminaldiving on 2023-08-20
> **Paddy Landau said:**
> I would retry installing 22.04, and if the problem recurs (which seems likely to happen), take a screenshot or photograph of the problem, and post it here.

The forum won't let me post screenshots until I have at least 10 posts. Give me a minute to comment on some other threads.

---

### Post by Paddy Landau on 2023-08-20
> **subliminaldiving said:**
> The forum won't let me post screenshots until I have at least 10 posts. Give me a minute to comment on some other threads.
You can also use [Pasteboard]("https://pasteboard.co/"), though it's less convenient.

---

### Post by deadflowr on 2023-08-20
> **subliminaldiving said:**
> The forum won't let me post screenshots until I have at least 10 posts.

I'm not sure that's a thing. Maybe it is and I wasn't aware it was.
We do have a 10 post limit in order for users to make changes to their profile,
but posting screenshots should not be affected by that.
Anyway, it's best to use our attachment system to post screenshots.

To add attachments click on Reply to Thread and then click on the paperclip icon in your edit box toolbar.

You can also post a link to 3rd party image hosting sites.

> Give me a minute to comment on some other threads.
Unless you are being genuinely helpful with your posts, bean-mining is a no-no here.
And unhelpful posts in other threads made to simply bring up a bean count will be removed,
and possible sanctions applied.

---

