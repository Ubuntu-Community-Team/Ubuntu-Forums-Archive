---
title: "C++11 GNU Issue with cmake"
date: 2014-04-27
forum: Programming Talk
---

### Post by andamaru on 2014-04-27
I'm writing an application and I'm using cmake and a few features from C++11, when I compile my application I get this error:

> 
Thisfilerequirescompilerandlibrarysupportforthe[COLOR=#c0c0c0]\[/COLOR]ISOC[COLOR=#000000]++[/COLOR][COLOR=#000080]2011[/COLOR]standard[COLOR=#000000].[/COLOR]Thissupportiscurrentlyexperimental[COLOR=#000000],[/COLOR][COLOR=#000000]and[/COLOR]mustbe[COLOR=#c0c0c0]\[/COLOR]enabledwiththe[COLOR=#000000]-[/COLOR]std[COLOR=#000000]=[/COLOR]c[COLOR=#000000]++[/COLOR][COLOR=#000080]11[/COLOR][COLOR=#000000]or[/COLOR][COLOR=#000000]-[/COLOR]std[COLOR=#000000]=[/COLOR]gnu[COLOR=#000000]++[/COLOR][COLOR=#000080]11[/COLOR]compileroptions[COLOR=#000000].[/COLOR]

I've added that option to cmake but I'm still getting the issue. What is the correct way to add it?

> 
[COLOR=#808000]cmake_minimum_required[/COLOR](VERSION2.8)
[COLOR=#808000]project[/COLOR](sky-network)
[COLOR=#808000]
add_definitions[/COLOR](-DBUILDING_DLL)

if(CMAKE_COMPILER_IS_GNUCXX)
[COLOR=#808000]  add_definitions[/COLOR](-std=c++11)
[COLOR=#808000]endif[/COLOR]()


I'm on Ubuntu 14.04 using QT Creator, everything is from their repo.

---

### Post by andamaru on 2014-04-27
I found the solution at this web site:

[http://stackoverflow.com/questions/15100351/changing-cmake-cxx-flags-in-project](http://stackoverflow.com/questions/15100351/changing-cmake-cxx-flags-in-project)

---

