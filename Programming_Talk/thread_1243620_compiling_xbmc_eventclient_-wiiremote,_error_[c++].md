---
title: "compiling xbmc eventclient -wiiremote, error [c++]"
date: 2009-08-18
forum: Programming Talk
---

### Post by funkyjansson on 2009-08-18
Hi!

I'm trying to edit the Eventclient for letting a wiiremote controling XBMC so that it will start up xbmc when I hit the conect-button on the wiimote (or just the 1+2, it does the same thing).

However, even before I have changed anything I'l get a warning on compile, and an error at run.

```
micke@micke-desktop:~/Documents/XBMC/tools/EventClients/Clients/WiiRemote$ g++ WiiRemote.cpp -lcwiid -o WiiRemote
WiiRemote.cpp: In member function ‘void CWiiRemote::SetBluetoothAddress(const char*)’:
WiiRemote.cpp:158: warning: taking address of temporary
WiiRemote.cpp:158: warning: taking address of temporary
micke@micke-desktop:~/Documents/XBMC/tools/EventClients/Clients/WiiRemote$ sh WiiRemote 
WiiRemote: 1: Syntax error: "&" unexpected (expecting ")")
micke@micke-desktop:~/Documents/XBMC/tools/EventClients/Clients/WiiRemote$ 
```

(The code is C++)

I have tryed to check out more early versions from the svn-repos och even tryed to download both 8.10 and 9.04 from the source-downloadpage at xbmc.org, but I always get the exact same result.

I have done this before (but I reinstalled everything so I lost the code) so I figure there must be something wrong in my system now, sense it worked before and I know that the client works in both 8.10 and 9.04.

The only dependencies the sourcecode speaks of is the following.

```
// Compiles with g++ WiiRemote.cpp -lcwiid -o WiiRemote
// Preferably with libcwiid >= 6.0

#include "WiiRemote.h"
```

When I check in synaptic it says version 0.6.0.0 on libcwiid (so I presume it's right, despite the zero in front of the six) and WiiRemote.h lives in the same folder as WiiRemote.cpp.

Anyone have any idea about what can be wrong here?

---

### Post by dwhitney67 on 2009-08-18
First of all, I would fix the warning that the compiler is spitting out.

If I could see the offending code, then perhaps I could help you resolve the issue.

As for running the C++ program, why are you attempting to run it as if it were a shell script?

This statement produces a executable file that is your application:
```

g++ WiiRemote.cpp -lcwiid -o WiiRemote

```

To run the program:
```

./WiiRemote

```

---

### Post by funkyjansson on 2009-08-19
> **dwhitney67 said:**
> First of all, I would fix the warning that the compiler is spitting out.

If I could see the offending code, then perhaps I could help you resolve the issue.

As for running the C++ program, why are you attempting to run it as if it were a shell script?

This statement produces a executable file that is your application:
```

g++ WiiRemote.cpp -lcwiid -o WiiRemote

```

To run the program:
```

./Wiiremote

```

Ahh! Now I feel stupid, my bad. When I run it the right way everything works.

So, the warning.
The code is as follows
```
/* Basicly this just sets up standard control bits */
void CWiiRemote::SetBluetoothAddress(const char *btaddr)
{
  if (btaddr != NULL)
    str2ba(btaddr, &m_btaddr);
  else
    bacpy(&m_btaddr, &(*BDADDR_ANY));
}
```

Row 158 witch generates the warning is the last one, with "bacpy(&m_btaddr, &(*BDADDR_ANY));"

Tanks for the help.

---

