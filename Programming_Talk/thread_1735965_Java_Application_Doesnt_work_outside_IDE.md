---
title: "Java Application Doesnt work outside IDE"
date: 2011-04-22
forum: Programming Talk
---

### Post by shababhsiddique on 2011-04-22
Hi

I have a program developed under java with netbeans. It has a text  pane that takes text written in non English language and do some operation including save open new.....

 The program was fine and complete worked flawlessly when i run it from netbeans. But when i go to the dist folder and run the jar (which was supposed to be the executable) it runs good but when i open a previously saved file to the editor it shows mysterious fonts.
like-
    
    &#2482;&#2495;&#2454; "The original inputs are" << &#2472;&#2468;&#2497;&#2472;_&#2482;&#2494;&#2439;&#2472;;
    &#2458;&#2482;&#2476;&#2503;(&#2488;&#2434;&#2454;&#2509;&#2479;&#2494; &#2474;=&#2534;;&#2474;<&#2479;&#2468;&#2463;&#2494;;&#2474;++)

becomes

  à¦²à¦¿à¦– "The original inputs are" << à¦¨à¦¤à§&#65533;à¦¨_à¦²à¦¾à¦‡à¦¨;
    à¦šà¦²à¦¬à§‡(à¦¸à¦‚à¦–à§&#65533;à¦¯à¦¾ à¦ª=à§¦;à¦ª<à¦¯à¦¤à¦Ÿà¦¾;à¦ª++)

is there something i need to do to publish JAR when native support is required?

---

### Post by An Sanct on 2011-04-22
The encoding is wrong ... can you set the encoding to be UTF8 like:
```
file.encoding=UTF-8
``` in eclipse?

PS. got this from a Netbeans forum

> If you right-click on your project in the  projects pane, and choose Properties, then Sources, there is a drop-down  box for encoding where you can choose UTF-8.

---

### Post by shababhsiddique on 2011-04-22
Got my solution here

[http://stackoverflow.com/questions/5752323/java-native-language-application-doesnt-work-outside-ide](http://stackoverflow.com/questions/5752323/java-native-language-application-doesnt-work-outside-ide)

---

