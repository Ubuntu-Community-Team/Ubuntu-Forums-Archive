---
title: "How to log into the console as root"
date: 2006-12-07
forum: Outdated Tutorials &amp; Tips
---

### Post by loyeyoung on 2006-12-07
[SIZE="5"]**How to log in as root**[/SIZE]

This How-To is based on Kubuntu (i.e., Ubuntu with the KDE Desktop instead of GNOME). Similar techniques may be employed in the GNOME environment.

If you are like me, you tire of typing "sudo" every time you want to execute a command as root, especially when building your box for the first time. It's much easier just to open a console as root. 

There are three methods, which I list in increasing order of effort:

1. Hit Alt-F2, which brings up the "Run Command" dialog box. Type:
```
kdesu konsole
```
Another dialog box will pop up asking for your password. Type in your own password. When Konsole opens, you will note that you are logged in as root.

2. If you already have Konsole open: 
[LIST]
[*]Click on the Session drop-down menu at the top of the Konsole window. 
[*]Select "New Root Shell". A new tab in the Konsole window will open up. 
[*]Type in your own password when prompted and press Enter.
[/LIST]
This method is convenient for going back and forth between root and regular user. 

3. If you are regularly tinkering with your system (you may if you are administering a server or a box used by several people), you can set up a "Konsole ROOT" menu item: 
[LIST]
[*]Right click on the KMenu (the big K at the lower left corner of your screen), and select "Menu Editor". 
[*]Find the menu item for Konsole, which is in the "System" sub-menu unless you've been rearranging your menu already. 
[*]Right click on the Konsole item and select "Copy". 
[*]Right click on the System sub-menu and select "Paste". You will now have a second Konsole item, which will have the name "Konsole-2". 
[*]Edit the name to something bold and snazzy like "Konsole ROOT". 
[*]Edit the little box called "Command" to be "kdesu konsole". 
[*]Check the box that says "Run as a different user". The Username box will light up; type "root" in the text box. 
[*]SAVE your changes by pressing Cntl-S, clicking on the Save toolbutton, or selecting Save from the File menu. Close the KDE Menu Editor.
[*]When you want to log into the console as root, click on your brand-spanking new menu item. KDE will ask you for your password once and then present you with a console terminal as root. 
[/LIST]

Actually, my personal preference is to enable the root user account (go to System Settings and open up the User Management module) and give root a complex password that's different from my own. That enables me to log into the root account in single user mode (i.e., using the Rescue boot option in GRUB), without logging into KDE. It also enables me to use "su". I believe that an enabled root account with a complex password is more secure than strict reliance on the "sudo" method, but that's a long argument for another thread.

If you REALLY want to log into KDE as root, first enable the root user account as described in the previous paragraph. Then edit (as root) /etc/kde3/kdm/kdmrc. Find the line that says "AllowRootLogin=false" and change it to "AllowRootLogin=true". Log off and restart your X session.

WARNING WILL ROBINSON!! DANGER!! 
Exercise good judgment. A root password in the hands of a lazy, ignorant, stupid, or evil person is dangerous. Don't be one of them. 

Some believe that you should NEVER log into a graphical user interface as root, because (in their opinion) GUIs are inherently insecure. My belief is that all root activity is insecure to some degree and a GUI is helpful if you are rusty on something or a noob. Do what root needs to do, taking common sense precautions, and log root off. Meanwhile, try to learn some command line techniques along the way so that you can use the console. 

For the same reasons, it's also a bad idea to leave a root console running unless you are actually working with it. Do your business and exit. If your "friend" in the cube next to yours decides to "help" you while you are down the hall taking care of business, you are a sitting duck for whatever malfeasance your friend may have in mind. Also, if you happen to have VNC or other remote access enabled, it's possible someone with the VNC password could take control of your root console without touching your keyboard. 

STANDARD ADMONITIONS: Use complex passwords. Don't give your personal password to anyone. Don't give the root password to anyone except your boss, and then only if your boss needs it. Use the root account as little as possible. Don't browse the Internet as root. Don't run as root any product made by or for Microsoft. YHBW (You Have Been Warned). 

Vaya con Dios,

Loye Young
Laredo, Texas

---

### Post by aysiu on 2006-12-07
I think you're forgetting just about the easiest way to get a root Konsole: ```
sudo -s
```

---

### Post by loyeyoung on 2006-12-07
No, I didn't forget. *I didn't know* about the -s option on sudo. Learn something everyday. 

Thanks for the tip!

Loye Young
Laredo, Texas

---

### Post by aysiu on 2006-12-07
You can read more here:
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by TheWizzard on 2006-12-08
> **aysiu said:**
> I think you're forgetting just about the easiest way to get a root Konsole: ```
sudo -s
```

and again i learned something :D 
i always used ```
sudo -i
```, but this takes you to the root's home dir. thanks for the advice!

---

