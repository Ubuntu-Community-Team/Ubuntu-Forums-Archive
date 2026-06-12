---
title: "Ubuntu HDMI close lid issue"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by mushroom08 on 2012-04-19
Hi im having trouble figuring out how to disable suspend on my laptop so that i can use my plasma tv without having my laptop lid open how do i fix this? :confused:

---

### Post by Jose Catre-Vandis on 2012-04-19
Assuming you have turned off all power saving options, including screensaver, it could be hardwired into the laptop. Check the bios for options?

---

### Post by mushroom08 on 2012-04-19
when i go to system and power management it gives me only 4 options for laptop lid closed blank screen, suspend, hibernate, and shutdown so what im looking for is a way around this

---

### Post by audiomick on 2012-04-19
What happens with the blank screen option? Does the HDMI output go off too?


If you do get this to work, keep an eye on the temperature, at least initially. My laptop gets very warm if I leave it running with the lid shut for any length of time.

---

### Post by mushroom08 on 2012-04-19
ya the HDMI goes off to and as for temp i have a cooling dock on it for that will that be good?

---

### Post by audiomick on 2012-04-19
Hard to say about the cooling dock. You will just have to observe it and see.

It is possible that you may not be able to get the internal monitor and the HDMI ouput to switch independantly. I doubt a bit that you will find anything useful in the BIOS. I think it is a question of what the video card can do.

If you can't get them to switch seperately, you could perhaps find a satisfactory comprimise by making your desktop background black.

---

### Post by mushroom08 on 2012-04-19
ok i have them working as two separate monitors but i cant get the tv to display any workstations just my background](*,) i have not done this before how do i give my tv its own workstation this would be nice as ling as i dont have my movies playing on two screens im fine

---

### Post by audiomick on 2012-04-19
What video card is it?

What you are looking for is to have the one desktop spread over both screens. On an nVidia card, the mode is called "twin view". Otherwise, I think it is called Xinerama. 

It is also possible to set up two seperate x screens. This is a little more complicated, I believe.

What have you got (which mode) set up now?

---

### Post by mushroom08 on 2012-04-19
i have both in parallel and intel integrated graphics

---

### Post by audiomick on 2012-04-19
> **mushroom08 said:**
> i have both in parallel ...
Sorry to have to ask again: does that mean that you see the same on both screens or not?

I have a feeling that you are not seeing the same on both screens. If this is the case, I think you should be able to move your mouse over to the other screen. It may not be set to the way the screens are physically standing. Try moving your mouse over all four borders of the internal monitor and see if it turns up on the other screen. 

There is an option in the screen manager tool to tell the graphic card in which orientation the screens are, like left-of or right-of or whatever. 

If you can move your mouse over to the other screen, then you should be able to just drag your movie player over and maximise it on the big screen, or put it into full screen mode there.

Having said that, I think I have seen a case where the full screen mode only worked on the internal screen of whatever machine it was. In that case, your best option is to just maximise the movie player on the larger screen.

---

### Post by mushroom08 on 2012-04-19
That is indeed what im doing i just wanted to give the tv its own dedicated workstation so i could turn the laptop screen off without closing the lid and turn it back on later but yes i have them so they are not showing the same thing

---

### Post by audiomick on 2012-04-19
> **mushroom08 said:**
> ...so i could turn the laptop screen off without closing the lid and turn it back on later...


Ok, so you would have  gathered by now that this might not be possible. I think this possibility, although eminently logical for ignorant users like us, doesn't occur to the people that make video cards. ;)

Anyway, it sounds like you should at least be able to get your movie player to play on the bigger screen. Is that the case?

---

### Post by mushroom08 on 2012-04-19
Ya ill get by but it was just in system display it gives me the option when i have more than one monitor on to turn one or the other off so i just thought if i could get 2 workstations going i could do that my hdmi is not very long so my laptop screen is distracting thanks for your help time to get rdy for work ill tinker with it later

---

### Post by Jose Catre-Vandis on 2012-04-20
You can use xrandr to turn off one "screen" that is served up by the graphics card as the same "display" as the other "screen" (complicated I know). Very often display 0:0 will run both screen 0 and screen 1.

```
xrandr -q
``` will give info about the multiple screens running on the same display. For example I get LVDS1 (laptop) and VGA1 (monitor). Now I can turn each one off independently:
```
xrandr &#8211;output LVDS1 &#8211;off
``` turns off the laptop screen. To turn it back on
```
xrandr &#8211;output LVDS1 &#8211;auto
```Maybe this will help.

Re power management, you should be able to turn it off altogether....

---

