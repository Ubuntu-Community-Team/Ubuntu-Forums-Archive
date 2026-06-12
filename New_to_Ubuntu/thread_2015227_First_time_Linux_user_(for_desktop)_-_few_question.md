---
title: "First time Linux user (for desktop) - few questions"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by Red Squirrel on 2012-07-02
Rather than make a whole bunch of posts, I have a few questions and I'll just post them here.

First off, as some intro, I'm not new to Linux itself, I run several servers at home and one dedicated online, and I'm fairly comfortable with the server side of things.  Apache, mysql, postfix, dovecot, rsync backups, cron etc....  I still consider myself intermediate and not advanced though.  I finally decided a few days ago, it was time to make the switch for my desktop.  I've been wanting to do this for a while and it feels great. 

So anyway, I'm running Xubuntu, and got a few issues/questions.  If you rather I make separate threads I can, but thought these are probably rather simple fixes that it may be better off in one. 


1: When I first boot, the screen is black for about 30 seconds.  From what I imagine, it's the loading process.  Is there a way to show what's going on?  It always makes me nervous as it looks like it failed to boot.  The first time I actually reinstalled it because I thought it did not install properly.  

2: I have a MS Ergo 4000 keyboard, and the volume control does not work. It works in the sense that I get a little popup showing that it moves the volume/mutes, but it does not correspond with the real volume.  From what I read online it's because there's two volume managers and it's controlling the wrong one, but I have not found an actual fix.  

3: When resizing windows, it seems I need to get the cursor dead on the 1 pixel area where it lets me resize, is there a way to increase this to a few pixels?  It makes resizing windows very difficult. 

4: How do I get rid of the password requirement for doing trivial tasks like shutting down?  

That's what I can think of right now anyway.  Surprisingly this has been fairly smooth.  I'm quite impressed how far Linux desktop has come since the last time I tried it.  Most of the stuff worked out of the box such as my printer.  Even in Windows I'd have to install drivers for it to work.

---

### Post by spikoley on 2012-07-03
1.  You can turn off the boot splash by editing grub.

```
gksudo gedit /etc/default/grub
```

Remove "quiet splash", save and then run:

```
sudo update-grub
```

2.  No idea.  Somebody else will have to help you there.  Also, try searching the forum.

3.  I hate that issue.  Hopefully somebody has a solution.

4.  You could create a regular user who is not an admin.  It shouldn't ask you for a password for shutting down, but I understand what you mean.

---

### Post by mastablasta on 2012-07-03
> **Red Squirrel said:**
> 
3: When resizing windows, it seems I need to get the cursor dead on the 1 pixel area where it lets me resize, is there a way to increase this to a few pixels? It makes resizing windows very difficult. 

 
Have you tried a different theme? i am not using a default one and i haven't seen this problem. the window frame on my theme is quite thick.
 
> 
4: How do I get rid of the password requirement for doing trivial tasks like shutting down? 

 
shutting down shouldn't require a password.
 
if you are tlaking about tasks such as installing programmes, then the password is there for a good reason. i.e. to protect user from malware. the malware/virus/trojan would need your password in order to run. since they can't easilly get it it means they can't run themselves. 
 
so it is strongly advised you keep the password as it is a layer of security for the system and user's data. 
 
you can disable a password on login which is not advised if more users are going to use the mashicne. but if it's just you and maybe familly then go ahead (in system settings)
 
but as i said shutting down shouldn't require you to type a password.
 
Drivers in linux (if source is open) are (unlike in windows) included in kernel. So computer get's configured on reboot and necessary drivers for found devices get loaded.

---

### Post by PPN13 on 2012-07-03
Don't know if it's different for Xubuntu but Ubuntu will require an admin account's password if there are more than one users logged in when you try to shutdown. I like that cause my parents tend to shutdown the PC when they are done even though they found it ON (downloading for example).

---

### Post by Merrattic on 2012-07-03
Resizing windows is a two handed job on Xubuntu. Press the ALT key then right click and drag to resize, left click and drag to move. Don't know why they took away the clickable area in the bottom right hand corner for doing resizing ?

---

### Post by flemur13013 on 2012-07-03
1: Edit /boot/grub/menu.lst (grub = v.9) or  /boot/grub/grub.cfg (grub2 = v1.something)
On the kernel line, remove "quiet" and "splash" parameters.

2: Dunno
3: Dunno

4: Some people recommend fooling with the sudoers file, but it doesn't work consistently for me, so I do [this]("http://askubuntu.com/questions/29589/chmod-ux-versus-chmod-x"):

$ sudo chmod u+x /sbin/shutdown (or whatever command)
$ ls -al /sbin/shutdown
-rwsr-xr-x 1 root root 60280 Apr 26 09:26 /sbin/shutdown

---

### Post by amanchesterman on 2012-07-04
Re (1), I raised this question ... sort of anyway ... a while back here:
[http://ubuntuforums.org/showthread.php?t=2004054](http://ubuntuforums.org/showthread.php?t=2004054)

Essentially you get the black screen because the grub menu doesn't appear, and it doesn't appear because you only have one OS installed. If you want an image or something to reassure you that the boot is proceeding OK you would need to use plymouth - though note that some people say it can be unpredictable. I've no idea how you could get it to show 'what is going on' if you mean getting it to reveal the sequence of steps it is going through as it boots.

Re (3) I don't understand your difficulty. I have xubuntu 12.04 and I do the following:
- open or focus on the window that needs to be resized
- at the extreme left of the top bar (the window title bar) there is an icon representing the app that is open in the window
- left-click on the icon and a menu appears, one of the options is 'resize'
- left-click on that option and the cursor is immediately positioned at the bottom right hand corner of the window, grabbing it
- hold down left mouse button as you move the cursor and the window resizes
- release the mouse button to stop resizing

Can't help you with (2) and I have never experienced (4), probably 'cos I'm the sole user of this machine.

Hope that is some help.

John

---

### Post by brainwash on 2012-07-04
2) [http://askubuntu.com/questions/130927/how-to-switch-default-sound-device-controlled-by-hardware-keys-in-xubuntu](http://askubuntu.com/questions/130927/how-to-switch-default-sound-device-controlled-by-hardware-keys-in-xubuntu)

3) [http://xubuntu.org/news/window-resizing-in-xubuntu-and-xfce/](http://xubuntu.org/news/window-resizing-in-xubuntu-and-xfce/)

Just wanted to add these links. :)

---

### Post by Red Squirrel on 2012-07-04
Cool thanks for the tips, seems I have mostly everything under control now.  I managed to get the standard text bootup mode, which is what I wanted.  Somehow it actually cut down my boot time by about 10 seconds too. 

For resizing, I was doing it from the lower corners, I never even thought of trying from the top, it definitely is easier from there.  The alt trick is good to know too!  

I will try the sound thing and hopefully that will work. At least I was able to find that setting though, lot of the stuff I googled was telling me to go to places that did not exist.  I can't reboot now to test but I will later and report back.  

As for the password requirement, it somehow stopped doing it, I was messing around in a sudo edit tool (I forget the name now but it was basically a text editor made for sudo editing) and it seems to have gone away.  I still get the prompts for installing stuff but I suppose I can live with that.  It's kinda like UAC but at least it has a purpose because it requires user input.  A UAC "ok" box could easily be bypassed by a well crafted script.

Edit: yep volume works now!   Thanks for the help, I should be good now.  Going to take an image of this machine soon so I don't lose all these changes in the event of a HDD crap out.  I do have an OCZ after all.

---

