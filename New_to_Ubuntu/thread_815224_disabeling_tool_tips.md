---
title: "disabeling tool tips"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by fminmexico on 2008-06-01
How do you disable tool tips.The other post does not say how to disable them.
 fminmexico.

---

### Post by K.Mandla on 2008-06-01
Moved to Absolute Beginner Talk.

---

### Post by alzie on 2008-06-01
I believe this link will tell you what you need to know:

[http://ubuntuforums.org/showthread.php?t=672864](http://ubuntuforums.org/showthread.php?t=672864)

I hope this helps :)

---

### Post by angry_johnnie on 2008-06-02
Press **Alt + F2**

Type  **gconf-editor** and press enter.

In the window that will open, find **Apps > Panel > Global > Tooltips_enabled**

Uncheck the box.

They're gone!

Edit:  Whoops, nevermind.  I still have to figure out a way to get nautilus not to show them...

---

### Post by mcduck on 2008-06-02
The only way I know to _completely_ get rid of tooltips in every program is to configure Compiz to display them with 0 opacity (thus making all tooltips invisible).

---

### Post by sdennie on 2008-06-02
mcduck: That is an entertaining but probably very valid way to do it.

---

### Post by fminmexico on 2008-06-02
> **mcduck said:**
> The only way I know to _completely_ get rid of tooltips in every program is to configure Compiz to display them with 0 opacity (thus making all tooltips invisible).

Could you please give me a step by step on how to do that.
    fminmexico.

---

### Post by sdennie on 2008-06-02
```

sudo apt-get install compizconfig-settings-manager

```

Then go to System->Preferences->Advanced Desktop settings.  Click General Options and then go to the Opacity Settings tab.  Click New and add a rule.  Make the a rule that is simply Tooltip.  Set the opacity value to 0.

---

### Post by fminmexico on 2008-06-03
> **vor said:**
> ```

sudo apt-get install compizconfig-settings-manager

```

Then go to System->Preferences->Advanced Desktop settings.  Click General Options and then go to the Opacity Settings tab.  Click New and add a rule.  Make the a rule that is simply Tooltip.  Set the opacity value to 0.

There is no Advanced Desktop settings in my preferences only desktop effects/background/remote.When I try the sudo apt-get install compizconfig-settings-manager  I get Reading package lists... Done
Building dependency tree       
Reading state information... Done E: Couldn't find package compizconfig-settings-manager

    fminmexico.

---

### Post by sdennie on 2008-06-03
That's odd that you can't install it.  You may want to look at System->Administration->Software Sources and insure that you have things enabled.  After that:

```

sudo apt-get update
sudo apt-get install compizconfig-settings-manager

```

---

