---
title: "for the newbie windows 2 linux converts/paranoid joes..."
date: 2009-04-06
forum: Recurring Discussions
---

### Post by krakk2k on 2009-04-06
heres probably the best and easiest antivirus for ubuntu/linux:

32bit - [http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run](http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.i586.deb.run)

64bit - [http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run](http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/BitDefender-Antivirus-Scanner-7.6-4.linux-gcc4x.amd64.deb.run)

request a free key here:

[http://www.bitdefender.com/site/Products/ScannerLicense/](http://www.bitdefender.com/site/Products/ScannerLicense/)

and relax =}

---

### Post by cardinals_fan on 2009-04-06
How does that offer protection?

---

### Post by krakk2k on 2009-04-06
> **cardinals_fan said:**
> How does that offer protection?

because it kills any of the very few linux viruses that exist maybe?

---

### Post by cardinals_fan on 2009-04-06
> **krakk2k said:**
> because it kills any of the very few linux viruses that exist maybe?
Signatures-based antivirus apps provide nothing more than a false sense of security.  They depend on instantly-outdated definitions and menial scans of every file.

You could argue in favor of heuristics-based antivirus apps, but even these are trivial when compared to cautious behavior and a limited account.

---

### Post by swoll1980 on 2009-04-06
I believe the Linux anti virus programs only look for Windows viruses.

---

### Post by krakk2k on 2009-04-06
> **cardinals_fan said:**
> Signatures-based antivirus apps provide nothing more than a false sense of security.  They depend on instantly-outdated definitions and menial scans of every file.

You could argue in favor of heuristics-based antivirus apps, but even these are trivial when compared to cautious behavior and a limited account.

instantly outdated dosent really apply to linux so much, but yeah the user is the best defence.

---

### Post by krakk2k on 2009-04-06
> **swoll1980 said:**
> I believe the Linux anti virus programs only look for Windows viruses.

no it nukes linux worMs etc...

typo - meant worms not works /doh.

---

### Post by cardinals_fan on 2009-04-06
> **krakk2k said:**
> instantly outdated dosent really apply to linux so much, but yeah the user is the best defence.
It still applies.  If I were to write some Linux malware right now (not hard if I utilize social engineering), your scanner would do nothing to protect you.

---

### Post by swoll1980 on 2009-04-06
> **krakk2k said:**
> no it nukes linux worms etc...

Cool. Learn something new everyday.

---

### Post by krakk2k on 2009-04-06
> **cardinals_fan said:**
> It still applies.  If I were to write some Linux malware right now (not hard if I utilize social engineering), your scanner would do nothing to protect you.

yeah but im intelligent enough to resist your evilness =P

---

### Post by lisati on 2009-04-06
Opinions in these forums seem to vary about the necessity of having antivirus with Ubuntu. As previously mentioned by cardinals_fan, caution and limited account can be useful in preventing trouble.

I'd include taking care with anything you might send or receive from Windows machines, regardless of how likely (or otherwise) the chance any stowaways causing mischief on your Ubuntu system.

---

### Post by FuturePilot on 2009-04-06
> **cardinals_fan said:**
> Signatures-based antivirus apps provide nothing more than a false sense of security.  They depend on instantly-outdated definitions and menial scans of every file.

You could argue in favor of heuristics-based antivirus apps, but even these are trivial when compared to cautious behavior and a limited account.

Indeed. Signature based antivirus apps really are not that great. Apparmor or SElinux are a much much better solution. Take a look [here]("http://www.friedcpu.net/?p=70")

---

### Post by krakk2k on 2009-04-06
> **lisati said:**
> Opinions in these forums seem to vary about the necessity of having antivirus with Ubuntu. As previously mentioned by cardinals_fan, caution and limited account can be useful in preventing trouble.

I'd include taking care with anything you might send or receive from Windows machines, regardless of how likely (or otherwise) the chance any stowaways causing mischief on your Ubuntu system.

true, but i only posted that because it dosent hurt to cover all your bases.

---

### Post by lisati on 2009-04-06
> **krakk2k said:**
> true, but i only posted that because it dosent hurt to cover all your bases.

