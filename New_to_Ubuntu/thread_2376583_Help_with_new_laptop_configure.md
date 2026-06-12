---
title: "Help with new laptop configure"
date: 2017-11-03
forum: New to Ubuntu
---

### Post by pointy2 on 2017-11-03
Hello forumland... I'm looking for suggestions and guidance for a green noob, but teachable.  After switching to a dual boot, Ubuntu 16.04 LTS/Win10, I'm now sold on the brilliance of Ubuntu. Here's the scenario...purchased new laptop with win10 installed as oem. I want to scrub the SSD and do a fresh install of 17.10, and update it to 18.04 LTS when the final version is ready.   I'm leaning on running virtualbox, or VMWare in a separate partition, to access another OS (yet to be determined). Having never installed Ubuntu or a secondary OS, how do I download drivers for the new laptop? Aside from the hardware drivers...sound, wifi, ect, I also want to keep the touch screen and scrolling capabilities (which is not present in the 16.04LTS that's installed along side of Win10.   I'll create a bootable Win10 usb in case I ever need to return to Win (don't know why).  I've created a bootable 17.10 usb for the upcoming project. (will this erase all data an the SSD, or write over it?) I'd prefer to have it all zero'd out.   I noticed that there are many partitions on the Ubuntu side of my current drive. Does the Ubuntu install partition separate packages by default?  My goal is to really 'lock down' the computer for paranoid mode, making it spy and hack proof from a twisted sister (who has the resources in her palm). I've been good at using the repository and terminal for all downloads. The one exception has been my VPN client.   The new laptop  is running an i7 7th gen cpu on a ddr4 motherboard. All bells and whistles are functioning as new. Any comments or suggestions are reuested, and will engage as needed. Till then....

---

### Post by TheFu on 2017-11-03
Nothing is hack-proof if you allow physical access. PERIOD.

I would load Ubuntu letting the automatic installer for full-disk-encryption handle everything.  That will setup the most secure possible setup.  Be certain you like the US keyboard and retain that setup, if you use encryption.  Changing it later will make it impossible to get into the disk.  You'll get LVM this way, which is an amazing tool

Drivers are included.  Linux isn't Windows.  It is best NOT to go out and get drivers from the vendor unless something is broken.

I'd avoid vbox and anything from vmware.  Choose KVM+virt-manager.  It is faster. Spice makes it a nice GUI capability and if you have Intel GPUs, they've been working on GPU sharing between the host and VMs for near-native performance.   gvt-g is their buzzword.  No need for a different partition using any of these hypervisors.

And if you do go with encryption, and you should on every portable device you own, then having encrypted, daily, automatic, backups is mandatory.  If anything bad happens, backups are the only solution to recover your data.

All of this assumes you want to wipe the disks completely.

---

### Post by pointy2 on 2017-11-04
My personal pc is just that...personal. I don't intend on allowing any physical access to my data, especially after a year of dodging an obsessed psychopath. Disc encryption is going to be utilized, even as there wouldn't be anything incriminating for a legal authority...thanks for this recommendation. By LVM, do your reference Logical Volume Manager? I'll study it to get acclimated. I was studying CubesOS and the system reuirements(a certain key doesn't work), and yes, their gvt-g was mentioned as a reuirement for their hypervisors. I'm looking for the method to protect the BIOS from outside attacks from a determined attacker. Are there any suggestions for this?

---

### Post by TheFu on 2017-11-04
vtv-g is NOT a requirement.  It will be a "nice to have" ... when it gets into production mode.  It works with KVM and Xen.  I don't/won't use the others anymore, so I don't follow them.

LVM = Logical Volume Manager  - I've never seen that abbr used for anything else.

To protect a BIOS, use a BIOS password and put some security tap over the screws that open the case.  Also, use SecureBoot and UEFI. These are best practices from the Linux Foundation for workstation security.  Someone CAN modify your boot still, but it will be harder (Nation-state types, not little sisters).  With physical access, almost anything can be hacked.  The most secure, networked, OS that I know is ChromeOS, but that doesn't have any privacy and has lots of other limitations.  

Whoever owns the network you are on can make security much harder. They can control the DNS, which allows them to MITM pretty much all traffic.  This isn't the place to discuss these things. Lots and lots of other forums cover that stuff.

---

### Post by william.hua on 2017-11-04
By "lock down the computer" do you mean the computer entirely or just the VM. If it is your whole computer, use BitLocker. If you want to just "lock down" the VM, you can do that during the install.

---

### Post by pointy2 on 2017-11-05
> **william.hua said:**
> By "lock down the computer" do you mean the computer entirely or just the VM. If it is your whole computer, use BitLocker. If you want to just "lock down" the VM, you can do that during the install.

By lockdown, I meant security to keep an attacker from accessing through the network. ie; establishing a remote connection, installing rootkits, key loggers, ect., reflashing the bios, As far as exploits from physical possession, I'm not too concerned about that. 

I switched to Linux due to the amateurish silliness with games and obnoxiously large codded programs for Win, not to mention the enormous exploits that are prevalent for any bored attention seeker to wreak havoc on innocent users.

---

### Post by william.hua on 2017-11-05
Make sure all the ports for incoming connections on your router/firewall are blocked, unless you are running a server on your network that needs to be accessed from the internet. Also, if your computer supports Intel AMT, I would disable that in the BIOS if you are really concerned. That will prevent someone from trying to flash the BIOS remotely. Also, you can use a BIOS password, but that can be reset fairly easily. Lastly, going back to what TheFu said, physical security should be your primary concern.

---

### Post by pointy2 on 2017-11-05
haven't connected to the net as of yet, and will update/patch (if needed) the BIOS before the scrub and install of Arty Aardvark. I've chosen 17.10 over the current 16.04 LTS on my current lappy, since I want to run the Gnome desktop as native. By the time i get acclimated with it, 18 should be ready for a seamless install. Firewall blocks all, and am not planning to run a server....yet. As for Intel AMT, I was reading about the pros and cons of the tech. I'll refresh on the subject, later.

---

