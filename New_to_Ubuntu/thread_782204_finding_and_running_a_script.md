---
title: "finding and running a script"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by vinceUUUU on 2008-05-04
Hello forum people,

can anybody help me to run a Linux script?

I have been using the distro called Archie. 

Archie is a live CD......but it also has a HDD install script inside it.


The name of the HDD install script is...............arch-hdinstall (0.2.0pre1)

how do i find this script in the distro?

how do i run this script?

Archie uses similar file search tools to any other distro...

thanks

Vince.

---

### Post by freebeer on 2008-05-04
I don't know anything about what you're doing, but I did find this via Google: [Linky]("http://user-contributions.org/forums/userproject/viewtopic.php?t=316")

Seems that the script is in /etc/archie.  I also took note that in that thread someone said it was buggy.  Maybe if I read more of the thread...

---

### Post by vinceUUUU on 2008-05-05
Hello

thanks very much for your reply

I managed to use the script and run it from root...Archie installed correctly to the hdd....

but the script finally asks me to also install GRUB or LILO...so my machine can boot up..

but i don't know how to install GRUB or LILO (the script does not do it)...

going to try this all again.....anyhow...

thanks

Vince.

---

### Post by bodhi.zazen on 2008-05-05
Arch is a great distro, but there will be little or no hand holding. You are expected to RTFM.

At any rate, it is quite easy to install grub, can be done from almost any live CD or with the supergrub disk.

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

You may need to manually configure /boot/grub/menu.lst

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Last piece of advice, if you are not prepared to google and RTFM perhaps Arch is not the distro for you. The disadvantage of using Archie is that you skipped the installation manual. Installing Arch teaches you to sys admin arch.

[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

You should plan to read that install guide.

---

### Post by vinceUUUU on 2008-05-05
Hello

thank for your reply.

Yes, Arch does mention that it is not for mew people to linux..

however...having now got Archie installed on the HDD it feals close to bieng sorted out.

i realized that the drives must also be re-mounted...so i did this..

the next step is configuring grub menu1.....grub has correctly installed to the hard drive with Archie....but at boot it simple gives a grub prompt...

i need to configure the menu1 file for grub...

this should then get Archie to boot proper from the HDD..hopefully

i feal Arch is good because it is quik.

there is another distro called Crux that is also quik...but can be a little tricky to install

will read your links above

thanks

(my system simply has a clean approach.....the hard drive has HDA1 and swap partitions..... and Archie is installed on hda1

thanks

VInce.

---

