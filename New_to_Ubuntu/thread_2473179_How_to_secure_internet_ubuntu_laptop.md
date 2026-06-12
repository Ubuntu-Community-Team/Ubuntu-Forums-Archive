---
title: "How to secure internet ubuntu laptop"
date: 2022-03-26
forum: New to Ubuntu
---

### Post by bhubunt on 2022-03-26
Hi,
I got a new laptop with Ubuntu 20.04, which I am going to be using with an ethernet connection. 

I would like to enable ufw. What exactly do I need to do to protect my OS, w/o blocking my ability to connect to the internet? My aim is not to get hacked ;-).

Do you need to set up an account for livepatch or can you use it w/o an account?

And I need to get rid of bugs in Ubuntu 20.04?

 What's the best anti-virus protection?

I did update the OS but I noticed my connection is slower than on my windows computer. Is there anything I need to do to speed it up?

Thanks for the suggestions!

---

### Post by psychohermit on 2022-03-26
Welcome to the forum.

Here is my firewall rules.  You will want to add 25 & 110 tcp for email if you're using traditional email.  I'm using web mail so I don't need it.

```

sudo ufw default deny incoming
sudo ufw default deny outgoing
sudo ufw allow out 53,67,68/udp
sudo ufw allow out 53,80,443/tcp
sudo ufw disable && sudo ufw enable

```

They say you don't need antivirus for Linux.  You need an account for livepatch, and the email should match what your email is for the forums.

--glenn

---

### Post by #&amp;thj^% on 2022-03-26
**Please take this as I'm **not** trying to go over the top, but...If it's facing the internet, all bets are off.
To be clear, the only way you can achieve 100% network security is to turn off your devices, put them into a safe and never use them again. Why is this? Simple – because most security issues come from our own mistakes. Human error is the number one issue you’ll run into with network security in my opinion.

Because there is no silver bullet to keep your network safe, I recommend using all the tools at our disposal. In addition to that, it’s also important to verify that everything is operating correctly on a schedule. For myself personally, I usually setup an “audit” day once a month to really drill down on everything. This means checking logs, verifying applied patches and looking for anything out of the ordinary.

Security is a very broad, potentially daunting subject to a new Ubuntu user. It's crazy to think that anyone can boil security down to a list of 7 things. 
A good start: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by grahammechanical on 2022-03-26
> And I need to get rid of bugs in Ubuntu 20.04?

If you identify a bug in Ubuntu you cannot get rid of it unless you are a computer programmer and are able to edit the source code of Ubuntu. But we can report bugs.

