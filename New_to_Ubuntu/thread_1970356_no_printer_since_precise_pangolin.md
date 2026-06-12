---
title: "no printer since precise pangolin"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by harfin on 2012-05-01
I have now [COLOR="Red"]almost[/COLOR] got a good set up with the new version (after some assistance from this forum regarding connection to my broadband) - my printer an epson stylus S20.  The printer worked fine with the previous version,

I have tried the feature to add a new printer, and the system seems to find the printer fine.  However when I select print form Open Office documents (also a new version?) the printer ready light flashes once or twice then stops and the job disappears from the print queue - but no print.

I have tried printing a test page from the add printer gizmo with the same result.

What else can I try?

Alan

---

### Post by plucky on 2012-05-01
> **harfin said:**
> I have now [COLOR="Red"]almost[/COLOR] got a good set up with the new version (after some assistance from this forum regarding connection to my broadband) - my printer an epson stylus S20.  The printer worked fine with the previous version,

I have tried the feature to add a new printer, and the system seems to find the printer fine.  However when I select print form Open Office documents (also a new version?) the printer ready light flashes once or twice then stops and the job disappears from the print queue - but no print.

I have tried printing a test page from the add printer gizmo with the same result.

What else can I try?

Alan

In your Browser (Chrominium!!) type into the address bar ```
127.0.0.1:631
``` which will open the CUPS interface.

Check if the printer has the correct paper size (A4) and not letter in the default settings.

Also the CUPS interface has the errorlog information.

Good Luck

---

### Post by harfin on 2012-05-01
> **plucky said:**
> In your Browser (Chrominium!!) type into the address bar ```
127.0.0.1:631
``` which will open the CUPS interface.

Check if the printer has the correct paper size (A4) and not letter in the default settings.

Also the CUPS interface has the errorlog information.

Good Luck

Thankyou for that!  
My printer is there. 
Paper set to A4
Interesting reading, but the job log says that all jobs were completed.  They weren't!
When I go to look in-depth it requires me to log in, i.e. User name & password. 

How do I establish what my user name is?  Is it something generic like "admin"? 
Is my password the same as for my computer system log-in?

