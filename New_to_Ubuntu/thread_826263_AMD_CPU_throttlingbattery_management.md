---
title: "AMD CPU throttling/battery management"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by TitanTiger on 2008-06-11
I have an Acer 5002wlmi laptop with an AMD Turion processor.  The battery lasts noticeably longer when running Windows than it does running Ubuntu.  A friend told me it was likely due to Windows throttling back the processor when on battery power and Ubuntu not doing that.  But he thought there was a way to manually manage the processor in Ubuntu.  I'm not sure what I should install or how to manage that and don't want to screw up my laptop trying.

Will something called "emifreq-applet" do what I need or is there something else I should do with this specific processor?

---

### Post by TitanTiger on 2008-06-12
bump

---

### Post by prshah on 2008-06-12
> **TitanTiger said:**
> I have an Acer 5002wlmi laptop with an AMD Turion processor.  The battery lasts noticeably longer when running Windows than it does running Ubuntu.  


If your CPU can be frequency-managed, most likely ubuntu will already be doing it. You can check with the following commands```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
cat /proc/cpuinfo
```

Actually only the first command will tell you if it is being powermanaged; the others will give more information that will be useful to debug the problem.

If you get "ondemand" or "powersave" for the first command then it is already being managed. To see it in action, right click a blank space on your ubuntu bar, choose "Add to Panel.." and add the applet "CPU frequency scaling monitor"

---

### Post by sdennie on 2008-06-12
There are also good resources for drastically improving battery life on Linux.  Check [www.lesswatts.org](www.lesswatts.org).  Also, while on battery power, try the powertop tool in the terminal:

```

sudo apt-get install powertop
sudo powertop

```

---

### Post by TitanTiger on 2008-06-13
Ok, I ran the scaling_governor commands and ondemand is managing it.  But it doesn't seem to do a good job.

I installed powertop and ran it and it suggests enabling "ac97 powersave" mode or something like that.  What does that mode do and how easy is it to reverse it?

---

### Post by cariboo on 2008-06-13
Check out this link:

[http://www.thinkwiki.org/wiki/How_to_enable_AC97_power_saving](http://www.thinkwiki.org/wiki/How_to_enable_AC97_power_saving)

Took two seconds to find it with Google.

JIm

---

### Post by TitanTiger on 2008-06-13
> **cariboo907 said:**
> Check out this link:

[http://www.thinkwiki.org/wiki/How_to_enable_AC97_power_saving](http://www.thinkwiki.org/wiki/How_to_enable_AC97_power_saving)

Took two seconds to find it with Google.

JIm
I appreciate that, but I did Google it first.  The links I was finding were discussions that seemed to assume everyone already knew what it was.  I must have missed that link somehow.

---

### Post by walmartshopper67 on 2008-06-17
I've always used the cpufreq package (it's in the repos somewhere) to scale my processor, which makes a HUGE difference on battery life. The other key to longer battery life is dimming the screen, and turning the wifi card off if you're not using it.

---

