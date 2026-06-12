---
title: "Text on websites is too light to read"
date: 2021-10-08
forum: New to Ubuntu
---

### Post by mimosa8 on 2021-10-08
New to using Linux and Ubuntu and feel so frustrated!

Any time I go to a website, the text is so pale it is hard to read. Why is this? What do I need to adjust? I really don't want to go back to using Windows 10.

Any help appreciated.

---

### Post by ajgreeny on 2021-10-08
All websites or just a few?
Give us an example and if possible add a screenshot of the problem.
Please use the attachment facility to add a screenshot.  You can create a screenshot by hitting the PntSc/SysRq key, saving the image to disk.
Click on the paperclip icon in the Reply to Thread toolbar, navigate to the screenshot from the Browse button, click Upload and the image will then appear in your post.
Bear in mind that the problem could be more related to your screen settings than actually being a problem, but let's try things one by one.

---

### Post by coffeecat on 2021-10-08
> **mimosa8 said:**
> 
Any time I go to a website, the text is so pale it is hard to read.

That is not a feature of Ubuntu. I can't remember an occasion in 15+ years' use of Ubuntu where that was a issue for me. Perhaps if you post a link to a website whose text is too pale for you, forum members could check it on their systems and possibly get a hint of what might be the problem.

---

### Post by ActionParsnip on 2021-10-08
What browser(s) have you tried?
Do you have addons/extensions in the browser which my cause this?
If you make a new Ubuntu user and log in as that, do the websites display OK?

---

### Post by mimosa8 on 2021-10-08
Can't even figure out how to make a screenshot.
But the text is pale on all websites that I go to.

---

### Post by QIII on 2021-10-08
As was asked before:  Which browser are you using?

This is almost certainly a browser setting.

---

### Post by T6&amp;sfpER35% on 2021-10-08
if the text is fine on the rest of the system ,and only pale on websites, then it's something with the browser you are using which is probably Firefox since you say your'e new and i doubt you installed other browsers.
try running this command in terminal```
sudo apt install  ttf-mscorefonts-installer
``` when you get to the "agreement" page the mouse won't work ,use the right arrow to navigate to <ok> and next screen again arrow keys to <ok>

also have a look [here]("https://askubuntu.com/questions/21030/font-rendering-in-firefox-is-blurry")

have you updated anything since the install? run this command ```
[COLOR=#000000][FONT=&amp]sudo apt update[/FONT][/COLOR]
```
see if it helps

---

### Post by mimosa8 on 2021-10-09
Sorry for the delay in responding everyone. Had to go do something else that took up all evening.
Thank you for your reply. I typed in the first command and got this:
Reading package lists... Done
Building dependency tree... Done
Reading state information...Done
ttf-mscorefonts-installer is already the newest version (3.8ubuntu2).
ttf-mscorefonts-installer set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I never saw an agreement page.

I ran the sudo apt update and it said All Packages are up to date.

There doesn't seem to be any difference in the way web pages display test. i.e. still too light to be easily readable.

---

### Post by mimosa8 on 2021-10-09
Sorry for the delay, had to leave for the rest of the evening.


I am using Firefox. What browsers are recommended?

---

### Post by coffeecat on 2021-10-09
> **mimosa8 said:**
> What browsers are recommended?

Firefox.

Firefox is fine and I do not see too-pale text. You have been asked whether you have any browser extensions/addons, but you have not answered. You were also asked to provide screenshots, but you merely stated that you couldn't figure out how to take a screenshot. It's not difficult. If you can't work it out, ask how. And I asked you to provide a link or links to websites where you find the text too pale, but you ignored that request.

if you don't provide the information that is asked for, it is unreasonable to expect forum members to be able to help you.

---

### Post by mimosa8 on 2021-10-09
My apologies for the late reply. I had to be away from my computer all evening yesterday.

Here is a screenshot:

[IMG]x-special/nautilus-clipboard copy file:///home/linix/Pictures/Screenshot%20from%202021-10-09%2014-50-25.png[/IMG]

Here is another:

[IMG]x-special/nautilus-clipboard copy file:///home/linix/Pictures/Screenshot%20from%202021-10-09%2015-04-16.png[/IMG]

I don't know if I have other browser extensions or addons. I am a newbie to Ubuntu.

Hope this clarifies the situation.

---

