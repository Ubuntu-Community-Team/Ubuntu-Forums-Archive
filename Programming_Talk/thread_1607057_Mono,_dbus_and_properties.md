---
title: "Mono, dbus and properties"
date: 2010-10-27
forum: Programming Talk
---

### Post by hurra on 2010-10-27
Hello experts

I'm working on a project, and have run into two problems regarding mono and dbus. 

First up, I have managed to get some simple mono and dbus example running, where I connect to the NetworkManager. I have implemented a few methods and signals/events, and both seems to work. 

My example looks something like this:
```
[Interface(“org.freedesktop.NetworkManager”)]
public interface INetworkManager : Introspectable
…

INetworkManager nmProxy = conn.GetObject<INetworkManager>(“org.freedesktop.NetworkManager”, new ObjectPath(“/org/freedesktop/NetworkManager”));
```

And after this, I'm able to invoke the methods I have implemented, and receive signals.

My problem is now with the properties. How do I get access to them? Is it supported in ndesk-sharp (using version 0.6) at all? If not, can I make it work through a simple hack or will I have to write a wrapper in e.g. C++? Basically I'm only interested in the getters, so the hack I could imagine would be calling the getter methods directly.

My next problem is probably really simple, but I can not figure it out anyway. I have been using D-Feet to browse my dbus. I can see that the NetworkManager publish several interfaces, among others Devices. How do I connect to that interface? By applying simple intuition to the information from d-feet

```
[Interface(“org.freedesktop.NetworkManager.Device.Wired”)]
public interface IDevice : Introspectable
…

IDevice dProxy = conn.GetObject<IDevice>(“org.freedesktop.NetworkManager.Device.Wired”, new ObjectPath(“/org/freedesktop/NetworkManager/Devices/0”));
```

But the above does not work. Can anybody tell me why?

A third smaller question. I have never done anything in C# before, mono seems to be doing quite well. Anyway, C# would not be the first thing on my mind when talking about developing linux applications. Is it 'normal' to do linux development in C# or is it just something you do for the fun of it?

In advanced, thanks

---

### Post by directhex on 2010-10-27
Looks like [http://www.ndesk.org/DBus_Documentation](http://www.ndesk.org/DBus_Documentation) mentions the properties thing.

---

### Post by hurra on 2010-10-28
Doh, but thanks for pointing out my ignorance :)

I had actually read that part of the documentation before, but I had misunderstood it untill you made me re-read it. And by accident it also solved my other problem.

String name = “org.freedesktop.NetworkManager”;
Org.freedesktop.DBus.Properties props = conn.GetObject<Properties>(name, new ObjectPath(“/org/freedesktop/NetworkManager”));
UInt32 state = (UInt32) props.Get(name, “State”);

My problem with connecting to others interfaces was that I had misunderstood the 'name' attribute, that is NOT referring to the interface name, but the bus name instead.

---

