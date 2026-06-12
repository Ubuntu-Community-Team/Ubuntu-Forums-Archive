---
title: "ERROR: The system is running in low-graphics mode"
date: 2013-11-12
forum: New to Ubuntu
---

### Post by t_a_y_l_o_s on 2013-11-12
I cannot figure out how to fix this error.  I have ubuntu 12.04.  It was working fine but when I restarted I got the error.  Below is all of the screens I can access and everything that it says on every screen.  Everything that is posted in between the squiggly brackets {} are added by me and do not actually appear on the screen.  The numbers at the top left are unique identifiers for each screen.  {--> #} means that that option leads to screen number #.  That's to anyone in advance for your help.


____________________________________________________________________________________________________________________________________
1


! The system is running in low-graphics mode
     Your screens graphics card, and input device settings
     could not be detected correctly.  You will need to configure these yourself.
                                                                                       ______
                                                                                       | OK   | {--> 2}
                                                                                                   
___________________________________________________________________________________________________________________________________
2


What would you like to do?
      .  Run in low-graphics mode for just one session {--> 9}
      .  Reconfigure graphics {--> 8}
      .  Troubleshoot the error {--> 4}
      .  Exit to console login {--> 3}


___________________________________________________________________________________________________________________________________
3


mountall: Plymouth command failed
                                              mountall: Disconnected from Plymouth
                                                                                                 {I can type stuff here}


___________________________________________________________________________________________________________________________________
4


What information would you like to review?
      .  Review the xserver log file {--> 5}
      .  Review the startup errors {--> 6}
      .  Edit configuration file {--> 4}
      .  Archive configuration and logs {--> 7}


____________________________________________________________________________________________________________________________________
5


[   26.258]
X.Org X Server 1.11.3
Release Data: 2011-12-16
[   26.258] X Protocol Version 11, Revision 0


{ Many many pages of stuff that looks like the above }


[   27.152] Server termminated successfully (0). Closing log file.
                                                                                       ______
                                                                                       | OK   | {--> 4}


___________________________________________________________________________________________________________________________________
6


{ All blank, nothing is here }
                                                                                       ______
                                                                                       | OK   | {--> 4}


___________________________________________________________________________________________________________________________________
7


 i   Relevant configuration and log files have been saved to:
       /var/log/failsafeX-backup-131112115100.tar
       Bug reports can be submitted at [http://www.launchpad.net/ubuntu](http://www.launchpad.net/ubuntu)
                                                                                       ______
                                                                                       | OK   | {--> 4}


___________________________________________________________________________________________________________________________________
8


How would you like to reconfigure your display?
      .  Use default (generic) configuration {--> 8}
      .  Use back-up configuration {--> 8}


___________________________________________________________________________________________________________________________________
9


Stand by one minute while display restarts...
  { loading bar is full here }
                                                                         __________     ______
                              {can't click cancel}                 | x  cancel|     | OK   | {--> 11}


___________________________________________________________________________________________________________________________________
10


* Stopping system V runlevel compatibility                                                                                                         [ OK ] 
* Stopping cold plug devices                                                                                                                           [ OK ] 


* Stopping log initial device creation                                                                                                                 [ OK ] 


* Starting enable remaining boot-time encrypted block devices                                                                              [ OK ] 


* Starting configure network device security                                                                                                      [ OK ] 


* Starting save udev log and update rules                                                                                                         [ OK ] 


* Starting configure virtual network devices                                                                                                       [ OK ] 


* Stopping udev log and update rules                                                                                                                [ OK ] 


* Stopping configure virtual network devices                                                                                                      [ OK ] 


_________________________________________________________________________________________________________________________________
11

* checking battery state...                                                                                                                              [ OK ]
                                                                                                                                                                         m
ountall: Disconnedted from Plymouth
                                                { I can type stuff here, it just sits here and does nothing }

__________________________________________________________________________________________________________________________________

{ End of screens }

And that's all.  That's all I can do.  Any help or information is greatly appreciated.

---

### Post by heir4c on 2013-11-12
Boot up and choose in the grub menu the second line (Recovery mode) and then when you come in a small menu you click just Enter. Load it now further to the Desktop?

---

### Post by t_a_y_l_o_s on 2013-11-12
Hello, heir4c.  Thanks for your response.  When I follow your instructions it displays { Screen 1 } from my first post, and I have the same options as I detailed there.  So it still doesn't load to the desktop.  Is this expected?

---

### Post by fantab on 2013-11-13
> What would you like to do?
      .  Run in low-graphics mode for just one session {--> 9}
      .  Reconfigure graphics {--> 8}
      .  Troubleshoot the error {--> 4}
      .  Exit to console login {--> 3}


What happens when you choose 'Reconfigure graphics' and/or 'Troubleshoot the error'?

---

### Post by t_a_y_l_o_s on 2013-11-13
Hi, fantab.  Thanks for responding.

> [COLOR=#000000]What happens when you choose 'Reconfigure graphics' and/or 'Troubleshoot the error'?[/COLOR]

When I choose [COLOR=#000000]'Reconfigure graphics' it goes to screen number 8 (this is what the {--> 8} is trying to refer to).  Screen number 8 is given by:

[/COLOR][COLOR=#000000]__________________________________________________ __________________________________________________ _______________________________[/COLOR]
[COLOR=#000000]8[/COLOR]


[COLOR=#000000]How would you like to reconfigure your display?[/COLOR]
[COLOR=#000000]. Use default (generic) configuration {--> 8}[/COLOR]
[COLOR=#000000]. Use back-up configuration {--> 8}
_________________________________________________________________________________________________________________________

Same story for 'Troubleshoot the error', it goes to screen number 4 (as indicated by {--> 4}):


[/COLOR][COLOR=#000000]__________________________________________________ __________________________________________________ _______________________________[/COLOR]
[COLOR=#000000]4[/COLOR]


[COLOR=#000000]What information would you like to review?[/COLOR]
[COLOR=#000000]. Review the xserver log file {--> 5}[/COLOR]
[COLOR=#000000]. Review the startup errors {--> 6}[/COLOR]
[COLOR=#000000]. Edit configuration file {--> 4}[/COLOR]
[COLOR=#000000]. Archive configuration and logs {--> 7}

_____________________________________________________________________________________________________________________________

[/COLOR]Please let me know if my responses are not clear.

---

### Post by fantab on 2013-11-13
What Graphics do you have onboard?

> [COLOR=#000000]How would you like to reconfigure your display?[/COLOR]
[COLOR=#000000]. Use default (generic) configuration {--> 8}[/COLOR]
[COLOR=#000000]. Use back-up configuration {--> 8}[/COLOR]

What happens when you use the options above?

Do you have your Important data backed up? If NOT, then BACK UP ALL YOUR IMPORTANT DATA, preferably to an External Device. These Graphic issues are sometimes dicey and you may have re-install ubuntu.

The following Links contain some great information about Graphics issues, see if you can find something useful:
[http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
[http://askubuntu.com/questions/225090/the-system-is-running-in-low-graphics-mode-error-in-virtualbox](http://askubuntu.com/questions/225090/the-system-is-running-in-low-graphics-mode-error-in-virtualbox)

---

### Post by heir4c on 2013-11-13
You can also try:
Boot up and when you see the Grub menu click the 'e' on your keyboard. Then you get a text. One of the lines have 'Linux' at the front and at the end of that line you have: quiet splash.
Navigate to the end of the line with the arrowkeys. Type in: nomodeset
You need a space between 'splash' and nomodeset. 
Click b to boot further. 
Go it now to the login/Desktop?

---

### Post by t_a_y_l_o_s on 2013-11-14
Thanks fantab.  I found the solution.  The solution was in the first link you posted under the heading of "**You have too many files on your computer, and have exhausted disk space**".  I followed those instructions and it fixed it.  Thanks.

---

### Post by fantab on 2013-11-15
You are Welcome!
Mark the thread as "Solved" from Thread Tools. It helps others looking to 'solve' a similar issue.

---