[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

The Ubuntu Weekly Newsletter has information about the number of bugs being worked and the security vulnerabilities being fixed.

[https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue727?action=show&redirect=UbuntuWeeklyNewsletter%2FCurrent](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue727?action=show&redirect=UbuntuWeeklyNewsletter%2FCurrent)

The Linux developer community work very hard to identify bugs and vulnerabilities and fix them. An updated OS is more secure then an OS that has not been kept up to date. The advantage of Livepatch is that it will install security updates to the Linux kernel without requiring a system reboot. This is very useful in the business environment.

[https://ubuntu.com/security/livepatch](https://ubuntu.com/security/livepatch)

Home users without Livepatch are required to authenticate a Linux kernel upgrade and are then offered the options to "restart now or restart later."

Regards

---

### Post by DuckHook on 2022-03-27
If you are relatively new to Linux, your questions are completely understandable, but please appreciate that what you are asking is like the old Douglas Adams sendup—you are asking for the answer to Life, The Universe and Everything. With tongue planted firmly in cheek, I could reply "42", but that wouldn't help you at all, would it?

What I'm trying to say is that the answers to your questions are complex, involved, very deep and cannot possibly be summarized in a forum thread. As others have pointed out, you need to do your research and educate yourself about the details, then make your own decisions. Recommendations from other forum members have limited applicability when it comes to matters like security. You will have a different risk tolerance than me, your use case is different than mine, your balance of convenience over security will be different, and so on.

1fallen has given you wise words. Security is a lifelong learning exercise. The more you learn, the better you will get at it and the more secure you will be. It comes slowly and in stages. Reading through the material in his link is a great start.

At the risk of diluting your attention from that excellent link, I will add this:

Windows users have been conditioned to approach security by way of magic thinking. Whether it is magic apps that enhance security merely by installing them (antivirus), magic OSes that come "pre&#8209;hardened", or magic settings that one adds to ones configuration and then forget about. These all suffer from the same fallacy: security is not about outside factors that involve adding things or tweaking things, it's about inside factors that involve personal discipline and good habits. The weakest security link is always the entity between the chair and the keyboard and the vast majority of security failings are due to user foolishness and poor computing hygiene.

Example: it doesn't matter how "hardened" you make your firewall rules. If you visit a bad site and download bad stuff, no amount of hardening will save you. Another example: we routinely get new users who come on these forums asking to nerf challenge/response. There really is no helping such people and I wish they would stick to Windows where they can continue to foul that nest instead of fouling ours.

As to specifics, a real world example of why security isn't just following some recipe can be seen in psychohermit's ruleset. This works only for his specific use case. It would break my system because I use not only an imap/smtp client but also nfs, steam, openvpn and a few high ports for network monitoring utilities. You need to know your network topology to apply firewall rules intelligibly. Otherwise, you are either breaking your setup due to too much constraint, or kneecapping your firewall due to too much laxity.

Again, separate from but related to firewall rulesets are sandboxing rulesets. How hardened are your apparmor profiles? Are you prepared to install SELinux? Note that both are quite arcane and require a lot of initial elbow grease.

You may be starting to see how complex Linux security can get.

I don't want to discourage you. Good gracious, anything but that. I think you are off to an excellent start just asking about this topic. So here's what I would suggest.

Instead of asking a bunch of overly broad questions in shotgun style, try narrowing your approach down into a series of bite size pieces. Take them on one at a time. That way, you have an excellent chance of digesting them. For example, start only with firewall rules. Learn the fundamentals (like how to prevent yourself from locking yourself out), then apply rules methodically and patiently. Ask *specific* questions on these forums once you've had an initial go at it yourself. You will get far more out of your efforts that way (and you will avoid cheeky answers like "42" from dolts like me).

Good Luck and Happy Ubuntu-ing!

---

### Post by ActionParsnip on 2022-03-27
Run the browser in a docker. Run it as a restricted user and not root. Could always add anti ad stuff to your hosts file or deploy a pihole.

---

### Post by mIk3_08 on 2022-03-27
> **bhubunt said:**
> Hi,
I got a new laptop with Ubuntu 20.04, which I am going to be using with an ethernet connection. 
I would like to enable ufw. What exactly do I need to do to protect my OS, w/o blocking my ability to connect to the internet? My aim is not to get hacked ;-).
Do you need to set up an account for livepatch or can you use it w/o an account?
And I need to get rid of bugs in Ubuntu 20.04?
 What's the best anti-virus protection?
I did update the OS but I noticed my connection is slower than on my windows computer. Is there anything I need to do to speed it up?

Thanks for the suggestions!
In my case. Its all about the user. Using ufw is not bad. It is you who will make your machine safe but once your in the internet meaning your machine is open to all kinds of threats. So you be careful.
> **bhubunt said:**
> 
Do you need to set up an account for livepatch or can you use it w/o an account?

Yes you need to create an account. so Good Luck and cheers

---

### Post by bhubunt on 2022-03-27
Thanks psychohermit and all but I am not sure what to do. So all I did was type the following code: enable ufw. Is that enough? 

I am afraid I am not very tech savvy and function best if I get the code.

And do I need ClamAv?

Thanks also for this link: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity) 

I believe I have basic security as I enabled ufw. But I did not enter any rules, as I am not sure how to do that or what to look for. 

In the terminal it says status active -- deny incoming, allow outgoing, disabled routed

Now I wonder if I need to close ports or not through which hackers typically might enter. I don't have VPN, am simply using a cable connection.

What code do I need to enter for closing which ports? And will this hamper my internet access?

---

### Post by DuckHook on 2022-03-27
Okay. A short firewall primer:

Ubuntu already comes with incoming ports turned off by default. However, these are implicit settings. What this means is that if an app asks to have a port opened, Ubuntu will allow it.

When you install UFW and turn it on, it changes those incoming rules to explicit ones. This means that even if an app requests it, the firewall will not allow the port to open. This is clearly more secure. However, if an app needs an open port, then explicit firewall denial rules will break the functionality of the app. This is the reason you need to understand your network topology before anyone on this forum can help you.

As only some examples:

