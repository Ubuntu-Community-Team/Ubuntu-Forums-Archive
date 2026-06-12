---
title: "Setting &quot;quod libet&quot; as default"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by acimi66 on 2012-12-06
I recently downloaded "Quod Libet" from the SC but it does not show up as a default option in the system settings - default apps

Any work arounds?

---

### Post by levlaz on 2012-12-06
This is kind of a backwards workaround but it should work. 

Assuming you are going to be using this app as your default player to listen to .mp3 you can find an .mp3 file on your computer, right click on it, and select the properties. Under the default applications you can change it to whatever you want. 

Now whenever you open an .mp3 it will automatically open with Quod Libet. You can do this for whatever other type of files you are going to be using with it. 

Not sure why it is not showing up as an option under system defaults. I think this little fix will work until a better workaround comes around.

---

### Post by acimi66 on 2012-12-06
Thanks for the reply.
nice idea but doesn’t work either, even when i go to find applications online quod libet is not in the list.

I guess it must be in a config file somewhere...any thoughts?

---

### Post by levlaz on 2012-12-06
I found a solution for *my* workaround. 

I noticed that in 12.10, in the properties of a file "adding a custom command" is greyed out.  To fix this you need to install ubuntu-tweak 

Look at the bottom of [this posting ]("http://askubuntu.com/questions/145243/where-did-open-with-user-defined-command-go")

Once ubuntu-tweak is installed you should be able to use the method that I talked about and enter a custom command. For this specific application the command that you want to use is 

```
 quodlibet --play-file %F
```

EDIT: To add the custom command, right click on the file type, go to properties --> open with --> add (it should no longer be greyed out) 


[INDENT][LEFT]
[/LEFT]
[/INDENT]

---

### Post by acimi66 on 2012-12-09
Yeah, This final worked. Thanks for the help

---