### Post by walts48 on 2021-10-09
You might want to try the [https://addons.mozilla.org/en-US/firefox/addon/darkreader/]("https://addons.mozilla.org/en-US/firefox/addon/darkreader/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search") extension.

---

### Post by T6&amp;sfpER35% on 2021-10-09
> [COLOR=#000000]ttf-mscorefonts-installer is already the newest version (3.8ubuntu2).[/COLOR]
ok so it was already installed ,hence you won't see an agreement page to install it

pls post the requests from coffeecat

you could try another browser and then will definitely know if its the browser or something else 
any browser will do ...chrome , brave , Vivaldi 
me personally only use brave
[https://brave.com/linux/](https://brave.com/linux/)

---

### Post by T6&amp;sfpER35% on 2021-10-09
your screenshots isn't showing
go to the **advance tab** at bottom right of text box , then press the little attachment icon at the toolbars
go to **add file** then **choose file **then **insert inline** and** done**

---

### Post by T6&amp;sfpER35% on 2021-10-09
> [COLOR=#000000]I don't know if I have other browser extensions or addons[/COLOR]
in firefox click the little 3 bars on top right corner and go to **add-ons and themes** , there you'll see extensions and plugins

---

### Post by ActionParsnip on 2021-10-09
> **mimosa8 said:**
> Sorry for the delay, had to leave for the rest of the evening.


I am using Firefox. What browsers are recommended?

Try Chrome. See if it's different there

---

### Post by Impavidus on 2021-10-09
I wouldn't expect ttf-mscorefonts-installer to make a difference. I've never had that installed and never had any such problems with Firefox.

You shouldn't need specific themes or extensions to fix this. This problem shouldn't occur if you had no themes or extensions installed.

There should be no need for a different browser. Every browser can do this correctly.

What you could try is starting Firefox with a fresh firefox profile. I guess the problem is some setting in your profile. You could try this by starting Firefox from a terminal with the command **firefox -P**. That will start Firefox with the profile manager, where you can create a new profile. This won't have your extensions, favourites, browse history etc. It basically resets Firefox to defaults. The same way, you can delete profiles.

Or you could just try and fix this with your current profile. Try the Edit ->Settings menu in Firefox, or use the address bar to navigate to about:preferences. The general settings should have something about fonts and colours. Maybe you have to fix that.

---

### Post by mimosa8 on 2021-10-09
testing screenshot

---

### Post by mimosa8 on 2021-10-09
Thank you for the suggestion. I tried it but really could not see that it changed anything.

I also tried the Brave browser with no difference.

Failed at trying to get a decent screenshot after trying various methods.

The interface for Ubuntu is difficult to understand.

Honestly, I am feeling discouraged.

---

### Post by ajgreeny on 2021-10-09
Your screenshot looks quite normal to me.
What about the text if you open the attachment looks pale to ýou in that mouse settings dialogue?

That screenshot is not, however, a website which would have made more sense.

---

### Post by T6&amp;sfpER35% on 2021-10-09
is everything on your system like that or only on websites through whatever browser ??

---

### Post by tea for one on 2021-10-09
Your screenshot in Post 18 displays the Ubuntu Forums website beneath the Ubuntu Settings window.

The Ubuntu Forums web page is legible (i.e. the text is not pale or difficult to read).

---

### Post by T6&amp;sfpER35% on 2021-10-09
only notices that now too ...what gives ?

---

### Post by tea for one on 2021-10-09
> **3nd said:**
> only notices that now too ...what gives ?

And **The South African** plays the starring role........(in the screenshot)

---

### Post by jim Kane on 2021-10-09
have you tried having play with the fonts and sizes

---

### Post by kurt18947 on 2021-10-10
> **mimosa8 said:**
> Thank you for the suggestion. I tried it but really could not see that it changed anything.

I also tried the Brave browser with no difference.

Failed at trying to get a decent screenshot after trying various methods.

The interface for Ubuntu is difficult to understand.

Honestly, I am feeling discouraged.

Use the same procedure as you used to get the image shown above but do it with a problematic web page on the screen. It's typical to feel frustrated when starting with something unfamiliar. Hang in there.

---

### Post by T6&amp;sfpER35% on 2021-10-10
> [COLOR=#000000]And [/COLOR]**The South African ****plays the starring role**

retreats from trying to help in any form

---

### Post by tea for one on 2021-10-10
> **3nd said:**
> retreats from trying to help in any form

Apologies if my post appeared sarcastic or derisive - certainly not my intention.
I was only pointing out (in a clumsy way) that your avatar was clearly visible in the OP's screenshot.

---

### Post by pantazi on 2021-10-10
I use dark mode in the Brave browser, very clear using your settings screenshot example.

---

### Post by T6&amp;sfpER35% on 2021-10-11
> [COLOR=#000000]your avatar was clearly visible in the OP's screenshot.[/COLOR]
:cool: it's all good , i prematurely jumped on my high horse , sorry :)

---

### Post by michael-hi on 2021-10-17
I too find pale text on websites a problem. Website designers seem to favour grey text instead of a proper black and this makes the page tiring to read, especially if your eyesight is not the best. I suppose web designers tend to be younger people with good eyesight and good computer screens (not entry-level laptops). One solution is to go to "Add-ons and Themes" in the Firefox menu and install the extension Blacken. I find this works well. It may sometimes slow down big webpages with lots of text but you could turn it off if this happens.

---

### Post by psychohermit on 2021-10-21
To take a screenshot hit the PrintScreen button.  When I did it it put the image in my Pictures folder.  --glenn

---

