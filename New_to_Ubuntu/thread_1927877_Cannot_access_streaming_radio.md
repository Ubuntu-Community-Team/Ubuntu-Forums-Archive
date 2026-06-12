---
title: "Cannot access streaming radio"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by kizzyaggots on 2012-02-18
[SIZE="2"][B][COLOR="DarkOrchid"]Hi I was wondering if somebody could help me with online streaming radio? I have reinstalled my drivers, checked if i have restricted extras and Gstreamer plugins. I have no idea why i can't listen to the radio stations as i did before, I have tried to launch radio tray and it will not respond either. Please if anybody has an idea of what i'm doing wrong could you please help me.

                Kind Regards Kizzy. [/COLOR][/B][/SIZE]

---

### Post by ron999 on 2012-02-18
> **kizzyaggots said:**
> [SIZE="2"]**[COLOR="DarkOrchid"] I have tried to launch radio tray and it will not respond either.[/COLOR]**[/SIZE]
Hi
Look in this folder:- **/home/user/.local/share/radiotray**
Find the file "**config.xml**", re-name it "**config.xml.bak**".
Then launch RadioTray again (it will create a new config.xml file).

---

### Post by kizzyaggots on 2012-02-19
Hi mate, thanks for your help, i am in the xml folder but i cannot change the name. Is there a secret to changing the name?


                    Cheers Kizzy.

---

### Post by ron999 on 2012-02-19
> **kizzyaggots said:**
> Is there a secret to changing the name?

Right-click "Rename"
or
Right-click "Delete".

---

### Post by kizzyaggots on 2012-02-19
Yep tried both those options and they won't allow me to access the file name to change it sorry.

           Kizzy.

---

### Post by gordintoronto on 2012-02-19
What version of Ubuntu? What radio station?

You might need the "non-free codecs" from Medibuntu, which are not included in the restricted extras in some versions.

---

