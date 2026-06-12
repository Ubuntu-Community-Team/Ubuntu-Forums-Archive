---
title: "Trouble running opengts from GPS2OpenGTS application"
date: 2014-01-26
forum: Programming Talk
---

### Post by IAMTubby on 2014-01-26
Hello,
 I have installed the opengts framework [http://opengts.sourceforge.net/](http://opengts.sourceforge.net/) successfully, but am facing a few issues when using the GPS2OpenGTS_Trial Android application. When I open the link ```
http://192.168.0.101:8080/gprmc/Data?acct=acct&dev=test01&gprmc=$GPRMC,172413,A,3848.8028,N,08957.3521,W,0,000.0,171111,,*16
``` in the browser, it gives me "OK". But, when I key in the following credentials (*1.Servername :192.168.0.101 2.PortNumber : 8080 3.UserID:acct 4.VehicleID : test01 5. CommunicationMode : HTTP 6.LoggingInterval :5*) and use the communication test screen in the application, it gives me ,**Getting Test [RX HTTP] : Error command**


 I tried going through the logs and feel a question mark(?) is missing between 'Data' and 'acct=acct' and so it gives 'Command not supported'. The logs from $GTS_HOME/logs/w-gprmc.log are as follows
```
[INFO_|01/26 14:58:41|Data.logInfo:1447] gprmc: [192.168.0.102] POST: http://192.168.0.101:8080/gprmc/Data acct=acct&dev=test01&gprmc=$GPRMC,092837,A,3128.7540,N,14257.6714,W,000.0,000.0,260114,,*7 [acct=acct&dev=test01&gprmc=$GPRMC,092837,A,3128.7540,N,14257.6714,W,000.0,000.0,260114,,*7]
[INFO_|01/26 14:58:41|Data._doWork:899] Command not supported:
```


Note 1 : In my webapp.conf, I have uncommented the lines 'gprmc.parm.account' and 'gprmc.parm.device' from the GPS2OpenGTS configuration and GPRMC properties sections.
Note 2 : Both devices(my computer on which opengts is running and the android device on which the GPS2OpenGTS_Trial is installed are connected to the same wifi and are pinging each other)

Please let me know how I can get the application to talk to the gts backend and any other details I need to provide.

Thanks.

---

### Post by innovatek on 2014-03-10
Hi,

Did you solve this? I have the same trouble.

Thanks!

---

### Post by IAMTubby on 2014-03-10
Hi innovatek,
As I said on PM, trying with an earlier version of OpenGTS worked for me.

---

