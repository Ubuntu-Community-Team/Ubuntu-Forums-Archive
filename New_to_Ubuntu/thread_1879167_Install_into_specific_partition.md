---
title: "Install into specific partition"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by Kubischbuntu on 2011-11-11
Hi,

I want to install 11.10 (64) into a separate partition while keeping my existing setup . I have already made some space on the HDD. When I start the install it only gives me the option to wipe the entire drive or to go manual - when I select to go manual it goes to a screen that looks a lot like partition management tool (creating, editing, resizing partitions) - however what this tool doesnt seem to have is a button to indicate which partition I want it to go into - any ideas?

Cheers

Andreas

---

### Post by coffeecat on 2011-11-11
The manual option is now called "something else" in 11.10. Choose that and you are presented with a list of all your partitions. Highlight the one you want to use to install Kubuntu 11.10 to and either right-click on it or click on the change/edit button below the partition list. (I'm going from memory - I can't remember whether the button is "change" or "edit".) A new window will open where you can select the filesystem type ("use as"), whether or not you want to reformat it, and the mountpoint. Select '/' if this is your root partition. 

If there are any other partitions on your drive you want mounted on bootup, select them and you can type in a custom mountpoint in the mount field. Obviously, if one is a data or pre-existing home partition, do **not** tick the format box! When you've finished selecting all the partitions you need, double-check what the installer is going to do with each partition, to be sure you haven't told it to reformat a partition you don't want reformatting. If you have a pre-existing swap partition, the installer will pick that up automatically for you. If you don't have a swap partition it will complain if you don't create one.

---

### Post by Kubischbuntu on 2011-11-11
Thanx for that coffecat - one thing I am still not sure about is - how does the installer know which one of the root mounted partitions it should be installing to? Due to the fact that I already have 2 other versions of Ubuntu installed on this machine - following your instructions I would end up with 3 partitions mounted at root but only one of them I want the installer to touch

---

### Post by coffeecat on 2011-11-11
The installer will only know which partition to use as the root partition by you telling it so, as I described before. An installation can have only one partition mounted as root. If you already have two installations of Ubuntu on other partitions, these are only root partitions when running those installations. If you install Kubuntu to a third partition you won't have three root partitions; you'll have three independent installations each with their own root partition. Independent, but they can share the swap partition and the /home partition if you have a separate /home.

Did you want three (k)ubuntu installations on your machine or were you intending to replace one of the two current ones with your new Kubuntu installation?

---

### Post by Kubischbuntu on 2011-11-12
Thanx that told me what I need to know - and it did what I wanted it to do. I know it sounds strange but I actually want 3 versions on this machine - different things seem to work in different versions - plus with the one I just installed now I went to 64 bit (rumor has it that this now plays nice with 32 bit apps)

---

### Post by coffeecat on 2011-11-12
Not at all strange! :) I like to keep both the current and immediately previous versions up-to-date and running, which means I have Natty and Oneiric on adjacent partitions, and have other partitions ready for trying out other desktops and/or distros.

I've been using 64-bit for more than 2 years now and have not had any problems that I am aware of.

Good luck!

---

