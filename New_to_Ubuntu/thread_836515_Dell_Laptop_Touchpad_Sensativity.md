---
title: "Dell Laptop Touchpad Sensativity"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Grendel336 on 2008-06-21
I have a Dell Inspiron E1505 laptop and I'm a super-newb with Ubuntu and Linux in general. 

I am a member of numerous forums. When I am surfing about, or posting, there are many times when moving the curser around using the touchpad that I inadvertently highlight and move text without intending to, or even have the entire page click over to something else without intention. Like I clicked something, but I didn't. 

Is this my touchpad software doing that, or am I doing something that's harmless in windows OS, yet triggers something in ubuntu?

---

### Post by sdennie on 2008-06-21
I have the same problem with an XPS m1330.  I don't use tap clicking so I disabled it with System->Preferences->Mouse->Touchpad->Enable Mouse Clicks with Touchpad.  That solves the problem but, if you use tap clicking, it may not be ideal (though, it's easy to train yourself to not use it).

---

### Post by Grendel336 on 2008-06-21
Thanks. I checked, and touchpad clicks was enabled. 
I clicked it off and I'll see if that fixed things.

---

### Post by anewguy on 2008-06-21
Have you tried the synaptics (sp?) package?  It lets you configure your touchpad.  It's in the packages seen in synaptics package manager.

---

### Post by unutbu on 2008-06-21
I think the package anewguy is referring to is gsynaptics.

```

apt-cache show gsynaptics

Description: configuration tool for Synaptics touchpad driver of X server
 GSynaptics is a GUI configuration tool for the Synaptics touchpad
 driver of the X server.  This allows for modifications of the driver
 parameters on the fly.
```

---

### Post by anewguy on 2008-06-23
> **unutbu said:**
> I think the package anewguy is referring to is gsynaptics.

```

apt-cache show gsynaptics

Description: configuration tool for Synaptics touchpad driver of X server
 GSynaptics is a GUI configuration tool for the Synaptics touchpad
 driver of the X server.  This allows for modifications of the driver
 parameters on the fly.
```

That's exactly it - thanks for getting the correct name for me!  I've used that in the past to configure all sorts of things on a touchpad.:)

---

