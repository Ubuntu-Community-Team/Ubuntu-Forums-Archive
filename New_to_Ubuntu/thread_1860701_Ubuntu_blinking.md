---
title: "Ubuntu blinking"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by lorddenis on 2011-10-15
So after olmost 2 years i decides to give Ubunto another go and it didnt go as planed. A friend of mine instaled a dual boot on my PC. Win 7 works fine. But when i want to run Ubunto (i told him to instal the newest version.) it doesn work fine.

 After i choose ubunto in the boot menu it shows a ubunto backround with i think 5 stars under it. and then it starts to blink meanin the screan becomes black and then again to the backround. It does that a fev times and then the desktop backround shows with out any thing else besides the mouse pointer. Then it again blink's a fev times and after a fev blink's the** left menu bar show's. **and then it contonues blinking. The bold part hapent when i first tried running it. meanin i didnt see the upper menu. The second time evrything was the same only i saw the upper menu first and later after a few blink's the left one. I clicked on the upper left button to open the menu. After a fev blink's i got this:
[http://toastytech.com/guis/ubuntu114dash.png](http://toastytech.com/guis/ubuntu114dash.png)
(Found the pic on google.) But only that what i clicked. the upper and left menu dissapeared. 

My friend say's he has tested after it instaled and it worked fine. He think its the refreshing of the screan. The pc has a 24 inch samsung.

Does anyone know what to do ?

i shuld mention that in the booting screan i saw  ubunto linox (save or somthing like that). when i tried that it was for inserting code. and there was also a save screan. 

Have a nice day!

---

### Post by lorddenis on 2011-10-16
Anyone :confused:

---

### Post by Perfect Storm on 2011-10-16
Sounds like video driver issue. Which video card does it have?

---

### Post by lorddenis on 2011-10-16
> **Artificial Intelligence said:**
> Sounds like video driver issue. Which video card does it have?

Thank you for your replay.

Its  Ati radeon HD 5450.

---

### Post by Perfect Storm on 2011-10-16
Are you using Open Driver or restricted driver?

---

### Post by lorddenis on 2011-10-16
> **Artificial Intelligence said:**
> Are you using Open Driver or restricted driver?
What do you mean by that ? i googled restricted and found that those are the ones that need paying for ?

---

### Post by Perfect Storm on 2011-10-16
restricted = close source driver.

---

### Post by lorddenis on 2011-10-16
> **Artificial Intelligence said:**
> restricted = close source driver.
When in windows its open(have to instaled the drivers for the card). But as far as i know there is no connection betwen win and ubunto.

---

### Post by sadaruwan12 on 2011-10-16
It's a drivers issue as you have described it but my dear friend it seems like you don't know much about Linux and how it works.

What I would say is to before diving in to unknown waters do some research and educate your self after that when you feel comfortable come back.

No heart feelings

---

### Post by lorddenis on 2011-10-16
> **sadaruwan12 said:**
> It's a drivers issue as you have described it but my dear friend it seems like you don't know much about Linux and how it works.

What I would say is to before diving in to unknown waters do some research and educate your self after that when you feel comfortable come back.

No heart feelings
Thats true. Dont know anything about linux. Well i do know a fev thing's but nothing to complex.

Maybe your right. Maybe it was a mistake to want to try another operating system. I jsut wish they would have showed somthing else besides win in school.

---

### Post by sadaruwan12 on 2011-10-16
Yes, dear friend currently don't mess your set up just learn about linux there are lot of resources on the internet for free heres a [first step]("http://www.learninglinux.com/") for you if you're willing to learn it.

My advice to you the same thing happened to my they only show us the dumb system of windows but when we mature we see more at that point we see that windows is just a lie.

At that point you'll the light of Linux so prepare your self use the resources come under our wing we'll guide you but you've to do your own studying and thank you for using Ubuntu.

---

### Post by d4m1r on 2011-10-16
Burn a "LiveCD" of 11.10 (download the client 32bit version from ubuntu.com) and boot it on the PC.

Does everything work fine? It will basically test if your PC is the problem of the install. It will basically run Ubuntu off the CD.

---

### Post by mglennpooh on 2011-10-16
Canonical has an Agreement with Intel, Nvidia, ATI, et al for Driver Updates. I suspect the 3rd party & "restricted" options are turned off on your Software Sources ( which is a simplified replacement for the older Synaptic Packages Manager) - bring up this App, then, checkmark each such option, then, bring up Update Manager, then, click on CHECK to refresh the search cache to include the above mentioned options.

If this doesn't work then uninstall & reinstall as often as you need until it does. You need to expect missing or corrupt files via the Server due the overwhelming demand the 1st week following the new release date. 

If you did or can use a Wubi installer then download that plus the Desktop iso image to the same download folder. The Wubi will utilize the iso image instead of downloading the tar.xz file (which often fails when it swells up like a balloon during the installation process),

---

