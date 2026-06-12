---
title: "Vpython help? program wont run"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by racs24 on 2012-11-23
[HTML] 
 
 
from __future__ import division
from visual import *
from visual.graph import *
 
basket=frame ()
 
basketball=sphere (color=(1,.3,0), radius=.25, mass=.57, pos=(0,-4,0))
hoop=ring (frame=basket, pos=(6.95,-1.5,0), color=color.red, axis=(0,1,0), radius=0.5, thickness=.05)
ground=box (pos=(10,-5,0), size=(4,.1,15), axis=(1,0,0), color=(0,.5,.9))
groundR=box (pos=(2,-5,9.5), size=(20,.1,4), axis=(1,0,0), color=(0,.5,.9))
groundL=box (pos=(2,-5,-9.5), size=(20,.1,4), axis=(1,0,0), color=(0,.5,.9))
court=box (pos=(0,-5,0), size=(16,.1,15), axis=(1,0,0), color=(.8,.7,.4))
pole=cylinder(frame=basket, pos=(8,-5,0), length=3.5, radius=.15, axis=(0,1,0),color=(.5,.5,.5))
backboard=box (frame=basket, size=(.1,2,3), pos=(7.5,-1,0))
support=box (pos=(8,-1.5,0), size=(1,.5,.5),color=(.5,.5,.5))
FTline=box (pos=(2,-4.999,0), size=(.1,.1,3))
FTR=box (pos=(5,-4.999,1.5), size=(6,.1,.1)) 
FTL=box (pos=(5,-4.999,-1.5), size=(6,.1,.1))
redline1=box (frame=basket, pos=(7.4999,-1.5,0), size=(.1,.1,1), color=color.red)
redline2=box (frame=basket, pos=(7.4999,-.75,0), size=(.1,.1,1), color=color.red)
redline3=box (frame=basket, pos=(7.4999,-1.125,.5), size=(.1,.75,.1), color=color.red)
redline2=box (frame=basket, pos=(7.4999,-1.125,-.5), size=(.1,.75,.1), color=color.red)
scoreboard=box (pos=(-8,5,0), size=(4,2,3), color=(.3,.3,.3))
SBsupp=cylinder (pos=(-8,6,0), length=2, radius=.1, axis=(0,1,0), color=(.3,.3,.3))
score= label(pos=scoreboard.pos, text='Scoreboard', zoffset=1, height=.05, border=.2, opacity=.2)
 
t=0
deltat=0.01
 
pick = None
picked=False
draging=True
firstClick=True
 
scene.autoscale = True
 
graph1 = gdisplay(x=429, y=0, width=600, height=350,
title='"Y" Velocity vs. Time', xtitle='time (s)', ytitle='v (m/s)',
xmax=45, xmin=0., ymax=20, ymin=-20,
foreground=color.black, background=color.white)
ballY = gcurve(gdisplay = graph1, color = color.black)
 
graph2 = gdisplay(x=429, y=350, width=600, height=350,
title='"X" Velocity vs. Time', xtitle='time (s)', ytitle='v (m/s)',
xmax=45, xmin=0., ymax=20, ymin=-20,
foreground=color.black, background=color.white)
ballX = gcurve(gdisplay = graph2, color = color.black)
 
basketball.velocity=vector(0,0,0)
 
 
while True:
    rate(140)
if basketball.pos.x+basketball.radius+(1/2)*backboard.size.x > backboard.pos.x: #backboard bounce
    if basketball.pos.x-basketball.radius-(1/2)*backboard.size.x: 
        if basketball.pos.y>backboard.pos.y-(1/2)*backboard.size.y-basketball.radius:
            if basketball.pos.y:
                if basketball.pos.z:
                    if basketball.pos.z>backboard.pos.z-(1/2)*backboard.size.z-basketball.radius:
                        basketball.velocity.x = -basketball.velocity.x
                    if basketball.pos.x-basketball.radius-(1/2)*scoreboard.size.x:
                        if basketball.pos.x+basketball.radius>scoreboard.pos.x-scoreboard.size.x:
                            if basketball.pos.y>scoreboard.pos.y-(1/2)*scoreboard.size.y:
                                if basketball.pos.y:
                                    basketball.velocity.x = -basketball.velocity.x
 
if basketball.pos.y+basketball.radius>scoreboard.pos.y-(1/2)*scoreboard.size.y: #scoreboard bounce
    if basketball.pos.y-basketball.radius:
        if basketball.pos.x:
            if basketball.pos.x>scoreboard.pos.x-(1/2)*scoreboard.size.x:
                basketball.velocity.y=-basketball.velocity.y
 
