---
title: "Linux equivalent to MSDN's GetBestRoute() C++"
date: 2012-04-10
forum: Programming Talk
---

### Post by eskimo9 on 2012-04-10
Hi

I'm trying to port some network classes written in C++ for Windows to a Linux platform. Most of it is fairly straightforward, thanks to the C++ STL having a healthy set of equivalent headers for Linux and Windows, but there's one I haven't been able to find on Google.

The header file iphlpapi.h under Windows defines a method GetBest Route, with the following description:

```

//////////////////////////////////////////////////////////////////////////////
//                                                                          //
// Gets the best (longest matching prefix) route for the given destination  //
// If the source address is also specified (i.e. is not 0x00000000), and    //
// there are multiple "best" routes to the given destination, the returned  //
// route will be one that goes out over the interface which has an address  //
// that matches the source address                                          //
//                                                                          //
//////////////////////////////////////////////////////////////////////////////

DWORD
WINAPI
GetBestRoute(
    IN  DWORD               dwDestAddr,
    IN  DWORD               dwSourceAddr, OPTIONAL
    OUT PMIB_IPFORWARDROW   pBestRoute
    );

```

Is there a function in the C++ STL for Linux that does the same job? I'm using the g++ compiler, Linux kernel 2.6.

Thanks.

---

### Post by CynicRus on 2012-04-10
As such - no analogues, so that either implement the function yourself, or look in the direction of libwine, which in itself is a terrible crutch.

---

### Post by eskimo9 on 2012-04-10
Thanks CynicRus for the fast response.

Ok, so if there is no analogue to finding the best route path, what is the best way to check if a destination is reachable? I'm sure this sounds like a simple question, but I am really just getting my feet wet with networking, and with porting Windows apps to Linux.

The reason GetBestRoute was called was in the context of determining whether the destination was reachable. 

```

//Check to see if destination is reachable
MIB_IPFORWARDROW tester;
DWORD result;
result = GetBestRoute(ipAddr, 0, &tester);
//if error querying or local addresses mismatch when not connected via INADDR_ANY or no route found
if(result != NO_ERROR || ((tester.dwForwardDest != (localaddr.S_un.S_addr & localSubnet)) && localAddr.S_un.S_addr) || !tester.dwForwardDest)
{
   //throw exception
}
//Continue opening TCP socket connection

```

I apologise for the msdn code, but I'm hoping somebody recognises a neat way to do this in Linux C++. At least which part of the STL should I be looking in?

Thanks

---

