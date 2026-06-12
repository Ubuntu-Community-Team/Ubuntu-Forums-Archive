---
title: "Autodetect of network shares is still broken"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by MockY on 2008-09-19
By the release of Hardy Heron, the auto detection of network shares using SAMBA via Places - Network is broken. It was not fixed in 8.04.1 either. During the time with Hardy, I simply manually added the shares. This seemed odd at the time and due to other bizarre behavior in Hardy, I decided to stay with Gutsy. No real harm done since Gutsy is working just fine. 

However it is always fun to have the latest of everything so I have been patiently been waiting for Intrepid. I finally downloaded the last alpha that was released today to see if this was still the case. I was extremely surprised to see that the auto detection is still broken. Yes, it is is an alpha release, but since it is the last one, I now fear that this will remain in the final release in October.

So, does anyone out there know what the deal is? Will this be the case with every future release? And if so, what is even the point of having the ability to browse the network. Just remove the Places - Network if this will be the case. What is your take on this?

---

### Post by bobsmith2 on 2008-09-19
For me it comes and goes. Sometimes I'm able to browse the network, other times it just disappears. Tonight it disappeared, so I rebooted, and it appeared again. I'm always able to connect to network shares via my bookmarks, and remote PCs can always connect to me, but browsing the network is only available about, oh... maybe half the time. I thought it was just me, so I appreciate your post. Now that I know I won't waste time trying to fix it.

---

### Post by gregphil on 2008-09-19
It is my opinion it is these bugs: (ignore the bug titles and read through the entire thread)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

Basically the bug in the gnome gvfs library (that nautilus and other gnome GUI apps use) prevents correct browsing of shares form Windows machines if the shares require authentication (are not anonymous or "guest" shares).  Note that Nautilus WILL connect is you type in the full path to the share, it just won't browse.

The command line tools that don't use the library in question work fine (try smbclinet -L COMPUTERNAME   or smbtree ).  Also with identical hardware and samba setting (dual boot) a kubuntu setup does NOT have the browsing bug (using konqueror as the network browser).

After reading *many* posts about this issue I am fairly sure the ubuntu/gnome problem is the bugs I listed above.

Thanks.

---

### Post by MockY on 2008-09-19
I guess that all we (the non programmers) can do is sit back and wait for this bug to be resolved. I thought that functionalities such as this, which has been working as long as I can remember, just didn't break like this. Especially not when this has been a know issue for quite a while.

But like you stated, there are workarounds, and I have to resort to those method when the final release of Intrepid is released.

Thanks

---

### Post by mgmiller on 2008-09-25
> Note that Nautilus WILL connect is you type in the full path to the share, it just won't browse.

Thank you for that.  My whole network suddenly went nuts this morning and all my smb shares stopped working on all 4 of my ubuntu 8.04.1 machines.    ](*,)  When I edited them to the actual IP path, the shares were available again.  The network browsing GUI, however, remains broken.  It won't browse the network at all.  

Why did this suddenly happen?  It was perfect till this morning.  I remember there were some samba updates recently, maybe those broke it?

---

