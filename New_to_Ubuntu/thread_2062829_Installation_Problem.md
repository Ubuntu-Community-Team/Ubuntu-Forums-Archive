---
title: "Installation Problem"
date: 2012-09-25
forum: New to Ubuntu
---

### Post by Janade on 2012-09-25
Please Help Me!! I am no computer geek, but have been enjoying the use of Ubuntu for a while. I some how pressed the upgrade button this morning to install 12.04 ( I figure). I now end up with a list of processing commands which the last line reads 
init:Failed to create pty -disabling logging for job
I have tried a number of suggestions online for similar problems but nothing seem to be working. Thank you in advance for the needed help!!!

---

### Post by Bashing-om on 2012-09-25
Janade; Hi ! Welcome to the forum.

Firstly, let's see what we are working with.
Please post the output of terminal commands:
```
cat /etc/lsb-release && uname -r 

```Pending this info, we will update/upgrade as called for resolution.
[INDENT]regards <==BDQ
[/INDENT]

---

### Post by Janade on 2012-09-25
Okay. Please tell me exactly what info are you asking for?

---

### Post by newb85 on 2012-09-25
What Bashing-om put in the Code box is a terminal command.  Open a terminal using Ctrl+Alt+T.  Copy the command from Bashing-om's post and paste it at the prompt (after the $) in the terminal.  (The paste keyboard shortcut in the terminal is Ctrl+Shift+V, not just Ctrl+V.)  Hit enter to execute the command.  It will return the results in the terminal.  Copy them into a new post.  (Again, the copy keyboard shortcut in the terminal is Ctrl+Shift+C.)

Oh, and put the output in quote tags like this:

> [noparse][QUOTE]Output
goes
here.[/noparse][/quote]

---

### Post by Janade on 2012-09-25
Since the script you are attempting to invoke has been converted to an upstart job, you may also use the start(8) utility , eg. start S25bluetooth
*PulseAudio configured for per-user sessions
Rather than invoking init scripts through /etc/init.d, use the service (8) utility, e.g. service S90binfmt- support start
initctl: unknown job: S90binfmt- support

Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the start (8) utility, e.g. start S90binfmt - support
*Checking battery state...     [OK]
{14.949348]  init: Failed to create pty -disabling logging for job

---

