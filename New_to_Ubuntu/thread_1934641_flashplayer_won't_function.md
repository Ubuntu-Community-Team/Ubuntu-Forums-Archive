---
title: "flashplayer won't function"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by benjie1 on 2012-03-02
Installed adobe flash player from Ubuntu software center and it won't function, with icu2.com  Using Ubuntu version 11.10 and gnome desktop. Have the latest firefox browser. icu2.com web page has a box that tells me to get the latest plugin and did that but not sure which of the choices in the drop down box to use. The bottom one says APT Ubuntu 10.x and it won't download at all. The other choices say for "other llinux" and one other one specifies yum, which I assume is for Fedora. So which one do I choose and if it's the one specifying Ubuntu why won't it download. Clicking the yellow arrow for download does nothing. Flashplayer does work in opensuse v 12.1 and Fedora v 16 on the icu2.com webpage and the latest firefox.  Any ideas what to do? Thanks. Noob here.          Bob

---

### Post by winh8r on 2012-03-02
Hi,

click on the link "help with flash" in my sig below and follow the instructions to install Flash Aid, this will sort out your issues.

Hope this helps.

---

### Post by Jake5 on 2012-03-02
my suggestion would be to undo whatever you have done, after that open the terminal and run:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get update grub
sudo apt-get install ubuntu-restricted-extras
```

one at a time, obviously.

---

### Post by benjie1 on 2012-03-02
> **winh8r said:**
> Hi,

click on the link "help with flash" in my sig below and follow the instructions to install Flash Aid, this will sort out your issues.

Hope this helps.

Forgot to mention  I tried this and it did not work either. It got me to the page in icu2.com where your camera should enable but it doesn't. And the page is frozen as well. I removed it and that got me back to the get plugin page. Tried both the stable 32 bit version and the beta version. Both gave the same results.   Thanks.

---

### Post by benjie1 on 2012-03-02
> **Jake5 said:**
> my suggestion would be to undo whatever you have done, after that open the terminal and run:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get update grub
sudo apt-get install ubuntu-restricted-extras
```one at a time, obviously.


already un-did what I had tried. Will do these steps tomorrow. But ... after the last step, where do you get to install the plugin and which veersion from the download arrow do you use. Maybe that's all set after the last step. If not, what do I do after the last step is finished .  Noobie here. Thanks                                    Bob


Ran the 4 steps and at the end of the last step a Package Configuration Box appeared. It had a EULA for True type fonts from Microsoft. Clicked <ok> but nothing happened. Closed the box and now I don't know what the next step is? Do I try to install flashplayer  or was it installed in the steps you gave me?  Not sure what's next. Thanks for the help.                           Bob

Tried installing skype from ubuntu software center and it failed. Got this error message  




 Is this related ti trying to install flashplayer?  sorry I don't know how to make the screenshot smaller. Help please.  Thanks                     Bob

Guess I don't know how to attach a screenshot. Please help. I have an error message I'd like to attach here. Sorry for the troubles.                        Bob

---

### Post by benjie1 on 2012-03-06
Guess I made a mess of things trying too hard to do too many things. The 4 steps you listed worked fine, but when the last one finished, I didn't know how to proceed. As you see, I tried a few things but still can't get flashplayer to instal. Tried it by using install software and it didn't install. Can you please help me. I will just do only the things you tell me and not jump ahead and guess at things. Sorry for making a mess of things.  Thanks again.                   Bob

---

### Post by benjie1 on 2012-03-06
> **benjie1 said:**
> Guess I made a mess of things trying too hard to do too many things. The 4 steps you listed worked fine, but when the last one finished, I didn't know how to proceed. As you see, I tried a few things but still can't get flashplayer to install. Tried it by using install software and it didn't install. Can you please help me. I will just do only the things you tell me and not jump ahead and guess at things. Sorry for making a mess of things.  Thanks again.                   Bob

No reply so I guess I did something wrong. Sorry. Flashplayer is not installed and I haven't attempted any more installs of it. Will wait to hear from you so I can install it properly and get it working correctly. Guess I'm guilty of too much effort and not enough knowledge in trying to install flashplayer. Hope to hear from you and will follow what you say. The 4 steps you suggested worked fine but after the last step I had no idea what to do and went on foolish attempts to try things. Again, sorry. BTW, flashplayer is working in both openSuse 12.1 and Fedora 16. Thanks.                     Bob

---

### Post by haqking on 2012-03-07
if you are using firefox then try the flashaid plugin

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

and to take screenshots, press the prtsc key.

Cheers

---

### Post by benjie1 on 2012-03-07
Flash aid did not work. The web page icu2,com opens and then there is a box 'enable webcam' I clicked it and then there's another box that says: Adobe flashplayer settings: you can either "allow or deny" Neither one does anything at all, and icu2 freezes. Have the latest firefox here and in openSuse where that adobe flash player box also appears and clicking "allow" lets the camera become enabled. So I still can't get it to work here. In opensuse v 12.1 flashplayer installed from their software center. Wold that work here and should I remove flash aid? Thanks for your help. Much appreciated. The camera won't work in Skype either (for Linus).             Bob

Correction: The cam did work in Skype but the image is reversed left to right.

---

### Post by benjie1 on 2012-03-09
Update to post #9. Contacted icu2.com re: the flashplayer settings box problem. They replied with the following: Flashplayer won't play for Ubuntu 11.10 until either Canonical or Adobe fix it. A workaround - start Ubuntu, then at the login screen, click the cog/wheel at the right and choose Ubuntu2D. I did this and it works beautifully. The adobe settings box allows the camera to be recognized now and things work fine. Have no idea why there is a problem with Adobe and Ubuntu and not with Fedora 16 or openSuse 12.1. Hope this info is helpful to you. BTW, all the versions of Linux above, have the self images reversed left to right. Can that be corrected? Thanks for the help.         Bob

