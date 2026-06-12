---
title: "Typing Hebrew"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by Carnivorum on 2012-05-16
Bs'd

What do I do to make ubuntu 12.04 type Hebrew?

---

### Post by cortman on 2012-05-16
You doubtless mean how can YOU type in Hebrew? Do you just need a font, or are you wanting the system language to be Hebrew?
[This]("https://help.ubuntu.com/community/HebrewLocalizationHowto") any help?

---

### Post by donkyhotay on 2012-05-16
You'll need a hebrew font of course and some programs will allow you to type right to left but be aware not all programs will do so.

---

### Post by Carnivorum on 2012-05-17
> **cortman said:**
> You doubtless mean how can YOU type in Hebrew? Do you just need a font, or are you wanting the system language to be Hebrew?
[This]("https://help.ubuntu.com/community/HebrewLocalizationHowto") any help?

Bs'd

I just need a font, I want my system language to remain English. 

I found on your link this:  "Navigate to "System"-->"Administration"-->"Language Support" but when I go to System tools, and then to Administration, then I don't see there any Language Support.  

Where can I find that?

---

### Post by codemaniac on 2012-05-17
you should look for the packages culmus and culmus-fancy, which contain high-quality Hebrew fonts.

---

### Post by Carnivorum on 2012-05-17
> **codemaniac said:**
> you should look for the packages culmus and culmus-fancy, which contain high-quality Hebrew fonts.

Bs'd

I installed both of 'm, how do I get them to work?

---

### Post by codemaniac on 2012-05-17
> **Carnivorum said:**
> Bs'd

I installed both of 'm, how do I get them to work?

Navigate to "System"-->"Administration"-->"Language Support". Mark "Hebrew" as your desired language, and choose to "Apply" the changes. 

Here is a complete howto for you .
[https://help.ubuntu.com/community/HebrewLocalizationHowto](https://help.ubuntu.com/community/HebrewLocalizationHowto)

---

### Post by Carnivorum on 2012-05-17
> **codemaniac said:**
> Navigate to "System"-->"Administration"-->"Language Support". Mark "Hebrew" as your desired language, and choose to "Apply" the changes. 

Here is a complete howto for you .
[https://help.ubuntu.com/community/HebrewLocalizationHowto](https://help.ubuntu.com/community/HebrewLocalizationHowto)

Bs'd

I have ubuntu 12.04 with the classic GUI.  For "Language Support" I have to go to Applications --> System Tools --> System Settings --> Language Support.

But there I only see options to set the language of my system to Hebrew, no option to just type Hebrew.

---

### Post by aharonl on 2012-05-29
Hi

You need to change keyboard layout!

go to :
System Settings -> keyboard -> layout settings -> '+' button

Cheers

---

### Post by Carnivorum on 2012-08-04
> **aharonl said:**
> Hi

You need to change keyboard layout!

go to :
System Settings -> keyboard -> layout settings -> '+' button

Cheers

Bs'd

Tried it, doesn't help.   I still cannot type Hebrew.

---

### Post by mikewhatever on 2012-08-04
> **Carnivorum said:**
> Bs'd

Tried it, doesn't help.   I still cannot type Hebrew.

It's been a while, so welcome back. Have you added a Hebrew keyboard layout as suggested by aharonl? What exactly do you mean by 'cannot type Hewbrew'? Why not?

---

### Post by gifford on 2012-08-05
If you followed the instructions for adding Hebrew as a keyboard layout, you should have the choice of changing to it on the top panel at the keyboard icon.

---

### Post by Carnivorum on 2012-08-06
> **gifford said:**
> If you followed the instructions for adding Hebrew as a keyboard layout, you should have the choice of changing to it on the top panel at the keyboard icon.

Bs'd

I did add Hebrew to the keyboard, but where can I find a keyboard icon?

---

### Post by ub07 on 2012-08-06
> **Carnivorum said:**
> Bs'd

I did add Hebrew to the keyboard, but where can I find a keyboard icon?

The keyboard icon should be among the icons in the top right of your screen.

---

### Post by Carnivorum on 2012-08-06
> **ub07 said:**
> The keyboard icon should be among the icons in the top right of your screen.

Bs'd

I guess you mean in the desktop.  But I have the classic GUI, and no keyboard icon there.

---

### Post by NoLedgeSeeker on 2012-12-02
> **Carnivorum said:**
> Bs'd

I guess you mean in the desktop.  But I have the classic GUI, and no keyboard icon there.
[RIGHT]&#1489;&#1505;"&#1491;

[LEFT]Try running this in an Xterm:
[/LEFT]

[/RIGHT]
/usr/bin/python  /usr/bin/gnome-language-selector  -n
(which is what the Language Support button does in the background).

You may have to first install the gnome-language-selector to make this work.

Then you will also want to go the xfce4 panel and add the language (keyboard) switcher applet... you click on the applet to change flags indicating different inputs.  And as noted at the beginning of this post, it would appear to have worked for me.

Now... if *I* can only figure out how to get MythTv to use a Hebrew enabled font so song titles in that language show up *in that* language rather than:  "??? ?? ???????"

---

### Post by dkohen on 2012-12-31
You need to do two things to type in Hebrew - add Hebrew to the installed languages (System Settings->Language Support:Install/Remove Languages and check the box for Hebrew), and add it to the keyboard (System Settings->Keyboard:Layout Settings:+)

 You may also want to use the Options:Keys To Change Layouts in keyboards to have a quick select option to toggle your keyboards.

---

### Post by Carnivorum on 2013-01-30
> **dkohen said:**
> You need to do two things to type in Hebrew - add Hebrew to the installed languages (System Settings->Language Support:Install/Remove Languages and check the box for Hebrew), and add it to the keyboard (System Settings->Keyboard:Layout Settings:+)

 You may also want to use the Options:Keys To Change Layouts in keyboards to have a quick select option to toggle your keyboards.

Bs'd

Thanks, I got it working.

---

