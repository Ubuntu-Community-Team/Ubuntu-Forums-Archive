---
title: "error message (gnome-panel)"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by NubiNubi on 2008-07-07
Error Message:
An error occurred while loading or saving configuration information for gnome-panel. Some of your configuration settings may not work properly.

Details:
Type mismatch: Expected `string' got `int' for key /apps/nautilus/desktop/computer_icon_name

_________

Happened when I tried to turn off "computer" and "trash" icon in nautilus.  Clicked the "computer_icon_name" field instead of "icon visible" box made the field go blank.  Tried retyping "<no value>" (same as what appears for other icon names) but it didn't like it.

Problems: Desktop files disappeared and I can't get menu when right-clicking the desktop.

Using Hardy Heron installed via Wubi.  I also have desklets, awn dock, custom wallpaper, icons, themes, and login installed.  I found info about PCMan File Manager online and installed it so I can access my files again and it seems to work fine.  But I get the error message every time I open and close it.  Same happens when I open and close awn dock but not every time.

Any fixes .... without re-installing?

Everything else seems to be working fine.

---

### Post by annda on 2008-07-07
hit ALT-F2 and enter gconf-editor. navigate to /apps/nautilus/desktop and fix the values - double-click the key value and you will get a popup where you can choose the right type (integer, boolean, string) and insert the right value.

since you have so much stuff customized, avoid reinstalling by all means.

---

### Post by NubiNubi on 2008-07-07
> **annda said:**
> hit ALT-F2 and enter gconf-editor. navigate to /apps/nautilus/desktop and fix the values - double-click the key value and you will get a popup where you can choose the right type (integer, boolean, string) and insert the right value.

since you have so much stuff customized, avoid reinstalling by all means.

Hi, thanks for such a fast reply!  I've tried the gconf-ed all the way to the "key edit" window.  I've managed to get my desktop files back and I get the dropdown menu when I right-click the desktop, but I'm still getting the error message when I open and close PCMan File Manager.

I've reset the values as follows:

"computer_icon_name"
value = 0

I'm assuming zero because the others say "<no value>".  But I don't think that's the problem.

The "Key Edit" window includes 3 lines:

Name: /apps/nautilus/desktop/computer_icon_name (this line is fixed)
Type:  Integer (this is also fixed)
Value:  0  (this I can change to any value, positive or negative.  I'm assuming "0" because all the other read "<no value>")

I tried typing in "<no value>" like it reads for the others but it won't accept it.

I checked the other icons listed and all the "Type" menus read "String", not "Integer", which is what the computer can't find according to the error message details.

How do I "unfreeze" the "Type" dropdown so I can select "String"?

Here's another oddity.  As I try to change the settings in the "Key Edit", a file folder sometimes gets dropped on the desktop named, "<no value>".  I don't know where it comes from or where it's supposed to go.  But when I close the "Key Edit" menu, it goes away.

Any other thoughts?  Thanks.

---

### Post by NubiNubi on 2008-07-08
SOLUTION

1.  gconfig-edit...apps...nautilus...desktop...desktop icons listing.

2.  Right-click the error listing - in this case, "computer_icon_name".

3.  See dropdown menu for: "New Key"|"Edit Key"|"Unset Key"|"Set as Default"|"Set as Mandatory".

4.  Select "Unset Key" - deletes error "key".

5.  Select "New Key" - creates new "key".

6.  Specify correct values, incl. "String"/ not "Integer" - "Type:" drop-down should work now.

7.  Do a little chair dance.  Pat yourself on the back.  Click, "Okay".

8.  If you're a Nubi like me, this is your double-whammy FREAK OUT!! where you've just lost the friggin' "key", ijit!  NO NEW "KEY"!!  WTF??

9.  Abject sigh of defeat.  Close config edit. Re-install?  Re-install?   Re-install???...

10.  Start over for the DUMB-teenth time.  gconfig-edit......

     WAL-LAH!  Brand New Key!!  MAH-GIC!   \\:D/\\:D/\\:D/

11.  Check values.  Check settings.  Check desktop, files, PCMan, open/close, o/c, o/c,o/c, etc.  No more error message!

     Nubi-buntu LIVES!!!

12. Hasta la Linux baby. I'll be Nubi-Bach.  ):P

---

