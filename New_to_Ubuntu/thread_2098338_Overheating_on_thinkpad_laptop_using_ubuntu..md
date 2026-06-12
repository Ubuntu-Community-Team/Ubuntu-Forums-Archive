---
title: "Overheating on thinkpad laptop using ubuntu."
date: 2012-12-26
forum: New to Ubuntu
---

### Post by Rajat Channan on 2012-12-26
Hi , i am a first time user of linux currently on 12.10 . 
I am having a problem with my system temp and my laptop overheating and shutting down while playing even weak games through wine. the problem is that this also used to happen in windows but before playing a game i used the turbo boost function in thinkpad powermanager and the fan used to become very fast and the game used to run perfectly without any overheat. now i cant find thinkpad powermanager software for linux and i have seen some threads on increasing fan speed manually but have not understood the process ........ can someone please help me out with a very basic step by step solution ?

My specs:
Lenovo TP-L420
i3
4gb ram
hd 300 graphics.

---

### Post by audiomick on 2012-12-26
Since you say you also have or had problems in Windows, I would consider the possibility that the machine is not cooling properly for reasons that have not to do with any software. You shouldn't have to provoke the machine to turn the fan up, at least not in Windows. I know that fan control is sometimes not optimal in the Linux world. Having said that, the tendency seems to be that the fan runs at full speed all the time rather than that it runs too slow. Anyway...

Did the machine behave like this from new, or did it develope the problem over time?

Is it possible that is needs to have the dust blown out? How old is the machine?

If the machine is a bit older, and the problem developed over time, you might want to think about renewing the thermal paste on the CPU and so on.

---

### Post by Rajat Channan on 2012-12-27
No this overheating only used to happen when i used to play heavy games like crysis etc. to avoid this i had to swithc on turbo boost mode , that did something that used to make the game run perfectly... i noticed the fan getting quicker on activation of turbo mode...... this had always been the case since i got the laptop........ i just need a substitute to turbo boost on linux.

---

### Post by superDave972 on 2012-12-27
Perhaps this will be of some assistance

[Put your mouse here and CLICK!]("http://askubuntu.com/questions/37618/is-turbo-boost-working")

---

### Post by audiomick on 2012-12-27
> **Rajat Channan said:**
> .. that did something that used to make the game run perfectly... i noticed the fan getting quicker on activation of turbo mode.......

What the turbo boost button does is increase the processor speed. That is why the games ran smoother. The increase in fan speed is either triggered by the sensors sensing that the CPU is getting warm, or simply that the turbo button switches the fan to maximum when it is activated. The latter would be logical, because the CPU will always run hotter when is has been sped up.


Regarding your problem, I can't really help directly, but I did find this.

[https://github.com/Stanko/ThinkPad-Fan-Control#readme]("https://github.com/Stanko/ThinkPad-Fan-Control#readme")

which is also referred to here

[http://www.thinkwiki.org/wiki/How_to_control_fan_speed]("http://www.thinkwiki.org/wiki/How_to_control_fan_speed")

Perhaps that would be of some help.

---

