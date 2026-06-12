---
title: "A couple of questions on 20.04 LTS"
date: 2020-05-25
forum: New to Ubuntu
---

### Post by jw-middleton on 2020-05-25
I've played with various distro over the years, although haven't touched it for over 3 years. I Recently bought a RPi-4b on which I installed Raspbian. I was fun to play with, but a bit limited. So, I grabbed my BiL's old Dell Optiplex 7010 and installed a disc of 16.04 LTS. Upgraded to 18.04, then 20.04. I might should have stayed with 18.04 for a while as it has much more community support. Anyway, I was surprised at how little difference I saw in 20.04. So, I started asking Google about the differences. I read webpages and watched Youtube videos. I was surprised that my screen didn't look like the ones I saw. Most of the info was from the day of release, or a few days after. So, stuff may have changed. Anyway, here are a couple of the items I saw that were different on my system that I would like to have.

1. There is no date at the top center. You are suppose to be able to click it to set "Do Not Disturb" and to see a calendar. I installed Tweaks to set it, but my Tweaks menu does not have Top Bar as an option in the left menu.

2. Every screen shot I observed had a Nine-Dot Grid at the bottom of the launcher for Other Apps. Mine has a Trash can. 

I've searched for answers with no luck. Any idea what is going on? I am running GNOME version 3.36.2 on Ubuntu 20.04 LTS,

John

---

### Post by coffeecat on 2020-05-25
Your description matches the Unity desktop. Unity was the default desktop in 16.04, but this changed to gnome in 18.04. However, you can install Unity in both 18.04 and 20.04, so my guess is that the Unity packages were updated during the upgrades to 18.04 and then to 20.04, and your login still defaults to Unity. 

See if there are any other options at the login screen.

I note you say that you are running gnome 3.36.2, but Unity uses some gnome libraries. Where did you get that information?

---

### Post by Perfect Storm on 2020-05-25
Sounds like Unity. You can keep it if you wish or you could try ubuntus many flavor.

---

### Post by jw-middleton on 2020-05-25
> **coffeecat said:**
> Your description matches the Unity desktop. Unity was the default desktop in 16.04, but this changed to gnome in 18.04. However, you can install Unity in both 18.04 and 20.04, so my guess is that the Unity packages were updated during the upgrades to 18.04 and then to 20.04, and your login still defaults to Unity. 

See if there are any other options at the login screen.

I note you say that you are running gnome 3.36.2, but Unity uses some gnome libraries. Where did you get that information? *[SIZE=3][COLOR=#ff0000]I can't tell you until it comes up as I don't remember, but it was one of the About screens.[/COLOR][/SIZE]* 


Thanks! That confirmed my findings. I installed  something called *fetch that showed me that my DE was Unity. I think it kept Unity because I started the upgrade with 16.04. I tried twice to install and switch to GNOME, but it didn't change my DE after rebooting.  So, I download 20.04 on my Win10 machine and burned a DVD. I am now reinstalling. The desktop just came up before rebooting and I saw the date at the top. So, I am on the right track. BUT, while rebooting it is getting a LOT of I/O errors and now seems to be hung. 

John

---

### Post by coffeecat on 2020-05-25
Please do not reply to a quote by typing your reply in red inside a quote box. The quote box should only contain text posted by the person you are quoting. The way to reply is simply to type your reply in the body of your text after the quote box.

---

### Post by jw-middleton on 2020-05-25
I am back and using GNOME! It is different as many things are backwards from Unity, like the Tile Bar Buttons being on the top right. 

I'm about to check the disk to see if there are any bad spots.

The utility I used to find the version of GNOME was Setting>About. It looks the same with the change.

John

---

