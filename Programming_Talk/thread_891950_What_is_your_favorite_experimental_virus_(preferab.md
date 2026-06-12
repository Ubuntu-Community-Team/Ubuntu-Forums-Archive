---
title: "What is your favorite experimental virus? (preferably that your wrote)"
date: 2008-08-16
forum: Programming Talk
---

### Post by Achetar on 2008-08-16
What is your favorite experimental computer virus that you wrote? I am not talking about malicious stuff here. I am talking about experiments to see if there are ways an autonomous computer program can spread itself even with security measures in place.

I have written a couple. The simplest is copying itself over and over into the same directory.

---

### Post by dwhitney67 on 2008-08-16
I didn't write it, but once I used M$ Windows.

---

### Post by bobbocanfly on 2008-08-16
I wrote a worm that exploited a hole in a server I wrote then I was about 12. The vuln basically gave you root access to run commands on a machine. (Dont worry, the server was useless (cowsay over IP :D) and I never distributed it)

It was pretty much just a bash script that looked for the vulnerable server, then downloaded the worm script from a webserver and executed it. Would have been better if it copied itself onto the server, but that would make the thing *alot* more complex and it was just a quick proof of concept.

---

### Post by Torajima on 2008-08-16
I wrote a funny trojan for the Mac using Applescript. 

When launched:
A dialog box opens, and says "Hey Meathead! Are you sure you want to delete your hard drive?"

If you press 'cancel', it sets your volume to max, and using the Mac's built in speech capability, it screams "You stupid *#@%, I'm going to delete your hard drive, and there ain't nothing you can do about it!"

Of course, that's all it does. I was going to put it on a co-workers machine for an April Fool's joke, but I just didn't have the heart to do it...

---

### Post by Achetar on 2008-08-21
Nice!

I wrote a Windows virus once that adds itself to the Outlook Outbox and then messes up the WINDOWS directory.

I never released it. Thank God I don't use Outlook (Thunderbird all the way).

Oh and I wrote a program that could gain root priveleges without the password. But that is still open, so no posting it here. *cough*passwd*cough*

---

### Post by LaRoza on 2008-08-21
I never wrote a true virus, but I have written things that...mess with people.

Interestingly, they were all in VBScript or Batch on Windows...

A few of my favourites were the server drive bombs (a batch file which would "delete" everything if clicked, instructors couldn't resist clicking that weird file in my personal folder on the drive with all the students' assignments with which they had read/write permissions for every student. Searching for all .doc files (in Word class) and changing their attribute to "hidden", then deleting itself is what it did.) and the dialogs (VBScript) that you couldn't quit but made it look like if you did anything the hard drive would be erased (the average Windows user doesn't know what "wscript.exe" is in the Task Manager...)

---

### Post by mssever on 2008-08-21
> **LaRoza said:**
> a batch file which would "delete" everything if clicked, instructors couldn't resist clicking that weird file in my personal folder on the drive with all the students' assignments with which they had read/write permissions for every student. Searching for all .doc files (in Word class) and changing their attribute to "hidden", then deleting itself is what it did.Awesome. How did your instructor respond? (That wouldn't have worked on my machines, because I always configure Windows to display hidden files. Of course, I might have wondered why all those icons suddenly dimmed.)

---

### Post by LaRoza on 2008-08-21
> **mssever said:**
> Awesome. How did your instructor respond? (That wouldn't have worked on my machines, because I always configure Windows to display hidden files. Of course, I might have wondered why all those icons suddenly dimmed.)

I do the same (show extensions, show hidden), but the instructor didn't (and most people don't).

He thought it was funny as hell. (After all, it wasn't his grades)

---

### Post by loell on 2008-08-21
during college days, i only got to write one with vbscript, searches for shares, and hoses MSoffice.

---

### Post by rikxik on 2008-08-22
Well I don't consider it a virus - I exploited a writable directory in $PATH by putting a fake "su" - the program did "su: sorry", mailed the password to me and deleted itself so the re-try succeeded and user didn't even know that root was compromised. Ran it once and told the password to the guy who had root custody - the expression on his face was very nice :)

---

### Post by Xealot on 2008-08-22
Never written any self replicating viruses, but I have written a couple of trojans for experimental purposes, though none released.

My favourite "fun" program was something I wrote quickly one evening to annoy my brother. It was very simple, it would just switch capslock on and off for each keypress he pressed :)

