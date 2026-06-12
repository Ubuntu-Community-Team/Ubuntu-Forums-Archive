---
title: "ValueError: setting an array element with a sequence"
date: 2011-03-03
forum: Programming Talk
---

### Post by ayamgolek on 2011-03-03
here is my python programme for a runge-kutta ode. but i dont know how 2 make it right... please help me...
 
import math,numpy
 
def rk4_odesolve(d_config_by_dt, config_start,
t0, t_max, nsteps):
 
      """return the approximation using runge-kutta"""
 
          dt = (t_max-t0)/float(nsteps)
          s = config_start
          for n in range(nsteps):
          s1=d_config_by_dt*(s,t0+n*dt)
          s2=d_config_by_dt*(s+numpy.dot(0.5*dt,s1),t0+(n+0.5)*dt)
          s3=d_config_by_dt*(s+numpy.dot(0.5*dt,s2),t0+(n+0.5)*dt)
          s4=d_config_by_dt*(s+numpy.dot(dt,s3),t0+(n+1)*dt)
 
return s+(1/6)*dt*(s1+2*s2+2*s3+s4)

---

### Post by cgroza on 2011-03-03
Please put the code in code tags, the indentation has been lost and the code is almost unreadable.

---

### Post by ayamgolek on 2011-03-03
im sorry,but how do i do that?

---

### Post by cgroza on 2011-03-03
When you click New Reply, an editor will show up, look for a # button to insert the tags.

---

