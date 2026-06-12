---
title: "Oneric not saving sound settings"
date: 2011-09-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by alphacrucis2 on 2011-09-26
I notice after upgrading to 11.10 that the sound reverts to full volume on reboot. In previous versions the volume was restored to whatever it was previously set to. Anyone else seeing this issue.

---

### Post by FerroPower on 2011-09-26
I too upgraded to 11.10.

Sound is working the way it should. maybe something wrong with your settings.

---

### Post by alphacrucis2 on 2011-09-26
Problem was solved by removing the hidden folder .pulse in my home directory. The folder was recreated on restart and now the volume level is remembered correctly.

---

### Post by bbrg548 on 2011-09-26
> **alphacrucis2 said:**
> I notice after upgrading to 11.10 that the sound reverts to full volume on reboot. In previous versions the volume was restored to whatever it was previously set to. Anyone else seeing this issue.

I am seeing this also. I've reported it as [Bug #860153]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/860153").

Edit: Okay, you posted the fix while I was reporting the bug.:) It also worked for me, so I've updated the bug report to show the fix, but left the status for the devs to decide.

Did you have a fresh install, or was it an upgrade from Natty? Mine was an upgrade, and I wonder if it's something the upgrade-tool isn't cleaning up properly.

---

### Post by cariboo on 2011-09-26
> **bbrg548 said:**
> I am seeing this also. I've reported it as [Bug #860153]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/860153").

Edit: Okay, you posted the fix while I was reporting the bug.:) It also worked for me, so I've updated the bug report to show the fix, but left the status for the devs to decide.

Did you have a fresh install, or was it an upgrade from Natty? Mine was an upgrade, and I wonder if it's something the upgrade-tool isn't cleaning up properly.

The upgrade tool never has cleaned up your personal settings in /home/$USER, and it shouldn't. Can you imagine the outrage, even more so than removing gimp and synaptic from the default installation, that would arise?

---

### Post by alphacrucis2 on 2011-09-26
> **cariboo907 said:**
> The upgrade tool never has cleaned up your personal settings in /home/$USER, and it shouldn't. Can you imagine the outrage, even more so than removing gimp and synaptic from the default installation, that would arise?

Well given that you have to delete settings/preferences files to get this particular thing to work properly then you aren't exactly better off for the settings being left alone. The ideal way would be for the developer to cater for import/conversion of old settings files as part of the upgrade process.

---

### Post by bbrg548 on 2011-09-27
> **cariboo907 said:**
> The upgrade tool never has cleaned up your personal settings in /home/$USER, and it shouldn't. Can you imagine the outrage, even more so than removing gimp and synaptic from the default installation, that would arise?

It's not something I would think would be a "personal setting" in the first place. It worked correctly in Natty, and I did a normal upgrade to Oneiric. My Natty install was a fresh install, complete with formatting the partition, and I never changed any of my sound settings at all (other than normal volume changes) between that install and posting here.

That's why I asked if it was a fresh install or an upgrade - to clarify where the problem might be originating. Deleting the file might simply fix the problem but not the cause, or there might be a single line in the default setup from Natty that can be easily checked for and changed when updating. More information helps.

---

### Post by cariboo on 2011-09-28
> **bbrg548 said:**
> It's not something I would think would be a "personal setting" in the first place. It worked correctly in Natty, and I did a normal upgrade to Oneiric. My Natty install was a fresh install, complete with formatting the partition, and I never changed any of my sound settings at all (other than normal volume changes) between that install and posting here.

That's why I asked if it was a fresh install or an upgrade - to clarify where the problem might be originating. Deleting the file might simply fix the problem but not the cause, or there might be a single line in the default setup from Natty that can be easily checked for and changed when updating. More information helps.

Anything in your home directory is a personal setting, to prove this, revert to the original pulse audio setting, then create a new user, and check to see if you have the same problem, and if the file/directory has the same content.

---

### Post by bbrg548 on 2011-09-28
> **cariboo907 said:**
> Anything in your home directory is a personal setting, to prove this, revert to the original pulse audio setting, then create a new user, and check to see if you have the same problem, and if the file/directory has the same content.

I'm not doubting that it *is* a personal setting, I'm just surprised that something in the personal settings (rather than the systemwide settings) is behind this since I was running an unaltered stock install when I upgraded - there should have been nothing to "clean up" that the upgrade-tool shouldn't know about and be able to handle.

Given the nature of the "fix", I doubt this would occur at all in a fresh install of 11.10, but it would be good to know so the devs can have that information if they decide to troubleshoot it.

I expect something in pulse audio itself changed between distributions to make it interpret some setting differently (or to not recognize it). In a fresh install those settings are created by the new version of pulse audio, and the user doesn't have the problem, but in an upgrade the settings created by the previous version are kept, and the problem occurs. It could also be an issue with certain hardware and not others, which would explain why alphacrucis2 and I both experienced it but FerroPower did not, when all three of us upgraded.

As I said before, more information is better.

---

