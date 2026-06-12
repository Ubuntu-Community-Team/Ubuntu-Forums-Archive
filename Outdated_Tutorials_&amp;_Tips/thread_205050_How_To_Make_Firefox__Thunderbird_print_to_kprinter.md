---
title: "How To: Make Firefox / Thunderbird print to kprinter automatically in KDE / Kubuntu"
date: 2006-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by msak007 on 2006-06-27
Well I know there are a few threads out there on how to integrate Firefox into KDE and how to get Firefox to print to **kprinter**, but there was nothing that I could find on how to do it automatically and seamlessly (instead of selecting "PostScript/default" manually every time) and not much info on Thunderbird. So here are the steps I took to get Firefox and Thunderbird to print to kprinter automatically once you click "Print". 

_**Firefox:**_
1. First, if you haven't done so, you need to print to PostScript in order for the needed entry in prefs.js to be populated. This will be done automatically the first time you print. Open any web page and go to:

File --> Print --> choose **PostScript/default** (it should be the default if you haven't installed any printers yet) --> click "Print"

Once you have done this and it prints, it'll add the PostScript entry you need to edit. 

2. In the URL bar, type

```
about:config
``` to open the config page.

3. In the "Filter" bar, type

```
print.printer_PostScript/default.print_command
``` 
This should filter everything out but that line.

4. Right-click on the line, click on "Modify", and change the entry to say

```
kprinter
``` then click OK. This will make Firefox print to kprinter any time you select the "PostScript/default" printer.

5. Right-click anywhere in the white space, then click on "New --> Boolean" to add a new Boolean entry. Type

```
print.always_print_silent
``` 

and set its value to "true". This will force Firefox to print to the default printer without prompting you. If "PostScript/default" is the only printer you have and there are no local / network printers, it works great and you can stop here. But if you installed a printer through CUPS, it complicates things as Firefox will want to use that as a default and all your prints will go there without prompting you! So even if you don't have a local printer, it's a good idea to add the following line in case you add one later. 

6. Once again, right-click and choose "New --> Boolean". Type

```
print.postscript.cups.enabled
``` 
and set its value to "false". That will disable CUPS printing in Firefox, and it will default to the "PostScript/default" printer. And since you've changed the output of that to kprinter, you'll see a "processing" dialog for a split second when you print, after which kprinter will open up. There you can choose all your printers, including PDF, PostScript, and any CUPS installed printers :) .
_________________________________

_**Thunderbird:**_
The procedure for Thunderbird is exactly like it is for Firefox, but with one difference: there's no URL bar to get to about:config.*

1. Just as with Firefox, you first need to print something to PostScript in order for the entry you need to modify to be present.

2. Go to "Edit --> Preferences", click on "Advanced", then click on the "General" tab. Click on the "Config Editor..." button to open the about:config window. 

3. Once the about:config window is open, follow steps 3-6 above for Firefox. This will also make Thunderbird print to kprinter automatically.

* There's an alternative way to get to about:config in Thunderbird - install the about:config extension. Go [here]("http://aboutconfig.mozdev.org/installation.html") and download the extension. Install it and restart Thunderbird. Once you've launched it again, there should be an entry for about:config in your Tools menu (Tools --> about:config). You can also customize your Toolbar and add a button for about:config. 
_________________________________

_**Resetting everything back to default:**_
If you ever want to disable these options or revert back to the defaults, simply do the following. If you've already closed about:config, open it up again. 

1. Find the **print.printer_PostScript/default.print_command** again, right-click on it, and choose "Modify". Then type the following

```
lpr ${MOZ_PRINTER_NAME:+-P"$MOZ_PRINTER_NAME"}

``` 
and click OK. This will revert Firefox back to its native printing system.

2. Find **print.always_print_silent**, right-click on it, and choose "Toggle" to set its value to "False". This will change it back to the default behavior of prompting you for a printer rather than printing automatically.

3. Find **print.postscript.cups.enabled**, right-click on it, and choose "Toggle" to set its value to "True". This will allow Firefox to see CUPS printers again.

Hope this helps!

---

