---
title: "Ubuntu 20.04 -- Please explain &quot;remote&quot; on following screenshot"
date: 2023-04-05
forum: New to Ubuntu
---

### Post by bhubunt on 2023-04-05
Hi, 
I have had this happen often: when working on documents, whether on LibreOfficeWriter or on LibreOffice Impress, suddenly my doc will say "remote" at the top, in parentheses. 

[It says at the top: Untitled 1 (Remote) LibreOffice Impress, see attached screenshot.]

Can someone familiar with this explain what is going on here? 

Why the "remote"? How did this happen?

The weird "remote" ref popped up at 19:43:11 in the following partial log, between lines 77 and 78: [https://pastebin.com/tiqs7fak](https://pastebin.com/tiqs7fak)

---

### Post by Dennis N on 2023-04-05
I've get that in LibreOffice when I open a file over a network connection. I believe it locks out anyone else trying to open the same file while you have it open.

---

### Post by bhubunt on 2023-04-06
> **Dennis N said:**
> I've get that in LibreOffice when I open a file over a network connection. I believe it locks out anyone else trying to open the same file while you have it open.

Thanks for the reply, but can you explain what you mean by "opening a file over a network connection"? 

It's definitely not the case that every time you are on the internet a doc in LibreOffice therefore is remote. To the contrary. For example, I am connected to my modem right now, but when I open LibreOffice right now, it definitely does not say "remote," which is in fact the way it should be. The opened LibreOffice file is just on my computer and not a remote file.

In fact, there is a separate button in the drop-down menu under File in LibreOffice to activate "remote." If you click on it, it says you need to fill in the service. Since I never use remote files and also don't save files as remote files, I have no services listed or activated (see screenshot below, taken just now).

Perhaps you do use remote services, but I definitely do not. That's the reason why I put the tag "strange behavior" in this posting.

My question still is: how is it that I get remote file references on some of these docs, when I have no remote services activated and never use remote files?

(P. S.: I also don't have a server or a router, just use Ubuntu 20.04 LTS desktop and my internet connection happens through a commercial DSL modem.)

---

### Post by TheFu on 2023-04-06
The attached image doesn't show "remote" in the title bar, where I expected it.  Looks like it is just a dialog to open remote files using one of the many supported methods, like WebDAV or Google or CIFS or sftp or ... [https://help.libreoffice.org/6.2/en-US/text/shared/guide/cmis-remote-files-setup.html](https://help.libreoffice.org/6.2/en-US/text/shared/guide/cmis-remote-files-setup.html)

I did a test running libreoffice v7.3 on a remote system and had it access NFS storage remote to both my desktop and the libreoffice system. No "remote" showed up in the titlebar.

---

### Post by bhubunt on 2023-04-07
> **TheFu said:**
> The attached image doesn't show "remote" in the title bar, where I expected it.  Looks like it is just a dialog to open remote files using one of the many supported methods, like WebDAV or Google or CIFS or sftp or ... [https://help.libreoffice.org/6.2/en-US/text/shared/guide/cmis-remote-files-setup.html](https://help.libreoffice.org/6.2/en-US/text/shared/guide/cmis-remote-files-setup.html)

I did a test running libreoffice v7.3 on a remote system and had it access NFS storage remote to both my desktop and the libreoffice system. No "remote" showed up in the titlebar.


Hi The Fu,
Thanks so very much for the reply and for running a test. However, when you say that the attached image doesn't show remote in the title bar, you are referring to the second screenshot in post #3, which indeed does not show "remote" in the title bar. 

However, the weird LibreImpress doc that this thread is about does have "remote" in the title bar and is posted in post #1.  I am attaching it again to this post, see below.

Since you are able to do tests, I wonder if you could possibly do a test in which you share your desktop and a Libreoffice doc with another user? Here are the instructions: [https://help.ubuntu.com/stable/ubuntu-help/sharing-desktop.html](https://help.ubuntu.com/stable/ubuntu-help/sharing-desktop.html)

---

### Post by bhubunt on 2023-04-07
deleted because duplicate of post #5

---

### Post by ActionParsnip on 2023-04-07
Remote control....maybe (bit of a stretch). If you disable that, does it go away?
[https://help.libreoffice.org/6.0/media/screenshots/cui/ui/optionsdialog/impressoptionsgeneraldialog.png](https://help.libreoffice.org/6.0/media/screenshots/cui/ui/optionsdialog/impressoptionsgeneraldialog.png)
:-k

---

### Post by bhubunt on 2023-04-07
> **ActionParsnip said:**
> Remote control....maybe (bit of a stretch). If you disable that, does it go away?
[https://help.libreoffice.org/6.0/media/screenshots/cui/ui/optionsdialog/impressoptionsgeneraldialog.png](https://help.libreoffice.org/6.0/media/screenshots/cui/ui/optionsdialog/impressoptionsgeneraldialog.png)
:-k


Thanks very much for the question and suggestion, ActionParsnip. 

As a matter of fact, my LibreImpress is always set to "Enable presenter console," never to "Enable remote control."  I am not a member of a group or small network and also not  logged into a server where the members share their screens and files. I am just a user of Ubuntu 20.04 LTS desktop version on my Lenovo Thinkpad x240 laptop, hooked up to a commercial internet provider via a DSL modem. I do not own a separate router.

I am attaching a screenshot of my settings for LibreImpress, below.

But I must say that it does seem to me that the "remote" reference in the title bar of screenshot #1 in post #1 indicates remote control of the file.

Are there any signs in the system log that there is remote desktop/screen sharing? The remote LibreImpress file appeared at around 19:43:11 -- between lines 77-78 in the log: [https://pastebin.com/tiqs7fak](https://pastebin.com/tiqs7fak)

And here's the longer log that preceded: [https://pastebin.com/dLfDuRgd](https://pastebin.com/dLfDuRgd)

---

### Post by ActionParsnip on 2023-04-07
If you close all LibreOffice apps then run:
```

mv ~/.config/libreoffice ~/.config/libreoffice_2023-04-07

```
Then rerun the application, do you still see the "remote" text?

You may also want to try posting on the LibreOffice forum
[https://ask.libreoffice.org/](https://ask.libreoffice.org/)

---

### Post by TheFu on 2023-04-07
> **bhubunt said:**
>  Since you are able to do tests, I wonder if you could possibly do a test in which you share your desktop and a Libreoffice doc with another user? Here are the instructions: [https://help.ubuntu.com/stable/ubuntu-help/sharing-desktop.html](https://help.ubuntu.com/stable/ubuntu-help/sharing-desktop.html)

I use remote stuff daily and was using it for this test.  The window with libreoffice inside it was on my local system, but libreoffice was running on a remote system using X11 forwarding through ssh.  If you are on the same LAN, that's the best way.  

Full remote desktops are a complete waste of resources, unless you are going over the internet and for that situation, I use x2go.  I'm unwilling to install VNC or RDP on my systems and I think most Gnome system stuff are abominations. Sorry.

So, my test was using x11-forwarding over ssh.  That works fine. It should be faster than any other method and it is certainly 1000x easier.  
I don't have x2goserver setup on the system where libreoffice is installed, but eventually, if I start traveling again, it will be needed.
I did run another test over a SPICE connection. This does provide a full, fast, remote desktop, but it isn't secure.  I seldom use it. It isn't something I can disable.  Anyway, no "remote" in the title bar with it either.  

Whatever you are doing seems to be less about libreoffice and more about the way sharing is enabled/accessed on your system.

---

### Post by maglin2 on 2023-04-07
just a thought picked up from another thread, what does
```
grdctl status
```
yield?

---

### Post by bhubunt on 2023-04-07
> **TheFu said:**
> I

Whatever you are doing seems to be less about libreoffice and more about the way sharing is enabled/accessed on your system.

Thanks, but there is *no* sharing enabled/accessed on my system -- that being my Lenovo laptop. 

As I said, I have no server, I am also not connected to a server (as far as I know), I am not a member of a network, and have never ever set up sharing with anyone. 

May I ask if you had a chance to check the system log links from pastebin that  I posted in post #8?

Is there anything you see in those system logs that indicates my desktop/screen is being shared?

---

### Post by bhubunt on 2023-04-07
> **maglin2 said:**
> just a thought picked up from another thread, what does
```
grdctl status
```
yield?

The terminal says: ```
 command not found 
```.

---

### Post by mIk3_08 on 2023-04-07
> **bhubunt said:**
> The terminal says: ```
 command not found  
``` If terminal says command not found, Maybe there is a  problem with your system. The command ```
grdctl status
``` usually gives you the status of your RDP
    and VNC. Regards and cheers.

---

### Post by TheFu on 2023-04-07
None of my systems have that command and I didn't remove it.  Seems related to gnome-remote-desktop package.

---

### Post by maglin2 on 2023-04-08
In a default 22.04 desktop install you should see something like
```
grdctl status
RDP:
    Status: disabled
    TLS certificate: 
    TLS key: 
    View-only: yes
    Username: (hidden)
    Password: (hidden)
VNC:
    Status: disabled
    Auth method: prompt
    View-only: yes
    Password: (empty)
```

(In VM attempts I found it hard to remove from 22.04 without killing other things, so masked the service instead. It is easy to remove in 22.10).

I was just wondering if someone in Ubuntu might have thought this was such a good feature in 22.04 they'd decided it should be backported to 20.04! 
Obviously not.

---

### Post by bhubunt on 2023-04-08
> **TheFu said:**
> None of my systems have that command and I didn't remove it.  Seems related to gnome-remote-desktop package.

I agree with The Fu. My laptops also don't have that command and I also did not remove it.



I'd still be grateful if someone could check the system logs in post #8 and see if there is any code in those logs that suggests remote desktop sharing was going on at the time. 

As mentioned, I have no router and I am also not on a small network nor logged into a server. Plus, I have  never activated remote desktop sharing or any file sharing with anyone for that matter on any of my laptops.

Thanks to all for your help.

---

### Post by MAFoElffen on 2023-04-08
Agreed. It's not going to be there if gnome-remote-desktop is not there.
```

mafoelffen@Mikes-ThinkPad-T520:~$ grdctl status
RDP:
    Status: disabled
    TLS certificate: 
    TLS key: 
    View-only: yes
    Username: (empty)
    Password: (empty)
VNC:
    Status: disabled
    Auth method: prompt
    View-only: yes
    Password: (empty)

mafoelffen@Mikes-ThinkPad-T520:~$ apt list gnome-remote-desktop --installed
Listing... Done
gnome-remote-desktop/now 42.4-0ubuntu1 amd64 [installed,upgradable to: 42.7-0ubuntu1]
N: There is 1 additional version. Please use the '-a' switch to see it

```

---

### Post by kinddolphin8827 on 2023-04-13
I may not have any experience with X11 forwarding in any fashion, even though my first ever  experience was to  jump right into setting up a file and print server. So I knew right away that we would infarct need the log files.

1. Please provide us with log files via paste bin
2. Annotate them if possible
3. If at all possible try to keep your answers  concise

---

