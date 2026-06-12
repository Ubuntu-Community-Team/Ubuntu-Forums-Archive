---
title: "c++ ns3 simulator compiling error"
date: 2013-04-17
forum: Programming Talk
---

### Post by binaryperson on 2013-04-17
Hello. I am trying to compile the code below using the command line. The error I get is: 

```
one.cpp:8:29: fatal error: ns3/core-module.h: No such file or directory compilation terminated.
```

This how I am compiling:

```
g++ -o one one.cpp
```

Can someone please explain how to compile this code through the command line?

Note: When I try to compile using Geany it compiles fine. 

Tutorial:

[http://www.nsnam.org/docs/tutorial/singlehtml/index.html](http://www.nsnam.org/docs/tutorial/singlehtml/index.html)

```

/*
 * UdpEchoClient     UdpEchoServer
 *   10.1.1.1          10.1.1.2
 *      n0 -------------- n1
 *         point-to-point
 */

#include <ns3/core-module.h>
#include <ns3/network-module.h>
#include <ns3/internet-module.h>
#include <ns3/point-to-point-module.h>
#include <ns3/applications-module.h>

using namespace ns3;

int main ()
{
  LogComponentEnable ("UdpEchoClientApplication", LOG_LEVEL_INFO);
  LogComponentEnable ("UdpEchoServerApplication", LOG_LEVEL_INFO);

  NodeContainer nodes;
  nodes.Create (2);

  PointToPointHelper pointToPoint;
  pointToPoint.SetDeviceAttribute ("DataRate", StringValue ("5Mbps"));
  pointToPoint.SetChannelAttribute ("Delay", StringValue ("2ms"));

  NetDeviceContainer devices;
  devices = pointToPoint.Install (nodes);

  InternetStackHelper stack;
  stack.Install (nodes);

  Ipv4AddressHelper address;
  address.SetBase ("10.1.1.0", "255.255.255.0");

  Ipv4InterfaceContainer interfaces;
  interfaces = address.Assign (devices);

  UdpEchoServerHelper echoServer (9);

  ApplicationContainer serverApps = echoServer.Install (nodes.Get (1));
  serverApps.Start (Seconds (1.0));
  serverApps.Stop (Seconds (10.0));

  UdpEchoClientHelper echoClient (interfaces.GetAddress (1), 9);
  echoClient.SetAttribute ("MaxPackets", UintegerValue (1));
  echoClient.SetAttribute ("Interval", TimeValue (Seconds (1.0)));
  echoClient.SetAttribute ("PacketSize", UintegerValue (1024));

  ApplicationContainer clientApps = echoClient.Install (nodes.Get (0));
  clientApps.Start (Seconds (2.0));
  clientApps.Stop (Seconds (10.0));

  Simulator::Run ();
  Simulator::Destroy ();
  return 0;
}

```

---

### Post by dwhitney67 on 2013-04-18
Typically, system and other package header files are placed in /usr/include (sometimes in /usr/local/include).

You should verify that the directory /usr/include/ns3 exists on your system, and that it has the file core-module.h.  If you lack the former, then you should consider installing the ns3 development package, which undoubtedly will provide the header files and associated shared-object (possibly static) libraries.

If all you are missing is the header file, then you need to ensure that the code you are developing is conformant with the version of ns3 that you are using.

---

### Post by r-senior on 2013-04-18
The tutorial is a very long document but, as far as I can see, you are expected to used a custom build tool called "waf" to build projects? Judging by the output this tool does a similar job to GNU Autotools and I would expect that involves setting up the correct library and header paths.

Is there somewhere you have found that suggests you can build directly with g++ without using waf?

---

### Post by binaryperson on 2013-04-18
I was instructed to use Geany to compile and run the program. Geany compiles and runs the program without any problems. I prefer using a command line text editor so I was just wondering why this error is coming up. It's all right, I'll just use Geany. Unless someone can explain how to use "waf".

---

### Post by steeldriver on 2013-04-18
Are you running geany in the same directory that you are trying to compile from?

Is there a custom compile / build environment ('Set Build Commands' under the 'Build' menu)?

You can always add the -v switch to g++ which will show you explicitly which include paths it is searching e.g.

```
$ g++ -v -Wall -o "hello" "hello.cpp"
.
.
.
GNU C++ (Ubuntu/Linaro 4.6.3-1ubuntu5) version 4.6.3 (i686-linux-gnu)
    compiled by GNU C version 4.6.3, GMP version 5.0.2, MPFR version 3.1.0-p3, MPC version 0.9
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring nonexistent directory "/usr/local/include/i386-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i686-linux-gnu/4.6/../../../../i686-linux-gnu/include"
[B]#include "..." search starts here:
#include <...> search starts here:
 /usr/include/c++/4.6
 /usr/include/c++/4.6/i686-linux-gnu/.
 /usr/include/c++/4.6/backward
 /usr/lib/gcc/i686-linux-gnu/4.6/include
 /usr/local/include
 /usr/lib/gcc/i686-linux-gnu/4.6/include-fixed
 /usr/include/i386-linux-gnu
 /usr/include
End of search list.
[/B]GNU C++ (Ubuntu/Linaro 4.6.3-1ubuntu5) version 4.6.3 (i686-linux-gnu)
    compiled by GNU C version 4.6.3, GMP version 5.0.2, MPFR version 3.1.0-p3, MPC version 0.9
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 2ed62271b86e2b75137544459bab1a81
COLLECT_GCC_OPTIONS='-v' '-Wall' '-o' 'hello' '-shared-libgcc' '-mtune=generic' '-march=i686'
```

---

### Post by binaryperson on 2013-04-18
I am using a prepackaged Linux image. I tried compiling using Geany on another computer and I got an error. I tried compiling through the command line on the Linux image and I again got the error. So, I can only compile and run in Geany on the prepackaged image. So I'm guessing the person that made the image and installed geany somehow added the libraries and linked them.

---

