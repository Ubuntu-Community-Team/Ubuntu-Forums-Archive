---
title: "how to off updates? any download."
date: 2022-03-29
forum: New to Ubuntu
---

### Post by ax3lpl on 2022-03-29
Hello, after trying to disable update multiple times - question - How to disable ANY updates in ubuntu? What should I set so that ubuntu does not download anything from the internet (NOTHING means NOTHING)

---

### Post by ajgreeny on 2022-03-29
> **ax3lpl said:**
> Hello, after trying to disable update multiple times - question - How to disable ANY updates in ubuntu? What should I set so that ubuntu does not download anything from the internet (NOTHING means NOTHING)
That would be a very silly and dangerous thing to do!

Why do you wish to stop all updates?

---

### Post by crip720 on 2022-03-29
The easiest way to have NOTHING means NOTHING is to disable wired and wireless setting, this will prevent everything to do with the internet, no downloads, no cookies, no browsing.  If you only want to disable updates, which is a very bad idea if you still want the internet, then there settings in the update manger to disable them.  It is up to you if you want your machine to be hacked, read all your passwords to banks/online stores that have your credit information, have someone clean out your bank accounts.  Your choice, but updates are mostly safe to do.

---

### Post by him610 on 2022-03-29
I do not use Ubuntu myself as I strictly use Xubuntu on my machines; however, you probably have in Settings a widget for Software & Updates. There are tabs in Software & Updates - one being 'Updates'. In Tab Updates, there are configurable options for updates that one can choose. You should explore those options; however, you are advised to ***never*** turn off security updates.

---

### Post by QIII on 2022-03-29
I believe that setting is found at the power outlet to which you have your modem/router/gateway connected.

Are you certain you understand what you are asking for?

We can tell you how to do something foolish if you would like, but this is a case where such foolishness could affect a community through a compromised machine.  This would probably not be in your best interests or that of the community.

---

### Post by DuckHook on 2022-03-29
Please provide some context. Are you trying to turn off automatic updates because you want to have fine manual control over the update process? Or do you wish to never update again, period?

---

### Post by mastablasta on 2022-03-30
i have it set to just check and notify about new updates, but not to download them.

on server i have automatic security updates, but for feature updates it would send me an email notification. 

anyway all this can easily be disabled so that no updates are checked for or done. but from the observed regular daily attacks on server, this is a suicide option. it is a free world, but one's freedom ends with anothers. so when that PC starts attacking others in the net...

---

### Post by ax3lpl on 2022-04-14
> **ajgreeny said:**
> That would be a very silly and dangerous thing to do!

Why do you wish to stop all updates?

> **crip720 said:**
> The easiest way to have NOTHING means NOTHING is to disable wired and wireless setting, this will prevent everything to do with the internet, no downloads, no cookies, no browsing.  If you only want to disable updates, which is a very bad idea if you still want the internet, then there settings in the update manger to disable them.  It is up to you if you want your machine to be hacked, read all your passwords to banks/online stores that have your credit information, have someone clean out your bank accounts.  Your choice, but updates are mostly safe to do.

> **him610 said:**
> I do not use Ubuntu myself as I strictly use Xubuntu on my machines; however, you probably have in Settings a widget for Software & Updates. There are tabs in Software & Updates - one being 'Updates'. In Tab Updates, there are configurable options for updates that one can choose. You should explore those options; however, you are advised to ***never*** turn off security updates.

> **QIII said:**
> I believe that setting is found at the power outlet to which you have your modem/router/gateway connected.

Are you certain you understand what you are asking for?

We can tell you how to do something foolish if you would like, but this is a case where such foolishness could affect a community through a compromised machine.  This would probably not be in your best interests or that of the community.

> **DuckHook said:**
> Please provide some context. Are you trying to turn off automatic updates because you want to have fine manual control over the update process? Or do you wish to never update again, period?

> **mastablasta said:**
> i have it set to just check and notify about new updates, but not to download them.

on server i have automatic security updates, but for feature updates it would send me an email notification. 

anyway all this can easily be disabled so that no updates are checked for or done. but from the observed regular daily attacks on server, this is a suicide option. it is a free world, but one's freedom ends with anothers. so when that PC starts attacking others in the net...

In the "update" settings I have already changed everything so that it does not download, so that it only informs about security updates, so that it informs about all security. But these changes WILL NOT CAUSE ANYTHING !!! These are selectable options and it doesn't work at all. Same download hours ... no matter what you set, it downloads whenever it wants. Often during the day and the internet slows me down because I have a data limit. after exceeding it, the download speed drops to 128kb / s. I wanted to turn off autoupdate while I AM USING the Internet. IS IT POSSIBLE TO DO IT SOME OR SIMPLY
UBUNTU IS LIKE THIS?

---

