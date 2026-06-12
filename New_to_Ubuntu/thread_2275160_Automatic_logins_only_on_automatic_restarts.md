---
title: "Automatic logins only on automatic restarts"
date: 2015-04-24
forum: New to Ubuntu
---

### Post by TheBigBean on 2015-04-24
I suspect this is not possible, but I thought I would ask to double check. 

I have a desktop running Lubuntu 14.04 sitting in an office. It is currently turned on all the time and I back-up stuff to it with Syncthing. I would like to be able to protect the data on it in the event someone walked into the office and stole it (thus powering it off at the same time). I could add an encrypted directory, but I would also like updates to continue to install and all the automated re-starts to happen without requiring a person to be physically present to input the password. Is it possible?

Many thanks in advance.

---

### Post by ian-weisser on 2015-04-24
Is it possible for your system to restart automatically after a  restart-requiring upgrade? Yes, but it requires a bit of tinkering and  is usually not worthwhile. Only kernel and kernel-related upgrades require a restart (and soon not even those!)
Is it possible to encrypt individual data files (or a /home/USERNAME directory) without encrypting the entire system? Yes.
Is it possible for your system to automatically upgrade without anybody logged in? Yes, that is the default behavior already.

Is it possible for your system to automatically access (decrypt) encrypted data without human approval? Generally not - that would defeat the purpose of encrypting data. However, it's easily possible to sync encrypted files *without decrypting them*.

Automatic login is a convenience - if the machine is physically accessible by others, then don't use it.
Use the login screen for it's intended purpose - to protect each authorized user's account and data.
Use the guest account for it's intended purpose - limited access for untrusted users.

For the specific use case you discuss - backing up encrypted files to a laptop -  my simple personal solution would be to encrypt each file before backup. I would not login to the laptop unless using it. Logging in would not decrypt any files - I would decrypt/encrypt on the laptop manually as needed. I'm not a fan of whole-disk encryption nor /home-dir encryption yet, file-level envryption is what I'm comfortable with, so of course that colors my suggestion.

You could encrypt your entire /home/<you> directory...but then you wouldn't be able to autologin to that account.
It's also simple to sync backups to a remote machine without staying logged into the remote machine.

Many other solutions are possible. That's what would work for me; might (not) be a desirable solution for you.

---

### Post by TheBigBean on 2015-04-27
Many thanks for your detailed response. It is very helpful.

I hadn't considered encrypting before I back up. That might be a solution, but it will need some thought.

---

