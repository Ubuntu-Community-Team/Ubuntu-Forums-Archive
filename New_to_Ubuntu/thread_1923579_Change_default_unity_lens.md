---
title: "Change default unity lens?"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by d4m1r on 2012-02-10
Hey guys, I am surprised this hasn't been answered before but is there a way to change the default unity lens? I know you can install custom ones, but what if I just want to change it to another one of the default ones? Mainly because the large icons of the default page are useless to me, I'd like the 2nd page (Applications lens) to become the default.

How can I set it to be?

---

### Post by cariboo on 2012-02-10
If you can put up with the default until Precise is released at the end of April, you won't have to put up with the large icons any more. See the screenshot.

---

### Post by d4m1r on 2012-02-11
> **cariboo907 said:**
> If you can put up with the default until Precise is released at the end of April, you won't have to put up with the large icons any more. See the screenshot.

Even then, "recent" files and programs wouldn't be my first choice...Is there a way to change the default lens in 11.10? I definitely hope there is a way in the 12.04 LTS release as that is better, but not by much...

---

### Post by sadaruwan12 on 2012-02-11
You could try the new version of unity unity 5.0 it's still a work in progress but works nicely on my laptop use the below repo to get it installed. And the best thing is that there are lot of customizing option available through the copmizconfig-settings-manager.

    ```
sudo add-apt-repository ppa:unity-team/staging
    sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by d4m1r on 2012-02-11
> **starwarfans said:**
> Default lens is in the data editor lens editor to change.


Mind elaborating on that or how I could access that editor?

---

### Post by DGINSD on 2012-05-02
> **d4m1r said:**
> Mind elaborating on that or how I could access that editor?

Install the package dconf-tools then in a ternminal
```
dconf-editor
```

The item he's referring to I believe is under desktop/unity/dash. unfortunately it looks like the first view with recently used and available apps is pat of the applications lense. There is another entry below labeled lenses, but I don't have time right now to look into it, hope this helps.

---

### Post by d4m1r on 2012-05-02
> **DGINSD said:**
> Install the package dconf-tools then in a ternminal
```
dconf-editor
```The item he's referring to I believe is under desktop/unity/dash. unfortunately it looks like the first view with recently used and available apps is pat of the applications lense. There is another entry below labeled lenses, but I don't have time right now to look into it, hope this helps.

Please let me know when you have time to look into it, as I would really appreciate it ;)

Also, I have dconf-editor installed, but there is no such thing as desktop/unit/dash...there is only devices, launcher, panel, and runner.

---

### Post by DGINSD on 2012-05-03
I just realized your running 11.10, so your dconf would be slightly different then mine. When I get home tonight I'm gonna digg around through CCSM and see if there's any way to make the applications lens exclude the recently used stuff, as I don't care much for it myself, in the mean time I've gotten in the habit of calling up the dash and immediately typing the first few letters of the program I want.

---

### Post by d4m1r on 2012-05-03
> **DGINSD said:**
> When I get home tonight I'm gonna digg around through CCSM and see if there's any way to make the applications lens exclude the recently used stuff, as I don't care much for it myself 

Please do and thanks in advance! :P

---

### Post by DGINSD on 2012-05-04
While compiz configuration settings manager has plenty of nice settings and customization, I didn't find anything regarding lenses.

I'm attaching some screen shots of dconf showing the options there it seems as if those are the only options to change the behavior of the default lenses, and if you correct about them not being there in 11.10 they may only be available in 12.04.

[[img]http://s19.postimage.org/qfex67avj/dconf.jpg[/img]](http://postimage.org/image/qfex67avj/)

[[img]http://s19.postimage.org/rvqfocdsf/dconf2.jpg[/img]](http://postimage.org/image/rvqfocdsf/)

---

### Post by NikTh on 2012-05-04
> **d4m1r said:**
> Even then, "recent" files and programs wouldn't be my first choice...Is there a way to change the default lens in 11.10? I definitely hope there is a way in the 12.04 LTS release as that is better, but not by much...

Hi
if you want to remove **recent files **and **available apps**  use MyUnity tool. 
If you have 12.04 just install it from terminal with
```
sudo apt-get install myunity
```if you have 11.10 then you must add an ext.repository first 
```
 sudo apt-add-repository ppa:myunity/ppa && sudo apt-get update
```and then install with
```
sudo apt-get install myunity
```Find it on Dash and open it.. 
you will find interesting tweaks. 
:)
Thanks

---

### Post by d4m1r on 2012-05-04
Thanks for that but yah, 11.10 doesn't seem to have any of those options :(

---

### Post by deonis on 2012-05-04
try gnome-shell: sudo apt-get install gnome-shell
I had the same kind of questions a year ago. I still don't understand all useless stuff implemented in there.

---

### Post by d4m1r on 2012-05-05
> **deonis said:**
> try gnome-shell: sudo apt-get install gnome-shell
I had the same kind of questions a year ago. I still don't understand all useless stuff implemented in there.


Not a fan of Gnome, Unity is for me ;-)

---

### Post by DGINSD on 2012-05-05
> **d4m1r said:**
> Not a fan of Gnome, Unity is for me ;-)

I have both installed but when I want to get something done I'm using Unity, personal preference thing I guess.

You could try installing the new Unity (post #4) and perhaps these dconf options would be available to you then. I tried deselecting those options and rebooting but it didn't seem to change much, certainly not what I was looking for, could be different for you who knows, just a thought.

---

### Post by d4m1r on 2012-05-08
Well....Even since I've upgraded to 12.04 and I do get a few extra lens related settings, I am still not able to change the menu to open to the 2nd lens (Installed)....Unless I am doing something wrong? :confused: Is it even possible?

---

### Post by ledzepjes on 2012-05-13
I used to go to Ubuntu Tweak for such things, but ever since the previous version the UI stopped being functional and I stopped recommending it, that in part and it doesn't give the options or functionality it used to. The whole interface of Ubuntu Tweak has become horrid in my opinion compared to what it was before. I preferred all the main menu items on the side. You can't even install common software from it anymore, like google chrome or deluge or unrestricted extras or shutter, on and on, I don't see any options to install any software or get the nicer more logical layout back.

I would mention MyUnity, but I don't see any option to do this from there either.

When you find a solution to change the default lenses let me know.

Currently, from looking at dconf editor, desktop->unity->dash shows ```
home-lens-ordering ['applications-lens','files.lens','music.lens']
```

but what comes up as the default lens isn't the applications lens, so I don't know where to look, since it's obviously not there, or it's not being handled by dconf-editor at all, the default lens must be handled some where else.

If someone had a tutorial showing how to edit things and submit your own patches I'd do more of it my self.

---

### Post by itagomo on 2012-09-29
this (lens) is not configurable yet as far as I know .. not sure if someone had already made some changes like what you want .. home-lens is always the default lens that shows up first, but if you want directly open the lens you want, right-click the Dash key and you'll see a Quicklist Menu ..

---

### Post by czgirb on 2012-09-30
> **cariboo907 said:**
> If you can put up with the default until Precise is released at the end of April, you won't have to put up with the large icons any more. See the screenshot.

Oh my God! There are a lots of applications icon.
Please inform ... how big is your monitor?
How can you make it? Please guide me ...

**PS:**
I used **Ubuntu 12.04** and **Compaq CQ40 14inch** lappie.

---

### Post by Canterwood on 2012-10-03
Google brought me here since I was looking for a way to change the default lens in the Unity Dash. I read your thread and later found out that Super + A opens up the Applications lens. It's an extra key but it'll take you where you need to be.

---

