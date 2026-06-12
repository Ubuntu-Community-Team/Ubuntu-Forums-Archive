---
title: "Thunderbird mail question"
date: 2023-10-16
forum: New to Ubuntu
---

### Post by drichardson2 on 2023-10-16
In thunderbird mail, I've lost my "Read" and "Unread" button to click.  How do i get it back?

---

### Post by TheFu on 2023-10-16
Which version of Ubuntu (the number)?
Which version of Thunderbird?
Is Thunderbird a snap package or a debian package?

Try deleting the profile or creating a new profile. Is it back?

Obviously, if you delete stuff, you'll want to have a backup that can be restored later. If you don't have that, expect to lose things.

Did you do or notice anything related before this happened?  For example, did you apply patches, but forgot to restart Thunderbird?  Sometimes I forget to restart my system after patching with patches that require a reboot. About 3 days later, usually Firefox starts acting odd, so I get a gentle reminder to reboot.  Best not to patch daily (or let the system patch daily), since then your system is constantly being modified and when any issue happens, you don't immediately think it was due to a patch.  I patch Saturday mornings.  If there are issues after that on Sat/Sun, then it is likely from a patch. Stuff that happens in the middle of the week probably aren't related to a patch.

---

### Post by drichardson2 on 2023-10-16
Ubuntu 22.x lts is what I'm using
Thunberbird mail is version 115.3.1

Before my desktop died I had someone on another board tell me what to click in the menus to bring this feature back, but I can't find the message again to bring it back on this laptop.

---

### Post by #&amp;thj^% on 2023-10-16
The Unread button is on the Quick Filter Bar (Ctrl+Shift+K) or under View/Toolbars.

---

### Post by drichardson2 on 2023-10-16
> **1fallen said:**
> The Unread button is on the Quick Filter Bar (Ctrl+Shift+K) or under View/Toolbars.

That's what I needed.  marking this as solved

---

### Post by TheFu on 2023-10-16
The new thunderbird moved some things around.  Some things are better. Some things I'm still getting used to.  

I like how adding "unread folders" shows up at the bottom, not the top of the Server --> Folder list.  I have a few different email accounts, so there are multiple Servers in my left panel.  I use the classic 3-panel view.  Folders on the left, message list top+right and which ever message is active in the bottom+right.

I didn't notice the new version ... except the icon changed for the first time in about 20 yrs.  Since I use **gnubiff** to know when new messages arrive, I'm not always dealing with thunderbird.  When I get busy, may only check email 2x a day, if I don't have time between other tasks/compiles to change gears.  GnuBiff is the only biff tool that seems to support imap, but it has issues with multiple imap accounts. Sigh.  

I miss **xbiff**. It was tiny and clear.  White mailbox for no new messages.  Black mailbox with a flag up if there's 1+ new messages.  Alas, xbiff would only check the /var/spool/mail/ and ~/.mbox/ locations. No pop3 or imap support.

---

