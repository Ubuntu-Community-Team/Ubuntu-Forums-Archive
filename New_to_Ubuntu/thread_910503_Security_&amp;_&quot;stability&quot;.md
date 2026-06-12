---
title: "Security &amp; &quot;stability&quot; ??"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by faron45 on 2008-09-04
2 issues...I need to purchase an airtime card for my phone.I would like to do this online.My concern is,can I do this safely using xubuntu with no anti-virus,spyware or firewall running on my pc ?

Issue #2...Even before installing xubuntu on my pc,I had begun having performance issues.Like,sometimes,when I right click on a link & would like to "open the link in a new tab",instead of giving me that option,a "bookmark" dialogue box would open instead.
 
 And,sometimes,when I click on things,like,trying to go from one tab to another,things seem to become "sticky" or "jumpy".Like the pc seems to be having problems going from one tab to another.Scrolling seems to be "sticky" & "jumpy" also.

I've opened up my system monitor & cpu & memory usage always seem to be quite high.Although,I really don't have much running.And,very few pages or tabs open.Granted,I only have 248.6 mb of mem on this pc [which is double what I had.But,I was having these problems even before I installed the extra memory.
 
 I had to install more memory just to install xubuntu,[for some reason]And,a geek friend of mine installed this,so,I really don't know much about what he did during installation.

Another thing that happens...when I move the cursor with the mouse to go back & fix a mistake sometimes,instead of replacing the cursor,text will be highlighted.

Helllllllllppppppppp !! Anybody have any ideas ? As always,any & all help GREATLY appreciated.

          Yer pal,faron45:(:confused::guitar::mad:

---

### Post by Peter09 on 2008-09-04
Firstly, ubuntu is pretty secure so I shouldn't worry too much about viruses and spyware (its not XP).

As to your performance problems it sounds to me that your touchpad is not set up properly.

Go to System->Preference->Mouse and try changing your settings.

---

### Post by HunterA3 on 2008-09-04
The first part of your call for help is any easy one. There are no real viruses that effect linux. So no anti-virus, spyware remover, or anything along those lines is needed. A good firewall may still be of use, but if you're behind a NAT firewall--such as a Cable/DSL router--you're fine. If you want a software based firewall, try Firestarter. I believe you can find it in the Synaptic Package Manager.

The second part needs a bit more information before we can rule out certain things. First, are you dual booting or running Linux as the only OS on the drive? Second, is this something you've noticed prior to or after installing xubuntu? How old of a machine are you running this on and what are your system specs?

---

### Post by faron45 on 2008-09-04
Peter-Thanks.Apparently,my system is not set up as yours.When I go to "systems" under "applications","preferences" is not there.But,this,I know how to deal with.So,thanks very much for the info.I will check on this.
 
Hunter-Running only Linux.As I recall,these things began happening even before xubuntu install.This machine is old.I would say at least7-8 years old.As far as system specs go,I would have to check into that one.Thanks for helpl & patience.

---

### Post by Peter09 on 2008-09-04
Yes - I am running Ubuntu.

---

### Post by HunterA3 on 2008-09-04
It sounds like your system is using a lot of your swap and is using too much virtual memory because it's running thin on physical address spaces in RAM. If you've got an option to add more, I'd try that. Or perhaps try a lighter weight DE.

---

### Post by faron45 on 2008-09-04
Hunter-Huh ?? Hmmmmm.Sorry my friend.I basically unerstood like [almost nothing] of what you just said.And,DE ??  What is that ? Can you help with any of this ?

---

### Post by HunterA3 on 2008-09-04
Hmm. I'll see if I can reword it. I apologize in advance if it seems like I'm attempting to over simplify this. I also should disclaim that I am not a linux memory management guru so I may be way off on how linux uses physical and virtual memory.

In a typical x86 based PC, your RAM has a limited amount of space for use by the OS and applications. If you've got a lot of processes running, each will require a select amount of space in RAM. Once you've reached the capacity of your physical memory, your OS will begin using the designated part of the hard drive set up for swap or page files. It will store those processes not currently being utilized there until the OS calls for them again. Then it grabs that process, moves it back to physcial memory and moves another program into the swap to make room for the newcomer. Physical RAM is much faster than virtual memory on a mechanical hard drive obviously. Because the hard drive is slower and the fact that the OS has to load and unload processes that are running in order to make room for another process, it could look like your PC is slower to respond as well as slow on-screen image rendering which may explain the "sticky" or "jumpy" behavior. Adding more RAM to your system can sometimes corrrect this behaviour.

Oh and DE would be Desktop Environment :)

---

### Post by oldos2er on 2008-09-04
Firestarter is just a GUI front-end to the already-installed software firewall "iptables."

---

### Post by faron45 on 2008-09-04
Hunter-thanks for all that.So,basically what you're saying is instead of being able to tweak a few things here & there,I should try installing more ram ? And,as far as DE's go,more than likely,I'm probably using the lightest DE there probably is considering the person who installed xubuntu on here, realized that memory was already a problem on this pc.Is there any way that you could help me to find out if I could get any lighter ?

---

### Post by HunterA3 on 2008-09-04
You could download and compile a newer kernel and get better performance since the generic kernel loads some things you probably won't or don't need.

---

