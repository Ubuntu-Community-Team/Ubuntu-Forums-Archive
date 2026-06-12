---
title: "Cannot copy the words to the root shell!"
date: 2012-12-24
forum: New to Ubuntu
---

### Post by infernoking3 on 2012-12-24
I am really newbie about these topics guys.I have installed ubuntu for wireless password you know...I read the topic then did everyhing but I stuck somwhere.Ubuntu did not find my wireless chip.When I type iwconfig it says no wireless extensions.And my main problem is starting here.I searched internet about this error.I found solutions but I cant type the commands to ubuntu.CTRL+C doesnt work at all.I think I need to learn how to copy/paste first.I cant go further without copy paster.
Thanks for you help.):P

---

### Post by haqking on 2012-12-24
> **infernoking3 said:**
> I am really newbie about these topics guys.I have installed ubuntu for wireless password you know...I read the topic then did everyhing but I stuck somwhere.Ubuntu did not find my wireless chip.When I type iwconfig it says no wireless extensions.And my main problem is starting here.I searched internet about this error.I found solutions but I cant type the commands to ubuntu.CTRL+C doesnt work at all.I think I need to learn how to copy/paste first.I cant go further without copy paster.
Thanks for you help.):P

copy and paste with your mouse or use edit menu in the terminal.

Of course you could always type what you see, in the time you typed this post you could of manually typed the commands you needed ;-)

Peace

---

### Post by doja on 2012-12-24
in terminal ctl+c doesn't work. Use right mouse click and then choose copy and paste.

Maybe there is better solution but I'm also no expert

---

### Post by infernoking3 on 2012-12-24
right click doesnt work in root shell screen what should I do ?

---

### Post by infernoking3 on 2012-12-24
> **haqking said:**
> copy and paste with your mouse or use edit menu in the terminal.

Of course you could always type what you see, in the time you typed this post you could of manually typed the commands you needed ;-)

Peace
I tried to write all commands via my hands.But I geting error.For example some code says ...apt-get... when I type that it says apt-get not found ..

---

### Post by haqking on 2012-12-24
> **infernoking3 said:**
> right click doesnt work in root shell screen what should I do ?

Edit menu.

And why are you using a root shell, if you need elevated privelege use sudo for your commands

---

### Post by doja on 2012-12-24
yes, sudo is a kind of magic command ;).
I made my own experience.

---

### Post by snowpine on 2012-12-24
Why not take a deep breath and step back, then tell us what you are trying to accomplish and what steps you have tried so far... we can (hopefully) teach you a safe and easy way to accomplish the task... for example applications can be installed with a few mouse clicks from the Software Center, no need to mess around with apt-get in the shell if you are uncomfortable. :)

---

### Post by infernoking3 on 2012-12-24
> **snowpine said:**
> Why not take a deep breath and step back, then tell us what you are trying to accomplish and what steps you have tried so far... we can (hopefully) teach you a safe and easy way to accomplish the task. :)
So I want to use feeding bottle tool.When I use feeding bottle it doesnt notice my wireless card.Everyhing says N/A at select wireless card screen.So I cant go further.Then some said type iwconfig at the root shell.I did and I received no wireless extensions error.
afther that message I searched internet.People sadi they found the solution but I cant copy and paster their commands to my ubuntu.Thats the problem.
So ubuntu doesnt found my wireless card what should I do for make it find my wireless chip.

---

### Post by snowpine on 2012-12-24
Here's a guide to troubleshooting wireless in Ubuntu: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

In particular I think you should read this: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices)

Once you have identified your device then I recommend you start a new thread with your specific device and brief description of the problem in the thread title. :)

**Please don't** blindly copy & paste terminal commands you found on some website into your root terminal. :) 

That being said, the keyboard shortcuts to copy & paste in terminal are Ctrl+Shift+C and Ctrl+Shift+V (or middle click of the mouse).... use this knowledge wisely, grasshopper! :)

---

### Post by snowpine on 2012-12-24
ps I have no idea what is "feeding bottle tool"---is this some kind of supported software from Ubuntu?

---

### Post by infernoking3 on 2012-12-24
> **snowpine said:**
> Here's a guide to troubleshooting wireless in Ubuntu: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

In particular I think you should read this: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices)

Once you have identified your device then I recommend you start a new thread with your specific device and brief description of the problem in the thread title. :)

**Please don't** blindly copy & paste terminal commands you found on some website into your root terminal. :) 

That being said, the keyboard shortcuts to copy & paste in terminal are Ctrl+Shift+C and Ctrl+Shift+V (or middle click of the mouse).... use this knowledge wisely, grasshopper! :)
all the commands was from this site.And I tried ctrl+shift+c but it is still doesnt work.Souns like I am damned or somethings very wrong.

---

### Post by snowpine on 2012-12-24
> **infernoking3 said:**
> all the commands was from this site.And I tried ctrl+shift+c but it is still doesnt work.Souns like I am damned or somethings very wrong.

Anyone can post on this site, there is no intelligence test to post here, you'll get good advice and bad advice. :)

Which terminal app are you using? (gnome-terminal, xterm, something different) Have you tried middle-click yet?

Anyway without knowing your wireless card (or what "feeding bottle tool" is) I can't offer any advice, sorry.

---

### Post by deadflowr on 2012-12-24
> **snowpine said:**
> ps I have no idea what is "feeding bottle tool"---is this some kind of supported software from Ubuntu?

Seems to be a wifi cracking tool.
Might be wrong though.

---

### Post by snowpine on 2012-12-24
> **deadflowr said:**
> Seems to be a wifi cracking tool.
Might be wrong though.

Good luck with that, infernoking---I'm out of here. :(

---

### Post by infernoking3 on 2012-12-24
> **snowpine said:**
> Anyone can post on this site, there is no intelligence test to post here, you'll get good advice and bad advice. :)

Which terminal app are you using? (gnome-terminal, xterm, something different) Have you tried middle-click yet?

Anyway without knowing your wireless card (or what "feeding bottle tool" is) I can't offer any advice, sorry.Ok I forgot about the copy paste.I read your recent link and typed nm-tool to my terminal but it said "not found".First time I thought I typing wrong but now I am sure it is right but still says not found.

---

### Post by doja on 2012-12-24
> **snowpine said:**
> the keyboard shortcuts to copy & paste in terminal are Ctrl+Shift+C and Ctrl+Shift+V 

thanks, snowpine
again a bit wiser. ;)

actually  the shortcut is shown under edit I don't know why I never looked there for this.

---

### Post by haqking on 2012-12-24
> **infernoking3 said:**
> So I want to use feeding bottle tool.When I use feeding bottle it doesnt notice my wireless card.Everyhing says N/A at select wireless card screen.So I cant go further.Then some said type iwconfig at the root shell.I did and I received no wireless extensions error.
afther that message I searched internet.People sadi they found the solution but I cant copy and paster their commands to my ubuntu.Thats the problem.
So ubuntu doesnt found my wireless card what should I do for make it find my wireless chip.

aircrack is not supported in this forum so be careful what you ask ;-)

Peace

---

### Post by sffvba[e0rt on 2012-12-24
AS the original issue about copying and pasting in terminals have been solved and the rest is about a questionable topic (air-crack) this thread is now **closed**.


404

---

