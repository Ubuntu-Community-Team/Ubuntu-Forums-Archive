---
title: "interface for network-manager"
date: 2006-03-26
forum: Programming Talk
---

### Post by zachtib on 2006-03-26
where can i find a howto to create a custom frontend for networkmanager
im working on a carpc project. id like to use networkmanager to manage connections, but i want to build the interface into the main programs gui

---

### Post by moephan on 2006-03-26
Zachtib,

I'll be very interested to see responses to this. I asked a similar question a few months ago. I ended up interacting with it via the command line. For example, to let the user configure a wireless interface, I ended up with python code like this:

```

subprocess.call(["network-admin", "-c", interfacename])

```

where "interfacename" was a variable for the interface to configure. This pops up just the configuration dialog for that interface over my window and returns control to my window when the user is done with it.	

You probably know this, but for completeness I'll suggest:
```

network-admin --help-all

```

to see all the command line options.

Cheers, Rick

---

