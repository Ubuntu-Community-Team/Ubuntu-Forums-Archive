---
title: "Installing Ubuntu"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by asw1asw on 2013-04-27
Hi,completly new to Linux, Ubuntu etc, but love the look the flexibility and want to learn, I have a few questions but mainly I brought home from work a ibm xseries x335 server which was going in the bin, this works great, well it fires up and I can load software to it, currently have xubuntu 12.04 on there however what I am aiming to do is setup a little home server which can be my domain for all my pc's but also stream music and movies etc, so I was going to install ubunto server but I struggle as I just get a black screen after the install with the words out of range, I have an old p4 3.06ghz pc with 200gb hdd which I have been using to experiment installing software, I have tried both the server edition and desktop Ubuntu 12.04 both of which do not seem to work as I get the out of range issue again, anyway, having tried for days to get working I have tried to install the new ubunto desktop 13.04 which seems to have gone all good, after the install the screen came back on and all looked good, a desktop background also appeared so I thought this was a good sign but that's it, nothing else has happened, no icons or desktop features as per the Ubuntu site, I can right click an add say a folder or change background settings which from there I can access the desktop settings to change screen resolution which I thought was the issue but its not, so I give in, its loaded and sat there but I have no idea on how to use it and what to do next, I have had no problem warnings come up or any other issue arise? please help !! thanks andrew

---

### Post by ibjsb4 on 2013-04-27
How much ram you have?

And no way that your onboard graphics going to run Unity.  Add Gnome-Classic desktop to it.  When you get to whatever your first screen is, hit:

Ctrl + Alt + F1

That will take you to a text only screen.  After you login on that screen, enter:

```
sudo apt-get install gnome-session-fallback
```

Follow that with:

```
sudo reboot
```

Then when you get back to the login screen, click on the icon and (I forget the exact wording) Gnome No Effects.

Of course if you have less than a gig of ram, this will not work either and you will need to go to a more efficient desktop.

---

### Post by grahammechanical on 2013-04-27
Use that right click on the desktop to change desktop background to open system settings and in Software & updates go to the Additional Drivers tab and try another video driver. I would suggest you activate the Nouveau open source driver.

---

