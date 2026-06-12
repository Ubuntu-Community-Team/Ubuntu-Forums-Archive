---
title: "HOWTO: Install Brother MFC210C"
date: 2005-12-19
forum: Outdated Tutorials &amp; Tips
---

### Post by BobSongs on 2005-12-19
[FONT=Verdana]**[SIZE=4]A "how to" for the Brother MFC-210C printer.[/SIZE]**

[SIZE=1][SIZE=3][COLOR=DimGray][B] [COLOR=Red]>>>> THIS THREAD IS ABANDONED!! <<<<
If you want a more current thread, then click
this link: [MFC210C]("http://ubuntuforums.org/showthread.php?t=590793")[/COLOR][/B]
[B][COLOR=DarkRed][SIZE=2]
[/SIZE][/COLOR][/B][/COLOR][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=1][SIZE=3][COLOR=DimGray][B][COLOR=DarkRed][SIZE=2]* Author no longer uses the MFC-210C printer.
* This POST is NOT "up-to-date" (though answers are provided by kind forum members).
* Continue at your own risk.[/SIZE][/COLOR][/B][/COLOR][/SIZE][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][SIZE=3][COLOR=DimGray][B][COLOR=DarkRed][SIZE=2]
INK CARTRIDGE SAYS EMPTY? Click here: [BlackTape]("http://www.wisebread.com/how-to-refill-an-ink-cartridge-with-a-small-piece-of-tape")

[/SIZE][/COLOR][/B][/COLOR][/SIZE][/SIZE][/FONT][FONT=Verdana][SIZE=1][SIZE=3][COLOR=DimGray]**[COLOR=DarkRed][SIZE=2]NOTE TO THE ADMINS:[/SIZE][/COLOR]**[/COLOR][/SIZE][/SIZE][/FONT]
[FONT=Verdana][SIZE=1][SIZE=3][COLOR=DimGray][B][COLOR=DarkRed][SIZE=2]Many people monitor this thread. Delete this one if you so choose. However, some people are getting their questions answered.

[/SIZE][/COLOR][/B][/COLOR][/SIZE] [/SIZE] [/FONT][FONT=Verdana]________________________________[/FONT]
   [FONT=Verdana][SIZE=3]**MFC-215C**?[/SIZE][/FONT][FONT=Verdana][**Matchless**]("http://ubuntuforums.org/member.php?u=14308") [/FONT][FONT=Verdana]has worked very hard at putting together two tutorials to help you with your 215C:
[/FONT]
[LIST]
[*][FONT=Verdana][**click here**]("http://ubuntuforums.org/showthread.php?t=302960") if you're running Fiesty Fawn[/FONT]
[*][FONT=Verdana] [**click here**]("http://ubuntuforums.org/showthread.php?t=263047") if you're running Dapper/Edgy.[/FONT]
[/LIST]
[FONT=Verdana]________________________________[/FONT]
[FONT=Verdana]**[COLOR=Green]Edgy & Feisty[/COLOR]-specific instructions added,**[/FONT][FONT=Verdana] courtesy of **magean.**
[/FONT][FONT=Verdana]________________________________[/FONT]
[FONT=Verdana]**[SIZE=3]INSTALL SCRIPTS for [COLOR=Blue][B]DAPPER DRAKE**[/COLOR] **and** **[COLOR=SeaGreen]EDGY EFT/FEISTY FAWN[/COLOR]** (What works for Edgy... works for Feisty).[/SIZE][/B][/FONT][INDENT][FONT=Verdana][[Click here]("http://ubuntuforums.org/showthread.php?p=2277190#post2277190")] A big thanks goes to **guitara** and **googleninja **for their hard work and dedication. [/FONT][/INDENT][FONT=Verdana]________________________________[/FONT]
[FONT=Verdana] **[SIZE=3]Introduction[/SIZE]**[/FONT][INDENT][FONT=Verdana]Follow this step-by-step guide to get this low-cost Multi Function Centre working.

Do you have another Brother product? Don't give up hope. Some have reported success having followed this tutorial (see a partial list at the bottom of this post).

**Note**: This tutorial assumes:[/FONT]
[LIST]
[*][FONT=Verdana]Device: Brother MFC210C[/FONT]
[*][FONT=Verdana]Connection: USB direct from PC to Printer
[/FONT]
[*][FONT=Verdana]System: 32-bit Intel/AMD[/FONT]
[*][FONT=Verdana]Operating System: GNU/Linux Ubuntu ([/FONT][FONT=Verdana][COLOR=Blue]**Dapper Drake**[/COLOR][/FONT][FONT=Verdana]/[/FONT][FONT=Verdana][COLOR=SeaGreen]**Edgy Eft/Feisty Fawn**[/COLOR][/FONT][FONT=Verdana])[/FONT]
[/LIST]
[/INDENT][FONT=Verdana]________________________________[/FONT]
[FONT=Verdana]**[SIZE=3]About the color codes[/SIZE]**[/FONT][INDENT][FONT=Verdana]**[COLOR=SeaGreen]* Edgy Eft/Feisty Fawn[/COLOR]** (6.10 & 7.04)-specific instructions are in green.
**[COLOR=Blue]* Dapper Drake[/COLOR]** (6.06.1)-specific instructions are in blue.
[/FONT]   [FONT=Verdana]*** Standard black** text will be used where it applies to all.
******* Breezy, Hoary, Warty:** not supported.
[/FONT][/INDENT][FONT=Verdana][B][SIZE=3] 
_Preliminary procedures                                                     _[/SIZE][/B]

Create a folder on the desktop and name it **mfc210c**. Put all downloaded files in that folder.

[B][SIZE=3]
_ Step 1: Download from Brother                  _[/SIZE][/B]

[B][COLOR=Blue][COLOR=Black][[The CUPS wrapper]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc210c_1.0.0-1_i386.deb&lang=English_cups")]
[[The LPR Driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb&lang=English_lpr")][/COLOR]
[/COLOR][/B][/FONT][INDENT][FONT=Verdana][B]
For other Brother machines:[/B] Please make sure the appropriate drivers are downloaded. Check the Brother website for
[LPR Drivers]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html#de") and 
[CUPS Wrappers]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de").[/FONT][/INDENT][FONT=Verdana][B][SIZE=3]
_ Step 2: Install the C Shell_[/SIZE][/B][/FONT]
```
sudo aptitude install csh
```[INDENT][SIZE=2][FONT=Verdana]**I**[/FONT]**[FONT=Verdana]f this step fails because it returns the following error:[/FONT] **> [FONT=Courier New]E: Couldn't find package csh[/FONT][B][FONT=Verdana]follow the Ubuntu Guide instructions on [How To Add Extra Repositories]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories").[/FONT]

[/B][/SIZE][/INDENT][FONT=Verdana][SIZE=5]**:: TURN PRINTER [COLOR=Red]OFF[/COLOR] ::**[/SIZE][/FONT][FONT=Verdana]
:!: DO NOT SKIP THIS STEP OR THINGS GO TERRIBLY WRONG ](*,) 


_**[SIZE=3]Step 3: LPR Driver Install[/SIZE]**_[/FONT]
```
sudo mkdir /var/spool/lpd
``````
sudo mkdir /var/spool/lpd/[COLOR=Red]**MFC210C**[/COLOR] (**replace with your printer name**)
``````
sudo dpkg -i ~/Desktop/mfc210c/mfc210clpr-1.0.2-1.i386.deb
```[B][SIZE=3]
_[FONT=Verdana] Step 4: Install the CUPS Wrapper                  [/FONT]_[/SIZE][/B]
```
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
``````
sudo dpkg -i ~/Desktop/mfc210c/cupswrappermfc210c_1.0.0-1_i386.deb
```[B][SIZE=3]
_[FONT=Verdana]Finalization                                                    [/FONT]_[/SIZE][/B]  [FONT=Verdana][SIZE=5][B]

:: TURN PRINTER [COLOR=Green]ON[/COLOR] ::
[/B][/SIZE][/FONT]Please follow these steps. From the menu bar click:
[FONT=Verdana]
[B]System &#8594; Administration &#8594; Printing

[/B]Right-click the MFC210C and click &#8220;Properties&#8221;[/FONT]
[LIST]
[*][FONT=Verdana]**Connection Tab:** :!: [COLOR=Red]**Ensure local printer is connected**[/COLOR] (Printer Type: **Local Printer**) and (**Use a Detected Printer:** Brother MFC-210C)[/FONT]
[*][FONT=Verdana]**General Tab:** Here I rename 'MFC210C' to 'Brother Printer'. Let's the whole family know the printer they're selecting.[/FONT]
[*][FONT=Verdana]**Paper Tab:** Ensure your local paper size is selected.[/FONT]
[*][FONT=Verdana]**Advanced Tab:** Review the choices and make appropriate adjustments.[/FONT]
[*][FONT=Verdana]**From any tab:** Click "Print a test page" to confirm all works well.[/FONT]
[/LIST]
[FONT=Verdana][SIZE=4]**[COLOR=SeaGreen]Edgy/Feisty: [/COLOR]***[SIZE=2][COLOR=SeaGreen](thanks Magean)[/COLOR][/SIZE]*[/SIZE][/FONT] [COLOR=SeaGreen][FONT=Verdana]
If you got the error message[/FONT]> [FONT=Courier New]lpadmin:Unable to copy PPD file[/FONT]when installing the Wrapper do the following:

[FONT=Verdana][SIZE=2] Find out the device url[/SIZE][/FONT]```
lpinfo -v
```[FONT=Verdana]Read and "remember" the device url[/FONT]

[FONT=Verdana] (for example)[/FONT]> [FONT=Courier New]usb://Brother/MFC-210C[/FONT][FONT=Verdana]Find the name and path of the ppd file[/FONT]```
ls /usr/share/cups/model
```[FONT=Verdana]Read and remember the filename

(for example)[/FONT]> [FONT=Courier New]/usr/share/cups/model/brmfc210c_cups.ppd[/FONT][FONT=Verdana]Administer the printer
[/FONT]```
sudo lpadmin -p (printer name) -E -v (device url) -P (PPD file path and name)
```[FONT=Verdana](for example)
[/FONT] > [FONT=Courier New]sudo lpadmin -p MFC210C -E -v usb://Brother/MFC-210C -P /usr/share/cups/model/brmfc210c_cups.ppd[/FONT][FONT=Verdana]All done!

For printer options turn your browser of choice to
[/FONT]  [/COLOR][INDENT][FONT=Verdana][COLOR=SeaGreen][http://localhost:631/printers/](http://localhost:631/printers/) [/COLOR][/FONT] [/INDENT][FONT=Verdana][COLOR=SeaGreen](this requires local access)[/COLOR][/FONT][FONT=Verdana]     


**[SIZE=4]Fax Printing[/SIZE]**[/FONT][INDENT][FONT=Verdana]To print using the fax capabilities of the MFC the drivers must be downloaded and installed. This tutorial assumes the **mfc210c** folder is still on the desktop.[/FONT][/INDENT][FONT=Verdana][B][SIZE=3]
Step 1: Download from Brother[/SIZE][/B]

[/FONT]  [FONT=Verdana][COLOR=Black][B][[The Fax CUPS wrapper]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxcups-1.0.0-1.i386.deb&lang=English_gpl")]
[[The Fax LPR Driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxlpd-1.0.0-1.i386.deb&lang=English_lpr")][/B][/COLOR][/FONT]  [FONT=Verdana][SIZE=5][B]

:: TURN PRINTER [COLOR=Red]OFF[/COLOR] ::[/B][/SIZE][/FONT][FONT=Verdana]
:!: [/FONT][FONT=Verdana]DO NOT SKIP THIS STEP OR THINGS GO TERRIBLY WRONG[/FONT][FONT=Verdana] ](*,) 

[/FONT]  ```
sudo dpkg -i ~/Desktop/mfc210c/brmfcfaxlpd-1.0.0-1.i386.deb
``````
sudo dpkg -i ~/Desktop/mfc210c/brmfcfaxcups-1.0.0-1.i386.deb
```[FONT=Verdana][SIZE=5][B]

:: TURN PRINTER [COLOR=Green]ON[/COLOR] ::[/B][/SIZE][/FONT][FONT=Verdana]

**System &#8594; Administration &#8594; Printing**

Right-click the BRFAX and click &#8220;Properties&#8221;[/FONT]
[LIST]
[*][FONT=Verdana]**Connection Tab:** :!: Ensure local printer is connected (Printer Type: Local Printer) and (Use a Detected Printer: Brother MFC-210C -- If the printer is still off this step will be impossible to complete.)[/FONT]
[*][FONT=Verdana]**General Tab:** Here I rename 'BRFAX' to 'Brother Fax Machine'. Let's the whole family know which printer they're selecting.[/FONT]
[*][FONT=Verdana]**Paper Tab:** Ensure your local paper size is selected.[/FONT]
[*][FONT=Verdana]**Advanced Tab:** Review the choices and make appropriate adjustments. I use FINE for Quality.[/FONT]
[/LIST]
[FONT=Verdana]Click "Close". This box will not allow direct printing.

**[SIZE=4]Sending a Fax[/SIZE]**[/FONT][INDENT][FONT=Verdana]Thanks to **Matchless** for untangling this mess. "This printer is not used to print faxes directly. It is used by the 'brpcfax' utility script file. To send a fax, you must use the &#8220;brpcfax&#8221; utility to process your print jobs and you can only use a postscript file."[/FONT][/INDENT][INDENT][FONT=Verdana]Let's use GEdit to set this up.[/FONT][/INDENT][FONT=Verdana]**Applications &#8594; Accessories &#8594; Text Editor**[/FONT]
[LIST]
[*][FONT=Verdana]Type some text into Text Editor. (It's not necessary that it be important text. The file doesn't have to be faxed for this to work.)[/FONT]
[*][FONT=Verdana]From the menu bar click File &#8594; Print...[/FONT]
[*][FONT=Verdana]Under the **Print** tab click "Generic Postscript" as your printer selection.[/FONT]
[*][FONT=Verdana]Change "Location" from "lpr" to "File". This will let us print to file.[/FONT]
[*][FONT=Verdana]Click the "Save As" button to the right of "File" (it appears only when you select "File").[/FONT]
[*][FONT=Verdana]Name the file **faxtest.ps**. For **Save In Folder** choose Desktop (for convenience only&#8212;delete the file when you're done).[/FONT]
[*][FONT=Verdana]Click the Save button.[/FONT]
[*][FONT=Verdana]Click the Print button.[/FONT]
[/LIST]
[FONT=Verdana]Your document has been saved as file to your Desktop. Now let's finish Step 2.[/FONT]
[LIST]
[*][FONT=Verdana]Right-click the **faxtest.ps** file on your Desktop. In the context menu point to "Open With >". In the flyout menu click "Open with Other Application"[/FONT]
[*][FONT=Verdana]When the "Open With" box appears, click "Use a custom command at the bottom near the Cancel button. A small text field should appear.[/FONT]
[*][FONT=Verdana]Enter this into that field: **/usr/bin/brpcfax**[/FONT]
[*][FONT=Verdana]Complete the task by clicking Open.[/FONT]
[/LIST]
[FONT=Verdana]This should cause the Dial Pad to appear. You can close it as we're finished with it for the moment.

From this point forward this is how to send a fax:

a) Use &#8220;Print to file&#8221; from your application to generate a postscript file.
b) Right click the file (should end in .ps) and select &#8220;Open with&#8221; and click &#8220;brpcfax&#8221;.
c) When the dialup screen GUI comes up, enter fax number and click Send.


**[SIZE=4]Scanner Setup[/SIZE]**

**[SIZE=3]Preliminary procedures[/SIZE]**

[/FONT]         [FONT=Verdana][SIZE=5]**:: TURN PRINTER [COLOR=Red]OFF[/COLOR] ::**[/SIZE][/FONT][FONT=Verdana]
:!: [/FONT][FONT=Verdana]DO NOT SKIP THIS STEP OR THINGS GO TERRIBLY WRONG[/FONT][FONT=Verdana] ](*,) 


**[SIZE=3]Step 1: Download from Brother[/SIZE]**

For** [COLOR=Blue]Dapper Drake[/COLOR] **(6.06): **[[Sane Scanner Backend]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.1-0.i386.deb&lang=English_sane")]**
For** [COLOR=Green]Edgy/Feisty[/COLOR] **(6.10/7.04): [B][[Sane Scanner Backend]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.3-0.i386.deb&lang=English_sane")]

[/B][/FONT][INDENT][FONT=Verdana]For other Brother machines: Please make sure the appropriate drivers are downloaded. Check the Brother website for the [Scanner Backend]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html").[/FONT][/INDENT][FONT=Verdana]**Applications &#8594; Accessories &#8594; Terminal**


[/FONT]  ```
**[COLOR=Blue]sudo dpkg -i ~/Desktop/mfc210c/brscan2-0.2.1-0.i386.deb[/COLOR]**
```[FONT=Verdana][COLOR=Blue]The scanner should be installed.[/COLOR][/FONT]```
[COLOR=SeaGreen]**sudo dpkg -i ~/Desktop/mfc210c/brscan2-0.2.3-0.i386.deb**[/COLOR]
```[FONT=Verdana][COLOR=SeaGreen]Make scanner accessible to all users[/COLOR][/FONT]
```
[COLOR=SeaGreen]gksudo gedit /etc/udev/rules.d/45-libsane.rules[/COLOR]
```[FONT=Verdana][COLOR=SeaGreen]Add the following above the last row:[/COLOR][/FONT]
> [FONT=Courier New][COLOR=SeaGreen]#brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"[/COLOR][/FONT][FONT=Verdana][COLOR=SeaGreen]The last four rows should then look like:[/COLOR][/FONT]> [FONT=Courier New][COLOR=SeaGreen]#brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"

LABEL="libsane_rules_end"[/COLOR][/FONT] [FONT=Verdana][COLOR=SeaGreen]Restart the OS.[/COLOR][/FONT]


[FONT=Verdana]**[SIZE=3]Step 3: Installing XSane[/SIZE]**

To use the scanner requires that Ubuntu's scanner software be installed. Copy the following code into the Terminal:[/FONT] 
```
sudo aptitude install sane xsane libsane sane-utils
```[B][SIZE=3]
[FONT=Verdana]
Finalizing The Setup[/FONT][/SIZE][/B]  [FONT=Verdana][SIZE=5][B]

:: TURN PRINTER [COLOR=Green]ON[/COLOR] ::[/B][/SIZE][/FONT][FONT=Verdana]
[B][SIZE=3] Verify the install with XSane
[/SIZE][/B][B]
Applications &#8594; Graphics &#8594; XSane Image Scanning Program

[/B][B][SIZE=3]
Setup Complete[/SIZE][/B]

Move the setup folder from your desktop to the trash if you so desire, or to some other location in the file system.

[B][SIZE=4]
Network Installation[/SIZE][/B][/FONT][INDENT][FONT=Verdana]**Please note:** Contributions to help with network setups are detailed below. I do not have the MFC as an independent part of the network so I cannot test the following instructions. However these links are offered in hope of problem-free configuration.[/FONT][/INDENT][FONT=Verdana]**ubu69** has had success with a network setup. He's using a Debian system and believes this should prove helpful [[click here]("http://www.ubuntuforums.org/showpost.php?p=644004&postcount=21")].

**shawndoggie** notes success with the MFC attached to an XP box [[click here]("http://www.ubuntuforums.org/showpost.php?p=719307&postcount=40")].

**stalefries** has put together a nicely detailed howto in this thread. Network scanning! I just love the layout. [[click here]("http://www.ubuntuforums.org/showpost.php?p=935120&postcount=83")]

[B][SIZE=4]
Other Brother Products[/SIZE][/B][/FONT][INDENT][FONT=Verdana]**Please note:** If you have a different Brother product don't go away dejected. There may be hope. Here's a list of some related success stories. With a bit of tweaking it seems this tutorial has proven helpful.[/FONT][/INDENT][FONT=Verdana]**Jose Catre-Vandis** has a mini tutorial on the for the DCP-540CN in an Edgy HowTo [[click here]("http://www.ubuntuforums.org/showthread.php?p=2275292#post2275292")]

**Gray.** notes success with the MFC-620CN [[click here]("http://ubuntuforums.org/showpost.php?p=629121&postcount=19")]

**ubu69** notes success with the MFC-420CN in Debian [[click here]("http://ubuntuforums.org/showpost.php?p=644004&postcount=21")]

**crhooker** notes success with the MFC-3220C [[click here]("http://ubuntuforums.org/showpost.php?p=686523&postcount=32")]

**shawndoggy** notes success with the MFC-5440CN [[click here]("http://ubuntuforums.org/showpost.php?p=719307&postcount=40")]

**thedavis** notes success with the DCP-115C [[click here]("http://ubuntuforums.org/showpost.php?p=761313&postcount=47")]

**Mack1** notes success with the MFC-425CN [[click here]("http://ubuntuforums.org/showpost.php?p=772013&postcount=52")]

**bigken** notes success with the MFC-3820CN [[click here]("http://ubuntuforums.org/showpost.php?p=778035&postcount=56")]

**Bucanero** notes success with the MFC-5440N [[click here]("http://ubuntuforums.org/showpost.php?p=904967&postcount=73")]

**Jasman** and **Boelcke** both note success with the Brother HL-2040
[[click here]("http://www.ubuntuforums.org/showpost.php?p=1054771&postcount=131")] and [[click here]("http://www.ubuntuforums.org/showpost.php?p=1066795&postcount=133")]

[B][SIZE=3]
Other distros:[/SIZE][/B]

**bigken** notes success on SuSE 10.0 [[click here]("http://ubuntuforums.org/showpost.php?p=935744&postcount=85")]


_________________________

Found an error? Lemme know. Errors will be replaced with your astute observations and you'll be credited.

Got a question? I'll explain the best I can.

History: This tutorial was designed for Ubuntu/Edubuntu (Breezy, then updated for Dapper) to help me remember what steps I took in the first place. It exploded with the help of posters and onlookers like you. Thanks!!

**Xubuntu/Kubuntu:**
It may not work with other Ubuntu-based releases (Xubuntu, Kubuntu, etc.) - searching for a Kubuntu/Xubuntu-related tutorial recommended.

Variations from the Brother website instructions reflect the difference between Ubuntu and a pure Debian system.

**Brother**® is a Registered Trademark.

[/FONT]                               [FONT=Verdana][COLOR=Gray][SIZE=1](This HOWTO comes with absolutely no warranty, to the extent permitted by applicable law. However, the author will return on a regular basis to ensure the Brother files are still available and up-to-date and that the tutorial looks prettier and prettier.)[/SIZE][/COLOR][/FONT]

---

### Post by Nightwind on 2005-12-24
Quick question, since my brother MFC210C is set up as a network printer, not attached to any machine, will these instructions work or will I need to do something different?

---

### Post by BobSongs on 2005-12-24
[quote=Nightwind]Quick question, since my brother MFC210C is set up as a network printer, not attached to any machine, will these instructions work or will I need to do something different?[/quote]

[FONT=Verdana] Excellent question, Nightwind. If you've got the printer correctly installed on a network box then I suppose it won't hurt at all to have the drivers set up on your machine.

I'm a new Ubuntu user myself. In the Windows world you need the drivers set up on all PCs that will access the network printer(s). At this point I haven't quite figured out how to "share" my printer on my LAN (not that I'm in a hurry: my three-year-old son would end up printing every other image... in colour... from each TuxPaint screen he'd create... not cool). Once I figure that out I'll let you know.

Keep the questions coming.[/FONT]  

:smile:

---

### Post by Nightwind on 2005-12-24
[QUOTE=BobSongs]Excellent question, Nightwind. If you've got the printer correctly installed on a network box then I suppose it won't hurt at all to have the drivers set up on your machine.

I'm a new Ubuntu user muhself. In the Windows world you need the drivers set up on all PCs that will access the network printer(s). At this point I haven't quite figured out how to "share" my printer on my LAN (not that I'm in a hurry: my three-year-old son would end up printing every other screen... in colour... from each TuxPaint screen he'd create... not cool). Once I figure that out I'll let you know.

Keep them questions coming.

:smile:[/QUOTE]
Well I can say there is something missing, I followed the instructions to the letter, **thanks** for being so straighforward  with them I wish all the instructions were as clear. I can see the printer, but cannot print to the printer. I told  it to do a test page but that failed. There was no error message. 
So I am trying to figure it out. If you have any clues for a newborn newbie please advise.
Thanks again 
Trish

---

### Post by Nightwind on 2005-12-24
[QUOTE=Nightwind]Well I can say there is something missing, I followed the instructions to the letter, **thanks** for being so straighforward  with them I wish all the instructions were as clear. I can see the printer, but cannot print to the printer. I told  it to do a test page but that failed. There was no error message. 
So I am trying to figure it out. If you have any clues for a newborn newbie please advise.
Thanks again 
Trish[/QUOTE]
One thing I forgot to mention, I have 6 of the "W machines as well as 1 IMac, plus an Intergraph server, everything else is seeing and using the printer at this point. I did manage to share an HP printer that is phsically installed on a Win XP Pro box. So that was good.

---

### Post by BobSongs on 2005-12-24
[quote=Nightwind]One thing I forgot to mention, I have 6 of the "W machines as well as 1 IMac, plus an Intergraph server, everything else is seeing and using the printer at this point. I did manage to share an HP printer that is physically installed on a Win XP Pro box. So that was good.[/quote]

[FONT=Verdana]Yeah. Sharing a printer on a Windows XP box is fairly easy. It think right-clicking it and selecting "Share" is about how complex it gets.

Okay. Let me get to work investigating. I'll "share" this printer on my PC and see if I can get it printing. Then I'll get back to you asap.

[quote=Nightwind]thanks for being so straighforward with them I wish all the instructions were as clear.[/quote]

:smile: Thank you, thank you. I've had my hand held in the past in areas where I was completely lost. I've also had vague & ambiguous instructions. I know which I prefer. ;) I don't feel insulted in the least to have a clear set of instructions where some part of it seems a bit "overdone" in its simplicity. The tutorial was done for the uber new user to feel quite at home.[/font]

---

### Post by BobSongs on 2005-12-24
[quote=Nightwind]<snip> I can see the printer, but cannot print to the printer. I told  it to do a test page but that failed. There was no error message. 
So I am trying to figure it out. If you have any clues for a newborn newbie please advise.
Thanks again 
Trish</snip>[/quote]

[FONT=Verdana]Yes: this tutorial is obviously for the MFC210C attached directly to the PC in question. Your ability to see the printer and yet not be able to print to feels like it might be just a bit beyond my abilities at the moment.

I saw [this link]("http://gerona.gov.ph/davidjr/?p=57") in another thread, but I believe that allows for Ubuntu to Ubuntu printing, and not necessarily through a server.

Which box is your printer connected to? Or is it connected directly to the server? (Okay. I'm stalling. But I'm still investigating.)[/font]

---

### Post by Nightwind on 2005-12-25
Hi Merry Christmas! 
Stalling is ok I have learned to do that myself. It's not attached to any machine. It's networked in from the switch. Network setup is as follows.
Sat modem/router to switch CAT 5 to all the units. Really simple set up.  
All the Windows boxes have the software installed and do not share per say the printer.
The server does not print to it or any other printer (have 3) as it's a SME 6.5 (Linux) box, Raid 0 set up as a file server/backup machine that I am STILL working on. That's another long story.](*,)  It might become a Ubuntu server before long if I can't get the raid issue corrected. I will check out the link and report back. 
One more ?:confused:  Is there a simple way to install any type of driver or does each flavor require it's own little installation gig? So much to learn so little brain power.

---

### Post by BobSongs on 2005-12-26
[FONT=Verdana][quote=Nightwind]<snip>One more ?:confused:  Is there a simple way to install any type of driver or does each flavor require it's own little installation gig? So much to learn so little brain power.</snip>[/quote]
Depends on how old each printer is.  Before buying equipment for your machines you may wish to investigate whether they are Linux friendly. In my mind running Ubuntu is a bit like running a Mac in terms of what I buy.

My Logitech Clicksmart 820 completely locks my PC when I try to do anything more than copy out the photos. Same with the MFC210C's scanner features. But I bought them before doing any investigation. At that time I wasn't as committed to Linux as I am now.

In future I'll be much more careful. If it isn't very Linux compatible... I'll keep hunting.

Meanwhile, have you tried this on the Ubuntu box?
[quote=http://gerona.gov.ph/davidjr/?p=57] (Note, this link is no longer valid. **[DavidJr's blog is now here]("http://teqnix.blogspot.com/")**.)

On the Ubuntu or Linux boxes where you want to share your printer, open to edit /etc/cups/client.conf:

```
sudo gedit /etc/cups/client.conf
```And add the following:[/FONT]     [INDENT][FONT=Verdana]ServerName hostname (hostname or IP of the printer server)[/FONT][/INDENT][FONT=Verdana]Once this is all setup, you should be able to go to: System -> Administration -> Printing and in the top tool bar you’ll see: Global Settings. You’ll want to make sure the following is checked:

[/FONT]  [FONT=Verdana]Detect LAN Printers

On the Windows boxes, just add the printer server as you normally do.

To make your printer browseable in a LAN network, edit your /etc/cups/cupsd-browsing.conf:

```
sudo gedit /etc/cups/cupsd-browsing.conf
```Simply replace the word “Off” with “On” (without the “”), don’t worry…that file has only one line so you won’t ever have difficulties finding it. I guess you have to do a “sudo /etc/init.d/cupsys restart” after this. :)

So that’s it![/quote][/FONT]

---

### Post by Nightwind on 2005-12-27
[QUOTE=BobSongs]Depends on how old each printer is.  Before buying equipment for your machines you may wish to investigate whether they are Linux friendly. In my mind running Ubuntu is a bit like running a Mac in terms of what I buy.

My Logitech Clicksmart 820 completely locks my PC when I try to do anything more than copy out the photos. Same with the MFC210C's scanner features. But I bought them before doing any investigation. At that time I wasn't as committed to Linux as I am now.

In future I'll be much more careful. If it isn't very Linux compatible... I'll keep hunting.

Meanwhile, have you tried this on the Ubuntu box?[/QUOTE]
Hi there!
All the printers/copiers here are a year old or less. 3 of them. I was asking not just about printer drivers, but  ALL drivers and  programs in general. Is there a hard fast rule on that?
I read that post and it would probably work. I'm going to try it, I'll let you know how it goes. I was going to attach the brother to the 5.10 box physically just for the heck it , but decided I really didn't want to mess with the layout here. Printers are in a case that's all printers, computers are EVERYWHERE.
I figured out that I was going to have to set up a server to handle this any way for the time being.The one server I have setup is a toy really, just to learn on. My S.O want's it short and to the point, no stress. So that's what I'll do. He's not the adventurous type when it comes to changing things except he wants me to build a system to handle server duties as well as run the cameras outside and the media here. That will be an adventure, prob take a year as slow as I am. Pray for me. I think it's time for a UNIX class.

---

### Post by BobSongs on 2005-12-29
[quote=Nightwind]Hi there!
All the printers/copiers here are a year old or less. 3 of them. I was asking not just about printer drivers, but  ALL drivers and  programs in general. Is there a hard fast rule on that?[/quote]
[FONT=Verdana]Whew! Good question. I've gotten on the Linux bandwagon less than a month ago. I am seriously in need of courses. You can only learn so much from re-installing Linux and then running everyone else's scripts and stuff.[/font]
[quote=Nightwind]I figured out that I was going to have to set up a server to handle this any way for the time being. The one server I have setup is a toy really, just to learn on. My S.O want's it short and to the point, no stress. So that's what I'll do. He's not the adventurous type when it comes to changing things except he wants me to build a system to handle server duties as well as run the cameras outside and the media here. That will be an adventure, prob take a year as slow as I am. Pray for me. I think it's time for a UNIX class.[/quote]
[FONT=Verdana]Time spent learning Unix is useful even if you apply it to XP or Apple's O/S X.

Let me know if that link is helpful to you. I applied it on my system and now PC2 prints through PC1 to the MFC210C without any bugs.

I wish you success. My prayers are with you. Army? Or Salvation Army?[/font]

---

### Post by Nightwind on 2005-12-30
Hi Ya!
As soon as we get these other 7 computers out of the way and in with the other 40 I will attack this with a vengeance. I'm going to redo the whole network here and attempt to get all the boxes talking to all the printers through the server.
This should be interesting to say the least.
I learn best by doing, which in this case requires classes as there is no one around here that uses UNIX/Linux. The forums are a great tool and I have learned tons from reading on them as well as the on-line Linux tutorials. I've had a Linux distro before but was so frustrated by the lack of response on the forums that I just dropped it. It has matured greatly in the past few years. I'll let you know if that link works here.

---

### Post by AllenM on 2005-12-31
I aaam using kde desktop.  My printer is now working in Linux.  Your instructions were esier to read and follow than Brothers.  Thank you for your help.

---

### Post by fishfillet on 2006-01-01
I just wanna sincerely thank you Bob for referring to my ubuntu printer sharing how-to and I hope more ideas could come up from it.

[QUOTE=BobSongs]Yes: this tutorial is obviously for the MFC210C attached directly to the PC in question. Your ability to see the printer and yet not be able to print to feels like it might be just a bit beyond my abilities at the moment.

I saw [this link]("http://gerona.gov.ph/davidjr/?p=57") in another thread, but I believe that allows for Ubuntu to Ubuntu printing, and not necessarily through a server.

Which box is your printer connected to? Or is it connected directly to the server? (Okay. I'm stalling. But I'm still investigating.)[/QUOTE]

---

### Post by BobSongs on 2006-01-02
[quote=Nightwind]<snip>I've had a Linux distro before but was so frustrated by the lack of response on the forums that I just dropped it. It has matured greatly in the past few years. I'll let you know if that link works here.</snip>[/quote][FONT=Verdana]This particular forum is very friendly to new users. I hear this is becoming more common in regard to other forums.

After you return from your network surgery let us know how well the Ubuntu box prints on the network. If you're still having problems let's create a brand new thread in the Networking forum. When you arrive at a solution we'll link this thread to it.[/font]

---

### Post by Nightwind on 2006-01-02
Originally Posted by BobSongs

<snip>This particular forum is very friendly to new users. I hear this is becoming more common in regard to other forums. After you return from your network surgery let us know how well the Ubuntu box prints on the network. If you're still having problems let's create a brand new thread in the Networking forum. When you arrive at a solution we'll link this thread to it.</snip>

Hi and thanks I'll do that. We are still working on getting the other units moved, I don't know what's heavier the servers or the "21 monitors.

---

### Post by BobSongs on 2006-01-02
[quote=fishfillet]I just wanna sincerely thank you Bob for referring to my ubuntu printer sharing how-to and I hope more ideas could come up from it.[/quote]
[FONT=Verdana]Hey dude: no problem. I kinda enjoy reading your pages. I've even modified my desktop look based on your suggestions.[/font]

---

### Post by angrykeyboarder on 2006-01-03
> **BobSongs]**[SIZE=4]A "how to" for the Brother MFC210C printer.[/SIZE]**

**[SIZE=3]Introduction[/SIZE]**
Setting up a Brother MFC210C might appear a bit daunting for a new Ubuntu user. Locating the drivers alone is a challenge (they're *not* available on the Brother setup CD). And Brother's ambiguous instructions may leave you tempted to abandon Ubuntu.

For those of us who have this low-cost Multi Function Centre and have not been able to use it, here's a step-by-step instruction set to get it printing. A tutorial on how to get the scanner features going is welcome.

**[SIZE=3]Preliminary procedures[/SIZE]**
Create a folder on your desktop and call it **mfc210c**:[LIST]
[*]Right-click the desktop and click **Create Folder** in the context menu
[*]Name it **mfc210c** (in lower case, this is important)[/LIST]**[SIZE=3]Step 1: Download from Brother[/SIZE]**
Click each of the following links. Click **I Accept** when the browser loads the page:[LIST]
[*][The CUPS wrapper]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc210c_1.0.0-1_i386.deb&lang=English_cups")
[*][The LPR Driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb&lang=English_lpr")[/LIST][INDENT]**Note**: The browser will ask if you wish to open or download the file. Don't open it. Download and save it in the **mfc210c** folder on the desktop.[/INDENT]**[SIZE=3]Step 2: Install the C Shell[/SIZE]**
Ubuntu does not come with the C shell pre-installed. It is necessary for this installation. The rest of the setup requires an open Terminal.[INDENT]**Applications &#8594 said:**
> and enter the following (or copy the following command, paste it in and hit Enter):

```
sudo apt-get install csh
``` This command will require your password.

Don't close the Terminal. We'll need it again.


**[SIZE=3]Step 3: Install the LPR Driver[/SIZE]**
Enter the following commands into the Terminal:

```
sudo mkdir /var/spool/lpd
``` ```
sudo mkdir /var/spool/lpd/MFC210C
``` ```
sudo dpkg -i ~/Desktop/mfc210c/mfc210clpr-1.0.2-1.i386.deb
```[INDENT]**Note:** this tutorial is designed with the idea that both downloaded files are in the **mfc210c** folder on the desktop. The last command above will fail otherwise.[/INDENT]**[SIZE=3]Step 4: Install the CUPS Wrapper[/SIZE]**
Enter the following commands into the Terminal:

```
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
``` ```
sudo dpkg -i ~/Desktop/mfc210c/cupswrappermfc210c_1.0.0-1_i386.deb
``` 
**[SIZE=3]Finalization[/SIZE]**
Open the printer panel to ensure the MFC210C is installed.[INDENT]**System &#8594; Administration &#8594; Printing**[/INDENT]Right-click the printer and click “Properties”.[LIST]
[*]Print a test page from the General tab.
[*]Click the Paper tab and adjust the paper size accordingly, possibly replacing A4 with Letter.
[*]Review the choices under the Advanced tab and make adjustments.[/LIST]_________________________

If you encounter an error in these instructions or added several steps to make it more complete, please post your findings/additions and appropriate modifications will be made.

Explanations as to the above procedures are available upon request: the steps outlined above have been modified and expanded from those offered at the Brother website. Brother is a registered trademark.

[SIZE=1][COLOR=Silver](This HOWTO comes with absolutely no warranty. to the extent permitted by applicable law. However, the author will return on a regular basis to ensure the Brother files are still available and up-to-date.)[/COLOR][/SIZE] 
***Where*** did you find this information? I was beginning to think that Ubuntu users didn't use printers, period, let alone a Brother MFC....

Now I'm off to see if I can adapt these to my shiny new [Brother 7820N MFC]("http://www.brother-usa.com/mfc/mfc_detail_AREA=MFC_1&PRODUCTID=MFC7820N.aspx")....

I got it for Christmas and it's gotten very little use since I've been stumped as to how to get it working with Ubuntu.

---

### Post by Gray. on 2006-01-05
These steps worked for the MFC-620CN. I was stuck on one part with the error ```
/etc/init.d/cups: Command not found
``` then the symbolic link fixed that up.

*EDIT* If you Google for Brother Linux Drivers, it should be the first result.

---

### Post by BobSongs on 2006-01-08
[quote=angrykeyboarder]<snip>***Where*** did you find this information? I was beginning to think that Ubuntu users didn't use printers, period, let alone a Brother MFC....</snip>[/quote][FONT=Verdana]It's a basic modification of the [Brother website]("http://solutions.brother.com/linux/en_us/")'s instructions. My first attempt to install the drivers produced errors. I figured it was because the drivers were designed for a pure Debian system. I decided not to panic and run to this forum for help. I knew I'd be asked what I had tried up to this point. Saying "Not much" wasn't going to make anybody happy.

So I carefully reviewed each error output. (This is where Linux shines: error details.) I noted what went wrong and made the appropriate modifications (create a folder, create a link...). Eventually the printer just worked.

Instead of posting a thread asking what to do, I posted one explaining what to do. :-D[/font]

---

### Post by ubu69 on 2006-01-10
Thank you for the hand-holding. With a combination of your tutorial and Brother's instructions, I was able to set up my new printer (MFC420CN). While I'm using straight Debian, the steps were the same. 

I figured out how to get the printer to just be on the network (not attached to a print server). This will only work with models that have a built-in ethernet port (perhaps this howto should be expanded to cover installing Brother drivers in a general sense).

-To start, you'll need to know the IP address of the printer. The printer can tell you this (check out the instruction booklet as the command combinations may be different for different models.) 

-Follow the previous instructions given in this thread. -Open your browser to CUPS <http://localhost:631/>. Click "Manage Printers." You may have to have root powers to accomplish this. 

-If everything went well, you should see your printer in the list. 

-Select "Modify Printer." The important step is to select the device for the printer. Choose "LPD/LPR Host or Printer." 

-In the next step you enter lpd://xxx.xxx.xxx.xxx in the window (where the xxx's are the printer's IP address). 

-Send it a test page. You can configure paper size from CUPS (it seems to default to A4). 

-From here you can set your print manager to use CUPS if you so desire and it will also print on the network. 

If these instructions aren't clear, I'll do my best to clear them up. It's late and I stayed up most of the night trying to figure this out.

---

### Post by BobSongs on 2006-01-10
[FONT=Verdana]> **ubu69]Thank you for the hand-holding.[/quote]Alright! Don't forget to rate the thread.  said:**
> If these instructions aren't clear, I'll do my best to clear them up. It's late and I stayed up most of the night trying to figure this out.Feel free to clean up the tutorial and add it for our "pure" Debian buddies, ubu69. Of course, take the time to recover. Model it after my tutorial and this thread'll rate 6 stars on 5. :D[/font]

---

### Post by Lunixfanboy on 2006-01-13
And now, for the scanner portion of the MFC210C.

1. Go to [http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html") to obtain the sane scanner backend. You will need the brscan2 .deb package. Save same into directory of your choice (Downloads on my machine).

2. Open terminal, cd into directory containing brscan2 .deb package.

3. sudo dpkg -i brscan2-0.0.1-0.i386.deb

4. cd /etc/hotplug/usb

5. sudo vi libsane.scannermap

6. Look for one of the two lines containing Brother (which look like this:  # Brother|MFC 5100C). This will be followed by a line which reads  libusbscanner             0x0003      0x04f9   0x1029 followed by more hexadecimal values. We are only interested in the second and third ones {the ones right after the 0x0003}. Change the 0x1029 to read 0x0161. 

7. Save and exit vi.

8. Run sane-find-scanner | grep usb. It should report  found USB scanner (vendor=0x04f9, product=0x0161) at libusb:001:002 (the values after libusb might be different, depending upon where in your USB chain you have the scanner connected.)

9. Open Xsane and scan to your hearts' content.

---

### Post by massong on 2006-01-14
Hi, first off - thank you, this is an excellent guide.

I am however running into a small problem at this step:

```
sudo dpkg -i ~/Desktop/mfc210c/mfc210clpr-1.0.2-1.i386.deb
```

I have followed all other steps to the letter as far as I can tell, when I run the above command I get the following output:

```

(Reading database ... 74840 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.0-1 (using .../cupswrappermfc210c_1.0.0-1_i386.deb) ...
lpadmin: Unable to connect to server: Connection refused
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
lpadmin: Unable to connect to server: Connection refused

```

Incidentally, when I try to go to System / Administration / Printer I also get the error "The CUPS Server could not be contacted"

So, it seems I the CUPS server is not running, however I am not sure how to start it, if that is indeed that problem.

Any help would be appreciated :) 

Gary

PS: ubuntu ROCKS!!!

---

### Post by massong on 2006-01-15
Before I actually tried to add my printer through system / administration / printing I edited the client.conf file as indicated in your email below (sudo gedit /etc/cups/client.conf) and placed the ServerName as the name of the remote PC with my MFC210 on it.

Doing this ; that computer isn't running a CUPS Server and that's why I was getting my error.

I misread your message originally Bob, re-reading this now I understand I would edit this file if my Brother MFC210 was locally attached to my linux box and I wanted to share it on the network, which is not the case.

After I commented the ServerName line back out, I was able to run the System/Administration/Printing command and add my network printer with zero problems.

I printed out a quick test page and it looks perfect.  Have I mentioned that ubunut rocks?  I've never been able to accomplish so much with any other linux Distrobution, I'm dang near ready to make the switch!!! 

Gary


[QUOTE=BobSongs]Depends on how old each printer is.  Before buying equipment for your machines you may wish to investigate whether they are Linux friendly. In my mind running Ubuntu is a bit like running a Mac in terms of what I buy.

My Logitech Clicksmart 820 completely locks my PC when I try to do anything more than copy out the photos. Same with the MFC210C's scanner features. But I bought them before doing any investigation. At that time I wasn't as committed to Linux as I am now.

In future I'll be much more careful. If it isn't very Linux compatible... I'll keep hunting.

Meanwhile, have you tried this on the Ubuntu box?[/QUOTE]

---

### Post by BobSongs on 2006-01-17
[FONT=Verdana][quote=massong]<snip>I printed out a quick test page and it looks perfect.  Have I mentioned that Ubuntu rocks?  I've never been able to accomplish so much with any other linux Distrobution, I'm dang near ready to make the switch!!!</snip>[/quote]As a PC repair person I have begun to direct my customers to Ubuntu. I give them a level deal. It's not perfect. But just as there are trade-offs in Ubuntu, there are trade-offs in XP. Let's not kid ourselves. Climb on board, even if it's your 2nd O/S.[/FONT]

---

### Post by BobSongs on 2006-01-17
[FONT=Verdana][quote=Lunixfanboy]<snip>And now, for the scanner portion of the MFC210C.</snip>[/quote]Whoa! Excellent!! Giving it a try now. Many thanks for posting this. Job well done.[/font]

---

### Post by BobSongs on 2006-01-17
[FONT=Verdana][quote=Lunixfanboy]And now, for the scanner portion of the MFC210C.[/quote]Woot! It works! It works! Glory and thanks to God for sending you along to improve this tutorial.

I have added it to the main tutorial crediting you for your generous addition.[/font]

---

### Post by crhooker on 2006-01-19
BobSongs,

I have a Brother MFC3220C which is probably very close to your model. I have read your HowTo (excellent, thanks by the way) and would like to try it but before doing so I am hoping to make sure it does not mess up what I had already done.

Ubuntu found and correctly identified my model, the driver list however did not. I selected the one it reccomended and tried to print out a test page, the job queue recieved the job and apparently processed but nothing came out.

Should I perform the steps for your install after getting the right drivers for my printer (I actually think they are the same as I have gone to the Brother site but I am apparently not smart enough to understand what they are telling me to do - same thing with linuxprinting.org too)?

Thanks.

carl

---

### Post by BobSongs on 2006-01-19
[FONT=Verdana]Sorry I didn't get to your post sooner, Carl. Today's band practice day.

First, try using Google for the Brother Linux drivers. Brother will give instructions on how to install them. What I did was take their tutorial and try each step noting any errors. At one point the error stated a certain folder did not exist. So my instructions indicate the creation of a seemingly random folder. The setup then complained that it could not start/stop the 'cups' server. So when I looked in the folder I  found a file named 'cupsys'. So I give instructions on creating a symbolic link to 'cupsys' named 'cups'. All worked fine.

You see: it was very, very basic. Careful noting of what went wrong followed by a tweak here or there that Ubuntu needed in particular. Once that was in place the install worked better and better until it reported no flaws.

I would encourage you to try the same. Download and try it out using Brother's somewhat flawed instructions. Tweak as you go and you'll be ready to create your own "How-To". If you liked my tutorial (yeah, yeah: lots of hand holding... but I'm not ashamed of gearing this for the absolute beginner ;)), please add one for your printer too.

I am no way a guru. Utter newbie. I've got lots of Win/DOS experience that is very helpful at times. But a careful perusal of my tutorial will show that it's as basic as you can get. No real radical moves there at all, other than the symbolic link, and I got help for that.[/FONT]

---

### Post by crhooker on 2006-01-20
Thanks for taking the time. I will start out with your system and give it a whirl. When I looked at the Brother site a few days ago it seems to me the drivers for my printers are the same as for yours. If so and it works well I will get back to you with any tweaks I might have made and you can update your HowTo with my printer model.

Thanks again.

carl

---

### Post by crhooker on 2006-01-27
bobsongs,

YOU ARE THE MAN!  \\:D/ 

I have the MFC3220C as I said in earlier posts. I downloaded the proper drivers from the Brother site, followed your directions to the letter, of course I called my folder mfc3220c and altered the files to run to install the drivers. And, hello, out comes the test page. Thanks, I will move on to your scanner install next. I also obtained fax drivers from Brother and may even take a stab at them.

I did notice that the setup was to network printer, not being sure what that was about I clicked the local button, tried another test page and it worked as well. If you know the difference I would appreaciate some insight.

Now that you have solved my printer issue how about taking a stab at my webcam?? :-D

---

### Post by BobSongs on 2006-01-29
[FONT=Verdana][quote=crhooker]bobsongs,

YOU ARE THE MAN!  \\:D/ 

I have the MFC3220C as I said in earlier posts. I downloaded the proper drivers from the Brother site, followed your directions to the letter, of course I called my folder mfc3220c and altered the files to run to install the drivers. And, hello, out comes the test page. Thanks, I will move on to your scanner install next. I also obtained fax drivers from Brother and may even take a stab at them.

I did notice that the setup was to network printer, not being sure what that was about I clicked the local button, tried another test page and it worked as well. If you know the difference I would appreaciate some insight.

Now that you have solved my printer issue how about taking a stab at my webcam?? :-D[/quote]

:D Love it. I'd like to see **my** webcam going! It's a Logitech Clicksmart 820. I can download photos from it, no problem. But the moment I try to use it as a webcam my PC locks right down to the mouse movement. I'm sure it is a matter of a simple tweak as in the scanner tutorial. A number here, a small file there and boom: it works. But nothing yet.

**Lunixfanboy**'s tutorial worked fine for my scanner.

:)[/FONT]

---

### Post by LxP on 2006-01-29
Thank you very much for your efforts BobSongs. Thanks also to ubu69 for the useful information on getting a standalone network printer to function (i.e. one connected only to a hub/switch/router and not directly to any computer).

I am attempting to set up my router-connected Brother MFC410CN to print from Ubuntu and I am close; printing of test pages does not work however.

I think that the problem is that I can't modify CUPS settings through its web interface; it is disabled under Ubuntu 'for security reasons' and my attempts to enable it have been fruitless.

It's obvious that I want to select Network Printer from the Connection tab from the printer properties window. Do I want to select IPP or LPD though? I know that I need to enter an IP address somewhere; ubu69's instructions suggest that I want to select LPD but two text fields appear. You can't split an IP address over two text fields! :p

Any guidance would be greatly appreciated.

---

### Post by BobSongs on 2006-01-29
[FONT=Verdana][quote=LxP]Thank you very much for your efforts BobSongs. Thanks also to ubu69 for the useful information on getting a standalone network printer to function (i.e. one connected only to a hub/switch/router and not directly to any computer).

I am attempting to set up my router-connected Brother MFC410CN to print from Ubuntu and I am close; printing of test pages does not work however.

I think that the problem is that I can't modify CUPS settings through its web interface; it is disabled under Ubuntu 'for security reasons' and my attempts to enable it have been fruitless.

It's obvious that I want to select Network Printer from the Connection tab from the printer properties window. Do I want to select IPP or LPD though? I know that I need to enter an IP address somewhere; ubu69's instructions suggest that I want to select LPD but two text fields appear. You can't split an IP address over two text fields! :p

Any guidance would be greatly appreciated.[/quote]
Thank-you, **LxP**, for your kind words. I just started this tutorial because a friend of mine tried Ubuntu and I wanted to give him a step-by-step. Since then others have added to it and as a community we've made it useful.

Feel free to post any detected errors in the command line installation or attempts to connect produce and I'm sure some kind soul will make the effort to fix what's broke.[/FONT]

---

### Post by ubu69 on 2006-01-30
LxP, 

Are you using KDE or Gnome (or something else)? Maybe we can figure it out. 

One thing you might try is setting it up as LPD. In the first text box enter the IP address. In the second text box enter the name of the printer (the "queue" in LPD-speak). Or leave the second text box empty, if possible. 

Just a stab in the dark. 

I never had success with IPP. I figured it was because of the driver. 

Is the CUPS web interface really disabled in Ubuntu? I've found it most useful on my iMac and Linux (Debian and Gentoo) machines. 

Anyway, little baby steps. We'll all figure it out.

---

### Post by LxP on 2006-01-30
Thanks for your attention ubu69!

> **ubu69]Are you using KDE or Gnome (or something else)?[/QUOTE]
I'm using GNOME. It's not much different from the standard Ubuntu installation (although I understand that you don't use Ubuntu).

[QUOTE=ubu69]One thing you might try is setting it up as LPD. In the first text box enter the IP address. In the second text box enter the name of the printer (the "queue" in LPD-speak). Or leave the second text box empty, if possible.[/QUOTE]
I'll try entering just the IP itself in the first box and in the second one I'll enter the *host name* as governed by the printer's settings. Please let me know if either of these are incorrect.

[QUOTE=ubu69]I never had success with IPP. I figured it was because of the driver.[/QUOTE]
Are there any major differences between the two? Coming from Windows, I'm not used to such choice (although as IPP doesn't seem to work, it's not exactly a choice anyway).

[QUOTE=ubu69]Is the CUPS web interface really disabled in Ubuntu? I've found it most useful on my iMac and Linux (Debian and Gentoo) machines.[/QUOTE]
It's not entirely disabled said:**
> [SIZE="4"]Unauthorized[/SIZE]
Administrative commands are disabled in the web interface for security reasons. Please use the GNOME CUPS manager (System > Administration > Printing).

---

### Post by ubu69 on 2006-01-31
LxP,

Are you able to view the help documentation in the CUPS web interface? I have found some answers there in the past. They give examples both using the web interface and the command line. Are you able to configure CUPS from the command line at least?

I tried logging in with GNOME to see if I could see what the GNOME CUPS manager is doing  to you but my environment is set up differently and I don't even have it! Some help I am...

Give it a shot from GNOME and let us know how it works. Oh, and give the CUPS help a read. It will explain a lot. There is also a printing HOWTO buried in /usr/share/doc/HOWTO/en-txt on your system (at least it's on mine) or you can get it online at The Linux Documentation Project <http://www.tldp.org/>. You may get some answers there, as well (IPP, LPD and all that stuff).

After that you may have to futz around with the command line...

We're all learning together. The curve is steep but the support is there.

---

### Post by LxP on 2006-02-09
Well,

I'm not sure what I did but now everything's working for me.

Attached is a screenshot of my Configuration tab. The **10.0.0.2** represents my printer's IP address. I do remember entering **BROTHER** into the *Queue* field (which is what my printer advertises as its host name) but as this has disappeared, I don't know if that was necessary.

One thing that I feel is quite important to note: there is a much longer gap between the time that one creates a print job and the time that the printer responds (at least on this computer compared to Windows). I think that perhaps I was cancelling my test pages before they were reaching the printer; perhaps if I'd been more patient!...

Thanks again to ubu69 and BobSongs and to everyone who has contributed to this thread.

---

### Post by shawndoggy on 2006-02-09
Sweet, just wanted to get on record that I've successfully adapted these instructions to printing from a MFC5440CN which is attached to an XP box on my network.

First I installed the driver per these instructions, using brother's 5440CN driver.

Then I set up the new printer, following the dialog.  Ubuntu found the printer on my network, and then I selected the previously installed driver to run the printer.

The only snag I hit was after that, the printer wouldn't work, even though it was shared on my windows machine.  The wiki saved me there -- even though I don't have user authentication set up on the xp box for the shared printer, ubuntu wants to see "***guest***" typed in the user part on the network printer dialog.  Once I did that, it worked like a champ.

---

### Post by LxP on 2006-02-09
shawndoggy, from your wording it seems that you have your printer directly connected to your Windows machine. Can you please confirm that?

(This should be known to people who are trying to set up a stand-alone 5440CN, i.e. directly connected to a hub/switch/router, because the above information may then not apply to them.)

---

### Post by ubu69 on 2006-02-12
I found this article to be comforting and humorous. The author has written several books on programming and Unix/Linux. While it won't help this particular problem, it is a good read (and explains why we are all dumbfounded by what should be a simple task).

Check it out:

[http://www.catb.org/~esr/writings/cups-horror.html](http://www.catb.org/~esr/writings/cups-horror.html)

---

### Post by djur on 2006-02-20
Regarding the installation of an MFC420CN (MFC 420 CN) printer as a network printer.   If you are trying to share the printer with a windows or other machine....   Obviously make sure you have both samba and cups correctly installed.
Two configuration files of great interest are:  /etc/samba/smb.conf and /etc/cups/cupsd.conf.   If you are unsure of the settings please see the man files by typing 
man cupsd.conf
or man smb.conf

it is important that security is set to user, and that you have added the user by typing:  sudo smbpasswd -a (username)
you will need to set up a password.

Proper set up requires both a USB and network cable to be attached to the printer.  When you have properly set this up it will show as a network printer, and you will see this:   usb:/dev/usb/lp0 in the field.

Ensure you have completed all steps on brother's linux driver website... lpr driver first, and then cupswrapper.

Good luck.

---

### Post by darrenrxm on 2006-02-21
This is funny my dad, just purchased this exact model last week. Unfortunately, it works perfectly with windows. All you have to do is put the cd in the drive and click a couple of button's to get it to install. 

Well, at least they made driver's for linux.

---

### Post by LxP on 2006-02-21
[QUOTE=djur]Regarding the installation of an MFC420CN (MFC 420 CN) printer as a network printer.
...
Proper set up requires both a USB and network cable to be attached to the printer.[/QUOTE]
Hmm... are you sure about this?

My beliefs have been that you either set it up with a USB cable and share it via the connected computer (presumably with Samba) *or* you use a network cable and it's equally available to all computers.

I have set up my MFC-410CN as a network printer using only a network cable; there was no need for USB cables or Samba and both Linux and Windows computers on the network can print to it.

---

### Post by marcw on 2006-02-21
[QUOTE=djur]Regarding the installation of an MFC420CN (MFC 420 CN) printer as a network printer.   If you are trying to share the printer with a windows or other machine....   Obviously make sure you have both samba and cups correctly installed.[/QUOTE]

Huh???

The 420CN is already a network printer i.e. it has a print server built in.  Why would you need another machine from which to share it?  The only reason I can think of to use the USB connection directly (instead of the Ethernet network connection) is to utilize the scanner.  There might be a reason; I just can't think of it...

The reason I know this is because I'm using it right now with a network connection.  My network settings look like this:

---

### Post by thedavis on 2006-02-22
I followed the HowTo for my DCP-115C and its working fine now :) hehehe Thanks :) But I have a question....for scaning?!! :S:S


Sorry if my english suX!!! I tried to write in my best way :D

---

### Post by shawndoggy on 2006-02-22
> shawndoggy, from your wording it seems that you have your printer directly connected to your Windows machine. Can you please confirm that?

(This should be known to people who are trying to set up a stand-alone 5440CN, i.e. directly connected to a hub/switch/router, because the above information may then not apply to them.)

You are correct.  While the MFC 5440CN *can* be hooked directly to a router, mine is not.  It's plugged into the back of my XP box using a usb cable.

---

### Post by djur on 2006-02-22
[QUOTE=marcw]Huh???

The 420CN is already a network printer i.e. it has a print server built in.  Why would you need another machine from which to share it?  The only reason I can think of to use the USB connection directly (instead of the Ethernet network connection) is to utilize the scanner.  There might be a reason; I just can't think of it...

The reason I know this is because I'm using it right now with a network connection.  My network settings look like this:[/QUOTE]

That's right.  As far as I know, to do that you have to have the printer set up on a static IP (not necessarily with your ISP, but within your internal network), and that static IP should not be within the range that DHCP is assigning.  The method with both the USB and network cable attached will work with DHCP.  It may be possible to get it working in such a manner with just the network cable if there is I don't know it, but whenever I disconnect either cable this scenario does not work for me.  Thanks for posting that thumbnail though.  If someone wants to do a static IP, that is probably a more stable method..  I sometimes have to restart samba or cups because this set up can sometimes revert to a "local printer" if there is some temporary network problem when the computer boots.

---

### Post by BobSongs on 2006-02-23
[FONT=Verdana][quote=darrenrxm]This is funny my dad, just purchased this exact model last week. Unfortunately, it works perfectly with windows. All you have to do is put the cd in the drive and click a couple of button's to get it to install. 

Well, at least they made driver's for linux.[/quote]Funny, in a sad sort of way. I hear you. My understanding is: the hardware company hands the task of software creation to a 3rd party. Windows users enjoy the bells and whistles. Linux users have to fend for themselves.

Don't get me wrong. I appreciate Brother's downloadable Linux drivers. Coupled with Xsane it's a pretty decent replacement for the bundled Windows scanner software.[/font]

---

### Post by Zerocool10482 on 2006-02-25
Can anyone tell me how to print with a Canon MP750. I'm a newbie and we have a new business where my boss said if we can do everything will Ubuntu. He will have all the PC run Ubunut. I'm thinking of trying [http://www.turboprint.info/](http://www.turboprint.info/) . I'm not sure if it will work. but has anyone used this?

Thanks and I hope my company can have an all Ubuntu office.

---

### Post by Mack1 on 2006-02-26
HI all,

Just wanted to express my thanks to Bobsong and everyone else that contributed!

My MFC425CN now works like a charm while connected to my network-router :) 

If anyone has any ideas about make the scanner work via the network (not via usb) i would be most gratefull!

Sorry but i cannot help you Zerocool, i'm fairly new to ubuntu...but i'm learning! \\:D/

---

### Post by BobSongs on 2006-02-27
[FONT=Verdana][quote=Zerocool10482]Can anyone tell me how to print with a Canon MP750. I'm a newbie and we have a new business where my boss said if we can do everything will Ubuntu. He will have all the PC run Ubunut. I'm thinking of trying [http://www.turboprint.info/](http://www.turboprint.info/) . I'm not sure if it will work. but has anyone used this?

Thanks and I hope my company can have an all Ubuntu office.[/quote]I hope you can have an Ubuntu office as well there, Zerocool. Here's my suggestion to make this work.[LIST=1]
[*]Scour the Canon website for Linux drivers or instuctions on how to set up this device.
[*]Download whatever you find in terms of drivers: those that relates directly to Ubuntu or general Debian Linux (Ubuntu Linux is based on Debian).
[*]Download the files.
[*]Follow the Ubuntu/Debian instructions and note any error output at the command line.
[*]Open a thread asking for help with any difficult errors.
[*]Post a HOWTO thread with your success story.[/LIST]This thread is for the Brother MFC210C so it would be wasted if you did it all here.

We look forward to hearing from you about the results of your search and installation! :)[/FONT]

---

### Post by BobSongs on 2006-02-27
[FONT=Verdana][quote=Mack1]HI all,

Just wanted to express my thanks to Bobsong and everyone else that contributed!

My MFC425CN now works like a charm while connected to my network-router :) 

If anyone has any ideas about make the scanner work via the network (not via usb) i would be most gratefull!

Sorry but i cannot help you Zerocool, i'm fairly new to ubuntu...but i'm learning! \\:D/[/quote]You're very welcome. Again: a big 'thank-you' to all those who have contributed to make this thread possible and helpful.

:D[/font]

---

### Post by ningsean on 2006-02-28
This is really excellent tutorial. I followed it, and my MFC-210C worked right away.

I have a problem for the scanner part, though. I got the following error when I tried to install brscan2-0.0.2-1.i386.deb:

/usr/local/Brother/sane/setupSaneScan2: line 7: /etc/sane.d/dll.conf: No such file or directory

Should I create a folder just as for the printer part?

Thanks a lot!!

---

### Post by bigken on 2006-02-28
Hi all i got my mfc3820cn working using this thread on a network also got scanner working on network ;)
 
Setup as Unix printer (lpd)
Description MFC3820CN
Host 192.168.XXX.XXX set as static ip on printer control panel 
Queue BRN_463041
 
worked on all listed bellow 
 
breezy 5.10 gnome/kde/enlightenment 17
dapper 6 .06 gnome/kde
suse 10 gnome/kde
Edgy Eft Knot2
Freespire
 
cheers bobsongs your a :KS



and also got my brother mfc660cn working with ubuntu aand kubuntu :p

---

### Post by BobSongs on 2006-02-28
[FONT=Verdana][quote=ningsean]This is really excellent tutorial. I followed it, and my MFC-210C worked right away.

I have a problem for the scanner part, though. I got the following error when I tried to install brscan2-0.0.2-1.i386.deb:

/usr/local/Brother/sane/setupSaneScan2: line 7: /etc/sane.d/dll.conf: No such file or directory

Should I create a folder just as for the printer part?

Thanks a lot!![/quote]It would appear that either you're missing the 'dll.conf' file under /etc/sane.d/ or there is no such folder as /etc/sane.d. Open a Terminal and do:```
cd /etc/sane.d
ls -A
```and tell me what you see.

If you're simply lacking the file I have attached it to this post (it's called 'dll.txt'. Simply rename it 'dll.conf' and place it in /etc/sane.d if it's not there. If the folder exists and is empty then something went very wrong).

If you cannot open the folder because no such folder exists try reinstalling the scanner backend again. Ensure you're running it as 'sudo'.[/font]

---

### Post by ningsean on 2006-02-28
Thank.

I try to enter the sane.d folder, but no luck. There is no folder named sane.d under /etc

```
cd /etc/sane.d
bash: cd: /etc/sane.d: No such file or directory
```

I tried to install it again and got the following information:

```
(Reading database ... 73187 files and directories currently installed.)
Preparing to replace brscan2 0.0.2-1 (using brscan2-0.0.2-1.i386.deb) ...
mv: cannot stat `/etc/sane.d/dll.conf': No such file or directory
/usr/local/Brother/sane/setupSaneScan2: line 20: /etc/sane.d/dll.conf: No such file or directory
cat: /etc/sane.d/dll.conf.tmp: No such file or directory
Unpacking replacement brscan2 ...
Setting up brscan2 (0.0.2-1) ...
/usr/local/Brother/sane/setupSaneScan2: line 7: /etc/sane.d/dll.conf: No such file or directory
```

Thanks!

---

### Post by BobSongs on 2006-03-01
[FONT=Verdana]Do you have the XSane Image scanning program set up on your system?

Applications &#8594; Add Applications &#8594; Graphics[/FONT]

---

### Post by ningsean on 2006-03-01
Thanks. I installed XSane Image Scanning program and brscan now. Both were successful. However, I cannot find libsane.usermap under /etc/hotplug/usb/ . The only files in that folder are libgphoto2  and libgphoto2.usermap. I tried to search MFC in the file libgphoto2.usermap, but found none. Is this because I am using Debian? I think Debian and Ubuntu are similar (at least the printer part succeeded).

Thanks!!

---

### Post by BobSongs on 2006-03-04
[FONT=Verdana][quote=ningsean]Thanks. I installed XSane Image Scanning program and brscan now. Both were successful. However, I cannot find libsane.usermap under /etc/hotplug/usb/ . The only files in that folder are libgphoto2  and libgphoto2.usermap. I tried to search MFC in the file libgphoto2.usermap, but found none. Is this because I am using Debian? I think Debian and Ubuntu are similar (at least the printer part succeeded).

Thanks!![/quote]
heehee! Cute. You had me worried there!

Here I am pulling my hair out wondering what on earth's wrong with your copy of Ubuntu!

Debian and Ubuntu **are** similar. Like fraternal twins. Not identical twins. And the differences make them distinct enough.

Initially I wanted to give Debian Linux a whirl. But all my friends jumped at the chance to shout: "For heaven's sake!! NOOOOO! Install Ubuntu. Don't you know Debian is ***broken***?? Are you out of your mind?"

So I reconsidered and installed Ubuntu instead. It's been nothing but fun ever since.

All that to say: I cannot vouch for a pure Debian system. They're similar but the differences will force you to persue Debian forums for answers. We'll be as helpful here as we can. But in the end all my advice is going to be Ubuntu-centric. This is my first real serious dip into Linux as a primary system. (My friends cannot believe XP is **not** what they see on my desktop.) So I'm going to have to plead ignorance about Debian, Slackware, SuSE, Redhat/Fedora, etc. What you could do is search the Brother website. I believe they have instructions on how to install the Sane drivers. Step-by-step instructions.

Beyond that... I cannot help you. :'(

Sorry.[/FONT]

---

### Post by ningsean on 2006-03-05
Thank you for your help.
I like this forum very much and I find most HOW-TOs work for me so far. That's why I think this scanner thing is probably going to work, too. Sorry for not clarifying this at the beginning. Maybe I should consider to change to Ubuntu :-)

Thanks again.

---

### Post by BobSongs on 2006-03-05
[FONT=Verdana][quote=ningsean]Thank you for your help.
I like this forum very much and I find most HOW-TOs work for me so far. That's why I think this scanner thing is probably going to work, too. Sorry for not clarifying this at the beginning. Maybe I should consider to change to Ubuntu :-)

Thanks again.[/quote]At this point I would only recommend installing Ubuntu to fully use your printer. But hey: most would consider that a really lousy reason to switch distributions. ;)

Nevertheless, Ubuntu has been very satisfactory. Everything I've needed in an O/S has been supplied in these forums or the wiki or some satellite sites. This forum is famed for its friendliness. I've never seen anyone told to "read the manual". Ubuntu itself just ... works. That's probably the best I can put forward.

But I'd love to hear your reasons for why you're using Debian. Write a personal note if you choose.

Thanks.[/FONT]

---

### Post by montablac on 2006-03-05
ACK

i installed the printer by my self (despite the fact that ive had little time in ubuntu,GO ME)

i installed all the things for the scaner,but when i run xsane i get the folowing reply
> failed to open device `brother2;bus3;dev1':eror during device I/O

any help for a newbe?

---

### Post by BobSongs on 2006-03-06
[font=Verdana][quote=montablac]ACK

i installed the printer by my self (despite the fact that ive had little time in ubuntu,GO ME)

i installed all the things for the scaner,but when i run xsane i get the folowing reply


any help for a newbe?[/quote]
By now you've probably figured it out. I had that same problem. What I needed to do was shut the printer off ... then turn it back on. At least: that's what solved it for me. Like that old, old expression says: "If at first you don't succeed: reboot".

**Edit**: I've added the shutdown/restart to the tutorial.[/font]

---

### Post by montablac on 2006-03-06
thx for that man

---

### Post by punkass on 2006-03-15
[QUOTE=marcw]Huh???

The 420CN is already a network printer i.e. it has a print server built in.  Why would you need another machine from which to share it?  The only reason I can think of to use the USB connection directly (instead of the Ethernet network connection) is to utilize the scanner.  There might be a reason; I just can't think of it...

The reason I know this is because I'm using it right now with a network connection.  My network settings look like this:[/QUOTE]

Did you have to do anything else to get it hooked up to the network printer.  I have all the drivers installed etc, but I can not seem to get a connection with the printer itself..I know its working as windows machines can access it.  I have tried iip, lpd etc, but with no luck ( for example where did you get the binary_p1 from )

---

### Post by niknak on 2006-03-25
A newbee needs help, I've followed bobsongs directions but failed to load the c shell. I have my mfc5840 connected to my router and I cannotget it to work. I've obviously missed something and lost the original thread where another mfc5840 owner had some success using bobsongs methods. I also have major problems with deb and rpm files downloaded off the brother-linux website. can anyone help?..

---

### Post by BobSongs on 2006-03-25
[font=Verdana][quote=niknak]A newbee needs help, I've followed bobsongs directions but failed to load the c shell. I have my mfc5840 connected to my router and I cannotget it to work. I've obviously missed something and lost the original thread where another mfc5840 owner had some success using bobsongs methods. I also have major problems with deb and rpm files downloaded off the brother-linux website. can anyone help?..[/quote]
Please note the warning placed on page 1: > This tutorial assumes that your MFC is attached directly to your PC.Somewhere in this thread you'll find a link to setting up the MFC as a network printer. But I'm afraid that doesn't involve having it attached directly to the router. The notable reason: there are some programming changes that need to occur on the host PC. Attaching it directly to the router may be a bit of a challenge.

However, if you find a solution: post it here. I'll be glad to add it to the basic tutorial. If anyone else has a hot tip on how to access MFCs directly from the router: fill me in.

> ...failed to load the c shell.And what was the problem with the C-Shell? Are you using Ubuntu? Forgive me for asking but so far there have been posts to this thread from users of other systems. I'm happy to assist anyone... but I need to know from the start what version of Linux you're using. I can make no assumptions if I'm going to be helpful. Otherwise it's: ](*,)
> ...lost the original thread where another mfc5840 owner had some success using bobsongs methodsWow. I didn't know. Cool.
> I also have major problems with deb and rpm files downloaded off the brother-linux website.Please be more specific. The more info you give the more I can help.[/font]

---

### Post by marcw on 2006-03-25
[QUOTE=niknak]A newbee needs help, I've followed bobsongs directions but failed to load the c shell. I have my mfc5840 connected to my router and I cannotget it to work. I've obviously missed something and lost the original thread where another mfc5840 owner had some success using bobsongs methods. I also have major problems with deb and rpm files downloaded off the brother-linux website. can anyone help?..[/QUOTE]

This thread deals with the 210.  Since you have a different model it probably would have been best to start a new thread somewhere other than in the HOWTO section.

Anyway, your 5840 has a built in print server and it sounds like that's how you have it connected.  That should work fine.  I did it with the 420CN.  The only thing you'll probably want to do is to assign it a static IP address.  You'll have to do that both within the printer itself as well as the router.  Your router manual will have instructions for this as will your Brother manual.  Then look for one of my posts within this thread for more information on setting up the Ubuntu client.  Also, search for a thread I started some time ago on getting a 420 to work.  Searching for Brother mfc-420cn should do the trick for you.

You also mention that you didn't install the c shell.  Why not?  What failed?  Using Synaptic or apt-get should be all you need.  The Brother install will simply not work without the c shell.

---

### Post by niknak on 2006-03-26
Sorry!, I've started a new thread now. called it "installing a network printer". but to answer your questions. I have ubunti 5.10, a router/wireless/modem/print spooler all-in-one-box made by safecom. It all works great in windows and all computers see the printer. This machine (unbuntu) is connected through the router and the mfc5840cn is also connected to the router. I have setup the printer with a static IP address. I personally think that there is so many variables in my setup it'll be impossible to crack. 
C shell didn't work as the file csh? couldn't be found. I did tell you I was a newbee!!
I have seen somewhere that my version is also know as debian?

---

### Post by BobSongs on 2006-03-26
[font=Verdana]Install the C Shell using the following:```
sudo apt-get install csh
``` Then the drivers will work.

Return to the tutorial and follow the steps carefully. Besides: my tutorial was designed for new Ubuntu users, not for the experienced. But I cannot do anything for anyone who is impatient. ;) The steps were carefully thought out, tested and improved with each user who, thankfully, has added to it.

Give it another go.[/font]

---

### Post by Bucanero on 2006-04-09
Just to let you know

I've follow this how to with my Brother MFC5440N and it works great !, thanks

The printer is connected via network to my switch.

I'll try the scanner, any luck to network scan ? what about the fax ?

Thanks

Bucanero

---

### Post by BobSongs on 2006-04-09
[font=Verdana]I've seen a number of different users rejoice at how their particular printer works with my tutorial. (Kudos to Brother for their well-written drivers.)

Now I do make the disclaimer that "this tutorial assumes your MFC is attached directly to your PC and your PC is Intel-based 32-bit." When it comes to networking the printer, you're on your own. I'm not trying to be unkind: my printer is connected directly.

However, if you patiently read through this whole thread there is a reference to an instructional link showing how to make the MFC a network printer. But I doubt it's of any value when the MFC is attached to a hub or whatnot.

Should you discover how to make your printer work as a stand-alone device please post a very, very carefully detailed account and I'll happily add it to my tutorial. (When it comes to new users never assume they know more than how to turn the PC on. I don't mind a challenge. It's no fun for them to comb over poorly written instructions trying to get a feature to work, cool?) Detail what you do step by step (tedious as it is) and I wish you complete success.[/font]

---

### Post by splendid on 2006-04-16
Folks, I have a Brother HL2070N Printer that I am trying to setup, and keep having problems.  The printer is connected to my DLink Router.  Any ideas??  I have both the CUPS and LPR Drivers loaded, but still can't seem to get the thing to work.

Help Please.

Thanks,

Rob

---

### Post by marcw on 2006-04-16
[QUOTE=splendid]Folks, I have a Brother HL2070N Printer that I am trying to setup, and keep having problems.  The printer is connected to my DLink Router.  Any ideas??  I have both the CUPS and LPR Drivers loaded, but still can't seem to get the thing to work.[/QUOTE]

I think you're going to have to do better than this.  Exactly how is it not working?  What is happening or not happening?  What have you tried so far?  Have you read this thread in its entirety?  (It doesn't sound like it but can't tell for sure.)  Have you searched for other Brother related threads?  Have you read through Brother's own documentation?  (There quite a bit posted on the Brother site.)  Did the installs go exactly as documented?  If not, how so?

I'm not familiar with your model, but can tell you that I have installed two different Brother printers - 210C and 420CN - one of which, the 420CN, has a built in print server and is connected directly to a router and have written about both installs in the Ubuntu forums.  So it can be done despite what you may have read from others.

---

### Post by splendid on 2006-04-16
I installed the CUPs and LPR Drivers.  The printer does appear in the  System-Administration-Printing tab.  I get a message that say's:

Printing: Unable to connect to IPP host: Success

Tried printing a test page, but the job just sits in the queue.  On my Windows network, there is no problem with the printer.  It works fine, and I have another computer print to it as well.

---

### Post by marcw on 2006-04-16
What does the General, Driver, and Connection tabs of your printer properties say?  Pictures would be fine...

---

### Post by splendid on 2006-04-16
** General**

Name:  HL2070N for CUPS

Location:  blank

Resolution:  600dpi

Status:  Printing: Unable to connect to IPP host: Success

**Driver**

Manufacturer:  Brother

Model:   HL2070N

Driver:  Standard      Suggested

**Connection**

Printer Type:  Network Printer   CUPS Printer
URL:  [http://hostname:](http://hostname:) 631/

P.S.  Since I am a "newbie"  how do you copy pictures to post?

---

### Post by BobSongs on 2006-04-16
[font=Verdana]**markw**: thanks for your input! I do moderate this thread as often as I can. It's been read by wayyy more people than I ever expected it would be. So I try to drop in as often as possible. Your moderation of the thread was very helpful. :D Should I send you cookies? ;)

Go placidly.[/font]

---

### Post by marcw on 2006-04-17
[QUOTE=splendid]
**Connection**

Printer Type:  Network Printer   CUPS Printer
URL:  [http://hostname:](http://hostname:) 631/

P.S.  Since I am a "newbie"  how do you copy pictures to post?[/QUOTE]


Go back and read message #46 in this thread and look at the picture.  See if that method works for you like it did me...

---

### Post by bigken on 2006-04-18
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=8457&stc=1&d=1145344492[/IMG]

---

### Post by stalefries on 2006-04-18
This is for all of you out there who want a networked scanner!

I have confirmed this to work both with Brother's confirmation program, and by making a preview scan of a random item I had lying around by the printer.

BobSongs: Feel free to add this to your original post. 
The first part is shamelessly ripped and modified from **Lunixfanboy's** part of the tutorial. I'm sorry. The second part is shamelessly ripped and modified from the Brother tutorial. I'm sorry, once again.

NEW: Success! These directions work, unmodified, with Dapper. Sure, this is a little late, with Edgy coming in a couple of weeks, but better late than never! Most likely, unless something drastically changes with Edgy, these directions should work then too.
 
 **[SIZE=3]Step 1: Download from Brother[/SIZE]**
 
Go [over there]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html#model") to obtain the 'sane scanner' backend. 

 Save the file, for the sake of consistency, to the **mfc210c** folder on your desktop. If the terminal is closed, please open it again:[INDENT]**Applications &#8594; Accessories &#8594; Terminal**[/INDENT]Code:
     [LEFT]sudo dpkg -i ~/Desktop/mfc210c/brscan2-0.0.2-1.i386.deb[/LEFT]
      
 Note: The above command will depend on which sane backend you downloaded, "brscan" or "brscan2". 

The following is the part from [Brother's HOWTO]("http://solutions.brother.com/linux/sol/printer/linux/sane_install-net.html#2").

This step is only necessary if you have previously uninstalled Sane:
Install The latest versions of Sane and Xsane
           
```
apt-get install sane xsane
```To use your machine as a network scanner, you need to set the friendly name, model name and IP address or node name in the driver using the commands below. [B][COLOR=#000000]Please make sure which scanner driver "brscan" or "brscan2" you are using. If you are using "brscan" driver, please use "brsaneconfig". If you are using "brscan2" driver, please use "brsaneconfig2".

[/COLOR][/B][COLOR=#000000]P.S.: I have no idea what they mean by "node name", I ended up using the IP address that I used in setting up the printer for printing.[/COLOR][B][COLOR=#000000]

[/COLOR][/B] Using IP address:

```
brsaneconfig -a name=FRIENDLY-NAME model=MODEL-NAME ip=xx.xx.xx.xx 
```   or 
```
brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME ip=xx.xx.xx.xx 
```  Using node name:

  ```
brsaneconfig -a name=FRIENDLY-NAME model=MODEL-NAME nodename=BRN_xxxxx 
``` or 
  ```
brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME nodename=BRN_xxxxx 
```  i.e) When your model name is "MFC-7820N", nodename is "BRN_XXXXX" and   friendly name is "SCANNER1", set the command as below:

```
brsaneconfig -a name=SCANNER1 model=MFC-7820N nodename=BRN_XXXXX
```   or 
 ```
brsaneconfig2 -a name=SCANNER1 model=MFC-7820N nodename=BRN_XXXXX
```You can check the result by running the command:
          ```
brsaneconfig -q
```       or 
     ```
brsaneconfig2 -q
```      [COLOR=#000000]If the setting is done correctly, you will see the result as below:[/COLOR]
      0 SCANNER1 "MFC-7820N" N:BRN_XXXXX

Finally, to make sure it REALLY worked, open up Xsane

   [B]Applications &#8594; System Tools &#8594; Xsane image scanning program
[/B]
Yeah, it's ugly. 

Now stick something in your scanner. I ended up using a blue comb that was lying around. Crazy, huh?

Click Acquire Preview in the Preview window (your mileage may vary, just hunt around for an Acquire Preview button.) 

If you hear a whirring sound from your scanner, and see a scan starting to materialize on your screen, let out a yelp of joy, for you have a functioning scanner being used via a network connection, in less (and, IMHO, easier) steps than those poor people who are using their Brother scanner via USB!

---

### Post by LxP on 2006-04-18
[QUOTE=stalefries]This is for all of you out there who want a networked scanner![/quote]
Works like a charm! Thanks very much for sharing.

And now to figure out how this XSane software works. ;)

---

### Post by bigken on 2006-04-19
great job on the scanner thx once again bobsongs :D

Works with dapper flight 6 no probs
also suse 10 no probs

---

### Post by danalog on 2006-04-19
[QUOTE=stalefries]To use your machine as a network scanner, you need to set the friendly name, model name and IP address or node name in the driver using the commands below. [B][COLOR=#000000]Please make sure which scanner driver "brscan" or "brscan2" you are using. If you are using "brscan" driver, please use "brsaneconfig". If you are using "brscan2" driver, please use "brsaneconfig2".

[/COLOR][/B][COLOR=#000000]P.S.: I have no idea what they mean by "node name", I ended up using the IP address that I used in setting up the printer for printing.[/COLOR][B][COLOR=#000000]

[/COLOR][/B] Using IP address:

```
brsaneconfig -a name=FRIENDLY-NAME model=MODEL-NAME ip=xx.xx.xx.xx 
```   or 
```
brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME ip=xx.xx.xx.xx 
```   [/QUOTE]

Doing this step I get: 
```
bash: brsaneconfig2: command not found
```
What now? (wat nou?)

---

### Post by LxP on 2006-04-19
[QUOTE=danalog]Doing this step I get: 
```
bash: brsaneconfig2: command not found
```[/QUOTE]
You didn't properly install the **brscan2** package. Please refer again to the appropriate part of the original message.

---

### Post by danalog on 2006-04-19
[QUOTE=LxP]You didn't properly install the **brscan2** package. Please refer again to the appropriate part of the original message.[/QUOTE]
What I did:

1) got the deb from brother
2) installed the deb (sudo dpkg -i ~/Desktop/mfc210c/brscan2-0.0.2-1.i386.deb)
```

danalog@dev:~$ sudo dpkg -i ~/Desktop/mfc210c/brscan2-0.0.2-1.i386.deb
(Reading database ... 105274 files and directories currently installed.)
Preparing to replace brscan2 0.0.2-1 (using .../brscan2-0.0.2-1.i386.deb) ...
Unpacking replacement brscan2 ...
Setting up brscan2 (0.0.2-1) ...

```

3) sudo apt-get install sane xsane
4) brsaneconfig2 -a name=Scanner model=MFC210C ip=192.168.1.34

Result:

bash: brsaneconfig2: command not found

===========
I am on latest Dapper Drake.

================

edit:

I tried it with newer version of brscan: brscan2-0.2.0-0.i386.deb

Now I get a bit further but it gives me an error on an invalid model name: 
```

danalog@dev:~$ brsaneconfig2 -a name=MFC210C model=MFC210C ip=192.168.1.34
Invalid model name

```

=====
edit:

FIXED

Forgot to add - (dash) in model name: MFC-210C

Scanning works!!

---

### Post by stalefries on 2006-04-19
danalog: Have you ever installed/removed any of these packages before? Can you show us your $PATH?


LxP (and anyone else who cares): Check out the [Xsane Documentation]("http://www.xsane.org/doc/sane-xsane-doc.html").


Also, good to know it helped a bunch of people so soon, and that it went smoothly for (almost) all of you!

---

### Post by bigken on 2006-04-19
[quote=danalog]What I did:

1) got the deb from brother
2) installed the deb (sudo dpkg -i ~/Desktop/mfc210c/brscan2-0.0.2-1.i386.deb)
```

danalog@dev:~$ sudo dpkg -i ~/Desktop/mfc210c/brscan2-0.0.2-1.i386.deb
(Reading database ... 105274 files and directories currently installed.)
Preparing to replace brscan2 0.0.2-1 (using .../brscan2-0.0.2-1.i386.deb) ...
Unpacking replacement brscan2 ...
Setting up brscan2 (0.0.2-1) ...

``` 
3) sudo apt-get install sane xsane
4) brsaneconfig2 -a name=Scanner model=MFC210C ip=192.168.1.34

Result:

bash: brsaneconfig2: command not found

===========
I am on latest Dapper Drake.[/quote] 

try brsaneconfig2 -a name=Scanner1 model=MFC-210C ip =192.168.1.34

---

### Post by danalog on 2006-04-19
[QUOTE=bigken]try brsaneconfig2 -a name=Scanner1 model=MFC-210C ip =192.168.1.34[/QUOTE]
Ah thank you... I figured it out before reading your reply, thanks anyway!

---

### Post by stalefries on 2006-04-19
danalog: I ended up using brsaneconfig, but this might apply to you. Open Synaptic, and look in the "Unknown" category. Find brsane2 in there, and select it. Now, click the properties button at the top of the window. Click the Installed Files tab, and look through there for "/usr/bin/brsaneconfig2". If that isn't there, keep looking for a path that ends in "brsaneconfig2". Type that instead of just brsaneconfig2 in that long command, and see if it works.

---

### Post by BobSongs on 2006-04-19
[font=Verdana]:-D 

This is excellent. The additions are fabulous: great formatting, **stalefries**!! You know what I like and you complied to the standard I set. =D> What can I say?

I will gladly copy & paste any finished tutorial parts added. I'm going to trust that everything is functional, so I'll keep a sharp eye on any additions. All added parts to the tutorial will be credited to the appropriate author and correctors.

Good work, team! The additions to the tutorial should be in place before Sunday, April 23rd. I'm in hospital at the moment with my oldest daughter (enlarged appendix) so pardon the delay. But the additions will get in very soon.[/font]

---

### Post by bigken on 2006-04-19
Thank you bobsongs your tutorials are great my life was a nightmare unit I hit this how to I tried for 3 months before this with no joy once again cheers hope the daughter has a speedy recovery =D>

---

### Post by stalefries on 2006-04-20
Good to know you like it BobSongs!

---

### Post by bigken on 2006-04-20
[quote=splendid]** General**

Name:  HL2070N for CUPS

Location:  blank

Resolution:  600dpi

Status:  Printing: Unable to connect to IPP host: Success

**Driver**

Manufacturer:  Brother

Model:   HL2070N

Driver:  Standard      Suggested

**Connection**

Printer Type:  Network Printer   CUPS Printer
URL:  [http://hostname:]("http://hostname:") 631/

P.S.  Since I am a "newbie"  how do you copy pictures to post?[/quote] 

Hi In printer properties select conection tab select network printer unix printer (lpd) and add the printer ip address to the host hope this helps 

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=8457&d=1145344499[/IMG]

---

### Post by splendid on 2006-04-21
Big Ken,

Where should I get the Printer IP Address from?  

Thanks,

splendid

---

### Post by bigken on 2006-04-22
Hi splendid you need to setup a static ip address using the printer control panel 
it is probablys set to dhcp read your printer manual if you dont have it download from makers web site

---

### Post by splendid on 2006-04-22
Big Ken,
Bob Songs,

Thank You both very much!!!  You guy's are awesome!  When I followed Ken's last post, I downloaded a program off of the Brother web site called BRAdmin Professional.  From there I loaded and installed the program.  It auto assigned an IP Address after searching for devices (Brother HL 2070N)  that I went in and changed to Static.  Wrote the IP Address down on a piece of paper.  Next I booted into Linux, and downloaded and re-installed the LPR driver from the Brother site just to be safe.    Went into properties and put in the IP address.  Clicked resume on the printer, and then print test page.  The test page printed successfully.  woohoo.

One final question, should I put anything in the Queue setting?

Thanks Again,

Splendid

---

### Post by bigken on 2006-04-22
[QUOTE=splendid]Big Ken,
Bob Songs,

Thank You both very much!!!  You guy's are awesome!  When I followed Ken's last post, I downloaded a program off of the Brother web site called BRAdmin Professional.  From there I loaded and installed the program.  It auto assigned an IP Address after searching for devices (Brother HL 2070N)  that I went in and changed to Static.  Wrote the IP Address down on a piece of paper.  Next I booted into Linux, and downloaded and re-installed the LPR driver from the Brother site just to be safe.    Went into properties and put in the IP address.  Clicked resume on the printer, and then print test page.  The test page printed successfully.  woohoo.

One final question, should I put anything in the Queue setting?

Thanks Again,

Splendid[/QUOTE]


No no need if its working if you wanted too it would be the name your printer gives its self ie mine is BRN_463041 look on the printer setup panel and you will see what it is

---

### Post by BobSongs on 2006-04-24
Added the fax drivers. See main tutorial.

---

### Post by stalefries on 2006-04-28
One thing that has always confused me is this: if the Brother drivers are GPL'ed (which they are) why aren't they included with all the other built-in CUPS drivers?

---

### Post by Hero_boy on 2006-05-01
Is there any way to use this driver on an AMD 64bit system?

---

### Post by BobSongs on 2006-05-01
[font=Verdana][quote=Hero_boy]Is there any way to use this driver on an AMD 64bit system?[/quote]Well, you read the caveat at the beginning. With an AMD 64-bit machine you're somewhat on your own. But I have a recommendation:

**Recommended:** work your way through the tutorial keeping an eye on the Brother website for file sources (see the first paragraph of the tutorial; it has the appropriate link). Try your best to get it working. Check out the error codes given to you in the terminal. Post them here and we'll see what we can do.

Once you've completed your installation, post a copy of your notes (you'll be taking notes, right?). I'll add a link in the tutorial to your additional setup steps. You'll improve my tutorial, benefit the community and you'll get the credit. If you re-install your notes will be here for a quick restore.

That's it... short of my buying a 64-bit AMD to do the testing... and that's not about to happen any time soon. ;)[/font]

---

### Post by BobSongs on 2006-05-03
[font=Verdana][quote=stalefries]One thing that has always confused me is this: if the Brother drivers are GPL'ed (which they are) why aren't they included with all the other built-in CUPS drivers?[/quote]Or, perhaps, on the setup CD that comes with the printer.[/font]

---

### Post by stalefries on 2006-05-03
Capital idea! Maybe even an automated installer? 

Nah.:p

---

### Post by teejcee on 2006-05-04
If you have a Brother MFC620CN, this HOWTO works perfectly. 

Simply substitute the model number where applicable.

As an adjunct, if you want to run the printer from a hub - this model is network ready - while you are checking the properties of the printer, 
select the Connection tab, 
check Network Printer, 
select UNIX Printer (LPD),
enter the printer's ip address in the Host box. 

Should all work like a charm.

---

### Post by BobSongs on 2006-05-05
[font=Verdana][quote=stalefries]Capital idea! Maybe even an automated installer? 

Nah.:p[/quote]
Speaking of automated installers, have you seen [Autopackage]("http://autopackage.org/") yet? I've used it to install a few favorites like the latest Inkscape, Stallarium and SuperTux. They've worked hard on this packaging idea. It seems to work for any GNU/Linux distribution. So drivers set up according to autopackage might not be a bad idea. Sadly, I don't have the programming skills. But I can look and see what they've got in the way of a tutorial. No promises.[/font]

---

### Post by stalefries on 2006-05-06
Not a bad idea, although most opinions I've heard of Autopackage have been more negative than positive. Now, I don't remember why. So you might as well try, for those who prefer an autopackage. I think the better thing would be to create an install script similar to what the Automatix guy did, using zenity. It's installed by default on Ubuntu (unlike autopackage) and would probably make this process easier.

I'd imagine it like this:
It would start out with links to the listings of the various drivers and such necessary, explaining what one needs to do at each page. 
Even better, would be a pre-programmed drop-down list of all the supported models. Say I wanted to install an MFC-3820CN. I would select it from the drop-down list, and then this script would grab all the necessary drivers and things, excluding the fax or scan drivers if I told it to (by unchecking a check box or something). 

Then, it would install all of these, and make the necessary changes, like changing those certain hex codes for that one procedure. It would then explain to the user what to do next (Go to System>Administration>Printing and fill out this and that, etcetera.) 
It would then exit.

That's how I imagine it. I can't say I know how to do it, but I'll try to learn some more shell scripting and using zenity if no one else is capable or volunteers.

---

### Post by BobSongs on 2006-05-07
[font=Verdana][quote=stalefries]<snip>That's how I imagine it. I can't say I know how to do it, but I'll try to learn some more shell scripting and using zenity if no one else is capable or volunteers.</snip>[/quote]Well, you have the makings of genius!

That's far better than anything I imagined. I'll tell you what: I'm putting so much time into my band (public performance and recording studio) that I don't have too much time to set aside for the scripting.

It's not laziness or lack of care, just time constraints. But if you'd like to give it a go there's a whole lot of people out there that would be tickled and would speak favorably of you for years to come. ;)

**Edit**: Yo, dude; do you think this might be of value? [[Click here]]("http://ubuntuforums.org/showthread.php?t=168391"). The author doesn't use Zenity, but it's possible something basic could be done.[/font]

---

### Post by stalefries on 2006-05-08
My one concern is that users need to install extra software for just that, while zenity is included with Gnome. 

I'll look into zenity, maybe I'll look at the source for Automatix to get a grasp of its use.

---

### Post by BobSongs on 2006-05-08
[font=Verdana]I explained to a friend of mine the task at hand. Let me tell you what we're working on.

We're taking the structure of Automatix and rewriting the script Automatix runs. We're going to credit **arnieboy**, naturally, but his script is GPLed so as far as we understand it's free to take and modify.

We're going to remove all the installables he's got listed and we're replacing it exclusively with the three aspects of the MFC-210C: Printer drivers, Fax drivers and Scanner drivers.

This will be marked version 0.0.1. It will not include support for 1) any other distro than Breezy Badger and 2) any other Brother product.

Now, you'll be free to examine the contents and see what my programmer friend did. Please: take it and run with it. Compare it to the script that runs Automatix and add as much as you desire. I'll be more than happy to add a link right in the tutorial.

As it grows the version number can rise too. You'll be credited in the script, naturally. We should be done the better part of the script today. Then we'll have to figure out how all the rest was processed to get it to work correctly.[/font]

---

### Post by stalefries on 2006-05-08
That's great that you and your friend have got it started (actually, I started giving a whack at it, also). There's only one problem I see: making it exclusively for the MFC-210C. From all the comments on this thread, it seems that people are using it for more than just the 210C. I, for example, have an MFC-3820CN. 

The approach I have taken with my version is to provide a list of all the printers that can be installed, and then installing whichever one is selected. Of course, this may bulk up the script somewhat, but I think it's for the greater good. 

Of course, my approach won;t work for every multi-function, as some do have scanners or copiers or faxes, and some don't. I figured I woulod include the scanner and fax installers in different scripts, maybe all linked to from one master script. 

I think we should both do our own thing, and then get back together and compare/contrast, and combine the better portions of either script into one super-script!

---

### Post by stalefries on 2006-05-09
For anyone who has been following this: BobSongs and I have continued this conversation via PM, to keep from clogging this thread. We are making headway, and I imagine a script will be posted soon.

---

### Post by Lunixfanboy on 2006-05-10
As an aside to the howto, Dapper does NOT have hotplug, so editing the libsane.usermap will not be an option. However, getting brscan2-0.2.0-i386.deb and using that in Dapper has made the scanner functional again. I apt-get dist-upgraded from Breezy to Dapper when Flight 7 was announced, and immediately lost access to the scanner function. I just checked with Brother, and they have a newer release for those with kernel >= 2.6.13 which remedied the problem.

---

### Post by BobSongs on 2006-05-10
[FONT=Verdana]Thanks dude. It is noted.

The script that will eventually be added to the tutorial will be, for the time being, exclusively for the Breezy/MFC210C combo. But it will be open for anyone to make additions.

When Dapper is released I will see what I can do to about modifying the script to include it as well.

Many thanks for the heads-up![/FONT]

---

### Post by vojtek on 2006-05-11
I'm using MFC 215C with 210C driver. My model (dont know if 210 too) has card reader - is it any possibility see that cards on Ubuntu Breezy? How can I send any file to card using card reader on my printer?

---

### Post by stalefries on 2006-05-11
The card reader can't be accessed from any pc. The card reader on your printer (and I imagine this applies to any printer with a card reader) is only for the printer to be able to print off the pictures on the card. Sorry.

Funny thing: i have a friend named Vojtek who's from Poland also.

---

### Post by woot on 2006-05-12
Hey maybe a little addition in the howto as already mentioned somewhere on page 2 i think when having problems with installing lpr support:

error:
/etc/init.d/lpd: No such file or directory

can be solved with
```
ln -s /etc/init.d/cupsys /etc/init.d/lpd 
```

To be honest im not sure if it will work as im not at home now. i just installed the drivers on my laptop so i can add the printer through the network as soon as i get home. But creating the link let me go throught the howto succesfullyl.

so step 3 should be (in some cases, i was trying to install a mfc9180). 

```

sudo mkdir /var/spool/lpd
sudo mkdir /var/spool/lpd/MFC210C  (replace with your printer name)
ln -s /etc/init.d/cupsys /etc/init.d/lpd 
sudo dpkg -i ~/Desktop/mfc210c/mfc210clpr-1.0.2-1.i386.deb

```

thnx BobSongs for the nice howto... people who write tutorials like you (and perhaps some which you used as base for your howto) make life a lot eassier. I had been trying to get my printer working some months ago under breezy but i ended up with being unable to uninstall some mfc package whilst saying i had to reinstall it to uninstall it..which was freaky as i wasnt able to install it...this time better luck with Dapper and this nice howto

thnx!

---

### Post by BobSongs on 2006-05-12
[font=Verdana][quote=woot]error:
/etc/init.d/lpd: No such file or directory[/quote]That's an interesting error. I've never come across it before. And I must admit I've installed Ubuntu quite a few times (I tend to mess with it and break it, but it's all part of the learning process). 

I await your return from work for the confirmation of the following code as a solution to the problem:

```
ln -s /etc/init.d/cupsys /etc/init.d/lpd 
```If this is correct it will be in the tutorial before long.

Thanks for the "heads up".[/font]

---

### Post by stalefries on 2006-05-12
I imagine a "sudo mkdir /etc/init.d/lpd" would suffice, although I know very little about this.

---

### Post by woot on 2006-05-13
[QUOTE=stalefries]I imagine a "sudo mkdir /etc/init.d/lpd" would suffice, although I know very little about this.[/QUOTE]

to be honest i think you're wrong... most files in init.d aren't directories rather scripts or something like that...

(though i might be wrong)


I still can't confirm wheter it works...im having troubles configuring the samba side of the network printing :(

when i run: 

cd /var/log/cups/
tail -f error_log

i get all lines like:

E [13/May/2006:12:09:23 +0200] cupsdAuthorize: Local authentication certificate not found!

anyone? i have been trying everything :S 

well, ill try plugging it in by usb, if it works then, at least im sure about the drivers being correct

*edit*
i can now confirm that adding the specific link helped me install succesfully a brother mfc 9180 printer on ubuntu dapper drake (by usb port)

worked like charm

now the damn samba network thingy!

---

### Post by stalefries on 2006-05-13
Well, it shows how little I know.

In other news, does anyonie know why ubuntu-desktop needs to be removed whenever I install lpr, and vice versa? I thought ubuntu-desktop was just a meta-package.

---

### Post by BobSongs on 2006-05-14
[font=Verdana][quote=stalefries]Well, it shows how little I know.

In other news, does anyonie know why ubuntu-desktop needs to be removed whenever I install lpr, and vice versa? I thought ubuntu-desktop was just a meta-package.[/quote]
It would appear that a lot will disappear from your Ubuntu setup if you remove the Ubuntu-desktop package. Not recommended. I haven't tried it. But then again I don't want to see nine tenths of my setup vanish because of a mouse-click. ;)[/font]

---

### Post by stalefries on 2006-05-15
[quote=BobSongs]It would appear that a lot will disappear from your Ubuntu setup if you remove the Ubuntu-desktop package. Not recommended. I haven't tried it. But then again I don't want to see nine tenths of my setup vanish because of a mouse-click. ;)[/quote]
 
It didn't remove anything but the ubuntu-desktop package. Everything is still there. Wait, does this mean you didn't have to install lpr at any point? I hope it's true.

---

### Post by BobSongs on 2006-05-15
[font=Verdana]lol

No, dude. Only read the description in Synaptic. It didn't appear to be something I wanted to do. But if all works well, then I should have kept my mouth shut.

Well. I'll be posting the script soon, on your recommendation. It works when one opens a command prompt and does sudo ./brotherscript.sh

I'll have that up some time tomorrow.

:)[/font]

---

### Post by stalefries on 2006-05-15
I guess that misconception was left over from when I tried to install the printer from before. For some reason, i was led to think that I needed lpr installed. Guess what's getting fixed right now!

Good to hear the script is coming along.

---

### Post by bgolden12345 on 2006-05-15
You guys are great got my MFC-5440CN scanner to work this way....  Thanks.

---

### Post by BobSongs on 2006-05-16
**[SIZE=4]An "Install Script" for the Brother MFC210C printer.[/SIZE]**

**Removed for Breezy Badger**

Breezy Badger is hereby officially no longer supported by this thread or by Canonical.

Thanks

Bob

---

### Post by stalefries on 2006-05-18
Also, for all of you who have a printer other than the MFC-210C, and manage to install it by modifying the afore-mentioned script, please post your modified script here so we can incorporate it into the next version. Hopefully, we'll be able to eventually cover all Brother printers with this script!

---

### Post by Jasman on 2006-05-26
Thanks for this thread. If anyone cares, I just managed to install my Brother HL-2040 printer to work through my Asus WL-500G Deluxe Access Point with print server using instructions from this thread/script (modified, of course, for my printer, and using the two files readily available from Brother - the cups wrapper and LPR driver) and then installing as a network printer in Gnome System Printers using the basic IP for my router (in this case 192.168.1.1). The kicker, however, was choosing HP JetDirect to send print jobs through port 9100. Works like a charm, and I never even connected my printer directly to my laptop (it's connected via USB to the AP).

---

### Post by BobSongs on 2006-05-26
Thanks for the post. I'll add it to the list of success noted at the bottom of the tutorial.

---

### Post by Boelcke on 2006-05-29
I'm following your tutorial (thanks!) for a Brother HL-2040, directly connected to a ubuntu 5.10 PC via USB.  All was sailing smoothly until step four.

```

mike@ubuntu2:~$ sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
mike@ubuntu2:~$ sudo dpkg -i /home/mike/downloads/brotherHL-2040/cupswrapperhl2040_1.0.0-1_i386.deb
Selecting previously deselected package cupswrapperhl2040.
(Reading database ... 82093 files and directories currently installed.)
Unpacking cupswrapperhl2040 (from .../cupswrapperhl2040_1.0.0-1_i386.deb) ...
Setting up cupswrapperhl2040 (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperHL2040
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
lpadmin: Unable to connect to server: Connection refused
```

What's happening with this Unable to connect to server stuff?  Everything worked well up until then.  I've tried restarting the printer, and trying running the command again (which didn't work well).  Nothing has appeared in the System, Administration,Printers window.

WAIT!  STOP THE PRESSES!  While typing this message, perhaps 10 minutes since what I described above happened, things suddenly started working.  I went into System, Administration, Printers to check something, cycled the power *again* on the printer, and WHAMO!  The printer now appears there!  Whats more, it works pretty well too.

You've just made my ubuntu weekend.  Thanks.  I wonder what made it take so long.  Whatever it is, the advice is to wait a seriously long time!

(Now, onto investigate why KMyMoney imports my old Quicken file and shows I've got $334,000 in my checking account...)

---

### Post by BobSongs on 2006-05-30
[QUOTE=Boelcke]I'm following your tutorial (thanks!) for a Brother HL-2040, directly connected to a ubuntu 5.10 PC via USB.  All was sailing smoothly until step four.

...

WAIT!  STOP THE PRESSES!  While typing this message, perhaps 10 minutes since what I described above happened, things suddenly started working.  I went into System, Administration, Printers to check something, cycled the power *again* on the printer, and WHAMO!  The printer now appears there!  Whats more, it works pretty well too.

You've just made my ubuntu weekend.  Thanks.  I wonder what made it take so long.  Whatever it is, the advice is to wait a seriously long time![/QUOTE]Well, you've found it. I think patience is the most important part of working with a Brother device. You waited and boom: it worked.

My own script for the MFC-210C only works correctly if the printer is turned off, on, off, on at the right times. 

I'm pleased that the tutorial has proven helpful. Brother's drivers for Debian work fairly well in Ubuntu, just a minor modification here and there and we're printing.

---

### Post by timsch75 on 2006-05-30
I used this tutorial to install my DCP110C with Breezy with immediate success.  I upgraded to Dapper this weekend and the printer would no longer work.  I've reinstalled with the same directions assuming I'd have to tweak based on error messages, but I didn't get any.  


[I]EDIT
tim@ubuntu:~/printer/dcp110c$ **sudo dpkg -i dcp110clpr-1.0.2-1.i386.deb**
(Reading database ... 106367 files and directories currently installed.)
Preparing to replace dcp110clpr 1.0.2-1 (using dcp110clpr-1.0.2-1.i386.deb) ...
Unpacking replacement dcp110clpr ...
Setting up dcp110clpr (1.0.2-1) ...
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1.0' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so' to `/usr/lib/libbrcompij2.so.1.0.2': File exists

tim@ubuntu:~/printer/dcp110c$ **sudo dpkg -i cupswrapperdcp110c_1.0.0-1_i386.deb **
(Reading database ... 106367 files and directories currently installed.)
Preparing to replace cupswrapperdcp110c 1.0.0-1 (using cupswrapperdcp110c_1.0.0-1_i386.deb) ...
lpadmin: The printer or class was not found.  ** [THIS LINE WAS NOT INCLUDED IN A RUN I DID JUST BEFORE.  THE PRINTER WAS PROBABLY OFF WHEN i RAN THE LINE AS THE DIRECTIONS SAY]**
 * Restarting Common Unix Printing System: cupsd                                                            [ ok ] 
Unpacking replacement cupswrapperdcp110c ...
Setting up cupswrapperdcp110c (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperDCP110C
 * Restarting Common Unix Printing System: cupsd [/I]



  The printer is recognized under SYSTEM>ADMIN.>PRINT and when I send a test page nothing happens.  The printer icon changes from "printing" to "paused".  The output of dmesg is:

*
[I][4392132.204000] usb 3-2.4: new full speed USB device using ehci_hcd and address 5
[4392132.254000] scsi1 : SCSI emulation for USB Mass Storage devices
[4392132.254000] usb-storage: device found at 5
[4392132.254000] usb-storage: waiting for device to settle before scanning
[4392137.264000]   Vendor: Brother   Model: DCP-110C          Rev: 1.00
[4392137.264000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4392137.265000] usb-storage: device scan complete
[4392191.454000] ppdev0: registered pardevice
[4392191.496000] ppdev0: unregistered pardevice
[4392191.496000] ppdev1: claim the port first
[4392191.496000] ppdev2: claim the port first
[4392196.259000] ppdev0: registered pardevice
[4392196.349000] ppdev0: unregistered pardevice
[4392196.349000] ppdev1: claim the port first
[4392196.349000] ppdev2: claim the port first
[4392322.601000] ppdev0: registered pardevice
[4392322.642000] ppdev0: unregistered pardevice
[4392322.662000] ppdev1: claim the port first
[4392322.662000] ppdev2: claim the port first[/I]
*

Any ideas would be greatly appreciated.  Thanks

---

### Post by BobSongs on 2006-05-30
**A.** Two failed attempts to upgrade my Breezy to Dapper have left me a "Breezy user" and not a "Dapper tester". Perhaps by the time I finally upgrade to Dapper there will be a superior tutorial created by someone else. Unless that happens my fellow forum friends will have to wait for a revised version of the tutorial.

**B.** The forum has expanded somewhat to include, indirectly, other Brother products. Since I'm only a home user and I don't have a laboratory of MFCs with a variety of different systems to test them on you're very much at the mercy of the little I've gleaned from my experience with the inexpensive MFC-210C on a 32-Bit PC running Breezy Badger.

Since I've not been invited to work for printer development (I'd gladly join the payroll!) you're stuck having to get help from the Dapper Drake development team. Now you may wish to ensure you've got the latest drivers from Brother. Perhaps re-installing them and carefully determining what goes wrong. The command line will show you this. If working with the command line is **not** something you consider fun then you may have to wait for other assistance.

---

### Post by BobSongs on 2006-05-30
[QUOTE=timsch75]
tim@ubuntu:~/printer/dcp110c$ **sudo dpkg -i cupswrapperdcp110c_1.0.0-1_i386.deb **
(Reading database ... 106367 files and directories currently installed.)
Preparing to replace cupswrapperdcp110c 1.0.0-1 (using cupswrapperdcp110c_1.0.0-1_i386.deb) ...
lpadmin: The printer or class was not found.  ** [THIS LINE WAS NOT INCLUDED IN A RUN I DID JUST BEFORE.  THE PRINTER WAS PROBABLY OFF WHEN i RAN THE LINE AS THE DIRECTIONS SAY]**
 * Restarting Common Unix Printing System: cupsd                                                            [ ok ] 
Unpacking replacement cupswrapperdcp110c ...
Setting up cupswrapperdcp110c (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperDCP110C
 * Restarting Common Unix Printing System: cupsd [/I]

The printer is recognized under SYSTEM>ADMIN.>PRINT and when I send a test page nothing happens.  The printer icon changes from "printing" to "paused".  The output of dmesg is:[/QUOTE]
Just to let you know. My tutorial requires the printer be off during this phase of the installation. So I doubt this is the problem.

Have you verified if Dapper Drake has added your Brother printer in its list of native printers?

---

### Post by timsch75 on 2006-05-31
I've not seen the list of Dapper's native printers....

The command line is fine.  However, I just downloaded and installed the .deb files about a month ago at most, so those should be current.  It looks like i'm just in the same ol' boat as most other Dapper dudes.  If it weren't going to be such a hassle, I'd go back to Breezy....

---

### Post by BobSongs on 2006-05-31
Keep an eye on the Dapper threads. If many things appear broken it might be a good idea to dig in for a while and let the cutting-edge folks work out the bugs. I'm all for helping but my problem is the need for a PC that's ready to work for the family. I've got that with Breezy. It'll be available in Dapper. I just can't tell when.

---

### Post by nixt on 2006-06-01
I concur with timsch75's findings - a fresh dapper install, followed instructions to the letter and got the exact same error messages. DCP115C here.

[COLOR="Red"]EDIT: I actually got my printer to work with dapper! No debs to install too. Just go through the normal Add Printer process, it will detect your attached printer automatically (switch it on before you start the wizard), press Next and select MFC210C... and print a test page. I was quite surprised when the page printed.[/COLOR]

EDIT: Not true!! Read on the next few replies..

---

### Post by BobSongs on 2006-06-02
Welcome to the forum, **nixt**. Thanks for the heads up.

I recall a post in this thread by **Lunixfanboy** saying he upgraded to Drake and had a bit of trouble with the scanner part of the MFC-210C. He installed the latest driver and it fixed things for him. My point is: the printer drivers worked for him. There was no mention of any modification of that part of the set up.

So I'm just wondering what the problem might be. Would you be so kind as to run through the process again and copy/paste the system's reponses. This will help a great deal towards getting some kind of answer.

Thanks.

---

### Post by nixt on 2006-06-02
Thanks **BobSongs**.. I'm certainly digging harder at this issue at the moment.

I kinda jumped the gun earlier when I declared that my DCP115C worked out of the box with dapper. ](*,) Sorry!

I tried to confirm my findings and purged the debs I installed earlier (dpkg --purge) while following the tutorial. 

I deleted the printer entry and started from the Add Printer (System->Adminstration->Printing->New Printer) part again. The printer detected fine, but at the second dialog box where you had to select a compatible printer (we're looking for MFC-210C here), I couldn't find the listing anymore!

Now if we followed the tutorial step by step, we'll get a printer entry created for us, without having to go through the Add Printer dialog. 

Our friend **timsch75** mentioned earlier that he tried to print a test page through this printer entry and failed.

I found out that this works (at least for me):

1. Install the debs
2. Delete the newly created printer entry (important!)
3. Add a new printer using the New Printer dialog, and select MFC-210C when asked
4. Print a test page.

I need a real nap now, will be back later. Scanning doesn't work for me right now by the way...

---

### Post by sab_nico17 on 2006-06-04
I just switched from MS Windows to Linux... I followed the HowTo for my DCP-110C. The driver is installed, but my prints stay in "pause". Does anyone have a solution for this problem ?

Thanks.

---

### Post by BobSongs on 2006-06-04
You've tried restarting the printer and you're still getting the pause thing?

---

### Post by BobSongs on 2006-06-04
[QUOTE=nixt]

...Scanning doesn't work for me right now by the way...[/QUOTE]
**Lunixfanboy** mentions in [post 115]("http://www.ubuntuforums.org/showpost.php?p=1002409&postcount=115") that the tutorial fails when it comes to the **[COLOR="Sienna"]scanner[/COLOR]** in **Dapper Drake**:[quote=Lunixfanboy]

As an aside to the howto, Dapper does NOT have hotplug, so editing the **libsane.usermap** will not be an option. However, getting brscan2-0.2.0-i386.deb and using that in Dapper has made the scanner functional again. I apt-get dist-upgraded from Breezy to Dapper when Flight 7 was announced, and immediately lost access to the scanner function. I just checked with Brother, and they have a newer release for those with kernel >= 2.6.13 which remedied the problem.[/quote]
I believe [this is the link]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html") to the list of more recent scanner drivers by Brother.

Hope that gets your scanner up and running again. :-D

---

### Post by musther on 2006-06-13
If you're trying to set up a DCP-115C you'll have a problem when you try to install the scanner (at least I did on Dapper).  You should find that when you load xsane you get an error:

> Failed to open device 'brother2:bus3;dev1':
Error during device I/O.

If you try running xsane as root:

```
sudo xsane
```

it will work (after you click continue on the message about it being unsafe).

If you've got to this point and are not happy with scanning as root (you shouldn't be), then you need to do what this message from Brother told me to do.

> Dear Sir/Madam

This is the Japanese Solutions Center.
Thank you for your inquiry.

The current driver works with only a root user.
However for Ubuntu, the following solution could be a help.

Would you try this?

1.Create the file "10-local.rules" under the directory:
"/etc/udev/rules.d/"
which includes the following content:

===========
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="_end"
# For brother
SYSFS{idVendor}=="04f9", MODE="666", GROUP="scanner"
LABEL="_end"
===========

2.Restart the OS.


Best regards,
Brother Solutions Center

All should now be working.

Enjoy!

---

### Post by d3dtn01 on 2006-06-14
Hi. When I first got my MFC210c, I was running Breezy. The directions in the howto worked great (thanks!). About 4 weeks ago I upgraded to Dapper. Now the printer won't work. It's still listed as being there, but whenever I try to print, it does nothing. When I open the printer queue, the state is "Pending: printer-stopped."

Does dapper require another step to get the thing working?

Thanks.

---

### Post by BobSongs on 2006-06-14
Dear sir;

While I devoted time and effort in developing a thorough walk-through for the MFC210C in Breezy Badger, the attention given this project resulted in my neglecting to harvest heat-sink lint which was considerable once this task was addressed. An unfortunate side-effect with the carmelization of my motherboard, due to its inability to dissipate heat as designed... the net result is an eBay entry for one case, a video card, ... well, you get idea.

No burial of the ashes will be necessary as cannibalization has already begun. :-({|= :-({|= :-({|= 

In other words... the PC that ran my printer is dead. So, until such time as a new machine is acquired ... I will be unable to address your query.

Regrets... and most terribly sorry.

---

### Post by BobSongs on 2006-06-15
**:: PUBLIC NOTICE ::**

Apologies to all for the delay. With the demise of my PC and my reluctance to switch my O/S over to Dapper things have been a bit hairy, to say the least.

However, I have just moved my 2nd PC over to the station where my 1st PC once sat. Now I'm running **[COLOR=#c8813a]Dapper Drake version 6.06[/COLOR]** and I've got it attached to my **[COLOR=Red]Brother MFC210C[/COLOR]**. Here are the results so far.

The installation of the drivers has proven successful. No hitch. The test page printed correctly.

**Please note**: *this is not an upgrade*. I repeat: *this is not an upgrade*. Ubuntu GNU/Linux 6.06 LTS on this system was a **[COLOR=#4444ff]clean install[/COLOR]**. For those who are experiencing technical difficulties due to their systems being upgraded from Breezy Badger (5.10) it may be best to remove the drivers and restart the driver install.
[INDENT]**Edit**: The tutorial has been updated. It now contains modifications for **[COLOR=Blue]Dapper Drake[/COLOR]** changes. It will probably need a bit of cleaning up to make it look prettier. But it is now fairly accurate for both Breezy and Dapper.

**Edit 2**: The tutorial has been trimmed a bit (explanations removed) and it looks dapper with formatting changes. The Dapper Drake version of the installer script is also available. Hope its useful.
[/INDENT]

---

### Post by Mr.Mechano on 2006-06-19
Hi there!

Installing the new Dapper 6.06 my MFC-425CN (that use the MFC-210C driver) started to print in reverse order from last to first page on mutiple pages documents.

I wrote to Brother service  and after 4 days I received the response from Japan.
Now the printer works correctly.

[HTML]Dear Sir/Madam,

We could make this issue happen at our side too.

The "reverse order print" you said is actually correct
due to its original specification of the CUPS.
The CUPS you had been using so far was not supporting it.


If you want to change it, please do the following.

1.Open the file MFC210C.ppd which is located under the directory
"/etc/cups/ppd/".

2.Delete the line "*DefaultOutputOrder: Reverse".


Best regards,
Brother Solutions Center[/HTML]

---

### Post by BobSongs on 2006-06-19
Thanks, Mr.Mechano! I examined this file on my PC:  /etc/cups/ppd/MFC210C.ppd and it says the same thing: reverse order. But it seems to print normally; however, I'll be more attentive next time I print two or more pages.

Users: take note on how to change it. (I may just pop that in the tutorial!)

---

### Post by vincedesalpages on 2006-06-21
Hi there,

One question concerning installation of [COLOR="Black"]**MFC-5440CN**[/COLOR] as a scanner (fax and printer are ok).

On **step 3:** "Modify the /etc/fstab file"
I am in that case: 
"-For Kernel 2.6.* version of distribution Users:
$ echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab "

Here is what is written and get back in the terminal:

vincent-bertin@ubuntuvb:/$ sudo -i
Password:
root@ubuntuvb:~# echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab
root@ubuntuvb:~#
root@ubuntuvb:~# echo 'none /proc/bus/usb usbfs auto,devmode=0666 0 0' >> /etc/fstab
root@ubuntuvb:~# umount /proc/bus/usb
umount: /proc/bus/usb: not mounted
root@ubuntuvb:~# mount /proc/bus/usb
root@ubuntuvb:~# mknod -m 666 /dev/usbscanner c 180 48
mknod: `/dev/usbscanner': File exists
root@ubuntuvb:~#

Then, when I use Xsane Image Scanner, this message is displayed: "Failed to open device "brother2:bus2;dev1": Error during device I/O"

What did I do wrong and **how can I correct it**?

Thank for your support.
Vincent



> **BobSongs]**[SIZE=4]A "how to" for the Brother MFC210C printer.[/SIZE]**
**[SIZE=2]Now includes instructions for both [COLOR=Blue]Dapper Drake (6.06)[/COLOR] and [COLOR=Red]Breezy Badger[/COLOR] (5.10).[/SIZE]**


**[SIZE=3]Introduction[/SIZE]**[INDENT]Follow this step-by-step guide to get this low-cost Multi Function Centre working.

Do you have another Brother product? Don't give up hope. Some have reported success having followed this tutorial.

**Note**: This tutorial assumes:[LIST]
[*]Device: Brother MFC210C
[*]Connection: USB direct from PC to MFC
[*]System: 32-bit Intel/AMD
[*]Operating System: GNU/Linux Ubuntu[/LIST][/INDENT]**[SIZE=3]Whoa! Can’t I skip this tutorial? It looks kinda… long.[/SIZE]**[INDENT]Would you rather use a script to setup your MFC-210C? Do you feel you don't learn anything from tutorials except that it takes too long to get anything done? Well this script's for **you**! [[COLOR=Blue]**CLICK HERE**[/COLOR]]("http://www.ubuntuforums.org/showpost.php?p=1024581&postcount=129") to get downloading.[/INDENT]**[SIZE=3]Preliminary procedures[/SIZE]**

**:: Please ensure the MFC is OFF ::**

Create a folder on the desktop and name it **mfc210c**:[LIST]
[*]Right-click the desktop and click **Create Folder** in the context menu
[*]Name it **mfc210c** (in lower case, this is important)[/LIST]**[SIZE=3]Step 1: Download from Brother[/SIZE]**

For the MFC210C, click each of the following links. Click **I Accept** when the browser loads the page:

[B][COLOR=Blue][COLOR=Black][[The CUPS wrapper]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc210c_1.0.0-1_i386.deb&lang=English_cups")]
[[The LPR Driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb&lang=English_lpr")][/COLOR]
[/COLOR][/B][INDENT]**Note**: The browser may ask to open or download the file. Don't open it. Download and save/move it in the **mfc210c** folder on the desktop. If the browser doesn't ask then it has likely been dropped on your desktop. Drag it to the **mfc210c** folder.[/INDENT][INDENT]**For other Brother machines:** Please make sure the appropriate drivers are downloaded. Check the Brother website for the [LPR Drivers]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html#de") and for the [CUPS Wrapper]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de").[/INDENT][B][SIZE=3]
Step 2: Install the C Shell[/SIZE][/B]

For the setup to work in Ubuntu the **C shell** is required. To install it we will need the help of the Terminal. From the menu bar above:[INDENT]**Applications &#8594 said:**
> Enter the following (or copy [Ctrl+C] the following command, paste it [Ctrl+Shift+V]) into the Terminal:

```
sudo apt-get install csh
``` 
and hit Enter.

This command will require the system password. **Do not close the Terminal at this point.**[INDENT]**Important:** if the **csh** (C shell) did not install extra repositories, sources for new programs, must be added.[INDENT][COLOR=Blue]**Dapper Drake**[/COLOR] users [[**click here**]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")].
[COLOR=Red]**Breezy Badger**[/COLOR] users [[**click here**]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")].
[/INDENT][/INDENT][B][SIZE=3]
Step 3: LPR Driver Install[/SIZE][/B][INDENT]**Note**: the LPR driver setup fails to create the appropriate folders in Ubuntu's file structure. The first two commands below correct this. To set up a Brother printer other than the MFC210C using these drivers -- change the second command below with **the appropriate printer name**. The capital letters used in the 2nd command are deliberate (remember: GNU/Linux's file structure is case sensitive).[/INDENT]```
sudo mkdir /var/spool/lpd
sudo mkdir /var/spool/lpd/**MFC210C**  (**replace with your printer name**)
sudo dpkg -i ~/Desktop/mfc210c/mfc210clpr-1.0.2-1.i386.deb
```[INDENT]**Note:** Please ensure both downloaded files are in the  **mfc210c** folder on the desktop. The last command above will fail otherwise if copied and pasted as is. More experienced users know how to use **dpkg**.[/INDENT][B][SIZE=3]
Step 4: Install the CUPS Wrapper[/SIZE][/B][INDENT]**Note**: this is another departure from the Brother setup instructions. Ubuntu has 'cupsys' instead of 'cups'. The first line corrects this difference by creating a necessary symbolic link.[/INDENT]Enter the following commands into the Terminal:

```
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
sudo dpkg -i ~/Desktop/mfc210c/cupswrappermfc210c_1.0.0-1_i386.deb
``` 
[B][SIZE=3]
Finalization[/SIZE][/B]

**:: Turn the MFC ON ::**

Open the printer panel to ensure the MFC210C is installed.[INDENT]**System &#8594; Administration &#8594; Printing**[/INDENT]Right-click the MFC120C and click “Properties”.[LIST]
[*]Print a test page from the General tab.
[*]Click the Paper tab and adjust the paper size accordingly, possibly replacing A4 with Letter.
[*]Review the choices under the Advanced tab and make adjustments.[/LIST][B][SIZE=4]
Fax Printing[/SIZE][/B][INDENT]To print using the fax aspect of the MFC the special drivers must be downloaded and installed. This tutorial assumes the **mfc210c** folder is still on the desktop.[/INDENT][B][SIZE=3]
Step 1: Download from Brother[/SIZE][/B]

For the MFC210C, click each of the following links. Click **I Accept** when the browser loads the page:

[COLOR=Black][B][[The Fax CUPS wrapper]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxcups-1.0.0-1.i386.deb&lang=English_gpl")]
[[The Fax LPR Driver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxlpd-1.0.0-1.i386.deb&lang=English_lpr")][/B][/COLOR]

Simply install each one through the Terminal:

```
sudo dpkg -i ~/Desktop/mfc210c/brmfcfaxcups-1.0.0-1.i386.deb
sudo dpkg -i ~/Desktop/mfc210c/brmfcfaxlpd-1.0.0-1.i386.deb
``` 
Open the printer panel to ensure the MFC210C fax driver is installed.[INDENT]**System &#8594; Administration &#8594; Printing**[/INDENT]Right-click the BRFAX and click “Properties”.[INDENT]NOTE: *The above is based on the Brother website's instructions. If you have had success in fax printing after following the steps outlined above, please notify me. Once I get confirmation I'll remove this paragraph. Until then kindly consider this section "experimental".*[/INDENT][B][SIZE=4]
Scanner Setup[/SIZE][/B][INDENT]Courtesy of **Lunixfanboy** the second part of the tutorial is now added: the scanner setup.[/INDENT]**[SIZE=3]Preliminary procedures[/SIZE]**

**:: Please ensure the MFC is OFF ::**


**[SIZE=3]Step 1: Download from Brother[/SIZE]**

For the MFC210C, click the following link. Click **I Accept** when the browser loads the page:[INDENT]For** [COLOR=Blue]Dapper Drake[/COLOR] **(6.06): **[[Sane Scanner Backend]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.1-0.i386.deb&lang=English_sane")]**
For** [COLOR=Red]Breezy Badger[/COLOR]** (5.10):** [[Sane Scanner Backend]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.0.2-1.i386.deb&lang=English_sane")]**[B]

For other Brother machines:[/B] Please make sure the appropriate drivers are downloaded. Check the Brother website for the [Scanner Backend]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html"). 
[/INDENT]Save the file, for the sake of consistency, to the **mfc210c** folder on the desktop. If the terminal is closed, please open it again:[INDENT]**Applications &#8594; Accessories &#8594; Terminal**[/INDENT]For** [COLOR=Blue]Dapper Drake[/COLOR] **(6.06):
```
**[COLOR=Blue]sudo dpkg -i ~/Desktop/mfc210c/brscan2-0.2.1-0.i386.deb[/COLOR]**
```[INDENT]**Dapper Drake users**: proceed to **Step 3** below.  The scanner should be installed. No need to do anything further.[/INDENT]For [COLOR=Red]**Breezy Badger**[/COLOR] (5.10):
```
**[COLOR=Red]sudo dpkg -i ~/Desktop/mfc210c/brscan2-0.0.2-1.i386.deb[/COLOR]**
``` 

[B][SIZE=3]
Step 2: Modifying the ‘libsane.usermap’ file[/SIZE][/B]

For [COLOR=Red]**Breezy Badger**[/COLOR] (5.10):

[COLOR=Red]Copy and paste the following code into the terminal:

[/COLOR] ```
[COLOR=Red]sudo gedit /etc/hotplug/usb/libsane.usermap[/COLOR]
``` [COLOR=Red]
When **gedit** appears activate the search feature:
[/COLOR][INDENT][COLOR=Red]**Search &#8594; Find...**[/COLOR][/INDENT][COLOR=Red] Enter this text in the Search box: 

[/COLOR]  [COLOR=Red]
This will be followed by a line which reads

[/COLOR]  [COLOR=Red]
followed by more hexadecimal values. We are only interested in the third one (the one right after the 0x04f9). Change **0x010f** to read **0x0161**.

Save and exit **gedit**.[/COLOR]   


**[SIZE=3]Step 3: Installing XSane[/SIZE]**

To use the scanner requires that Ubuntu's scanner software be installed. Copy the following code into the Terminal:

```
sudo apt-get install sane xsane
``` 

[B][SIZE=3]
Finalizing The Setup[/SIZE][/B]

**:: Turn the MFC ON ::**

For [COLOR=Red]**Breezy Badger**[/COLOR] (5.10)

[COLOR=Red] Copy the following code into the Terminal[/COLOR]

```
[COLOR=Red]sane-find-scanner | grep usb[/COLOR]
``` 
[COLOR=Red] It should report

[/COLOR]  [COLOR=Red]
(the values after libusb might be different, depending upon where the scanner is connected in the USB chain.)[/COLOR] 

For both** [COLOR=Blue]Dapper Drake[/COLOR] **(6.06) and** [COLOR=Red]Breezy Badger[/COLOR] **(5.10)

[B][SIZE=3]
Verify the install with XSane[/SIZE][/B][INDENT]**Applications &#8594; Graphics &#8594; XSane Image Scanning Program**[/INDENT][B][SIZE=3]
Setup Complete[/SIZE][/B]

Move the setup folder from your desktop to the trash if you so desire, or to some other location in the file system.


**[SIZE=4]Network Installation[/SIZE]**[INDENT]**Please note:** Contributions to help with network setups are detailed below. I do not have the MFC as an independant part of the network so I cannot test the following instructions. However these links are offered in hope of problem-free configuration.[/INDENT]**ubu69** has had success with a network setup. He's using a Debian system and believes this should prove helpful [[click here]("http://www.ubuntuforums.org/showpost.php?p=644004&postcount=21")].

**shawndoggie** notes success with the MFC attached to an XP box [[click here]("http://www.ubuntuforums.org/showpost.php?p=719307&postcount=40")].

**stalefries** has put together a nicely detailed howto in this thread. Network scanning! I just love the layout. [[click here]("http://www.ubuntuforums.org/showpost.php?p=935120&postcount=83")]


**[SIZE=4]Other Brother Products[/SIZE]**[INDENT]**Please note:** If you have a different Brother product don't go away dejected. There may be hope. Here's a list of some related success stories. With a bit of tweaking it seems this tutorial has proven helpful.[/INDENT]**Gray.** notes success with the MFC-620CN [[click here]("http://ubuntuforums.org/showpost.php?p=629121&postcount=19")]

**ubu69** notes success with the MFC-420CN in Debian [[click here]("http://ubuntuforums.org/showpost.php?p=644004&postcount=21")]

**crhooker** notes success with the MFC-3220C [[click here]("http://ubuntuforums.org/showpost.php?p=686523&postcount=32")]

**shawndoggy** notes success with the MFC-5440CN [[click here]("http://ubuntuforums.org/showpost.php?p=719307&postcount=40")]

**thedavis** notes success with the DCP-115C [[click here]("http://ubuntuforums.org/showpost.php?p=761313&postcount=47")]

**Mack1** notes success with the MFC-425CN [[click here]("http://ubuntuforums.org/showpost.php?p=772013&postcount=52")]

**bigken** notes success with the MFC-3820CN [[click here]("http://ubuntuforums.org/showpost.php?p=778035&postcount=56")]

**Bucanero** notes success with the MFC-5440N [[click here]("http://ubuntuforums.org/showpost.php?p=904967&postcount=73")]

**Jasman** and **Boelcke** both note success with the Brother HL-2040
[[click here]("http://www.ubuntuforums.org/showpost.php?p=1054771&postcount=131")] and [[click here]("http://www.ubuntuforums.org/showpost.php?p=1066795&postcount=133")]

[B][SIZE=3]
Other distros:[/SIZE][/B]

**bigken** notes success on Dapper Drake (testing) and SuSE 10.0 [[click here]("http://ubuntuforums.org/showpost.php?p=935744&postcount=85")]

**woot** notes success on Dapper Drake (final) with the MFC9180 using a slight modification of the setup process
[[click here]("http://www.ubuntuforums.org/showpost.php?p=1008624&postcount=119")]



**[SIZE=4]Linux Gurus[/SIZE]**

[SIZE=1]This tutorial was designed for new GNU/Linux users, who've recently switched from Windows. I make no apologies for that. There's nothing like a patient tutorial to help a reluctant new user to factor in the helpfulness of the Ubuntu forums as a reason to stick with this distro. If the tutorial seems too long please download the script listed at the top of the tutorial. Comments on its effectiveness are welcome. Thanks.[/SIZE]


_________________________

If you encounter an error in these instructions or added several steps to make it more complete, please post your findings/additions and appropriate modifications will be made. The above tutorial was designed for Ubuntu/Edubuntu and may not work with other Ubuntu-based releases. Feel free to request an explanation of the above procedures. The steps outlined above are modified from those offered at the Brother website in order to accomodate the differences between Ubuntu and a pure Debian system.

**Brother**® is a registered trademark.

[SIZE=1][COLOR=Silver](This HOWTO comes with absolutely no warranty, to the extent permitted by applicable law. However, the author will return on a regular basis to ensure the Brother files are still available and up-to-date and that the tutorial looks prettier and prettier.)[/COLOR][/SIZE]

---

### Post by BobSongs on 2006-06-21
Greetings, vincedesalpages.

Could I ask you for a favour? Would you kindly edit your post and remove the quoted text? It's a very long tutorial and it makes reading through the various posts much better without it, okay? Cool.

Now, did you turn off your printer and turn it back on? It seems to be fairly imporant that you go through the procedure as described. And this is a step often skipped by new users.

Oh, and are you using Dapper Drake? Or Breezy Badger. If you're using Drake you should be skipping about half the scanner section.

---

### Post by holycow32432 on 2006-06-22
guys, for the 420cn, don't forget that udev has no rules for setting up a device node for the scanner.

udev sees it but doesn't know what to do with it.

make sure to follow these instructions to create the proper udev rule for ubuntu for the 420cn and you will have scanning capability.

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html](http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html)

---

### Post by dgoran on 2006-06-23
Ok MFC420CN networked (router) sucessfully installed following mixture of post #1 and comon sense :). If anyone needs how to let me know.

-G

---

### Post by vincedesalpages on 2006-06-26
Hi there,

Concerning Scanning installation step with a MFC 5440CN, the error message is displayed when lauching XScan: "Failed to open device "brother2:bus;dev1': Error during device I/O".
FYI, Fax and Printer have been succesfully installed.
Thanks for the tutorial. Any help would he appreciated.

Cheers,
Vincent

---

### Post by BobSongs on 2006-06-26
When it comes to the Scanning section it's important that you include the version of Ubuntu you're using (Dapper Drake - 6.06 or Breezy Badger - 5.10). 

Thanks.

---

### Post by d351GuJu on 2006-06-28
I would like to thank you for making the script available for quick installation.
Although, the installation was fairly easy using the script, I did ran into a problem printing a test page.  Here are the specs:

**Printer:**  MFC-210C
**Distro:**  Kubuntu Dapper 6.06
**Interface:**  USB
**Exp. Using the printer:** 1 day (just received it!)  :D 

For those who have problems printing after the installation of the script and ran into a printer pausing/stopping itself after a few seconds, make sure that in *System Settings* > *Printers*, the MFC210C listed printer is using proper USB interface.

Here's what I did to correct that issue:

After selecting the printer, click on **Properties** Tab and go to **Interface** then select **Change...**, make sure **Local printer** is selected (for USB interface), and click **Next**.  After that make sure to select "Brother MFC-210C" under USB category, and then start the printer.
Now your printer should work!  :D ;)

---

### Post by BobSongs on 2006-06-29
Greetings, d351GuJu, and welcome.

I've just uploaded the installer script for Dapper Drake. Hope you find it more effective than using the Breezy version.

Enjoy. Comments welcome.

---

### Post by umuro on 2006-07-02
MFC7820N works with a few additional steps:
[http://www.ubuntuforums.org/showthread.php?p=1206934#post1206934]("http://www.ubuntuforums.org/showthread.php?p=1206934#post1206934")

---

### Post by bela42 on 2006-07-03
Hi all,

I have currently setup my MFC as a network printer and network scanner following this tutorial and using the brother drivers.

This solved occasional postscript errors and a general "pages get cut at the top" when using the MFC as network printer with, for instance a HP PostScript "driver" (aka ppd).

But now I experience an ominous "pages get cut at the bottom" issue when printing from OOo (, which worked well using a "compatible" ppd as described above!). All pages are generally shifted down by at leas 1/2 of an inch and the OOo printer settings only offers "letter" page size although I'm using A4 and am able to select this in Gnome printing properties OK. 

So, of course I could just use a different "driver" to print from OOo, but, honestly, I can't understand what the problem is and that's driving me nuts!

Anyone?

Thanks,
Bernd.

---

### Post by licklick on 2006-07-11
hello fairly new to unbuntu  i have 2 desktops running ubuntu dapper and a notebook running xp all wireless,a wireless dlink router/print server and a mfc210c connected to wireless router. i followed the instruction posted here to install the mfc210c drivers.I change the connection properties to unix printer(lpd)host was 192.168.0.1 which is router address(could very depending on router) and Queue to lp1 everything works fine all computers can access and printer, this might help somebody

---

### Post by BobSongs on 2006-07-11
Well, we're glad these instructions have garnered success. I'm sure others will be helped by your resources.

The success of this forum is based on respect and mutual assistance. So I hope that many other threads will prove as or more useful!

Happy surfing.

---

### Post by TheRabbit777 on 2006-07-18
[SIZE="5"]I have managed to get to step 2 and then things get hung up with errors

I enter the command in a terminal window "sudo apt-get install csh"
The end result I get is

Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)
Any suggestions as to how I can fix this[/SIZE]

---

### Post by BobSongs on 2006-07-19
> **TheRabbit777 said:**
> I have managed to get to step 2 and then things get hung up with errors

I enter the command in a terminal window "sudo apt-get install csh"
The end result I get is

Errors were encountered while processing:
 emacs21
 cedet-common
 eieio
 speedbar
E: Sub-process /usr/bin/dpkg returned an error code (1)
Any suggestions as to how I can fix thisOkay.
1. Are you using Ubuntu Linux, or some other version (Examples: Debian, SuSE)?
2. Are you using Dapper Drake, or some other version?
3. Have you changed your repositories or are they the original ones?
4. What model of Brother printer are you using?
5. Have you read through all the posts in this thread to see if someone might have an answer?
6. Do you have any broken packages on your system?

This appears to be a repository problem. But with so few details I can only hazard a guess.

Try repairing any broken packages in your system.

[INDENT]o System > Administration > Synaptic Package Manager
o Edit > Fix Broken Packages[/INDENT]

Here are links to broaden your list of repositories, that is: sources where your system can retrieve and install software.

[indent]o [How to add extra repositories]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories")
o [Adding Other Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu")[/indent]

---

### Post by Matchless on 2006-08-05
Bobsongs,
          Please forgive, but during my browsing to get my brother MFC-215c printer to work, I used your excellent howto and also a few hints and tips picked up on other forums and posts. In the process I really mangled your howto and rewrote it to focus on dapper kubuntu. If it is any use to you or anyone here it is:

_Howto:Printer Brother MFC215C Install on Kubuntu Dapper._

Download the following files from the [Brother Website]("http://solutions.brother.com/linux/en_us/"),   [CUPSwrapper]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc210c_1.0.0-1_i386.deb&lang=English_cups") , [LPRdriver ]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb&lang=English_lpr") , [Fax CUPSwrapper]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxcups-1.0.0-1.i386.deb&lang=English_gpl") , [Fax LPRdriver]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxlpd-1.0.0-1.i386.deb&lang=English_lpr") and the [URL="http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.1-0.i386.deb&lang=English_sane"]Sane Scanner backend
[/URL]
Note that some printer driver files for the MFC-215c are not yet ready and Brother suggests that the files for the MFC-210C are used used in the meantime. The direct links are for the latest at time of writing, so check the website for any updates and use those if available.

There are some preparations required, such as installing C Shell, Sane, (and Xsane if you use Ubuntu, Kubuntu uses Kooka) Some folder corrections needed to be done as the .deb files from the Brother site are for debian and was not compiled specifically for Kubuntu Dapper.
You can install the .deb files in many ways, dpkg -i, local repository or CD via Synaptic. I have used the Kubuntu shortcut from the gui to keep the instructions short and clear. You can also use krusader or konqueror for creating and moving files in root mode etc.

Preparations
Create a folder on the desktop, called “brother”, and put all downloaded files in that folder.
Use Synaptic to install csh (C Shell) and sane from the repositories
Create a new directory in /var/spool/lpd                 (Dapper needs lpd directory which is not present)
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups            (Dapper uses cups and file wants cupsys - link)

Install the printer drivers: (Works + tested)

NB: Ensure printer is switched off

Right click on the mfc210clpr-1.0.2-1.i386.deb file and select Kubuntu Package Menu, Install Package
Right click on the cupswrappermfc210c_1.0.0-1_i386.deb file and select Kubuntu Package Menu, Install Package

Switch the printer back on

In the menu go to System Settings, Printers
If the printer is connected to the same PC then the driver has already been installed and selected
Right-click the MFC210C and click “Test Printer”. See if test page is received

If the printer is shared, say with another PC using Windows XP, Add printer, SMB shared printer and follow the screen instructions. Samba must be installed. It works well sharing with Windows.

Camera media card reading;
You can just insert the media card and it will appear as a usb flash disk on Kubuntu and just copy, read or whatever from and to it. Just do not change the special file structure that your camera created as it may make the card unusable in your camera.

Fax Printing  (Not been able to get this to work yet)

To allow fax working special drivers must be downloaded and installed. 
Install both in this sequence:

NB: Ensure printer is switched off
The order of installing the two drives is important, first lpd, then cups.

Right click on the brmfcfaxlpd-1.0.0-1.i386.deb file and select Kubuntu Package Menu, Install Package
Right click on the brmfcfaxcups-1.0.0-1.i386.deb file and select Kubuntu Package Menu, Install Package


Switch the printer back on

In the menu go to System Settings, Printer

 Right-click the BRFAX and the fax printer is there but now no faxing from the PC works as per the Brother website.

Scanner Installation: (works and tested)

Ensure you have already installed sane as per the beginning of this howto.
You must additionally install a special driver which is the Brother backend for sane scanner which is used by Kooka (Kubuntu).

Ensure that printer is switched off

Right click on the brscan2-0.2.1-0.i386.deb file and select Kubuntu Package Menu, Install Package

Switch the printer on

Run Kooka in root  (kdesu kooka) to check if the installation works (or Xsane if using Ubuntu)
The reason for this is that the scanner MFC-215C is quite new and not yet present in the config files and you can just add these two lines. To fix this go to /etc/udev/rules.d/45-libsane.rules and find the 2 lines starting with #Brother MFC-210C , copy these lines below and change the model number to 215 and the product id to 0193 and reboot. Kooka should now run as ordinary user from the menu. This probably is more dapper related. And lsusb in the terminal can give you the scanner details as well

# Brother|MFC 210C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="664", GROUP="scanner"
# Brother|MFC 215C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0193", MODE="664", GROUP="scanner"



Network Installation (printer own IP) (Not tested yet)

This is how to get the printer to just be on the network (not attached to a print server). This will only work with models that have a built-in ethernet port. (MFC-425CN). The model MFC-215C will have to have an external network driver module (jetdirect) attached. Otherwise it will have to use another PC as a print server.

You need to know the IP address of the printer. The printer can tell you this (check out the instruction booklet as the command combinations may be different for different models.) 

Open your browser to CUPS by entering [http://localhost:631/](http://localhost:631/). Click "Manage Printers." 

If everything went well, you should see your printer in the list. 

Select "Modify Printer." The important step is to select the device for the printer. Choose "LPD/LPR Host or Printer." 

Enter lpd://xxx.xxx.xxx.xxx in the window (where the xxx's are the printer's IP address). 

Send it a test page. You can configure paper size from CUPS (it seems to default to A4). 

From here you can also set your print manager to use CUPS if you so desire and it will also print on the network. 


Printer sharing on PC in home network: (works & tested Kubuntu to XP only)

First example  Printer installed directly to a Windows XP PC and shared with a Kubuntu PC over the network. This means drivers for the MFC-215C must be installed on both PC's, XP and Kubuntu.
Enable the Printer sharing in Windows and give the printer an unique share name i.e Brotherxp

Now in Kubuntu go to Menu System Settings, Printers, Add printer, Add printer wizard opens and you need to complete this. Next, enter nothing here(security), next and click Scan.
If you PC can see the Windows PC it will show the workgroup name and the PC name. Enter these in Workgroup, Server and put the Printer share name you gave in XP in Printer, Next.
KDE will now build a database of drivers and you can select Brother, scroll down to MFC-210C (which you have installed in the first part) , Next, Test page and you are working.

Second example Printer is installed on the Kubuntu PC and tested. Now the same procedure is followed above from the second kubuntu PC. The PC is picked up on scan and the wizard is completed, but it does not print (This yet has to be sorted out)


Scanner over network (printer has own IP) (Not tested yet)

It is assumed that the scanner drivers and sane have been installed as shown at the beginning of this howto.
To use your machine as a network scanner, you need to set a friendly name, model name and IP address or node name for the driver:  

using IP address:
brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME ip=xx.xx.xx.xx
or
using node name
brsaneconfig2 -a name=FRIENDLY-NAME model=MODEL-NAME nodename=BRN_xxxxx

Example
brsaneconfig2 -a name=BROTHER-SCANNER model=MFC-215C nodename=BRN_XXXXX

You can check the result by running the command:
brsaneconfig2 -q

If the setting is done correctly, you will see the result as below:
	0 BROTHER-SCANNER "MFC-215C" N:BRN_XXXXX

Now run Kooka ( Xsane if using Ubuntu)
	And scan something, click Acquire Preview and hope it works...

---

### Post by Jeef on 2006-08-05
BobSongs... =D>

You, my friend, are simply amazing! \\:D/

I have tried to get my MFC-5440CN printer working over the network for *ages upon ages* in numerous UNIX-esque operating systems (from FreeBSD to Debian to Ubuntu, now), using Brother's official drivers one way or another. I have gotten close (even going as far as to manually send PostScript files over JetDirect via telnet), in the past, but I have never actually had success. Today, after reading your guide, however, I finally figured out the two little details I had always missed: the C shell requirement (I should have vim'd the scripts, probably :)), and the lpd directory that had to be manually created. Now, thanks to your wonderful help, my networked MFC-5440CN now works flawlessly via JetDirect! Thank you!

I doubt I can get SANE working over the network (I have never used it, so I'm not sure of its limitations), but I will give it a shot tomorrow, perhaps, and report back with my findings. :)

---

### Post by BobSongs on 2006-08-06
> **Matchless said:**
> Bobsongs,
          Please forgive...Forgive? My goodness! Thank-you very, very much for your addition. Perhaps I could post it to the front page? Of course, I will credit you for the hard work.

Your post is much appreciated. No need to ask forgiveness! You did good. =D> I will update my tutorial to accomodate Kubuntu.

Please note: this tutorial has grown in leaps and bounds because of contributions by friendly people the world over. It no longer resembles the simple thing it was when I first started it.

Thanks, Matchless.

---

### Post by BobSongs on 2006-08-06
> **Jeef said:**
> BobSongs... =D>

You, my friend, are simply amazing!
As you well know it really isn't me. I just downloaded the files from Brother. Hey: someone showed me where they were for that matter. I worked out some bugs for the basic install. After posting a very simple tutorial a huge crowd of buddies turned it into something useful.[QUOTE=Jeef]I have tried to get my MFC-5440CN printer working over the network for *ages upon ages* in numerous UNIX-esque operating systems (from FreeBSD to Debian to Ubuntu, now), using Brother's official drivers one way or another. I have gotten close (even going as far as to manually send PostScript files over JetDirect via telnet), in the past, but I have never actually had success. Today, after reading your guide, however, I finally figured out the two little details I had always missed: the C shell requirement (I should have vim'd the scripts, probably :)), and the lpd directory that had to be manually created.[/quote]My first attempts also proved fruitless. As a complete and utter noob I read the output at the command prompt to see my errors. **bash** told me what was missing. So, I made the corrections and tried again. *Eventually* it worked. I was impressed with the command line's ability to explain itself in better terms than "Bad command or filename".
[QUOTE=Jeef]Now, thanks to your wonderful help, my networked MFC-5440CN now works flawlessly via JetDirect! Thank you![/quote]Hey: thanks for the kind and generous words. And I wish to share them with the community that helps make this tutorial useful to thousands! Thanks![QUOTE=Jeef]I doubt I can get SANE working over the network (I have never used it, so I'm not sure of its limitations), but I will give it a shot tomorrow, perhaps, and report back with my findings. :)[/QUOTE]When you get xsane working over the network I'll gladly add your notes to the main tutorial (or create an appropriate link). You'll be fully credited for your hard work.

---

### Post by Jeef on 2006-08-08
> **BobSongs said:**
> When you get xsane working over the network I'll gladly add your notes to the main tutorial (or create an appropriate link). You'll be fully credited for your hard work.
Hello, again. It turns out that getting this beast to run over the network is actually quite easy; in fact, it might even be easier for you than the USB route, if you have a printer that supports networking, understand the gist of networking, and have a spare RJ45 jack on your switch!

I will provide a quick summary of what I did; however, Brother actually has very nice documentation on this process, so I will keep my summary simple!

**Brother's Instructions**
Brother's instructions for setting up network scanning can be found here:
[http://solutions.brother.com/linux/sol/printer/linux/sane_install-net.html#2](http://solutions.brother.com/linux/sol/printer/linux/sane_install-net.html#2)

**My Instructions (nearly identical)**
First, obtain the latest sane driver release from solutions.brother.com. For 32-bit Debian/Ubuntu users, here is Brother's brscan2 package:
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.1-0.i386.deb&lang=English_sane](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.1-0.i386.deb&lang=English_sane)

Next, download the driver, and move it somewhere safe that you will remember; personally, I archive packages in /var/cache/apt/archives (since apt-get does this, as well) for future reference. To accomplish this feat, one might download the driver to his or her desktop in GNOME or KDE, and execute:
> $ sudo mv ~/Desktop/brscan2-0.2.1-0.i386.deb /var/cache/apt/archives
Then, install both sane and xsane to meet Brother's driver's dependencies:
> $ sudo apt-get install sane xsane
Continuing on, install Brother's scanner driver from wherever you chose to save it; I chose /var/cache/apt/archives:
> $ sudo dpkg -i /var/cache/apt/archives/brscan2-0.2.1-0.i386.deb
After it is installed, configure the driver to use your networked printer's settings. If you are unsure of how your printer's networking is currently configured, either check your printer's "LAN Settings" sub-menus, or simply print out a "Network Config" report (this function is built into the printer). Once you have obtained your printer's NetBIOS host name**[1]**, IP address**[1]**, and model name**[2]** execute the following command:
> $ sudo brsaneconfig2 -a name=<NetBIOS Host Name> model=<Printer Model Name> ip=<IP Address>
For instance, because my printer is a MFC-5440CN, and is configured to use the static IP address 10.0.0.5, with the static NetBIOS host name "MAMIMI", I executed:
> $ sudo brsaneconfig2 -a name=MAMIMI model=MFC-5440CN ip=10.0.0.5
At this point, you should have a working driver. To test your configuration, you should attempt to query your networked scanner using Brother's sane driver configuration utility:
> $ brsaneconfig2 -q | tail -n 2
Your output should look something like this:
> jeff@chii:~$ brsaneconfig2 -q | tail -n 2
Devices on network
  0 MAMIMI              "MFC-5440CN"        I:10.0.0.5
Optionally, I would also recommend using the same utility to ping your printer a few times (you may stop the pinging prior to ten attempts using CTRL+C):
> $ brsaneconfig2 -p
Your output should resemble this:
> jeff@chii:~$ brsaneconfig2 -p
test MAMIMI
ping 10.0.0.5 -w 10

PING 10.0.0.5 (10.0.0.5) 56(84) bytes of data.
64 bytes from 10.0.0.5: icmp_seq=1 ttl=60 time=2.95 ms
64 bytes from 10.0.0.5: icmp_seq=2 ttl=60 time=2.07 ms
64 bytes from 10.0.0.5: icmp_seq=3 ttl=60 time=3.77 ms
64 bytes from 10.0.0.5: icmp_seq=4 ttl=60 time=2.08 ms
64 bytes from 10.0.0.5: icmp_seq=5 ttl=60 time=2.63 ms
64 bytes from 10.0.0.5: icmp_seq=6 ttl=60 time=2.06 ms
64 bytes from 10.0.0.5: icmp_seq=7 ttl=60 time=2.95 ms
64 bytes from 10.0.0.5: icmp_seq=8 ttl=60 time=2.07 ms
64 bytes from 10.0.0.5: icmp_seq=9 ttl=60 time=2.10 ms
64 bytes from 10.0.0.5: icmp_seq=10 ttl=60 time=2.50 ms

--- 10.0.0.5 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9040ms
rtt min/avg/max/mdev = 2.068/2.523/3.772/0.541 ms
With this said, the only thing that you have left to do is fire up XSane and perform at least a scan preview to see how your hard work has paid off. To do this, within GNOME, you should navigate through the following menus:

*Applications* -> *Graphics* -> *XSane Image Scanner*

With XSane open, click the large "Acquire Preview" button in the preview window. Congratulations! You now have a working Brother network scanner. :)

**[1]**: You may also configure your printer using an alternative method, which revolves around using a "node name" rather than an IP address and NetBIOS host name. I do not know much about this (since I have no use for it); so, if you need to use this method, instead, please use Brother's instructions (which I linked to, earlier) to fill in for this portion of the installation.

**[2]**: As far as I know, the model name of your printer should be entered into brsaneconfig2 exactly how it is seen on the printer itself; for instance, a "MFC-5440CN" is entered as "MFC-5440CN"; you do not need to remove the hyphen or format it any differently than usual. If you are unsure if your multifunction printer is supported, or want to verify that you are entering its model name properly, use the following command to list all of the supported models:
> $ brsaneconfig2 -q

---

### Post by whistlerspa on 2006-08-08
Well I don't know why but I followed all these instructions and my printer still won't print a test page or anything else. It just sits there until it times out. The scanner works fine though.

It's set up as BRFAX , says it's ready and is set to 

CUPS Printer (ipp)
URL ipp://usb/dev/usb/lp0

All of which seems corrrect. Oh now it says the printer is not connected (but it is) , now it says connecting to usb port ... 

BH what is going on here:sad:

---

### Post by BobSongs on 2006-08-08
Did you have your MFC off when you installed the drivers?

I can't emphasize this too much. Leaving it on can do some pretty wonky things. 

I once forgot to follow my *own* instructions. The printer wouldn't work. Here's what I did to straighten it out.

System > Administration > Printing > Right-click MFC210C > Properties > Connection Tab > Printer Type = Local Printer > Use Detected Printer = Brother MFC-210C.

See if that helps.

---

### Post by whistlerspa on 2006-08-09
Tried all that - nothing. I reinstalled all the drivers with the printer off still no good. It works fine in Windows XP so it's not a hardware or cable fault.

WP

---

### Post by whistlerspa on 2006-08-09
OK I'm a complete FW on this one - i hadn't installed the printer drivers -only the fax drivers  - itworks now:rolleyes:

---

### Post by olking on 2006-08-09
Hi I just ran the procedure as listed to install my mfc210c and everything went through beautifully.
However when I did system>admin>printing and asked it to print a test page it didnt.
A job is showing in the print queue for the mfc210 but nothing happens.
Any advice please

---

### Post by sdb2028 on 2006-08-09
I have a MFC420CN which I am having trouble getting to work. I read threads explaining "how to", unfortunatly I had my printer on when I installed the LPR and CUPS drivers. My computer recognizes the printer, displaying an icon when I click on Computer in the places column of the menu. When I go to System/Administation/Printing - all I see is an icon for "New Printer" - I click on "New Printer" and the wizard opens and asks to use detected printer where my printer is listed in the box. I click on forward and my printer is not in the model list. I have try'd to reinstall the drivers but the system say's they are already there. I am at a dead end. How do I remove the drivers and start over or is there an easier way to correct the problem?

---

### Post by sdb2028 on 2006-08-10
Got my MFC420CN Printer (printer part) working finally, however the scanner part wont open when I open the xsane image scanner application. It say's "Failed to open device 'brother2:bus1;dev1':Error during device I/O." Any helpfull suggestions would be appreciated.

---

### Post by BobSongs on 2006-08-10
What version number of scanner driver did you use to install it on your Dapper Drake Ubuntu?

---

### Post by sdb2028 on 2006-08-10
I used - brscan2-0.2.1-0.i386.deb

---

### Post by BobSongs on 2006-08-10
That's the right driver, all right. Having the scanner 'on' when installing either the printer drivers or the scanner drivers just wreaks havoc. I've made that mistake several times so far. I think I'll change the tutorial and put it in huge red text.

In the mean time I am not sure what to tell you. Have you tried ```
lsusb
```to see whether the printer shows up in the list?

---

### Post by sdb2028 on 2006-08-10
Yes, I did have the printer off when I installed the scanner driver, I made that mistake earlier when installing the printer drivers. Took forever to get that fixed. The printer works fine now, just no scanner. Here is the out-put from lsusb : 
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 002: ID 04f9:0162 Brother Industries, Ltd
Bus 001 Device 003: ID 046d:c402 Logitech, Inc. Marble Mouse (2-button)
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
I also ran  sane-find-scanner | grep usb, here is the out-put:
found USB scanner (vendor=0x04f9, product=0x0162) at libusb:001:002
Here is the exact error when I try to open XSane Image Scanner:
[ATTACH]14111[/ATTACH]

---

### Post by sdb2028 on 2006-08-10
near as I can figure, XSane is trying to open Bus2,Dev1 and my MFC Printer unit is listed as Bus1,Dev2, any ideas?

---

### Post by BobSongs on 2006-08-10
My printer is set to ```
Bus 005 Device 002: ID 04f9:0161 Brother Industries, Ltd
```You may have to connect to an IRC to get an answer there. Have you ever done so?

---

### Post by sdb2028 on 2006-08-10
I don't think so, not sure what you are speaking of.

---

### Post by BobSongs on 2006-08-10
Let's take this off the main thread and I'll PM you.

---

### Post by olking on 2006-08-11
I just tried the
 
ystem > Administration > Printing > Right-click MFC210C > Properties > Connection Tab > Printer Type = Local Printer > Use Detected Printer = Brother MFC-210C.

and it worked perfectly.
Thanks to Bob songs for that:D

---

### Post by kodachrome64 on 2006-08-20
Hi this how to worked great and I'm printing happily from ubuntu dapper.

Anyone else have this problem?

Problem is now I can not install from Synaptic or aptitude in the terminal anymore!
I'm pretty sure it has somthing to do with the Brother lpr/cups install I did per this how-to. I used the mcf4800 drivers for my printer. This could be the cause?

Errors I get when using (Aptitude) in the terminal.

The following NEW packages will be installed:
  mtools syslinux
0 packages upgraded, 2 newly installed, 0 to remove and 125 not upgraded.
Need to get 0B of archives. After unpacking 983kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate file for the mfc4800lpr package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
adam@ubuntu-macbook:~/Desktop$

I've tried reinstalling the lpr driver to fix the issue but only get this error.


adam@ubuntu-macbook:~/Desktop$ sudo dpkg -i mfc4800lpr-1.1.2-1.i386.deb
Selecting previously deselected package mfc4800lpr.
(Reading database ... 78527 files and directories currently installed.)
Preparing to replace mfc4800lpr 1.1.2-1 (using mfc4800lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc4800lpr ...
/var/lib/dpkg/info/mfc4800lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing mfc4800lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc4800lpr-1.1.2-1.i386.deb
adam@ubuntu-macbook:~/Desktop$

Thanks for any help on this!

Doing all this on a Macbook via Pararells. The printing over a network is working great. Just super stuck on this issue described above.

---

### Post by Boberg on 2006-08-20
> **olking said:**
> I just tried the
 
ystem > Administration > Printing > Right-click MFC210C > Properties > Connection Tab > Printer Type = Local Printer > Use Detected Printer = Brother MFC-210C.

and it worked perfectly.
Thanks to Bob songs for that:D

I also looked there after MANY hours of ](*,) Now my DCP-115C prints perfectly when connected to my amd64 laptop. Many thanks to the person who wrote about that option!:KS

---

### Post by BobSongs on 2006-08-25
> **olking said:**
> I just tried the
System > Administration > Printing > Right-click MFC210C > Properties > Connection Tab > Printer Type = Local Printer > Use Detected Printer = Brother MFC-210C.

and it worked perfectly.
Thanks to Bob songs for that:DIt's been added to the main tutorial. I thought of it in the past but now I figure I'd better add it.

---

### Post by Matchless on 2006-08-26
Bobsongs,
         I have tried to get the PC-fax function working on my Brother MFC-215C after discovering some more info on Brothers site. I think I am close but need to know if BRFAX can print a test page or not - can anyone help?


Below is my howto so far, in case someone else also want to try:

[U][B]PC-Fax Working Brother MFC-215C  (Nearly working!)
[/B][/U]
Thanks to Brothers latest information on their website, the information below was compiled and a word of thanks to them for really getting into linux support. 
Ensure that SUN JAVA is installed as this runs the applet  /usr/local/Brother/fax/brmfcfax.jar, which is the dialup gui for your PC-Fax. Test this by going to the file and double clicking it. It may be necessary to go to konquerer and set the file association .jar for Java.
Now while the PC is switched off, install the two special drivers from the Brother website. The order of the driver installation is important, first lpd, then cups.
Install both in this sequence:

Right click on the brmfcfaxlpd-1.0.0-1.i386.deb file and select Kubuntu Package Menu, Install Package
Right click on the brmfcfaxcups-1.0.0-1.i386.deb file and select Kubuntu Package Menu, Install Package

Switch the printer back on

In the menu go to System Settings, Printer and you should see another printer installed called BRFAX.

This printer is not used to print faxes directly. It is used by the “brpcfax” utility script file. To send a fax, you must use the “brpcfax” utility to process your print jobs and you can only use a postscript file.

a) Use “print to file” from your application to generate a postscript file called i.e “testfax.ps”
b) Right click the testfax.ps file and select “Open with”  and now click “Send As Fax”, the dialup screen gui should come up, enter fax number and click Send.

Before you can do this Konquerer must first be configured

1)Open Konquerer
2)Go to Settings, Configure konquerer
3)Click file associations
4)Type “ps” in the search box and select “Application”-- “Postscript” from the list
5)Click “Add” and type “brpcfax” and click OK
6)Select the new “brpcfax option and click 'Edit”
7)Select the Application tab
8)In Command line enter: brpcfax -P BRFAX -o PAPER=A4
9)For the Name enter Send As Fax
10)Click on the blank Icon, System Icons, select printmgr (looks like a fax)
11)Click OK and save

Everthing seems to be in place and created, but the dialup gui does not appear when the fax is sent.
The file to be printed can be found queing in the BRFAX, but the printer does not respond at all. Does anyone know if a test page can be printed from BRFAX, as I cannot get BRFAX to do anything? By the way normal printing works.
Please can anyone else test this on any brother printer??

---

### Post by ignorance.is.evil on 2006-08-28
Fantastic! Solved my problem, thanks!


> **Mr.Mechano said:**
> Hi there!

Installing the new Dapper 6.06 my MFC-425CN (that use the MFC-210C driver) started to print in reverse order from last to first page on mutiple pages documents.

I wrote to Brother service  and after 4 days I received the response from Japan.
Now the printer works correctly.

[HTML]Dear Sir/Madam,

We could make this issue happen at our side too.

The "reverse order print" you said is actually correct
due to its original specification of the CUPS.
The CUPS you had been using so far was not supporting it.


If you want to change it, please do the following.

1.Open the file MFC210C.ppd which is located under the directory
"/etc/cups/ppd/".

2.Delete the line "*DefaultOutputOrder: Reverse".


Best regards,
Brother Solutions Center[/HTML]

---

### Post by BobSongs on 2006-08-28
> **Matchless said:**
> Bobsongs,
         I have tried to get the PC-fax function working on my Brother MFC-215C after discovering some more info on Brothers site. I think I am close but need to know if BRFAX can print a test page or not - can anyone help?I'll give your tutorial a test run. I've got Ubuntu, Kubuntu and Xubuntu on this PC and the MFC-210C is connected directly via USB and it's connected to the phone line.

I'll have to locate brmfcfax.jar because there's no link to the file. But other than that... here goes!

**Edit:** Okay. I get the pop up box for the phone number. So I'm a step further ahead. However, the files I try to fax just get stuck in the list of faxes to send. So... I'm  no further ahead... but I'm inspired!! I'm not giving up right away. I think I may test this whole procedure in SuSE 10.1.

---

### Post by Matchless on 2006-09-08
> **BobSongs said:**
> I'll give your tutorial a test run. I've got Ubuntu, Kubuntu and Xubuntu on this PC and the MFC-210C is connected directly via USB and it's connected to the phone line.

I'll have to locate brmfcfax.jar because there's no link to the file. But other than that... here goes!

**Edit:** Okay. I get the pop up box for the phone number. So I'm a step further ahead. However, the files I try to fax just get stuck in the list of faxes to send. So... I'm  no further ahead... but I'm inspired!! I'm not giving up right away. I think I may test this whole procedure in SuSE 10.1.

BobSongs,
          Thanks, let us know if you find out anything more. I have a suspician that BRFAX does not work, but if you can get it prove if it can run under SuSe then maybe we are a step closer. It is a funny that no BRFAX is found in the drivers list after the installation. I can only create the BRFAX printer when installing the drivers and if I try to change anything afterwords it acts as if not installed.

---

### Post by BobSongs on 2006-09-08
Okay: here's the BRFAX update.

I have just purchased a ... MacBook Pro. 8-[ (Don't throw anything at me!) It's got an Intel CoreDuo... so it's still kindof a PC. ;-)

I have given over the PC with Ubuntu to the family to use and I'm using this new laptop exclusively. So putting SuSE on would be frowned upon by my wife and family who've grown very accustomed to Ubuntu Linux.

So. I must leave the tinkering to brave users who will come after me. I think this thread has served its purpose. Many questions have been answered and new users should be able to set up their printers without trouble. Still, I will occasionally inspect it to see what advances are added to this thread, including a fixed BRFAX. :-)

I will be committing myself to learning Mac OS X for the next few months. When OS X 10.5 is released I will upgrade and triple boot Mac OS X, Ubuntu Linux 6.06.1 and Windows XP Pro SP2 (no "vista" for me).

If someone wants to monitor this thread please PM me and we'll talk it over.

---

### Post by Lary Grant on 2006-09-12
I followed the instructions here a few weeks ago (using your shell script) and it worked perfectly!  However, recently scanning stopped working.  When I go into xsane and click Scan, I get "Failed to start scanner - invalid argument".  I am not pressing any button on the scanner itself.

The only change I can think if that I've done recently is install wine.  Would that interfere with the scanner?

Anyway, I can't seem to get the scanner to work again.  I re-ran the shell script and that didn't help.  I also followed the instructions on this site: [http://solutions.brother.com/linux/sol/printer/linux/sane_install.html](http://solutions.brother.com/linux/sol/printer/linux/sane_install.html) (which I hope did not make things worse... I'm a bit puzzled because it had me modifying /etc/fstab and perfroming mounts, which I don't think your shell script does).

Anyway... how do I get out of this mess!!?

---

### Post by BobSongs on 2006-09-13
I'm not exactly sure. I've had troubles with the scanner when I didn't go by my own tutorial and left the MFC **on**. That really messed things up so bad that only a re-install solved the problem. I should have followed the script because it reminds me to switch it off! lol!!

I find Ubuntu is a bit like Windows 98. Some things just go ... odd after a while. Why... is a mystery to me. I just set things up in such a way that backing up my info is easy and most of my data (photos, files, downloads) are on another partition. A full re-install takes less than about 3 hrs. That's worth my time when something as useful as the scanner up and mysteriously dies.

Beyond that? I'm afraid I'm not a guru. "If at first all goes off track, login, reboot or re-install" is my motto.

---

### Post by tonywhelan on 2006-09-13
I have just posted a new thread on Setting up a networked Brother MFC5840CN on Ubuntu 6. Yet to be approved by the moderator. 

But just want to say that the solution I adopted owes a lot to this thread here as well as a couple of other tips I picked up on the net., Thanks folks.:)

---

### Post by Matchless on 2006-09-22
Hi,
    I have just posted a new thread on installing the Brother MFC-215C on Kubuntu Dapper. Yet to be approved by the moderator. BRFAX is also working, just search for MFC-215C under the howto's. BobSongs and the Brother Solutions Centre are thanked for their contributions.

---

### Post by BobSongs on 2006-09-23
> **Matchless said:**
> Hi,
    I have just posted a new thread on installing the Brother MFC-215C on Kubuntu Dapper. Yet to be approved by the moderator. BRFAX is also working, just search for MFC-215C under the howto's. BobSongs and the Brother Solutions Centre are thanked for their contributions.

You got the fax working too? Way to go! Heehee. Excellent. I will eventually try it on my PC. However it's not in my house at the moment. So I'm going to have to wait until it returns to try out the fax end of things.

In the mean time getting the scanner and the printer to work is wayyy more than I ever expected. I bought it before I downloaded Ubuntu and never expected half my periferals to work.

---

### Post by Matchless on 2006-09-23
Brother support helped me with the fax and it also works from another PC on the same lan. Just for info there are firmware updates on the Brother site as well.

---

### Post by wgaprotest on 2006-09-24
Hey, fellow-Canuck!

Everyone's right: this is a great howto. The only thing I had to do differently in my origianl installation was to use the --force-architecture option to get the lpd and cups working, as I'm running an amd64 system. I never could get the scanner working, and didn't test the fax part, as I don't fax often, and I had bigger problems to fix with that install, like trying to get my lamp working prior to installing mythtv. That's the end goal, as this 7-mth-old pc was always intended and built to be an htpc.

Two tries wtih the ubuntu server package later and it's great. I prefer kubuntu, but am presently back in gnome because I've installed this printer so many times on so many operating systems I got cocky-and-forgetful. I searched the thread, saw one of your replies (quoted below), and yep, I forgot to turn it off, too. <sigh> I tried to follow your remedy, and have problems with the remedy, and a few other things I've tried, so am hoping you can help me. Here's your advice:

"Did you have your MFC off when you installed the drivers? I can't emphasize this too much. Leaving it on can do some pretty wonky things.

I once forgot to follow my own instructions. The printer wouldn't work. Here's what I did to straighten it out.

System > Administration > Printing > Right-click MFC210C > Properties > Connection Tab > Printer Type = Local Printer > Use Detected Printer = Brother MFC-210C."

The problem is that there is no MFC210C to right-click in Printing. The only item that does exist is the Add Printer. In addition, my /usr/lib/spool/lpd/MFC3210C directory is still empty, no brlpdwrapper exists, and sure enough, when I tried to remove the package with the appropriate dpkg command, shell told me it wasn't installed. 

So of course I try to install it, but all I got in response (at first) was this:
"Preparing to replace mfc210clpr 1.0.2-1 (using mfc210clpr-1.0.2-1.i386.deb) ...
Unpacking replacement mfc210clpr ...
Setting up mfc210clpr (1.0.2-1) ...
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1.0' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so' to `/usr/lib/libbrcompij2.so.1.0.2': File exists"

I thought these links could be blocking something, so I did remove them, but it only helped to a small degree. Yes, after it had haleped a bit, I went on to the second part of your howto (the cupswrapper part) but still nada. I tried a few other things, but finally decided that there was no help for it: do the searches for key items in the file system (e.g. mfc and br as part of the name) and removing all the files by hand -- (I've had to do this in windows and its registry, after brother tech support told me to after virus packages ruined an install, and it's an exhaustive process, but I usualy go even further in terms of cleaning my windows). I'm extremely careful when I do this type of operation.

Is there anything else you can think of, like configuration files that have been changed, and I'll need to edit? Any other pointers? I really don't think there's any help for it but to try and remove it completely from the system, but the usual linux ways won't work if it's not properly installed in the first place.

---

### Post by wgaprotest on 2006-09-24
k, removing all the individual files I could find, by hand, and it worked to the point where I could install the printer to the way I remembered it. However, there is that final step: getting it to work under cupsys through the web interface, that I couldn't remember how to do properly. 

The web interface at localhost:631 gives lots of pps problems because it asks for passwords, and no passwords work, sening the user into an endless loop. So I tried following the instructions in this thread, after checking with the debian readme file: [http://ubuntuforums.org/showthread.php?t=263180&highlight=cupsys+password](http://ubuntuforums.org/showthread.php?t=263180&highlight=cupsys+password)

Now I'm worse off than before I tried to follow the instructions in the thread, as I can get to the localhost:631 site, but when I click the admin tab, or any other tab, firefox and konqueror tell me they can't access the localhost:631 site. The printer won't print a test page when configured as a local-only lpd printer or under the still-incomplete cupsys installation. Yes, I've reverted my /etc/cups/cupsysd.conf back to the original one. 

What am i doing wrong?

P.s. latest update: still don't have a clue has to what I did wrong and -actually - how i fixed it, but it's finally printing a test page under cups...so that's what matters.

Once again, bobsongs: thank you! you've done a lot for us in the community. I've now paid over three grand (probably closer to 4 grand) for the home theatre pc, counting the monitor that replaced the even-more-expensive-hdtv-that-died, but I learned awhile back not to spend lots of $ on printers, as they'll become obsolete faster than they wear out, so you can't get printing supplies anymore. And I will say this for brother: they give great tech support. They even replaced the mainboard for free even though it was 2 days after the warranty expired. I'm much happier with the printer than I was with the hp or epson printers I've had.

---

### Post by retep57 on 2006-09-25
hmmm  i have brother mfc-215     the 210 srcipt set up ok    , says installed but no print  :(  thanx anyway but am  effecetively innefective in tersm of printer, ie no can print :(

---

### Post by BobSongs on 2006-09-26
> **retep57 said:**
> hmmm  i have brother mfc-215     the 210 srcipt set up ok    , says installed but no print  :(  thanx anyway but am  effecetively innefective in tersm of printer, ie no can print :(As you've already figured out -- the script for the MFC-210C only applies to this specific printer. I am not certain how much the MFC-215C deviates from the 210 design. For any other Brother device the only other option, currently, is to follow the tutorial.

This tutorial takes just a few minutes to follow. Links are given to the Brother website (to the Linux drivers, not just to some home page) if you have a different machine.

If I get any further reports that MFC-215C users are trying to use this script on their 215s then I'm going to have to pull the script. I'm on my way back to that post to warn future 215 users **not** to use it.

---

### Post by bigken on 2006-09-26
Yo Bobsongs I just downloaded the new drivers for my mfc3820cn 
installed edgy Knot3 folllowed your tutorial to point of making the folders then just double clicked the driver files installed using Gdebi
went into printer changed from usb to unix lpd printer and added the static ip address and hey presto it printed 1 other thing when your setting up your mfc on a network no need to turn it off ;)

scanner the same way double click the driver file install then in the terminal 
  	 	 	 	 	 	 	 	 	  [COLOR=#000000][SIZE=2]brsaneconfig -a name=Scanner model=MFC-3820CN ip=192.168.1.9[/SIZE][/COLOR] life gets easier but hats to you my freind for making this possible in the 1st place I will try the fax later and let you know

---

### Post by altonbr on 2006-09-26
What about a MFC-8440? Has anyone tried this?

I followed how to install the printer.. but it just hangs... MFC-8300 is the only driver that works so far even though it's a MFC-8440!

---

### Post by BobSongs on 2006-09-26
> **bigken said:**
> Yo Bobsongs I just downloaded the new drivers for my mfc3820cn 
installed edgy Knot3 folllowed your tutorial to point of making the folders then just double clicked the driver files installed using Gdebi
went into printer changed from usb to unix lpd printer and added the static ip address and hey presto it printed 1 other thing when your setting up your mfc on a network no need to turn it off ;)

scanner the same way double click the driver file install then in the terminal 
  	 	 	 	 	 	 	 	 	  [COLOR=#000000][SIZE=2]brsaneconfig -a name=Scanner model=MFC-3820CN ip=192.168.1.9[/SIZE][/COLOR] life gets easier but hats to you my freind for making this possible in the 1st place I will try the fax later and let you knowI'm glad the joint effort of this tutorial has been useful.

---

### Post by BobSongs on 2006-09-26
> **altonbr said:**
> What about a MFC-8440? Has anyone tried this?

I followed how to install the printer.. but it just hangs... MFC-8300 is the only driver that works so far even though it's a MFC-8440!What hangs? At what point do things go wrong? Is there an output to the screen you can capture and paste? I haven't noticed your printer's driver in the list, sadly. I don't think Brother has created one yet. I don't know what to suggest in terms of proper drivers.

---

### Post by altonbr on 2006-09-27
I found the MFC-8440 driver here: [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC8440-1.0.2-1.i386.deb&lang=English_gpl]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC8440-1.0.2-1.i386.deb&lang=English_gpl")

I ran the first part of your tutorial
```

Step 1: Download from Brother

[The CUPS wrapper]
[The LPR Driver]


    For other Brother machines: Please make sure the appropriate drivers are downloaded. Check the Brother website for the LPR Drivers and for the CUPS Wrapper.


Step 2: Install the C Shell
Code:

sudo apt-get install csh

:: TURN PRINTER OFF ::
(DO NOT SKIP THIS STEP! THINGS GO TERRIBLY WRONG WHEN THIS IS AVOIDED!)


Step 3: LPR Driver Install
Code:

sudo mkdir /var/spool/lpd sudo mkdir /var/spool/lpd/MFC210C (replace with your printer name) sudo dpkg -i ~/Desktop/mfc210c/mfc210clpr-1.0.2-1.i386.deb


Step 4: Install the CUPS Wrapper
Code:

sudo ln -s /etc/init.d/cupsys /etc/init.d/cups sudo dpkg -i ~/Desktop/mfc210c/cupswrappermfc210c_1.0.0-1_i386.deb

Finalization

:: TURN PRINTER ON ::

System &#8594; Administration &#8594; Printing

Right-click the MFC120C and click “Properties”

    * Connection Tab: Ensure local printer is connected (Printer Type: Local Printer) and (Use a Detected Printer: Brother MFC-210C)
    * General Tab: Select paper type
    * Paper Tab: Ensure your local paper size is selected.
    * Advanced Tab: Review the choices and make appropriate adjustments.
    * From any tab: Click "Print a test page" to confirm all works well.

```

Skipping the LPR driver... because I can't find one of those for the MFC-8440. Is this crucial? Or does this just add functionality to the printer?

---

### Post by altonbr on 2006-09-27
Oh, I found the LPR Driver ([http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc8440lpr-1.1.2-1.i386.deb&lang=English_lpr]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc8440lpr-1.1.2-1.i386.deb&lang=English_lpr"))

I'll install that as well when I get home.

---

### Post by thingmarius on 2006-09-27
Hello

I've got a mfc410cn connectied to a USB port on my desktop computer. I've got Ubuntu 5.10 installed, and up-to-date. I'm having some trouble with installing the drivers, ie:

1) couldn't install csh, got the error that there was no package, so I installed tcsh, hope that's ok.

2) the cups folder isn't in /etc/init.d/, it's in /etc/, so I'm getting the No such file or folder error. should I move the cups folder or ln to its current location ?

3) also I get the following error:

> sudo dpkg -i ~/Desktop/mfc410cn/mfc410cnlpr-1.0.2-1.i386.deb
(Reading database ... 61380 files and directories currently installed.)
Preparing to replace cupswrappermfc410cn 1.0.0-1 (using .../mfc410cnlpr-1.0.2-1.i386.deb) ...
/usr/local/Brother/cupswrapper/cupswrapperMFC410CN-1.0.0: No such file or directory.
Unpacking replacement cupswrappermfc410cn ...
Setting up cupswrappermfc410cn (1.0.0-1) ...
ERROR : Brother LPD filter is not installed.
rm -f /usr/lib/cups/filter/brlpdwrapperMFC410CN
chmod: cannot access `/usr/local/Brother/inf/brMFC410CNrc': No such file or directory
chmod: cannot access `/usr/local/Brother/inf': No such file or directory
/etc/init.d/cups: Permission denied.

That's as far as I could go with the installation. If I want to start back from scratch, what files should I delete ?

---

### Post by altonbr on 2006-09-28
Ok, so I repeated your steps when after I downloaded the LRN driver.

I tried to get it to work with JUST the CUPS driver, but to no avail. So here is my terminal window after running your commands (and yes, I repeated all of them JUST to make sure).

```

brett@brettalton:~$ sudo mkdir /var/spool/lpd
Password:
mkdir: cannot create directory `/var/spool/lpd': File exists
brett@brettalton:~$ sudo mkdir /var/spool/lpd/MFC8440 mkdir: cannot create directory `/var/spool/lpd/MFC8440': File exists
brett@brettalton:~$ sudo dpkg -i ~/Desktop/mfc8440/mfc8440lpr-1.1.2-1.i386.deb
Selecting previously deselected package mfc8440lpr.
(Reading database ... 89033 files and directories currently installed.)
Unpacking mfc8440lpr (from .../mfc8440lpr-1.1.2-1.i386.deb) ...
Setting up mfc8440lpr (1.1.2-1) ...
/var/lib/dpkg/info/mfc8440lpr.postinst: line 4: /etc/init.d/lpd: No such file or  directory
dpkg: error processing mfc8440lpr (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 mfc8440lpr
brett@brettalton:~$ sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
ln: creating symbolic link `/etc/init.d/cups' to `/etc/init.d/cupsys': File exis ts
brett@brettalton:~$ sudo dpkg -i ~/Desktop/mfc8440/cupswrapperMFC8440-1.0.2-1.i3 86.deb
(Reading database ... 89045 files and directories currently installed.)
Preparing to replace cupswrappermfc8440 1.0.2-1 (using .../cupswrapperMFC8440-1. 0.2-1.i386.deb) ...
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
Unpacking replacement cupswrappermfc8440 ...
Setting up cupswrappermfc8440 (1.0.2-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC8440
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
 * Restarting Common Unix Printing System: cupsd                         [ ok ]

brett@brettalton:~$
```

It seems to be that the LPR Driver isn't the correct one.. But I could still install the CUPS Driver.. Do you know what's goin on BobSongs?

Lastly, for anyone that needs a visualization, the product URL is [http://www.brother.ca/en/all-in-one/description.asp?Prodid=1019&features=on]("http://www.brother.ca/en/all-in-one/description.asp?Prodid=1019&features=on")

---

### Post by bigken on 2006-09-28
go into synaptic and remove anything to do with brother printers 
just search for brother then start again but you must install lpr driver 1st

[mfc8440 lpr]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc8440lpr-1.1.2-1.i386.deb&lang=English_lpr")

[mfc8440 cups ]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC8440-1.0.2-1.i386.deb&lang=English_gpl")

---

### Post by altonbr on 2006-09-28
Error when removing mfc8440lpr:

```
E: mfc8440lpr: subprocess post-removal script returned error exit status 127
```

So I ran the tutorial again, just in case... and the same error came up.

```
brett@brettalton:~$ sudo mkdir /var/spool/lpd
Password:
mkdir: cannot create directory `/var/spool/lpd': File exists
brett@brettalton:~$ sudo mkdir /var/spool/lpd/MFC8440 brett@brettalton:~$ sudo dpkg -i ~/Desktop/mfc8440/mfc8440lpr-1.1.2-1.i386.deb
Selecting previously deselected package mfc8440lpr.
(Reading database ... 89025 files and directories currently installed.)
Preparing to replace mfc8440lpr 1.1.2-1 (using .../mfc8440lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc8440lpr ...
/var/lib/dpkg/info/mfc8440lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing /home/brett/Desktop/mfc8440/mfc8440lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 /home/brett/Desktop/mfc8440/mfc8440lpr-1.1.2-1.i386.deb
brett@brettalton:~$

```

How do I forcefully remove mfc8440lpr so I can re-install it?

Now when opening Synaptic, I recieve this:

```
E: The package mfc8440lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

---

### Post by bigken on 2006-09-28
in a terminal I think its sudo dpkg -r (name of package)

---

### Post by altonbr on 2006-09-28
**sudo dpkg -r mfc8440lpr**
```
dpkg: error processing mfc8440lpr (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 mfc8440lpr

```

**sudo apt-get remove mfc8440lpr**
```
Reading package lists... Done
Building dependency tree... Done
E: The package mfc8440lpr needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by bigken on 2006-09-28
sudo aptitude purge (name of package)

sudo apt-get purge (name of package)

---

### Post by altonbr on 2006-09-28
**sudo aptitude purge mfc8440lpr**
```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  mozilla-firefox-locale-en-gb
The following packages will be REMOVED:
  mfc8440lpr{p}
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 713kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing mfc8440lpr (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
brett@brettalton:~$ Errors were encountered while processing:
 mfc8440lpr
```

**sudo apt-get purge mfc8440lpr**
```
E: Invalid operation purge
```

---

### Post by harry555 on 2006-09-30
Big thanks for the howto for the 210c.   I have the 215c printing perfectly.
I have not set up the fax and scanner yet.  I am using Dapper.   The only glitches I experienced were these:

1. sudo apt-get install csh did not work it could not find csh.  I went to Synaptic and enabled every repository I could find there and got csh installed easily that way.

2.  I found that sometimes you had to navigate to the actual directory before I could get mkdir work.  For example when making the MFC215C directory.

3. I got an error message when I went sudo dpkg etc for the cupswrapper it comlained about not finding init.d but the printer is working perfectly!!

So, thanks again.  I was about to go and buy a HP printer but now I won't have to.

harry

---

### Post by Matchless on 2006-09-30
> **harry555 said:**
> Big thanks for the howto for the 210c.   I have the 215c printing perfectly.
I have not set up the fax and scanner yet.  I am using Dapper.   The only glitches I experienced were these:

1. sudo apt-get install csh did not work it could not find csh.  I went to Synaptic and enabled every repository I could find there and got csh installed easily that way.

2.  I found that sometimes you had to navigate to the actual directory before I could get mkdir work.  For example when making the MFC215C directory.

3. I got an error message when I went sudo dpkg etc for the cupswrapper it comlained about not finding init.d but the printer is working perfectly!!

So, thanks again.  I was about to go and buy a HP printer but now I won't have to.

harry

Maybe this link will give you some more details for the MFC-215C [http://ubuntuforums.org/showthread.php?t=263047](http://ubuntuforums.org/showthread.php?t=263047)

---

### Post by BobSongs on 2006-09-30
> **Matchless said:**
> Maybe this link will give you some more details for the MFC-215C [http://ubuntuforums.org/showthread.php?t=263047](http://ubuntuforums.org/showthread.php?t=263047)

Matchless: I'm going to add your link to this tutorial at the very top in order to redirect MFC-215C owners lest they continue trying to get their printer going with my tutorial.

---

### Post by altonbr on 2006-10-01
My uncle's MFC-420CN connected locally and my MFC-8440 connected locally both do not work. Both computers are running Ubuntu 6.06.1 and I followed your tutorial exactly, downloading the proper drivers from the Brother website.

Now, what does "not working" mean? Well, for the MFC-420CN, the install went fine, but it just sits there, acting as if no print job has been sent to it. My MFC-8440 does the same, but that's because my LPR didn't install properly.

<see postings above>

any advice?

---

### Post by BobSongs on 2006-10-02
> **altonbr said:**
> My uncle's MFC-420CN connected locally and my MFC-8440 connected locally both do not work. Both computers are running Ubuntu 6.06.1 and I followed your tutorial exactly, downloading the proper drivers from the Brother website.

Now, what does "not working" mean? Well, for the MFC-420CN, the install went fine, but it just sits there, acting as if no print job has been sent to it. My MFC-8440 does the same, but that's because my LPR didn't install properly.

<see postings above>

any advice?Okay. Do(es) the printer(s) show up in the list of printers in the system? Or are they not at all visible?

Did any of the installs offer any grief? Some hint that may have been offered at the command line?

This part is sometimes forgotten:

> System &#8594; Administration &#8594; Printing

Right-click the installed printer and click “Properties”

    * Connection Tab: Ensure local printer is connected (Printer Type: Local Printer) and (Use a Detected Printer: Brother MFC-whatever)

---

### Post by Leebobs on 2006-10-03
:D Thanks very much for the guide

I used it to sucesfully install both the printer & Scanner on a Brother DCP-110C.

Leebobs

---

### Post by Alvant on 2006-10-03
Thanks for the guide. My DCP 7010 (printer and scanner) is working.

I had to edit some files though to ge my scanner working. As suggested to my problem(When scanning I receive the error "Error during device I/O") by the scanner faq on the brother page:
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html")

---

### Post by harry555 on 2006-10-05
Just did the 202mb 179 package update and now the printing is stuffed up.
Click print and wait for one minute and paper gets drawn into printer, wait another 20 seconds, then it prints at normal speed.   Wait for another 10 secs and out comes the paper.   This is with the Brother mfc215c printing out a 'one word' test print.

Prob. going to do a re-install and forget the updates altogether.  Then I will see if it's printing o.k then try the scanner again using the tip on the brother page. (plus howto)

Other than these problems I am loving Ubuntu.  My digital camera, a Kodak works perfectly.  Same with a usb flash drive.

---

### Post by harry555 on 2006-10-05
Now I'm really happy.  I re-installed Dapper with none of the updates.   The printer *and* scanner are now working perfectly.   Many thanks to the other posters here or I would never have got this stuff working. :D :D :D

To get the scanner working.  I went sudo gedit in the terminal program and modified that 45-libsane.rules file.    After that I followed the instructions in the how-to listed earlier in the thread.

\\:D/

---

### Post by stalefries on 2006-10-06
Any word on getting network printing with Dapper working yet? It'd be nice to have this for my school work.

---

### Post by Matchless on 2006-10-07
> **BobSongs said:**
> Matchless: I'm going to add your link to this tutorial at the very top in order to redirect MFC-215C owners lest they continue trying to get their printer going with my tutorial.

Thanks, it would be better to have all the Brother howto's together. I think you can be called the "Brother pioneer" for really putting something complete together for other users. Have you thought of putting your howto in the wiki?  I think that could be the proper place for it now.
Thanks for your inputs from all of us.

---

### Post by altonbr on 2006-10-08
@BobSongs

I'm in Xubuntu at the moment and I don't have any printers set up, so I can't give you exact details, but for the MFC-420CN, it was a simple mistake; I merely had to change the connection port from usb:_____ to "Use a detected printer"... I don't know why that worked, but it did so I won't complain. Now if only I can get the IPP working properly for my laptop on wireless then I'm all set.

Also, for the MFC-8440 (which is my printer), I will be setting that up shortly following your tutorial and I'll see if it works. I'll keep you updated.

Thanks again.

---

### Post by altonbr on 2006-10-08
Yes, something is definetly wrong with the LPR. I've installed it in Xubuntu and Ubuntu and both same with the same error. Here is exactly what I did in the terminal:

```
brett@brett-xubuntu:~$ sudo apt-get install csh
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  csh
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 239kB of archives.
After unpacking, 393kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com dapper/universe csh 20050313-1 [239kB]
Fetched 239kB in 1s (125kB/s)
Selecting previously deselected package csh.
(Reading database ... 59957 files and directories currently installed.)
Unpacking csh (from .../csh_20050313-1_i386.deb) ...
Setting up csh (20050313-1) ...

brett@brett-xubuntu:~$ sudo mkdir /var/spool/lpd
brett@brett-xubuntu:~$ sudo mkdir /var/spool/lpd/MFC8440
brett@brett-xubuntu:~$ sudo dpkg -i ~/Desktop/mfc8440/mfc8440lpr-1.1.2-1.i386.deb
Selecting previously deselected package mfc8440lpr.
(Reading database ... 59966 files and directories currently installed.)
Unpacking mfc8440lpr (from .../mfc8440lpr-1.1.2-1.i386.deb) ...
Setting up mfc8440lpr (1.1.2-1) ...
[B]/var/lib/dpkg/info/mfc8440lpr.postinst: line 4: /etc/init.d/lpd: No such file or directory
dpkg: error processing mfc8440lpr (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 mfc8440lpr[/B]
```

Why is it having problems with /etc/init.d/lpd???

And then it had problems removing it:

```
brett@brett-xubuntu:~$ sudo aptitude remove mfc8440lpr
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  mfc8440lpr
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 59979 files and directories currently installed.)
Removing mfc8440lpr ...
[B]/var/lib/dpkg/info/mfc8440lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing mfc8440lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 mfc8440lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:[/B]
```

Last time to remove this exact same error, I had to rename /var/lib/dpkg/info/mfc8440lpr.postrm so aptitude or dpkg could not find it.
This is the code:

```
$ sudo mv /var/lib/dpkg/info/mfc8440lpr.postrm /var/lib/dpkg/info/mfc8440lpr.postrm-bak
$ sudo dpkg --purge mfc8440lpr
```

Can't say I'm not confused or at a loss.

---

### Post by stalefries on 2006-10-09
Nevermind, I figured it out from one of the other threads on here. I think I'll tackle scanning next and see if I can update my HOWTO.

---

### Post by BobSongs on 2006-10-14
> **altonbr said:**
> <snip>
/etc/init.d/lpd: No such file or directory
</snip>
Have you tried creating this directory?
Is the file damaged?

---

### Post by stalefries on 2006-10-14
Good news! I just tried out my directions for network scanning on Breezy with my Dapper laptop, and they worked flawlessly!
[http://www.ubuntuforums.org/showthread.php?p=935120#post935120](http://www.ubuntuforums.org/showthread.php?p=935120#post935120)

---

### Post by altonbr on 2006-10-15
> **BobSongs said:**
> Have you tried creating this directory?
Is the file damaged?

I would figure, yes. The file is damaged. I'll try contacting Brother. Good ol' $599 CDN printer out the window!

---

### Post by varkatope on 2006-10-15
I followed the HOWTO and everything works. Printing, scanning even over network works. But printing is extremely slow. It takes about 30 seconds for the printing to start an about 2 minutes to print a simple A4-Textpage in normal resolution.

Any ideas what to reconfigure to solve this problem?

The MFC-210C is connected via USB. And the same HOWTO lead me to success on Breezy without the speedproblem.

---

### Post by altonbr on 2006-10-16
> **varkatope said:**
> I followed the HOWTO and everything works. Printing, scanning even over network works. But printing is extremely slow. It takes about 30 seconds for the printing to start an about 2 minutes to print a simple A4-Textpage in normal resolution.

Any ideas what to reconfigure to solve this problem?

The MFC-210C is connected via USB. And the same HOWTO lead me to success on Breezy without the speedproblem.

I have the same problem when I use the MFC8300 driver instead of the proper MFC8440 driver. I know this isn't an answer, but I'm merely stating that it happens to me too (when using the wrong driver). I couldn't tell you if it changes when using the "proper" driver, but I'll let you know when it's fixed!

---

### Post by stalefries on 2006-10-16
I use the proper driver for the MFC3820CN, but I still get slower printing speeds. The printout part doesn't go slowly (compared to network printing from a Windows machine), but the time period between clicking print and the printout starting is definitely delayed.

---

### Post by mbelinky on 2006-10-17
Hi,
I'm running a fresh copy of Edgy, and have a DCP-115C.
I've followed the instructions on the HOWTO, however after installing the CUPS wrapper, I get the following msg:

```

maga@ubuntu:~/Desktop$ sudo dpkg -i cupswrappermfc210c_1.0.0-1_i386.deb 
Selecting previously deselected package cupswrappermfc210c.
(Reading database ... 86744 files and directories currently installed.)
Unpacking cupswrappermfc210c (from cupswrappermfc210c_1.0.0-1_i386.deb) ...
Setting up cupswrappermfc210c (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
lpadmin: Unable to copy PPD file!
```

and when I try to print a test page, I see a msg on the printer saying "receiving data", but nothing happens.

any ideas?

thanks

**edited to add:** I just followed the instructions on [http://www.ubuntuforums.org/showthread.php?t=232276&highlight=unable+to+copy+ppd]("http://www.ubuntuforums.org/showthread.php?t=232276&highlight=unable+to+copy+ppd") this post and it works fine now. It's worth adding to the HOWTO, I think, seems it looks like an Edgy specific situation.

---

### Post by mbelinky on 2006-10-17
more Edgy / DCP-115C notes, I saw some of this on the thread already but I'm adding it so there's an Edgy specific entry.

after installing the brscan2 driver, xsane fails with a I/O error, then follow the instructions on the brother FAQ: [http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#20]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#20")
, and do the following:
```

1.Open the file "/etc/udev/rules.d/45-libsane.rules" with an editor.
2.Add the following description to the file as below:
=================
#brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"
LABEL="libsane_rules_end"
=================
3.Restart the OS.

```

I just added the SYSFS line, not the LABEL one, since the file has other vendor specific rules and a LABEL end at the end of file.

no need to restart the OS really, you can just do a 
```

sudo /etc/init.d/udev restart

```

and scanning on Edgy with the DCP-115C works fine after that.

---

### Post by altonbr on 2006-10-20
Well, apparently Brother doesn't care about helping my MFC8440 problems. ](*,) They've had a week or so to e-mail me back.. and I've got no word.

So everyone just becareful with the MFC8440... the driver is corrupted (possibly)... can you add this printer to the black list?

---

### Post by musther on 2006-10-21
Using the instructions in this thread I've managed to install both a DCP110C and a DCP115C.

In both cases however, the printer doesn't really seem to know what paper it's printing on.  The Ubuntu test page comes out ok, the lines around the edge fit nicely around the page except at the bottom where they leave extra space, but I think this is because the Ubuntu test is in letter format and I'm printing on A4.

However the problems start when printing actual documents.  I can't print from OOo Writer in ladscape because the content is so shifted up and to the right that it cuts off the side of the sheet.  

Also in the GIMP, I try to print an A4 document, and it is shifted up and this time to the left, on the 115C it manages to cut off the bottom of the image.

I've got the paper size set to A4, and I've got the page region set to A4 also.  If I change these to letter it doesn't seem to make any difference.

It's not just an issue with OOo, I've exported an offending (landscape) document to a PDF ([http://www.flamingfatherland.org/jon/stuff/temporary/ps.pdf](http://www.flamingfatherland.org/jon/stuff/temporary/ps.pdf)) so if anyone would like to they can test it, see how it comes out for them.  

The DCP110C is using the correct driver, the DCP115C was using the MFC210C driver (that's what brother recommend).

I've contacted brother, and they've responded, but as yet seem unable to help.

I'm getting very frustrated, please help me before I pull all of my hair out.

---

### Post by d3dtn01 on 2006-10-21
Thanks to the HowTo I was printing and scanning just fine with my mfc210c. But recently I crashed my system and have had several problems since getting it to work again. (In fact, to solve the problems, I had to start using the user profile I had previously set up for my girlfriend since things still don't work perfect under my profile.) So I went to print for the first time since this big crash and it doesn't work. I hit print and the icon pops up in the tray, but the printer sits there oblivious. If I open the printer icon, it says that my printer isn't connected. It clearly is (I checked both ends of the cord to make sure they are properly connected). So I plugged the printer into another USB port and rebooted. Same problem. It's not the USB ports because my mouse works fine when I plug it in to these ports. Any suggestion on how to trouble shoot this?

---

### Post by vojtek on 2006-10-22
> **mbelinky said:**
> more Edgy / DCP-115C notes, I saw some of this on the thread already but I'm adding it so there's an Edgy specific entry.

after installing the brscan2 driver, xsane fails with a I/O error, then follow the instructions on the brother FAQ:

Thank You for this information, it works on my Edgy (Brother MFC 215) after changes You wrote about.

---

### Post by PrinceVince on 2006-10-23
[SIZE="4"][color=#660000]BobSongs, please consider adding this to the appropriate section in your HowTo.[/color][/SIZE]

I imagine, this close to the Edgy release, many users will stumble upon this problem. I tried a lot until i stumbled upon this post on page 23 (which solved it just fine)

thanks.

> **mbelinky said:**
> **edited to add:** I just followed the instructions on [http://www.ubuntuforums.org/showthread.php?t=232276&highlight=unable+to+copy+ppd]("http://www.ubuntuforums.org/showthread.php?t=232276&highlight=unable+to+copy+ppd") this post and it works fine now. It's worth adding to the HOWTO, I think, seems it looks like an Edgy specific situation.

> **mbelinky said:**
> Hi,
I'm running a fresh copy of Edgy, and have a DCP-115C.
I've followed the instructions on the HOWTO, however after installing the CUPS wrapper, I get the following msg:

```

maga@ubuntu:~/Desktop$ sudo dpkg -i cupswrappermfc210c_1.0.0-1_i386.deb 
Selecting previously deselected package cupswrappermfc210c.
(Reading database ... 86744 files and directories currently installed.)
Unpacking cupswrappermfc210c (from cupswrappermfc210c_1.0.0-1_i386.deb) ...
Setting up cupswrappermfc210c (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
lpadmin: Unable to copy PPD file!
```

and when I try to print a test page, I see a msg on the printer saying "receiving data", but nothing happens.

any ideas?

thanks

---

### Post by altonbr on 2006-10-23
I recieved this e-mail today from Brother:

```
From: Keith Selman
Sent: Mon 10/16/2006 10:28 AM
To: dealer.support
Subject: FW: Web feedback


Use the driver for the  HL5150D  or HL5170DN

 
http://solutions.brother.com/linux/sol/printer/linux/linux_config_list2.html#1

```

Although I don't know what his link is, because the LPR driver is [here]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html") and the CUPS wrapper is [here]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html"), I will test out using the HL-5150D or HL-5170DN drivers for my MFC-8440 tonight. Wish me luck.

---

### Post by altonbr on 2006-10-23
[SIZE="6"]**ALRIGHT THAT'S IT**[/SIZE]

Here is me trying to dpkg hl5150dlpr-1.1.2-1.i386.deb & hl5170dnlpr-1.1.2-1.i386.deb

```
sudo dpkg -i ~/Desktop/hl5150dlpr-1.1.2-1.i386.deb 
Selecting previously deselected package hl5150dlpr.
(Reading database ... 70756 files and directories currently installed.)
Unpacking hl5150dlpr (from .../hl5150dlpr-1.1.2-1.i386.deb) ...
Setting up hl5150dlpr (1.1.2-1) ...
/var/lib/dpkg/info/hl5150dlpr.postinst: line 4: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl5150dlpr (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 hl5150dlpr

```

```
sudo dpkg -i ~/Desktop/hl5170dnlpr-1.1.2-1.i386.deb 
Selecting previously deselected package hl5170dnlpr.
(Reading database ... 70770 files and directories currently installed.)
Unpacking hl5170dnlpr (from .../hl5170dnlpr-1.1.2-1.i386.deb) ...
dpkg: error processing /home/brett/Desktop/hl5170dnlpr-1.1.2-1.i386.deb (--install):
 trying to overwrite `/usr/bin/brprintconf', which is also in package hl5150dlpr
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 /home/brett/Desktop/hl5170dnlpr-1.1.2-1.i386.deb

```

So absolutely no .deb files work on my computer. Is there a package or dependencies that I can completely remove and then reinstall to fix my DEB installation woes? I'm getting SICK of this.


Using gnome-cups-manager, I added the MFC-8440 printer via the HL-7150D seems to work perfectly (they appear to be the same driver... so this should be the preferred method for anyone with the same printer (MFC-8440))... now I'm just worried about my computer... what's going on? Here is a link to my other post regarding install errors: [http://www.ubuntuforums.org/showpost.php?p=1595032&postcount=231]("http://www.ubuntuforums.org/showpost.php?p=1595032&postcount=231")

I can't upgrade my computer now because hl5170dnlpr is broken! When this happened to my mfc8440 deb files, I was able to use this little trick below:

```
$ sudo mv /var/lib/dpkg/info/mfc8440lpr.postrm /var/lib/dpkg/info/mfc8440lpr.postrm-bak
$ sudo dpkg --purge mfc8440lpr
```

But it doesn't work because /var/lib/dpkg/info/hl5170dnlpr.postrm doesn't exist.

---

### Post by altonbr on 2006-10-27
I tried installing the SANE driver for my MFC-8440 (MFC8440) and I get this error in GIMP when trying to Aquire:

Is there anything that WORKS for my printer?

---

### Post by Boberg on 2006-10-30
I'm having problems with the cupswrapper. At the end of the installation, after restarting CUPS it says:

 * Restarting Common Unix Printing System: cupsd                         [ ok ]
lpadmin: Kunde inte kopiera PPD-fil!

(Could not copy PPD-file)

Any ideas on what might be wrong here? ](*,) 

I had no problem installing using the guide when i ran Dapper, but now in Edgy this problem appeared.

Any help would be appreciated! :-k

---

### Post by livinginx on 2006-10-31
> **marcw said:**
> Huh???

The 420CN is already a network printer i.e. it has a print server built in.  Why would you need another machine from which to share it?  The only reason I can think of to use the USB connection directly (instead of the Ethernet network connection) is to utilize the scanner.  There might be a reason; I just can't think of it...

The reason I know this is because I'm using it right now with a network connection.  My network settings look like this:

Mine looks almost similar to that for a 420cn, but The top field is just the IP, no lpd or anything.  The bottom box didn't work when I put the name in, so now it just looks like this: /192.168.0.116/

---

### Post by orsula on 2006-10-31
Same problem as post #249 exactly!!
I also tried ```
sudo cp /usr/share/cups/model/brmfc210c_cups.ppd /usr/share/ppd/
``` bu tthat didn't help. 

Would love to hear ideas...

---

### Post by bigken on 2006-11-01
Hi all I just istalled my mfc3820cn on edgy and it did not work either 
this how I got it to work make the folders 

sudo mkdir /var/spool/lpd

sudo mkdir /var/spool/lpd/MFC3820CN

download the drivers from brother 

double click on them to install 

then I went to system/administration/printers 

double click new printer 

select local printer then next 

now select brother then click on install driver 

then navigate to file system/usr/share/cups/model

then just double click brmfc3820cn_cups.ppd (in my case)

then select it from the brother menu 

if you are on a network its the same just select it as a unix (lpd)
and give it a ip address 

hope this helps ;)


oops forgot to mention install csh (sudo aptitude install csh)

---

### Post by Boberg on 2006-11-01
> **orsula said:**
> Same problem as post #249 exactly!!
I also tried ```
sudo cp /usr/share/cups/model/brmfc210c_cups.ppd /usr/share/ppd/
``` bu tthat didn't help. 

Would love to hear ideas...

I reinstalled with the i386 version of the os instead of the amd64 version. The same error then appeared as I installed the printer, but when I tested it it worked, so problem solved for me in that way. Hope it will work out for you as well somehow. 8)

---

### Post by inspired on 2006-11-04
> **BobSongs said:**
> **[SIZE=4]An "Install Script" for the Brother MFC210C printer.[/SIZE]**

**Requirements**[INDENT]Intel-based PC running Ubuntu
MFC-210C (**not** applicable to the MFC-215C!) connected directly to the PC via USB[/INDENT]**Download**[INDENT][COLOR=Red][**Click here**]("http://breezybadger.50webs.com/Brother_MFC-210C_Installer.sh") to download the script for _**Breezy Badger**_.
***Save it to your desktop.***[/COLOR]

[COLOR=Blue][**Click here**]("http://dapperdrake.50webs.com/Brother_MFC-210C_Installer.sh") to download the script for _**Dapper Drake**_.
***Save it to your desktop.***[/COLOR][/INDENT]**Open a Terminal**

Applications -> Accessories -> Terminal

Enter the following
```
cd ~/Desktop
chmod 740 Brother_MFC-210C_Installer.sh
sudo ./Brother_MFC-210C_Installer.sh
``` This will require the system password.

A box will appear. Just check each item you want installed and click OK.[INDENT]**[COLOR=#aa00aa]Follow the instructions in the popup boxes carefully. I know they're annoying. Believe me. But if you just "*click OK to make it go away*" things go very wrong quickly.[/COLOR]**

Hope to hear from you about your success. Remember: it's a beta. We hope all the bugs are worked out but some slip through.

Huge thanks to **GoogleNinja** for his indispensible help, and to **arnieboy** for his original Automatix script upon which this installer is based.[/INDENT]Current [COLOR=Red]**Breezy**[/COLOR] version available: **0.08a-1**
Curren **[COLOR=Blue]Dapper[/COLOR]** version available: **0.09-1**
[SIZE=1]Uploaded June 29th, 2006: new version for Dapper Drake available.[/SIZE]

I have modified this script to install the MFC-7820N (MFC7820N) printer. 
I would like to know if there is a simple way to change the script to support installing a network connected MFC-7820N (or any other network enabled brother printer). As far as I can tell it will require obtaining the IPP address for the printer and then applying that to the URI address.

Either the script would obtain this address or the user could obtain it and then a prompt fron the script asks the user what it is. I believe it will be in the format "http://my.printer.name:631/ipp" so perhaps the script can just set that as "http://MFC7820N:631/ipp" since MFC7820N is what it names the printer. I am just not sure how to modify the script to use this URI in stead of the "usb:/dev/usb/lp0" address that presently ends up in the URI.

Any ideas?

With thanks,

Jonathan Evatt

BTW: At present I am not able to test the script fully because it is a client that has this printer on his Ubuntu system. I thought it might help to know that.

---

### Post by BobSongs on 2006-11-05
> **inspired said:**
> <snip>I have modified this script to install the MFC-7820N (MFC7820N) printer. 
I would like to know if there is a simple way to change the script to support installing a network connected MFC-7820N (or any other network enabled brother printer). As far as I can tell it will require obtaining the IPP address for the printer and then applying that to the URI address.</snip>

Let me know if you get the script completed. My friend did all the leg work for me so I cannot assist, I'm afraid.

However if you accomplish your task I'll be glad to host the file for you at the same location where I'm hosting the other scripts.

Feel free to create a HowTo for that printer. I'll put a link to it in my HowTo.

---

### Post by jrgii on 2006-11-06
> **bigken said:**
> Hi all I just istalled my mfc3820cn on edgy and it did not work either 
this how I got it to work make the folders 

...

then navigate to file system/usr/share/cups/model

then just double click brmfc3820cn_cups.ppd (in my case)

then select it from the brother menu 



I have been trying for the past few days to get my 420cn to work under edgy, this did the trick!!!

---

### Post by bigken on 2006-11-06
> **jrgii said:**
> I have been trying for the past few days to get my 420cn to work under edgy, this did the trick!!!

Pleased it worked for you for the scanner just follow the guide already in this thread ;)

---

### Post by lothar_m on 2006-11-19
I've sucessfully installed a Brother DCP-340CW via network (ethernet) using you're excelent tutorial. i've used the 210 drivers and then configured cups with the gnome-printer-manager.

it prints fine.

I've also been able to setup the scanner following the brother tutorial [here]("http://solutions.brother.com/linux/sol/printer/linux/sane_install-net.html")

drivers found [here]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html")


I haven't read all the posts in this huge tread so please ignore me if this isn't new....

---

### Post by shekhark on 2006-11-23
Can anyone here help me with installing an MFC5100C on Dapper? Unfortunately the needed drivers are not on the Brother site with all the other Linux drivers. CUPS recognises it and I can even scan with XSane from it, but printing doesn't work.

---

### Post by BobSongs on 2006-11-26
Shekhark; I did some research and basically nothing turned up. I don't know which printer is similar enough to the 5100C for use so I cannot recommend lpr drivers for you.

Your machine must be fairly new. In terms of Brother printers it would appear older models are more compatible with Ubuntu. Brother is actively creating drivers. However this one's not ready yet.

The most I could recommend is to keep an eye out on the site for updates. And when one is added put a note in this thread; it appears to be one of the more helpful ones on the Internet.

---

### Post by Grosser on 2006-11-27
Hello BobSongs,

do you write new the Installer-Script (MFC210C) for Edgy new?
With the Script for Dapper i could install my DCP115, but on Edgy it not goes, i take some errors.
Sorry for my bad English!

---

### Post by alaw005 on 2006-12-01
Here is how I got my networked Brother (MFC640CW) Wireless Printer to work in Ubunty 6.10 (Edgy) using the Brother MFC210C driver.

These steps are based on those at [http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#60](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#60) but have been modified specifically for Ubuntu 6.10 (Edgy). Follow these instructions exactly.

1. Download "mfc210clpr-1.0.2-1.i386.deb" and "cupswrappermfc210c_1.0.0-1_i386.deb" from brother website 

2. Open Terminal (Applications --> Accessories --> Terminal) and do following

3. Install csh, in Terminal type:
	a. sudo apt-get install csh

4. Install mfc210clpr-1.0.2-1.i386.deb, in Terminal type:
	a. sudo mkdir /var/spool/lpd
	b. sudo mkdir /var/spool/lpd/MFC210C
	c. sudo dpkg -i mfc210clpr-1.0.2-1.i386.deb 

5. Install cupswrappermfc210c_1.0.0-1_i386.deb, in Terminal type:
	a. sudo dpkg -i cupswrappermfc210c_1.0.0-1_i386.deb
	NB: Ignore any errors, especially if last line is" lpadmin: Unable to copy PPD file!"

6. Turn printer on

7. Configure, in Terminal type:
	a. lpadmin -p MFC210C -E -v usb:/dev/usb/lp0 -P /usr/share/cups/model/brmfc210c_cups.ppd

8. COnfigure continued, open you web browser and do the following:
	a. enter "http://localhost:631/printers", printer should be displayed on page
	b. click "modify printer"
	c. click "continue"
	d. select "LPD/LPR Host or Printer" and click continue
	e. enter "lpd://xx.xx.xx.xx/binary_p1" in "Device URI" field where xx.xx.xx.xx is the ip address of your printer and click continue
	f. click "browse" and navigate to "/usr/share/cups/model/" and select "brmfc210c_cups.ppd" then click "Modify Printer@
	NB: If asked for login and password use your ubuntu login and password

8. Click "Print Test Page" and should work perfect

I couldn't get printer working for hours until finally worked through this from fresh install. Good luck to anyone trying. I will now see if I can get scanner going .... wish ME luck

---

### Post by Grosser on 2006-12-01
Hello alaw005 :KS 

Thank you very mouch, now i can printing on Edgy :-)
The first file has an error at installing (could not copy...)
Than i have copy the content of the packet to the right directory, and than its gone.

Scanning:
At my Brother i could scan.
I have install the brscan2-0.2.1-0.i386.deb and used the Script of BobSongs.
For Scanning you must use sudo-rights for xsane ans co.
Good luck :-)

Thanks and Greets,

Grosser

---

### Post by BobSongs on 2006-12-03
> **Grosser said:**
> Hello BobSongs,

do you write new the Installer-Script (MFC210C) for Edgy new?
With the Script for Dapper i could install my DCP115, but on Edgy it not goes, i take some errors.
Sorry for my bad English!

Your English is no problem: what you meant to say is understood.

In answer to your question: the installer script was developed for the MFC-210C under Dapper Drake (Ubuntu 6.06.1) and Breezy Badger (Ubuntu 5.10). I have no plans to install Edgy Eft (Ubuntu 6.10) for the moment.

Ubuntu (Canonical) promised long term support (LTS) with Dapper Drake and I intend to profit from it. I am not a typical "upgrade it because it's there" type. I use my PC for work and switched to Ubuntu to get away from the endless tweaking XP promised me. The way I use a computer it's not worth for me. So the script will remain useful for Breezy and Dapper only for the MFC-210C.

Apologies to all who may feel cheated by this. This tutorial might give the impression I work for Brother. (I don't and have no means to test the script on dozens of printers.) It all started as a way for me to post on this forum a reminder of how I succeeded in getting the printer to work. A friend was pressed into service to help write the script based on my tutorial. I had no idea how many different Brother product owners this tutorial would help. I'm truly impressed.

Please feel free to examine the script and make modifications for your model. If you can run the script successfully send me a copy. I'll gladly add it to the tutorial and host the file.

---

### Post by sdb2028 on 2006-12-03
I am still having problems with my printer. I got the scanner working, however it wont print. I went through your instructions, when it asks for a password, I use my Ubuntu login- It won't accept it. What do I do now?

---

### Post by BobSongs on 2006-12-03
Are you the system administrator? If you're the only user on the system your super-user password should be the same as your personal password, unless you've made any changes. Just your your main password; that should do it.

If not then speak to your system administrator to either change your account to "execute system administration tasks" (System - Administration - Users and Groups).

---

### Post by sdb2028 on 2006-12-03
Yup, I am administrator. It won't let me use my login though. However, I figured out my problem and fixed it through the System Administration panel in printing-properties. works fine now, thanks for your help. I am using an MFC420CN in network mode.

---

### Post by VladArod on 2006-12-12
After a few days I was able to figure out out to install a Brother printer in Ubuntu X64. I have a brother DCP-340CW with a network connection, but using MFC-210c driver.

Here are the how-to:
1. Follow the instructions of the how-to in post #1. Just use flag --force-all when using dpkg. This forces the installation in a different architecture. 

2. Follow Brother recommendation: "However, if you are using an AMD64 bit distribution, we recommend you try copying the file named "brlpdwrapper" from /usr/lib/cups/filter to /usr/lib64/cups/filter."

3. Download the cupswrapper source code "bh7-cupsw-src.1.0.0-9.tar.gz" using the third link in [http://solutions.brother.com/linux/sol/printer/linux/cups_source.html](http://solutions.brother.com/linux/sol/printer/linux/cups_source.html). And, unpack it.

4. Just in case, in directory /usr/local/Brother/cupswrapper backup file  cupswrapperMFC210C-1.0.0

5. Using the unpacked source files: 
5.1. Include the string mfc210c in file model_list
5.2. Run: make
5.3. Run: sudo sh mk_cupswrapper
5.4. Overwrite cupswrapperMFC210C-1.0.0 with the new wrapper, 
running: sudo cp cupswrappermfc210c /usr/local/Brother/cupswrapper/cupswrapperMFC210C-1.0.0

6. Using any of printer setup tools and the ppd file in /usr/share/cups/model, the printer "should" be working.

Hope it helps,
Best regards

---

### Post by bornakke on 2006-12-19
> **lothar_m said:**
> I've sucessfully installed a Brother DCP-340CW via network (ethernet) using you're excelent tutorial. i've used the 210 drivers and then configured cups with the gnome-printer-manager.
it prints fine.
I haven't read all the posts in this huge tread so please ignore me if this isn't new....

Brother DCP-340 CW via wireless network succesfully installed successfully on Ubuntu Edgy. 

Used your guide, then followed these steps:
[http://www.ubuntuforums.org/showpost.php?p=644004&postcount=21](http://www.ubuntuforums.org/showpost.php?p=644004&postcount=21)
using the PDD file available from here: 
/usr/share/cups/model/yourprintername.PPD

First time I made some Hardwear work in ubuntu without help from my friends and I feel GREAT! :mrgreen:

---

### Post by Philip P on 2006-12-23
Excellent after following the walk though finally got the Brother Printer installed

Thanks

---

### Post by randiroo76073 on 2007-01-03
I'll just heap more aprobos on all who've taken their time to put this fine tutorial together, my MFC 420CN is up and running beautifully!  Thank you, thank you, thank you :)

---

### Post by randiroo76073 on 2007-01-04
I didn't see this mentioned[might have missed] but a real easy way to install is get "GDebi Package Installer" with Synaptic, once installed you can point it to any .deb for install, it'll check for dependencies too :)

---

### Post by randiroo76073 on 2007-01-05
I'm back, unfortunately with a problem, my scanner is not being "recognized" right?  Whenever I try to scan or start Xsane I get this error:thumb#1
My scanner works as I can boot into 98se & use, here is a shot of my device manager if it helps:thumb#2  I tried uninstalling Xsane & reinstalling, no help, and yes, I did have my MFC420CN turned off during install.  Has anyone else run into this or might have some ideas?
Thanks for any help.


Resolved thru re-re-reading this thread :D, kept missing it.....Duh Oh!

---

### Post by BobSongs on 2007-01-17
> **Grosser said:**
> Hello BobSongs,

do you write new the Installer-Script (MFC210C) for Edgy new?
With the Script for Dapper i could install my DCP115, but on Edgy it not goes, i take some errors.
Sorry for my bad English!

**guitara** has had some help from Matchless to write a script for Edgy Eft. However, do not use the Fax Drivers in this script. I will edit all 3 scripts and remove them. A new section has been added to the main tutorial. Faxing DOES work. But not from the scripts!

---

### Post by Grosser on 2007-01-17
Hello BobSongs

yes, i had problems too.
My Brother-modell has no Fax, it's alike.
Thanks for the information and write the script new.

---

### Post by mikebangkok on 2007-01-20
SHOT MYSELF RIGHT IN THE FOOT!

Hi

I followed the intructions, running the script for edgy, and the printer showed up, but sending a test page didn't work. So I worked through the manual instructions, but in doing so managed to delete /etc/init.d/cupsys, thinking I was only deleting a link! Oops...

So I have tried removing and reinstalling cupsys package several times in several different ways, but nothing seems to put /etc/init.d/cupsys back. I even tried compiling from source but cupsys-1.2.4 complains that gcc cannot produce executables. I have tried with gcc 3.4 and 4.1. I only have backups of the home directories. 

What can I try to get cupsys back? Is it a script or an executable. I'm running i686, ubuntu 2.6.17-generic, perhaps if possible someone could send me a copy of their /etc/init.d/cupsys if it is only a script.

---

### Post by BobSongs on 2007-01-20
> **mikebangkok said:**
> SHOT MYSELF RIGHT IN THE FOOT!

Hi

I followed the intructions, running the script for edgy, and the printer showed up, but sending a test page didn't work. So I worked through the manual instructions, but in doing so managed to delete /etc/init.d/cupsys, thinking I was only deleting a link! Oops...
...
What can I try to get cupsys back? Is it a script or an executable. I'm running i686, ubuntu 2.6.17-generic, perhaps if possible someone could send me a copy of their /etc/init.d/cupsys if it is only a script.Well, I guess it's possible if some kind soul would **attach it** to a reply to this thread. Shouldn't be a problem to just paste it back to your folder. I, however, am still runner Dapper Drake and intend to for a while. Any takers?

---

### Post by mikebangkok on 2007-01-22
My version of cupsys is, I assume, 1.2.4, but if anyone wants to help me out I'll give any version a try. If you don't want to post a script here, you can send to my email at mikeamy1979 (AT) msn.com

---

### Post by Snookered on 2007-02-13
Thank you, Bob (and everyone). Your tutorial is the best! Slowly but surely I'll convince people of the goodness that is Linux!

---

### Post by jackdaw28 on 2007-03-01
Has anyone managed to get the fax working in Xubuntu edgy? It shows up in CUPS but the brpcfax script doesn't open the dialler. If I open the jar file the script refers to the dialler opens but it has nothing to print because it wasn't opened via the script.:confused:

---

### Post by BobSongs on 2007-03-02
> **jackdaw28 said:**
> Has anyone managed to get the fax working in Xubuntu edgy? It shows up in CUPS but the brpcfax script doesn't open the dialler. If I open the jar file the script refers to the dialler opens but it has nothing to print because it wasn't opened via the script.:confused:

Forgive me for not answering sooner. But I was hoping some brave soul would answer your question. However the most this will manage is a "bump".

I'm afraid I'm not familiar with Xubuntu. So many flavours of Ubuntu, so few PCs on which to install them! ;-)

Have you read how I managed sending faxes in the tutorial? It's made for Dapper and GNOME and I don't know how well it will work. But if you try it and it works, please let us know. You're helping the community if you do.

Thanks!

---

### Post by jackdaw28 on 2007-03-04
A liitle more detail (Xubuntu edgy):
I followed both Bobsongs' and Matchless' instructions. The printer works fine. The fax is installed correctly via CUPS and has the same URI as the printer.
I've used the custom command /usr/bin/brpcfax in Thunar to open the .ps file but this will not open /usr/local/Brother/fax/brmfcfax.jar for some reason. brmfcfax.jar is in this directory and so corresponds with the location in the brpcfax script. I have java installed and if I click on brmfcfax.jar the dialler opens but has nothing to fax becuase it wasn't opened by the script..
Strangely the .ps file shows up in the queue in CUPS.
Edit/Delete Message

---

### Post by balloons on 2007-03-10
Below are the automated install scripts. It will install the fax, printing and scanner drivers for you. It will also prompt to setup the fax drivers automatically after it installs the drivers. Please note that the setup portion of the fax drivers only prompts if your running gnome. In order to fax, simply right click on any postscript file (ps extenstion) in gnome and select open with BRFAX. The dialer will pop up and you can fax from there. See the first page tutorial for more detailed instructions. Be sure and choose the right version for the OS you are running. If you scanner doesn't work after installing. Try running ```
sudo xsane
``` from the command line. If this works, follow the instructions below. I will at some point place this into the script, so it is not needed to be done manually. ```
sudo sane-find-scanner
``` this will give you the values to put in /etc/udev/rules.d/45-libsane.rules So, ```
sudo gedit /etc/udev/rules.d/45-libsane.rules
``` Add the info you get from the first command to the bottom of the file IE for the 210c it's 04f9, and 0161. I've shown the example entries below ```
# Brother|MFC 115C SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="664", GROUP="scanner" # Brother|MFC 210C SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="664", GROUP="scanner" # Brother|MFC 215C SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0193", MODE="664", GROUP="scanner"
``` replace the vendor and product ids, if they are different for your brother printer. Make sure you are part of the scanner group ```
sudo usermod -a -G scanner yourusername
``` Restart your computer and run this ```
rm -rf ~/.sane
```

---

### Post by jackdaw28 on 2007-03-11
Xubuntu edgy problem solved.:) 

The problem was not with Xubuntu edgy at all but with java 1.6.
I ran "java  -jar /usr/local/Brother/fax/brmfcfax.jar" in a terminal and got the error "java command not found". This was odd because I could open brmfcfax.jar just by double clicking on it in Thunar.
A little searching revealed that this error is common with installations of linux java 1.6 and is not an ubuntu specific issue.
I had installed java through Synaptic and so marked it for complete removal. I then installed it via Automatix which correctly made the path for the java command. It now works perfectly.

---

### Post by BobSongs on 2007-03-14
> **jackdaw28 said:**
> Xubuntu edgy problem solved....

Thanks. I'll see what I can do about reshaping the entire tutorial and adding this in.

---

### Post by TURNER on 2007-03-18
Hi all, 

I am a complete Ubuntu beginner, and have also ran into problems whilst attempting to fire up my Brother DCP 115C.

Here are the steps which I've thus far taken:

Originally I googled and located the [brother linux driver site]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html"), noticing the message which states:

> Note to users of: DCP-115C, DCP-120C, DCP-315CN, DCP-340CW, MFC-215C, MFC-425CN, MFC-640CW, MFC-820CW:
Please use the MFC-210C driver as an alternative solution.

I proceeded to download the MFC-210C driver .deb to my desktop, double clicked it and selected the option to install the package. 

Upon selecting system->administration-printing I opted to set up a new printer, as the printer is already set up Ubuntu detected the printer correctly (DCP 115C), proceeding to the next screen to select a driver I was unable to locate the recently installed MFC-210C driver, strange!? 

I took the option for a differing DCP model, which ubuntu seemed to accept, however upon printing a test page, and subsequent other pages from open office, the print job is sent to the printer and also indicates that it is printing, but nothing pops out of my printer!

After drinking more coffee, and searching the forums, I located this thread, and proceeded to copy the instructions provided.

starting with

```
sudo aptitude install csh
```

this part being successful 

next

```

sudo mkdir /var/spool/lpd
```

which resulted in

```

mkdir: cannot create directory `/var/spool/lpd': File exists
```

good, the dir is already there.....

next

```
sudo mkdir /var/spool/lpd/DCP115C
```

Creating a new printer within system->admin->printing

next

```
sudo dpkg -i ~/Desktop/print/mfc210clpr-1.0.2-1.i386.deb
```

*the file is located on my desktop in "print", hence the name change.

as the file had already been installed via a differing route as explained above, no new files were installed.

next the cups! which although seemed to install, kicked up the following error:

```
turner@turner-desktop:~$ sudo dpkg -i ~/Desktop/print/cupswrappermfc210c_1.0.0-1_i386.deb
(Reading database ... 87575 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.0-1 (using .../cupswrappermfc210c_1.0.0-1_i386.deb) ...
lpadmin: The printer or class was not found.
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
lpadmin: Unable to copy PPD file!

```

now I went into my sys->admin->printing tab and printed a test page,  although I receive a message that one print job is being processed, and the job remains in "print jobs", still nothing actually comes out of the printer.....(see screen shots)

frustrating!

Any ideas or assistance would be greatly appreciated!:guitar:

---

### Post by Galban on 2007-03-19
Hi every one!

I've followed this great howto since Dapper came out and everything worked fine, but after upgrading to Edgy, then to Feisty, thanks God, the printer part still working but not the scanner part.Openig Xsane gives me a window with the fallowing error:

Failed to open device ' brother2:bus2:dev1':
Error during device I/O

Checking if Xsane finds the scanner gives me this:

```
rodolfo@amdasus:~$ sane-find-scanner | grep usb
found USB scanner (vendor=0x04f9, product=0x0161) at libusb:001:002
rodolfo@amdasus:~$ 

``` 

Evidently Xsane finds my scanner but is unable to open the device.Thanks in advance for your time and help. Any clues and hints will be really appreciated.

---

### Post by Grosser on 2007-03-19
Hello Galban,

please make this:

_sudo gedit /etc/fstab_

Input this Text :

> none /proc/bus/usb usbfs auto,devmode=0666 0 0


_Input to Terminal:_

> sudo umount /proc/bus/usb
sudo mount /proc/bus/usb
sudo mknod -m 666 /dev/usbscanner c 180 48

---

### Post by Galban on 2007-03-19
Hello Grosser. Thnaks for your prompt answer.

This line was already on my fstab:
none /proc/bus/usb usbfs auto,devmode=0666 0 0

and I did those inputs to terminal. but unfortunelly I still getting the same error message as soon as I open Xsane. Thanks again anyways  :)

---

### Post by Grosser on 2007-03-19
Somites XSane needs sudo rights to work with the Brother-Scanner. Please test this, maybe it goes.

---

### Post by Galban on 2007-03-19
Grosser, you are right, it works! Doing it from the terminal as a root works. That's good enough for the moment. My question now is, it's possible configure xsane somewhere (lets say xsane.conf or something like that) to work as if every user were a root  and not calling Xsane as root from the terminal?? Thanks a lot Grosser!!!  :)

---

### Post by Grosser on 2007-03-19
This with my bad English...

Make a new starter (with "sudo xsane") to the panel and choice a "starter in terminal". when do that's right, it's open the terminl and ask for the sudo password when you klick on this.
i hope you understand or better you speak german. ;)

---

### Post by Galban on 2007-03-19
Grosser , yea it's a good option, the only thing it's like that others than myself will need the root password to use Xsane and that is unsafe. I'm pretty sure it should be a way to do that without have to use "sudo" from the termnial.

And your English it's ok .You know?,my maternal language is Spanish, my second is French and I have some knowledge of English and It's wonderful to me still able to communicate to somebody from Germany! :lol:

---

### Post by Grosser on 2007-03-19
Now i know what you mean...
You can take the other users to the group "scanner", maybe they needs no sudo rights.

---

### Post by Galban on 2007-03-22
\\:D/  Ok, my problem is solved. It was a line missing in /etc/udev/rules.d/45-libsane.rules. Please visit this thread [http://www.ubuntuforums.org/showthread.php?t=71104](http://www.ubuntuforums.org/showthread.php?t=71104) if you are having the same issues with a MFC 210c. Watch for post #11

---

### Post by ubuntu-mike022465 on 2007-03-24
I'm having trouble with my Brother MFC440CN which I assume is similar to the 210C, I've tried and tried and tried, uninstalled, reinstalled, etc and have gotten nowhere.

here's a screenshot of the print manager open



Help

---

### Post by BobSongs on 2007-03-27
> **ubuntu-mike022465 said:**
> I'm having trouble with my Brother MFC440CN which I assume is similar to the 210C, I've tried and tried and tried, uninstalled, reinstalled, etc and have gotten nowhere.

here's a screenshot of the print manager open



Help

[FONT=Verdana]Mr. Anderson... err, I mean: Neo... uhm... ubuntu-mike, rather. It would seem impatience has prevented the use of your printer. This particular step, from the tutorial, was obviously skipped:

> **Connection Tab:** :!: Ensure local printer is connected (Printer Type: Local Printer) and (Use a Detected Printer: Brother MFC-210C)By the way, can you dodge bullets? ;-)[/FONT]

---

### Post by ubuntu-mike022465 on 2007-03-27
The problem is, Mr Smith, :P, is that the USB option in CUPS does NOT show up. Unless I can't read English, I haven't seen Local or USB as options within the printer type selection.  If it was there, it wouldn't be an issue.  If you want, I can post a screenshot of the options within the list and we can go from there, and I totally appreciate the help and advice being given.  

Btw, I'm not a total n00b, been using Linux since Mandrake 7, when there was such an animal :D

Thanks Bob for your input, any further advice is much anticipated.


M.

Bullet dodging is my next training sim... time to go plug in    :lolflag:

---

### Post by BobSongs on 2007-03-28
> **ubuntu-mike022465 said:**
> The problem is, Mr Smith, :P, is that the USB option in CUPS does NOT show up. Unless I can't read English, I haven't seen Local or USB as options within the printer type selection.  If it was there, it wouldn't be an issue.  If you want, I can post a screenshot of the options within the list and we can go from there, and I totally appreciate the help and advice being given.  

Btw, I'm not a total n00b, been using Linux since Mandrake 7, when there was such an animal :D

Thanks Bob for your input, any further advice is much anticipated.


M.

Bullet dodging is my next training sim... time to go plug in    :lolflag:

heeheehee

Well, *Mr. Anderson*, it would appear you're living two lives. A programmer by day at a respectable software company and by night you go by the hacker alias... Neo... aww, man! Now you got me all worked up! ;-)

Your first post had a print screen showing the **MFC440CN Properties **dialog box. The box shows "Printer Type" and "Local Printer" is not selected but appears to be available (all this under the **Connection** tab, mind you).

The MFC must be off when it's installed. But the side effect of that is that the printer doesn't appear to be "there" when that dialog box is opened. It defaults to "Network Printer". When I first install my printer I can't use it either. I've got to get to that panel and click "Local Printer". When I do the MFC-210C appears in the "Use a detected printer" field just underneath.

This doesn't work for you? Lemme know. Click that option, Neo, and tell me what happens. Attach print screens of the MFC440CN dialog box after that's clicked, cool?

Thanks.

*sigh* I'm going to have to install Edgy to get those updated instructions.

*sigh*

---

### Post by ubuntu-mike022465 on 2007-03-28
Here's a couple of screenshots showing that USB is not an option, and I do have the printer plugged in via usb cable,  and turned on.


Still scratching my head... time for thinking straight sim.... :D

---

### Post by ubuntu-mike022465 on 2007-03-29
Umm, obviously the  "thinking straight" sim did bugger all for me... I found out that the USB cable was plugged into the wrong port on the printer side...


Time to return to the Source...

:confused: :redface: #-o :biggrin:

---

### Post by BobSongs on 2007-03-30
> **ubuntu-mike022465 said:**
> Umm, obviously the  "thinking straight" sim did bugger all for me... I found out that the USB cable was plugged into the wrong port on the printer side...


Time to return to the Source...

:confused: :redface: #-o :biggrin:
[FONT=Verdana] lol

Well, I was about to complain about my inability to help you because you were running a printer that wasn't an MFC-210C and that you were using Edgy... and in the end it was that mischievous cable. I'm sure originally you put it in the right slot. But Cable Gnomes mess with such things under the cover of the night.[/FONT]  ;-)

---

### Post by ubuntu-mike022465 on 2007-03-31
In actuality, I'm using Feisty Fawn 7.04 Beta right now.  At least we know that this particular set of instructions that you wrote will work with the newest Ubuntu and MFC-440CN. 

YEAH!!


:guitar:

---

### Post by FlyingIsFun1217 on 2007-04-01
Very nice!

I was thinking that I would never find any help for such an obscure printer! I'm glad I was wrong!

My one concern though is that even after using the installer script for the MFC-210C, my printer just freezes after giving it a test print job through the print administration. On the screen it says 'Recieving Data'. But thats all it does.

Is there a configuration file somewhere that needs to be changed?

Thanks for your help!
FlyingIsFun1217

---

### Post by THE_T.H.O.M.A.S.S.O_144 on 2007-04-02
Hi, I just got an Brother MFC240C, followed the instruction at the very beginning of this thread, still not getting the scanner and fax to scan and fax, but it does print. :)  However, I have a printer problem with MFC240C.... I can print text, web pages, but when I print a photo, or a PDF, I get a Big-Black-Square, instead of the desired photo. I tried setting the "photo" and "text" setting in CUPS, plus using the "Print Options" say in OpenOffice, But I still get the Big Black Square. Any thought, fixes or ideas?

Also, is it possible to write a Shell Scrip that would automaticly install everything for the Brother Printer, so that a newbie doesn't need to cut and paste command lines and upload drives separately?

---

### Post by magean on 2007-04-06
Am I the only one not getting what i select in preview scanned. This annoys me.

---

### Post by BobSongs on 2007-04-07
> **magean said:**
> Am I the only one not getting what i select in preview scanned. This annoys me.[FONT=Verdana]No doubt is quite annoying.

What printer model do you have? (Just about every kind of Brother printer has been represented within this thread.)

What distribution of Linux are you using? (Though Debian-centered some have noted this tutorial has helped them with their SuSE Linux distribution.)

If it's Ubuntu, what release are you using? (Though geared for Dapper Drake, 6.06.x, others use Edgy and some are using Fiesty.)[/FONT]

---

### Post by magean on 2007-04-08
I own a MFC 210c and use Ubuntu EDGY or more precisely XUbuntu edgy. 

When I use "full size" preset area Xsane seems to think that my A4 paper is aproximately 1 cm to high and the width about ,5 cm to big if I read the rulers surrounding the preview window. 

When I select an area what accurly gets scanned is about half a cm to the right and about a cm down 

If I choose "letter port" as preset area it seems to scan what I select in preview but then I only get 90% of the height in preview and the rulers are way off.

What I do to get around this is scan everything and trim it in GIMP before saving. However a bit annoying.

---

### Post by balloons on 2007-04-13
> **FlyingIsFun1217 said:**
> Very nice!

I was thinking that I would never find any help for such an obscure printer! I'm glad I was wrong!

My one concern though is that even after using the installer script for the MFC-210C, my printer just freezes after giving it a test print job through the print administration. On the screen it says 'Recieving Data'. But thats all it does.

Is there a configuration file somewhere that needs to be changed?

Thanks for your help!
FlyingIsFun1217

If you give us some more info, we should be able to help. Which version of ubuntu are you running? Can you attach a screenshot of what's happening or give more explanation?

---

### Post by magean on 2007-04-13
This is how I do it. Both printer and scanner. Works for all 3 flavors versions of ubuntu. 

Installing MFC 210C through terminal

Printer:

Download CUPS Wrapper and LPR Driver from brother.
for example
wget [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb)
wget [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc210c_1.0.0-1_i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc210c_1.0.0-1_i386.deb)

Install the C Shell
sudo apt-get install csh

TURN PRINTER OFF THIS IS IMPORTANT!

sudo mkdir /var/spool/lpd
sudo mkdir /var/spool/lpd/MFC210C (printer name at the end)

sudo dpkg -i mfc210clpr*

sudo ln -s /etc/init.d/cupsys /etc/init.d/cups

sudo dpkg -i cupswrappermfc210c*

Turn Printer ON

If you got the error message "lpadmin:Unable to copy PPD file" when installing the Wrapper do the following

Find out the device url
lpinfo -v
Read and "remember" the device url for example "usb://Brother/MFC-210C"

Find the name and path of the ppd file
ls /usr/share/cups/model
Read and remember the filename for example "/usr/share/cups/model/brmfc210c_cups.ppd"

Administer the printer
sudo lpadmin -p (printer name) -E -v (device urk) -P (PPD file path and name)

for example
sudo lpadmin -p MFC210C -E -v usb://Brother/MFC-210C -P /usr/share/cups/model/brmfc210c_cups.ppd

All done!
For printer options turn your browser of choice to 
[http://localhost:631/printers/](http://localhost:631/printers/) (this requires local access)


Install MFC 210c Scanner
Turn MFC210 OFF THIS IS IMPORTANT!

Download scanner driver from Brother
for example
wget [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.3-0.i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.3-0.i386.deb)
install sane and Xsane
sudo apt-get install sane xsane

install scanner
sudo dpkg -i brscan2*

Turn printer ON

Make scanner accesible to all users

Edit /etc/udev/rules.d/45-libsane.rules

Use your favorite text editor and add the following above the last row:
#brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"

The last four rows should then look like:
#brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"

LABEL="libsane_rules_end"

Restart the OS.
sudo shutdown -r now

---

### Post by BobSongs on 2007-04-15
[FONT=Verdana]:-) Nice. I imagine the 3 flavours of Ubuntu you speak of are Kubuntu, Ubuntu and Xubuntu of the Edgy flavour?

As my instructions are based on Dapper Drake I'll send folks to your post for Edgy instructions.[/FONT]

---

### Post by Kulag on 2007-04-18
Thanks for the tutorial.

Oddly enough, in 64 bit Feisty, I needed to install sun-java6-bin after following this tutorial to get it to work... I think.

---

### Post by whistlerspa on 2007-04-21
I use the shell script file 

**Brother_MFC-210C_Installer.sh** which takes you through the whole process. 

You need to run this twice for some reason and during the second install run the command

**sudo cp /usr/share/cups/model/brmfc210c_cups.ppd /usr/share/ppd/**

Until you do this the paper settings don't work and you can't print anything.

A manual copy and paste as root user doesn't work for me for some reason.
I downloaded the shell script some time ago and don't remember from where but a Google search should locate it I think.

This takes the hassle and pain out of the process and I installed the printing software on a laptop and desktop yesterday in about 10 minutes.

---

### Post by TURNER on 2007-04-23
Upon Feisty release I decided to conduct a fresh install of Ubuntu using the new Feisty release. All has gone smoothly aside from one glitch, my printer now refuses to work!

Using the instructions provided below I was able to get my Brother DCP 115C printer working completely fine in Edgy:



```
1. Download "mfc210clpr-1.0.2-1.i386.deb" and "cupswrappermfc210c_1.0.0-1_i386.deb" from brother website

2. Open Terminal (Applications --> Accessories --> Terminal) and do following

3. Install csh, in Terminal type:
a. sudo apt-get install csh

4. Install mfc210clpr-1.0.2-1.i386.deb, in Terminal type:
a. sudo mkdir /var/spool/lpd
b. sudo mkdir /var/spool/lpd/MFC210C
c. sudo dpkg -i mfc210clpr-1.0.2-1.i386.deb

5. Install cupswrappermfc210c_1.0.0-1_i386.deb, in Terminal type:
a. sudo dpkg -i cupswrappermfc210c_1.0.0-1_i386.deb
NB: Ignore any errors, especially if last line is" lpadmin: Unable to copy PPD file!"

6. Turn printer on
```

Followed by:


```

sudo gedit /etc/fstab

ADD:

none /proc/bus/usb usbfs auto,devmode=0666 0 0

sudo umount /proc/bus/usb
sudo mount /proc/bus/usb
sudo mknod -m 666 /dev/usbscanner c 180 48
```

As mentioned, this was enough to get my printer working in Edgy.....seems Feisty doesn't like it however!

The printer is present under system admin printers, and accepts a test page, which doesn't make it to the printer, interestingly enough my printer does momentarily display "receiving data"....but doesn't attempt to print.

Feistys new auto detection wizard does recognise my printer successfully as a Brother DCP 115, and recommends a driver as part of the set up....however this results in the same story as before!

Any assistance or recommendations??

---

### Post by balloons on 2007-04-23
Try the script found here:

[http://ubuntuforums.org/showthread.php?p=2277190#post2277190](http://ubuntuforums.org/showthread.php?p=2277190#post2277190)

EDIT: I should mention, try and uninstall or remove whatever you did, and then run the script.

---

### Post by TURNER on 2007-04-24
>  Try the script found here:

thanks for the reply, I am at work in Win**ws at the mo, I will certainly give it a try when I get back home.

I managed to uninstall the lp and cups wrapper via synaptic, I tried my best via the terminal, but for some reason I just couldnt remove the installed drivers....one thing to note however, the files and folders created during install are still there, is this ok or should they also be removed?

Thanks

Dale

---

### Post by balloons on 2007-04-24
If you removed the drivers, you should be ok - just note that the script will install as an MFC210C. So, I see you actually have a compatible model that uses the same drivers, so it will probably set up the printer as a MFC210C in the printers administration box.

---

### Post by Kynan on 2007-04-26
Wohoo! guitara you are a champ!
I have a DCP-115c printer aswell which used to work on Edgy but will nolonger worked on feisty using the same methods. I downloaded the scipt but had no clue as how to get it to run, i've only been using ubuntu for just over a week now. 
After some research [www.monkeyblog.org/ubuntu/installing](www.monkeyblog.org/ubuntu/installing) I figured out how to run it... 
for noobies like myself this is how i did it..

1. Make sure your printer is connected to your computer.

2. right click on the downloaded file and goto properties and the tab permissions click allow executing file as program.

3. go to the terminal and type
sudo /home/"username"/Desktop/Feisty_Brother_MFC-210C_Installer.sh

4. A box should come up, asking what you want to install (beautiful), choose to install just the printer first because when i tried doing both at the same time nothing worked for some reason. 

5. Follow the pop up messages.

6. Once completed the print box should appear and now right click on it and select properties, if you can change the paper type you should have no troubles printing, Try printing a test page, if  it doesn't work then try again it took me 2 attempts to get it to work.

7. Try installing the Scanner (mine still doesn't work but maybe it will work for you)

Goodluck and thanks guitara your script works well :-)

---

### Post by bigken on 2007-04-26
Heres how I got my mfc3820cn working in feisty (network)

sudo aptitude install csh

download drivers from brother and use the debi installer 

and hey presto it printed 

for the scanner 

again download drivers from brother and use the debi installer 

then in a terminal run
 
brsaneconfig -a name=Scanner model=MFC-3820CN ip=xxx.xxx.xxx.xxx


many thanks to bobsongs without him this would never have being possible :)


its never being so easy :):)

---

### Post by lambretta on 2007-04-27
Thanks all for you posts, I have managed to get the MFC-440CN working great on my network (at least for printing at this stage).  It is connected to my network through the router. :) 

I didn't use any scripts.

I am running 7.04.

---

### Post by TURNER on 2007-04-27
> I have a DCP-115c printer aswell which used to work on Edgy but will nolonger worked on feisty using the same methods

****....still no success...

I followed the instructions to a T.

First downloaded the Feisty.sh

gave it the correct permissions

ran  sudo /home/"username"/Desktop/Feisty_Brother_MFC-210C_Installer.sh (selected printer only)

followed the prompts, and nothing....

I removed the printer and tried it again.....still nothing.

The printer is there, recognised as MFC210C....but within the properties dialog box (after selecting print test page is the status: Printing: Printer not connected; will retry in 30 seconds...)

I can amend the paper (or at least paper size), and the printer is plugged into a working usb port....

---

### Post by TURNER on 2007-04-29
Ok no need to panic....(as if anybody was :) ) my printer is up and running.Thanks all!

---

### Post by balloons on 2007-04-29
Thanks - more than likely the scanner is requiring root provileges. try running sudo xsane and see if it works. It's not really a fix, but a workaround. If it works, I can help you resolve the issue.

> **Kynan said:**
> Wohoo! guitara you are a champ!
I have a DCP-115c printer aswell which used to work on Edgy but will nolonger worked on feisty using the same methods. I downloaded the scipt but had no clue as how to get it to run, i've only been using ubuntu for just over a week now. 
After some research [www.monkeyblog.org/ubuntu/installing](www.monkeyblog.org/ubuntu/installing) I figured out how to run it... 
for noobies like myself this is how i did it..

1. Make sure your printer is connected to your computer.

2. right click on the downloaded file and goto properties and the tab permissions click allow executing file as program.

3. go to the terminal and type
sudo /home/"username"/Desktop/Feisty_Brother_MFC-210C_Installer.sh

4. A box should come up, asking what you want to install (beautiful), choose to install just the printer first because when i tried doing both at the same time nothing worked for some reason. 

5. Follow the pop up messages.

6. Once completed the print box should appear and now right click on it and select properties, if you can change the paper type you should have no troubles printing, Try printing a test page, if  it doesn't work then try again it took me 2 attempts to get it to work.

7. Try installing the Scanner (mine still doesn't work but maybe it will work for you)

Goodluck and thanks guitara your script works well :-)

---

### Post by balloons on 2007-04-29
I wasn't worried :-)  - did a reboot seem to make it work - or did it just work after a few seconds? people seem to be saying that it takes a few minutes before it will print after the install.

> **TURNER said:**
> Ok no need to panic....(as if anybody was :) ) my printer is up and running.Thanks all!

---

### Post by Kynan on 2007-04-30
Hey thanks guitara i did manage to get it to work through typing sudo xsane and i found a workaround, by following the instructions on post number 5 on this link [http://ubuntuforums.org/showthread.php?t=166944](http://ubuntuforums.org/showthread.php?t=166944) but i noticed (as everyone else that did this on that link) you get 3 error messages when trying to close, before it actually closes. still better than before tho.

---

### Post by Kynan on 2007-04-30
> **guitara said:**
> I wasn't worried :-)  - did a reboot seem to make it work - or did it just work after a few seconds? people seem to be saying that it takes a few minutes before it will print after the install.
I forgot to mention in my steps that i had to change the printer device from network printer to local printer, before it would print, that was the case for TURNER and ChilliBob also on this link [http://ubuntuforums.org/showthread.php?p=2544341#post2544341](http://ubuntuforums.org/showthread.php?p=2544341#post2544341)

---

### Post by Matchless on 2007-05-01
BobSongs,
               I have updated to Feisty and have updated my MFC-215C howto. Maybe you would care to update the link in your howto [http://ubuntuforums.org/showthread.php?t=302960](http://ubuntuforums.org/showthread.php?t=302960)

Great work on your side and keep it up! It is always good to see someone really dedicated to sharing and helping others.

---

### Post by Matchless on 2007-05-01
> **guitara said:**
> Feisty's HERE! I've added a beta version of the script. PLEASE give me some feedback if you find something not working.
EDIT: I've changed nothing, but we've had a few confirmed good feisty installs. If your printer is a MFC-210C, DCP-115C, DCP-117C, DCP-120C, DCP-315CN, DCP-340CW,MFC-215C, MFC-425CN, MFC-640CW, or MFC-820CW this should work for you. Although it was written specifically for and tested on a MFC-210C. One final note, if your scanner doesn't work, try sudo xsane. If that solves the problem post, and we can help you resolve the issue.

Thanks,
           I have added a link to this thread in my howto for the Brother MFP-215C on Feisty at [http://ubuntuforums.org/showthread.php?t=302960](http://ubuntuforums.org/showthread.php?t=302960)

---

### Post by BobSongs on 2007-05-01
> **Kynan said:**
> I forgot to mention in my steps that i had to change the printer device from network printer to local printer, before it would print, that was the case for TURNER and ChilliBob also on this link [http://ubuntuforums.org/showthread.php?p=2544341#post2544341](http://ubuntuforums.org/showthread.php?p=2544341#post2544341)
[FONT=Verdana]This is an annoying part of the tutorial. And it is covered: the idea that... for some reason the printer is listed as a Network Printer. I believe this is due to the drivers installed when the printer is off.

Turning the printer **on** when installing the drivers is disastrous. Do yourself a favour and avoid this. But with the printer off the system assumes the installation was network related. Resetting this is important and often overlooked. Bit of a head ache at times:

[/FONT][LIST]
[*][FONT=Verdana]**"Connection Tab:** :!: Ensure local printer is connected (Printer Type: Local Printer) and (Use a Detected Printer: Brother MFC-210C)."[/FONT][/LIST]

---

### Post by bigjohn992 on 2007-05-04
> **guitara said:**
> I've attached a new version of the script for edgy and dapper that automates the setup of the fax drivers, as well as corrects a naming bug. I've tested this, and it works on my machine for edgy. It will prompt to setup the fax drivers automatically after it installs the drivers. Please note that the setup portion of the fax drivers only prompts if your running gnome. Let me know if it works for you. After it's all done, simply right click on any postscript file (ps extenstion) in gnome and select open with BRFAX. The dialer will pop up and you can fax from there.

EDIT: No one said anything, but I just realized this won't work unless java5 is installed (BRFAX requires sun java). The updated scripts take care of the issue by installing and configuring sun java if necessary. If BRFAX never showed up when you right-clicked to fax, that's why, and reinstalling with this script should fix it. Stay tuned for a feisty version - around the same time feisty is released. There's a kernel bug preventing me from upgrading (again) right now.

EDIT: Feisty's HERE! I've added a beta version of the script. PLEASE give me some feedback if you find something not working.
EDIT: I've changed nothing, but we've had a few confirmed good feisty installs. If your printer is a MFC-210C, DCP-115C, DCP-117C, DCP-120C, DCP-315CN, DCP-340CW,MFC-215C, MFC-425CN, MFC-640CW, or MFC-820CW this should work for you. Although it was written specifically for and tested on a MFC-210C. One final note, if your scanner doesn't work, try sudo xsane. If that solves the problem post, and we can help you resolve the issue.

Thanks guitara!  I'm a ubuntu newbie running Feisty and had no problem getting my mfc210c printer working using your excellent work.  I also installed the scanner and can get it work only by using "sudo xsane" as you suggest.  I tried using just "xsane" from the terminal, but got an error "Brother 2:Bus4;Dev1: Error During I/O".  Do you have any suggestions?

---

### Post by ahalin on 2007-05-06
Your help file was spot on. Only one thing I had to work out for myself was that the code

[INDENT][/INDENT]ls /usr/share/cups/model

returned the following file name:

[INDENT][/INDENT]brmfc210c_cups.ppd  custom  gutenprint  pxlcolor.ppd  pxlmono.ppd

which didn't work, so I just used your example:

[INDENT][/INDENT]/usr/share/cups/model/brmfc210c_cups.ppd

with a final code string of:

[INDENT][/INDENT]sudo lpadmin -p BrotherMFC210C -E -v usb://Brother/MFC-210C -P /usr/share/cups/model/brmfc210c_cups.ppd

which worked a treat, thank you.

John S, East Timor

---

### Post by balloons on 2007-05-07
> **bigjohn992 said:**
> Thanks guitara!  I'm a ubuntu newbie running Feisty and had no problem getting my mfc210c printer working using your excellent work.  I also installed the scanner and can get it work only by using "sudo xsane" as you suggest.  I tried using just "xsane" from the terminal, but got an error "Brother 2:Bus4;Dev1: Error During I/O".  Do you have any suggestions?

Type this into a terminal
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```

Add this line at the bottom of the file, and save

```
# Brother MFC 210C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="664", GROUP="scanner"
```

At some point, I'll have to put this step into the script as well - it appears it's always needed.

---

### Post by ginestre on 2007-05-23
I used the Feisty version of the script, accepting all options (print-fax-scan). However, when I try to print the printer stays permanently in "Data reception" mode. Any ideas? It's an Italian MFC 210C, ie, the firmware gives me messages in Italian. I've appended below the script output: grateful for help. Printing in Ubuntu seems to be the pits! All help very gratefully received.

[EDIT] Looking at the print jopbs via the CUPS interface I find that CUPS says they are completed. But no paper comes out of the printer <SOB!>. The scaner works wonderfully; and the fax gives a CUPS message of 'Stopped."




PASTING script output------------

richard@Richard-upstairs:~$ sudo /home/richard/systemdocs/Feisty_Brother_MFC-210C_Installer.sh
Password:
init: illegal runlevel: (null)
Try `init --help' for more information.
root
Brother MFC-210C Fax Driver|Brother MFC-210C Scanner Driver
--11:30:44--  [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxcups-1.0.0-1.i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxcups-1.0.0-1.i386.deb)
           => `brmfcfaxcups-1.0.0-1.i386.deb.1'
Resolving solutions.brother.com... 213.144.186.200, 213.144.186.209
Connecting to solutions.brother.com|213.144.186.200|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29,308 (29K) [application/octet-stream]

100%[====================================>] 29,308       156.57K/s             

11:30:44 (156.03 KB/s) - `brmfcfaxcups-1.0.0-1.i386.deb.1' saved [29308/29308]

--11:30:44--  [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxlpd-1.0.0-1.i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/faxshare/brmfcfaxlpd-1.0.0-1.i386.deb)
           => `brmfcfaxlpd-1.0.0-1.i386.deb.1'
Resolving solutions.brother.com... 213.144.186.200, 213.144.186.209
Connecting to solutions.brother.com|213.144.186.200|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,716 (25K) [application/octet-stream]

100%[====================================>] 25,716       147.75K/s             

11:30:45 (147.69 KB/s) - `brmfcfaxlpd-1.0.0-1.i386.deb.1' saved [25716/25716]

(Reading database ... 
dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
109015 files and directories currently installed.)
Preparing to replace brmfcfaxcups 1.0.0-2 (using .../brmfcfaxcups-1.0.0-1.i386.deb) ...
Unpacking replacement brmfcfaxcups ...
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Setting up brmfcfaxcups (1.0.0-2) ...
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

(Reading database ... 
dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
109015 files and directories currently installed.)
Unpacking brmfcfaxlpd (from .../brmfcfaxlpd-1.0.0-1.i386.deb) ...
dpkg: error processing /tmp/brmfcfaxlpd-1.0.0-1.i386.deb (--install):
 trying to overwrite `/usr/local/Brother/inf/setupPrintcap', which is also in package hl1230lpr
Errors were encountered while processing:
 /tmp/brmfcfaxlpd-1.0.0-1.i386.deb
ln: creating symbolic link `/usr/share/ppd/brfax_cups.ppd' to `/usr/share/cups/model/brfax_cups.ppd': File exists
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
 5488 ?        00:00:26 gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflac++5c2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  sun-java6-bin
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-sazanami-gothic
  ttf-sazanami-mincho
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  sun-java6-jre
The following packages will be upgraded:
  sun-java6-bin
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/32.5MB of archives.
After unpacking 93.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package sun-java6-jre.
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
109015 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
Preparing to replace sun-java6-bin 6-00-2ubuntu2 (using .../sun-java6-bin_6-00-2ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-bin ...
Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

Setting up hl1230lpr (1.1.2-1) ...
/var/lib/dpkg/info/hl1230lpr.postinst: 4: /etc/init.d/lpd: not found
dpkg: error processing hl1230lpr (--configure):
 subprocess post-installation script returned error exit status 127
Setting up sun-java6-bin (6-00-2ubuntu2) ...

Setting up sun-java6-jre (6-00-2ubuntu2) ...

Errors were encountered while processing:
 hl1230lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.6.0-sun
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
Brother MFC-210C Fax Driver|Brother MFC-210C Scanner Driver
--11:33:41--  [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.1-0.i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/sane_debian/brscan2-0.2.1-0.i386.deb)
           => `brscan2-0.2.1-0.i386.deb'
Resolving solutions.brother.com... 213.144.186.200, 213.144.186.209
Connecting to solutions.brother.com|213.144.186.200|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 68,010 (66K) [application/octet-stream]

100%[====================================>] 68,010        58.01K/s             

11:33:44 (57.84 KB/s) - `brscan2-0.2.1-0.i386.deb' saved [68010/68010]

Selecting previously deselected package brscan2.
(Reading database ... 109917 files and directories currently installed.)
Unpacking brscan2 (from /tmp/brscan2-0.2.1-0.i386.deb) ...
Setting up brscan2 (0.2.1) ...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sane is already the newest version.
xsane is already the newest version.
The following packages were automatically installed and are no longer required:
  libflac++5c2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up hl1230lpr (1.1.2-1) ...
/var/lib/dpkg/info/hl1230lpr.postinst: 4: /etc/init.d/lpd: not found
dpkg: error processing hl1230lpr (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 hl1230lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@Richard-upstairs:~$

---

### Post by balloons on 2007-05-23
you've got a real issue with apt. try this first

```
sudo apt-get remove hl1230lpr
sudo apt-get autoremove
```

if that gives any errors, do this:

```
sudo rm /var/lib/dpkg/info/hl1230lpr.postrm && sudo apt-get remove hl1230lpr && sudo dpkg --purge hl1230lpr
```

once you can run
```
sudo apt-get update
sudo apt-get dist-upgrade
```
with no errors, post back.

EDIT: let's not try running the script again till you've posted
one more thing - post the output of you running the code i gave thanks

---

### Post by ginestre on 2007-05-24
Guitara, first and foremost, thanks for the clear and prompt reply!

Second, I tried the commands you gave: the first command 

[sudo apt-get remove hl1230lpr]

told me that it couldn't find hl1230lpr, and since I assume that is an error I ran your third command after the second, as instructed.
The second
[sudo apt-get autoremove]

ran happily, and the third 

[sudo rm /var/lib/dpkg/info/hl1230lpr.postrm && sudo apt-get remove hl1230lpr && sudo dpkg --purge hl1230lpr]

gave me this message:
richard@Richard-upstairs:~$ sudo rm /var/lib/dpkg/info/hl1230lpr.postrm && sudo apt-get remove hl1230lpr && sudo dpkg --purge hl1230lpr
rm: cannot remove `/var/lib/dpkg/info/hl1230lpr.postrm': No such file or directory


Thanks again for your help.




-------------- terminal session --------------

here is the COMPLETE output from the terminal session, in case it helps understand: I'm afraid it's rather long because I hadn't noticed a system update was due, and that happened as well as the other output- but I'm loath to edit it as I might cut something important by mistake

richard@Richard-upstairs:~$ sudo apt-get remove hl1230lpr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package hl1230lpr is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libflac++5c2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
richard@Richard-upstairs:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libflac++5c2
The following packages will be REMOVED:
  libflac++5c2
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 188kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 109928 files and directories currently installed.)
Removing libflac++5c2 ...
richard@Richard-upstairs:~$ sudo rm /var/lib/dpkg/info/hl1230lpr.postrm && sudo apt-get remove hl1230lpr && sudo dpkg --purge hl1230lpr
rm: cannot remove `/var/lib/dpkg/info/hl1230lpr.postrm': No such file or directory
richard@Richard-upstairs:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US
Get:2 [http://www.telemail.fi](http://www.telemail.fi) edgy Release.gpg [189B]                           
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                      
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://www.telemail.fi](http://www.telemail.fi) edgy/fonts Translation-en_US                        
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US        
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US    
Hit [http://www.telemail.fi](http://www.telemail.fi) edgy Release                              
Err [http://www.telemail.fi](http://www.telemail.fi) edgy Release                                        
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US              
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Get:11 [http://www.telemail.fi](http://www.telemail.fi) edgy Release [1211B]                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources               
Ign [http://www.telemail.fi](http://www.telemail.fi) edgy Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages     
Ign [http://www.telemail.fi](http://www.telemail.fi) edgy/fonts Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages             
Ign [http://www.telemail.fi](http://www.telemail.fi) edgy/fonts Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://www.telemail.fi](http://www.telemail.fi) edgy/fonts Packages                           
Hit [http://www.telemail.fi](http://www.telemail.fi) edgy/fonts Sources                            
Get:12 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg [189B]                    
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release
  
Get:13 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release [7228B]
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources
Fetched 8826B in 2m1s (73B/s)                                                  
Reading package lists... Done
W: GPG error: [http://www.telemail.fi](http://www.telemail.fi) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
richard@Richard-upstairs:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  libfreetype6
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 338kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libfreetype6
Install these packages without verification [y/N]? y
Get:1 [http://www.telemail.fi](http://www.telemail.fi) edgy/fonts libfreetype6 2.3.4-0mlind1.1~edgy1 [338kB]
Fetched 338kB in 1s (249kB/s)        
(Reading database ... 109924 files and directories currently installed.)
Preparing to replace libfreetype6 2.3.4-0mlind1~edgy1 (using .../libfreetype6_2.3.4-0mlind1.1~edgy1_i386.deb) ...
Unpacking replacement libfreetype6 ...
Setting up libfreetype6 (2.3.4-0mlind1.1~edgy1) ...

richard@Richard-upstairs:~$

---

### Post by balloons on 2007-05-24
Ok - looks like you've got edgy and feisty sources. are you running edgy or feisty? stick with the repos for the version you have. if you are running feisty, remove all of the edgy entries in your /etc/apt/sources.list. 

```
sudo gedit /etc/apt/sources.list
```

it looks like you have non-offical repos as well, so i assume you've done this before. After you've changed the list, update.

```
sudo apt-get update
```

next remove any installed printers the script installed.

```
System->Administration->Printing
```

you can select and delete them. Should be mfc210c, and BRFAX.

then try running the script and pasting the output.

---

### Post by ginestre on 2007-05-24
Thank you! That worked, and now the printer prints. I edited out the entries in the sources.list -originally I had edgy but I then accepted the 'upgrade to feisty' option and it looks as though the sources list wasn't taken care of properly. My fault, I'm sure- but this is a new universe for me. 

Now the sources list is really short: is that right? Maybe I should get an uncontaminated one from somewhere (where?) and use that? 

But thanks a million! I've been using ubuntu for a month without a printer! 

Next task: set the laser printer up. Another Brother, but connected over the network. I thinj this is what is called a steep learning curve!


Best, and thanks again.

---

### Post by balloons on 2007-05-24
glad to hear it worked..

ask and ye shall receive

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

this will generate a sources.list for you to use

---

### Post by Killtown on 2007-05-29
Is there a current install instructions list for the MFC-210C for Feisty?

---

### Post by BobSongs on 2007-05-29
> **Killtown said:**
> Is there a current install instructions list for the MFC-210C for Feisty?

[font=Verdana]Well. This is my current status.

My MFC-210C is now attached to my MacBook Pro (I'm a traitor... I'll admit it).

My family PC is not easily messed with. It's a practical family PC and members do not want me to "upgrade" or "tinker" with it unless necessary. So it runs Dapper Drake until further notice.

I visit this thread to ensure all is well and it appears many have chosen to adopt it and answer questions. Kudos people!!

However I can no longer make updates to the tutorial. But I will do my best to get others to help me there. Let's see what I can do.[/font]

---

### Post by djshag on 2007-05-31
First of all, thank you for this tutorial. I am somewhat of a newb and found this to be very easy to follow. Next, I'd like to second the call for a feisty tutorial only in that it appears that feisty may not properly support my MFC 240C as it will print without issue, but faxing and scanning won't work.

After installation of the drivers as per this tutorial, when I right-click the post script file to print it to fax, I follow the instructions and nothing happens. No errors, no dialpad.... nothing.

The scanner shows in X-Sane but produces a "Failed to open device 'brother2:bus4;dev1'; Error during device I/O." All settings appear to be correct, but feisty just seems not to like this printers scanning capabilities.

Or perhaps I am just really screwing up (a definite possibility)!

Thanks

---

### Post by balloons on 2007-05-31
did you use the install script?
does sudo xsane work to scan?

---

### Post by djshag on 2007-06-01
OMG! sudo xsane worked! So is it somehow a permission thing? Thank you for the reply!
Oh.... I did follow the script. Very carefully.....   :-)

---

### Post by balloons on 2007-06-01
I typed this a few pages ago - it's still not in the script, sorry. :-( this will fix your issue.

Type this into a terminal

```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```

Add this line at the bottom of the file, and save

```
# Brother MFC 210C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="664", GROUP="scanner"

```

as to the faxing issue - is java installed and configured properly? the script should have done this for you.
```

		sudo apt-get install sun-java6-jre
		sudo update-java-alternatives -s java-1.6.0-sun
```

does this pop up the dialpad?
```
java -jar /usr/local/Brother/fax/brmfcfax.jar
```

what about this?
```
java -jar /usr/bin/brmfcfax,jar
```

---

### Post by faberlillo on 2007-06-03
Hey the mfc 210c doesn't appear on the printer box....what I have to do now???

I follow your instruction with the commad ./Feisty_Brother_MFC-210C_Installer.sh after become sudo /bin/bash,  and I have a Feisty 7.04, and a printer Brother Dcp 115C.... help this blessed printer wiork perfectly on Edgy...and now???


Fabrizio

---

### Post by balloons on 2007-06-06
did your printer stop working on the upgrade? what is the terminal output of the script when you run it? can you paste it here? Thanks. The correct way to run is to download the script, then type
```
 sudo ./Feisty_Brother_MFC-210C_Installer.sh 
```

---

### Post by djshag on 2007-06-12
guitara:

Hope your still around. Been busy and kinda forgot that this was still an issue.
Anyway:

Already loaded...
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```


And this...
```
# Brother MFC 210C
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="664", GROUP="scanner"
```


This is installed as well...
```
sudo apt-get install sun-java6-jre
```

This however...
```
sudo update-java-alternatives -s java-1.6.0-sun
```
produced...
> update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.6.0-sun

This....
```
java -jar /usr/local/Brother/fax/brmfcfax.jar
```
produces...
> Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at javax.swing.JFrame.<init>(libgcj.so.70)
   at brFaxDialog.<init>(brmfcfax.java:72)
   at brmfcfax.main(brmfcfax.java:314)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...6 more


And finally this...
```
java -jar /usr/bin/brmfcfax,jar
```
produces...
> Failed to load Main-Class manifest attribute from /usr/bin/brmfcfax,jar


Does that give you any indication as to what is happening?
Thanks for the help! :D

---

### Post by applecookie on 2007-06-12
Can somebody help me please?

I tried all, written in the howto, but the Brother cupswrapper driver and lpr - Driver made no PPD - File and so I can't select any MFC-210 - Printer.

I use edgy (in near future feisty) and a Brother DCP-340CW

Scanning works perfectly - only printing not...

Frank

---

### Post by bluvy on 2007-06-13
Hey there,
I'm currently using Feisty fawn..I just installed it last night, so I'm a super noob.
I installed my MFC-7420 lps and cuswrapper and when I go to Admin > Printing, the MFC7420 is displayed there.
But here's the problem... I can't seem to print... When I want to print something it says it's "printing 1 job"...but the printer never starts printing! When I go to the printer properties, it says "printer not connected: retry in 30sec"... but the printer is connected
did something go wrong during my setup?

---

### Post by balloons on 2007-06-15
sorry dshjag, it's

```
sudo update-java-alternatives -s /usr/lib/jvm/java-6-sun
```

java-6-sun should be a symlink to whatever folder java 6 is installed in.

---

### Post by timephoenix on 2007-06-19
I'm having trouble with an MFC-620CN. I've followed the howto, successfully installed the CUPS and LPR drivers, but when I try to print a test page, the LCD simply lights, displays "Receiving Data" then stops before doing anything.

Any help is appreciated. 

TP

---

### Post by balloons on 2007-06-19
timephoenix and bluvy - did you follow the tutorial on the first page, or use my script?
[http://ubuntuforums.org/showthread.php?p=2277190#post2277190](http://ubuntuforums.org/showthread.php?p=2277190#post2277190)

You may want to try running the script, or following the tutorial. It sounds like this is the issue:

 Go to System -> Admin -> Printing, and right click the mfc210c (or whatever printer you installed), and click properties. Then click the connection tab. What does it say? Try changing to local or detected printer. if that doesn't work, try Network printer (IPP Printer), and uri (in my case usb://Brother/MFC-210C). You want to input the device uri here. you can load up [http://localhost:631/printers/](http://localhost:631/printers/) in your browser and find the device uri listed for your printer there.

---

### Post by djshag on 2007-06-21
Just thought I'd check in to say thanks to those that offered assistance. Printing, printing over the network (from Windows and linux boxes is working great).
Thanks again!

---

### Post by bluvy on 2007-06-21
Thank you soooo much!  Whew..I'm such a noob at this... my printer finally works! :)

---

### Post by Killtown on 2007-06-27
Followed instructions at OP, but my MFC210C still doesn't print.  My printer does read "transmitting data" when trying to do a test print.  The printer icon *does* show up in the Admin/Printer section however.

When I hit "properties" over the printer icon, I notice there certain options don't appear to be able to change under the following tabs:

**General** - resolution
**Paper** - no options show
**Advanced** - nothing shows up


My scanner does work with XSane though.

[Solved [below]("http://ubuntuforums.org/showpost.php?p=2925114&postcount=356")]

---

### Post by Killtown on 2007-06-27
Ok, I figured it out (apparently I didn't read too well!).  I'll repeat what I did for anybody who runs into the same problem trying to set up the Brother MFC-120C printer for Ubuntu 7.04 Feisty Fawn.


1.  Follow the directions in the [original post]("http://ubuntuforums.org/showpost.php?p=587083&postcount=1").

2.  If you run into the problem I did in the [above post]("http://ubuntuforums.org/showpost.php?p=2924773&postcount=355"), download the following script (originally found [here]("http://ubuntuforums.org/showpost.php?p=2277190&postcount=283")) to your desktop: 
[URL="http://ubuntuforums.org/attachment.php?attachmentid=30031&d=1176933547"]
Feisty_Brother_MFC-210C_Installer.sh[/URL] (click link and then select "Save to Disk")


(Original directions to the following below are found [here]("http://ubuntuforums.org/showpost.php?p=2537762&postcount=318"), but there was one mistake.)

3. **Important:** right-click mouse on the file you just downloaded to your Desktop, go to "Properties", then "Permissions", then **check the** "Execute" box.

4. Open your Terminal and change your directory to Desktop (make sure you capitalize "D"):

```
cd Desktop
```

5. Then paste **this code** into Terminal and enter, then your password and hit enter:

```
sudo ./Feisty_Brother_MFC-210C_Installer.sh
```

A small window should pop up:  "Brother MFC-120C Beta Installer"

6. **Only check** the "Printer Driver" box (or it may not work), hit "OK" and it will do the rest for you.

Your printer should now show all the configure options in your MFC120C icon in your *Printers* box in System/Administration/Printing and should now be able to print.


(Instructions also found [here]("http://ubuntuforums.org/showpost.php?p=2925204&postcount=12").)

---

### Post by bogr@ on 2007-06-29
Hi, 
I've followed all of this thread (and the others with similar issues) and have got the drivers installed; MFC210C displays "Ready"; properties & connection are set correctly and the DCP-115C is detected on USB #1.

I click "Print a Test Page" and it responds "Letter test page has been sent to MFC210C";
but there is no response from the printer to show any connection at all.

I've tried the same through "localhost:631/printers" and still no response.

But nothing prints.

Feisty 7.04 64bit
DCP-115C

Are the brother drivers OK for 64bit?

---

### Post by lordrahvin on 2007-07-05
I'm having trouble getting the MFC-210c to work with Xubuntu 7.04 running GNOME.  
I have the same problem described by the above users.  Printer shows ready.  Printer shows as a print option.  Printer even "receives information" but nothing prints.  

It looks like there was an error in running the script.  I have no idea why.  The same error pops up even when I run "sudo dpkg -i --force-all cupswrappermfc210c_1.0.0-1_i386.deb".  It says there's a permission issue but I don't understand how there can be a permission issue if I'm running it under sudo.

The permissions for the directory show "root" and so I tried becoming root for a short time to see if that would help, using "sudo su" but I got the same results.  


I miss my printer.  *sniffle*

Here's a copy of the terminal session.  (I added color to show the areas that I thought might help identify the problem.)


root@lordrahvin-desktop:/home/lordrahvin# cd /home/lordrahvin/Desktop
root@lordrahvin-desktop:/home/lordrahvin/Desktop# sudo ./Feisty_Brother_MFC-210C_Installer.sh
init: illegal runlevel: (null)
Try `init --help' for more information.
root
Brother MFC-210C Printer Driver
mkdir: cannot create directory `/var/spool/lpd': File exists
mkdir: cannot create directory `/var/spool/lpd/MFC210C': File exists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
csh is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 45 not upgraded.
--19:49:29--  [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc210c_1.0.0-1_i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc210c_1.0.0-1_i386.deb)
           => `cupswrappermfc210c_1.0.0-1_i386.deb'
Resolving solutions.brother.com... 64.212.100.110, 64.212.100.124
Connecting to solutions.brother.com|64.212.100.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12,342 (12K) [application/octet-stream]

100%[======================================>] 12,342        50.18K/s             

19:49:29 (50.04 KB/s) - `cupswrappermfc210c_1.0.0-1_i386.deb' saved [12342/12342]

--19:49:29--  [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb)
           => `mfc210clpr-1.0.2-1.i386.deb'
Resolving solutions.brother.com... 64.212.100.124, 64.212.100.110
Connecting to solutions.brother.com|64.212.100.124|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 740,022 (723K) [application/octet-stream]

100%[======================================>] 740,022       79.85K/s    ETA 00:00

19:49:39 (78.78 KB/s) - `mfc210clpr-1.0.2-1.i386.deb' saved [740022/740022]

(Reading database ... 99719 files and directories currently installed.)
Preparing to replace mfc210clpr 1.0.2-1 (using .../mfc210clpr-1.0.2-1.i386.deb) ...
Unpacking replacement mfc210clpr ...
Setting up mfc210clpr (1.0.2-1) ...
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1.0' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so' to `/usr/lib/libbrcompij2.so.1.0.2': File exists

(Reading database ... 99719 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.0-1 (using .../cupswrappermfc210c_1.0.0-1_i386.deb) ...
/etc/init.d/cups:[COLOR="Red"] Permission denied.[/COLOR]
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
/etc/init.d/cups: [COLOR="Red"]Permission denied.[/COLOR]
lpadmin: [COLOR="Red"]Unable to copy PPD file![/COLOR]

sudo: /etc/init.d/cups: [COLOR="Red"]command not found[/COLOR]

(gnome-printer-view:25596): [COLOR="Red"]GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/COLOR]

---

### Post by lordrahvin on 2007-07-06
Anyone have any ideas for these?

When printing from the screen when you select your printer:  "Unable to look up host 'usb'.  Unknown host."

In PRINTERS beneath the checkmarks for Enabled, Accepting Jobs, and Shared:  "Not published.  See Server settings."

---

### Post by risico on 2007-07-06
Hello,

I used guitara's script to install the printer/fax/scanner drivers. Unfortunately it did not work automatically for me. But after I ran the script, I was able to add my Brother DCP-115C manually. Printing works fine now. I don't care much about the Fax driver, but the scanner still does not work. In Xsane I get the following error: 

[IMG]http://i15.tinypic.com/639tut5.png[/IMG]

It is in Dutch. Translated it says: Could not find the device brother2:bus1;dev1. Error during device communication.

I tried to add some lines, to some files to solve permission problems, but I did not succeed in solving it. Hope anyone can help me.

lsusb gives:
Bus 002 Device 003: ID 5986:0100  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04f9:018c Brother Industries, Ltd 
Bus 001 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 001 Device 001: ID 0000:0000  
scanimage -L gives:
device `brother2:bus2;dev1' is a Brother DCP-115C USB scanner
device `v4l:/dev/video0' is a Noname USB2.0 Camera virtual device
sudo scanimage -L gives:
device `brother2:bus2;dev1' is a Brother DCP-115C USB scanner
device `v4l:/dev/video0' is a Noname USB2.0 Camera virtual device 

thanks in advance

---

### Post by balloons on 2007-07-08
risico, does sudo xsane work?

---

### Post by balloons on 2007-07-08
> **lordrahvin said:**
> I'm having trouble getting the MFC-210c to work with Xubuntu 7.04 running GNOME.  
I have the same problem described by the above users.  Printer shows ready.  Printer shows as a print option.  Printer even "receives information" but nothing prints.  

It looks like there was an error in running the script.  I have no idea why.  The same error pops up even when I run "sudo dpkg -i --force-all cupswrappermfc210c_1.0.0-1_i386.deb".  It says there's a permission issue but I don't understand how there can be a permission issue if I'm running it under sudo.

The permissions for the directory show "root" and so I tried becoming root for a short time to see if that would help, using "sudo su" but I got the same results.  


I miss my printer.  *sniffle*

Here's a copy of the terminal session.  (I added color to show the areas that I thought might help identify the problem.)


root@lordrahvin-desktop:/home/lordrahvin# cd /home/lordrahvin/Desktop
root@lordrahvin-desktop:/home/lordrahvin/Desktop# sudo ./Feisty_Brother_MFC-210C_Installer.sh
init: illegal runlevel: (null)
Try `init --help' for more information.
root
Brother MFC-210C Printer Driver
mkdir: cannot create directory `/var/spool/lpd': File exists
mkdir: cannot create directory `/var/spool/lpd/MFC210C': File exists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
csh is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 45 not upgraded.
--19:49:29--  [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc210c_1.0.0-1_i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrappermfc210c_1.0.0-1_i386.deb)
           => `cupswrappermfc210c_1.0.0-1_i386.deb'
Resolving solutions.brother.com... 64.212.100.110, 64.212.100.124
Connecting to solutions.brother.com|64.212.100.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12,342 (12K) [application/octet-stream]

100%[======================================>] 12,342        50.18K/s             

19:49:29 (50.04 KB/s) - `cupswrappermfc210c_1.0.0-1_i386.deb' saved [12342/12342]

--19:49:29--  [http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb](http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc210clpr-1.0.2-1.i386.deb)
           => `mfc210clpr-1.0.2-1.i386.deb'
Resolving solutions.brother.com... 64.212.100.124, 64.212.100.110
Connecting to solutions.brother.com|64.212.100.124|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 740,022 (723K) [application/octet-stream]

100%[======================================>] 740,022       79.85K/s    ETA 00:00

19:49:39 (78.78 KB/s) - `mfc210clpr-1.0.2-1.i386.deb' saved [740022/740022]

(Reading database ... 99719 files and directories currently installed.)
Preparing to replace mfc210clpr 1.0.2-1 (using .../mfc210clpr-1.0.2-1.i386.deb) ...
Unpacking replacement mfc210clpr ...
Setting up mfc210clpr (1.0.2-1) ...
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1.0' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1' to `/usr/lib/libbrcompij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so' to `/usr/lib/libbrcompij2.so.1.0.2': File exists

(Reading database ... 99719 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.0-1 (using .../cupswrappermfc210c_1.0.0-1_i386.deb) ...
/etc/init.d/cups:[COLOR="Red"] Permission denied.[/COLOR]
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
/etc/init.d/cups: [COLOR="Red"]Permission denied.[/COLOR]
lpadmin: [COLOR="Red"]Unable to copy PPD file![/COLOR]

sudo: /etc/init.d/cups: [COLOR="Red"]command not found[/COLOR]

(gnome-printer-view:25596): [COLOR="Red"]GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/COLOR]

This looks like a xubuntu thing perhaps? Does /etc/init.d/cupsys exist? How about /etc/init.d/cups? Also, it shows 45 packages not upgraded - are you running a full install of fiesty - a confirmed good install? Can you upgrade all those packages? sudo apt-get dist-upgrade

---

### Post by risico on 2007-07-09
> **guitara said:**
> risico, does sudo xsane work?

Yes, xsane works. The program starts, but when I select the device, I get the error message from my previous entry in this topic.

---

### Post by balloons on 2007-07-09
> **risico said:**
> Yes, xsane works. The program starts, but when I select the device, I get the error message from my previous entry in this topic.


Ok, I meant does it work when run as root? IE, sudo xsane. Does it scan and not give the error then? If not, run sudo xsane from the terminal, and paste the output.

---

### Post by risico on 2007-07-10
> **guitara said:**
> Ok, I meant does it work when run as root? IE, sudo xsane. Does it scan and not give the error then? If not, run sudo xsane from the terminal, and paste the output.

I pasted sudo xsane in the terminal. Xsane and the scanning worked properly then. Only when I save an image, it has root rights and I can't open it normally. How can I solve this?

Thanks again

---

### Post by balloons on 2007-07-10
ok, i haven't added this to the script (yet), maybe in time for gusty. You'll need to run this command: ```
sudo sane-find-scanner
``` this will give you the values to put in /etc/udev/rules.d/45-libsane.rules So, ```
sudo gedit /etc/udev/rules.d/45-libsane.rules
``` Add the info you get from the first command to the bottom of the file IE for the 210c it's 04f9, and 0161. I've shown the example entries below ```
# Brother|MFC 115C SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="664", GROUP="scanner" # Brother|MFC 210C SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="664", GROUP="scanner" # Brother|MFC 215C SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0193", MODE="664", GROUP="scanner"
``` replace the vendor and product ids, if they are different for your brother printer. Make sure you are part of the scanner group ```
sudo usermod -a -G scanner yourusername
``` Restart your computer and run this ```
rm -rf ~/.sane
``` Now, xsane will work without running as root. Thanks for fixing the typos d351GuJu!

---

### Post by d351GuJu on 2007-07-13
It's not "sudo gedit /etc/udev/rules.d/45-libsane.rule"
It is "sudo gedit /etc/udev/rules.d/45-libsane.rules" ;)

BTW, once that's done, make sure you restart your computer otherwise it will NOT work, and once that is done you need to remove /home/[username]/.sane directory to reset configurations.

---

### Post by risico on 2007-07-14
> **guitara said:**
> ok, i haven't added this to the script (yet), maybe in time for gusty. You'll need to run this command: ```
sudo sane-find-scanner
``` this will give you the values to put in /etc/udev/rules.d/45-libsane.rules So, ```
sudo gedit /etc/udev/rules.d/45-libsane.rules
``` Add the info you get from the first command to the bottom of the file IE for the 210c it's 04f9, and 0161. I've shown the example entries below ```
# Brother|MFC 115C SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="664", GROUP="scanner" # Brother|MFC 210C SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0161", MODE="664", GROUP="scanner" # Brother|MFC 215C SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="0193", MODE="664", GROUP="scanner"
``` replace the vendor and product ids, if they are different for your brother printer. Make sure you are part of the scanner group ```
sudo usermod -G scanner yourusername
``` Restart your computer and run this ```
rm -rf ~/.sane
``` Now, xsane will work without running as root. Thanks for fixing the typos d351GuJu!


thanks this worked for me. I already figured out the "rules" typo.

---

### Post by crazyknight on 2007-07-22
Just got my 210C setup! Thanks for the help/script :)

---

### Post by Kynan on 2007-07-25
Thanks again guitara! Works perfectly.

---

### Post by mrwasabi on 2007-07-25
Worked like a charm gentlemen, I have the MFC420CN on my network with 2 xp pro boxes ( ugh), installed to Ubuntu 7.04. Thanks very much for providing this, it really helped me!

---

### Post by cblanquer on 2007-08-03
> **thedavis said:**
> I followed the HowTo for my DCP-115C and its working fine now :) hehehe Thanks :) But I have a question....for scaning?!! :S:S


Sorry if my english suX!!! I tried to write in my best way :D

Hola,

Suposo que ja en tens la solució. Amb Ubuntu 7.04, jo he seguit les instruccions i respecte al SCANNER no problem my friend, xuta perfectament.
La clau per mi va estar en que vaig seguir abans les instruccions :
[http://ubuntuforums.org/showthread.php?t=488016&highlight=DCP-115](http://ubuntuforums.org/showthread.php?t=488016&highlight=DCP-115)

Atenció al meu comentari a:
[http://ubuntuforums.org/showthread.php?p=3129314#poststop](http://ubuntuforums.org/showthread.php?p=3129314#poststop)

---

### Post by hanzj on 2007-08-05
BobSongs (OP),
I'm using Feisty Ubuntu 7.04 and printing and scanning works. Good stuff.
Are you planning on updating your post to Feisty? Perhaps the instructions are still the same, but viewers may get the impression that, because you only mention 6.04 and 6.10, your instructions are not going to work with Feisty.

---

### Post by balloons on 2007-08-06
Hanz - the instructions are different for Dapper vs Edgy. The instructions for Feisty remain unchanged from Edgy. So Edgy instructions work for Feisty too.

---

### Post by BobSongs on 2007-08-07
> **hanzj said:**
> BobSongs (OP),
I'm using Feisty Ubuntu 7.04 and printing and scanning works. Good stuff.
Are you planning on updating your post to Feisty? Perhaps the instructions are still the same, but viewers may get the impression that, because you only mention 6.04 and 6.10, your instructions are not going to work with Feisty.[FONT=Verdana]A good point, **hanz**. I will add **guitara's** note into the tutorial.

**guitara**: thanks for monitoring the thread!![/FONT]

---

### Post by bogr@ on 2007-08-20
Hi,
Still can't get my DCP-115C to print.  Have installed CUPS and it found the USB printer, using the MFC210C drivers as recommended at the Brother website.

Tried printing the test page from CUPS and printing my documents from various applications - they show up in the print spool and later in the completed jobs list, but nothing comes out of the printer...

This is the next-to-last thing to complete my conversion from windows, but it's driving me mad...  I'm sure there's a quick fix... Help:confused::confused::(

---

### Post by cblanquer on 2007-08-21
Have a look here, I had it working (scanner + printer) on a friends PC.
Linkk:[http://ubuntuforums.org/showthread.php?p=3129364#poststop](http://ubuntuforums.org/showthread.php?p=3129364#poststop)

Good luck.I was about to give up, then Igot the solution.

---

### Post by bogr@ on 2007-08-21
OK, thanks - scanner now working, but still no printer...
Still trying, but I'm a least a step further:)

Edit: Could the problem be that I'm running 64bit???

---

### Post by cblanquer on 2007-08-22
I could not have the printer work at the first time, so I uninstalled what I did before (forllowing the instrucitons in the reverse way) and that worked for those instructions the second time.
I do not have access to that computer anymore so I can provide little added help.

Regarding 64 bits systems, my children PC is a 64b and I had sometimes trouble to install things, it could be a reason but I woud rather advice to try again carefully after undoing.

---

### Post by bogr@ on 2007-08-22
Thanks for your help - I'll keep trying

---

### Post by Col-1023 on 2007-08-23
This thread and tutorial have been a real help, however I still can't use xsane without sudo.

I'm using Ubuntu 7.04

After following the tutorial, I restarted my pc and entered,

rm -rf ~/.sane

Terminal replied with,

rm: cannot chdir from `/home/grumpy/.sane/xsane' to `batch-lists': Permission denied

when I entered the command,

 sudo rm -rf ~/.sane

It seemed to work, however I still can't use the scanner without being root.

Any help appreciated.

---

### Post by tanapon on 2007-08-23
Dear BobSong,

I am using MFC-4800 with Feisty on both my notebook and desktop. Firstly, I followed your steps to install printer on my notebook successfully.

Then I installed the printer again on my desktop but it returned some error about brmfc4800lpr after;
>sudo dpkg -i ~/Desktop/mfc4800/mfc4800lpr-1.1.2-1.i386.deb

Sorry, I can't remember error message exactly. It also caused Synaptic to shutdown itself at startup. I thought I could have done your step wrong so I installed Feisty again and again.

*After reinstalling Fesity 4-5 times I realized that I used to do these steps on my notebook before;
- installed package called "lpr" and it asked to remove "cupsys-bsd" and "ubuntu-desktop"
- installed only cupswrapperMFC4800-1.0.2-1.i386.deb and removed it
- installed cupsys-bsd, ubuntu-desktop back again so lpr was removed

Then I repeat these steps on my desktop so this time no more error message again. I am not sure if these steps leave any traces in the system so it corrected my errors. 

Now I happily use my MFC-4800 on my two Feisty boxes. Sorry I haven' t tried fax or scanner yet.

Regards,
Tony

Note : In Dapper, I only had to install package "lpr" then "cupswrapperMFC4800-1.0.2-1.i386.deb" and the printer worked fine.

---

### Post by BobSongs on 2007-08-24
> **tanapon said:**
> Dear BobSong,

I am using MFC-4800 with Feisty on both my notebook and desktop. Firstly, I followed your steps to install printer on my notebook successfully.

Then I installed the printer again on my desktop but it returned some error about brmfc4800lpr after;
>sudo dpkg -i ~/Desktop/mfc4800/mfc4800lpr-1.1.2-1.i386.deb

Sorry, I can't remember error message exactly. It also caused Synaptic to shutdown itself at startup. I thought I could have done your step wrong so I installed Feisty again and again.

*After reinstalling Fesity 4-5 times I realized that I used to do these steps on my notebook before;
- installed package called "lpr" and it asked to remove "cupsys-bsd" and "ubuntu-desktop"
- installed only cupswrapperMFC4800-1.0.2-1.i386.deb and removed it
- installed cupsys-bsd, ubuntu-desktop back again so lpr was removed

Then I repeat these steps on my desktop so this time no more error message again. I am not sure if these steps leave any traces in the system so it corrected my errors. 

Now I happily use my MFC-4800 on my two Feisty boxes. Sorry I haven' t tried fax or scanner yet.

Regards,
Tony

Note : In Dapper, I only had to install package "lpr" then "cupswrapperMFC4800-1.0.2-1.i386.deb" and the printer worked fine.
[FONT=Verdana]Ah yes. I've even moved on from Dapper to Feisty. However, my MFC-210C resides squarely besides my Mac. So I still haven't tried setting up a printer on Feisty.

Still: glad to hear you had success. And very little of it is to my credit, really. The credit belongs to the Ubuntu Forums teamwork that makes using Ubuntu enjoyable.

Thanks to all who make this thread useful and successful.
[/FONT]

---

### Post by Lary Grant on 2007-08-30
Is there any way to get the "Scan" button on the scanner to work?  Currently, the only way I can scan is to open the scanning program manually and click "Scan" from there.  If I just push the "Scan" button on the machine, nothing happens.

---

### Post by Col-1023 on 2007-08-31
I still have to be root to start Xsane.

Should I just log in as root and change certain file, such as the xsane executable and the like so that they will start without being root.

I change the xsane bin permissions but this had no effect, so should I change other files permissions, or leave them alone.

Does it really if I'm using xsane as root, is the risk that great, or have the xsane writers been a bit paranoid?

Any help appreciated.

---

### Post by Colbrac on 2007-09-03
As mentioned in some other thread or page I can't remember right now, you can scan as a user by doing the following:

open the file /etc/udev/rules.d/45-libsane.rules with your fav. editor, eg:
```
sudo nano /etc/udev/rules.d/45-libsane.rules
```

add 2 lines like this:

Before:
```
# Dell 1600n
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5250", MODE="664", GROUP="scanner"

LABEL="libsane_rules_end"
```
After:
```
# Dell 1600n
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="5250", MODE="664", GROUP="scanner"

# Brother DCP-115C (custom rule)
SYSFS{idVendor}=="04f9", SYSFS{idProduct}=="018c", MODE="666" GROUP="scanner"

LABEL="libsane_rules_end"
```

And reboot your system for this rulechange to take effect.
Note: This is for the DCP-115C. If you have a different printer, find your idProduct (idVendor should be the same) by running:
```
lsusb
```

output:
```
Bus 003 Device 006: ID 04f9:018c Brother Industries, Ltd 
Bus 003 Device 003: ID 046d:08b4 Logitech, Inc. QuickCam Zoom
Bus 003 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
```

so the 04f9:018c is the idVendor:idProduct codes.

Good luck!

---

### Post by Col-1023 on 2007-09-04
Thanks for your reply.

I've followed the guides, including modifying the file and I still can't use xsane accept if I am root (sudo).

I put lsusb in a terminal and got the following,

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 04f9:0161 Brother Industries, Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

This is for my Brother MFC210C, so ubuntu knows it's there, but for some reason xsane wants to be run as root.

Is this still a problem in Gutsy?

---

### Post by d351GuJu on 2007-09-04
Scanning in Gutsy works using included guidelines as well as setting permissions to start xsane using normal user; however, I am still having problems printing, going to work on it later.

d351GuJu

---

### Post by BobSongs on 2007-10-09
Imagine appealing to my own tutorial for assistance.

My black will not print. Our summer was warm and the printer did not see much use. The black was showing signs of drying and multiple cleanings worked. However it has now ceased completely.

I've run the clean process a good... 15 times now without success. If anyone knows how to get a color working again  by some other means, please tell me. Otherwise I buy a different printer and someone else will have to take up the torch. 

Any suggestions?

---

### Post by FlyingIsFun1217 on 2007-10-13
BobSongs: Do you dual boot with another OS? Try and make sure that it's actually Ubuntu's fault. If it is... Hmm. If you still get the same issue, just try some new cartridges.

Does anybody know whether or not the MFC-210C is correctly installed automatically in Gutsy?

FlyingIsFun1217

---

### Post by jubilee0824 on 2007-10-18
Has anyone succeed using MFC-210c on Gutsy (7.10)?

I could use both printer and scanner functions on 7.06, but not anymore since updating to 7.10. And, the new automatic printer setting does not work....

---

### Post by tdiguy on 2007-10-18
This tutorial is absolutly great. I have finally been able to install my brother print driver. I also am running kubuntu now and i really love the gui on this version other.

My problem is unrelated to the tutorial. I am using a hawking technology hps12u print server its a really basic print server so i can connect both my printers to the network and print to either one i cant use any of the multifunction things on the brother which has allways bothered me a little but it still faxes so its very usefull to me anyway. 

I just cant quite figure out how to get this working like i said i finally have the print driver on the computer i just cant figure out how to use the print server. It has the following for print technologies supported LPR  IPP NETWARE APPLETALK NETBUI and SMB. I just cant seem to get any of these to work and i cant get the software for the print server to work it comes up with a error saying i dont have tcp ip installed.

---

### Post by Samhain13 on 2007-10-20
Hello, I just used the install script mentioned a couple of pages back and I'd like to confirm that the** "Install Scanner"** part works in **Gutsy Gibbon**. I still have not tried installing the printer-- no ink for testing. :)

---

### Post by Col-1023 on 2007-10-20
Hi Bobsongs,

I hadn't used mhy brother for a while, and when I tried printing found that the cartridges showed as empty even though before they were quite full, the printer wouldn't recognise them as still having ink so I replaced them.

The generics I had installed fine, but nothing printed, then I realised that I hadn't removed the air-cap from the cart.

Once the caps were removed and after some cleaning, the printer worked fine.

The instructions for my carts referred to paper tape, which wasn't there, instead I had to remove a hard plastic cap to get things workihttp://ubuntuforums.org/showthread.php?t=579746&highlight=unichrome+pro&page=13ng.

Hope this helps.

PS, - does SANE still need root access in gutsy, since I always get nervous using sane with root in fiesty?

---

### Post by Jose Catre-Vandis on 2007-10-20
Brother DCP-540CN howto (see first page) updated and tested and working on clean install of GUTSY 7.10

[http://ubuntuforums.org/showpost.php?p=2275292&postcount=31](http://ubuntuforums.org/showpost.php?p=2275292&postcount=31)

---

### Post by tdiguy on 2007-10-22
I finally discovered sucsess with my hawkings hps12u print server. After i finally got the brother print driver in kubuntu. I used tcp printing with the interactive wizard in kubuntu. went to the IP of the print server and reserved that address on my router also (odviously so it wont bounce around on me and play hide and seek) then scanned the port this is where its a bit hit or miss it seems that there are multiple port numbers that can be had this is a hit or miss thing because the print server has 3 ports so running test prints will need to be done untill you find the right one. I wish i could be more specific on this but using the TCP option is what worked for me the rest was hit or miss untill i hit the right port number.

---

### Post by altonbr on 2007-10-23
So I've had nothing but troubles with the MFC-8440 (for scanning and faxing) but this project looks promising: [http://brother-mfc.sourceforge.net/](http://brother-mfc.sourceforge.net/). Anyone seen it yet?

---

### Post by penciledin on 2007-10-24
Had a great experience with my MFC-210C on 7.04, but ever since I upgraded to Gutsy, I have two problems:

1) In XSane, I get this error: 
```
Failed to open device 'brother2:bus3;dev1':
Error during device I/O.
```

2) My printer gets no error, and it says it's printing, but reality doesn't agree.

Any help would be majorly appreciated.

---

### Post by altonbr on 2007-10-24
> **penciledin said:**
> Had a great experience with my MFC-210C on 7.04, but ever since I upgraded to Gutsy, I have two problems:

1) In XSane, I get this error: 
```
Failed to open device 'brother2:bus3;dev1':
Error during device I/O.
```

2) My printer gets no error, and it says it's printing, but reality doesn't agree.

Any help would be majorly appreciated.

I've had this exact problem and it turns out that you have to run XSANE or flegita as root.

Give it a try at least.

```
$ sudo flegita
```
```
$ sudo xsane
```

---

### Post by penciledin on 2007-10-24
> **altonbr said:**
> I've had this exact problem and it turns out that you have to run XSANE or flegita as root.

Give it a try at least.

```
$ sudo flegita
```
```
$ sudo xsane
```

Oh, my heavens. It works! Now, I guess I'll just create a new launcher for it...

Thanks!

---

### Post by drejom on 2007-10-28
dont need to run as root, try this thread
[http://ubuntuforums.org/showthread.php?p=3626510#post3626510]("http://ubuntuforums.org/showthread.php?p=3626510#post3626510")

---

### Post by limplenny on 2007-10-29
hi all, im on gutsy (kubuntu) and ran into a little bit of difficulty.

when i tried to install the .deb packages i got the error:
can't find file/folder /etc/init.d/lpd

solved it by linking cupsys to lpd and lprng:
```
ln -s /etc/init.d/cupsys /etc/init.d/lpd
ln -s /etc/init.d/cupsys /etc/init.d/lprng

```
and after the deb packages were installed:
rm /etc/init.d/lpd

thought it might help someone :)
lennard

---

### Post by Mujaheiden on 2007-10-31
The scanner + printer also works with the mfc-7820n network printer/scanner in gutsy gibbon.
The printer is automatically found by the Ubuntu printer configuation, and for the scanner, 
follow instrucitons here:[http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/sane_drivers.html")

---

### Post by supportbroker on 2007-10-31
I am a newbie! 

I cannot get my printer to print
W
 I installed /home/bryan/Desktop/cupswrappermfc210c_1.0.0-1_i386.deb
and 
/home/bryan/Desktop/mfc210clpr-1.0.2-1.i386.deb

and everything installed. In system-administrator-printing mfc210c shows as the default printer

in the printer properties in the general tab
name: mfc210c
description: mfc210c
location: blank
resolution:blank
status: ready: unable to lookup host 'usb' - Unknown host

Under the Connections Tab it seems to default to a network printer

When I first click on detected printer nothing is shown later the brother MFC210C shows up

When I try to print an Office Document-Brother shows in the display screen as Receiving Data.

Can someone help me.

I

---

### Post by geegee on 2007-11-03
i use gutsy gibbon with my mfc240c

---

### Post by Mujaheiden on 2007-11-27
Anyone knows how to make the scanner not to save files as "brscan.R31684" but as brscan.R31684.PPM ?

I linked the brscan folder to a samba resource, and want my colleagues to get their scans tehmselves, without me needing to rename the files all the time. Even better would be to get the files to be saved as TIF, I think.

---

### Post by rkdss on 2007-12-20
Hi! I'm trying to configure a Brother MFC620CN trought a network setup, Feisty Fawn on an AMD64. 

Following the different messages of this thread, and appling the right drivers, now I can use the scanner function of my device (nice!), but still no luck with the printer. CUPS can find it (and I tried to setup manually also) but printing always give the same strange result: no error is reported, the printer stays quiet (and the job apparently gets done). The only error I've found appearing, is this strange message in the syslog...

Dec 20 14:44:10 [host] cups-check-pam-auth: PAM option: nullok invalid

...repeated again and again. I've searched but no pages found on that topic... Anybody please can help?

Thank you very much

---

### Post by BobSongs on 2007-12-20
Bump.

Anyone?

---

### Post by rkdss on 2007-12-21
OMG! finally! I've got it! This thing almost drove me nuts! :-G
Suspecting from the 32bits - 64bits issue I've tested all programs used by the driver in /usr/local/Brother/  looking for missed libs
The problem was in one of them, exactly:

/usr/local/Brother/lpd/rastertobrij2

This app was missing this lib: libbrcompij2.so.1.0.2

So I copied it from /usr/lib to /usr/lib32:

$ sudo cp /usr/lib/libbrcompij2.so* /usr/lib32/

Now it works like a charm... yihaa!!

---

### Post by colossus73 on 2007-12-22
Hi,

I have a DCP-115C printer. After a while I accessed the sd card with any program the processes freeze:

gt[~]$ ps ax | grep D
PID TTY STAT TIME COMMAND
2547 ? D< 0:00 [scsi_eh_7]
2548 ? D< 0:00 [usb-storage]
5346 ? D 0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)

and I can't kill them anymore even with sudo. I'm forced to reboot the PC. I have this in the logs:

```

[   41.851676] scsi 7:0:0:0: Direct-Access     Brother  DCP-115C         1.00 PQ: 0 ANSI: 2
[   41.871636] sd 7:0:0:0: [sdc] 999936 512-byte hardware sectors (512 MB)
[   41.887622] sd 7:0:0:0: [sdc] Write Protect is off
[   41.887625] sd 7:0:0:0: [sdc] Mode Sense: 1e 00 00 08
[   41.887628] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   41.932578] sd 7:0:0:0: [sdc] 999936 512-byte hardware sectors (512 MB)
[   41.948562] sd 7:0:0:0: [sdc] Write Protect is off
[   41.948565] sd 7:0:0:0: [sdc] Mode Sense: 1e 00 00 08
[   41.948567] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   41.948571]  sdc: sdc1
[   41.982540]  sdc: p1 exceeds device capacity
[   41.989566] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[   41.989622] sd 7:0:0:0: Attached scsi generic sg2 type 0
[   42.545440] attempt to access beyond end of device
[   42.545446] sdc: rw=0, want=1000298, limit=999936
[   42.545449] Buffer I/O error on device sdc1, logical block 1000064
[   42.545453] attempt to access beyond end of device

```

This line looks suspicious to me: [ 41.982540] sdc: p1 exceeds device capacity.
The kernel is: Linux gt-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux. On windoz the card works like a charm so it's not a problem of filesystem.

Please help!

---

### Post by niceguy123 on 2008-01-02
> Note: This tutorial assumes:

    * Device: Brother MFC210C
    * Connection: USB direct from PC to Printer
    * System: 32-bit Intel/AMD
    * Operating System: GNU/Linux Ubuntu (Dapper Drake/Edgy Eft/Feisty Fawn)


I'm trying to add a brother dcp115c that is hooked upto a winxp machine on a network. 

I have Feisty Fawn on this machine and do not see brother dcp115c on the list of printers in the setup . I saw on on of the threads on this forum someone who says: > you should use the MFC-210C driver for your DCP-115C,

But I couldn't find MFC-210C on the list ether.

How can I run the printer?

(next question: Can I run the scanner over the network?)

Thanks

---

### Post by parian on 2008-01-26
I'm running Gutsy Gibbon and trying to print to a networked printer installed on a WinXP machine. I am 'connected' to the printer in localhost:631 but nothing is actually getting printed. :confused:

---

### Post by altonbr on 2008-03-11
New drivers are in the works for Brother printers in Gutsy and Hardy. Please see the thread here: [https://bugs.launchpad.net/ubuntu/+bug/25966](https://bugs.launchpad.net/ubuntu/+bug/25966).

For Hardy: [http://upload.leservicetechnique.com/brother](http://upload.leservicetechnique.com/brother)
For Gutsy: [http://upload.leservicetechnique.com/brother/gutsy](http://upload.leservicetechnique.com/brother/gutsy)
For knowing what packages to install: [https://wiki.ubuntu.com/BrotherDriverPackaging](https://wiki.ubuntu.com/BrotherDriverPackaging)

Please test these drivers and report back to Saïvann Carignan via the Launchpad thread.

Good luck!

---

### Post by dankan79 on 2008-03-12
rkdss you are a genius!!!!
after spending many hours trying to make my MFC620CN to print (scan was working fine) I always ending up with a quiet printer and no errors what so ever.

Your solution in #407 did the trick!!!! Copying the library:
$ sudo cp /usr/lib/libbrcompij2.so* /usr/lib32/

and the printer is working excellent!!!! Many thanks, GREAT WORK! :guitar:

---

### Post by kalesh7 on 2008-03-23
All I can say is wow excellent and clear instructions. 
Got my dcp130c printer/scanner working in one try.:guitar:

---

### Post by FlyingIsFun1217 on 2008-03-25
Hardy has now made the process extremely simple.

(1) Open up Synaptic
(2) Click Search
(3) Type in your printer model (in this case, 'MFC-210C')
(3) Choose both the cups wrapper and the lpr drivers
(4) Apply and plug in your printer

This should give you everything you need to install the printer just by plugging it in.

Be warned: The print quality is still a very bad second to that of Windows printing. But at least it works.

FlyingIsFun1217

---

### Post by Enigmacat on 2008-03-26
> **bigken said:**
> Hi all I just istalled my mfc3820cn on edgy and it did not work either 
this how I got it to work make the folders 

sudo mkdir /var/spool/lpd

sudo mkdir /var/spool/lpd/MFC3820CN

download the drivers from brother 

double click on them to install 

then I went to system/administration/printers 

double click new printer 

select local printer then next 

now select brother then click on install driver 

then navigate to file system/usr/share/cups/model

then just double click brmfc3820cn_cups.ppd (in my case)

then select it from the brother menu 

if you are on a network its the same just select it as a unix (lpd)
and give it a ip address 

hope this helps ;)


oops forgot to mention install csh (sudo aptitude install csh)

Ok, I am new to Ubuntu as well as Linux OS, further I am not yet a programmer. I am just an ordinary Joe who is fed up with being force fed Windows and thought there has to be a better way. Much like the guy in the Wendy's commercial. Anyway, I hate to be such a noob :oops: , but could you dumb that down a bit. I've got the first part done (sudo mkdir /var/spool/lpd/MFC3820CN), now how do I go about the other half. :-k Thnks

---

### Post by altonbr on 2008-03-27
@Enigmacat

Wait for Ubuntu Hardy 8.04, coming out in April, 2008 (if it's a possibility). The Brother drivers will be included by default and should be automatically installed upon installation of Ubuntu.

---

### Post by dislocated on 2008-04-26
> **FlyingIsFun1217 said:**
> Hardy has now made the process extremely simple.

(1) Open up Synaptic
(2) Click Search
(3) Type in your printer model (in this case, 'MFC-210C')
(3) Choose both the cups wrapper and the lpr drivers
(4) Apply and plug in your printer

This should give you everything you need to install the printer just by plugging it in.

Be warned: The print quality is still a very bad second to that of Windows printing. But at least it works.

FlyingIsFun1217
Was mucking about with the old method for Gutsy trying to get my MFC-420CN working with no luck. Then I finally scrolled to the end of this thread to find your Hardy advice, and I was up and running in no time... Thank-you!

---

### Post by Mainiak Blaniak on 2008-04-27
First of all, a big Thank You to all who contributed to this thread.  After a mild struggle and a little searching, I was able to get my MFC-685CW to print and scan with Gutsy.  Very little modification was required to the instructions presented above. 

A couple of minor items still nag at me though, and I was wondering if anyone has sorted them out (couldn't find them searching this forum or google, and I don't have the time to read 42 pages of posts right now...)  The printer is stand-alone on the wireless network (no cable connection to any pc).

Nagging item #1) With the windoze drivers for this printer (I also have it set up on this box with XP dual boot and a Vista laptop) there is an option to configure the printer so that when scanning, the printer offers options of networked PC's to send the scan to (this is presented on the LCD of the scanner itself).  Has anyone found a way to 'tell' the scanner that there is an Ubuntu box out there that can be scanned to?

Nagging item #2) It was my, perhaps mistaken, impression that the SD card reader on this printer could be used as a network drive, as well as printing from camera SD cards.  Is this actually the case?  If so, how is it done.  Neither my Ubuntu machine or the windoze machines see a network drive when cards are installed in the printer.

Thanks in advance for any help available...

MB

---

### Post by lizhao on 2008-05-02
So far, so luck to print to brother 115c on hardy 8.04
Anybody success?
appreciate to share experience.

---

### Post by Grosser on 2008-05-03
Hello lizhao,

it´s the same of post #416.
Take the MFC-210C Driver for your DCP-115C and it works very fine.
On my PC it goes with Hardy 64-bit i have test it on Hardy 32-bit.

Greets

---

### Post by lizhao on 2008-05-04
> **Grosser said:**
> Hello lizhao,

it´s the same of post #416.
Take the MFC-210C Driver for your DCP-115C and it works very fine.
On my PC it goes with Hardy 64-bit i have test it on Hardy 32-bit.

Greets
Hi, Grosser
Thanks
I tried it, and use MFC-210C driver following instruction.
Tried to print test page, nothing happened.

No clue to solve it. 

Also tried driver for 110c, failed too.
PS: the scanner is OK

---

### Post by altonbr on 2008-05-05
> **lizhao said:**
> Hi, Grosser
Thanks
I tried it, and use MFC-210C driver following instruction.
Tried to print test page, nothing happened.

No clue to solve it. 

Also tried driver for 110c, failed too.
PS: the scanner is OK

Maybe post a bug or ask a question at [http://launchpad.net/ubuntu?](http://launchpad.net/ubuntu?) The developers may be able to help you there.

---

### Post by Snel on 2008-06-18
Hi Guys i`m running ubuntu 8.04

I had the same problem when i tried my dcp-115c but i finally got it to print a test page.

All the steps worked up to this one. [ sudo dpkg -i ~/Desktop/mfc210c//cupswrapperMFC210C-1.0.2-3.i386.deb ] with error message [touch: can`t access `/usr/share/cups/model/brmfc210c_cups.ppd' : No such file or directory
/usr/share/cups/model/brmfc210c_cups.ppd: No such file or directory.]

I found the directory missing and created it myself [ sudo mkdir /usr/share/cups/model ] after that i ran that first command again and finaly the mfc210c driver showed !

I`m new to this but it worked on mine hopefully it will be of some help to you.

Cheers

---

### Post by Ozdemon on 2008-07-09
See my other post at 
[http://ubuntuforums.org/showthread.php?t=848075](http://ubuntuforums.org/showthread.php?t=848075)

Brother tech support confirmed today that the drivers on the Brother site are not meant to be used for 8.04 because of non-standard changes in the file structure.

Remove all Brother software and use Synaptic.

---

### Post by slacksonof on 2008-07-16
I used sudo apt-get install brother-cups-wrapper-extra
then in synaptic ticked Brother boxes.
Then in printer chose brother dcp-110c cups v 1.1
And it works and not much slower than xp.
I would like to thank everyone for their posts,to many to do personaly
and i cannot remember them all,seen that many today.
been using Linux/Ubuntu 30hours and well impressed.

---

### Post by Proodigy on 2008-07-16
thx for this info!:guitar:

---

### Post by wilcan34 on 2008-09-22
Thanks for the How To.
Every time i upgrade it allways knocks out the printer and I end up back here to reinstall.
Upgraded to the latest,8.10 and sure enough out went the printer.
Just coppied the 7.10 release sudo"s
Much appreciated,
G

---

### Post by laviandra on 2008-12-21
Hi. I am having problems installing my printer (dcp-115c).
I tried installing csh and tcsh using the terminal and the Synaptic Package Manager but both end up failing. 

The error in Synaptic package manager:
W: Failed to fetch [http://ro.archive.ubuntu.com/ubuntu/pool/universe/c/csh/csh_20070713-1_i386.deb](http://ro.archive.ubuntu.com/ubuntu/pool/universe/c/csh/csh_20070713-1_i386.deb)
  Could not connect to ro.archive.ubuntu.com:80 (192.129.4.120), connection timed out

In terminal:
lavi@lavi-desktop:~$ sudo apt-get install tcsh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  tcsh
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 350kB of archives.
After this operation, 733kB of additional disk space will be used.
Err [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) intrepid/universe tcsh 6.14.00-7ubuntu1
  Connection failed
Failed to fetch [http://ro.archive.ubuntu.com/ubuntu/pool/universe/t/tcsh/tcsh_6.14.00-7ubuntu1_i386.deb](http://ro.archive.ubuntu.com/ubuntu/pool/universe/t/tcsh/tcsh_6.14.00-7ubuntu1_i386.deb)  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

What do I do now?

---

### Post by altonbr on 2008-12-22
> **laviandra said:**
> Hi. I am having problems installing my printer (dcp-115c).
I tried installing csh and tcsh using the terminal and the Synaptic Package Manager but both end up failing. 

The error in Synaptic package manager:
W: Failed to fetch [http://ro.archive.ubuntu.com/ubuntu/pool/universe/c/csh/csh_20070713-1_i386.deb](http://ro.archive.ubuntu.com/ubuntu/pool/universe/c/csh/csh_20070713-1_i386.deb)
  Could not connect to ro.archive.ubuntu.com:80 (192.129.4.120), connection timed out

In terminal:
lavi@lavi-desktop:~$ sudo apt-get install tcsh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  tcsh
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 350kB of archives.
After this operation, 733kB of additional disk space will be used.
Err [http://ro.archive.ubuntu.com](http://ro.archive.ubuntu.com) intrepid/universe tcsh 6.14.00-7ubuntu1
  Connection failed
Failed to fetch [http://ro.archive.ubuntu.com/ubuntu/pool/universe/t/tcsh/tcsh_6.14.00-7ubuntu1_i386.deb](http://ro.archive.ubuntu.com/ubuntu/pool/universe/t/tcsh/tcsh_6.14.00-7ubuntu1_i386.deb)  Connection failed
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

What do I do now?

If you're in Intrepid, try installing the new brother packages that have been developed...

```
sudo aptitude install brother-lpr-drivers-extra brother-cups-wrapper-extra
```

---

### Post by corigo on 2009-02-23
What happens if you DON'T turn off the printer? I went through this entire process and my printer seems to be correctly installed and identified by the system, but the printer doesn't respond to print jobs sent. And XSane sees the machine at startup, but not after launch.

---

### Post by tamirtoad on 2009-03-21
thanks so much for the automated install script. it worked perfectly on feisty.

---

### Post by BobSongs on 2009-04-08
> **corigo said:**
> What happens if you DON'T turn off the printer? I went through this entire process and my printer seems to be correctly installed and identified by the system, but the printer doesn't respond to print jobs sent. And XSane sees the machine at startup, but not after launch.
[COLOR=Red]Please note:[/COLOR]

This thread is abandoned. The instructions clearly say so.

At the time this thread was created, I was using Ubuntu GNU/Linux 5.10. It was updated and enhanced with the help of many thoughtful users. However, many of the warnings originally put in the tutorial may now be pointless. The problem is: I cannot verify the procedure any more.

However, my MFC210c died a horrible death. Since then I've used an MFC240c on my MacBook Pro. My PC currently uses Ubuntu 8.10 - without a printer.

---

### Post by bilsta1000 on 2009-08-09
I'm sorry but this is one of the reasons i'm not an avid Linux user. i thought id experiment with it and see if i could use it for a simple task - to run a usb printer for use on a network. even that it can't do with a stupid amount of messing about.

I followed this tutorial EXACTLY even copying and pasting the codes.
right now i cant install the printer because it cant find the driver.

any help. before i give in?

thankyou
Billy

---

### Post by joeoshawa on 2010-05-26
I have a brother mfc 4420c that was given to me free as it does not do pictures very well. I know brother has not made a driver for it as of yet but i was wondering if someone has tried the other brother Linux drivers. I would really like to get this printer working as it is the only printer i have atm and i cannot afford another. (Yes even a cheap one don't ask)

---

### Post by BobSongs on 2010-08-14
[SIZE=3][COLOR=#777777]**AGAIN: This thread was created when I started with Ubunut in 2005. Since starting it my printer is now dead no longer used, so I can't keep up with what it needs.**[/COLOR][/SIZE]

Please note:

I've installed Ubuntu Linux Karmic Koala on someone's PC and found that the repositories had a much better set up with Brother Printers.

I believe many of the Bother Printer problems are resolved now.

If you encounter an issue, post it here so that others might know what you've encountered.

---

