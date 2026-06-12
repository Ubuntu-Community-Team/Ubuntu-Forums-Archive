---
title: "Very simple home network"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by kman14 on 2008-09-29
I'm looking for a very simple guide for setting up a network at home.
I've read many, many threads on the forum and can't get my head around it, (usually the forum has what I'm looking for).

I think I need Samba - that's what everyone seems to recommend, but all the threads seem quite old, or they talk about the problems it's having with nautilus. I'd like something simple and definitive if it's at all possible.

If there are problems with Samba and Nautilus should I just wait until 8.10 is released?

Any help is much appreciated.
Thanks.

---

### Post by Peter09 on 2008-09-29
Hi,
you need Samba to share files between Linux and windows systems. If you only want to see windows shares you will only need the Samba Client. 

Both of these applications are available from the repositories.

You may need to tell us a little more about the issues that you have for us to help.

---

### Post by kman14 on 2008-09-29
Thanks Peter09.

My problem is that I don't have a single issue as such - it's more I don't understand the subject at all.
That's why I was hoping to be pointed in the right direction as far as tutorials and "how to's" go.

I checked out the Samba website, but it was more than my puny brain could handle, (that may have more to do with the fact i have the flu).

I know it's a big subject - that's why I'm looking for someone to point and say,"Go and look there", rather than help me with each step.

Cheers.

---

### Post by Peter09 on 2008-09-29
OK,
as a first pass you do not need to do any of those things.

Assuming you want to see windows shares.

Goto Applications->Synaptic Package Manager

once that starts type Samba in the search box.

Once found look for an application which is the Samba Client and tick the box.(if it is already filled in then it is already installed).

Then click the apply button and it should install it.

Lets get that far and see where we go. You may then be able to see your windows shares in the Places->Network menu.

---

### Post by hyper_ch on 2008-09-29
what do you want to do on your home network?

---

### Post by Nepherte on 2008-09-29
This is a good tutorial to start with: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by t0p on 2008-09-29
> **Peter09 said:**
> 
Lets get that far and see where we go. You may then be able to see your windows shares in the Places->Network menu.

But the OP hasn't said anything about windows shares... :confused:

---

### Post by lapubell on 2008-09-29
if you need to share files between windows machines, then samba is the tool.

for a *NIX and Mac network, just set up the folders where you want the shared data to go and use sshfs.

it's really simple and works across the internet, as well as local.

example:
mkdir ~/networkDrive (the forlder where I want the share to show up on my machine)
sshfs UserName@ServerAddress:/ ~/networkDrive (this would give you access to the root of the server with the same permissions as that of "UserName")

Mine looks like this:
sshfs lapubell@192.168.3.150:/ /media/server
so this makes the machine at 192.168.3.150 accessable to me at /media/server.  get it?

---

### Post by kman14 on 2008-09-30
Hey, thanks for the replies.
There's no desperate need for me to set this up - it's more out of curiosity than anything else.

I've got Ubuntu 8.04 on my pc and a laptop - the laptop also has XP on another partition.

I'd like to be able to share things around between the two and print from a single printer that is attached to the pc.

Here's the strange thing - I started this thread because I'd done a lot of reading and eventually came across [[COLOR="Blue"]this[/COLOR]]("http://prash-babu.blogspot.com/2008/05/how-to-setup-samba-in-linux.html") tutorial.
(i think he's a member on this forum), which i tried and which seemingly didn't work.
I created a folder that I wanted to share, in my Home folder called "kmshare" and when I right-clicked and tried to set up the sharing options it wouldn't let me.
I then typed "gksu nautilus" - which, I think, allowed me to get to the "kmshare" folder via "filesystem/home....etc - as root; where I could enable the share option through the right click menu. (I know little about the command line - not sure if this was the right thing to do.)

Anyway, a couple of hours later I came back to the computer and clicked on "Network" from the "Places" menu.
This opened up Nautilus and in the window was an icon: "Windows Network".
Clicking on that revealed a new icon: "Workgroup".
Clicking on that revealed a new icon: "Mookow-home", (Mookow is my username on this computer).
Clicking that revealed two folder type icons: "kmshare" and "print$".
Clicking on the "kmshare" reveals the file I'd placed there as a test.

I then went to the laptop - clicked on "network"etc etc, and found "kmshare" and inside it was the test file.:shock:

So, to cut a long story short, (too late), it seems to have worked and yet I have very little idea how or why.

Here's a question.
If I shared my home folder instead of the "kmshare" folder does that mean I could access everything in that folder (pictures, videos, documents tec), on my laptop?

Scrap that. I tried that and it seems to work.

Is there a way to do this remotely?
If I'm out and about with the latop - can I access my pc?
Is this what "shh" or "ssh" is?

I'm going to look at printing from the laptop now.

Thanks.

---

