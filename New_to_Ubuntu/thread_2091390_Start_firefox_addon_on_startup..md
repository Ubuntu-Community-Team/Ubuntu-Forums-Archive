---
title: "Start firefox addon on startup."
date: 2012-12-05
forum: New to Ubuntu
---

### Post by Crisislord on 2012-12-05
I want to start Dta when my ubuntu starts up. how can i do that.
I looked at this tread
>  [http://ubuntuforums.org/showthread.php?t=1256699&highlight=start+firefox+addon+from+terminal](http://ubuntuforums.org/showthread.php?t=1256699&highlight=start+firefox+addon+from+terminal)
But when i do
> firefox -chrome chrome://dta/content/dta/manager.xulTHe manager is all white i cannot access my downloads as well as i manage it and stays like so:
[IMG]http://contantine.comule.com/new/dta.png[/IMG]

---

### Post by vasa1 on 2012-12-05
> **Crisislord said:**
> I want to start Dta when my ubuntu starts up. how can i do that.
...

It's a Firefox add-on and **won't start** without Firefox starting. I'm not sure you can "start Dta when my ubuntu starts up".

And re.
"firefox -chrome chrome://dta/content/dta/manager.xul", that comes from an old thread and it's quite possible that what worked then won't work now.

In any case, could you please explain what exactly you're trying to do?

---

### Post by Crisislord on 2012-12-05
Well sorry for the crappy english :P.

Here is the deal:
Lets suppose i want Skype to start when i boot Ubuntu, i would just add Skype as a command in start-up application to boot it.

I want to start a firefox addon when Ubuntu boot. In this case it is DTA.
Like marshall explained, in order for dta to start downloading the dta manager much be opened after firefox has been loaded, I just want to automate these step and make it all start when ubuntu boot.

I just want to know the the sets of command that will make it possible.
When i try the previous commands i mentioned above the manger stay like in the picture and the downloads inside cannot be manipulated.

---

### Post by black veils on 2012-12-05
essentially you want a firefox add-on to start with ubuntu, but the add-on can only start with firefox, thus you need to add firefox to the start-up applications.

the command should just be [I][B]firefox

[/B][/I]if you need to add a delay for some start-up applications, here is a command example ```
sh -c "sleep 5m; skype"
```
the number is the minutes, skype is the app.

---

### Post by Crisislord on 2012-12-05
WEll the addon (downloadthemall) has a gui and inorder for  the downloads to start you need to start the gui after you have opened firefox. It does not do it automatically.

---

### Post by Crisislord on 2012-12-14
bump

---

