---
title: "airport-utils --&gt; where to find how to info"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by JeremySchubert on 2012-01-02
Using 11.10.  I've just installed a package called airport-utils through the Software Center.  It says to run it though Terminal.  But I can't find any documentation such as where to navigate to in terminal and what commands are available.  Can anyone help me out here?
Thanks,
Jeremy

---

### Post by bluexrider on 2012-01-02
[http://packages.ubuntu.com/hardy/airport-utils](http://packages.ubuntu.com/hardy/airport-utils)

[http://bamajr.com/2011/02/01/kubuntu-configure-an-airport-base-station-in-linux/#more-4882](http://bamajr.com/2011/02/01/kubuntu-configure-an-airport-base-station-in-linux/#more-4882)

may help

---

### Post by danran on 2012-03-15
```
man airport2-config
```

that's all I found so far. there's a debug command argument it says you can set, but it's not working for me.

```
sudo airport2-config DEBUG=1
```

*UPDATE

it appears the airport2-config is a wrapper script for this jar file, running this command returns nothing to the terminal. Is this supposed to launch a gui?

```
me@here:~$ java -jar /usr/share/java/airport-utils/Airport2BaseStationConfig.jar
me@here:~$ echo $?
0
```

---

