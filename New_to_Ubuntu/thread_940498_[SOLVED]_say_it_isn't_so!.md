---
title: "[SOLVED] say it isn't so!"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by MelissaEpiphany on 2008-10-07
OK, something very weird's been happening on my OS.

I think I got a virus through a bit of social engineering by an email a family member sent me. Stupid me assumed this family member had the sense, and the cents, to ensure good protection on their own PC. 

I noticed an email from aforesaid family member with link about a .. frog I think?? Nothing came up on screen but words. Have never had a problem before so opened, To my shock, I recently read online that there is a green frog jpg file that is actually a trojan. 

Before I get a plethora of responses saying it's not possible, I did scan with ClamAV and it came up with a virus. An email virus to be exact. I quarantined it but problems persisted. Afterwards I ran ClamAv again and Chkrootkit, both then said no infected files found.


Afterwards, when I clicked "send/receive" a number of emails would be supposedly coming into my account, expunging messages would occur like normal, but then no emails would actually arrive. More suspiciously than that, all emails that were sitting in my account to begin with - simply disappeared!

Surfing the web became fraught with my screen spontaneously moving up or down and I did find a whole bunch of WRL~ files in one of my documents which I have not ever seen since I used Windows and had a worm, which I thought was impossible in Linux.

I have actually rebooted my whole OS again and things were fine but Evolution is being a nuisance again! I tried to open it and change password, but do not know how, and my emails are doing the same thing again - opening verrryyy slowly then not coming through into inbox at all, despite send/receive saying there are 47 emails waiting for me.  

I know this is naive, but if someone had access to my email account details and passwords on my last OS, could they possibly be able to access Evolution anytime I opened it even if I had rebooted a new OS???

If so, what the hell do I do? If not, what the hell is going ON??
Can someone who puts a trojan in my email gain access to other compartments on Linux? Please say no!

I have not lost any files of folders from my home folder, all still there. 

ack, help !

Mel

---

### Post by Orange_and_Green on 2008-10-07
Dear MelissaEpiphany,

1) Don't panic.
2) Is your e-mail account POP3 or IMAP? If you are using IMAP (or you have a full message backup) you could try uninstalling evolution, deleting the .evolution directory in you home, then reinstall, reconfigure your account and see if the problem persists.
If, on the other hand, you have an un-backed up POP3 account, you could try a different client (like thunderbird) with either IMAP or POP3 keeping a copy of the messages on the server and make sure your mail is received normally.


I have yet to see a "cross-platform" trojan - so I believe the problem with the mail must be related to some error in the mail client configuration.

~wrl files are temporary files created by microsoft word, they normally get deleted unless word crashes. So those files most likely are either your own old temporary word files that you previously imported from windows onto Ubuntu, or maybe someone sent you a bunch of zipped documents and included the temp files too by mistake. To be 100% sure, you could try renaming the ~wrl files to .rtf and see if openoffice can open them.

> I know this is naive, but if someone had access to my email account details and passwords on my last OS, could they possibly be able to access Evolution anytime I opened it even if I had rebooted a new OS???
No, that kind of information is of no relevance for breaking into your computer LOCALLY (unless, obviously, the login and password for your OS are the same as the ones for your e-mail). What they could do if they have your login and password is read your mail and send e-mail in your name, and change the password locking you out of your own account, so if you suspect someone knows this kind of information, please contact your e-mail provider.

Good luck:KS keep us posted.

---

### Post by hyper_ch on 2008-10-07
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by MelissaEpiphany on 2008-10-07
Thank you so much Orange and Green.

Don't panic? Was too late for that! lol. 


WRL ~ files would come from where you say.

Passwords are different between OS and email. Am a little worried about the possibility that someone is getting my email though. Seem to be sending them alright though. I am using POP3 but have already thought of shifting to Thunderbird.

Will post if problems persist or if and when I solve my problem.

Thanks for your patience.

Hyper_Ch: thanks for the tip, will make specific and not obscure topic title from now on.

Cheers, Mel

---

### Post by billgoldberg on 2008-10-07
Mark the thread as solved please.

--

ps: don't worry the scanner found the virus.

Yes you have downloaded the virus onto you computer without you knowing it.

However it will just sit there like any other file. It will not be able to run it course and infect your pc.

Just delete the file(s) to make sure you don't pass it along.

--

---

