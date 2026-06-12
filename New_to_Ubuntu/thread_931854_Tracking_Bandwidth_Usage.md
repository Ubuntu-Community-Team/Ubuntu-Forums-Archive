---
title: "Tracking Bandwidth Usage"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Case04 on 2008-09-27
Hey, sorry if this is anywhere else on the forum, but I couldn't find a match -- and my problem is fairly specific.

Well, the story is that my ISP only allows 95GB in bandwidth a month and recently, my family has been going over it -- WAY over it.

I know it's not me, but I need to know if there's a program that'll track my bandwidth usage on a per-day basis and can give me monthly printouts about how much I've used, so I can show my family that I really haven't been hogging the bandwidth.

Keep in mind, I'm a beginner -- so GUI is obviously a concern because commands through the console confuses the hell out of me for the time being (I'm still learning).

Any applications available through any of the repositories? Any help would be greatly appreciated.

Thanks in advance.

---

### Post by dhughes on 2008-09-27
There are some desklets/screenlets that will do that but the one I tried suddenly freaked out and went from a few GB to "200345566202" or something like that.

 Anyway install and then try some desklets or screenlets, gDesklets is in Applications>Add/Remove Applications then search for gDesklets and after that look around the categories to see the network monitors that are available.

**edit**: Actually use Screenlets I know that was the one where I found the Network Monitor that also measured the up and down amounts you sent and received. Screenlets can be found in Synaptic Package Manager, Screenlets tend to be more glossy and Apple-like if you're into that. But as I said before watch out the one I used was a bit buggy, maybe write down your usage just in case!

---

### Post by Case04 on 2008-09-27
> **dhughes said:**
> There are some desklets/screenlets that will do that but the one I tried suddenly freaked out and went from a few GB to "200345566202" or something like that.

 Anyway install and then try some desklets or screenlets, gDesklets is in Applications>Add/Remove Applications then search for gDesklets and after that look around the categories to see the network monitors that are available.

**edit**: Actually use Screenlets I know that was the one where I found the Network Monitor that also measured the up and down amounts you sent and received. Screenlets can be found in Synaptic Package Manager, Screenlets tend to be more glossy and Apple-like if you're into that. But as I said before watch out the one I sed was a bit buggy, maybe write down your usage just in case!
I'll look into it, thanks.

Any other suggestions? Maybe one that isn't reportedly buggy?

Thanks.

---

### Post by dhughes on 2008-09-27
You could also look into using your router to track usage, I know Tomato does and DD-WRT (third-party replacements for a router's firmware) probably also has built-in tracking, but Tomato is also a big buggy as I found out the hard way after an update. And as you said you're a beginner so that may be a bit too complex at the moment.

---

### Post by Case04 on 2008-09-27
Yeah, I really couldn't find a suitable screenlet for my needs.

Really, I'm just trying to find something that starts automatically on login, keeps track of downloading and uploading on a daily basis over a monthly period and logging it so I could literally print it out at the end of the month.

None of those screenlets really had any sort of tracking or logging...

---

### Post by binbash on 2008-09-28
vnstat

---

### Post by robalcorn on 2008-09-28
If your provider is rogers you can go to their website rogers.com and create an account there you can see your daily usage of upl/dl activity.

---

### Post by Case04 on 2008-09-28
> **robalcorn said:**
> If your provider is rogers you can go to their website rogers.com and create an account there you can see your daily usage of upl/dl activity.
Ah, but there are others on my network who're blaming me for all the usage. I just want all the usage done by MY IP address or whatever they use to track individual connections. Rogers has already told me the total bandwidth used based on everyone on my network... 178GB in one month... doesn't that seem a bit HIGH to you guys?

---

### Post by Kevbert on 2008-09-28
The screenlet you require is Network Monitor which can be found [[COLOR="Red"]here[/COLOR]]("http://gnome-look.org/content/show.php/Net+Monitor?content=72013").  You can manually reset it whenever you want.

---

### Post by chalewa on 2008-09-28
i really don't know what i would do if i had a 95 gb cap

---

### Post by Case04 on 2008-09-28
> **Kevbert said:**
> The screenlet you require is Network Monitor which can be found [[COLOR="Red"]here[/COLOR]]("http://gnome-look.org/content/show.php/Net+Monitor?content=72013").  You can manually reset it whenever you want.
NetMonitor is exactly what I needed.. Thank you.

And thanks to everyone else who responded.

This forum is a great resource to make the switch from Windows to Ubuntu much easier.

Thanks again

---

### Post by dhughes on 2008-09-28
> **Case04 said:**
> ... 178GB in one month... doesn't that seem a bit HIGH to you guys?

 6GB per day seems very high to me.
 6GB is 51,539,607,552 bits in 30 days.
 2,147,483,648 bits or 256MB per hour!
 4M**Bytes** per second or 33.5Mbits/second
 
 
 So if I worked this out right you're getting downloads of 35Mbps which if my math is right I can't see you having. This is considering your connection being on all the time and acheiving those speeds of 35Mbps all day and all night.

 I may be wrong but it seems impossible that your connection can do this.

 **edit:** yeah I think I did that wrong, that should be 584Kbps * 24 hours is 6.1GBytes/day

---

### Post by psam3 on 2008-10-29
Imagine having a 17gb monthly limit ](*,)

---

### Post by I-75 on 2008-10-29
> **psam3 said:**
> Imagine having a 17gb monthly limit ](*,)

  17 GB is about the amount of podcasts I listen to a month...lol

---

