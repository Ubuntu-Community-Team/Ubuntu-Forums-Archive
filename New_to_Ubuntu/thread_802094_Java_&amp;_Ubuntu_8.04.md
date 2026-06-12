---
title: "Java &amp; Ubuntu 8.04"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Azalar on 2008-05-21
I have a new laptop which I have installed Ubuntu 8.04 on and need to get the laptop setup with the Java plugin for Firefox 3 beta 5 and for Java development with Net Beans.
In the last version of Ubuntu I had on my home pc I had problems, especially getting the plugin to work as there was a non standard version of Java pre-installed.
I was wondering what procedure I would need to go through to get Java working in Firefox and then working with Net Beans so I don't have similar problems like last time.

thanks
Az

---

### Post by billgoldberg on 2008-05-21
> **Azalar said:**
> I have a new laptop which I have installed Ubuntu 8.04 on and need to get the laptop setup with the Java plugin for Firefox 3 beta 5 and for Java development with Net Beans.
In the last version of Ubuntu I had on my home pc I had problems, especially getting the plugin to work as there was a non standard version of Java pre-installed.
I was wondering what procedure I would need to go through to get Java working in Firefox and then working with Net Beans so I don't have similar problems like last time.

thanks
Az

If you installed the restricted ubuntu extras, first thing to do is to remove "open-java".

You can do this in synaptic.

In synaptic then search for "sun java6" and download the needed packages.

---

### Post by Azalar on 2008-05-21
Thanks for the reply.
I didn't have open-java installed.
Have they changed this since the last version of Ubuntu as I am sure it had a default Java installed as a default.
I searched in Synaptic sun java6 as you suggested and this has returned a few results.
I generally download Net Beans with Java bundled so I probably don't need the development kit. I'm guessing I need to install the plugin for use with the latest Firefox but will there be any conflicts installing this and then allowing the normal sdk via Net Beans?

---