if basketball.pos.y-basketball.radius-(1/2)*backboard.size.y<=backboard.pos.y:#top of backboard
    if basketball.pos.y+basketball.radius+(1/2)*backboard.size.y>=backboard.pos.y:
        if basketball.pos.x>backboard.pos.x-(1/2)*backboard.size.x:
            if basketball.pos.x:
                basketball.velocity.y=-basketball.velocity.y
 
if basketball.pos.x+basketball.radius+pole.radius > pole.pos.x: #pole bounce
    if basketball.pos.x-basketball.radius-pole.radius:
        if basketball.pos.y>pole.pos.y-(1/2)*pole.length-basketball.radius:
            if basketball.pos.y:
                basketball.velocity.x=-basketball.velocity.x
 
if basketball.pos.x+basketball.radius>=hoop.pos.x-hoop.radius-hoop.thickness: #hoop bounce
    if basketball.pos.x-basketball.radius<=hoop.pos.x-hoop.radius+hoop.thickness:
        if basketball.pos.y:
            if basketball.pos.y>hoop.pos.y-hoop.thickness:
                basketball.velocity.x=-basketball.velocity.x
 
if basketball.pos.y-basketball.radius<=hoop.pos.y+hoop.thickness: #hoop bounce
    if basketball.pos.y+basketball.radius>=hoop.pos.y-hoop.thickness:
        if basketball.pos.x>=hoop.pos.x-hoop.radius-hoop.thickness:
            if basketball.pos.x<=hoop.pos.x-hoop.radius+hoop.thickness:
                basketball.velocity.y=-basketball.velocity.y
            if basketball.pos.x+basketball.radius>=hoop.pos.x+hoop.radius-hoop.thickness: #hoop bounce
                if basketball.pos.x-basketball.radius<=hoop.pos.x+hoop.radius+hoop.thickness:
                    if basketball.pos.y:
                        if basketball.pos.y>hoop.pos.y-hoop.thickness:
                            basketball.velocity.x=-basketball.velocity.x
 
if basketball.pos.y-basketball.radius<=hoop.pos.y+hoop.thickness: #hoop bounce
    if basketball.pos.y+basketball.radius>=hoop.pos.y-hoop.thickness:
        if basketball.pos.x>=hoop.pos.x+hoop.radius-hoop.thickness:
            if basketball.pos.x<=hoop.pos.x+hoop.radius+hoop.thickness:
                basketball.velocity.y=-basketball.velocity.y
            if basketball.pos.y-basketball.radius-(1/2)*ground.size.y<=ground.pos.y:
                basketball.velocity.y = -basketball.velocity.y
                basketball.velocity.y = .75*basketball.velocity.y #.75 = coefficient of restitution
                basketball.pos = basketball.pos + basketball.velocity*deltat
 
if basketball.pos.x<=-10:
    basketball.pos=(0,-4,0)
    basketball.velocity.x=0
    basketball.velocity.y=0
if basketball.pos.x>=15:
    basketball.pos=(0,-4,0)
    basketball.velocity.x=0
    basketball.velocity.y=0
 
if basketball.pos.y > ground.pos.y+ basketball.radius:
    basketball.pos=basketball.pos + basketball.velocity*deltat
 
if picked:
    basketball.velocity.y=basketball.velocity.y-(9.8*deltat)
 
if scene.mouse.events:
    m1 = scene.mouse.getevent() # get event
    if m1.drag and m1.pick == basketball: # if touched ball
        drag_pos = m1.pickpos # where on the ball
        pick = m1.pick # pick now true (not None)
    if firstClick:
        posOne=m1.pos
        t1=t
        firstClick=False
    elif m1.drop: # released at end of drag
        pick = None# end dragging (None is false)
        picked=True
        posTwo=m1.pos
        t2=t
        draging=false
    if pick:
        # project onto xy plane, even if scene rotated:
        new_pos = scene.mouse.project(normal=(0,0,1))
        if new_pos != drag_pos: # if mouse has moved
        # offset for where the ball was clicked:
            pick.pos += new_pos - drag_pos
            drag_pos = new_pos # update drag position
 
if not draging:
    velocityScale=0.5
    basketball.velocity.x=velocityScale*((posTwo.x-posOne.x)/(t2-t1))
    basketball.velocity.y=velocityScale*((posTwo.y-posOne.y)/(t2-t1))
    draging=True
    firstClick=True
 
#Graph Velocities
ballY.plot(pos = (t, basketball.velocity.y))
ballX.plot(pos = (t, basketball.velocity.x))
t=t+deltat
 
[/HTML]

---

