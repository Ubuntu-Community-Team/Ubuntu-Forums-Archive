---
title: "Adding packages - mass confusion"
date: 2006-03-07
forum: Repositories &amp; Backports
---

### Post by Paul Sherman on 2006-03-07
I just installed Warty from a CD and want to add packages (and probably
update).  When I went into Synaptic, it only shows the packages already 
installed.  I read the How-to Wiki and it looks mostly like I'm doing what 
I'm supposed to, but apparently not....  My questions:

1.  Are there more packages on the CD than were loaded at install?
2.  From the Wiki, it says Synaptic may not work if I use a router and
don't have a static IP.  The workaround sounded like it would cause me 
to have to reconfigure my whole network and/or pay my ISP for a static
address.  Is that so?
3.  Am I missing something glaringly obvious? (probably)

Also, I am having an issue with connection speed (seems limited
to ~40Kb/sec), so massive file downloading takes some time... 

I was going to post this on the absolute beginners forum, but I've been 
using various RedHats for several years (so the sticky said to go 
somewhere else)- this is my first attempt at a Debian based distro....

---

### Post by ssalman on 2006-03-07
[quote=Paul Sherman]I just installed Warty from a CD and want to add packages[/quote]

 Well, I started with Breezy, So I'm not sure how it used to be, but I do have a dynamic IP from my ISP, and I have a router, and Synaptic works just fine. If you are looking for more applications than what you see in synaptic, you need add other repositories (such as the universe). It is straightforward and I didn't need a how-to to walk me through, and I'm new to Linux. Give it a try, but again that's all said for Breezy.

---

### Post by Paul Sherman on 2006-03-07
I looked for a way to add the universe and didn't spot it.

Is there something I need to type in? (which is terrifying, as
I'm dyslexic and can mistype the simplest item without 
knowing it, typing in a long address string is basically impossible).

I'm at work right now, so can provide more details about
what I didn't find when I get home and on the system.

---

### Post by ssalman on 2006-03-07
Check out this wiki page, no typing required :)
[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29]("https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29")

---

### Post by Paul Sherman on 2006-03-07
more mass confusion?

I went through that Wiki last night and thought I had followed it...
If memory serves, all I saw were a link to my CD, and two archives
(with no mention of universe or multiverse).  Could be because
I'm using Warty

I'll try again this evening.  Now that I'm registered, I can pass on
what I see and sort this out.

All to try and load Frozen Bubble...

---

### Post by Ptero-4 on 2006-03-07
From the Wiki:

For Warty.
"Start Synaptic Package Manager from the Computer , System Configuration menu"

For all version of ubuntu.

1. "In Synaptic, choose the Repositories item in the Settings menu"
2. "A list of repositories is shown. Click the Settings button at the bottom and tick Show disabled software sources. Then click the Close button."
3. "You should now see checkboxes next to the repositories. Scroll down and enable the Universe repository by ticking the checkboxes next to the Community Maintained (Universe) entries. To enable the Multiverse repository, for each of the Community Maintained (Universe) entries click on the entry, click Edit, then change the entry for Sections from 'universe' to 'universe multiverse'. Click OK to save your settings."
4. "Save the changes and close the window by clicking OK and update the list of available packages with Reload in the main window."

That's it. Now you can install apps from the universe repository.
And no typing required. And other thing. IIRC Synaptic works the same on all ubuntu versions (IP-wise).

---

### Post by az on 2006-03-08
[QUOTE=Paul Sherman]
1.  Are there more packages on the CD than were loaded at install?.[/QUOTE]

Yes, and they are cached onto your hard drive during the install.

[QUOTE=Paul Sherman]

2.  From the Wiki, it says Synaptic may not work if I use a router and
don't have a static IP.  The workaround sounded like it would cause me 
to have to reconfigure my whole network and/or pay my ISP for a static
address.  Is that so?.[/QUOTE]
Where did you read that?  That's not the case.  You do not need a static IP.

[QUOTE=Paul Sherman]

