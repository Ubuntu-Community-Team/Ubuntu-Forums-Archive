---
title: "Change Unity (?) desktop environment to older Gnome?"
date: 2023-03-28
forum: New to Ubuntu
---

### Post by kharrisma-j on 2023-03-28
Hi Forum Folks,

I tried Ubuntu quite some time ago and liked it a great deal, but I was heavily into gaming at the time and I couldn't play many of my then-favorite games, so I went back to Windows.  Two "upgrade" iterations of Windows later, I've finally had enough of Microsoft's nonsense, and switched to Linux ONLY.  

The other reason I dropped Ubuntu was the switch to the "Unity" (?) desktop... I absolutely hated it... and I still do.  I felt I didn't really give it a fair trial when I first ran into it, but I determined to give a fair trial this time.

Nope... can't do it.  I dislike it intensely, and I'm wondering if there's any way to "roll back" to the older desktop paradigm, GNOME I believe?  I've been using the old 'standard' layout for far too long to adapt to something as radically different as what's currently in use here.

I'd *rather* run Ubuntu, since it's the "parent" OS that all the variants derive from, and it has Canonical behind it.  Plus, it's already installed and loaded with my files from Windows.  I'd rather just change environments than do a total re-install again, if that's possible.

If it isn't, which distro would you recommend as most like the traditional way of managing a desktop... I guess "Windows-like" is what I'm trying to say without actually having to say it!  ;-)

Thanks for your suggestions!

---

### Post by send2 on 2023-03-28
There is  the package gnome-session-flashback if that is what you are referring to. The current version in Synaptic is:  gnome-session-flashback 1:3.44.0-1ubuntu2.  You would have to update your 
system first and then install it:

sudo apt update and then 
sudo apt install gnome-session-flashback. 

After installing it then you would log out and before logging back in you would choose it by hitting the cog on lower right of log in screen and choosing GNOME Flashback (Metacity) out
of the list of desktop environments. Mine are Ubuntu, Ubuntu on Xorg and Gnome Flashback (Metacity). I have this legacy gnome version because I have Compiz (window effects) installed.
For reference I am using Ubuntu 22.04.2 LTS.

I hope this will help you or at least give you an idea of one option for you.

---

### Post by Frogs Hair on 2023-03-28
Could you please indicate what version of Ubuntu is installed. Gnome 3 and beyond replaced unity as the default desktop environment in 2017 , but older versions would still have Unity. There are multiple DE's available on Ubuntu if you don't care for the gnome shell either.  . [https://ubuntu.com/desktop/flavours](https://ubuntu.com/desktop/flavours)

---

### Post by kharrisma-j on 2023-03-28
Hi Frogs Hair,

The installed version is 22.04.2 LTS x86_64.  To give you an idea of what I'm remembering, I think "Jaunty Jackalope" was the name of the version I was using (ver 9.04), which was (I believe) prior to Unity.  If I'm understanding what I'm reading correctly in the "Jaunty" blueprint page, KDE was the desktop environment.   Maybe instead of trying to turn a cadillac into a VW I should just back up and install one of the other distros like Mint or MX....

---

### Post by Frogs Hair on 2023-03-28
9.04 is long out of support and 22.04 would come with the gnome shell. If you like the older gnome environment you could try Ubuntu Mate 22.04 which is a fork of gnome 2 or Kubuntu which uses KDE. You'll find that many distros offer a choice of desktop environments. Spend some time researching them especially if you have been away from Linux for a while and enjoy the the DE and distro of your choice. The link will give an idea whats available not only on Ubuntu , but other distros as well. Mint has it's own DE too named Cinnamon.

---

### Post by coffeecat on 2023-03-28
@kharrisma-j, you refer to "older desktop", possibly gnome in your OP. And now to Jaunty Jackalope. I think the desktop you are referring to is the now deprecated gnome 2. However, it has been forked into the Mate desktop, and is the default desktop in the official Ubuntu flavour, Ubuntu Mate. Here's their website: [https://ubuntu-mate.org/](https://ubuntu-mate.org/)

Scroll through the screenshots on the first page. You can configure the Mate desktop in several different ways, which the screenshots demonstrate, but the screenshot that shows Applications - Places - System top left is the one that most closely emulates the old gnome 2. Was this what you are looking for?

**Edit:** ninja'd by Frogs Hair.

---

### Post by jim Kane on 2023-03-28
you could try Xubuntu a more traditional looking desktop

---

### Post by lucant on 2023-03-28
I think I understand?... Download the 'extension manager' app and disable the items:
- Desktop Icons
- Ubuntu Dock
You will thus have an experience close to vanilla gnome.

---

### Post by MAFoElffen on 2023-03-28
I can confirm that package 'gnome-session-flashback' is the Old Gnome Classic styled desktop, that works with gnome-sessions (Gnome3).
```

sudo apt update
sudo apt install gnome-session-flashback

```

The first attached screenshot is Gnome Classic 'gnome-session-fallback' (Fallback - metacity). The second attached screenshot is Lunar with Gnome3 'gnome-session'.

---

### Post by angisky on 2023-04-03
Gnome-session-flashback is okay but I really think OP would be better off with Ubuntu Mate. They wouldn't even have to do a fresh install. If they install the package "tasksel" they can select the mate desktop and it'll install all the apps that Ubuntu Mate normally comes with. It might double up on some of the system apps but the gnome 3 versions could be uninstalled later

---

