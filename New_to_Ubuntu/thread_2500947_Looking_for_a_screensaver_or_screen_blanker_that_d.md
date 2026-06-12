---
title: "Looking for a screensaver or screen blanker that does not totally stop sending signal"
date: 2024-09-16
forum: New to Ubuntu
---

### Post by bullwinkle2 on 2024-09-16
**EDIT:** I am redefining my request, since the word "screensaver" seems to have some negative connotations.  So now I am looking for something that will let me launch a full screen static image (.png or .jpeg or similar file) and display it until I come back and hit a key or something. That will do what I need and in particular it **will not** lock the screen or turn off the signal to the display or activate power management or anything like that.

(This is what I had written previously, please ignore it as it seems to inspire "solutions" that won't work for me and that kind of miss the whole point, I am only leaving it here so the discussion that follows in the first few messages makes sense and because some of the proposed solutions may work for other, even if they don't work for me).

I just started using Ubuntu 24.04 as my main desktop computer and I am looking for a screensaver that turns the full screen area black (or very dark grey) after some period of inactivity but does NOT completely turn off the signal to the display, and that still allows popup notifications to be displayed.  So nothing involving lock screens, power management or anything like that, just something that sends a static black or dark grey image to the full screen area until there some activity with the keyboard or mouse.  The privacy/security setting in Ubuntu isn't suitable because it stops sending any signal at all; I need it to send an all-black or very dark image to the display.

---

