---
title: "Changing default OS with Grub2 version 1.99"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by oscarivera9 on 2011-09-13
I used to be able to change default start-up OS with prior versions of Grub2, but since Natty came out there have been a few changes made and now I can no longer change my default OS.  Start-up Manager & Grub Customizer do not work with version 1.99, so does anybody know how to change the default OS?

---

### Post by Quackers on 2011-09-13
No they don't work with Grub 1.99 version.
The only way I know of is to edit /etc/default/grub and change the 
GRUB_DEFAULT=0
line to 
GRUB_DEFAULT=X
where X is the number of the grub menu item you want to be set as default, minus 1 (as the first entry is 0, not 1)
Details in this guide by drs305 - scroll down a way to the section headed
/etc/default/grub

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Once that's done, save the file then run sudo update-grub in the terminal to update the grub menu.

---

### Post by oscarivera9 on 2011-09-13
> **Quackers said:**
> No they don't work with Grub 1.99 version.
The only way I know of is to edit /etc/default/grub and change the 
GRUB_DEFAULT=0
line to 
GRUB_DEFAULT=X
where X is the number of the grub menu item you want to be set as default, minus 1 (as the first entry is 0, not 1)
Details in this guide by drs305 - scroll down a way to the section headed
/etc/default/grub

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Once that's done, save the file then run sudo update-grub in the terminal to update the grub menu.

I believe that will not work because apparently ''The use of a number in GRUB_DEFAULT is not possible with version 1.99.  
Check it out, I read it here:   [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) if you go down just a bit you'll come across this:
> **[COLOR=DarkRed][SIZE=3]Grub Submenu[/SIZE][/COLOR] **
Test versions of Ubuntu 11.04 (Natty Narwhale) are being released with Grub 1.99. One of the new features is the use of the *Submenu*.  The submenu is still being tweaked, but should hide older kernels in  the main OS. Clicking on the Submenu entry will reveal the underlying  older kernels. Using a Submenu kernel as the default initially was not  possible, but a patch has been submitted by Colin Watson. The user will  be able to use either the exact menuentry title or the "saved" function  in /etc/default/grub's GRUB_DEFAULT= setting to set a submenu default. **The use of a number in GRUB_DEFAULT is currently not possible.** More details as they become available.
So then, I tried to write in the name of the operating system inside quotes as recommended, and that didn't work either.

---

### Post by Quackers on 2011-09-13
If you have older kernels installed then that is likely to be the case. 
I suspect that the number can be replaced with an exact copy of the /boot/grub/grub.cfg menu entry for the entry you want to be the default one. This would need to be in quotes, I think.

---

### Post by drs305 on 2011-09-13
I ended up creating a separate tutorial dealing with Grub 1.99 submenus, as this issue is bound to come up from time to time:
[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316")

---

### Post by oscarivera9 on 2011-09-13
> **Quackers said:**
> If you have older kernels installed then that is likely to be the case. 
I suspect that the number can be replaced with an exact copy of the /boot/grub/grub.cfg menu entry for the entry you want to be the default one. This would need to be in quotes, I think.
First off, thanks for your quick response.  Now, as far as older kernels, all that I have is whatever was installed from the Live CD two weeks ago, as this is a new PC that I just built.  When I say that I used to change menu entries in the past, it was with an older Pentium 4 machine that as of two weeks ago I no longer use.

---

### Post by drs305 on 2011-09-13
I forgot to mention that Grub Customizer should now work with Grub 1.99 submenus and it's a great GUI app for dealing with Grub 2. Daniel Richter and I discussed this issue when Grub 1.99 came out and he was very proactive in modifying his program. (See the 'Customizer' link in my signature line.)

---

### Post by Quackers on 2011-09-13
Thanks drs305, that's much clearer :-)
So numbers can be used.
If the required menu choice is in the submenu then the form changes to X>Y, where X is the submenu's number and Y is the entry in that submenu, starting again from 0.
As ever, many thanks for your time :-)

oscarivera9, as I understand it in your circumstances the number should still be an option for you.

---