It was fun when he told me he had a virus and showed me his TyPiNg.

---

### Post by Tony Flury on 2008-08-22
I once wrote a script that would emulate a "DELETE *.*" command on DEC VMS, including suitable delays for big files, and the normal output, cataloguing each file as it was deleted. It then "hid" the directory, by overidding the DIR command so that his local directory showed as empty - by virtue of a little flag file.

I was then able to insert the whole thing into a colleagues Home login script (in order to highlight how lax the default security settings where on our development system - I had no special priveleges).

he had the shock of his life when he next logged on and saw his entire home folder - including a lot of un-archived source code changes, all being deleted. I came to the rescue with the recovery script - which miraculosly recovered his files (by deleting the flag file) - but had a suitable laborious output as it "recovered" each file in turn.

---

### Post by kpatz on 2008-08-22
I've written one experimental virus, and one trojan, both around 13 years ago.

In 1995-96, when MS Word macro viruses first started to appear, I had read about the Concept virus, and I thought, I could do that. ;)  So I wrote one that was directed at a company I did consulting work for at the time (I hated the place).  One of the things it would do was, anytime you printed a document, it would search for the name of a particularly annoying VP and insert "A-hole" in between his first and last names, let the document print, then remove the alteration afterward.  I never released it, it was more of a programming exercise and frustration release for me.

Now on to the trojan.  This was around 1995 as well.  I was doing work on an Unix system at the same company as above.  I wrote a little program that simply executed a shell, and then embedded some code into a script that (when run as root) would install that program into a directory in the path and give it SUID root privileges.  I gave it an obscure Unix-command-looking name so it wouldn't be obvious to someone viewing the directory it was installed in, and "touched" the date stamp to match the dates of the other files in the directory, to make it appear legitimate.  I then gave the script to the sys admin of the box (it was a script that did legitimate stuff as well) and had him run it.  Once the program was installed, I could run it to get a root shell, and then I edited the script to remove the code that installed it.  I only used it to explore parts of the system I didn't have access to from my normal account, and I wouldn't spend much time in there (didn't want to get in trouble).  Oh yeah, the program also checked the UID it was run from, so it wouldn't exec the root shell if it wasn't run from my UID, that way if someone else ran it, it did nothing.

---

### Post by mssever on 2008-08-22
Since I've learned how to program, I've generally had too many useful things to do to write any kind of prank/experimental virus/trojan. But I have taken advantage of security holes occasionally to teach a lesson.

When I was in college, I was in a friend's dorm room and we were browsing the SMB network, looking for any information on someone who had managed to change his IP to mine and do banned things in my name. There was one machine on the network with a name that we didn't recognize. So, I tried going to \\machinename\c$ and found myself with full priviledges on his entire machine. I decided to put a text file on the guy's desktop explaning the need for more security, and listing several things I could have done had I wanted to.

Another time, I was in my school's computer lab and discovered that someone had installed AOL on the machine. What's more, they had saved their password to avoid getting promped for it. So, I logged on to their account and send them an e-mail from themselves advising them to change their password and pointing out what a foolish thing they'd done and the potential consequenses of the wrong person getting their password (at the time, you could shop on AOL and AOL would simply charde the credit card they already had on file). I should have changed their password for them and locked them out until they called AOL customer service.

---

### Post by drubin on 2008-08-22
Put a batchscript in the start up reg of my schools computers that.
Opened Sol.exe, and then opened itself.  (Recursion)

You would be amazed at how many of those dam sol.exe applications can run before crashing windows...

---

### Post by snova on 2008-08-22
I once tried writing a few viruses.

The first one just created a bunch of files on a floppy drive. I never could get it to work.

