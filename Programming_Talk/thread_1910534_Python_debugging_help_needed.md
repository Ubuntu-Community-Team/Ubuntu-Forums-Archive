---
title: "Python debugging help needed"
date: 2012-01-16
forum: Programming Talk
---

### Post by hermatician on 2012-01-16
Hello Guys, 

I need your help. I am making a program in ABAQUS script/python for making a spring for which angle, pitch and Z values are given. 

I have made a program but unable to de-bug it please help. please.

```
from abaqus import *
from abaqusConstants import *
import __main__

def Macro2():
    import section
    import regionToolset
    import displayGroupMdbToolset as dgm
    import part
    import material
    import assembly
    import step
    import interaction
    import load
    import mesh
    import job
    import sketch
    import visualization
    import xyPlot
    import displayGroupOdbToolset as dgo
    import connectorBehavior

    
    theta = [0,3,6,9,12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,72,75,78,81]
    z = [-0.291,-0.291,-0.282,-0.276,-0.252,-0.224,-0.184,-0.145,-0.114,-0.084,-0.054,-0.027,0.001,0.029,0.051,0.074,0.101,0.127,0.157,0.188,0.214,0.24,0.264,0.288,0.311,0.333,0.355,0.375]
    outrad = 6.692
    pitch = [-0.291,0.009,0.007,0.024,0.028,0.04,0.04,0.031,0.03,0.03,0.027,0.028,0.028,0.023,0.023,0.027,0.026,0.03,0.031,0.026,0.026,0.024,0.024,0.024,0.021,0.022,0.02,0.019]
    for i in range(28):

        
        myList = [theta[i],z[i], pitch[i]]
        for i in range(28):
            key = [myList]

            
        

    for j in range(28):
                        

        s1 = mdb.models['Model-1'].ConstrainedSketch(name='__profile__', 
            sheetSize=200.0)
        g, v, d, c = s1.geometry, s1.vertices, s1.dimensions, s1.constraints
        s1.setPrimaryObject(option=STANDALONE)
        s1.ConstructionLine(point1=(0.0, -100.0), point2=(0.0, 100.0))
        s1.FixedConstraint(entity=g[2])
        s1.CircleByCenterPerimeter(center=((-outrad - 0.8)*cos(radians(key[j][0])),(-outrad - 0.8)*cos(radians(key[j][0])), key[j][2]), point1=(-outrad*cos(radians(key[j][0])),-outrad*sin(radians(key[j][0]),- key[j][2]))
        p = mdb.models['Model-1'].Part(name='Part-1', dimensionality=THREE_D, 
            type=DEFORMABLE_BODY)
        p = mdb.models['Model-1'].parts['Part-1']
        p.BaseSolidRevolve(sketch=s1, angle=key[j][0], flipRevolveDirection=OFF, 
            pitch=key[j][2], flipPitchDirection=OFF, moveSketchNormalToPath=OFF)
        s1.unsetPrimaryObject()
        p = mdb.models['Model-1'].parts['Part-1']
        session.viewports['Viewport: 1'].setValues(displayedObject=p)
        del mdb.models['Model-1'].sketches['__profile__']
```

---

### Post by sffvba[e0rt on 2012-01-17
Post moved to own thread.


404

---

### Post by Tony Flury on 2012-01-17
You don't say what actual error you are getting, or whether your code runs but fails to produce the expected value.

If you are just getting the wrong value - Have you used a liberal sprinkling of "print" statements through your code to make sure you are getting the right values at each step.

If you are getting a run-time traceback error - what is the error ? That can often be a good pointer to where the issue is.

A few style pointers : 

```

from <module> import *

```
is usually not considered a great idea as it adds a lot of stuff into the global namespace - and therefore will hide clashes (modules with the same name in different packages, or modules with the same name as built-ins for example).

```

import __main__

```
just seems plain odd to me - can you give a pointer why you do that ?

Importing modules just inside a function - not a great idea - where are all of those modules defined - they don't look like standard ones.

Also your Macro2 is not being called from anything in the code you have provided - I assume this script is executed as part of a bigger program ?

---

### Post by CoffeeRain on 2012-01-17
Could you post your error message?

---

