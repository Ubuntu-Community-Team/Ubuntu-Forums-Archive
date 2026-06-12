---
title: "Does a beginning home user need more than ufw and ClamAV?"
date: 2024-10-29
forum: New to Ubuntu
---

### Post by mavengarlick on 2024-10-29
Hi! I have Ubuntu 24.04.1 LTS which I just upgraded to Pro-the free version for home users. I installed ufw and ClamAV, but I'm wondering if I should add more security utilities? Duck.ai chat advised adding fail2ban, knockd, and SSH hardening instruction which I've posted below. 

As a beginning linux user, I'm not doing anything important or "critical" but I do want to protect myself since I have financial info etc on my laptop. I have been searching for these here and have seen mostly posts that are over my head, not direct advice on what a newbie should consider installing, but I have been able to cross off rkhunter and knockd from my list. It does seem that many users are using fail2ban and SSH hardening protocols though.

Do I need the added stuff or is just ufw and ClamAV along with Ubuntu Pro a reasonable strategy? 

2. **SSH Hardening**
 If you are using SSH, consider hardening your SSH configuration:
 
[LIST]
[*]Change the default SSH port (22) to a non-standard port. 
[*]Disable root login via SSH. 
[*]Use key-based authentication instead of password authentication. 
[/LIST]
 You can edit the SSH configuration file:
 bash


[LEFT][COLOR=var(--sds-color-text-01)][FONT=var(--sds-font-family-monospace)][COLOR=#393A34]sudo[/COLOR] [COLOR=#393A34]nano[/COLOR] /etc/ssh/sshd_config
[/FONT][/COLOR][/LEFT]

 Make the following changes:
 ini


[LEFT][COLOR=var(--sds-color-text-01)][FONT=var(--sds-font-family-monospace)]Port <your_custom_port>
PermitRootLogin no
PasswordAuthentication no

[/FONT][/COLOR]
[/LEFT]

---

### Post by ajgreeny on 2024-10-29
Don't bother with anti-virus applications of any sort unless you are running a mail server when clamav may be considered.
If you're running a standard desktop system (even if it's on a laptop) forget about viruses as they arejust about unknown in the wild in Linux and therefore running antivirus is pointless.