I agree.
Unfortunately, I have yet to discover any package that can completely protect me from my own stupidity. ***_Polite_*** suggestions are welcome!

---

### Post by cardinals_fan on 2009-04-06
> **krakk2k said:**
> yeah but im intelligent enough to resist your evilness =P
*evil cackle*

Seriously, I think that your mindset is what matters most.  If you actually like wasting your resources scanning files, knock yourself out.  The problem is inexperienced users who want some magic solution that will just make them secure and assume that antivirus software does that.  I proudly endorse RESPONSIBILITY.  Accepting the fact that everything that happens on your computer stems from your actions and choices is the first step to security.

---

### Post by toupeiro on 2009-04-07
There's actually another factor to consider.  With entities such as CIFS/Samba, FTP, or something like ntfs-3g, that can pass transparently between Linux and Windows filesystems, nothing stops linux from *storing* a virus that infects windows peers on a network.  The scary thing about this is, a linux virus scanner will likely not detect an unactivated windows virus, and a windows virus scanner may not have the necessary rights to properly clean an active virus on non-windows managed network filesystems.  Windows and Linux are no longer as silo'ed as they once were.  Maybe linux isn't the likely target for viruses, but that doesn't mean linux should dismiss due-diligence in protecting systems from being infected by viruses.

---

### Post by macogw on 2009-04-07
> **cardinals_fan said:**
> Signatures-based antivirus apps provide nothing more than a false sense of security.  They depend on instantly-outdated definitions and menial scans of every file.

You could argue in favor of heuristics-based antivirus apps, but even these are trivial when compared to cautious behavior and a limited account.

And heck, if you just want to check that none of your binaries or config files have been modified, that's why we have debsums.

---

### Post by gn2 on 2009-04-07
> **toupeiro said:**
> Maybe linux isn't the likely target for viruses, but that doesn't mean linux should dismiss due-diligence in protecting systems from being infected by viruses.

I take the view that it's up to users of Windows PCs and servers to protect them from viruses.
It certainly isn't the responsibility of the Linux community.

---

### Post by macogw on 2009-04-07
> **gn2 said:**
> I take the view that it's up to users of Windows PCs and servers to protect them from viruses.
It certainly isn't the responsibility of the Linux community.

That doesn't make it responsible of you to distribute malware to your friends, though, now does it?

---

### Post by toupeiro on 2009-04-07
> **gn2 said:**
> I take the view that it's up to users of Windows PCs and servers to protect them from viruses.
It certainly isn't the responsibility of the Linux community.

Then you've completely missed the point I was trying to make.

1) I never said its the responsibility of "The Linux Community" to protect windows PC's and Servers from viruses.  What I said is that Windows Viruses can be transparently stored on Linux based filesystems, and thwart the efforts of Windows administrators to protect their systems based on their method of attachment and underlying security model in place.  If every linux admin took your position in a situation like this, they'd likely be the ones explaining to their supervisors why their systems keep getting reinfected, and how well do you think that message would sell linux as a "secure" alternative to upper supervisory types?

2) If you take the view that any community of people is not influenced by things outside their immediate sphere of impact, you're missing quite a bit of what "community" means.  Or, do you believe there is no reason to ever port a great Linux application to windows and vice versa?!

You can't have your cake and eat it too.  At least, not if you consider yourself a participating part of "the linux community" in my opinion.

My point here is, there is still validity to virus scanners running on linux, even if they were to be designed to prevent the spread of a virus to non-linux systems, since network filesystems are becoming more and more transparent.  Guess what?  The I/O of SMB 2.0 is on par with NFS, which means when you combine CIFS with SMB 2.0 for windows clients, and NFS for linux clients, and share the exact same NAS storage device for two different OSes simultaneously.  If you understand how CIFS works, and don't see the potential risk for seeding a windows virus that perhaps only a linux admin could address, I'm not sure how to better explain it to you but I'll try:

Typical CIFS environment
**NAS or Linux/UNIX Host:***/volume/exported_directory*   UID:root GID:Unix_Users rwxrwxr-x