The error-log shows
E [01/May/2012:06:42:43 +0100] Filter "oopstops" not found.
E [01/May/2012:06:42:43 +0100] Filter "hpgltops" not found.
E [01/May/2012:06:42:43 +0100] Filter "pstoraster" not found.
W [01/May/2012:06:42:43 +0100] no access to /System/Library/ColorSync/Profiles/sRGB Profile.icc
W [01/May/2012:06:42:43 +0100] no access to /System/Library/ColorSync/Profiles/sRGB Profile.icc
W [01/May/2012:06:42:43 +0100] no access to /System/Library/ColorSync/Profiles/Generic CMYK Profile.icc
W [01/May/2012:06:42:43 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON-Stylus-S20-Gray..' already exists
W [01/May/2012:06:42:43 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON-Stylus-S20-RGB..' already exists
W [01/May/2012:06:42:43 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-EPSON-Stylus-S20' already exists

Does that help?

Alan

---

### Post by plucky on 2012-05-01
> How do I establish what my user name is? Is it something generic like "admin"? 

It is the "username" and "password" that you use to login to your account.

Try adding your printer again using the CUPS interface.

Does it ask you what driver you want to use?

Try a Test Page from the CUPS interface and see what is logged in the errorlog.

---

### Post by harfin on 2012-05-01
> **plucky said:**
> It is the "username" and "password" that you use to login to your account.

Try adding your printer again using the CUPS interface.

Does it ask you what driver you want to use?

Try a Test Page from the CUPS interface and see what is logged in the errorlog.


The box that comes up "The server requires a user name & password. The server says CUPS", that does not accept my Ubuntu Forum username and password!

I had already tried adding the printer anew, and CUPS 'found' the printer and selected the driver.

As I said a bit back, I tried printing a test page from CUPS and although the printer's 'ready' flashed a time or two, nothing else happened; no test page, no nothing.

Alan

---

### Post by harfin on 2012-05-02
> **plucky said:**
> It is the "username" and "password" that you use to login to your account.

Try adding your printer again using the CUPS interface.

Does it ask you what driver you want to use?

Try a Test Page from the CUPS interface and see what is logged in the errorlog.

I am afraid that whatever I do on that CUPS interface it wants to know my account and password.

Sorry, but this is ultra confusing to me!  
I have no "account" as such with CUPS, though I tried to set one up, but that's another story.
I have a user name and password on this Ubuntu Forum. 
I also have a an user name and a password on the PC
Neither of those work on the CUPS interface.
What the heck is the user name and account I need to be able to get into the CUPS interface so I can follow the recommended steps (again) 

Alan

---

### Post by florus on 2012-05-02
You need the username and password that you log into your computer with. (Assuming that the printer is connected directly to your computer, and not to another computer on a network.)

---

### Post by harfin on 2012-05-02
> **florus said:**
> You need the username and password that you log into your computer with. (Assuming that the printer is connected directly to your computer, and not to another computer on a network.)

As I said earlier, I have tried my password and user i/d already and all that happens is it reverts to a grey box that has at the top "The Server127.0.0.1:631 requires a user name and password. The server says :CUPS."

Alan

---

### Post by harfin on 2012-05-02
> **harfin said:**
> As I said earlier, I have tried my password and user i/d already and all that happens is it reverts to a grey box that has at the top "The Server127.0.0.1:631 requires a user name and password. The server says :CUPS."

Alan

i.e. the sign-on box!
:-(

---

### Post by harfin on 2012-05-02
> **florus said:**
> You need the username and password that you log into your computer with. (Assuming that the printer is connected directly to your computer, and not to another computer on a network.)

I've tried that.  No joy.
Yes the printer is connected into this computer directly.

Any advice?

Alan

---

### Post by florus on 2012-05-02
Well, no, not a lot really. Since changing to Pangolin I am having printer problems as well - a six minute delay before even a simple page prints. 
Two suggestions in the absence of more informed contributions from some one else: try deleting the printer, re-booting and adding the printer again; alternatively try using Linux Mint. It is based on Ubuntu, but more conservative; I like it a lot with the cinnamon environment.

---

### Post by harfin on 2012-05-03
> **florus said:**
> Well, no, not a lot really. Since changing to Pangolin I am having printer problems as well - a six minute delay before even a simple page prints. 
Two suggestions in the absence of more informed contributions from some one else: try deleting the printer, re-booting and adding the printer again; alternatively try using Linux Mint. It is based on Ubuntu, but more conservative; I like it a lot with the cinnamon environment.

Just did that.
It looked for the driver, and then came back with a settings box (as part of the Printer gizmo). I then selected print test page. Printer ready light flashed, then the printer started up as though it was about to load a sheet of paper and begin printing. Then the ready light stopped flashing.  A minute or two later, the printer then made it's normal noise (cartridge holder docking?) and then nothing else.  Light showing steady now.

In the settings window it shows the following:
Device URI = 'usb://EPSON/Stylus%20S20?serial=4B4B36503034393823'
Make & Model = 'Epson Stylus S20 - CUPS+Gutenprint (OpenPrinting LSB 3.2) v5.2.5 Simplified'
Printer State = 'Idle - Rendering completed'
Under Policies it shows: check boxes for State Enabled / Accepting jobs / Shared all checked '
Access Control : 'Allow printing for everyone' checked

Any of that helpful in identifying my problem to any adviser?

Alan

---

### Post by harfin on 2012-05-03
> **harfin said:**
> Just did that.
It looked for the driver, and then came back with a settings box (as part of the Printer gizmo). I then selected print test page. Printer ready light flashed, then the printer started up as though it was about to load a sheet of paper and begin printing. Then the ready light stopped flashing.  A minute or two later, the printer then made it's normal noise (cartridge holder docking?) and then nothing else.  Light showing steady now.

In the settings window it shows the following:
Device URI = 'usb://EPSON/Stylus%20S20?serial=4B4B36503034393823'
Make & Model = 'Epson Stylus S20 - CUPS+Gutenprint (OpenPrinting LSB 3.2) v5.2.5 Simplified'
Printer State = 'Idle - Rendering completed'
Under Policies it shows: check boxes for State Enabled / Accepting jobs / Shared all checked '
Access Control : 'Allow printing for everyone' checked

Any of that helpful in identifying my problem to any adviser?

Alan

No takers?

Alan

---

### Post by kurt18947 on 2012-05-03
When logging onto CUPS, I have to use a username & password that has authority to administer printers.  That would be users with SUDO privileges or (I think) users that can manage printers.  I've never worked with Epson so can't help with that.  There is a site that has software for many Epson printers, which is now hosted by Seiko Epson, it seems.

[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

Anything useful there?  If your machine is pretty new there may not be open source drivers for it yet or the drivers available are not tweaked for the newest CUPS.

---

### Post by harfin on 2012-05-03
> **kurt18947 said:**
> When logging onto CUPS, I have to use a username & password that has authority to administer printers.  That would be users with SUDO privileges or (I think) users that can manage printers.  I've never worked with Epson so can't help with that.  There is a site that has software for many Epson printers, which is now hosted by Seiko Epson, it seems.

[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

Anything useful there?  If your machine is pretty new there may not be open source drivers for it yet or the drivers available are not tweaked for the newest CUPS.

Hi Kurt

Thanks for that.

I'm the Administrator on my PC (and everything else!).  I've just checked my permissions under users accounts and groups and I can edit printers (and also have a check mark against 'sudo').  Still cannot log in, though.

The drivers on that website do not attribute the Precise Pangolin 12.04 to my printer (Epson Stylus S20). The list of available systems for my oprinter seems to stop at 10.04.  It certainly worked fine under Oneiric

That unchanged driver may account for my printer not working, perhaps, but it doesn't account though for why I cannot get on to CUPS editing etc. :-(

Any idea where I can find out about whether there will be a driver modification to 12.04 that will allow me to use my trusty Epson?  If not, I guess I am going to have to buy a new one.

Regards
Alan

---

### Post by kurt18947 on 2012-05-03
Hi harfin

I just tried logging onto my CUPS server from a desktop user account.  I'm running 12.04 gnome-shell updated to current. I just typed this:

```
http://localhost:631
```

I used this account's user name and password and was able to log onto the CUPS admin page.  This account can configure printers but does not have SUDO priviledges.  The drivers on Epson's site were dated 21 December 2011 though the OSs listed are older than that.  I didn't download and extract any of them to see what format they're in.  Maybe an Epson user will be along with better advice.

---

### Post by harfin on 2012-05-03
> **kurt18947 said:**
> Hi harfin

I just tried logging onto my CUPS server from a desktop user account.  I'm running 12.04 gnome-shell updated to current. I just typed this:

```
http://localhost:631
```

I used this account's user name and password and was able to log onto the CUPS admin page.  This account can configure printers but does not have SUDO priviledges.  The drivers on Epson's site were dated 21 December 2011 though the OSs listed are older than that.  I didn't download and extract any of them to see what format they're in.  Maybe an Epson user will be along with better advice.

Just tried that Karl; no go.  

Had a quick scour through the CUPS Forum, but nothing seems relevant.  They talk of 'Root User Name ' and Root Password'.  What the heck are they?

Regards
Alan

---

### Post by kurt18947 on 2012-05-03
> **harfin said:**
> Just tried that Karl; no go.  

Had a quick scour through the CUPS Forum, but nothing seems relevant.  They talk of 'Root User Name ' and Root Password'.  What the heck are they?

Regards
Alan

I'm no expert so take this for what it's worth.  Some distros,  I think Fedora and PCLinuxOS are two that have administrators log on as root.  A root user can do _*anything*_ to their system, including screwing it up beyond all recognition.  Debian and Ubuntu prefer SUDO (Super User DO) which seem to grant  administrative powers in smaller parcels and for a  limited time.  At least that's how I understand it.

---

### Post by florus on 2012-05-04
I now have much the same problem. My printer, a Brother 5240, has gone from taking 6 minutes to print a simple text page, via whirring but producing nothing, to totally locking up, and finally to giving me a printout reading "ERROR NAME: memoryfull". This last being the first job after being turned off all night.

---

### Post by harfin on 2012-05-04
Tried printing test page again this am.  Ready light flashed, cartridges moved as if about to print, few more winks of the light, then steady, then cartridges moved back to standby.

I still cannot sign on to CUPS to perform admin tasks, no matter what I enter as user and password.

So, can someone tell us what is going on with 12.04 and printers?

Alan

---

### Post by JFK.NM on 2012-05-04
Same issue here - only since upgrade. Can print light text (gedit document), but any image or the like results in "memoryfull" , ioerror, limitcheck.

---

### Post by kurt18947 on 2012-05-04
> **harfin said:**
> Tried printing test page again this am.  Ready light flashed, cartridges moved as if about to print, few more winks of the light, then steady, then cartridges moved back to standby.

I still cannot sign on to CUPS to perform admin tasks, no matter what I enter as user and password.

So, can someone tell us what is going on with 12.04 and printers?

Alan

The fact that you're unable to log onto CUPS makes me wonder if you have something odd going on with your 12.04 installation.  Some sort of permissions problem?  Something to do with a fire wall?  Do you have a means to do a second clean install without messing with your current?  

I had printing issues during 12.04's gestation -- Brother printers would take 45-50 seconds from pressing the 'print' button to the printer coming alive.  That was remedied on one of the last updates prior to 12.04 being released, both MFCs come alive within 10 seconds of pressing the 'print' button.  There were 3 or 4 CUPS updates after 12.04 A2 was released.

---

### Post by intruderukr on 2012-05-04
I have the same problem, no printing in Precise...:(  I hope to follow these posts until I find a solution...
thank you - Alleykat

---

### Post by harfin on 2012-05-04
> **kurt18947 said:**
> The fact that you're unable to log onto CUPS makes me wonder if you have something odd going on with your 12.04 installation.  Some sort of permissions problem?  Something to do with a fire wall?  Do you have a means to do a second clean install without messing with your current?  

I had printing issues during 12.04's gestation -- Brother printers would take 45-50 seconds from pressing the 'print' button to the printer coming alive.  That was remedied on one of the last updates prior to 12.04 being released, both MFCs come alive within 10 seconds of pressing the 'print' button.  There were 3 or 4 CUPS updates after 12.04 A2 was released.

Karl, I am loath to try reinstalling as the 1st time took so long, and (other than my printer issue) it works very well; can be a bit slow at boot-up though.  The time for Pangolin download wasn't helped the following day by having to download a brand new version of the complete Open Office suite.  The descriptor of my 12.04 version is 12.04 LTS, Is that the same as the one you refer to? 

Only other event that occurred with the 12.04, is that my Belkin wireless device has for some reason ceased to work when I sign on to the Windows XP sign on option.  It's not a real issue, and one I'll get around to in due course.

Regards
Alan

---

### Post by florus on 2012-05-04
I have just done a complete fresh install of 12.04 with no improvement - still the message "ERROR NAME: memoryfull" printed on the sheet of paper. I am even using Unity rather than installing my preferred option of cinnamon. My next re-install will be Mint 12; I know that works ok. A shame as I have been using Ubuntu since Feisty Fawn.

---

### Post by florus on 2012-05-04
There are confirmed bugs on Launchpad relating to network and wireless printing (though not to local host printing). This would suggest that the problem is fairly general and we may just have to wait for a bug fix.

---

### Post by harfin on 2012-05-05
> **florus said:**
> There are confirmed bugs on Launchpad relating to network and wireless printing (though not to local host printing). This would suggest that the problem is fairly general and we may just have to wait for a bug fix.

Hopefully we will not have to wait TOO long for someone to fix the bug(s).
Alan

---

### Post by florus on 2012-05-06
I keep trying to find a workaround, but there seems to be no way of trying different drivers for the printer.

---

### Post by harfin on 2012-05-06
> **florus said:**
> There are confirmed bugs on Launchpad relating to network and wireless printing (though not to local host printing). This would suggest that the problem is fairly general and we may just have to wait for a bug fix.

I had a look through these, and it appears that all is not well with 12.04. I found another bug (not connected with printing) that I experience since 12.04 with Evolution and icons.  I wonder how may more there are yet to crop up.

---

### Post by florus on 2012-05-06
There are inevitably bugs in a new release, but this is the first time that one as seriously inconvenienced me. I check for known issues before installing, but there was nothing about printing problems.

---

### Post by JFK.NM on 2012-05-07
This is killing me! I use this printer to print invoices for customers - uggggh!

---

### Post by JFK.NM on 2012-05-07
FIXED with: Installation of package:  brother-cups-wrapper-laser Reinstalled Printer Selected driver "MFC8860DN" Seems to work fine.

---

### Post by harfin on 2012-05-07
> **JFK.NM said:**
> This is killing me! I use this printer to print invoices for customers - uggggh!

I'm not sure, as a relative beginner to this forum, what happens now.  

I guess we are reliant on someone 'in the know' to tell us 
1) what the developers have in train
2) some sort of timetable to fix whatever the problem or bug is
and if a fix is not about to happen in the short-term, 
3) a work-around as a short term option

Alan

---

### Post by harfin on 2012-05-08
> **harfin said:**
> I'm not sure, as a relative beginner to this forum, what happens now.  

I guess we are reliant on someone 'in the know' to tell us 
1) what the developers have in train
2) some sort of timetable to fix whatever the problem or bug is
and if a fix is not about to happen in the short-term, 
3) a work-around as a short term option

Alan

Alas all the alternative drivers in CUPS Epson S20 don't work.  Anyone any ideas on alternative drivers my my printer?
Alan

---

### Post by JFK.NM on 2012-05-08
[B]:KSI HAVE RESOLVED THIS ISSUE ON MY COMPUTERS BY SWITCHING THE DRIVER BY THE FOLLOWING METHOD:KS<BR>
<BR>
Install Package  :  _brother-cups-wrapper-laser_ <BR>
</b>
[/B]This package provide all cups wrapper drivers for models DCP-7010 DCP-7020 DCP-7025 DCP-8060 DCP-8065DN FAX-2820 FAX-2920 HL-2030 HL-2040 HL-2070N HL-5240 HL-5250DN HL-5270DN HL-5280DW MFC-7220 MFC-7225N MFC-7420 MFC-7820N MFC-8460N MFC-8660DN MFC-8860DN MFC-8870DW 	  

<B> After installing package, you must change the driver specified in printers the new driver appears as "MFC**** FOR CUPS" (scroll up)
<Br>
Before installing this new driver, on Precise, I would receive an error message - now everything works perfectly.

---

### Post by harfin on 2012-05-08
> **JFK.NM said:**
> [B]:KSI HAVE RESOLVED THIS ISSUE ON MY COMPUTERS BY SWITCHING THE DRIVER BY THE FOLLOWING METHOD:KS<BR>
<BR>
Install Package  :  _brother-cups-wrapper-laser_ <BR>
</b>
[/B]This package provide all cups wrapper drivers for models DCP-7010 DCP-7020 DCP-7025 DCP-8060 DCP-8065DN FAX-2820 FAX-2920 HL-2030 HL-2040 HL-2070N HL-5240 HL-5250DN HL-5270DN HL-5280DW MFC-7220 MFC-7225N MFC-7420 MFC-7820N MFC-8460N MFC-8660DN MFC-8860DN MFC-8870DW 	  

<B> After installing package, you must change the driver specified in printers the new driver appears as "MFC**** FOR CUPS" (scroll up)
<Br>
Before installing this new driver, on Precise, I would receive an error message - now everything works perfectly.

That's fine if your printer is a Brother!
Mine is an Epson - so still no printer and I have to wait until there is an **Epson driver fix**!

---

### Post by florus on 2012-05-08
> **JFK.NM said:**
> [B]
Install Package  :  _brother-cups-wrapper-laser_ [/B].
Thanks, JFK.NM. I installed the package as suggested, deleted the printer and then added it again. It did not offer me a choice of drivers, but it seems to be working properly so far.

---

### Post by florus on 2012-05-08
No, I spoke too soon. The printer is working intermittently, but still printing error messages instead of emails.

---

### Post by harfin on 2012-05-09
> **florus said:**
> No, I spoke too soon. The printer is working intermittently, but still printing error messages instead of emails.

Not sure if you have done the following or not.On my set up if I go to Printers via the extreme right icon in the top tool-bar, there is an option called 'Printers'
If you click on that you get a window which gets a printer image with the name of the connected printer.
If you click on that image you get a window with a list of things relating to that printer, one of which (the top one on the window) is 'Settings'
If you click settings (it may come up anyway as it's the 1st option) and select 'Make and Model', and if you select the 'Change' button beside that line you then get a window headed 'Change Driver'
Your printer's manufacturer's name should be highlighted with the top radio button on the three possible actions at the top, with the text @Select printer from Database.
If you select the 'Forward' button in the bottom right corner, you should then see the drivers that it has for your make and model.
It may work for you, but I tried each of the three drivers for my Epson S20 and the result was no working printer still.
Alan

---

### Post by Avolancher on 2012-05-09
where do i get this package.

---

### Post by harfin on 2012-05-10
> **Avolancher said:**
> where do i get this package.
You should have a top toolbar, with link icons or words.  
Mine on the top right has the following:
icon of an envelope, 
an icon for my wireless strength, 
an icon for my speaker volume
The day, date and time
an icon of a human plus user name signed on 
and at the extreme right an icon that looks like a gear cog

If you click on the gear cog looking icon, you should see a drop down list that strats with
System Settings
Displays etc down to the 6th item (on mine) that says 'Printers'.
Thats the starting item I was referring to in the earlier post
Hope that helps


Alan

---

### Post by florus on 2012-05-10
@Avolancher
Install Synaptic using the software centre.
Start synaptic and type the make of your printer into the search box.
This will give you a list of packages available for that make of printer.

---

### Post by harfin on 2012-05-10
So Ubuntu gurus, no further advice for my non-working Epson S20 printer in Precise Pangolin?

I've deleted and re-installed it.

I've searched for and installed the recommended driver (plus other optional ones as well)

All I get (at best) is a winking ready light!

Please,any sort of response would be great.

Alan

---

### Post by florus on 2012-05-13
Well, I have solved the problem from my point of view. I have replaced Pangolin with Mint 12, and can now print again. Like Harfin, I have a business to run.

---

### Post by TenPlus1 on 2012-05-13
Lubuntu is quite light on the printers drivers as well since I have to install hplip to get my printer working ok, have you tried isntalling epson-escpr and then searching for your printer again ?

---

### Post by harfin on 2012-05-14
> **TenPlus1 said:**
> Lubuntu is quite light on the printers drivers as well since I have to install hplip to get my printer working ok, have you tried isntalling epson-escpr and then searching for your printer again ?

Yes I did download that, and it made no difference to the number (or behaviour!) of the epson s20 drivers I had previously tried unsuccessfully before.  There were some additional (old) dot matrix printer drivers, but no new s20 ones.

I have hooked the printer up to a netbook running an earlier version of Ubuntu (Oneiric I think), and the printer performed very well, as it did before my upgrade to Pangolin.

I don't appear to have any other options!

Alan

---

### Post by harfin on 2012-05-18
I don't know why, but I decided to have yet another go at getting my Epson S20 to work on Precise Pangolin.

I selected driver STP00539.ppd which shows a Make  & Model reference Epson Stylus S20 - CUPS+Gutenprint v5.2.8-pre

Just for the heck of it, I selected Print Test Page and knock me down with a feather it actually worked!

Whether this was as a result of some of the updates in the last 4 or 5 days or something else, I have absolutely no idea.

Fingers crossed that all is now well as Pangolin in all other respects is brilliantly quick and reliable.

Congratulations and thankyou Ubuntu / forum users / experts or [I]"ingredient X"[I]

Alan

---

