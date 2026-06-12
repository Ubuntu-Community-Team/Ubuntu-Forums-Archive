---
title: "HOW TO: Reset keyring password"
date: 2010-03-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Francewhoa on 2010-03-14
*[FONT=Arial][SIZE=2]Note to myself: When this how-to is approved and published delete the following comment. Then link to this how-to.[/SIZE][/FONT]* [http://ubuntuforums.org/showthread.php?p=8966489#post8966489](http://ubuntuforums.org/showthread.php?p=8966489#post8966489)


[FONT=Arial][SIZE=2]**REQUIEREMENTS**[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Ubuntu 8.04.x LTS desktop edition[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]**ISSUE**[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]You're trying to change your Keyring password but the following error message is output.[/SIZE][/FONT]
> [FONT=Arial][SIZE=2]*Couldn’t change keyring password.*[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]*    Access Denied*[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]You tried every possible passwords including your Ubuntu administrator password but none are working.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]**STEPS TO RESET YOUR KEYRING PASSWORD **[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Go to APPLICATIONS -> ACCESSORIES -> PASSWORD AND ENCRYPTION KEYS[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Go to EDIT menu -> PREFERENCES option[/SIZE][/FONT]
 
 [FONT=Arial][SIZE=2]Highlight the LOGIN AUTOMATICALLY UNLOCKED WHEN USER LOGS IN entry. [/SIZE][/FONT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Click on REMOVE KEYRING button.[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Click on OK button.[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Click on ADD KEYRING button.[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Type in a NEW KEYRING NAME. For example MY NEW KEYRING. This name could be anything. [/SIZE][/FONT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Type in a PASSWORD and CONFIRM PASSWORD. Usually the same as your Ubuntu admin password. But it could be anything. A complex password is safer. Such as mixing letters, numbers and symbols. Note that you will need to remember this password in future if Ubuntu asks your keyring. [/SIZE][/FONT] [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Click on CLOSE button.[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]You new keyring has been saved.[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]At the same time a new DEFAULT keyring as been created. To test this go to APPLICATIONS -> ACCESSORIES -> PASSWORD AND ENCRYPTION KEYS[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Go to EDIT menu -> PREFERENCES option[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Under the section PASSWORD KEYRING you should see your new keyring in there and another one title DEFAULT.[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]At the bottom of this window make sure that LOCATION FOR APPLICATION PASSWORD is set to DEFAULT.[/SIZE][/FONT][FONT=Arial][SIZE=2] Find below attached screenshot to clarify final result.
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Click on CLOSE button.[/SIZE][/FONT][FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]That's it you're done.[/SIZE][/FONT]

---

