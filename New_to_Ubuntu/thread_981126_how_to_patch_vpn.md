---
title: "how to patch vpn?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Petermet on 2008-11-13
Forgive me, please, if I am needing the sort of help required only by the complete Linux novice, which is what I am! 

I have had the "no secrets" problems configuring the 8.10 vpn pptp applet documented by many others, and have tried applying the pptp network patch provided at [https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/284212](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/284212), using the process outlined at [http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html). 

I think I have got the syntax right, to apply the patch to the correct binary, but I get the following error message in terminal:

"patching file /usr/lib/network-manager-pptp/nm-pptp-auth-dialog
Hunk #1 FAILED at 23.
Hunk #2 FAILED at 78.
Hunk #3 FAILED at 166.
3 out of 3 hunks FAILED -- saving rejects to file /usr/lib/network-manager-pptp/nm-pptp-auth-dialog.rej"

Can someone please advise? 

Thank you very much indeed.

---

### Post by quirks on 2008-11-13
Can you give me the precise permalink to the post where you downloaded the patch from? On Launchpad, every post has a small hyperlink titled "permalink" in the header of the post.

Can you post the exact commands, which you ran?

---

### Post by Petermet on 2008-11-13
Thanks very much. This is the link.

 [https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/284212/comments/20](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/284212/comments/20)

I hope it helps.

---

### Post by Petermet on 2008-11-13
Sorry - and this is the precise command copied from terminal:

peter@Lenovo:~$ sudo patch -p1 /usr/lib/network-manager-pptp/nm-pptp-auth-dialog keyring_memory_free.patch
patching file /usr/lib/network-manager-pptp/nm-pptp-auth-dialog
Hunk #1 FAILED at 23.
Hunk #2 FAILED at 78.
Hunk #3 FAILED at 166.
3 out of 3 hunks FAILED -- saving rejects to file /usr/lib/network-manager-pptp/nm-pptp-auth-dialog.rej
peter@Lenovo:~$ 

The .rej file appears in the folder in the file browser, so the command is evidently accessing the file.

---

### Post by quirks on 2008-11-13
```
peter@Lenovo:~$ sudo patch -p1 /usr/lib/network-manager-pptp/nm-pptp-auth-dialog keyring_memory_free.patch
patching file /usr/lib/network-manager-pptp/nm-pptp-auth-dialog
```
This is wrong: you do not apply a patch to an already compiled program. A patch is a collection of changes to the source code of a program. It is a plain text file, which tells the "patch" tool what lines in the code to modify. At the beginning of the patch file, it tells the patch tool, what files of the source code to modify. If you read further through the patch file, you can see that some lines start with a "-" and others with a "+". A "-" symbolizes deletion of a line and a "+" addition of a line. All the patch tool does is apply these rules to the source code. But not to the compiled program. That is why the tool fails with all those "Hunk #x FAILED at xx" messages. So much about patching in general.

Now to your specific case:
The patch that you linked to was written for network-manager 0.7. This is the version used in Intrepid. Do you have Intrepid or do you still use Hardy? If you don't use Intrepid, we can stop right here, because then you do not have a chance to get it to work. If you do use Intrepid, you can download the source of the package using the following command:
```
cd ~/Desktop
apt-get source network-manager
```
This will download the source to your desktop. Then you can apply the patch in the same fashion that you already attempted - but this time to the proper file!
```
patch ~/Desktop/network-manager-0.7~~svn20081018t105859/vpn-daemons/pptp/auth-dialog/main.c ~/Desktop/keyring_memory_free.patch
```
After that you can compile your patched program and install it. If you need help with that, too, just ask. There are plenty of people out there who can assist you - including me.

---

### Post by Petermet on 2008-11-14
Thank you very much indeed for your very clear and helpful explanation! I greatly appreciate it. I'll try to do exactly as you say. I will certainly need instructions on how to compile and install the patched program, once I've completed the steps you outline, and if it's not too tedious for you, would be equally grateful for instructions on that. I am using intrepid, btw.

---

### Post by Petermet on 2008-11-14
Following your kind instructions I have downloaded and patched without error (!) and would be grateful for guidance on the next stages of compiling and installing, at your convenience.

---

### Post by quirks on 2008-11-14
Sorry for the delay. I have been trying all day to compile the program. It was a tough one, but I finally got it to work. The procedure is a little complex. But as the result of my attempts, I created a ready-to-install Debian-package for you (see attachment), so you do not have to do this again yourself. It replaces the network-manager-pptp package with my self-made version (0.7.0-quirks-1). Let me know, if this version (which has the patch applied) solves your problem. If you have trouble installing the package, tell me and I will show you the procedure for compiling the program yourself. I would be thankful for a quick response as I am currently using a LiveCD, which is the only way I can work with an Intrepid system. And during that time, I cannot use my actual (Hardy) installation.

