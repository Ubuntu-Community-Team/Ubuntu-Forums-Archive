---
title: "Naming windows shares in Hardy"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by cormic on 2008-04-22
Hi all,

I have just done a new install of Hardy RC and cannot figure this one thing out.  

In Gutsy I was able to connect to a Windows share and name the directory that appears on the desktop.  In Hardy I can create a bookmark in Nautilis but it still shows up as "*sharename* on *servername*" on the desktop.

This is quite annoying and I would love to sort it out.

Thanks

Cormic

---

### Post by stalker145 on 2008-04-22
> **cormic said:**
> Hi all,

I have just done a new install of Hardy RC and cannot figure this one thing out.  

In Gutsy I was able to connect to a Windows share and name the directory that appears on the desktop.  In Hardy I can create a bookmark in Nautilis but it still shows up as "*sharename* on *servername*" on the desktop.

This is quite annoying and I would love to sort it out.

Thanks

Cormic

OK, just to make sure I'm getting this right: you do not want the icon on your desktop?

If that's the story, you can rename the Nautilus bookmark simply by right-clicking and choosing rename. Then, removing the icon from the desktop is either delete it, rename it (you should be able to), or open up gconf-editor (<alt>F2 gconf-editor), drill down to apps~>nautilus and you'll find icon view in there *somewhere*. untick the option for showing mounted drives. The only drawback there is that you won't see any external drives on the desktop if you plug them in.

Check back if this doesn't answer/fix your problem.

---

### Post by cormic on 2008-04-22
Thanks for the reply.  

I want to keep the icon on the desktop and I want to rename it.  Unfortunately I do not have that option when right clicking on the icon.

---

### Post by Iowan on 2008-04-22
I haven't taken the plunge to Hardy yet, but on Gutsy the desktop icon appeared on the Places drop-down.  Right-clicking that gave a rename option.

---

### Post by oroboro on 2009-04-29
I also find this extremely annoying and cannot find a solution. The solution above does not work as right clicks on entries in the Places menu are treated as left clicks now for some reason.

I tried using nautilus as root but the mount icon doesn't appear.

I am reviving this topic so that the solutions posted won't be proposed again. I apologize if there's something wrong with reviving old topics, but this is regarding Hardy (though RC1, this issue hasn't changed).

Just to clarify so that the issue isn't misunderstood again:
When you connect to a Windows share (not sure about other connections), an icon is automatically placed on your dekstop called "<sharename> on <servername>". Though very convenient, the inability to rename this shortcut/bookmark is very annoying, since the name gets rather long.

Any help would be appreciated. Thank you in advance.

---

### Post by oroboro on 2009-05-03
Bump

---

### Post by doas777 on 2009-05-03
all I can suggest, is to backup and rebuild using the full release Hardy 8.04.1 or mabey even Jaunty.

good luck

---

### Post by BslBryan on 2009-05-03
I think this is what you want:

Applications --> System Tools --> Configuration Editor.
 
Then, apps --> nautilus --> desktop --> network_icon_name

---

