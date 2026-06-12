---
title: "Using root priv. within Python"
date: 2011-07-04
forum: Programming Talk
---

### Post by KoolPenguin on 2011-07-04
Is there a way to execute a series of commands with only having to ask for the root password once?  The first code is what I have now and the second is what I attempted to do but only the first command is completed as root and not the second.

```

            os.system("gksudo rm " + localBin + "/minecraft_server")
            os.system("gksudo rm " + usrApps + "/minecraft_server.desktop")

```
```

            os.system("gksudo rm " + localBin + "/minecraft; rm " + usrApps + "/minecraft.desktop")

```

...or is there another way of doing this all together?

Thanks
--
Chris

---

### Post by Arndt on 2011-07-04
> **KoolPenguin said:**
> Is there a way to execute a series of commands with only having to ask for the root password once?  The first code is what I have now and the second is what I attempted to do but only the first command is completed as root and not the second.

```

            os.system("gksudo rm " + localBin + "/minecraft_server")
            os.system("gksudo rm " + usrApps + "/minecraft_server.desktop")

```
```

            os.system("gksudo rm " + localBin + "/minecraft; rm " + usrApps + "/minecraft.desktop")

```

...or is there another way of doing this all together?

Thanks
--
Chris

```
os.system("gksudo sh -c '(command1; command2)'")
```

ought to work. Since both your commands are 'rm', you can also do this:

```
os.system("gksudo rm " + localBin + "/minecraft_server " + usrApps + "/minecraft_server.desktop")
```

---

### Post by KoolPenguin on 2011-07-04
@Arndt

That did it!

Thanks
--
Chris

---

### Post by juancarlospaco on 2011-07-04
Remember that theres no gksudo on KDE...

---

### Post by KoolPenguin on 2011-07-04
> **juancarlospaco said:**
> Remember that theres no gksudo on KDE...

Yes, I know.  However, there is an apt-get install gksu command tho. :)

Best
--
Chris

---