[LIST=1]
[*]Do you use nfs? This is the common network file sharing protocol used by 'nixes.
[*]Do you use openvpn? This is the protocol used to establish strong encrypted tunnels between different devices.
[*]Do you use wireguard? Like openvpn above.
[*]Do you use ssh? An encrypted protocol used to access remote shells securely.
[*]Do you use smb? The "Windows" version of nfs.
[*]Do you use rdp? This is a dangerous one that many people nonetheless use. It is the protocol that allows users to manipulate remote desktops across their local LAN or even across the Internet.
[/LIST]
There are dozens of other services, all requiring their own ports.

We have no idea what services you are running, or how your system is set up, so how can we advise you?

Do you access the Internet through a router? If so, then it is arguably more important to have good firewall rules set up on your router than on your computer (though both wouldn't hurt).

It's complicated.

Hackers do not enter through "typical" ports. They enter using social engineering methods like phishing or spear&#8209;phishing that fool uninformed or careless users into installing malware. Most (but not all) Linux apps that rely on open ports are typically hardened against penetration, but this relies on you keeping your system patched. Many new users will turn off all incoming ports and live quite happily. But some will encounter the problem where they graduate to become power users, try to run some app or service, forget they have strict firewall rules set up, and then spend a great deal of time and trouble trying to figure out why their new service isn't working. So, yes, firewall rules can potentially hamper your Internet access, but this depends on how you access the Internet.

Antivirus is not needed in Linux, but this is a hotly debated point and my position is not shared by some. However, it is worth noting that ClamAV is just a scanner (as it should be) and does not plant hooks into your kernel like the commercial Antivirus vendors do. In my opinion, monkeying around with my kernel by outsiders is absolutely verbotten, which makes commercial AV something not much short of malware itself, but again, this is my personal opinion. It is also worth noting that there are few (if any) Linux viruses in the wild. An AV product would not be catching Linux malware. They are almost all designed to catch Windows malware. Yet again, my personal view on this subject is that Windows should look after its own problems and not obligate me to do so for them.

Clearly, I do not have AV installed on any of my systems. I've been operating Linux for well over a decade and have never run into a malware issue. I would encourage you to gain an understanding of how AV actually works before deciding whether to install it or not. Again, try to avoid the whole "magic app" thinking that is so prevalent in the Windows universe from which you came. You do not automatically gain extra security just because you install AV. You may actually be compromising security because you are adding attack surface for no good reason.

---

### Post by TheFu on 2022-03-27
43.  That answer is 1 better than 42.

There used to be a sticky thread in the top of the Security sub-forum  (308).  Read through that.
If you aren't comfortable using ufw, use gufw. It is a little GUI.  For most home users, enabling GFW with a default DENY inbound will be as far as they want to go.  But if you have other devices on the same LAN an wish for them to have access to your Ubuntu system or files, they will be denied.  There are options in GUFW to allow inbound LAN access, but block inbound non-LAN access.

Security is not just a checkbox.  It is a process.  For me, it is complex enough that I have a checklist to work through.  Most of what I do is because over the decades I've had systems hacked by professions and simple bonehead kiddies.  It is never ending, the learning to be just a bit more secure.

If you care about security, don't use wifi or bluetooth. Every current wifi protocol has security faults.
Bluetooth has been a security nightmare, always.  I've actually been hacked over bluetooth on a freshly installed and patched Ubuntu laptop. I was a target.  So ... that wireless keyboard, mouse, headset, cell phone connection, speakers ... all very bad for security.

I'll leave you with these ... patched weekly.  Don't patch daily or more often. Weekly is sufficient to handle 99.95% of the issues a home user should hit. 

Patch your router monthly. If it hasn't gotten any patches in 3 months, time to get a new router.

Avoid automatic patching. It is too easy for those to fail and cause bad things.

Stay on a supported Ubuntu release and move to the next during the overlap period while both releases are supported.  Use only LTS releases, not the non-LTS versions.  If you are a target for some reason, they will find a way in, but probably NOT through Ubuntu.

Learn about and create versioned backups of any data you don't want to lose.  Daily or weekly, are ideal.  Test the backups. Ensure you KNOW how to recover afterwards. Untested backups aren't sufficient. Until you actually test the restore, you'll never really know what is missing.  Dragging and dropping a directory to other storage **isn't** a proper backup.

---