### Post by oscarivera9 on 2011-09-13
> **drs305 said:**
> I ended up creating a separate tutorial dealing with Grub 1.99 submenus, as this issue is bound to come up from time to time:
[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316")
  I'm a bit confused here.  I actually went ahead and read what you are suggesting last night and I thought it didn't apply to me because I am using a new PC that only has Ubuntu 11.04 and Windows 7.  So the only "older kernel" is the one that was included with the installation.  I'll go ahead and read up on it again and try what's suggested.  Thanks in advance!

 The only reason I want to change the default entry is that I read in the ''Linux Format'' magazine about half a year ago that often with Windows Vista and Windows 7 the service packs will fail to install.  So I figure that if Windows is the default OS maybe I will not have that problem, but I could be wrong.

---

### Post by Quackers on 2011-09-13
The only time that submenus will be a problem (and previous kernels) is when you have a menu entry "previous Linux versions", as I understand it.
You should be ok to use the number (minus 1) of the entry you wish to be the default one.
As to whether it will work when Windows service packs are installed I'm afraid I don't know. It may be that the installation of a service pack will over-write the mbr of the drive, therefore replacing grub with the Windows bootloader.
But that's just a guess.

---

### Post by Rex Bouwense on 2011-09-13
I had a similar problem a couple of days ago.  I was dual booting with Ubuntu 10.04 (Lucid) and Lubuntu 11.04 (Natty).  See this thread:
[http://ubuntuforums.org/showthread.php?p=11242146](http://ubuntuforums.org/showthread.php?p=11242146)

Sorry, I didn't read Windows when I read your post.  Well, I read it but it didn't sink in until after I posted.

---

### Post by drs305 on 2011-09-13
OK. Since you want to make Windows your default OS and it should remain on the main menu page, you can use the more conventional method of selecting it.

Use the exact title of the Windows menuentry (between the quotes) as the default. Don't use the numeral method. Since this is a new installation, you most likely don't have an extra kernel. Once you do, the numbers of the main page entries will change. I'd have to go back and read my own tutorial to try to remember if they automatically update when a new submenu is created, but using the title would be safer as the Windows entry should never be moved to a submenu.

As far as making Windows the primary OS in Grub; I don't think it's going to prevent whatever potential problem you read about. The reason is that whether it is the default OS or not, the way it's set up it's still going through Grub 2 and Grub 2 is on the MBR. Although this isn't a Windows forum, if you found the link someone knowledgeable could tell you whether the issue is still relevant and what to do about it. Just don't create a separate thread dealing specifically with a Windows problem on the Ubuntu Forums.  ;-)

---

### Post by oscarivera9 on 2011-09-13
> **Quackers said:**
> If you have older kernels installed then that is likely to be the case. 
I suspect that the number can be replaced with an exact copy of the /boot/grub/grub.cfg menu entry for the entry you want to be the default one. This would need to be in quotes, I think.

Quackers, it worked!  I did exactly as you told me and I used the copy/paste method with the /boot/grub/grub.cfg menu entry on to /etc/default/grub with quotes and it worked!

THANKS TO EVERYONE who jumped on-board to try and help me!
):P

---

### Post by Quackers on 2011-09-13
I'm glad that things are working ok.
I think that's the same as drs305 was saying. That entry should stay as default now whatever happens. 
As I said earlier I have no idea whether a Windows service pack will over-write it or not. You'll have to cross that bridge if you come to it.
All the stuff I quote about grub2 comes from drs305's guides. Without drs305 I would be lost too! (Any mistakes are my own though!).

---

### Post by oscarivera9 on 2011-09-13
> **drs305 said:**
> As far as making Windows the primary OS in Grub; I don't think it's going to prevent whatever potential problem you read about. The reason is that whether it is the default OS or not, the way it's set up it's still going through Grub 2 and Grub 2 is on the MBR. Although this isn't a Windows forum, if you found the link someone knowledgeable could tell you whether the issue is still relevant and what to do about it. Just don't create a separate thread dealing specifically with a Windows problem on the Ubuntu Forums.  ;-)

> **Quackers said:**
> I'm glad that things are working ok.
I think that's the same as drs305 was saying. That entry should stay as default now whatever happens. 
As I said earlier I have no idea whether a Windows service pack will over-write it or not. You'll have to cross that bridge if you come to it.
All the stuff I quote about grub2 comes from drs305's guides. Without drs305 I would be lost too! (Any mistakes are my own though!).

Both of you guys were so helpful in this and I would like to thank you.  As for the Windows problem, I think it might have been irrelevant because I just read somewhere that it applies to Grub Legacy, not Grub2.  So it seems like I'll be o.k.  Either way, sooner or later we would have had to find out how to change the default OS menu entry and drs305 was right about that. 
Problem solved.

---

### Post by Blasphemist on 2011-09-13
I'm betting that the only problem with the windows update is that windows is often configured to automatically reboot after certain updates. The update then wouldn't actually finish the update until windows was next booted if an ubuntu or other linux is the default boot item. The only time I can think of that this might really be an issue is if it is a wubi installation. And maybe not even then.

---

### Post by oscarivera9 on 2011-09-13
> **Blasphemist said:**
> I'm betting that the only problem with the windows update is that windows is often configured to automatically reboot after certain updates. The update then wouldn't actually finish the update until windows was next booted if an ubuntu or other linux is the default boot item. The only time I can think of that this might really be an issue is if it is a wubi installation. And maybe not even then.
No, actually I've never had a Wubi installation.  My current computer has Windows 7 and Ubuntu 11.04 without Wubi.  On another PC I have Windows XP, Ubuntu 10.10, Debian 6, and Mandriva 2010.2.  But like I said just a little while ago, I think the problem (whatever it might have been), has been resolved with Grub2, I think it only applied to Grub Legacy.  I just found that out recently, after starting this thread.

---

