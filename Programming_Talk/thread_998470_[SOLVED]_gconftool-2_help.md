---
title: "[SOLVED] gconftool-2 help"
date: 2008-11-30
forum: Programming Talk
---

### Post by anotherdisciple on 2008-11-30
I am writing a quick BASH script with a zenity GUI... one thing I wanted to add is the option to change the main-menu icon. In the gconf-editor you would change

```
/apps/panel/objects/[COLOR="Red"]*[/COLOR]/use_custom_icon
```

to true, and
```

/apps/panel/objects/[COLOR="Red"]*[/COLOR]/custom_icon
```

to the location of the new icon.

My problem... The "[COLOR="Red"]*[/COLOR]" could be different for each user.... it may be object_1, object_3, etc.

So, how can make the script only use the key for the object whose object_type is "menu-object"?


I'm stumped!!! Help me figure this one out!

---

### Post by anotherdisciple on 2008-11-30
Okay... here is what I have so far...

```
nick@nick-laptop:~$ gconftool-2 --search-key object_type | grep menu-object | awk '{print $1}'

```

... and that returned this:
```
/apps/panel/objects/object_0/object_type
```

Now, how do I remove the object_type leaving just "/apps/panel/objects/object_0/" ?

---

### Post by anotherdisciple on 2008-12-01
... so basically you would add this pipe:

```
| sed 's/object_type//'
```

Fort Wayne Linux User Group is faster than you... haha.. but there is the answer if anyone needs it!

---

