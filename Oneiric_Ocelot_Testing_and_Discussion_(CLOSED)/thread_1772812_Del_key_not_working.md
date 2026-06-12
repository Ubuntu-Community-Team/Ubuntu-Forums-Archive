---
title: "Del key not working?"
date: 2011-06-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-06-01
Anyone seeing this behavior? The keyboard "Delete" key seems disabled and I have to right click and pick "move to trashcan" from the drop down menu. I have a keyboard on my desktop machine and would like to use if that is still possible. :)

Thanks Bill

---

### Post by Framli on 2011-06-01
Try Shift+Del, it works for me. Maybe it's the new Nautilus behavior.

---

### Post by afv on 2011-06-01
It's **Ctrl+Delete** now. ;)

---

### Post by MacUntu on 2011-06-01
Indeed sounds like a GNOME behavior: "Because you could accidentally hit the Del key and move files to Trash!" :D

You'll soon have to verify every action with an iris scan.

---

### Post by Framli on 2011-06-01
Apparently it's
**Ctrl+Delete** to move to the trash
**Shift+Delete** to have a confirmation dialog about moving something to the trash

I'm very curious about the rationale behind this...

---

### Post by lucazade on 2011-06-01
> **Framli said:**
> Apparently it's
**Ctrl+Delete** to move to the trash
**Shift+Delete** to have a confirmation dialog about moving something to the trash

I'm very curious about the rationale behind this...

I'd like to know as well why I've to use Alt+left mouse+right mouse click on gnome-panel to get the contextual menu (edit panel properties).

It seems a magic combo like for MortalKombat or StreetFighter :P

---

### Post by mc4man on 2011-06-01
To reset delete button
dconf-editor
org > gnome > desktop > interface > check can-change-accels.

open nautilus > highlight any file > edit > mouse over delete, press delete button twice

Or if preferred do it over the 'move to trash' so delete moves to trash

> rationale behind this..
same as removing Ctrl+Alt+backspace, scroll on desktop ect. ect.

---

### Post by Framli on 2011-06-01
> same as removing Ctrl+Alt+backspace, scroll on desktop ect. ect.
I meant the rationale behind having Shift+Del and Ctrl+Del with two different behaviors: one opening a confirmation dialog before moving to trash and not the other.

---

### Post by mc4man on 2011-06-01
> **Framli said:**
> I meant the rationale behind having Shift+Del and Ctrl+Del with two different behaviors: one opening a confirmation dialog before moving to trash and not the other.

I must of missed something - I thought one moved to trash, the other deleted, confirmation is just a nautilus preference that applies to both.

---

### Post by Framli on 2011-06-01
My mistake, I misread the prompt. :rolleyes:
**Shift+Del** doesn't move to the trash, but deletes after confirmation.

---

### Post by sparker256 on 2011-06-01
> **Framli said:**
> My mistake, I misread the prompt. :rolleyes:
**Shift+Del** doesn't move to the trash, but deletes after confirmation.
I would think just pressing "Delete" should put the item in trash. If you press shift or and other key plus "Delete" with conformation it does not go in the trash. I do not understand why these concepts that have been around for a very long time needed to be changed.  :)

Bill

---

### Post by mc4man on 2011-06-01
> I do not understand why these concepts that have been around for a very long time needed to be changed
In cases like this it didn't need to be changed, someone (s) in a position to change decided to.
If you don't like it then change it back so delete moves to trash.

---

### Post by sparker256 on 2011-06-01
> **mc4man said:**
> In cases like this it didn't need to be changed, someone (s) in a position to change decided to.
If you don't like it then change it back so delete moves to trash.
Sorry re read your post and after a little playing around I do have the behavior that I wanted. Thank you and am slowly learning to understand that most can be changed if you know where to look. :D

Bill

---