In case it works, I recommend locking down the version of this package, so that it will not get overwritten by updates. If you do not know how to lock down a version, I can show you as well.

---

### Post by Petermet on 2008-11-14
Wow! Thank you so much! I also tried intermittently to compile and install via terminal, using directions accessed at various places, but without success. You are too kind! I have downloaded the deb, and would indeed be very grateful to know how to lock and (while you are at it) install and/or compile it. I can't tell you how much I appreciate your help!

---

### Post by Petermet on 2008-11-14
I'm just leaving my office for home (UK) - will be back online in about 45 minutes.

---

### Post by quirks on 2008-11-14
Glad to here, I could help you. Have you already tested, if this really fixes your problem? Or have you only installed it so far?

If it all works, I do not recommend compiling it again. But just in case you are interested, here are the steps (might be helpful if you want to compile something else in the future):

1. Download the Ubuntu development tools:
```
sudo apt-get install build-essential
```
This is a meta-package, which depends on common tools needed to build/compile stuff.

2. Download the header files of depending packages. The source code of Network Manager makes use of the source files of some other packages. And those are needed during compilation. Otherwise the compiler would return errors, saying that it does not know the meaning of some functions/variables/constants/etc.
```
sudo apt-get build-dep network-manager
```
You can use this with any package. The apt-get then tries to figure out what dev-packages are needed to compile the package in question. But sometimes, it forgets some - for example in this case.

3. For that reason, you will need to download the following package manually:
```
sudo apt-get install libnm-glib-dev
```

4. Patch the source code as explained in my previous posts.

5. Move to the following directory of the network-manager source code:
```
~/Desktop/network-manager-0.7~~svn20081018t105859/vpn-daemons/pptp
```
This is where the code of the network-manager-pptp package is located.

6. From there, run these commands:
```
./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install
```
This will compile and install the program on your system. I found these commands on the NetworkManager developer page: [http://projects.gnome.org/NetworkManager/developers/](http://projects.gnome.org/NetworkManager/developers/) Usually, the first command is different. That is why, I was stuck at the beginning myself.

Optional:
In Ubuntu (and most other Linux distributions) software is organized in packages. This helps keep track of versions/conflicts/etc., plus you can uninstall it easily. If you want to put the program into a package, do the following.

7. Install a program, to build Debian packages:
```
sudo apt-get install checkinstall
```

8. You must still be in the same directory as in step 5, then:
```
sudo checkinstall
```
Follow the instructions (should be self-explaining). Make sure that you name the package "network-manager-pptp". Otherwise, Synaptic will show a conflict error with the original network-manager-pptp package, when you try to install it. After that, you can find a .deb package in that directory. Also, when you open Synaptic, you will see that the package is installed. And you can uninstall it from there again.

To lock down the version, do this:
1. Open Synaptic.
2. Find the package and highlight it.
3. Go to Package -> Lock Version.
It should be highlighted red, and a padlock should appear as an icon.
From time to time, you ought to check the release notes of NetworkManager. When they finally publish the fix, there will not be any need for your self-made package anymore. And you can receive udpates again.

---

### Post by Petermet on 2008-11-14
Sorry for the delay in getting back to you. I had to try installing once I got home. The bad news - it seemed to open and install, but I get an error message "There was a problem launching the authentication dialog for VPN connection type 'org.freedesktop.NetworkManager.pptp'. Contact your system administrator."

---

### Post by quirks on 2008-11-14
When exactly does this happen? I cannot test every aspect of the NetworkManager plugin, because I do not use VPN connections. All I can say is that the dialog for adding new VPN/PPTP connections shows without errors. Does this work for you?

---

### Post by Petermet on 2008-11-14
Thanks - I was just having dinner, so apologies for delay in responding. Yes. The popup window for adding new vpn's appears as it did before, and the error message is as it was - i.e. if I enter a password the small popup below the network indicator gives the "no secrets" error message.

---

### Post by quirks on 2008-11-14
I don't know, if it is necessary to reload NetworkManager (would make sense). Have you rebooted ever since the installation, so that the new version is used?

---

### Post by Petermet on 2008-11-14
Yes, I have rebooted. I will try a complete re-install of Network manager and see if that helps. But I think we may not be able to solve this and it might be best not to trouble you further with it - you have been exceptionally kind and helpful!

---

### Post by quirks on 2008-11-14
Too sad ... I hope they release the fix soon, so you (and others) don't have to bother with compiling and stuff, anymore.

One last question: you are working on a 32bit platform, right? Because I compiled my package for that architecture.

---

### Post by Petermet on 2008-11-14
Well, I thank you very much anyway for your very generous and patient help! I am entirely new to Linux as you will have realised but I am keen to learn, as it is very attractive to be able to really know what is going on behind the GUI. I am using 32 bit i386 - yes. All the best - will wait for an update.

---

