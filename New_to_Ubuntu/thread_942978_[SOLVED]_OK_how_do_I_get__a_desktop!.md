---
title: "[SOLVED] OK how do I get  a desktop!"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by eddiemec on 2008-10-09
All I hear is how neat Linux is; when I open  windows I get a nice gui that even an idiot can traverse. I download ubuntu and it installs; even gives me a choice at boot up, Windowsxp, MSDos, and Ubuntu. Ubuntu opens with a command line; I don't want a command line, I want KDE or Gnome something that I can relate to. I see Linux as an elitist group. Just simply show me how Ubuntu can work simply. A while ago I installed Mandriva and it worked; maybe I should go back there.

---

### Post by SunnyRabbiera on 2008-10-09
Woa, woa hold on a sec.
No need to be hostile here, I know you might be frustrated but please dont come in here with an attitude and expect help.
Can you give us full details on your ubuntu install?
Did you encounter errors and did you check your installer CD for defects?

---

### Post by damis648 on 2008-10-09
Also, could you might have accidentally installed the Server Edition?

---

### Post by tjwoosta on 2008-10-09
did you install the server edition?

---

### Post by Big_Kahunaca on 2008-10-09
When it opens to the command line, after you login with the username/password that you setup during the installation, can you type "startx".  

If that doesn't work can you post the results?

---

### Post by jerome1232 on 2008-10-09
> **eddiemec said:**
> All I hear is how neat Linux is; when I open  windows I get a nice gui that even an idiot can traverse. I download ubuntu and it installs; even gives me a choice at boot up, Windowsxp, MSDos, and Ubuntu. Ubuntu opens with a command line; I don't want a command line, I want KDE or Gnome something that I can relate to. I see Linux as an elitist group. Just simply show me how Ubuntu can work simply. A while ago I installed Mandriva and it worked; maybe I should go back there.

Now that your done with your rant maybe you can provide some useful info so we can help you with the problem

What version did you try to install, did you verify the integrity of the download, and did you verify the integrity of the burnt disc?

What does the command line your looking at look like? Does it have any errors you can see?

---

### Post by damis648 on 2008-10-09
Yes. Okay in short, the info we need is:

1. Which version, server or desktop? Did you check the integrity?

2. What does the prompt look like? Does it declare itself as BusyBox and the prompt is
```
(initramfs)
```
or does it ask for a username and password?

---

### Post by eddiemec on 2008-10-09
> **Big_Kahunaca said:**
> When it opens to the command line, after you login with the username/password that you setup during the installation, can you type "startx".  

If that doesn't work can you post the results?
startx is not an option; there is a restricted number of commands

---

### Post by eddiemec on 2008-10-09
> **damis648 said:**
> Yes. Okay in short, the info we need is:

1. Which version, server or desktop? Did you check the integrity?

2. What does the prompt look like? Does it declare itself as BusyBox and the prompt is
```
(initramfs)
```
or does it ask for a username and password?

That's what it looks like. Ubuntu 8.04 desktop

---

### Post by damis648 on 2008-10-09
Okay. Now, at the boot menu, highlight the Ubuntu option and press "e". Now go down to the second line and press "e" again. Use backspace to remove the two words at the end of the line "quiet" and "splash". Now press enter and then press "b". When you see the BusyBox prompt again, look for errors right before it. Tell us what it said right before you got the BusyBox.

---

