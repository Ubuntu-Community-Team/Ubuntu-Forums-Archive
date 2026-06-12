---
title: "UBUNTU VMM ON SYNOLOGY- Remote Desktop or VNC"
date: 2022-10-24
forum: New to Ubuntu
---

### Post by PrettyMarigolds on 2022-10-24
Hello Everyone,

Running Ubuntu 22.04.1 LTS Gnome 42.4

I have a Virtual machine running on Synology nas. I first have to log into the Synology and directly log into Ubuntu VM.
Once I log in from the nas, I am then able to log in either from Remote Desktop or from VNC. If my session times out or if logged off due to inactivity. I can not log back in from either Remote desktop or VNC. 
I first have to log on from the nas, and after the initial logon I can then use either Remote desktop or VNC.


Any workaround for this??

Thanks

---

### Post by TheFu on 2022-10-24
Use ssh.

---

### Post by ActionParsnip on 2022-10-25
When you say "I first have to log into the Synology and directly log into Ubuntu VM" what does this actually involve? What do you do in the OS once connected?

---

### Post by MAFoElffen on 2022-10-26
More information needed. (Even for ssh)

-What is the virtual host system?
-What is the virtual network switch of that the VM is setup through? If NAT, then that explains why you would have to connect to the Virt Host first, to get to it's VM Guest. If Bridge, then it could be connected to, straight from the host network.

This last, the virtual switch matters whether you are trying to connect to the guest, whether VNC, Xrdp or ssh...

---

### Post by PrettyMarigolds on 2022-10-26
Log into Synology Nas
Open Virtual Machine Manager (VMM)
Click on connect to the Ubuntu virtual machine, which opens a browser window similar to a vnc window which opens to the Ubuntu desktop and I am able to login.
Once I do this I can either minimize the web browser or close it completely. 
Now I can log into Ubuntu from either VNC or Remote Desktop.

I am able to SSH into desktop without first logging in from Synology nas.

---

### Post by TheFu on 2022-10-26
Is the Ubuntu VM running before you try to open it?  If not, look for that setting in the VM settings ... "Start on Boot" or something like that.
I typically don't use VMM, virt-manager, to get a GUI into a VM.

On the same LAN, I use X11 forwarding with ssh to display the application from on my local workstation, but have it running on either a VM or other remote systems on the LAN.

When traveling, I'll use x2go, which uses the NX protocol to securely connect to a desktop (either new or already running) on my VM host from the internet.  Only the ssh port needs to be open.  There are x2go clients for the main 3 desktop OSes. NX uses ssh for authentication and performs 2-3x faster than any other remote desktop.  For a few years, I use x2go to connect to my main Linux desktop from _that other OS_ daily - 14+ hours every day to get real work done.  

Actually, this browser window and my thick email client are running inside a VM workstation that I connect with from my local workstation.  VMs are so flexible that I prefer using them for nearly all applications with just a few exceptions like video editing.
The actual command I use to connect to thunderbird is:
~/bin$ more thunderbird.sh 
```
#!/bin/bash
FJ_OPTS="--dns=172.22.22.80 --rlimit-as=4700000000 "
TB_OPTS="-no-remote "

# limit RAM VSS to 4G
PID=$(ssh -X  regulus /usr/bin/firejail $FJ_OPTS /usr/bin/thunderbird $TB_OPTS $@ & )
exit;

```

but I want to run thunderbird inside a protected sandbox with RAM access limited.  A simple command would be:
```
ssh -X  regulus /usr/bin/thunderbird -no-remote
```
Open a terminal and see if that will work to your remote VM, assuming it is named "regulus" in DNS and has thunderbird installed.  The "-no-remote" option is necessary for Mozilla programs so they don't ask the window manager to only show 1 instance of program X (thunderbird), even if the other instance is running on a completely different system.

If I want to run a terminal on the remote system, but have it on my local GUI, I use this:
```
xterm -geometry 80x22+0+630 -sb -e ssh -X regulus &
```
For me these are scripts and menu items in a custom menu, but there are lots of ways to do it.  I typically use the same 10 systems daily and have a layout for where I want each terminal to be on my 2nd workspace.  If it isn't clear, ssh keys have been exchanged between the client and server, so I'm not prompted more than once each boot to unlock my ssh keys.  ssh-agent makes them available to other hosts as needed.  ssh isn't just more secure, but it is more convenient than nearly any other connection/transfer method that I know.  The NX protocol honors ssh keys, btw.  

The only time I use virt-manager is when I'm setting up a new VM or modifying settings for an existing one.  For day-to-day use, ssh is the main method used.  ssh is how Unix people communication between different systems and if it isn't straight ssh, it is some other tool that is based on ssh.

Just to clarify, is this the tool you are using? [https://virt-manager.org/](https://virt-manager.org/)  That is what we mean by virt-manager, also called VMM or Virtual Machine Manager. It has been a F/LOSS  tool since around 2007.  If Synology has stolen the VMM name for some other tool, I'd be disappointed.

I googled and found this: [https://www.storagereview.com/review/synology-virtual-machine-manager-review](https://www.storagereview.com/review/synology-virtual-machine-manager-review)  which claims to be VMM, but clearly isn't.

---

