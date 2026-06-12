---
title: "Razer Abyssus driver issue."
date: 2014-02-21
forum: New to Ubuntu
---

### Post by David_Willou on 2014-02-21
Hi, 

I was looking for a good answer about Razer Abyssus sensivity.
I was found this thread without any answer : [http://ubuntuforums.org/showthread.php?t=2073071&p=12303914#post12303914](http://ubuntuforums.org/showthread.php?t=2073071&p=12303914#post12303914)

The good answer (for me) is other there : [http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/](http://patrickmylund.com/blog/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/)

Here is the way to do it.

**1. Identified you mouse**

```
  $ xinput --list --short&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Razer  Razer Abyssus                        id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Logitech HID compliant keyboard             id=8    [slave  keyboard (3)]
    &#8627; Logitech HID compliant keyboard             id=9    [slave  keyboard (3)]
```
[B]2. Find the good settings for you
[/B](Here's mine)

```
$ xinput --set-prop "Razer  Razer Abyssus" "Device Accel Constant Deceleration" 1.5
$ xinput --set-prop "Razer  Razer Abyssus" "Device Accel Velocity Scaling" 1
```

3. Create a script

```
#!/bin/sh
xinput --set-prop "Razer  Razer Abyssus" "Device Accel Constant Deceleration" 1.5
xinput --set-prop "Razer  Razer Abyssus" "Device Accel Velocity Scaling" 1
```


4. Configure gnome to use this script during opening session

```
$ gnome-session-properties
```

[B][U]That's all !

[/U][/B]
Bye bye and have fun.
David

---

