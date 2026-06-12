---
title: "Security for online banking"
date: 2014-10-31
forum: Recurring Discussions
---

### Post by lucy3 on 2014-10-31
Hi all,

I know this question has been asked thousands of times before but people seem to have differing opinions on the security of linux and I need to be sure or as sure as possible for obvious reasons. If I want to access my bank online what protection/security do I need to have installed? 

I'm running lubuntu 14.04 on a 32bit netbook. I have gufw firewall installed and enabled. Is there anything else I should have in place before I log in? I use firefox as my web browser. 

On a related note, when I was using lxle, just switched to lubuntu, I followed this post to try and fix a screen brightness issue, [http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/) but like a newbie I put a quote mark in and messed up my boot sequence! I managed to get boot back by following the instructions in the same post but afterwards my PC name in terminal had changed to lucy@lucy whereas before it was just lucy in terminal. This stayed the same even when I completely erased lxle and installed lubuntu. Does this mean that I moved my root folder and is it a security risk. I would like to change it back if possible.

Thanks in advance.

---

### Post by The Cog on 2014-10-31
To be honest, I would be inclined to use a live DVD or USB stick that you only boot for banking and nothing else. That way, even if you do catch some malware in the course of your normal computer use, it won't be in the OS you use for banking.

---

### Post by buzzingrobot on 2014-10-31
> **lucy3 said:**
> Hi all,

I know this question has been asked thousands of times before but people seem to have differing opinions on the security of linux and I need to be sure or as sure as possible for obvious reasons. If I want to access my bank online what protection/security do I need to have installed? 

I'm running lubuntu 14.04 on a 32bit netbook. I have gufw firewall installed and enabled. Is there anything else I should have in place before I log in? I use firefox as my web browser. 



Using Linux is fine. The greatest vulnerability is the user.  It's much easier to fool the user into giving away secure info. 

I've used online banking for years, with zero issues.  So, here are my recommendations:

Use a strong password at the bank. Don't use it anywhere else.

Bookmark what you know to be the bank's correct URL.  Don't rely on manually entering the URL. People register domain names that correspond to common typos of legitimate domains, and then host scam sites on those domains.

If your bank offers Two-Factor Authentication, use it! E.g., my bank requires 2FA for any transaction to move money out of an account or to set up a new bill-pay item. 

If your bank does not offer Two-Factor Authentication, think hard about find a new bank that does.

If your bank (or credit card issuer) offers optional text/email alerts for things like transactions above a specified amount, or transactions that do not fit your typical pattern, etc., sign up. 

Banks don't want to send out paper statements any more, but I still get one because its arrival in the mail prompts me to look at the transactions it lists, something I'd never get around to doing if the only option was going to their web site.

Banks *do not* need to send you email asking you to verify account numbers, phone numbers, etc.

The fewer times you use the bank online, the less your vulnerability.  I access my bank online once a month to pay bills, from one device, and only that device.

---

