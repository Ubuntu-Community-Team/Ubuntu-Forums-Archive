---
title: "How to Create Custom Resolution *.sh for My display info ..."
date: 2015-06-30
forum: New to Ubuntu
---

### Post by limsruntek on 2015-06-30
Hi ! every i'm using lubuntu now and it was better and way too fast but only problem that concern me is display resolution i have nvidia server setting but the settings was gone after restart here my display res :
DISPLAY FOR FIX :
ViewPortIn : 1593x1049
VIewPortOut : 1593x1049+85+0
panning : 1593x1049

THZ IF YOU CAN HELP ME I MEAN THIS IS NOT SO SERIOUS FOR U USED TO HAVE LINUX ):P

---

### Post by Bucky Ball on 2015-06-30
Welcome. Install arandr (Software Centre), launch it and tweak with that. Enter the correct settings and see if it hold them. 

When you have the screens set up the way you want, you can save the setup as a bash file very easily via the interface (File> Save). If it breaks again, simply launch arandr and open that file.

I created a launcher using arandr's script so when I click, I get only one screen of two. Sure you could do the same for your resolutions. Get them right, save the setup, open the script arandr produces and have a look.

---

### Post by limsruntek on 2015-06-30
Hi bro why there is no khmer,central in ibus input ? but i can see it in language support anyway to install

---

### Post by Bucky Ball on 2015-06-30
Sorry, don't see how this relates to your original support request. Please post a new thread for any issues other than getting your resolution working. Just causes confusion mixing support requests on one thread and dilutes community effort. Thanks. :)

---

### Post by buzzingrobot on 2015-07-01
It's unclear, but if you are using the Nvidia proprietary driver, you should also have the Nvidia Settings tool installed. That allows you to write configuration changes to a file that will be reloaded on restart.

---

