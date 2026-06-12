---
title: "I've lost my panels and can't open the terminal!!"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by kauboy on 2008-05-13
I was trying to install Avant Window Manager and promptly removed my Gnome panels as was instructed. Now, I'm unable to run the AWM due to some compiz-fusion issue and my alt+F1/F2 doesn't bring up the Terminal or the Run Application window either. I'm on Ubuntu 8.04 Hardy Heron. Having lost my panels as well as my keyboard shortcut for the Terminal, I'm afraid I've doomed myself! Any workarounds? I just want to have my old Desktop back. I'll deal with the AVM later. Someone had earlier suggested Ctrl+T for the terminal, that din't work either. Please help! :(

---

### Post by shinobitux on 2008-05-13
Ok, I'll have to do some research to restore gnome but some things you can try at the time being.

How far do you get in the boot process?

Can you still "Ctrl+Alt+F6" or "Ctrl+Alt+F2" and login to a different TTY?

Another thing to do is press ESC at the GRUB men when the computer starts and start Ubuntu in recovery mode.

At the very least you can gain access to all your files by using a live CD and this will allow you to backup your data is you need to.

---

### Post by kauboy on 2008-05-13
I think I was misinterpreted. I'm still working in Ubuntu now as I type. The only problem is : I've lost my panels and I can't open the Terminal, the command prompt. The boot process and login are all perfect. No problem with the files and drives, only that I can't access my main menu.

---

### Post by Inxsible on 2008-05-13
Just to be sure.... Alt + F2 doesnt bring up a run dialog?

if it does, then type in "gnome-terminal" without the quotes in it to get a terminal.

---

### Post by shinobitux on 2008-05-13
Ok, first thing:

Try typing "Ctrl+Alt+(F2 through F6)"

It should display a TTY asking for a login.
Login with your username and password and you should now have command-line access.

"Ctrl+Alt+F7" should return you to your desktop.

Let me know if this works.

---

### Post by shinobitux on 2008-05-13
This is from another thread I'm watching.

> **pearjam said:**
> Try this from the command prompt?

(May have to hit ctrl+alt+f6, then log in as user or su. If already at a command prompt, then type below.)

sudo apt-get update

sudo apt-get -f install

sudo apt-get install ubuntu-desktop

(If you used ctrl+alt+f6 above, then use ctrl+alt+f7 to get out.)

Then reboot. It's worked when something like that happened to me.

Hope that helps!

---

### Post by abn91c on 2008-05-13
right click on the desktop then click on run command the open a terminal  from there

---

### Post by NateMan on 2008-05-13
What guide did you use to disable the panels? It would be very helpful to know what you did to delete both panels since you shouldn't be able to do that. I had a problem with awn during 7.10 where I had one top panel and awn as a bottom panel. AWN freaked out one day and my top panel disappeared. I was able to fix that by hitting alt + F2 and then running metacity --replace. I was never told in my prior install however to remove all panels. A little more information will be extremely helpful in solving your issue. PS- to run the terminal or any other program without a launcher or menu bar alt+F2 opens up a run menu which can be used to run any program with a command.

---

### Post by solitaire on 2008-05-13
Think the posters problem is the bar along the top is MISSING.

Right click on the desktop and select "Create Launcher"
enter in "gnome-terminal" as the command and name. then click OK.

Then click on the icon and see if that opens the terminal.

---

### Post by kauboy on 2008-05-14
Thanks a lot. I created a Terminal Launcher on the desktop and the rest followed. My problem was that I din't know how to get to the terminal without the gnome panels and non-functional keyboard shortcuts.

---

### Post by silberj on 2008-05-31
Thank you so very much. I had this problem and started doing the noob freak out dance. I tried your method and everything restored perfect. Thanks again!!

---

### Post by silberj on 2008-05-31
thank you shinobitux for that post. Your method worked perfectly. I was doing the noob freak out dance when I tried it and settled down quickly. Thanks again.

---

### Post by silberj on 2008-05-31
> **shinobitux said:**
> This is from another thread I'm watching.
thank you shinobitux for that post. Your method worked perfectly. I was doing the noob freak out dance when I tried it and settled down quickly. Thanks again.

sorry for them multiple posts, didn't realize my edits were not refreshing

---

### Post by Craigusus on 2010-10-17
[SIZE=1]Hi,[/SIZE]

[SIZE=1]I know this is a VERY old thread and will probaly be told off for posting, but...[/SIZE]

[SIZE=1]Thank you to [/SIZE][[SIZE=1][COLOR=#000000]shinobitux[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=449897")[SIZE=1] for your information, I was so lost when I booted up and had no panels and no access to the terminal.[/SIZE]

[SIZE=1]Thank you ![/SIZE]

---