For more information on this and much else about security in Linux read through the details at [https://easylinuxtipsproject.blogspot.com/p/security.html](https://easylinuxtipsproject.blogspot.com/p/security.html)

Most of what you have needed to use in Windows is no longer necessary in Linux so be prepared to rethink everything related to the OS security.

And finally don't forget that the weakest part of security in computers is usually the person at the keyboard

---

### Post by mavengarlick on 2024-10-29
Uh oh, I think I'm in trouble! :redface:

Seriously though, thank you for the advice. I take it well! My general computing ignorance is a problem I'm working daily to mitigate. I've learned to research carefully commands I get when asking ai for help. And I'm trying to limit where I download utilities and apps, since I don't yet know the linux world well enough to know who is trustworthy. But I'm making a big assumption that Ubuntu repositories are safe. Lots to learn for sure! But I feel better about not being able to afford a W11 pc these days. Trying Ubuntu has made me realize I've been quite unsafe with my W10 pc and my smartphone too! But trying to secure those is really frustrating. Linux is sort of fun even when stressful.

---

### Post by TheFu on 2024-10-29
There's a security subforum here.  Go there, read all the "Sticky Threads" at the top.

Security isn't a checkbox or a list of programs to install, it is a process.  If you don't use ssh, then adding ssh protection isn't useful.  Only you know which network services are running on your system, so only you can decide which firewall rules or which log monitoring brute-force blocking tools are needed.

My #1 security tool is automatic, daily, versioned, backups.  With those, should anything go bad, I can get back to the way it was the day before or 20 days ago or 86 days ago.  That's very powerful.  I can also compare file changes over all that time, so if I do get hacked, I can know with some confidence what they did and didn't actually accomplish.

Also, be careful trusting AI to provide good answers.  About 50% of the time, I find the answer to be either incorrect or making assumptions that don't apply.

---

### Post by ian-weisser on 2024-10-29
A default install of Ubuntu is secure and safe to use.

No further "hardening" action is needed.
There is a lot of clickbait hogwash out there, Ignore it (and don't click on it). 
Almost anything AI-written on this topic will be baloney, often lifted from the clickbait. AI/LLM don't care about what's true or false. Easy to read, persuasive baloney is still baloney. 

It's open source software. We have choices. Why would we use a distro that *wasn't* secure and safe by default?

---

### Post by Rubi1200 on 2024-10-30
Been using Linux for 19 years now. Never needed an AV or any other special tools.

One thing you might want to consider is using something like firejail to secure/harden your web browser.

But if you don't know what you are doing, I would just leave it and use defaults because, as pointed out, Ubuntu is already secure out-of-the-box.

My recommendation is to spend some time and effort learning and understanding the Linux filesystem and command line. It will make you a better user and give you a greater understanding of what you have now in your hands.

---

### Post by pantazi on 2024-10-30
> **Rubi1200 said:**
> 

My recommendation is to spend some time and effort learning and understanding the Linux file system and command line. It will make you a better user and give you a greater understanding of what you have now in your hands.

Wise words and this quote should head the 'New to Ubuntu' thread.

---

### Post by Autodave on 2024-10-30
Never ran any AV on any of my machines......and one of which was open to the public.  Relax.

---

### Post by Norm24 on 2024-10-30
I do use Clamav as I have over the past year been doing a lot of back and forth with others who use Windows,done more for them than me.

As @Rubi1200 suggested Firejail is a great sandboxing tool for your browser especially if you do online banking/bill paying etc.

Outside of that there isn't really much you need to do out of the box.Security in Linux is more using common sense than anything else.

---

### Post by maglin2 on 2024-10-30
> **Norm24 said:**
> As @Rubi1200 suggested Firejail is a great sandboxing tool for your browser especially if you do online banking/bill paying etc.
I'd be surprised if firejail works with the default Ubuntu browser (Firefox snap - already sandboxed). But then I'm often surprised!

---

### Post by Norm24 on 2024-10-30
> **maglin2 said:**
> I'd be surprised if firejail works with the default Ubuntu browser (Firefox snap - already sandboxed). But then I'm often surprised!

Can't say as I've only ever used .deb package of FF to which Firejail works fine with.

---

### Post by mavengarlick on 2024-10-30
> **maglin2 said:**
> I'd be surprised if firejail works with the default Ubuntu browser (Firefox snap - already sandboxed). But then I'm often surprised!

Yes, I'm using the default Ubuntu browser and glad to see this. I've been trying to stick to snap packages since that's Ubuntu's default. I've run into some users that don't like snap packages and refuse to use them, but I don't know enough yet about linux to really understand their reasons. My understanding is that it's more secure, easier to update, and easier to uninstall if needed. I'm interested in trying firejail, but I think I need to better understand how snap packages work first.

I do backup my files every day to a google drive with Deja Dup, and using Timeshift to create snapshots of my system. But I haven't used either of these yet to practice retrieving a file or restoring my system. I've never had a successful restoration of files using Windows backup or the backup function I had on the smartphone I had that got damaged, so I'm a little nervous about that. Saving photos in my Google Drive is my only successful backup history. 

I'm struggling with the idea of uninstalling ClamAv as suggested in the link provided by ajgreeny: [https://easylinuxtipsproject.blogspot.com/p/security.html](https://easylinuxtipsproject.blogspot.com/p/security.html), but I think it's some kind of Windows trauma reflex. Maybe I'll toughen up after I get enough nerve to practice restoring my system.

---

### Post by 1fallen on 2024-10-30
Firejail will not work with snaps, as already said in this thread.

I'll remain silent on why others like me wont use them, and it is not about hate, it's a matter of strict confinements with them with how we use our system is all....

---

### Post by mavengarlick on 2024-10-30
Thank you for the clarification! My system and needs are much simpler than advanced users I think.

Per the suggestion to read the Security subforum stickies, I've been reading [https://help.ubuntu.com/community/DoINeedAFirewall](https://help.ubuntu.com/community/DoINeedAFirewall). I've gotten a little hung up on whether to use browser extensions with Firefox. It suggests NoScripts and I do have the Bitwarden extension which I'd be lost without. But you and others have suggested no extensions. I definitely won't add anymore, and it's another thing to keep reading up on.

So far, I think my biggest mistake with this install has been only setting up one user account, which has sudo privileges and is also my account for the things that introduce vulnerability like a browser and steam. I created another user account for admin stuff, but I'm a bit scared to assign sudo privileges to it and withdraw sudo from the other.

---

### Post by ian-weisser on 2024-10-30
> **mavengarlick said:**
> So far, I think my biggest mistake with this install has been only setting up one user account, which has sudo privileges and is also my account for the things that introduce vulnerability like a browser and steam. I created another user account for admin stuff, but I'm a bit scared to assign sudo privileges to it and withdraw sudo from the other.

Not quite.
Ubuntu does not use "admin" accounts. That's called the root account, and Ubuntu's is disabled by default. Leave it that way.
Your original user account does not introduce vulnerabilities. It's just a user account. Continue to use it.
When you need to do something admin, you will be prompted for your password.
Simply be aware that being prompted for your password (except during login) means that you are doing something admin, and thus potentially dangerous. Entering your password means "remove the guardrails"

Steam installed from a snap is sandboxed. Your browser installed from a snap is sandboxed. As long as you are getting your software from a trustworthy source (like the Ubuntu Software application), then don't fret. You will be fine.

The #1 mistake Windows users make is to wander the internet downloading software instead of using the Ubuntu Software application. They typically just break their systems and need to reinstall. The most common intrusions are via the browser: Keylogging extensions and cryptominers embedded in shady web pages. They only work when the browser is running. So avoid shady extensions and stay away from shady websites. Use your browser's security features.

---

### Post by TheFu on 2024-10-30
> **ian-weisser said:**
>  
The #1 mistake Windows users make is to wander the internet downloading software instead of using the Ubuntu Software application.  

And only use the GPU drivers that are available through the "Additional Drivers" tool. Don't grab them from nvidia or AMD or Intel directly.

---

### Post by mavengarlick on 2024-10-31
> **TheFu said:**
> And only use the GPU drivers that are available through the "Additional Drivers" tool. Don't grab them from nvidia or AMD or Intel directly.

Thank you, this is good to know. I would reflexively trust them since they're large companies, but I'm guessing this is more of a compatibility issue than a security one? I was very lucky I didn't need to install any drivers with this laptop. Anyway, yes I'll only be installing from Ubuntu repositories moving forward.

---

### Post by TheFu on 2024-10-31
> **mavengarlick said:**
> Thank you, this is good to know. I would reflexively trust them since they're large companies, but I'm guessing this is more of a compatibility issue than a security one? I was very lucky I didn't need to install any drivers with this laptop. Anyway, yes I'll only be installing from Ubuntu repositories moving forward.

Sometimes we need to install stuff from outside the Canonical repositories.  That is possible, but manually downloading some setup.exe or archived file is the very last way anyone should get software for a linux system since around 1997. When I say "last", I mean about 5th on the list of possible methods.  

GPU drivers are a special case - well, nvidia GPU drivers are a special case.  AMD and Intel drivers are pre-included in Canonical's repos.  

[rant]  Don't read, if you are busy.
Nvidia will someday realize their funky method that prevents distro makers from including and integrating their software/drivers into a Linux distro will go away.  I think they've been working on it for about 4 yrs, trying to protect their intellectual property while still making drivers that can be redistributed.  For high-end GPU users, nvidia really is the only game in town - but if you are spending less than $1000 on a GPU, just get an AMD and be much happier.  For the most part, everything on AMD "just works" without doing anything special.  I pulled a cheap nvidia GPU from a system and replaced a Ryzen CPU with a Ryzen APU (that's AMD's name for CPU+GPU in one).  The result was faster performance from the AMD GPU and less power use from the wall, less heat, less noise, and ZERO driver hassles.  The nvidia drivers caused me problems about once every 2-3 months when a new kernel was released.  They must have fixed that in newer releases, but I tend to run 2+ yr old LTS releases of Ubuntu, so dealing with the issue for multiple years got old.

To be fair, the nvidia GPU I had was the cheapest 1030 I could get. I actually didn't want a new GPU, but nVidia dropped support for the 7200GS I'd been using and the free drivers didn't support the screen resolution (1920x1200) I'd been using with the exact same hardware for 5+ yrs.  I'd still be using that 7200GS if I could.  Heck, it might work still and the F/LOSS drivers for it certainly have improved.  Today, all my systems use onboard GPUs.

I never intend to give nvidia another dime, if I can help it.  I have a short list of companies on my "never let them make money off me" list. Some are extremely popular, so many millions of people don't feel the same. That's fine.  When I feel mistreated by a company, there isn't much I can do, beside try to ensure they never get any money from me directly or indirectly.  That 2nd option isn't always possible.  If I were younger and didn't work for myself, I'd have less ability to implement these things.
[/rant]

Thanks, I feel better now.  Sometimes it is therapeutic.

---

