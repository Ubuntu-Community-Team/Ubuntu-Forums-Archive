---
title: "Newbie: Errors in iPhone app"
date: 2011-09-27
forum: Programming Talk
---

### Post by Azareus on 2011-09-27
Hi guys! I'm really newbie in iOS and I have to handle a complicated situation. I was given an iPhone app developed by someone and I have to make it work. The guy who developed it has told me that it worked, but sometimes crashed in an iPhone. I've never developed using iOS and I don't really know how this app works.

Well, when I open the app with Xcode, the first problem that I detect is some errors with the references. The app uses the project CorePlot-CocoaTouch.xcodeproj. I've added again this project and solved the references (I've followed some other posts like this one: [http://www.jaysonjc.com/programming/pie-chart-drawing-in-iphone-using-core-plot-library.html](http://www.jaysonjc.com/programming/pie-chart-drawing-in-iphone-using-core-plot-library.html)). 

I want to test it with the simulator (I don't have an iPhone yet). I have a doubt here...should I use iOS Device, or iOS Simulator as Base SDK? Firstly I chose iOS Simulator, but it appeared a problem with Cocoa.framework (it turned into red).

Anyway, using iOS Device as Base SDK, I build the project and it says "Build failed (59 errors, 3 warnings)". I check out the errors, and most of them are "Expected specifier-qualifier-list before ..."

Can anyone help me? This is more or less the situation, but I can provide more expecific details if they're needed.

I'm sorry if I'm talking about something really basic, but I've been trying to solve it for 2 weeks and I give up. I've tried to talk to the guy, but he's not really helpful..

---

