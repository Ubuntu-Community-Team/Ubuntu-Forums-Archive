---
title: "Mono, DBus and NetworkManager"
date: 2011-07-14
forum: Programming Talk
---

### Post by Uuranor on 2011-07-14
Hello, I'm facing some problems trying to add the notification of the network status using Mono and NetworkManager.
What I basically need is to being notified when the network interface is online or offline.
To do it I use dbus-sharp 0.7  (I obtain the same result with Ndesk.DBus 0.6) to receive the signals from NetworkManager but ...well, that lib doesn't fire any event at all. I tried the same small application in OpenSUSE 11.4. 

In here  you can find a simplified version of  the main body of the program: [http://pastebin.com/Eq0v2qTN](http://pastebin.com/Eq0v2qTN)
And in here the interfaces and the enums used: [http://pastebin.com/47CGa57C](http://pastebin.com/47CGa57C)

I'm probably doing something _very_ stupid, but I can't figure out what. What it makes me even more confused is the fact I almost replicated the code of Banshee and of some other objects, but the result is the same. Following the specifications of NetworkManager I removed all the deprecated methods and signals, but actually the only thing it works is ...a deprecated method to obtain the initial status.
Anyone has any idea?

Thanks for any hint,
Mat.

PS: can't wait for Mono 2.12 with the implementation of System.Net.NetworkInformation! WooT! \ò/

---