### Post by TheFu on 2024-09-16
**xscreensaver** doesn't work? 
Run the **xscreensaver-demo** to tweak the settings. [https://www.jwz.org/xscreensaver/](https://www.jwz.org/xscreensaver/)  has more details, if you need them.  The trick is the "Advanced tab" and choosing the glSlideShow screen saver.  

To be clear, Wayland probably won't work with xscreensaver.

---

### Post by ActionParsnip on 2024-09-17
Could just turn the monitor off.....

---

### Post by bullwinkle2 on 2024-09-17
> **TheFu said:**
> **xscreensaver** doesn't work? 
Run the **xscreensaver-demo** to tweak the settings. [https://www.jwz.org/xscreensaver/](https://www.jwz.org/xscreensaver/)  has more details, if you need them.  The trick is the "Advanced tab" and choosing the glSlideShow screen saver.  

To be clear, Wayland probably won't work with xscreensaver.

Ubuntu 24.04 runs Wayland,  And yes I know it is possible to boot into X but that increases the bootup time significantly and I am not sure what else it might break.  There's no screensaver or screen blanker that works with Wayland?

---

### Post by Holger_Gehrke on 2024-09-17
Most - if not all - screen savers and screen lockers are meant for an environment where there are people around who are not meant to read your screen, so they hide notifications by basically putting an undecorated window on top of everything. Letting notifications get on top of that window would be considered a security breach in such an environment (think of an email notification giving the sender and topic of the mail ...).

Holger

---

### Post by TheFu on 2024-09-17
[https://www.jwz.org/blog/2023/09/wayland-and-screen-savers/](https://www.jwz.org/blog/2023/09/wayland-and-screen-savers/) has some statements about Wayland and screen savers.

---

### Post by bullwinkle2 on 2024-09-17
> **Holger_Gehrke said:**
> Most - if not all - screen savers and screen lockers are meant for an environment where there are people around who are not meant to read your screen, so they hide notifications by basically putting an undecorated window on top of everything. Letting notifications get on top of that window would be considered a security breach in such an environment (think of an email notification giving the sender and topic of the mail ...).

Holger

I have no idea why you would assume that, I know plenty of home users that run screensavers.  That said I could live without the notifications being visible, as long as it sends some kind of signal to the display so I don't get the bouncing warning that there is no signal.

---

### Post by bullwinkle2 on 2024-09-17
> **TheFu said:**
> [https://www.jwz.org/blog/2023/09/wayland-and-screen-savers/](https://www.jwz.org/blog/2023/09/wayland-and-screen-savers/) has some statements about Wayland and screen savers.

Well I almost wish you had not posted that, because I did not  understand much of it (the technical parts - I am not a programmer so  those are pretty meaningless to me) but the rest of it just kind of made  me angry.  Why are the Gnome developers on such high horses about  screensavers?  That is the sort of thing that turns people into distro  hoppers.  I have been using Ubuntu on my home theater PC for years and  always had to turn off the screensaver on it, now I finally decide to  make the jump to using Ubuntu on the desktop (having left MacOS) and I  keep running into these little issues where the problem always seems to  be Wayland, OR the combination of Gnome and Wayland.  I'm starting to  feel really sorry I did not choose Linux Mint with the Cinnamon desktop;  only reason I didn't was because I don't like the "Windows look" of  Mint and I don't like that it comes pre-loaded with all kinds of  software I'd never use.  I think Gnome with X Windows would have been  fine (and still would be if it didn't take so damn long to boot, what's  with that?) or maybe Wayland and some other desktop, but it seems to me  that the combination of Wayland and Gnome is kind of toxic and now from what  I have been reading I think that may be more on Gnome than on Wayland.

That  said, even though I am not a programmer, I really don't see why a  screen blanker should be so difficult.  I could probably figure out some  way to make a very long, low res video that is solid black with no  sound and play it full screen in VLC, but seems like that would waste a  lot of power just to turn the screen black   But if VLC can go full  screen and Firefox can go full screen, isn't there anything that can  just display an image file full screen?  I can create a solid black  image in GIMP, if it comes to that.  Maybe because I used the term  "screensaver" people are overthinking this, I just want a way to turn  the screen black for short periods.  Other people might want a way to put up a particular picture on their screen while they are away.  Are you seriously saying there is no way to do that in Ubuntu, and that it is because the Gnome developers have some kind of bug up their butts about screensavers?

---

### Post by 1fallen on 2024-09-17
Well this thread looks fun, but as others have already mentioned, Wayland does not support screensavers or screen blankers in the same way that X11 does. The xscreensaver package, which is designed for X11, does not work natively with Wayland.


 Wayland &#8220;does not have any provision that allows screen savers to even exist in any meaningful way.&#8221; This suggests that the architecture of Wayland does not provide the necessary hooks or APIs for screensavers to function. (Yet!)
I see TheFu already posted the Link.


I can't see why your short with folks trying to help you....;) It is what it is.

EDIT: the best I can do on Wayland is to use [Super+L] to lock screen it works on Plasma tested, I'm no Gnome user so you will have to confirm that.
Or just a blank black screen:
```
gnome-screensaver-command --lock
```[FONT=var(--theme-post-body-font-family]
Providing that "[COLOR=#E0DDD9][FONT=ui-monospace]xscreensaver[/FONT][/COLOR][FONT=var(--ff-mono)]" is installed.[/FONT][/FONT]
[FONT=inherit][FONT=inherit][COLOR=#E0DDD9][FONT=-apple-system][FONT=inherit]
[/FONT]
[/FONT][/COLOR]
[/FONT]
[/FONT]

---

### Post by bullwinkle2 on 2024-09-17
> **1fallen2 said:**
> Well this thread looks fun, but as others have already mentioned, Wayland does not support screensavers or screen blankers in the same way that X11 does. The xscreensaver package, which is designed for X11, does not work natively with Wayland.

Part of why I am a little bent out of shape about this is that everyone seems to think that this is just normal. It's like the dog in the "this is fine" meme, except the flame around him are the flaming file of rubbish that is Wayland.  Okay, that may be a little unfair, I know that there are good reasons to move away from X but dammit, Wayland isn't ready yet!  And I am partly kicking myself for installing Ubuntu 24.04 but I really did not realize how poor the combination of Gnome+Wayland is.  I do appreciate that people have enlightened me on this but there are so many distros to choose from and people still say Ubuntu is one of the best for new users (which in a way I am, because I have never attempted to use Linux on my primary desktop system before).  And I think that was probably absolutely true when 18.04 or 20.04 was the current Ubuntu version, but all I can say is if I had known about some of the little details that make 24.04 such a pain in the posterior I would have run away!

 > **1fallen2 said:**
> Wayland &#8220;does not have any provision that allows screen savers to even exist in any meaningful way.&#8221; This suggests that the architecture of Wayland does not provide the necessary hooks or APIs for screensavers to function. (Yet!)
I see TheFu already posted the Link.

Right, and again to me that should have been a good indication that Wayland isn't ready yet.  It's one of those situations where some folks would never have a problem because they don't feel the need to run anything that isn't working with Wayland, but I have to tell you, this is about the fifth thing I have run into that makes my think Wayland sucks in about the space of two weeks (prior to which I barely understood what the difference was between X and Wayland, or why it would matter which was used).  And why Ubuntu folks just go "this is fine" is what I don't get. Is everyone too afraid to say that there are things about Linux that suck compared to MacOS or even maybe Windows?  I mean just the simple act of copying and pasting text is such a hit-or-miss proposition it makes me want to scream sometimes.

> **1fallen2 said:**
> I can't see why your short with folks trying to help you....;) It is what it is.

And that's EXACTLY why I'm that way.  That attitude, right there.  The acceptance of rubbish.  It just belies everything I have ever heard about how great Linux is!

I have a feeling if this problem were entirely confined to some other distro, Ubuntu users would be much more inclined to see how bad it is that you can't do simple ordinary things because "the Gnome developers..." or "Wayland doesn't yet..." (despite the fact that Wayland has been around for how long now?).  But to me this is exactly why people will turn away from Ubuntu, maybe not today or tomorrow, but soon.  Honestly, I had held off on switching for as long as I could because the way all the YouTubers were talking, the Cosmic desktop was going to be the next big thing.  But it is like everything else, it takes time, and I did not want to mess with alpha software.  But they have been making progress, I just wonder if they will have the same issues with Wayland as Gnome does.  I never understood why some of the YouTube Linux channels had so much hate for Gnome, but I am starting to see understand now.  Last time I updated my media center I put Debian and XFCE on it and in some respects that's working a whole lot better than my desktop system, but then again, that's still running X!

> **1fallen2 said:**
> EDIT: the best I can do on Wayland is to use [Super+L] to lock screen it works on Plasma tested, I'm no Gnome user so you will have to confirm that.

Again, the issue with a lock screen (besides the fact that locking the screen is something I specifically wanted to avoid) is that it stops sending any signal at all to the monitor.  And then I get this bright blue box traveling around the screen complaining of no HDMI signal.

> **1fallen2 said:**
> Or just a blank black screen:
```
gnome-screensaver-command --lock
```[FONT=var(--theme-post-body-font-family]
Providing that "[COLOR=#E0DDD9][FONT=ui-monospace]xscreensaver[/FONT][/COLOR][FONT=var(--ff-mono)]" is installed.[/FONT][/FONT][FONT=inherit]
[/FONT]

Really I am realizing that I didn't ask the right question.  The question I SHOULD have asked is, how can I display a full screen image (such as a 1920x1080 .png or ,jpeg) static image on the screen just by launching a script or program, that will work in Wayland.  I cannot believe that is totally impossible.  Maybe some people would use that to display a picture of their family, or a relaxing beach scene, or a mountain lake, or the night sky.  Me, I would just display a totally black or a dark gray image.  I have no problem with triggering it manually, but it MUST send some signal to the monitor so I don't get the damn blue box.  This thread has been helpful in that regard, I have learned that there is a negative connotation to the word "screensaver" for some unfathomable reason, so I am NOT asking for a screensaver anymore! :rolleyes:

---

### Post by bobunderwood99 on 2024-09-17
You could use Image Viewer (eog) or Mirage to display a black image file fullscreen.

---

### Post by tea for one on 2024-09-18
Have you considered Xubuntu 24.04?
It includes xfce4-screensaver	4.18.3-1build1

---

### Post by lucant on 2024-09-18
I'm sorry, but that's your problem. Everyone who uses Gnome knows that it has a lock screen... In case the machine is inactive for a while.
If this bothers you so much, instead of complaining about things we can't help you with, download another DE... Mate or Xfce, they have the screensaver you want. You just need to download it and select it at startup.

---

### Post by grahammechanical on 2024-09-18
I think that you are making an assumption. Many of those who post help on this forum do not use Ubuntu + Gnome. Some don't even use Ubuntu. Yet they are experts on Linux or on uses of Linux other than as a desktop OS. This is fine. It is freedom of choice. It does not mean that they accept things without complaining or wanting change.

Me? I gave up messing with the user interface years ago. I accept whatever Ubuntu + Gnome gives. I get on with my computer using life. One of the good things about Linux is user choice. If things are not the way we like it, then we are free to change it. One of the bad things about Linux is User choice. People are never satisfied with what they are given. I can understand developers having a "this is the way our software project works and looks. We like it. If you don't like it, then too bad."

Regards

---

### Post by bullwinkle2 on 2024-09-18
> **bobunderwood99 said:**
> You could use Image Viewer (eog) or Mirage to display a black image file fullscreen.

THANK YOU!  Image Viewer does exactly what I want, it took me about 30 seconds to make a solid black image using GIMP and I can just display that full screen.

Sorry if I did not make myself clear to begin with but that is really all I wanted.   I sure didn't need a whole page on how the Gnome developers don't like screensavers, although it was educational, and something I will keep in mind when next picking a distro/desktop. But since I JUST finished setting up Ubuntu and I no longer have another computer to fall back on (other than my home theater PC), changing distros just to get a couple of features seems a bad tradeoff at this point, though if Pop_OS and Cosmic turn out to be as good as they are hoping for I may well revisit my decision when they come out of alpha/beta.

I still feel like the shift to Wayland should have been put off until maybe 26.04 because right now it is hurting Ubuntu's reputation as a user friendly distro, as least for those who want to use their computers for something other than simply reading their email and viewing web pages.  But that is just my opinion; others are of course free to disagree.  Anyway thanks for helping me find a solution.

---

### Post by 1fallen on 2024-09-18
> **bullwinkle2 said:**
> 
And that's EXACTLY why I'm that way.  That attitude, right there.  The acceptance of shittiness.  It just belies everything I have ever heard about how great Linux is!



I wish you well....:)

---

### Post by bullwinkle2 on 2024-09-18
> **grahammechanical said:**
> I think that you are making an assumption. Many of those who post help on this forum do not use Ubuntu + Gnome. Some don't even use Ubuntu. Yet they are experts on Linux or on uses of Linux other than as a desktop OS. This is fine. It is freedom of choice. It does not mean that they accept things without complaining or wanting change.

If you don't even use Ubuntu WHY would you be hanging out in a Ubuntu forum? :confused: Yes, I did assume that those in a UBUNTU forum would be using UBUNTU!

---

### Post by 1fallen on 2024-09-18
Because we like to help others, plain and simple right?

---

### Post by him610 on 2024-09-18
> **bullwinkle2 said:**
> If you don't even use Ubuntu WHY would you be hanging out in a Ubuntu forum? :confused: Yes, I did assume that those in a UBUNTU forum would be using UBUNTU!

Just drop it! Let it go. You got what you came after. 
Be a little more civil to those who have been trying to help you.

Don't forget to mark your issue as *solved*.

---

### Post by bullwinkle2 on 2024-09-18
> **1fallen2 said:**
> I wish you well....:)

Well bless your heart!

---

### Post by bullwinkle2 on 2024-09-18
> **him610 said:**
> Just drop it! Let it go. You got what you came after. 
Be a little more civil to those who have been trying to help you.

Don't forget to mark your issue as *solved*.

Well let's see.  I have been told that what I wanted was not possible in Gnome, I have been told I should just settle for what other people thought I should want, and I have been told that the Gnome developers have made certain design decisions that we should all just accept.  And then when I rejected those things, I was told I should be "more civil".

If in another five or ten years everyone turns to an AI for answers, or I should say, if by then AI's have started giving accurate information so that no one has use a forum such as this, everyone will be bemoaning the lack of use of the forums and how they had "community" in the old days.  But what I have experienced here will be exactly why no one will want to use an online forum anymore.  AI's don't get bent out of shape if you reject their first proposed solutions as unworkable in your situation

I didn't come here for moralizing
I didn't come to be told how I should behave
I didn't come to be told what I should settle for
I didn't come here to be told to enable a feature that would cause a bright blue box to float around on my display (though I understand why at first people might have at first thought that was a good solution).
Most of all I did not come here to make anyone feel good about giving unworkable answers in my situation.  Be adults for crying out loud, what can be a good solution in one situation might be the totally wrong approach in another.  Solutions are like underwear, one size does NOT fit all.
I came to ask if a certain kind of software was available.  My mistake was not realizing that the word "screensaver" apparently has negative connotations in the Gnome community, but then, how was I even supposed to know that?

I did appreciate the help, but I did not appreciate the admonitions to be "more civil".  But that's all I will say about it.  I am still looking forward to the day when you can ask an AI a question and get CORRECT answers instead of made up garbage.

---

### Post by cainesaj on 2024-09-25
> **bullwinkle2 said:**
> I am looking for something that will let me launch a full screen static image (.png or .jpeg or similar file) and display it until I come back and hit a key or something.

Any decent image viewer should offer a full screen option. You can easily obtain or create a 1x1 back (#000000) PNG image, open it with your image viewer and make that image full screen. Closing this on your return should be straightforward. You can make this as clever and automated as you want.

For a limited example: the GNOME [Loupe]("https://apps.gnome.org/Loupe/") image viewer, which I have installed as a Flatpak, is very basic and can't launch directly into fullscreen, so I can run ```
$ flatpak --user run org.gnome.Loupe black_pixel.png
```press F11 to make it fullscreen, then control-w to close the window.

---

### Post by lonnux on 2024-11-04
I do need a screensaver that won't power off or suspend the monitor. I  run the Windows program through WINE on Linux. If the monitor is turned  off or suspended, the Windows program will be auto closed because of  dispaly source exception error. I need a screensaver or slideshow  program that can turn the display black/dim and hide the mouse pointer.

---

