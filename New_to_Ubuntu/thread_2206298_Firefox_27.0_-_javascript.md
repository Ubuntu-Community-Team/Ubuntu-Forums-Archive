---
title: "Firefox 27.0 - javascript"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by benoit3 on 2014-02-18
Today Ubuntu proposed an update of Firefox, which I did install and since then javascript does not work anymore. When I go to Preferences/Content there is no longer a box where you enable/disable java. Thanks for helping.

---

### Post by Dave_L on 2014-02-18
See [http://stackoverflow.com/questions/18093222/enable-disable-javascript-in-firefox-23](http://stackoverflow.com/questions/18093222/enable-disable-javascript-in-firefox-23)

---

### Post by vasa1 on 2014-02-18
> **benoit3 said:**
> Today Ubuntu proposed an update of Firefox, which I did install and since then javascript does not work anymore. When I go to Preferences/Content there is no longer a box where you enable/disable java. Thanks for helping.
Advance apologies if I'm misunderstanding things but ...

[LIST]
[*]Javascript is different from Java
[*]The option to disable javascript [has been removed from Preferences]("https://support.mozilla.org/en-US/questions/969764") because Mozilla claimed users were accidentally turning of javascript and then wondering why things didn't work
[*]The Java plugin haa been deemed injurious to health [and is disabled in recent versions of Firefox]("https://blog.mozilla.org/addons/2013/01/11/protecting-users-against-java-vulnerability/"). You should see mention of that in about:plugins if you had the Java plug-in installed
[/LIST]

---

### Post by benoit3 on 2014-02-18
Sorry to have provoked some confusion. The problem is that javascript is not working anymore.

---

### Post by vasa1 on 2014-02-18
> **benoit3 said:**
> ... The problem is that javascript is not working anymore.
How do you know?
If you need help you'll be better off providing more information.

---

### Post by benoit3 on 2014-02-19
What do you need for information. When I try to use Gmail I get the following message: "JavaScript must be enabled in order for you to use Gmail in standard view. However, it seems JavaScript is either disabled or not supported by your browser. To use standard view, enable JavaScript by changing your browser options, then try again."

---

### Post by JeQhdMD on 2014-02-19
See the link below  .. .. the settings can be changed via "right mouse click",

[https://support.mozilla.org/en-US/questions/975415](https://support.mozilla.org/en-US/questions/975415)

---

### Post by monkeybrain20122 on 2014-02-19
Can you test it with a different profile?

P.s. I think the javascript options are in about:config, if you search "dom" there are a whole bunch of stuffs, maybe somehow your default values have changed.

---

### Post by benoit3 on 2014-02-19
This is solved. in the about:config I found the solution. Thanks a lot.

---