### Post by ActionParsnip on 2022-04-14
[https://linuxnightly.com/how-to-disable-automatic-updates-in-ubuntu/](https://linuxnightly.com/how-to-disable-automatic-updates-in-ubuntu/)

Its a REALLY bad idea. You can do it. It's your funeral

---

### Post by ax3lpl on 2022-04-14
why bad? Can I turn off the update when I use the Internet and turn it on at night?

---

### Post by ActionParsnip on 2022-04-14
> **ax3lpl said:**
> why bad? Can I turn off the update when I use the Internet and turn it on at night?

I guess. That makes sense. You could even cron it if it's command line based

---

### Post by deadflowr on 2022-04-14
Do you have a metered connection option under the network settings?
(In the network settings click on the cog icon for your current connection to open it's settings window)

---

### Post by ax3lpl on 2022-04-14
So you can't just "turn off" the download by blocking the process from connecting to the internet? There are so many things to do to stop? Do you type everything in the terminal?

---

### Post by ax3lpl on 2022-04-14
> **deadflowr said:**
> Do you have a metered connection option under the network settings?
(In the network settings click on the cog icon for your current connection to open it's settings window)


[COLOR=#000000]This "metered connection" is broken at all, if I want to change it, no window opens, nothing. Sometimes it shows, sometimes it is, sometimes it is not - like in the lotto.[/COLOR]

---

### Post by DuckHook on 2022-04-14
The developers of an operating system have a thankless task. They must decide how much they automate updates in order to protect fools from themselves. There is no one *correct* approach; just approaches that work for the greatest number so that harm is minimized and security is maximized but all done so that disruption to workflow is also minimized.

Your circumstances are unique enough that this approach does not work for you. That's why you have to take special measures.

The measures are complex because:

[LIST]
[*]Security is hard to achieve. It takes many different systems carefully balanced to get good security. They must provide the widest reasonable coverage without stepping on each other.
[*]Few people want to turn off updates altogether. As you have been warned numerous times, it is a very risky thing to do. Not only do you put yourself at risk, but you also put at risk the entire computing community. The devs make it hard to turn off updates possibly because they want to discourage people from doing so.
[*]Linux is a complex operating system. It is not designed for those seeking simplistic solutions. People who want simplicity use the proprietary OSes. Linux users tend to be geeks who have no problem with more complex solutions.
[*]Ubuntu tries very hard to automate as many things as possible, so turning off complex and bundled services requires a lot of work. If you do not like this aspect of Ubuntu and want finer grained control, then you may wish to consider an even more geeky distro like Arch, Slack or Gentoo. Those distros will not assume that users want a prepackaged set of security measures and will allow you to customize your update routines to your heart's content. However, be warned that they are even more geeky than Ubuntu and will require more scripts and knowledge.
[/LIST]
For those wanting a shallow learning curve, especially for actions that are not common, Linux is the wrong operating system for them.

---

### Post by ax3lpl on 2022-04-17
So linux is for idiots and you have to take something from them, turn it off because they will "break". But at the same time you write that for the intelligent because you have to learn a little yourself. I already know why Windows is so popular - BECAUSE IT WORKS AS IT SHOULD. Unlike something that causes a problem even with an update. Tell me then, if the updates are so important, then ... if I don't have an internet connection for half a year and after half a year I will connect my computer to the Internet, isn't it even more dangerous than the fact that I won't update at 3 p.m. only at 2 am?

---

### Post by DuckHook on 2022-04-17
You are misinterpreting what I wrote.

Linux is not *for* idiots. But because anyone can install it, it does have to defend itself *from* idiots. All OSes do. Some just do this better than others. Between Windows and Linux, it's pretty obvious which one does this better. So, if you still think Windows is superior in this (or any other) respect, then Windows is the OS you should be using.

I get it that you are frustrated and irritated at the perceived lack of control in Ubuntu. In fact, I sympathize with your feelings. I also desire finer&#8209;grained control of all sorts instead of the defaults that are built into Ubuntu. Such control is possible, but it requires fiddling with obscure settings deep within the guts of the OS. So, we actually share a common goal: easier and more personal control of downloads and updates—we don't want this stuff automated—we want to do it ourselves.

I am not saying that our situation is *unreasonable*; what I am saying is that our situation is *unusual*. And because it is not common, other considerations have taken precedence over it. The devs have to address a much bigger problem: people who are not inclined to take any security precautions at all. That's why downloads/updates are automated. And because security is a complex layered process consisting of linked interdependencies, it is not a trivial exercise to unlink them. This is true of all OSes.

ActionParsnip has already given you instructions to turn off all updates in post #9 above. So, it is no longer a question of whether it can be done: only a question of whether you will do it.

I've stated the above in my capacity as a forum member. What follows is in my capacity as staff:

We all understand frustration and irritation and make allowance for the posting style that may result from such feelings. But the forum also has rules which exist for the larger purpose of protecting forum netiquette. These forums work only because we all practice civility, courtesy and mutual respect.

Of course Ubuntu can be improved. Any OS can be improved. But these forums are not the venue for such demands. They are entirely user run and user supported. The devs don't visit here. So, venting your spleen on these threads is not only pointless, it is counterproductive.

I've already had to edit two of your prior posts for unacceptable outbursts. Please refrain from posting in a style that will only alienate those who are here to help you.

---

### Post by QIII on 2022-04-17
> **ax3lpl said:**
> BECAUSE IT WORKS AS IT SHOULD

There is no need to shout about something that is highly debatable, especially in the arena of security.

I believe this thread has run it's course and can go nowhere but into an inevitable series of caustic complaints and poor netiquette.

Closed.

---

