---
title: "How to disable login password sound?"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by paker on 2013-05-07
12.04 LTS, upgraded from 10.04 LTS
I just cannot get rid of this sound that broadcasts my password as I type it. I searched this forum and internet. Removed sound from "Startup". No effect. Please help. "Sound" doesn't have event sound. Thanks.

PS: If it is something I cannot get rid of, what can be the usefulness of this feature?

---

### Post by DuckHook on 2013-05-07
This is a new one to me. Never heard of it before. Do you mean to say that your computer plays a tone with each password character that you type and every time that you type it? If I'm not getting it, please clarify.

---

### Post by paker on 2013-05-07
Yes, exactly as you said, each character verbalized.

---

### Post by Lightning Dragon on 2013-05-07
Hi,

You need to disable Screen Reader on the top right of the screen. It looks like this;

[IMG]http://s4.postimg.org/rdozzti9p/lightdm_unity_greeter_ubuntu12_04_precise.png[/IMG]

I can think of a few reasons why the feature would be useful; if your keyboard keys lost their "letter" and you can't tell what is what. Another reason for it could to test if your keyboard is fried and "Y", for example", actually prints out "Y". I can't think of much else, though.

---

### Post by paker on 2013-05-07
> **Lightning Dragon said:**
> .........You need to disable Screen Reader on the top right of the screen.........
Thanks for the lead. I disabled Screen Reader in Universal Access. Then I rebooted. Screen Reader was reactivated. I needed a permanent disable.

I searched internet. 2 ways: either to remove screen reader (Orca) completely or disable Orca from Startup. My mouse (right button) is misbehaving and I cannot copy/paste links. Search for "disable orca" or "disable screen reader." 

Thank you again for leading me in the right direction. "screen reader" was the key word.

---

### Post by Lightning Dragon on 2013-05-07
Hi,

Ah! That is weird...If you haven't already found the solution, please try the following;

[http://askubuntu.com/questions/81960/how-do-i-stop-orca-from-starting-up-on-login](http://askubuntu.com/questions/81960/how-do-i-stop-orca-from-starting-up-on-login)

You can also try this link, though I would only advise it as the last resort option;

[http://www.hecticgeek.com/2012/06/few-things-to-speed-up-ubuntu/](http://www.hecticgeek.com/2012/06/few-things-to-speed-up-ubuntu/)

---

### Post by black veils on 2013-05-10
i remember someone having the same problem, just uninstall "espeak" if you dont need any speech synthesizer features on your system, i also had a similar issue and did the same.

---

### Post by Frogs Hair on 2013-05-10
Remove Orca from start up applications if it appears there. It's a nice application for the visually impaired if needed.

---

