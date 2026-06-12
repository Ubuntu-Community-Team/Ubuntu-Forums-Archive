---
title: "Keyboard  in Chinese"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by Rrory on 2012-02-04
Okay, I'm using Ocelot and wanted to start learning Chinese, so I fiddled around and tried installing stuff.

And now when I turn Ubuntu on it's in Chinese. And I don't understand the Chinese characters on how to return it back to English. Heelp! Please.

---

### Post by durand on 2012-02-04
Lets see if this works...:
Click on the icon in the top right corner (looks like a cog/power icon) of your desktop, then on the first item in the menu. Next, click on the icon that look like a blue flag. You might get a message popping up asking you to download more packages for that language. Click on the non-highlighted button (left) to ignore that for now. Once the languages window opens, you should see a list. Find English and drag it to the top of the list. Click the button at the bottom right of the window and log out and back in by clicking on the top right cog icon again and selecting the third item from the bottom. Finally, click on the highlighted button when a message pops up.
Everything should be back to normal after that :S

EDIT: I converted mine to Japanese to test out these steps and discovered a few more details.

---

### Post by Rrory on 2012-02-04
Gosh you're a lifesaver! It worked like a charm, English is back. And stupidly I forgot to say I had  Unity turned off, but the cog icons were there & your instructions first rate:KS

Is there an article anywere on input of Chinese & Japanese for Ocelot? As I'd like to try but now I'm pretty nervous.

---

### Post by durand on 2012-02-05
Glad it worked :) It is pretty simple to use both. What you did was change the language for applications to chinese when you actually just want to input chinese.

1.click dash home, search for "language support"

2.click "install/remove language" and add Chinese

3.click dash home, search for "keyboard input method"

4.under "input method",add Chinese input method

[http://askubuntu.com/questions/59356/how-do-i-get-chinese-input-to-work](http://askubuntu.com/questions/59356/how-do-i-get-chinese-input-to-work)

Then you probably need to logout and back again. Finally, to switch between english and chinese input, you just press Ctrl + Space and you'll see the keyboard icon on the top right change to chinese input. Now you can type in chinese and if you want to switch back, use Ctrl + Space again.

Hope that helps

---

### Post by oldschool29 on 2012-02-10
Hi, the same thing happened to me last night! What are the odds huh?   My question is this. I've tried the same manuever, (changing language and text in system) but when i go to the installed langauges i mostly get what looks to be a lot of variations on Mandarin (Chinese) but no English.   Somehow i seem to have messed up my langauge database. Is there some way to re-install English again? Any help would be very much appreciated.

---

### Post by durand on 2012-02-10
Two buttons below that list should be a button to install new languages. Click on that, tick the English option in the list and click on the button on the right hand side at the bottom. That should install the english packs again for you. If you need any more help, just ask :)

---

### Post by oldschool29 on 2012-02-10
Hey Durand, thanks for the reply! Are you talking about the INSTALL/REMOVE LANGUAGES button? When i click on this english and most other languages have been removed. i've really managed to foul things up Haha!!    I was wondering if maybe there is some package in synaptic or such that would make english available again in the INSTALL/REMOVE LANGUAGE option? Thanks again for any heads up here.

---

### Post by oldschool29 on 2012-02-10
Well, this is frustrating. I found "language-pack-en" in synaptic and installed them, and now i'm getting English (US) at the top of the list and bottom of available languages. when i try the bottom button "install/remove" though english isn't available though. i'm going to try a reboot i guess.

Nevermind, i got it working. Would not have happened without the info you gave earlier though so Thank You!

---

### Post by durand on 2012-02-11
Yeah, not sure what happened there. Glad you got it working :)

---

### Post by Rrory on 2012-02-14
Durand; 
 I was sick, but today I finally installed Chinese and Japanese via your directions. It was really easy, though, under 'keyboard input method system' you must choose 'ibus'  

It works like a charm, in 2 secs I was typing in Mandarin and then Japanese.
many thanks!:KS
Rory

---

### Post by Rrory on 2012-03-27
Now I think my language bar is broken. I needed to add Maori for the macrons as I'm working on a Latin book.

 Did so but I can't access this. I then tried to access the other european languages I previously added: french & German. I couldn't.
  I then turned Ibus off & took out the Japanese and Chinese. Chinese & Japanese still appear on my language bar.

is the language bar broken or am I doing something wrong? :confused:
heeelp I need those macrons
rory

---

### Post by durand on 2012-03-27
Hey, I won't be able to try it until the evening because I'm not near my laptop. That said, I have a few ideas:
1) Try restarting (I'm sure you've already tried this but worth mentioning)
2) Delete/move the ibus config from ~/.config/ibus and try adding the languags again
3) If you only need a few characters, you could try using a character bar instead: [http://askubuntu.com/questions/30334/what-application-indicators-are-available/52281#52281](http://askubuntu.com/questions/30334/what-application-indicators-are-available/52281#52281)

Hope that helps!

---

### Post by Rrory on 2012-03-27
1. I had restarted, no change (no problem reminding me)

2. what is the delete instruction for Python, as when I typed ~/.config/ibus  I got 'this is a directory'

3. I need my principal research languages too: French, German, Italian, Russian.

gosh I feel a bit sick I broke my language bar....

---

### Post by durand on 2012-03-28
Sorry, I completely forgot to check when I got back home :( To delete the config folder, just open the file manager, press Ctrl H and find the .config folder in your home and delete the ibus folder inside it. Or you can open a terminal and type in ```
rm -rf ~/.config/ibus
```

---

### Post by Rrory on 2012-03-29
Durand; you're a god! I pasted the code in the terminal, rebooted and
it worked.
gr&#257;tias tibi ag&#333;!
 ):P grateful rory

---

### Post by durand on 2012-03-29
Ah, good! Hope it doesn't happen again :)

---