The second one I rewrote at least 5 times. I called it rabbit- it ran itself in an infinite loop with system(). The idea was to make the system run out of memory. I didn't know that system() waited until the program finished, though.

I ran it on another computer, but I don't think I managed to crash it. I gave up waiting for it, but I saw quite a number of MS-DOS boxes pop up before I did.

When I took the computer I wrote it on to a PC store much later (Windows was broken, and wouldn't stay running for longer than a few seconds- I needed them to backup my stuff) somebody there ran "tree" (I forget how). He pointed out the virus/ directory to me. When I told him, "Oh, I made that", he said something to the effect of "I used to write viruses, now I have to remove them".

I could never understand why my programs were over 400 KB. A virus should be small! No matter how I reduced the code though, it didn't seem to help. Now I know libstdc++ was being staticly linked. I also know how to write an ELF header from scratch and make system calls...

My cousin once asked me to write something for him, and I did. I made three:

[LIST=1]
[*]Printed '\a' infinitely. When I tried this on my computer, I couldn't stop it. I had to reboot.
[*]Copied itself to several system directories. I forget what it did there.
[*]Don't remember.
[/LIST]
I never heard what the results were.

And I'm one of those people that enables extensions, hidden files, system files, and everything else on Windows XP. I think it bugs my mom a bit, but I don't like it when programs try to hide from me. Maybe that's why I like Linux- though I detest having several dozen dotfiles lying around.

The title of this thread contains "preferably that you wrote", but my favorite real-life virus is Slammer (though technically a worm, and not experimental at all).

Very amusing stories, by the way. How do you do the caps lock thing? I never did learn to program for Windows.

---

### Post by loganwm on 2008-08-22
I wrote up a prog that copies a 1 Meg file thousands of times on a disk until it fills up all named "I am a Monument to All Your Sins.filenumber"

Oh it freaked someone out.

---

### Post by jimi_hendrix on 2008-08-22
never figured out how to have something multiply

---

### Post by jimi_hendrix on 2008-08-22
> **Achetar said:**
> Nice!

I wrote a Windows virus once that adds itself to the Outlook Outbox and then messes up the WINDOWS directory.


that reminds me...my dad when he first signed up for MSN messenger (yes he uses windows :() he got a very popular bug where every time he opens outlook he gest a little thing that says something about him having to verify his email...no one on google knows how to fix the bug and hes had it for 3 or 4 years

---

### Post by drubin on 2008-08-22
> **jimi_hendrix said:**
> that reminds me...my dad when he first signed up for MSN messenger (yes he uses windows :() he got a very popular bug where every time he opens outlook he gest a little thing that says something about him having to verify his email...no one on google knows how to fix the bug and hes had it for 3 or 4 years

It is a relatively common bug. It is in actual fact a virus written by a group of highly paid individuals. The virus started out as an upgrade to a pre-existing application. It grew into the current version that is out there plaguing our computer systems.

---

### Post by jimi_hendrix on 2008-08-23
well in windows all you have to do is edit autoexe.bat and you can make a lot of non lethal viruses involving popup boxes and programs running that they dont want on start up

---

### Post by jimi_hendrix on 2008-08-23
> **snova said:**
> I once tried writing a few viruses.
When I took the computer I wrote it on to a PC store much later (Windows was broken, and wouldn't stay running for longer than a few seconds- I needed them to backup my stuff) somebody there ran "tree" (I forget how). He pointed out the virus/ directory to me. When I told him, "Oh, I made that", he said something to the effect of "I used to write viruses, now I have to remove them".


what was the guys reaction that you told that too?

---

### Post by Achetar on 2008-09-04
Nice stuff. I wrote another [trojan] the other day. It would download bittorrent files (for real) and then in the background seed every torrent file on PirateBay. Not really nasty, but useful. I didn't actually release it. It eats up way too much bandwidth seeding to go unnoticed. But if I added code that would spread itself using bittorrent (seeding a file and adding itself to the end) then it would have been a new golden age of BT

---

