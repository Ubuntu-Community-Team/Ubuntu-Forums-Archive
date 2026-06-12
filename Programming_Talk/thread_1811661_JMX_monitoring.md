---
title: "JMX monitoring"
date: 2011-07-25
forum: Programming Talk
---

### Post by newelfik on 2011-07-25
Hi,

I'm looking for an API to monitor remote JVM (remote it's means 'between users on a same workstation').

The JVM are ever devellop, so I would like API which don't need to touch the specifics JVM. So no MBeans...

I'm looking in JMX connectors but it's seams that they need always MBeans.

Have you got any advice ?

---

### Post by slavik on 2011-07-25
> **newelfik said:**
> Hi,

I'm looking for an API to monitor remote JVM (remote it's means 'between users on a same workstation').

The JVM are ever devellop, so I would like API which don't need to touch the specifics JVM. So no MBeans...

I'm looking in JMX connectors but it's seams that they need always MBeans.

Have you got any advice ?
umm, JMX specification calls for mbeans to do rmi ... that is how the jvm spec is.

how exactly do you imagine monitoring a jvm without mbeans?

---

### Post by newelfik on 2011-07-25
Hmm, I would say without edit the code so much.

I'm reading that I have to use them yes..

Because It's seams that it exists a real difference between java5 and 6 and i would like to stay a maximum in version5.

I don't need to edit remote object. Only profiling data like check name of an object, or something like that.

---

### Post by slavik on 2011-07-25
> **newelfik said:**
> Hmm, I would say without edit the code so much.

I'm reading that I have to use them yes..

Because It's seams that it exists a real difference between java5 and 6 and i would like to stay a maximum in version5.

I don't need to edit remote object. Only profiling data like check name of an object, or something like that.
JMX does not do code profiling. You can only gather information and invoke operations that are exposed via MBeans. If you don't need to edit the remote object, then don't edit it ...

If you want to profile your code, look into something like Wily, Foglight, AppDynamics.

---

### Post by newelfik on 2011-07-26
These 3 technologies don't get java API to edit externs application.

(And Wily doesn't exist anymore).

The goal is to develop java application which can display information about other JVM on the same workstation like value data or heapsize.

---

### Post by slavik on 2011-07-26
JMX allows you to attach to other processes (this is what jstat does).

---

