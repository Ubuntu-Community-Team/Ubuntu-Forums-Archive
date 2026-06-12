---
title: "Auto Updates"
date: 2013-10-03
forum: New to Ubuntu
---

### Post by Quarkrad on 2013-10-03
Can you specify how long a Ubuntu machine is on line before the auto update (if there are any) window pops up? A family member uses their machine mainly to check email and do a bit surfing and they never see the Update window (they are running 12.04). It would ideal if the update window popped up two or three minutes after establishing a connection.

---

### Post by speartip on 2013-10-03
A window doesn't pop up, the updater appears in the Unity bar, with the number of updates in.
Just set it to check for updates everyday, using synaptic / software sources / updates.
12.04 is now 17 months old though & quite stable, so updates may only come through once a week or so.

---

### Post by deadflowr on 2013-10-03
Update Manager usually starts running a check within a couple of minutes after booting in.
Then usually does periodic rechecks every so often, depending on how long you've been on-line.
like stated before 12.04 is old and quite stble at this point.
You should be getting few updates, mainly for updates to browsers, email clients, and new kernel versions.
You can go several weeks on 12.04 without an update.

If it truly becomes bothersome, click the "check" button and run the update manually. 

The update manager will also tell you the last time it checked for updates when you launch it.
(It's in the top banner section of the Update-Manager)

---

### Post by Quarkrad on 2013-10-04
Is there a way to get a pop up window appear on the Desktop at the same time, or instead of, the icon appearing in the launcher bar?  In this real world test people are not noticing/seeing the launcher bar icon so not getting updates.

---

### Post by Quarkrad on 2013-10-06
bump

---

### Post by Quarkrad on 2013-10-06
I believe one of the issues is when a user has their launcher configured as auto-hide (as I have done for many friends/family with laptops) - they do not notice something like the updater icon in the hidden launcher.  I have asked people to look out for it but it is not happening.  That is why a pop up window on the Desktop (as per 9.04 onwards days) would be much better for this type of user.

---

### Post by speartip on 2013-10-06
The problem with a pop up window, is that you have to be sat in front of your screen to see it. If you go & make a cup of tea & come back the pop up window will have gone as any notifications are set to disappear after so many seconds.
 Surely if the Unity icon thing is such a problem, then just get into the habit of checking for updates every week or so, its only a couple of mouse clicks.

---

### Post by 3rdalbum on 2013-10-06
Users don't want a window suddenly popping up and interrupting what they were doing. This isn't Windows XP.

Go into Software Sources and set it to "Check for updated automatically" and then they will recieve a notification when updates are found. If they are not confident computer users, though, probably best to set Software Sources to automatically install security updates.

---

### Post by Quarkrad on 2013-10-08
I'm trying to simulate this in Virtualbox - how do know these updates are happening in thr background?   Also, what happens if you shut down part way through an install of the downloads?  I'm thinking of when there is an install of a new linux image - would shutting down part way through cause any issues?  (Be interested to see the evidence of users not wanting pop up windows for something as important as security updates - where is it?).

---

### Post by speartip on 2013-10-08
Quarkrad, updates are not installed automatically, it only "checks" for updates, & then warns you in the Unity bar that there are updates available. It is then upto the user to click the icon & install them. So shutting down half way through an install wouldn't happen.

---

### Post by 3rdalbum on 2013-10-08
> **Quarkrad said:**
> I'm trying to simulate this in Virtualbox - how do know these updates are happening in thr background?   Also, what happens if you shut down part way through an install of the downloads?  I'm thinking of when there is an install of a new linux image - would shutting down part way through cause any issues?  (Be interested to see the evidence of users not wanting pop up windows for something as important as security updates - where is it?).

I never, EVER want a window to pop up unexpectedly. If I'm busy working at my desk and somebody suddenly puts their face in front of mine and tells me something unrelated to my work, I get annoyed; the same applies with my computer.

The correct thing to do is to display a notification that can be looked at and does not request immediate action from the user.

I can't answer the question of "what happens if you shut down part-way through an install"; never tried it. Two theories: Either the apt-daemon will continue to run, blocking shut down of the computer until it's done (probably not a good idea); or the system will still shut down and you'll need to run "sudo dpkg --configure -a" when you next boot up.

---

### Post by ian-weisser on 2013-10-08
> **Quarkrad said:**
> Can you specify how long a Ubuntu machine is on line before the auto update (if there are any) window pops up?
Yes, but it's not easy. It's not a setting. You need to modify a file, and know what you are doing. The change will be overwritten (reverted) next time the Update Manager itself gets upgraded, so you need to keep redoing the change.

> **Quarkrad said:**
> A family  member uses their machine mainly to check email and do a bit surfing  and they never see the Update window (they are running 12.04). It would  ideal if the update window popped up two or three minutes after  establishing a connection.
From the description, why bother them with updates at all?
Set for automatic (background) security updates only. This keeps their system secure...which seems like all they really need.
It's not difficult for you to go onto their system once every two years to manually upgrade to the next LTS.

> **Quarkrad said:**
> Is there a way to get a pop up window appear on the Desktop at the same time, or instead of, the icon appearing in the launcher bar?
Yes, but it's not easy. You need to understand dbus, and write a dbus service, to use the icon-change signal as a trigger.
It's just as not-easy to uninstall that service entirely, and write your own replacement startup job.

> **Quarkrad said:**
> how do know these updates are happening in thr background?
You will know when the aptdaemon process consumes a non-trivial amount of resources.

> **Quarkrad said:**
> what happens if you shut down part way through an  install of the downloads?
Depends on how you shut down.
If you do it the right way, shutdown will be delayed while the install completes.
If you do it the wrong way, you will break your system.
You are welcome to experiment....I recommend frequent data backups.

---

### Post by Quarkrad on 2013-10-08
Thanks to all.  I don't know whether I'm being too concerned here.  I have converted about 12 family/friends from Windoze to Ubuntu and to a man/women they are more than happy.  Virtually all of them just use their (mainly laptops but some Desktops) machines for surfing and email - so some of them are not using the machine for very long.  There is a mix of classic gnome desktop and unity - but all who are using unity has it auto hides the launcher as it gets in the way of their laptop screen.   When I remotely log into their machines to make sure everything is OK I notice many of them (they all either 12.04 or 13.04) are not being updated.   I have told them to look out for the update icon but I'm having to accept that for what ever reason these users machines are not being updated.   Updating the apps is not important compared to the security updates so hence this thread.  I'm looking for a good solution that doesn't need me to keep remotely logging on to do the updates manually.  The ages range from 40+ to 80+.   I personally use Unity and like playing with my machine so not a problem but I have to accept these machines are not being kept upto date by the users.   They need something in their face re the notification - not a small icon that some of them probably cannot see.

---

### Post by ian-weisser on 2013-10-08
> **Quarkrad said:**
> I have to accept these machines are not being kept upto date by the users.   They need something in their face re the notification - not a small icon that some of them probably cannot see.

Not at all.
Go into Software Sources (Synaptic --> Repositories or Software Center --> Software Sources)
Look at the 'Updates' tab.

Only security updates need to be kept up to date...and that can be automatic.
If they don't care about other updates, that's okay. Don't pester them. Other updates are optional.

---

### Post by DuckHook on 2013-10-09
> **Quarkrad said:**
> Thanks to all. I don't know whether I'm being too concerned here. I have converted about 12 family/friends from Windoze to Ubuntu and to a man/women they are more than happy....welcome to the preaching fraternity. I similarly help out friends and family. Yours is a laudable quest, if I can say so without sounding too self-serving, but it's what's next that has me concerned...> When I remotely log into their machines to make sure everything is OK...If this is not done properly and securely, then it endangers them far more than any amount of neglected updates.

Are you using SSH or VPN? Have you disabled passwords and allowed only keys? And most alarmingly, have you installed VNC? If so, have you disabled passwords and allowed only SSH tunnels? I may be jumping to conclusions here and, for all I know, you've already got these gaping security holes covered. If not, you are highly advised to read [this]("http://ubuntuforums.org/showthread.php?t=510812") sticky, along with the solutions that it links to. Not hard to implement. Can be done remotely in fact.

It's one thing to take chances with our own boxes, but when we take on the responsibility of looking after others, I'm sure you will agree that we must not imperil their security through our actions.

Not trying to hijack this thread. Just trying to help.

---

### Post by Quarkrad on 2013-10-09
DuckHook - thank you for your response.   I have tried SSH/VNC in the past but didn'y have much success as Linux is still a challange - I have been using a commercial product called Teamviewer to remotely log-on and carry out any work.  I know many, from my perspective, 'experts' look after servers using SSH but as I've said it has been a challange to set it up.  If you feel I should be using some ssh based link rather than Teamviewer I would welcome your opinion.  I may have to create another thread if I get stuck (again) setting it up.

---

### Post by ian-weisser on 2013-10-09
I agree with DuckHook. That's good advice.
I went another route.

Perception of privacy is important, too.
Most of our local machines have no remote-login capability at all. SSH server is not installed.
Remote machines have an easy-to-enable login capability under their control. SSH server is installed, but disabled.
And, yeah, Software Sources on all of them (except mine) is set to security-updates-only. A manual upgrade to the next LTS every two years. No complaints.

---

### Post by DuckHook on 2013-10-09
> **Quarkrad said:**
> ...I have been using a commercial product called Teamviewer to remotely log-on and carry out any work.I have no objections to using a commercial product in lieu of SSH/VNC. But I don't use Teamviewer so can give you no advice on its proper use. Others here may be better placed to give such insights. However, no matter what you use for support, it is advisable to implement full-scale security precautions. This includes activating Ubuntu's built-in firewall *UFW*, setting Teamviewer to a high-numbered non-standard port, disabling passwords, allowing only certificate- or key-based connections, etc. These security precautions are very basic for any machine exposed to remote control since unhardened VNCs are one of the primary exploits that crackers use to take over soft targets.> If you feel I should be using some ssh based link rather than Teamviewer I would welcome your opinion.  I may have to create another thread if I get stuck (again) setting it up.You are right that it would be better to start a new thread to discuss SSH. Perhaps I can just give a short response without getting this thread moved. To answer your question: I don't necessarily recommend SSH. I don't find it hard to set up for those whom I help, but that is probably because I am used to it. If you and your clients are used to Teamviewer, and it's already set up for everyone, I don't see any reason to stop using it. As I've already stated, it's not the app you use that concerns me, but how much it has been hardened. Switching to SSH/VNC would be not save you any work when it came to hardening the remote systems.

Hope this clarifies.

---

