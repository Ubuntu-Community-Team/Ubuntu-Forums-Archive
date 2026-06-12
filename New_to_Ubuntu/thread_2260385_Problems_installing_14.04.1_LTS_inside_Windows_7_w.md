---
title: "Problems installing 14.04.1 LTS inside Windows 7 with older Ubuntu version present."
date: 2015-01-11
forum: New to Ubuntu
---

### Post by dr-amo on 2015-01-11
I have a HP W7 laptop with an older version of Ubuntu installed, 12.something. I used it infrequently, lost my login info, and decided to install the latest release. I burned a good DVD image of it, configured my BIOS to boot from the disc, and went to install. It opened up and went through the basic setup, I selected the option to install alongside/inside W7, install updates and necessary software, set up internet access, then was prompted to remove the installation disc and reboot. I did so and the typical boot screen popped up. I choose Ubuntu, and the old version pops up asking me to log in with the info I no longer have. What did I miss? How do I get the new version to install and get rid of the old? thanks so much for your help. I grow weary of Windows, but Ubuntu seems to be fighting me.;)

---

### Post by oldfred on 2015-01-11
Along and inside are totally different installs. Which did you do?
If inside with wubi that is not supported anymore.

 Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

But most Windows 7 systems have issues creating a new partition as they use all 4 primary partitions.
      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by dr-amo on 2015-01-11
I installed it inside. The options were inside, or to replace windows and basically reformat the hard drive. So, the latest version will not install on W7 with the supplied wubi software? Hmm. Is this an issue with a W8.1 machine? Thanks for the quick response. I need to look into creating another partition as shown on the links.

---

### Post by Mark Phelps on 2015-01-11
> The options were inside, or to replace windows and basically reformat the hard drive.

That most likely means that your machine already has the maximum of four partitions allocated on the drive.  IF you FORCE the creation of another, you will automatically convert ALL your partitions to Dynamic Disks -- something you do NOT want to do.

Read the links that oldfred provided carefully -- BEFORE you take any more steps.

---

### Post by dr-amo on 2015-01-11
Good advice.

---