**Bob the admin on windows Client**:  *ID doesn't match ID in Unix_Users and no ID redirection rule is specified*, _read only permission granted.._

Bob scans file in exported_directory.  Bob cannot delete file.  Call 1.800.LINUX-ADMIN :-D

Community is more than just about taking care of your own, your neighbors count too.

---

### Post by macogw on 2009-04-07
> **toupeiro said:**
> \
2) If you take the view that any community of people is not influenced by things outside their immediate sphere of impact, you're missing quite a bit of what "community" means.  Or, do you believe there is no reason to ever port a great Linux application to windows and vice versa?!

Spam!  Clean up the Windows machines, and you get less spam!

Though, I am saddened by really nice apps that are ported from Linux to Windows.  That just makes it easier to stay in The Land Without Freedom even longer :(

---

### Post by toupeiro on 2009-04-07
> **macogw said:**
> Spam!  Clean up the Windows machines, and you get less spam!


ok, you lost me??? ;)  can you translate this with regard to my post for someone who is up way too late tonight?

With regard to the other part of your post, I must be missing something..  Do the apps suddenly become non-FOSS because they were compiled on Windows?? (of course, I know they don't)  I guess I don't believe that just because your OS is proprietary that there is no place for FOSS.  Freemind, for example, is a super-powerful mindmapping tool that is open source and cross-platform, and used cross-platform where I work for valid cases in both environments respectively.  Why *shouldn't* this happen??

---

### Post by macogw on 2009-04-07
> **toupeiro said:**
> ok, you lost me??? ;)  can you translate this with regard to my post for someone who is up way too late tonight?

Spam comes from machines that have had their security compromised and are being used by an attacker to send the spam.  Guess what OS they usually run?  So, if you clean up all the malware and install all the updates on every Windows computer you come across, what's the net effect?  Fewer compromised machines doing stupid things to your mail server.
> 
With regard to the other part of your post, I must be missing something..  Do the apps suddenly become non-FOSS because they were compiled on Windows?? (of course, I know they don't)  I guess I don't believe that just because your OS is proprietary that there is no place for FOSS.  Freemind, for example, is a super-powerful mindmapping tool that is open source and cross-platform, and used cross-platform where I work for valid cases in both environments respectively.  Why *shouldn't* this happen??
Ever heard the term "killer app"?  If all the good apps are available on Windows too, what incentive does anyone have to switch to Linux?  I was the really good apps to stay on Linux.  Then people go "wow, I really want that, but it's only on Linux.  I guess I'll have to try Linux."

---

### Post by inobe on 2009-04-07
virus removal applications

viruses


hmmm one must be really paranoid to assume the vendors create the viruses their applications remove, or would they really be paranoid :-k

---

### Post by gn2 on 2009-04-07
> **macogw said:**
> That doesn't make it responsible of you to distribute malware to your friends, though, now does it?

Not really.
If they choose to run a defective system, that's their look-out, not mine.

---

### Post by bapoumba on 2009-04-07
Welcome to the recurring discussions.

---

### Post by toupeiro on 2009-04-07
> **macogw said:**
> Spam comes from machines that have had their security compromised and are being used by an attacker to send the spam.  Guess what OS they usually run?  So, if you clean up all the malware and install all the updates on every Windows computer you come across, what's the net effect?  Fewer compromised machines doing stupid things to your mail server.

Ever heard the term "killer app"?  If all the good apps are available on Windows too, what incentive does anyone have to switch to Linux?  I was the really good apps to stay on Linux.  Then people go "wow, I really want that, but it's only on Linux.  I guess I'll have to try Linux."

Maybe I am the exception to the rule, but it was not one application alone that made me switch to Linux, but linux itself, and all that it encompasses.  Your definition of "Killer App" sounds too proprietary to fit the rest of the message linux and FOSS tries to send, and I don't see how its any different than what Microsoft does with things like Office aside from it being "for profit." So, one could say, by trying to follow Microsoft development model with free software, it really makes the developers of free programs no better than Microsoft developers writing proprietary apps.  If thats what killer app means, then I'm not on board.

---

