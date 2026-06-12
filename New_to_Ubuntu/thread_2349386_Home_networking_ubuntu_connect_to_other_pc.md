---
title: "Home networking ubuntu connect to other pc"
date: 2017-01-14
forum: New to Ubuntu
---

### Post by linux1pacman on 2017-01-14
Hi There Im running ubuntu 14.04lts  64bit , I cant get this os to open my other windows network computers get the prompt for password every time. Ive played with the samba conf and tried to setup I have no passwords on any other pc but it keeps asking for one. Tried it with 16.04lts same issue
I dual boot into windows 7 and have no problem connecting. I use to run ubuntu 12.04lts and had a smaller issue with failed to receive share list and added the [COLOR=#1A1A1A][FONT=consolas]name resolve order = bcast host
[/FONT][/COLOR]:mad: I added this to the global part of my samba conf and it worked . I would just click on the pc in places/network and wallah but now ive got the password required window why is linux so hard to do basic home network:confused::confused::confused:

---

### Post by TheFu on 2017-01-14
Welcome to the forums.

Not sure I understand the issue. 
Try this first: [https://www.unixmen.com/how-to-access-remote-linux-and-windows-shares-with-gigolo/](https://www.unixmen.com/how-to-access-remote-linux-and-windows-shares-with-gigolo/) - Gigolo
[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide) is how to mount Windows shares from an Ubuntu machine.
and [https://help.gnome.org/users/gnome-help/3.22/nautilus-connect.html.en](https://help.gnome.org/users/gnome-help/3.22/nautilus-connect.html.en)

IME, most system-to-system connection issues are caused because home users don't manage their network in the way Unix systems prefer.  
* Every machine wants a name. 
* Every machine wants to _know_ the name of the other machines on the network. 
* Each machine should be able to 'ping' the other machines by name. 
There are lots of work-arounds, but nothing works as well as having static IPs setup for each machine and that data inside the /etc/hosts (even on Windows).  Linux is not windows. Expecting it to work the same way is asking for frustration.

Projects have attempted to make this "finding each other" easier over the years.  There are DHCP Reservations which can be managed at the home router, many devices support this, but not all.  There is avahi - which seems to work better now (previously it had major issues). I don't use avahi.

If mounting by name doesn't work, use the IP address instead.

If you want to access storage on the Ubuntu PC from other computers and samba isn't working, use sftp (WinSCP or Filezilla).  Just install openssh-server and fail2ban on the Ubuntu machine to get that working.  From Linux, you can use sftp:// ... URLs to sftp servers.  Plus, ssh/sftp/scp/sshfs are all considered secure enough for use over the internet, unlike samba.

---

### Post by linux1pacman on 2017-01-14
Thefu WOW Thank you Thankyou so much Ive been trying to connect my home network for 10mths, just a simple password entry after I got onto Gigalo.
 here`s what I did

Step 1 backup samba conf then configure samba config with the section under global under workgroup = WORKGROUP put name resolve order = bcast host
and #   wins support = no change to yes
and under Authentication obey pam restrictions = yes change to no
save samba conf 

step 2 Make sure on your windows devices you have folder shares with full permissions as everybody restart all (windows) machines 


step 4 If you get error when saving samba config, On Ubuntu system open terminal and enter these 2 commands
sudo apt-get purge gedit
sudo apt-get install gedit


step 5 Optional Install Gigalo open terminal
sudo apt-get install gigolo gvfs-fuse -y


In Gigalo, I found the option for windows shares and connected using step 7


good guide [https://www.unixmen.com/how-to-access-remote-linux-and-windows-shares-with-gigolo/](https://www.unixmen.com/how-to-access-remote-linux-and-windows-shares-with-gigolo/)


step 6 Now this is why I had the password problem. My machines except my Ubuntu dont have passwords. so I was leaving the password blank when trying to connect to other machines, I entered my ubuntu password and strangely enough I could open my windows network shared folders so to access your home network from ubuntu I had to give it permissions crazy but worked for me.

---

### Post by TheFu on 2017-01-14
Your last post will confuse others. Please correct it.

gedit has NOTHING to do with this. 
Step 1 is unimportnat.
Step 4 is unimportant.

I didn't need to restart anything. That seems to be a Windows-ism left over that people think it is needed. It isn't.  I don't reboot systems unless there is a new kernel. It really is that simple.

Those steps aren't necessary.  The smb.conf file has NOTHING to do with these either.  I don't even have samba installed on my box. Installing Gigalo brought in the dependencies.

If it is working for you, please mark the thread as "solved" to help others looking for an answer and prevent folks wanting to help from wasting their time.

---

### Post by linux1pacman on 2017-01-14
thanks I edited post, this is what worked for me I dont believe installing gigalo was the problem as I dont need to use gigalo to access home network. I can access by going to places then click on network im using gnome desktop not unity.

---

### Post by TheFu on 2017-01-15
> **linux1pacman said:**
> thanks I edited post, this is what worked for me I dont believe installing gigalo was the problem as I dont need to use gigalo to access home network. I can access by going to places then click on network im using gnome desktop not unity.

gigalo and gvfs tie into nautilus, the file manager, under the covers. [https://ubuntuforums.org/showthread.php?t=1958655](https://ubuntuforums.org/showthread.php?t=1958655) by Morbius1 explains.

Being a member of "fuse" group doesn't seem to be necessary anymore. Probably due to systemd handling mounts, but I don't really know. Just know that I'm NOT a member of fuse and the group doesn't exist on my 16.04 box.

---