### Post by sotiris2 on 2014-10-31
With regards to your pcname in terminal is it lucy@lucy or do you mean lucy@lucy@lucy ???
In ubuntu termina the prompt is username@host-name(PC's name):PATH(by default when you open a new terminal ~ which stands for your home folder, NOT ROOT).  What this means is that you gave your PC the same name as your username. I don't think it is a problem I named mine sotiris-desktop for example. 

Moving your root folder would break the system completely so you haven't done anything of the sort.

---

### Post by MartyBuntu on 2014-10-31
> **buzzingrobot said:**
> Using Linux is fine. The greatest vulnerability is the user.  It's much easier to fool the user into giving away secure info. 



I agree with Buzz. The primary enemy is *phishing*, not *malware.*

---

### Post by Bucky Ball on 2014-10-31
*Thread moved to **Recurring Discussions**.*

Yes, it has been asked thousands of times before.

Live media or a virtual machine is probably most secure. Other good suggestions given. I, like buzzingrobot, have used online banking and bill paying for years with no issue.

---

### Post by rsgangr on 2014-10-31
I use Lightweight Portable Security (LPS-Public Deluxe version), a thin Linux operating system that boots from a CD or USB stick. See the website "http://www.spi.dod.mil/lipose.htm"  It does not mount the local hard drives in the computer. Therefore if you need to download and keep a copy of a Payment Receipt for example, you will have to copy it to a USB stick before rebooting to your usual operating system.

---

### Post by buzzingrobot on 2014-10-31
Lucy, the "lucy@lucy" you see in a terminal is called the "prompt".  It's there to tell you who is logged in (the current user is to the left of the "@") and to indicate where anything you type will be entered.

The prompt has nothing to do with your root folder or any other folders.  The content of the prompt can be controlled by editing an entry in a hidden file in your home folder (.bashrc).

If you do a "sudo -i" in a terminal and provide your password, the current user will switch to "root" and you will see that reflected in the prompt.  Be sure to switch back to your regular user by entering "exit".

The label that appears to the right of the '@' is the 'hostname'.  This has more relevance in a networked environment, but in a typical single-user set up, it amounts to the name you gave your system when you installed it. 

The prompt can be configured in many, many different ways to display many different things. For eample, from something like a simple '>', or to something including the current time and date, to some favorite long string of text you want to put in there. 

I'm not aware of any GUI tool that can be used to configure the prompt. (Doesn't mean there isn't one, though.) If you want to get into configuring it by hand, here's a relevant wiki page: [https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt).  Otherwise, leaving it alone makes sense.  It's just reminding you that Lucy is logged onto to a machine called Lucy.

---

### Post by lucy3 on 2014-10-31
Wow, your're all too quick for me. Thank you for all your replies. 

Cog, great idea. :)

BuzzingRobot, thanks for the advice, happy to say I do all of that/my bank does all that. I completely agree with you about paper statements.


Regarding the terminal name, > your home folder, NOT ROOT). That's a weight off my mind thanks. BUT before I screwed up my boot sequence. It was showing *lucy-n150P* one guess as to what my computer is ;) and since I deleted that folder that screwed up boot, which presumely was deleted with a fresh install of lubuntu it now says *lucy@lucy-N150P* so I'm thinking I must've changed something somewhere.

However if it is > just reminding you that Lucy is logged onto to a machine called Lucy. Then I'll leave but want to be sure.

Should I install anything else or am I fine with just the firewall, assuming I'm sensible and don't go into root without exiting?!

Thanks everyone.

---

### Post by buzzingrobot on 2014-10-31
> **lucy3 said:**
> 
Should I install anything else or am I fine with just the firewall, assuming I'm sensible and don't go into root without exiting?!

Thanks everyone.

I don't see a reason to install anything else.  

My example of "sudo -i" was just to illustrate how the prompt will change when the current user changes. Stick with the standard Ubuntu precaution to avoid running as the root user.

---

### Post by lucy3 on 2014-10-31
Will do thanks. Buzzingrobot. Marked as solved.

---

### Post by whitesmith on 2014-10-31
For future reference, one-question-per-post is a good rule to follow, here and everywhere. By bouncing between security and the unrelated hostname issue, you introduce a small amount of stochastic data into our minds. That, times 100,000 pieces of unrelated entropy, and we (burnouts) get headaches. I am not criticizing, just offering friendly help to a low-seed poster. I +1 **@buzzingrobot** for his advice. I would add this: get yourself a really good hosts file. Keeping junk out your computer is _much_ easier than allowing it in and then driving it out. (Vampires, you doubtless recall, cannot enter your premises without permission!)

My hosts file is published widely on the 'net, so it's aged-in-the-book and as safe as suchlike comes. Use it if you like. It lives in /etc under its own name (/etc/hosts). Since you have no privileges there, you'll need good 'ol sudo:```
sudo cp hosts /etc/hosts
```My own file is attached. Oh, be sure to change my hostname (2nd active line) to yours, which is the only change you'll need! I hope this has helped and wish you the best of luck.

---

### Post by Camilia on 2015-03-02
> **rsgangr said:**
> I use Lightweight Portable Security (LPS-Public Deluxe version), a thin Linux operating system that boots from a CD or USB stick.
How and where do I get this?

---

