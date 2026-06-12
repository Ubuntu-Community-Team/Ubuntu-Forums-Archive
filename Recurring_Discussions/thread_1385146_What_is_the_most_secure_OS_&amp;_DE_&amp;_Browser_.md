---
title: "What is the most secure O/S &amp; DE &amp; Browser &amp; Add-On set-up?"
date: 2010-01-19
forum: Recurring Discussions
---

### Post by Roger Allott on 2010-01-19
I've been led to believe that, for reasons I really don't even begin to understand, Linux is a more secure O/S than Windows.

As far as I can tell though, it's only more secure if the user doesn't assign root privileges to any old app that wants it. Where it presumably is better is in preventing 'burrowing' of a virus/trojan/worm app from gaining root (or administrator) privileges.

With all the recent hoo-har over Google and China, and Germany & France telling it's citizens to use a browser other than IE, it begs the question of what set-up is currently considered by the computer security peeps as the best at preventing problems. And why.

I'm using Ubuntu (obviously) 9.10 with Gnome and I've recently gone from Firefox with AdBlock to Chromium with AdThwart. Can I improve my security by using a different arrangement?

Are the different DEs vulnerable to different types of attack? For example, could it be said that Kubuntu is more (or less) vulnerable to (say) worms than Xubuntu, or is the choice of DE a bit meaningless when it comes to security?

---

### Post by Mighty_Joe on 2010-01-19
[Use a live CD]("http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html")

---

### Post by Roger Allott on 2010-01-19
> **Mighty_Joe said:**
> [Use a live CD]("http://voices.washingtonpost.com/securityfix/2009/10/avoid_windows_malware_bank_on.html")

Q. "Suggest how you would resolve the staging difficulties inherent in a production of Ibsen's Peer Gynt"

A. "Do it on the radio."

---

### Post by presence1960 on 2010-01-19
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by 3rdalbum on 2010-01-19
Desktop environment is pretty much irrelevent in security discussion because the desktop environment is just the GUI layer and almost nothing in your DE will listen to incoming connections. Any malware will try and get deeper into your system.

Using an up-to-date distribution with a good security record and good security features, with a browser that has a good security record and its own sandboxing system? Excellent.

If you wanted to go overboard, you could run OpenBSD in a virtual machine on top of Xen.

---

### Post by bodhi.zazen on 2010-01-19
Security is a process, you learn how your OS works and you monitor it.

Start with the security sticky linked by presence1960

From there, if you wish, look at hardening Ubuntu, Apparmor, SELinux, snort, OSSEC, niagios, etc.

If you run servers, learn to secure them. For example, ssh - use iptables / fail2ban / denyhosts , use keys (disable passwords), etc.

---

### Post by swoody on 2010-01-19
What should really be kept in mind here is that for the most part, viruses/trojans/malware aren't targeted to you in specific, they mostly prey on 'user ignorance'. Don't click on links or popups that you come across, don't enter your username or password to sites asking for it if you don't recognize them, don't reply to emails that 'might be' from your bank/email client/etc - go directly to the site in question and login there. On top of that, don't try to install random scripts/programs/plug-ins that you find just anywhere on the internet, unless you are familiar with them. It is a *very* rare thing indeed for someone to target you and/or your computer directly, most of what's out there is put up for the general public to come across. The biggest recommendation I can give is to not run anything as Root that doesn't explicitly need it. This was and is one of the main reasons Windows is so vulnerable to attacks - when you install Windows, the first account you setup is an Admin account, and has control over your system. Most users use this as their main account, so any bad things they accumulate are automatically given Admin privileges.

Another good plugin to help you with this is the Web of Trust extension. It uses totalled user ratings of websites to show you a rank of how 'trusted' a particular website is. Another great one is NoScript. This will by default block all java-script on new pages you visit. Java script is *usually* how malware finds it's way onto your computer, so by blocking it all by default it will help tremendously to increase your security. For sites you visit often, you can white-list various things that require java-script so you don't always have to select to see them manually.

Everything I mentioned is very basic guidelines about seciurity. To get much more in-depth knowledge, please feel read over the Ubuntu Security post by bodhi.zazen that was linked above. It does a much better job at going into the intricacies of Ubuntu security, and is great reading for users of all experience levels :)

-Woody

---

### Post by Psumi on 2010-01-19
Tinfoil Hat Linux.

---

