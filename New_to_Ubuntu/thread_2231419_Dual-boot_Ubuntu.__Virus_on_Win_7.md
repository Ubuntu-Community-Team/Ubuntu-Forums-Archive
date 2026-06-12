---
title: "Dual-boot Ubuntu.  Virus on Win 7"
date: 2014-06-25
forum: New to Ubuntu
---

### Post by Jane_Ralph on 2014-06-25
I was playing around with Gimp in Ubuntu, then I tried to get out of it and something crashed so my mouse no longer worked.  I did a hard re-boot and still no mouse.  (it came back after the computer was turned off overnight).  

In the meantime I went into the Windows half and tried to access some information using IE when suddenly I got a BSOD and a notice that I had a deadly virus and to call this toll-free number.  I immediately shut off the computer after writing down the number, but I'm a bit afraid to call it as it could be some kind of scam.  I have not gone into windows since then and honestly don't know what to do now.  This is a brand new Dell Inspiron with 1 TB hard drive which I partitioned roughly in half.  

I'm wondering if I should get rid of windows 7 completely but I have no idea how to do that either.  Any help would really be appreciated.

---

### Post by grahammechanical on 2014-06-25
See the official Microsoft response to this kind of thing. 

[COLOR=#333333][FONT=Segoe ui]Here are some of the organizations that cybercriminals claim to be from:[/FONT][/COLOR]
> 
[LIST]
[*][COLOR=#333333]Windows Helpdesk[/COLOR]

[*][COLOR=#333333]Windows Service Center[/COLOR]

[*][COLOR=#333333]Microsoft Tech Support[/COLOR]

[*][COLOR=#333333]Microsoft Support[/COLOR]

[*][COLOR=#333333]Windows Technical Department Support Group[/COLOR]

[*][COLOR=#333333]Microsoft Research and Development Team (Microsoft R & D Team)[/COLOR]
[/LIST]


> [COLOR=#333333][FONT=Segoe ui]There are some cases where Microsoft will work with your Internet service provider and call you to fix a malware-infected computer&#8212;such as during the recent cleanup effort begun in our [/FONT][/COLOR][botnet takedown actions]("http://www.microsoft.com/botnets")[COLOR=#333333][FONT=Segoe ui]. These calls will be made by someone with whom you can verify you already are a customer. You will never receive a legitimate call from Microsoft or our partners to charge you for computer fixes.[/FONT][/COLOR]

[http://www.microsoft.com/en-gb/security/online-privacy/avoid-phone-scams.aspx](http://www.microsoft.com/en-gb/security/online-privacy/avoid-phone-scams.aspx)

[http://www.microsoft.com/en-gb/security/online-privacy/msname.aspx](http://www.microsoft.com/en-gb/security/online-privacy/msname.aspx)

[http://support.microsoft.com/contactus/cu_sc_virsec_master?ws=support](http://support.microsoft.com/contactus/cu_sc_virsec_master?ws=support)

Regards.

---

### Post by Jane_Ralph on 2014-06-25
Thanks.

---

### Post by SuperFreak on 2014-06-25
This forum may be of help removing the malware from Windows [http://www.bleepingcomputer.com/forums/]("http://www.bleepingcomputer.com/forums/")

---

### Post by Jane_Ralph on 2014-06-25
Sounds interesting.  I have now used the M$ scanner, added Avast and scanned win 7 with that and it comes up clean.  I'd suspect the toll-free number might be for McAfee, which came partially bundled with it, but I can't find it on their website.  I'll play around on the bleeping site.  Thanks.

---

### Post by maglin2 on 2014-06-25
If you have avast I would recommend their forum. They have some very talented malware removal experts.

---

### Post by Jane_Ralph on 2014-06-25
You're right.  And last time I used them they were really helpful.  Even though I'm still on the free version.

---

### Post by DuckHook on 2014-06-25
Welcome to Ubuntu and the forums, Jane_Ralph.

The advice you've already received from other forum experts on virus removal is all excellent stuff. I would only add the following:

Did you create the W7 reinstall disks when you first got your computer? Do you have a recent backup of your critical data? If so, you might consider re-installing your whole W7 OS rather than take chances with an incomplete virus cleanup. It's been a long time since I've had to deal with Win malware, but I always ended up re-installing even when AV tools told me the virus had been removed. Once infected, I could never truly trust the old OS again.

If you take this step, be prepared to lose your Ubuntu install as well. W7 rescue disk does not recognize Linux and will overwrite the whole HDD to bring your computer back to its original state when purchased. Frankly, it doesn't hurt to completely repartition and reformat the HDD anyways to be sure that no residual malware remains.

This is admittedly a very paranoid take on things, so please take the nature of this advice into consideration when assessing my suggestion.

---

### Post by Jane_Ralph on 2014-06-25
Thanks, DH.  I think I will take a wait-and-see attitude before I go through that much pain again.  I am still new and relatively chicken when it comes to talking to the Terminal and messing with the BIOS.  I don't really plan on using the windows half that much anyway.  Of course, it could be that you're right...

---

### Post by Rob Sayer on 2014-06-26
Useful Windows security tip:  do not use Internet Explorer.  It's inherently unsafe because it is part of Windows Explorer and as such has permission levels no browser should have.

This is basically because Windows permission levels really stink.  In Linux they're much better.

*Any* windows browser is better than IE.

---

### Post by LastDino on 2014-06-26
I second [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"), this sounds like your usual scam. You mentioned McAfee partially bundled with W7? That opens door for whole another level of problems. What do you mean it came partially bundled with anyway? Does that mean it is  something like ''scan only'' thing? 

I've seen that stuff on my W7 and it installed itself with some thing other I tried to download and install from some very trustworthy sites. It allegedly scans your computer for viruses for free.  So, IMO, W7 itself might have not yet at the stage of throwing out, but it will do good if you cleaned it up. Preferably through recovery disks if you've them.

Also, please stop using IE. Its not just that it has permissions problems, it is biggest piece of problem source you can have on any OS. Windows OS itself might not be as bad as you may read when compared to Linux, but things you do on it may very much make it your worse nightmare.

---

### Post by Jane_Ralph on 2014-06-26
I've been using Firefox except for the Windows half of this computer because every website I tried to go to gave me an "Unknown certificate" error.  But I still haven't found any viruses.  I do plan to ask on the Avast forum when I get some time.  Thanks again.

---

### Post by collisionystm on 2014-06-26
Not sure if you have cleared the virus yet or not but I have seen this one many times. The .exe for this thing is most likely in C:\Users\<YourUserName>\AppData\Local\Temp. Just delete all contents of temp as the items in here are not important. There is another temp folder in C:\Windows\Temp. Clear those contents as well.

Reboot into Windows (should load now).

Before opening Internet Explorer, it is important to do 2 things.

1. Open Registry (regedit.exe) and Navigate to Hkey_Current_user, Software, Microsoft, Windows, Current version. Delete the subkey called 'Internet Settings'. This will remove any potential proxy placed into IE. 
2. Navigate to control panel, Internet Options, Advanced tab, Reset IE. Delete all personal settings (wont remove favorites).

The simplest solution I can provide now is to run Malware Bytes or Microsoft Safety scanner. [http://www.microsoft.com/security/scanner/en-us/default.aspx](http://www.microsoft.com/security/scanner/en-us/default.aspx)

Protect yourself in the future by using Firefox/Chrome with adblock plus installed. Use this with Microsoft Security essentials instead of McAffee or Norton as they do more harm than good.

I have attached a hosts file that contains 27,000 entries of known bad websites that will redirect to 127.0.0.1. This is optional, however I use it a lot on customers and it may help you.

---

