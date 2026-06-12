---
title: "Unable to change remap a key."
date: 2018-02-16
forum: New to Ubuntu
---

### Post by ftv on 2018-02-16
I'm using the Icelandic keyboard layout and want to remap the TLDE key which currently returns " ° " I want it to output " < " when pressed normally and " > " when pressing using shift. 
I've read the documentation on remapping keys but I'm extremely new to using Ubuntu (Linux) so I've been having problems.  

Best regards,
FTV

---

### Post by DuckHook on 2018-02-16
Welcome to the forums, ftv.

You need to provide enough info if you want us to help. At a minimum, what version and flavour are you using? Please post back the results of the following: ```
uname -a
``````
lsb_release -a
``````
loginctl show-session `loginctl|grep <YOUR_USER_NAME>|awk '{print $1}'` -p Type
```…where <YOUR_USER_NAME> is properly replaced with your username (without the pointy brackets). Also tell us what "documentation" you've been following. Links if you have them.

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by ftv on 2018-02-16
> **DuckHook said:**
> Welcome to the forums, ftv.

You need to provide enough info if you want us to help. At a minimum, what version and flavour are you using? Please post back the results of the following: ```
uname -a
``````
lsb_release -a
``````
loginctl show-session `loginctl|grep <YOUR_USER_NAME>|awk '{print $1}'` -p Type
```&#8230;where <YOUR_USER_NAME> is properly replaced with your username (without the pointy brackets). Also tell us what "documentation" you've been following. Links if you have them.

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the *Adv Reply* toolbar.


Hi, sorry for the lack of info.
Here's the info you requested in the image below.

Documentation:
[https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions?action=show&redirect=Howto%3A+Custom+keyboard+layout+definitions](https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions?action=show&redirect=Howto%3A+Custom+keyboard+layout+definitions)

Image:
[URL="https://imgur.com/IoM4l9S"]https://imgur.com/IoM4l9S

[/URL]

---

### Post by DuckHook on 2018-02-17
No need for screenshots. You can highlight the text from a terminal session and copy it with a right click of your mouse. You can then paste this into the forum posting box between code tags and the forum software will automatically format it into code boxes.

[LIST]
[*]Perhaps you should tell us what you are trying to do and why?
[*]Are you using a Mac or PC?
[*]What physical keyboard are you using?
[*]Why do you wish to remap the tilde key?
[*]Which symbols file are you trying to edit? I assume it is: ```
/usr/share/X11/xkb/symbols/is
```
[*]What have you done so far? Have you started editing this or any other system files?
[*]Please post the results of: ```
cat /usr/share/X11/xkb/symbols/is
```
[/LIST]
Users have reported corrupted keyboards and the inability to log in when playing with the **xkb** file. Best not to play around with it unless you first make a backup of the file and have a LiveUSB with which you can boot into the system and restore the file.

---

### Post by ftv on 2018-02-17
Okay so,
I guess what was hindering me was general Linux knowledge. I tried to edit the 
"/usr/share/X11/xkb/symbols/is" before posting this thread, but was unable due to permissions. So what I did now was install gksudo and run the /usr/share/X11/xkb/symbols/is file through gedit  and was able to change it from there.

Thanks for the help and sorry for not being clear enough about my problem and not providing enough information.

Best regards.

---

### Post by DuckHook on 2018-02-17
*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

