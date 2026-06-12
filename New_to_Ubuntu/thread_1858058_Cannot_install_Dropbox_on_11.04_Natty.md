---
title: "Cannot install Dropbox on 11.04 Natty"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by Paddy Landau on 2011-10-11
I have installed 11.04. I downloaded the [.deb file from Dropbox]("https://www.dropbox.com/downloading") (Ubuntu 64-bit version 0.6.9).

After Ubuntu Software Centre has installed Dropbox, Dropbox gives me two errors:

[LIST=1]
[*]In order to use Dropbox, you must download the proprietary daemon.
[*]Trouble connecting to Dropbox servers. Maybe your internet connection is down, or you need to set your http_proxy environment variable.
[/LIST]
 
I have submitted a ticket to Dropbox, but no reply has been forthcoming, and I have not found a suitable solution on the Dropbox forum.

Do you have any idea what I can do to fix this?

EDIT: On a slightly-unrelated issue, I have submitted [a bug]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/872406").

---

### Post by John Peschken on 2011-10-11
1. This part is normal.  The install then automatically should start the process of downloading and installing the needed daemon.

2. Is there any chance you might actually have a poor internet connection?  Otherwise, I do not yet know how to check or set environment variables in Linux.  Maybe this environment variable is what prevents problem 1 from downloading the daemon.  Experts, please!

---

### Post by Paddy Landau on 2011-10-11
> **John Peschken said:**
> 1. This part is normal.  The install then automatically should start the process of downloading and installing the needed daemon.
Unfortunately, in my case it does not. It just ends right there.


> **John Peschken said:**
> 2. Is there any chance you might actually have a poor internet connection?
No. I have a good broadband connection that has been working well. I have retried this problem over three days, always with the same results.

---

### Post by Frogs Hair on 2011-10-11
You could try the PPA . [http://www.ubuntuupdates.org/ppa/dropbox?dist=natty](http://www.ubuntuupdates.org/ppa/dropbox?dist=natty)

---

### Post by Paddy Landau on 2011-10-11
> **Frogs Hair said:**
> You could try the PPA . [http://www.ubuntuupdates.org/ppa/dropbox?dist=natty](http://www.ubuntuupdates.org/ppa/dropbox?dist=natty)
That had the same bug :(

---

### Post by clive littlewood on 2011-10-11
Hi Paddy

Have you tried dropbox from the repos ?

Called nautilus dropbox in synaptic / software centre.

Hope this helps

Clive

---

### Post by John Peschken on 2011-10-11
> **Frogs Hair said:**
> You could try the PPA . [http://www.ubuntuupdates.org/ppa/dropbox?dist=natty](http://www.ubuntuupdates.org/ppa/dropbox?dist=natty)

That's interesting.  When I follow your link, I see this.

"This repository is available for: Lucid  Maverick  Natty"

The words "Lucid" and "Maverick" are links, but not "Natty"

Could it be that it does not work with Natty?  Is it possible that Ubuntu is making trouble since it might compete with Ubuntu One?  Could they be that petty?  I hope not.

---

### Post by John Peschken on 2011-10-11
> **clive littlewood said:**
> Hi Paddy

Have you tried dropbox from the repos ?

Called nautilus dropbox in synaptic / software centre.

Hope this helps

Clive


Clive,

I do not see dropbox in the Ubuntu Software Center.  It was there once upon a time.  I had not gotten around to installing it in 11.04.  I wonder why they would do that.

---

### Post by John Peschken on 2011-10-11
My fears of a conspiracy were not well founded.  I just installed dropbox on Natty, no problems.  It went just like it always has.

---

### Post by clive littlewood on 2011-10-12
Hi John

I've just installed from synaptic on 3 machines (11.10) and everything is OK.

Had to install synaptic first though !!!!!!

Clive

---

### Post by John Peschken on 2011-10-12
> **clive littlewood said:**
> Hi John

I've just installed from synaptic on 3 machines (11.10) and everything is OK.

Had to install synaptic first though !!!!!!

Clive

Isn't that there by default?  It must be, I did nothing to install it.

---

### Post by clive littlewood on 2011-10-12
Hi John

Not default in 11.10 

Clive

---

### Post by Paddy Landau on 2011-10-13
> **clive littlewood said:**
> Have you tried dropbox from the repos ?
I searched Synaptic. It's not in there by default (you have to add the repository, which installing DropBox will do automatically).

> **clive littlewood said:**
> I've just installed from synaptic on 3 machines (11.10) and everything is OK.
That is so unfair!

EDIT: Will Ubuntu One synchronise as easily and --more importantly -- as quickly as Dropbox does? Perhaps I can replace Dropbox with Ubuntu One.

---

### Post by kolinab on 2011-10-13
Hi Paddy,

I've had some problems myself with dropbox installation a time or two.

What finally worked for me was removing dropbox completely, deleting your /.dropbox folder (not the data folder, just the hidden preferences folder), and reinstalling from the dropbox website. It worked for me just last week. 

Ubuntu One might be much better now but I gave up on it back in Maverick days. I should probably give it another shot but I like the way dropbox works for me now.

---

### Post by Paddy Landau on 2011-10-13
@kolinab: Thanks, but my attempts at installation do not even create a .dropbox folder. I have tried installing several times from the website -- that's the only place I know where to install from!

I also like Dropbox, but if it won't work, I'll have to use something else. I'll test Ubuntu One.

---

### Post by kolinab on 2011-10-13
Paddy,

You have probably already tried this so I apologize if you have already looked, but you need to CTRL+H to show hidden folders (starting with '.')in your /home.

---

### Post by John Peschken on 2011-10-13
> **Paddy Landau said:**
> @kolinab: Thanks, but my attempts at installation do not even create a .dropbox folder. I have tried installing several times from the website -- that's the only place I know where to install from!

I also like Dropbox, but if it won't work, I'll have to use something else. I'll test Ubuntu One.

Paddy,

I installed it from the web site as well, and it worked fine.  So, it seems like it must be something specific to your system.  Unfortunately, determining what that might be is above my modest knowledge right now

Ubuntu One has been working fine for me, and you do get 5 GB free instead of 2.  When it was first introduced, I had some troubles with things taking days to sync,  but I have not experienced that recently.   On the other hand,  I have mostly used dropbox mainly out of habit.  I am also not sure what the status of Windows or Mac clients if that matters to you, I suggest checking out.

---

### Post by Paddy Landau on 2011-10-14
> **kolinab said:**
> ... you need to CTRL+H to show hidden folders (starting with '.')in your /home.
Thanks, I already know that.

> **John Peschken said:**
> ... it seems like it must be something specific to your system.
Oh well. Maybe when I upgrade to 12.04.

> **John Peschken said:**
> Ubuntu One has been working fine for me...
Thanks for the information. I'll try it out today or tomorrow. If it works, that will be fine for my purposes.

---

### Post by Paddy Landau on 2011-10-18
I have discovered the problem.

For security, I recently implemented the [blacklisting as described in JournalXtra]("http://journalxtra.com/2011/07/faster-safer-ad-free-browsing-with-a-little-domain-blocking/").

Unfortunately, it turns out that those blacklists include some bona fide sites, including Dropbox.

I have reverted to the default and now Dropbox works.

So, apologies to Dropbox, and I shall mark this thread as solved.

---

