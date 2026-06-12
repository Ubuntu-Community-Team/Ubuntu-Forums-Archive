---
title: "UBUNTU HOLD ALT key shortcut pop up"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by diabolusss on 2012-10-16
Hi there! 
 I want to change ubuntu shortcut pop up contents, however i can not find where it's stored. Any clues, please?

---

### Post by MG&amp;TL on 2012-10-17
> **diabolusss said:**
> Hi there! 
 I want to change ubuntu shortcut pop up contents, however i can not find where it's stored. Any clues, please?

Your question is a little vague. What exactly is it that you want to change? Keyboard shortcuts? What displays in the HUD?

Thanks, we'll hopefully be able to help if you give us a little more. :)

---

### Post by diabolusss on 2012-10-17
Sorry, i thought it would be clear enough. 
[IMG]https://dl.dropbox.com/u/33606473/Pictures/ubuntu_default_final_en.jpg[/IMG] 
I want to change the contents of that if it's possible, as i don't use a lot of them, but need another ones that are important.

PS. i have Precise Pangolin, however i have disabled that key somehow and i don't want to re-enable that if there is no chance to edit contents... so it's not mine pop up, but i hope now it's clear what about i am telling.

---

### Post by MG&amp;TL on 2012-10-17
> **diabolusss said:**
> Sorry, i thought it would be clear enough. 
I want to change the contents of that if it's possible, as i don't use a lot of them, but need another ones that are important.

PS. i have Precise Pangolin, however i have disabled that key somehow and i don't want to re-enable that if there is no chance to edit contents... so it's not mine pop up, but i hope now it's clear what about i am telling.

So...you want to change keyboard shortcuts? Head to the "keyboard" app, then click the "Shortcuts" tab. 

There might be some not accessible through there, though, so install the package *compizconfig-settings-manager* and run the application once installed. Then, click the button with "Ubuntu Unity" on it, and navigate through the dialog until you find what you want.

Hope that helps. :)

---

### Post by diabolusss on 2012-10-17
> **MG&TL said:**
> So...you want to change keyboard shortcuts? Head to the "keyboard" app, then click the "Shortcuts" tab. 
Thanks for reply! but nope xD i need to change a content of that pop up, e.g. to place my own text - commands, or everything else instead that is there. MAybe to place a pray there :guitar: So to conclude i want to pop up there what i set not default

---

### Post by MG&amp;TL on 2012-10-17
> **diabolusss said:**
> Thanks for reply! but nope xD i need to change a content of that pop up, e.g. to place my own text - commands, or everything else instead that is there. MAybe to place a pray there :guitar:
Ahah. Not a bad idea. ;)

Well, unfortunately, I believe you'll need to recompile and hack around with unity (the desktop environment) to do that.

If you're willing to do that:[ http://ubuntuforums.org/showthread.php?t=2049872]("http://ubuntuforums.org/showthread.php?t=2049872") -good luck!
If not: sorry. I don't know what else to suggest, really. :(

---

### Post by diabolusss on 2012-10-17
Anyway thanks for a quick reply and a good tip. I'll try that someday. Seems not too bad. :) but it's not portable. i mean that with new ubuntu reinstall i must re-do it and it's not my aim. one thing change files, another to re-build unity xD i'll be looking for another solution. maybe to map some keys to pop up window or picture, smth that i can store for future use.

PS i found the most simplest is to make shortcut that opens picture, and a half harder to make a binary that pops up and closes by click. maybe in future smth will change...

---

### Post by MG&amp;TL on 2012-10-17
> **diabolusss said:**
> Anyway thanks for a quick reply and a good tip. I'll try that someday. Seems not too bad. :) but it's not portable. i mean that with new ubuntu reinstall i must re-do it and it's not my aim. one thing change files, another to re-build unity xD i'll be looking for another solution. maybe to map some keys to pop up window or picture, smth that i can store for future use.

PS i found the most simplest is to make shortcut that opens picture, and a half harder to make a binary that pops up and closes by click. maybe in future smth will change...

That's true. And annoying. :)

If you're into programming, it would be quite a simple task (I'm thinking PyGTK here...just a suggestion). If not, your current solution is pretty good.

---

### Post by diabolusss on 2012-10-18
> **MG&TL said:**
> That's true. And annoying. :)

If you're into programming, it would be quite a simple task (I'm thinking PyGTK here...just a suggestion). If not, your current solution is pretty good.

Something like that. But there is nothing you can't learn, so thanks again for amazing tip.(i haven't thought about how to programm this, thorough, but the first thing that came upon me was magick++ as i remember there was window management, however it demands for a deeper research. I haven't worked with python, only c. now i remembered about x.org... another pain is how to make window be active only when keys are hold/active, not to toggle or close by click)

---