### Post by newb85 on 2015-04-27
I'm not sure I understand the push for encrypting individual files instead of the /home directory or the entire partition.  Automatic update installation occurs regardless of who is logged in.  However, the system won't automatically restart.  (It's not like Windows, where you get a popup saying "The system will restart in 30 seconds" every so often and you have to keep preventing it if restarting is currently undesirable.  Ubuntu waits for your approval to restart.)

Also, be aware, the default behavior is *not* for all updates to install automatically.  It's for security updates to install automatically.  If you want to automatically install *all* updates (from the repos), you'll need to take an approach like installing unattended-upgrades.

My opinion: set the updates however you want them.  Don't use any automatic login.  Don't think in terms that having to type your password is nuisance.  (Is having to unlock your car in a busy city a nuisance?)  If you don't trust everyone who has physical access, make sure it locks when you leave.

---

### Post by TheBigBean on 2015-04-27
Thanks for your comments newb85. I think I may have misunderstood how the updates work. My other version of Lubuntu 14.04 (which has the default update setting) rivals windows in terms of requesting regular updates and requiring restarts, are you saying that these updates are not necessary for security reasons? If so, then I think the solution you detail would work quite nicely: disable auto-login, lock it when I'm not around and restart once in a while to install the non-security stuff. I'm just trying to avoid the situation where either it stops syncing in the middle of the night or fails to get security updates.

With regard to encryption of the entire /home versus a single folder, it makes little difference to me in terms of what is being encrypted, but from what I read it is likely to be easier to implement now given that I didn't choose the option on installation.

Finally, I probably should just play around with the settings and see what happens, but changing the auto-login setting / lock screen setting isn't as easier as I expected!

---

### Post by newb85 on 2015-04-27
Let me clarify.  Ubuntu and Lubuntu's updates work the same way.  There are security updates, recommended updates, proposed updates, and backported updates.  The security updates address issues that are security-related.  The recommended updates are things like bug fixes, which improve the performance of applications, but aren't necessary to stay on top security-wise.  Proposed updates are updates that are planned for a future release, but haven't run the gammit of testing and approval.  Backported updates are updates that have been approved and included in a release subsequent to the one you're using.  (E.g., if you're using 14.04, enabling backports will give you the updates in 14.10 and 15.04.)  

In Software & Updates (which can be accessed directly from the Dash, from System Settings, from Software Center, or from Software Updater), you can chose which of these are enabled.  You should definitely use security updates.  Proposed updates can make your system unstable, so it's probably best to avoid them.  Recommended and backports are optional.

You can also chose how security updates are handled and how all other updates are handled.  If you want, you can have all security updates automatically installed in the background without notifying you or needing approval.  (It will ask for approval before restarting whenever there are kernel updates.)  With other updates, however, you can only have them automatically downloaded in the background and displayed for your approval.  Automatic installation is not an option in the default install; however you can change this by installing unattended-upgrades, which will automatically install all updates in the enabled repositories regardless of your selections in Software & Updates.  Note That with unattended-upgrades, you will still be prompted for restarts, but everything else will be handled in the background, with the exception of updates from PPAs.

You are correct that Ubuntu is similar to Windows in that it prompts to install updates and then (occasionally) for restarts.  It differs, though in that you can push the updates to the background, if you so choose.

Hope that helps.

Also, auto-login and lock screen settings should be very easy to change.  Under System Settings, click User Accounts.  If you hit the unlock button in the upper-right corner and enter your password, you can throw the switch for whether your user is automatically logged in.  Under System Settings, click Brightness & Lock.  There you can set an inactive time limit for the account to lock.  Also, you can always manually lock the account with Ctrl+Alt+L.

---

### Post by ian-weisser on 2015-04-27
> **TheBigBean said:**
> I'm just trying to avoid the situation where either it stops syncing in the middle of the night or fails to get security updates.

newb85 is right - your Windows update experience *does not apply here*. It's leading you down a path that's both complicated and unnecessary.

When Ubuntu prompts you for a restart, most updates have *already been applied*. If you ignore the restart and open an application, you will get the *fixed* version of that application. The restart is merely to boot you into an updated kernel. Rebooting does not 'apply' any updates. Those happened in the background while you were working.

It's really simple for you: When you see a 'restart is required' prompt, it's a low priority task. Keep working. Reboot when you are finished - at lunchtime or at the end of your workday.

---

### Post by newb85 on 2015-04-27
> **ian-weisser said:**
> It's really simple for you: When you see a 'restart is required' prompt, it's a low priority task. Keep working. Reboot when you are finished - at lunchtime or at the end of your workday.

Precisely.

---

### Post by TheBigBean on 2015-04-28
Thank you both very much. That is exceedingly useful information and far more detailed and informative than I could possibly have hoped for.  It is all clear to me now. My apologies for my Windows style thinking.


> **newb85 said:**
> 
Also, auto-login and lock screen settings should be very easy to change.  Under System Settings, click User Accounts.  If you hit the unlock button in the upper-right corner and enter your password, you can throw the switch for whether your user is automatically logged in.  Under System Settings, click Brightness & Lock.  There you can set an inactive time limit for the account to lock.  Also, you can always manually lock the account with Ctrl+Alt+L.

I think this is where Lubuntu is different from Ubuntu. Basically it doesn't seem to work as intended, but I found some solutions on the internet e.g. I have changed a file in /etc to prevent autologin and I have added light-locker to the list of software that runs on start-up. It mostly works now, but it is an area that Lubuntu could probably refine a little!

---

