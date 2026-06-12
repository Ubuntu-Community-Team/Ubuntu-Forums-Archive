---
title: "Side bar not triggering properly"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by Drowz0r on 2012-06-20
Hello all

I've updated 11.10 to 12.04 and I find the side bar doesn't trigger properly. I find this on my tablet PC (32bit) and my dual screen PC (64bit). More often than not. Say 4/5 times, I move my cursor to the left and try to trigger the side bar into opening and it won't slide out. I have to push the cursor to the side about 5 times before it works or just give up and press my Windows key.

Any ideas on how to fix this?

---

### Post by zombifier25 on 2012-06-20
Try reseting unity:
```
unity --reset
```

---

### Post by MG&amp;TL on 2012-06-20
> **Drowz0r said:**
> Hello all

I've updated 11.10 to 12.04 and I find the side bar doesn't trigger properly. I find this on my tablet PC (32bit) and my dual screen PC (64bit). More often than not. Say 4/5 times, I move my cursor to the left and try to trigger the side bar into opening and it won't slide out. I have to push the cursor to the side about 5 times before it works or just give up and press my Windows key.

Any ideas on how to fix this?

You can try reducing the launcher sensitivity in CCSM, this will reduce the amount of pressure that is needed to produce the launcher.

If you don't have CCSM, you can look for Compiz-Config-Settings-Manager in the software centre. Go to the Unity tab in CCSM, click on it, then head to "experimental".

---

### Post by NikTh on 2012-06-20
> **MG&TL said:**
> You can try reducing the launcher sensitivity in CCSM, this will reduce the amount of pressure that is needed to produce the launcher.

If you don't have CCSM, you can look for Compiz-Config-Settings-Manager in the software centre. Go to the Unity tab in CCSM, click on it, then head to "experimental".

It will not need to install CCSM . 
This option is in Ubuntu by default , just right click on desktop and "**change desktop background**" , then at appearance window click on **behavior** and "**Reveal Sensitivity**"   , move the bar to the end.

---

### Post by Drowz0r on 2012-06-20
> **NikTh said:**
> It will not need to install CCSM . 
This option is in Ubuntu by default , just right click on desktop and "**change desktop background**" , then at appearance window click on **behavior** and "**Reveal Sensitivity**"   , move the bar to the end.

Sorry but isn't sensitivity to do with the duration the cursor is pushed to the side to trigger the side bar? I can leave the cursor there for 5 minutes and still nothing happens. It seems to just not detect that my cursor has hit the side of the screen.

I tried it anyway but it made no difference :c

---

### Post by MG&amp;TL on 2012-06-20
> **NikTh said:**
> It will not need to install CCSM . 
This option is in Ubuntu by default , just right click on desktop and "**change desktop background**" , then at appearance window click on **behavior** and "**Reveal Sensitivity**"   , move the bar to the end.

My apologies. I admit I hadn't noticed that one. :)

@OP:

You have to continue moving your cursor against the launcher, not just leave it there. You have to "push" it. Sensitivity is how much pushing you do, not how long you leave it there for.

If you're still struggling with the pressure, even with the minimum setting, you could always try increasing your mouse sensitivity. Just a thought.

---

### Post by Drowz0r on 2012-06-20
> **MG&TL said:**
> My apologies. I admit I hadn't noticed that one. :)

@OP:

You have to continue moving your cursor against the launcher, not just leave it there. You have to "push" it. Sensitivity is how much pushing you do, not how long you leave it there for.

If you're still struggling with the pressure, even with the minimum setting, you could always try increasing your mouse sensitivity. Just a thought.

Oh, weird. You have to push into the side of the screen to get it to trigger? Previously if I even brushed against it, it would trigger... in fact, on my 11.10 machine down stairs, it still triggers on a hair touch. o.o Is there a way to make it so it triggers on touch rather than push? It means every now and then I have to pick up and return my mouse to the right hand side of the mousemat. It's a little irritating. I suppose there's not a way to change it back..?

P.S. I've already adjusted the settings to max sensitivity.

---

### Post by MG&amp;TL on 2012-06-20
> **Drowz0r said:**
> Oh, weird. You have to push into the side of the screen to get it to trigger? Previously if I even brushed against it, it would trigger... in fact, on my 11.10 machine down stairs, it still triggers on a hair touch. o.o Is there a way to make it so it triggers on touch rather than push? It means every now and then I have to pick up and return my mouse to the right hand side of the mousemat. It's a little irritating. I suppose there's not a way to change it back..?

P.S. I've already adjusted the settings to max sensitivity.

Yeah, it's a feature of 12.04, user feedback said that hair trigger launchers interfered with the browser back button. No, there's not a way to change it back. I too find it irritating, so I've set mine not to hide. It takes up surprisingly little screen estate, particularly if you resize it.

---

### Post by NikTh on 2012-06-20
> **MG&TL said:**
> 
You have to continue moving your cursor against the launcher, not just leave it there. **You have to "push" it.** Sensitivity is how much pushing you do, not how long you leave it there for.

Yes , thats the correct behavior of Launcher revealing feature.

---

### Post by colin.p on 2012-06-21
> **MG&TL said:**
> Yeah, it's a feature of 12.04, user feedback said that hair trigger launchers interfered with the browser back button. No, there's not a way to change it back. I too find it irritating, so I've set mine not to hide. It takes up surprisingly little screen estate, particularly if you resize it.

I also got tired of struggling with the sidebar and just leave it displayed. I have a Dell 1545 laptop and it really doesn't take up too much room and have the icon size at 32.

---

### Post by Drowz0r on 2012-06-21
Ahh I see. Thank you for the feedback everyone. It's a shame it's not an option. I'd leave hide off but I'm on 4:3 screens so the width is pretty important to me. I'll have to find some other way of working.

Thanks again all.

---

### Post by MG&amp;TL on 2012-06-21
> **colin.p said:**
> I also got tired of struggling with the sidebar and just leave it displayed. I have a Dell 1545 laptop and it really doesn't take up too much room and have the icon size at 32.

I have a laptop too, IMO it works better with a mouse. I.e. not a trackpad.

---

