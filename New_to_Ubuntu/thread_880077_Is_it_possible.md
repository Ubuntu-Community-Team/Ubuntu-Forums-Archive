---
title: "Is it possible?"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by ChocolateChip_Wookie on 2008-08-04
I've just had a rather acrimonious discussion with someone.

I have aMSN running on the latest Linux. 

I have been kicked out of MSN (for good and always) it seems because I just cannot get back in. My husband reports that MSN on windows is fine. The person I was having the 'discussion' with has moderate computer skills and a bit torrent account or two. Is there some software of which I am unaware that will kill all MSN's remotely? I have tried re-installing and booting, but it sticks at trying to log in....?

Yes, I did type my user name and password correctly...

---

### Post by benfindlay on 2008-08-04
Do you mean that you can't access the MSN website, or that you can't log into AMSN using your MSN 'passport'?

It is very unlikely that you are being remotely blocked or hacked by some other user, especially not one who is not an administrator for MSN (the website OR messenger, depending on your situation)

It is more likely that AMSN is suffereing connection problems, perhaps due to firewall/proxy/other settings.

You should try using pidgin to connect to your MSN account, as it should be installed by default.

Hope this helps!

---

### Post by ChocolateChip_Wookie on 2008-08-04
Thanks very much. I've just logged in via Windows successfully so guess it must be aMSN having problems. No worries.

---

### Post by Vadi on 2008-08-04
Try [Pidgin]("apt:pidgin") or [Emesene]("apt:emesene")?

---

### Post by mc4100 on 2008-08-04
It's possible your 'acrimonious' discussion (well put, btw) is simply a coincidence, but just to be sure:
I believe an msn messenger account is tried to an email one, so, to eliminate the possibility that your account has been hacked (someone guessed the password, etc.,), try logging in to the mail service at

mail.live.com

If you can access that fine, then there is no problem with the account, per se. 
(There could be problem's with the MSN service)
but I suggest using another IM client with the same account, incase the problem lies with aMSN. (In which case something is configured wrongly)

Edit: too late, never mind.

---

### Post by motang on 2008-08-04
I would try Pidgin like benfindlay suggested. Or try [Meebo]("http://www.meebo.com") which is a web based instant messageing system.

---

### Post by Vadi on 2008-08-04
Meebo is powered by Pidgin afaik, so it would be the same.

---

### Post by ChocolateChip_Wookie on 2008-08-05
It's so wierd. I removed aMSN and then put it back with Synaptic and I am still getting the same problem 24 hours on. If I didnt know better I'd say that I had been nuked!

I am so foxed because this is Linux. This shouldnt even be possible..?

I can log in with MSN Windows, I can log in with Pidgin. I just cant use aMSN (at all it seems)

---

### Post by Achetar on 2008-08-05
It may be a bug in aMSN. Or Microsoft finding a way to detect if you are using aMSN and blocking all aMSN users because they want you to use Windows Messenger. I would go with Pidgin anyway, but if you prefer aMSN you could try their forums.

---

### Post by ChocolateChip_Wookie on 2008-08-05
> **Achetar said:**
> ..Or Microsoft finding a way to detect if you are using aMSN and blocking all aMSN users because they want you to use Windows Messenger.

What's the old saying? I'm not paranoid, they really are out to get me? Lol.

No. I had it working - last night. Right before the ...um...culmination of the aforsaid acrimonious discussion. Everything was fine. The reason I want it is because I want to video chat capabilities which (to my limited experience) Pidgin does not appear to have. (Yes, I have skype too but there are reasons prohibiting the other person from using it - namely, she cant get her head around it, I kid you not. I've only just dragged her kicking and screaming into the 21st century with MSN, I dont want to frighten her)

I have completely un-installed and I will reboot tonight and see if a re-install fixes the problem. If not, then I dont know what the hell is up.

---

### Post by gandaran on 2008-08-05
removing and reinstall won't fix your problem, the amsn configuration files will still be there in your home folder! best if you just look for the hidden home amsn folder and delete it and start amsn again with default settings.

---

### Post by ChocolateChip_Wookie on 2008-08-05
Oh thanks ;)

How do I do that? (sorry, I've only had Linux for a week, still working out the kinks)

---

### Post by gandaran on 2008-08-05
> **ChocolateChip_Wookie said:**
> Oh thanks ;)

How do I do that? (sorry, I've only had Linux for a week, still working out the kinks)

nautilus » view » show hidden files
I don't use amsn, but there must be a amsn folder somewhere in your hidden home directory.

---

### Post by ChocolateChip_Wookie on 2008-08-05
Found it. Good old 'search'. I still havnt got used to the file structure. I keep looking for a 'program files' directory and other common folders.

---

### Post by gandaran on 2008-08-05
have a look at this thread [http://ubuntuforums.org/showthread.php?t=880839](http://ubuntuforums.org/showthread.php?t=880839)
could be your amsn problem.

---

### Post by ChocolateChip_Wookie on 2008-08-05
Ah ha, interesting. Thanks. I'll try it.

---

