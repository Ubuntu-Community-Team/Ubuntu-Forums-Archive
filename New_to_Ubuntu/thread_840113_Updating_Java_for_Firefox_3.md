---
title: "Updating Java for Firefox 3?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by deejaypip on 2008-06-25
So I feel like an idiot, but I've been trying for a solution for a long time to no avail.

I'm playing with wordle.net. 
Up until yesterday, it worked fine. Generated text, all that.
But now when I want to create new text, it says "starting applet," then "start: applet not initialized."
The FAQs for wordle.net tell me to update to the latest version of Java.

So... if you can help; that'd be great.
Thanks.

---

### Post by starcannon on 2008-06-25
open up synaptic package manager,

search for jre

if you need the latest then choose sun jave 6, if you need blackboard (a college website that totally sux monkey stuff) then you'll need sun java 5

If you have one of those installed already, then click on it and choose re-install. see if that gets you rolling.

GL

---

### Post by deejaypip on 2008-06-25
Thanks!
My school does use blackboard, so I installed 5 also. Thanks for that heads-up.

---

### Post by starcannon on 2008-07-04
Your eventually going to run into a professor or online class that uses Real Media as well so be sure to go here and get the closed source version (the open source version doesn't work)

[http://www.real.com/linux](http://www.real.com/linux)

Use the Gold "Download RealPlayer" Button.

Or click this link if you want.
[Download RealPlayer]("http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin")

Save the file to your Desktop.

Open a terminal in the Desktop Directory:

```
cd ~/Desktop
```

Make it executable:
```
sudo chmod a+x ./Real*.bin
```

Install it:
```
./Real*.bin
```

Test it out:
[http://www.slp3d2.com/launchsiteglobal/test.cfm](http://www.slp3d2.com/launchsiteglobal/test.cfm)

GL you may have to mess with it a bit, play around with the preferences, and force firefox to use Real Media Player instead of Totem, I might take some time and write a guide if one doesn't already exist.

---

### Post by silkstone on 2008-07-04
Not sure if there's a guide here, but there's one in the wiki that worked for me...

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_Real_Player_11_and_Configuring_Mozilla_Plugin)

---