### Post by slavik on 2006-07-25
I am working on setting up Firefox on Linux for my college and only recently found that the terminal needs to be able to print ... this will work very nicely (as I am have done all work to lockdown the system).

---

### Post by msak007 on 2006-07-25
Thanks for letting me know it helped you. I was starting to wonder if I was the only person who found this useful.

---

### Post by helmar on 2006-08-18
Thanks for the description! On my debian-box i ran into problems because firefox does also use the xprint-printers (and xprint does also offer the CUPS-printers). I solved the problem in simply removing xprint: apt-get remove --purge xprint xprint-common . Since i didn't notice any problems with other programs this to me seems the simplest way to get rid of the unwanted printers.

---

### Post by msak007 on 2006-08-18
I never heard of or used xprint. Are you saying that it conflicted with the instructions I gave, and that you had to remove it completely in order to get Firefox to print to kprinter?

---

### Post by helmar on 2006-08-18
When printing firefox (if not compiled with --disable-xprint) looks also for xprint-printers ([http://xprint.mozdev.org/](http://xprint.mozdev.org/)). So when CUPS and xprint are present you have:

- CUPS-printers
- xprint-printers
- PostScript/default

When disabling only CUPS (print.postscript.cups.enabled=false) you still have the xprint-printers, so PostScript/default is not the only printer left. Only after disabling (uninstalling was the easiest way for me, maybe there are others) xprint the only printer left is PostScript/default.
As i mentioned i had this problem on debian, so maybe on a standard (k)ubuntu installation it isn't there (xprint normally not installed or firefox compiled with --disable-xprint?).

---

### Post by msak007 on 2006-08-18
Ok that's kind of how I understood the problem. I don't think xprint is installed by default in Ubuntu. I've only used the Ubuntu repo version and the official version from the Mozilla web site, so never had the need to complie it and I'm not sure if it's compiled with xprint enabled or disabled. I couldn't find any about:config settings for xprint, so maybe uninstalling it was the easiest route. Either way hopefully you got some use out of this and it's working for you.

---

### Post by johannes121 on 2006-11-24
Is there a way to do this for all users on a system? I.e. is there a way to configure some files in /etc/ in order that all users will have printing via kprinter? 

Thanks, 
Johannes

---

### Post by msak007 on 2006-11-24
> **johannes121 said:**
> Is there a way to do this for all users on a system? I.e. is there a way to configure some files in /etc/ in order that all users will have printing via kprinter? 
 
Thanks, 
Johannes
Well, I've never tried it so I can't be sure. Editing the options in about:config only modifies the prefs.js file in your profile folder. I believe there is a global prefs.js that I assume can be edited to contain this info. I will look into it when I get home as I'm at work now (using Windows and IE...bleh).

---

### Post by qpieus on 2006-11-24
msak007, you rule! Thanks a lot for this how to. I wanted to setup the "print to pdf" to save webpages and stuff (rather than bookmarking everything) several weeks ago. But I soon found out that the pdf printer was only available to KDE apps. Well, this fixes that problem. Thanks.

---

### Post by msak007 on 2006-11-25
> **qpieus said:**
> msak007, you rule! Thanks a lot for this how to. I wanted to setup the "print to pdf" to save webpages and stuff (rather than bookmarking everything) several weeks ago. But I soon found out that the pdf printer was only available to KDE apps. Well, this fixes that problem. Thanks.Thanks :). I was going through the same problem, trying to find a way to print to pdf, and it was very annoying. That's why I started looking for ways to do what I outlined above, and I'm glad it helped you out. Don't get too many comments on this thread so I can't tell if many people actually found it useful so thanks for letting me know.

**johannes121**: I believe I found a way to enable this globally. There is a file that controls global settings, but it's not **prefs.js** - it's called (ironically) **firefox.js**. Depending on how you installed Firefox, it'll be in one of 2 spots:
1. Ubuntu repo version will place the file in** /usr/share/firefox/defaults/pref/**
2. Installing the Mozilla version will put it in the folder you extracted it to, in the folder **<main folder>/firefox/defaults/pref/**. In my case I installed the app in /opt, so my firefox.js was in [B]/opt/firefox/defaults/pref/

[/B]Anyway, once you find the file, make sure you have Firefox closed and edit the file using your favorite editor. I assume in Kubuntu you're using KEdit or Kate, so make a backup of the file (just in case) then edit it with one of them. These are all examples using the Ubuntu repo version, edit your paths / commands accordingly:

```
cd /usr/share/firefox/defaults/pref/
sudo cp firefox.js firefox.js.backup
kdesu kate firefox.js
```Enter your password, and when Kate opens up add the following to the very end of the file:

```
// Print to kprinter by default for all users
pref("print.postscript.print_command", "kprinter");
pref("print.print_command", "kprinter");
pref("print.always_print_silent", true);
pref("print.postscript.cups.enabled", false);
```Save the file and launch Firefox. This will not overwrite or modify and user set entries (the entries in **bold** in about:config), so it will only affect new profiles. If you've already modified your profile, this will not change any of the settings in it. I've tried it out on my laptop and it seems to work with all new profiles I create. Please try it out and let me know if it works for you, and if so I'll modify the first post with the updated instructions.

---

### Post by mmebane on 2006-12-04
Thanks for the guide!

---

### Post by Gaiwecoor on 2006-12-06
msak007 - 
First of all, thanks for the work.  Any time we can get better integration into KDE, we all benefit.  *grin*

I only have one problem.. I'm not being asked for *which* printer to use, or a filename to print to.  Instead, it defaults to whatever is located in Firefox's print.printer_PostScript/default.print_to_filename key.  When I clear the key, it picks ~/mozilla.ps for me.

Any ideas on what I might be missing that drives the kprinter dialogs away?

*Note:* I switched over to Kubuntu from Windows about six months ago, so while I can typically take care of myself and keep myself out of trouble on the system, I don't know where to look for some of the more advanced settings.  If there's anything you want to know about my setup, I can get it to you.

Thanks in advance!

*Edit:*
A possible relevant point:  Firefox's default (and only) printer is simply "default", rather than "PostScript/default".  Does this matter?

---

### Post by msak007 on 2006-12-08
> **Gaiwecoor said:**
> msak007 - 
First of all, thanks for the work.  Any time we can get better integration into KDE, we all benefit.  *grin*

I only have one problem.. I'm not being asked for *which* printer to use, or a filename to print to.  Instead, it defaults to whatever is located in Firefox's print.printer_PostScript/default.print_to_filename key.  When I clear the key, it picks ~/mozilla.ps for me.

Any ideas on what I might be missing that drives the kprinter dialogs away?
...
Thanks in advance!

*Edit:*
A possible relevant point:  Firefox's default (and only) printer is simply "default", rather than "PostScript/default".  Does this matter?

**Gaiwecoor**: Thanks, I agree about the whole KDE thing and wish there would be more work on a "Firefox KDE" package to configure some of the more common tweaks we have to do manually to make it more integrated...but I digress. Regarding the issue you're having, I don't think the name of the printer has anything to do it. The repository version of Firefox 2.0 in Edgy seems to have "default" as the printer, not "PostScript/default" like 1.5 in Dapper. I verified this on my laptop, but on my Desktop I have the Mozilla version of Firefox and the printer still shows up as "PostScript/default". But the odd thing is that even on my laptop when I check about:config, the "PostScript/default" entries were still added when I tried to print the first time to the "default" printer, and they are in bold (meaning they were user customizations and not system defaults). It seems to me you have those entries as well as you posted above.

In about:config, check the following lines and post what their respective values are:

print.print_command
print.print_printer
print.printer_PostScript/default.print_command

Once you post those, I can compare them to mine and tell you if they need to be corrected.

---

### Post by swimmerken on 2006-12-10
In accordance with msak007's instructions I was able to make kprinter the default printer application for Firefox, but not for Thunderbird.  About six months ago I installed versions 1.5 of both applications.  As I already had CUPS installed in my box, CUPS showed up as one of the options for both.  Both also had a Postscript/default option as well.  Firefox also had the various options of the Xprint printer daemon as well; whereas Thunderbird did not.

In Thunderbird, the print window originally showed only two options: CUPS/LJ2P (LJ2P=HP LaserJet IIP) and Postscript/default.  Both options gave the same printing result.

When however I made the changes msak007 suggested, when print was selected no print window appeared.  Instead the print preparation window appeared, twice I think, then a window saying printing, or something to that effect, then all windows disappeared, and the text was printed.

I consequently had to go back to the original configuration, because when the printer window appears I at least have the option to print to file with the Postcript/default option.  It creates a .ps file which can be converted to a .pdf file using the ps2pdf command.

Someone suggested that if the Xprint daemon gets in the way the Xprint package can be removed.  I am reluctant to do so however, because Xprint is also used by Nvu, Mozilla's stand-alone webpage creator.  I would if I could figure out how to configure to use kprinter.

Finally, I took up msak007's suggestion to install the aboutconfig extension.  Six months ago, when I installed Thunderbird 1.5 I was warned against using extensions because they are difficult to get to work.  Needless to say, it did not work.  Now I am stuck with a situation that when I start Thunderbird for about 30 seconds there is a blinking icon while Thunderbird tries to install an extension in the extensions list which it cannot install.  I cannot use Thunderbird until after it gives up the installation attempt.  Deleting the .xpi file does not help.

For the record I am now using Debian 3.1r2 "Sarge".

---

### Post by xtalman on 2006-12-11
I just wanted to post that this guide was great!  The only problem I had was when I set the print.always boolean to true, I wasn't getting any indication of anything working.

I turned it to false, and was able to get the standard kprinter dialog and do everything I needed.

---

### Post by msak007 on 2006-12-11
**swimmerken**: I don't use Thunderbird anymore, but when I did the instructions I provided worked for it just as well as Firefox. I also never had any problems with extensions and personally used the about:config extension without any issues. I apologize if my instructions screwed up your installation, I would not have recommended the extension if I did not personally use it without any adverse effect. As far as NVU, I've never used that application so I can't help much there. I could not find anything on disabling xprint aside from disabling it at compile time, and I'm not sure if the version in the repos had it disabled. I also could not find anything on getting NVU to use anything but xprint, except random blurbs on the update logs about how the Linspire version calls kprinter. Sorry I couldn't be of much help.

> **xtalman said:**
> I just wanted to post that this guide was great!  The only problem I had was when I set the print.always boolean to true, I wasn't getting any indication of anything working.

I turned it to false, and was able to get the standard kprinter dialog and do everything I needed.

**xtalman**: Thanks for letting me know. It's odd that the print.always boolean was doing that, and disabling it shows kprinter. The whole purpose of adding that flag was so that it would suppress Firefox's own print dialog, and as a result go straight to kprinter. Can you post the output of the 3 lines I asked for several posts earlier?

---

### Post by karls0 on 2007-01-20
Hi msak007,
first of all, thank You for these instructions, they are great. Everything works fine in Firefox, but with Thunderbird I have much the same problem as xtalman. 

When I set 
print.always_print_silent    true
the behavior is like xtalman said - there are two windows "prepare print..." (or the like) and printing starts immediately without a printer-dialog to choose a printer.

If I set
print.always_print_silent    false
I get a print-dialog, but not the one from kprinter! The only printer to choose there is PostScript/default. I can print then, but it would be nice, if it worked like You described it earlier. 

In about:config I have the following:
print.print_command    lpr ${MOZ_PRINTER_NAME:+'-P'}${MOZ_PRINTER_NAME}
print.print_printer          CUPS/HPLJ1200hpijs
print.printer_PostScript/default.print_command        kprinter

tia
Karl

PS: I use Kubuntu 6.06 LTS, Thunderbird 1.5.0.9 and a LaserJet via CUPS.

---

### Post by KPingus on 2007-01-26
I am using Firefox 1.5.0.9 under Kubuntu and the how-to did not work at all for me. At no moment does kprinter come up. If I set always_print_silent to true, then Firefox prints right away to the default printer, and if I set it to false, the "regular" print dialog comes up.

Any ideas?

---

### Post by KPingus on 2007-01-29
Progress. Things are now working in Firefox 1.5.0.9. Things look especially spiffy with the Konquefox extension and the slick icons. Now that's integration!

The instructions got me nowhere for Thunderbird, where I run into the same problems as two previous posters. However, if you set print.always_print_silent to False, the usual Thunderbird dialog comes up, where only the default printer is available. If you click on 'Properties', change the command to 'kprinter' and hit 'Print', the kprinter dialog will come up.

This is a 2-step fix.

---

### Post by msak007 on 2007-01-29
Hey guys, sorry I haven't replied to your posts I haven't had much time lately. I've switched to KMail since I wrote this thread so haven't had a chance to test anything, but I'll give it a shot on my laptop later and post the results. 

**karls0** - Try the following and let me know if it helps you:

```
print.print_command    lpr ${MOZ_PRINTER_NAME:+'-P'}${MOZ_PRINTER_NAME}
```Replace with```
 print.print_command    kprinter
```It also looks like you're using an HP LaserJet 1200 - CUPS can get in the way if you want kprinter to be your default so add a boolean in about:config with the following value:

```
print.postscript.cups.enabled
``` and set its value to "False" to disable CUPS. You'll still be able to use your LJ1200 once kprinter pops up and you can choose it from there.

```
print.printer_PostScript/default.print_command        kprinter

``` This is fine, this is what will actually get kprinter to come up once you disable CUPS printing. It will force the default printer to be the PostScript/default printer, and since you've changed its output command to kprinter it should pop up. Please try the suggestions and let me know.

**KPingus** - Please try what I suggested above for Thunderbird and let me know if it helps you.

---

### Post by karls0 on 2007-01-31
Hi msak007,
thank You for your hints. I tried to set all parameters as You said.But it didn´t work - when I looked into the configuration after printing a page from the standard print-dialogue I noticed that 
print.printer_PostScript/default.print_command    had changed back to the original setting. I tried twice to change it, but it always came back to the original. 
Then I searched through the parameters and found two more places with the "lpr...." print-command. I changed them to "kprinter". Now I get the standard print-dialogue and after clicking on "Print" the kprinter dialogue opens.

Setting print.always_print_silent to true suppresses both print-dialogues (what I dont want). 

Please, could You give one more tip to reduce the count of print-dialogues :D ??
tia
Karl

---

### Post by Linookser on 2007-02-07
This works for me, when I go to File/Print it goes straight to the Kprinter after showing the progress bar.  But custom functionality in the kprinter dialog, like HTML Settings when printing from Konqueror, aren't there.  This limits functionality since features like Firefox's "Print Selection" are also no longer available.  There's still need for better integration of Firefox in KDE IMO, but interesting how-to, anyhow.

---

### Post by jpmac on 2007-04-19
Yes, I found the same problem.  I just changed the print.always_print_silent back to false, so I can print by selection.  It works, but it is a bit clumsy.

On that note, can anybody think of a more effective way to do this?

---

### Post by manducasexta on 2007-05-22
Thanks for describing what each step does. This solved my problem. Thanks!

---

### Post by johnrobert on 2007-09-14
Thank you for this tip! I just tried it on my new installation of Feisty on a G4 Powerbook, and it works fine. I really appreciate you taking the time to put this information on the forums. Thanks again! You rock!

---

### Post by Hasufin on 2007-10-09
> **msak007 said:**
> **swimmerken**: I don't use Thunderbird anymore, but when I did the instructions I provided worked for it just as well as Firefox. I also never had any problems with extensions and personally used the about:config extension without any issues. I apologize if my instructions screwed up your installation, I would not have recommended the extension if I did not personally use it without any adverse effect. As far as NVU, I've never used that application so I can't help much there. I could not find anything on disabling xprint aside from disabling it at compile time, and I'm not sure if the version in the repos had it disabled. I also could not find anything on getting NVU to use anything but xprint, except random blurbs on the update logs about how the Linspire version calls kprinter. Sorry I couldn't be of much help.



**xtalman**: Thanks for letting me know. It's odd that the print.always boolean was doing that, and disabling it shows kprinter. The whole purpose of adding that flag was so that it would suppress Firefox's own print dialog, and as a result go straight to kprinter. Can you post the output of the 3 lines I asked for several posts earlier?

I had the same problem -- by adding the print.always key to the about:config was broken.  I double & triple checked the settings.... but whatever reason when I printed, the dialog came up, processed & printed 100% and Kprinter never showed up.

For grins, I set it to false.. and tried.  The firefox print dialog came up, I clicked print.. and then Kprinter showed up.  I changed the print.always back to true....... and guess what?  It worked as advertised.  So fiddling with it was required.........

Thanks for the great guide!  Great comments folks!

BTW:  I am a Feisty User!

---

### Post by vange on 2007-11-02
mask007: I just applied your "global" fix for Firefox, and it just works. Thank you.

Is there a way to do it for Thunderbird globally on the system?

I am running Kubuntu 7.10

---

### Post by msak007 on 2007-11-02
> **vange said:**
> mask007: I just applied your "global" fix for Firefox, and it just works. Thank you.

Is there a way to do it for Thunderbird globally on the system?

I am running Kubuntu 7.10
Thanks, you're the first person that confirmed for me that the global fix worked. I already knew it worked on my machine, but nobody else let me know if it worked for them. As far as Thunderbird goes, I'll install it this weekend when I get some free time and try to figure out how to make it work the same way, and I'll clean up the first post a little to put the global fix as well as any updated instructions in there.

---

### Post by sneakypeteb on 2007-11-18
Works like a charm - thanks!

---

### Post by vange on 2007-11-19
A minor annoyance is, that you cannot print a selection. Anyone got a solution for that?

---

### Post by kruppe on 2008-03-12
> **msak007 said:**
> Thanks for letting me know it helped you. I was starting to wonder if I was the only person who found this useful.

Thanks so much - I have no idea why they don't use these as defaults - makes more sense.:guitar:

---

### Post by mmmeier on 2008-08-12
Many thanks to msak007 for the great tips! 

Does anyone else have the problem that the generated PDF-files 
are _not searchable_, neither in Acrobat Reader, nor kpdf, nor ...
pdf2text also does not work. 

Does anyone know if this is a Firefox-problem or a kprinter-problem 
and if there's a fix for it? 

Konqueror and the old Netscape on the other hand produce searchable 
PDF-files thru kprinter. 

Many thanks,
MM

---

### Post by pinx on 2008-09-01
Hi,

I'm using Kubuntu Hardy with KDE 4.1 and FF 3.0.1 (from the Ubuntu reps), and installed kdeprint (kprinter) manually (this works). Could someone verify if the proposed method works also for a similar setup? Because in my case I can't get it to work: Strangely, the postscript/default printer doesn't even exist. No change in the prefs file seems to affect the print menu that shows only the "Print To File" and "PDF" options.

---

### Post by craq on 2008-12-27
@pinx, did you figure out how to do this? I am also using Kubuntu Hardy, KDE 3.5 and Firefox 3 and also have no postscript print option (except via 'Print to File', which results in different options in the about:config menu). In addition to 'Print to File' and 'PDF' I also have 'kop' which is my default printer and doesn't work.

---

### Post by noBananas on 2009-01-27
In Firefox 3, you cannot access the KDE kprinter dialog.

However, you can apply a simple change in "about:config" that will make the "print to file" choice in the print dialog window default to pdf (rather than postcrpit) and will also set up a default directory and the file name of your choice.

For instructions, go to [http://forums.mozillazine.org/viewtopic.php?f=8&t=1010695]("http://forums.mozillazine.org/viewtopic.php?f=8&t=1010695") and scroll to the last post in this thread.

---

### Post by platinummonkey on 2010-04-09
[http://tamulug.tamu.edu/wiki/firefox_print_kerberos](http://tamulug.tamu.edu/wiki/firefox_print_kerberos)

this will still let your other programs print without double dialogs ;)

---

