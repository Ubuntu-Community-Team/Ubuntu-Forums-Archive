---
title: "[SOLVED] How to put icons on Desktop"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by lyni on 2008-06-30
hi could someone please tell me how to put icons on my desktop eg: I want to put the Document folder on the desktop. How would I do this?
thanks 
lyn

---

### Post by hyper_ch on 2008-06-30
what options do you get when you right-click the desktop?

---

### Post by Marshal0505 on 2008-06-30
> **lyni said:**
> hi could someone please tell me how to put icons on my desktop eg: I want to put the Document folder on the desktop. How would I do this?
thanks 
lyn


right click your desktop , choose 'create launcher',
choose type 'location' in the top field. 
Click 'browse' to define path to location in the 3rd field.

---

### Post by lyni on 2008-06-30
thank you for the replies. Marshall I just tried your instructions and didn't get far. could you please expand on what you said and what I do next? thanks again. sorry but I am very new to ubuntu.
lyni

---

### Post by hyper_ch on 2008-06-30
you could say what you did, how far you got and where you had a problem....

---

### Post by sayakb on 2008-06-30
Press Alt+F2 and type in **gconf-editor **and press enter
Navigate to /apps/nautilus/desktop and **check** the *home_icon_visible* checkbox.

---

### Post by mcduck on 2008-06-30
If you want Computer, Documents, Network and Trash icons on your desktop here's hoe to enable them:

1. Press Alt-F2 and run "gconf-editor"

2. Browse to apps/nautilus/desktop

3. Enable which ever icons you want. You can also change their names in the same place.

---

### Post by WRDN on 2008-06-30
The easiest way to do this is to right click on the folder and select "Make Link". Then, just cut and paste the link onto the desktop.

So, in the case of your Documents folder, go to the "/home/[user]/" directory, right click on "Documents" and select "Make Link".

---

### Post by NovaAesa on 2008-06-30
One way of doing it is to drag your documents folder onto the Desktop while holding down control and shift. This will create a link, which is similar to a shortcut on Windows.

---

### Post by lyni on 2008-06-30
thanks again everyone. I now have the Documents folder on my desktop.
lyni

---