3.  Am I missing something glaringly obvious? (probably)

Also, I am having an issue with connection speed (seems limited
to ~40Kb/sec), so massive file downloading takes some time... 
.[/QUOTE]

Some repositories see a lot of traffic and are slow.  You should really dist-upgrade to Breezy if you have the bandwidth.  There have been a lot of changes and improvements.

---

### Post by Paul Sherman on 2006-03-09
OK, I'm back on the system (finally)

I printed the info from the Wiki

I did the Synaptic > Repositories  part
I see repositories (with check boxes), but no 'universe' on them.

Here's where it gets weird...
There's no 'setting' button in the 'repositories' menu
to enable the universe.

What can I do?
Confuseder and confuseder  :confused:

---

### Post by Paul Sherman on 2006-03-09
Also, as an experiment, I JUST tried getting frozen-bubble via
apt-get in the command line.  (Copied what I found elsewhere on the site)

sudo apt-get install frozen-bubble

Response was:

Reading Package Lists... Done
Building Dependency Tree... Done
E:  Couldn't find package frozen bubble

I'm sooooo confused...

---

### Post by Lord Illidan on 2006-03-09
Erm, is there any reason why you are using Warty? It is quite outdated now that Dapper Drake is coming out in a month.
Use Breezy Badger, at least..

---

### Post by Paul Sherman on 2006-03-10
Yep, there is a reason.

It's the only Ubuntu CD I have.

With an internet connection of 40KB/sec, downloading an upgrade
or new version is not too viable.  When I did install it from CD 
(last week), I had to let the install run overnight just because 
downloading the updates ran a few hours.

FYI - I'm not sure what's bogging down the connection,
it's DSL and should be faster, but isn't.

Basically,if I don't run Warty, I don't run Ubuntu.

For those familiar with Warty:

When in 'Repositories' I can bring up any listed repository
in another window, and the link appears editable.

Does this mean if I add 'universe' on the end of the link 
save it and refresh, that I may be able to access the archives?

---

### Post by Ptero-4 on 2006-03-16
Have you tried your DSL with other linux distros b4? I ask b/c some DSL ISP's are quite unfriendly towards linux users and do nasty things like intentionally setting your DSL speed to some low setting if they detect you're running linux.

---

### Post by Paul Sherman on 2006-03-17
It appears to be OS independent, does it when I'm running Windows too.

When I can get some time to work on the network (without my wife around,
she gets real unhappy when she can't get to her e-mail), I'm going to bypass the router and see if that helps.  It'll at least help me narrow down the
problem.

Is there a handy source for a single CD of a newer release?
I got the Warty directly from Ubuntu - 10 copies was the minimum order.  
I still have several here (not much of a promoter), and feel real uncomfortable doing it again just for a new release.

---

### Post by Ptero-4 on 2006-03-18
You just need to order it from shipit. It&#347; free, they even pay the shipping fee for you. And IIRC their system has a minimun of one copy not 10 (It may have been set like that after warty though).

---

### Post by aysiu on 2006-03-18
Your DSL is slow on Windows, too?
Maybe you should complain to your internet service provider.

Ubuntu hurts on slow internet speed.

---

### Post by Paul Sherman on 2006-03-19
Success!!!!

I don't know what happened, but tonight I went back into
Synaptic, looked at the Repositories (with the CD in, to see
if it had any unloaded packages), and spotted two unmarked
repositories.  I could swear they weren't there before, but

When I looked at them, the details said they were 'universe'...
I selected them and reloaded - the indexes were downloaded.

For the true test I decided to try and get Frozen Bubble -
selected it and let'er buck.

Downloaded and installed (took a little while with that 40K
connection).  I just played a round - no sound, but otherwise
it worked....

Thanks for the gentle help through the process.

Now to work on ssllooww connection.
1st step, bypass the router and see if that helps.

Also, will see about that single copy of a newer distro.
But this old gray f**t is happy now and gonna hit the sack.

---