---

### Post by Cheesemill on 2012-03-09
> **benjie1 said:**
> BTW, all the versions of Linux above, have the self images reversed left to right. Can that be corrected? Thanks for the help.         Bob

Are you sure that the image has been flipped?

Remember it's a camera and not a mirror :)

---

### Post by haqking on 2012-03-09
> **Cheesemill said:**
> Are you sure that the image has been flipped?

Remember it's a camera and not a mirror :)

yes its very easy most webcam apps have a flip/mirror tick box

to OP make sure in your preferences for your webcam you dont have flip/mirror enabled.

Cheers

---

### Post by forrestcupp on 2012-03-09
If you still haven't gotten Flash to work, I can tell you what finally worked for me.

Try out Flash-Aid again. Just in case you didn't know this, it's not enough to just install the extension; you have to run the wizard. To get to the wizard in Firefox, go to the Flash-Aid menu in the Tools menu, and choose Wizard Mode.

When I used Flash-Aid, it didn't work for me at first, either. Nothing I tried worked. Then I tried going back to Flash-Aid and installing the 32-bit Stable version instead of the newer Beta version, even though I'm using 64-bit Firefox in 64-bit Ubuntu. Flash-Aid set the 32-bit version up to work with 64-bit Firefox, and now it works perfectly. That is the only way I could get it working on my computer.

Since then, after some updates once, it somehow updated to the 64-bit beta, and I had to go back into Flash-Aid and install the 32-bit Stable again.

---

### Post by benjie1 on 2012-03-10
Strange, but in the logitech 9000 camera software, there are 2 choices re: the mirror and normal view. If I set it to normal, the image is reversed, left to right. If I set it to mirror, then the image is normal. So it mirror is ticked, the image is normal. If I raise my right hand, I see my hand at the right side of the image. If normal is ticked, then my right hand appears at the left side of the image. This holds true for win 7. In Ubuntu 11.10 the image is reversed left to right, i.e. my right hand appears at the left of the image. Can't change it cause the Logitech software won't work in Linux I guess.  Thanks             Bob

BTW flashplayer is working, just the strange problem with the l to r orientation is a pain.

---

### Post by forrestcupp on 2012-03-10
> **benjie1 said:**
> Strange, but in the logitech 9000 camera software, there are 2 choices re: the mirror and normal view. If I set it to normal, the image is reversed, left to right. If I set it to mirror, then the image is normal. So it mirror is ticked, the image is normal. If I raise my right hand, I see my hand at the right side of the image. If normal is ticked, then my right hand appears at the left side of the image. This holds true for win 7. In Ubuntu 11.10 the image is reversed left to right, i.e. my right hand appears at the left of the image. Can't change it cause the Logitech software won't work in Linux I guess.
You're not thinking about it right. That's how it's supposed to work. If you look in a mirror and raise your right hand, the hand on the right side of the mirror goes up. That's a mirror image. If you take the mirror away and have someone face you and they raise their right hand, it would be on your left side. That's normal.

The way you described it is how it is supposed to work.

---

### Post by benjie1 on 2012-03-10
OK then in Win7 if I raise my right hand the image of my right hand appears on the right side of the camera image.  In ubuntu, 11.10 the image of my right hand appears on the left of the camera image. That's what I mean by reversed. Logitech software of the quickcam pro 9000 is not Linux friendly and I can't do anything to adjust the software. Still curious why camera image of right hand is on the right of the camera image in win 7 and on the left in Ubuntu.  Thanks again.                       Bob

---

### Post by Cheesemill on 2012-03-10
Because Windows is flipping the image, Ubuntu is showing the correct behaviour.

---

### Post by benjie1 on 2012-03-10
I'd like to have Ubuntu show right hand on right side of camera image like win 7, regardless of the reason. Can that be done?  Tks.

---

### Post by forrestcupp on 2012-03-11
So what you're saying is that you want it to be mirrored, but there's no option for that in Ubuntu's drivers.

That's usually not going to be a driver setting, but a setting in whatever software you're using your webcam with. I know that Cheese and Guvcview both have settings for mirroring your webcam, so you might want to investigate into those. 

Just keep in mind that if you're mirroring your image while chatting with someone, even though it's less confusing for you, it's going to be more confusing to them because it's a mirror of how they normally see you. But it can be done within a lot of the software that uses the webcam.

---

### Post by benjie1 on 2012-03-12
OK Didn't know it was confusing to the other party. Guess I'll leave well enough alone. Perhaps some day Logitech will become user- friendly to Linux.  LOL?  Thanks                 Bob

---

### Post by forrestcupp on 2012-03-14
> **benjie1 said:**
> OK Didn't know it was confusing to the other party. Guess I'll leave well enough alone. Perhaps some day Logitech will become user- friendly to Linux.  LOL?  Thanks                 Bob

Well, like I said, a lot of our webcam software does have a mirroring option that should work with your webcam. And as far as the other person being confused, it probably doesn't affect them as much as it is confusing to you. The only reason I said that is because I had mine mirrored when I was chatting with my brother once, and he was trying to figure out where I was in my house. Then I realized he couldn't figure it out because it was mirrored. :) 

What they need to do is make a setting where it is mirrored for you, but not the other person. I saw another discussion on that, and it appears that there is no way to do that right now.

---

### Post by dasking on 2012-10-20
> **haqking said:**
> if you are using firefox then try the flashaid plugin

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

and to take screenshots, press the prtsc key.

Cheers
THANK YOU SO MUCH IVE TRIED EVERYTHING I WISH I COULD GIVE YOU A HUGE HUG:guitar::confused: did i say that out loud

---

