---
title: "[SOLVED] Share Folder won't take, NOT NETWORK RELATED!"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Kellemora on 2008-09-27
Hi Gang

I really feel stupid asking this, since I did have everything working fine before I decided to replace the hard drive and reload everything.

ON the Desktop I created a folder named Shared Stuff.

I can find no way to get the SHARING to take on this folder.

I HAVE tried moving it into the documents folder and into the /home/me folder to no avail.

SHARE does work on the existing Ubuntu generated folders of /home/me/public and /home/me/documents just fine.

Same way with Pictures, Videos, Music, Templates, they all work fine.  But NO NEW FOLDER placed in /home/me/folder-name can be shared.

Seems I had this problem when I first stared but figured it out.

Since then I must have become exceedingly dumber, hi hi.....

I can also move any of the existing Ubuntu created folders to the desktop and they STAY shared and work fine.

Somebody, HIT this olde man over the head with a mallet and tell me what I forgot to do!

Thanks

TTUL
Gary

---

### Post by Kellemora on 2008-09-27
Just wanted to add some more pertinent details.

I CAN go into Nautilus via Root and Create the Share, but when I exit Nautilus and go to the /home/desktop and see the folder, it is no longer shared, and will give the error 255 if I try to share it outside of root nautilus.

That's HOW I got it to share last time, was using the root terminal and gksu nautilus, then went to the folder and shared it.  This time it WILL NOT TAKE.  NO error 255 is given either, and the FLAG (hand) does come up while I'm in Nautilus.

One should NOT have to use the root terminal to share a folder!
But when you do, it SHOULD stick!

I can see the Ubuntu created folders when they are shared no problem, just can't share any new folders.

Any Ideas?

TTUL
Gary

---

### Post by _sAm_ on 2008-09-27
And you are trying to share the folder to a Windows pc?

---

### Post by Kellemora on 2008-09-27
Hi Sam

The problem is NOT network related!
I can't set the folder to SHARE at ALL.  All permissions must be correct because I can share any and all Ubuntu generated folders.

I had this problem a couple of months ago when I first started using Ubuntu but at that time, using nautilus in root allowed me to set the share and it would STICK so it was usable when NOT in root.

This time, if I leave root, the folder is no longer shared for some reason.  Also, if I move it from the /home/me folder to the /home/me/desktop folder it even looses it's sharing while in Root.

None of these problems occur when working with Ubuntu created folders.

I've checked everything I know to check from user shares all the way through smb.conf, NOTHING I can find is different than on a working system where sharing works just fine.

In fact, I can put the old small hard drive back into the computer and I can again share new folders on the desktop, no problem.

This is how I've been comparing the various files and settings looking for some difference, any difference at all and can find none.

As USER, since messing around, I'm NOW getting the Error 255 that I was not getting before too.  So, I'm making it worse by clicking on permissions to allow things in the group settings.

Maybe if I sleep on it until tomorrow, whatever it is might come to me!

Thanks

TTUL
Gary

---

### Post by jamesrfla on 2008-09-27
Where you successful on sharing the folder? No errors when you click Create Share?

---

### Post by Kellemora on 2008-09-27
Hi James

In my Home folder NOT logged in as root, only as User, I can do the following.

Share ANY Ubuntu created folder in the /home/me directory.

These include Documents, Examples, Music, Pictures, Public, Templates & Videos.

I just hit right click, Sharing Options, tick the sharing features I want and hit Create Share and it works just fine.
Each of those folders appear on the network.

However, I created a NEW FOLDER and named it SharedStuff.

It was asking to set permissions earlier, now it doesn't do that, just shows Error 255 message now.

If I go into ROOT and open Nautilus, I CAN Share the Folder, but as soon as I leave Root, the sharing disappears, until I return back to Root.

And YES I'm sure I'm in the correct folder while in root!
/home/me/sharedstuff

Now, if I put my old hard drive back in and do the same steps as above, everything works just fine, the sharedstuff folder shares and appears on the network as well.

With one exception:  Since I edited the smb.conf file and changed workgroup = WORKGROUP to workgroup = MYWORKGROUPNAME I no longer get both folders on the Windows Network Neighborhood Screen, which is great as the folders NOW appear under MYWORKGROUPNAME where they belong.

Since it is the same computer, only different drives behind dropped in and out to see the differences.  It's only logical that all the configuration files for the network and the smb.conf file are identical.
ifconfig -a, route -n and others all read identical to each other.  Except of course the number of packets shown changes with each viewing.

The fact that it works fine on the little first hard drive I tried Ubuntu on, but doesn't work on the larger hard drive from a clean install with all upgrades and same downloads as the other, really has me baffled big time.  
I've read the samba configuration directions enough times I almost know it by heart, hi hi...........

Oh well, like I said, I think I should sleep on it.  Been at this one task, trying to figure it out all day long.

TTUL
Gary

---

### Post by Kellemora on 2008-09-27
Problem Solved!

The Folder itself was corrupt!

Once I removed that folder, all new folders I created could then be shared without difficulty.

Have no idea how the folder became corrupted though!

TTUL
Gary

---

