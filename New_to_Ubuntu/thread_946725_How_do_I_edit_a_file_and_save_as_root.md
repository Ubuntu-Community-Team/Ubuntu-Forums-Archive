---
title: "How do I edit a file and save as root?"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by VitaminBB on 2008-10-13
This is such a simple question but I cant find the answer elsewhere.

I want to change the title of a file but when I try it says I dont have permission

How do I make it save the new file title I want?

---

### Post by patrickballeux on 2008-10-13
You have to open it as root...

For example:
In a terminal
> sudo gedit /etc/someconfigfile.conf

or pressing ALT-F2
> gksudo gedit /etc/someconfigfile.conf

You will be asked for the root's password (or your own actually)...

This way, you are invoking the software with root access...

EDIT: Just saw you wrote edit "title"...  misread, sorry...  but the sudo applies anyway...

In a terminal:
> sudo mv FILE NEWFILENAME

You could gksudo nautilus, but that is pretty dangerous to screw up your system...

---

### Post by SuperSonic4 on 2008-10-13
```
gksudo nautilus
``` will open nautilus as root and you should be able to navigate and rename in the standard way. Although it's best to be careful since it could screw up your system

---

### Post by Nxion on 2008-10-13
> **VitaminBB said:**
> This is such a simple question but I cant find the answer elsewhere.

I want to change the title of a file but when I try it says I dont have permission

How do I make it save the new file title I want?

What are you using to edit the file?

There are a few ways of doing this. You could edit from a terminal with admin privligaes like so..

```
sudo nano /path/to/file
```OR say you want to edit something with gedit (linux equlivlent to text edit or wordpad in Windows). Again, open a terminal and do..

```
sudo gedit /path/to/file
```OR you could even do this.
[URL="http://ubuntuforums.org/showthread.php?t=47525"]
[/URL]

> **How to open files as root user via right click **

 gedit $HOME/.gnome2/nautilus-scripts/Open\ as\ root

[LIST]
[*]Insert the following lines into the new file
[/LIST]
 for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
    gksudo "gnome-open $uri" &
done

[LIST]
[*]Save the edited file
[/LIST]
 Places -> Home -> View -> Show Hidden Files -> .gnome2 -> nautilus-scripts -> *Right click* on Open as root -> 
Properties -> Permissions -> Execute

*Right click* on file -> Scripts -> Open as rootI got that from here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

And ONE more link for ya. This link has a whole lot more scripts for nautilus.

[http://www.ubuntu-unleashed.com/2007/09/125-nautilus-scripts-to-simplify.html](http://www.ubuntu-unleashed.com/2007/09/125-nautilus-scripts-to-simplify.html)


Hope that this has help you in some way.

:)

---

### Post by VitaminBB on 2008-10-13
Thanks guys ...

The second problem I has was I couldnt find the file then realized I need to "show hidden files" all the damn time *L*

Fixed now :)

---

### Post by Nxion on 2008-10-14
> **VitaminBB said:**
> Thanks guys ...

The second problem I has was I couldn't find the file then realized I need to "show hidden files" all the damn time *L*

Fixed now :)

Don't forget to make this as solved :) This can be done by clicking the drop down on the top labeled "Thread Tools" and click "Mark as Solved"

Cheers!,
Nxion

---

