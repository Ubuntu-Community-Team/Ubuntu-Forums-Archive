---
title: "Beryl on Huron?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by eladriano on 2008-04-24
So I'm totally new to linux. At school we have beryl on the computers which I find really cool.  I tried to install it on ubuntu Hardy Huron but it fought with the other ui program (compiz I think it's called?) and I lost my minimize/maximize/exit buttons. Beryl did work though. I searched some forums to figure out how to get my buttons back. I found some command that did it but I lost the functionality of beryl. So I decided to just reinstall ubuntu(so easy now through windows :). Can someone tell me/point me in the direction of the proper procedure of installing beryl? Thanks.

---

### Post by Joeb454 on 2008-04-24
Beryl is unsupported.

Open up synaptic, or add remove, and search for compizconfig-settings-manager :)

It'll then appear in System>Preferences :) Compiz-Fusion is the merge of Compiz and Beryl :D

Hope this helps

---

### Post by Paqman on 2008-04-24
You already have it. Compiz is Beryl (it's complicated)

To enable desktop effects, make sure you have drivers for your graphics card (System > Admin > Hardware Drivers) then go into Appearance and enable desktop effects.

---

### Post by rouge568 on 2008-04-24
Sorry to burst your bubble, but beryl is now obsolete, replaced by compiz. (compiz is actually a merge of beryl and a previous compiz; it's a little confusing) Don't worry, however. Compiz has all the same and even more goodies than beryl does, including the spinning cube, falling snow, water effects, wobbly windows, and a whole lot more. Plus, you will gain the ability to install Avant Window Navigator, which is a very slick mac-like dock, and screenlets, which is a widget program. 

To use compiz, you will want to install compizconfig-settings-manager. ```
sudo apt-get install compizconfig-settings-manager
``` This is located under System>Preferences>Advanced_Desktop_Settings. From there, you can configure how compiz will work for you.

Before you do all of this, however, you want to make sure that you have all your drivers installed. Go to System>Administration>Hardware_Drivers (if you are using anything other than 8.04, this will be Restricted_Drivers_Manager). Make sure that all of them are enabled, and you can now use compiz!

To run compiz, open up a terminal and type in 'compiz --replace'. If it starts, great! You can now have it start at boot. As a precaution, go to the compiz settings manager and enable the crash handler. Check off the "start other window manager" box and put the command as 'metacity --replace'. Now you have a fall-back in case anything messes up. If compiz doesn't start up, post any error outputs here so we can help you. 

To get compiz to start automatically at boot, go to System>Preferences>Sessions. Add a new process and have the command be 'compiz --replace'.

Let me know how this works out, and have fun!

---

### Post by eladriano on 2008-04-24
> **Joeb454 said:**
> Beryl is unsupported.

Open up synaptic, or add remove, and search for compizconfig-settings-manager :)

It'll then appear in System>Preferences :) Compiz-Fusion is the merge of Compiz and Beryl :D

Hope this helps

Awesome thanks so much!:)

---

### Post by Joeb454 on 2008-04-24
> **Paqman said:**
> You already have it. Compiz is Beryl (it's complicated)

I tried to explain it as well as I could :)

---

### Post by eladriano on 2008-04-25
*Edit* Nvm I just tried again and it worked!

Thanks so much rouge568 that was very informative and very much appreciated.  I'm having a problem downloading the compiz manager I do that command and then I get an error connecting to the server (ca.archive.ubuntu.com (129.97.134.71) Now I'm guessing this is because the servers are getting hit hard do to Huron's release. Are there any mirrors or other repos I could use to get the compiz manager?

---

### Post by SunnyRabbiera on 2008-04-25
> **Paqman said:**
> You already have it. Compiz is Beryl (it's complicated)

To enable desktop effects, make sure you have drivers for your graphics card (System > Admin > Hardware Drivers) then go into Appearance and enable desktop effects.

My card works right away actually... never had a problem with it.

---

### Post by Paqman on 2008-04-25
> **eladriano said:**
> Are there any mirrors or other repos I could use to get the compiz manager?

You could always try switching to another country's servers (System > Admin > Software sources)

---

