---
title: "Recover E-mail"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by Crawdog on 2012-10-26
I had my Windows Vista PC converted to Linux Ubuntu at my repairman's suggestion after experiencing countless crashes.  Now, while on the Internet I had another crash (with Linux) and my e-mail is no longer available. Clicking onto the Email logo opens up an 'Evolution Setup Assistant' window.  Following the prompts opens a 'Restore From Backup' checkbox.  Checking this box brings the prompt "Please select an Evolution Archive to restore" with a dropdown which has 21 folders and 3 files.  I've opened each one and there is no reference to e-mails.

Any help in recovering the e-mail function would be appreciated.

---

### Post by Gone fishing on 2012-10-26
This is a little hard through lack of detail.

Its hard to know what you mean by Internet crash, however. If you still have your Windows personal files such as your mail file it should be possible. If in Windows you used Thundirbird as a mail client then it would be easy just to install Thunderbird in Ubuntu and and past the old mail file into the profile in Ubuntu.

> On Windows XP this folder is in ...\Documents and Settings\%username%\Application Data\Thunderbird\Profiles\zzzz.default. On Ubuntu, the profile, as expected, is in $HOME/.mozilla-thunderbird\xyxyx.default (zzzz and xyxy are random names).  Just copy the "XP" profile to $HOME/.mozilla-thunderbird/ on the Ubuntu system, rename it or set the correct folder name in $HOME/.mozilla-thunderbird/profiles.ini, and start Thunderbird. Et voila, your Thunderbird in Ubuntu looks and behaves exactly as it did on Windows XP, and all your mail messages are still there. [http://users.telenet.be/mydotcom/howto/linux/migration01.htm](http://users.telenet.be/mydotcom/howto/linux/migration01.htm)

If you used Outlook outlook espress its still possible [http://www.wikihow.com/Migrate-from-Windows-to-Ubuntu](http://www.wikihow.com/Migrate-from-Windows-to-Ubuntu)

However, I suggest that you go and see the repairman and get him to finish the job, If this is not possible before you can be really helped we need to know:

* What was your mail client in Windows.
*  Where the old Windows back up files are (I'm hoping the answer is is on a Windows partition)

---

### Post by Bucky Ball on 2012-10-26
Sounds like you have an older release as Thunderbird is now the default email client. Did you install Evolution yourself or was that the default?

---

### Post by Crawdog on 2012-10-26
Gone Fishing and Bucky Ball,

I am in the "Absolute Beginners" for a reason.  I don't even understand your questions of me, but I'll try.

Internet Crash = I was online when the monitor went black.  On reboot I renewed the last session and everything came back except I could not access my e-mail (as I described).

You ask about "Windows" and "Outlook".  Are these not Microsoft programs (I don't know what Thunderbird is)?  Why would Microsoft be relative to Linux/Ubuntu?  I had MS Vista before the changeover but I don't understand their relationship to my current issue.

I am not being combative; I'm just not sure how to help you help me.  And if I could find the little worm who talked me into this I would have him do it.  However, he is not to be found, along with my other computer that he was going to have back to me "tomorrow".  This was in March.  If I need to bring it in to a shop, then please advise that also.

---

### Post by newb85 on 2012-10-26
First of all, Welcome to the forums!

Secondly, take a deep breath and relax.  Your problem can probably be solved here.

I think Gone fishing misunderstood your situation.  You are only trying to recover the emails and settings you had on Ubuntu.  Is that correct?

Here's a little background for you.  The person who set you up with Ubuntu probably should have explained this to you.

Every six months, Ubuntu comes out with a new "release", or version.  Releases are numbered by the scheme yy.mm.  For example, I'm running 12.04, which was released this past April.  Releases are also given alliterative adjective-animal names.  For example, 12.04 is named Precise Pangolin.  The initials for each successive release increment by one.  11.10 Oneiric Ocelot was the release before 12.04.

Evolution and Thunderbird are two different email programs available on Ubuntu.  Both are excellent programs.  Prior to 11.10, Evolution was the default.  Since 11.10, Thunderbird has been.  Either one is fine to use regardless of your release.

It will be easier for us to help you if we know what release you're running.

Open a terminal by hitting Alt+F2 and typing "gnome-terminal" (without the quotes).  Copy and paste the following command and hit enter.
```
cat /etc/issue
```

---

### Post by Gone fishing on 2012-10-27
> Internet Crash = I was online when the monitor went black. On reboot I renewed the last session and everything came back except I could not access my e-mail (as I described).

You ask about "Windows" and "Outlook". Are these not Microsoft programs (I don't know what Thunderbird is)? Why would Microsoft be relative to Linux/Ubuntu? I had MS Vista before the changeover but I don't understand their relationship to my current issue.

Sorry if I've missunderstood I assumed that the Windows move was very recent and that was where your mail was. However, as that is not the case how did you access your mail? If on Ubuntu, the most likely options are Thunderbird, Evolution or some webmail system. As you are saying that you couldn't get the mail after an Internet crash were you using some webmail system that you can't get to now? What is your mail adress (I don't want the full address) [email]user@whetever.com[/email]

---

### Post by Crawdog on 2012-10-29
Gone Fishing:

"However, as that is not the case how did you access your mail?"

I opened the e-mail program by clicking onto the 'envelope' logo in the upper right-hand corner of the screen (where the shut-off and calendar programs are).  This opened the Evolution e-mail program.

newb85:

OK, I did this as instructed.  This opened a window with: (my name) @(my name); (my Computer ID #)"-07~$ cat/etc/issue."  Under this is "Ubuntu 11.04\n\(some digit I can't decipher - looks like a backwards J with the top horizontal strike only on the left side.  What am I to do with this?

Again, please forgive me.  After years of MS (XP Pro & Vista) I was a chimp at best.  With the Linux / Umbuntu I am like a chimp with not enough oxygen to the brain.  All help is appreciated.

---

### Post by newb85 on 2012-10-29
You should have copied and pasted the output into the post, surrounded by code tags, like this:

[noparse]```
Pasted Output
Here
```[/noparse]

That character you couldn't decipher is a lowercase "L".

That output tells us you have Ubuntu 11.04 (Natty Narwhal) installed.

---

### Post by newb85 on 2012-10-29
Okay, Crawdog, I'd like to check a few things.

Please open a terminal (Ctrl+Alt+T would be quicker than the method I told you earlier) and run the following.

```
ls .local/share/evolution/mail
```

Copy the output and paste it into another post surrounded by code tags.

---

### Post by Bucky Ball on 2012-10-30
@ Crawdog: A heads up; for your own benefit, I have removed your personal email address from post #7. Please refrain from posting personal details on the forums for your own security.

*Anyone* can see any post on the forums. Being a member of the forums guarantees nothing as *anyone* can become a member easily and trawl for posted email addresses. ;)

---

### Post by newb85 on 2012-10-30
> **Bucky Ball said:**
> @ Crawdog: A heads up; for your own benefit, I have removed your personal email address from post #7. Please refrain from posting personal details on the forums for your own security.

*Anyone* can see any post on the forums. Being a member of the forums guarantees nothing as *anyone* can become a member easily and trawl for posted email addresses. ;)

Er...that wasn't Crawdog's actual address.  Per Gone fishing's directions in the previous post, Crawdog used the fake user name *user*.  The point was to let us know the domain part of the address.

---

### Post by Bartender on 2012-10-30
A couple of suggestions/guesses, although these don't help with your immediate email problem.

It seems to me that your "repair guy" sent you off in the wrong direction if the PC is continuing to crash just like it did before with Windows.  This indicates a hardware problem, not something that would be fixed with different software.

How old is the PC?

It kinda sounds like you're describing the PC shutting itself off??  If so, first guess would be that the CPU heatsink is not doing its job anymore and the CPU is shutting itself down.  This is not at all uncommon, especially as the years go by.  Two things happen.  Well, at least two.  Dust builds up on the CPU heatsink, and the thermal paste loses its original plasticity.

The CPU heats up, then shuts itself off.  This can happen within a minute or two of turning on the PC, or quite a while later.  The problem might only pop up when you ask the computer to do something CPU-intensive.

---

### Post by Bucky Ball on 2012-10-30
> **newb85 said:**
> Crawdog used the fake user name *user*.  The point was to let us know the domain part of the address.

Message received and understood.

---

