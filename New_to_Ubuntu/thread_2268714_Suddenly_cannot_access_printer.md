---
title: "Suddenly cannot access printer"
date: 2015-03-10
forum: New to Ubuntu
---

### Post by penny3 on 2015-03-10
When I installed Ubuntu 14.04, I networked the Canon printer that is connected to a computer running Windows XP. Everything was tickety-boo until today when, all of a sudden, I cannot get anything to print and I get a message stating that: "cannot access CIFS host". Can somebody tell me why this might have happened and what I need to do to fix it and get my printer back again? I have checked the 'settings' and the printer icon has a green arrow indicating it is 'there' and active but ... 

Thank you!

---

### Post by pdc on 2015-03-10
Hi Penny

from this

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

it seems that samba will be involved; 

__________________--

this link [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu_print_server_compatible_with_Windows_.28Samba.29](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu#Ubuntu_print_server_compatible_with_Windows_.28Samba.29) is just a few paragraphs down the first link ........... is any of this of help?

_______________________

actually; browsing more posts in the Ubuntu forum

[http://ubuntuforums.org/showthread.php?t=2268145&highlight=canon](http://ubuntuforums.org/showthread.php?t=2268145&highlight=canon)

this was of a similar story to yours: sounds like samba issues; sounds like terminal commands etc

---

### Post by penny3 on 2015-03-10
Thanks, pdc. I did a search in the posts and kept running into this 'Samba' thing but ... I thought it was a different OS. Oops! I will read your links and see if I can understand them.

---

### Post by penny3 on 2015-03-10
The last thread that you linked to sounds exactly like what I am experiencing. I am trying to follow the same commands that worked for the other poster but I am stuck at this point ...

"Then edit the smb.conf file.  You can edit the file with gedit with this command 	Code:

 	gksudo gedit /etc/samba/smb.conf 
[COLOR=#ff0000]You will need to add this to the [global] section[/COLOR] 	Code:

 	netbios name = HP-LAPTOP
name resolve order = bcast 
...you can use a different netbios name if you like.  Just remember that it can't be longer than 15 characters."

I have highlighted that problem area 'global' section ... where do I find that? After I entered the '
gksudo gedit /etc/samba/smb.conf' command a screen popped that says

smb.conf (etc/samba)-gedit with a menu of 'file, edit, view, search ... etc. but when I clicked on the drop down menus 
for each, nothing came up as 'global'.

---

### Post by penny3 on 2015-03-11
Also - I have minimized both the 'gedit' screen and the terminal screen as I don't know it I will mess anything up now that I have reached this point in the process if I exit out of them ...

---

### Post by sandyd on 2015-03-11
> **penny3 said:**
> Also - I have minimized both the 'gedit' screen and the terminal screen as I don't know it I will mess anything up now that I have reached this point in the process if I exit out of them ...

Gedit is equivalent to notepad in Windows

Press Control + F and search for [global]

You can add the two lines on a new line after [global]

Side note:
Alternatively, assuming that you haven't modified the file, close everything (and say no when it asks about saving) and run
```

sudo sed -i '/\[global\]/anetbios name = HP-LAPTOP\nname resolve order = bcast' /etc/samba/smb.conf
```

---

### Post by penny3 on 2015-03-11
Thank you, Sandyd - when I tried to do a search using Control + F for [global] nothing came up. So I exited out of gedit and used the code you provided. This is the error message that came up: "sed: -e expression #1, char 64: unterminated address regex"

Looks like there is more happening here than a simple bios name change ... :(

---

### Post by pdc on 2015-03-11
so Penny; we have no need for samba; so I know nothing about it; 

however I see the standard ubuntu install has samba and when I type ```
gedit /etc/samba/smb.conf
``` in a terminal (so it is read-only) I have the [SIZE=4][COLOR="#FF0000"]> [global][/COLOR][/SIZE] mentioned near the top of the file; it has its own little section

_________________

so maybe try what I did: ```
gedit /etc/samba/smb.conf
``` so that uses [COLOR="#008000"]gedit[/COLOR], the text editor; and it opens the file [COLOR="#B22222"]smb.conf[/COLOR] (the configure file for samba) .. that is; very logically I guess; inside the [COLOR="#0000FF"]samba[/COLOR] directory, that is inside the [COLOR="#0000FF"]etc[/COLOR] directory

........... when you want to make changes, the gksudo prefix allows you to save changes you make so it is the ```
gksudo gedit /etc/samba/smb.conf
``` command; I often suggest to folks they first-time open a file with the read-only powers ...then you can't change the established files that way .. 

____________________

(I just wonder you don't edit the Title of this thread to something like SAMBA help needed to attract the right sort of reader to your thread ..............

---

### Post by penny3 on 2015-03-11
Very good suggestion, pdk - to change the thread title to 'need Samba help'. To avoid unnecessary confusion, I will start a new thread with that title.

---

