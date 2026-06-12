---
title: "How to launch a script containing java execution line using Cron"
date: 2013-01-30
forum: Programming Talk
---

### Post by namoo on 2013-01-30
I have a script (runMyScript.sh) that contains five lines:
1 pkill java
2 pkill chrome
3 pkill chromedriver
4 pkill firefox
5 java -Xmn128M -Xms256M -Xmx512M -Dwebdriver.chrome.driver=/usr/selenium/chromedriver -jar /usr/selenium/selenium-server-standalone-2.28.0.jar -role node -nodeConfig /usr/selenium/nodeConfig.json

When I open a terminal and run rnMyScript.sh, all 5 lines are executed and I see things happening on my terminal.  When I run the same script using cron, only the first 4 lines are executed, but the last line does not run.  I know line 4 runs because when I leave firefox open, it gets terminated.

Can someone tell me what might I be doing wrong?  Thanks.

---

### Post by namoo on 2013-01-30
I figured out the problem.
For some reason my JAVA_HOME variable wasn't being applied in case of cron execution.  When I used the full path to the java binary, I was able to run the program.

---

### Post by Bucky Ball on 2013-01-30
*Thread moved to** Programming Talk***

---

