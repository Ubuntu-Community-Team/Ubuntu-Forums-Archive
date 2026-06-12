---
title: "Linux and .Net"
date: 2010-10-13
forum: Programming Talk
---

### Post by BetterSense on 2010-10-13
I'm upgrading some industrial equipment. I plan to use a PC running Linux for the main control computer. Part of the upgrade involves replacing the legacy laser controller with a new, modern one. The new, modern replacement that I have found apparently is only operable through a .Net API--it has serial and remote TCP/IP interfaces, but they are crippled compared to the capabilities that are available through the API methods. 

From TFM:
```

The API is implemented in Microsoft C# language and is distributed as Windows .Net assemblies.
In order to use this API to develop an application you have to refer the following two DLL's:
• Etl.Hardware.ScanDevice.Base.dll
• Etl.Hardware.ScanDevice.ScanInterface.dll
In order to run the application with the EC1000 Scan card, the following two DLL's must be available in
the application folder:
• Etl.Hardware.ScanDevice.dll
• Etl.Hardware.ScanDevice.EC1000.dll
Rev. 1.0.0_
```

Will I (or rather, will the programmers that I hire) be able to control this device through the API using a Linux box? 

It boggles the mind that a company would use .Net to do this for a piece of industrial equipment that is expected to have a 20 year lifespan.

---

### Post by scrooge_74 on 2010-10-13
And then beware of windows viruses design to cripple Iranian nuclear power plants making its way into your equipment

---

### Post by worseisworser on 2010-10-13
Whether it'll work or not is pretty much a gamble.

.Net is Windows only, and Mono is not .Net.

[http://en.wikibooks.org/wiki/File:VennSymmetricDifference.jpg](http://en.wikibooks.org/wiki/File:VennSymmetricDifference.jpg)

This is probably one of those things one will have to try out to be able to see or say anything. If you are lucky the Mono environment will give you proper feedback as to what it determines will not work and the developers can resolve this -- perhaps in collaboration with the ones providing these libraries. If you are not so lucky it'll simply appear to run OK, but actually have bugs. If you are lucky everything will run OK.

> It boggles the mind that a company would use .Net to do this for a piece of industrial equipment that is expected to have a 20 year lifespan.

I agree.

---

### Post by directhex on 2010-10-13
> **BetterSense said:**
> I'm upgrading some industrial equipment. I plan to use a PC running Linux for the main control computer. Part of the upgrade involves replacing the legacy laser controller with a new, modern one. The new, modern replacement that I have found apparently is only operable through a .Net API--it has serial and remote TCP/IP interfaces, but they are crippled compared to the capabilities that are available through the API methods. 

From TFM:
```

The API is implemented in Microsoft C# language and is distributed as Windows .Net assemblies.
In order to use this API to develop an application you have to refer the following two DLL's:
&#8226; Etl.Hardware.ScanDevice.Base.dll
&#8226; Etl.Hardware.ScanDevice.ScanInterface.dll
In order to run the application with the EC1000 Scan card, the following two DLL's must be available in
the application folder:
&#8226; Etl.Hardware.ScanDevice.dll
&#8226; Etl.Hardware.ScanDevice.EC1000.dll
Rev. 1.0.0_
```

Will I (or rather, will the programmers that I hire) be able to control this device through the API using a Linux box? 

It boggles the mind that a company would use .Net to do this for a piece of industrial equipment that is expected to have a 20 year lifespan.

The answer is "it depends".

If their assemblies are 100% managed (i.e. pure .NET code, no C libraries; annoyingly they're both named .dll in Windows), AND if those managed assemblies are completely cross-platform in design (e.g. they don't try to run commands from c:\windows\system32\user32.dll or similar), then Mono should be fine. In that regard, you have a much higher chance of the TCP/IP interface being cross-platform than the RS232 one.

There's an app on mono-project.com called MoMA, which can scan assemblies & give a portability report.

---

### Post by BetterSense on 2010-10-13
> In that regard, you have a much higher chance of the TCP/IP interface being cross-platform than the RS232 one.

Let me clarify. The device in question has 3 interfaces

The .Net API
An RS232 interface
A TCP/IP "remote" interface that is documented but very limited.

Basically everything interesting that the controller does has to be done through methods of the .Net API, as far as I can tell. The other two interfaces are just for basic control. 

So, were you saying that my chances of the .Net API being cross-platform are higher than the chances of the RS232 interface being xplatform? Why; RS232 is completely cross platform isn't it?

---

### Post by directhex on 2010-10-13
> **BetterSense said:**
> Let me clarify. The device in question has 3 interfaces

The .Net API
An RS232 interface
A TCP/IP "remote" interface that is documented but very limited.

Basically everything interesting that the controller does has to be done through methods of the .Net API, as far as I can tell. The other two interfaces are just for basic control. 

So, were you saying that my chances of the .Net API being cross-platform are higher than the chances of the RS232 interface being xplatform? Why; RS232 is completely cross platform isn't it?

Sorry, I think I misunderstood your initial description of the interfaces on the device.

At any rate, try flinging the libraries they've provided into MoMA.

---

