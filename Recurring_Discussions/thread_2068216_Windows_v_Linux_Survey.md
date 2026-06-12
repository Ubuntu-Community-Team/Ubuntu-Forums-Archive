---
title: "Windows v Linux Survey"
date: 2012-10-08
forum: Recurring Discussions
---

### Post by 0N3 on 2012-10-08
My college has asked me to make up a Linux Questionnaire. I was wondering if i could get some help here on what sort of questions to ask. Basically im doing a project on comparison of the Windows Operating System and the Linux Operating System. Detailing its usability the benefits of using either the negatives im also posting on a windows forum to get there thoughts and reactions to this survey. Thanks very much in advance and would appreciate any input on the situation no matter how big or small.

---

### Post by daslinkard on 2012-10-08
> **0N3 said:**
> My college has asked me to make up a Linux Questionnaire. I was wondering if i could get some help here on what sort of questions to ask. Basically im doing a project on comparison of the Windows Operating System and the Linux Operating System. Detailing its usability the benefits of using either the negatives im also posting on a windows forum to get there thoughts and reactions to this survey. Thanks very much in advance and would appreciate any input on the situation no matter how big or small.
Here is a [link]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CCgQFjAB&url=http%3A%2F%2Fzach.in.tu-clausthal.de%2Fteaching%2Fwerkzeuge_literatur%2FLinuxvWindows.pdf&ei=3ypzUOEDxubSAZT6gNgO&usg=AFQjCNGH6zzLlWlgOwkb310lgMfG94L3vA&sig2=IgAHA01WFEnZ3PTNkJBtqA") where a survey was done about Linux Vs Windows...personally I switched over from Windows to Linux after growing tired of dealing with BSOD, viruses, worrying about antivirus, continuous Windows Updates, etc.  The list could go on and on for the pro's of Linux versus Windows.

The day I dropped Windows for Linux is the same day that I sold all my stock in headache relief.

---

### Post by hal8000 on 2012-10-08
Windows NTFS filesystem Never The Flaming Same ??

NTFS is slow insecure and contains a single copy of the FAT.
By contrast linux file systems are more resilient, journalled containing
multiple copies of the superblock.

I've never lost any data on ext3, ext4 or resiser filesystems. Plenty of data on NTFS.

99% of all web servers are linux based. Its used on everything mission critical including NYSE, NASA, CERN, etc.


I cant think of anything that windows is better at, except crashing.
I've had a few X window crashes but nothing major and nothing that lost data. I moved to linux in 1999 and never looked back.

---

### Post by wyliecoyoteuk on 2012-10-08
The biggest advantage of Linux?

Choice.
Choice of desktop environment, choice of Distro, Choice of thousands of free applications, Choice of how you use the computer that you own.
I choose freedom. :)

---

### Post by 0N3 on 2012-10-08
I have been using Ubuntu since 8.04 and absolutely love it myself. Thanks for the input hopefully few more and I can document this :)

---

### Post by 0N3 on 2012-10-08
For the average user its hard to ask them Q's based on Linux no ideas where to start.

---

### Post by Peripheral Visionary on 2012-10-08
Linux is proven on servers and still largely experimental on the desktop. So I think some questions should be used to determine what the user wants to use his or her computer for.

For businesses who need servers, Linux (and Unix) is great and proven. For professionals who need specific software, the software may not be available for Linux. For big time heavy-duty gaming, sorry, Linux. Not yet, anyway.

For home users who just want to surf the net, do Facebook, e-mail, shop online, pay bills online, write letters, do school work and such, Linux has the advantage of being free (as in cost) and full of options to choose from for all those home uses. Big win for Linux at home for "ordinary use."

So the questions depend on what the user intends to use a computer for.  You might end up with separate questionnaires for home users, business users, professionals, and gamers.

---

### Post by 0N3 on 2012-10-08
Thank you for your replies much appreciated. Cant say same for windows forum got zero replies :(

---

### Post by newbie-user on 2012-10-08
> **0N3 said:**
> Thank you for your replies much appreciated. Cant say same for windows forum got zero replies :(

Probably because the vast majority of Windows users have no clue what Linux is. And that's going to be a huge problem right there. Linux users almost certainly have used Windows, but not the other way around.

Anyway, Peripheral Visionary had a good reply. That's pretty much what I would say. It all depends on what kind of user is answering the questionnaire.

---

### Post by sidzen on 2012-10-08
To spoon-feed the OP:

Do you or your organization use the GNU/Linux Operating System (hereafter, Linux)?
If so, why?

Have you or your organization switched from Windows to Linux?
If so, why?

Do you or your organization use both Windows and Linux Operating Systems (hereafter, OS)?
If so, why do you use both OS?

What are the major advantages and disadvantages of both OS, in your opinion?

---

### Post by mike acker on 2012-10-08
one day while ferreting thru various computer news i stumbled on this essay

[http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/](http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/)

it's a bit dated, -- yet still insightful

I would love to find a good Beginners' Introduction to  Linux architecture. Mainly because I want to learn more about what is meant by "running in userland"

when I first read the discussion I took "userland" as meaning RING1 or RING2 in the Intel x86 model (RING0 is kernel mode and RING3 is application )

If "userland" means RING3 then what we want to verify is that executable code loaded from a system library into "userland" is loaded onto EXEC only  pages -- so that an attacker cannot effect any "code injection" into a "trusted" program -- which might have special privileges...
e.g. see [http://www.ibm.com/developerworks/linux/library/l-linux-kernel/](http://www.ibm.com/developerworks/linux/library/l-linux-kernel/)

Based on my reading of Bill Blunden's Rootkit Arsenal -- 
[http://www.amazon.com/Rootkit-Arsenal-Escape-Evasion-Corners/dp/144962636X/ref=sr_1_1?s=books&ie=UTF8&qid=1345294140&sr=1-1&keywords=rootkit+arsenal](http://www.amazon.com/Rootkit-Arsenal-Escape-Evasion-Corners/dp/144962636X/ref=sr_1_1?s=books&ie=UTF8&qid=1345294140&sr=1-1&keywords=rootkit+arsenal)

-- Windows does not fully implement the storage protection model in x86, relying instead on the virtual memory support...... which would tend to explain why Windows needs ASLR DEP and such .   

I'm still a n00b here -- I hope chattering is OK in this "recurring discussions" section. maybe it's a section I should use more

---