### Post by Bashing-om on 2012-09-25
sure... 
ctl+alt+t ->opens a terminal:
in this terminal copy/past from this post the commands, pasting back to this post the output between code tags ('#").  Simple process and you will get the hang of it quickly!

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by Bashing-om on 2012-09-25
Janade; 
irt your post #5, Do not know where that could have come from. Into an active terminal copy/paste the first requested commands only that one line "cat ...........-r"

hth <==BDQ

---

### Post by Janade on 2012-09-25
Oh Thank you much Newb85. I did that just now. the result is as follows:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
3.2.0-31-generic

---

### Post by Janade on 2012-09-25
Bashing-om did as you stated!

---

### Post by Bashing-om on 2012-09-25
looking good..... you are upgraded to the latest version... all we have to do now is update this installation.
into the terminal input the following two commands... one command at a time ... awaiting and noting any errors at each input.
```
sudo apt-get update
sudo apt-get upgrade
 
```be advise the use of "sudo" is administrative authority, requiring the use of your password. There will be no echo to the screen (security reasons).[INDENT]BDQ
[/INDENT]

---

### Post by Janade on 2012-09-25
I did the first command (sudo apt-get update). The following are the last two responses:

W: Some index files failed to download . They have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

Typed in the command therefore: sudo dpkg --configure -a
And it is processing for the past five minutes. End up with:

xapian. DatabaseError: Error writing block: No space left on device

---

### Post by Bashing-om on 2012-09-25
We are cooking with Crisco now! ...Do as dpkg advises.
from terminal input:
```
sudo dpkg --configure -a

```
then do the second command ...when all is kosher, we will do some clean up. post back with details.

[INDENT]bdq
[/INDENT]

---

### Post by Janade on 2012-09-26
.GRcorrect {	POSITION: relative; PADDING-BOTTOM: 0px !important; BACKGROUND: url(correction.gif) repeat-x left bottom; TEXT-DECORATION: none !important}.GRSpellingCorrect {	POSITION: relative; PADDING-BOTTOM: 0px !important; BACKGROUND: url(correction.gif) repeat-x left bottom; TEXT-DECORATION: none !important}.GRspelling {	POSITION: relative; PADDING-BOTTOM: 0px !important; BACKGROUND: url(correction.gif) repeat-x left bottom; TEXT-DECORATION: none !important}.GRline {	POSITION: absolute; BOTTOM: 0px; BACKGROUND: url(correction.gif) repeat-x left bottom; HEIGHT: 3px; RIGHT: 0px; LEFT: 0px}.GRnoMark {	BACKGROUND: none transparent scroll repeat 0% 0%}.GRwrapper {	BORDER-BOTTOM: transparent 0px solid; POSITION: absolute; BORDER-LEFT: transparent 0px solid; PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; OVERFLOW: hidden; BORDER-TOP: transparent 0px solid; BORDER-RIGHT: transparent 0px solid; PADDING-TOP: 0px}.GRcontour {	POSITION: absolute; MARGIN: 0px}.GRrichText {	BORDER-BOTTOM-COLOR: transparent; PADDING-BOTTOM: 3px; BORDER-RIGHT-WIDTH: 0px; BORDER-TOP-COLOR: transparent; MARGIN: 0px; DISPLAY: block; WHITE-SPACE: pre-wrap; BORDER-TOP-WIDTH: 0px; BORDER-BOTTOM-WIDTH: 0px; COLOR: transparent; BORDER-RIGHT-COLOR: transparent; OVERFLOW: hidden; BORDER-LEFT-COLOR: transparent; BORDER-LEFT-WIDTH: 0px; -webkit-text-fill-color: transparent}.GRinputWrapper .GRrichText {	POSITION: absolute; TOP: 50%}.GRtextareaWrapper .GRrichText {	}#GRmenuList {	BOX-SIZING: content-box; POSITION: relative; BORDER-LEFT: #8ed231 2px solid; PADDING-BOTTOM: 0px; PADDING-LEFT: 8px; WIDTH: 108px; PADDING-RIGHT: 8px; BACKGROUND: #fff; FLOAT: left; BORDER-RIGHT: #8ed231 2px solid; PADDING-TOP: 0px}#GRmenuList UL {	POSITION: relative; PADDING-BOTTOM: 0px; LIST-STYLE-TYPE: none; MARGIN: -1px 0px 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FLOAT: left; PADDING-TOP: 0px}#GRmenuList UL LI {	FONT: 12px/18px tahoma; WHITE-SPACE: nowrap; FLOAT: left; COLOR: #484848; CLEAR: left; CURSOR: pointer}#GRmenuList UL LI:first-child {	FONT-WEIGHT: bold}#GRmenuList UL LI:hover {	COLOR: #000}#GRtop {	BORDER-TOP: #8ed231 2px solid; TOP: -7px}#GRbottom {	BORDER-BOTTOM: #8ed231 2px solid; BOTTOM: -6px}.GRcorner_cnt {	POSITION: absolute; WIDTH: 112px; BACKGROUND: #fff; HEIGHT: 7px; LEFT: 6px}#GRcontact {	Z-INDEX: 1; POSITION: relative; TEXT-ALIGN: center; WIDTH: 100%; BOTTOM: -4px; DISPLAY: inline-block; FONT: 11px/18px tahoma; BACKGROUND: url(undefinedbottom-line-mid.png) left top; FLOAT: left; HEIGHT: 19px; COLOR: #fff; TEXT-DECORATION: none}#GRcontact:hover {	BACKGROUND-POSITION: left bottom}#GRcontact STRONG {	COLOR: #fff; FONT-SIZE: 12px}.GRcorner {	POSITION: absolute; DISPLAY: block; BACKGROUND: url(undefinedcorners-2.png)}.GRmenu_tl {	WIDTH: 8px; BACKGROUND-POSITION: 0px 0px; HEIGHT: 7px; TOP: -2px; LEFT: -8px}.GRmenu_tr {	WIDTH: 8px; BACKGROUND-POSITION: -10px 0px; HEIGHT: 7px; RIGHT: -8px; TOP: -2px}.GRmenu_bl {	WIDTH: 10px; BOTTOM: -2px; BACKGROUND-POSITION: 0px -7px; HEIGHT: 21px; LEFT: -8px}.GRmenu_br {	WIDTH: 10px; BOTTOM: -2px; BACKGROUND-POSITION: -8px -7px; HEIGHT: 21px; RIGHT: -8px}.hover {	BACKGROUND: url(undefinedcorners-hover.png) 0px 0px}.hover {	BACKGROUND: url(undefinedcorners-hover.png) -8px 0px}#GRmenuList #GRseparator {	MARGIN: 3px 0px; WIDTH: 100%; BACKGROUND: #e5e5e5; HEIGHT: 1px; CURSOR: default}#GRmenuList #GRignore {	TEXT-INDENT: -999px; WIDTH: 31px; BACKGROUND: url(undefinedmenu-ignore.gif) 0px 0px; HEIGHT: 15px; OVERFLOW: hidden}#GRmenuList #GRignore:hover {	BACKGROUND-POSITION: 0px -15px}#GRmenuMask {	Z-INDEX: 2147483647; POSITION: fixed; WIDTH: 100%; BACKGROUND: url(undefinedmenu-bg.gif); HEIGHT: 100%; TOP: 0px; LEFT: 0px}
Hey Bashing - om! I have done that and have been doing some experiment I am now at the point where I turn on the computer it boost up to the ponit of a dialogue box which says:
 
The system is running in low-graphics mode
your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.              [ok]
 
Clicking [ok] leads to another dialogue box:
 
What would you like to do?
*run in low-graphics mode for just one season
* Reconfigure graphics
*Troubleshoot the error
*Exit to console login                     [cancel][ok]

---

### Post by Janade on 2012-09-26
Hey Bashing - om! I have done that and have been doing some experiment I am now at the point where I turn on the computer it boost up to the ponit of a dialogue box which says:

The system is running in low-graphics mode
your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself. [ok]

Clicking [ok] leads to another dialogue box:

What would you like to do?
*run in low-graphics mode for just one season
* Reconfigure graphics
*Troubleshoot the error
*Exit to console login [cancel][ok]

---

### Post by Janade on 2012-09-26
.GRcorrect {	POSITION: relative; PADDING-BOTTOM: 0px !important; BACKGROUND: url(correction.gif) repeat-x left bottom; TEXT-DECORATION: none !important}.GRSpellingCorrect {	POSITION: relative; PADDING-BOTTOM: 0px !important; BACKGROUND: url(correction.gif) repeat-x left bottom; TEXT-DECORATION: none !important}.GRspelling {	POSITION: relative; PADDING-BOTTOM: 0px !important; BACKGROUND: url(correction.gif) repeat-x left bottom; TEXT-DECORATION: none !important}.GRline {	POSITION: absolute; BOTTOM: 0px; BACKGROUND: url(correction.gif) repeat-x left bottom; HEIGHT: 3px; RIGHT: 0px; LEFT: 0px}.GRnoMark {	BACKGROUND: none transparent scroll repeat 0% 0%}.GRwrapper {	BORDER-BOTTOM: transparent 0px solid; POSITION: absolute; BORDER-LEFT: transparent 0px solid; PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; OVERFLOW: hidden; BORDER-TOP: transparent 0px solid; BORDER-RIGHT: transparent 0px solid; PADDING-TOP: 0px}.GRcontour {	POSITION: absolute; MARGIN: 0px}.GRrichText {	BORDER-BOTTOM-COLOR: transparent; PADDING-BOTTOM: 3px; BORDER-RIGHT-WIDTH: 0px; BORDER-TOP-COLOR: transparent; MARGIN: 0px; DISPLAY: block; WHITE-SPACE: pre-wrap; BORDER-TOP-WIDTH: 0px; BORDER-BOTTOM-WIDTH: 0px; COLOR: transparent; BORDER-RIGHT-COLOR: transparent; OVERFLOW: hidden; BORDER-LEFT-COLOR: transparent; BORDER-LEFT-WIDTH: 0px; -webkit-text-fill-color: transparent}.GRinputWrapper .GRrichText {	POSITION: absolute; TOP: 50%}.GRtextareaWrapper .GRrichText {	}#GRmenuList {	BOX-SIZING: content-box; POSITION: relative; BORDER-LEFT: #8ed231 2px solid; PADDING-BOTTOM: 0px; PADDING-LEFT: 8px; WIDTH: 108px; PADDING-RIGHT: 8px; BACKGROUND: #fff; FLOAT: left; BORDER-RIGHT: #8ed231 2px solid; PADDING-TOP: 0px}#GRmenuList UL {	POSITION: relative; PADDING-BOTTOM: 0px; LIST-STYLE-TYPE: none; MARGIN: -1px 0px 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FLOAT: left; PADDING-TOP: 0px}#GRmenuList UL LI {	FONT: 12px/18px tahoma; WHITE-SPACE: nowrap; FLOAT: left; COLOR: #484848; CLEAR: left; CURSOR: pointer}#GRmenuList UL LI:first-child {	FONT-WEIGHT: bold}#GRmenuList UL LI:hover {	COLOR: #000}#GRtop {	BORDER-TOP: #8ed231 2px solid; TOP: -7px}#GRbottom {	BORDER-BOTTOM: #8ed231 2px solid; BOTTOM: -6px}.GRcorner_cnt {	POSITION: absolute; WIDTH: 112px; BACKGROUND: #fff; HEIGHT: 7px; LEFT: 6px}#GRcontact {	Z-INDEX: 1; POSITION: relative; TEXT-ALIGN: center; WIDTH: 100%; BOTTOM: -4px; DISPLAY: inline-block; FONT: 11px/18px tahoma; BACKGROUND: url(undefinedbottom-line-mid.png) left top; FLOAT: left; HEIGHT: 19px; COLOR: #fff; TEXT-DECORATION: none}#GRcontact:hover {	BACKGROUND-POSITION: left bottom}#GRcontact STRONG {	COLOR: #fff; FONT-SIZE: 12px}.GRcorner {	POSITION: absolute; DISPLAY: block; BACKGROUND: url(undefinedcorners-2.png)}.GRmenu_tl {	WIDTH: 8px; BACKGROUND-POSITION: 0px 0px; HEIGHT: 7px; TOP: -2px; LEFT: -8px}.GRmenu_tr {	WIDTH: 8px; BACKGROUND-POSITION: -10px 0px; HEIGHT: 7px; RIGHT: -8px; TOP: -2px}.GRmenu_bl {	WIDTH: 10px; BOTTOM: -2px; BACKGROUND-POSITION: 0px -7px; HEIGHT: 21px; LEFT: -8px}.GRmenu_br {	WIDTH: 10px; BOTTOM: -2px; BACKGROUND-POSITION: -8px -7px; HEIGHT: 21px; RIGHT: -8px}.hover {	BACKGROUND: url(undefinedcorners-hover.png) 0px 0px}.hover {	BACKGROUND: url(undefinedcorners-hover.png) -8px 0px}#GRmenuList #GRseparator {	MARGIN: 3px 0px; WIDTH: 100%; BACKGROUND: #e5e5e5; HEIGHT: 1px; CURSOR: default}#GRmenuList #GRignore {	TEXT-INDENT: -999px; WIDTH: 31px; BACKGROUND: url(undefinedmenu-ignore.gif) 0px 0px; HEIGHT: 15px; OVERFLOW: hidden}#GRmenuList #GRignore:hover {	BACKGROUND-POSITION: 0px -15px}#GRmenuMask {	Z-INDEX: 2147483647; POSITION: fixed; WIDTH: 100%; BACKGROUND: url(undefinedmenu-bg.gif); HEIGHT: 100%; TOP: 0px; LEFT: 0px}}I tried typing in 
 
aptidtude autoclean
 
the response:
 
E: could not open lock file /var/cache/apt/archives/lock - open (13: permission denied)
E: unable to lock the download directory
 
HEEEEEELLLLPPPPPP!!!!!!

---

### Post by Janade on 2012-09-26
.GRcorrect {	POSITION: relative; PADDING-BOTTOM: 0px !important; BACKGROUND: url(correction.gif) repeat-x left bottom; TEXT-DECORATION: none !important}.GRSpellingCorrect {	POSITION: relative; PADDING-BOTTOM: 0px !important; BACKGROUND: url(correction.gif) repeat-x left bottom; TEXT-DECORATION: none !important}.GRspelling {	POSITION: relative; PADDING-BOTTOM: 0px !important; BACKGROUND: url(correction.gif) repeat-x left bottom; TEXT-DECORATION: none !important}.GRline {	POSITION: absolute; BOTTOM: 0px; BACKGROUND: url(correction.gif) repeat-x left bottom; HEIGHT: 3px; RIGHT: 0px; LEFT: 0px}.GRnoMark {	BACKGROUND: none transparent scroll repeat 0% 0%}.GRwrapper {	BORDER-BOTTOM: transparent 0px solid; POSITION: absolute; BORDER-LEFT: transparent 0px solid; PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; OVERFLOW: hidden; BORDER-TOP: transparent 0px solid; BORDER-RIGHT: transparent 0px solid; PADDING-TOP: 0px}.GRcontour {	POSITION: absolute; MARGIN: 0px}.GRrichText {	BORDER-BOTTOM-COLOR: transparent; PADDING-BOTTOM: 3px; BORDER-RIGHT-WIDTH: 0px; BORDER-TOP-COLOR: transparent; MARGIN: 0px; DISPLAY: block; WHITE-SPACE: pre-wrap; BORDER-TOP-WIDTH: 0px; BORDER-BOTTOM-WIDTH: 0px; COLOR: transparent; BORDER-RIGHT-COLOR: transparent; OVERFLOW: hidden; BORDER-LEFT-COLOR: transparent; BORDER-LEFT-WIDTH: 0px; -webkit-text-fill-color: transparent}.GRinputWrapper .GRrichText {	POSITION: absolute; TOP: 50%}.GRtextareaWrapper .GRrichText {	}#GRmenuList {	BOX-SIZING: content-box; POSITION: relative; BORDER-LEFT: #8ed231 2px solid; PADDING-BOTTOM: 0px; PADDING-LEFT: 8px; WIDTH: 108px; PADDING-RIGHT: 8px; BACKGROUND: #fff; FLOAT: left; BORDER-RIGHT: #8ed231 2px solid; PADDING-TOP: 0px}#GRmenuList UL {	POSITION: relative; PADDING-BOTTOM: 0px; LIST-STYLE-TYPE: none; MARGIN: -1px 0px 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FLOAT: left; PADDING-TOP: 0px}#GRmenuList UL LI {	FONT: 12px/18px tahoma; WHITE-SPACE: nowrap; FLOAT: left; COLOR: #484848; CLEAR: left; CURSOR: pointer}#GRmenuList UL LI:first-child {	FONT-WEIGHT: bold}#GRmenuList UL LI:hover {	COLOR: #000}#GRtop {	BORDER-TOP: #8ed231 2px solid; TOP: -7px}#GRbottom {	BORDER-BOTTOM: #8ed231 2px solid; BOTTOM: -6px}.GRcorner_cnt {	POSITION: absolute; WIDTH: 112px; BACKGROUND: #fff; HEIGHT: 7px; LEFT: 6px}#GRcontact {	Z-INDEX: 1; POSITION: relative; TEXT-ALIGN: center; WIDTH: 100%; BOTTOM: -4px; DISPLAY: inline-block; FONT: 11px/18px tahoma; BACKGROUND: url(undefinedbottom-line-mid.png) left top; FLOAT: left; HEIGHT: 19px; COLOR: #fff; TEXT-DECORATION: none}#GRcontact:hover {	BACKGROUND-POSITION: left bottom}#GRcontact STRONG {	COLOR: #fff; FONT-SIZE: 12px}.GRcorner {	POSITION: absolute; DISPLAY: block; BACKGROUND: url(undefinedcorners-2.png)}.GRmenu_tl {	WIDTH: 8px; BACKGROUND-POSITION: 0px 0px; HEIGHT: 7px; TOP: -2px; LEFT: -8px}.GRmenu_tr {	WIDTH: 8px; BACKGROUND-POSITION: -10px 0px; HEIGHT: 7px; RIGHT: -8px; TOP: -2px}.GRmenu_bl {	WIDTH: 10px; BOTTOM: -2px; BACKGROUND-POSITION: 0px -7px; HEIGHT: 21px; LEFT: -8px}.GRmenu_br {	WIDTH: 10px; BOTTOM: -2px; BACKGROUND-POSITION: -8px -7px; HEIGHT: 21px; RIGHT: -8px}.hover {	BACKGROUND: url(undefinedcorners-hover.png) 0px 0px}.hover {	BACKGROUND: url(undefinedcorners-hover.png) -8px 0px}#GRmenuList #GRseparator {	MARGIN: 3px 0px; WIDTH: 100%; BACKGROUND: #e5e5e5; HEIGHT: 1px; CURSOR: default}#GRmenuList #GRignore {	TEXT-INDENT: -999px; WIDTH: 31px; BACKGROUND: url(undefinedmenu-ignore.gif) 0px 0px; HEIGHT: 15px; OVERFLOW: hidden}#GRmenuList #GRignore:hover {	BACKGROUND-POSITION: 0px -15px}#GRmenuMask {	Z-INDEX: 2147483647; POSITION: fixed; WIDTH: 100%; BACKGROUND: url(undefinedmenu-bg.gif); HEIGHT: 100%; TOP: 0px; LEFT: 0px}.GRcorrect {    POSITION: relative; PADDING-BOTTOM: 0px !important; BACKGROUND: url(correction.gif) repeat-x left bottom; TEXT-DECORATION: none !important}.GRSpellingCorrect {    POSITION: relative; PADDING-BOTTOM: 0px !important; BACKGROUND: url(correction.gif) repeat-x left bottom; TEXT-DECORATION: none !important}.GRspelling {    POSITION: relative; PADDING-BOTTOM: 0px !important; BACKGROUND: url(correction.gif) repeat-x left bottom; TEXT-DECORATION: none !important}.GRline {    POSITION: absolute; BOTTOM: 0px; BACKGROUND: url(correction.gif) repeat-x left bottom; HEIGHT: 3px; RIGHT: 0px; LEFT: 0px}.GRnoMark {    BACKGROUND: none transparent scroll repeat 0% 0%}.GRwrapper {    BORDER-BOTTOM: transparent 0px solid; POSITION: absolute; BORDER-LEFT: transparent 0px solid; PADDING-BOTTOM: 0px; MARGIN: 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; OVERFLOW: hidden; BORDER-TOP: transparent 0px solid; BORDER-RIGHT: transparent 0px solid; PADDING-TOP: 0px}.GRcontour {    POSITION: absolute; MARGIN: 0px}.GRrichText {    BORDER-BOTTOM-COLOR: transparent; PADDING-BOTTOM: 3px; BORDER-RIGHT-WIDTH: 0px; BORDER-TOP-COLOR: transparent; MARGIN: 0px; DISPLAY: block; WHITE-SPACE: pre-wrap; BORDER-TOP-WIDTH: 0px; BORDER-BOTTOM-WIDTH: 0px; COLOR: transparent; BORDER-RIGHT-COLOR: transparent; OVERFLOW: hidden; BORDER-LEFT-COLOR: transparent; BORDER-LEFT-WIDTH: 0px; -webkit-text-fill-color: transparent}.GRinputWrapper .GRrichText {    POSITION: absolute; TOP: 50%}.GRtextareaWrapper .GRrichText {    }#GRmenuList {    BOX-SIZING: content-box; POSITION: relative; BORDER-LEFT: #8ed231 2px solid; PADDING-BOTTOM: 0px; PADDING-LEFT: 8px; WIDTH: 108px; PADDING-RIGHT: 8px; BACKGROUND: #fff; FLOAT: left; BORDER-RIGHT: #8ed231 2px solid; PADDING-TOP: 0px}#GRmenuList UL {    POSITION: relative; PADDING-BOTTOM: 0px; LIST-STYLE-TYPE: none; MARGIN: -1px 0px 0px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; FLOAT: left; PADDING-TOP: 0px}#GRmenuList UL LI {    FONT: 12px/18px tahoma; WHITE-SPACE: nowrap; FLOAT: left; COLOR: #484848; CLEAR: left; CURSOR: pointer}#GRmenuList UL LI:first-child {    FONT-WEIGHT: bold}#GRmenuList UL LI:hover {    COLOR: #000}#GRtop {    BORDER-TOP: #8ed231 2px solid; TOP: -7px}#GRbottom {    BORDER-BOTTOM: #8ed231 2px solid; BOTTOM: -6px}.GRcorner_cnt {    POSITION: absolute; WIDTH: 112px; BACKGROUND: #fff; HEIGHT: 7px; LEFT: 6px}#GRcontact {    Z-INDEX: 1; POSITION: relative; TEXT-ALIGN: center; WIDTH: 100%; BOTTOM: -4px; DISPLAY: inline-block; FONT: 11px/18px tahoma; BACKGROUND: url(undefinedbottom-line-mid.png) left top; FLOAT: left; HEIGHT: 19px; COLOR: #fff; TEXT-DECORATION: none}#GRcontact:hover {    BACKGROUND-POSITION: left bottom}#GRcontact STRONG {    COLOR: #fff; FONT-SIZE: 12px}.GRcorner {    POSITION: absolute; DISPLAY: block; BACKGROUND: url(undefinedcorners-2.png)}.GRmenu_tl {    WIDTH: 8px; BACKGROUND-POSITION: 0px 0px; HEIGHT: 7px; TOP: -2px; LEFT: -8px}.GRmenu_tr {    WIDTH: 8px; BACKGROUND-POSITION: -10px 0px; HEIGHT: 7px; RIGHT: -8px; TOP: -2px}.GRmenu_bl {    WIDTH: 10px; BOTTOM: -2px; BACKGROUND-POSITION: 0px -7px; HEIGHT: 21px; LEFT: -8px}.GRmenu_br {    WIDTH: 10px; BOTTOM: -2px; BACKGROUND-POSITION: -8px -7px; HEIGHT: 21px; RIGHT: -8px}.hover {    BACKGROUND: url(undefinedcorners-hover.png) 0px 0px}.hover {    BACKGROUND: url(undefinedcorners-hover.png) -8px 0px}#GRmenuList #GRseparator {    MARGIN: 3px 0px; WIDTH: 100%; BACKGROUND: #e5e5e5; HEIGHT: 1px; CURSOR: default}#GRmenuList #GRignore {    TEXT-INDENT: -999px; WIDTH: 31px; BACKGROUND: url(undefinedmenu-ignore.gif) 0px 0px; HEIGHT: 15px; OVERFLOW: hidden}#GRmenuList #GRignore:hover {    BACKGROUND-POSITION: 0px -15px}#GRmenuMask {    Z-INDEX: 2147483647; POSITION: fixed; WIDTH: 100%; BACKGROUND: url(undefinedmenu-bg.gif); HEIGHT: 100%; TOP: 0px; LEFT: 0px}
 
 
I tried typing in 
 
aptidtude autoclean
 
the response:
 
E: could not open lock file /var/cache/apt/archives/lock - open (13: permission denied)
E: unable to lock the download directory
 
HEEEEEELLLLPPPPPP!!!!!![/QUOTE]

---

### Post by Bashing-om on 2012-09-26
I am back....things not looking as good as they could...but on the brighter side..not too bad ...Let me slow down and look at this slopyation (should have paid more attention to the bottom line ya gave out last night)...

Ok ...two things off the top of my head.... disk allocation and getting your graphics card configured. ...By the way ...what version did you have prior to the upgrade button push ?

lemme see the output from terminal of:
```
df-h
```

see iffen we do indeed have to make more operating space.

---

### Post by Janade on 2012-10-03
df-h gives a response: command not found

sudo rm/var//lib/dpkg/lock
sudo rm/var/cache/apt/archives/lock
sudo rm/var/lib/lists/lock
sudo apt-get update

Response:no space left on device

sudo reboot 

Response: low graphics

ALT F1
dpkg--configure-a 

Response: operation requires superuser privilege

sudo apt-get clean
sudo apt-get autoremove

Response: have to do manually  sudo -configure-a

sudo --configure -a
sudo apt-get update
sudo apt-get upgrade

Response: E:unmet dependencies. Try using -f

sudo apt-get install-f

Response: This APT has supercow powers

sudo apt-get update
sudo reboot

With all this I was able to get to my homepage!!!! Felt great!!!!!
However I have no top panel or bottom panel!!!! Hellllppppp!!!!

---

### Post by Bashing-om on 2012-10-03
Janade; Ok are we still where we left off ?
1. Disk space
2. graphics card configuration ?

looking back at the df command, i did a type-o; correct command to:
```
df -h
```
that is a space before the "-h".

Get this straightened up so we have some operating space => then next.

[INDENT]try'n to help <==BDQ

[/INDENT]

---

