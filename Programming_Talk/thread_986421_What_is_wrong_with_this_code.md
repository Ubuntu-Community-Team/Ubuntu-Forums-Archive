---
title: "What is wrong with this code?"
date: 2008-11-18
forum: Programming Talk
---

### Post by jluksetich07 on 2008-11-18
This is a code I wrote for VPython and I can't figure out why it won't run. It keeps telling me there is a "Token Error: EOF in Multi-Line Statement" but I tried fixing the perenthises and nothing worked. Also, somethings it tells me there is something wrong with my tabliture and I dont think there is... here is a copy of the code... if you know what might be wrong please tell me and I will try it!
NOTE: Since this can't sense the tabs I have... there are tabs before "rate(50)" until "sate.trail.append(pos=sate.pos)" and there is a double tab before "stage".


from visual import*

ms=173
me=5.9E24
mm=7.35E22
rm=1.74E6
x=50
dtot=3.85E8
G=6.67E-11
vo=vector(10,0,0)

scene.center=((-dtot/2),0,0)

sate=box(pos=(0,0,0)),size=(200,200,1), color=color.orange
sate.trail= curve(color=color.yellow)
earth= sphere(pos=((-x-re),-10,0)), radius=re, color=color.blue
moon= sphere(pos=((dtot-x+rm),0,0), radius=rm, color=color.white

fm=(G*mm*ms)/((dtot+rm-x)*(dtot+rm-x))

fe=(G*me*ms)/((re+x)*(re+x))

sate.momentum=ms*vo
sate.velocity=sate.momentum/ms
sate.forces=vector((fm-fe),0,0)

t=0
dt=10

go=1
while (go==1):
    rate(50)
    t=t+dt

    fm=(G*mm*ms)/((dtot+rm-sate.pos.x)*(dtot+rm-sate.pos.x))
    fe=(G*me*ms)/((re+sate.pos.x)*(re+sate.pos.x))
    sate.forces=vector((fm-fe),0,0)
    sate.momentum=sate.momentum+sate.forces
    sate.velocity=sate.momentum/ms
    sate.pos+sate.pos+sate.velocity*dt

    sate.trail.append(pos=sate.pos)

        stage=2

---

### Post by Tony Flury on 2008-11-18
can you repost your code using code tags : - click the # in the toolbar - that way we can see your indentation - rather than try to mentally recreate it :-)

Also i would suggest that using tabs is a bad idea - use spaces, and set up your favourite editor to replace the tab key with 4 (or 6 or 8) spaces.

Thanks

---

### Post by stevescripts on 2008-11-18
> **Tony Flury said:**
> can you repost your code using code tags : - click the # in the toolbar - that way we can see your indentation - rather than try to mentally recreate it :-)

Also i would suggest that using tabs is a bad idea - use spaces, and set up your favourite editor to replace the tab key with 4 (or 6 or 8) spaces.

Thanks

+1 - see this link :[http://ubuntuforums.org/showthread.php?t=641693]("http://ubuntuforums.org/showthread.php?t=641693")

Steve

---

### Post by fiddler616 on 2008-11-18
OP seems to have gone AWOL for a bit, so here's this to give us more time to ponder it:
[php]
from visual import*

ms=173
me=5.9E24
mm=7.35E22
rm=1.74E6
x=50
dtot=3.85E8
G=6.67E-11
vo=vector(10,0,0)

scene.center=((-dtot/2),0,0)

sate=box(pos=(0,0,0)),size=(200,200,1), color=color.orange
sate.trail= curve(color=color.yellow)
earth= sphere(pos=((-x-re),-10,0)), radius=re, color=color.blue
moon= sphere(pos=((dtot-x+rm),0,0), radius=rm, color=color.white

fm=(G*mm*ms)/((dtot+rm-x)*(dtot+rm-x))

fe=(G*me*ms)/((re+x)*(re+x))

sate.momentum=ms*vo
sate.velocity=sate.momentum/ms
sate.forces=vector((fm-fe),0,0)

t=0
dt=10

go=1
while (go==1):
         rate(50)
    
         t=t+dt

    
         fm=(G*mm*ms)/((dtot+rm-sate.pos.x)*(dtot+rm-sate.pos.x))

         fe=(G*me*ms)/((re+sate.pos.x)*(re+sate.pos.x))

         sate.forces=vector((fm-fe),0,0)

         sate.momentum=sate.momentum+sate.forces

         sate.velocity=sate.momentum/ms

         sate.pos+sate.pos+sate.velocity*dt

         sate.trail.append(pos=sate.pos)

                      stage=2[/php](I *think* that's it...)

---

